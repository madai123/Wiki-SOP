# Research Knowledge Base SOP

This repository contains a reusable SOP for building an AI-assisted research knowledge base. It focuses on paper discovery, PDF parsing, paper summaries, concept and entity indexing, research gaps, comparisons, and synthesis notes.

The repository is organized as a set of operating procedures and page templates. It is intended to be adapted to your own research area, tools, and publishing targets.

## What This Is

- A workflow for turning papers into structured research notes.
- A directory convention for separating raw inputs, parsed material, wiki pages, and SOP documents.
- A set of templates for paper summaries, concepts, entities, gaps, comparisons, synthesis pages, and daily paper reports.
- A set of guardrails for source verification, human confirmation, and avoiding fabricated links or identifiers.

## What This Is Not

- It is not a finished public research wiki.
- It does not include private paper PDFs, raw OCR outputs, or personal reading logs.
- It does not require a specific note-taking app, automation platform, or external document service.

## Repository Map

```text
.
├── CLAUDE.md                 # Agent-facing global SOP
├── INDEX-*.md                # Optional Dataview-style overview pages
├── docs/
│   ├── Workspace.md          # Docs map and workspace structure
│   ├── UserFocus.md          # Public template for focus preferences
│   ├── operation/            # Task procedures
│   └── pattern/              # Page templates
├── wiki/                     # Knowledge-base pages
├── raw/                      # Parsed paper outputs
└── downloads/                # Source PDFs and metadata
```

## Recommended Public/Private Split

Safe to publish:

- `README.md`
- `CLAUDE.md`, after reviewing tool-specific instructions
- `docs/`
- empty or example `INDEX-*.md` files

Usually keep private or publish only as examples:

- `downloads/`
- `raw/`
- `wiki/log.md`
- full daily reports
- private focus preferences
- unpublished paper notes or drafts

## How To Use

1. Read [docs/Workspace.md](docs/Workspace.md) for the workspace structure and document map.
2. Use [CLAUDE.md](CLAUDE.md) as the global execution contract for an AI assistant.
3. For a task, read the corresponding file in `docs/operation/`.
4. When writing a page, use the corresponding template in `docs/pattern/`.
5. Keep source identifiers real and verifiable. Do not invent DOI, arXiv, OpenReview, Semantic Scholar, or other source IDs.

## Customization Points

- Replace `docs/UserFocus.md` with your own current research interests.
- Adjust discovery sources in `docs/operation/DailyPaperWorklist.md`.
- Add or remove frontmatter fields to match your note-taking system.
- Replace optional publishing targets with your own export workflow.

## License

Choose a license before publishing if you want others to reuse this SOP.
