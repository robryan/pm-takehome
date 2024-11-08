Trying to hire a good product manager? Assess your candidate with this data-driven case.

![intro-background-rio-de-janiero](/images/intro-bg-rio.jpg)
## Trouble in Paradise

You are a product manager at [Olist (OL)](https://olist.com/), the leading e-commerce platform in Brazil. Olist allows anyone to set up an online store and mobile app to sell their products. Olist also handles shipping from sellers to consumers. It's a healthy profitable business but no longer growing as quickly as it was a few years earlier.

OL's core product is an online store-building tool that allows retailers to pick a custom domain, upload inventory, and manage shipping. New user growth has gradually slowed over the last year but end-user satisfaction is still high. More concerning is that over the last few months, customer churn is up 10% from last year, and there's no obvious change in the product or major bug to point to. 

The top three options the team has come up with are … 
1. Slowly phase out the on line store-building tool and start listing all vendor's products in one integrated online store run by OL, like Amazon.com
2. Offer discounted or free shipping to retailers to speed up their delivery times.
3. Improve the OL reporting dashboard for customers that currently shows sales metrics like avg ticket size, order volume over time, most popular products, top referrer sites, etc.



### Part 1

A data analyst on your team pulled together the last few years of order, reviews, and funnel data. (You’ll find [two datasets posted under `/data/`](/data/) and their [documentation under `/docs`)](/docs). <br>

Use the data to diagnose the issue: why are retailers churning? Use your best judgment to propose a solution, choosing from the team’s three options or inventing your own. Lay out the presentation that you’d give the OL team to explain the problem and your solution. Include a plan for the next six (6) weeks of product development and a conservative delivery date for the MVP.

![data schema for orders](/images/data-schema-orders.png)
![data schema for orders](/images/data-schema-marketing.png)

### Part 2

Your engineering team just notified you that the db cluster lost data due to a misapplied migration. You’ve lost all address data for orders placed in the last 96 hours. A growing chorus of customers are logging into OL to print shipping labels … but are seeing an error instead. The OL engineering team says they can reconstruct the lost order data but they need three to five days to work through the problem with a 3rd party logistics vendor. How would you communicate this to users and what would you say, knowing sellers and buyers will both be disappointed? 

<hr> 

## Submission and scoring

When you’re ready, submit your work to your recruiter by email. There are many possible correct answers. We :x: don’t penalize you for using AI tools, search engines, or code libraries. Don’t commit any crimes, but give us the best submission you can using any tools you can. 

Your answer to Part 1 may be in the form of a brief, slides, a video, a website, or whatever creative format makes sense to you. 📎 **Include a `.zip` file of any code** you wrote to answer Part 1.

Your answer to Part 2 can be plaintext, markdown, or HTML. Imagine the email you're sending to the recruiter is *literally* what OList customers will get, pixel for pixel.

### Rubric
We score your responses from 1-10 on multiple dimensions …

#### Values

measure | description | score
-- | -- | -- 
Curiosity | The candidate doesn’t accept easy answers. They find  surprising insights by asking *“why, why, why …”* a lot.  They ask more questions than other candidates during  the entire process. | [1-10]
Flexibility | If you disagree with them, they get more pliant, not less  cooperative. They entertain multiple hypotheses at the  same time. | [1-10]
Simplicity | Given a 50/50 option to add or remove detail, the  candidate prefers to remove. | [1-10]

#### Skills
measure | description | score
-- | -- | -- 
Data | They can pull quant data from multiple sources. They don’t need an analyst to support them. | [1-10]
Writing | They’re solid at written communication. They adapt to their audience better than other candidates. | [1-10]
Costing | They can predict software complexity about as well as an engineer. | [1-10]

#### Market experience
measure | description | score
-- | -- | -- 
Marketplace | The candidate has worked at a two-sided marketplace company. | [1-10]
Artificial intelligence | They have built systems based on NLP, computer vision, fraud detection, LLMs, etc. | [1-10]
Distributed teams | They’ve worked with a remote workforce before and done  well. | [1-10]