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
PUT /api/orders/R707657075/addresses/283
Accept: application/json
X-Spree-Order-Token: Y8P_ryiZ95KxLOuQFabiRQ
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
ETag: W/&quot;70e32ef89a7b6b851bd1dd05d8171a5f&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 6bd9afbe-b23b-49cf-b11d-e7b1d3db8538
X-Runtime: 0.053289
Content-Length: 513
200 OK
```


```json
{
  "id": 284,
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
  "country_id": 243,
  "country_iso": "US",
  "state_id": 232,
  "state_name": null,
  "state_text": "AL",
  "country": {
    "id": 243,
    "iso_name": "UNITED STATES",
    "iso": "US",
    "iso3": "USA",
    "name": "United States",
    "numcode": 840
  },
  "state": {
    "id": 232,
    "name": "Alabama",
    "abbr": "AL",
    "country_id": 243
  }
}
```



# LineItem

Representation of a single cart item for a specific variant with price of vendor

## Creating a line item


### Request

#### Endpoint

```plaintext
POST /api/orders/R790926782/line_items
Accept: application/json
X-Spree-Order-Token: OuFa8uwbU7sUUXRoMsQwOA
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/:order_number/line_items`

#### Parameters


```json
line_item[variant_id]=482&line_item[options][vendor_id]=1590
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
ETag: W/&quot;4c2000e48d883f7832b03af0ba4dd069&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 31c1de25-ab51-4e09-a4b0-9548f4881704
X-Runtime: 0.112051
Content-Length: 733
201 Created
```


```json
{
  "id": 125,
  "quantity": 1,
  "price": "19.99",
  "variant_id": 482,
  "vendor_id": 1590,
  "single_display_amount": "$19.99",
  "display_amount": "$19.99",
  "total": "19.99",
  "variant": {
    "id": 482,
    "name": "Product #9 - 2963",
    "sku": "SKU-11",
    "price": "19.99",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": false,
    "slug": "product-9-2963",
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
        "id": 173,
        "name": "Size-3",
        "presentation": "S",
        "option_type_name": "foo-size-3",
        "option_type_id": 173,
        "option_type_presentation": "Size"
      }
    ],
    "images": [

    ],
    "product_id": 320
  },
  "vendor_name": "Vendor #28",
  "adjustments": [

  ]
}
```



## Deleting a line item


### Request

#### Endpoint

```plaintext
DELETE /api/orders/R904419522/line_items/122
Accept: application/json
X-Spree-Order-Token: mpNOgWNhUyN_46hopLt5LA
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
X-Request-Id: 2b87357d-6cf1-4109-b5b8-c1d001c0712c
X-Runtime: 0.155080
204 No Content
```




## Updating a line item


### Request

#### Endpoint

```plaintext
PUT /api/orders/R654165351/line_items/123
Accept: application/json
X-Spree-Order-Token: eEPoOTEELqMmvKMcyTJTZw
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
ETag: W/&quot;78ba090e5ddc677a046defc0424f6590&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 4053c39d-a73c-407f-bf28-045ffc576b4f
X-Runtime: 0.097608
Content-Length: 588
200 OK
```


```json
{
  "id": 123,
  "quantity": 2,
  "price": "10.0",
  "variant_id": 477,
  "vendor_id": 1582,
  "single_display_amount": "$10.00",
  "display_amount": "$20.00",
  "total": "20.0",
  "variant": {
    "id": 477,
    "name": "Product #6 - 326",
    "sku": "SKU-7",
    "price": "19.99",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": true,
    "slug": "product-6-326",
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
    "product_id": 317
  },
  "vendor_name": "Vendor #21",
  "adjustments": [

  ]
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
Date: Wed, 26 Jun 2019 07:52:49 GMT
Surrogate-Control: max-age=900
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;c73d53af5acae11f7dcbf0afb9de99ba&quot;
X-Request-Id: dd62c1b1-1bea-4ffe-a9ae-a43cb950d630
X-Runtime: 0.085890
Content-Length: 860
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
      "id": 314,
      "name": "Product #3 - 1748",
      "description": "As seen on TV!",
      "price": "19.99",
      "display_price": "$19.99",
      "available_on": "2018-06-26T07:52:49.748Z",
      "slug": "product-3-1748",
      "meta_description": null,
      "meta_keywords": null,
      "shipping_category_id": 197,
      "taxon_ids": [

      ],
      "total_on_hand": 0,
      "meta_title": null,
      "has_variants": false,
      "master": {
        "id": 473,
        "name": "Product #3 - 1748",
        "sku": "SKU-3",
        "price": "19.99",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-3-1748",
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
GET /api/products/product-1-9127
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
Date: Wed, 26 Jun 2019 07:52:49 GMT
Surrogate-Control: max-age=900
Surrogate-Key: product_id=1
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;ee189c9c28cab12ea2ec3dec661a0659&quot;
X-Request-Id: 8f3acf2e-db32-4184-a803-25255d7dd21e
X-Runtime: 0.215641
Content-Length: 778
200 OK
```


```json
{
  "id": 312,
  "name": "Product #1 - 9127",
  "description": "As seen on TV!",
  "price": "19.99",
  "display_price": "$19.99",
  "available_on": "2018-06-26T07:52:49.002Z",
  "slug": "product-1-9127",
  "meta_description": null,
  "meta_keywords": null,
  "shipping_category_id": 195,
  "taxon_ids": [

  ],
  "total_on_hand": 0,
  "meta_title": null,
  "has_variants": false,
  "master": {
    "id": 471,
    "name": "Product #1 - 9127",
    "sku": "SKU-1",
    "price": "19.99",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": true,
    "slug": "product-1-9127",
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
X-Request-Id: c1c4c981-a940-4ec9-a8bd-01b8e93a38b5
X-Runtime: 0.020051
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
ETag: W/&quot;2faf73157fe3ee02a4f310981537522d&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: f9edebde-0341-448b-9b1d-9931c917328e
X-Runtime: 0.136214
Content-Length: 193
200 OK
```


```json
[
  {
    "id": 519,
    "name": "Kids",
    "permalink": "category/kids",
    "parent_id": 517,
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
X-Request-Id: f5a4d217-abf6-4b0b-8e48-5c6f4effa7d4
X-Runtime: 0.006211
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
ETag: W/&quot;918eb87ad6c5bb80f042b2c9ab7dc0be&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 13a9e6c4-ade8-4f19-86a6-65b0c013c909
X-Runtime: 0.010768
Content-Length: 411
200 OK
```


```json
[
  {
    "id": 523,
    "name": "Ruby on Rails",
    "permalink": "brand/ruby-on-rails",
    "parent_id": 522,
    "depth": 1,
    "position": 0,
    "brand_taxon?": true,
    "brand_all": true,
    "brand_discover": false,
    "highlight": false,
    "header_link": false
  },
  {
    "id": 524,
    "name": "Ruby on Rails",
    "permalink": "brand/ruby-on-rails",
    "parent_id": 522,
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
ETag: W/&quot;342d7d8aebae2160bfb1f6b37f785d4e&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: ab15b79d-217f-46c2-bd1d-c020aab23ee0
X-Runtime: 0.011488
Content-Length: 211
200 OK
```


```json
[
  {
    "id": 528,
    "name": "Ruby on Rails",
    "permalink": "category/ruby-on-rails",
    "parent_id": 527,
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



# Variant



## Fetching a variant


### Request

#### Endpoint

```plaintext
GET /api/variants/475
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
ETag: W/&quot;b80ed90361c1a2fe7b87bda5e62fd42e&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 6f60d900-5664-4361-85a6-9ec6c10f012d
X-Runtime: 0.101329
Content-Length: 1285
200 OK
```


```json
{
  "id": 475,
  "name": "Product #4 - 6933",
  "sku": "SKU-4",
  "price": "10.0",
  "weight": "0.0",
  "height": null,
  "width": null,
  "depth": null,
  "is_master": false,
  "slug": "product-4-6933",
  "description": "As seen on TV!",
  "track_inventory": true,
  "display_price": "$10.00",
  "options_text": "Size: S",
  "in_stock": false,
  "is_backorderable": false,
  "total_on_hand": 0,
  "is_destroyed": false,
  "option_values": [
    {
      "id": 171,
      "name": "Size-1",
      "presentation": "S",
      "option_type_name": "foo-size-1",
      "option_type_id": 171,
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
      "attachment_updated_at": "2019-06-26T07:52:50.368Z",
      "attachment_width": 489,
      "attachment_height": 490,
      "alt": null,
      "viewable_type": "Spree::Variant",
      "viewable_id": 475,
      "mini_url": "/spree/products/2/mini/thinking-cat.jpg?1561535570",
      "small_url": "/spree/products/2/small/thinking-cat.jpg?1561535570",
      "product_url": "/spree/products/2/product/thinking-cat.jpg?1561535570",
      "large_url": "/spree/products/2/large/thinking-cat.jpg?1561535570"
    }
  ],
  "variant_properties": [

  ],
  "stock_items": [

  ],
  "prices": [
    {
      "id": 908,
      "price": "10.0",
      "vendor_id": 1572,
      "display_price": "$10.00",
      "total_on_hand": 0
    },
    {
      "id": 909,
      "price": "20.0",
      "vendor_id": 1573,
      "display_price": "$20.00",
      "total_on_hand": 0
    }
  ]
}
```



