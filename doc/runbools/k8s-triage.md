# Kubernetes Triage Runbook (EKS/GKE)

## Goal
Quickly determine whether the incident is **application**, **cluster**, **network**, or **dependency** and stabilize service.

---

## 2-minute checks
- Did a deploy happen? (rollout history)
- Is impact single namespace or global?
- Are nodes under pressure (CPU/mem/disk)?

---

## Commands (copy/paste)
### Workload status
```bash
kubectl get pods -n <ns>
kubectl describe pod <pod> -n <ns>
kubectl logs <pod> -n <ns> --tail=200
kubectl get events -n <ns> --sort-by=.lastTimestamp | tail -n 50
