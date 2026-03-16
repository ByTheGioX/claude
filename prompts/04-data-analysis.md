# 100 AI Mega Prompts for Business
## Category 04: Data Analysis & Reporting

> **10 expert-level prompts** that help you interpret data, build executive reports, design dashboards, write SQL queries, spot trends, and turn raw numbers into decisions — without needing a data science degree. Each prompt replaces 1–3 hours of manual analysis work.

---

## Prompt 1: The Executive Summary Report Builder

**Title:** *Data Narrator — Turn Raw Metrics Into a Board-Ready Executive Summary*

### Prompt

```
You are a senior business analyst and management consultant who specialises in translating complex data into clear, decision-enabling executive summaries. Your reports are known for cutting through noise and telling leadership exactly what they need to know — and what they need to do about it.

Context:
- Company name: {company_name}
- Report type: {report_type — e.g. "Monthly Business Review", "Quarterly Board Update", "Weekly KPI Digest"}
- Reporting period: {reporting_period — e.g. "Q1 2025", "Week of March 10"}
- Audience: {audience — e.g. "CEO and C-suite", "Board of Directors", "Department Heads"}
- Key metrics to include (paste raw numbers): {raw_metrics}
- Previous period metrics for comparison: {prior_period_metrics}
- Targets or budgets for each metric: {targets}
- Context or events that affected the numbers (e.g. product launch, outage, seasonal shift): {context_notes}
- 2–3 decisions or actions the leadership team needs to take based on this data: {required_decisions}
- Format preference: {format — e.g. "written narrative", "bullet-point briefing", "slide-ready sections"}

Write a complete executive summary that includes:

1. **Headline (1 sentence):** The single most important thing leadership needs to know this period
2. **At-a-Glance Scorecard:** A table showing each metric vs. target vs. prior period with a status indicator (on track / at risk / off track)
3. **What Happened (3–4 paragraphs):** The story behind the numbers — what drove performance up or down, any anomalies, and what's a trend vs. a one-off
4. **What It Means:** 3 bullet points translating the data into business implications — not observations, but so-what statements
5. **Recommended Actions:** 3 specific, time-bound recommendations with owners
6. **What to Watch:** 2 leading indicators to monitor in the next period

Write in clear, confident prose. No passive voice. No hedging language like "it appears" or "it seems." If something is a hypothesis, label it clearly. Length: 400–600 words for the narrative sections.
```

### Example Output

**Headline:** Revenue grew 18% YoY but gross margin compression in the mid-market segment requires immediate pricing review.

---

**At-a-Glance Scorecard:**

| Metric | Target | Actual | vs. Prior Period | Status |
|---|---|---|---|---|
| Total Revenue | $2.4M | $2.51M | +18% YoY | ✅ On Track |
| Gross Margin | 72% | 67% | -5pp | 🔴 Off Track |
| New ARR | $380K | $341K | -12% MoM | 🟡 At Risk |
| Churn Rate | <2% | 2.4% | +0.4pp | 🟡 At Risk |
| NPS | >50 | 54 | +3 pts | ✅ On Track |

---

**What Happened:**

Revenue exceeded target for the third consecutive quarter, driven primarily by enterprise expansion revenue — existing accounts grew an average of 23% through upsells on the new Analytics module. This is a structural positive: expansion revenue now represents 61% of new ARR, up from 44% twelve months ago.

However, the margin story is more complex. Gross margin fell to 67% — 5 points below target — due to a combination of increased cloud infrastructure costs (up 31% following the data centre migration) and a pricing concession pattern in the mid-market segment. Analysis shows that mid-market AEs are discounting an average of 19% off list price, compared to 9% for enterprise deals. This is the primary margin leak and it is structural, not seasonal...

*(Report continues through all sections)*

---

**Recommended Actions:**
1. **Pricing review (Owner: CRO — due April 15):** Audit mid-market discount authority and set a 12% discount floor without VP approval
2. **Infrastructure cost audit (Owner: CTO — due April 8):** Identify top 3 cost drivers in new data centre setup; target 15% reduction by Q2 close
3. **Churn investigation (Owner: VP CS — immediate):** Pull cohort analysis on the 6 accounts that churned; identify whether this is a product, onboarding, or ICP fit issue

---

### Variations

**Variation A — Investor Update**
> Adjust the audience to investors or a board with equity stakes. Add: *"Include a fundraising or runway section. Frame all metrics relative to the investment thesis. Use investor-standard language: ARR, NRR, CAC, LTV, burn multiple. Keep the tone confident and forward-looking — acknowledge risks but never dwell."*

**Variation B — Department-Level Operations Report**
> Narrow the scope: *"Write this as an internal ops report for a single department head (e.g. VP Marketing, Head of Engineering). Focus on operational metrics, team productivity, and process health — not financial metrics. The audience manages the work, not the business."*

---

---

## Prompt 2: The SQL Query Writer

**Title:** *SQL Translator — Convert Business Questions Into Ready-to-Run Queries*

### Prompt

