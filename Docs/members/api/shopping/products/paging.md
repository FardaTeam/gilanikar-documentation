# Shopping predefiend Products
-------------------------------

## URL:

``
/members/api/shopping/products/paging
``

## Request Specification

<table>
<tr>
	<td>Method</td>
	<td>POST</td>
</tr>
<tr>
	<td>Content-Type</td>
	<td>application/json</td>
</tr>
</table>

## URL Parameters (Query string)

Parameter | Type | Description
---|---|---
search | string | name of product that must be search in database products, return any product that contain search key in its title or brand
product_category_id | int | id of **product category** , filter result base on _product_category_
sub_categories | boolean (0,1) | if this set **1** (true) and **product_category_id** set, result come from both this and its sub categories
job_id | int | is use with either ``job_products`` or ``not_in_job`` parameters to filter result
job_products | boolean (0,1) | if set to **1** filter result to return only defined job by ``job_id`` products
not_in_job | boolean (0,1) | if set to **1** filter result to return only products than <u>_**not in defined**_</u> job by ``job_id`` .
user_products | boolean (0,1) | if set to **1** filter result to return user defined product (<q>user's own products</q>)
available | 0 or 1 | filter result to return only **available** product
with_categories | boolean (0,1) | if set this to **1**, a list of all categories that is include in current query, return by ``categories`` key.
with_category_ids |  boolean (0,1) | if set this to **1**, a list of all ``categories` id`` that is include in current query, return by ``categories`` key.
with_brands |   boolean (0,1) | if set this to **1**, a list of all brands name that is include in current query, return by ``brands`` key.


## Response Body

**Response Content-Type:** application/json

**Response Type:** Laravel Eloquent Pagination Result

Key | Description
--|--
data | a list of [product item](#product-item-object-keys)
first_page_url| first page url for pagination
from | page first item index
to | page last item index
last_page | the number of last page (pages count)
last_page_url | last page url for pagination
next_page_url | next page url for pagination
path | base url of query (current url)
per_page | list count of each page
prev_page_url | previus page url for pagination
total  | total count of query result

## product item object keys

- product_id 
- product_category_id
- title
- brand
- description
- price
- measure
- unit
- job_product_price
- job_product_sell_price
- job_product_off
- job_product_available
- job_product_description
- job_product_stock
- owned
- job_images
- image
- unit_string
- status_string
- category
	- category_id
	- title
	- created
	- updated
	- image