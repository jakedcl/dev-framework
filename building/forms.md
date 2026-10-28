# Forms and server actions

- **Show "Sent" only after the server confirms the email went out.** Every failure (Turnstile down or rejected, expired form, paused inbox, mail error) shows a real error with another way to reach the client. Why: the Abis form said Sent while dropping real leads. (Abis #39)
- **Spam heuristics flag, never drop.** A suspicious submit still emails, with a "Check this one:" subject. Only the honeypot and Turnstile may block. Why: names like "Ty Ng" and "Need [10] trays" were silently thrown away. (Abis #39)
- **Make submits idempotent.** Clear the form, confirm it worked, and have the server reject duplicates: a submission ID reserved before sending, released on failure, remembered for about 10 minutes (Workers Cache on Cloudflare). Why: double taps saved every bannquet photo twice. (bannquet, Abis #40)
- **Expired sessions ask the user to sign in again, never crash.** (bannquet)
- **Missing keys never crash a form.** An unfinished form says plainly that it isn't connected yet, with no "call us" placeholder. Why: a client read "please call" as intended. (Abis, Jake Oct 25, 2026)
- **One bad file never sinks a batch upload,** and deleting a photo also deletes its thumbnail. (bannquet)
- **Block spam for free:** a honeypot field, a too-fast-submit check, a per-IP limit, plus Turnstile and a rate limit on Cloudflare. (bannquet, Abis)
- **Turnstile renders `compact` when its container is under 300px.** Why: the flexible widget never shrinks below 300px and scrolled a 246px form card sideways on 320px phones. (Abis #60)
- **Server logs tell a rejected Turnstile secret apart from Cloudflare being down,** and log only the secret's length, never its value. (Abis #50)
- **Never collect sensitive data in your own forms.** → [security.md](security.md)
