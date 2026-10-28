# Lesson 2.1 — Build a context architecture

**Module:** Context Engineering  
**Level:** Advanced  
**Estimated duration:** 60 minutes instruction + 90 minutes lab  
**Version:** draft v0.1

## Learning outcomes

By the end, you can:

1. Map the sources that can influence an AI-assisted coding task.
2. Separate durable repository knowledge from task instructions, retrieved evidence, tool observations, and session-specific state.
3. Place guidance where it is most likely to apply, while checking each tool's actual discovery and precedence rules.
4. Test whether the guidance changes work quality, rather than assuming that a file was read or followed.

## Core idea

Context engineering is the deliberate design of information selection, organization, timing, and validation around a task. It includes repository guidance, current task details, relevant code and tests, retrieved documentation, and observations returned by tools. It does not mean that the model has permanently learned the repository.

Treat every context source as a hypothesis: it may be absent, stale, irrelevant, contradictory, or misinterpreted. The workflow must make important sources discoverable and the resulting work verifiable.

## A practical context map

For one representative task, record the following sources:

| Source | Typical lifetime | Question to ask |
|---|---|---|
| Task request and acceptance criteria | One task | Is the requested outcome observable and bounded? |
| Repository instructions | Until changed | Who owns them, where do they apply, and how are they discovered? |
| Source code, schemas, tests, and configuration | As the repo changes | Which file is authoritative for this behavior? |
| Retrieved docs or examples | Until the source changes | Is this current, relevant, and attributable to a source? |
| Tool output and execution results | One action or session | What did the tool actually observe or change? |
| Session notes or external memory | Tool-dependent | Is this durable, scoped, and safe to reuse? |

The categories are a reasoning aid, not a promise that every product exposes them separately. Inspect the tool in use and record what it actually reads.

## Put guidance where it belongs

Use a repository-wide instruction file for stable conventions that apply to most work: architecture boundaries, build commands, test expectations, and project-specific terminology. Keep task-specific goals and acceptance criteria in the task request. Put detailed behavior beside its authoritative source where possible, and use narrow, path-specific guidance only when the tool supports it and the additional rule is truly local.

Avoid copying the same facts into multiple instruction files. Duplication creates multiple places to update and lets versions drift. Prefer a short explanation that points to the authoritative file. Do not place secrets, private customer data, credentials, or generated transcripts in durable instructions.

A sound instruction should be actionable and checkable. “Write clean code” is difficult to evaluate. “Keep parsing in `src/parser`; add a fixture for each supported input shape; run `make test-parser`” can be checked in a specific repository. Use actual paths and commands from the project; do not invent them.

## Check discovery and conflict behavior

Instruction filenames and precedence are product- and surface-specific. A filename supported by one editor, CLI, or hosted agent may be ignored by another. Even within one vendor, different surfaces can support different subsets. Confirm:

- recognized filenames and locations;
- whether nested files are discovered;
- whether files are combined, overridden, or scoped to matching paths;
- whether the current workspace root affects discovery;
- whether the tool shows which instructions it loaded.

When two rules conflict, resolve the conflict in repository documentation or task scope. Do not rely on a model to infer which document is newer. Record an owner and review trigger for guidance that can become stale.

## Measure the result

Compare a baseline workflow with the proposed instruction set on multiple tasks. Keep prompts, repository state, tool settings, and scoring criteria stable. Use tasks that were not used to write the instructions. Record correctness, required rework, unnecessary changes, safety issues, task time, and whether the assistant used the intended commands. A single successful run is anecdotal evidence, not a reliable evaluation.

Instructions can also make results worse by adding noise, conflicting rules, or outdated facts. The correct output may be “no change needed”; score that outcome correctly.

## In-class exercise

In pairs, map context for a small change request. One person lists every source the assistant could use; the other marks each source as authoritative, advisory, transient, or unverified. Find one missing source, one possible conflict, and one fact that should not be copied into a general instruction file.

## Takeaways

- Context is assembled for a task; repository familiarity is not proof of persistent model memory.
- Durable guidance should have a clear scope, owner, source of truth, and way to verify its effect.
- Tool discovery and precedence are implementation details that require current verification.
- Evaluate context changes on repeated, held-out tasks and keep the evidence.

## References to verify before delivery

- GitHub Docs, “About customizing GitHub Copilot responses”: https://docs.github.com/en/copilot/concepts/prompting/response-customization
- OpenAI Cookbook, “Codex Prompting Guide” (section “Using agents.md”): https://developers.openai.com/cookbook/examples/gpt-5/codex_prompting_guide

Checked 28 October 2026. These references describe specific products and surfaces; they are examples, not universal rules for other tools. Recheck availability, naming, and behavior before each course release.
