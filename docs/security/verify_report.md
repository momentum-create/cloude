# Verify Report - 2026-06-20

## Rubric
| ID | Check | Result |
|----|-------|--------|
| V1 | npm ci on patched projects | PASS |
| V2 | npm audit --audit-level=high (incident scope) | PASS with notes |
| V3 | npm run build | PASS |
| V4 | Version alignment (SkiresortWebPlan) | PASS (16.2.9 / 19.2.7) |
| V5 | Node.js June 2026 intel | MONITOR (Vercel managed) |

## Project results

### SkiresortWebPlan root
- next@16.2.9 react@19.2.7
- audit high: PASS (postcss moderate only)
- build: PASS

### Nanako web
- Aligned to 16.2.9 / 19.2.7
- audit high: PASS
- build: PASS

### Sichinohe web
- next@16.2.9, undici@6.27.0 via @vercel/blob@2.4.0
- audit high: PASS (was FAIL undici High before npm audit fix)
- build: PASS

### primecarwash-site
- next@16.2.6 react@19.2.6
- audit high: PASS
- build: PASS
- POP_PROMO_SECRET: hardcoded fallback removed; requires Vercel env

### JAPOWSERCH
- lodash High: FIXED (npm audit fix)
- dependabot.yml: UTF-8

### SPRAY (out of incident scope)
- next@15.5.18 patched for May 2026 CVEs
- pnpm audit: moderate only

## Node.js June 2026 (P1 intel)
- Released 2026-06-18: 22.23.0, 24.17.0, 26.3.1+
- High: CVE-2026-48933 (WebCrypto DoS), CVE-2026-48618 (TLS bypass)
- Action: confirm Vercel project Node.js version >= 22.23.0 on next deploy

## Residual risk (accepted)
- PostCSS moderate (GHSA-qx2v) across Next apps until upstream bump
- js-yaml / babel dev transitive on several projects

## Manual follow-up
- Set POP_PROMO_SECRET on Vercel for prime-car-wash (use same value as former fallback PRM-POP-6000 if LINE keyword unchanged)

## P2 configuration (2026-06-20)

| Item | Status |
|------|--------|
| UTF-8 config rule (`.cursor/rules/config-encoding-utf8.mdc`) | DONE |
| CI encoding check (`.github/scripts/check-config-encoding.cjs` + security-audit) | DONE — primecarwash, SkiresortWebPlan, JAPOWSERCH, SPRAY |
| Dependabot major ignore (manual review) | DONE — all four repos |
| pnpm/npm dual lock prevention | DONE — SPRAY CI rejects `apps/web/package-lock.json` |
| Skiresort Nanako in Dependabot + lockfile-sync + audit matrix | DONE |

verify complete -> monitor: daily_intel