# momentum.jp /contact（方向B）

写真主役の設計相談ページです。文言・UIはすべて**日本語**です。

## 構成

```
sites/momentum-jp-contact/
├── index.html          # / → /contact/ へ誘導
├── contact/index.html  # 相談ページ本体
├── styles.css
├── CNAME               # カスタムドメイン momentum.jp
├── images/hero.svg     # 仮画像（要差し替え）
└── README.md
```

公開URL: `https://momentum.jp/contact/`

## 公開前にやること

1. **代表写真を置く**  
   `images/hero.jpg` を追加し、`contact/index.html` の `<img src>` を `../images/hero.jpg` に変更

2. **フォーム受信を接続**  
   - Formspree: `action="https://formspree.io/f/YOUR_FORM_ID"` を実IDに変更  
   - または Googleフォームの iframe に差し替え

3. **GitHub Pages**  
   - このフォルダ内容を Pages 用リポジトリのルートに置く（推奨）  
   - または本リポジトリで Pages の公開フォルダを `sites/momentum-jp-contact` に設定

4. **DNS**  
   `momentum.jp` の A / CNAME を GitHub Pages に向ける  
   （GitHub の Docs: Configuring a custom domain）

## デザインメモ

- PC: 左写真 / 右フォーム
- SP: 写真 → 文言 → フォーム
- フォント: Shippori Mincho + Zen Kaku Gothic New
- 趣味・SNSリンク集・カードUIは置かない
