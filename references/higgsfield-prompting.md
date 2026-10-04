# Higgsfield prompting — the rules that were learned the hard way

Each rule here replaced something that failed in production. Follow them literally.

## Keeping the look consistent across hundreds of clips

Consistency comes from **reference images**, not from describing the style in words. Words drift; references do not.

Generate two or three anchor images first and approve them before anything else. Then pass them as `image_references` on every subsequent image. Typical set:

- a **warm** anchor (the resolution register)
- a **cold** anchor (the problem register)
- a **macro** anchor (close detail: hands, objects, texture)

If there is a recurring character, generate one master portrait, approve it, and pass it as a reference on every shot that character appears in. Without it the face changes between clips and the channel looks like several channels.

## Text inside the frame

**Never let the model write words.** It produces letter-shaped nonsense that viewers notice immediately.

Saying "no text" or "no legible words" is not enough. Use:

> abstract ink strokes with no letterforms, nothing a viewer could read

If a shot genuinely needs words on screen (a note, a label, a sign), generate it blank and composite real text over it afterwards. Always.

## Vertical images

Models trained mostly on landscape will leave an empty band where they think a caption goes. Every vertical prompt needs:

> full-bleed, fills the entire frame edge to edge with no blank areas

Check the first batch for cream or grey bands at the top or bottom. If they appear, the phrase is missing.

## Prompt shape that works

```
Vertical full-bleed painterly illustration, [lighting], [palette].
[Subject doing one specific thing], [framing].
Painted illustration, soft brushwork, no text, no letterforms,
fills the entire frame edge to edge with no blank areas.
```

One subject, one action, one light source. Compound scenes come back muddled. If a beat needs two things, it needs two shots.

## Animation

Image to video. Five seconds. Audio off — the generated audio is unusable and you are laying your own anyway.

Camera movement is slow or still. Every prompt ends with:

> Calm, cinematic, no cuts, no text, no camera shake.

Ask for one gentle move: a slow push-in, a slow pull-back, a slow drift. "Dynamic" and "dramatic" produce warping faces and melting hands.

## Rate limits

Expect constant 429s. The pattern that works: submit eight to twelve, keep the ones that succeed, resubmit the failures with the next batch. Do not retry a single failure in a tight loop.

Poll in groups of twelve. Collect results as they finish rather than waiting for a whole batch.

## Voice

Generate **one clip per clause**, never one for the whole script, and generate **two takes of each**. Per-clause generation makes the timing exact by construction, and the second take is what saves you when the first is defective — which happens more than you would expect.

Known failure modes, all observed:

- Junk spoken before the line.
- A word swallowed before a colon at the end of a clause. Send that clause as its own sentence with a full stop instead. Colons *inside* a sentence are fine.
- The first consonant of a short isolated word dropped, so "Sitting?" becomes "heating".
- A take that is the right length but near-silent.
- Rarely, a line the model simply will not say, returning the same unrelated recording every time. The fix is to generate it as the *second* sentence of a longer prompt and cut the audio at the pause.

This is why the quality gate compares words and not durations.

## Budget

Images are cheap. Video clips are not, and they dominate the cost of a video. Before a batch, count the clips, multiply, and tell the user the number. Keep a reserve: running out mid-way through a video is worse than producing one fewer.
