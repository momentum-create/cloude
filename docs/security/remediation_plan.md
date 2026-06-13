# Remediation Plan - CVE-2026-23870 / Next.js May 2026 Security Release

## 参照
- 調査日時: 2026-06-13T12:00:00+09:00
- 主要 advisory:
  - CVE-2026-23870 / GHSA-rv78-f8rc-xrxh (React Server Components DoS) - High
  - GHSA-8h8q-6873-q5fj - https://github.com/vercel/next.js/security/advisories/GHSA-8h8q-6873-q5fj
  - GHSA-26hh-7cqf-hhc6 (Middleware bypass follow-up) - High
  - Vercel 統合リリース - https://vercel.com/changelog/next-js-may-2026-security-release
  - Next.js v16.2.6 - https://github.com/vercel/next.js/releases/tag/v16.2.6
- 目標修正版:
  - next: **16.2.6** (現行 16.2.4)
  - react / react-dom: **19.2.6** (現行 19.2.4)
  - eslint-config-next: **16.2.6**

## スコープ

### 対象 (incident / AFFECTED High)
| デプロイ単位 | パス | Git リポジトリ | 現行 | 目標 |
|-----------|------|--------------|------|------|
| SkiresortWebPlan ルート | SkiresortWebPlan/ | momentum-create/SkiresortWebPlan | 16.2.4 | 16.2.6 |
| Nanako web | NanakoCyoueiSki/web/ | 同上 | 16.2.4 | 16.2.6 |
| Sichinohe web | resorts/Sichinohe-CyoueiSki/web/ | 同上 | 16.2.4 | 16.2.6 |
| primecarwash-site | primecarwash-site/ | Seeker-x1/PrimeCarWash | 16.2.4 | 16.2.6 |

編集: package.json + package-lock.json (各デプロイ単位)

### 対象外 (monitor)
- WebTest: next 16.2.6 済み
- SPRAY: next 15.5.18 済み
- JAPOWSERCH lodash / Node.js 6/17 予告

## Pre-flight
- [ ] ブランチ: security/CVE-2026-23870
- [ ] ロールバック HEAD: SkiresortWebPlan c2ebbf5 / primecarwash f5b807e
- [ ] Vercel Preview 確認後に本番
- [ ] シークレットローテーション不要

## 修正手順

### Phase 1: SkiresortWebPlan ルート [implementer]
1. next/react/react-dom/eslint-config-next -> 16.2.6 / 19.2.6
2. ローカルのみ npm install で lock 更新 (CI/Vercel は npm ci)
3. npm run build && npm audit --audit-level=high
4. push -> Preview

### Phase 2: NanakoCyoueiSki/web [implementer]
- Phase 1 と同様、独立 lock を更新

### Phase 3: Sichinohe-CyoueiSki/web [implementer]
- Phase 2 と同様
- vercel.json installCommand: npm ci は維持
- @vercel/blob moderate は別チケット

### Phase 4: primecarwash-site [implementer]
- 別リポ Seeker-x1/PrimeCarWash で同様の更新

### Phase 5: 本番デプロイ
- Preview smoke 合格後、リポごとに main マージ
- 順序: ルート -> Nanako -> Sichinohe -> primecarwash

## ダウンタイム
- パッチリリースのみ、メジャーアップグレードではない
- CI/Vercel は npm ci 準拠

## 代替控制 (パッチ遅延時のみ、期限 2026-06-20)
- レート制限 / WAF
- 完全緩和は不可、パッチ必須

## ロールバック
```bash
# SkiresortWebPlan
git checkout c2ebbf5 -- package.json package-lock.json
git checkout c2ebbf5 -- NanakoCyoueiSki/web/package.json NanakoCyoueiSki/web/package-lock.json
git checkout c2ebbf5 -- resorts/Sichinohe-CyoueiSki/web/package.json resorts/Sichinohe-CyoueiSki/web/package-lock.json

# primecarwash-site
git checkout f5b807e -- package.json package-lock.json
```

## 検証 (vuln-verify-auditor)
- [ ] npm ci 成功
- [ ] npm audit --audit-level=high exit 0
- [ ] npm ls next react react-dom -> 16.2.6 / 19.2.6
- [ ] npm run build 成功
- [ ] Security audit workflow 緑
- [ ] Smoke: / と主要ルート

## リスク接受
| 項目 | 期限 |
| PostCSS moderate | 2026-07-13 |
| Node.js 6/17 | リリース後 |

plan ready -> implementer: vuln-patch-implementer (「実装して」で実行)