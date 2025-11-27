## MODIFIED Requirements
### Requirement: Completion validation and summary
AQ-J 各フォームは、全問回答を必須とする厳格な検証フローと、未回答があっても完了できるデモ用の緩いフローを両立させ、常に未回答数を利用者へ明示しなければならない（SHALL）。

#### Scenario: Strict validation remains available
- **WHEN** 本番向けなどの厳格モードが有効な場合
- **THEN** 未回答のまま完了しようとすると、これまで通り完了をブロックし、最初の未回答をハイライトしなければならない。

#### Scenario: Relaxed demo summary across variants
- **WHEN** いずれかの AQ-J バリアント（ドロップダウン／縦スクロール／カルーセル／1回答1画面）でサマリーを開いた場合
- **THEN** 未回答が残っていてもサマリーを開けるようにしなければならない
- **AND** サマリーのヘッダーで未回答数と該当する質問番号を明記しなければならない
- **AND** 各バリアントは、その場で編集に戻れる導線（例: セクションを自動展開、最初の未回答カードへスクロール、カルーセルで該当スライドをハイライト）を提示し、サマリーを閉じずに修正を再開できるようにする。

## ADDED Requirements
### Requirement: Step variant alternating focus cues
1回答1画面（ステップ）型は、質問が遷移したことを回答者が瞬時に把握できるよう、常に視覚的な切り替えの手がかりを示さなければならない（SHALL）。

#### Scenario: Alternating question background
- **WHEN** ステップ型が新しい質問カードを描画するとき
- **THEN** 奇数問題と偶数問題で、アクセシビリティに配慮した淡い背景色（またはアクセント枠）を交互に適用しなければならない
- **AND** 利用者が前後に移動した場合でも、現在表示中のカードが常に適切な色分けを維持し、色の違いだけで質問番号の奇遇が判断できるようにする。

### Requirement: Simplified summary presentation
AQ-J のすべてのバリアントは、コピー専用のテキストエリアや専用コピー操作を廃し、1つのサマリー表示に統一しなければならない（SHALL）。

#### Scenario: One summary per variant
- **WHEN** どのバリアントでもサマリーを開いたとき
- **THEN** 50問すべての回答（または「未回答」）を含む単一の一覧／テーブルのみを表示しなければならない
- **AND** 追加のプレーンテキスト用テキストエリアや専用「コピー」ボタンは表示せず、必要な場合はOS標準のコピー操作で対応できる状態にする。

