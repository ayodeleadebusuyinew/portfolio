# Rollback Playbook (Release Safety)

## When to rollback
- Error rate spikes after deploy
- Latency regression beyond threshold
- Increased pod crashes / failed health checks
- SLO burn-rate alerts triggered by release

## Rollback options (ranked)
1. **Rollback to last stable version**
2. **Disable feature flags** (if used)
3. **Scale down new version / scale up stable**
4. **Traffic shift back** (canary/blue-green)

## Kubernetes rollback (examples)
- Helm:
  - `helm history <release> -n <ns>`
  - `helm rollback <release> <REVISION> -n <ns>`
- Deployments:
  - `kubectl rollout undo deploy/<name> -n <ns>`
  - `kubectl rollout status deploy/<name> -n <ns>`

## Verification after rollback
- Confirm key endpoints
- Validate error/latency returns to baseline
- Watch saturation and pod stability
- Update stakeholders with recovery confirmation

## After action
- Open follow-up ticket
- Capture root cause notes
- Schedule postmortem if SEV1/SEV2
