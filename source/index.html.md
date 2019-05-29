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
PUT /api/orders/R545880644/addresses/103
Accept: application/json
X-Spree-Order-Token: yJ4V5rOv_iEv9B0GZXVkGQ
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
ETag: W/&quot;3a358f5dd0506ae700b43768927f271e&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 7c376318-d55d-44c9-9e99-a9b74f745b9e
X-Runtime: 0.059628
Content-Length: 513
200 OK
```


```json
{
  "id": 104,
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
  "country_id": 134,
  "country_iso": "US",
  "state_id": 123,
  "state_name": null,
  "state_text": "AL",
  "country": {
    "id": 134,
    "iso_name": "UNITED STATES",
    "iso": "US",
    "iso3": "USA",
    "name": "United States",
    "numcode": 840
  },
  "state": {
    "id": 123,
    "name": "Alabama",
    "abbr": "AL",
    "country_id": 134
  }
}
```



# LineItem

Representation of a single cart item for a specific variant with price of vendor

## Creating a line item


### Request

#### Endpoint

```plaintext
POST /api/orders/R122345805/line_items
Accept: application/json
X-Spree-Order-Token: DPQiH92NaFv8jUnX7g94Xg
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/:order_number/line_items`

#### Parameters


```json
line_item[variant_id]=166&line_item[options][vendor_id]=481
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
ETag: W/&quot;b59b37b1f9b86e4d1c9ae7ea7a392cac&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 998026d3-7b97-4e2b-8917-a2b2e33a3df8
X-Runtime: 0.108399
Content-Length: 701
201 Created
```


```json
{
  "id": 28,
  "quantity": 1,
  "price": "19.99",
  "variant_id": 166,
  "vendor_id": 481,
  "single_display_amount": "$19.99",
  "display_amount": "$19.99",
  "total": "19.99",
  "variant": {
    "id": 166,
    "name": "Product #4 - 8586",
    "sku": "SKU-4",
    "price": "19.99",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": false,
    "slug": "product-4-8586",
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
        "id": 67,
        "name": "Size-1",
        "presentation": "S",
        "option_type_name": "foo-size-1",
        "option_type_id": 67,
        "option_type_presentation": "Size"
      }
    ],
    "images": [

    ],
    "product_id": 105
  },
  "adjustments": [

  ]
}
```



## Deleting a line item


### Request

#### Endpoint

```plaintext
DELETE /api/orders/R208500634/line_items/26
Accept: application/json
X-Spree-Order-Token: AjMu1b7Huu1eXPwL9nYYhA
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
X-Request-Id: be5530a1-92fa-4e6a-80db-aa4220bec9c9
X-Runtime: 0.067252
204 No Content
```




## Updating a line item


### Request

#### Endpoint

```plaintext
PUT /api/orders/R677258716/line_items/25
Accept: application/json
X-Spree-Order-Token: NBQtrw3c12Of57-R-IvjQQ
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
ETag: W/&quot;7173b24dc64c596f01d4e7612f2b000a&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: dc163388-e064-469c-b0b4-1cdfb9b49d87
X-Runtime: 0.393791
Content-Length: 561
200 OK
```


```json
{
  "id": 25,
  "quantity": 2,
  "price": "10.0",
  "variant_id": 162,
  "vendor_id": 477,
  "single_display_amount": "$10.00",
  "display_amount": "$20.00",
  "total": "20.0",
  "variant": {
    "id": 162,
    "name": "Product #1 - 6500",
    "sku": "SKU-1",
    "price": "19.99",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": true,
    "slug": "product-1-6500",
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
    "product_id": 102
  },
  "adjustments": [

  ]
}
```



# Product Management



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
Date: Wed, 29 May 2019 14:29:42 GMT
Surrogate-Control: max-age=900
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;aa9090dc7af2549c627b71f62946cc35&quot;
X-Request-Id: 89350e06-d04c-4192-95d0-924ae515ec59
X-Runtime: 0.090933
Content-Length: 859
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
      "id": 106,
      "name": "Product #5 - 1575",
      "description": "As seen on TV!",
      "price": "19.99",
      "display_price": "$19.99",
      "available_on": "2018-05-29T14:29:42.228Z",
      "slug": "product-5-1575",
      "meta_description": null,
      "meta_keywords": null,
      "shipping_category_id": 92,
      "taxon_ids": [

      ],
      "total_on_hand": 0,
      "meta_title": null,
      "has_variants": false,
      "master": {
        "id": 167,
        "name": "Product #5 - 1575",
        "sku": "SKU-6",
        "price": "19.99",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-5-1575",
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
GET /api/products/product-6-5280
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
Date: Wed, 29 May 2019 14:29:42 GMT
Surrogate-Control: max-age=900
Surrogate-Key: product_id=1
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;cf6da9b44511989ccb424406bce9589d&quot;
X-Request-Id: a064104c-f943-4864-a975-56292d8f60e7
X-Runtime: 0.054589
Content-Length: 777
200 OK
```


