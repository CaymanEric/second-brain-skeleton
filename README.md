# Second Brain (structure only)

This is a structure-only mirror of my Obsidian vault. Every folder is real and
carries the same name as the private vault, but the notes themselves stay
private. Each folder has a README that says what lives there and how it is used.

The vault is a markdown-first second brain that doubles as the context layer
for the AI tools I run (Claude Code, a local Codex/Astra agent, and a local
voice assistant called Namyac). The notes are the AI's memory as much as mine.

## How it is organized

The base is the ACE method (Atlas, Calendar, Efforts) from Nick Milo, plus a
few source folders and an `AI/` layer that agents read before they work.

```
.
├── Home.md              entry point, retrieval order: project > topic > source > date
├── CLAUDE.md            rules and memory Claude Code loads every session
├── AGENTS.md            the same for Codex/Astra
├── Atlas/               ideas, one per note, in my own words, linked to sources   (~110 notes)
├── Calendar/            daily notes, habit log, reading bookmark
├── Efforts/             active projects, each note owns its next actions
│   └── Archive/         finished projects
├── School/              coursework, one folder per class, grouped by term
│   └── Fall 2026/<COURSE>/{Lectures,Lessons,Assignments}/
├── AI Lessons/          one markdown summary per video or course lesson        (~435 notes)
│   ├── Nate Herk/       creator subfolders for the two largest sources
│   ├── Zubair Trabzada/
│   ├── transcripts/     raw captions paired with each summary                   (~227 files)
│   └── attachments/     downloaded course files, indexed from the notes
├── Reels/               one note per Instagram reel, written by a reels agent   (~33 notes)
├── Mail/                everything pulled out of email, one subfolder per source
├── Namyac/              operating rules and dashboard for the local voice assistant
├── AI/                  the context layer agents read: orientation, memory, logs, loops
│   ├── Conversation Library/   curated notes imported from past AI chats        (~700 notes)
│   ├── Knowledge/       vault index, agent roster, privacy rules, gotchas
│   ├── Memory/          decisions, preferences, patterns that worked and failed
│   ├── Logs/            dated build logs, written only when a run taught something
│   ├── Loops/           reports from an overnight scheduler, plus its proposals
│   ├── Projects/        per-project context for agents
│   └── Templates/       spec and project-context templates
├── .claude/skills/      custom Claude Code skills that live with the vault
├── .agents/skills/      the same skills exposed to Codex
└── Attachments/         the few non-markdown files the vault needs
```

## The rules the system runs on

- Markdown only. No PDFs or docx inside the vault, because Obsidian cannot
  search inside them, cannot backlink from them, and they dead-end the graph.
  "File over app."
- One idea per Atlas note, rephrased in my own words, linked back to the source
  it came from.
- Input must produce output. Before another summary goes in, the last one has to
  have produced an Atlas note or an Effort action.
- Every folder has a hub note with the same name as the folder (`Atlas/Atlas.md`,
  `School/School.md`). The graph chain is Home > index > source note > Atlas.
- Agents read the least context that will do the job: `AI/Project Context.md`
  first, then whatever `AI/Knowledge/Vault Index.md` points at, then stop.
- Agents create freely but never delete or overwrite a note, never send anything
  outside the vault, and never run bulk operations without sign-off.
- When an assistant gets corrected, the lesson goes into `CLAUDE.md` or
  `AGENTS.md` as a one-line rule before it continues, so the mistake is not paid
  for twice.

## Pipelines that feed it

- **Video intake.** A link goes in, a transcript script pulls captions, on-screen
  text (OCR), chapters, description links, and correction-shaped comments. A
  summary lands in `AI Lessons/`, at least one reusable idea is pulled into
  `Atlas/`, and both are linked from the index notes.
- **Reels agent.** Watches an inbox note, writes one note per reel into `Reels/`,
  and updates the reels index between two marker comments.
- **Class recorder.** Lectures are recorded on a tablet, synced through OneDrive,
  transcribed by a watcher on the desktop, and filed into the right class folder
  by matching the start time against a timetable note. A `class-lesson` skill
  turns a transcript into a study note on request.
- **Conversation librarian.** Imports past AI chats into `AI/Conversation
  Library/` as curated notes, with a review queue for suggestions.
- **Night Shift.** A local scheduler runs small, capped agent loops overnight
  (mostly on a local model, sometimes on Claude) and leaves one morning report
  plus proposals in `AI/Loops/`. Loops may write only in that folder.
- **Backup.** The vault is a git repo. A scheduled task commits and pushes it
  several times a day with a timestamped message.

## Tools

Obsidian, Claude Code (with custom skills and a six-agent roster), Codex,
Ollama for local models, Python for the transcript and scheduler scripts, git
for backup.

## Why the real vault is private

It holds coursework, mail, family correspondence, finances, and the memory
files the assistants use. This mirror exists so the structure and the method
can be shown without any of that. Nothing here is generated from note content.
