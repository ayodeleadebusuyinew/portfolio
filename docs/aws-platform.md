# AWS Platform Engineering (Deep Proof)

This page summarizes how I design, automate, secure, and operate AWS platforms in production — with Kubernetes (EKS) at the core where container orchestration is required.

---

## 1) AWS Foundations (Network + Accounts)
- AWS Platform: aws-platform.md

### VPC architecture patterns
- Segmented subnets (public/private), route tables, IGW/NAT
- Private connectivity via **VPC endpoints** (S3/ECR/CloudWatch/etc.)
- Security posture with **security groups** and controlled egress

### Environment strategy
- Repeatable environments via **Terraform modules**
- Separation by account and/or VPC boundaries for blast-radius control

---

## 2) EKS Platform (Kubernetes on AWS)

### Cluster design
- Managed node groups, capacity strategy (on-demand/spot where appropriate)
- Ingress via **ALB** and Kubernetes ingress controller
- Add-ons: metrics-server, external-dns (Route53), cert-manager (ACM integration patterns)

### IAM for workloads (IRSA)
- Workload-level permissions using **IAM Roles for Service Accounts**
- No sharing node IAM credentials across workloads
- Clear least-privilege policies per service

---

## 3) Security-by-default on AWS

### Identity and auditability
- IAM least privilege + role-based access
- **CloudTrail** for audit logs, plus centralized logging patterns
- KMS encryption for sensitive data

### Secrets & config
- Secrets Manager or SSM Parameter Store (no secrets in Git)
- Rotation discipline and access boundaries

---

## 4) Observability on AWS (Ops readiness)

- CloudWatch metrics + logs for baseline visibility
- Alerting tied to customer impact (error rate/latency/saturation)
- SLO-style thinking with burn-rate style alerts where applicable
- Integration with Datadog/Prometheus/Grafana for deeper service telemetry

---

## 5) Reliability & Cost (practical platform ownership)

- Right-sizing requests/limits and node capacity to reduce waste
- Autoscaling strategies and safe deployment patterns
- Reduce MTTR via runbooks + rollback playbooks + postmortems
- Cost-aware design: private endpoints, managed services, and avoiding “always-on” waste
