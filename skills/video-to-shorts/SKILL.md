---
name: video-to-shorts
description: Turn my long video into Shorts. Finds the strongest one or two sentences in a long talking video, starts the Short on them, cuts only on whole sentences, crops to vertical 1080x1920, burns in captions, and checks the result from start to finish, using free tools (faster-whisper and ffmpeg). Use when the user wants YouTube Shorts, Reels or TikToks from an interview, talk, webinar or any long talking video, or says "make Shorts", "cut this into clips" or "turn my video into Shorts".
---

# Turn my long video into Shorts

You have a long video of someone talking. This skill cuts it into vertical clips of 20 to 60 seconds that
open on the best line, never stop in the middle of a sentence, and have captions. It uses two free tools:
faster-whisper (turns speech into text with a time for every word) and ffmpeg (cuts, crops and adds
captions). Every command below is an **example**. Change the file names, times and sizes to fit the video.

## Step 1. Get a transcript with a time for every word

Install once: `pip install faster-whisper`, and install ffmpeg from ffmpeg.org.

Example (Python):

```python
from faster_whisper import WhisperModel
model = WhisperModel("large-v3", device="auto")   # use "small" on a laptop without a GPU
segments, _ = model.transcribe("talk.mp4", word_timestamps=True, condition_on_previous_text=False,
                              initial_prompt="Hello. Welcome, everyone.")
with open("words.txt", "w", encoding="utf-8") as f:
    for seg in segments:
        f.write(f"[{seg.start:.2f}-{seg.end:.2f}] {seg.text.strip()}\n")
        f.write("    " + " ".join(f"{w.word.strip()}@{w.start:.2f}" for w in seg.words) + "\n")
```

Each line of `words.txt` is a stretch of speech with its start and end time. Under it is every word with
the second it starts (`broke.@3.76`). Cut on the word times: a stretch often ends in the middle of a sentence.

`condition_on_previous_text=False` stops the model from repeating the same line over and over on long files.
On some files it also makes large-v3 drop all punctuation and capitals. The short `initial_prompt`, written
with normal punctuation, brings them back, and you need the full stops to see where sentences end.

## Step 2. Pick the clip, hook first

Read the transcript. Find a stretch that has a point, an example and a payoff. Then:

