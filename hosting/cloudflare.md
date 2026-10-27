# Cloudflare (Workers + OpenNext)

- **Deploy to the client's own Cloudflare account, with keys in Worker secrets.** Why: the client owns the site. (Abis)
- **Pre-render every page you can.** Why: per-request rendering hit "exceeded resources" on the free plan. (Abis)
- **No runtime image resizing on the free plan.** Use `images.unoptimized` and make image sizes at build time. Why: resizing costs money and CPU. (Abis)
- **With the OpenNext static cache, the build command ends in `populateCache local`.** Why: without it, pre-built pages are never used. (Abis)
- **Stay on a supported Next major.** Never use `--dangerouslyUseUnsupportedNextVersion`. Why: Abis's builds broke when Next 15 support ended. (Abis)
- **The Worker name must match the Cloudflare project name, and the gzipped bundle stays under 3 MiB.** (Abis)
- **Builds run one at a time, so cancel superseded builds.** (Abis)
- **The agent adds DNS records itself through the API connector, with the smallest scopes.** Ask before widening access. (jasiahpowers)
- **Email sending costs:** see [email.md](../building/email.md).
