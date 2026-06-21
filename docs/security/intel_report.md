# Intel Report - 2026-06-21

## 調査日時
2026-06-21T09:04:12Z

## 情報源
| 名称 | URL | 取得時刻 |
|------|-----|----------|
| Vercel - Next.js May 2026 security release | https://vercel.com/changelog/next-js-may-2026-security-release | 2026-06-21T09:04:12Z |
| React advisory - GHSA-rv78-f8rc-xrxh / CVE-2026-23870 | https://github.com/facebook/react/security/advisories/GHSA-rv78-f8rc-xrxh | 2026-06-21T09:04:12Z |
| Next.js advisory - GHSA-8h8q-6873-q5fj / CVE-2026-23870 | https://github.com/vercel/next.js/security/advisories/GHSA-8h8q-6873-q5fj | 2026-06-21T09:04:12Z |
| Next.js advisory - GHSA-267c-6grr-h53f / CVE-2026-44575 | https://github.com/vercel/next.js/security/advisories/GHSA-267c-6grr-h53f | 2026-06-21T09:04:12Z |
| Next.js advisory - GHSA-26hh-7cqf-hhc6 / CVE-2026-45109 | https://github.com/vercel/next.js/security/advisories/GHSA-26hh-7cqf-hhc6 | 2026-06-21T09:04:12Z |
| Next.js advisory - GHSA-mg66-mrh9-m8jx / CVE-2026-44579 | https://github.com/vercel/next.js/security/advisories/GHSA-mg66-mrh9-m8jx | 2026-06-21T09:04:12Z |
| Next.js advisory - GHSA-492v-c6pp-mqqv / CVE-2026-44574 | https://github.com/vercel/next.js/security/advisories/GHSA-492v-c6pp-mqqv | 2026-06-21T09:04:12Z |
| Next.js advisory - GHSA-c4j6-fc7j-m34r / CVE-2026-44578 | https://github.com/vercel/next.js/security/advisories/GHSA-c4j6-fc7j-m34r | 2026-06-21T09:04:12Z |
| Next.js advisory - GHSA-36qx-fr4f-26g5 / CVE-2026-44573 | https://github.com/vercel/next.js/security/advisories/GHSA-36qx-fr4f-26g5 | 2026-06-21T09:04:12Z |
| Node.js - Thursday, June 18, 2026 Security Releases | https://nodejs.org/en/blog/vulnerability/june-2026-security-releases | 2026-06-21T09:04:12Z |
| Node.js release v22.23.0 | https://nodejs.org/en/blog/release/v22.23.0 | 2026-06-21T09:04:12Z |
| Node.js release v24.17.0 | https://nodejs.org/en/blog/release/v24.17.0 | 2026-06-21T09:04:12Z |
| Node.js release v26.3.1 | https://nodejs.org/en/blog/release/v26.3.1 | 2026-06-21T09:04:12Z |
| undici advisory - GHSA-vxpw-j846-p89q / CVE-2026-12151 | https://github.com/nodejs/undici/security/advisories/GHSA-vxpw-j846-p89q | 2026-06-21T09:04:12Z |
| undici advisory - GHSA-hm92-r4w5-c3mj / CVE-2026-6734 | https://github.com/nodejs/undici/security/advisories/GHSA-hm92-r4w5-c3mj | 2026-06-21T09:04:12Z |
| lodash advisory - GHSA-r5fr-rjxr-66jc / CVE-2026-4800 | https://github.com/lodash/lodash/security/advisories/GHSA-r5fr-rjxr-66jc | 2026-06-21T09:04:12Z |
| GitHub Advisory Database - npm High since 2026-06-01 | https://github.com/advisories?query=ecosystem%3Anpm+severity%3Ahigh+published%3A%3E2026-06-01 | 2026-06-21T09:04:12Z |
| SkiresortWebPlan repo manifest check | https://github.com/Seeker-x1/SkiresortWebPlan | 2026-06-21T09:04:12Z |
| SPRAY repo manifest check | https://github.com/momentum-create/spray | 2026-06-21T09:04:12Z |
| POWDER repo manifest check | https://github.com/momentum-create/POWDER | 2026-06-21T09:04:12Z |

