# .github

このリポジトリは、katalalab組織全体で共通して利用される設定や公開ゲートウェイを管理するためのリポジトリです。組織の紹介ページのほか、公開リポジトリに環境固有データや秘密情報が混入していないかを検査する再利用可能なCIワークフローを提供しています。

配下の公開リポジトリにおいて環境固有データや機密情報の混入を呼び出し元のCI実行時に検査したい場面や、組織全体の公開ポリシーや共通の検証ルールを一元的に参照したい場面で活用できます。

本リポジトリの内容は組織プロフィールの記述とCIスキャンワークフローの定義に限られます。実際の検査スクリプト本体は別リポジトリで管理されており、すべての漏洩を技術的に防ぐことを保証するものではありません。

- `profile/README.md` — the organisation landing page.
- `.github/workflows/instance-data-gate.yml` — reusable publish-time gate. Public
  repositories call it instead of vendoring their own copy, so a blind spot found in
  one place closes everywhere.

The gate's implementation and canaries live in
[katala-os](https://github.com/katalalab/katala-os) under `scripts/`. This repository
only wires them up; edit them there.
