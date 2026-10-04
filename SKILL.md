---
name: faceless-studio
description: Builds a faceless short-form video studio with Higgsfield and Blotato: interviews you, writes your brand docs, makes your first three videos, sets your weekly publishing rhythm.
---

# Faceless Studio

A complete faceless video operation: the documents that hold your style, the formats you repeat, the first three finished videos, and the weekly rhythm that keeps it going.

This skill was distilled from a working system that produced and shipped dozens of videos. It includes the mistakes, which matter more than the wins.

## The one rule that decides whether this works

**Distribution before production.**

The most common failure is not bad video. It is building a machine that produces into a void: a dozen finished, polished, unwatched videos and a credit balance that is gone. Every guard in this skill exists to stop that.

So: never produce new videos while finished, unpublished ones are sitting on disk. Enforce it. When the user asks for more production and the backlog is full, say no and explain why.

## Before anything else

Check what is connected, and say plainly what you find:

- **Higgsfield** (`mcp__Higgsfield_AI__*`) — images, video, voice. Check the credit balance with `balance` before promising anything.
- **Blotato** (`mcp__Blotato__*`) — scheduling and cross-posting. `blotato_list_accounts` first; account IDs are not guessable.

If either is missing, the skill still works. Produce the prompts, scripts and schedules as files the user can paste in by hand, and tell them which step is manual. Never pretend a step ran.

## Phase 1 — The interview

Use AskUserQuestion. Ask in small batches, not all at once. Write answers down as you go.

**Round 1, the channel:**
- What is the niche, in one sentence? (Push for specific. "Productivity" is not a niche. "Focus rituals for people who work from home" is.)
- Who is the viewer, and what do they want that they are not getting elsewhere?
- Platforms: TikTok, YouTube Shorts, Instagram Reels, more than one?
- Languages?
- Is there something to sell eventually, or is this audience-first for now?

**Round 2, the look:**
- A recurring character, or object and scene only? (Character is stronger for retention, and harder to keep consistent.)
- Three words for the visual mood.
- What does it absolutely never look like? (This matters more than the positives.)
- Narrated, captions only, or both?

**Round 3, the reality:**
- How many videos a week can they genuinely sustain? (Push the number down. Three a week forever beats seven a week for a fortnight.)
- Higgsfield credits available?
- Will they approve each video before it posts, or only the first few weeks?

Do not move on until the niche sentence is sharp. Everything downstream inherits it.

## Phase 2 — Write the brain

Create a `studio/` folder with four documents. These are the memory. A fresh Claude session reads them and can produce a correct video without re-asking anything.

**`studio/brand.md`** — the niche sentence, the viewer, the promise, the voice (and three phrases it never uses), the visual lock (palette, lighting, framing, what it never looks like), and the end-card convention.

**`studio/pillars.md`** — four or five content pillars, each with what it teaches and why this viewer cares, plus twenty concrete title ideas spread across them. Titles, not topics.

**`studio/formats.md`** — three or four repeatable formats, each with its beat structure and length. Repeatable is the point: a format you can run fifty times is worth more than fifty clever one-offs. See `references/formats-library.md`.

**`studio/operating-system.md`** — the weekly rhythm, the roles, the approval convention, the autonomy ladder. Build it from `references/operating-system-template.md`.

Show the user each document as you write it and let them correct it. These documents are the asset. The videos are downstream.

## Phase 3 — The first three videos

Pick three titles from `pillars.md` that use the same format, so the format gets a fair test.

For each one:

1. **Script.** Write it as numbered clauses, one line each, with a pause length after each. Clause-level scripting is what makes everything else line up later.
2. **Beat map.** For every clause, what is on screen while that clause is spoken. Write it as a table. The rule: *what is being said must be what the viewer is seeing at that moment. A correct visual five seconds late is still wrong.*
3. **Images.** One prompt per scene. Follow `references/higgsfield-prompting.md` exactly — the rules there were learned by getting them wrong.
4. **Animate.** Image to video, 5 seconds, no generated audio, slow and calm camera movement.
5. **Voice** if narrated. One generation per clause, never one for the whole script. Per-clause means the timing is exact by construction instead of measured afterwards.
6. **Check before you assemble.** See the quality gate below.
7. **Assemble**, then write the caption, the hashtags and the hook text for each platform.

Submit generations in batches and expect rate limits. Submit eight to twelve, keep what succeeds, resubmit the failures with the next batch.

## The quality gate

Never hand over a video without these four checks. Each one caught a real defect that would otherwise have shipped.

**Does the voice say the words?** If text-to-speech is involved, listen to or transcribe every clause and compare it to the script. Generated voice drops words, swallows the first consonant of short words, adds junk before a line, and occasionally returns something else entirely. A duration check does not catch this — a swallowed word makes a take *shorter*, which makes it score *better*. Compare words, not length.

**Is any shot stretched?** If a five-second clip has to cover eight seconds, it freezes. Check every beat against the real length of its clip before assembling, not after.

**Watch it muted.** Does the visual story still read as problem, development, resolution? If it only works with sound, it will not work on a muted autoplay feed, which is most of them.

**Watch it with your eyes closed.** Does it teach or deliver one thing without the pictures? If not, the writing is doing nothing and the video is decoration.

## Phase 4 — The rhythm

**Scheduling.** With Blotato: `blotato_list_accounts`, confirm the target account with the user out loud, then schedule. Publishing reaches real audiences, so confirm before every scheduled batch, every time.

**The Monday brief.** Set up a weekly scheduled task that reads the `studio/` docs and last week's numbers, then sends one message: what shipped, what it did, what is proposed this week as numbered items, and what needs a decision. The user replies with numbers. This is the whole approval mechanism and it should stay this simple.

**The autonomy ladder.** Do not start on autopilot. Earn it:

- *Now* — drafts, research, internal documents, private uploads.
- *After four clean weeks* — captions and metadata edits, reposting an approved video to a second platform.
- *After eight clean weeks* — publishing short videos on schedule without a per-item approval.
- *Never automatic* — anything in the user's own voice or face, anything making a factual claim, any spend.

A clean week means nothing was published that the user would have changed. Reset the counter when that is not true.

## How to behave while running this

Keep the user in the loop at every phase, briefly. They are watching a system get built and they should recognise it as theirs.

Tell the truth about costs. Generation costs real money. Say roughly what a batch will cost before running it, and stop if the balance is low.

When the user wants to skip the documents and go straight to videos, push back once. The documents are what make video fifty as good as video three.

When a generated image or clip is wrong, say so and regenerate. Do not pass bad assets along with a caveat.
