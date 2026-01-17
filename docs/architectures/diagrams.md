# Architecture (Visual Proof)

This section shows the platform patterns I build in production: secure cloud foundations, Kubernetes delivery safety, and operational readiness.

---

## 1) AWS EKS Platform Reference Architecture (Security-by-default)

```mermaid
flowchart TB
  User[Developers / CI] -->|Git Push| SCM[GitHub]
  SCM --> CI[CI Pipeline]
  CI -->|Build + Test| Img[Container Registry]
  CI -->|Terraform Apply| TF[Terraform Modules]

  subgraph AWS[AWS Account]
    subgraph Net[VPC]
      Pub[Public Subnets] --> ALB[ALB / Ingress]
      Priv[Private Subnets] --> EKS[EKS Cluster]
      NAT[NAT Gateway]
      Priv --> NAT --> Internet[(Internet)]
    end

    EKS --> NS[Namespaces]
    NS --> App[Workloads]
    App --> IRSA[IAM Roles for Service Accounts]
    EKS --> Logs[Central Logs]
    EKS --> Metrics[Metrics/Tracing]
    Logs --> SIEM[Security Analytics / SIEM]
    Metrics --> Alert[Alerts + On-call]
  end

  Img --> EKS
  TF --> AWS
