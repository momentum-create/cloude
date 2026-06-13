---
name: web-vuln-remediation
description: Plans remediation for Next.js, Node, and Vercel deployments — dependency bumps, middleware hardening, CI pins, rollback. Use with vuln-remediation-planner. Fetch fixed versions from web, do not hardcode in plans.
---

# Web Vulnerability Remediation Planning

## Pre-flight checklist

- [ ] Branch: `security/{advisory-id}`
- [ ] Staging or preview deploy available (Vercel)
- [ ] Rollback: previous lockfile commit hash noted
- [ ] Secrets: rotate if advisory involves credential leak

## Patch order (default)

1. **Lock root cause** — bump direct dependency to vendor-fixed version (verify via WebFetch on GHSA)
2. **Transitive** — `npm update` / overrides / `pnpm.overrides` if documented
3. **Next.js** — framework bump may require codemods; check Next.js upgrade guide (fetch current URL)
4. **Node runtime** — align `engines` + Vercel/Docker base image
5. **Compensating controls** — if no fix: disable feature, WAF rule, env kill-switch

## Stack-specific notes

### Next.js / React
- Check `next.config` for experimental flags tied to advisory
- Re-run `next build` after bump
- Review middleware / server actions if auth-related CVE

### Node API
- Pin `engines.node` in package.json
- Review `express` / body-parser / cookie settings for known classes

### Vercel / CI
- **Install command:** `npm ci` (never `npm install` in CI/Vercel). pnpm: `--frozen-lockfile`
- **Dependabot:** merge security PRs from `.github/dependabot.yml`; re-run `security-audit` workflow
- Set `installCommand` in `vercel.json` when not default
- Pin GitHub Actions to SHA where supply-chain CVE
- Review `vercel.json` headers (CSP, HSTS) if XSS-related

## Plan template

```markdown
# Remediation Plan — {advisory-id}

## 参照
- Advisory URL:
- 目標修正版（調査日時 {date}）:

## スコープ
Projects: ...

## 手順
1. [implementer] ...
2. [implementer] ...

## ロールバック
1. git checkout {hash} -- package-lock.json
2. redeploy preview

## 検証（verify-auditor）
- [ ] npm audit clean for {id}
- [ ] build
- [ ] smoke: {routes}
```

## Rules

- Version targets must cite advisory URL fetched same session
- Document accepted risk if patch deferred (with expiry date)
