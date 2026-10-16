# Aarosh

On-demand cybersecurity expert for Claude Code. Scans code for vulnerabilities against real security standards (OWASP, CIS) and proposes reviewable fixes — never patches without asking first.

## Install

```
/plugin marketplace add LazyHusky26/Aarosh
/plugin install aarosh@aarosh
```

When prompted for scope, pick **"Install for you (user scope)"** so `/aarosh:*` commands are available in any project, not just this one. Restart Claude Code, then confirm with `/plugin list`.

## Uninstall

```
/plugin uninstall aarosh@aarosh
/plugin marketplace remove aarosh   # removes the marketplace entirely
```

## Usage

| Command | Standard | Scope |
|---|---|---|
| `/aarosh:scan-web` | OWASP Top 10:2025 | Web apps, backend routes |
| `/aarosh:scan-api` | OWASP API Security Top 10:2023 | REST / GraphQL / RPC |
| `/aarosh:scan-mobile` | OWASP Mobile Top 10 | iOS / Android / RN / Flutter |
| `/aarosh:scan-infra` | CIS Docker/K8s Benchmarks + OWASP CI/CD Top 10 | Dockerfiles, K8s, IaC, CI/CD |
| `/aarosh:scan-ai` | OWASP Top 10 for LLM Applications | Agents, prompts, RAG |

```
/aarosh:scan-web src/
/aarosh:scan-web src/ --mode=cokezero
```

Path defaults to the working directory. `--mode` controls scan depth, not which checks run (default **espresso**):

- `lactose` — grep-only, fastest
- `espresso` — grep + read flagged files to confirm (default)
- `cokezero` — adds cross-file tracing for ambiguous findings

Every scan reports a File/Line/Vulnerability/Category/Severity table (worst first), calls out anything that can't be patched in place (e.g. secrets already in git history), then asks before patching — never without a yes.
