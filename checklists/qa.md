# QA checklist

What QA checks on a PR when Jake asks for a review, and the bar each check has to clear. QA runs it on the PR's preview, at every page the PR touches, and on the whole site before launch if Jake asks. Most rules live in their topic files; this file links them and sets the pass bar and severity.

## Severity
- **P0: blocks merge.** The site, a page or a lead is lost: down or error pages, a form that says Sent without sending, a leaked secret, production set to `noindex`, `www` that doesn't resolve.
- **P1: blocks merge.** Broken for real visitors or breaks a framework rule: broken links or images, sideways scroll, axe serious or critical, missing title or OG image, CMS images through `/_next/image`, placeholder copy live, an unexplained visual change.
- **P2: noted, fix soon.** Works but looks or performs worse than it should: slow mobile LCP, missing security headers, AI-sounding copy, stale years, structured data that doesn't match.
- **P3: noted, polish.** Small wins: oversized thumbnails, minor axe issues, cache headers.

A PR passes when its latest commit adds no P0 or P1. Issues already on main get logged and reported, but they don't block an unrelated PR. QA lists every P2 and P3 so the project bot can fix them in the same PR or log them. A bug that was fixed before and comes back is at least P1.

## Checks

### Links and images
- [ ] Every internal link and image returns 200 (a redirect is fine if it lands in one hop). Fail: P1.
- [ ] External links open the real page. Sites that block bots (DoorDash, Uber Eats, Instagram, Facebook) get opened by hand before they're called broken. Fail: P2.
- [ ] An unknown URL returns a real 404 page, not a 200 or a login screen. Fail: P1. → [seo-launch.md](../hosting/seo-launch.md)
- [ ] No `.vercel.app` links anywhere a visitor can see. Fail: P1. → [domains.md](../hosting/domains.md)

### Layout at 320, 375, 768 and 1280
- [ ] No sideways scroll: the page is exactly the viewport width at every width. Fail: P1. → [testing.md](../working/testing.md)
- [ ] Nothing overlaps or gets cut off: text over images, covered buttons, clipped words, a sticky header over a scroll target. Fail: P1. → [ux.md](../building/ux.md)
- [ ] Long CMS text wraps instead of widening the page (test with a 40-character word in a heading, a card and an hours label). Fail: P2. → [ux.md](../building/ux.md)
- [ ] The mobile menu sits above everything and works by tap. Fail: P1.

### Forms
- [ ] Every path through a stubbed-mailer harness: success, each spam check, Turnstile failure, expired form, paused inbox, mail error. "Sent" shows only when the server confirms a send. Any false Sent: P0. → [forms.md](../building/forms.md), [testing.md](../working/testing.md)
- [ ] Every failure shows a real error with another way to reach the client. Fail: P1.
- [ ] A double tap or a retry after a timeout sends one email. Fail: P1.
- [ ] Spam protection is on (honeypot, timing check, rate limit, Turnstile on Cloudflare), and heuristics flag rather than drop. Fail: P1.
- [ ] Inputs are labelled and at least 16px on phones, and Turnstile fits a 320px phone. Fail: P2 (unlabelled: P1).
- [ ] Before any real submission, check where it sends. Never submit a live client form. → [testing.md](../working/testing.md)

### Accessibility
- [ ] axe (WCAG 2.2 AA plus best practices) at a phone width and at 1280: no serious or critical issues. Fail: P1. Moderate and minor: P3.
- [ ] Keyboard: every control is reachable, focus is visible, there's a skip link, and the mobile menu keeps focus inside and returns it to the toggle on close. No visible focus at all: P1. Menu focus problems: P2.
- [ ] Content images have alt text that describes them, and decorative ones have `alt=""`. Missing: P1. Wrong: P2.
- [ ] Text contrast passes axe. Fail: P1.
- [ ] Anything that moves on its own has a pause control and respects reduced motion. Fail: P2. → [ux.md](../building/ux.md)

