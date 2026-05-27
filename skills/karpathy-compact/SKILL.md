---
name: karpathy-compact
description: Use when writing, debugging, reviewing, or refactoring code. Enforce context-first, minimal, surgical, testable changes; avoid overengineering, speculative abstractions, dead code, and unverified assumptions. Do not use for pure explanation or non-code tasks.
---

# Karpathy Compact

Bias toward correctness, simplicity, and reviewability. Apply lightly for trivial edits; strictly for risky, ambiguous, or multi-file work.

## 1. Orient

- Read relevant code, tests, errors, and AGENTS.md before editing.
- Surface assumptions only when they affect code.
- Ask only when blocked, unsafe, destructive, or valid interpretations require different code; otherwise make the smallest reversible assumption, name it, and continue.

## 2. Simplify

Minimum code. Nothing speculative.

- No extra features, single-use abstractions, new dependencies, config, APIs, migrations, or broad refactors unless required.
- No defensive code for states made impossible by explicit types, invariants, or control flow.
- If 200 lines could be 50, rewrite it. If a senior engineer would call it overcomplicated, simplify.

## 3. Cut Surgically

- Touch only what the request requires; match existing style and architecture.
- Every changed line must trace to the request.
- Clean up only your mess: remove imports, variables, tests, or helpers made unused by your change.
- Mention unrelated dead code or debt; do not fix or delete it unless asked.

## 4. Preserve Guarantees

- Do not weaken validation, security, error boundaries, concurrency guarantees, public behavior, compatibility, or documented contracts.
- Prefer clear local code over clever code.
- If the solution grows, delete, localize, or reuse before adding structure.

## 5. Verify

Define success before patching.

- Bugs or behavior changes: reproduce or characterize -> add/update the narrowest useful test when practical -> patch minimally -> run the narrowest relevant check -> run broader checks only when risk justifies cost.
- Multi-step work: `Step -> verify: check`.

## 6. Report Honestly

Scale the report to the size and risk of the change.

- Report what changed and why, files changed, checks run/failed/skipped, assumptions, and remaining risk.
- Report only checks actually run; if a check failed or was not run, say so.
