# Laci OKF profile

Canonical records live at `records/<stable-id>.md`. Each has scalar YAML frontmatter
and a Markdown body. Neptune writes JSON-quoted scalar values, a valid YAML subset;
keep this serialization when editing with external tools. The path is the identity.
`index.md` is the entry point. Generated search databases are outside this bundle.

Required metadata: `type` (`knowledge`, `note`, or `flashcard`), `title`, `status`
(`active` or `archived`), `created`, and `updated` (ISO dates). Optional user metadata:
`Author`, `Date`, `Context`. Date defaults to entry date without another question.
Bodies may include ordinary relative links to other Laci records or source URLs.
Use explicit source links and Context to preserve provenance; do not fabricate it.

Flashcards additionally store `front`, `back`, `deck`, `due`, and `interval` (whole
days). Their Markdown Front/Back sections mirror those fields. Reviews also record
`last_review`. Archived records remain stored but are excluded from normal retrieval.

Neptune's mutation command enforces exact-path identity, current revision checks,
atomic replacement, and a writer lock. Edits preserve the path and created date;
note promotion changes type in place. Delete removes the canonical record.
Use the command interface documented in Neptune rather than hand-editing during a
runtime task. External edits are detected as index staleness and revision conflicts.
