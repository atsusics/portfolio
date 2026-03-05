---
name: pr
description: Create a branch, commit all changes, and open a pull request
disable-model-invocation: true
argument-hint: "[PR description (optional)]"
---

現在の変更からブランチを作成し、コミットしてPRを作成してください。

## 手順

1. `git diff` と `git status` で現在の変更内容を確認する
2. 変更内容に基づいて適切なブランチ名を決定する（例: `fix/xxx`, `feat/xxx`, `chore/xxx`）
3. ブランチを作成してチェックアウトする
4. 変更をステージングしてコミットする（コミットメッセージは変更内容に基づいて自動生成）
5. リモートにプッシュする
6. `gh pr create` でPRを作成する

## ルール

- ブランチ名は英語のケバブケースで、変更内容を簡潔に表す
- コミットメッセージは Conventional Commits 形式（`fix:`, `feat:`, `chore:` 等）
- PRのタイトルはコミットメッセージと同じ形式
- PRのbodyは日本語で、Summary と Test plan を含める
- ユーザーが引数で説明を渡した場合（$ARGUMENTS）、それをPRの内容に反映する
- Co-Authored-By: Claude Code <noreply@anthropic.com> をコミットメッセージに含める
