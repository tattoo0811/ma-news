# ma-news

ChatGPT Scheduled Research → GitHub Issues → Multica のための **M&Aニュース起票専用キュー** です。

## 役割

このリポジトリでは記事本文や実装コードを管理しません。

- ChatGPT Scheduled: 外部Webを広く監視・一次情報を確認
- GitHub Issue: 調査結果を構造化して保存する Source of Truth / Job Queue
- Multica: Issueを読み取り、各agentへ仕事を分配
- Claude: 記事構成・本文・最終編集
- OMP: 対象repo内の探索、既存記事・コンポーネント・リンク調査、軽作業
- AGY: 独立視点、別仮説、追加論点
- Codex: MDX/React/SEO metadata/テスト/PR
- Codex ImageGen: Hero/OGPなど画像生成

## 基本フロー

```text
Web / IR / PR / News
        ↓
ChatGPT Scheduled Research
        ↓
duplicate / relevance check
        ↓
tattoo0811/ma-news Issue
        ↓
Multica
   ├─ OMP repo scout
   ├─ AGY alternative analysis
   ├─ Claude writer
   ├─ Codex implementation
   └─ Codex ImageGen
        ↓
target repository PR
```

## 原則

1. **1ニュース = 1 Issue**
2. 一次情報（IR、適時開示、公式発表等）を優先する
3. 同一案件の重複Issueを作らない
4. 記事化前の広いWebリサーチはChatGPT側で行う
5. OMPは主に対象repo内部の探索に使う
6. Issueには、後段agentが再調査しなくて済むだけのResearch Packetを残す
7. 画像生成はCodex ImageGenへ限定する
8. 実装・公開先はIssueの `Target Repository` に明示する

## 推奨Issue状態

Issue本文の Workflow Status を更新して管理します。

- `discovered` — 候補発見
- `research-ready` — 一次調査完了
- `production-ready` — 記事化決定
- `in-production` — Multica/agents作業中
- `pr-open` — PR作成済み
- `published` — 公開完了
- `rejected` — 見送り

## Multica Routing

標準ルート:

```text
research: ChatGPT
repo_scout: OMP
writer: Claude
alternative_analysis: AGY
implementation: Codex
image: Codex ImageGen
review: Claude
```

Issue Template: **M&A News Research Packet** を利用してください。
