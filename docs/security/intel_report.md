# Intel Report - 2026-07-23

## 調査日時
2026-07-23T09:04:10+00:00

## 情報源
| 名称 | URL | 取得時刻 |
|------|-----|----------|
| Next.js July 2026 Security Release | https://nextjs.org/blog/july-2026-security-release | 2026-07-23T09:04:10+00:00 |
| Next.js v16.2.11 release | https://github.com/vercel/next.js/releases/tag/v16.2.11 | 2026-07-23T09:04:10+00:00 |
| Next.js v15.5.21 release | https://github.com/vercel/next.js/releases/tag/v15.5.21 | 2026-07-23T09:04:10+00:00 |
| Next.js GHSA-m99w-x7hq-7vfj | https://github.com/vercel/next.js/security/advisories/GHSA-m99w-x7hq-7vfj | 2026-07-23T09:04:10+00:00 |
| Next.js GHSA-6gpp-xcg3-4w24 | https://github.com/vercel/next.js/security/advisories/GHSA-6gpp-xcg3-4w24 | 2026-07-23T09:04:10+00:00 |
| Next.js GHSA-p9j2-gv94-2wf4 | https://github.com/vercel/next.js/security/advisories/GHSA-p9j2-gv94-2wf4 | 2026-07-23T09:04:10+00:00 |
| Next.js GHSA-89xv-2m56-2m9x | https://github.com/vercel/next.js/security/advisories/GHSA-89xv-2m56-2m9x | 2026-07-23T09:04:10+00:00 |
| sharp GHSA-f88m-g3jw-g9cj | https://github.com/lovell/sharp/security/advisories/GHSA-f88m-g3jw-g9cj | 2026-07-23T09:04:10+00:00 |
| OSV: js-yaml GHSA-52cp-r559-cp3m | https://osv.dev/vulnerability/GHSA-52cp-r559-cp3m | 2026-07-23T09:04:10+00:00 |
| OSV: brace-expansion GHSA-3jxr-9vmj-r5cp | https://osv.dev/vulnerability/GHSA-3jxr-9vmj-r5cp | 2026-07-23T09:04:10+00:00 |
| pnpm GHSA-fr4h-3cph-29xv | https://github.com/pnpm/pnpm/security/advisories/GHSA-fr4h-3cph-29xv | 2026-07-23T09:04:10+00:00 |
| Node.js July 2026 security release pre-alert | https://nodejs.org/en/blog/vulnerability/july-2026-security-releases | 2026-07-23T09:04:10+00:00 |

## 新規 / 更新 advisory
| ID | 概要 | 影響パッケージ | ベンダー深刻度 |
|----|------|----------------|----------------|
| CVE-2026-64641 / GHSA-m99w-x7hq-7vfj | App Router + Server Actions の CPU DoS。回避策なし、upgrade 推奨。 | next >=13.0.0 <15.5.21, >=16.0.0 <16.2.11 | High |
| CVE-2026-64642 / GHSA-6gpp-xcg3-4w24 | Turbopack + single locale App Router の Middleware / Proxy bypass。 | next >=16.0.0 <16.2.11 | High |
| CVE-2026-64645 / GHSA-p9j2-gv94-2wf4 | request-controlled hostname を使う rewrites / redirects の SSRF / Open Redirect。 | next >=12.0.0 <15.5.21, >=16.0.0 <16.2.11 | High |
| CVE-2026-64649 / GHSA-89xv-2m56-2m9x | custom server 上の Server Actions forwarding/redirect SSRF。 | next >=14.1.1 <15.5.21, >=16.0.0 <16.2.11 | High |
| CVE-2026-64643 / GHSA-955p-x3mx-jcvp | internal Server Function endpoint disclosure。 | next >=13.0.0 <15.5.21, >=16.0.0 <16.2.11 | Moderate |
| CVE-2026-64644 / GHSA-q8wf-6r8g-63ch | Image Optimization API SVG DoS。 | next >=15.5.0 <15.5.21, >=16.0.0 <16.2.11 | Moderate |
| CVE-2026-64646 / GHSA-4c39-4ccg-62r3 | Edge runtime Server Action payload memory DoS。 | next >=13.0.0 <15.5.21, >=16.0.0 <16.2.11 | Moderate |
| CVE-2026-64647 / GHSA-4633-3j49-mh5q | invalid UTF-8 request body による fetch response body cache confusion。 | next >=13.0.0 <15.5.21, >=16.0.0 <16.2.11 | Moderate |
| CVE-2026-64648 / GHSA-68g3-v927-f742 | request body 付き server-side fetch の response body cache confusion。 | next >=13.0.0 <15.5.21, >=16.0.0 <16.2.11 | Moderate |
| GHSA-f88m-g3jw-g9cj | sharp が利用する libvips の High 2件を含む脆弱性群。untrusted image input 処理が影響。 | sharp <0.35.0 | High |
| CVE-2026-59869 / GHSA-52cp-r559-cp3m | js-yaml merge-key chain による quadratic CPU consumption。 | js-yaml >=3.0.0 <3.15.0, >=4.0.0 <4.3.0 | High |
| CVE-2026-13149 / GHSA-3jxr-9vmj-r5cp | brace-expansion の非展開 `{}` 連続入力による exponential-time DoS。 | brace-expansion <1.1.16, >=2.0.0 <2.1.2, >=3.0.0 <5.0.7 | High |
| CVE-2026-59196 / GHSA-fr4h-3cph-29xv | pnpm hoisted install が crafted lockfile alias を node_modules 外へ展開し得る。 | pnpm <10.34.4, >=11.0.0 <11.7.0 | High |
| Node.js July 2026 pre-alert | 22.x / 24.x / 26.x に最大 High の security release 予定。詳細は 2026-07-27 以降。 | Node.js 22.x, 24.x, 26.x | High |

## Cloude 横断メモ
- SkiresortWebPlan: npm audit で `next@16.2.9` (root / Nanako / Sichinohe web) が July 2026 Next.js High ranges に AFFECTED。`sharp@0.34.5`, `js-yaml`, `brace-expansion` High も検出。Critical なし、High + AFFECTED のため incident 推奨のみ。
- SPRAY: `pnpm audit --json` で `apps/web` の `next@15.5.18`, transitive `sharp@0.34.5`, `js-yaml@4.1.1`, `brace-expansion@1.1.14/5.0.6` が High。root `packageManager` は `pnpm@9.15.0` で GHSA-fr4h-3cph-29xv の affected range。incident 推奨のみ。
- POWDER: `npm audit --json` は 0 vulnerabilities。今回の Next.js / sharp / pnpm advisory 対象 package は未導入、`lodash@4.18.1` は現時点で audit clean。
- JAPOWSERCH: standalone repo は `momentum-create/*` / `Seeker-x1/*` で未解決。POWDER の package name は `japowserch` だが audit clean。
- WebTest: standalone repo は今回も未解決。ローカル監査不可のため UNKNOWN。

## 次アクション
-> vuln-impact-analyst
