# Working with AI agents

Rules for any AI tool or assistant working on Jake's projects.

## Before starting
- **Read the repo's AGENTS.md and match existing patterns.** Why: subtle systems break when an agent "simplifies" them. (drewdella, metrotapes)
- **Confirm the real repo and dataset, and pull the latest main.** Why: agents have built on stale main and on the wrong dataset. (logiparty, compactpickup)
- **Restate multi-part or vague asks before building.** Why: motion and layout requests were misread repeatedly. (drewdella, favoritesonnyc)
- **Plan first on multi-part work, then build.** Why: cheap models get it right when there's a plan. (headsuptrucker)
- **Find assets and facts yourself from real sources before asking Jake.** Why: "u cant find the links online urself?" (Abis)

## While working
- **Find the root cause before patching.** Why: workarounds hide the real problem. (drewdella)
- **Make small, reviewable changes.** Never do overnight multi-phase revamps. Why: three stacked phases "broke too much." (metrotapes)
- **Keep scope tight on the cheap default model.** Don't rescan the repo or take screenshots unless asked, and give exact text when it's already decided. Why: usage limits are low, and tokens go on testing, not chat. (cursor helper, jasiahpowers)
- **When you send feedback to a running agent, confirm it landed.** Why: one round ran an hour without the change. (metrotapes)
- **Keep a running list of asks.** When context fills up, hand off to a fresh agent with that list. Why: nothing gets dropped. (bannquet)
- **Update brief and research files when facts change.** Why: other agents read them. (favoritesonnyc)
- **Never put secrets in prompts.** → [security.md](../building/security.md)

## Launching cloud agents
- **Launch inside the repo's saved cloud-agent environment when one exists, never a plain VM.** Nearly every jakedcl repo has one. How to do it per tool: [tools/cursor.md](../tools/cursor.md). Why: the environment already has the setup, so the agent doesn't spend usage rebuilding it. (dependabot, Jake)
- **Every cloud agent starts from the repo's AGENTS.md and the framework rules it links to, not a repo rescan.** Why: so agents don't rediscover the same things every time. (dependabot, Jake)
- **Keep briefs tight:** the default model, no screenshots unless the work is visual, no full-repo rescans, no Co-authored-by lines, and never merge unless Jake said to. Why: usage is limited, and merging is Jake's call. (cursor helper, dependabot)

## Reporting and permission
- **Talk in plain words:** what changed, what's broken, what Jake needs to do. (logiparty)
- **Send the preview link the moment it's ready, and say "done" only after seeing it live.** (favoritesonnyc, bannquet)
- **Confirm a problem before you report it as an outage.** Check a private window and the logs first. (Abis)
- **When Jake has to choose, give the options and context.** (Abis)
- **"Push everything" never includes items Jake held back.** (bannquet)
- **Ask before deleting anything.** Name exactly what goes, and check that nothing else depends on it. Why: a careless delete could have taken real projects with it. (drewdella, bannquet)
- **Don't change connectors or account settings without a go-ahead.** (cursor helper)

## How to decide
- **Model:** use the cheap default. Switch to a stronger one when Jake says quality matters or the cheap one has failed twice. If the cloud agent can't run it, tell Jake.
- **Same agent or a new one:** the same agent continues the same PR or thread. Use a fresh agent only for unrelated work, and cancel duplicates.
