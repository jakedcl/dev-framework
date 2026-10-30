# Grok Bot

Grok Bot skills that encode framework rules. The framework is the source of truth; when a rule changes here, update the skill to match.

| Skill | Framework rules |
| --- | --- |
| `image-delivery-for-cms-backed-sites-on-vercel` | [building/images.md](../building/images.md), [building/user-uploads.md](../building/user-uploads.md) |
| `qa-review` | [checklists/qa.md](../checklists/qa.md), [working/git.md](../working/git.md) |
| `launch-cloud-agent-efficiently` | [working/agents.md](../working/agents.md), [working/git.md](../working/git.md), [tools/cursor.md](cursor.md) |

## QA bot
- **When Jake asks, project bots send PRs to the QA bot in Grok Bot** with the PR link, the preview URL, what changed, and what to focus on. QA replies to the project bot and to CTO tech with a PASS or FAIL note, and never merges. → [working/git.md](../working/git.md)
