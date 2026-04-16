# 📱 Mobile Push Notification Targeting Model
### Maximizing Campaign Profitability via Logistic Regression Targeting

---

## 🎯 Business Problem

Tuango (a Groupon-like platform in China) assumed the cost of sending mobile push notifications was effectively zero — but the **true marginal cost was 9 RMB per message**, because over-messaging customers caused them to block future notifications, permanently closing a high-value marketing channel.

The core question: **Which customers should receive a deal push notification to maximize profitability — and which ones should be skipped?**

This is directly analogous to challenges faced by any consumer app (e.g., dating apps, subscription platforms) deciding when and to whom to send engagement nudges.

---

## 📊 Approach

**Dataset:** 20,908 randomly sampled mobile customers offered a karaoke deal (5% pilot sample from 418,160 eligible users in Hangzhou)

**Step 1 — Response Analysis**
- Calculated baseline response rate and average order size from pilot sample

**Step 2 — Targeting Models**
- Logistic regression to predict purchase probability (`buyer`) using RFM variables + demographics
- Linear regression to predict order size among buyers
- Key predictors: monetary value, frequency, music category purchase history

**Step 3 — Profitability Analysis**
- Calculated breakeven response rate using margin structure
- Compared two strategies: target everyone vs. model-based targeting
- Validated projected results against actual rollout data (397,252 customers)

**Tech Stack:** Python, Polars, pyrsm, plotnine

---

## 🔍 Key Findings

| Metric | Value |
|--------|-------|
| Pilot response rate | ~9.3% |
| Average order size (buyers) | 3.94 sessions |
| Breakeven response rate | ~9.3% |
| Messages sent — targeted approach | ~174,671 (vs. 397,252) |

**Profitability Comparison (Projected):**

| Strategy | Profit (RMB) | ROME |
|----------|-------------|------|
| Target Everyone | ~130,578 | ~4% |
| Model-Based Targeting | ~884,566 | ~56% |

> The targeted approach sent **56% fewer messages** while generating **6.8x more profit**.

---

## 💡 Business Implications

1. **Treating push notifications as "free" is a costly mistake.** The hidden cost of opt-outs means broadcast campaigns can destroy long-term customer value even when they generate short-term revenue.

2. **Targeting based on predicted purchase probability dramatically improves ROME.** By only messaging customers above the breakeven response rate, Tuango could cut wasteful spend while concentrating messages on high-intent users.

3. **RFM signals are strong predictors.** Monetary value and purchase frequency were the most important features — customers who spend more and buy more frequently are significantly more likely to convert on new deals.

4. **The model generalizes well.** Projected results from the test sample were validated against actual rollout outcomes, confirming the targeting strategy's real-world effectiveness.

---

## 📁 Files

| File | Description |
|------|-------------|
| `tuango.ipynb` | Full analysis notebook (EDA → modeling → profitability) |
| `tuango-case.pdf` | Business case background |
| `data/tuango_pre.parquet` | Pilot sample data (test = 1) |
| `data/tuango_post.parquet` | Full rollout data for validation |

---

## 🔗 Relevance to Consumer Product Analytics

This project mirrors the targeting decisions made by subscription and consumer apps every day:
- When should a platform send a re-engagement push vs. risk churn from notification fatigue?
- Which users have the highest conversion probability on a promotional offer?
- How do you quantify the true cost of over-messaging?

These are precisely the trade-offs relevant to **product analytics, growth, and marketing strategy** roles in consumer tech.
