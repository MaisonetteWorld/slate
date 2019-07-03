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
PUT /api/orders/R150764993/addresses/473
Accept: application/json
X-Spree-Order-Token: mUFiPkEcIG6a_QVllQufLg
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
ETag: W/&quot;f9c4a6765904f062098f2d7178111281&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: fce258be-bf72-46c0-a5db-6439b612a467
X-Runtime: 0.046912
Content-Length: 513
200 OK
```


```json
{
  "id": 474,
  "firstname": "John the Tester",
  "lastname": null,
  "full_name": "John the Tester",
  "address1": "A Different Road",
  "address2": "Northwest",
  "city": "Herndon",
  "zipcode": "10008",
  "phone": "555-555-0199",
  "company": "Company",
  "alternative_phone": "555-555-0199",
  "country_id": 308,
  "country_iso": "US",
  "state_id": 297,
  "state_name": null,
  "state_text": "AL",
  "country": {
    "id": 308,
    "iso_name": "UNITED STATES",
    "iso": "US",
    "iso3": "USA",
    "name": "United States",
    "numcode": 840
  },
  "state": {
    "id": 297,
    "name": "Alabama",
    "abbr": "AL",
    "country_id": 308
  }
}
```



# LineItem

Representation of a single cart item for a specific variant with price of vendor

## Creating a line item


### Request

#### Endpoint

```plaintext
POST /api/orders/R620903303/line_items
Accept: application/json
X-Spree-Order-Token: mFpJvXgTNn27wHFH77FoYQ
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/:order_number/line_items`

#### Parameters


```json
line_item[variant_id]=612&line_item[options][vendor_id]=2043
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
ETag: W/&quot;2213ba792277a268dc5b99b63ec7e0e9&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 651f6abd-600a-4ec5-8e25-772e235af5b6
X-Runtime: 0.422658
Content-Length: 731
201 Created
```


```json
{
  "id": 217,
  "quantity": 1,
  "price": "19.99",
  "variant_id": 612,
  "vendor_id": 2043,
  "single_display_amount": "$19.99",
  "display_amount": "$19.99",
  "total": "19.99",
  "variant": {
    "id": 612,
    "name": "Product #3 - 3293",
    "sku": "SKU-4",
    "price": "19.99",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": false,
    "slug": "product-3-3293",
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
    "product_id": 435
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
DELETE /api/orders/R467973894/line_items/219
Accept: application/json
X-Spree-Order-Token: EX0IZTx2onZA2V6BcYlgLw
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
X-Request-Id: 6b76818e-1e5b-4606-873c-e2f300f439f7
X-Runtime: 0.058910
204 No Content
```




## Updating a line item


### Request

#### Endpoint

```plaintext
PUT /api/orders/R968868742/line_items/218
Accept: application/json
X-Spree-Order-Token: ry8IAqQZOfbIm6VThgYZlg
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
ETag: W/&quot;cde6a1f1f8538896e85813622d7be381&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: d08e3580-a164-4555-86b5-0e031ca0def9
X-Runtime: 0.084052
Content-Length: 590
200 OK
```


```json
{
  "id": 218,
  "quantity": 2,
  "price": "10.0",
  "variant_id": 613,
  "vendor_id": 2049,
  "single_display_amount": "$10.00",
  "display_amount": "$20.00",
  "total": "20.0",
  "variant": {
    "id": 613,
    "name": "Product #4 - 3782",
    "sku": "SKU-6",
    "price": "19.99",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": true,
    "slug": "product-4-3782",
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
    "product_id": 436
  },
  "vendor_name": "Vendor #11",
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
X-Spree-Token: 320ef0a2c1f771905544b68b8eea4ab3e4b376eed8ea033e
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
X-Request-Id: 8cd182c2-4a49-4a23-a1c3-5511499ed700
X-Runtime: 0.021255
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
Date: Wed, 03 Jul 2019 15:30:24 GMT
Surrogate-Control: max-age=900
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;934b2fe568f58ad5ad55bdebfdd8d6f9&quot;
X-Request-Id: dfc9b82a-4153-4aa3-994f-e30c3a4674b5
X-Runtime: 0.072610
Content-Length: 907
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
      "id": 440,
      "name": "Product #8 - 716",
      "description": "As seen on TV!",
      "price": "19.99",
      "display_price": "$19.99",
      "available_on": "2018-07-03T15:30:24.136Z",
      "slug": "product-8-716",
      "meta_description": null,
      "meta_keywords": null,
      "shipping_category_id": 262,
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
        "id": 617,
        "name": "Product #8 - 716",
        "sku": "SKU-10",
        "price": "19.99",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-8-716",
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
GET /api/products/product-6-4509
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
Date: Wed, 03 Jul 2019 15:30:23 GMT
Surrogate-Control: max-age=900
Surrogate-Key: product_id=1
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;e335ed4685b586ba8cd0c6581cf2dcd9&quot;
X-Request-Id: 60578f21-0c29-4ac2-a9a7-02d33f15ae89
X-Runtime: 0.078469
Content-Length: 828
200 OK
```


```json
{
  "id": 438,
  "name": "Product #6 - 4509",
  "description": "As seen on TV!",
  "price": "19.99",
  "display_price": "$19.99",
  "available_on": "2018-07-03T15:30:23.853Z",
  "slug": "product-6-4509",
  "meta_description": null,
  "meta_keywords": null,
  "shipping_category_id": 260,
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
    "id": 615,
    "name": "Product #6 - 4509",
    "sku": "SKU-8",
    "price": "19.99",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": true,
    "slug": "product-6-4509",
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
X-Request-Id: 41b1e552-71e5-4678-aaa5-bef54a0af6b0
X-Runtime: 0.023341
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
ETag: W/&quot;1682b45ea159370fc43ad71f3859ea8c&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 6d027c8b-9ba5-4873-abef-bdee499477d6
X-Runtime: 0.008391
Content-Length: 193
200 OK
```


```json
[
  {
    "id": 597,
    "name": "Kids",
    "permalink": "category/kids",
    "parent_id": 595,
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
X-Request-Id: 7ecf40d6-e15b-4597-b564-1562b68c559f
X-Runtime: 0.006076
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
X-Request-Id: 27a73286-56b4-443c-9cf6-ccf480bf4435
X-Runtime: 0.010632
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
ETag: W/&quot;86e6581a94912a8ac9ab66134e412afc&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 8292372b-ac07-42b2-9795-6fcd4218ff00
X-Runtime: 0.008953
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
user[email]=email5%40example.com&user[password]=secret
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
X-Spree-Token: 7a383fe9838ac2dc778f28ad0fd2ea7abfbb42b72e3863dd
ETag: W/&quot;84cbfee8de6de53922ed335da4a5f230&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 2b120290-6e1e-4c66-82d4-fa6b7a69cb1e
X-Runtime: 0.007952
Content-Length: 551
200 OK
```


```json
{
  "id": 264,
  "email": "email5@example.com",
  "persistence_token": null,
  "perishable_token": null,
  "last_request_at": null,
  "login": "email5@example.com",
  "ship_address_id": null,
  "bill_address_id": null,
  "created_at": "2019-07-03T15:30:24.347Z",
  "updated_at": "2019-07-03T15:30:24.353Z",
  "spree_api_key": "7a383fe9838ac2dc778f28ad0fd2ea7abfbb42b72e3863dd",
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
X-Spree-Token: d0fedafd2a4cec04ad7ff079fa87020b18bb591c987796d2
ETag: W/&quot;3403402efdf5bdb65d7c14008e16976b&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: d5c8419d-7189-4996-b72a-f4610ea8e4ac
X-Runtime: 0.030002
Content-Length: 157
201 Created
```


```json
{
  "id": 265,
  "email": "test@example.com",
  "created_at": "2019-07-03T15:30:24.373Z",
  "updated_at": "2019-07-03T15:30:24.375Z",
  "bill_address": null,
  "ship_address": null
}
```



# Variant



## Fetching a variant


### Request

#### Endpoint

```plaintext
GET /api/variants/619
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
ETag: W/&quot;eddf6811e3e90d0af0f744029846c4e0&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: c8ee701a-c2c1-4b5e-b775-6b6a3d8fc581
X-Runtime: 0.090962
Content-Length: 1378
200 OK
```


```json
{
  "id": 619,
  "name": "Product #9 - 2146",
  "sku": "SKU-11",
  "price": "10.0",
  "weight": "0.0",
  "height": null,
  "width": null,
  "depth": null,
  "is_master": false,
  "slug": "product-9-2146",
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
      "attachment_updated_at": "2019-07-03T15:30:24.976Z",
      "attachment_width": 489,
      "attachment_height": 490,
      "alt": null,
      "viewable_type": "Spree::Variant",
      "viewable_id": 619,
      "mini_url": "/spree/products/2/mini/thinking-cat.jpg?1562167824",
      "small_url": "/spree/products/2/small/thinking-cat.jpg?1562167824",
      "product_url": "/spree/products/2/product/thinking-cat.jpg?1562167824",
      "large_url": "/spree/products/2/large/thinking-cat.jpg?1562167824"
    }
  ],
  "variant_properties": [

  ],
  "stock_items": [

  ],
  "prices": [
    {
      "id": 1191,
      "price": "10.0",
      "vendor_id": 2071,
      "display_price": "$10.00",
      "total_on_hand": 0,
      "country_iso": null,
      "final_sale": false
    },
    {
      "id": 1192,
      "price": "20.0",
      "vendor_id": 2072,
      "display_price": "$20.00",
      "total_on_hand": 0,
      "country_iso": null,
      "final_sale": false
    }
  ]
}
```



