# HNews Radar Report Spec

This file is the durable contract for every scheduled HNews Radar run.

## Storage contract

- Repository: `geekjourneyx/hnews-radar`
- Daily report path: `reports/YYYY/MM/DD.md`
- One calendar day = one Markdown report.
- 10:00 creates or refreshes the baseline.
- 14:00 and 19:00 update the same file idempotently.
- Never depend on a prior chat transcript for continuity. Always read the current report and at least the previous day's report from GitHub before deciding what is new.
- Do not append duplicate sections for the same run. Re-running the same time slot should replace/update that slot's content.

## Required report structure

```markdown
# HN 强信号雷达｜YYYY-MM-DD

> Last updated: YYYY-MM-DD HH:mm Asia/Shanghai

## 今日总判断

## 10:00 上午基线
### 本轮新增
### 综合强信号
### 项目与工具雷达
### 热点讨论与反直觉观点
### 产品 / 商业 / 产业机会
### 最值得精读
### 噪音与待验证

## 14:00 下午增量
### 相比上一轮新增
### 项目与工具雷达增量
### 热点讨论升温 / 分歧变化
### 新证据与结论修正

## 19:00 晚间收盘
### 相比上一轮新增
### 项目与工具雷达增量
### 热点讨论升温 / 分歧变化
### 今日最终判断

## 今日项目与工具索引

## Evidence Registry
```

Sections with no qualifying signal may say so explicitly instead of inventing content.

## Project & tool radar: mandatory

Every run must explicitly inspect HN items that are projects, open-source repositories, developer tools, libraries, utilities, products, infrastructure or unusually concrete demos.

Do not treat popularity as the gate. A low-points item can outrank a 300+ point item when it has higher product, engineering or strategic signal.

For every selected project/tool include:

- **Name + one-line description**
- **Problem solved** — the concrete pain or job-to-be-done
- **Why now** — why it matters in this run/day
- **What is actually interesting** — product insight, architecture, workflow, interaction pattern, economic shift, or engineering trick
- **Contrarian / non-obvious angle** — when evidence supports one
- **Evidence chain** — normally 2–5 links, distinguishing:
  - HN discovery/discussion
  - primary source: repo/docs/release/paper/official post/demo
  - independent web evidence: third-party discussion, comparison, adoption signal, benchmark, prior art, user reports
- **Discussion signal** — what HN participants are actually debating, including high-information comments or disagreement
- **Limitations / counterevidence**
- **Signal class** — `strong`, `worth-watching`, `early-potential`, `unverified`
- **Share angle** — one short angle that could justify a public post

A README claim alone is not a full evidence chain. Search the public web when it can clarify why the project matters, what problem it solves, how it differs from alternatives, whether the claim is new, and why HN is discussing it.

## Hot discussions: mandatory

Every run must separately inspect discussion quality, not only linked articles.

Prioritize:

- threads where comments add more value than the original link;
- expert disagreement with concrete evidence;
- surprising practitioner reports;
- comments that overturn the naive interpretation of the story;
- rapid growth in comments/points together with rising information density;
- multiple independent HN posts or comments converging on one trend.

For each selected discussion explain:

- the central question;
- the strongest competing views;
- the best evidence/examples used by each side;
- what changed compared with the prior run, if applicable;
- the most useful takeaway without pretending the debate is settled.

Where possible, link directly to useful comment permalinks.

## Evidence policy

Every important claim must be traceable.

Use these evidence labels:

- `verified_fact` — directly supported by a primary or authoritative source
- `author_claim` — stated by the author/project but not independently validated
- `community_evidence` — HN or other practitioner reports; describe sample limitations
- `inference` — reasoned conclusion from cited evidence
- `unknown` — material point that remains unresolved

Do not turn inference into fact. Do not turn one anonymous comment into community consensus.

For time-sensitive claims, verify exact publication/release/commit dates so resurfaced old material is not reported as new.

## Incremental update rules

At 14:00 and 19:00, read the current day's existing report before researching new material.

Only add/update a previously covered topic when at least one material change occurred:

- new primary-source information;
- official response;
- new release/commit/data;
- significant increase in HN points/comments together with better discussion quality;
- a strong new comment or counterexample;
- signal status changes, e.g. `unverified -> verified`;
- important correction or contradiction;
- new product/business/engineering implication.

Do not repeat the same explanation merely because the thread remains on the front page.

## Research scope

Always scan these HN feeds/surfaces as discovery layers:

- `https://hnrss.org/newest`
- `https://hnrss.org/bestcomments`
- `https://hnrss.org/frontpage`
- `https://hnrss.org/newest?points=300`

Then follow qualified candidates to original articles, repositories, papers, releases, official docs, company posts and the HN discussion.

Use broader web search for selected projects/tools and hot topics when it materially improves understanding or verification.

## Output behavior

The repository is the complete archive. Chat output after a scheduled run should stay compact and contain only:

- run time;
- created/updated report path;
- number of strong signals and notable projects/tools;
- 1–3 top takeaways;
- GitHub commit SHA or write failure.

Do not dump the full report into the conversation unless explicitly asked.

## Quality bar

- Signal Value > HN points.
- Prefer original sources.
- Preserve disagreement and counterevidence.
- Do not force a quota.
- If no strong new signal exists, record that plainly.
- Hunt for early projects and tools before they become obvious.
- Do not miss a genuinely hot technical/product discussion solely because it does not fit the user's usual AI/Harness interests.
