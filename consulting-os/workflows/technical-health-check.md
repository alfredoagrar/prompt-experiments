# Workflow: .NET / Azure Technical Health Check

## Purpose

Use this workflow to deliver a focused technical assessment for a client with a .NET and Azure-based system.

## Step 1: Discovery

Collect the initial context:

- What problem is the client trying to solve?
- What system or workflow is affected?
- What stack is currently used?
- What hurts most: cost, reliability, delivery speed, bugs, performance, or maintainability?
- What artifacts can the client provide?

Run the **Intake Agent**.

Expected output:

- Consulting brief
- Missing information
- Recommended next step
- Follow-up questions

## Step 2: Artifact Collection

Request only what is required for the assessment:

- Repository access or selected files
- File tree
- Pipeline YAML
- Dockerfiles
- Bicep or Terraform files
- Architecture diagram or notes
- Azure resource inventory
- Logs or screenshots
- Known incidents or release pain points

## Step 3: Repository Review

Run the **Repository Audit Agent** with:

- Repository summary
- File tree
- Key files
- Known issues
- Client goal

Expected output:

- Repository findings
- Maintainability risks
- Architecture concerns
- Quick wins
- Open questions

## Step 4: DevOps and Azure Review

Run the **DevOps & Azure Audit Agent** with:

- Pipeline files
- Docker files
- IaC files
- Azure resource inventory
- Architecture notes
- Monitoring configuration
- Known release issues

Expected output:

- Pipeline maturity score
- Cost risk level
- Reliability risk level
- Findings
- Quick wins
- Metrics needed for validation

## Step 5: Consultant Review

Before sending anything to the client:

- Remove false positives.
- Verify that each finding has evidence.
- Remove confidential values.
- Prioritize findings based on business impact.
- Convert technical noise into client-relevant recommendations.

## Step 6: Report Generation

Run the **Report & Proposal Agent** in `report` mode.

Use the `templates/technical-health-check-report.md` structure.

Expected output:

- Executive summary
- Scope
- Methodology
- Key findings
- Detailed findings
- Quick wins
- Roadmap
- Risks and assumptions
- Next steps

## Step 7: Proposal Generation

If the client wants implementation support, run the **Report & Proposal Agent** in `proposal` mode.

Use the `templates/proposal-template.md` structure.

Expected output:

- Objectives
- Scope of work
- Deliverables
- Timeline
- Pricing options
- Assumptions
- Out-of-scope items
- Next steps

## Step 8: Delivery

After implementation work, use the `templates/handoff-document-template.md` structure.

Expected output:

- Delivery summary
- Completed work
- Modified files or components
- Validation steps
- Deployment steps
- Rollback notes
- Known limitations
- Open items
- Recommended next steps

## Recommended Pricing

| Package | Price Range | Best For |
|---|---:|---|
| Starter Health Check | $8,000-$12,000 MXN | Initial validation or small systems |
| Professional Health Check | $18,000-$30,000 MXN | Deeper assessment across repo, CI/CD, and Azure |
| Implementation Support | Quoted separately | Teams that want fixes implemented |

## Definition of Done

The health check is complete when:

- Findings are evidence-based.
- Priorities are clear.
- Quick wins are actionable.
- Assumptions are documented.
- The client has a concrete next step.
- Sensitive information has been removed.
