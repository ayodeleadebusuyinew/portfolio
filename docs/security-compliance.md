# Security & Compliance

I build platforms with security controls embedded into the default delivery path — so teams ship faster safely.

## Baseline security controls
- **Least privilege IAM** with role-based access and scoped policies
- **IRSA** for Kubernetes workloads (no shared node credentials)
- **Encryption** at rest (KMS-ready patterns) and TLS in transit
- **Segmentation**: private workloads where needed, controlled ingress/egress
- **Secrets discipline**: no plaintext secrets, rotation expectations, boundary-based access

## DevSecOps in the pipeline
- **SAST + dependency scanning** as required checks
- **Container image scanning** with triage + remediation workflow
- **IaC scanning** (tfsec/checkov-style) with actionable failures
- **Change traceability**: approvals, commits, releases, and audit-friendly history

## Compliance readiness (practical)
- Evidence-by-design via:
  - CI/CD logs + build artifacts
  - IaC state and versioned changes
  - Release notes + change approvals
  - Runbooks + incident timelines + postmortems
