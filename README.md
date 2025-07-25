# Slidds (Claude Code x marp)

統一されたデザインのプレゼンテーションスライドを効率的に作成するためのテンプレートシステムです。

> [!NOTE] 登壇スライド作成もClaude Codeに任せたい 〜家でも外でも移動中も〜](https://zenn.dev/> loglass/articles/a8b4b069c09002) こちらの記事を参考にClaude Codeで生成しました。

## 概要

このリポジトリは、Marpを使用して一貫性のあるプレゼンテーションを迅速に作成するためのテンプレートとツールを提供します。

## 必要な環境

- [Marp CLI](https://github.com/marp-team/marp-cli)
- Node.js (v14以上推奨)
- [Claude Code](https://claude.ai/code)（スライド自動生成用）

## インストール

```bash
# Marp CLIのインストール
npm install -g @marp-team/marp-cli

# リポジトリのクローン
git clone [your-repo-url]
cd slides
```

## 使い方

### 1. `input/YYYYMMDD_xxxx.md`に内容を書く

- 話したい内容や、関連のリンクなどを書く
- プレゼンの長さやターゲットなども書く

### 2. 入力ファイルからの生成（Claude Code使用）

Claude Codeでコマンドを実行

```
/project:generate-slides input/YYYYMMDD_your_topic.md
```

生成されたファイルは `output/` ディレクトリに保存されます。

### 3. プレビューとエクスポート

```bash
# プレビュー（テーマ適用）
marp --preview output/YYYYMMDD_your_topic.md --theme themes/theme.css

# PDF出力（テーマ適用）
marp output/YYYYMMDD_your_topic.md --pdf --theme themes/theme.css --allow-local-files

# HTML出力（テーマ適用）
marp output/YYYYMMDD_your_topic.md --html --theme themes/theme.css --allow-local-files
```

## ディレクトリ構造

```
.
├── .claude/                # Claude Code設定
│   └── commands/          # カスタムコマンド
├── .images/               # 画像アセット
│   ├── background.png    # 背景画像
│   ├── logo_primary.png  # メインロゴ
│   └── logo_vertical.png # 縦型ロゴ
├── themes/                # カスタムテーマ
│   └── theme.css         # CSSテーマファイル（作成予定）
├── input/                 # 入力ファイル
│   └── input-example.md  # 入力例
├── output/                # 生成されたスライド
│   ├── output-example.md # 出力例
│   └── *.pdf            # PDFファイル
├── resources/             # 参考資料
├── YYYYMMDD_template.md   # マスターテンプレート
└── CLAUDE.md             # Claude Code用ガイド
```

## カスタマイズ

### テーマの設定

`themes/theme.css`にカスタムCSSを定義することで、独自のデザインを適用できます：

```css
/* themes/theme.css */
@theme custom {
  @import 'default';

  section {
    background-color: #f5f5f5;
    color: #333;
  }

  h1 {
    color: #0066cc;
  }
}
```

### 画像アセットの追加

`.images/`ディレクトリに画像を配置し、スライドから参照：

```markdown
![bg](.images/background.png)
![logo](.images/logo_primary.png)
```

## ベストプラクティス

1. **命名規則**: `YYYYMMDD_title.md`形式でファイル名を付ける
2. **バージョン管理**: 重要なプレゼンテーションはGitで管理
3. **画像最適化**: 画像は適切なサイズに圧縮
4. **テンプレート活用**: 基本構造は常にテンプレートから開始

## トラブルシューティング

### Marpが動作しない
```bash
# Node.jsのバージョン確認
node --version

# Marpの再インストール
npm uninstall -g @marp-team/marp-cli
npm install -g @marp-team/marp-cli
```

### PDFエクスポートエラー
- Chromiumの依存関係を確認
- ファイルパスに特殊文字が含まれていないか確認

## ライセンス

[MIT License](LICENSE)

## 関連リンク

- [Marp公式ドキュメント](https://marpit.marp.app/)
- [Marp CLI](https://github.com/marp-team/marp-cli)
- [Claude Code](https://claude.ai/code)
