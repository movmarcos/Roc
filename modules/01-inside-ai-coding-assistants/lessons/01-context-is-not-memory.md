# Lesson 1.1 — Context is not memory

**Module:** Inside AI Coding Assistants  
**Level:** Advanced  
**Estimated duration:** 45 minutes instruction + 60–90 minutes lab  
**Version:** draft v0.1

## Learning outcomes

By the end, you can:

1. Distinguish a model's learned parameters from its current prompt context, workspace files, retrieved information, and persisted tool/session state.
2. Explain why a coding assistant may appear to know a project across sessions without assuming the underlying model has permanently learned it.
3. Build a testable map of the information sources that influence a coding assistant's answer.
4. Detect stale, contradictory, or irrelevant context before committing generated code.
5. Measure how explicit context changes the repeatability and correctness of a development task.

## The problem

After months of using an AI terminal assistant, it can feel like a colleague who knows the codebase: it references architectural choices, follows naming conventions, and remembers ongoing tasks. But the statement **“the AI knows my project”** hides several technically different mechanisms. You need to know which mechanism is responsible before deciding whether your workflow is reliable.

## A practical mental model

An assistant response depends on multiple inputs. Consider this *conceptual model*, not a precise vendor implementation:

`result = model(weights, instructions, conversation_context, supplied_files, retrieved_content, tool_results, execution_policy)`

- **Model weights:** broad capabilities learned during training. Running a coding session does not normally train those weights on your repository.
- **Instructions:** current system/developer/project/repository guidance; authority and precedence vary by product.
- **Conversation context:** messages and selected tool outputs presented to the model for a request. A context window is finite, and applications may compress or select history.
- **Supplied or retrieved project content:** explicitly opened files, indexed snippets, searches, or repository metadata. The model cannot reliably infer unseen code.
- **Persisted state:** product-specific sessions, summaries, notes, caches or external stores; persistence and retrieval are not guaranteed across all products.
- **Tools and policy:** what files may be read, what commands may execute, whether changes need approval and how results are returned.

**Key distinction:** context is information made available *now*. Memory is an overloaded product term that may refer to retained notes, session persistence, retrieval, or user preferences. Always ask what is stored, where, for how long, and by what retrieval mechanism.

## Why apparent expertise is fragile

Imagine a repo migrated from SQLite to PostgreSQL. Six months ago the assistant was told that all tests use an in-memory SQLite database. Today that may be false. If old conversation text or an outdated project instruction is still influential, the assistant may confidently generate obsolete fixtures. The failure is not necessarily a weak model; it may be a context-provenance failure.

A robust assistant should be able to cite a current file or command output for architecture-sensitive claims and flag any discrepancy between documentation and implementation.

## Context quality over context volume

More context is not automatically better. Large unrelated files can increase expense and make relevant facts harder to identify. Context engineering means selecting the **minimum sufficient, authoritative, fresh and task-relevant** information, while preserving constraints and verification requirements.

A useful priority order for an ordinary code change is:

1. Current task and acceptance criteria.
2. Existing code and tests for the affected feature.
3. Relevant architecture and repo conventions.
4. Recent decisions that override older conventions.
5. Broader history only when evidence shows it matters.

This is a design heuristic, not a claim about a product's fixed internal precedence rules.

## Architecture exercise: locate the evidence

For your current repository, answer:

- Which facts are **in the code** versus **in project instruction files**?
- Which facts are only **in past conversations**?
- Which facts require **tool calls** to verify (dependency versions, CI state, database schemas)?
- Which facts could be outdated?
- Which facts can be checked with an automated test?

For each important assertion, record its source, last verified date and confidence.

## Failure modes worth recognising

**Stale instruction:** repo policy says one thing while current code says another. Resolution: inspect both, check history, and update the source of truth.

**False continuity:** the assistant claims to recall a decision that is not actually available in the current session. Resolution: ask it to show evidence, not confidence.

**Context flooding:** loading the whole repo obscures the one function that matters. Resolution: scoped retrieval, file map, progressive disclosure.

**Authority confusion:** instructions embedded in a retrieved README or issue are treated as higher-trust commands. Resolution: treat retrieved content as untrusted data and constrain tool authority.

**Unverified success:** the assistant reports a code change is complete without executing relevant checks. Resolution: require explicit evidence and distinguish attempted from verified outcomes.

## Knowledge check

A new session accurately describes the repo architecture. Name at least three possible causes other than the base model having learned the repository during this session. For each, propose a test that might distinguish it from the others.

## Next step

Complete the [Project Context Audit](../labs/01-project-context-audit.md). Do not refactor the production project for the exercise. Use an isolated branch or a copy and record your observations.

## Source verification note

This first lesson teaches product-independent concepts. Current product-specific claims about Claude Code, Codex, and Copilot will be independently checked against their official documentation before commercial release.
