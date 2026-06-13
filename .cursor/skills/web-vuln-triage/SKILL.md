---
name: web-vuln-triage
description: Triages vulnerability impact across Next.js and Node monorepos. Runs npm audit, maps GHSA/CVE to installed versions, assigns Cloude-specific severity. Use with vuln-impact-analyst or pr_dependency_gate pipeline.
---

# Web Vulnerability Triage

## Workflow

1. Ingest intel (`intel_report.md` or user CVE)
2. Discover projects: `**/package.json` under Cloude (exclude `node_modules`)
3. Per project run:

```bash
cd <project> && npm audit --json
# or: pnpm audit --json
```

4. Map advisory affected range → installed version (direct + transitive)
5. Classify reachability:

| Label | Meaning |
|-------|---------|
| direct | Listed in dependencies |
| transitive | Lockfile only |
| devOnly | devDependencies; prod deploy unaffected |
| not_installed | Advisory package not in tree |

## Severity override (our environment)

| Condition | Our severity |
|-----------|--------------|
| RCE / auth bypass on production route | Critical |
| High CVE in direct prod dep, reachable | High |
| Transitive only, no exploit path in our code | Medium |
| Dev-only or not installed | Low |

## Impact assessment template

```markdown
# Impact Assessment — {date}

## サマリー
{one paragraph}

## プロジェクト別
### {project}
- 判定: AFFECTED | NOT_AFFECTED | UNKNOWN
- 深刻度: Critical | High | Medium | Low
- パッケージ: {name}@{installed} (advisory: {range})
- 到達性: direct | transitive | devOnly | not_installed
- 推奨パイプライン: incident | daily_intel | monitor

## エスカレーション
- [ ] vuln-remediation-planner (Critical/High + AFFECTED)
```

## Commands

```bash
# Find vulnerable package in lockfile
npm ls <package> --all

# Next.js version
npx next --version
```
