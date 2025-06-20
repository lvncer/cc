# Claude Code Configuration

Claude Code で開発を行う際の設定ファイルとカスタムプロンプトを管理するプロジェクトです。

## 📁 プロジェクト構成

```sh
cc-test/
├── CLAUDE.md          # Claude Code開発ルール・ガイドライン（日本語）
├── .mcp.json          # MCP（Model Context Protocol）サーバー設定
├── .prompts/          # 実装ログディレクトリ
│   └── *.md          # 各実装の詳細ログ（yyyy-mm-dd_機能名.md形式）
└── README.md          # このファイル
```

## 🎯 主要ファイルの説明

### CLAUDE.md

Claude Code での開発時に使用する包括的なルールとガイドライン集です。以下の内容が含まれています：

- **グローバルルール**: 明示的指示なしの変更禁止、段階的実行
- **通知システム**: 全タスク完了時の必須通知（音付き）
- **ワークフロー**: Issue 管理、ブランチ戦略、PR 作成・マージ手順
- **技術スタック**: React + Next.js + TypeScript + Bun ベースの推奨構成
- **テスト戦略**: TDD（Red-Green-Refactor）サイクル
- **UI/UX 制約**: 既存 UI 変更時の承認必須
- **データベース設計**: Prisma + Supabase での命名規則とセキュリティ
- **必須チェックリスト**: 開発開始から完了までの確認項目

### .mcp.json

Claude Desktop アプリで MCP（Model Context Protocol）サーバーを設定するファイルです。

- **deepwiki**: 検索・情報取得用 MCP サーバー
- **github**: GitHub 操作用 MCP サーバー（要 Personal Access Token）

### .prompts/ ディレクトリ

**必須**: 全ての実装完了後に実装ログを保存するディレクトリです。

- ファイル形式: `yyyy-mm-dd_機能名.md`
- 内容: 実装詳細、変更されたファイル、完了状況など

## 🚀 導入方法

### ステップ 1: ファイルのコピー

```bash
# プロジェクトルートに設定ファイルをコピー
cp CLAUDE.md /path/to/your/project/
cp .mcp.json ~/.claude/
```

### ステップ 2: 重要な設定変更

#### CLAUDE.md の設定変更

`CLAUDE.md`の以下の箇所を**必ず**あなたの環境に合わせて変更してください：

```markdown
### 1. Preparation

GitHub Username: lvncer # ← あなたの GitHub ユーザー名に変更
```

#### .mcp.json の設定変更

GitHub MCP サーバーを使用する場合は、Personal Access Token を設定してください：

```json
{
  "mcpServers": {
    "github": {
      "type": "http",
      "url": "https://api.githubcopilot.com/mcp",
      "headers": {
        "Authorization": "YOUR_PAT_HERE" // ← あなたのPATに変更
      }
    }
  }
}
```

### ステップ 3: ディレクトリ作成

```bash
# プロンプトログ用ディレクトリを作成
mkdir .prompts
```

### ステップ 4: Claude Desktop の再起動

設定を反映するために Claude Desktop アプリを再起動してください。

## 💡 使用方法

### カスタムプロンプトとして使用

1. Claude Code（Cursor）でプロジェクトを開く
2. `@CLAUDE.md`でファイルを参照してカスタムプロンプトとして読み込ませる
3. Claude が設定されたルールに従って開発を支援

### 実装ログの管理

全ての実装完了後、自動的に`.prompts/`ディレクトリに実装ログが保存されます：

```sh
.prompts/
├── 2024-12-30_user-authentication.md
```

## ⚠️ 重要な注意事項

### 必須の設定変更

- **GitHub Username**: `CLAUDE.md`内の`GitHub Username: lvncer`を必ずあなたのユーザー名に変更
- **Personal Access Token**: `.mcp.json`内の GitHub 認証情報を設定

### 開発時の制約

- 既存 UI の変更は承認なしで禁止
- 全タスク完了時に通知が必須
- 実装ログの保存が必須
- Issue 番号をコミットメッセージに含める

### ワークフロー

1. Issue 作成 → 2. ブランチ作成 → 3. 開発 → 4. PR 作成 → 5. マージ → 6. ログ保存

## 🔧 カスタマイズ

プロジェクトの要件に応じて`CLAUDE.md`の以下のセクションをカスタマイズできます：

- **Tech Stack**: 使用技術の変更
- **Directory Structure**: プロジェクト構造の調整
- **Notification Templates**: 通知音やメッセージの変更
- **Essential Checklist**: チェック項目の追加・削除

## 📝 ライセンス

このプロジェクトは個人・商用問わず自由に使用できます。

## 🤝 貢献

改善提案やバグ報告は Issue または Pull Request でお願いします。
