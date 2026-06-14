# mythos-stack-demo

> **Status: nightly run is green — see the [Actions tab](../../actions). Each run verifies the signed mandate, produces and verifies a SHA-256 work receipt, and seals the session into an attestation bundle. Remaining: on-chain broadcast of the attestation (Base Sepolia) and swapping the model-free stand-in for the live aeon agent.**

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

## How it's wired

`.mcp.json` exposes exactly one MCP server to the agent: the Sentinel proxy.
Everything else (filesystem tools, payment servers) lives behind it as
upstreams in `mythos.policy.json` — one guarded door, no side entrances.
The policy ships strict: unknown tools need approval, payments need a signed
mandate, daily cap enforced from Sentinel's own ledger.

## Roadmap to working

- [x] scheduled workflow skeleton
- [x] sentinel proxy wired into the agent's MCP config
- [x] signed mandate committed
- [x] router receipts in the loop
- [ ] first attested session
- [ ] aeon as the agent runner
- [ ] first attested unattended aeon run
