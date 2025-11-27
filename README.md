## AQ-J モバイル回答デモ

AQ 日本語版（一般成人用・50問）の回答体験を、モバイルフレンドリーな 3 形式で比較検証するための静的プロトタイプ集です。

- `web/aqj-dropdown.html` — プルダウン選択形式（10問単位のセクションで折りたたみ）
- `web/aqj-single-question.html` — 50問を1ページに縦スクロール表示＋進捗バーと回答ドット
- `web/aqj-carousel.html` — 横スワイプ／ボタン操作のカルーセル形式

共通のスタイルとデータ (`web/aqj.css`, `web/aqj.js`) のみを利用し、GitHub Pages などの静的ホスティングにそのまま配置できます。  
ページを開いた瞬間に Q1 から回答でき、全 50 問を埋めると回答サマリー（テーブル＋テキスト）が表示されます。サマリーはコピーしてメモ等に貼り付けられます。

### ローカルプレビュー

```bash
# 例: VS Code の Live Server / `npx serve` など任意の静的サーバで web/ を公開
cd web
npx serve
```

`http://localhost:3000/aqj-dropdown.html` のように各ファイルへ直接アクセスしてください。

### GitHub Pages への配置

1. `web/` ディレクトリをリポジトリの公開ブランチ（例: `gh-pages`）に含める。
2. GitHub Pages 設定でルートを `/(root)` または `/web` に設定。
3. 公開 URL（例: `https://<org>.github.io/aqj-demo/web/aqj-carousel.html`）を QA 参加者へ共有。

> 3 ファイルとも直リンクで開けるようにし、比較テスト時は各 URL をそのまま配布します。

#### Actions による自動デプロイ

- `.github/workflows/deploy-gh-pages.yml` を有効にすると、`main` ブランチへ push するたびに `web/` 以下が GitHub Pages へ自動デプロイされます。
- GitHub リポジトリの設定で Pages のソースを「GitHub Actions」に変更してください。
- デプロイ後は `https://<org>.github.io/aqj-demo/` にある `index.html` から各デモへアクセスできます。

### 想定シナリオ

- UX研究/ユーザビリティテストで 3 形式を A/B/C 比較。
- モバイル画面幅（320〜414px）で横スクロールが不要かどうかの確認。
- 選択肢タップ領域・テキストサイズ・進捗把握のしやすさを被験者にヒアリング。
- 「回答を確認」ボタン押下時に、未回答が自動ハイライトされることを検証。

### 回答フロー

1. ページ表示直後から Q1 が操作可能（氏名などの事前入力は無し）。
2. 各設問の回答はブラウザメモリにのみ保持され、戻る/進むを繰り返しても失われません。
3. 「回答を確認」または最後の質問の確定で、全バリアント共通のサマリーを表示。未回答があっても一覧を開け、件数と該当Qが明示され、ワンクリックで未回答位置へ戻れます。
4. サマリーは50問ぶんのテーブルに統一しており、必要なときはブラウザ標準のコピーで転記してください（テキストエリア／専用コピー操作は廃止）。
5. 「リセット」を押すと全回答が消去され、Q1からやり直しになります（サーバ送信は一切無し）。

### 既知の制約

- サーバサイド保存やスコア算出は実装しておらず、ブラウザ内の一時状態のみ保持します（ページを再読み込みすると消えます）。
- 途中保存やファイル出力は範囲外（必要に応じて別変更で対応予定）。
- 実機検証は iOS Safari / Android Chrome での目視を前提にしています。

### テスト観点メモ

- 各形式で 50 問すべてが表示され、スケール（1〜4）の意味づけが保持されていること。
- Dropdown: 10問単位のセクションが折りたため、不要なブロックを閉じてスクロール量を調整できる。
- Single-question: 進捗バー・回答済みドット・残り問数が同期して更新される。
- Carousel: ヘッダーの「現在の質問番号/全体」が常時表示され、スワイプとボタンどちらでも遷移できる。
- 3 形式すべてで「回答を確認」操作時に未回答が自動的にハイライトされる。
- サマリー表示後でも各質問に戻って再編集できる。
- すべての形式でラジオ/ドロップダウンは縦方向に並び、横スクロールが発生しない。

### 参考ガイドライン

- [Six Degrees – Effective Mobile Survey Design for Market Research](https://www.six-degrees.com/effective-mobile-survey-design-for-market-research/)
- [Qualtrics – マトリクス質問のモバイル表示ガイド](https://www.qualtrics.com/support/jp/survey-platform/survey-module/editing-questions/question-types-guide/standard-content/matrix-table/)
- [Questant – マトリクス・スマホ向けデザイン](https://help.questant.jp/hc/ja/articles/900005430346-%E3%83%9E%E3%83%88%E3%83%AA%E3%83%83%E3%82%AF%E3%82%B9-%E3%82%B9%E3%83%9E%E3%83%9B%E5%90%91%E3%81%91%E3%83%87%E3%82%B6%E3%82%A4%E3%83%B3)


