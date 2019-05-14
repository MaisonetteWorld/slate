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
PUT /api/orders/R751568157/addresses/103
Accept: application/json
X-Spree-Order-Token: tzPXPMHzlfaHmJ4bhsrodA
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
ETag: W/&quot;af3f3e6a9d472894be5d8c6429ce4155&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: debf1476-b0ca-47fc-8200-8b1dcf3af9ab
X-Runtime: 0.059714
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
  "country_id": 105,
  "country_iso": "US",
  "state_id": 104,
  "state_name": null,
  "state_text": "AL",
  "country": {
    "id": 105,
    "iso_name": "UNITED STATES",
    "iso": "US",
    "iso3": "USA",
    "name": "United States",
    "numcode": 840
  },
  "state": {
    "id": 104,
    "name": "Alabama",
    "abbr": "AL",
    "country_id": 105
  }
}
```



# LineItem

Representation of a single cart item for a specific variant with price of vendor

## Creating a line item


### Request

#### Endpoint

```plaintext
POST /api/orders/R738631971/line_items
Accept: application/json
X-Spree-Order-Token: o5cQS1Iy8YvBHciDcZPmHw
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/:order_number/line_items`

#### Parameters


```json
line_item[variant_id]=156&line_item[options][vendor_id]=321
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
ETag: W/&quot;246f6da317937ecd60298b4cd7cf4e5c&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 0cef2409-646b-46e2-8003-31fceb78107b
X-Runtime: 0.102259
Content-Length: 700
201 Created
```


```json
{
  "id": 28,
  "quantity": 1,
  "price": "19.99",
  "variant_id": 156,
  "vendor_id": 321,
  "single_display_amount": "$19.99",
  "display_amount": "$19.99",
  "total": "19.99",
  "variant": {
    "id": 156,
    "name": "Product #5 - 7145",
    "sku": "SKU-6",
    "price": "19.99",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": false,
    "slug": "product-5-7145",
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
        "id": 61,
        "name": "Size-2",
        "presentation": "S",
        "option_type_name": "foo-size-2",
        "option_type_id": 61,
        "option_type_presentation": "Size"
      }
    ],
    "images": [

    ],
    "product_id": 100
  },
  "adjustments": [

  ]
}
```



## Deleting a line item


### Request

#### Endpoint

```plaintext
DELETE /api/orders/R385968941/line_items/25
Accept: application/json
X-Spree-Order-Token: JRIfU0M9sQVL_d2IgLrusQ
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
X-Request-Id: 7d361082-66b9-456c-96c2-befcf2b80d59
X-Runtime: 0.178036
204 No Content
```




## Updating a line item


### Request

#### Endpoint

```plaintext
PUT /api/orders/R376569258/line_items/26
Accept: application/json
X-Spree-Order-Token: lKuxiSxQkq3_hTFH728f9w
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
ETag: W/&quot;599f601fd3e42a9b69366173bbdcbe28&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 5ca5daf3-58db-4fcf-a329-d3760cbe4795
X-Runtime: 0.126762
Content-Length: 559
200 OK
```


```json
{
  "id": 26,
  "quantity": 2,
  "price": "10.0",
  "variant_id": 153,
  "vendor_id": 320,
  "single_display_amount": "$10.00",
  "display_amount": "$20.00",
  "total": "20.0",
  "variant": {
    "id": 153,
    "name": "Product #3 - 2443",
    "sku": "SKU-4",
    "price": "19.99",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": true,
    "slug": "product-3-2443",
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
    "product_id": 98
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
Date: Tue, 14 May 2019 13:20:50 GMT
Surrogate-Control: max-age=900
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;d55927a06b2657b7ee23431fac595e05&quot;
X-Request-Id: 37f11730-5c36-4f2d-89aa-0bf1dbd16ac8
X-Runtime: 0.107582
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
      "id": 101,
      "name": "Product #6 - 3278",
      "description": "As seen on TV!",
      "price": "19.99",
      "display_price": "$19.99",
      "available_on": "2018-05-14T13:20:50.465Z",
      "slug": "product-6-3278",
      "meta_description": null,
      "meta_keywords": null,
      "shipping_category_id": 88,
      "taxon_ids": [

      ],
      "total_on_hand": 0,
      "meta_title": null,
      "has_variants": false,
      "master": {
        "id": 157,
        "name": "Product #6 - 3278",
        "sku": "SKU-8",
        "price": "19.99",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-6-3278",
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
GET /api/products/product-7-8743
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
Date: Tue, 14 May 2019 13:20:50 GMT
Surrogate-Control: max-age=900
Surrogate-Key: product_id=1
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;6a030347de470160b4c45739d929e421&quot;
X-Request-Id: 35120efa-dc18-47ad-a1dc-80f84c0fe17d
X-Runtime: 0.061847
Content-Length: 776
200 OK
```


```json
{
  "id": 102,
  "name": "Product #7 - 8743",
  "description": "As seen on TV!",
  "price": "19.99",
  "display_price": "$19.99",
  "available_on": "2018-05-14T13:20:50.681Z",
  "slug": "product-7-8743",
  "meta_description": null,
  "meta_keywords": null,
  "shipping_category_id": 89,
  "taxon_ids": [

  ],
  "total_on_hand": 0,
  "meta_title": null,
  "has_variants": false,
  "master": {
    "id": 158,
    "name": "Product #7 - 8743",
    "sku": "SKU-9",
    "price": "19.99",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": true,
    "slug": "product-7-8743",
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
X-Request-Id: dd08d6f1-a292-4d41-9dd4-347835b6feec
X-Runtime: 0.042181
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
X-Request-Id: e1b751a5-d0ca-4681-b5eb-1fa192087f34
X-Runtime: 0.178327
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
X-Request-Id: b705e6c9-f79d-48c4-b846-f9ad885f40d6
X-Runtime: 0.008369
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
X-Request-Id: f86373a5-d573-4f1e-9918-5865ee7a3036
X-Runtime: 0.013493
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
X-Request-Id: 734f60d7-b3eb-4b58-98ff-50cd97f6e2e1
X-Runtime: 0.016540
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
GET /api/variants/151
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
ETag: W/&quot;a312f76f8cbf6f929dad66131cba4ef4&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: fb06910c-6794-4603-a1cb-e47877b5b381
X-Runtime: 0.153949
Content-Length: 1370
200 OK
```


```json
{
  "id": 151,
  "name": "Product #1 - 5702",
  "sku": "SKU-1",
  "price": "10.0",
  "weight": "0.0",
  "height": null,
  "width": null,
  "depth": null,
  "is_master": false,
  "slug": "product-1-5702",
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
      "id": 60,
      "name": "Size-1",
      "presentation": "S",
      "option_type_name": "foo-size-1",
      "option_type_id": 60,
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
      "attachment_updated_at": "2019-05-14T13:20:48.168Z",
      "attachment_width": 489,
      "attachment_height": 490,
      "alt": null,
      "viewable_type": "Spree::Variant",
      "viewable_id": 151,
      "mini_url": "/spree/products/2/mini/thinking-cat.jpg?1557840048",
      "small_url": "/spree/products/2/small/thinking-cat.jpg?1557840048",
      "product_url": "/spree/products/2/product/thinking-cat.jpg?1557840048",
      "large_url": "/spree/products/2/large/thinking-cat.jpg?1557840048"
    }
  ],
  "variant_properties": [

  ],
  "stock_items": [
    {
      "id": 151,
      "count_on_hand": 0,
      "stock_location_id": 84,
      "backorderable": true,
      "available": true,
      "stock_location_name": "NY Warehouse"
    }
  ],
  "prices": [
    {
      "id": 211,
      "price": "10.0",
      "vendor_id": 317,
      "display_price": "$10.00"
    },
    {
      "id": 212,
      "price": "20.0",
      "vendor_id": 318,
      "display_price": "$20.00"
    }
  ]
}
```



