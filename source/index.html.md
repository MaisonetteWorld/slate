---
title: API Documentation
language_tabs:
  - json: JSON
  - shell: cURL
---


# Address

As a guest user

## Updating Address


### Request

#### Endpoint

```plaintext
PUT /api/orders/R303602338/addresses/475
Accept: application/json
X-Spree-Order-Token: K82u_V30nOlv5vGPRuRTCw
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PUT /api/orders/:order_id/addresses/:id`

#### Parameters


```json
address[firstname]=John+the+Tester
```


| Name | Description |
|:-----|:------------|
| order_id *required* | Order number |
| id *required* | Ship or Bill Address id |
| address[firstname]  | Address firstname |
| address[lastname]  | Address lastname |
| address[first_tname]  | Address first tname |
| address[last_name]  | Address last name |
| address[address1]  | Address address1 |
| address[address2]  | Address address2 |
| address[city]  | Address city |
| address[country_id]  | Address country |
| address[state_id]  | Address state |
| address[zipcode]  | Address zipcode |
| address[phone]  | Address phone |
| address[state_name]  | Address state name |
| address[country_iso]  | Address country iso |
| address[alternative_phone]  | Address alternative phone |
| address[company]  | Address company |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
ETag: W/&quot;2cc0fb24a7a95072996a5475c49b405b&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 99aa1db5-a53e-4793-b564-def6a676b757
X-Runtime: 0.151797
Content-Length: 513
200 OK
```


```json
{
  "id": 476,
  "firstname": "John the Tester",
  "lastname": null,
  "full_name": "John the Tester",
  "address1": "A Different Road",
  "address2": "Northwest",
  "city": "Herndon",
  "zipcode": "10002",
  "phone": "555-555-0199",
  "company": "Company",
  "alternative_phone": "555-555-0199",
  "country_id": 303,
  "country_iso": "US",
  "state_id": 292,
  "state_name": null,
  "state_text": "AL",
  "country": {
    "id": 303,
    "iso_name": "UNITED STATES",
    "iso": "US",
    "iso3": "USA",
    "name": "United States",
    "numcode": 840
  },
  "state": {
    "id": 292,
    "name": "Alabama",
    "abbr": "AL",
    "country_id": 303
  }
}
```



# LineItem

Representation of a single cart item for a specific variant with price of vendor

## Creating a line item


### Request

#### Endpoint

```plaintext
POST /api/orders/R952060824/line_items
Accept: application/json
X-Spree-Order-Token: K8fNdsBnMac8n0dzDN7XLw
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/:order_number/line_items`

#### Parameters


```json
line_item[variant_id]=620&line_item[options][vendor_id]=2075
```


| Name | Description |
|:-----|:------------|
| line_item[variant_id] *required* | Line item variant |
| line_item[options]  | Hash containing the vendor_id. It's used to set the price based on vendor |
| line_item[quantity]  | default value when not provided is 1 |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
ETag: W/&quot;8d6cf356f2d7c8c4a0781233961f7009&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: ede722fc-e527-4974-8fe8-04ca73f8ef1e
X-Runtime: 0.075575
Content-Length: 732
201 Created
```


```json
{
  "id": 222,
  "quantity": 1,
  "price": "19.99",
  "variant_id": 620,
  "vendor_id": 2075,
  "single_display_amount": "$19.99",
  "display_amount": "$19.99",
  "total": "19.99",
  "variant": {
    "id": 620,
    "name": "Product #7 - 8457",
    "sku": "SKU-8",
    "price": "19.99",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": false,
    "slug": "product-7-8457",
    "description": "As seen on TV!",
    "track_inventory": true,
    "display_price": "$19.99",
    "options_text": "Size: S",
    "in_stock": false,
    "is_backorderable": false,
    "total_on_hand": 0,
    "is_destroyed": false,
    "option_values": [
      {
        "id": 188,
        "name": "Size-2",
        "presentation": "S",
        "option_type_name": "foo-size-2",
        "option_type_id": 188,
        "option_type_presentation": "Size"
      }
    ],
    "images": [

    ],
    "product_id": 443
  },
  "vendor_name": "Vendor #18",
  "adjustments": [

  ]
}
```



## Deleting a line item


### Request

#### Endpoint

```plaintext
DELETE /api/orders/R430891965/line_items/220
Accept: application/json
X-Spree-Order-Token: ndSGn-goVTocgH369hIz3w
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`DELETE /api/orders/:order_number/line_items/:line_item_id`

#### Parameters


None known.


### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Cache-Control: no-cache
X-Request-Id: ecf62f72-bda0-4811-931e-8152ae2a272c
X-Runtime: 0.109609
204 No Content
```




## Updating a line item


### Request

#### Endpoint

