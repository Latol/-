# CLAUDE.md

## このリポジトリについて

Claude Code（主にクラウドセッション）で読み込むプロジェクトスキルを置くためのリポジトリ。
アプリケーションコードはなく、ビルド・テストもない。

```
.claude/skills/<skill-name>/
  SKILL.md   # frontmatter（name, description, allowed-tools）+ 本文
  LICENSE    # 外部由来のスキルは元のライセンスを同梱する
```

現在のスキル:

| スキル | 出典 | 前提 |
|---|---|---|
| `ai-music` | agentspace-so/runcomfy-agent-skills（MIT） | `runcomfy` CLI と `RUNCOMFY_TOKEN`。どちらもこの環境には未導入 |

## スキル追加時のルール

- 1スキル = `.claude/skills/<skill-name>/` の1ディレクトリ。ディレクトリ名は frontmatter の `name` と揃える。
- 外部スキルを取り込むときは:
  - `LICENSE` を必ず同梱し、出典（リポジトリ名・スキル名）をコミットメッセージに書く。
  - 取り込む前に SKILL.md 全文を読み、`allowed-tools` と実行されるコマンド・送信先を確認する。範囲が広すぎるもの（`Bash(*)` など）は取り込まない。
  - 改変した場合はその内容をコミットメッセージに残す。
- `description` はトリガー判定に使われるため、何をするスキルか・いつ使うかを具体的に書く。
- API キーやトークンはリポジトリに書かない。クラウド環境の環境変数（シークレット）で渡す。

## 作業ルール

- 指定された作業ブランチで作業し、`main` などへ直接 push しない。
- この CLAUDE.md は毎セッション読み込まれる。リポジトリの構成が変わったら上の表と構成図を更新し、内容は短く保つ。
