---
name: call-follow-up
description: Turn my call into a follow-up email. Transcribes a call recording, pulls out who decides, what they have, what they want and the agreed next step, then drafts a short follow-up email and a calendar invite, using only what was said on the call. Use after any sales, partner, client or intro call, and when the user says "follow up on my call", "write up the call" or shares a call recording or transcript.
---

# Turn my call into a follow-up email

You just finished a call. This skill turns the recording into a short email the other side can act on, plus a
calendar invite for the next meeting. It uses only what was said. Nothing is added, guessed or turned into a
promise nobody made.

## Step 1. Get a transcript

If the user has a transcript, use it. If they have a recording (phone voice memo, Zoom or Meet file), transcribe
it. Any tool works. A free one that runs on your own computer is faster-whisper (a speech-to-text program):

```bash
pip install faster-whisper
python -c "from faster_whisper import WhisperModel; m=WhisperModel('small'); s,_=m.transcribe('call.m4a'); [print(f'[{int(x.start//60):02d}:{int(x.start%60):02d}] {x.text.strip()}') for x in s]" > call_transcript.txt
```

Use a bigger model (`medium` or `large-v3`) for better accuracy if the computer can handle it. Keep the
transcript private. It is a record of someone else's words.

Speech-to-text gets names and product words wrong. Fix them against the emails or notes you already have, and
mark any name you cannot confirm.

## Step 2. Pull out what matters

Read the whole transcript. Write down each of these with its timestamp:

- **Who decides.** Did they say who makes the call? Quote it ("I'm the owner").
- **What they have.** Products, stock, people, budget, dates, as they said them.
- **What they want.** What they asked for, what they said no to, any worry they raised.
- **The agreed next step.** What happens, who does it, the day and time, and whose time zone.
- **What you promised.** Anything the user said they would send or do.
- **Open questions.** Anything left unanswered.

If something was not said, it does not go in. If a time was mentioned but not agreed, it is not agreed.

## Step 3. Draft the email

Short and plain, under about 150 words. Shape:

1. One line of thanks and the reason for the email.
2. Three to five bullets: what you heard. Quote their exact words where the words decide something (a number,
   a yes, a condition).
3. What you will do, and by when.
4. The next step with the day, and the time in **both** time zones (for example "Thursday 11:30am Eastern /
   8:30am Pacific").
5. Sign-off.

If the user has a partner or teammate on the deal, write them a second, shorter note: who decides, what the other
side has, the next step, and what the partner should do before it.

## Step 4. Draft the calendar invite

Title (both company names and the purpose), date, start time in the organizer's time zone, length, who is
invited, the video link or phone number, and two lines of agenda taken from the call.

## Step 5. Show the user before anything is sent

- Show the email, the partner note and the invite as drafts. Never send or book anything without the user's OK.
- Next to each fact, show where it came from: the timestamp in the transcript.
- List anything you marked as unclear, so the user can fix it before sending.

## Rules

- Never invent anything that is not in the transcript or the user's own notes. No made-up prices, dates or
  agreements.
- Quote, do not paraphrase, when the exact words decide something.
- Never paste the full transcript into the email.

## Example

The user shares `call.m4a` from a call with Sam Rivera at Acme Trailer Rentals. (Sam and Acme are made up.)

At [01:45] Sam says "I'm the owner." At [03:10] he says "Thursday at 11:30 my time works." Sam is on Eastern time.
The user is on Pacific time.

The draft email:

> Hi Sam,
>
> Thanks for the time today. Here is what I heard:
>
> - You have two trailers free now and one coming back this week.
> - You are open to leasing them to the customers on our list.
> - You make the call on new business ("I'm the owner").
>
> I will send the terms by end of day tomorrow.
>
> Next step: a 15-minute call on Thursday at 11:30am Eastern / 8:30am Pacific. Invite to follow.
>
> Alex
