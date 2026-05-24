# Bicep IaC Review Checklist

Use this checklist when reviewing Azure infrastructure-as-code written in Bicep.

The goal is to identify risks around maintainability, deployment reliability, environment consistency, security, cost, and operational readiness.

## 1. Scope

Review the following artifacts when available:

- Main Bicep files
- Bicep modules
- Parameter files
- Deployment scripts
- GitHub Actions or Azure DevOps pipeline files
- Azure resource inventory
- Naming convention documentation
- Environment strategy documentation
- Existing deployment errors or logs

## 2. Core Review Areas

### Structure and Maintainability

- [ ] Bicep files are organized by responsibility.
- [ ] Reusable resources are extracted into modules.
- [ ] Module names are clear and consistent.
- [ ] Resource names follow a documented naming convention.
- [ ] Parameters are grouped logically.
- [ ] Outputs are meaningful and not excessive.
- [ ] Hardcoded values are avoided where parameters or variables are appropriate.
- [ ] Complex expressions are readable and documented when needed.

### Parameters and Environment Strategy

- [ ] Environment-specific values are passed through parameter files or pipeline variables.
- [ ] Parameter names are clear and consistent.
- [ ] Secure values use `@secure()` where appropriate.
- [ ] Defaults are safe and do not accidentally target production.
- [ ] Allowed values are used for constrained parameters where appropriate.
- [ ] Existing environments can be redeployed without manual edits.

### Resource Naming and Tagging

- [ ] Resources follow a consistent naming convention.
- [ ] Environment, workload, region, and ownership are reflected where appropriate.
- [ ] Tags include owner, environment, cost center, application, and criticality where applicable.
- [ ] Tags are applied consistently across modules and child resources.

### Security and Secrets

- [ ] Secrets are not hardcoded in Bicep files or parameter files.
- [ ] Sensitive parameters are marked with `@secure()`.
- [ ] Key Vault is used for secret references where appropriate.
- [ ] Managed identities are preferred over static credentials.
- [ ] RBAC assignments follow least privilege.
- [ ] Role assignments are scoped as narrowly as possible.
- [ ] Public network access is disabled where not required.
- [ ] Diagnostic data does not expose sensitive information.

### Reliability and Idempotency

- [ ] Deployments are idempotent.
- [ ] Existing resources are referenced using the `existing` keyword where appropriate.
- [ ] Dependencies are explicit only when necessary.
- [ ] Implicit dependencies are used when possible.
- [ ] Resource deployment order is predictable.
- [ ] Redeployment does not unintentionally reset critical settings.
- [ ] Modules can be deployed repeatedly without drift or failure.

### Cost Control

- [ ] Expensive SKUs are intentional and documented.
- [ ] Autoscaling is configured where appropriate.
- [ ] Log Analytics and Application Insights ingestion risks are considered.
- [ ] Cosmos DB throughput configuration is reviewed.
- [ ] AKS or container resource sizing is reviewed.
- [ ] Unused or orphaned resources are not created by default.
- [ ] Non-production environments use cost-conscious SKUs.

### Observability and Diagnostics

- [ ] Diagnostic settings are configured for critical resources.
- [ ] Logs are routed to the correct Log Analytics workspace or monitoring destination.
- [ ] Application Insights is connected where appropriate.
- [ ] Alerts are defined for critical resources.
- [ ] Metric and log retention settings are intentional.
- [ ] Sampling or ingestion controls are considered for high-volume systems.

### Deployment Pipeline Integration

- [ ] Bicep validation runs before deployment.
- [ ] What-if analysis is used before applying changes.
- [ ] Deployments are separated by environment.
- [ ] Pipeline variables are clearly mapped to Bicep parameters.
- [ ] Service connections use least privilege.
- [ ] Deployment outputs are captured when needed.
- [ ] Failed deployments are visible and actionable.

### Cross-Subscription and Cross-Resource References

- [ ] Cross-subscription references are explicit and documented.
- [ ] Existing resources are referenced with correct scope.
- [ ] Resource group and subscription scopes are clear.
- [ ] Role assignments across scopes are reviewed carefully.
- [ ] Dependencies on shared resources are documented.

### Azure Policy and Governance

- [ ] Bicep templates are compatible with current Azure Policies.
- [ ] Required tags are included.
- [ ] Required diagnostic settings are included.
- [ ] Region restrictions are respected.
- [ ] SKU restrictions are respected.
- [ ] Policy assignment conflicts are known or documented.

## 3. Common Bicep Findings

| Finding | Priority | Why It Matters | Recommendation |
|---|---|---|---|
| Hardcoded environment values | Medium | Reduces portability and increases deployment risk | Move environment-specific values to parameters |
| Missing `@secure()` on sensitive parameters | High | Sensitive values may be exposed in deployment history | Add `@secure()` and use Key Vault references |
| No what-if step in pipeline | Medium | Risk of unexpected infrastructure changes | Add Bicep what-if before deployment |
| Missing tags | Low/Medium | Reduces cost visibility and governance compliance | Add standardized tags to all resources |
| Overly broad role assignment scope | High | Increases security risk | Scope RBAC to the smallest required resource |
| No diagnostic settings | Medium/High | Reduces operational visibility | Add diagnostic settings for critical resources |
| Production and non-production share same SKU strategy | Medium | Can increase unnecessary cost | Use environment-specific SKU parameters |
| Cross-subscription dependency undocumented | Medium | Increases deployment and maintenance risk | Document scope and use explicit `existing` references |

## 4. Bicep Finding Template

```markdown
### Finding: [Title]

**Priority:** Critical / High / Medium / Low / Informational  
**Category:** Security / Cost / Reliability / Maintainability / Observability / Governance  
**Evidence:** [File, module, resource, or parameter reviewed]  
**Impact:** [Why this matters]  
**Recommendation:** [What should be changed]  
**Estimated Effort:** Small / Medium / Large  
**Expected Benefit:** [Cost control, safer deployment, better governance, improved observability, etc.]
```

## 5. Recommended Bicep Review Prompt

```text
You are reviewing Azure infrastructure-as-code written in Bicep.

Analyze the provided Bicep files, parameter files, and deployment pipeline context.

Focus on:
- Maintainability
- Module structure
- Parameter strategy
- Environment consistency
- Secret handling
- Managed identity and RBAC
- Cost risks
- Observability and diagnostic settings
- Deployment reliability
- Cross-subscription or shared-resource references
- Azure Policy and governance compatibility

Do not invent resources or behavior that is not present in the files.

For each finding, include:
- Title
- Priority
- Category
- Evidence
- Impact
- Recommendation
- Estimated effort
- Expected benefit

Clearly list missing information and assumptions.
```

## 6. Minimum Required Inputs for a Good Review

```yaml
bicep_files:
  - main.bicep
  - modules/*.bicep
parameter_files:
  - *.parameters.json
pipeline_files:
  - azure-pipelines.yml
  - .github/workflows/*.yml
azure_context:
  - target subscriptions
  - target resource groups
  - environment names
  - naming convention
  - existing shared resources
known_issues:
  - failed deployments
  - policy conflicts
  - role assignment issues
  - cost concerns
```