```plaintext
PUT /api/orders/R124882116/line_items/223
Accept: application/json
X-Spree-Order-Token: F2LAsbnAxyglUZiWholZEw
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PUT /api/orders/:order_number/line_items/:line_item_id`

#### Parameters


```json
line_item[quantity]=2
```


| Name | Description |
|:-----|:------------|
| line_item[options]  | Hash containing the vendor_id |
| line_item[quantity] *required* | Line item quantity |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
ETag: W/&quot;b966b257fcf50ce09044186272b6d30c&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 04cb04ba-ddb7-4bba-a75d-ecab65ce263f
X-Runtime: 0.068016
Content-Length: 591
200 OK
```


```json
{
  "id": 223,
  "quantity": 2,
  "price": "10.0",
  "variant_id": 621,
  "vendor_id": 2081,
  "single_display_amount": "$10.00",
  "display_amount": "$20.00",
  "total": "20.0",
  "variant": {
    "id": 621,
    "name": "Product #8 - 5926",
    "sku": "SKU-10",
    "price": "19.99",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": true,
    "slug": "product-8-5926",
    "description": "As seen on TV!",
    "track_inventory": true,
    "display_price": "$19.99",
    "options_text": "",
    "in_stock": false,
    "is_backorderable": false,
    "total_on_hand": 0,
    "is_destroyed": false,
    "option_values": [

    ],
    "images": [

    ],
    "product_id": 444
  },
  "vendor_name": "Vendor #23",
  "adjustments": [

  ]
}
```



# Orders



## Get my orders


### Request

#### Endpoint

```plaintext
GET /api/orders/mine
X-Spree-Token: 11935dc7fa75233032c0a8c911f92e3c319678fef9f05593
Host: example.org
Cookie: 
```

`GET /api/orders/mine`

#### Parameters



| Name | Description |
|:-----|:------------|
| per_page  | Specify the amount of records returned, default is 25 |
| page  | Specify the page |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
ETag: W/&quot;bfd93c467923e2902c20109270f7395a&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: a8f05b2e-db47-4cda-ab46-142640ca04b8
X-Runtime: 0.171555
Content-Length: 80
200 OK
```


```json
{
  "orders": [

  ],
  "count": 0,
  "total_count": 0,
  "current_page": 1,
  "pages": 0,
  "per_page": 25
}
```



# Product Management

get product by slug

## Get products


### Request

#### Endpoint

```plaintext
GET /api/products
Host: example.org
Cookie: 
```

`GET /api/products`

#### Parameters


None known.


### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Date: Thu, 04 Jul 2019 13:00:27 GMT
Surrogate-Control: max-age=900
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;11ca1fec8e4ecab0c2a3f8d084eda641&quot;
X-Request-Id: d0560656-d784-483e-9bf4-ff7b845aa92e
X-Runtime: 0.044618
Content-Length: 910
200 OK
```


```json
{
  "count": 1,
  "total_count": 1,
  "current_page": 1,
  "pages": 1,
  "per_page": 25,
  "products": [
    {
      "id": 439,
      "name": "Product #3 - 6920",
      "description": "As seen on TV!",
      "price": "19.99",
      "display_price": "$19.99",
      "available_on": "2018-07-04T13:00:27.338Z",
      "slug": "product-3-6920",
      "meta_description": null,
      "meta_keywords": null,
      "shipping_category_id": 261,
      "taxon_ids": [

      ],
      "total_on_hand": 0,
      "meta_title": null,
      "trends": [

      ],
      "brand": null,
      "brand_description": null,
      "has_variants": false,
      "master": {
        "id": 614,
        "name": "Product #3 - 6920",
        "sku": "SKU-3",
        "price": "19.99",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-3-6920",
        "description": "As seen on TV!",
        "track_inventory": true,
        "display_price": "$19.99",
        "options_text": "",
        "in_stock": false,
        "is_backorderable": false,
        "total_on_hand": 0,
        "is_destroyed": false,
        "option_values": [

        ],
        "images": [

        ]
      },
      "variants": [

      ],
      "option_types": [

      ],
      "product_properties": [

      ],
      "classifications": [

      ]
    }
  ]
}
```



## Return a product


### Request

#### Endpoint

```plaintext
GET /api/products/product-1-8128
Host: example.org
Cookie: 
```

`GET /api/products/:id`

#### Parameters


None known.


### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Date: Thu, 04 Jul 2019 13:00:27 GMT
Surrogate-Control: max-age=900
Surrogate-Key: product_id=1
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;c3493c3573f99d99a22d669cf181696c&quot;
X-Request-Id: 023a2624-693f-42dd-aa49-7b6c53d7d186
X-Runtime: 0.100363
Content-Length: 828
200 OK
```


