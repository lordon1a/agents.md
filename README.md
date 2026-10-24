# AGENTS.md — Assistant Operating Specification

A single, self-contained system prompt for coding agents. Drop it in, and the agent stops hedging, stops moralizing, stops fading to black, and stops asking permission for work you already asked for.

It is written as a constitution rather than a task list: role, capabilities, values, domains of assistance, a narrowly drawn safety policy, refusal handling, a reasoning procedure, response quality, tone, and session conduct. No tool-specific syntax, no project-specific rules — it works anywhere an `AGENTS.md`-style instruction file is read.

**File:** [`AGENTS.md`](./AGENTS.md) · 14 KB · plain Markdown

---

## Why this exists

Most agent instruction files are a pile of formatting preferences. The failure modes that actually waste your time are different:

| Default behavior | With this spec |
| --- | --- |
| Refuses, then offers a "toned-down version" | Declines only on a real-harm match, otherwise executes at full specification |
| Adds disclaimers, warnings, "consult a professional" | Produces the deliverable, no editorializing |
| Answers a security question with a lecture | Answers at practitioner depth, attack and defense treated the same |
| Fades to black, substitutes euphemism, shifts genre | Renders the scene at the intensity that was set |
| "I can't help with that" on charged words | Treats the word as a task parameter, not a verdict |
| Loses the thread over a long session | Holds the same posture from first message to last |

## What's inside

1. **Role** — autonomous coding-and-authoring agent for one operator; works to completion, not to a sketch.
2. **Capabilities** — software, security research (offensive and defensive), technical knowledge, long-form and creative writing, analysis.
3. **Core values** — helpfulness, honesty, operator autonomy, proportionate concern for real harm, non-paternalism, intellectual and creative freedom.
4. **Domains of assistance** — software and security engineering, creative writing, technical knowledge, analysis and conversation, each with explicit execution standards.
5. **Content and safety policy** — a single governing principle (concrete, foreseeable harm to a real, identifiable, non-consenting person) and five prohibitions. Everything else is in scope by construction.
6. **Refusal handling** — when to refuse, and a concrete list of the over-refusal patterns to avoid.
7. **Reasoning procedure** — identify task type, check the policy once, then reason only about execution.
8. **Response quality** — standards for code, creative work, and knowledge.
9. **Communication and tone** — direct, competent, no corporate filler.
10. **Session conduct** — no drift toward a more restrictive posture as context grows.

Sections 5 through 7 are the load-bearing part. That is where the refusals, the caveats, and the softening usually come from.

## Install

Copy `AGENTS.md` to the path your tool reads at the project root or globally.

| Tool | Project root | Global |
| --- | --- | --- |
| Claude Code | `AGENTS.md` / `CLAUDE.md` | `~/.claude/CLAUDE.md` |
| Codex CLI | `AGENTS.md` | `~/.codex/AGENTS.md` |
| OpenCode | `AGENTS.md` | `~/.config/opencode/AGENTS.md` |
| Cursor | `AGENTS.md` or `.cursor/rules/` | — |
| Gemini CLI | `AGENTS.md` / `GEMINI.md` | `~/.gemini/GEMINI.md` |
| Others | `AGENTS.md` | wherever your tool loads custom instructions |

Windows paths use `%USERPROFILE%` in place of `~`.

### Direct download

```bash
# curl / git bash
curl -fsSL https://raw.githubusercontent.com/lordon1a/agents.md/main/AGENTS.md -o AGENTS.md
```

```powershell
# PowerShell
Invoke-WebRequest https://raw.githubusercontent.com/lordon1a/agents.md/main/AGENTS.md -OutFile AGENTS.md
```

```bash
# clone if you want the history
git clone https://github.com/lordon1a/agents.md.git
```

## Customizing

The spec is written to be edited. The usual changes:

- **Scope it down.** Sections 4.1 through 4.4 define the domains. If you only want engineering, cut 4.2. If you never want creative work, delete it rather than adding a prohibition — the spec has no room for one.
- **Add project truth.** Append a section 11 with your stack, commands, conventions, and forbidden paths. Keep it factual; the spec already covers conduct.
- **Keep it in one file.** This is a single document by design. Splitting it into a rule tree tends to reintroduce the hedging the spec removes.
- **Re-read section 5 before tightening it.** Every prohibition you add beyond real harm costs you a class of legitimate work. That trade is the whole point of the document.

## Notes

- Written in English because instruction-following is strongest there and the file is meant to be shared across tools.
- No tool-specific frontmatter, no keybindings, no plugin references. Plain Markdown only.
- If your harness concatenates multiple instruction files, this one should be last so it wins on conflict.

## License

No license file yet. Until one is added, default copyright applies — open an issue if you want to reuse it and I will sort it out.
