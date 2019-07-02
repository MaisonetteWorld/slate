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
PUT /api/orders/R394211562/addresses/465
Accept: application/json
X-Spree-Order-Token: qbeEbRWbvwOTAV2qaJN92A
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
ETag: W/&quot;7c879a00bc24b9c420e768001328e15e&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: ecf0ddcb-38ec-4567-88b8-d2af4bcfeeb9
X-Runtime: 0.040512
Content-Length: 513
200 OK
```


```json
{
  "id": 466,
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
  "country_id": 284,
  "country_iso": "US",
  "state_id": 273,
  "state_name": null,
  "state_text": "AL",
  "country": {
    "id": 284,
    "iso_name": "UNITED STATES",
    "iso": "US",
    "iso3": "USA",
    "name": "United States",
    "numcode": 840
  },
  "state": {
    "id": 273,
    "name": "Alabama",
    "abbr": "AL",
    "country_id": 284
  }
}
```



# LineItem

Representation of a single cart item for a specific variant with price of vendor

## Creating a line item


### Request

#### Endpoint

```plaintext
POST /api/orders/R195966053/line_items
Accept: application/json
X-Spree-Order-Token: 7xbRAyPMzgPuzUzc73nC9g
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/:order_number/line_items`

#### Parameters


```json
line_item[variant_id]=588&line_item[options][vendor_id]=1943
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
ETag: W/&quot;b9b26252e3d98dd1c81ef6a86ea95ae8&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 41a32427-0db8-4331-9c7d-26aaf4a33c75
X-Runtime: 0.069796
Content-Length: 732
201 Created
```


```json
{
  "id": 214,
  "quantity": 1,
  "price": "19.99",
  "variant_id": 588,
  "vendor_id": 1943,
  "single_display_amount": "$19.99",
  "display_amount": "$19.99",
  "total": "19.99",
  "variant": {
    "id": 588,
    "name": "Product #5 - 2073",
    "sku": "SKU-7",
    "price": "19.99",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": false,
    "slug": "product-5-2073",
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
        "id": 183,
        "name": "Size-3",
        "presentation": "S",
        "option_type_name": "foo-size-3",
        "option_type_id": 183,
        "option_type_presentation": "Size"
      }
    ],
    "images": [

    ],
    "product_id": 416
  },
  "vendor_name": "Vendor #16",
  "adjustments": [

  ]
}
```



## Deleting a line item


### Request

#### Endpoint

```plaintext
DELETE /api/orders/R956639958/line_items/212
Accept: application/json
X-Spree-Order-Token: t2_faqXfxbkRhHztH2sGKg
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
X-Request-Id: 779a2bcb-e937-4382-97e3-c9eaed2af62e
X-Runtime: 0.147663
204 No Content
```




## Updating a line item


### Request

#### Endpoint

```plaintext
PUT /api/orders/R260661196/line_items/215
Accept: application/json
X-Spree-Order-Token: _bJAC3zn-foMdR4G8XNzQA
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
ETag: W/&quot;0b7bf9bb7768d187b7bb1d423822bdaa&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: ba38a305-f2d7-43ce-9df5-5705e6366fd6
X-Runtime: 0.059741
Content-Length: 590
200 OK
```


```json
{
  "id": 215,
  "quantity": 2,
  "price": "10.0",
  "variant_id": 589,
  "vendor_id": 1949,
  "single_display_amount": "$10.00",
  "display_amount": "$20.00",
  "total": "20.0",
  "variant": {
    "id": 589,
    "name": "Product #6 - 8091",
    "sku": "SKU-9",
    "price": "19.99",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": true,
    "slug": "product-6-8091",
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
    "product_id": 417
  },
  "vendor_name": "Vendor #21",
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
X-Spree-Token: dc6dc54558230414859c8ab83c335d58ac140d0708f34802
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
X-Request-Id: 300fafa5-bdce-42f8-bd8d-dfb74c2ff1e5
X-Runtime: 0.040108
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
Date: Tue, 02 Jul 2019 13:06:03 GMT
Surrogate-Control: max-age=900
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;af51f00f4125c50d130101367448fc23&quot;
X-Request-Id: 18c8d988-65c0-4b7e-9d87-f72ec80bc169
X-Runtime: 0.070040
Content-Length: 857
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
      "id": 418,
      "name": "Product #7 - 366",
      "description": "As seen on TV!",
      "price": "19.99",
      "display_price": "$19.99",
      "available_on": "2018-07-02T13:06:03.644Z",
      "slug": "product-7-366",
      "meta_description": null,
      "meta_keywords": null,
      "shipping_category_id": 242,
      "taxon_ids": [

      ],
      "total_on_hand": 0,
      "meta_title": null,
      "has_variants": false,
      "master": {
        "id": 590,
        "name": "Product #7 - 366",
        "sku": "SKU-10",
        "price": "19.99",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-7-366",
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
GET /api/products/product-8-7102
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
Date: Tue, 02 Jul 2019 13:06:03 GMT
Surrogate-Control: max-age=900
Surrogate-Key: product_id=1
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;67df1fe1f56fcd799a0d6c7ad4e200a4&quot;
X-Request-Id: 6fa94258-c3c1-4a1a-a998-0d3f4ef85e09
X-Runtime: 0.033002
Content-Length: 779
200 OK
```


```json
{
  "id": 419,
  "name": "Product #8 - 7102",
  "description": "As seen on TV!",
  "price": "19.99",
  "display_price": "$19.99",
  "available_on": "2018-07-02T13:06:03.785Z",
  "slug": "product-8-7102",
  "meta_description": null,
  "meta_keywords": null,
  "shipping_category_id": 243,
  "taxon_ids": [

  ],
  "total_on_hand": 0,
  "meta_title": null,
  "has_variants": false,
  "master": {
    "id": 591,
    "name": "Product #8 - 7102",
    "sku": "SKU-11",
    "price": "19.99",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": true,
    "slug": "product-8-7102",
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
X-Request-Id: f3e005b4-a253-41ad-a711-726a14e0259a
X-Runtime: 0.015862
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
X-Request-Id: b325adb7-9d96-4710-9813-8a5f91d3e489
X-Runtime: 0.011044
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
X-Request-Id: 6150e2c7-1a51-4b9e-8b92-cdf516e2c177
X-Runtime: 0.004203
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
X-Request-Id: bb97a481-1710-4882-b4c4-1303997e0cea
X-Runtime: 0.006704
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
X-Request-Id: 8fc0cf10-0777-4eb9-9cd5-225a2efdc0ff
X-Runtime: 0.007059
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
user[email]=email6%40example.com&user[password]=secret
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
X-Spree-Token: 83ee09dffa66815b587951969cc9bc03cd9f681363d11d58
ETag: W/&quot;b442b58d45a5dbdf29b8d1f2d66e78bb&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: d4d46832-673a-4339-90e5-b4a75bcc38a7
X-Runtime: 0.005029
Content-Length: 551
200 OK
```


```json
{
  "id": 262,
  "email": "email6@example.com",
  "persistence_token": null,
  "perishable_token": null,
  "last_request_at": null,
  "login": "email6@example.com",
  "ship_address_id": null,
  "bill_address_id": null,
  "created_at": "2019-07-02T13:06:03.627Z",
  "updated_at": "2019-07-02T13:06:03.630Z",
  "spree_api_key": "83ee09dffa66815b587951969cc9bc03cd9f681363d11d58",
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
X-Spree-Token: bbf69ea9ac2e61d0e155788288c1a8e482f91737bceb052a
ETag: W/&quot;58c0629e160234bc4b400b624a84f38b&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: ae5c0886-4a0f-4653-8288-c5dda8b437dc
X-Runtime: 0.031387
Content-Length: 157
201 Created
```


```json
{
  "id": 261,
  "email": "test@example.com",
  "created_at": "2019-07-02T13:06:03.599Z",
  "updated_at": "2019-07-02T13:06:03.601Z",
  "bill_address": null,
  "ship_address": null
}
```



# Variant



## Fetching a variant


### Request

#### Endpoint

```plaintext
GET /api/variants/582
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
ETag: W/&quot;86dbd04f46b61a9221b55ca43bcb9fe0&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 1dd95192-6e59-4a58-9256-25d2a092649a
X-Runtime: 0.226002
Content-Length: 1287
200 OK
```


```json
{
  "id": 582,
  "name": "Product #1 - 1184",
  "sku": "SKU-1",
  "price": "10.0",
  "weight": "0.0",
  "height": null,
  "width": null,
  "depth": null,
  "is_master": false,
  "slug": "product-1-1184",
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
      "id": 181,
      "name": "Size-1",
      "presentation": "S",
      "option_type_name": "foo-size-1",
      "option_type_id": 181,
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
      "attachment_updated_at": "2019-07-02T13:06:01.468Z",
      "attachment_width": 489,
      "attachment_height": 490,
      "alt": null,
      "viewable_type": "Spree::Variant",
      "viewable_id": 582,
      "mini_url": "/spree/products/2/mini/thinking-cat.jpg?1562072761",
      "small_url": "/spree/products/2/small/thinking-cat.jpg?1562072761",
      "product_url": "/spree/products/2/product/thinking-cat.jpg?1562072761",
      "large_url": "/spree/products/2/large/thinking-cat.jpg?1562072761"
    }
  ],
  "variant_properties": [

  ],
  "stock_items": [

  ],
  "prices": [
    {
      "id": 1112,
      "price": "10.0",
      "vendor_id": 1929,
      "display_price": "$10.00",
      "total_on_hand": 0
    },
    {
      "id": 1113,
      "price": "20.0",
      "vendor_id": 1930,
      "display_price": "$20.00",
      "total_on_hand": 0
    }
  ]
}
```



