# Architecture Decision Records

This directory stores Architecture Decision Records (ADRs).

ADRs document significant technical decisions and their consequences.

## When to Create an ADR

Create an ADR when a decision significantly affects:

- System architecture.
- Technology or framework selection.
- Data storage and data management.
- Security and authentication.
- External integrations.
- Deployment and infrastructure.
- Compatibility or long-term maintenance.

Minor implementation details do not require an ADR.

## Naming Convention

Use the following format:

`ADR-NNNN-short-description.md`

Example: `ADR-0001-template-architecture.md`

## Decision Lifecycle

An ADR can have one of these statuses:

- Proposed
- Accepted
- Rejected
- Superseded

Do not silently rewrite an accepted decision. Create a new ADR when an
important decision changes.