### Performance
- [ ] Lighthouse mobile on each changed page: performance 80 or more. Under 80: P2. Under 50: P1.
- [ ] LCP 2.5s or less on Lighthouse mobile. Over 2.5s: P3. Over 4s: P2.
- [ ] CLS 0.1 or less. Over 0.1: P2. Over 0.25: P1.
- [ ] INP 200ms or less in field data when it exists; otherwise total blocking time 200ms or less in the lab. TBT over 600ms: P2.
- [ ] CMS images load from the CMS CDN, with no `/_next/image` URLs for them, and `sizes` is set. Fail: P1. → [images.md](../building/images.md)
- [ ] The hero or banner image (the LCP element) is eager with `fetchpriority="high"`, and images below the fold are lazy. A lazy LCP image: P2.
- [ ] No autoplaying embeds, and thumbnails aren't full-size images. Fail: P3. → [ux.md](../building/ux.md)

### SEO and metadata
- [ ] Every page has a unique title with the site name and a meta description. Missing: P1. Duplicate: P2. → [seo-launch.md](../hosting/seo-launch.md)
- [ ] Open Graph and Twitter tags, and an OG image that loads. Fail: P1.
- [ ] A canonical on the real domain. Missing: P2. Points at a preview: P1.
- [ ] `robots.txt` and `sitemap.xml` load outside any login and list the real domain. Fail: P1. Production blocked from search (`noindex` or `Disallow: /`): P0.
- [ ] Structured data parses and matches the page (hours, address, reservations). Doesn't parse: P1. Doesn't match: P2.
- [ ] At launch (business sites): Search Console Domain property verified (a `google-site-verification` TXT record on the apex) and the sitemap submitted, and for local businesses the Business Profile links the site. Fail: P3. → [seo-launch.md](../hosting/seo-launch.md)

### Security basics (production and launch)
- [ ] `http` and `www` both 301 to the apex in one hop and keep the path. `www` doesn't resolve: P0. Other failures: P1. → [domains.md](../hosting/domains.md)
- [ ] HSTS is on. Fail: P1.
- [ ] `X-Content-Type-Options`, `Referrer-Policy`, `Permissions-Policy` and `X-Frame-Options` (or CSP `frame-ancestors`) are set, without breaking Studio, Maps or Turnstile. Fail: P2. No CSP: P3.
- [ ] No tokens or keys in the HTML, the JS bundle or `NEXT_PUBLIC_`/`VITE_` variables. Fail: P0. → [security.md](../building/security.md)
- [ ] The Studio route is kept out of search with an `X-Robots-Tag` header. Fail: P3.

### Content
- [ ] No placeholder or unconfirmed text live: lorem ipsum, TODO, `[TBD`, "coming soon", template text. Fail: P1. → [design.md](../building/design.md)
- [ ] No invented facts, and hours, prices and addresses match the CMS, the structured data and the client's listings. Invented or wrong: P1. Listings disagree: P2.
- [ ] Copy doesn't read like AI ("elevate your", "seamless", "nestled in") or like a tutorial. Fail: P2. → [design.md](../building/design.md)
- [ ] No stale years, such as a © line from last year. Fail: P2.
- [ ] No photo of an identifiable person without the client's OK, and no duplicate photos in one gallery. Person: P1. Duplicate: P2.
- [ ] The site's own console has no errors. Fail: P2.

### Visual diff against main
- [ ] Screenshot every touched page at all four widths on the PR preview and on main (or production), and diff them. Every change is one the PR describes. An unexplained change: P1. Expected changes get listed in the QA note.

## The QA note
- Verdict first: PASS or FAIL, the commit it applies to, and what was tested.
- Then P0 to P3 findings, each with the page, the width, a screenshot or other evidence, and a suggested fix.
- Then the retest results for the project's earlier bugs.
- A pass applies only to that commit. A new push needs a recheck.
