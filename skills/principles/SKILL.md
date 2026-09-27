---
name: principles
description: "pstack engineering principles: when to delete vs add, how to model data, where guards go, how to verify, debug, sequence, and delegate. Use before designing or refactoring code, writing tests or types, debugging, planning multi-step or migration work, declaring a task done, or when a fix has failed twice."
---

# Principles

Match the situation to an entry below, then read that reference file in full before applying it. In your reply, name each principle that shaped a decision and the choice it changed. Cite only principles whose reference file you read this session.

Cross-links inside a reference file look like `../principle-<name>/SKILL.md`. They point to `references/<name>.md` in this skill.

## Core

- **Laziness Protocol** ([references/laziness-protocol.md](references/laziness-protocol.md)). Refactoring, sizing a diff, or tempted to add abstractions, layers, or signal threading. Bias to deletion and the smallest change that solves the problem.
- **Foundational Thinking** ([references/foundational-thinking.md](references/foundational-thinking.md)). Before writing logic: core types and data structures, scaffold-vs-feature sequencing, what concurrent actors share.
- **Redesign from First Principles** ([references/redesign-from-first-principles.md](references/redesign-from-first-principles.md)). Integrating a new requirement into an existing design. Redesign as if it had been foundational from day one.
- **Attack the Premise** ([references/attack-the-premise.md](references/attack-the-premise.md)). Two or more fixes that share one premise have failed the same gate. Take a census of which actors hold the imbalance before the next fix, then question the premise.
- **Subtract Before You Add** ([references/subtract-before-you-add.md](references/subtract-before-you-add.md)). Sequencing an addition, refactor, or rewrite. Remove dead weight first, then build on the simpler base.
- **Minimize Reader Load** ([references/minimize-reader-load.md](references/minimize-reader-load.md)). Reviewing or shaping code that's hard to trace. Count layers and hidden state, collapse one-caller wrappers, shrink mutable scope.
- **Outcome-Oriented Execution** ([references/outcome-oriented-execution.md](references/outcome-oriented-execution.md)). Planned rewrites and migrations with explicit phase boundaries. Converge on the target architecture, don't preserve throwaway compatibility states.
- **Experience First** ([references/experience-first.md](references/experience-first.md)). Product, UX, or feature-scope tradeoffs. Choose user delight over implementation convenience.
- **Exhaust the Design Space** ([references/exhaust-the-design-space.md](references/exhaust-the-design-space.md)). A novel interaction or architectural decision with no precedent. Build 2-3 competing prototypes and compare before committing.
- **Build the Lever** ([references/build-the-lever.md](references/build-the-lever.md)). Any non-trivial work. Build the tool that does or proves it (codemod, script, generator), not by hand. The tool is the artifact a reviewer reruns.

## Architecture

- **Model the Domain** ([references/model-the-domain.md](references/model-the-domain.md)). Stateful logic, or code that branches a lot or repeats a shape assumption across files. Encode the domain in a structure instead of scattered conditionals.
- **Boundary Discipline** ([references/boundary-discipline.md](references/boundary-discipline.md)). Wiring validation, error handling, or framework adapters. Guards at system boundaries, trust internal types, keep business logic pure.
- **Type System Discipline** ([references/type-system-discipline.md](references/type-system-discipline.md)). Designing types or a signature in any typed language. Make illegal states unrepresentable, brand primitives, parse external data at boundaries.
- **Make Operations Idempotent** ([references/make-operations-idempotent.md](references/make-operations-idempotent.md)). Commands, lifecycle steps, or loops that run amid crashes and retries. Converge to the same end state.
- **Migrate Callers Then Delete Legacy APIs** ([references/migrate-callers-then-delete-legacy-apis.md](references/migrate-callers-then-delete-legacy-apis.md)). New internal API while old callers exist. Migrate and delete in one wave.
- **Separate Before Serializing Shared State** ([references/separate-before-serializing-shared-state.md](references/separate-before-serializing-shared-state.md)). Concurrent actors might write the same file, branch, key, or object. Eliminate the sharing first.

## Verification

- **Prove It Works** ([references/prove-it-works.md](references/prove-it-works.md)). After a task, before declaring done. Verify against the real artifact, not a proxy or "it compiles". If the project has a `verify-*` skill, use it.
- **Fix Root Causes** ([references/fix-root-causes.md](references/fix-root-causes.md)). Debugging. Reproduce first, ask why until you reach the root cause, fix it there.
- **Sequence Work into Verifiable Units** ([references/sequence-verifiable-units.md](references/sequence-verifiable-units.md)). Multi-step work and how you stack commits and PRs. Small units that each end in a check, verified before the next.
- **Test Behavior, Not Implementation** ([references/test-behavior-not-implementation.md](references/test-behavior-not-implementation.md)). Writing, changing, or keeping a test. Call the code the way its users do and assert against a literal expected value.

## Delegation

- **Guard the Context Window** ([references/guard-the-context-window.md](references/guard-the-context-window.md)). Large outputs, long files, repeated reads, fan-out planning. Route bulk to subagents, keep summaries in the main thread.
- **Never Block on the Human** ([references/never-block-on-the-human.md](references/never-block-on-the-human.md)). Tempted to ask "should I do X?" on reversible work. Proceed, present the result, let the human course-correct.

## Meta

- **Encode Lessons in Structure** ([references/encode-lessons-in-structure.md](references/encode-lessons-in-structure.md)). Writing the same instruction a second time. Encode it as a lint, flag, runtime check, or script instead of more text.
