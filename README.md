# just-tell-me

**Cut the fluff. Get the thing.**

A skill definition that trains LLM agents to kill preamble, bury tangents, and serve every answer as a numbered action plan. No "Great question!", no "Hope this helps!", no detours.

## What changes

| Before | After |
|---|---|
| "Great question! Let me investigate. It looks like the build is failing because of a missing flag in the ci configuration file. You might want to check line 24..." | Line 24 of `ci.yml` is missing `--prod`. Fix: `npm ci` → `npm ci --prod`. |
| "There are a few things to consider here. Your pipeline has multiple stages and we'll need to think about..." | Update `config/pipeline.yml` line 34, then re-run the job. |
| "Fixed. Also, your API version is deprecated and that config key is invalid and there are three unused imports..." | Fixed. Separately: the API version is deprecated. Want me to handle that next? |
| "Oh no, it looks like something went wrong with the build..." | Build fails at `deploy.sh:19`: missing `NODE_ENV`. Add it to `.env.local` and retry. |
| "Done! On to the next part?" | Step 2 of 4 done: environment variables set. Next: seed the database. Run the script? |

First line = the thing you do. Last line = what you do next. Everything in between = numbered steps.

## Install

Copy `skills/just-tell-me/SKILL.md` to your agent's skill directory, or reference it in your system prompt / project config.

```bash
curl -O https://raw.githubusercontent.com/yuckier/just-tell-me/main/skills/just-tell-me/SKILL.md
```

Then invoke it with:

```
/just-tell-me
```

## The 10 rules

The full text lives in [`skills/just-tell-me/SKILL.md`](skills/just-tell-me/SKILL.md). The short version:

1. Lead with the next action
2. Number multi-step tasks
3. Close with one concrete next action
4. Suppress tangents
5. Restate state every turn
6. Give specific time estimates
7. Make completed work visible
8. State errors without drama
9. Cap lists at 5 items
10. No preamble, no recap, no sign-off

## Tweak it

Edit `skills/just-tell-me/SKILL.md` and re-invoke `/just-tell-me`. Your rules, your tone.

## Credits

Inspired by the [`i-have-adhd`](https://github.com/ayghri/i-have-adhd) project. Adapted for anyone who wants answers, not essays.

## License

MIT © [yuckier](https://github.com/yuckier)
