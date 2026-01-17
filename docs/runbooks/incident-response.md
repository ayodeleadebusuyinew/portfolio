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
3. Confirm current blast radius (who/what is impacted)
4. Identify last known good state + recent changes
5. Execute stabilization action (rollback, scale, disable feature, failover)

## Triage checklist
- Is it a deploy regression? (compare to last release)
- Is it infra capacity? (CPU/mem, node pressure, saturation)
- Is it dependency failure? (DB, cache, external API)
- Is i
