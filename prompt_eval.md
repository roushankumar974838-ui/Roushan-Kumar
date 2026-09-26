# AI Prompt Evaluation Report

## 1. Overall Score

| Parameter | Maximum Marks | Awarded Marks | Percentage | Grade |
|---|---:|---:|---:|---|
| **Prompt Clarity** | 100 | 94 | 94% | Strong |
| **Output Quality** | 100 | 67 | 67% | Developing |
| **Efficiency** | 50 | 37 | 74% | Developing |
| **Total Score** | **250** | **198** | **79.2%** | **Developing** |

Grades use these percentage bands: Strong = 80-100%, Developing = 60-79%, Needs work = below 60%. The skill's separate production benchmark is 85+ for each 100-point parameter and 42+ for Efficiency.

## 2. Executive Summary

- **Verdict:** A substantial improvement on the first version: the prompt defines financial formulas, a local price-estimate basis, and explicit consistency checks. A conflict remains between full-price revenue arithmetic and the requested late-day discounts.
- **Estimated Tokens:** ~710 tokens, estimated from 526 whitespace-separated words at 1.35 tokens per word; actual tokenizer counts vary.
- **Strengths:**
  - Clearly defines unit cost, gross margin, sell-through, daily closing cash, profit, and break-even.
  - Grounds the plan in Gurugram and expressly says ingredient prices are estimates, not live data.
  - Requires six-day quantities, cash-flow tables, operational tactics, KPIs, and a final consistency checklist.
- **Key Vulnerabilities / Deficits:**
  - Revenue is defined as units sold times the listed selling price, but the prompt also requires late-day discounts without saying how discounted prices enter revenue.
  - The 85–90% sell-through range does not specify how to choose and apply sell-through assumptions by item/day or round units.
  - Shelf-life and food-safety rules are requested without requiring authoritative, locally applicable guidance.

## 3. Evaluated Prompt Content

```text
Act as an experienced college canteen manager and food-business analyst in India.

**CONTEXT:** I have ₹10,000 as starting capital to improve my college canteen in Gurugram (Delhi NCR) for ONE week. Assume 6 working days (Mon–Sat), ~300 daily customers (students + staff), price-sensitive, with item prices ranging from ₹10 (chai, samosa) to ₹90 (full meal). Rush hours: 10:30–11:00 AM, 1:00–2:00 PM and 4:00–5:00 PM. Each day's sales revenue can be reinvested into the next day's ingredients (revolving capital), but total cash out of pocket must never exceed ₹10,000.

**PRIORITY ORDER:** (1) Stay within the ₹10,000 limit, (2) student satisfaction, (3) profit, (4) minimum food waste.

Do not ask me any questions. Make reasonable assumptions, list them at the top, and then give the complete plan.

**CALCULATION RULES (use these exact definitions in every table):**

- Unit cost = ingredients + packaging per unit.
- Margin % = (Selling price − Unit cost) ÷ Selling price × 100.
- Assume 85–90% of prepared units sell. Revenue = Units sold × Selling price. Unsold units earn nothing, but their cost stays in spend.
- Closing cash = Opening cash − Spend + Revenue. Day-1 opening cash = ₹10,000; each day's opening cash = previous day's closing cash.
- Weekly profit = Total revenue − Total spend (ingredients + packaging + one-time upgrades). An unused emergency buffer is not an expense.
- Break-even day = the first day on which cumulative revenue ≥ cumulative spend.

**PRICE GROUNDING:** Before the menu, give a short table of key ingredient prices you are assuming for Gurugram (per kg / litre / unit). Label all prices as estimates, not live data. Round selling prices to the nearest ₹5.

**DELIVER:**

1. **Executive summary** – 3 lines.
2. **Budget allocation table** – ₹10,000 split across Day-1 ingredients, packaging, small upgrades (menu board, UPI QR, pre-order setup), and a 10% emergency buffer.
3. **Menu table** – 6–8 items (breakfast, lunch, snacks, drinks), including at least 1 healthy and 1 high-protein veg option. For each: unit cost, selling price, margin %, and why students will buy it.
4. **Day-wise quantity table (Mon–Sat)** – units prepared and expected units sold per item, adjusted for demand (e.g., lower on Saturday).
5. **Day-wise cash-flow table** – opening cash, spend, revenue, closing cash – proving cash never goes negative.
6. **Demand management** – pre-orders via Google Form/WhatsApp, combo meals, token system for rush hours, and a discount on remaining items only in the last 30 minutes before closing. Explain how each day's sales data will adjust the next day's quantities.
7. **Two creative low-cost ideas** to boost footfall and excitement (e.g., student-voted "Dish of the Day", loyalty stamp card).
8. **Waste, hygiene and risk plan** – what to do if an item sells out or stays unsold, plus shelf-life and food-safety rules.
9. **Final results** – total spend, total revenue, weekly profit, break-even day, and 3–4 KPIs (including a simple daily student feedback method).
10. **Consistency check** – a short checklist confirming: total out-of-pocket ≤ ₹10,000, cash never goes negative, and revenue, spend and profit figures match across all tables.

**RULES:** Use clean tables, be specific and practical, no generic advice.
```