```
You are a senior data analyst and SQL expert with deep experience across PostgreSQL, MySQL, BigQuery, Snowflake, and Redshift. You write clean, efficient, well-commented SQL that a non-technical stakeholder can understand and a senior engineer would be proud of.

Context:
- Database platform: {database_platform — e.g. "PostgreSQL", "BigQuery", "Snowflake", "MySQL"}
- The business question I need to answer: {business_question — describe in plain English what you're trying to find out}
- Tables available (describe each): {table_descriptions — e.g. "orders table: order_id, customer_id, created_at, total_amount, status; customers table: customer_id, email, plan_tier, signup_date, country"}
- Columns relevant to the query: {relevant_columns}
- Filters needed: {filters — e.g. "only paying customers", "last 90 days", "exclude test accounts with email domain @test.com"}
- Aggregation or grouping required: {grouping — e.g. "by month", "by plan tier", "by country"}
- Sort order: {sort_order}
- Output format I need: {output — e.g. "one row per customer", "monthly summary", "ranked list"}
- Any known data quality issues to work around: {data_issues — e.g. "nulls in the revenue column should be treated as 0", "duplicate rows in orders where status = 'duplicate'"}

Write the following:
1. The complete SQL query with inline comments explaining each major section
2. A plain-English explanation of what the query does (3–5 sentences, jargon-free)
3. Expected output structure (column names and data types)
4. 2 variations of the query:
   - A simplified version for quick exploration
   - An extended version that adds a useful additional dimension (e.g. period-over-period comparison, percentile ranking, or running total)
5. One potential performance optimisation note (indexing suggestion, partition filter, etc.)
6. 2 follow-up queries that would naturally come next given the business question

Write clean, readable SQL: use CTEs over nested subqueries, alias all columns clearly, and add a section header comment for each logical block.
```

### Example Output

```sql
-- ============================================================
-- QUERY: Monthly Revenue by Plan Tier (Last 12 Months)
-- Business question: How is revenue distributed across plan tiers
--                    and how has it trended month over month?
-- Platform: PostgreSQL
-- Author: [analyst name] | Created: 2025-03-10
-- ============================================================

WITH
-- Step 1: Filter to relevant orders in the last 12 months
-- Exclude test accounts and refunded/voided orders
base_orders AS (
    SELECT
        o.order_id,
        o.customer_id,
        DATE_TRUNC('month', o.created_at)  AS revenue_month,
        COALESCE(o.total_amount, 0)         AS revenue,  -- treat NULLs as 0
        c.plan_tier
    FROM orders o
    INNER JOIN customers c
        ON o.customer_id = c.customer_id
    WHERE
        o.created_at >= NOW() - INTERVAL '12 months'
        AND o.status NOT IN ('refunded', 'voided', 'duplicate')
        AND c.email NOT LIKE '%@test.com'              -- exclude test accounts
),

-- Step 2: Aggregate revenue by month and plan tier
monthly_revenue AS (
    SELECT
        revenue_month,
        plan_tier,
        COUNT(DISTINCT customer_id)  AS paying_customers,
        SUM(revenue)                 AS total_revenue,
        AVG(revenue)                 AS avg_revenue_per_customer
    FROM base_orders
    GROUP BY
        revenue_month,
        plan_tier
)

-- Step 3: Final output — sorted by month descending, then tier
SELECT
    TO_CHAR(revenue_month, 'YYYY-MM')  AS month,
    plan_tier,
    paying_customers,
    ROUND(total_revenue, 2)            AS total_revenue,
    ROUND(avg_revenue_per_customer, 2) AS arpc
FROM monthly_revenue
ORDER BY
    revenue_month DESC,
    total_revenue DESC;
```

**Plain-English explanation:**
This query pulls all paid, non-test orders from the past 12 months, joins them to customer plan tier information, and groups the results by month and plan tier. For each group, it counts the number of unique paying customers and calculates total and average revenue. The result is a monthly breakdown showing how revenue is split across your pricing tiers — useful for spotting which tier is growing fastest and whether average revenue per customer is rising or falling over time.

---

**Extended variation — adds MoM % change:**

```sql
-- Adds LAG() to calculate month-over-month revenue growth per tier
SELECT
    month,
    plan_tier,
    total_revenue,
    LAG(total_revenue) OVER (
        PARTITION BY plan_tier ORDER BY month
    )                                                        AS prior_month_revenue,
    ROUND(
        (total_revenue - LAG(total_revenue) OVER (
            PARTITION BY plan_tier ORDER BY month)
        ) / NULLIF(LAG(total_revenue) OVER (
            PARTITION BY plan_tier ORDER BY month), 0) * 100
    , 1)                                                     AS mom_growth_pct
FROM monthly_revenue
ORDER BY month DESC, total_revenue DESC;
```

---

### Variations

**Variation A — No SQL Knowledge (Natural Language Only)**
> Change the prompt framing to: *"I don't know SQL. Describe to me in step-by-step plain English exactly what data I need to pull and in what order, so I can hand this description to a data analyst or paste it into a BI tool's query builder."*

**Variation B — dbt Model Writer**
> Adjust to: *"Write this as a dbt model instead of a raw SQL query. Include the model config block, source references using {{ source() }} and {{ ref() }}, and a schema.yml file with column-level documentation and tests (not_null, unique, accepted_values)."*

---

---

## Prompt 3: The Dashboard Design Brief

**Title:** *Dashboard Architect — Design a KPI Dashboard That Drives Decisions, Not Just Views*

### Prompt

