---
name: sync
description: Merge latest main branch into current working branch
disable-model-invocation: true
---

最新のmainブランチの変更を現在の作業ブランチに取り込んでください。

## 手順

1. 現在のブランチ名を確認（mainでないことを確認）
2. `git fetch origin main`
3. `git merge origin/main` で最新のmainを作業ブランチにマージ
4. コンフリクトがあれば報告して対応を相談
5. 完了後、マージ結果を表示して確認