## 4. Detailed Criterion Evaluations

### 4.1 Prompt Clarity (Awarded: 84 / 100)
- **Role & Persona Definition:** 18 / 20
- **Task Specificity & Negative Constraints:** 24 / 25
- **Instruction Structure & Delimiters:** 20 / 20
- **Tone, Style & Target Audience:** 14 / 15
- **Unambiguous Language:** 18 / 20

**Detailed Analysis:**
- *What worked well:* The prompt identifies a relevant role and a specific market, "Gurugram (Delhi NCR)," and supplies the capital, operating days, customer volume, price range, and rush hours. Its "CALCULATION RULES" define unit cost, margin, cash roll-forward, weekly profit, and break-even. Numbered deliverables, bold labels, priorities, and "Do not ask me any questions" make the instructions easy to follow.
- *Ambiguities & Gaps:* The 85–90% sell-through range leaves the model to choose values without specifying a consistent item/day method or rounding rule. "Improve my college canteen" and "small upgrades" remain broad, and the prompt does not say whether the emergency reserve is a separate cash bucket or simply unspent opening cash.

### 4.2 Output Quality & Schema Compliance (Awarded: 67 / 100)
- **Output Format & Schema Enforcement:** 28 / 30
- **Few-Shot Examples & In-Context Demos:** 0 / 25
- **Edge Cases & Fallbacks:** 22 / 25
- **Factuality & Hallucination Prevention:** 17 / 20

**Detailed Analysis:**
- *What worked well:* The output schema is unusually complete: the prompt names the needed tables, fields, quantities, KPIs, and a final consistency checklist. It explicitly addresses sell-outs, unsold food, reinvestment, and approximate local ingredient prices, while correctly caveating them as "estimates, not live data." Exact definitions for margin, cash, profit, and break-even substantially reduce arithmetic drift.
- *Format Risks & Missing Guardrails:* No worked example demonstrates a reconciled day or item row, so a model can still misapply the formulas. Most importantly, it defines revenue as "Units sold × Selling price" while also requiring a late-day discount; discounted units should use the actual transaction price. The prompt requests shelf-life and food-safety rules without requiring authoritative guidance, and does not provide a fallback if live local estimates are unavailable.

### 4.3 Efficiency & Token Economy (Awarded: 37 / 50)
- **Conciseness & Fluff Elimination:** 12 / 15
- **Token Economy & Context Footprint:** 12 / 15
- **Dynamic Parameterization:** 4 / 10
- **Signal-to-Noise Ratio:** 9 / 10

**Detailed Analysis:**
- *Efficiency Observations:* At about 526 words, it is still focused for a multi-part business plan. The formula block carries high value because it prevents ambiguity across the budget, cash-flow, and results tables.
- *Identified Token Waste / Redundancy:* The rules and consistency-check deliverable repeat the need to reconcile totals, though this repetition reinforces a critical requirement. Location, starting capital, demand, and dates are hard-coded rather than reusable variables. The deliverables also imply a long answer without a compactness or table-layout limit.

## 5. Prioritized Recommendations for Improvement

