# Stack and versions

- **Start on the latest supported majors** (currently Next 16+, React 19, TypeScript, Tailwind 4), and check the support window first. Why: Abis's builds broke when Next 15 support ended. (Abis)
- **Next.js support:** a major is Active LTS until the next major ships, then Maintenance LTS for two years from its own release. Next 16 is Active LTS since Oct 21, 2025. Next 15 (Oct 21, 2024) hit end of support around Oct 21, 2026, so sites still on 15 get upgraded. Check <https://nextjs.org/support-policy> before starting or upgrading. (Jake, Oct 27, 2026)
- **Use a Node version the host still supports.** (drewdella)
- **Prefer free data and map sources** (OpenFreeMap, USGS, NWS) over paid APIs. (bannquet)
- **Don't port a site to a new framework without a reason.** Not everything needs Next. (metrotapes)
- **Major upgrades use the official codemod, then a hand check of the preview.** Next 16's breaking changes: `middleware` becomes `proxy`, `revalidateTag` becomes `updateTag` in actions, `params` become async, and lint runs as its own step. (Oct 23, 2026 upgrades)
