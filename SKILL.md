---
name: financial-morning-brief
description: This skill should be used when generating a Chinese domestic financial-market morning brief, daily market report, or scheduled automation output focused on how global markets, commodities, FX, central-bank policy, geopolitics, and major corporate events affect A-share, Hong Kong, China equities, RMB, bonds, and China commodity futures. It enforces a stable output structure, 10-point impact scoring, concrete numeric data, source links, and consistency checks.
agent_created: true
---

# Domestic Financial Morning Brief

## Overview

Generate a stable, repeatable Chinese financial-market morning brief for domestic investors. Focus on the transmission from global overnight events and latest news into A-share, Hong Kong, China markets, RMB exchange rate, China bonds, and domestic commodity futures.

Use this skill for requests such as “今日早报”, “来一份金融早报”, “生成国内金融市场早报”, “每日金融早报自动化”, or any short continuation command in an existing financial-brief workflow such as “来”, “产出”, “再来一版”.

## Non-Negotiable Output Rules

- Use simplified Chinese.
- Title the report exactly as `【YYYY年M月D日】金融市场早报` unless the user requests another date format.
- If producing a file, name it `早报-YYYY-MM-DD.html` by default.
- Keep the report structure stable across runs. Do not drop fixed modules because of sparse data.
- Use only a 10-point impact score such as `10/10`, `9.5/10`, `8/10`. Do not use a separate decimal “影响系数” such as `0.95`.
- Sort core events by impact on domestic financial markets from high to low.
- Expand the top 2-3 events in detail: background, exact data, transmission path, domestic market impact, and trading implication.
- Describe middle-ranked events with moderate detail.
- Keep low-impact events brief, usually one sentence plus key data.
- Use concrete numbers for all magnitudes: index levels, percentage changes, turnover, basis points, probabilities, prices, amount, market capitalization, profit, revenue, or dates.
- Avoid vague adjectives when they replace numbers: do not use “大幅”, “明显”, “显著”, “大量”, “暴涨”, or “暴跌” without exact figures immediately attached.
- Attach source links for every core news item and for market-data sources when available.
- Use China-market color convention in any financial visualization or HTML styling: red for rising prices and green for falling prices.
- Refer to Hong Kong and Taiwan as “中国香港” and “中国台湾” where jurisdictional wording matters.

## Required Fixed Structure

Always include these sections in this order unless the user explicitly asks for a different layout:

1. **Header / Core Conclusion**
   - Date, coverage window, and one-sentence market stance.
   - State the most important domestic-market implication in the first screen.

2. **Global Major Market Close Snapshot**
   - Include prior trading-day performance for at least:
     - A-share: 上证指数, 深证成指, 创业板指, 科创50 or 沪深300 when relevant.
     - Hong Kong, China: 恒生指数, 恒生科技指数.
     - US: 道指, 标普500, 纳指, 费城半导体指数.
     - Asia-Pacific: 日经225, 韩国KOSPI when available.
     - Europe: 德国DAX, 法国CAC, 英国富时 or 欧洲斯托克50 when available.
   - Include index level, percentage change, and the date/session of the data.
   - If a market was closed, explicitly mark it as closed and use the latest available session.

3. **Commodities, FX, and Rates Snapshot**
   - Include WTI, Brent, spot gold or COMEX gold, silver when relevant, copper or other industrial metals when relevant.
   - Include US Dollar Index, USD/CNY or onshore/offshore RMB, USD/JPY when relevant, and 10Y US Treasury yield.
   - Include price/yield, percentage change or basis-point move, and data time/session.

4. **A-share Previous Trading-Day Turnover and Trend Assessment**
   - Include total A-share or沪深成交额 for the previous trading day.
   - Include recent turnover trend, preferably 3-5 trading days.
   - Calculate or state day-on-day change and trend judgment, such as 放量确认, 缩量反弹, 缩量下跌, 高位换手, or 流动性退潮.
   - Explain the domestic-market meaning in 2-4 sentences.

5. **Impact-Ranked Core Events**
   - Present each event with a 10-point score.
   - Suggested count: 6-10 events.
   - For each event include:
     - Headline.
     - Impact score.
     - Exact facts and numbers.
     - Transmission path to domestic markets.
     - Domestic sectors/assets affected.
     - Source links.