## 新規 / 更新 advisory
| ID | 概要 | 影響パッケージ | ベンダー深刻度 |
|----|------|----------------|----------------|
| Node.js Jun 18 2026 / CVE-2026-48933 | WebCrypto AES integer overflow により `subtle.encrypt()` 入力条件次第でプロセス abort / DoS。 | Node.js 22.x, 24.x, 26.x（公式リリース: 22.23.0 / 24.17.0 / 26.3.1） | High |
| Node.js Jun 18 2026 / CVE-2026-48618 | Unicode dot separator の hostname 正規化差異により TLS wildcard-depth 認証境界を迂回し得る。 | Node.js 22.x, 24.x, 26.x（公式リリース: 22.23.0 / 24.17.0 / 26.3.1） | High |
| Node.js Jun 18 2026 / CVE-2026-48615, CVE-2026-48619, CVE-2026-48928, CVE-2026-48930, CVE-2026-48934, CVE-2026-48937 他 | proxy credential leak、HTTP/2 memory growth / cleanup、TLS/mTLS hostname handling、permission model bypass 等の同時修正。 | Node.js 22.x, 24.x, 26.x（一部 CVE は特定 line のみ） | Medium / Low |
| GHSA-vxpw-j846-p89q / CVE-2026-12151 | undici WebSocket client が fragment 数を制限せず、悪意ある WebSocket server により memory exhaustion / DoS。 | undici `>=6.17.0 <6.27.0`, `>=7.0.0 <7.28.0`, `>=8.0.0 <8.5.0` | High |
| GHSA-hm92-r4w5-c3mj / CVE-2026-6734 | undici `Socks5ProxyAgent` の pool reuse により cross-origin request routing / credential leakage の可能性。 | undici `>=7.23.0 <7.28.0`, `>=8.0.0 <8.2.0` | High |
| Vercel Next.js May 2026 coordinated release | Next.js 13 advisories（DoS、middleware/proxy bypass、SSRF、cache poisoning、XSS）。Vercel は WAF では完全緩和不可、patch が完全緩和と明記。 | Next.js 13.x/14.x all, 15.x `<=15.5.17`, 16.x `<=16.2.5`; react-server-dom-* 19.0/19.1/19.2 affected ranges | High / Moderate / Low |
| GHSA-rv78-f8rc-xrxh / CVE-2026-23870 | React Server Components の server function endpoint に crafted request を送ることで CPU / memory resource exhaustion。 | `react-server-dom-webpack`, `react-server-dom-parcel`, `react-server-dom-turbopack` 19.0.0-19.0.5, 19.1.0-19.1.6, 19.2.0-19.2.5 | High |
| GHSA-8h8q-6873-q5fj / CVE-2026-23870 | Next.js App Router Server Function endpoint 経由の Server Components DoS（React upstream issue の Next.js downstream advisory）。 | `next >=13.0.0 <15.5.16`, `>=16.0.0 <16.2.5`（Vercel aggregate は 15.5.18 / 16.2.6 を推奨） | High |
| GHSA-267c-6grr-h53f / CVE-2026-44575 | App Router segment-prefetch route variant により middleware/proxy authorization bypass。 | `next >=15.2.0 <15.5.16`, `>=16.0.0 <16.2.5` | High |
| GHSA-26hh-7cqf-hhc6 / CVE-2026-45109 | CVE-2026-44575 の incomplete fix follow-up。`middleware.ts` + Turbopack に fix が適用されない。 | `next >=15.2.0 <15.5.18`, `>=16.0.0 <16.2.6` | High |
| GHSA-mg66-mrh9-m8jx / CVE-2026-44579 | Cache Components / Partial Prerendering 利用時の connection exhaustion DoS。 | `next >=15.0.0 <15.5.16`, `>=16.0.0 <16.2.5` | High |
| GHSA-492v-c6pp-mqqv / CVE-2026-44574 | Dynamic route parameter injection による middleware/proxy authorization bypass。 | `next >=15.4.0 <15.5.16`, `>=16.0.0 <16.2.5` | High |
| GHSA-c4j6-fc7j-m34r / CVE-2026-44578 | Built-in Node.js server self-hosting + WebSocket upgrade handling で SSRF。Vercel-hosted deployments は advisory 上 not affected。 | `next >=13.4.13 <15.5.16`, `>=16.0.0 <16.2.5` | High |
| GHSA-36qx-fr4f-26g5 / CVE-2026-44573 | Pages Router + i18n + middleware/proxy auth で protected page data を迂回取得可能。 | `next >=12.2.0 <15.5.16`, `>=16.0.0 <16.2.5` | High |
| GHSA-r5fr-rjxr-66jc / CVE-2026-4800 | lodash `_.template` の `options.imports` key name 経由 code injection。 | `lodash`, `lodash-amd`, `lodash-es` `>=4.0.0 <=4.17.23`; `lodash.template >=4.0.0 <4.18.0` | High |

## Cloude 横断メモ
- SkiresortWebPlan: read-only manifest check では root / NanakoCyoueiSki/web / resorts/Sichinohe-CyoueiSki/web が `next@16.2.9`, `react@19.2.7`。今回取得した Next.js / React High ranges には該当しない見込み。Node runtime は manifest だけでは確定不可（`engines.node >=20`）。本番が Node 22 < 22.23.0、24 < 24.17.0、26 < 26.3.1、または EOL line の場合は High + AFFECTED として incident 推奨。
- SPRAY: `apps/web` は package range が `next ^15.1.0` だが `pnpm-lock.yaml` 上は `next@15.5.18` / `react@19.2.6`。Vercel aggregate の推奨下限を満たすため、Next.js / React RSC advisories は現時点で NOT_AFFECTED 見込み。直接 `undici` dependency は lock 上確認できず。Node runtime は L1 で確認。
- POWDER: `package.json` name は `japowserch`。read-only lock check では `lodash@4.18.1`、Next.js / React / undici direct dependency は確認できず。GHSA-r5fr-rjxr-66jc は NOT_AFFECTED 見込み。Node runtime は L1 で確認。
- JAPOWSERCH: standalone repo は今回の GitHub repo search でも特定できず。POWDER の package name が `japowserch` であるため、別 repo / deploy unit が存在する場合は manifest URL を L1 に渡す必要あり。
- WebTest: repo は今回の GitHub repo search で特定できず。Next.js / React / Node runtime / undici / lodash の manifest 確認が未完了のため、L1 で inventory 要確認。
- Critical / High + AFFECTED の扱い: 今回の L0 では manifest から明確な app dependency AFFECTED は確認できない。Node runtime が affected line/version と判明した場合、または未確認 WebTest/JAPOWSERCH が上記 affected ranges に該当した場合のみ incident 推奨を記載する。

## 次アクション
- vuln-impact-analyst: Node.js runtime versions（Vercel / Docker / CI / production）を SkiresortWebPlan, SPRAY, POWDER, WebTest, JAPOWSERCH で確認。
- vuln-impact-analyst: WebTest / standalone JAPOWSERCH の正式 repo/deploy unit を解決し、manifest / lockfile に対して上記 advisory ranges を照合。

intel complete -> next: vuln-impact-analyst
