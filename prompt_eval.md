# AI Prompt Evaluation Report

## 1. Overall Score

| Parameter | Maximum Marks | Awarded Marks | Percentage | Grade |
|---|---:|---:|---:|---|
| **Prompt Clarity** | 100 | 84 | 84% | Strong |
| **Output Quality** | 100 | 54 | 54% | Needs work |
| **Efficiency** | 50 | 39 | 78% | Developing |
| **Total Score** | **250** | **177** | **70.8%** | **Developing** |

Grades use these percentage bands: Strong = 80-100%, Developing = 60-79%, Needs work = below 60%. The skill's separate production benchmark is 85+ for each 100-point parameter and 42+ for Efficiency.

## 2. Executive Summary

- **Verdict:** A clear, useful business-planning prompt with unusually strong constraints and deliverable coverage. Its biggest weakness is that it asks for several interdependent financial tables without defining a consistent accounting model or validation method.
- **Estimated Tokens:** ~478 tokens, estimated from 354 whitespace-separated words at 1.35 tokens per word; actual tokenizer counts vary.
- **Strengths:**
  - Gives concrete operating context: "6 working days (Mon–Sat), ~300 daily customers" and specific rush periods.
  - Establishes explicit priorities and a hard capital constraint, including the use of daily sales revenue.
  - Specifies a broad, practical deliverable set, from menu economics and cash flow to hygiene, waste, and KPIs.
- **Key Vulnerabilities / Deficits:**
  - Doesn't define whether budget allocation, daily spend, remaining inventory, and profit use cash or accrual accounting.
  - "Approximate current Indian market prices" lacks a location, date/source requirement, or fallback for unavailable live price data.
  - No worked example or explicit reconciliation equations ensure all tables agree.

## 3. Evaluated Prompt Content

```text
Act as an experienced college canteen manager and food-business analyst in India.

CONTEXT: I have ₹10,000 as starting capital to improve my college canteen for ONE week. Assume 6 working days (Mon–Sat), ~300 daily customers (students + staff), price-sensitive, with item prices ranging from ₹10 (chai, samosa) to ₹90 (full meal). Rush hours: 10:30–11:00 AM, 1:00–2:00 PM and 4:00–5:00 PM. Each day's sales revenue can be reinvested into the next day's ingredients (revolving capital), but total cash out of pocket must never exceed ₹10,000.

PRIORITY ORDER: (1) Stay within the ₹10,000 limit, (2) student satisfaction, (3) profit, (4) minimum food waste.

Do not ask me any questions. Make reasonable assumptions, list them at the top, and then give the complete plan.

DELIVER:
1. Executive summary – 3 lines.
2. Budget allocation table – ₹10,000 split across Day-1 ingredients, packaging, small upgrades (menu board, UPI QR, pre-order setup), and a 10% emergency buffer.
3. Menu table – 6–8 items (breakfast, lunch, snacks, drinks), including at least 1 healthy and 1 high-protein veg option. For each: cost per unit, selling price, margin %, and why students will buy it.
4. Day-wise quantity table (Mon–Sat) – units per item, adjusted for demand (e.g., lower on Saturday).
5. Day-wise cash-flow table – opening cash, spend, revenue, closing cash – proving cash never goes negative.
6. Demand management – pre-orders via Google Form/WhatsApp, combo meals, token system for rush hours, and a discount on remaining items only in the last 30 minutes before closing. Explain how each day's sales data will adjust the next day's quantities.
7. Two creative low-cost ideas to boost footfall and excitement (e.g., student-voted "Dish of the Day", loyalty stamp card).
8. Waste, hygiene and risk plan – what to do if an item sells out or stays unsold, plus shelf-life and food-safety rules.
9. Final results – total cost, total revenue, profit, break-even day, and 3–4 KPIs (including a simple daily student feedback method).

RULES:
- Use approximate current Indian market prices.
- Double-check all calculations before answering; totals must match across tables.
- Use clean tables, be specific and practical, no generic advice.
```

## 4. Detailed Criterion Evaluations

### 4.1 Prompt Clarity (Awarded: 84 / 100)
- **Role & Persona Definition:** 18 / 20
- **Task Specificity & Negative Constraints:** 23 / 25
- **Instruction Structure & Delimiters:** 18 / 20
- **Tone, Style & Target Audience:** 12 / 15
- **Unambiguous Language:** 13 / 20

