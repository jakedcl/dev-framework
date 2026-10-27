# Neon Postgres

- **Previews get their own Neon branch,** with database env vars scoped to Preview. Verify which database previews actually use. Why: bannquet's previews were found on the live database. (bannquet)
- **Neon Auth needs each preview host added as a trusted domain.** (bannquet)
- **`DATABASE_URL` is the pooled URL, and `DATABASE_URL_UNPOOLED` is the direct one.** (bannquet)
- **Write migrations as re-runnable SQL (`IF NOT EXISTS`).** Apply to preview, test, then apply to main before merging. Why: production never runs code that expects a missing column. (bannquet)
- **Agents write migrations but never apply them.** The PR says which SQL to run. (bannquet)
- **Know whether your migration runner tracks history.** If it doesn't, run one named file at a time. (logiparty, bannquet)
- **Try risky schema or security changes on a throwaway branch first.** (logiparty)
- **Enforce multi-tenant isolation with row-level security,** using an app role that can't bypass it. (logiparty)
- **Data-changing scripts dry-run first and need an explicit confirm env var.** (bannquet)
- **Settle the data model before bulk imports.** (bannquet)
- **Reset the preview database when needed, then recreate the standing test account.** (Jake, Oct 25, 2026)
