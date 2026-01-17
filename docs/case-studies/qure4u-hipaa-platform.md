# HIPAA-Compliant AWS + EKS Platform Delivery (Healthcare SaaS)

## Executive summary
Built and operated a secure-by-default AWS + Kubernetes platform supporting healthcare workflows, focusing on repeatability, audit readiness, and production reliability.

## Context
Healthcare SaaS requires:
- Strong access controls and auditability
- Secure delivery practices (no “cowboy deploys”)
- Operational readiness (monitoring, incident response, rollback discipline)

## What I owned (high level)
- **Platform foundations**: AWS networking patterns, environment separation, secure defaults
- **Kubernetes operations**: upgrades, scaling, release safety, workload reliability
- **Infrastructure as Code**: reusable Terraform modules for repeatable environments
- **CI/CD**: build → test → scan → deploy → verify → rollback patterns
- **Observability**: dashboards, alerting, and on-call readiness

## Architecture decisions (what matters)
- **IRSA** for workload access (least privilege per service)
- **Private workload patterns** where appropriate + controlled ingress/egress
- **Progressive delivery** (canary/blue-green) with rollback readiness
- **Operational guardrails**: runbooks, incident comms templates, postmortems

## Outcomes (replace with your real metrics as you like)
- Reduced manual ops and “snowflake” deployments
- Faster recovery through rollback playbooks and standardized triage
- Improved deployment confidence with scanning + gates + verification

## Proof artifacts
- Architecture diagrams (see **Architecture** tab)
- Runbooks and incident response templates (see **Runbooks** tab)
