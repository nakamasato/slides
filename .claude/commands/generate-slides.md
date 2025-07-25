# Generate Marp Slides from Input

入力ファイルからMarpスライドを生成します。


## 実行手順

1. **入力ファイルの読み込み**
   - $ARGUMENTS で指定された入力ファイル（デフォルト: `input/` 内の最新ファイル）を読む
   - タイトル、目的、対象者、アジェンダを抽出
   - 入力ファイルにurlがあればFetchして中身もInputの内容に含める

2. **テンプレートの準備**
   - `YYYYMMDD_template.md`をコピーして新規ファイル作成
   - ファイル名: `YYYYMMDD_[タイトル].md` <- inputのファイル名と同じにする

3. **スライド生成**
   - 入力内容を適切なセクションに配置
   - 技術的内容にはコードブロックやMermaid図を追加
   - CLAUDE.mdのルールに従う：
     - 1スライド1メッセージ
     - タイトル最大30文字
     - headerはタイトルをちゃんと全部いれる
     - 1行最大40文字、1スライド最大400文字/12行
     - 箇条書きは3-5項目

4. **スタイリング適用**
   - frontmatterで`theme: themes/theme`を指定
   - 画像は`.images/`から参照

5. **出力**
   - 生成ファイルを`output/`に保存
   - ファイル名はインプットと同様
   - プレビューコマンドを提示

## 使用例
```
/generate-slides input/my-presentation-outline.md
```

引数なしの場合は`input/`内の最新ファイルを使用。
