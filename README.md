# AI Agent Code of Conduct

A portable, auditable framework for how AI agents are expected to behave when working on `<Your Name>`'s behalf. The repository contains a canonical reference document, a compact agent-facing version optimized for context loading, a Claude entry point, and a version history.

## What this is

An AI agent doing work on your behalf is, in effect, acting as your representative. Its decisions reflect on you, its mistakes affect you, and the data it touches is your responsibility. This document set defines:

- **Hard rules** — bright lines an agent does not cross on its own initiative. Most are overridable by you with explicit, in-the-moment authorization (the agent logs any objection and complies); two — adherence to applicable law and no physical harm to humans — are absolute and cannot be overridden by anyone.
- **Guiding principles** — judgment-based expectations: how the agent reflects on you, communicates, handles uncertainty, anticipates needs, protects your data, avoids the perception of impropriety.
- **Operational standards** — day-to-day quality bar: accuracy, concision, mistake handling, documentation, working with subagents and tools.
- **Process** — how to handle ambiguity and conflicts, what counts as a violation, what termination means, how the document changes over time.

The document is written personal-first (governing agents working for `<Your Name>`) but is structured to be forked for team or organizational use. See section 8.5 of the canonical document for fork guidance.

## Files

| File | Purpose |
|---|---|
| `AI_CODE_OF_CONDUCT.md` | **Canonical document.** Full rationale, examples, and explanation. Read for edge cases. ~4,650 words / ~6,000 tokens. |
| `AI_CODE_OF_CONDUCT_OPERATIVE.md` | **Compact agent-facing version.** Every rule and principle, no rationale or examples. Loaded into agent context. ~1,900 words / ~2,475 tokens. |
| `CLAUDE.md` | **Claude entry point.** Tells Claude to read and follow the operative version. |
| `CHANGELOG.md` | **Version history.** Date-based entries describing each change. |
| `CONTRIBUTING.md` | Guidance for contributors who want to suggest changes or fixes. |
| `README.md` | This file. |

## Adapt for yourself before installing

This document set is published as a personal-first template. Before installing it for any AI agent, replace the placeholders throughout the documents — find-and-replace handles all of them in a few seconds:

| Placeholder | Replace with | Where it appears |
|---|---|---|
| `<Your Name>` | Your name (or the name of the person the agent is working on behalf of) | Throughout `AI_CODE_OF_CONDUCT.md`, `AI_CODE_OF_CONDUCT_OPERATIVE.md`, `CLAUDE.md`, `README.md` |
| `<your federal/national jurisdiction>` | Your country's federal/national legal jurisdiction (e.g., "United States federal law," "European Union law") | Section 4.5 of canonical and operative |
| `<your state/regional jurisdiction>` | Your state, province, or regional jurisdiction (e.g., "California state law," "Ontario provincial law"). If not applicable, replace the placeholder phrase with empty string. | Section 4.5 of canonical and operative |

Other adjustments to consider:

- **Update the `Maintained by:` field** at the top of `AI_CODE_OF_CONDUCT.md` and `AI_CODE_OF_CONDUCT_OPERATIVE.md`.
- **Replace or reset the `CHANGELOG.md`** if you don't want the upstream history in your fork.
- **Review section 8.5** of the canonical document for additional guidance on adapting for team or organizational use (multiple principals, named escalation paths, organizational policy in Section 4).
- **Add a `LICENSE` file** appropriate to how you intend to share or use your fork.

Once placeholders are replaced and any organizational adjustments are made, follow the install instructions below for whichever Claude product or third-party agent you're using.

## How to install

### Claude Code (CLI)

Copy all three files into your home `.claude` directory:

- `~/.claude/AI_CODE_OF_CONDUCT.md`
- `~/.claude/AI_CODE_OF_CONDUCT_OPERATIVE.md`
- `~/.claude/CLAUDE.md`

Claude Code reads `~/.claude/CLAUDE.md` automatically at the start of every session. The `CLAUDE.md` file uses an `@import` directive to load the operative version into context. The canonical version sits alongside it for edge-case interpretation. No additional configuration required.

To verify it's working, start a new `claude` session in any directory and ask: *"What does principle 3.7 of the AI Code of Conduct say?"* — a correct answer (something about being clear, honest, not condescending, audience-aware) confirms the setup.

**Updates:** When the source files in this repository change, copy the updated `AI_CODE_OF_CONDUCT.md` and `AI_CODE_OF_CONDUCT_OPERATIVE.md` to `~/.claude/`.

### Claude Cowork (Desktop App)

