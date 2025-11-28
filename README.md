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

 # Schema Diagram
 (აქ შემდეგ დავამატებთ შენი pgAdmin-ის Diagram screenshot-ს)

 # 3. Tools & Technologies
 
 | Tool | Purpose | 
|-----|------------------|
| **PostgreSQL 18** | Database & SQL execution |
| **pgAdmin 4** | Table creation, import, queries |
| **Excel / CSV** | Dataset preparation |
| **Power BI (optional)** | Visualization layer |
| **PostgreSQL 18** | GitHub |

# 4. Database Structure (DDL)

```sql
user_id BIGINT PRIMARY KEY  
country VARCHAR(2)  
state VARCHAR(2)  
registration_dt DATE  
device_type VARCHAR(20)
```

# payment_methods

```sql
method_code VARCHAR(20) PRIMARY KEY  
method_name VARCHAR(50)  
method_type VARCHAR(20)  
is_local BOOLEAN
```

# payments

```sql
payment_id BIGSERIAL PRIMARY KEY  
user_id BIGINT  
method_code VARCHAR(20)  
status VARCHAR(20)  
event_dt DATE  
device_type VARCHAR(20)
```

# 5. Data Generation (Simulation)

აქ ჩავდებთ SQL-ს

# 6. Analysis

# 6.1. Payment Method Performance
Metrics:
- Total attempts
- Successful transactions
- Success rate %
- Ranking of worst-performing methods

# SQL Query:
აქ უკვე ჩავსვამთ შენს მიერ გაშვებულ PM performance query-ს

# Screenshot of Result:
აქ ჩასვამ სქრინს ან Excel export-ს

# 6.2. Device-Level Drop-Off 
Metrics:
- Success rate by device
- Volume comparison (Android vs iOS vs PC)

# SQL Query:
აქ ჩავაგდებთ device breakdown query-ს

# 6.3. Daily Traffic Behavior (BR Region)

Metrics:
- raffic trend
- Daily success/fail variance
- Spikes or anomalies

SQL + visualization in Power BI (optional)

# 7. Insights (Business Findings)

აქ ბოლოს დავწერთ შენი აღმოჩენებს.
მაგალითად:

# Insight #1 — Local payment methods underperform
Success rate for certain BR methods is significantly lower (7–15%).
May indicate:
- integration issues
- timeout behavior
- poor UX
- bank-side declines

# Insight #2 — Android users convert worse than iOS
Possible reasons:
- SDK difference
- network quality
- app version fragmentation

# Insight #3 — Peak failure times correlate with traffic spikes
(ეს ყველაფერი ჩვენ ერთად დავამატებთ, როცა დავასრულებთ ანალიზს)

# 8. Recommendations

- Prioritize fixing low-performing payment methods
- Implement fallback method routing
- Improve Android checkout UX
- Add error logging granularity

# 9. Project Structure

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


