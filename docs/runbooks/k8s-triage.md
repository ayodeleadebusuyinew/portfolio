# Kubernetes Triage Runbook

## Goal
Quickly determine whether the issue is **workload**, **cluster**, **network**, or **dependency**.

## First checks (2 minutes)
- `kubectl get pods -A | grep -E "CrashLoopBackOff|Error|Pending|ImagePullBackOff"`
- `kubectl get nodes` (Ready? pressure?)
- Check recent deploys (what changed?)

## Pods flapping / CrashLoopBackOff
- `kubectl describe pod <pod> -n <ns>`
- `kubectl logs <pod> -n <ns> --previous`
Common causes:
- bad config/env vars
- missing secrets
- failing health checks
- dependency unavailable
- resource limits too low

## High latency / timeouts
- Check ingress/ALB metrics
- Check service endpoints:
  - `kubectl get endpoints <svc> -n <ns>`
- Look for network policy changes
- Validate DNS:
  - CoreDNS health and resolution

## Pending pods
- `kubectl describe pod <pod> -n <ns>`
Common causes:
- insufficient CPU/memory
- node taints/tolerations
- missing PV/PVC binding

## Node pressure
- `kubectl describe node <node>`
Look for:
- MemoryPressure / DiskPressure / PIDPressure
Mitigations:
- scale node group
- evict noisy workloads
- increase requests/limits accuracy

## “Golden signals” focus
- errors, latency, saturation, traffic
Tie changes to these metrics before deciding rollout/rollback.
