# About Dataset
## Marketing Funnel by OList
Welcome! This is a marketing funnel dataset from sellers that filled-in requests of contact to sell their products on OList Store. The dataset has information of 8k Marketing Qualified Leads (MQLs) that requested contact between Jun. 1st 2017 and Jun 1st 2018. They were randomly sampled from the total of MQLs.

Its features allows viewing a sales process from multiple dimensions: lead category, catalog size, behaviour profile, etc.

This is real data, it has been anonymized and sampled from the original dataset.

### Joining with Brazilian E-Commerce Public Dataset by OList
This dataset can also be linked to [the Brazilian E-Commerce Public Dataset by OList](/data/orders/) using `seller_id`. There you will find information of 100k orders, price, payment, freight performance, customer location, product attributes and finally reviews written by customers. A quickstart on joining is [available here](https://www.kaggle.com/andresionek/joining-marketing-funnel-with-brazilian-e-commerce).

### Context
This dataset was generously provided by OList, the largest department store in Brazilian marketplaces. [OList](www.OList.com) connects small businesses from all over Brazil to channels without hassle and with a single contract. Those merchants are able to sell their products through the OList Store and ship them directly to the customers using OList logistics partners. See more on our website: 

**A seller joins OList through a marketing and sales funnel.**

#### Steps in marketing funnel

1. Sign-up at a landing page.
2. Get contacted by a Sales development Representative (SDR), confirm some information and schedule a consultancy.
3. Consultancy is made by a Sales Representative (SR). 4. The SR may close the deal (lead sing up) or lose the deal (led leaves without sign in)
5. Lead becomes a seller and starts building his catalog on OList.
6. His products are published on marketplaces and ready to sell!

#### ⚠️ Attention
A seller MQL might come from multiple sources (s/he might subscribe on two different landing pages, for instance).

#### Examples of Landing Pages
![landing page example number one](/images/marketing-landing-page-example-1.png)

![landing page example number two](/images/marketing-landing-page-example-2.png)

### Data Schema
The data is divided in multiple datasets for better understanding and organization. Please refer to the following data schema when working with it:

collection | details 
-- | --
2 files | all `.csv`
18 columns | 6 `string`, 6 `uuid`, 2 `DateTime`, 4 other

![schema diagram joining marketing and orders](/images/data-schema-marketing.png)

#### Columns

##### 🏁 `olist_closed_deals_dataset.csv`

After a qualified lead fills in a form at a landing page he is contacted by a Sales Development Representative. At this step some information is checked and more information about the lead is gathered.

<details>

`mql_id` | `seller_id` | `sdr_id` | `sr_id` | `won_date` | `business_segment` | `lead_type` | `lead_behaviour_profile` | `has_company` | `has_gtin`
-- | -- | -- | -- | -- | -- | -- | -- | -- | -- 
Marketing Qualified Lead id | Seller id | Sales Development Representative id | Sales Representative | Date the deal was closed. | Lead business segment. Informed on contact. | Lead type. Informed on contact. | Lead behaviour profile. SDR identify it on contact. | Does the lead have a company (formal documentation)? | Does the lead have Global Trade Item Number (barcode) for his products? 
`5420aad7fec3549a85876ba1c529bd84` | `2c43fb513632d29b3b58df74816f1b06` | `a8387c01a09e99ce014107505b92388c` | `4ef15afb4b2723d8f3d81e51ec7afefe` | `2018-02-26 19:58:54` | `pet` | `online_small` | `cat` | `true` | `false`
`...` | `...` | `...` | `...` | `...` | `...` | `...` | `...` | `...` | `...`

</details>

##### 📣 `olist_marketing_qualified_leads_dataset.csv`

After a lead fills in a form at a landing page, a filter is made to select the ones that are qualified to sell their products at Olist. They are the Marketing Qualified Leads (MQLs).

<details>

`mql_id` | `first_contact_date` | `landing_page_id` | `origin`
-- | -- | -- | --
Marketing Qualified Lead id | Date of the first contact solicitation. | Landing page id where the lead was acquired | Type of media where the lead was acquired
`dac32acd4db4c29c230538b72f8dd87d` | `2018-02-01` | `88740e65d5d6b056e0cda098e1ea6313` | `paid_search`
`...` | `...` | `...` | `...` 

</details>