# Send Control のインストール

English INSTALL: [INSTALL.md](INSTALL.md)

## 動作要件

- macOS 13（Ventura）以降
- アクセシビリティおよび入力監視の権限

## 1. ダウンロードと検証

1. [GitHub Releases](https://github.com/u23ken/app-sendcontrol/releases) から `Send-Control-v*.zip` と `SHA256SUMS.txt` をダウンロードします。
2. ZIP の checksum を確認します。

```bash
shasum -a 256 "Send-Control-v*.zip"
```

3. 出力結果を `SHA256SUMS.txt` の値と比較します。

## 2. インストール

1. ダウンロードしたファイルを展開します。
2. `Send Control.app` を `/Applications/` に移動します。

## 3. アプリを開く

1. `/Applications/` の `Send Control.app` をダブルクリックします。
2. Developer ID で署名済み、Apple による公証（notarization）済みのため、Gatekeeper の警告なしで起動します。

## 4. 必要な権限を付与する

Send Control には、次の両方の権限が必要です。

1. `システム設定 > プライバシーとセキュリティ > アクセシビリティ`
2. `システム設定 > プライバシーとセキュリティ > 入力監視`

権限付与後に protection が自動で ON にならない場合は、アプリを再起動してください。

## 5. 動作確認

1. Send Control のメニューバーアイコンが表示されていることを確認します。
2. メニューバー項目を開き、protection が ON であることを確認します。
3. 対象アプリで Return と Shift+Return を試します。

## 6. アンインストール

1. メニューバーから Send Control を終了します。
2. `/Applications/` から `Send Control.app` を削除します。
3. 権限が不要になった場合は、アクセシビリティと入力監視のエントリも削除します。詳しくは [PRIVACY.md](PRIVACY.md) を参照してください。
