# Aarosh

On-demand cybersecurity expert for Claude Code. Scans code for vulnerabilities against real security standards (OWASP, CIS) and proposes reviewable fixes.

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

| Command | What it does |
|---|---|
| `/aarosh:scan-web` | Scans web apps and backend routes against OWASP Top 10:2025 |
| `/aarosh:scan-api` | Scans service code (REST, GraphQL, RPC) against OWASP API Security Top 10:2023 |
| `/aarosh:scan-mobile` | Scans mobile app code (iOS, Android, RN, Flutter) against OWASP Mobile Top 10 |
| `/aarosh:scan-infra` | Scans infra config (Dockerfiles, K8s, IaC, CI/CD) against CIS Docker/K8s Benchmarks + OWASP CI/CD Top 10 |
| `/aarosh:scan-ai` | Scans LLM/agent code (prompts, tools, RAG) against OWASP Top 10 for LLM Applications |

```
/aarosh:scan-web src/
/aarosh:scan-web src/ --mode=cokezero
```

Path defaults to the working directory. `--mode` controls scan depth, not which checks run (default **espresso**):

- `lactose` — grep-only, fastest
- `espresso` — grep + read flagged files to confirm (default)
- `cokezero` — adds cross-file tracing for ambiguous findings

Every scan reports a File/Line/Vulnerability/Category/Severity table (worst first), calls out anything that can't be patched in place (e.g. secrets already in git history), then asks before patching.

---

*I made this plugin because installing and running it looks cooler than just dropping a skill in `.claude/skills/` and calling it with `/skills`.*
