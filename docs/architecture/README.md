# Architecture Guidelines

## Purpose

This directory contains architecture documentation for the project.

Architecture MUST reflect actual requirements. This template does not
prescribe a specific programming language, framework, or architecture style.

## Architecture Documentation

When documenting an architecture, describe the relevant items:

1. System purpose and scope.
2. High-level components and responsibilities.
3. Component dependencies and communication.
4. Data flow and storage.
5. External services and integrations.
6. Security boundaries and sensitive data.
7. Deployment and runtime environment.
8. Important constraints and trade-offs.

## Design Guidelines

- Prefer clear module boundaries.
- Keep business logic independent from infrastructure where practical.
- Avoid unnecessary coupling.
- Introduce abstractions only when they provide real value.
- Document important decisions in `docs/decisions/`.
- Update architecture documentation when significant design changes occur.

## Project-Specific Architecture

The actual architecture MUST be defined during the Spec Kit planning stage
and updated as the project evolves.
