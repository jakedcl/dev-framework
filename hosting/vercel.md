# Vercel

- **Hobby is non-commercial.** Paid client sites need Pro (about $20/mo) or another host, like [Cloudflare](cloudflare.md). (Abis)
- **Hobby quotas are team-wide:** 5,000 image transformations a month, 100 deploys a day and one build at a time across all projects. Keep previews light. Why: one photo-heavy site used 75% of the image quota. (jasiahpowers, bannquet)
- **Keep on-demand overage at or near $0.** Stay in included usage, set a spend limit and usage alerts, and check Usage when anything spikes. Why: [free or cheap by default](../principles.md). (Jake, Oct 27, 2026)
- **Domain-locked browser keys fail on previews.** That's expected, so test those features on production. (drewdella)
- **Previews sit behind Vercel login,** so test them in a signed-in browser. (bannquet)
- **After saving a secret, verify it, then redeploy.** Why: a key was saved cut off, and env vars don't reach existing deploys. (bannquet)
- **Confirm the merge actually deployed.** If Vercel missed the push, push an empty commit or trigger a production deploy. (jakedcl.com, jasiahpowers)
- **Take preview URLs from the deployment, never a guessed pattern.** (compactpickup)
- **Hobby keeps about an hour of logs,** so log important events (like failed sign-ins) to the app's own database. (bannquet)
- **No WebSockets on Vercel functions.** Simple realtime polls instead. (bannquet)
- **When clearing deployments, keep live production, the newest deploy on each unmerged branch, and anything under 24 hours old.** (cleanup vercel)
