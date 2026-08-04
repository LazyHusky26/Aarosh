# Aarosh
CyberSec Claude Code Plugin

An on-demand cybersecurity expert that scans code for vulnerabilities against real security standards (OWASP, CIS) and proposes reviewable fixes — never patches without asking first.

## Install

This repo is private for now — not published to a public marketplace. `/plugin marketplace add` still works against a private repo you have GitHub access to:
```
/plugin marketplace add LazyHusky26/Aarosh
/plugin install aarosh@aarosh
```

When prompted for install scope, pick **"Install for you (user scope)"** — makes `/aarosh:scan-web` available in any project you work in, not just this repo. ("Project scope" shares it with repo collaborators, "local scope" ties it to this one repo only — neither is what you want for a scanner meant to run against other codebases.)

Restart/reload Claude Code after install so it picks up the skill. Check it's active with `/plugin list`.

**Uninstall:** `/plugin uninstall aarosh@aarosh`. To remove the marketplace entirely: `/plugin marketplace remove aarosh`.

## Usage
```
/aarosh:scan-web src/          # OWASP Top 10:2021 — web apps, backend routes
/aarosh:scan-api routes/       # OWASP API Security Top 10:2023 — REST/GraphQL/RPC
/aarosh:scan-mobile app/       # OWASP Mobile Top 10 — iOS/Android/RN/Flutter
/aarosh:scan-infra .           # CIS Docker/K8s Benchmarks + OWASP CI/CD Top 10
/aarosh:scan-ai agents/        # OWASP Top 10 for LLM Applications

/aarosh:scan-web src/ --mode=cokezero
```

Modes (control depth via tool-call budget, not which checks run — default is Espresso):
- `--mode=lactose` — grep-only pass, fastest
- `--mode=espresso` — grep + read flagged files to confirm (default)
- `--mode=cokezero` — adds cross-file tracing where a finding's exploitability is ambiguous

Every scan: reports a File/Line/Vulnerability/Category/Severity table (worst first), calls out anything that can't be patched in place (e.g. secrets already in git history), then asks before patching. Never patches without a yes.

## Status
All 5 `scan-*` skills implemented. Not yet built: the `sec-expert` deep cross-file review sub-agent.
