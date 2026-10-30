# SUBSCRIPTION CREEP RADAR : A Power BI project report on recurring spend, subscription health, payments and usage

Subscription Creep Radar is a Power BI analytics solution designed to make recurring subscription costs and related activity easier to understand. Multiple individually low-cost subscriptions can accumulate into a material monthly expense. At the same time, subscription status, automatic renewal, payment outcomes and usage records are often spread across different datasets. The project brings these perspectives together in one analytical model. 

The solution uses four related CSV datasets—Customers, Subscriptions, Payments and Usage—prepared in Power Query and connected through a one-to-many relational model. DAX measures calculate key indicators such as active monthly-equivalent spend, active subscriptions, customer count, payment totals and average payment amount. A three-page report explores subscription overview, subscription health, and usage/payment insights. Selected visuals are also pinned to a Power BI Service dashboard for at-a-glance monitoring. 

The project was selected because it is a practical, recognisable business problem that demonstrates a balanced range of Power BI skills without requiring an overly complex enterprise architecture. It moves beyond a basic expense chart by combining financial, operational and behavioural indicators. 

Important:
- This is a synthetic, fictional dataset created for a classroom Power BI project.
- It does not contain real customers or actual company billing records.
- Currency is INR (Indian Rupees).
- Snapshot date used for renewal-date generation: 26 October 2026.

Files:
1. Customers.csv
   One row per customer. CustomerID is the unique key.
2. Subscriptions.csv
   One row per subscription. SubscriptionID is the unique key; CustomerID links to Customers.
   CurrentMonthlyEquivalentINR is the current monthly-equivalent cost for fair comparison of monthly and annual plans.
   EstimatedPriceIncreasePct is the modeled cumulative increase from the original monthly price.
3. Payments.csv
   One row per generated billing event. SubscriptionID links to Subscriptions; CustomerID links to Customers.
   Annual plans may have one charge in the 12-month window depending on the subscription's start month.
   NetAmountINR is amount after discount. PaymentStatus includes some failed payments for analysis.
4. Usage.csv
   One row per subscription per month when the subscription is considered present in the simulated period.
   UsageHours and ActiveDays support underused-subscription analysis.

Suggested report pages:
Page 1 — Subscription Spend Overview:
- Total monthly recurring cost (active subscriptions)
- Active subscriptions, total customers, average spend per customer
- Monthly spend by category and service
- Spend by customer segment/city

Page 2 — Creep & Waste Detection:
- Original vs current monthly-equivalent price
- Total estimated price increase
- Subscriptions with price increases
- Underused/no-activity subscriptions and estimated monthly cost at risk
- Auto-renewing subscriptions with upcoming renewal dates

Page 3 — Customer & Renewal Insights:
- Subscription count by customer / customer type
- Renewal calendar or upcoming renewals
- Failed payment rate and net payments by month
- Slicers: category, status, billing cycle, city, age group

Suggested relationships:
- Customers[CustomerID] 1:* Subscriptions[CustomerID]
- Subscriptions[SubscriptionID] 1:* Payments[SubscriptionID]
- Subscriptions[SubscriptionID] 1:* Usage[SubscriptionID]
- Optional: Customers[CustomerID] 1:* Payments[CustomerID]
