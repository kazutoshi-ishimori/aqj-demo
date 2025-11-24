## Why
AQ日本語版（一般成人用）の50問アンケートを、モバイル端末でも負担が少ない形で回答できるようにしたい。
Six Degrees のモバイル調査デザインガイドが推奨する「短い設問テキスト」「一問一画面」「縦方向の選択肢」「画像を減らす」「複数端末での検証」などのベストプラクティスに沿って、複数のUIパターン（ドロップダウン形式・一問一回答形式・カルーセル形式）のデモを用意し、GitHub Pages上で比較検証できるようにすることが目的である。  
参照: `https://www.six-degrees.com/effective-mobile-survey-design-for-market-research/`

Qualtrics および Questant のマトリクス質問スマホ表示ガイドが示すように、PC向けの横長マトリクス表をそのままスマホに流用すると可読性・操作性が低下するため、AQ-J もモバイル前提のレイアウトに再設計する必要がある。  
参照: `https://www.qualtrics.com/support/jp/survey-platform/survey-module/editing-questions/question-types-guide/standard-content/matrix-table/`  
参照: `https://help.questant.jp/hc/ja/articles/900005430346-%E3%83%9E%E3%83%88%E3%83%AA%E3%83%83%E3%82%AF%E3%82%B9-%E3%82%B9%E3%83%9E%E3%83%9B%E5%90%91%E3%81%91%E3%83%87%E3%82%B6%E3%82%A4%E3%83%B3`

## What Changes
- AQ日本語版成人用50問アンケートを、静的HTML/CSS/JSのみで構成されたWebフォームとして実装可能にするための仕様を追加する。
- 3種類のモバイル向けデモフォームを用意し、それぞれ別ファイルとしてGitHub Pages上から直接アクセスできるようにする。
  - ドロップダウン選択形式（1ページに50問、各問はプルダウン）
  - 一問一回答方式（1画面に1問＋縦方向のラジオボタン）
  - カルーセル方式（スワイプ/次へボタンで横に遷移する1問表示のスライド形式）
- いずれの形式も、横スクロール不要・縦方向の操作で完結し、タップターゲットと文字サイズがスマホで十分な可読性/操作性を持つことを要件化する。
- 3つのデモはいずれも、AQ_Adult_Japanese.md に定義された設問文・選択肢・順序を忠実に再現し、回答スケール（1〜4）の意味づけを保持する。

## Impact
- Affected specs:
  - 新規: `specs/aqj-web-questionnaire/spec.md`（AQ日本語版Webアンケートおよび3種デモフォームの能力を追加）
- Affected code:
  - 静的プロトタイプ（例）:
    - `aqj-dropdown.html`（ドロップダウン形式）
    - `aqj-single-question.html`（一問一回答形式）
    - `aqj-carousel.html`（カルーセル形式）
    - 共通スタイル/スクリプト: `aqj.css`, `aqj.js` など