```
You are a data visualisation strategist and BI architect who has designed dashboards for Fortune 500 companies and fast-growth startups. You know that 80% of dashboards are ignored because they're built for the person who made them, not the person who uses them. Help me design a dashboard that leaders actually open every week.

Context:
- Dashboard name and purpose: {dashboard_name_and_purpose}
- Primary audience: {audience — role, seniority, how data-savvy they are}
- How often it will be reviewed: {review_frequency — e.g. "daily", "every Monday morning", "monthly board meeting"}
- The top 3 decisions this dashboard should enable: {decisions}
- Data sources available: {data_sources — e.g. "Salesforce", "Google Analytics", "Stripe", "PostgreSQL", "Mixpanel"}
- BI tool being used: {bi_tool — e.g. "Looker", "Tableau", "Power BI", "Metabase", "Google Data Studio"}
- Key metrics to include: {key_metrics}
- Time ranges needed: {time_ranges — e.g. "current week vs. last week", "MTD vs. prior month", "rolling 90 days"}
- Filters the user needs: {filters — e.g. "by region", "by product line", "by sales rep"}
- Alerts or thresholds to flag: {alert_thresholds}

Design a complete dashboard brief including:

1. **Dashboard Architecture** — how many sections, what goes where, and why (above the fold vs. below)
2. **Metric Hierarchy** — which 3 metrics go in the hero row (most prominent), which go in the secondary row, which go in detail sections
3. **Chart Type Recommendations** — for each metric, the ideal visualisation type and why (with one alternative)
4. **Colour and Status Logic** — define the colour system (green/amber/red thresholds for each metric)
5. **Filter Design** — which filters are global vs. local, and what the default view should be
6. **Refresh Cadence** — recommended data refresh frequency per data source
7. **Annotation Guidelines** — when and how to add context annotations to charts
8. **Anti-patterns to avoid** — 5 common dashboard mistakes to explicitly avoid for this use case
```

### Example Output

**Dashboard Architecture:**

*Name:* Weekly Revenue Operations Dashboard
*Audience:* CRO + VP Sales (review every Monday, 8am)
*Decisions enabled:* (1) Where to focus coaching effort, (2) Forecast accuracy review, (3) Pipeline health check

---

**Section Layout:**

**Hero Row (above the fold — always visible):**
3 KPI tiles: New ARR this month | Forecast vs. Target | Pipeline Coverage Ratio
*Why:* These are the three numbers the CRO checks first. Every other metric is context for these three.

**Row 2 — Pipeline Health:**
- Pipeline by stage (horizontal bar, colour-coded by age)
- Win rate by rep (bar chart, sortable)
- Average sales cycle trend (line, 13-week rolling)

**Row 3 — Activity & Forecast:**
- Forecast waterfall (current quarter: committed / best case / closed won)
- Deal slippage tracker (table: deals that moved out of forecast vs. last week)
- New pipeline added this week (by source)

**Below the fold — Detail Drill:**
- Rep-level scorecard table (all metrics, filterable by team/segment)
- Stage conversion funnel (interactive)
- Historical win/loss by competitor (last 90 days)

---

**Chart Type Recommendations:**

| Metric | Recommended Chart | Why | Alternative |
|---|---|---|---|
| New ARR vs. Target | KPI tile with sparkline | Immediate status read + trend in one glance | Bullet chart |
| Pipeline by stage | Stacked horizontal bar | Shows volume and composition simultaneously | Funnel chart |
| Win rate by rep | Ranked bar chart | Easy comparison, ranking drives action | Table with conditional formatting |
| Forecast waterfall | Waterfall chart | Shows movement between categories intuitively | Grouped bar |

---

**Anti-patterns to avoid:**
1. **The data dump:** Don't include every available metric — this dashboard should have ≤15 metrics total
2. **Pie charts for anything with >4 categories:** They become unreadable; use a sorted bar chart
3. **No default time filter:** Always set a sensible default (e.g. current quarter) so users don't open a blank-looking dashboard
4. **Metrics without targets:** A number without context is decoration, not data
5. **Daily refresh for weekly-reviewed data:** Unnecessary processing cost and creates false urgency

---

### Variations

**Variation A — Marketing Dashboard**
> Change the domain: *"Redesign this brief for a Head of Marketing reviewing weekly campaign performance. Replace pipeline metrics with: CAC, MQL volume, channel attribution, email performance, and content engagement metrics."*

**Variation B — Product Analytics Dashboard**
> Change the domain: *"Design a product analytics dashboard for a Head of Product. Include: DAU/MAU, feature adoption rates, retention curves, NPS by cohort, and a funnel from signup to activation. Recommend using Mixpanel or Amplitude chart types."*

---

---

## Prompt 4: The Trend Analysis & Insight Generator

**Title:** *Pattern Finder — Spot Trends, Anomalies, and Opportunities Hidden in Your Data*

### Prompt

```
You are a quantitative analyst and data scientist with expertise in identifying meaningful patterns in business data. You know the difference between a trend and noise, between a correlation and a cause, and between a vanity metric and an actionable insight. Analyse the data I provide and surface insights that a non-technical business leader can act on.

Data context:
- What this data represents: {data_description — e.g. "weekly website traffic by channel for the past 52 weeks"}
- The business context (what's been happening in the business): {business_context — e.g. "we launched a new product in February, ran a paid campaign in March"}
- The raw data (paste table, CSV, or describe the numbers): {raw_data}
- Metrics included: {metrics_list}
- Time period covered: {time_period}
- Granularity: {granularity — e.g. "daily", "weekly", "monthly"}
- What I was hoping to find or disprove: {hypothesis}
- Decisions I need to make based on this analysis: {decisions_needed}

Conduct the following analysis:

1. **Data Quality Check:** Note any obvious gaps, anomalies, or issues in the data before analysing (don't just assume the data is clean)

2. **Descriptive Summary:** Key statistics for each metric (mean, median, high, low, trend direction) — in plain language, not a statistics lecture

3. **Trend Identification:** What directional patterns are visible over the time period? Is performance accelerating, decelerating, or plateauing? Are there seasonal patterns?

4. **Anomaly Detection:** What data points are statistically or practically unusual? When did they occur and what might explain them?

5. **Correlation Analysis:** Which metrics move together? Which move in opposite directions? Flag any interesting relationships worth investigating further.

6. **Insight Statements (5 minimum):** Each insight must follow this format:
   - Observation: what the data shows
   - So what: why it matters to the business
   - Recommended action: what to do about it

7. **Limitations:** What this data does NOT tell you — what additional data would make the analysis stronger.
```

