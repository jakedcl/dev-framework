# Security and secrets

- **No CMS tokens in `NEXT_PUBLIC_` or `VITE_` variables.** Public datasets need no token. Why: those variables ship to every browser. (fix sanity cors)
- **No database credentials in agent prompts.** Use a throwaway branch or have a person run the step. (logiparty)
- **Keys live only in the host's secret store,** never in the repo, Notion or docs. Rotate any that leaked. Why: live keys turned up in Notion. (#GROKBOT, dcldev studio)
- **Never collect SSNs or similar data.** Send people to a vendor built for it. Why: the vendor carries the liability. (our island realestate)
- **Payment and print providers stay in sandbox unless real orders are intended.** (731photography)
- **Sign-in rules** are in [auth.md](auth.md).
