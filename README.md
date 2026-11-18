# KeepAISharp Skills

Free skills that make your AI agent check its homework: prep you for a call, turn the call into a follow-up email, research before it builds, and the real COPPA rules for any product a child might use.

Each skill is a folder with one `SKILL.md` file of instructions. They follow the open [Agent Skills](https://agentskills.io) format, so they work in Claude Code, OpenAI Codex, Cursor, Gemini CLI, GitHub Copilot and other agents that read `SKILL.md`.

```bash
npx skills add coding-island-js/keepaisharp-skills
```

## The skills

| Skill | What it does | When your agent uses it |
|---|---|---|
| [Prep me for a call](skills/call-prep/SKILL.md) (`call-prep`) | Writes a one-page call sheet you can read on your phone: the opening line, the two things you need from the call, what to say if they pick up or you get voicemail, and every fact checked at its source. | Before any sales, partner, client or intro call, and when you say "prep me for a call". |
| [Turn my call into a follow-up email](skills/call-follow-up/SKILL.md) (`call-follow-up`) | Transcribes the recording, pulls out who decides, what they have, what they want and the agreed next step, then drafts a short follow-up email and a calendar invite. Uses only what was said, and shows you the draft before anything is sent. | Right after a call, or when you share a call recording or transcript. |
| [research-first](skills/research-first/SKILL.md) | Stops the agent from designing, writing or building until a research file with a source for every fact covers five parts: the reader, how similar things succeed, competitors, the look, and the facts. | Before any landing page, sales page, email, video, resume or demo, and when you ask "did you do the research?" |
| [kids-privacy](skills/kids-privacy/SKILL.md) | The rules of COPPA (the US Children's Online Privacy Protection Rule, 16 CFR Part 312, as amended in 2025), each linked to its section, plus a 21-line check for a kids' privacy page. Not legal advice. It gets a page ready for a lawyer's read. | When you build or review a product a child under 13 might use, or mention COPPA, parental consent, kids' sign-up, children's data or data retention for kids. |

## Install

The first line works for most agents. The others are each agent's own route.

| Agent | How to install |
|---|---|
| Any agent (recommended) | `npx skills add coding-island-js/keepaisharp-skills` (add `-s research-first` for one skill, `-a <agent>` to pick an agent) |
| Claude Code | `/plugin marketplace add coding-island-js/keepaisharp-skills` then `/plugin install keepaisharp-skills@keepaisharp` |
| Any agent, through GitHub CLI 2.90 or later | `gh skill install coding-island-js/keepaisharp-skills <skill>` (per docs) |
| claude.ai | Zip the `skills/<skill>` folder. Then Customize > Skills > + > Create skill > Upload a skill. Code execution must be on. (per docs) |
| OpenAI Codex | `npx skills add coding-island-js/keepaisharp-skills -a codex`, or copy the folder to `~/.agents/skills/<skill>` (per docs) |
| Cursor | `npx skills add coding-island-js/keepaisharp-skills -a cursor`, or copy the folder to `.agents/skills/<skill>` (per docs) |
| Gemini CLI | `gemini skills install https://github.com/coding-island-js/keepaisharp-skills.git --path skills/<skill> --consent` (per docs) |
| GitHub Copilot | `gh skill install coding-island-js/keepaisharp-skills <skill> --agent github-copilot`, or copy the folder to `.github/skills/<skill>` (per docs) |
| By hand | `git clone https://github.com/coding-island-js/keepaisharp-skills` and copy `skills/<skill>` into your agent's skills folder |

"Per docs" means the line comes from that agent's own documentation and has not been tested here yet.

## Examples

**research-first.** You type: "Make a landing page for my bookkeeping service." Instead of writing the page, the agent first writes a research file: who the readers are and the words they use, how similar services get people to buy (book a call or pay online), 5 to 8 of the best real pages, what makes those look good, and every claim the page will make checked at its source. Only then does it build, and the page cites the file. If you ask "did you do the research?", it answers with the file path and which of the five parts it covers.

**kids-privacy.** You type: "Check the privacy page for my spelling app for kids." The agent runs the 21-line check and reports each line as PASS, FAIL or ASK with its section, for example: "8. Retention policy inside the page, with purpose, business need and a numeric timeframe per item? FAIL. The page says 'as long as necessary'. [§ 312.10]" Open questions are marked **[for the lawyer]** so you know what to take to one.

## What's in the repo

```
skills/<name>/SKILL.md          one folder per skill
.claude-plugin/marketplace.json  lets Claude Code install the skills as a plugin
AGENTS.md                        rules for an agent that edits this repo
```

## Contributing

Fixes and new skills are welcome as pull requests. Keep the skill folder name and the `name:` field the same, write the `description` as "what it does, then when to use it", keep `SKILL.md` under 500 lines, and add the skill to the table above and to `.claude-plugin/marketplace.json`. For the law in kids-privacy, link the section you are quoting.

## License

MIT. See [LICENSE](LICENSE).

Made by Raj Lakhani / KeepAISharp, [github.com/coding-island-js](https://github.com/coding-island-js).
