# Aarosh
CyberSec Claude Code Plugin

An on-demand cybersecurity expert that scans code for vulnerabilities against real security standards (OWASP, CIS) and proposes reviewable fixes — never patches without asking first.

## Install

This repo is private for now — not published to a public marketplace. `/plugin marketplace add` still works against a private repo you have GitHub access to:
```
/plugin marketplace add LazyHusky26/Aarosh
/plugin install aarosh@aarosh
```

## Usage
```
/aarosh:scan-web src/
/aarosh:scan-web src/ --mode=cokezero
```

Modes (control depth, not which checks run — default is Espresso):
- `--mode=lactose` — fast, surface-level pass
- `--mode=espresso` — standard pass (default)
- `--mode=cokezero` — deep, cross-file pass

## Status
Early scaffold. Only `scan-web` (OWASP Top 10) is implemented so far. Planned next: `scan-api`, `scan-mobile`, `scan-infra`, `scan-ai`, and the `sec-expert` deep-review sub-agent.
