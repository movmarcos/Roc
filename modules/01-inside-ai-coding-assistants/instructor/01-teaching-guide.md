# Instructor guide — Lesson 1.1

**Teaching thesis:** apparent memory is an outcome to investigate, not a mechanism to assume.

## Suggested 45-minute session

- 0–10 min: ask learners why their assistant seems to know a repo.
- 10–20 min: explain model weights, working context, retrieval, persisted notes and tools.
- 20–30 min: whiteboard a stale architectural decision and trace information sources.
- 30–40 min: demonstrate evidence-first repository exploration.
- 40–45 min: brief lab and scoring rubric.

## Misconceptions to correct

- “The model retrains itself on every conversation.”
- “A large context window guarantees all important files were read.”
- “A confident explanation proves the model saw the relevant code.”
- “An assistant's output is a verified test result.”

## Assessment rubric

**Excellent:** identifies distinct state sources and verifies the authoritative repo state; compares reproducible runs, notes confounders, and recommends maintenance practices.

**Adequate:** identifies at least three context mechanisms and provides a plausible source map; results are captured but have limited experimental controls.

**Needs revision:** attributes observed accuracy to unspecified memory without evidence or asserts cost savings without measured usage.

## Commercial production checklist

Record a clean-room demo repo; script the stale-context example; publish an anonymised completed worksheet; verify any tool-specific screenshots and command behaviour shortly before release. Keep students' proprietary repositories out of public recordings.