```json
{
  "id": 437,
  "name": "Product #1 - 8128",
  "description": "As seen on TV!",
  "price": "19.99",
  "display_price": "$19.99",
  "available_on": "2018-07-04T13:00:26.824Z",
  "slug": "product-1-8128",
  "meta_description": null,
  "meta_keywords": null,
  "shipping_category_id": 259,
  "taxon_ids": [

  ],
  "total_on_hand": 0,
  "meta_title": null,
  "trends": [

  ],
  "brand": null,
  "brand_description": null,
  "has_variants": false,
  "master": {
    "id": 612,
    "name": "Product #1 - 8128",
    "sku": "SKU-1",
    "price": "19.99",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": true,
    "slug": "product-1-8128",
    "description": "As seen on TV!",
    "track_inventory": true,
    "display_price": "$19.99",
    "options_text": "",
    "in_stock": false,
    "is_backorderable": false,
    "total_on_hand": 0,
    "is_destroyed": false,
    "option_values": [

    ],
    "images": [

    ]
  },
  "variants": [

  ],
  "option_types": [

  ],
  "product_properties": [

  ],
  "classifications": [

  ]
}
```



## does not return a product


### Request

#### Endpoint

```plaintext
GET /api/products/invalid
Host: example.org
Cookie: 
```

`GET /api/products/:id`

#### Parameters


None known.


### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
Cache-Control: no-cache
X-Request-Id: 10a100fb-a713-4113-9c82-f334b7e30a77
X-Runtime: 0.018365
Content-Length: 65
404 Not Found
```


```json
{
  "error": "The resource you were looking for could not be found."
}
```



# Taxon Endpoint For Navigation



## Does not return taxons with hidden ancestor


### Request

#### Endpoint

```plaintext
GET /api/taxons/nav
Host: example.org
Cookie: 
```

`GET /api/taxons/nav`

#### Parameters


None known.


### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
ETag: W/&quot;414b008aaa19ddc09600e24975441e87&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 1e10b105-2323-4f4c-82fb-102268380c6d
X-Runtime: 0.011053
Content-Length: 193
200 OK
```


```json
[
  {
    "id": 590,
    "name": "Kids",
    "permalink": "category/kids",
    "parent_id": 588,
    "depth": 1,
    "position": 0,
    "brand_taxon?": false,
    "brand_all": false,
    "brand_discover": false,
    "highlight": false,
    "header_link": false
  }
]
```



## Get taxons


### Request

#### Endpoint

```plaintext
GET /api/taxons/nav
Host: example.org
Cookie: 
```

`GET /api/taxons/nav`

#### Parameters


None known.


### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
ETag: W/&quot;4f53cda18c2baa0c0354bb5f9a3ecbe5&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 68d3444e-183a-4bcc-90c8-63d4cb6754f0
X-Runtime: 0.004355
Content-Length: 2
200 OK
```


```json
[

]
```



## Returns only brand taxons with brand_all or brand_discover


### Request

#### Endpoint

```plaintext
GET /api/taxons/nav
Host: example.org
Cookie: 
```

`GET /api/taxons/nav`

#### Parameters


None known.


### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
ETag: W/&quot;09b048bdcc151127adad19198bc6c737&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 0141226d-3250-4536-9299-e62de2c525dc
X-Runtime: 0.007282
Content-Length: 411
200 OK
```


```json
[
  {
    "id": 596,
    "name": "Ruby on Rails",
    "permalink": "brand/ruby-on-rails",
    "parent_id": 595,
    "depth": 1,
    "position": 0,
    "brand_taxon?": true,
    "brand_all": true,
    "brand_discover": false,
    "highlight": false,
    "header_link": false
  },
  {
    "id": 597,
    "name": "Ruby on Rails",
    "permalink": "brand/ruby-on-rails",
    "parent_id": 595,
    "depth": 1,
    "position": 0,
    "brand_taxon?": true,
    "brand_all": false,
    "brand_discover": true,
    "highlight": false,
    "header_link": false
  }
]
```



## Taxons contain all nav attributes


### Request

#### Endpoint

```plaintext
GET /api/taxons/nav
Host: example.org
Cookie: 
```

`GET /api/taxons/nav`

#### Parameters


None known.


### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
ETag: W/&quot;86e6581a94912a8ac9ab66134e412afc&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: e373a10a-ca9f-4f59-bf9a-b1abb6ab4039
X-Runtime: 0.010312
Content-Length: 211
200 OK
```


```json
[
  {
    "id": 594,
    "name": "Ruby on Rails",
    "permalink": "category/ruby-on-rails",
    "parent_id": 593,
    "depth": 1,
    "position": 0,
    "brand_taxon?": false,
    "brand_all": false,
    "brand_discover": false,
    "highlight": false,
    "header_link": false
  }
]
```



# Users

Create a new user and return a header X-Spree-Token to be used for further user related request

## Login


### Request

#### Endpoint

```plaintext
POST /api/users/login
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/users/login`

#### Parameters


```json
user[email]=email3%40example.com&user[password]=secret
```


| Name | Description |
|:-----|:------------|
| user[email] *required* | User email |
| user[password] *required* | User password |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
X-Spree-Token: 89bc94bb1d79cd7bac7e401e4ff031957fe93a522fa7b7b1
ETag: W/&quot;bbed530519dde1bea701a30dffdbcc5e&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 3b750720-5003-482b-afc2-7ec96ee33317
X-Runtime: 0.006362
Content-Length: 551
200 OK
```


