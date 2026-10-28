# ROC Project Handover

## Purpose

ROC is the repository for a commercial AI training course. The broader project is **AI Engineering Mastery — Beyond Prompting**. Use this document to carry project decisions between ChatGPT, Codex, and other AI tools without relying on chat history alone.

## Current status

- GitHub repository: [movmarcos/Roc](https://github.com/movmarcos/Roc)
- Default branch: main
- Repository was effectively empty at handover time: its only file was a minimal README.md.
- The GitHub connection authenticated as movmarcos and reported push access, but its contents API returned HTTP 403 for a file creation attempt.
- The shared conversation says course starter materials had already been developed in the associated ChatGPT Project: an initial course structure, Module 1, a practical lab, and instructor materials.
- Those source materials were not present in the shared conversation or in the repository when this handover was prepared. This handover records that gap; it does not recreate or replace the original materials.

## Agreed repository structure

    Roc/
    ├── curriculum/
    ├── modules/
    │   ├── 01-ai-fundamentals/
    │   │   ├── lessons/
    │   │   ├── labs/
    │   │   └── assessments/
    │   ├── 02-context-engineering/
    │   ├── 03-claude-code/
    │   ├── 04-codex-copilot/
    │   └── ...
    ├── instructor/
    ├── commercial/
    ├── examples/
    └── README.md

The structure is an initial proposal from the conversation. Keep the agreed module names and scope aligned with the source curriculum when it is available.

## Decisions captured

- Keep the ChatGPT Project as a place for course architecture, content creation, and review.
- Use GitHub as the permanent source of truth for approved course materials.
- The intended workflow is to develop and commit course files in ROC, then review changes against the project decisions.
- Treat the GitHub write failure as a tool/permission recovery case study. Autonomy means trying another authorised route and verifying the result, not bypassing access controls.
- Potential case study topic: **Agent Autonomy, Tool Failures, Permission Boundaries, and Recovery Strategies**.

## Next steps

1. Bring the existing course structure, Module 1, practical lab, and instructor materials from the ChatGPT Project into this repository without rewriting them from memory.
2. Reconcile the source material with the proposed directory structure.
3. Add assessments and examples only where the source curriculum calls for them.
4. Review links, filenames, and consistency, then record the source project and transfer date in the relevant files.
5. Expand this handover with product positioning, learner profile, course objectives, curriculum decisions, and technical architecture from the source project.

## Continuation notes

The shared conversation itself does not contain the complete course files or detailed curriculum decisions. A new session should inspect the ChatGPT Project's files or receive those source files before claiming they have been migrated.
