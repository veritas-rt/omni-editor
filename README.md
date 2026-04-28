# Omni Editor

[English](README_EN.md) | **[🌐 Live Demo](https://veritas-rt.github.io/omni-editor/)**

Omni Editorは、ブラウザだけで動く1ファイルの万能ローカルエディタ・ビューアです。サーバーやインストールは一切不要で、ChromeやEdgeでHTMLファイルを開くだけで、ローカルフォルダ（Vault）を丸ごと読み込んで編集できます。

Markdownの執筆はもちろん、画像、動画、音声、CSV、JSONなど様々なファイルのプレビューに対応しています。

## ✨ 主な機能

*   **完全ローカル・1ファイル完結**: `index.html` をブラウザで開くだけ。バックエンドサーバーは不要です。
*   **File System Access API**: 指定したローカルフォルダを直接読み書きし、フォルダツリーを表示します。
*   **強力なMarkdownプレビュー**:
    *   GitHub Flavored Markdown (GFM)
    *   **数式 (KaTeX)** `$E=mc^2$`
    *   **図表 (Mermaid)**
    *   フロントマター (YAML メタデータ) のテーブル表示
    *   チェックボックスの連動（プレビューからクリックして状態を保存）
*   **CodeMirror 6 搭載**: シンタックスハイライト、行番号、自動補完、Vimキーバインド (`Ctrl+Alt+V`) 対応。
*   **万能ビューア**: 画像、動画 (`.mp4` など)、音声 (`.mp3` など)、CSV（表に自動パース）、JSON・YAML（ハイライト表示）、PDF、HTMLなどをそのままプレビュー可能。
*   **Vault（フォルダ）全体検索**:
    *   ファイル名検索 (`Ctrl+P`)
    *   全文検索（Grep） (`Ctrl+Shift+F`)
*   **リッチなエクスポート**:
    *   単一Markdownから綺麗にレンダリングされたHTMLへの書き出し (`Ctrl+Shift+E`)
    *   Vault全体のMarkdownをまとめてHTMLファイルに一括エクスポート（画像やリンク関係を保持）

## 🚀 使い方

1.  `index.html` をダウンロードするかリポジトリをクローンします。
2.  Chrome, Edge, または File System Access API に対応したブラウザで `index.html` を開きます。（※ローカルのHTMLファイルを直接開いた場合、セキュリティ制限で一部のiframe機能が制限される場合があります。推奨はローカルサーバーの利用です）
3.  **Vaultを開く** をクリックして、編集したいフォルダを選択します。
4.  左側のサイドバーからファイルを選択して編集・プレビューします。

### キーボードショートカット

| ショートカット | アクション |
|---|---|
| `Ctrl + S` | 保存 |
| `Ctrl + Shift + O` | Vaultを開く |
| `Ctrl + P` | ファイル検索 |
| `Ctrl + Shift + F` | 全文検索 (Grep) |
| `Ctrl + E` | Edit/Preview/Split モード切替 |
| `Ctrl + H` | 検索と置換 |
| `Ctrl + Shift + E` | HTMLエクスポート |
| `Ctrl + Alt + V` | Vimモード切替 |

## 🛠 動作環境

*   File System Access API をサポートするモダンブラウザ（Google Chrome, Microsoft Edge など）
*   ※ Safari や Firefox は現在 File System Access API を完全サポートしていないため、ご利用いただけません。

## 📝 構成技術

*   [CodeMirror 6](https://codemirror.net/) (Editor)
*   [Marked](https://marked.js.org/) (Markdown Parser)
*   [Highlight.js](https://highlightjs.org/) (Syntax Highlighting)
*   [KaTeX](https://katex.org/) (Math Typesetting)
*   [Mermaid](https://mermaid.js.org/) (Diagrams)
*   [js-yaml](https://github.com/nodeca/js-yaml) (Frontmatter)

---
*Created as a single-file, highly portable Markdown & Media workspace.*