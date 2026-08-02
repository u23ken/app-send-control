# 既知の問題

English KNOWN_ISSUES: [KNOWN_ISSUES.md](KNOWN_ISSUES.md)

## インストール

- `/Applications/Send Control.app` が既に存在する場合、別フォルダのコピーを起動してもインストール済みのアプリにリダイレクトされます。
- 同じ bundle identifier のインスタンスは 1 つしか動作できません。2 つ目を起動すると自動終了します。

## 権限

- アクセシビリティと入力監視の両方が必要です。どちらかが欠けると event tap は OFF のままです。
- 権限設定を変更した直後は、アプリの終了と再起動が必要になる場合があります。

## アプリの互換性

- 対象アプリによっては、Return と Shift+Return の扱いが異なるため、動作に差が出ることがあります。
- modifyOtherKeys や kitty protocol を使用するターミナルアプリでは、ターミナル安全モードで自動的にリマップされます（AppTreatment で管理）。

## 未対応

- Mac App Store での配布は技術的に不可能です。CGEvent tap にはアクセシビリティ権限が必要ですが、App Sandbox 内では使用できません。
- 自動アップデート機能はありません。更新は [GitHub Releases](https://github.com/u23ken/app-sendcontrol/releases) を確認してください。
