# Repo AGENTS.md framework section

Paste this section into each client repo's AGENTS.md, under the repo's own notes. Keep it short. The framework repo is private, so the hard rules are copied in for agents that can't open it.

```markdown
## Framework
This repo follows Jake's dcldev dev framework: https://github.com/jakedcl/dev-framework (private, start at AGENTS.md). If you can't open it, these still apply:
- Squash-merge only. No Co-authored-by or other AI attribution lines.
- Never merge unless Jake said to. Ask before deleting anything.
- Root cause before patching. Small, reviewable changes. "Fixed" only after seeing it live.
- Latest supported majors (Next 16+). Dependabot weekly on Monday, minor+patch grouped, majors separate.
- One Sanity Studio, embedded at /studio. Never a hosted *.sanity.studio.
- CMS images go through the CMS image CDN with a per-image next/image loader, never Vercel Image Optimization.
- Keep Vercel overage at or near $0.
- No secrets in prompts, docs or NEXT_PUBLIC_/VITE_ variables.
```
