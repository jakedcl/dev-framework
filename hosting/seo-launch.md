# SEO and link previews

- **Every site ships Open Graph and Twitter tags, an OG image that loads, and the site name in every title.** Why: link previews in texts and Slack. (logiparty)
- **Keep `robots.txt` and `sitemap.xml` outside any login redirect.** (logiparty)
- **Unknown URLs get a real 404, not a login screen.** (logiparty)
- **Cache the marketing homepage on the CDN.** Don't serve it `no-store`. (logiparty)
- **Structured data matches the site.** Why: Abis's schema said it took reservations, but the site said to call. (Abis)
- **At launch, local businesses link the Google Business Profile.** The client owns it and Jake is a Manager. (Abis)
- **After launch, sweep every listing and old domain that points at the business** (Yelp, Instagram, Facebook, TripAdvisor, OpenTable, Apple Maps, Bing, directories) and give the client one fix list. Cancel or redirect the old site. Why: Abis's listings pointed at an unregistered domain, a domain someone else owns, and the old builder site. (Abis)

## Search Console (business sites)
- **Search Console is a handoff item, not a launch or merge blocker.** Why: the site works without it, and it can be added anytime.
- **The client is the verified owner, with their own TXT record.** They add a Domain property in their own Google account and send Jake the `google-site-verification` TXT value. Jake adds it at your DNS provider, then the client clicks Verify. Why: their access never depends on Jake's account or record.
- **The client then adds jake@dcldev.com as a Full user** in Settings > Users and permissions. Jake submits `/sitemap.xml` and checks the homepage with URL Inspection. Why: Jake can help without owning it.
- **Leave the TXT record in DNS for good.** Why: Google rechecks it, and removing it drops the owner's verification.
- **Only if the client can't do it, Jake verifies under jake@dcldev.com and adds the client as an Owner.** The handoff doc then says not to delete Jake's TXT record, and the client switches to their own record when they can. Why: an Owner added this way loses access if Jake's record goes.
