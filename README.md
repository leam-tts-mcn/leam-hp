# LEAM Corporate Site

株式会社LEAM コーポレートサイト（https://leam.co.jp/）

- `index.html` … サイト本体（1ファイル完結SPA・パス方式ルーティング）**←唯一の編集対象**
- `service/ member/ company/ contact/ privacy/` … gen_routes.py が index.html から自動生成する複製（ページ別のtitle/OGP/canonical焼き込み済み）。**手で編集しない**
- `gen_routes.py` … 上記の生成スクリプト＋ sitemap.xml / robots.txt 生成
- `_redirects` … 未知パスをトップへ流すSPAフォールバック（実ファイル・実ディレクトリが常に優先）
- `mcn/` … MCNクリエイター募集LP（実ページ・独立運用）
- `line/` … （予約）公式LINE用の中継ページ置き場。別セッションで作成予定
- `ogp.png` / `favicon-32.png` / `apple-touch-icon.png` / `icon-512.png` … 画像・アイコン

## 更新方法（必ずこの順番）
1. `index.html` を差し替え・編集
2. `python3 gen_routes.py` を実行（ルート別複製とsitemapを再生成）
3. `git add -A && git commit && git push` → Netlifyが自動デプロイ（1〜2分で本番反映）

⚠️ gen_routes.py を実行し忘れると `/service` 等が古い本文のまま残る。push前に必ず実行すること。
⚠️ `netlify.toml` によるNetlifyビルドは**使わない**（2026-07-21にビルド起因で全ページ404の事故。ビルドレス＝静的ファイルのみのデプロイに固定）。

## 運用メモ
- 編集はClaude Codeセッション経由（leam_hp_renewal メモリ参照）
- URL構造：`/` `/service` `/member` `/company` `/contact` `/privacy`（旧 `#/xxx` はサイト内JSで自動転送）
