# Sanity (CMS)

- **One Studio per site, embedded at `/admin`.** Never also deploy a hosted `*.sanity.studio`, and keep `/admin` out of search (`noindex`, disallowed in robots). Why: a stale hosted Studio showed a client "Unknown fields." `/admin` is Jake's call (Oct 28, 2026), though Sanity's docs default to `/studio`. Older sites on `/studio` stay as they are for now. (drewdella, Abis #45)
- **Fetch on the server.** Vite or SPA sites go through their own `/api`. Why: browser fetches break on previews (CORS), render blank and hurt SEO. (fix sanity cors)
- **Keep content fresh with timed revalidation or a publish webhook, not cron.** Why: both are free when nobody visits. (fix sanity cors)
- **CORS lists each production URL, never `*.vercel.app`.** Why: a wildcard lets any Vercel site call the project. (fix sanity cors)
- **CMS content lives only in the CMS.** No hardcoded fallbacks. Why: Jake called them "shady" on three sites. (drewdella, jasiahpowers, jakedcl.com)
- **Anything a client might edit is a field.** (jakedcl.com, jasiahpowers)
- **Read the schema before writing.** Never invent fields, seed scripts fill only empty fields, and remove leftover fields after schema changes. (drewdella, jasiahpowers)
- **When removing or renaming a schema field, unset that field on every existing document and draft.** Why: leftover values show Studio's yellow "Unknown fields found" box with a red Remove button, and clients think the site is broken. Grep the code first to confirm the field is unused; unset on published docs, then on drafts without publishing the client's in-progress edits. Hidden legacy reference fields count too. Why: five old gallery fields made about 65 photos look used and blocked their deletes. (jasiahpowers, Oct 27, 2026; Abis #55)
- **Run `sanity schema deploy` whenever the schema changes.** Why: publishing via the Sanity MCP or API validates against the deployed server schema; if it's stale, publishes fail. The agent environment needs the Sanity CLI logged in or a deploy token. This applies to embedded Studios too: `sanity schema deploy` only uploads the schema definition for tools (MCP, API); it does not host a Studio. That's `sanity deploy`, which we don't use. (jasiahpowers, Oct 27, 2026)
- **Back up the dataset before bulk edits.** Add only verified facts and delete nothing. Why: "fill in data only if its real!" (compactpickup)
- **Content migrations are additive and safe to run while the client edits.** Back up first, patch with `ifRevisionID`, and leave drafts alone. Why: bulk patches can overwrite a newer edit. (Abis)
- **Each fact lives in one place.** Why: duplicates in fields and body text drifted apart. (compactpickup)
- **Never discard drafts without asking.** (drewdella)
- **Turn off Sanity's "What's new" announcement popups in every client Studio.** Add `announcements: { enabled: false }` to `defineConfig` in `sanity.config`. Why: clients shouldn't see product marketing in their CMS. The flag is internal/hidden in Sanity v6 types but works. (jasiahpowers, Oct 27, 2026)
- **Client Studios work on a phone:** one page with fields in site order, 16px inputs, and "What's new" turned off. Why: clients edit from their phones, and iOS zoom blocks the keyboard. (731photography)
- **Client-proof the Studio before handoff.** Max lengths sized to the layout with a plain message, required key fields, singleton pages that can't be deleted or duplicated, strong references so a photo in use can't be deleted, plus a "Used in" list on each photo. A build-time content check fails the build when required content is missing. Why: Studio defaults let a client delete a photo in use, wipe a required field, delete a page or overflow a layout. (Abis #54, #59)
- **Studio labels say what changes on this site, in the client's words.** Toggles describe their normal state ("Email form requests to the restaurant," normally on). Never imply the Studio controls outside accounts. Why: "Search engine info" read like it edited the Google Business Profile. (Abis #54)
- **Structured facts (hours, prices) parse the way people type them and show a red Studio error on lines they can't read.** No hidden fallback fields. Why: a strict hours parser fell back to stale hidden values and sent them to Google. (Abis #46)

## How to decide
- **Use Sanity when non-developers edit content and the app has no database of its own.** If it already has a database and sign-in, build simple in-app forms instead. If there's no CMS yet, keep copy in `content/`, shaped like the future CMS types.
