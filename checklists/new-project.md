# New-project checklist

A quick pass when starting or onboarding a client site. Each item links to its topic.

- [ ] Latest supported Next/React majors and a host-supported Node version. → [stack.md](../building/stack.md)
- [ ] Repo: squash-merge only, no AI co-author lines, AGENTS.md that links to the framework ([template](../templates/repo-AGENTS.md)), saved cloud-agent environment, CI, Dependabot (weekly Monday, minor+patch grouped, majors separate, never daily). → [git.md](../working/git.md)
- [ ] Hosting in the right account (client's own), commercial-use plan for paid work, pages pre-rendered where possible. → [vercel.md](../hosting/vercel.md), [cloudflare.md](../hosting/cloudflare.md)
- [ ] CMS only if non-developers edit content; one embedded Studio, server-side fetching, no hardcoded fallbacks. → [sanity.md](../building/sanity.md)
- [ ] CMS images through the CMS CDN loader with `sizes` set; user uploads resized in the browser. → [images.md](../building/images.md), [user-uploads.md](../building/user-uploads.md)
- [ ] Server-action redirects land on the final page. → [server-action-redirects.md](../building/server-action-redirects.md)
- [ ] Database: preview branch, re-runnable migrations, RLS if multi-tenant. → [neon.md](../building/neon.md)
- [ ] Sign-in (if any): generic errors, cooldown lockout, failed-login logging. → [auth.md](../building/auth.md)
- [ ] No tokens in browser env vars; keys only in the host's secret store. → [security.md](../building/security.md)
- [ ] Leads reach the client from their own domain; form mail to jake@dcldev.com until launch; spam protection on. → [email.md](../building/email.md), [forms.md](../building/forms.md)
- [ ] Licensed fonts with a self-hosted fallback. → [fonts.md](../building/fonts.md)
- [ ] Real copy only; existing brand and logo kept. → [design.md](../building/design.md)
- [ ] Empty, loading and error states; tappable contact details. → [ux.md](../building/ux.md)
- [ ] Before go-live, run the [launch-checklist.md](launch.md).
