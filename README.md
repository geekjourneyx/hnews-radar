# HNews Radar

Hacker News high-signal radar and daily research archive.

This repository is the long-term source of truth for the scheduled HN radar. The scheduled task must not rely on previous chat-session output for continuity; it reads prior reports from this repository and writes every completed run back here.

## Archive layout

```text
reports/
  YYYY/
    MM/
      DD.md
```

Each calendar day has exactly one report file. The scheduled runs at 10:00, 14:00 and 19:00 update the same file idempotently:

- **10:00** — morning baseline
- **14:00** — afternoon incremental update
- **19:00** — evening close / final daily state

Later runs must preserve earlier verified findings and add only material changes, corrections, stronger evidence, new projects/tools, or newly important discussions.

## What the radar optimizes for

Signal value is more important than HN points.

The radar looks for:

- AI / Agent / Harness / models / developer tools / software architecture;
- noteworthy open-source projects, products and utilities;
- product, pricing, growth, distribution and business-model signals;
- industry and startup opportunities;
- high-quality technical disagreement and unusually informative comments;
- contrarian or counter-intuitive ideas that can change how a problem is understood;
- early low-popularity signals that may matter before they become mainstream.

## Mandatory project & tool research

Every run must explicitly inspect projects and tools surfaced by HN. A candidate is not sufficiently researched by reading the HN title or README alone.

For every selected project/tool, the report should answer:

1. **What problem does it solve?**
2. **What is actually new or unusually good about the approach?**
3. **Why is it worth attention now?**
4. **What evidence supports that judgment?**
5. **What is the strongest limitation, counterargument or unverified claim?**
6. **Is there a contrarian insight, product opportunity, engineering pattern or trend behind it?**

Evidence should normally include:

- the HN discussion or discovery source;
- a primary source such as the project repository, release, docs, paper, official post or demo;
- independent web research when useful: other technical discussions, third-party reporting, benchmarks, adoption evidence, author history, comparable products, or earlier work.

Clearly distinguish **verified fact**, **author claim**, **community evidence**, and **inference**.

## Report contract

See [`REPORT_SPEC.md`](REPORT_SPEC.md). Scheduled runs should treat that file as the durable output contract.
