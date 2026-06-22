# Impact Assessment - 2026-06-22

Investigation datetime: 2026-06-22T09:09:47Z

Intel input: `/workspace/docs/security/intel_report.md` dated 2026-06-22T09:03:39+00:00.

Monitored targets: SkiresortWebPlan, SPRAY, JAPOWSERCH, WebTest, POWDER.

## Summary

No Critical/High + AFFECTED dependency finding was confirmed in the resolvable monitored targets. SkiresortWebPlan and SPRAY are on the fixed Next.js / React Server Components versions from the May 2026 coordinated release (`next` 16.2.9 or 15.5.18; React 19.2.7 or 19.2.6). POWDER, whose package name is `japowserch`, has no npm audit findings and does not install the current intel packages. All resolvable repos contain GitHub Actions workflows using floating `node-version: "22"`; the exact Node 22 patch version used by CI/deploy/runtime was not proven from repository files, so the Node.js June 2026 advisory remains UNKNOWN pending runtime verification. Standalone JAPOWSERCH and WebTest repositories were not resolvable from the local workspace or read-only GitHub discovery.

## Evidence and commands used

### Workspace and repo resolution

- Local workspace discovery:
  - `Glob /workspace **/package.json` -> 0 files.
  - `Glob /workspace **/package-lock.json` -> 0 files.
  - `Glob /workspace **/pnpm-lock.yaml` -> 0 files.
- Read-only clones in `/tmp/cloude-impact-20260622`:
  - `git clone --depth 1 https://github.com/Seeker-x1/SkiresortWebPlan.git /tmp/cloude-impact-20260622/SkiresortWebPlan` -> revision `29c35914c0fe`.
  - `git clone --depth 1 https://github.com/momentum-create/spray.git /tmp/cloude-impact-20260622/SPRAY` -> revision `d0a7ebd0d013`.
  - `git clone --depth 1 https://github.com/momentum-create/POWDER.git /tmp/cloude-impact-20260622/POWDER` -> revision `3674cafda299`.
- Standalone unresolved target checks:
  - `gh repo view momentum-create/JAPOWSERCH`, `momentum-create/WebTest`, `Seeker-x1/JAPOWSERCH`, `Seeker-x1/WebTest` -> `NOT_FOUND_OR_NO_ACCESS`.
  - `gh search repos JAPOWSERCH --owner momentum-create`, `--owner Seeker-x1`, and equivalent WebTest searches -> no accessible results.
- Tooling used for audits:
  - `node -v` -> v22.14.0 (audit runner only, not treated as target runtime).
  - `npm -v` -> 10.9.7.
  - `pnpm -v` -> 10.33.3.

### Audit commands

| Target area | Command | Result |
|---|---|---|
| SkiresortWebPlan root | `(cd /tmp/cloude-impact-20260622/SkiresortWebPlan && npm audit --json)` | 3 Moderate, 0 High/Critical (`next`/`next-intl` via transitive `postcss` GHSA-qx2v-qp2m-jg93). |
| SkiresortWebPlan Nanako web | `(cd /tmp/cloude-impact-20260622/SkiresortWebPlan/NanakoCyoueiSki/web && npm audit --json)` | 1 Low, 5 Moderate, 0 High/Critical (`@babel/core`, `brace-expansion`, `js-yaml`, `next`/`next-intl` via transitive `postcss`). |
| SkiresortWebPlan Sichinohe web | `(cd /tmp/cloude-impact-20260622/SkiresortWebPlan/resorts/Sichinohe-CyoueiSki/web && npm audit --json)` | 3 Moderate, 0 High/Critical (`next`/`next-intl` via transitive `postcss`). |
| SkiresortWebPlan Nanako scripts | `(cd /tmp/cloude-impact-20260622/SkiresortWebPlan/NanakoCyoueiSki/scripts && npm audit --json)` | 0 vulnerabilities. |
| SkiresortWebPlan Sichinohe scripts | `(cd /tmp/cloude-impact-20260622/SkiresortWebPlan/resorts/Sichinohe-CyoueiSki/scripts && npm audit --json)` | 0 vulnerabilities. |
| SPRAY workspace | `(cd /tmp/cloude-impact-20260622/SPRAY && pnpm audit --json)` | 2 Moderate, 0 High/Critical (`postcss` via `next`; `js-yaml` via ESLint/dev tooling). |
| POWDER | `(cd /tmp/cloude-impact-20260622/POWDER && npm audit --json)` | 0 vulnerabilities. |

