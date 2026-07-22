# Intel Report - 2026-07-22

## 調査日時
2026-07-22T09:07:47Z

## 情報源
| 名称 | URL | 取得時刻 |
|------|-----|----------|
| Next.js July 2026 Security Release | https://nextjs.org/blog/july-2026-security-release | 2026-07-22T09:07:47Z |
| Next.js GitHub Security Advisories | https://github.com/vercel/next.js/security/advisories | 2026-07-22T09:07:47Z |
| Next.js GHSA-m99w-x7hq-7vfj | https://github.com/vercel/next.js/security/advisories/GHSA-m99w-x7hq-7vfj | 2026-07-22T09:07:47Z |
| Next.js GHSA-6gpp-xcg3-4w24 | https://github.com/vercel/next.js/security/advisories/GHSA-6gpp-xcg3-4w24 | 2026-07-22T09:07:47Z |
| Next.js GHSA-p9j2-gv94-2wf4 | https://github.com/vercel/next.js/security/advisories/GHSA-p9j2-gv94-2wf4 | 2026-07-22T09:07:47Z |
| Next.js GHSA-89xv-2m56-2m9x | https://github.com/vercel/next.js/security/advisories/GHSA-89xv-2m56-2m9x | 2026-07-22T09:07:47Z |
| Next.js GHSA-4c39-4ccg-62r3 | https://github.com/vercel/next.js/security/advisories/GHSA-4c39-4ccg-62r3 | 2026-07-22T09:07:47Z |
| Next.js GHSA-q8wf-6r8g-63ch | https://github.com/vercel/next.js/security/advisories/GHSA-q8wf-6r8g-63ch | 2026-07-22T09:07:47Z |
| Next.js GHSA-955p-x3mx-jcvp | https://github.com/vercel/next.js/security/advisories/GHSA-955p-x3mx-jcvp | 2026-07-22T09:07:47Z |
| Next.js GHSA-68g3-v927-f742 | https://github.com/vercel/next.js/security/advisories/GHSA-68g3-v927-f742 | 2026-07-22T09:07:47Z |
| Next.js GHSA-4633-3j49-mh5q | https://github.com/vercel/next.js/security/advisories/GHSA-4633-3j49-mh5q | 2026-07-22T09:07:47Z |
| Node.js July 2026 security release pre-alert | https://nodejs.org/en/blog/vulnerability/july-2026-security-releases | 2026-07-22T09:07:47Z |
| Node.js June 2026 security releases | https://nodejs.org/en/blog/vulnerability/june-2026-security-releases | 2026-07-22T09:07:47Z |
| js-yaml GHSA-52cp-r559-cp3m | https://github.com/nodeca/js-yaml/security/advisories/GHSA-52cp-r559-cp3m | 2026-07-22T09:07:47Z |
| brace-expansion GHSA-3jxr-9vmj-r5cp | https://github.com/juliangruber/brace-expansion/security/advisories/GHSA-3jxr-9vmj-r5cp | 2026-07-22T09:07:47Z |
| sharp GHSA-f88m-g3jw-g9cj | https://github.com/lovell/sharp/security/advisories/GHSA-f88m-g3jw-g9cj | 2026-07-22T09:07:47Z |
| pnpm GHSA-fr4h-3cph-29xv | https://github.com/pnpm/pnpm/security/advisories/GHSA-fr4h-3cph-29xv | 2026-07-22T09:07:47Z |
| pnpm GHSA-72r4-9c5j-mj57 | https://github.com/pnpm/pnpm/security/advisories/GHSA-72r4-9c5j-mj57 | 2026-07-22T09:07:47Z |
| pnpm GHSA-5wx6-mg75-v57r | https://github.com/pnpm/pnpm/security/advisories/GHSA-5wx6-mg75-v57r | 2026-07-22T09:07:47Z |
| lodash GHSA-r5fr-rjxr-66jc | https://github.com/lodash/lodash/security/advisories/GHSA-r5fr-rjxr-66jc | 2026-07-22T09:07:47Z |
| Vite GHSA-fx2h-pf6j-xcff | https://github.com/vitejs/vite/security/advisories/GHSA-fx2h-pf6j-xcff | 2026-07-22T09:07:47Z |

