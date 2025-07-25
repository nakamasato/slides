# プレゼンテーションのアウトライン

## タイトル: devcontainerで安全にclaude codeを使う

### 登壇日

2025/07/27

### 目的
- 技術的な開発環境の

### 対象者
- Devcontainerを使ったことがない人
- Claude Codeで--dangerously-skip-permissionsを使いたいけどYOLOモードは危険だと思って躊躇している人

### 主要ポイント

1. 背景と課題
2. Devcontainerの導入方法
3. Claudeに関する設定
4. 初めて使うときに引っかかるポイント
5. デモ

---

ざっくりとした想定した流れ

- 内容として話したい点
    - Devcontainerの重要性: Claude Codeの普及により、安全にClaude Codeを実行できる環境をつくれることが未然にセキュリティインシデントを防ぐうえで重要
        - [Cursor YOLO delted everything in my computer](https://www.reddit.com/r/theprimeagen/comments/1lbv5kg/cursor_yolo_deleted_everything_in_my_computer/)!
    - Devcontainer導入の流れ
        - フォルダと設定ファイル
        - 大まかなイメージ
            1. 提供されているDocker image指定
            2. Dockerfileでカスタムイメージ作成
            3. DBなど複数コンテナ使う場合にはDocker-Composeを使う
            ->  イメージを使ったら必要なRuntimeが動く
        - CLIが必要 (git, gh, claude, tig, jq, etc)
            1. インストールする features (gh, claude, etc)
            2. Dockerfileでカスタムイメージにいれる
        - CLIの認証
            1. git: 自動でホストのCredential helperが使われる
            2. gh: 毎回 gh auth loginしないといけない or GH_TOKENを設定する
            3. claude でブラウザ認証が毎回必要
    - 利点
        - 一回設定したら、チームで共通で使える
        - `claude --dangerously-skip-permissions` を使えるようになる。 (gh commandの権限などは付与されてるのでDenyルールの整備も必須)


### 内容ソース

- https://qiita.com/nakamasato/items/77b1567914fe51d08525.md qiitaのmdの内容で登壇

### 必要な図表

- Devcontainerとはの図: https://code.visualstudio.com/assets/docs/devcontainers/containers/architecture-containers.png
- 設定ファイルの構成
- DockerとVSCodeのIcon
- qiitaに貼ってある画像適宜


## 発表に関して

- 大体15分の登壇で前半でスライドで説明して、後半はVSCodeを使ってデモをやろうと思っているので、10分くらいで説明できる内容をピックアップしてください。
