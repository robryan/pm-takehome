# About Dataset
## Brazilian E-Commerce Public Dataset by Olist
Welcome! This is a Brazilian ecommerce public dataset of orders made at Olist Store. The dataset has information of 100k orders from 2016 to 2018 made at multiple marketplaces in Brazil. Its features allows viewing an order from multiple dimensions: from order status, price, payment and freight performance to customer location, product attributes and finally reviews written by customers. We also released a geolocation dataset that relates Brazilian zip codes to `lat`/`lng` coordinates.

This is real commercial data, it has been anonymised, and references to the companies and partners in the review text have been replaced with the names of Game of Thrones great houses.

### Join it with the marketing funnel
We have also released [a Marketing Funnel Dataset](/data/marketing-funnel/). You may join both datasets and see an order from Marketing perspective! A quickstart on joining is [available here](https://www.kaggle.com/andresionek/joining-marketing-funnel-with-brazilian-e-commerce).

### Context
This dataset was generously provided by [Olist, the largest department store in Brazilian marketplaces](www.olist.com). Olist connects small businesses from all over Brazil to channels without hassle and with a single contract. Those merchants are able to sell their products through the Olist Store and ship them directly to the customers using Olist logistics partners.

After a customer purchases the product from Olist Store a seller gets notified to fulfill that order. Once the customer receives the product, or the estimated delivery date is due, the customer gets a satisfaction survey by email where he can give a note for the purchase experience and write down some comments.

#### ⚠️ Attention
1. An order might have multiple items.
2. Each item might be fulfilled by a distinct seller.
3. All text identifying stores and partners where replaced by the names of Game of Thrones great houses.

#### Example of a product listing on a marketplace
![orders listing example](/images/orders-listing-example.png)

### Data schema
The data is divided in multiple datasets for better understanding and organization. Please refer to the following data schema when working with it

collection | details 
-- | --
9 files | all `.csv`
52 columns | 13 `string`, 13 `integer`, 12 `uuid`, 14 other

![data schema for orders and reviews](/images/data-schema-orders.png)


#### Columns
For each file we offer column definitions and a row of example data

##### 🙋 <code>olist_customers_dataset.csv</code>

This dataset has information about the customer and its location. Use it to identify unique customers in the orders dataset and to find the orders delivery location.

<details>

In our system each order is assigned to a unique `customer_id`. This means that the same customer will get different ids for different orders. The purpose of having a `customer_unique_id` on the dataset is to allow you to identify customers that made repurchases at the store. Otherwise you would find that each order had a different customer associated with.

`customer_id` | `customer_unique_id` | `customer_zip_code_prefix` | `customer_city` | `customer_state`
-- | -- | -- | -- | --
key to the orders dataset. Each order has a unique `customer_id`. | unique identifier of a customer. | first five digits of customer zip code | customer city name | customer state
`06b8999e2fba1a1fbc88172c00ba8bc7` | `861eff4711a542e4b93843c6dd7febb0` | `14409` | `franca` | `SP`
`...` | `...` | `...` | `...` | `...`

</details>

##### 🌎 <code>olist_geolocation_dataset.csv</code>

This dataset has information about Brazilian zip codes and its lat/lng coordinates. Use it to plot maps and find distances between sellers and customers.

<details>

`geolocation_zip_code_prefix` | `geolocation_lat` | `geolocation_lng` | `geolocation_city` | `geolocation_state`
-- | -- | -- | -- | --
first 5 digits of zip code | latitude | longitude | city name | state
`01037` | `-23.54562128115268` | `-46.63929204800168` | `sao paulo` | `SP` 
`...` | `...` | `...` | `...` | `...`

</details>

##### 🛍️ <code>olist_order_items_dataset.csv</code>

This dataset includes data about the items purchased within each `order`.

<details>

###### Example
The `order_id` = `00143d0f86d6fbd9f9b38ab440ac16f5` has 3 items (same product). Each item has the freight calculated accordingly to its measures and weight. To get the total freight value for each order you just have to sum.

The total `order_item` value is: `21.33 * 3 = 63.99`

The total freight value is: `15.10 * 3 = 45.30`

The total order value (product + freight) is: `45.30 + 63.99 = 109.29`


`order_id` | `order_item_id` | `product_id` | `seller_id` | `shipping_limit_date` | `price` | `freight_value`
-- | -- | -- | -- | -- | -- | --
order unique identifier | sequential number identifying number of items included in the same order. | product unique identifier | seller unique identifier | Shows the seller shipping limit date for handling the order over to the logistic partner. | item price | item freight value item (if an order has more than one item the freight value is split between items)
`00010242fe8c5a6d1ba2dd792cb16214` | `1` | `4244733e06e7ecb4970a6e2683c13e61` | `48436dade18ac8b2bce089ec2a041202` | `2017-09-19 09:45:35` | `58.90` | `13.29`

</details>


##### 💵 `olist_order_payments_dataset.csv`

This dataset includes data about the orders' payment options.


<details>

`order_id` | `payment_sequential` | `payment_type` | `payment_installments` | `payment_value`
-- | -- | -- | -- | --
unique identifier of an order. | a customer may pay an order with more than one payment method. If he does so, a sequence will be created to accommodate all payments. | method of payment chosen by the customer. | number of installments chosen by the customer. | transaction value.
`b81ef226f3fe1789b1e8b2acac839d17` | `1` | `credit_card` | `8` | `99.33`
`...` | `...` | `...` | `...` | `...`

</details>

##### 🤌🏽 `olist_order_reviews_dataset.csv`

This dataset includes customer satisfaction surveys gathered after we deliver the order.

<details>

After a customer purchases the product from Olist Store a seller gets notified to fulfill that order. Once the customer receives the product, or the estimated delivery date is due, the customer gets a satisfaction survey by email where he can give a note for the purchase experience and write down some comments.

`review_id` | `order_id` | `review_score` | `review_comment_title` | `review_comment_message` | `review_creation_date` | `review_answer_timestamp`
-- | -- | -- | -- | -- | -- | --
unique review identifier | unique order identifier | Note ranging from 1 to 5 given by the customer on a satisfaction survey. | Comment title from the review left by the customer, in Portuguese. | Comment message from the review left by the customer, in Portuguese. | Shows the date in which the satisfaction survey was sent to the customer. | Shows satisfaction survey answer timestamp.
`3948b09f7c818e2d86c9a546758b2335` | `e51478e7e277a83743b6f9991dbfa3fb` | `5` | `Super recomendo` | `Vendedor confiável, produto ok e entrega antes do prazo.` | `2018-05-23 00:00:00` | `2018-05-24 03:00:01`
`...` | `...` | `...` | `...` | `...` | `...` | `...`

</details>

##### 📦 `olist_orders_dataset.csv`
This is the core dataset. From each `order` you might find all other information.

<details>

`order_id` | `customer_id` | `order_status` | `order_purchase_timestamp` | `order_approved_at` | `order_delivered_carrier_date` | `order_delivered_customer_date` | `order_estimated_delivery_date`
-- | -- | -- | -- | -- | -- | -- | -- |
unique identifier of the order. | key to the customer dataset. Each order has a unique `customer_id`. | Reference to the order status (`delivered`, `shipped`, etc). | Shows the purchase timestamp. | Shows the payment approval timestamp. | Shows the order posting timestamp. When it was handled to the logistic partner. | Shows the actual order delivery date to the customer. | Shows the estimated delivery date that was informed to customer at the purchase moment.
`e481f51cbdc54678b7cc49136f2d6af7` | `9ef432eb6251297304e76186b10a928d` | `delivered` | `2017-10-02 10:56:33` | `2017-10-02 11:07:15` | `2017-10-04 19:55:00` | `2017-10-10 21:25:13` | `2017-10-18 00:00:00`
`...` | `...` | `...` | `...` | `...` | `...` | `...` | `...`

</details>

##### 📢 `olist_products_dataset.csv`

This dataset includes detailed info about each product listing sold on Olist.

<details>

`product_id` | `product_category_name` | `product_name_lenght` | `product_description_lenght` | `product_photos_qty` | `product_weight_g` | `product_length_cm` | `product_height_cm` | `product_width_cm`
-- | -- | -- | -- | -- | -- | -- | -- | --
unique product identifier | root category of product, in Portuguese. | number of characters extracted from the product name. | number of characters extracted from the product description. | number of product published photos | product weight measured in grams. | product length measured in centimeters. | product height measured in centimeters. | product width measured in centimeters.
`foo` | `foo` | `foo` | `foo` | `foo` | `foo` | `foo` | `foo` | `foo`
`...` | `...` | `...` | `...` | `...` | `...` | `...` | `...` | `...`

</details>

##### 🏪 `olist_sellers_dataset.csv`

This dataset includes data about the sellers that fulfilled orders made at Olist. Use it to find the seller location and to identify which seller fulfilled each product.

<details>

`seller_id` | `seller_zip_code_prefix` | `seller_city` | `seller_state`
-- | -- | -- | --
seller unique identifier | first 5 digits of seller zip code | seller city name | seller state
`3442f8959a84dea7ee197c632cb2df15` | `13023` | `campinas` | `SP`
`...` | `...` | `...` | `...`

</details>

##### ✏️ `product_category_name_translation.csv`

Translates the `product_category_name` to English.

<details>

`product_category_name` | `product_category_name_english`
-- | --
category name in Portuguese | category name in English
`beleza_saude` | `health_beauty` 
`...` | `...` 

</details>


