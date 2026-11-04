# Universal Project Template Constitution

## Core Principles

### I. Clear Architecture and Modularity

Every project MUST have a clearly defined purpose, architecture, and
responsibility boundaries.

- Separate business logic from presentation, infrastructure, and external
  integrations where appropriate.
- Modules MUST have clear responsibilities and well-defined interfaces.
- Avoid unnecessary coupling and circular dependencies.
- Choose architecture based on actual project requirements, not trends.
- Document important architectural decisions.

### II. Simplicity and Maintainability

Prefer the simplest solution that correctly satisfies the requirements.

- Follow YAGNI: do not implement speculative features.
- Avoid unnecessary abstractions, dependencies, and configuration.
- Reuse existing project conventions before introducing new ones.
- Write readable, consistent, maintainable code.
- Refactor when complexity makes future changes unnecessarily difficult.

### III. Test-Driven Quality

Testing MUST be considered throughout development.

- Define acceptance criteria before implementing significant features.
- Write or update tests for new behavior and bug fixes.
- Run relevant tests after implementation.
- Fix regressions before declaring work complete.
- Use unit, integration, and end-to-end tests where appropriate.
- Do not claim a test passed unless it was actually executed successfully.

### IV. Security and Privacy by Design

Security MUST be considered in architecture, implementation, and deployment.

- Never commit API keys, passwords, tokens, or private credentials.
- Use environment variables or an appropriate secrets-management mechanism.
- Validate and sanitize untrusted input.
- Apply least-privilege access.
- Avoid exposing sensitive information in logs or error messages.
- Review dependencies and external integrations for security risks.
- Obtain approval before destructive operations or actions with significant
  security, financial, or operational consequences.

### V. Documentation and Knowledge Sharing

Every project MUST provide documentation appropriate to its complexity.

- Maintain a README explaining purpose, prerequisites, installation,
  configuration, usage, and development.
- Provide an .env.example when environment variables are required.
- Document public interfaces, important workflows, and non-obvious behavior.
- Update documentation when implementation or configuration changes.
- Record significant architectural decisions when useful.

### VI. Portability and Reproducibility

Projects SHOULD be reproducible across supported development environments.

- Document required runtimes, tools, and versions.
- Use appropriate dependency manifests and lockfiles.
- Provide repeatable setup, build, test, and run instructions.
- Avoid machine-specific absolute paths and undocumented local assumptions.
- Support the target operating systems and deployment environments
  declared by each project's specification.

### VII. Observability and Reliability

Applications SHOULD provide enough diagnostic information to understand
their behavior and investigate failures.

- Use appropriate logging and error handling.
- Make failures explicit rather than silently ignoring them.
- Avoid logging secrets or sensitive user data.
- Define health checks and recovery behavior when relevant.
- Consider performance and resource usage according to actual requirements.

### VIII. Human Approval and Agent Responsibility

AI agents and automated tools MUST operate within the project's scope.

- Follow the project's specification, plan, tasks, and constitution.
- Inspect existing code and conventions before making changes.
- Do not fabricate command results, test results, or implementation status.
- Ask for approval before destructive operations, irreversible changes,
  production deployment, external publication, or unexpected costs.
- Explain important trade-offs when requirements are ambiguous.
- Keep changes focused and report what was changed and verified.

## Technical and Project Constraints

### Technology Selection

- Select languages, frameworks, databases, and tools according to project
  requirements and documented constraints.
- Do not impose a universal programming language or framework.
- Prefer actively maintained and well-supported dependencies.
- Avoid adding dependencies when the existing platform can solve the problem.
- Record important technology choices and their rationale.

### Repository Standards

- Use a consistent directory structure appropriate to the project.
- Keep generated files, build artifacts, caches, and local secrets out of
  version control unless explicitly required.
- Provide a .gitignore suitable for the selected technology stack.
- Keep configuration separate from application logic.
- Use meaningful names and consistent formatting.

### Compatibility and Performance

- Define supported platforms, runtime versions, and performance expectations
  in each project's specification.
- Avoid premature optimization.
- Validate performance-sensitive behavior when requirements justify it.
- Do not claim compatibility without appropriate verification.

## Development Workflow

### 1. Understand

- Inspect the existing repository and development environment.
- Identify project goals, constraints, and stakeholders.
- Clarify ambiguous or conflicting requirements.

### 2. Specify

- Write a specification describing user needs and expected behavior.
- Define acceptance criteria and relevant edge cases.
- Identify security, compatibility, and operational constraints.

### 3. Plan

- Select an appropriate architecture and technology stack.
- Identify dependencies, risks, and integration points.
- Break work into small, verifiable tasks.

### 4. Implement

- Follow the approved specification and implementation plan.
- Make focused changes.
- Add or update tests and documentation.
- Request approval when an operation requires human authorization.

### 5. Verify

- Run relevant tests, static checks, and build commands.
- Review security, error handling, and regressions.
- Confirm acceptance criteria.
- Report any checks that could not be performed.

### 6. Deliver

- Summarize implemented functionality and changed files.
- Report verification results honestly.
- Document known limitations and follow-up work.
- Provide clear instructions for running or deploying the result.

## Quality Gates

A feature or project milestone MUST NOT be declared complete until:

- Its agreed acceptance criteria have been addressed.
- Relevant tests and checks have been executed.
- No known critical regression remains unresolved.
- Required documentation has been updated.
- Security-sensitive configuration has been handled appropriately.
- Remaining limitations are explicitly reported.

Exceptions MUST be explained and documented.

## Governance

This Constitution governs project specifications, plans, implementation,
testing, reviews, and agent behavior.

- All contributors and AI agents MUST follow these principles.
- Project-specific requirements MAY add stricter rules but MUST NOT silently
  weaken security or approval requirements.
- Any exception MUST include its rationale, scope, and known risks.
- Amendments MUST be documented and reflected in the project workflow.
- When requirements conflict with this Constitution, the conflict MUST be
  identified and resolved before implementation proceeds.

**Version**: 1.0.0
**Ratified**: 2026-11-04
**Last Amended**: 2026-11-04
