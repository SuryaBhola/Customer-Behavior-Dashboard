# Customer Behavior Dashboard

A Power BI dashboard built on a customer shopping dataset of 3,900 purchases. I cleaned and prepared the data in Python (pandas, in a Jupyter notebook), then used it to look at who is buying, what they buy, and how much they spend.

![Customer Behavior Dashboard](images/dashboard.png)

---

## What I wanted to find out

- Which product categories bring in the most revenue?
- Which age groups spend the most?
- How many customers are subscribed, and do subscribers spend more?
- How satisfied are customers overall?
- How do shipping type and gender change the picture? (the dashboard has filters for both)

---

## Key numbers

| Metric | Value |
|---|---|
| Number of customers | 3,900 |
| Average purchase amount | $59.76 |
| Average review rating | 3.75 / 5 |
| Subscribed customers | 27% |
| Total revenue | about $233K |

---

## What I found

- **Clothing leads by a distance.** It has the most purchases (1,737) and the most revenue (about $104K, close to 45% of the total). Accessories come second, then Footwear and Outerwear.
- **Young adults spend the most.** The youngest age group (18 to 31) brings in about $62K, ahead of middle-aged customers (about $59K). Adults and seniors are close behind at roughly $56K each, so the gap between age groups is small.
- **Most customers are not subscribed.** Only 27% have a subscription, and subscribers spend almost exactly the same per purchase as non-subscribers (about $59 each). That suggests the subscription isn't yet driving higher spend, which is worth a closer look.
- **Ratings are good but not great.** The average review rating is 3.75, which leaves some room to improve.
- **Shipping is evenly spread.** All six shipping options are used by a similar number of customers, so no single option dominates.

---

## How I built it

### 1. Data cleaning and preparation (Python)

All the steps are in `notebook/customer_behavior.ipynb`:

1. Loaded the dataset and checked its structure with `info()` and `describe()`
2. Found **37 missing values** in `Review Rating` and filled them with the **median rating of each product category**
3. Renamed the columns to snake_case (for example `Purchase Amount (USD)` became `purchase_amount`)
4. Created an **`age_group`** column by splitting customers into four equal-sized groups by age:

   | Group | Age range |
   |---|---|
   | Young Adult | 18 to 31 |
   | Adult | 32 to 44 |
   | Middle-aged | 45 to 57 |
   | Senior | 58 to 70 |

5. Created a **`purchase_frequency_days`** column by converting text like "Weekly" or "Quarterly" into a number of days
6. Checked that `discount_applied` and `promo_code_used` always matched, then dropped `promo_code_used` since it was a duplicate
7. Saved the result as a cleaned CSV

### 2. Dashboard (Power BI)

- KPI cards for customers, average purchase amount and average rating
- Donut chart for subscription status
- Bar charts for revenue and number of sales by category and by age group
- Slicers for subscription status, gender, category and shipping type, so every chart can be filtered

---

## Repository structure

```
customer-behavior-dashboard/
├── data/
│   ├── customer_shopping_behavior.csv           # original dataset
│   └── cleaned_customer_shopping_behavior.csv   # cleaned version
├── notebook/
│   └── customer_behavior.ipynb                  # cleaning and feature engineering
├── dashboard/
│   └── customer_behavior_dashboard.pdf          # exported dashboard
├── images/
│   └── dashboard.png
└── README.md
```

---

## How to run it

1. Clone the repo
   ```bash
   git clone https://github.com/<your-username>/<your-repo-name>.git
   cd <your-repo-name>
   ```
2. Install the libraries
   ```bash
   pip install pandas jupyter
   ```
3. Open the notebook and run it from top to bottom
   ```bash
   jupyter notebook notebook/customer_behavior.ipynb
   ```
   The notebook reads `customer_shopping_behavior.csv`, so update the file path at the top if you keep the data in the `data/` folder.

---

## Tools used

- **Python** (pandas) and **Jupyter Notebook** for cleaning and feature engineering
- **Power BI Desktop** for the dashboard

---

## What I'd do next

- Compare subscribers and non-subscribers in more depth (frequency, discounts, ratings)
- Look at spending by location, season and payment method
- Check whether discounts and promo codes actually lift the purchase amount
- Add the previous purchases and purchase frequency columns to the dashboard

---

## About me

Created by **Surya Bhola** as part of my data analyst portfolio.

- LinkedIn: [linkedin.com/in/suryabhola-da](https://www.linkedin.com/in/suryabhola-da)
- Email: [isuryabhola@gmail.com](mailto:isuryabhola@gmail.com)

Feedback is always welcome.
