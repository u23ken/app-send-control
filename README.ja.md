<p align="center">
  <img src="SendControl/assets/sendcontrol-icon-macos-1024.png" width="128" height="128" alt="Send Control アイコン">
</p>

<h1 align="center">Send Control</h1>

<p align="center">
  macOS で日本語入力中に変換と間違えて Enter で文字が誤送信される問題を解決。<br>
  ChatGPT・Claude・Gemini など対象、設定不要。
  <br><br>
  <a href="README.md">English</a>
</p>

<p align="center">
  <a href="https://github.com/u23ken/app-sendcontrol/releases"><img src="https://img.shields.io/github/v/release/u23ken/app-sendcontrol" alt="Release"></a>
  <a href="https://github.com/u23ken/app-sendcontrol/releases"><img src="https://img.shields.io/github/downloads/u23ken/app-sendcontrol/total" alt="Downloads"></a>
  <a href="LICENSE"><img src="https://img.shields.io/github/license/u23ken/app-sendcontrol" alt="License"></a>
  <img src="https://img.shields.io/badge/macOS-13%2B-blue" alt="macOS 13+">
</p>

<p align="center"><img src="docs/screenshot.png" width="360" alt="Send Control メニュー"></p>

## こんな経験はありませんか？

ChatGPT・Claude・Gemini で日本語を入力中、変換を確定しようとして Enter キーを押したら、未完成のメッセージがそのまま送信されてしまった。

Send Control を入れるだけで、この誤送信のストレスを解消できます。無駄なトークン消費や、やり直しにかかる時間も節約できます。

## 仕組み

Send Control は Return キーと Shift+Return の動作を入れ替えます。

- **Return** → 改行（送信されない）
- **Shift+Return** → 送信

ChatGPT・Claude・Gemini のほか、Messenger など同様の問題が起きるアプリにも対応します。特定のアプリで入れ替えを無効にしたい場合は、メニューバーから除外リストに追加できます。

## ダウンロード

<a href="https://github.com/u23ken/app-sendcontrol/releases/latest">
  <strong>⬇ 最新版をダウンロード</strong>
</a>

## インストール

1. [Releases](https://github.com/u23ken/app-sendcontrol/releases) から `Send-Control-v*.zip` をダウンロード
2. 展開して `Send Control.app` を `/Applications/` に移動
3. 起動して 2 つの権限を付与:
   - **アクセシビリティ**（`システム設定 > プライバシーとセキュリティ > アクセシビリティ`）
   - **入力監視**（`システム設定 > プライバシーとセキュリティ > 入力監視`）

詳しい手順は [INSTALL.ja.md](INSTALL.ja.md) を参照してください。

## 特徴

- ON/OFF はメニューバーからワンクリック
- macOS のすべてのアプリでシステム全体に動作
- アプリごとに除外設定が可能
- 初回起動時に権限設定をガイド
- Gatekeeper 警告なしでインストール可能（Developer ID 署名・Apple 公証済み）
- シンプルを追求した設計。外部依存なし、常駐してもリソース消費は最小限

## 開発者向け

- CGEvent tap（`.defaultTap`）で Return (keyCode 36) と keypad Enter (76) を傍受し、Shift フラグを付け替え
- modifyOtherKeys / kitty protocol 対応のターミナル安全モード
- 約1400行、純粋な AppKit、外部依存なし
- Apache-2.0 ライセンス

## ドキュメント

| | English | 日本語 |
|---|---|---|
| インストール | [INSTALL.md](INSTALL.md) | [INSTALL.ja.md](INSTALL.ja.md) |
| プライバシー | [PRIVACY.md](PRIVACY.md) | [PRIVACY.ja.md](PRIVACY.ja.md) |
| 既知の問題 | [KNOWN_ISSUES.md](KNOWN_ISSUES.md) | [KNOWN_ISSUES.ja.md](KNOWN_ISSUES.ja.md) |
| クイックスタート | — | [QUICKSTART_BEGINNER.ja.md](QUICKSTART_BEGINNER.ja.md) |

## ライセンス

[Apache-2.0](LICENSE)
