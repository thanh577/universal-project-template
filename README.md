# Universal Project Template

A reusable, language-agnostic foundation for software projects.

## Included

- Spec Kit for specification-driven development.
- Hermes Agent integration through globally installed skills.
- Constitution defining engineering and security principles.
- Shared AI Agent instructions in `AGENTS.md`.
- Documentation, source, tests, and scripts directories.
- Generic Git ignore and EditorConfig configuration.

## Requirements

Install and configure the tools required by the selected project technology.

Spec Kit CLI and Hermes Agent should be available in the development
environment.

## Starting a New Project

1. Copy or clone this template into a new project directory.
2. Update this README with the new project's purpose and instructions.
3. Review `AGENTS.md` and `.specify/memory/constitution.md`.
4. Open the project directory with Hermes Agent.
5. Start the Spec Kit workflow with `/speckit-specify`.
6. Continue with clarification, planning, task generation, and implementation.

## Project Structure

- `.specify/`: specifications, templates, scripts, and project constitution.
- `.hermes/`: optional project-local Hermes configuration; excluded from Git.
- `docs/`: architecture and technical documentation.
- `scripts/`: development and automation scripts.
- `src/`: application source code.
- `tests/`: automated tests.
- `AGENTS.md`: instructions for AI coding agents.

## Technology Choices

This template does not enforce a programming language or framework.
Choose technologies according to each project's requirements and document
the decisions in its specification and implementation plan.