### Example Output

**Data Quality Check:**
Three issues to flag before analysing:
- Weeks 14 and 15 show zero organic traffic — likely a tracking outage, not genuine zero traffic. Recommend excluding from trend calculations.
- The "direct" channel shows a spike of 340% in week 22 — likely misattributed paid or referral traffic from the campaign launch. Should be split before drawing conclusions about true direct traffic.
- Conversion rate column contains two negative values (weeks 31 and 32) which are mathematically impossible — probably a data pipeline error.

---

**Trend Identification:**

Organic search traffic has grown consistently at approximately 4.2% per month over 52 weeks — a healthy, compounding growth rate that suggests SEO investment is working. However, growth rate has decelerated from 6.1% in H1 to 2.3% in H2, suggesting the early keyword gains are saturating and a new content push is needed to maintain momentum.

Paid search shows a different story: high volume, high cost, declining conversion rate. CTR has remained stable but conversion rate from paid click to trial has fallen from 4.1% to 2.7% over the year — a 34% drop. This is not a traffic problem; it is a landing page or product-market fit signal worth investigating urgently.

---

**Insight #1:**
- **Observation:** Email-referred traffic converts at 3.8x the rate of all other channels combined
- **So what:** Email is your highest-quality channel by far, but it represents only 8% of total traffic — it is massively underinvested
- **Recommended action:** Increase email send frequency from bi-weekly to weekly, and build a referral/forwarding mechanic into each issue to compound list growth

---

### Variations

**Variation A — Cohort Analysis Interpreter**
> Narrow the focus: *"Analyse this cohort retention data specifically. Identify which cohorts retain best, where the steepest drop-off occurs in the customer lifecycle, and what month-1 retention predicts for 12-month LTV."*

**Variation B — Competitive Benchmarking Analysis**
> Add a benchmarking layer: *"Compare my metrics against the industry benchmarks I'll provide. Identify where I'm above benchmark (competitive advantage), at benchmark (table stakes), and below benchmark (priority gaps). Rank the gaps by revenue impact."*

---

---

## Prompt 5: The A/B Test Results Interpreter

**Title:** *Experiment Analyst — Interpret A/B Test Results and Make a Clear Call*

### Prompt

```
You are a product analytics expert and statistician who interprets A/B test results for product and growth teams. You cut through statistical jargon and help teams make clear, confident decisions — including knowing when the data is not yet good enough to decide.

Test context:
- What was tested: {test_description — e.g. "two versions of the onboarding flow", "pricing page CTA button copy", "email subject line"}
- Hypothesis going into the test: {hypothesis — e.g. "we believe changing the CTA from 'Start Free Trial' to 'Try It Free' will increase click-through rate"}
- Control version (A): {control_description}
- Test version (B): {test_description}
- Primary metric: {primary_metric — e.g. "conversion rate", "click-through rate", "revenue per visitor"}
- Secondary metrics tracked: {secondary_metrics}
- Test duration: {test_duration}
- Sample sizes: Control: {control_n} | Test: {test_n}
- Results:
  - Control: {control_result — e.g. "3.2% conversion rate"}
  - Test: {test_result — e.g. "3.9% conversion rate"}
- Statistical significance level achieved: {significance — e.g. "92%", "not calculated"}
- Confidence interval (if known): {confidence_interval}
- Any segment breakdowns available: {segments — e.g. "by device type", "by traffic source"}

Provide:
1. **The verdict:** Ship it / Don't ship it / Need more data — and the primary reason in one sentence
2. **Statistical interpretation:** Was this test valid? Was the sample large enough? Was the test duration appropriate (accounting for day-of-week effects)? What is the risk of a false positive?
3. **Practical significance:** Even if statistically significant, is the effect large enough to matter for the business?
4. **Segment analysis:** Did the effect hold uniformly, or was it stronger/weaker in certain segments?
5. **Risk assessment:** What's the downside if we ship B and the effect doesn't hold in production?
6. **Recommended next steps:** What to do with the winning variant AND what to test next
7. **What this test does NOT prove:** Scope limitations — don't over-generalise the result
```

### Example Output

**The Verdict:** Ship it — but with a monitoring period.

The test shows a statistically significant lift (p=0.031, above the 0.05 threshold) and the absolute improvement of 0.7 percentage points represents a 22% relative uplift. At current traffic volumes, this translates to approximately 140 additional trial signups per month — worth shipping.

---

**Statistical Interpretation:**

The test ran for 21 days across 8,400 visitors per variant — sufficient for both statistical power and day-of-week coverage. One concern: the test was started on a Thursday, meaning the first week is weighted toward weekend traffic which converts differently. Recommend verifying that week 1 and weeks 2–3 show consistent direction.

Significance reached 96.9% — above the conventional 95% threshold. However, the confidence interval for the true effect is 0.2pp to 1.2pp, meaning there is a plausible scenario where the real effect is quite small. Don't plan resource allocation assuming the full 0.7pp gain.

---

**Segment Analysis:**

The headline result masks meaningful segment variation:
- Mobile visitors: +1.4pp lift (strong — ship immediately for mobile)
- Desktop visitors: +0.1pp lift (not significant — inconclusive for desktop)
- Organic traffic: +0.9pp lift
- Paid traffic: +0.2pp lift

Recommendation: consider shipping the new variant for mobile and organic segments immediately, and running a separate desktop-focused test before rolling out universally.

---

### Variations