## 新規 / 更新 advisory
| ID | 概要 | 影響パッケージ | ベンダー深刻度 |
|----|------|----------------|----------------|
| CVE-2026-64641 / GHSA-m99w-x7hq-7vfj | App Router + Server Actions の DoS。修正版は Next.js 15.5.21 / 16.2.11。 | next >=13.0.0 <15.5.21, >=16.0.0 <16.2.11 | High |
| CVE-2026-64642 / GHSA-6gpp-xcg3-4w24 | Turbopack + single locale の App Router middleware/proxy bypass。 | next >=16.0.0 <16.2.11 | High |
| CVE-2026-64645 / GHSA-p9j2-gv94-2wf4 | request-controlled hostname を使う rewrites/redirects の SSRF/Open Redirect。 | next >=12.0.0 <15.5.21, >=16.0.0 <16.2.11 | High |
| CVE-2026-64649 / GHSA-89xv-2m56-2m9x | custom server の Server Actions forwarding/redirecting における SSRF。 | next >=14.1.1 <15.5.21, >=16.0.0 <16.2.11 | High |
| CVE-2026-64644 / GHSA-q8wf-6r8g-63ch | Image Optimization API + SVG の CPU DoS。Vercel は not impacted、self-host + remotePatterns 等は要確認。 | next >=15.5.0 <15.5.21, >=16.0.0 <16.2.11 | Moderate |
| CVE-2026-64646 / GHSA-4c39-4ccg-62r3 | Edge runtime Server Actions の unbounded payload memory consumption。 | next >=13.0.0 <15.5.21, >=16.0.0 <16.2.11 | Moderate |
| CVE-2026-64643 / GHSA-955p-x3mx-jcvp | App Router Server Functions endpoint disclosure。 | next >=13.0.0 <15.5.21, >=16.0.0 <16.2.11 | Moderate |
| CVE-2026-64648 / GHSA-68g3-v927-f742 | request body 付き server-side fetch の cache confusion。 | next >=13.0.0 <15.5.21, >=16.0.0 <16.2.11 | Moderate |
| CVE-2026-64647 / GHSA-4633-3j49-mh5q | invalid UTF-8 request body による server-side fetch cache confusion。 | next >=13.0.0 <15.5.21, >=16.0.0 <16.2.11 | Moderate |
| Node.js July 2026 pre-alert | 2026-07-27 予定の Node 22/24/26 セキュリティリリース。最高深刻度 High、詳細 CVE は未公開。 | Node.js 22.x / 24.x / 26.x | High |
| CVE-2026-59869 / GHSA-52cp-r559-cp3m | js-yaml merge-key chain による quadratic CPU DoS。 | js-yaml >=3.0.0 <3.15.0, >=4.0.0 <4.3.0 | High |
| CVE-2026-13149 / GHSA-3jxr-9vmj-r5cp | brace-expansion の non-expanding brace groups による DoS。 | brace-expansion <1.1.16, >=2.0.0 <2.1.2, >=3.0.0 <5.0.7 | Moderate |
| GHSA-f88m-g3jw-g9cj | sharp が同梱する libvips の High/Medium 脆弱性群。untrusted input を sharp <0.35.0 で処理する場合に影響。 | sharp <0.35.0 | High |
| CVE-2026-59196 / GHSA-fr4h-3cph-29xv | pnpm hoisted install の lockfile alias path traversal。 | pnpm <10.34.4, >=11.0.0 <11.7.0 | High |
| CVE-2026-59194 / GHSA-72r4-9c5j-mj57 | pnpm patch-remove が patches dir 外の file を削除しうる。 | pnpm <10.34.4, >=11.0.0 <11.7.0 | High |
| CVE-2026-55487 / GHSA-5wx6-mg75-v57r | pnpm allowBuilds の manifest identity spoof。 | pnpm <10.34.2, >=11.0.0 <11.5.3 | High |
| CVE-2026-4800 / GHSA-r5fr-rjxr-66jc | lodash `_.template` imports key names 経由の code injection。 | lodash/lodash-es >=4.0.0 <=4.17.23, lodash.template <4.18.0 | High |
| CVE-2026-53571 / GHSA-fx2h-pf6j-xcff | Windows で公開 Vite dev server の `server.fs.deny` bypass。 | vite <=6.4.2, >=7.0.0 <=7.3.4, >=8.0.0 <=8.0.15 | High |

## Cloude 横断メモ
- SkiresortWebPlan: `main` f076f36 を監査。root / Nanako web / Sichinohe web は `next@16.2.9` で Next.js July 2026 の修正版 16.2.11 未満。npm audit は `sharp@0.34.5` High、dev tooling の `js-yaml` High / `brace-expansion` High を検出。
- SPRAY: `main` 5490f7b を監査。`apps/web` は lockfile 上 `next@15.5.18` で修正版 15.5.21 未満。pnpm audit は `sharp@0.34.5` High、`js-yaml@4.1.1` High、`brace-expansion@1.1.14/5.0.6` High を検出。root の `packageManager` は `pnpm@9.15.0` で pnpm High advisories の fixed range 未満。
- POWDER: `main` e034f9c を監査。npm audit は 0 件。`lodash@4.18.1` は lodash CVE-2026-4800 の fixed range。
- JAPOWSERCH: `momentum-create/JAPOWSERCH` / `Seeker-x1/JAPOWSERCH` は今回も GitHub で解決できず、npm audit 未実行。
- WebTest: `momentum-create/WebTest` / `Seeker-x1/WebTest` は今回も GitHub で解決できず、npm audit 未実行。

## 次アクション
→ vuln-impact-analyst

intel complete -> next: vuln-impact-analyst