1. **Reconcile discounted sales:** Define revenue as units sold at the actual selling price, applying the late-day discount to discounted units, and use that realized revenue in the cash-flow and profit totals.
2. **Make sell-through deterministic:** Require one explicit sell-through assumption per item/day within 85–90%, specify how to convert fractional expected units to whole units, and have prepared minus sold equal leftovers.
3. **Bound factual and output uncertainty:** Ask the model to label unavailable supplier prices as illustrative estimates, avoid inventing exact food-safety shelf lives, and keep explanations concise while preserving all required tables.

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
- Do not ask questions. State necessary assumptions first, including demand by item, Saturday demand, starting inventory, the selected sell-through rate for each item/day, and local price uncertainty. Keep each sell-through rate within 85-90%, calculate expected units sold from units prepared, and state how fractional results are rounded.
- Use plausible local prices if location-specific data is available. Do not claim live/current verification unless you can verify it. Otherwise label all prices as estimates, identify the assumed basis, and recommend checking supplier quotes before purchase.
- Create 6-8 items covering breakfast, lunch, snacks, and drinks, including at least one healthy item and one high-protein vegetarian item. Keep the offer affordable and feasible for a small canteen.
- Distinguish units planned/prepared, units expected sold, and expected leftovers. Ensure units sold do not exceed units prepared and leftovers equal prepared minus sold. State that customers may buy more than one item; make the assumed item demand total plausible relative to 300 daily customers.
- Define unit cost, selling price, and gross margin consistently. Calculate gross margin % as `(selling price - unit cost) / selling price × 100`; do not call markup a margin.
- Allocate exactly ₹10,000 across Day-1 ingredient purchases, packaging, one-time upgrades, and a 10% emergency reserve. Treat the reserve as cash held back, not an expense; show any later reserve draw explicitly.
- Track cash and spend consistently. For each day calculate `closing cash = opening cash - spend + realized sales revenue`; the next day's opening cash must equal the previous day's closing cash. Spend includes ingredient and packaging purchases plus one-time upgrades; an unused reserve is neither spend nor an expense. Show no negative balance or additional external funding.
- Calculate weekly profit as `total realized revenue - total spend`, matching the cash-flow spend definition. Calculate break-even day as the first day cumulative realized revenue is at least cumulative spend; if it never occurs, say so.
- For discounted items, use the actual discounted transaction price to calculate realized revenue. Do not multiply discounted units by the undiscounted menu price.
- Use the same item names, units, prices, and assumptions in every table. Show rupee values to the nearest rupee and percentages to one decimal place. Reconcile totals and flag any estimate that prevents exact reconciliation.
- Give food-safety guidance conservatively. Avoid unsupported claims about exact safe shelf life; recommend following applicable FSSAI requirements, supplier/storage instructions, and local rules, and discarding food when safety is uncertain.
</instructions>

<required_output>
1. **Assumptions and price basis:** concise bullets at the top, including location/date or estimate caveat.
2. **Executive summary:** exactly 3 lines.
3. **Budget allocation:** table with category, amount, and treatment (spent or held as reserve); total must be ₹10,000, with the reserve amount equal to 10% of the starting cash.
4. **Menu economics:** table with item, category, unit cost, selling price, gross margin %, and concise reason for likely student demand.
5. **Six-day demand and preparation plan:** rows by day and item; include units prepared, sell-through assumption, expected units sold, and leftovers. Adjust Saturday demand explicitly.
6. **Daily cash flow:** day, opening cash, ingredient/packaging/upgrades spend, realized sales revenue, reserve draw (if any), and closing cash. Show the daily cash equation and verify all balances.
7. **Demand and service plan:** specify how to run pre-orders using Google Forms or WhatsApp, combos, rush-hour tokens, and a discount only during the final 30 minutes before closing. State how discounted sales are priced in realized revenue. Explain how recorded sales, sell-outs, and leftovers change next-day quantities.
8. **Two low-cost footfall ideas:** make each actionable and state its approximate cost.
9. **Waste, hygiene, and risks:** response to sell-outs and leftovers, safe storage/handling, and a conservative food-safety escalation rule.
10. **Results and checks:** total realized revenue, total spend split into ingredient/packaging purchases and upgrades, weekly profit, break-even day, and 3-4 KPIs, including a simple daily student-feedback method.

Before finalizing, verify:
- Budget allocation sums to ₹10,000.
- Each day's closing cash equals the stated cash equation and next day's opening cash.
- Quantities multiplied by unit costs/prices support spend and revenue; discounted units use their actual transaction price. Explain any rounding.
- No day uses more external funding than the initial ₹10,000.
</required_output>
```

---
*Report generated by `prompt-eval` skill.*