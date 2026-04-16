# Mobile Push Notification Targeting Model
**Maximizing Campaign Profitability via Logistic Regression Targeting**

---

## Business Problem

Tuango (a Groupon-like deal platform in China) operated under the assumption that mobile push notifications were essentially free to send. In reality, the true marginal cost was **9 RMB per message** — because over-messaging customers caused them to block future notifications, permanently closing a high-value marketing channel.

The core question: which customers should receive a deal push notification to maximize profitability, and which should be skipped?

This problem mirrors targeting decisions faced by any consumer subscription or engagement-driven platform: when to send a nudge, to whom, and at what cost to long-term retention.

---

## Approach

**Dataset:** 20,908 randomly sampled mobile customers offered a karaoke deal (5% pilot from 418,160 eligible users in Hangzhou)

**Response Analysis**
Calculated baseline purchase rate and average order size from the pilot sample to establish campaign benchmarks.

**Targeting Models**
- Logistic regression to predict purchase probability using RFM variables and customer demographics
- Linear regression to predict order size among buyers
- Key predictors: monetary value, purchase frequency, music category history

**Profitability Framework**
- Derived breakeven response rate from campaign margin structure
- Compared broadcast vs. model-based targeting across projected and actual rollout outcomes

**Tech Stack:** Python, Polars, pyrsm, plotnine

---

## Results

| Metric | Value |
|--------|-------|
| Pilot response rate | ~9.3% |
| Average order size (buyers) | 3.94 sessions |
| Breakeven response rate | ~9.3% |
| Messages sent — targeted approach | ~174,671 (vs. 397,252) |

**Campaign Profitability Comparison (Projected)**

| Strategy | Profit (RMB) | ROME |
|----------|-------------|------|
| Broadcast (target everyone) | ~130,578 | ~4% |
| Model-based targeting | ~884,566 | ~56% |

The targeted approach sent 56% fewer messages while generating 6.8x more profit.

---

## Key Takeaways

**Treating push notifications as free is costly.** The hidden cost of opt-outs means broadcast campaigns can erode long-term customer value even when they generate short-term revenue.

**Targeting by predicted purchase probability dramatically improves ROME.** Restricting outreach to customers above the breakeven response rate concentrates spend on high-intent users and eliminates wasteful messaging.

**RFM signals are the strongest predictors.** Monetary value and purchase frequency were the most important features — customers who spend more and transact more frequently convert at significantly higher rates on new deal offers.

**The model generalizes.** Projected results from the pilot sample were validated against actual rollout outcomes across 397,252 customers, confirming real-world effectiveness of the targeting strategy.

---

## Files

| File | Description |
|------|-------------|
| `tuango.ipynb` | Full analysis: EDA, modeling, profitability framework |
| `tuango-case.pdf` | Business case background |
| `data/tuango_pre.parquet` | Pilot sample data used for model training |
| `data/tuango_post.parquet` | Full rollout data used for validation |
