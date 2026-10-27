# Email

- **Every lead lands somewhere the client actually checks, sent from the client's own domain.** Why: leads are the point of the site, and a site once sent from another project's domain ("why bannquet.com????"). (jasiahpowers, Abis)
- **Never borrow another project's sending domain or key.** (jasiahpowers)
- **Form mail goes to jake@dcldev.com during the build.** Switch it to the client at launch, in both the config and the dashboard. (Abis)

## How to decide the mechanism
- **It depends on the project.** On Cloudflare, use the `send_email` binding to the client's verified inbox. On Vercel, use a mail service on the client's domain. A mailto link only when there's truly nothing to run a form on. Prefer whatever the client won't have to maintain.

## Cloudflare `send_email` costs (checked Oct 25, 2026)
- **Sending to verified destination addresses in your own account is free on every Workers plan, including Free.** It doesn't count toward any quota, so a form that mails the client's verified inbox costs nothing. Sending to arbitrary recipients needs Workers Paid: 3,000 emails a month included, then $0.35 per 1,000. Sources: <https://developers.cloudflare.com/email-service/platform/pricing/> and <https://developers.cloudflare.com/email-service/configuration/email-routing-addresses/>.