```json
{
  "id": 107,
  "name": "Product #6 - 5280",
  "description": "As seen on TV!",
  "price": "19.99",
  "display_price": "$19.99",
  "available_on": "2018-05-29T14:29:42.432Z",
  "slug": "product-6-5280",
  "meta_description": null,
  "meta_keywords": null,
  "shipping_category_id": 93,
  "taxon_ids": [

  ],
  "total_on_hand": 0,
  "meta_title": null,
  "has_variants": false,
  "master": {
    "id": 168,
    "name": "Product #6 - 5280",
    "sku": "SKU-7",
    "price": "19.99",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": true,
    "slug": "product-6-5280",
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
X-Request-Id: 00b30f7d-c805-4e65-a8db-71fd1716e600
X-Runtime: 0.025292
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
ETag: W/&quot;66b7845b2b63850dbdff4b5b7245a612&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 4713c28e-48d9-4f7f-bab6-807e71c82b06
X-Runtime: 0.024892
Content-Length: 193
200 OK
```


```json
[
  {
    "id": 465,
    "name": "Kids",
    "permalink": "category/kids",
    "parent_id": 463,
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
X-Request-Id: 27794994-2146-4512-ad54-2d27ae682843
X-Runtime: 0.006309
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
ETag: W/&quot;39ceac48f201420ceeaaf8008f6655e0&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 447f21cf-6240-4cae-a51c-f78e247d9e1a
X-Runtime: 0.015282
Content-Length: 411
200 OK
```


```json
[
  {
    "id": 469,
    "name": "Ruby on Rails",
    "permalink": "brand/ruby-on-rails",
    "parent_id": 468,
    "depth": 1,
    "position": 0,
    "brand_taxon?": true,
    "brand_all": true,
    "brand_discover": false,
    "highlight": false,
    "header_link": false
  },
  {
    "id": 470,
    "name": "Ruby on Rails",
    "permalink": "brand/ruby-on-rails",
    "parent_id": 468,
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
ETag: W/&quot;366cd88aa00c92d3dda39ea1c9d94f0f&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 5c9d1a85-8379-4ffb-9984-55cb0b108177
X-Runtime: 0.012380
Content-Length: 211
200 OK
```


```json
[
  {
    "id": 474,
    "name": "Ruby on Rails",
    "permalink": "category/ruby-on-rails",
    "parent_id": 473,
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
GET /api/variants/171
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
ETag: W/&quot;3e496337a05d2f6cb6cf05f5494d9685&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 079a56ad-797c-4cba-a494-17ade3fb93f8
X-Runtime: 0.081812
Content-Length: 1245
200 OK
```


```json
{
  "id": 171,
  "name": "Product #8 - 1144",
  "sku": "SKU-9",
  "price": "10.0",
  "weight": "0.0",
  "height": null,
  "width": null,
  "depth": null,
  "is_master": false,
  "slug": "product-8-1144",
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
      "id": 68,
      "name": "Size-2",
      "presentation": "S",
      "option_type_name": "foo-size-2",
      "option_type_id": 68,
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
      "attachment_updated_at": "2019-05-29T14:29:43.065Z",
      "attachment_width": 489,
      "attachment_height": 490,
      "alt": null,
      "viewable_type": "Spree::Variant",
      "viewable_id": 171,
      "mini_url": "/spree/products/2/mini/thinking-cat.jpg?1559140183",
      "small_url": "/spree/products/2/small/thinking-cat.jpg?1559140183",
      "product_url": "/spree/products/2/product/thinking-cat.jpg?1559140183",
      "large_url": "/spree/products/2/large/thinking-cat.jpg?1559140183"
    }
  ],
  "variant_properties": [

  ],
  "stock_items": [

  ],
  "prices": [
    {
      "id": 232,
      "price": "10.0",
      "vendor_id": 490,
      "display_price": "$10.00"
    },
    {
      "id": 233,
      "price": "20.0",
      "vendor_id": 491,
      "display_price": "$20.00"
    }
  ]
}
```



