# Git ワークフロー

## ブランチ命名規約
```
<type>/<短い説明>
```

### タイプ一覧
| タイプ | 用途 | 例 |
|--------|------|-----|
| `feat/` | 新機能 | `feat/add-project-section` |
| `fix/` | バグ修正 | `fix/responsive-layout` |
| `chore/` | メンテナンス・設定変更 | `chore/update-dependencies` |
| `refactor/` | リファクタリング | `refactor/component-structure` |
| `docs/` | ドキュメント | `docs/update-readme` |

## コミットメッセージ規約
```
<type>: <簡潔な説明>
```

### 例
```
feat: add project showcase section
fix: correct responsive layout on mobile
chore: update build configuration
```

### ルール
- **英語**で記述する
- 動詞は**原形**で始める（add, fix, update, remove, refactor）
- 1行目は **72文字以内**
- 本文が必要な場合は空行を挟んで記述する
- 関連する変更は1つのコミットにまとめる

## Pull Request 規約

### タイトル
コミットメッセージと同じ形式（`<type>: <説明>`）

### 本文テンプレート
```markdown
## Summary
- 変更内容の箇条書き

## Test plan
- [ ] テスト項目
```

### マージ方針
- **main ブランチ**に対してPRを作成する
- マージ前にローカル動作確認を完了させる
- Squash merge を推奨

## 作業開始時
1. `main` ブランチから最新を pull する
2. 命名規約に従ってブランチを作成する
3. こまめにコミットする

## 作業終了時
1. 動作確認が完了していることを確認する
2. 必要に応じてPRを作成する
