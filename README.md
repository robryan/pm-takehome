Trying to hire a good product manager? Assess your candidate with this case study of a Brazilian ecommerce product.

![intro-background-rio-de-janiero](/images/intro-bg-rio.jpg)
## Trouble in Paradise

You are a product manager at [Olist (OL)](https://olist.com/), the leading e-commerce platform in Brazil. Olist allows anyone to set up an online store and mobile app to sell their products. Olist also handles shipping from sellers to consumers. It's a healthy profitable business but no longer growing as quickly as it was a few years earlier.

OL's core product is an online store-building tool that allows retailers to pick a custom domain, upload inventory, and manage shipping. New user growth has gradually slowed over the last year but end-user satisfaction is still high. More concerning is that over the last few months, customer churn is up 10% from last year, and there's no obvious change in the product or major bug to point to. 

The top three options the team has come up with are … 
1. Slowly phase out the on line store-building tool and start listing all vendor's products in one integrated online store run by OL, like Amazon.com
2. Offer discounted or free shipping to retailers to speed up their delivery times.
3. Improve the OL reporting dashboard for customers that currently shows sales metrics like avg ticket size, order volume over time, most popular products, top referrer sites, etc.



### Part 1

A data analyst on your team pulled together the last few years of order, reviews, and funnel data. (You’ll find [two datasets posted under `/data/`](/data/) and their [documentation under `/docs`)](/docs). 

![data schema for orders](/images/data-schema-orders.png)
![data schema for orders](/images/data-schema-marketing.png)

Use the data to diagnose the issue: why are retailers churning? Use your best judgment to propose a solution, choosing from the team’s three options or inventing your own. Lay out the presentation that you’d give the OL team to explain the problem and your solution. Include a plan for the next six (6) weeks of product development and a conservative delivery date for the MVP.

## Part 2

Your engineering team just notified you that the db cluster lost data due to a misapplied migration. You’ve lost all address data for orders placed in the last 96 hours. A growing chorus of customers are logging into OL to print shipping labels … but are seeing an error instead. The OL engineering team says they can reconstruct the lost order data but they need three to five days to work through the problem with a 3rd party logistics vendor. How would you communicate this to users and what would you say, knowing sellers and buyers will both be disappointed? 