# Freelance Consulting OS

A prompt-driven operating system for running a solo technical consulting practice focused on .NET, Azure, DevOps, cloud optimization, and enterprise integrations.

The goal is not to replace technical judgment. The goal is to make consulting delivery faster, more consistent, and easier to package.

## MVP Agent Set

1. Intake Agent
2. Repository Audit Agent
3. DevOps & Azure Audit Agent
4. Report & Proposal Agent

## Core Workflow

```text
Client message or discovery notes
  -> Intake Agent
  -> Repository Audit Agent
  -> DevOps & Azure Audit Agent
  -> Report & Proposal Agent
  -> Consultant review
  -> Client deliverable
```

## Recommended First Service

**.NET / Azure Technical Health Check**

A focused technical assessment for .NET and Azure-based systems. The service identifies risks, quick wins, cost optimization opportunities, CI/CD gaps, observability issues, and maintainability improvements.

## Deliverables

- Consulting brief
- Technical findings report
- Prioritized quick wins
- Implementation roadmap
- Optional implementation proposal

## Rules for Every Agent

- Do not invent facts, files, costs, metrics, incidents, or client context.
- Separate confirmed information from assumptions.
- Flag missing information clearly.
- Avoid exposing secrets or sensitive client data.
- Produce structured, actionable outputs.
- The consultant remains the final decision-maker.

## Folder Structure

```text
consulting-os/
  agents/
  templates/
  checklists/
  workflows/
  examples/
```
