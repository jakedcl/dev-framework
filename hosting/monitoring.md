# Monitoring

Every live site is watched, so Jake hears about an outage before the client does.

## Rules
- **Every live site gets an uptime monitor at launch.** Use the one dcldev UptimeRobot account (free plan, signed up with jake@dcldev.com), with an HTTP monitor on the production domain. Why: one account covers 50 sites at no cost, and you learn about outages in minutes.
- **Alerts go to jake@dcldev.com only, never to the client.** Why: Jake decides what the client hears (see [clients.md](../working/clients.md)).
- **Don't build per-repo uptime checks on GitHub Actions cron.** Why: an hourly check uses about 730 of the org's 2,000 free Actions minutes a month per repo, and you only hear about an outage up to an hour late.
- **Failed production builds alert Jake too.** Use the host's own deploy-failure notifications (Vercel or Cloudflare Workers Builds). A small workflow that opens a GitHub issue assigned to @jakedcl is fine when the host has no notifications. Why: a failed build means published content isn't going live.
- **Remove the monitor when the site is shut down or handed off.** Why: dead monitors send false alarms.

## How to decide
- If the site has an important endpoint beyond the homepage (an order API, or a health route), add a second monitor or a keyword check for it.