## Project impact

### SkiresortWebPlan

- Verdict: UNKNOWN
- Severity for us: High for unresolved Node.js runtime verification; Medium for audit-only transitive PostCSS findings; Low for current Next.js/RSC intel packages.
- Recommended pipeline: `monitor`
- Reachability and versions:
  - `next@16.2.9` is a direct production dependency in root, `NanakoCyoueiSki/web`, and `resorts/Sichinohe-CyoueiSki/web`; lockfiles confirm `node_modules/next` version 16.2.9. This is NOT_AFFECTED by the intel ranges requiring fixed `next` 15.5.18 / 16.2.6.
  - `react@19.2.7` and `react-dom@19.2.7` are direct production dependencies in the same Next.js app areas. This is NOT_AFFECTED by the React Server Components fixed line 19.2.6.
  - `react-server-dom-*`: not installed as standalone packages in searched package manifests/locks; reachability `not_installed`.
  - `undici@6.27.0` appears in `resorts/Sichinohe-CyoueiSki/web/package-lock.json` only; the intel `undici` range is 7.x/8.x, so this is NOT_AFFECTED. `undici-types@6.21.0` is a type package and not the advisory package.
  - `react-router`, `@remix-run/server-runtime`, `multer`, `@cyclonedx/cyclonedx-npm`, `tinacms`, `@tinacms/app`, `@tinacms/cli`, `@tinacms/mdx`, `assert-kit`, `ws`, `ai`, and `@ai-sdk/*`: not installed in searched manifests/locks; reachability `not_installed`.
  - Node.js runtime: package engines are `node >=20`; GitHub Actions use floating `node-version: "22"` in CI/security/deploy workflows, including the Vercel production workflow. Exact Node 22 patch level was not proven from repository files. Next step: verify GitHub Actions resolved Node >=22.23.0 and Vercel production runtime is not an affected Node 22/24/26 patch.
- Audit-only findings outside the current intel table:
  - `postcss@8.4.31` transitive through `next`, Moderate GHSA-qx2v-qp2m-jg93; reachability `transitive`.
  - Nanako web also has Low/Moderate dev-tooling findings (`@babel/core`, `brace-expansion`, `js-yaml`); reachability `devOnly`/tooling, no High/Critical.

### SPRAY

- Verdict: UNKNOWN
- Severity for us: High for unresolved Node.js runtime verification; Medium for audit-only transitive PostCSS/js-yaml findings; Low for current Next.js/RSC intel packages.
- Recommended pipeline: `monitor`
- Reachability and versions:
  - `apps/web/package.json` declares `next` as a direct production dependency (`^15.1.0`); `pnpm-lock.yaml` resolves `next@15.5.18`. This is NOT_AFFECTED by the intel ranges requiring fixed `next` 15.5.18 / 16.2.6.
  - `pnpm-lock.yaml` resolves `react@19.2.6` and `react-dom@19.2.6`; these are at the React Server Components fixed line and are NOT_AFFECTED.
  - `react-server-dom-*`, `react-router`, `@remix-run/server-runtime`, `undici`, `multer`, `@cyclonedx/cyclonedx-npm`, `tinacms`, `@tinacms/app`, `@tinacms/cli`, `@tinacms/mdx`, `assert-kit`, `ws`, `ai`, and `@ai-sdk/*`: not installed in searched manifests/lock; reachability `not_installed`.
  - Node.js runtime: root `package.json` requires `node >=20`; `.github/workflows/security-audit.yml` uses floating `node-version: "22"`. Exact Node 22 patch level was not proven from repository files. Next step: verify GitHub Actions/Vercel runtime resolves to Node >=22.23.0 or another unaffected line.
