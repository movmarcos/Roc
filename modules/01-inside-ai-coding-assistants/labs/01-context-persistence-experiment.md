# Lab 01 — Is your assistant remembering or reconstructing?

**Duration:** 60–90 min. **Difficulty:** advanced. **Runs locally in a test branch or disposable repo.**

## Goal
Identify where the assistant obtains project facts, and measure how source documentation changes its accuracy and work required.

## Safety
Use a repository you are authorised to analyse. Remove secrets and confidential content. Never give an agent unattended write access to production. Run experiments on a clean branch; do not commit session transcripts or proprietary prompts to the course repository.

## Setup
Choose three verifiable architecture facts, including one non-obvious convention. Record the correct answer and exact file path/line range in a private worksheet. Choose a factual question whose answer is **not** in a root README, if feasible.

## Experiment matrix

| Trial | Session conditions | Question | Required evidence |
|---|---|---|---|
| A | Existing long-running session | Ask for 3 facts + source files | Answer, inspected files, accuracy |
| B | Fresh session, same repo | Repeat same questions | Answer, inspected files, accuracy |
| C | Fresh session after concise versioned guide | Repeat questions | Answer, consulted guide, accuracy |
| D | Fresh session with a deliberately stale statement in a sandbox copy | Ask assistant to verify against code | Whether discrepancy is detected |

**Important:** vendors may retain session/project data differently. Record exact app/version/settings and restart procedure rather than assuming that “new chat” is a clean reset.

## Procedure
1. Create an isolated working tree/branch and make sure tests pass before changes.
2. Record the three ground-truth facts and their evidence.
3. Run trial A without coaching the assistant. Capture which files it explicitly reads.
4. Start a genuinely fresh session and run trial B with the exact same prompt.
5. Add a short, accurate architecture guide appropriate to the selected product, or a README that the assistant is explicitly instructed to consult; run trial C.
6. In a disposable copy, create a controlled conflict between a guide and the code; run trial D. Restore the repository afterwards.
7. Score outcomes: correct facts (0–3), citations verified (0–3), unsupported claims, interventions, elapsed time, and any available usage/cost data.
8. Write a 200–400 word recommendation: which information should be stored where, and what proof is missing?

## Trial prompt
> Explain three important architecture conventions of this repository. For each, identify the exact source file and the evidence. Explicitly say what you did not verify. Do not change any files.

## Measurement sheet
| Trial | Correct facts / 3 | Verified citations / 3 | Unsupported claims | Time | Usage/cost signal | Notes |
|---|---:|---:|---:|---:|---|---|
| A | | | | | | |
| B | | | | | | |
| C | | | | | | |
| D | | | | | | |

## Interpretation
Better performance in C suggests that the guide helps under the tested conditions; it does **not** independently prove that the product has durable memory, or that the guide will generalise to other repositories. Repeated trials improve confidence.

## Deliverable
A benchmark report, redacted evidence, and a proposed minimal repository knowledge policy.
