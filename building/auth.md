# Sign-in and accounts

- **Show one generic error for every failed sign-in.** Why: it doesn't reveal which accounts exist. (bannquet#15)
- **Lock out with a cooldown after repeated failures** (bannquet uses 8 tries per 15 minutes), not a permanent ban. (bannquet#15)
- **Log failed sign-ins to your own database, never passwords.** Why: host logs vanish fast. (bannquet#15)
- **Accept a username or an email, case-insensitive.** (bannquet#15)
- **Admins can issue a one-time, expiring reset link.** (bannquet)
- **After signing in, users return to the page they were on.** (bannquet)

## How to decide
- **For non-technical users, prefer email and password over codes or magic links.**
