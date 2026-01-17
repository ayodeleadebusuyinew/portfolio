# Security & Compliance (DevSecOps Proof)

I design security into delivery pipelines and runtime platforms so teams can ship quickly without weakening controls.

---

## Security pillars
### 1) Identity & access (least privilege)
- IAM roles scoped to workloads (IRSA on EKS)
- RBAC mapped by namespace and role
- Break-glass access audited and time-bounded

### 2) Secrets & encryption
- Secrets stored in managed secret systems (not in repos)
- Encryption in transit (TLS) and at rest (KMS)
- Key rotation and access logging

### 3) Supply chain security
- Dependency scanning (SCA)
- Container image scanning
- Signed artifacts / provenance where available
- SBOM generation in CI for critical services

### 4) Infrastructure as Code controls
- IaC scanning (Terraform checks)
- Policy-as-code gates for risky resources (public S3, open SGs, wildcard IAM)
- Mandatory tagging, logging, encryption defaults

### 5) Runtime hardening
- Namespace isolation + network policies
- Pod security controls, non-root containers, readonly FS where possible
- Ingress protections (WAF, rate limiting) when appropriate

---

## CI/CD security gates (release safety)
**Build → Scan → Approve → Deploy**
- Block deploy on critical findings (configurable severity policy)
- Canary releases with SLO checks + rollback
- Audit trail preserved: commits, artifacts, approvals, deployments

---

## Compliance posture (practical mapping)
### HIPAA / SOC2 style controls I implement
- **Access control:** least privilege, MFA, RBAC
- **Audit logging:** centralized logs, immutable retention
- **Change management:** PR reviews, pipeline approvals, deployment tracking
- **Incident response:** defined playbooks + postmortems + action items
- **Data protection:** encryption, secrets management, controlled egress

---

## Evidence artifacts (what reviewers can check)
- Runbooks: incident response, triage, rollback, postmortem template
- Architecture: secure EKS + delivery + observability diagrams
- Projects: pipelines and IaC patterns that align with these controls
