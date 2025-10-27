# Web Speech API デモ

Web Speech APIを使用した日本語テキスト読み上げデモサイト

## 概要

このプロジェクトは、ブラウザのWeb Speech API（Speech Synthesis）を使用して、テキストエリアに入力された日本語テキストを音声で再生するシンプルなデモアプリケーションです。

## 機能

- テキストエリアに日本語テキストを入力
- 「音声再生」ボタンをクリックして音声を再生
- デフォルトテキストが事前に入力済み
- 再生状態のリアルタイム表示（再生中、完了、エラー）
- ブラウザの対応状況チェック

## 技術スタック

- **HTML5**: 構造
- **CSS3**: スタイリング
- **JavaScript（バニラ）**: ロジック実装
- **Web Speech API**: 音声合成機能
- フレームワーク不使用

## ファイル構成

```
web-speech-api-test/
├── index.html                    # メインアプリケーション
├── .github/
│   └── workflows/
│       └── deploy.yml            # GitHub Actionsデプロイ設定
└── README.md                     # このファイル
```

## ローカルでの実行方法

1. リポジトリをクローン:
   ```bash
   git clone https://github.com/ikomiki/web-speech-api-test.git
   cd web-speech-api-test
   ```

2. ブラウザで `index.html` を開く:
   ```bash
   open index.html
   ```
   または、ファイルをブラウザにドラッグ&ドロップ

## デプロイ

GitHub Actionsを使用して、`ikomiki.github.io/web-speech-api-test` に自動デプロイされます。

### デプロイ設定

- **トリガー**: `main` ブランチへのpush
- **デプロイ先**: `ikomiki/ikomiki.github.io` リポジトリの `gh-pages` ブランチ
- **デプロイディレクトリ**: `web-speech-api-test`
- **使用アクション**: `peaceiris/actions-gh-pages@v4`

### 必要なシークレット

- `ACTIONS_DEPLOY_KEY`: デプロイ用のSSHキー

## 実装の詳細

### Web Speech API の使用

```javascript
const utterance = new SpeechSynthesisUtterance(text);
utterance.lang = 'ja-JP';       // 日本語設定
utterance.rate = 1.0;            // 速度（0.1〜10）
utterance.pitch = 1.0;           // 音程（0〜2）
utterance.volume = 1.0;          // 音量（0〜1）

speechSynthesis.speak(utterance);
```

### イベントハンドリング

- `onstart`: 音声再生開始時
- `onend`: 音声再生完了時
- `onerror`: エラー発生時

### ブラウザ対応チェック

```javascript
if (!('speechSynthesis' in window)) {
    // 非対応ブラウザの処理
}
```

## ブラウザ対応状況

- Chrome/Edge: ✅ フルサポート
- Firefox: ✅ フルサポート
- Safari: ✅ フルサポート
- Opera: ✅ フルサポート

## ライセンス

MIT

## 作成者

ikomiki
