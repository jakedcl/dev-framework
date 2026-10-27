# Sanity (CMS)

- **One Studio per site, embedded at `/studio`.** Never also deploy a hosted `*.sanity.studio`. Why: a stale hosted Studio showed a client "Unknown fields." (drewdella)
- **Fetch on the server.** Vite or SPA sites go through their own `/api`. Why: browser fetches break on previews (CORS), render blank and hurt SEO. (fix sanity cors)
- **Keep content fresh with timed revalidation or a publish webhook, not cron.** Why: both are free when nobody visits. (fix sanity cors)
- **CORS lists each production URL, never `*.vercel.app`.** Why: a wildcard lets any Vercel site call the project. (fix sanity cors)
- **CMS content lives only in the CMS.** No hardcoded fallbacks. Why: Jake called them "shady" on three sites. (drewdella, jasiahpowers, jakedcl.com)
- **Anything a client might edit is a field.** (jakedcl.com, jasiahpowers)
- **Read the schema before writing.** Never invent fields, seed scripts fill only empty fields, and remove leftover fields after schema changes. (drewdella, jasiahpowers)
- **Back up the dataset before bulk edits.** Add only verified facts and delete nothing. Why: "fill in data only if its real!" (compactpickup)
- **Each fact lives in one place.** Why: duplicates in fields and body text drifted apart. (compactpickup)
- **Never discard drafts without asking.** (drewdella)
- **Client Studios work on a phone:** one page with fields in site order, 16px inputs, and "What's new" turned off. Why: clients edit from their phones, and iOS zoom blocks the keyboard. (731photography)

## How to decide
- **Use Sanity when non-developers edit content and the app has no database of its own.** If it already has a database and sign-in, build simple in-app forms instead. If there's no CMS yet, keep copy in `content/`, shaped like the future CMS types.
