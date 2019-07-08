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
PUT /api/orders/R618608312/addresses/539
Accept: application/json
X-Spree-Order-Token: VwyL1WpLPYAggEaR4dcDjA
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
ETag: W/&quot;5405a11372af9580cde8219f2a5f8b2f&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 8285387b-d754-40fb-9fb1-30324da6824a
X-Runtime: 0.185979
Content-Length: 513
200 OK
```


```json
{
  "id": 540,
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
  "country_id": 332,
  "country_iso": "US",
  "state_id": 321,
  "state_name": null,
  "state_text": "AL",
  "country": {
    "id": 332,
    "iso_name": "UNITED STATES",
    "iso": "US",
    "iso3": "USA",
    "name": "United States",
    "numcode": 840
  },
  "state": {
    "id": 321,
    "name": "Alabama",
    "abbr": "AL",
    "country_id": 332
  }
}
```



# LineItem

Representation of a single cart item for a specific variant with price of vendor

## Creating a line item


### Request

#### Endpoint

```plaintext
POST /api/orders/R040930786/line_items
Accept: application/json
X-Spree-Order-Token: cM_X5XQ7oPBzwNvgFICuzw
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/:order_number/line_items`

#### Parameters


```json
line_item[variant_id]=683&line_item[options][vendor_id]=2249
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
ETag: W/&quot;bab5f6360133524f1bd0d346c6c6e7c4&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 90637aa4-d964-43d2-b0dd-d28ab08b9af8
X-Runtime: 0.180647
Content-Length: 731
201 Created
```


```json
{
  "id": 256,
  "quantity": 1,
  "price": "19.99",
  "variant_id": 683,
  "vendor_id": 2249,
  "single_display_amount": "$19.99",
  "display_amount": "$19.99",
  "total": "19.99",
  "variant": {
    "id": 683,
    "name": "Product #3 - 8443",
    "sku": "SKU-4",
    "price": "19.99",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": false,
    "slug": "product-3-8443",
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
        "id": 222,
        "name": "Size-2",
        "presentation": "S",
        "option_type_name": "foo-size-2",
        "option_type_id": 222,
        "option_type_presentation": "Size"
      }
    ],
    "images": [

    ],
    "product_id": 472
  },
  "vendor_name": "Vendor #6",
  "adjustments": [

  ]
}
```



## Deleting a line item


### Request

#### Endpoint

```plaintext
DELETE /api/orders/R653995564/line_items/257
Accept: application/json
X-Spree-Order-Token: 5L79oAG9E0qYCOfru5FGnA
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
X-Request-Id: eba34349-abe4-418f-a513-e3b7ddd04796
X-Runtime: 0.047148
204 No Content
```




## Updating a line item


### Request

#### Endpoint

```plaintext
PUT /api/orders/R054154469/line_items/258
Accept: application/json
X-Spree-Order-Token: rBdFBAyYhBdtOZgL2QDhUA
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
ETag: W/&quot;60f2c5ccfe0d696c7a973419e49d4375&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 47dcdef2-cbef-4bcc-8457-266cd7d7223b
X-Runtime: 0.056699
Content-Length: 588
200 OK
```


```json
{
  "id": 258,
  "quantity": 2,
  "price": "10.0",
  "variant_id": 685,
  "vendor_id": 2259,
  "single_display_amount": "$10.00",
  "display_amount": "$20.00",
  "total": "20.0",
  "variant": {
    "id": 685,
    "name": "Product #5 - 676",
    "sku": "SKU-7",
    "price": "19.99",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": true,
    "slug": "product-5-676",
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
    "product_id": 474
  },
  "vendor_name": "Vendor #14",
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
X-Spree-Token: eca6f3aabb24c2ae7e6b57e6b0a1205ccc0b820f4d6fdb53
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
X-Request-Id: a7acc427-d3e1-4f66-87d6-1d1da4be248d
X-Runtime: 0.014861
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
Date: Mon, 08 Jul 2019 15:09:18 GMT
Surrogate-Control: max-age=900
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;f748ef214a5ad99dcf20c246b627bc14&quot;
X-Request-Id: ac816de2-4d1a-4b9d-a49f-07c6af9fba60
X-Runtime: 0.049319
Content-Length: 911
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
      "id": 478,
      "name": "Product #9 - 2635",
      "description": "As seen on TV!",
      "price": "19.99",
      "display_price": "$19.99",
      "available_on": "2018-07-08T15:09:18.337Z",
      "slug": "product-9-2635",
      "meta_description": null,
      "meta_keywords": null,
      "shipping_category_id": 294,
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
        "id": 690,
        "name": "Product #9 - 2635",
        "sku": "SKU-12",
        "price": "19.99",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-9-2635",
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
GET /api/products/product-7-4326
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
Date: Mon, 08 Jul 2019 15:09:18 GMT
Surrogate-Control: max-age=900
Surrogate-Key: product_id=1
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;69ff3bb15ad440441126ee16af19e112&quot;
X-Request-Id: 6856a42f-baf2-4870-97ee-ca2a679aa7ca
X-Runtime: 0.064407
Content-Length: 829
200 OK
```


```json
{
  "id": 476,
  "name": "Product #7 - 4326",
  "description": "As seen on TV!",
  "price": "19.99",
  "display_price": "$19.99",
  "available_on": "2018-07-08T15:09:18.118Z",
  "slug": "product-7-4326",
  "meta_description": null,
  "meta_keywords": null,
  "shipping_category_id": 292,
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
    "id": 688,
    "name": "Product #7 - 4326",
    "sku": "SKU-10",
    "price": "19.99",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": true,
    "slug": "product-7-4326",
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
X-Request-Id: 0911bc5e-c779-4b75-a505-03ce00a765c1
X-Runtime: 0.015113
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
ETag: W/&quot;9acfca83eec60b447cc7d1ab35c99030&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 89de7927-54b5-4747-acfc-506cbcfe3a16
X-Runtime: 0.007798
Content-Length: 193
200 OK
```


```json
[
  {
    "id": 595,
    "name": "Kids",
    "permalink": "category/kids",
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
X-Request-Id: e3554289-dd2a-417c-859d-feb9141e0dec
X-Runtime: 0.003934
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
ETag: W/&quot;66c3e656e0577d6c326a37cd5e8be869&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: b678de55-7ecf-4692-adff-351b9c639a8f
X-Runtime: 0.010994
Content-Length: 411
200 OK
```


```json
[
  {
    "id": 589,
    "name": "Ruby on Rails",
    "permalink": "brand/ruby-on-rails",
    "parent_id": 588,
    "depth": 1,
    "position": 0,
    "brand_taxon?": true,
    "brand_all": true,
    "brand_discover": false,
    "highlight": false,
    "header_link": false
  },
  {
    "id": 590,
    "name": "Ruby on Rails",
    "permalink": "brand/ruby-on-rails",
    "parent_id": 588,
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
ETag: W/&quot;d4811eaa4f73cc513d03e53f2530b95f&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 0ab4904e-5782-4602-af40-a40028ffddcc
X-Runtime: 0.008616
Content-Length: 211
200 OK
```


```json
[
  {
    "id": 599,
    "name": "Ruby on Rails",
    "permalink": "category/ruby-on-rails",
    "parent_id": 598,
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

Validate user email and password. Does not handle any session and only return the user

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
user[email]=email2%40example.com&user[password]=secret
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
X-Spree-Token: 88ac44812776eeed2107990739c4aab99ace36b7d61008d0
ETag: W/&quot;d4a1dc25794b8a06fa1eaab24255b122&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: e25af6c4-269d-4703-889c-8aa0ffe75e6f
X-Runtime: 0.007156
Content-Length: 551
200 OK
```


```json
{
  "id": 299,
  "email": "email2@example.com",
  "persistence_token": null,
  "perishable_token": null,
  "last_request_at": null,
  "login": "email2@example.com",
  "ship_address_id": null,
  "bill_address_id": null,
  "created_at": "2019-07-08T15:09:16.017Z",
  "updated_at": "2019-07-08T15:09:16.021Z",
  "spree_api_key": "88ac44812776eeed2107990739c4aab99ace36b7d61008d0",
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
X-Spree-Token: ebdbad84a3bfa32264262b4d98948d616711c2660177f812
ETag: W/&quot;f60804b3c2396a8160eb197758eaf48c&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 130dd8a5-7fc0-4bab-89a2-e8472eb648aa
X-Runtime: 0.029230
Content-Length: 157
201 Created
```


```json
{
  "id": 300,
  "email": "test@example.com",
  "created_at": "2019-07-08T15:09:16.038Z",
  "updated_at": "2019-07-08T15:09:16.040Z",
  "bill_address": null,
  "ship_address": null
}
```



# Variant



## Fetching a variant


### Request

#### Endpoint

```plaintext
GET /api/variants/687
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
ETag: W/&quot;f0ed11207394f690d81a090bb737e789&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 15af95d6-5359-43a0-9b12-de8360f7cedc
X-Runtime: 0.075039
Content-Length: 1377
200 OK
```


```json
{
  "id": 687,
  "name": "Product #6 - 4360",
  "sku": "SKU-8",
  "price": "10.0",
  "weight": "0.0",
  "height": null,
  "width": null,
  "depth": null,
  "is_master": false,
  "slug": "product-6-4360",
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
      "id": 223,
      "name": "Size-3",
      "presentation": "S",
      "option_type_name": "foo-size-3",
      "option_type_id": 223,
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
      "attachment_updated_at": "2019-07-08T15:09:17.873Z",
      "attachment_width": 489,
      "attachment_height": 490,
      "alt": null,
      "viewable_type": "Spree::Variant",
      "viewable_id": 687,
      "mini_url": "/spree/products/2/mini/thinking-cat.jpg?1562598557",
      "small_url": "/spree/products/2/small/thinking-cat.jpg?1562598557",
      "product_url": "/spree/products/2/product/thinking-cat.jpg?1562598557",
      "large_url": "/spree/products/2/large/thinking-cat.jpg?1562598557"
    }
  ],
  "variant_properties": [

  ],
  "stock_items": [

  ],
  "prices": [
    {
      "id": 1333,
      "price": "10.0",
      "vendor_id": 2265,
      "display_price": "$10.00",
      "total_on_hand": 0,
      "country_iso": null,
      "final_sale": false
    },
    {
      "id": 1334,
      "price": "20.0",
      "vendor_id": 2266,
      "display_price": "$20.00",
      "total_on_hand": 0,
      "country_iso": null,
      "final_sale": false
    }
  ]
}
```



