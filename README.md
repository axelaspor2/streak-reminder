# GitHub Streak Reminder

毎日21時（JST）に GitHub のコントリビューション（草）をチェックし、その日の草がなければ Discord に通知を送信する GitHub Actions ワークフロー。

## セットアップ

### 1. Discord Webhook の作成

1. Discord サーバーの「サーバー設定」を開く
2. 「連携サービス」→「ウェブフック」を選択
3. 「新しいウェブフック」をクリック
4. 通知を送信したいチャンネルを選択
5. 「ウェブフック URL をコピー」をクリック

### 2. GitHub Secrets の設定

リポジトリの Settings → Secrets and variables → Actions で以下を追加：

| Secret 名 | 説明 |
|-----------|------|
| `ANTHROPIC_API_KEY` | Claude API キー（[Anthropic Console](https://console.anthropic.com/) から取得） |
| `DISCORD_WEBHOOK_URL` | Discord Webhook URL（上記で取得） |

### 3. 動作確認

1. リポジトリの Actions タブを開く
2. 「GitHub Streak Reminder」ワークフローを選択
3. 「Run workflow」ボタンで手動実行
4. ログを確認して動作を検証

## 動作仕様

- **実行時刻**: 毎日 21:00 JST（UTC 12:00）
- **チェック対象**: GitHub ユーザー `axelaspor2`
- **通知条件**: その日のコントリビューションが 0 件の場合のみ

## 注意事項

- GitHub Actions の cron は最大15分程度遅延する可能性があります
- `GITHUB_TOKEN` は自動で提供されるため、設定不要です