**Variation A — Underpowered Test (Inconclusive Result)**
> Adjust the inputs for a test that didn't reach significance: *"The test ran for 7 days with 400 visitors per variant and hasn't reached significance. Help me determine the minimum sample size needed, the projected time to significance at current traffic, and whether to extend the test or kill it."*

**Variation B — Multi-Variant Test (A/B/C)**
> Adjust for three variants: *"Interpret results across three variants. Account for the multiple comparison problem (apply Bonferroni correction or Benjamini-Hochberg). Identify the clear winner if one exists, and advise on whether pairwise follow-up tests are needed."*

---

---

## Prompt 6: The Financial Model Explainer

**Title:** *Finance Translator — Make Complex Financial Models Understandable to Any Audience*

### Prompt

```
You are a CFO-level financial advisor and communication specialist who can take complex financial models and make them understandable to non-finance audiences — without dumbing them down or losing precision. Help me explain a financial model or set of financials in plain language.

Context:
- The financial model or data I need explained: {model_description — paste figures or describe the model}
- The raw numbers or outputs (paste or describe): {financial_data}
- The audience for this explanation: {audience — e.g. "non-finance department heads", "potential investors", "board members", "employees at an all-hands"}
- Their financial literacy level: {literacy_level — e.g. "no finance background", "business-savvy but not finance specialists", "sophisticated investors"}
- The key question the audience has: {audience_question — e.g. "Are we healthy?", "Should we invest in this?", "What does this mean for headcount?"}
- What I want them to understand and feel after reading this: {desired_outcome}
- Any sensitive information to handle carefully: {sensitive_items}
- Format: {format — e.g. "written memo", "slide talking points", "verbal script for all-hands meeting"}

Write:
1. **The plain-English narrative** — explain the model story in 3–4 paragraphs using analogies where helpful; avoid jargon; define any financial term you must use
2. **The 3 numbers that matter most** — identify the three figures that tell 90% of the story, and explain why each one matters
3. **The so-what statement** — one paragraph connecting the financial picture to what it means for this specific audience (jobs, investment, strategy)
4. **Anticipated questions and answers** — the 5 questions this audience is most likely to ask, with plain-language answers
5. **What the model does not show** — important limitations or assumptions the audience should know about

Also write: a one-paragraph version (the "elevator pitch" of the financials) for when you only have 60 seconds.
```

### Example Output

**Plain-English Narrative:**

Think of the business like a shop. This year, we brought in $8.2 million in revenue — that's everything customers paid us. After paying for the things that went directly into delivering our product (our cloud infrastructure, third-party licences, and customer success team), we kept $5.7 million. That's our gross profit, and at 70% of revenue, it's healthy — it means for every dollar a customer pays us, we keep 70 cents before we pay for marketing, sales, or our office.

The challenge is what happens next. We spent $7.1 million on running the business — sales, marketing, engineering, G&A. That's $1.4 million more than we earned in gross profit, which means we're running at an operating loss of $1.4 million. That's intentional — we're investing in growth — but it's worth understanding what's driving it...

---

**The 3 Numbers That Matter Most:**

1. **70% Gross Margin:** Healthy. This means our unit economics work — each customer we sign is profitable at the product level. We can grow without the product getting more expensive to deliver.

2. **-$1.4M Operating Loss:** We're spending $1.40 for every $1.00 of gross profit. The key question is: is that investment producing pipeline that will pay back? The answer requires looking at sales efficiency, which brings us to number 3.

3. **$2.80 CAC Payback (in months):** It takes us 28 months to recover what we spend to acquire a customer. Industry benchmark for SaaS at our stage is 18 months. This is the metric we need to fix — and the model shows a clear path to 20 months by Q4 if we hit our enterprise targets.

---

### Variations

**Variation A — Startup Fundraising Narrative**
> Adjust the audience to investors: *"Rewrite this as a fundraising narrative for a Series A pitch. Frame every number in terms of growth trajectory, market opportunity, and return potential. Lead with the opportunity, not the financials."*

**Variation B — All-Hands Employee Communication**
> Adjust for a company-wide audience: *"Rewrite this for an all-hands meeting. Employees want to know: Is the company safe? Are our jobs secure? Are we growing? Answer those three questions directly, honestly, and without financial jargon."*

---

---

## Prompt 7: The Customer Segmentation Analyzer

**Title:** *Segment Strategist — Identify Your Most Valuable Customer Segments and What to Do With Them*

### Prompt

```
You are a customer analytics strategist who specialises in segmentation analysis for B2B and B2C companies. You help businesses stop treating all customers the same and start allocating resources toward the segments that drive disproportionate value. Conduct a segmentation analysis using the data I provide.

Context:
- Company and product: {company_and_product}
- Customer data available (describe the fields/dimensions): {data_fields — e.g. "customer ID, industry, company size, ARR, plan tier, signup date, last login date, NPS score, support tickets submitted, number of seats"}
- Total customer count: {total_customers}
- Sample data or summary statistics (paste if available): {data_or_summary}
- Business goal of this segmentation: {goal — e.g. "identify expansion opportunities", "reduce churn", "prioritise enterprise sales motion", "personalise marketing"}
- Current segmentation approach (if any): {current_approach}
- Resources available to act on segments: {resources — e.g. "a 3-person CS team", "a marketing automation tool", "a field sales team of 8"}

Conduct the following:

1. **Recommended Segmentation Dimensions:** Which 3–4 dimensions from the available data will produce the most actionable segments — and why

2. **Segment Identification:** Define 4–6 distinct customer segments based on the data. For each segment:
   - Name and description
   - Estimated % of customer base
   - Key characteristics (firmographic, behavioural, transactional)
   - Estimated % of total revenue
   - Strategic value (high/medium/low)
   - Biggest risk (churn risk, low expansion potential, etc.)

3. **Segment Strategy:** For each segment, the recommended action and channel

4. **The 80/20 Analysis:** Which segments likely make up 20% of customers but 80% of revenue — and what this means for resource allocation

5. **Quick Win:** One action you can take in the next 2 weeks using this segmentation without any new tooling

6. **Data Gaps:** What additional data would most improve the segmentation accuracy
```

