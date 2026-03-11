---
name: update-rules
description: Fetch latest AI rules from ai-rules template repo and intelligently merge into this project
disable-model-invocation: false
---

ai-rules テンプレートリポジトリから最新のルールを取得し、このプロジェクトの既存ルールとインテリジェントにマージしてください。

## 手順

1. 一時ディレクトリに ai-rules リポジトリをクローンする
   ```bash
   TMPDIR=$(mktemp -d)
   git clone --depth 1 git@github.com:atsusics/ai-rules.git "$TMPDIR/ai-rules"
   ```

2. 以下の対象ファイルについて、テンプレート（新）とプロジェクト（現）の両方を読み込んで比較する

   **対象ファイル：**
   - `CLAUDE.md`
   - `ai/rules/GIT_WORKFLOW.md`
   - `ai/rules/PROJECT_ARCHITECTURE.md`
   - `ai/rules/CODING_GUIDELINES.md`
   - `.claude/skills/main/SKILL.md`
   - `.claude/skills/pr/SKILL.md`
   - `.claude/skills/sync/SKILL.md`
   - `.claude/skills/update-rules/SKILL.md`

3. 各ファイルについて以下のルールでマージ判断を行う

4. 一時ディレクトリを削除する
   ```bash
   rm -rf "$TMPDIR"
   ```

5. 変更した内容のサマリーをユーザーに報告する

## マージルール

### プロジェクトにファイルが存在しない場合
- テンプレートからそのままコピーする

### 両方に存在する場合 — セクション単位で比較する
テンプレートとプロジェクトの内容をセクション（見出し `##` / `###` 単位）ごとに比較し、以下を判断する：

- **テンプレートで追加されたセクション** → プロジェクトに追記する
- **テンプレートで文言が更新されたセクション** → プロジェクト側が未変更ならテンプレートに合わせる。プロジェクト側が独自に編集済みなら、テンプレートの変更意図を汲んで手動マージする（機械的な上書きはしない）
- **テンプレートで削除されたセクション** → プロジェクト側でも不要と判断できれば削除。判断がつかない場合はユーザーに確認する
- **プロジェクト独自のセクション** → そのまま残す（絶対に消さない）

### スキルファイル（.claude/skills/）
- スキルファイルはプロジェクト側で編集することが少ないため、基本的にテンプレートで更新する
- ただしプロジェクト固有の変更（例: `gh pr` → MCP GitHub server）がある場合は、その変更を維持する

## 禁止事項

- プロジェクト固有の記述（技術スタック、コマンド、ディレクトリ構成、ルーティング等）を消さない
- 自動コミットはしない（ユーザーが差分を確認してから判断する）
- マージ判断に迷った場合は勝手に決めずユーザーに確認する
