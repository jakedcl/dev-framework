# Forms and server actions

- **Make submits idempotent.** Clear the form, confirm it worked, and have the server reject duplicates. Why: double taps saved every bannquet photo twice. (bannquet)
- **Expired sessions ask the user to sign in again, never crash.** (bannquet)
- **Missing keys never crash a form.** An unfinished form says plainly that it isn't connected yet, with no "call us" placeholder. Why: a client read "please call" as intended. (Abis, Jake Oct 25, 2026)
- **One bad file never sinks a batch upload,** and deleting a photo also deletes its thumbnail. (bannquet)
- **Block spam for free:** a honeypot field, a too-fast-submit check, a per-IP limit, plus Turnstile and a rate limit on Cloudflare. (bannquet, Abis)
- **Never collect sensitive data in your own forms.** → [security.md](security.md)
