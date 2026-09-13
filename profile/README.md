# katalalab

### katalalabへようこそ

katalalabは、AIが生成した判断や出力の検証可能性と実行規律を探求するオープンソースプロジェクト群です。モデルの規模拡大に伴う不確実性に対し、出力の検証性や規律ある運用の実現に向けた技術的アプローチを独立した立場から追究しています。

### やりたいこととリポジトリ一覧

| 目的 | リポ | 使いどころ | 実装範囲 |
| :--- | :--- | :--- | :--- |
| エージェントのツール実行や判断の妥当性を外部から検査したい | [katala-trust](https://github.com/katalalab/katala-trust) | ツール実行前の判定推奨取得、有害入力の検査 | 検証エンジンとエージェント接続アダプタの実装 |
| 回答文にエビデンスや特定の禁忌情報をラベル付けしたい | [katala-slm](https://github.com/katalalab/katala-slm) | 専門回答への根拠情報付与、警告ラベル付与の試作 | 推論APIとキーワードによる禁忌検査の実装（臨床判断用ではない） |
| Web検索と手元のコードベースを横断して調査ログを整理したい | [katala-web-research](https://github.com/katalalab/katala-web-research) | 調査結果の手元保存、エージェント向け検索インターフェース | CLIおよびMCPサーバーとしての収集・レポート生成機能の実装 |
| 複数環境や複数エージェントで指示ファイルの改変を検知したい | [katala-os](https://github.com/katalalab/katala-os) | エージェント設定の参照一元化、指示ファイルの変更検知 | 基準ファイルのハッシュ検知と同期スクリプトのひな型仕様 |
| データ圧縮のアルゴリズムを処理層ごとに分解して実験したい | [codec-lab](https://github.com/katalalab/codec-lab) | 各処理層の圧縮効果測定、可逆コーデックの試作 | 処理層モジュールと往復一致テストの実装 |
| 許可ドメインに限定してブラウザ操作の呼び出しを検査したい | [secure-browser-agent](https://github.com/katalalab/secure-browser-agent) | プロファイル分離による巡回、呼び出し先URLの制限 | ポリシー定義とCLI経由のブラウザ起動制御の実装 |

### katalalabの原則

公開リポジトリでは、環境固有データや秘密情報の混入を防ぐ運用を意図し、開かれた設計と実装の共有を目指しています。すべての成果物は、誇大な主張を避け、確認できた事実と実装範囲に基づいて公開する方針をとっています。

## 検証記録 — 2026-08-28（過去の記録）

| Repository | Observed local gate |
| --- | --- |
| katala-slm | Rust format, check, strict clippy, 56 tests |
| katala-trust | Typecheck, 149 core tests, 65 gateway tests, 30/30 trust eval |
| katala-web-research | 128 tests, Ruff, mypy, CLI and research-quality checks |
| katala-os | 2 manifest artifacts and 10 skills verified |
| Theorquen | Workspace format, strict clippy, and tests; cross-platform leaf-name regression covered |
| codec-lab | 11 round-trip tests and identical ratios on 6 nodes; per-node speed remains separate |
| secure-browser-agent | 466 tests plus strict compact-command and MCP smoke gates |
| minecraft-coexistence-bench | Documentation only; no executable gate yet |

These are commit-local observations, not release certification or cross-machine performance claims.

## What is not here

Katala's product R&D, the fleet's own operational records, and anything naming a
real machine, account, or address stay private. This organisation publishes reusable
shape; it is not a mirror of the working environment.

## Publishing rule

Repositories here are built clean-room against an **allowlist** — only what has been
confirmed publishable is copied in. Flipping an existing private repository to public
is not how anything gets here: history outlives redaction, and a single clone makes
the decision permanent.

Every public repository runs the instance-data gate in CI:

```yaml
jobs:
  no-instance-data:
    uses: katalalab/.github/.github/workflows/instance-data-gate.yml@main
```

The gate refuses real home paths (both POSIX and Windows spellings), private and
tailnet addresses, credential shapes, account identifiers, webhook endpoints, host
inventories, and dated first-person observations. It ships with canaries in both
directions, and those run before the scan — a pattern that has stopped matching
looks exactly like a clean tree otherwise.

A repository whose subject matter *is* something a scan looks for declares the
exception in a tracked `.instance-data-allow`, scoped to that one scan. Exemptions
arrive through a diff someone reads, and the gate prints how many it honoured.

An exposure judgement is never made by one reviewer. Two independent engines have to
agree, because a single pass has already returned "no findings" on a tree that a
second pass found a behavioural profile in.

## Licence

Per repository. `katala-os` is MIT.
