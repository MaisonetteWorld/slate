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
PUT /api/orders/R587604000/addresses/277
Accept: application/json
X-Spree-Order-Token: uv_oNLEsNtX0pbXPmbc6MQ
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
ETag: W/&quot;c8846c66f4548ff98246e85148732284&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: f6418c36-04f8-4dda-bb85-bf810472b1b2
X-Runtime: 0.041157
Content-Length: 513
200 OK
```


```json
{
  "id": 278,
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
  "country_id": 240,
  "country_iso": "US",
  "state_id": 229,
  "state_name": null,
  "state_text": "AL",
  "country": {
    "id": 240,
    "iso_name": "UNITED STATES",
    "iso": "US",
    "iso3": "USA",
    "name": "United States",
    "numcode": 840
  },
  "state": {
    "id": 229,
    "name": "Alabama",
    "abbr": "AL",
    "country_id": 240
  }
}
```



# LineItem

Representation of a single cart item for a specific variant with price of vendor

## Creating a line item


### Request

#### Endpoint

```plaintext
POST /api/orders/R101729752/line_items
Accept: application/json
X-Spree-Order-Token: CztSv3cndJpmCzOMANJpeg
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/:order_number/line_items`

#### Parameters


```json
line_item[variant_id]=480&line_item[options][vendor_id]=1582
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
ETag: W/&quot;cb2a69269e92beb66252b12ccf559733&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 51fb489c-6c00-415e-a2a9-42c72305348a
X-Runtime: 0.180621
Content-Length: 732
201 Created
```


```json
{
  "id": 123,
  "quantity": 1,
  "price": "19.99",
  "variant_id": 480,
  "vendor_id": 1582,
  "single_display_amount": "$19.99",
  "display_amount": "$19.99",
  "total": "19.99",
  "variant": {
    "id": 480,
    "name": "Product #7 - 1849",
    "sku": "SKU-9",
    "price": "19.99",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": false,
    "slug": "product-7-1849",
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
    "product_id": 318
  },
  "vendor_name": "Vendor #22",
  "adjustments": [

  ]
}
```



## Deleting a line item


### Request

#### Endpoint

```plaintext
DELETE /api/orders/R415939772/line_items/124
Accept: application/json
X-Spree-Order-Token: ab_06kwJ2aVLEcEhGyFF_w
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
X-Request-Id: 29178dd1-cfd2-4eda-a100-852acde79c4e
X-Runtime: 0.047480
204 No Content
```




## Updating a line item


### Request

#### Endpoint

```plaintext
PUT /api/orders/R278954416/line_items/125
Accept: application/json
X-Spree-Order-Token: zc3IFsrmWp_FJ-AMbwI2XQ
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
ETag: W/&quot;6266cc32c001b7068faf7ad801962979&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: a03f6dc4-4914-4780-8c07-a652af943123
X-Runtime: 0.059681
Content-Length: 591
200 OK
```


```json
{
  "id": 125,
  "quantity": 2,
  "price": "10.0",
  "variant_id": 482,
  "vendor_id": 1592,
  "single_display_amount": "$10.00",
  "display_amount": "$20.00",
  "total": "20.0",
  "variant": {
    "id": 482,
    "name": "Product #9 - 1607",
    "sku": "SKU-12",
    "price": "19.99",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": true,
    "slug": "product-9-1607",
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
    "product_id": 320
  },
  "vendor_name": "Vendor #30",
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
Date: Tue, 25 Jun 2019 14:54:51 GMT
Surrogate-Control: max-age=900
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;e9d878c35ae97475045ac97fac0e4add&quot;
X-Request-Id: 068e5c07-dc9f-4388-98c5-3f01d292afd9
X-Runtime: 0.085948
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
      "id": 313,
      "name": "Product #2 - 2497",
      "description": "As seen on TV!",
      "price": "19.99",
      "display_price": "$19.99",
      "available_on": "2018-06-25T14:54:51.593Z",
      "slug": "product-2-2497",
      "meta_description": null,
      "meta_keywords": null,
      "shipping_category_id": 196,
      "taxon_ids": [

      ],
      "total_on_hand": 0,
      "meta_title": null,
      "has_variants": false,
      "master": {
        "id": 473,
        "name": "Product #2 - 2497",
        "sku": "SKU-3",
        "price": "19.99",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-2-2497",
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
GET /api/products/product-3-6938
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
Date: Tue, 25 Jun 2019 14:54:51 GMT
Surrogate-Control: max-age=900
Surrogate-Key: product_id=1
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;04e2cf5770a0026d6be41175d80fc044&quot;
X-Request-Id: 0f44ca18-24ad-47ee-b7bb-b6945f008eb4
X-Runtime: 0.029303
Content-Length: 778
200 OK
```


```json
{
  "id": 314,
  "name": "Product #3 - 6938",
  "description": "As seen on TV!",
  "price": "19.99",
  "display_price": "$19.99",
  "available_on": "2018-06-25T14:54:51.753Z",
  "slug": "product-3-6938",
  "meta_description": null,
  "meta_keywords": null,
  "shipping_category_id": 197,
  "taxon_ids": [

  ],
  "total_on_hand": 0,
  "meta_title": null,
  "has_variants": false,
  "master": {
    "id": 474,
    "name": "Product #3 - 6938",
    "sku": "SKU-4",
    "price": "19.99",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": true,
    "slug": "product-3-6938",
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
X-Request-Id: 275bd2ae-ecc2-40ab-a92e-2768f865fc6c
X-Runtime: 0.014745
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
X-Request-Id: ec22d2ce-235f-411c-9caf-1d0b67b4b7a7
X-Runtime: 0.010068
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
X-Request-Id: f3d6d265-d7b5-44ce-91bc-c35a4d1b04fd
X-Runtime: 0.004153
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
X-Request-Id: b1e7b491-f458-44ac-a096-6915b8500738
X-Runtime: 0.006906
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
X-Request-Id: 902fe975-54cc-4f8f-9363-589bcf79e67a
X-Runtime: 0.008082
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
GET /api/variants/472
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
ETag: W/&quot;9bd1a802b45e5a3ebb477f419a175919&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 9918f2ea-6417-42b9-960f-15f511e249ca
X-Runtime: 0.220412
Content-Length: 1283
200 OK
```


```json
{
  "id": 472,
  "name": "Product #1 - 216",
  "sku": "SKU-1",
  "price": "10.0",
  "weight": "0.0",
  "height": null,
  "width": null,
  "depth": null,
  "is_master": false,
  "slug": "product-1-216",
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
      "attachment_updated_at": "2019-06-25T14:54:50.949Z",
      "attachment_width": 489,
      "attachment_height": 490,
      "alt": null,
      "viewable_type": "Spree::Variant",
      "viewable_id": 472,
      "mini_url": "/spree/products/2/mini/thinking-cat.jpg?1561474490",
      "small_url": "/spree/products/2/small/thinking-cat.jpg?1561474490",
      "product_url": "/spree/products/2/product/thinking-cat.jpg?1561474490",
      "large_url": "/spree/products/2/large/thinking-cat.jpg?1561474490"
    }
  ],
  "variant_properties": [

  ],
  "stock_items": [

  ],
  "prices": [
    {
      "id": 902,
      "price": "10.0",
      "vendor_id": 1560,
      "display_price": "$10.00",
      "total_on_hand": 0
    },
    {
      "id": 903,
      "price": "20.0",
      "vendor_id": 1561,
      "display_price": "$20.00",
      "total_on_hand": 0
    }
  ]
}
```