6. **Today’s Domestic Market Watchlist / Trading Framework**
   - Include likely affected domestic asset classes and sectors.
   - Separate risk triggers from positive catalysts.
   - Include specific levels or indicators to watch where possible: index support/resistance, turnover threshold, RMB level, oil/gold level, US yield level, or sector confirmation signal.

7. **Sources**
   - List source links grouped by topic or embedded under each event.
   - Prefer primary or reputable sources: exchanges, central banks, official statistical releases, company IR/filings, Reuters, Bloomberg, CNBC, MarketWatch, Investing.com, TradingView, Eastmoney, Sina Finance, Wallstreetcn, official Chinese ministries or exchanges.

## Research Workflow

1. **Review prior state when available**
   - For scheduled automations, read the automation memory first.
   - For project continuity, read the project memory rules if available.
   - Preserve recent user corrections: fixed index snapshot, commodity/FX snapshot, turnover trend module, and 10-point-only scoring.

2. **Collect market data**
   - Search for latest previous-session closes across US, Europe, Asia-Pacific, A-share, and Hong Kong, China markets.
   - Search commodities, FX, and rates data.
   - Check whether data is previous close, pre-market, intraday, or futures; label the timing precisely.

3. **Collect news catalysts**
   - Search past 24 hours and weekend events when applicable.
   - Cover: global equity moves, commodities, USD/RMB, US Treasury yields, Fed/ECB/BOJ/PBOC, geopolitics, China macro policy, major corporate earnings, semiconductor/AI/energy/financial-sector events.

4. **Rank by domestic impact**
   - Give highest scores to events that directly affect A-share liquidity, risk appetite, RMB, rates, imported inflation, energy costs, semiconductor/AI chain, Hong Kong, China tech, or China policy expectations.
   - Use `10/10` for events likely to dominate the domestic open or change risk appetite across multiple asset classes.
   - Use `9-9.5/10` for events with strong sector or macro transmission.
   - Use `7-8.5/10` for important but narrower market impacts.
   - Use `5-6.5/10` for background or low-priority items.

5. **Write the report**
   - Put the highest-value conclusion at the top.
   - Keep tables concise but complete.
   - Avoid changing section names across runs unless improving clarity without removing content.
   - Make all numbers auditable with a source or clear market-data label.

6. **Quality check before delivery**
   - Confirm all fixed modules are present.
   - Confirm impact scores are all 10-point format and sorted descending.
   - Confirm no decimal “影响系数” appears.
   - Confirm every core event has at least one source link.
   - Confirm all major numeric claims have concrete values.
   - Confirm file name and title date match.
   - Confirm HTML renders if producing an HTML file.

## HTML Report Guidance

When the user expects a file or an automation deliverable, prefer a polished single-file HTML report.

- Use a clean dashboard layout with cards and tables.
- Keep CSS inline in the HTML for portability.
- Use light-background cards unless the user specifically wants a dark style.
- Include source links as clickable anchors.
- Put the most important market stance and top risks above the fold.
- Use compact tables for market snapshots and turnover trend.
- Ensure Chinese financial color convention: rising values red, falling values green.

## Automation Memory Guidance

For scheduled automation runs:

- Read `.workbuddy/automations/<automation-id>/memory.md` before execution when available.
- After delivery, append only a high-level execution summary to automation memory.
- Do not store the full report body, full source list, or long market tables in automation memory.
- Include date, output file name, top 3-6 scored events, and any format/quality notes.

## Example Stable Outline

```markdown
# 【2026年7月27日】金融市场早报

## 核心结论
- 覆盖窗口：...
- 今日国内市场主线：...

## 全球主要市场收盘速览
| 市场 | 指数 | 收盘/点位 | 涨跌幅 | 数据时点 |

## 大宗商品、汇率与利率
| 类别 | 品种 | 最新/收盘 | 变动 | 数据时点 | 国内影响 |

## A股上个交易日成交额与趋势评估
- 上个交易日成交额：...
- 近5个交易日：...
- 趋势判断：...

## 按影响度排序的核心事件
### 1. 事件标题（10/10）
- 关键数据：...
- 传导路径：...
- 国内影响：...
- 来源：...

## 今日关注与交易框架
- 风险触发：...
- 正向催化：...
- 观察指标：...

## 来源
- ...
```
