# Cloudflare (Workers + OpenNext)

- **Deploy to the client's own Cloudflare account, with keys in Worker secrets.** Why: the client owns the site. (Abis)
- **Set Worker secrets by hand** (dashboard or `wrangler secret put`), never through the Cloudflare API connector. Why: the connector masks secret values to a 10-character placeholder, so the Worker got the placeholder and the live form returned 503. (Abis #50)
- **`workers_dev: false` in `wrangler.jsonc`** once the real domain is live. Why: the `*.workers.dev` copy is a second public site that skips the domain's rules. (Abis #48)
- **Pre-render every page you can.** Why: per-request rendering hit "exceeded resources" on the free plan. (Abis)
- **No runtime image resizing on the free plan.** Use `images.unoptimized` and make image sizes at build time. Why: resizing costs money and CPU. (Abis)
- **With the OpenNext static cache, the build command ends in `populateCache local`.** Why: without it, pre-built pages are never used. (Abis)
- **Stay on a supported Next major.** Never use `--dangerouslyUseUnsupportedNextVersion`. Why: Abis's builds broke when Next 15 support ended. (Abis)
- **The Worker name must match the Cloudflare project name, and the gzipped bundle stays under 3 MiB.** (Abis)
- **Builds run one at a time, so cancel superseded builds.** (Abis)
- **Non-production branch builds use the OpenNext commands too, or stay off.** Build command `npx opennextjs-cloudflare build`, non-production deploy command `npx opennextjs-cloudflare upload`. Why: with `npm run build` and the default Wrangler deploy, branch builds failed with "The entry-point file at .open-next/worker.js was not found," because only the OpenNext build makes that file. Abis turned branch builds off on Oct 26 instead. ([OpenNext](https://opennext.js.org/cloudflare/howtos/dev-deploy), [Workers Builds](https://developers.cloudflare.com/workers/ci-cd/builds/configuration/)) (Abis)
- **Failed builds alert Jake, never the client.** On Workers Builds, a small workflow on the build's GitHub check run opens an issue assigned to @jakedcl. No scheduled uptime workflows; uptime is covered in [monitoring.md](monitoring.md). (Abis c8ff8e1)
- **The agent adds DNS records itself through the API connector, with the smallest scopes.** Ask before widening access. (jasiahpowers)
- **Email sending costs:** see [email.md](../building/email.md).

## Troubleshooting
- **Error `10013` on `assets-upload-session` during deploy:** a Cloudflare-side API error ("An unknown error has occurred"), not your code. Retry the build once before debugging. Seen once on Abis (Oct 28, 2026): the next build, under a minute later, passed with no change. Treat a repeat as real.