- Audit-only findings outside the current intel table:
  - `postcss@8.4.31` transitive through `next`, Moderate GHSA-qx2v-qp2m-jg93; reachability `transitive`.
  - `js-yaml@4.1.1` via ESLint/dev tooling, Moderate GHSA-h67p-54hq-rp68; reachability `devOnly`.

### POWDER

- Verdict: UNKNOWN
- Severity for us: High for unresolved Node.js runtime verification; Low for current npm package advisories.
- Recommended pipeline: `monitor`
- Reachability and versions:
  - Repository resolved as `https://github.com/momentum-create/POWDER`; `package.json` name is `japowserch`.
  - `npm audit --json` reported 0 vulnerabilities.
  - Installed production dependencies are `kuroshiro@1.2.0` and `kuroshiro-analyzer-kuromoji@1.1.0`; lockfile also contains `lodash@4.18.1` transitively through `async`. The current intel report does not list a lodash advisory, and npm audit reported no lodash finding.
  - `next`, `react-server-dom-*`, `react-router`, `@remix-run/server-runtime`, `undici`, `multer`, `@cyclonedx/cyclonedx-npm`, `tinacms`, `@tinacms/app`, `@tinacms/cli`, `@tinacms/mdx`, `assert-kit`, `ws`, `ai`, and `@ai-sdk/*`: not installed in searched manifests/lock; reachability `not_installed`.
  - Node.js runtime: GitHub Actions workflows use floating `node-version: "22"` for security audit and weather update automation. Exact Node 22 patch level was not proven from repository files. Next step: verify GitHub Actions resolved Node >=22.23.0 or move the runtime check into the owning workflow report.

### JAPOWSERCH standalone

- Verdict: UNKNOWN
- Severity for us: High until dependency inventory is resolved, because the intel report includes High web/npm/Node advisories that cannot be mapped without a package inventory.
- Recommended pipeline: `monitor`
- Reachability and versions:
  - No standalone local repo or package manifest was present under `/workspace`.
  - Read-only GitHub checks for `momentum-create/JAPOWSERCH`, `Seeker-x1/JAPOWSERCH`, and owner-scoped repo search returned no accessible results.
  - POWDER's package name is `japowserch` and was audited separately above; this does not prove whether a separate standalone JAPOWSERCH deploy unit exists.
  - Reachability: `not_installed` in the Cloude workspace snapshot; `UNKNOWN` for any separate unavailable repo.
- Next step: provide the standalone repository URL or dependency lockfile; then run `npm audit --json` or the appropriate package-manager audit and map the intel package versions.

### WebTest

- Verdict: UNKNOWN
- Severity for us: High until dependency inventory is resolved, because the intel report includes High Next.js/RSC/Node advisories that cannot be mapped without a package inventory.
- Recommended pipeline: `monitor`
- Reachability and versions:
  - No local repo or package manifest was present under `/workspace`.
  - Read-only GitHub checks for `momentum-create/WebTest`, `Seeker-x1/WebTest`, and owner-scoped repo search returned no accessible results.
  - Reachability: `not_installed` in the Cloude workspace snapshot; `UNKNOWN` for any unavailable repo.
- Next step: provide the WebTest repository URL or dependency lockfile; then run `npm audit --json` and verify whether it pins vulnerable `next` 13-16, `react-server-dom-*`, or Node 22/24/26 runtime versions.

## Escalation

- No `Critical`/`High` + `AFFECTED` finding was confirmed, so do not start remediation or patching from this stage.
- Incident escalation condition to watch: if any resolved runtime check proves Node 22 <22.23.0, Node 24 <24.17.0, or Node 26 <26.3.1 in production/CI handling untrusted input, recommend `vuln-remediation-planner`.
- Current recommendation: continue `monitor` for Node runtime verification and unresolved standalone repo inventory; keep Medium audit-only findings in `daily_intel` tracking.

impact complete → incident: vuln-remediation-planner | monitor only
