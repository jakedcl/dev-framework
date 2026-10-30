# SEO and link previews

- **Every site ships Open Graph and Twitter tags, an OG image that loads, and the site name in every title.** Why: link previews in texts and Slack. (logiparty)
- **Keep `robots.txt` and `sitemap.xml` outside any login redirect.** (logiparty)
- **Unknown URLs get a real 404, not a login screen.** (logiparty)
- **Cache the marketing homepage on the CDN.** Don't serve it `no-store`. (logiparty)
- **Structured data matches the site.** Why: Abis's schema said it took reservations, but the site said to call. (Abis)
- **After launch, sweep every listing and old domain that points at the business** (Yelp, Instagram, Facebook, TripAdvisor, OpenTable, Apple Maps, Bing, directories) and give the client one fix list. Cancel or redirect the old site. Why: Abis's listings pointed at an unregistered domain, a domain someone else owns, and the old builder site. (Abis)

## Search Console (business sites)
- **At launch, every business site gets a Search Console Domain property, verified with a DNS TXT record** in the site's DNS (usually Cloudflare). Then submit `/sitemap.xml` and check with URL Inspection that the homepage is indexed. Why: a Domain property covers `www`, `http` and every subdomain, and it's the only place that shows what people search to find the site. (Abis)
- **Jake sets it up under jake@dcldev.com,** not his personal Gmail and not the client's account. Why: busy clients don't have to sign up or verify anything. (Jake, Oct 30, 2026)
- **At handoff, add the client as an Owner** in Settings > Users and permissions, using their Google account email. Why: they get full control without touching DNS. (Jake, Oct 30, 2026)
- **Never delete Jake's `google-site-verification` TXT record, and say so in the handoff doc.** Why: a client added that way is a delegated owner, and their access depends on a verified owner. If the record goes, Jake loses verification and, after a grace period, so does everyone else. (Search Console Help)
- **If Jake steps away, the client verifies with their own TXT record first, then Jake removes himself and his record.** Why: removing Jake first locks the client out. (Search Console Help)
- **Local businesses: the client owns the Google Business Profile, Jake is a Manager, and the profile links the website.** It's separate from Search Console and matters more for places like restaurants. Why: most local customers find them on Maps. (Abis)
- **Sites already live can be added anytime.** Why: data only starts when the property is added, with nothing from before, so launch day is best. (Search Console Help)
