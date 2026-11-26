# Olist E-Commerce Analysis

An 8-page Power BI report I built on the [Olist Brazilian e-commerce dataset](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce): about 99,000 orders from September 2016 to October 2018. I focused on January 2017 to August 2018, because those are the months with complete data.

All money in the report is in Brazilian reais (R$), not US dollars.

## Files

| File | What it is |
|---|---|
| [`Olist_Ecommerce_Analysis.pdf`](Olist_Ecommerce_Analysis.pdf) | All 8 pages. Start here if you don't have Power BI. |
| [`Olist_Ecommerce_Analysis.pbix`](Olist_Ecommerce_Analysis.pbix) | The interactive report. The data is included, so it opens in Power BI Desktop without any setup. |
| [`Olist_Ecommerce_Analysis_Guide.docx`](Olist_Ecommerce_Analysis_Guide.docx) | The full guide: what each page shows, what I see in it, and how I built the model. |

## What I found

Olist more than doubled in one year (GMV +137% year over year). But since the Black Friday peak in November 2017, growth has stayed flat at about R$0.85–1.0M a month, and my forecast says it will stay there through December 2018. I see three main problems holding it back:

- **Late deliveries.** 54% of late orders get a 1–2 star review, compared to 9% of on-time orders.
- **Almost nobody comes back.** Only 3.1% of customers ever buy a second time.
- **Revenue depends on a few sellers.** The top 10% of sellers bring in about two-thirds of GMV.

I also looked at delivery by product. Timing matters more than product: every category gets slower and faster at the same times. Health Beauty is the exception. Since March 2018, as it grew, it has been late more often than other categories (10.8% vs 8.5%), and a few sellers cause a big part of that.

## The pages

1. **Executive Overview** – We doubled, but growth has stalled.
2. **Sales and Growth** – The growth is real, but it's a plateau now.
3. **Delivery and Logistics** – RJ is the biggest delivery problem; MA is the worst by rate.
4. **Customer Satisfaction** – Late orders get 6x more bad reviews.
5. **Customers and Retention** – Almost nobody buys twice.
6. **Seller Concentration** – 10% of sellers make two-thirds of the money.
7. **Forecast and Recommendations** – Expect about R$0.9M a month; here's what to do.
8. **Delivery by Product** – Timing matters more than product, except for Health Beauty lately.

## My recommendations

| # | What to do | Owner | What to track | Expected impact |
|---|---|---|---|---|
| 1 | Fix late delivery in RJ, BA and MA | Operations | Late rate by state | Halving the gap could remove about 1,000 low reviews |
| 2 | Start a retention program in the first 90 days after a purchase | Marketing | Repeat customer rate | Going from 3.1% to 5% repeat means about 1,900 more repeat customers, roughly R$260k+ GMV |
| 3 | Monitor the health of the top 10% of sellers | Seller Ops | Top 10% seller GMV share | Protects R$9.17M of GMV, about two-thirds of the total |

## How I built it

- A star schema with 10 tables, 11 relationships and 40 measures.
- I built the forecast in Python (Holt damped-trend) instead of using Power BI's built-in one, so I could test it on past data first. Its error was about 15% (MAPE 15.1%).
- GMV is item price only, without freight. Late delivery rate is late orders divided by delivered orders.

More details on every page and on the model choices are in the [guide](Olist_Ecommerce_Analysis_Guide.docx).
