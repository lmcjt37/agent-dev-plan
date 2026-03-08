# Agent Dev Plan Skill

A planning skill for AI coding agents that **streamlines implementations** and **defines working structure** directly inside your project—so you can remember the *order* things should be implemented and provides context for the agent over several sessions.

It maintains three things at the **closest git repo root**:

- `plan/<branch>/plan.md` — a curated, bullet-pointed plan (succinct entries, with sub-bullets for added details)
- `plan/<branch>/decisions.md` — a searchable decision ledger (DR-### entries)

---

## Who this is for

- Developers using AI agents and wanting a reliable “paper trail” of their implementation.
- A way to keep track of the context of the feature plan across contexts.
- Anyone who wants to benefit from reducing repetitive planning sessions with their agent.

---

## What it does

### ✅ Plan making

This skill depends on Atlassian MCP, it utilises this MCP in order to carefully plan out a detailed implementation of your feature.

You provide it a ticket reference (hopefully with reasonable detail) and it can formulate the necessary steps required for a detailed plan.

Each plan includes:
- A breakdown of the ticket into small implementation chunks (bullet points) of effort which can be committed at each checkpoint.
- Each chunk or section should consist of sub-bullets with additional detail which can help for context in handover.

### ✅ Decision capture

If you have an issue with certain elements of a plan, no problem. Tell the agent to skip, reprioritise another section, or audit the codebase again.

It should be able to handle working in an agile approach to help you deliver your feature in the most efficient way possible.

---

## How to use this skill

Install the skill Using skills.sh:

```bash
npx skills add https://github.com/lmcjt37/agent-dev-plan --skill agent-dev-plan
```

---

## What gets written to your repo

After a checkpoint, you should see:
- `plan/<branch>/plan.md`
- `plan/<branch>/decisions.md`

Naming rules:
- Repo root: closest git root via git rev-parse --show-toplevel
- Branch: git rev-parse --abbrev-ref HEAD (slashes sanitized to -)
- Agent name: detected if possible, otherwise [AGENT]
- Session boundary: branch + day (so you can span multiple days safely)


Prompts that work well
- plan my ticket `<JIRA-REFERENCE>`
- Can you help plan my ticket `<JIRA-REFERENCE>`

OR;

Slash commands:
- /plan `<JIRA-REFERENCE>`


## FAQ

*Can it work across multiple projects?*

Yes. It always writes to the closest git root, so it naturally scopes to the current project.

*What if the repo doesn’t have plan.md yet?*

The skill creates it automatically using the required outline and style guidelines.


---

## Contributing

PRs welcome:

- Better redaction patterns
- Tighter decision detection
- Improved transcript compression heuristics

---

## License

See [LICENSE.md](./LICENSE.md).