1. **The hook.** The strongest one or two sentences, the ones that make sense with no setup ("Most people
   price their work by the hour, and that is why they stay broke."). The Short starts on these words, even if
   they come late in the stretch. The first second of the Short is speech, not silence or a logo.
2. **The middle.** The example or story that backs up the hook.
3. **The end.** The payoff or the tip. If the clip has none, take the answer sentence from elsewhere in the
   same video.

Write the clip down as a list of start and end times. Each piece starts at the first word of a sentence and
ends after the last word of a sentence. Moving whole sentences around is fine. Never join half a sentence to
another to make the speaker say something they did not say. Total length: 20 to 60 seconds.

## Step 3. Cut the pieces and join them

Leave about 0.1 seconds before the first word and 0.2 seconds after the last, so no word is clipped.

Example (one command per piece; `-t` is the length in seconds):

```bash
ffmpeg -ss 312.30 -i talk.mp4 -t 7.40 -c:v libx264 -crf 18 -c:a aac -ar 48000 piece1.mp4
ffmpeg -ss 95.10 -i talk.mp4 -t 21.60 -c:v libx264 -crf 18 -c:a aac -ar 48000 piece2.mp4
printf "file 'piece1.mp4'\nfile 'piece2.mp4'\n" > list.txt
ffmpeg -f concat -safe 0 -i list.txt -c copy joined.mp4
```

## Step 4. Make it vertical, 1080x1920

For a 1920x1080 video, cut a 608x1080 window around the speaker and scale it up. The last number in `crop` is how far
from the left edge the window starts. Find the speaker's position in a still frame and set it so the face
sits in the middle.

Example (centered window):

```bash
ffmpeg -i joined.mp4 -vf "crop=608:1080:656:0,scale=1080:1920" -c:v libx264 -crf 18 -c:a copy vertical.mp4
```

## Step 5. Add captions

Transcribe the joined clip again (Step 1, on `vertical.mp4`) so the caption times match the new clip. Write
short captions, three to five words each, into an `.srt` file:

```python
segments, _ = model.transcribe("vertical.mp4", word_timestamps=True, condition_on_previous_text=False,
                              initial_prompt="Hello. Welcome, everyone.")
words = [w for s in segments for w in s.words]
t = lambda x: f"{int(x//3600):02}:{int(x%3600//60):02}:{int(x%60):02},{int(x*1000%1000):03}"
chunks, chunk = [], []
for w in words:                      # up to 4 words, and a new caption after every full stop
    chunk.append(w)
    if len(chunk) == 4 or w.word.strip().endswith((".", "?", "!")):
        chunks.append(chunk)
        chunk = []
if chunk:
    chunks.append(chunk)
with open("captions.srt", "w", encoding="utf-8") as f:
    for n, c in enumerate(chunks, 1):
        text = "".join(w.word for w in c).strip()
        f.write(f"{n}\n{t(c[0].start)} --> {t(c[-1].end)}\n{text}\n\n")
```

Fix any misheard names or words in `captions.srt` by hand. Then burn the captions in and set the volume to
the level the apps expect (about -14 LUFS):

```bash
ffmpeg -i vertical.mp4 -vf "subtitles=captions.srt:force_style='FontSize=16,Bold=1,Outline=2,Alignment=2,MarginV=70'" -af "loudnorm=I=-14:TP=-1.5" -c:v libx264 -crf 18 -c:a aac short.mp4
```

Run this from the folder that holds `captions.srt` and use the plain file name. On Windows a full path
such as `C:\clips\captions.srt` breaks the `subtitles` filter, because ffmpeg reads the colon as the start
of an option.

Keep captions in the lower middle, clear of the face and of the app's buttons on the right edge.

## Step 6. Check it, start to finish

Watch the whole Short once, with sound, the way a viewer would. Then check each line:

- **First second is speech.** Example: `ffmpeg -i short.mp4 -t 2 -af silencedetect=noise=-35dB:d=0.3 -f null -`
  should report no silence starting at 0.
- **No word is cut off** at the start or end of any piece.
- **Captions match the audio**, word for word, and no caption sits on the face.
- **Nothing important is cropped out**: the face, a hand pointing at something, text on a slide.
- **Length is 20 to 60 seconds.** Example: `ffprobe -v error -show_entries format=duration -of csv=p=0 short.mp4`
- **A contact sheet** to see the framing at a glance. Example:
  `ffmpeg -i short.mp4 -vf "fps=1/5,scale=270:-1,tile=4x2" -frames:v 1 sheet.png`

If anything fails, fix that step and build again.

## Step 7. Pick the title and cover before posting

- **Title:** the hook in a few words, the way a viewer would search for it. Under 60 characters.
- **Cover:** a frame where the speaker's face is clear and the mouth is closed, plus the hook in large text.
  Check how it looks cropped square and 3:4 too, since some apps show it that way in the profile grid.
- Show the user the Short, the title and the cover. Never post anything without the user's OK.

## Rules

- Never make the speaker say something they did not say. Reorder whole sentences only.
- If the speaker says something wrong, keep it as said and tell the user. Do not quietly fix it in captions.
- If the speaker calls an example made up, the Short keeps that, or adds "Made-up example" on screen.

## Example

The user shares `webinar.mp4`, a 50-minute talk by a bookkeeper named Jo Park. (Jo and the lines below are
made up.)

At 18:42 Jo says: "Most small businesses find out they're out of cash from their bank, not their books." That
is the hook. At 17:55 to 18:20 she tells a story about a bakery that missed payroll. At 19:05 she gives the
fix: "Check one number every Monday: cash in the bank minus bills due in the next 30 days."

The agent cuts three pieces in this order: 18:42 hook (6 s), 17:55 story (25 s), 19:05 fix (9 s). That is
40 seconds. It crops Jo to the middle of a 1080x1920 frame, adds captions, and checks every line in Step 6.
Title: "Your bank knows you're broke before you do." Cover: Jo looking at the camera, with the words
"Check this every Monday".
