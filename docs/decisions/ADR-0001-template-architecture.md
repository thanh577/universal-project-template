# ADR-0001: Universal Project Template Architecture

- Status: Accepted
- Date: 2026-11-04

## Context

The repository is intended to serve as a reusable starting point for different
software projects.

Projects may use different programming languages, frameworks, deployment
targets, and architectural styles.

The template must provide common engineering standards without forcing every
project into the same technology stack.

## Decision

Adopt a language-agnostic repository structure with these shared components:

- `.specify/`: specification-driven development infrastructure.
- `AGENTS.md`: shared instructions for AI coding agents.
- `docs/`: architecture and technical decision documentation.
- `scripts/`: reusable development automation.
- `src/`: application source code.
- `tests/`: automated tests.
- `.github/workflows/`: optional CI automation.

Hermes Spec Kit skills are installed globally and are not copied into every
project by default.

Project-specific technology choices are made during specification and
planning.

## Consequences

### Positive

- The template can support multiple technology stacks.
- Shared engineering and security principles remain consistent.
- Spec Kit infrastructure can be reused across projects.
- AI agents have a common instruction source.

### Trade-offs

- Each new project must define its own source layout and toolchain.
- CI workflows must be added according to the selected technology.
- Some directories may remain unused in small projects.

## Alternatives Considered

### Enforce a single technology stack

Rejected because it would limit reuse across different project types.

### Duplicate all Hermes skills into every repository

Rejected because global installation avoids unnecessary duplication and
simplifies skill maintenance.