**Detailed Analysis:**
- *What worked well:* The role is relevant and grounded in the setting: "experienced college canteen manager and food-business analyst in India." The prompt gives a fixed six-day schedule, approximate customer volume, price range, rush periods, capital cap, and ordered priorities. "Do not ask me any questions" also clearly defines how missing inputs should be handled.
- *Ambiguities & Gaps:* "Improve my college canteen" is broad, while "small upgrades" and "total cash out of pocket" are not operationally defined. It is unclear whether the 10% emergency buffer is a reserved amount or a cash expense, whether cash-on-hand includes unsold inventory, or how to define "break-even day." The instruction to make assumptions helps, but does not require assumptions for each of these high-impact accounting choices.

### 4.2 Output Quality & Schema Compliance (Awarded: 54 / 100)
- **Output Format & Schema Enforcement:** 23 / 30
- **Few-Shot Examples & In-Context Demos:** 0 / 25
- **Edge Cases & Fallbacks:** 20 / 25
- **Factuality & Hallucination Prevention:** 11 / 20

**Detailed Analysis:**
- *What worked well:* The numbered "DELIVER" list gives a strong response outline, asks for named tables, and specifies important fields such as "opening cash, spend, revenue, closing cash." It anticipates sell-outs and unsold food, requires a daily quantity adjustment method, and asks for calculations to reconcile.
- *Format Risks & Missing Guardrails:* There is no example of a reconciled row or formula for margin, cash balance, profit, or break-even. "Margin %" could mean gross margin on selling price or markup on cost. Daily quantities do not distinguish forecast sales from units prepared or purchased, and the cash-flow table does not state whether "spend" includes one-time upgrades, packaging, buffer allocation, or only replenishment. "Approximate current Indian market prices" risks false precision because prices vary by city and date; the prompt neither supplies a location nor directs the model to disclose price assumptions or lack of live data.

### 4.3 Efficiency & Token Economy (Awarded: 39 / 50)
- **Conciseness & Fluff Elimination:** 13 / 15
- **Token Economy & Context Footprint:** 13 / 15
- **Dynamic Parameterization:** 4 / 10
- **Signal-to-Noise Ratio:** 9 / 10

**Detailed Analysis:**
- *Efficiency Observations:* At roughly 354 words, the prompt is compact relative to its nine requested deliverables. Its headings and numbered list make the constraints easy to locate, and the priority order is high-signal.
- *Identified Token Waste / Redundancy:* There is little filler. The main opportunity is parameterization: location, currency/date basis, customer volume, operating days, and budget are fixed inline rather than exposed as reusable inputs. Some redundancy between "proving cash never goes negative" and "totals must match" can be replaced with explicit equations and a single reconciliation requirement.

## 5. Prioritized Recommendations for Improvement

1. **Define the financial model:** Specify how the ₹10,000 cap, reserved buffer, cash purchases, daily revenue, inventory, profit, and break-even are calculated. Require opening cash plus revenue minus outflows to equal closing cash for every day.
2. **Constrain estimates and sales assumptions:** Require a location/date or clearly labeled illustrative prices, disclose when current local prices cannot be verified, and distinguish units forecast, prepared, sold, and left over. Explain that multiple items may be bought by one customer.
3. **Make outputs mechanically auditable:** Define gross margin as `(selling price - unit cost) / selling price × 100`, require shared units and currency across tables, and include explicit cross-table checks. Keep the existing numbered sections, which already provide a useful response schema.

## 6. Optimized & Production-Ready Prompt Rewrite

*Below is a fully refactored, production-ready version of the prompt incorporating all recommendations:*

