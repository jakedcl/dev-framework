# Git and GitHub

- **Squash-merge only, on every repo.** Why: one clean commit per change. (cursor helper)
- **No AI co-author lines.** Pass an explicit squash message so GitHub doesn't add one. Why: Jake doesn't want agent attribution in his history. (cursor helper)
- **Every repo has an AGENTS.md and CI (lint, typecheck, tests, build).** Why: agents start without rescanning, and breakage gets caught early. (cursor helper, dev helper)
- **Every repo's AGENTS.md links to this framework and copies in the few rules agents need for that repo.** Why: the framework lives in a private repo some agents can't open, so the essentials have to be in the repo itself. (dependabot, Jake)
- **Every project gets GitHub Dependabot (`.github/dependabot.yml`) set to weekly on Monday, never daily, with minor and patch updates grouped into one PR and majors as separate PRs.** Why: dependencies stay current without a daily flood of PRs, and majors get reviewed on their own because they can break things. (dev helper, Jake)
- **No Dependabot on the ranger repo.** (Jake, Oct 27, 2026)
- **Unrelated changes branch off main.** Why: parked work stays parked. (favoritesonnyc)
- **Group related fixes into one push with a commit per feature.** Why: it saves preview builds on the shared queue. (bannquet)
- **Restore old versions from git history, not from memory.** Why: "go find it dont just make it from memory." (compactpickup)
- **Before deleting code you moved, confirm every file arrived.** Why: six files went missing in one move. (jakedcl.com)
- **Delete one-off scripts after they run.** Git keeps them. (bannquet)
- **Public repos keep internal docs in `docs/internal/` and have a LICENSE, or they're private.** Why: clients and interviewers read them. (logiparty)

## How to decide: PR or straight to main
- **Decide by risk, not size.** Low-risk copy or style tweaks can go straight to main, and Jake checks them live. Anything touching data, auth, forms, payments, routing or a client-visible redesign gets a preview PR and a real check before merge. Never merge with conflicts or failing checks.
