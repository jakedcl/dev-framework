# Domains and DNS

- **On an inherited site, find out first who owns the domain, hosting, email and renewal notices.** Why: an old owner or an old email address is the biggest risk. (our island realestate)
- **Never touch email (MX) records when moving hosting.** Why: the client's email keeps working. (our island realestate)
- **Copy an old site's files for reference outside the repo, and skip the mail folder.** Why: old sites can hold sensitive data. (our island realestate)
- **Share real domains, never `.vercel.app` links.** Why: "i hate giving people a .vercel.app." (jakedcl.com)
- **`www` and `http` both land on the apex with one 301 that keeps the path.** On Cloudflare: a proxied `AAAA` `www` record to `100::`, one redirect rule, Always Use HTTPS and HSTS on. Why: Abis's zone had apex records only, so `www` didn't resolve. (Abis)
