# Architecture (Visual Proof)

This page provides high-signal architecture visuals that reflect how I design production-grade platforms: secure-by-default, observable, upgrade-ready, and operationally mature.

---

## 1) Reference Cloud Platform (AWS + EKS)

```mermaid
flowchart TB
  Dev[Developers] -->|PRs| Git[GitHub Repo]
  Git --> CI[CI Pipeline\n(Build/Test/Scan)]
  CI --> Reg[Container Registry]
  CI --> Helm[Helm/Manifests]
  CI --> IaC[Terraform\n(VPC/EKS/IRSA)]

  IaC --> AWS[AWS Account]
  AWS --> VPC[VPC\n(private/public subnets)]
  VPC --> EKS[EKS Cluster]
  EKS --> Ingress[Ingress / ALB]
  Ingress --> Svc[Services]
  Svc --> Pods[Pods]

  EKS --> Obs[Observability\n(Prometheus/Grafana/Datadog)]
  Obs --> Alerts[Alerting]
  Alerts --> OnCall[On-call / Incident Response]

  EKS --> Sec[Security Controls\n(IRSA, Network Policies,\nImage Policy, Secrets)]
