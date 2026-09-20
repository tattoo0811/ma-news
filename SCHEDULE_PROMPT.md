# Scheduled ChatGPT Prompt — M&A News → GitHub Issue

このプロンプトは ChatGPT Scheduled Research の定期実行用です。

## Mission

直近のM&A関連ニュース・一次情報を広く調査し、記事化価値のある案件だけを
`tattoo0811/ma-news` に **1案件 = 1 GitHub Issue** として起票する。

記事本文やコードはこの段階では作らない。

## Research Scope

優先して探索するもの:

- 企業買収
- 事業譲渡 / 事業売却
- MBO / TOB
- 合併 / 経営統合
- 資本業務提携
- PE / 投資ファンドによる取得・売却
- カーブアウト
- ブランド / 店舗 / Web事業 / SaaS / 人材 / 外食 / ECなどの買収
- 金額非開示でも事業上重要な案件

日本企業を優先するが、日本企業に影響する海外案件も対象。

## Source Priority

情報源は次の順で評価する。

1. 企業IR・公式発表
2. TDnet等の適時開示
3. 官公庁・取引所等
4. 信頼できる報道機関
5. 業界メディア
6. PR配信
7. その他

可能な限り一次情報を必ず確認する。

## Duplicate Check

Issue作成前に `tattoo0811/ma-news` のopen/closed Issueを検索する。

以下のいずれかが同じなら重複候補として扱う。

- Buyer
- Target
- 発表日
- 同一取引
- 同一公式発表

既存Issueがある場合、新規Issueは作らず、既存Issueに追加すべき新情報があるかを判断する。

## Selection

単なる人事・一般ニュースは除外。

記事候補として優先するもの:

- 事業構造が変わる
- 買収理由に分析余地がある
- ブランド認知が高い
- 検索需要が期待できる
- 買収金額やバリュエーションに注目点がある
- ロールアップや業界再編の文脈がある
- M&A実務・経営判断に学びがある
- 既存記事との差別化が可能

## Issue Title

```text
[M&A NEWS] Buyer → Target｜案件を一言で表す補足
```

## Issue Body

必ず以下を含める。

```markdown
<!-- ma-news-schema:v1 -->

## Discovered At
YYYY-MM-DD

## Category
Acquisition / Business Transfer / Capital Alliance / MBO / TOB / PE / Fund / Divestiture / Merger / Other

## Buyer / Acquirer
...

## Target / Seller
...

## Primary Sources
- URL
  - 要点

## Secondary Sources
- URL
  - 要点

## Deal Summary
- 発表日:
- スキーム:
- 取得比率:
- 取引金額:
- クロージング:
- アドバイザー:
- 未開示事項:

## Company Research

### Buyer
- 事業:
- 規模:
- 既存M&A:
- 公式に説明されている買収目的:

### Target
- 事業:
- 規模:
- 強み:
- 市場ポジション:

## Article Angles
1.
2.
3.

事実と分析・仮説を明確に分離する。

## SEO / Search Signals
- Primary query:
- Secondary queries:
- Search intent:
- Competitor pages:
- 関連トピック:

## Target Repository
ma-team333/growth-partnership

## Priority
P0 / P1 / P2 / P3

## Agent Routing
research: ChatGPT
repo_scout: OMP
writer: Claude
alternative_analysis: AGY
implementation: Codex
image: Codex ImageGen
review: Claude

## Workflow Status
status: research-ready

- [x] external research
- [x] primary-source check
- [x] ma-news duplicate check
- [ ] duplicate check against target repo
- [ ] repo scout
- [ ] article outline
- [ ] article draft
- [ ] alternative analysis
- [ ] hero / OGP image
- [ ] implementation
- [ ] build / test
- [ ] editorial review
- [ ] PR
- [ ] published

## Notes / Risks
- 不確実点:
- 要追加確認:
- 公開時の注意:
```

## Important Rules

- 不明な金額や比率を推測して事実のように書かない。
- 二次情報だけで確定扱いしない。
- 同一ニュースを複数Issueにしない。
- 数を増やすことより、後段agentがそのまま作業できるResearch Packet品質を優先する。
- このScheduled Jobでは記事本文・画像・実装を完成させない。
- Issue作成後はMultica側へ処理を渡す前提で、必要なコンテキストをIssueに集約する。
