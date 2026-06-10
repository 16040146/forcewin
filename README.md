# Forcewin 日本語サイト（forcewin-ict.jp）

Forcewin Electrical Contractor Pte. Ltd. の日本語コーポレートサイト（静的サイト）。
HTML / CSS / Vanilla JS のみ。ビルド不要・依存ゼロ。**GitHub Pages / Cloudflare Pages のどちらでも完全無料**で公開できます。

```
index.html      ... ページ本体
styles.css      ... スタイル
script.js       ... スクロール演出・カウンター・モバイルメニュー
CNAME           ... 独自ドメイン（GitHub Pages用）
.nojekyll       ... GitHub PagesのJekyll処理を無効化
robots.txt / sitemap.xml ... SEO
```

## ローカルで確認

```bash
cd /Users/stanley/GitHub/ForceWin
python3 -m http.server 8080
# ブラウザで http://localhost:8080 を開く
```

---

## 公開方法（独自ドメイン forcewin-ict.jp）

ドメインは取得済み。**ホスティングは無料**。おすすめは Cloudflare Pages か GitHub Pages。

### 案A：Cloudflare Pages（おすすめ・最速表示・商用OK）

1. GitHub にこのリポジトリを push（下記「GitHubへ push」参照）。
2. Cloudflare ダッシュボード → **Workers & Pages** → **Create** → **Pages** → **Connect to Git**。
3. リポジトリを選択。ビルド設定は **Framework preset: None**、Build command 空欄、Output directory `/`（ルート）。
4. デプロイ完了後、**Custom domains** タブで `forcewin-ict.jp` を追加。
5. ドメインのDNSを Cloudflare 管理にしている場合は自動でCNAMEが入る。外部DNSの場合は表示される **CNAME / A レコード** を、ドメイン管理画面に登録。
6. SSLは自動発行（数分〜数十分）。

> Cloudflare Pages を使う場合、`CNAME` ファイルは無視されて問題ありません（GitHub Pages専用のため）。

### 案B：GitHub Pages（最もシンプル・商用OK）

1. GitHub にこのリポジトリを push。
2. リポジトリ → **Settings** → **Pages** → Source を **Deploy from a branch** → `main` / `(root)` を選択 → Save。
3. **Custom domain** に `forcewin-ict.jp` を入力（リポジトリ内の `CNAME` ファイルが自動で使われます）。
4. ドメイン管理画面（お名前.com等）でDNSを設定：
   - `forcewin-ict.jp`（Apex）→ **A レコード** 4件：
     `185.199.108.153` / `185.199.109.153` / `185.199.110.153` / `185.199.111.153`
   - `www.forcewin-ict.jp` → **CNAME** → `<ユーザー名>.github.io`
5. Pages 設定で **Enforce HTTPS** にチェック（証明書発行後）。

---

## GitHub へ push（共通の前準備）

```bash
cd /Users/stanley/GitHub/ForceWin
git add -A
git commit -m "日本語モダンサイトを追加"

# GitHubで空のリポジトリを作成後：
git remote add origin https://github.com/<ユーザー名>/forcewin-jp.git
git push -u origin main
```

---

## 内容の編集

テキストはすべて `index.html` 内に直書きされています。会社概要・サービス項目・取引先・連絡先メールアドレスを書き換えるだけで更新できます。
現在の問い合わせ先メールは `info@forcewin.com.sg`（仮）。正しいアドレスがあれば `index.html` の `mailto:` を差し替えてください。
