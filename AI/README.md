# AI

The context layer that Claude Code, Codex/Astra, and Namyac read before they
work. It does not copy the vault; it points at it.

Reading order for a new session: `Project Context.md` first (short on
purpose), then `Knowledge/Vault Index.md` only if the request needs vault
knowledge, then the specific note it points to. Never load a whole folder
"to have context."

## The chain

```
me -> Claude Code (orchestrator)
   -> prompt-engineer (spec only, never executes)
   -> targeted vault retrieval
   -> specialist agents (researcher, analyst, writer, code-reviewer)
   -> qa-reviewer
   -> back to Claude Code -> me
```

Claude Code stays in charge the whole way. Agents do not call each other.

## Rules

- `CLAUDE.md` at the vault root is still the file that loads every session.
  This folder does not replace it.
- Nothing under `AI/` leaves the machine.
- Memory entries are dated and one line each, so they can be read and reversed.