### Example Output

**Recommended Segmentation Dimensions:**
Based on the data available, the four most powerful segmentation dimensions are:
1. **ARR** — directly determines economic value; the single most important dimension for resource allocation
2. **Product adoption score** (logins × features used) — predicts retention better than any firmographic variable
3. **Company size / employee count** — correlates with expansion potential and decision-making complexity
4. **Time to value** (days from signup to first meaningful action) — a leading indicator of long-term retention

---

**Segment Profiles:**

**Segment 1 — "Champions" (High ARR, High Adoption)**
- ~12% of customers | ~51% of revenue
- Characteristics: Enterprise, 500+ employees, using 7+ features, NPS 8–10, low support load
- Strategic value: Highest
- Risk: Complacency — they're quiet because things are working, but they're also your most attractive targets for competitors
- Action: Proactive QBRs, case study recruitment, reference programme, expansion conversations

**Segment 2 — "Sleeping Giants" (High ARR, Low Adoption)**
- ~8% of customers | ~19% of revenue
- Characteristics: Enterprise, purchased broadly but using narrowly; often bought by IT, used by one team
- Strategic value: High expansion potential, high churn risk
- Risk: Churn at renewal — they can't articulate value internally
- Action: Dedicated CSM, adoption playbook, executive stakeholder alignment

*(Segments 3–6 follow the same structure)*

---

**80/20 Analysis:**
Segments 1 and 2 combined represent approximately 20% of your customer base but generate 70% of ARR. Every CS hour spent on a long-tail SMB account is an hour not spent protecting and expanding your enterprise base. Recommend a tiered service model: high-touch for segments 1–2, tech-touch for segments 3–4, and self-serve for the tail.

---

### Variations

**Variation A — RFM Segmentation (E-commerce)**
> Reframe for a consumer or e-commerce context: *"Use RFM methodology (Recency, Frequency, Monetary value) to segment customers. Identify Champions, Loyal Customers, At-Risk customers, and Lost customers. Write a re-engagement strategy for each."*

**Variation B — ICP Scoring Model**
> Adjust the output: *"Use this segmentation analysis to build an Ideal Customer Profile (ICP) scoring model. Define the characteristics of a perfect-fit customer, assign point weights to each dimension, and produce a scoring rubric sales can use to qualify inbound leads."*

---

---

## Prompt 8: The Survey Data Analyzer

**Title:** *Survey Decoder — Turn Hundreds of Responses Into Clear Themes and Actionable Findings*

### Prompt

```
You are a qualitative and quantitative research analyst who specialises in making sense of survey data for business teams. You know how to move from raw responses to structured themes to clear recommendations — without losing the nuance in individual voices. Analyse the survey data I provide.

Survey context:
- Survey name and objective: {survey_name_and_objective}
- Who was surveyed: {respondent_profile}
- Total responses: {response_count}
- Response rate (if known): {response_rate}
- Survey type: {survey_type — e.g. "customer satisfaction", "employee engagement", "market research", "product feedback"}
- Quantitative results (paste rating/scale data): {quantitative_results}
- Open-text responses (paste or summarise): {open_text_responses}
- Key questions asked: {survey_questions}
- What decisions will be made based on this data: {decisions}

Produce the following analysis:

1. **Quantitative Summary:**
   - Score distributions for each rated question
   - Mean, median, and notable outliers
   - Score breakdown by any available segments (if data provided)
   - Trend vs. prior survey (if applicable)

2. **Qualitative Thematic Analysis:**
   - Identify 4–6 major themes from open-text responses
   - For each theme: theme name, frequency (approximate % of respondents), representative verbatims (3 quotes), and business implication

3. **Sentiment Analysis:**
   - Overall positive / neutral / negative sentiment breakdown
   - Top 5 positive themes
   - Top 5 negative themes / pain points

4. **Priority Matrix:**
   - Plot themes by: frequency (how often mentioned) vs. intensity (how strongly felt)
   - Identify the "high frequency + high intensity" quadrant as top priorities

5. **Recommended Actions (5 minimum):**
   - Each action tied to a specific finding, with a suggested owner and timeline

6. **Executive Summary (150 words):**
   - The 3 things leadership needs to know, and the 2 things they need to decide
```

### Example Output

**Quantitative Summary:**

Overall satisfaction: 3.9/5.0 (industry benchmark: 4.1)
Ease of use: 3.6/5.0 (lowest-scoring dimension — flagged)
Customer support quality: 4.4/5.0 (highest-scoring — a genuine strength)
Value for money: 3.8/5.0 (below benchmark of 4.0)

Score distribution for overall satisfaction:
- 5 (Very satisfied): 31%
- 4 (Satisfied): 28%
- 3 (Neutral): 22%
- 2 (Dissatisfied): 13%
- 1 (Very dissatisfied): 6%

Notable: The 19% scoring 1–2 is elevated. Correlating with open-text reveals this group is disproportionately newer customers (< 3 months) — an onboarding signal, not a product quality signal.

---

**Thematic Analysis:**

