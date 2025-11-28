# Xsolla-Brazil-Checkout-Optimization-Case
Identifying payment method inefficiencies and user-level drop-off patterns using PostgreSQL &amp; SQL Analytics

##  1. Introduction
This project replicates a real-world checkout conversion problem in Brazil (BR region).
The goal is to:
- simulate traffic, payment attempts, and user behavior
- analyze conversion performance
- detect root causes for drop-offs
- produce insights that a Product Analyst/BA would present
- demonstrate SQL, data modeling, and analytical thinking

 ##  2. Dataset Overview
 We created a synthetic but realistic dataset stored in PostgreSQL.
 ### Tables:
- `users` - user demographics, device, registration date
- `payment_methods` - available checkout payment methods in BR
- `payments` - simulated transactions (success/fail, method, device, date)

 ### Schema Diagram
 (აქ შემდეგ დავამატებთ შენი pgAdmin-ის Diagram screenshot-ს)

 ## 3. Tools & Technologies
 
 | Tool | Purpose | 
|-----|------------------|
| **PostgreSQL 18** | Database & SQL execution |
| **pgAdmin 4** | Table creation, import, queries |
| **Excel / CSV** | Dataset preparation |
| **Power BI (optional)** | Visualization layer |
| **PostgreSQL 18** | GitHub |

## 4. Database Structure (DDL)

```sql
user_id BIGINT PRIMARY KEY  
country VARCHAR(2)  
state VARCHAR(2)  
registration_dt DATE  
device_type VARCHAR(20)
```

### payment_methods

```sql
method_code VARCHAR(20) PRIMARY KEY  
method_name VARCHAR(50)  
method_type VARCHAR(20)  
is_local BOOLEAN
```

### payments

```sql
payment_id BIGSERIAL PRIMARY KEY  
user_id BIGINT  
method_code VARCHAR(20)  
status VARCHAR(20)  
event_dt DATE  
device_type VARCHAR(20)
```

## 5. Data Generation (Simulation)

აქ ჩავდებთ SQL-ს

## 6. Analysis

### 6.1. Payment Method Performance
Metrics:
- Total attempts
- Successful transactions
- Success rate %
- Ranking of worst-performing methods

### SQL Query:
აქ უკვე ჩავსვამთ შენს მიერ გაშვებულ PM performance query-ს

### Screenshot of Result:
აქ ჩასვამ სქრინს ან Excel export-ს

### 6.2. Device-Level Drop-Off 
Metrics:
- Success rate by device
- Volume comparison (Android vs iOS vs PC)

### SQL Query:
აქ ჩავაგდებთ device breakdown query-ს

## 6.3. Daily Traffic Behavior (BR Region)

Metrics:
- raffic trend
- Daily success/fail variance
- Spikes or anomalies

SQL + visualization in Power BI (optional)

## 7. Insights (Business Findings)

## 7. Insights (Core Finding)

### Primary Insight — Boleto is the main driver of checkout drop-offs
Analysis shows that **Boleto has the lowest success rate among all payment methods**, significantly underperforming compared to PIX and Credit Card.

This aligns with real-world characteristics of Boleto:
- delayed offline confirmation  
- frequent timeouts  
- bank API instability  
- users abandoning the payment after generating the slip  

**Business impact:**  
Optimizing Boleto or redirecting users toward PIX can create an immediate uplift in Brazil's checkout conversion.

##  8. Recommendations & Prioritization

Given that **Boleto is the primary driver of checkout failures**, the optimization plan prioritizes fixes that directly reduce Boleto-related drop-offs.

###  Priority #1 — Fix Boleto reliability (Highest Impact)
- Reduce timeout thresholds
- Improve bank-side API retry logic
- Add fallback routing: Boleto → PIX
- Provide clearer in-UI instructions for offline payment completion

**Expected impact:** Immediate and measurable uplift in Brazil’s checkout conversion.

---

###  Priority #2 — Promote PIX as the default payment option
- Display PIX at the top of the payment list
- Add micro-copy explaining it is instant & high-success
- Auto-suggest PIX when Boleto fails

---

###  Priority #3 — Improve performance during peak hours  
(Not a root-cause, but amplifies failures)
- Monitor queue processing
- Add auto-scaling for BR traffic spikes

---

###  Priority #4 — Device-level UX improvements (Optional)
- Optimize Android checkout flow
- Detect slow network and offer instant fallback

---

### Summary  
The roadmap is structured to fix the **core blocker first (Boleto)** while supporting improvements (PIX prioritization, load handling, device UX) that compound the overall conversion uplift.



## 9. Project Structure

xsolla-brazil-checkout-case/
│
├── data/                    # CSV files used for simulation (users, payments, traffic)
│
├── sql/                     # SQL scripts: DDL, inserts, main analytical queries
│
├── screenshots/             # pgAdmin query outputs, charts, Power BI visuals
│
├── analysis/                # Exported tables (CSV) with aggregated results
│
├── diagrams/                # ERD, schema visualization, flow diagrams (optional)
│
└── README.md                # Complete project documentation


