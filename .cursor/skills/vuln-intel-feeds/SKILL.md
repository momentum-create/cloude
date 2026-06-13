---
name: vuln-intel-feeds
description: Fetches latest web security advisories for Next.js, Node, npm, and Vercel via WebSearch and WebFetch. Use when running vuln-intel-scout, daily_intel pipeline, or when the user asks about new CVEs, GHSA, or security bulletins. Never use stale training data for version numbers.
---

# Vulnerability Intelligence Feeds

## Principle

**Always fetch live.** CVE IDs, fixed versions, and exploit status change daily. Use WebSearch + WebFetch every run.

## Search queries (rotate per run)

Use date-aware queries, e.g.:

- `Next.js security advisory 2026`
- `Node.js security release`
- `site:github.com/advisories next react`
- `npm audit critical vulnerability`
- `Vercel security bulletin`

For a specific package: `{package} CVE GHSA site:github.com/advisories`

## Primary sources (WebFetch these)

| Source | URL pattern |
|--------|-------------|
| GitHub Advisory | `https://github.com/advisories?query=ecosystem:npm` |
| Next.js blog | `https://nextjs.org/blog` (security posts) |
| Node releases | `https://nodejs.org/en/blog/vulnerability` |
| OSV | `https://osv.dev/list?ecosystem=npm` |
| npm audit docs | vendor pages linked from `npm audit` output |
| GitHub Dependabot | Repo **Security → Dependabot** alerts and open PRs |
| GitHub Actions | `.github/workflows/security-audit.yml` weekly `npm audit` |

See [sources.md](sources.md) for Cloude-specific project roots to mention in reports.

## GitHub (Cloude repos)

Each git repo has:

- `.github/dependabot.yml` — weekly npm + github-actions update PRs; security advisories become PRs
- `.github/workflows/security-audit.yml` — `npm ci` + `npm audit --audit-level=high` on push/PR/schedule

Repos: `SkiresortWebPlan`, `SPRAY`, `JAPOWSERCH`, `primecarwash-site`

When triaging, check open Dependabot PRs and failed `Security audit` workflow runs before WebSearch.

## Intel report template

```markdown
# Intel Report — {date}

## 調査日時
{ISO8601}

## 情報源
| 名称 | URL | 取得時刻 |
|------|-----|----------|

## 新規 / 更新 advisory
| ID | 概要 | 影響パッケージ | ベンダー深刻度 |
|----|------|----------------|----------------|

## Cloude 横断メモ
- {subproject}: {one line}

## 次アクション
→ vuln-impact-analyst
```

## Anti-patterns

- Do not copy CVE fix versions from this skill file
- Do not treat social media as sole source
- Do not skip timestamp on intel report
