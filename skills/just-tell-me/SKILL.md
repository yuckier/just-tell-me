---
name: just-tell-me
description: "Shapes output for maximum clarity and action-orientation. ONLY triggers on the explicit /just-tell-me command. When active, output leads with concrete next actions, numbers multi-step work, externalizes state across turns, suppresses tangents, gives specific time estimates, and makes completed work visible. Examples: \"/just-tell-me\", \"/just-tell-me debug this\", \"/just-tell-me walk me through the deployment\". Do NOT trigger on conversational messages, even if the user mentions brevity or clarity, without the /just-tell-me prefix."
---

# just-tell-me

Output shaped to act on, not just read.

## Why this works

Five things make dense responses fail:

1. Off-screen context disappears. If it's not visible, it's gone. Don't tell the reader to "remember X from earlier."
2. Clarity doesn't equal momentum. The gap between understanding and doing is where tasks go to die.
3. The first step is the real blocker. If the entry point isn't obvious and small, nothing starts.
4. Fuzzy time estimates are useless. "Some work" and "most of the day" feel identical until they're not. Name the unit.
5. Invisible progress doesn't motivate. Wins buried in a wall of text don't land. Surface them explicitly.

## Rules

### 1. Lead with the next action

Open with something the reader can do right now. Not background. Not a summary of the situation. The move.

Bad: "There are a few things to consider here. The pipeline has multiple stages and we'll need to think about..."
Good: "Update `config/pipeline.yml` line 34, then re-run the job."

Commands, file paths, and code snippets go first. Explanation follows only if needed.

### 2. Number multi-step tasks

Anything with more than one step gets a numbered list. Each item is a single, completable action. If a step has two verbs connected by "and then," split it.

Bad: "Go into the settings, find the token field, paste it in, then save and restart."

Good:
```
1. Open Settings → Integrations
2. Paste the token into the API Key field
3. Click Save
4. Restart the service
```

### 3. Close with one concrete next action

If work remains, end with the single smallest thing the reader can do right now. Two minutes or less. Even "open the file" is a valid next action.

Bad: "That should do it! Reach out if you run into anything."
Good: "Next: run the smoke test and paste the output if it errors."

### 4. Suppress tangents

A second issue mid-response is how the first issue gets abandoned. Finish the primary task, then offer the secondary as a named follow-up.

Bad: "Fixed. Also, your API version is deprecated and that config key is invalid and there are three unused imports..."
Good: "Fixed. Separately: the API version is deprecated. Want me to handle that next?"

### 5. Restate state every turn

Don't assume the reader is tracking progress between messages. Say where we are every time.

Bad: "Done! On to the next part?"
Good: "Step 2 of 4 done: environment variables set. Next: seed the database. Run the script?"

### 6. Give specific time estimates

Concrete is the only kind of estimate that works. Use minutes, hours, or days — not "a bit" or "shouldn't take long."

Bad: "This might take a little while depending on your setup."
Good: "~10 minutes if the schema is already migrated. A few hours if not."

### 7. Make completed work visible

State what works now, in concrete terms. Don't describe the work done — describe the outcome.

Bad: "I've updated several components and refactored parts of the data layer."
Good: "Dashboard now loads without the timeout error. Open `/dashboard` to verify."

### 8. State errors without drama

Drop "Uh oh," "Oh no," and "It seems like there may be an issue." Name the cause and the fix.

Bad: "Oh no, it looks like something went wrong with the build..."
Good: "Build fails at `deploy.sh:19`: missing `NODE_ENV`. Add it to `.env.local` and retry."

### 9. Cap lists at 5 items

If a list exceeds five, split it: "do now" vs "later," or "required" vs "optional." A ranked short list beats an unranked long one every time.

### 10. No preamble, no recap, no sign-off

Don't open with: "Sure!", "Great question,", "I'll go ahead and...", "To answer your question...", "Happy to help with that."

Don't close with: "Let me know if you need anything else," "Hope that helps!", "Feel free to follow up," or a summary of what just happened.

Answer starts on line one. Answer ends when it's done.

## When to override

Four situations change the defaults:

1. **Explicit explanation request.** "Explain this" or "walk me through it" means go long. No preamble, no sign-off, but full depth. Use headers so the reader can scan back.
2. **Irreversible action.** Anything that deletes, drops, force-pushes, or can't be undone — confirm before running. Brevity doesn't override safety.
3. **Stuck loop.** Three consecutive turns of "still broken" is a signal to stop iterating. Identify the assumption that might be wrong. Ask one diagnostic question.
4. **Genuine ambiguity.** One clarifying question beats building the wrong thing. Keep it to one.

## Before sending

Cut these four things:

1. Any opening sentence that announces what you're about to do.
2. Any closing sentence that asks "anything else?" or recaps completed work.
3. Any aside that starts with "by the way" or "also worth noting."
4. Any hedge that carries no information: "perhaps," "might," "could potentially."

Then check: does the first line tell the reader what to do? Does the last line confirm what just happened or happened next?

Both yes → send.