```json
{
  "id": 267,
  "email": "email3@example.com",
  "persistence_token": null,
  "perishable_token": null,
  "last_request_at": null,
  "login": "email3@example.com",
  "ship_address_id": null,
  "bill_address_id": null,
  "created_at": "2019-07-04T13:00:26.741Z",
  "updated_at": "2019-07-04T13:00:26.746Z",
  "spree_api_key": "89bc94bb1d79cd7bac7e401e4ff031957fe93a522fa7b7b1",
  "authentication_token": null,
  "deleted_at": null,
  "first_name": null,
  "last_name": null,
  "receive_emails_agree": false,
  "exemption_number": null,
  "vat_id": null,
  "avalara_entity_use_code_id": null,
  "default_payment_method_token": null
}
```



## Signup


### Request

#### Endpoint

```plaintext
POST /api/users
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/users`

#### Parameters


```json
user[email]=test%40example.com&user[password]=test123&user[password_confirmation]=test123
```


| Name | Description |
|:-----|:------------|
| user[email] *required* | User email |
| user[password] *required* | User password |
| user[password_confirmation] *required* | User password confirmation |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
X-Spree-Token: d91a6edfc5ca6dc09847e0076e3fb87fb80f4b9634173115
ETag: W/&quot;3c49d795883ce60385302735aba335fd&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 0207c93e-958d-4e54-bf39-9d096322b359
X-Runtime: 0.037285
Content-Length: 157
201 Created
```


```json
{
  "id": 266,
  "email": "test@example.com",
  "created_at": "2019-07-04T13:00:26.707Z",
  "updated_at": "2019-07-04T13:00:26.709Z",
  "bill_address": null,
  "ship_address": null
}
```



# Variant



## Fetching a variant


### Request

#### Endpoint

```plaintext
GET /api/variants/623
Host: example.org
Cookie: 
```

`GET /api/variants/:variant_id`

#### Parameters


None known.


### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
ETag: W/&quot;966368ab094600f85dcd2c8399291700&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 78f9f229-89e4-421e-ad02-c3fb91731ced
X-Runtime: 0.080471
Content-Length: 1378
200 OK
```


```json
{
  "id": 623,
  "name": "Product #9 - 3621",
  "sku": "SKU-11",
  "price": "10.0",
  "weight": "0.0",
  "height": null,
  "width": null,
  "depth": null,
  "is_master": false,
  "slug": "product-9-3621",
  "description": "As seen on TV!",
  "track_inventory": true,
  "lead_time": 2,
  "display_price": "$10.00",
  "options_text": "Size: S",
  "in_stock": false,
  "is_backorderable": false,
  "total_on_hand": 0,
  "is_destroyed": false,
  "option_values": [
    {
      "id": 189,
      "name": "Size-3",
      "presentation": "S",
      "option_type_name": "foo-size-3",
      "option_type_id": 189,
      "option_type_presentation": "Size"
    }
  ],
  "images": [
    {
      "id": 2,
      "position": 1,
      "attachment_content_type": "image/jpeg",
      "attachment_file_name": "thinking-cat.jpg",
      "type": "Spree::Image",
      "attachment_updated_at": "2019-07-04T13:00:29.054Z",
      "attachment_width": 489,
      "attachment_height": 490,
      "alt": null,
      "viewable_type": "Spree::Variant",
      "viewable_id": 623,
      "mini_url": "/spree/products/2/mini/thinking-cat.jpg?1562245229",
      "small_url": "/spree/products/2/small/thinking-cat.jpg?1562245229",
      "product_url": "/spree/products/2/product/thinking-cat.jpg?1562245229",
      "large_url": "/spree/products/2/large/thinking-cat.jpg?1562245229"
    }
  ],
  "variant_properties": [

  ],
  "stock_items": [

  ],
  "prices": [
    {
      "id": 1199,
      "price": "10.0",
      "vendor_id": 2087,
      "display_price": "$10.00",
      "total_on_hand": 0,
      "country_iso": null,
      "final_sale": false
    },
    {
      "id": 1200,
      "price": "20.0",
      "vendor_id": 2088,
      "display_price": "$20.00",
      "total_on_hand": 0,
      "country_iso": null,
      "final_sale": false
    }
  ]
}
```



