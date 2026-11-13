# Kloud Kart Data Strategy Engagement
## Architecture Case Study 
---


# Document : Recommendation and Roadmap

## The Recommendation

Build a reporting environment that is separated from the live website, governed, and trusted. Do not build a data lake, a lakehouse, or real-time streaming infrastructure in year one.

This is not a conservative recommendation. It is the correct sequence. A company that cannot reconcile its own Monday numbers is not ready to operate a lakehouse. A company whose customer data lives in an unknown number of spreadsheets is not ready to defend an ML model's training data to regulators.

---

### What to Build, in Order

**Step 1: Separate reporting from production (Q1)**

Deploy a MySQL read replica on the pre-approved second server. All reporting queries, CSV exports, and data jobs run against the replica. The live site becomes the only workload on the primary server. This eliminates the site-slowdown problem immediately and at the lowest possible cost.

**Step 2: Establish a warehouse for governed reporting (Q1–Q2)**

Load data from the replica into a managed cloud warehouse. BigQuery on Google Cloud is the recommended choice for Kloud Kart's data size and team profile: it requires no infrastructure management, scales with the data, and costs approximately $200–$400 per year at 40 GB with the usage pattern described. Snowflake is a reasonable alternative but carries a higher minimum commitment. The developer's instinct to buy rather than build is correct. Finance's concern about cost is addressed by BigQuery's on-demand pricing at this scale.

**Step 3: Define one revenue number (Q1–Q2)**

Finance and Operations agree on a single revenue definition before any report is built in the warehouse. The Analytics Engineer hired in Q2 owns this process. Until this definition exists, no dashboard is authoritative.

**Step 4: Govern customer data exports (Q1, ongoing)**

A controlled register is put in place before any new export is taken. All existing exports are inventoried and either brought into the register or destroyed. This is a process change, not a technical project. The Data Engineer can implement it in their first 30 days.

**Step 5: Inventory refresh for stock (Q1, ongoing)**

Inventory counts update from production to the warehouse every 15 minutes via the replica. All other data refreshes daily. This covers the overselling risk without streaming infrastructure.

---

### What Not to Build in Year One, and Why

**Real-time dashboards:** No business decision described in the brief requires data less than 24 hours old, except inventory. The board member who saw a real-time dashboard at another portfolio company saw a tool that company built after solving the problems Kloud Kart has not solved yet. Building real-time infrastructure now adds engineering cost and operational complexity without improving any decision Nana currently makes. This can be revisited in year two if a specific decision is identified that requires it.

**A lakehouse:** Kloud Kart's data is structured, relational, and 40 GB. A lakehouse architecture is designed for teams with large volumes of unstructured or semi-structured data and the engineering staff to govern it. Kloud Kart has neither. A warehouse handles everything Kloud Kart needs today and for the next two to three years at this growth rate.

**ML demand forecasting:** ML models require clean, historical, trusted data to train on. That data does not exist in a governed form yet. Building a forecasting model on ungoverned exports would produce predictions that cannot be defended to the board or to regulators. This is a year-two or year-three item.

---

### What It Costs (Approximate)

| Item | Estimated Annual Cost |
|---|---|
| BigQuery (40 GB, daily batch, inventory refresh) | $200–$400/year |
| Second server | Pre-approved, assumed covered |
| Data Engineer (Hire 1) | Market rate, Ghana mid-senior |
| Analytics Engineer (Hire 2) | Market rate, Ghana mid-senior |
| Export governance process | No additional tooling cost in year one |

The warehouse cost is low enough that Finance's concern is about the principle, not the number. The two hires are the material budget item.

---

## The Two Hires

### Hire 1: Data Engineer (Start Month 1)

**What this person does:** Moves data reliably from production to the reporting environment and keeps it moving. Implements the customer data register. Owns the pipeline.

**First 90 days:**
- Days 1–30: Set up replica-to-warehouse pipeline. Implement customer data export register. Inventory all existing exports.
- Days 31–60: Validate data quality. Confirm inventory refresh cadence. Document pipeline behavior.
- Days 61–90: Hand off documented pipelines. Support Analytics Engineer onboarding.

**Why first:** No reporting, no metrics definition, and no governance work is possible if the data is not moving reliably. This person unblocks everything else.

---

### Hire 2: Analytics Engineer (Start Month 3–4)

**What this person does:** Turns the data in the warehouse into trusted, governed metrics. Owns the revenue definition process. Builds the reports Nana and Finance both use.

**First 90 days:**
- Days 1–30: Facilitate the Finance-Operations revenue definition conversation. Document agreed definitions.
- Days 31–60: Build core reporting models in the warehouse (orders, revenue, inventory).
- Days 61–90: Replace Nana's CSV-based Monday report with a warehouse-sourced report. Confirm numbers match Finance.

**Why second:** This role needs clean, reliable data to work with. Starting before the Data Engineer has stabilized the pipeline produces rework.

---

## The 12-Month Roadmap

### Q1 (Months 1–3): Stop the bleeding

**Outcome Nana can verify:** The website does not slow down during Monday exports. Reports run from a separate system.

- Read replica deployed on second server
- All reporting queries moved off production
- Customer data export register created; existing exports inventoried
- Data Engineer in seat and pipeline from replica to warehouse operational
- Inventory refreshing every 15 minutes

---

### Q2 (Months 4–6): One version of the truth

**Outcome Nana can verify:** Nana's Monday number and Finance's number match. There is one place to get a revenue figure.

- Analytics Engineer in seat
- Single revenue definition agreed and documented
- Core reports (orders, revenue, inventory) live in the warehouse
- Nana's Monday report generated from the warehouse, not from a CSV export

---

### Q3 (Months 7–9): Governed and auditable

**Outcome Nana can verify:** If the Data Protection Commission asked today where every copy of customer data lives, Kloud Kart can answer within the 90-day window.

- All historical customer exports inventoried and either registered or destroyed
- Deletion-request response process documented and tested
- Nigeria pilot data flowing into the warehouse under the same governance rules
- First board data report produced from warehouse numbers, not spreadsheets

---

### Q4 (Months 10–12): Ready for year two

**Outcome Nana can verify:** The board has twelve months of consistent, reconciled numbers. The team can explain what real-time would cost and what problem it would solve.

- 12 months of consistent reporting data in the warehouse
- Documented data dictionary (what each metric means, who owns it)
- Assessment of whether any specific decision requires lower-latency data
- Demand forecasting feasibility note: what data exists, what quality it is, whether ML is worth pursuing in year two
