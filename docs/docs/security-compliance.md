# Security & Compliance

I build platforms with security controls embedded into the default path of delivery — so teams ship faster safely.

## Baseline controls
- Least privilege IAM (role-based access, scoped policies, IRSA for Kubernetes workloads)
- Encryption at rest (KMS-ready patterns) and TLS in transit
- Controlled ingress/egress and private workload patterns where applicable
- Secrets discipline (no plaintext secrets; rotation and access boundaries)

## DevSecOps delivery controls
- SAST + dependency scanning as pipeline gates
- Container image scanning and remediation workflow
- IaC scanning (tfsec/checkov patterns) with actionable failures
- Audit-friendly traceability: approvals, change history, release notes

## Compliance readiness (practical)
- “Evidence by design” via CI/CD logs, IaC state, and immutable change history
- Runbooks + incident response discipline aligned to operational readiness
