# Review Checklist Index

Use this file as the master checklist before sending any report, proposal, or handoff document to a client.

## Global Review

- [ ] No secrets, tokens, passwords, or connection strings are included.
- [ ] No confidential client identifiers are exposed unless explicitly allowed.
- [ ] Findings are supported by evidence.
- [ ] Assumptions are labeled clearly.
- [ ] Unsupported numbers, savings, or performance claims were removed.
- [ ] The tone is professional and client-ready.

## Repository Review

- [ ] Architecture concerns are clearly explained.
- [ ] Code-level findings include evidence.
- [ ] Recommendations are practical.
- [ ] Quick wins are separated from larger refactors.
- [ ] Missing information is documented.

## DevOps Review

- [ ] Pipeline findings are based on actual YAML or workflow notes.
- [ ] Deployment risks are prioritized.
- [ ] Secret handling is reviewed.
- [ ] Rollback and environment risks are called out.
- [ ] Quality gates are evaluated.

## Azure Review

- [ ] Cost risks are framed as opportunities unless billing data is available.
- [ ] Reliability risks include operational impact.
- [ ] Monitoring and alerting gaps are clear.
- [ ] App Insights, Cosmos DB, Service Bus, and container resources are reviewed where applicable.
- [ ] Required metrics for validation are listed.

## Report Review

- [ ] Executive summary is clear for non-technical stakeholders.
- [ ] Detailed findings are useful for technical leads.
- [ ] Roadmap has phases.
- [ ] Next steps are concrete.
- [ ] Risks and assumptions are included.

## Proposal Review

- [ ] Scope is explicit.
- [ ] Out-of-scope items are explicit.
- [ ] Deliverables are measurable.
- [ ] Timeline is realistic.
- [ ] Pricing assumptions are clear.
- [ ] Client responsibilities are listed.

## Handoff Review

- [ ] Completed work is listed.
- [ ] Modified files/components are documented.
- [ ] Validation steps are clear.
- [ ] Deployment steps are clear.
- [ ] Rollback notes are included.
- [ ] Known limitations and open items are transparent.
