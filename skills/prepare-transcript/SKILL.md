---
name: prepare-transcript
description: Turn a meeting transcript from Zoom, Google Meet, Teams, Otter, Fireflies, Granola, a .vtt or .srt caption file, or a rough paste into the one-speaker-turn-per-line text that the FounderBrain analyse_transcript tool needs. Use before calling analyse_transcript whenever the text has timestamps, caption numbers, labels on their own lines, or speaker labels with digits.
---

# Prepare a transcript for FounderBrain

`analyse_transcript` finds speakers by lines shaped like `Label: what they said`. Anything else is ignored, so a transcript in another shape reads as having no speakers, or too few words.

## The target shape

```
Ana Ruiz: Thanks for making the time. We started the company after ...
Tom: What does retention look like after the first month?
Ana Ruiz: About sixty percent of teams are still active at day thirty ...
```

- One line per speaker turn. Join the lines of a turn that were split across captions.
- A label is a name in any alphabet (José, Yiğit, 李) or a generic label such as `Speaker 2`, up to four words, starting with a letter. A timestamp just before the label (`00:01:02 Ana:` or `[00:01] Ana:`) or just after it (`Ana (00:01):`) is fine.
- Keep the same label for the same person all the way through.

## Steps

1. Remove caption numbers, `WEBVTT` headers, cue timings such as `00:01:02.000 --> 00:01:05.000`, and timestamps that sit on their own line.
2. If the label sits on its own line above the words (Otter, Teams, some Zoom exports), put it at the start of the words that follow.
3. Keep generic labels such as `Speaker 1` as they are, and use the same label for the same person throughout.
4. Merge consecutive turns by the same speaker into one line.
5. Keep every spoken word exactly as it was. Do not correct grammar, remove filler, summarise, or translate. The analysis depends on how the person actually talked.
6. Leave out lines that are not speech, such as "[inaudible]" on its own, chat messages, or meeting notes. Summaries and action items from a notes tool are not part of the transcript.

## Before sending

- Check that the person the user wants analysed has at least 300 words. Fewer than that cannot be analysed.
- Check the whole text is under 15,000 words. If it is longer, ask the user which part of the meeting matters most and send that part.
- Tell the user in one sentence what you changed, for example "I removed the timestamps and joined the caption lines." Then call `analyse_transcript`.
