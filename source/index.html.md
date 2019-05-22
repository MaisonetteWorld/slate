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
PUT /api/orders/R079480445/addresses/97
Accept: application/json
X-Spree-Order-Token: Fxe-if3FtCdobkLIoUzThQ
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
ETag: W/&quot;d18b34ca17c127c4b9777315054e4cb1&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 0643444e-4f45-4bca-9f14-310e3e02cae1
X-Runtime: 0.186869
Content-Length: 512
200 OK
```


```json
{
  "id": 98,
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
  "country_id": 123,
  "country_iso": "US",
  "state_id": 112,
  "state_name": null,
  "state_text": "AL",
  "country": {
    "id": 123,
    "iso_name": "UNITED STATES",
    "iso": "US",
    "iso3": "USA",
    "name": "United States",
    "numcode": 840
  },
  "state": {
    "id": 112,
    "name": "Alabama",
    "abbr": "AL",
    "country_id": 123
  }
}
```



# LineItem

Representation of a single cart item for a specific variant with price of vendor

## Creating a line item


### Request

#### Endpoint

```plaintext
POST /api/orders/R462788294/line_items
Accept: application/json
X-Spree-Order-Token: Dqijwjr4FnMkgyEFdpXWJA
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/:order_number/line_items`

#### Parameters


```json
line_item[variant_id]=154&line_item[options][vendor_id]=441
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
ETag: W/&quot;4f058e6062e06dbb64474c8b72502bef&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: de7585e3-49c8-4c47-9bea-88d210418f89
X-Runtime: 0.065294
Content-Length: 699
201 Created
```


```json
{
  "id": 28,
  "quantity": 1,
  "price": "19.99",
  "variant_id": 154,
  "vendor_id": 441,
  "single_display_amount": "$19.99",
  "display_amount": "$19.99",
  "total": "19.99",
  "variant": {
    "id": 154,
    "name": "Product #4 - 8611",
    "sku": "SKU-4",
    "price": "19.99",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": false,
    "slug": "product-4-8611",
    "description": "As seen on TV!",
    "track_inventory": true,
    "display_price": "$19.99",
    "options_text": "Size: S",
    "in_stock": false,
    "is_backorderable": true,
    "total_on_hand": 0,
    "is_destroyed": false,
    "option_values": [
      {
        "id": 60,
        "name": "Size-1",
        "presentation": "S",
        "option_type_name": "foo-size-1",
        "option_type_id": 60,
        "option_type_presentation": "Size"
      }
    ],
    "images": [

    ],
    "product_id": 99
  },
  "adjustments": [

  ]
}
```



## Deleting a line item


### Request

#### Endpoint

```plaintext
DELETE /api/orders/R369643207/line_items/25
Accept: application/json
X-Spree-Order-Token: qLf1vrBI1accpPSCcjvzKg
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
X-Request-Id: 7433c660-1a40-463f-b8ad-304e50457115
X-Runtime: 0.119372
204 No Content
```




## Updating a line item


### Request

#### Endpoint

```plaintext
PUT /api/orders/R034928784/line_items/26
Accept: application/json
X-Spree-Order-Token: mrpxXKTeMHwECDfcD9-tIg
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
ETag: W/&quot;89db6bec7491bbdfce80fb9e76394c8f&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 38609c8f-e468-48f0-a440-4914afce50cd
X-Runtime: 0.086350
Content-Length: 557
200 OK
```


```json
{
  "id": 26,
  "quantity": 2,
  "price": "10.0",
  "variant_id": 151,
  "vendor_id": 439,
  "single_display_amount": "$10.00",
  "display_amount": "$20.00",
  "total": "20.0",
  "variant": {
    "id": 151,
    "name": "Product #2 - 268",
    "sku": "SKU-2",
    "price": "19.99",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": true,
    "slug": "product-2-268",
    "description": "As seen on TV!",
    "track_inventory": true,
    "display_price": "$19.99",
    "options_text": "",
    "in_stock": false,
    "is_backorderable": true,
    "total_on_hand": 0,
    "is_destroyed": false,
    "option_values": [

    ],
    "images": [

    ],
    "product_id": 97
  },
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
Date: Wed, 22 May 2019 09:17:53 GMT
Surrogate-Control: max-age=900
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;1c622fdabeceb70c87cc05c0e43b5833&quot;
X-Request-Id: ae8e27e7-bae6-4d08-8d9e-55d21b74930e
X-Runtime: 0.037927
Content-Length: 858
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
      "id": 102,
      "name": "Product #7 - 6427",
      "description": "As seen on TV!",
      "price": "19.99",
      "display_price": "$19.99",
      "available_on": "2018-05-22T09:17:53.093Z",
      "slug": "product-7-6427",
      "meta_description": null,
      "meta_keywords": null,
      "shipping_category_id": 89,
      "taxon_ids": [

      ],
      "total_on_hand": 0,
      "meta_title": null,
      "has_variants": false,
      "master": {
        "id": 157,
        "name": "Product #7 - 6427",
        "sku": "SKU-8",
        "price": "19.99",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-7-6427",
        "description": "As seen on TV!",
        "track_inventory": true,
        "display_price": "$19.99",
        "options_text": "",
        "in_stock": false,
        "is_backorderable": true,
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
GET /api/products/product-5-6198
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
Date: Wed, 22 May 2019 09:17:52 GMT
Surrogate-Control: max-age=900
Surrogate-Key: product_id=1
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;1f07b28479807ce6c0a9011766eecabe&quot;
X-Request-Id: 701b03e8-261c-4dfb-b829-1041cd810096
X-Runtime: 0.062092
Content-Length: 776
200 OK
```


```json
{
  "id": 100,
  "name": "Product #5 - 6198",
  "description": "As seen on TV!",
  "price": "19.99",
  "display_price": "$19.99",
  "available_on": "2018-05-22T09:17:52.880Z",
  "slug": "product-5-6198",
  "meta_description": null,
  "meta_keywords": null,
  "shipping_category_id": 87,
  "taxon_ids": [

  ],
  "total_on_hand": 0,
  "meta_title": null,
  "has_variants": false,
  "master": {
    "id": 155,
    "name": "Product #5 - 6198",
    "sku": "SKU-6",
    "price": "19.99",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": true,
    "slug": "product-5-6198",
    "description": "As seen on TV!",
    "track_inventory": true,
    "display_price": "$19.99",
    "options_text": "",
    "in_stock": false,
    "is_backorderable": true,
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
X-Request-Id: 4bd9b15e-a638-4a5a-907e-c8b2a6fcc48a
X-Runtime: 0.015589
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
ETag: W/&quot;89023b2d01589ab2e287325b20f1b9e6&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 02f95c3f-5c70-4e10-90aa-08a42664c80e
X-Runtime: 0.008595
Content-Length: 193
200 OK
```


```json
[
  {
    "id": 470,
    "name": "Kids",
    "permalink": "category/kids",
    "parent_id": 468,
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
X-Request-Id: a6eddfbb-e6b7-441b-bebe-d35157bffcdd
X-Runtime: 0.007150
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
ETag: W/&quot;7e1c739c1cff3be714d290fbdb92e94a&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: e988cccf-39e1-49dc-a751-4a9448aed603
X-Runtime: 0.007915
Content-Length: 411
200 OK
```


```json
[
  {
    "id": 464,
    "name": "Ruby on Rails",
    "permalink": "brand/ruby-on-rails",
    "parent_id": 463,
    "depth": 1,
    "position": 0,
    "brand_taxon?": true,
    "brand_all": true,
    "brand_discover": false,
    "highlight": false,
    "header_link": false
  },
  {
    "id": 465,
    "name": "Ruby on Rails",
    "permalink": "brand/ruby-on-rails",
    "parent_id": 463,
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
X-Request-Id: cd35abf7-e9b3-4228-b735-90625f856fe8
X-Runtime: 0.008504
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
GET /api/variants/159
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
ETag: W/&quot;e6a16e00a08dba9ad773b8db1d7296fc&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 3c4fe500-c732-4d05-ac47-4f41e09e891d
X-Runtime: 0.062900
Content-Length: 1371
200 OK
```


```json
{
  "id": 159,
  "name": "Product #8 - 7552",
  "sku": "SKU-9",
  "price": "10.0",
  "weight": "0.0",
  "height": null,
  "width": null,
  "depth": null,
  "is_master": false,
  "slug": "product-8-7552",
  "description": "As seen on TV!",
  "track_inventory": true,
  "display_price": "$10.00",
  "options_text": "Size: S",
  "in_stock": false,
  "is_backorderable": true,
  "total_on_hand": 0,
  "is_destroyed": false,
  "option_values": [
    {
      "id": 61,
      "name": "Size-2",
      "presentation": "S",
      "option_type_name": "foo-size-2",
      "option_type_id": 61,
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
      "attachment_updated_at": "2019-05-22T09:17:53.600Z",
      "attachment_width": 489,
      "attachment_height": 490,
      "alt": null,
      "viewable_type": "Spree::Variant",
      "viewable_id": 159,
      "mini_url": "/spree/products/2/mini/thinking-cat.jpg?1558516673",
      "small_url": "/spree/products/2/small/thinking-cat.jpg?1558516673",
      "product_url": "/spree/products/2/product/thinking-cat.jpg?1558516673",
      "large_url": "/spree/products/2/large/thinking-cat.jpg?1558516673"
    }
  ],
  "variant_properties": [

  ],
  "stock_items": [
    {
      "id": 159,
      "count_on_hand": 0,
      "stock_location_id": 113,
      "backorderable": true,
      "available": true,
      "stock_location_name": "NY Warehouse"
    }
  ],
  "prices": [
    {
      "id": 219,
      "price": "10.0",
      "vendor_id": 450,
      "display_price": "$10.00"
    },
    {
      "id": 220,
      "price": "20.0",
      "vendor_id": 451,
      "display_price": "$20.00"
    }
  ]
}
```



