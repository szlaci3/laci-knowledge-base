# Laci knowledge base

Laci is a personal collection of knowledge, notes, and flashcards stored as plain
Markdown files with structured metadata. It provides a durable place for what I
learn, want to remember, or want to study, independently of the application used
to capture or retrieve it.

The repository contains the knowledge itself. Different projects, assistants, and
study tools can use the same records without making their conversation history or
search databases the source of truth. The files follow the local
[Laci OKF profile](SCHEMA.md); compatibility depends on supporting that profile.

## What belongs here

| Record type | Purpose |
|---|---|
| `knowledge` | Information saved for future reference and reuse. |
| `note` | An observation, idea, question, or working thought. |
| `flashcard` | A question and answer for study, with deck and review metadata. |

Records are saved on explicit user request. A personal note may express an open
question or an intention rather than an established fact. Source links and context
help readers and assistants distinguish those cases.

## Repository structure

```text
README.md       Overview for readers and integrating projects
index.md        Knowledge-base entry point
SCHEMA.md       Record format and metadata conventions
records/        Canonical Markdown records, one file per stable identity
```

Each record lives at `records/<stable-id>.md`. Its path is its identity, so changing
the title does not require renaming the file. YAML frontmatter describes the record;
the Markdown body holds its readable content and links.

Required fields include the record's type, title, active or archived status, and
creation/update dates. Flashcards also carry their question, answer, deck, and
review fields. See [SCHEMA.md](SCHEMA.md) for the full contract, including scalar
serialization and mirrored flashcard content.

## Reading and reusing the collection

Start at [index.md](index.md), or browse [records/](records/). Any text editor can
read the files. Integrating applications can parse the metadata, search the bodies,
follow relative links, and build their own indexes outside this repository.

When using these records to answer questions:

- Treat canonical files as the evidence; generated indexes only help locate them.
- Exclude archived records from normal retrieval while retaining them on disk.
- Cite the supporting record and preserve available source links and context.
- Distinguish recorded personal information from an assistant's interpretation.
- Say when the available records do not support an answer. Documentation and an
  empty collection are not evidence of personal facts.

## Using Laci across projects

The collection can be checked out on its own or included as a Git submodule in
another project. Each consumer supplies its own user interface, model integration,
retrieval tools, and study workflow; those components are not part of this repository.

Applications that write records should preserve stable paths, creation dates,
metadata, and source links, and follow the schema. Coordinate writers and detect
conflicting edits rather than overwriting another application's changes. Git
submodule checkouts can point to different revisions; they do not automatically
synchronize a shared live collection.

Search indexes are disposable derived data and should stay outside the knowledge
bundle. An application should refresh or invalidate its index when records change.

## Ownership and access

This is a personal knowledge base, not a general reference corpus. Its contents and
availability may change. Applications consuming it should respect the user's
instructions about saving, changing, deleting, and sharing information. Access to
the files does not itself authorize publishing them elsewhere.
