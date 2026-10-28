# ROC Project Handover

## Purpose

ROC is the repository for **AI Engineering Mastery — Beyond Prompting**, a practical, vendor-neutral AI engineering course. Use this note to carry project state between ChatGPT, Codex, and other tools.

## Current status — 28 October 2026

- Repository: [movmarcos/Roc](https://github.com/movmarcos/Roc), branch `main`.
- The source archive `AI-Engineering-Mastery-Beyond-Prompting-starter.zip` was found in the user's Downloads folder and its draft materials were migrated into this repository.
- The repository contains the course roadmap, Module 1 overview, two lesson drafts, two lab drafts, two instructor guide variants, an assessment rubric, reusable templates, editorial governance, commercial planning drafts, and changelogs.
- The starter set labels itself draft v0.1. These files need technical, instructional, vendor-feature, security, and IP review before publication. Commercial and licensing terms are not finalized.
- The GitHub Contents API returned 403 for writes; commits were completed through GitHub's repository web interface.

## Repository structure

- `curriculum/` — roadmap and curriculum index
- `modules/01-inside-ai-coding-assistants/` — Module 1 lessons, labs, instructor guides, and assessment
- `templates/` — lesson, lab, and lab-results templates
- `governance/` — editorial standard
- `commercial/` — product brief, product strategy, release checklist
- `docs/` — documentation changelog

## Source and organization notes

The archive includes parallel alternatives: `01-context-is-not-memory.md` and `01-context-is-constructed.md`; `01-project-context-audit.md` and `01-context-persistence-experiment.md`; and both a facilitator guide and teaching guide. They are retained as draft variants. Review them together before choosing canonical materials for a pilot.

The archive contained `ROADMAP.md` and `roadmap.md` with matching content. They were collapsed to one `curriculum/ROADMAP.md` to avoid a case-only filename collision on common filesystems; the curriculum index links to that file.

## Decisions captured

- Keep the ChatGPT Project for course architecture, drafting, and review.
- Use GitHub as the durable source of truth for approved materials.
- Retain the source drafts faithfully; record editorial consolidation and review decisions in GitHub.
- Do not distribute externally until licensing and commercial terms are settled.

## Next steps

1. Review the alternative Module 1 drafts and select the versions for a pilot.
2. Validate technical claims and version-sensitive vendor details.
3. Run the labs with learners and check that submitted evidence supports the assessment rubric.
4. Complete security, accessibility, and IP review.
5. Finalize licensing and commercial terms before external distribution.
