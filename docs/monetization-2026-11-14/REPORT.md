# food-waste-guide 収益化改善報告（2026年11月14日）

作業ブランチ：`improve/monetization-2026-11-14`。mainへのマージ・本番公開は未実施です。
既存サイトの修正です。公開中のデザイン、広告コード、Tracking ID、解析IDを保持。順位・AIO引用・成果発生は検証できていません。

## 優先問題と変更

3機種比較で生ごみ量・年間費用・型番の比較を補足。神奈川補助金記事に申請確認表を追加。404になっていた横須賀市PDF2URLを現行公式案内へ置換し、予算上限間近の告知を反映。

横須賀市の公式案内は2026年11月10日更新。2026年11月14日閲覧で、予算の残りが少なく受付できない可能性を確認。補助対象の取り違えや交付を前提にした購入を避ける案内を追加。

## 本文を充実した既存記事

文字数はHTMLからscript/styleと空白を除いた概算で、評価指標ではありません。文字数のための水増しはしていません。

| 記事（公開ディレクトリからの相対パス） | 本文概算・改善前 → 改善後 |
| --- | --- |
| `kanagawa-subsidy.html` | 941 → 1593 |
| `model-comparison.html` | 1542 → 2181 |

パンくずを追加した記事は、その表示内容に合うBreadcrumbListを設定。既存のArticleとcanonicalは照合済みです。架空のReview・AggregateRating・Offerは新設していません。購入者レビュー10本文以上を個別確認できた商品は0件で、レビュー要約は追加していません。価格・仕様の古い確認日を一律に新しくしていません。

## 検証結果

- 静的検証：10ページ（404含む）、エラー0。タイトル・description・h1、canonical、サイトマップ、内部リンク・アンカー・参照資産、JSON-LD、重複タイトル・canonical、トップからの到達性を点検。
- サイトマップ：8URL。noindexとの整合を検証。robots.txtは既存のクロール許可と本番Sitemap指定を維持。
- ブラウザ：360・390・1440pxの30ケース。ページ横はみ出し0。外部広告・解析への通信は遮断。画像の実配信や計測通信の成功を意味しません。
- 改善前の横はみ出し：0ケース → 改善後0ケース。
- 広告保全：リンク・広告画像のHTML断片18個をSHA-256照合、一致。`scripts/affiliate-baseline.json`が修正前の基準です。既存Tracking ID：moon12-22。
- 外部参照先：21URLをHTTP GETで点検。未確認・差し替え前404を含む応答記録は`external-links.json`参照。403/503はリンク切れと断定しません。
- 公開状態：本番の既存ページ・robots・sitemapは200、無効URLは404。ブランチの改善は本番未反映です。
- 表示速度：メダカでは外部画像6リクエストを除去。他サイトを含む本番CWV・Lighthouse・実ユーザーLCP/INP/CLSは未測定。高速化の数値効果は主張しません。

静的HTMLサイトのためビルド工程はありません。

## 未確認事項・公開前の判断

機種比較ページは既存noindexです。商品ASINの本体・色・セット照合が未完了なので、今回解除せずサイトマップから除外。全自治体の最新予算・受付・Amazon領収書対応は未確認です。既存構成の広告はAmazonで、A8コードはありません。A8案件を推測で新設していません。

共通：Amazonの商品ページの現在の表示・レビュー本文10件、A8管理画面の提携・成果対象・掲載URL、Search Consoleのクエリ別表示回数・CTR・順位、Cloudflare実測速度、実際の成果計測は未確認。広告をテスト購入・申込する検証は行っていません。既存の商品画像は、A8バナー・イメージ・メーカー参照を区別。新しい未許諾写真を追加していません。

## 全ページの診断台帳

`page-audit.json`にtitle/h1/description/canonical・index可否・サイズ・リンク数・構造化データ・到達性を保存。全ページに一律のタイトル変更はせず、検索意図が重なる販売年違いを区別し、問題のある記事とUIを優先しました。トップから到達できないindex許可ページ・内部リンク切れ・完全なタイトル重複は検証後0件。記事の統合・削除はしていません。

| ページ | 検索設定 | 本文概算 | 内部リンク先数 | 広告リンク・画像数 | 構造化データ |
| --- | --- | ---: | ---: | ---: | --- |
| `about.html` | index許可 | 380 | 3 | 0 | AboutPage |
| `index.html` | index許可 | 1365 | 9 | 6 | WebSite |
| `subsidy-guide.html` | index許可 | 4002 | 6 | 2 | Article, BreadcrumbList |
| `ppc15-electricity-cost.html` | index許可 | 1849 | 5 | 2 | Article, FAQPage, BreadcrumbList |
| `food-waste-dryer-checklist.html` | index許可 | 1669 | 7 | 2 | Article, BreadcrumbList |
| `kanagawa-subsidy.html` | index許可 | 1593 | 5 | 2 | Article, BreadcrumbList |
| `model-comparison.html` | noindex | 2181 | 6 | 2 | Article, BreadcrumbList |
| `404.html` | noindex | 63 | 1 | 0 |  |
| `privacy.html` | index許可 | 399 | 3 | 0 | WebPage |
| `ebina-subsidy.html` | index許可 | 771 | 5 | 2 | Article, BreadcrumbList |

## 再実行・差分の確認

- `python scripts/check_site.py .`（Python標準ライブラリのみ）
- 全差分：`git diff main...improve/monetization-2026-11-14`
- 本番へのマージ・デプロイは別途承認後。プレビュー環境が自動生成されても本番とは区別。
- 公開後はcanonical・サイトマップの実応答、Search Consoleの除外理由、記事→広告クリック→成果を確認。変更前後で同じ期間・クエリを比較してください。
