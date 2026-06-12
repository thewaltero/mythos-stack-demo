# mythos-stack-demo

> **Status: early — repo just created, pipeline being wired in public. Nothing here is runnable yet. Watch the commits.**

An autonomous agent that runs on a schedule, spends within a signed mandate,
writes code that is hash-verified, and seals every session as an attestation
on Base. This repo is the working demonstration of that pipeline.

## What it will contain

- a scheduled GitHub Actions workflow that runs the agent unattended
- agent tool access routed through [mythos-sentinel](https://github.com/thewaltero/mythos-sentinel) — every payment, shell, file, and network call gated by policy
- a signed EIP-712 spend mandate the agent cannot widen or talk itself out of
- code tasks executed through [mythos-router](https://github.com/thewaltero/mythos-router) — every claimed file change verified against the disk with SHA-256 receipts
- a session attestation committed at the end of each run

The morning-after artifact: one receipt trail showing what ran, what changed,
what it spent, and the authorization that allowed it.

## Roadmap to working

- [ ] scheduled workflow skeleton
- [ ] sentinel proxy wired into the agent's MCP config
- [ ] signed mandate committed
- [ ] router receipts in the loop
- [ ] first attested session
- [ ] aeon as the agent runner
- [ ] first attested unattended aeon run