```markdown
<role>
Act as an experienced college canteen manager and food-business analyst in India. Give a practical, conservative one-week operating plan.
</role>

<inputs>
- Location: [city/state; if unknown, label prices as illustrative India-wide estimates]
- Starting cash available: ₹10,000 maximum external out-of-pocket funding
- Operating days: Monday-Saturday (6 days)
- Typical daily customer count: about 300 students and staff
- Price-sensitive customers; expected item selling-price range: ₹10-₹90
- Rush periods: 10:30-11:00 AM, 1:00-2:00 PM, and 4:00-5:00 PM
- Revenue from each day may fund the following day's purchases. No additional external funding is allowed.
</inputs>

<priorities>
1. Never exceed the ₹10,000 external funding limit or let cash-on-hand go below zero.
2. Preserve student satisfaction.
3. Earn a profit.
4. Minimize unsold food and waste.
</priorities>

<instructions>
- Do not ask questions. State necessary assumptions first, including demand by item, Saturday demand, starting inventory, and local price uncertainty.
- Use plausible local prices if location-specific data is available. Do not claim live/current verification unless you can verify it. Otherwise label all prices as estimates, identify the assumed basis, and recommend checking supplier quotes before purchase.
- Create 6-8 items covering breakfast, lunch, snacks, and drinks, including at least one healthy item and one high-protein vegetarian item. Keep the offer affordable and feasible for a small canteen.
- Distinguish units planned/prepared, units expected sold, and expected leftovers. State that customers may buy more than one item; make the assumed item demand total plausible relative to 300 daily customers.
- Define unit cost, selling price, and gross margin consistently. Calculate gross margin % as `(selling price - unit cost) / selling price × 100`; do not call markup a margin.
- Allocate exactly ₹10,000 across Day-1 ingredient purchases, packaging, one-time upgrades, and a 10% emergency reserve. Treat the reserve as cash held back, not an expense; show any later reserve draw explicitly.
- Track cash separately from profit. For each day calculate `closing cash = opening cash - cash outflows + sales revenue`; the next day's opening cash must equal the previous day's closing cash. Include all actual purchases and one-time upgrade payments in cash outflows, and show no negative balance or extra funding.
- For profit, show revenue less consumed ingredient and packaging costs, spoilage/waste cost, and one-time upgrade costs. Report leftover usable inventory separately at purchase cost; do not count it as both a full expense and remaining inventory. State the break-even definition and identify the first day cumulative revenue covers cumulative costs under that definition; if it never does, say so.
- Use the same item names, units, prices, and assumptions in every table. Show rupee values to the nearest rupee and percentages to one decimal place. Reconcile totals and flag any estimate that prevents exact reconciliation.
- Give food-safety guidance conservatively. Avoid unsupported claims about exact safe shelf life; recommend following applicable FSSAI requirements, supplier/storage instructions, and local rules, and discarding food when safety is uncertain.
</instructions>

<required_output>
1. **Assumptions and price basis:** concise bullets at the top, including location/date or estimate caveat.
2. **Executive summary:** exactly 3 lines.
3. **Budget allocation:** table with category, amount, and treatment (spent or held as reserve); total must be ₹10,000.
4. **Menu economics:** table with item, category, unit cost, selling price, gross margin %, and concise reason for likely student demand.
5. **Six-day demand and preparation plan:** rows by day and item; include units planned/prepared, expected units sold, and leftovers. Adjust Saturday demand explicitly.
6. **Daily cash flow:** day, opening cash, ingredient/packaging/upgrades outflow, sales revenue, reserve draw (if any), and closing cash. Show the daily cash equation and verify all balances.
7. **Demand and service plan:** specify how to run pre-orders using Google Forms or WhatsApp, combos, rush-hour tokens, and a discount only during the final 30 minutes before closing. Explain how recorded sales, sell-outs, and leftovers change next-day quantities.
8. **Two low-cost footfall ideas:** make each actionable and state its approximate cost.
9. **Waste, hygiene, and risks:** response to sell-outs and leftovers, safe storage/handling, and a conservative food-safety escalation rule.
10. **Results and checks:** total sales revenue, ingredient/packaging cost consumed, waste cost, upgrade cost, closing usable inventory at cost, profit, and break-even day. Include 3-4 KPIs, one a simple daily student-feedback method.

Before finalizing, verify:
- Budget allocation sums to ₹10,000.
- Each day's closing cash equals the stated cash equation and next day's opening cash.
- Quantities multiplied by unit costs/prices support the purchase, revenue, and profit totals; explain any rounding.
- No day uses more external funding than the initial ₹10,000.
</required_output>
```

---
*Report generated by `prompt-eval` skill.*