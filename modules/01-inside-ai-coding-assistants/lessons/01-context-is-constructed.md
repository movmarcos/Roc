# Lesson 01 — Your coding assistant does not simply “know” your repository

**Estimated study:** 35–50 minutes plus lab  
**Audience:** experienced developers using an AI coding tool regularly  
**Status:** draft v0.1

## The question
After working with an assistant for months, you may feel it has learned the project. But what information is present *when a new task begins*? What is retrieved, what is injected, and what remains inaccessible unless a tool is called?

## A useful operational model

```text
Developer request
      |
      v
Context assembly (instructions + selected conversation + files/tool outputs)
      |
      v
Model inference ---> proposed response / tool call
                          |
                          v
                  Tool runner and permissions
                          |
                          v
                    Tool observation
                          |
                          +----> next model inference
```

This is an **abstract model**, not a claim that every vendor exposes or implements the same internal pipeline. Product implementations and session features differ.

### Five things developers routinely confuse

1. **Model parameters:** capabilities learned during training; not a per-repository memory of your recent edits.
2. **Active context:** information provided to the model for the current inference; finite and selected/managed by the product.
3. **Repository state:** files in source control or on disk; they do not all automatically fit in active context.
4. **Tool observations:** outputs from reads, searches, tests and terminal commands the assistant is allowed to run.
5. **Durable external knowledge:** explicit instruction files, documentation or other storage that can be consulted again. Presence in storage is not proof that it was consulted this turn.

### A misleading statement
“Claude knows our architecture because we have worked together for months.”

### A testable statement
“Given a fresh session and a documented set of project instructions, the assistant can correctly recover the architecture decision, cite its repository source, and avoid a conflicting implementation.”

The second statement can be measured. It also exposes whether the source is documentation, current repository inspection, recalled conversation, or a guess.

## What to inspect in a real workflow
Before accepting an architectural change, ask:
- What exact files or tools did the assistant inspect?
- Which project instructions were available and applicable?
- Did it infer a convention rather than verify it?
- Did it run tests, or merely predict that they would pass?
- Does a fresh session reach the same result?

## Practical failure case
Suppose the assistant confidently says *“all database access uses repository pattern X”*. The repository was recently migrated to pattern Y. If the assistant relied on older conversational context, the answer can be fluent and wrong. A robust workflow demands source verification, relevant file paths, and a test or review gate.

## Engineering takeaway
Treat assistant knowledge as a **claim requiring provenance**, not as magical accumulation. Put stable conventions in versioned documents, keep them concise, and test whether the assistant actually uses them.

## Check your understanding
1. Why is a file existing in the repository not equivalent to being in the active model context?
2. How would you distinguish retained session context from repository retrieval?
3. Which evidence would convince you that a new instruction file improved correctness rather than merely making answers longer?

## Next
Run `../labs/01-context-persistence-experiment.md`, document baseline results, and challenge your initial understanding.

## Research / verification notes
Prior to publish, add current official Anthropic, OpenAI and GitHub documentation links with access dates for each product-specific claim. This lesson deliberately uses a vendor-neutral model.
