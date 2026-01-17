# Incident Response Runbook (SRE)

## Purpose
A simple, reliable incident flow that stabilizes service quickly, keeps stakeholders informed, and drives permanent fixes.

## Severity levels
- **SEV1**: Major outage / customer impact / data risk
- **SEV2**: Partial degradation / high error rates / limited blast radius
- **SEV3**: Minor impact / workaround available

## Roles
- **Incident Commander (IC)**: owns coordination and decisions
- **Operations Lead**: drives technical triage + mitigation
- **Comms Lead**: updates stakeholders and timelines
- **Scribe**: records timeline, actions, and outcomes

## First 10 minutes (stabilize)
1. Declare severity + start incident channel/bridge
2. Freeze risky changes (pause deploys if needed)
3. Confirm blast radius (who/what is impacted)
4. Identify last known good state + recent changes
5. Execute stabilization action (rollback, scale, disable feature, failover)

## Triage checklist
- Deploy regression? compare to last release
- Infra capacity? CPU/mem/node pressure/saturation
- Dependency failure? DB/cache/external API
- Networking/DNS/certs? timeouts/TLS errors
- Kubernetes health? pods flapping/HPA/readiness

## Communication cadence
- SEV1: updates every 10–15 minutes
- SEV2: updates every 30 minutes

## Resolution & recovery
- Confirm recovery with metrics + smoke tests
- Re-enable deploys carefully
- Capture final impact summary

## Post-incident
- Postmortem within 24–72 hours
- Action items: owners + due dates + verification