**Theme 1 — Steep Learning Curve (mentioned by ~38% of respondents)**
*Representative verbatims:*
- *"Takes too long to figure out where things are — the navigation is confusing."*
- *"I had to watch 3 videos before I understood how to set up my first report."*
- *"My team gives up and asks me to do it for them because it's not intuitive."*
*Business implication:* Onboarding friction is a churn risk. This is a UX and documentation problem, not a features problem.

*(Themes 2–6 follow the same format)*

---

**Priority Matrix:**

| Theme | Frequency | Intensity | Priority |
|---|---|---|---|
| Steep learning curve | High (38%) | High | 🔴 Act now |
| Missing integrations | High (31%) | Medium | 🟡 Plan for next quarter |
| Pricing transparency | Medium (22%) | High | 🔴 Act now |
| Slow report load times | Medium (19%) | High | 🔴 Act now |
| Mobile experience | Low (11%) | Low | 🟢 Monitor |

---

### Variations

**Variation A — Employee Engagement Survey**
> Refocus: *"Analyse employee engagement survey data. Group themes by: Manager effectiveness, career development, culture/belonging, compensation, and workload. Flag any themes that are legal or HR risks requiring immediate attention."*

**Variation B — NPS Verbatim Analyzer**
> Narrow the scope: *"Analyse only the open-text verbatim comments from an NPS survey. Separate promoter verbatims from detractor verbatims. Extract the top 5 reasons people love us and the top 5 reasons people don't recommend us."*

---

---

## Prompt 9: The Forecasting Model Builder

**Title:** *Revenue Forecaster — Build a Defensible Forecast From Historical Data and Assumptions*

### Prompt

```
You are a financial planning and analysis (FP&A) specialist who builds revenue forecasts for SaaS, services, and product businesses. You know how to build a forecast that's credible enough for a board, flexible enough for scenario planning, and simple enough for a sales leader to actually use. Build me a revenue forecast.

Context:
- Company and business model: {company_and_model — e.g. "B2B SaaS, subscription revenue", "professional services", "e-commerce"}
- Forecast period: {forecast_period — e.g. "Q2 2025", "FY2026", "next 18 months"}
- Historical data available (paste or describe): {historical_data — e.g. "monthly revenue for last 24 months", "annual revenue for last 3 years"}
- Key revenue drivers: {revenue_drivers — e.g. "new customer acquisition, expansion revenue, churn rate" or "units sold × average order value"}
- Current ARR or revenue run rate: {current_arr}
- Known pipeline or committed revenue: {committed_pipeline}
- Growth assumptions you want to model: {growth_assumptions — e.g. "20% YoY", "50 new customers per quarter at $24K ACV"}
- Key risks to model: {risks — e.g. "potential churn acceleration", "delayed hiring plan", "seasonal dip in Q3"}
- Desired output format: {format — e.g. "monthly breakdown", "quarterly with annual total", "three scenarios"}

Build the following:

1. **Forecast Model Structure:** The recommended method for this business type (bottom-up vs. top-down, driver-based vs. run-rate) and why

2. **Base Case Forecast:** Month-by-month or quarter-by-quarter revenue projection with the assumptions behind each line

3. **Scenario Analysis (3 scenarios):**
   - Bear case: What happens if 2 key assumptions miss by 20%
   - Base case: Most likely outcome given current trajectory
   - Bull case: What's achievable if pipeline converts at the high end

4. **Key Assumptions Log:** A table of every assumption baked into the model, its source, and its confidence level

5. **Sensitivity Analysis:** Which 3 variables have the biggest impact on the forecast? What's the revenue impact of a 1% change in each?

6. **Forecast Narrative (200 words):** How to present this forecast in a board meeting — what to say, what to emphasise, what risks to flag proactively
```

### Example Output

**Forecast Model Structure:**

For a B2B SaaS business at this stage, a driver-based bottom-up model is recommended over a simple top-down growth rate. The reason: top-down ("we'll grow 30%") is unfalsifiable and offers no diagnostic value when you miss. A driver-based model breaks revenue into its components — new ARR from new logos, expansion ARR from existing accounts, and lost ARR from churn — which means you can see *why* you're off forecast, not just *that* you're off.

The model structure: `Beginning ARR + New ARR + Expansion ARR - Churned ARR = Ending ARR`

---

**Base Case Forecast (Q1–Q4):**

| Quarter | Beginning ARR | New ARR | Expansion ARR | Churned ARR | Ending ARR |
|---|---|---|---|---|---|
| Q1 | $4.2M | $340K | $180K | -$95K | $4.625M |
| Q2 | $4.625M | $380K | $210K | -$102K | $5.113M |
| Q3 | $5.113M | $350K | $225K | -$110K | $5.578M |
| Q4 | $5.578M | $420K | $260K | -$118K | $6.140M |

**FY2025 Total New ARR:** $1.49M | **Year-end ARR:** $6.14M | **YoY Growth:** 46%

---

**Sensitivity Analysis:**

| Variable | Base Assumption | Impact of +1% change | Impact of -1% change |
|---|---|---|---|
| Churn rate | 2.3% monthly | +$84K ARR | -$84K ARR |
| New logo ACV | $28,000 | +$52K ARR | -$52K ARR |
| Win rate | 24% | +$71K ARR | -$71K ARR |

*Churn rate is the highest-leverage variable. A 0.5pp churn improvement is worth more than a 20% increase in new logo volume at current pipeline levels.*

---

### Variations

**Variation A — Sales Pipeline Forecast**
> Reframe for a sales leader: *"Build a pipeline-based forecast using current CRM stage data. Apply historical stage-to-close conversion rates and average sales cycle length. Produce a 90-day commit forecast and a best-case forecast."*

