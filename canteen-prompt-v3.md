<role>
Act as an experienced college canteen manager and food-business analyst in India. Give me a practical, conservative one-week operating plan whose numbers fully reconcile.
</role>

<inputs>
- LOCATION: Gurugram (Delhi NCR) college canteen
- CAPITAL: ₹10,000 of my own money — the maximum external cash ever (no loans, no top-ups)
- DAYS: 6 working days (Mon–Sat)
- CUSTOMERS: ~300/day (students + staff), price-sensitive; each buys 1–2 items on average, so total units sold per day should stay between 300 and 600
- PRICE RANGE: ₹10 (chai, samosa) to ₹90 (full meal)
- RUSH HOURS: 10:30–11:00 AM, 1:00–2:00 PM, 4:00–5:00 PM
- EMERGENCY BUFFER: 10% of CAPITAL (₹1,000)
- OUT OF SCOPE: existing staff wages, rent, electricity (college covers them). Gas and consumables go inside unit cost.
</inputs>

<priorities>
1. Never exceed CAPITAL and never let cash go negative.
2. Student satisfaction.
3. Profit.
4. Minimum food waste.
When two goals conflict, follow this order and say in one line which one you chose.
</priorities>

<calculation_rules>
Use these exact definitions in every table:
- **Unit cost** = ingredients + packaging + gas/consumables per unit.
- **Margin %** = (Selling price − Unit cost) ÷ Selling price × 100. Never report markup as margin.
- **Purchasing:** perishable ingredients are bought fresh each morning for that day only.
- **Sell-through:** 90% Mon–Fri, 85% Sat. Units sold = prepared × sell-through, rounded **down**. Unsold = prepared − sold.
- **Discount:** some sold units go at a discount in the last 30 minutes before closing. Each item has one discount price (about 20–30% off, rounded to ₹5), shown in the menu table.
- **Revenue** = (full-price units × selling price) + (discounted units × discount price). Never count discounted units at full price.
- **Unsold cooked food** is waste: it earns nothing, its cost stays in spend, and it is never resold the next day.
- **Spend** (per day) = ingredients + packaging bought that day + any one-time upgrades bought that day.
- **Buffer rule:** each day's spend ≤ opening cash − buffer, so the ₹1,000 buffer is always held. Using the buffer counts as spend and must be shown in the "buffer draw" column with a reason.
- **Closing cash** = Opening cash − Spend + Revenue. Day-1 opening cash = CAPITAL; each day's opening cash = previous day's closing cash.
- **Weekly profit** = Total revenue − Total spend.
- **Break-even day** = first day on which cumulative revenue ≥ cumulative spend. If it never happens, say so.
- **Rounding:** rupees to nearest ₹1, percentages to 1 decimal, selling prices to nearest ₹5.
- **If cash is tight:** cut the quantity of the lowest-margin item first. Never break the buffer rule to make the numbers work.
</calculation_rules>

<example>
Format only — do not copy these numbers.

Quantity row:
| Day | Item | Prepared | Full-price sold | Discounted sold | Unsold |
|---|---|---:|---:|---:|---:|
| Mon | Samosa | 150 | 125 | 10 | 15 |

Samosa: unit cost ₹6, price ₹15, discount price ₹10, margin 60.0%. Sold = 150 × 90% = 135 (125 + 10).
Revenue = 125 × 15 + 10 × 10 = ₹1,975. Spend = 150 × 6 = ₹900.

Cash-flow row:
| Day | Opening | Spend | Revenue | Buffer draw | Closing | Cum. revenue | Cum. spend |
|---|---:|---:|---:|---:|---:|---:|---:|
| Mon | 10,000 | 7,400 | 9,850 | 0 | 12,450 | 9,850 | 7,400 |

Check: 10,000 − 7,400 + 9,850 = 12,450 ✅ · Spend 7,400 ≤ 10,000 − 1,000 ✅
</example>

<price_grounding>
Before the menu, give a short table of the key ingredient prices you assume for LOCATION (per kg / litre / unit). Label them as estimates, not live data, and tell me to confirm with local suppliers before buying.
</price_grounding>

<deliverables>
1. **Assumptions** – short bullets for everything not specified above (demand split, discount volume, etc.).
2. **Executive summary** – exactly 3 lines.
3. **Budget allocation** – table: category, amount, spent or held back. Categories: Day-1 ingredients, packaging, one-time upgrades (menu board, UPI QR, pre-order setup), emergency buffer. Total = ₹10,000.
4. **Menu** – 6–8 items across breakfast, lunch, snacks and drinks, with at least 1 healthy and 1 high-protein veg item. Columns: item, category, unit cost, selling price, discount price, margin %, why students will buy it (one line).
5. **Day-wise quantity table (Mon–Sat)** – same format as the example; one row per day per item, with lower Saturday demand.
6. **Day-wise cash-flow table** – same format as the example, all 6 days, plus a totals row.
7. **Demand management** – pre-orders via Google Form/WhatsApp, combo meals (combo price, cost, margin), rush-hour token system, and the last-30-minute discount. Give a next-day adjustment rule (e.g., sold out before 2 PM → +10%; more than 15% unsold → −10%).
8. **Two creative low-cost ideas** to boost footfall (e.g., student-voted "Dish of the Day", loyalty stamp card), each with cost and which budget line pays for it.
9. **Waste, hygiene and risk plan** – early sell-out and unsold-food actions, safe storage and handling, top 3 risks with a response each. Follow FSSAI guidelines; do not invent exact shelf-life hours; when in doubt, discard.
10. **Final results** – total spend (ingredients+packaging vs upgrades), total revenue, weekly profit, break-even day, total waste in units and ₹, and 3–4 KPIs including a simple daily student-feedback method.
11. **Consistency check** – ✅/❌ for each:
    - Budget allocation sums to ₹10,000.
    - Cash never negative; buffer rule held every day; no money beyond CAPITAL added.
    - Each day's closing cash = next day's opening cash.
    - Quantity × unit cost matches spend; quantity × price (full + discounted) matches revenue.
    - Daily units sold are between 300 and 600.
    - Final results totals match the cash-flow totals row.
</deliverables>

<rules>
- Do not ask me questions. Make reasonable assumptions and list them in section 1.
- Before answering, silently recalculate every table. If any check fails, fix the numbers — never submit a ❌.
- Use clean markdown tables, keep text between tables brief, be specific and practical, no generic advice.
</rules>
