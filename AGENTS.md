# dcldev dev framework

Jake's rules for building and running client sites as dcldev. Only rules that hold on every project are here, each one line with a short why. Anything situational is a short "How to decide" note. It's plain markdown so any AI tool or person can follow it, and the whole thing reads in about 15 minutes.

## Read order
1. [principles.md](principles.md)
2. [working/agents.md](working/agents.md) and [working/git.md](working/git.md)
3. The topic file for whatever you're touching (index below).

## Hard rules (every repo, every tool)
- Squash-merge only. No Co-authored-by or other AI attribution lines. → [working/git.md](working/git.md)
- Never merge unless Jake said to. Ask before deleting anything. → [working/agents.md](working/agents.md)
- PRs go to QA only when Jake asks for it. Otherwise Jake reviews and merges without a QA pass. → [working/git.md](working/git.md)
- Cloud agents launch in the repo's saved environment and start from its AGENTS.md. → [working/agents.md](working/agents.md)
- "Fixed" only after seeing it live. → [working/testing.md](working/testing.md)
- No secrets in prompts, notes, docs or browser env vars. → [building/security.md](building/security.md)
- Free or cheap by default: Vercel overage at or near $0. → [hosting/vercel.md](hosting/vercel.md)

## How we work
- **Principles**: free or cheap by default, grow the agency, only always-true rules. → [principles.md](principles.md)
- **AI agents**: confirm the repo and main first, root cause before patching, small changes, plain-word updates, ask before deleting. Cloud agents launch in the repo's saved environment, start from AGENTS.md, and get tight briefs. Plus how to pick a model and when to start a new agent. → [working/agents.md](working/agents.md)
- **Git**: squash-merge, no AI co-authors, QA only when Jake asks, AGENTS.md that links here, CI, Dependabot (weekly Monday, minor+patch grouped, majors separate, never daily, none on ranger). PR vs straight to main is decided by risk. → [working/git.md](working/git.md)
- **Testing**: "fixed" only after seeing it live, phone widths, real devices for 3D and fonts, test by risk. → [working/testing.md](working/testing.md)
- **Clients**: nothing goes out without Jake, placeholders in his voice, client owns accounts, handoffs. → [working/clients.md](working/clients.md)
- **Anti-patterns**: the quick list of things Jake has called out. → [working/anti-patterns.md](working/anti-patterns.md)

## Building
- **Stack**: latest supported majors (Next 16+, check the support timeline), supported Node, free data sources, no porting without a reason. → [building/stack.md](building/stack.md)
- **Sanity**: one embedded Studio at `/admin`, server-side fetching, all visible and SEO content in Studio with no hidden fallbacks, back up before bulk edits, client-proof before handoff. → [building/sanity.md](building/sanity.md)
- **Images**: CMS photos through the CMS CDN, never Vercel's optimizer. → [building/images.md](building/images.md)
- **User uploads**: resize in the browser (full plus thumbnail), render `unoptimized`. → [building/user-uploads.md](building/user-uploads.md)
- **Server-action redirects**: land on the final page, never a URL that redirects again. → [building/server-action-redirects.md](building/server-action-redirects.md)
- **Forms**: Sent only after a confirmed send, spam flagged never dropped, idempotent submits, unfinished forms say they aren't connected. → [building/forms.md](building/forms.md)
- **Email**: every lead reaches the client from their own domain; Cloudflare costs checked. → [building/email.md](building/email.md)
- **Legal**: privacy policy, accessibility statement and form consent on every new site; restaurant notices; cookie banner only with a tracker. → [building/legal.md](building/legal.md)
- **Sign-in**: generic errors, cooldown lockout, failed-login logging. → [building/auth.md](building/auth.md)
- **Security**: no browser tokens, no secrets in prompts or notes, no sensitive data. → [building/security.md](building/security.md)
- **Neon**: preview branches, re-runnable migrations applied by a person, RLS, dry-run scripts. → [building/neon.md](building/neon.md)
- **Fonts**: licenses, no OS-only fonts, confirm they load. → [building/fonts.md](building/fonts.md)
- **Design**: real copy, keep the existing look and logo, not vibecoded. → [building/design.md](building/design.md)
- **UX**: tappable contacts, predictable search, loading and empty states, light media. → [building/ux.md](building/ux.md)

## Hosting and launch
- **Vercel**: Hobby is non-commercial with team-wide quotas; overage at or near $0; verify secrets and deploys. → [hosting/vercel.md](hosting/vercel.md)
- **Cloudflare**: client's own account, secrets set by hand, pre-render, `populateCache`, supported Next, OpenNext commands on every build. → [hosting/cloudflare.md](hosting/cloudflare.md)
- **Domains**: audit ownership first, don't touch email records, no `.vercel.app` links. → [hosting/domains.md](hosting/domains.md)
- **Monitoring**: every live site on the one UptimeRobot account, alerts to jake@dcldev.com, failed builds alert Jake. → [hosting/monitoring.md](hosting/monitoring.md)
- **SEO**: OG tags, crawlable robots and sitemap, real 404, matching structured data, Search Console owned by the client at handoff. → [hosting/seo-launch.md](hosting/seo-launch.md)

## Checklists
- New project → [checklists/new-project.md](checklists/new-project.md)
- Launch → [checklists/launch.md](checklists/launch.md)
- Handoff → [checklists/handoff.md](checklists/handoff.md)
- QA review (checks, pass bar, severity) → [checklists/qa.md](checklists/qa.md)

## Templates
- New lesson → [templates/lesson.md](templates/lesson.md)
- Section every client repo's AGENTS.md copies → [templates/repo-AGENTS.md](templates/repo-AGENTS.md)

## Tool notes (optional, per tool)
- Cursor → [tools/cursor.md](tools/cursor.md)
- Grok Bot → [tools/grok-bot.md](tools/grok-bot.md)

## Changing the framework
Changes land as PRs that Jake approves (see [principles.md](principles.md)). New lessons use [templates/lesson.md](templates/lesson.md). Where each file came from: [SOURCES.md](SOURCES.md).