**Variation B — Headcount & Cost Forecast**
> Shift from revenue to cost: *"Build a headcount-driven cost forecast. Model salary + benefits + tooling per role, phased by hire date. Show how headcount cost scales against projected revenue and flag the quarter where burn rate becomes a concern."*

---

---

## Prompt 10: The Data Story Presentation Builder

**Title:** *Data Storyteller — Transform an Analysis Into a Presentation That Gets People to Act*

### Prompt

```
You are a data storytelling expert and presentation strategist who has coached analysts at McKinsey, Google, and Airbnb on communicating insights to executive audiences. You know that the most important skill in data analysis isn't finding the insight — it's making someone care enough to act on it. Help me turn my analysis into a presentation that drives a decision.

Context:
- The analysis I've done: {analysis_summary — describe what you found}
- Raw findings or data (paste): {findings}
- The audience: {audience — role, seniority, familiarity with data}
- The decision you want them to make after seeing this: {desired_decision}
- Their likely objection or hesitation: {anticipated_objection}
- Time available to present: {presentation_time — e.g. "10 minutes", "30-minute working session"}
- Presentation tool: {tool — e.g. "PowerPoint", "Google Slides", "Notion", "live Looker dashboard"}
- My narrative instinct (what I think the story is): {my_hypothesis}

Produce:

1. **The Single Storyline:** One sentence that captures the entire narrative arc of the presentation — the "so what" that every slide should serve

2. **Slide-by-Slide Structure:**
   For each slide:
   - Slide title (written as an insight statement, not a topic label — e.g. "Churn is accelerating in the mid-market" not "Churn Analysis")
   - One-sentence description of what goes on the slide
   - The "so what" point this slide makes
   - Recommended visual type

3. **The Recommendation Slide:** Full text of the ask — what you're recommending, why, what it costs, and what the expected outcome is

4. **Speaker Notes for the 3 Most Important Slides:** What to say, what not to say, and how to handle the most likely question

5. **The One-Slide Version:** If you only had one slide to make the entire case, what would it contain? (For executives who won't see the full deck)

6. **Objection Handling:** Prepare 3 responses to the most likely challenges the audience will raise
```

### Example Output

**The Single Storyline:**
*"Mid-market churn is accelerating due to an onboarding gap we can fix in 60 days for $40K — and if we don't, we'll lose $1.2M in ARR by year-end."*

---

**Slide Structure:**

**Slide 1 — Title:** "We have 60 days to fix a $1.2M problem"
*Content:* The headline number and the timeframe. Nothing else.
*So what:* Creates urgency from slide one.
*Visual:* Bold text only — no charts yet.

**Slide 2:** "Mid-market churn has doubled in 6 months"
*Content:* Line chart showing churn rate trend for mid-market segment vs. enterprise over 12 months
*So what:* The problem is real, recent, and accelerating — not noise
*Visual:* Line chart with clear divergence callout

**Slide 3:** "The root cause is a 14-day activation gap, not product quality"
*Content:* Funnel chart showing where mid-market customers drop off vs. enterprise; time-to-first-value comparison
*So what:* This is an onboarding problem, not a product problem — it's solvable
*Visual:* Side-by-side funnel comparison

**Slide 4:** "Three companies fixed this. Here's the playbook."
*Content:* 3-column benchmark comparison (Intercom, Notion, Loom) showing their onboarding interventions and churn impact
*So what:* This is a proven approach, not a theory
*Visual:* Comparison table with outcome callouts

**Slide 5 — The Ask:** "Approve a 60-day onboarding sprint: $40K investment, $1.2M ARR protected"
*Content:* Investment breakdown, timeline, expected outcome, owner, and success metric
*So what:* A clear, bounded ask with a defined return

---

**The One-Slide Version:**

| The Problem | The Cause | The Fix | The Cost | The Return |
|---|---|---|---|---|
| Mid-market churn doubled in 6 months | 68% of churned accounts never completed onboarding | Dedicated onboarding programme for first 30 days | $40K (1 hire + tooling) | $1.2M ARR protected; payback in 5 weeks |

---

**Objection Handling:**

*"How confident are you in the $1.2M figure?"*
> "Conservative estimate based on current churn rate applied to the at-risk cohort — 47 accounts, average $25K ARR. Even if only half churn, that's $590K. The investment pays back either way."

*"Is this really an onboarding problem or a product problem?"*
> "The data is clear: accounts that complete onboarding within 14 days churn at 1.8%. Accounts that don't: 11.4%. Same product, same price point, six-fold difference in churn rate. The product works — they just never learn to use it."

*"Why now — we have other priorities."*
> "Every month we wait costs approximately $100K in incremental churn from this cohort. At that rate, deferring one quarter costs more than the entire fix."

---

### Variations

**Variation A — Self-Serve Written Report (No Presentation)**
> Replace the slide structure with: *"Write this as a written memo in the Amazon-style 6-pager format: 1-page summary, problem statement, root cause analysis, proposed solution, financial case, and risks/open questions."*

**Variation B — Live Dashboard Walkthrough Script**
> Replace the deck with: *"Write a 10-minute verbal walkthrough script for a live dashboard. Structure it as: hook (what to look at first), narrative (what the data shows), decision point (what you need from the room). Include natural pause points for questions."*

---

---

*End of Category 04: Data Analysis & Reporting*

---

> **Part of the "100 AI Mega Prompts for Business" digital product.**
> Categories include: Sales & Cold Outreach · Content Creation & Repurposing · Customer Support Automation · Data Analysis & Reporting · Hiring & HR · Operations · Leadership & Strategy · Customer Success · Finance · Legal · and more.
