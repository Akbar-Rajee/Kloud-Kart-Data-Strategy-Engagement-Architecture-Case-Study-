# Kloud Kart Data Strategy Engagement
## Architecture Case Study 
---
# Document : Situation Diagnosis

## What Is Actually Wrong

The board conversation is at risk for three reasons, ranked by how quickly each one can cause damage.

---

### Risk 1 — The website and reporting share one machine (Highest Risk)

**Root cause:** Orders, inventory, customer accounts, and reporting queries all compete for the same CPU and memory on one server.

**Evidence:** A Monday CSV export slowed the live site twice last month. At 4,000 orders per day, a checkout failure during a reporting job is not a hypothetical.

**Cost if unresolved:** A single hour of checkout downtime at 4,000 orders per day, assuming an average order value of GHS 150, is roughly GHS 25,000 in lost transactions. The reputational damage with investors who just closed a round is harder to price.

**Board exposure:** If an investor asks "what happens to your site when you run a report?" Nana cannot answer confidently today.

---

### Risk 2 — Finance and Operations report different numbers (High Risk)

**Root cause:** There is no single, agreed definition of revenue or orders. Each team builds its own numbers from independent CSV exports taken at different times.

**Evidence:** Finance's spreadsheet never matches Nana's Monday report. Both teams believe they are correct.

**Cost if unresolved:** The board is making decisions from numbers that cannot be reconciled. If a board member asks Nana and the CFO the same revenue question in the same meeting, the answers will differ.

**Board exposure:** Irreconcilable numbers in a board meeting destroy credibility faster than any other single failure.

---

### Risk 3 — Customer data is ungoverned (High Risk, Compliance)

**Root cause:** Marketing exports customer lists with no record of how many copies exist, where they are stored, or who owns them.

**Evidence:** Approximately 300,000 customer records have been exported into an unknown number of spreadsheets and files across the organization.

**Cost if unresolved:** Ghana's Data Protection Act (Act 843) requires Kloud Kart to respond to a customer deletion request within 90 days. Without a register of where customer data lives, Kloud Kart cannot demonstrate compliance. A complaint to the Data Protection Commission would require locating data across files the company cannot currently inventory.

**Regulatory exposure:** A DPC complaint during the board's first post-funding year is a governance failure at the worst possible time.

---

### Risk 4 — The wish list commits to things that cannot yet be delivered (Medium Risk)

**Root cause:** "Real-time analytics" and "ML for demand forecasting" were promised to investors before Kloud Kart has a stable reporting foundation or the staff to operate one.

**Evidence:** One developer (PHP/MySQL). No Python expertise on the team. No existing pipeline or warehouse.

**Cost if unresolved:** Building real-time infrastructure before the basics are stable adds complexity and cost without fixing the problems above. If the board asks for a real-time dashboard in Q1 and the team is still reconciling Monday numbers, the promise accelerates the credibility problem rather than solving it.

---
