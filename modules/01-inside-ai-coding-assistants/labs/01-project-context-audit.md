# Lab 1.1 — Project Context Audit

**Goal:** determine whether a coding assistant's apparent project knowledge is attributable to explicit context, retrieval, durable guidance, or unsupported guesses.

**Time:** 60–90 minutes. **Environment:** VS Code + an existing repository + one AI coding assistant. **Safety:** use a separate worktree/branch; do not expose secrets, private customer data, or production credentials.

## Setup

1. Choose a harmless, verifiable architectural question about the repository (e.g. “where does request validation happen?”).
2. Record the correct answer from source files, tests, or configuration independently of the assistant.
3. Define a scoring rubric before making requests: factual correctness (0–3), evidence quality (0–3), uncertainty handling (0–2), and effort/cost (observed, not guessed).
4. Note product, model, relevant settings, repository revision and whether the session is fresh.

## Controlled trials

**A — Existing context:** ask the question in your established working session. Request file-path and line-based evidence. Save the response.

**B — Clean session:** start a fresh session while keeping repository access. Ask exactly the same question. Save the response.

**C — Explicit curated context:** supply a compact architecture summary and only the necessary file references. Ask the same question in a new session.

**D — Adversarial stale context:** on an isolated test copy, provide a clearly labelled *obsolete* architecture note that conflicts with actual current code. Ask the assistant to validate the assertion against the repo. Never inject deceptive content into the real team's live documentation.

For fairness, keep the wording and scoring criteria constant; record differences in tools, instructions, environment and model. Repeat each variant if usage permits. Do not claim causal proof from a single trial.

## Capture observations

Use [`templates/lab-results.md`](../../../templates/lab-results.md) for each variant. Record tool calls, duration, provided context, whether the model cited correct files and whether verification commands ran. Record API token use or metered cost only when the platform actually exposes those values; subscription allowances are not equivalent to token billing.

## Debrief

1. Which session performed best, and what evidence supports that conclusion?
2. Did the assistant state knowledge without providing a verifiable source?
3. Was more context helpful, harmful, or neutral?
4. Which facts should become maintainable repository documentation?
5. Which facts are better fetched just-in-time from code or tools?

## Completion criteria

Submit four results records, a one-page source-of-truth map, and three concrete improvements to context management. At least one improvement must be a proposed deletion or narrowing of unnecessary context, not simply “add more instructions.”
