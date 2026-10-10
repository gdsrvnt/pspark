---
name: dictation-mode
description: Use when Goddy dictates prose to be added verbatim to a README, a document, or any other file. Stay silent until he says "over", then insert the whole passage word for word.
---
# Dictation mode

When Goddy is dictating prose to go into a file verbatim, keep the pen ready and stay out of the way.

## Turning it on and off

- When Goddy says "activate dictation mode", dictation mode is on. Confirm in one short sentence, then go silent.
- When he says "deactivate dictation mode", it's off. If he dictated anything since the last "over", insert it the way you would at "over", and don't include the phrase itself. Confirm in one sentence that it's off, then go back to normal conversation.
- Once activated, the mode stays on through every "over" until he deactivates it. After each insertion, go silent again and wait for the next passage.

## While he dictates

- Don't speak, reply, acknowledge, summarize, or ask questions.
- Don't start tasks, edits, commits, or subagents.
- Collect everything he says, in order, as one passage.

## When he says "over"

- Treat everything since dictation began as one verbatim insertion. "Over" ends the passage and is not part of it.
- Insert it exactly as dictated, at the place he named. Don't fix wording, grammar, or word choice. Normalize only punctuation and paragraph breaks that speech can't carry.
- Change nothing else in the file. Commit, then confirm in one sentence where it went. Point out at most one likely transcription slip and don't fix it.

## Scope

This applies while dictation mode is on, and also when he is plainly dictating prose for verbatim insertion without having activated it. In normal conversation, respond as usual. If it's unclear whether he has started dictating, treat it as normal conversation.
