# faceless-studio

A Claude skill that builds you a faceless short-form video studio.

You install one file into Claude, answer about ten minutes of questions about
what you make and who you make it for, and come out with your brand documents,
your first three videos, and a weekly rhythm that keeps producing them.

No code. No terminal. You do not need this repository to use the skill — it is
here so you can read exactly what you are installing before you install it.

**[Download the skill](https://malikasani.com/faceless-studio.zip)** ·
[Read the walkthrough](https://malikasani.com)

## Install

Requires a Claude Pro, Max, Team or Enterprise plan. Custom skills cannot be
installed on the free plan.

1. Download `faceless-studio.zip` (from the link above, or from this repo). Do
   not unzip it.
2. In Claude: **Settings → Capabilities → Skills → Upload skill**, and pick the
   zip.
3. New conversation: `Set up my faceless video studio`

Full instructions, including what to do if your browser unzips it
automatically, are in [INSTALL.md](INSTALL.md).

## What is in here

| File | What it is |
| --- | --- |
| [`SKILL.md`](SKILL.md) | The skill itself. The interview, the four phases, the quality gate, the autonomy ladder. This is the whole brain. |
| [`INSTALL.md`](INSTALL.md) | Step by step install, the questions you will be asked, and the four things that commonly go wrong. |
| [`references/higgsfield-prompting.md`](references/higgsfield-prompting.md) | How to get consistent images, animation and voice out of Higgsfield. Reference images over adjectives, the phrasings that survive, and every voice generation failure mode I have hit. |
| [`references/formats-library.md`](references/formats-library.md) | Five repeatable short-form formats with their beat structures. |
| [`references/operating-system-template.md`](references/operating-system-template.md) | The weekly rhythm: Monday brief, the six roles, and the autonomy ladder. |
| `faceless-studio.zip` | The installable package. Same files, zipped for upload. |

## Tooling

The skill is written against **Higgsfield** for generation (images, animation,
voice) and **Blotato** for scheduling. If you do not have those connected it
still writes every script, image prompt and publishing calendar into files you
can use by hand, and it tells you which steps are manual rather than pretending
otherwise.

## Two things it will refuse to do

**It will not put you on autopilot on day one.** It gives you a ladder instead:
drafts and private uploads now, small things after four clean weeks, scheduled
publishing after eight. Anything in your voice, anything asserting a fact, and
anything spending money stays yours permanently.

**It will refuse to make new videos while you have finished ones you have not
published.** This is the most useful thing in it. I built my production before
my distribution and ended up with nine finished videos and forty-four views
across three channels. A factory with no road out of it. The refusal exists so
that does not happen to you.

## Changing it

It is a markdown file. Open `SKILL.md`, edit it, rezip the `faceless-studio`
folder, upload it again. Changing the interview questions, swapping Higgsfield
for another generator, adding your own formats to the library — all of that is
editing prose, not code.

## Licence

MIT. Use it, change it, ship it, sell what you make with it. No attribution
required, though I like hearing about it.

Built by [Malika Sani](https://malikasani.com).
