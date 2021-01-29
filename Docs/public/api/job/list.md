# Jobs Query
List,search and filter jobs. return laravel paginated collection

## URL:

`/public/api/job/list`

## Request Method
`GET`

## Request Query String Parameters

parameter | data type| description
----------|----------|--------
job_category_id| integer | identifier of categories
sub_categories| bit (0-1) | 0  eaquls false and 1 equals true. if set to 1 all sub categeories that defined by "job_category_id" return in result 
categories| array of int|  array of "job_category_id" that must **_(only)_** be in reuslt.	example: `?categories[]=1&categories[]=2&....`
order_filed| string | field that result order by it, by default is <q>**created**</q>. [acceptable values](#acceptable_order_fields_values)
orderType| string (descend-ascend) | default is **descend**. direction of sort
search| string | search in title of jobs or name of user owns job
city| int | **city_id** to filter returl by city
module| string | filter job by certain module
force_has_product| bit (0,1)| store that only has al least one product.



## acceptable <q>order_fields</q> values:
- title 
- visit
- favorite
- product_count
- created