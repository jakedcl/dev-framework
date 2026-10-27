# Cursor

How the generic rules in [working/agents.md](../working/agents.md) map to Cursor.

## Cloud agents: use the saved environment
- **Nearly every jakedcl repo has a saved Cloud Agents environment** with the setup already done. Why: the agent doesn't spend usage rebuilding it. (dependabot, Jake)
- **Before launching, find the environment whose repos include the target repo and launch in it.** Only use the plain default VM when no environment covers the repo, and say so in the notes.
- **The brief points the agent at the repo's AGENTS.md first,** and at the framework rules it links, before touching code.
- **Brief:** goal, exact branch or PR, what done looks like, what not to do. Default model unless Jake asked for another. No screenshots unless the work is visual, no full-repo rescans, no Co-authored-by lines, never merge unless Jake said to.
- **Follow-ups on the same branch go to the same agent,** not a new one, so it keeps its context and machine state.