Cowork doesn't currently support file-based auto-loading of behavioral instructions — plugin `SessionStart` hooks don't fire in Cowork (Issue [#27398](https://github.com/anthropics/claude-code/issues/27398)), and folder permission grants reset per session, so file-path references in Global Instructions trigger a permission prompt every time. The working approach is two-part:

**Step 1: Inline-paste the operative version into Global Instructions**

1. Open Cowork → Settings → Edit Global Instructions.
2. Paste the entire content of `AI_CODE_OF_CONDUCT_OPERATIVE.md`, prefixed with this preamble (substitute `<canonical path>` with the actual path you chose in Step 2):

   > Before any work, follow the AI Code of Conduct below. For edge-case interpretation, the canonical version with full rationale is at `<canonical path>/AI_CODE_OF_CONDUCT.md` — read it when interpreting nuance, accepting the one-time permission prompt only when needed.

3. Save.

This makes the operative rules always present in every Cowork session, with no per-session friction.

**Step 2 (optional): Place canonical in a Cowork-readable location for edge cases**

For times when the agent needs to reference the canonical document for nuance, place a copy at a path Cowork can reach:

- **Windows:** `%LOCALAPPDATA%\Claude\code-of-conduct\` (typically `C:\Users\<you>\AppData\Local\Claude\code-of-conduct\`)
- **macOS:** `~/Library/Application Support/Claude/code-of-conduct/`

Steps:

1. Create the folder at the path appropriate for your platform.
2. Copy `AI_CODE_OF_CONDUCT.md` into it.
3. The first time the agent reads from this path in a session, Cowork will prompt for permission. Grant it. Subsequent reads in that session won't prompt.

To verify the Global Instructions setup is working, restart Cowork, start a new task, and ask: *"What does principle 3.7 of the AI Code of Conduct say?"* — a correct answer without any folder access prompt confirms the operative is loaded.

**Updates:** When the operative version changes, re-paste the new content into Global Instructions. When the canonical changes, copy the updated file to the AppData location.

### Claude.ai Web (Projects)

1. Create a Project.
2. Upload `AI_CODE_OF_CONDUCT_OPERATIVE.md` to the project knowledge.
3. In the project's custom instructions, add: *"Before any work, read and follow `AI_CODE_OF_CONDUCT_OPERATIVE.md`. Reference `AI_CODE_OF_CONDUCT.md` for edge cases if needed."*
4. Optionally upload the canonical document as additional knowledge.

### Claude API

Include the contents of `AI_CODE_OF_CONDUCT_OPERATIVE.md` in your system prompt, prefixed with: *"You are operating under the following code of conduct. Follow it in all work."*

The canonical version is for human reference and edge-case interpretation, not routine context.

### Third-party agents (other LLMs, frameworks, custom agents)

The document set is model-agnostic. Approaches that work:

- **System prompt inclusion:** paste `AI_CODE_OF_CONDUCT_OPERATIVE.md` into the agent's system prompt, prefixed with: *"You are operating under the following code of conduct. Follow it in all work."*
- **Per-task preamble:** for agents without a configurable system prompt, include the operative version as a preamble to each task.
- **Agent framework instructions:** for frameworks like LangChain, AutoGen, CrewAI, or the Claude Agent SDK, include the operative version in the agent's instruction file or initial message.
- **Multi-agent systems:** when delegating work to subagents, ensure the operative version is passed forward — section 5.5 of the code of conduct requires that subagents inherit the same standards as the supervising agent.
- **Local LLM runners** (Ollama, LM Studio, llama.cpp, etc.): paste the operative version into the system prompt template the runner uses.

In all cases, the agent should treat the document as authoritative for behavioral expectations and surface conflicts with user instructions rather than silently choosing a path.

## Two-tier design and why it exists

Loading a behavioral document into every agent session has real costs: API token charges, context window consumption, and "context dilution" (long instructions tend to get partially tuned out by the model in favor of the immediate task). The two-tier design addresses this:

- The **canonical document** is what humans read, what gets reviewed and updated, and what the agent consults for edge cases.
- The **operative document** is what gets loaded into agent context. Every rule and principle, but no rationale or examples — it's the rule set, compressed.

This preserves full fidelity (no rule is lost) while reducing per-session context cost by roughly 70%.

The two files must be kept in sync. When the canonical document changes, update the operative to match. See `CONTRIBUTING.md` for the change process.

## Contributing changes

The document is maintained by `<Your Name>`. Agents working under it may propose changes when they observe gaps, conflicts, ambiguity, or stale references — but agents do not edit on their own initiative. See section 8.3 of the canonical document for the proposal format and `CONTRIBUTING.md` for contributor guidance.

For forks (team or organizational use), see section 8.5 of the canonical document for the minimum required updates.
