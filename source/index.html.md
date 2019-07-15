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
PUT /api/orders/R871534045/addresses/560
Accept: application/json
X-Spree-Order-Token: ZuMhGrtqsKiZgYvhhKjiig
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
ETag: W/&quot;013fa4c9382f93f7bc7321e4460e8c97&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: e87f1e43-4ecd-42c9-8c2c-c673708d1cf2
X-Runtime: 0.094433
Content-Length: 513
200 OK
```


```json
{
  "id": 561,
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
  "country_id": 343,
  "country_iso": "US",
  "state_id": 332,
  "state_name": null,
  "state_text": "AL",
  "country": {
    "id": 343,
    "iso_name": "UNITED STATES",
    "iso": "US",
    "iso3": "USA",
    "name": "United States",
    "numcode": 840
  },
  "state": {
    "id": 332,
    "name": "Alabama",
    "abbr": "AL",
    "country_id": 343
  }
}
```



# Checkout



## Processing the checkout payment step


### Request

#### Endpoint

```plaintext
PATCH /api/checkouts/R760623256
Accept: application/json
X-Spree-Order-Token: nI7XdeniphVLah7GBB10CA
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=208&order[payment_attributes][][source_attributes][wallet_payment_source_id]=15
```


| Name | Description |
|:-----|:------------|
| id *required* | Order number |
| order[payment_attributes]  | Order payment attributes |
| order[payment_attributes][payment_method_id]  | Order payment attributes payment method |
| order[payment_attributes][source_attributes][nonce]  | Order payment attributes source attributes nonce |
| order[payment_attributes][source_attributes][payment_type]  | Order payment attributes source attributes payment type |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
ETag: W/&quot;75c1c87976c87dba33217ae604bd66ec&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: f0ee0df8-f751-4483-aae1-8764677b3aac
X-Runtime: 0.174592
Content-Length: 3894
200 OK
```


```json
{
  "id": 277,
  "number": "R760623256",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 325,
  "created_at": "2019-07-15T14:43:40.969Z",
  "updated_at": "2019-07-15T14:43:41.430Z",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "email10@example.com",
  "special_instructions": null,
  "channel": "spree",
  "included_tax_total": "0.0",
  "additional_tax_total": "0.0",
  "display_included_tax_total": "$0.00",
  "display_additional_tax_total": "$0.00",
  "tax_total": "0.0",
  "currency": "USD",
  "covered_by_store_credit": false,
  "display_total_applicable_store_credit": "$0.00",
  "order_total_after_store_credit": "110.0",
  "display_order_total_after_store_credit": "$110.00",
  "total_applicable_store_credit": "0.0",
  "display_total_available_store_credit": "$0.00",
  "display_store_credit_remaining_after_capture": "$0.00",
  "canceler_id": null,
  "display_item_total": "$10.00",
  "total_quantity": 1,
  "display_total": "$110.00",
  "display_ship_total": "$100.00",
  "display_tax_total": "$0.00",
  "token": "nI7XdeniphVLah7GBB10CA",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 208,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 568,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "PO Box 1337",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10009",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 350,
    "country_iso": "US",
    "state_id": 339,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 350,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 339,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 350
    }
  },
  "ship_address": {
    "id": 569,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "A Different Road",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10010",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 350,
    "country_iso": "US",
    "state_id": 339,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 350,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 339,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 350
    }
  },
  "line_items": [
    {
      "id": 265,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 704,
      "vendor_id": 2317,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "variant": {
        "id": 704,
        "name": "Product #9 - 826",
        "sku": "SKU-11",
        "price": "10.0",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-9-826",
        "description": "As seen on TV!",
        "track_inventory": true,
        "display_price": "$10.00",
        "options_text": "Size: S",
        "in_stock": true,
        "is_backorderable": true,
        "total_on_hand": 10,
        "is_destroyed": false,
        "option_values": [
          {
            "id": 230,
            "name": "Size-3",
            "presentation": "S",
            "option_type_name": "foo-size-3",
            "option_type_id": 230,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 486
      },
      "vendor_name": "Vendor #26",
      "adjustments": [

      ]
    }
  ],
  "payments": [

  ],
  "shipments": [
    {
      "id": 226,
      "tracking": null,
      "tracking_url": null,
      "number": "H00402561107",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R760623256",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 227,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 209,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 227,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 209,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 209,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 143,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 301,
              "name": "ShippingCategory #7"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 704,
          "quantity": 1,
          "states": {
            "on_hand": 1
          }
        }
      ],
      "adjustments": [

      ]
    }
  ],
  "adjustments": [

  ],
  "permissions": {
    "can_update": false
  },
  "credit_cards": [

  ]
}
```



## Processing the checkout payment step


### Request

#### Endpoint

```plaintext
PATCH /api/checkouts/R594769436
Accept: application/json
X-Spree-Order-Token: o8KwFUlyDV5wwKphXzTrlQ
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=209&order[payment_attributes][][source_attributes][nonce]=fake-apple-pay-visa-nonce&order[payment_attributes][][source_attributes][payment_type]=ApplePayCard
```


| Name | Description |
|:-----|:------------|
| id *required* | Order number |
| order[payment_attributes]  | Order payment attributes |
| order[payment_attributes][payment_method_id]  | Order payment attributes payment method |
| order[payment_attributes][source_attributes][nonce]  | Order payment attributes source attributes nonce |
| order[payment_attributes][source_attributes][payment_type]  | Order payment attributes source attributes payment type |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
ETag: W/&quot;5a1e2317db40587b15d817cf614c4f7e&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: bff40044-9f52-43dd-8e77-2b02964834f2
X-Runtime: 0.125209
Content-Length: 3898
200 OK
```


```json
{
  "id": 278,
  "number": "R594769436",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 326,
  "created_at": "2019-07-15T14:43:41.808Z",
  "updated_at": "2019-07-15T14:43:42.096Z",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "email11@example.com",
  "special_instructions": null,
  "channel": "spree",
  "included_tax_total": "0.0",
  "additional_tax_total": "0.0",
  "display_included_tax_total": "$0.00",
  "display_additional_tax_total": "$0.00",
  "tax_total": "0.0",
  "currency": "USD",
  "covered_by_store_credit": false,
  "display_total_applicable_store_credit": "$0.00",
  "order_total_after_store_credit": "110.0",
  "display_order_total_after_store_credit": "$110.00",
  "total_applicable_store_credit": "0.0",
  "display_total_available_store_credit": "$0.00",
  "display_store_credit_remaining_after_capture": "$0.00",
  "canceler_id": null,
  "display_item_total": "$10.00",
  "total_quantity": 1,
  "display_total": "$110.00",
  "display_ship_total": "$100.00",
  "display_tax_total": "$0.00",
  "token": "o8KwFUlyDV5wwKphXzTrlQ",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 209,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 570,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "PO Box 1337",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10011",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 351,
    "country_iso": "US",
    "state_id": 340,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 351,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 340,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 351
    }
  },
  "ship_address": {
    "id": 571,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "A Different Road",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10012",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 351,
    "country_iso": "US",
    "state_id": 340,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 351,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 340,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 351
    }
  },
  "line_items": [
    {
      "id": 266,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 706,
      "vendor_id": 2323,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "variant": {
        "id": 706,
        "name": "Product #10 - 8308",
        "sku": "SKU-13",
        "price": "10.0",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-10-8308",
        "description": "As seen on TV!",
        "track_inventory": true,
        "display_price": "$10.00",
        "options_text": "Size: S",
        "in_stock": true,
        "is_backorderable": true,
        "total_on_hand": 10,
        "is_destroyed": false,
        "option_values": [
          {
            "id": 231,
            "name": "Size-4",
            "presentation": "S",
            "option_type_name": "foo-size-4",
            "option_type_id": 231,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 487
      },
      "vendor_name": "Vendor #31",
      "adjustments": [

      ]
    }
  ],
  "payments": [

  ],
  "shipments": [
    {
      "id": 228,
      "tracking": null,
      "tracking_url": null,
      "number": "H66086425526",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R594769436",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 229,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 210,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 229,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 210,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 210,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 144,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 302,
              "name": "ShippingCategory #8"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 706,
          "quantity": 1,
          "states": {
            "on_hand": 1
          }
        }
      ],
      "adjustments": [

      ]
    }
  ],
  "adjustments": [

  ],
  "permissions": {
    "can_update": false
  },
  "credit_cards": [

  ]
}
```



## Processing the checkout payment step


### Request

#### Endpoint

```plaintext
PATCH /api/checkouts/R246692294
Accept: application/json
X-Spree-Order-Token: gDl1o2fzJqEqkAG0KxMWkw
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=210&order[payment_attributes][][source_attributes][nonce]=fake-paypal-billing-agreement-nonce&order[payment_attributes][][source_attributes][payment_type]=PayPalAccount
```


| Name | Description |
|:-----|:------------|
| id *required* | Order number |
| order[payment_attributes]  | Order payment attributes |
| order[payment_attributes][payment_method_id]  | Order payment attributes payment method |
| order[payment_attributes][source_attributes][nonce]  | Order payment attributes source attributes nonce |
| order[payment_attributes][source_attributes][payment_type]  | Order payment attributes source attributes payment type |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
ETag: W/&quot;9e010272583ff1f319a4f79ace03b88c&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 9a5c4c97-e5c3-4039-9fa5-0899d68c7c8d
X-Runtime: 0.114069
Content-Length: 3898
200 OK
```


```json
{
  "id": 279,
  "number": "R246692294",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 327,
  "created_at": "2019-07-15T14:43:42.448Z",
  "updated_at": "2019-07-15T14:43:42.760Z",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "email12@example.com",
  "special_instructions": null,
  "channel": "spree",
  "included_tax_total": "0.0",
  "additional_tax_total": "0.0",
  "display_included_tax_total": "$0.00",
  "display_additional_tax_total": "$0.00",
  "tax_total": "0.0",
  "currency": "USD",
  "covered_by_store_credit": false,
  "display_total_applicable_store_credit": "$0.00",
  "order_total_after_store_credit": "110.0",
  "display_order_total_after_store_credit": "$110.00",
  "total_applicable_store_credit": "0.0",
  "display_total_available_store_credit": "$0.00",
  "display_store_credit_remaining_after_capture": "$0.00",
  "canceler_id": null,
  "display_item_total": "$10.00",
  "total_quantity": 1,
  "display_total": "$110.00",
  "display_ship_total": "$100.00",
  "display_tax_total": "$0.00",
  "token": "gDl1o2fzJqEqkAG0KxMWkw",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 210,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 572,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "PO Box 1337",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10013",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 352,
    "country_iso": "US",
    "state_id": 341,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 352,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 341,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 352
    }
  },
  "ship_address": {
    "id": 573,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "A Different Road",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10014",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 352,
    "country_iso": "US",
    "state_id": 341,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 352,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 341,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 352
    }
  },
  "line_items": [
    {
      "id": 267,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 708,
      "vendor_id": 2329,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "variant": {
        "id": 708,
        "name": "Product #11 - 6789",
        "sku": "SKU-15",
        "price": "10.0",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-11-6789",
        "description": "As seen on TV!",
        "track_inventory": true,
        "display_price": "$10.00",
        "options_text": "Size: S",
        "in_stock": true,
        "is_backorderable": true,
        "total_on_hand": 10,
        "is_destroyed": false,
        "option_values": [
          {
            "id": 232,
            "name": "Size-5",
            "presentation": "S",
            "option_type_name": "foo-size-5",
            "option_type_id": 232,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 488
      },
      "vendor_name": "Vendor #36",
      "adjustments": [

      ]
    }
  ],
  "payments": [

  ],
  "shipments": [
    {
      "id": 230,
      "tracking": null,
      "tracking_url": null,
      "number": "H68704825623",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R246692294",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 231,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 211,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 231,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 211,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 211,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 145,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 303,
              "name": "ShippingCategory #9"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 708,
          "quantity": 1,
          "states": {
            "on_hand": 1
          }
        }
      ],
      "adjustments": [

      ]
    }
  ],
  "adjustments": [

  ],
  "permissions": {
    "can_update": false
  },
  "credit_cards": [

  ]
}
```



## Processing the checkout payment step


### Request

#### Endpoint

```plaintext
PATCH /api/checkouts/R909378584
Accept: application/json
X-Spree-Order-Token: sT5EXWPE_zWsMYEHap0hqg
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=211&order[payment_attributes][][source_attributes][wallet_payment_source_id]=16
```


| Name | Description |
|:-----|:------------|
| id *required* | Order number |
| order[payment_attributes]  | Order payment attributes |
| order[payment_attributes][payment_method_id]  | Order payment attributes payment method |
| order[payment_attributes][source_attributes][nonce]  | Order payment attributes source attributes nonce |
| order[payment_attributes][source_attributes][payment_type]  | Order payment attributes source attributes payment type |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
ETag: W/&quot;92172b723d5bb5331a351eba8f3b320b&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 678b67e7-4ac4-4c5b-807c-29c10977689e
X-Runtime: 0.088031
Content-Length: 3899
200 OK
```


```json
{
  "id": 280,
  "number": "R909378584",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 328,
  "created_at": "2019-07-15T14:43:43.071Z",
  "updated_at": "2019-07-15T14:43:43.304Z",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "email13@example.com",
  "special_instructions": null,
  "channel": "spree",
  "included_tax_total": "0.0",
  "additional_tax_total": "0.0",
  "display_included_tax_total": "$0.00",
  "display_additional_tax_total": "$0.00",
  "tax_total": "0.0",
  "currency": "USD",
  "covered_by_store_credit": false,
  "display_total_applicable_store_credit": "$0.00",
  "order_total_after_store_credit": "110.0",
  "display_order_total_after_store_credit": "$110.00",
  "total_applicable_store_credit": "0.0",
  "display_total_available_store_credit": "$0.00",
  "display_store_credit_remaining_after_capture": "$0.00",
  "canceler_id": null,
  "display_item_total": "$10.00",
  "total_quantity": 1,
  "display_total": "$110.00",
  "display_ship_total": "$100.00",
  "display_tax_total": "$0.00",
  "token": "sT5EXWPE_zWsMYEHap0hqg",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 211,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 574,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "PO Box 1337",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10015",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 353,
    "country_iso": "US",
    "state_id": 342,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 353,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 342,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 353
    }
  },
  "ship_address": {
    "id": 575,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "A Different Road",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10016",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 353,
    "country_iso": "US",
    "state_id": 342,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 353,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 342,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 353
    }
  },
  "line_items": [
    {
      "id": 268,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 710,
      "vendor_id": 2335,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "variant": {
        "id": 710,
        "name": "Product #12 - 2508",
        "sku": "SKU-17",
        "price": "10.0",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-12-2508",
        "description": "As seen on TV!",
        "track_inventory": true,
        "display_price": "$10.00",
        "options_text": "Size: S",
        "in_stock": true,
        "is_backorderable": true,
        "total_on_hand": 10,
        "is_destroyed": false,
        "option_values": [
          {
            "id": 233,
            "name": "Size-6",
            "presentation": "S",
            "option_type_name": "foo-size-6",
            "option_type_id": 233,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 489
      },
      "vendor_name": "Vendor #41",
      "adjustments": [

      ]
    }
  ],
  "payments": [

  ],
  "shipments": [
    {
      "id": 232,
      "tracking": null,
      "tracking_url": null,
      "number": "H72418625265",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R909378584",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 233,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 212,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 233,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 212,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 212,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 146,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 304,
              "name": "ShippingCategory #10"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 710,
          "quantity": 1,
          "states": {
            "on_hand": 1
          }
        }
      ],
      "adjustments": [

      ]
    }
  ],
  "adjustments": [

  ],
  "permissions": {
    "can_update": false
  },
  "credit_cards": [

  ]
}
```



## Processing the checkout payment step


### Request

#### Endpoint

```plaintext
PATCH /api/checkouts/R145003613
Accept: application/json
X-Spree-Order-Token: cwsZ-jDN3Rc3BKtLGWWhHw
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=212&order[payment_attributes][][source_attributes][wallet_payment_source_id]=17
```


| Name | Description |
|:-----|:------------|
| id *required* | Order number |
| order[payment_attributes]  | Order payment attributes |
| order[payment_attributes][payment_method_id]  | Order payment attributes payment method |
| order[payment_attributes][source_attributes][nonce]  | Order payment attributes source attributes nonce |
| order[payment_attributes][source_attributes][payment_type]  | Order payment attributes source attributes payment type |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
ETag: W/&quot;728dfaf51b175a327d170e50a30f0e2d&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 3ca72e77-d964-49df-a293-f57080065100
X-Runtime: 0.116044
Content-Length: 3899
200 OK
```


```json
{
  "id": 281,
  "number": "R145003613",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 329,
  "created_at": "2019-07-15T14:43:43.603Z",
  "updated_at": "2019-07-15T14:43:43.882Z",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "email14@example.com",
  "special_instructions": null,
  "channel": "spree",
  "included_tax_total": "0.0",
  "additional_tax_total": "0.0",
  "display_included_tax_total": "$0.00",
  "display_additional_tax_total": "$0.00",
  "tax_total": "0.0",
  "currency": "USD",
  "covered_by_store_credit": false,
  "display_total_applicable_store_credit": "$0.00",
  "order_total_after_store_credit": "110.0",
  "display_order_total_after_store_credit": "$110.00",
  "total_applicable_store_credit": "0.0",
  "display_total_available_store_credit": "$0.00",
  "display_store_credit_remaining_after_capture": "$0.00",
  "canceler_id": null,
  "display_item_total": "$10.00",
  "total_quantity": 1,
  "display_total": "$110.00",
  "display_ship_total": "$100.00",
  "display_tax_total": "$0.00",
  "token": "cwsZ-jDN3Rc3BKtLGWWhHw",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 212,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 576,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "PO Box 1337",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10017",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 354,
    "country_iso": "US",
    "state_id": 343,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 354,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 343,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 354
    }
  },
  "ship_address": {
    "id": 577,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "A Different Road",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10018",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 354,
    "country_iso": "US",
    "state_id": 343,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 354,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 343,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 354
    }
  },
  "line_items": [
    {
      "id": 269,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 712,
      "vendor_id": 2341,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "variant": {
        "id": 712,
        "name": "Product #13 - 1259",
        "sku": "SKU-19",
        "price": "10.0",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-13-1259",
        "description": "As seen on TV!",
        "track_inventory": true,
        "display_price": "$10.00",
        "options_text": "Size: S",
        "in_stock": true,
        "is_backorderable": true,
        "total_on_hand": 10,
        "is_destroyed": false,
        "option_values": [
          {
            "id": 234,
            "name": "Size-7",
            "presentation": "S",
            "option_type_name": "foo-size-7",
            "option_type_id": 234,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 490
      },
      "vendor_name": "Vendor #46",
      "adjustments": [

      ]
    }
  ],
  "payments": [

  ],
  "shipments": [
    {
      "id": 234,
      "tracking": null,
      "tracking_url": null,
      "number": "H62027036131",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R145003613",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 235,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 213,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 235,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 213,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 213,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 147,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 305,
              "name": "ShippingCategory #11"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 712,
          "quantity": 1,
          "states": {
            "on_hand": 1
          }
        }
      ],
      "adjustments": [

      ]
    }
  ],
  "adjustments": [

  ],
  "permissions": {
    "can_update": false
  },
  "credit_cards": [

  ]
}
```



## Processing the checkout payment step


### Request

#### Endpoint

```plaintext
PATCH /api/checkouts/R828762904
Accept: application/json
X-Spree-Order-Token: G_o3UTLU2O8OAw5NTma4pQ
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=213&order[payment_attributes][][source_attributes][nonce]=fake-valid-visa-nonce&order[payment_attributes][][source_attributes][payment_type]=CreditCard
```


| Name | Description |
|:-----|:------------|
| id *required* | Order number |
| order[payment_attributes]  | Order payment attributes |
| order[payment_attributes][payment_method_id]  | Order payment attributes payment method |
| order[payment_attributes][source_attributes][nonce]  | Order payment attributes source attributes nonce |
| order[payment_attributes][source_attributes][payment_type]  | Order payment attributes source attributes payment type |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
ETag: W/&quot;73169cb6170489bd70d7ff362693e7b7&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 8722090d-ee41-49b3-9704-2f5a88530417
X-Runtime: 0.116420
Content-Length: 3899
200 OK
```


```json
{
  "id": 282,
  "number": "R828762904",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 330,
  "created_at": "2019-07-15T14:43:44.203Z",
  "updated_at": "2019-07-15T14:43:44.504Z",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "email15@example.com",
  "special_instructions": null,
  "channel": "spree",
  "included_tax_total": "0.0",
  "additional_tax_total": "0.0",
  "display_included_tax_total": "$0.00",
  "display_additional_tax_total": "$0.00",
  "tax_total": "0.0",
  "currency": "USD",
  "covered_by_store_credit": false,
  "display_total_applicable_store_credit": "$0.00",
  "order_total_after_store_credit": "110.0",
  "display_order_total_after_store_credit": "$110.00",
  "total_applicable_store_credit": "0.0",
  "display_total_available_store_credit": "$0.00",
  "display_store_credit_remaining_after_capture": "$0.00",
  "canceler_id": null,
  "display_item_total": "$10.00",
  "total_quantity": 1,
  "display_total": "$110.00",
  "display_ship_total": "$100.00",
  "display_tax_total": "$0.00",
  "token": "G_o3UTLU2O8OAw5NTma4pQ",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 213,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 578,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "PO Box 1337",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10019",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 355,
    "country_iso": "US",
    "state_id": 344,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 355,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 344,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 355
    }
  },
  "ship_address": {
    "id": 579,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "A Different Road",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10020",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 355,
    "country_iso": "US",
    "state_id": 344,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 355,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 344,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 355
    }
  },
  "line_items": [
    {
      "id": 270,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 714,
      "vendor_id": 2347,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "variant": {
        "id": 714,
        "name": "Product #14 - 4179",
        "sku": "SKU-21",
        "price": "10.0",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-14-4179",
        "description": "As seen on TV!",
        "track_inventory": true,
        "display_price": "$10.00",
        "options_text": "Size: S",
        "in_stock": true,
        "is_backorderable": true,
        "total_on_hand": 10,
        "is_destroyed": false,
        "option_values": [
          {
            "id": 235,
            "name": "Size-8",
            "presentation": "S",
            "option_type_name": "foo-size-8",
            "option_type_id": 235,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 491
      },
      "vendor_name": "Vendor #51",
      "adjustments": [

      ]
    }
  ],
  "payments": [

  ],
  "shipments": [
    {
      "id": 236,
      "tracking": null,
      "tracking_url": null,
      "number": "H47266533428",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R828762904",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 237,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 214,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 237,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 214,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 214,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 148,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 306,
              "name": "ShippingCategory #12"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 714,
          "quantity": 1,
          "states": {
            "on_hand": 1
          }
        }
      ],
      "adjustments": [

      ]
    }
  ],
  "adjustments": [

  ],
  "permissions": {
    "can_update": false
  },
  "credit_cards": [

  ]
}
```



# LineItem

Representation of a single cart item for a specific variant with price of vendor

## Creating a line item


### Request

#### Endpoint

```plaintext
POST /api/orders/R591954018/line_items
Accept: application/json
X-Spree-Order-Token: K1LFQdDKGcay2rI6m2wMaQ
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/:order_number/line_items`

#### Parameters


```json
line_item[variant_id]=701&line_item[options][vendor_id]=2308
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
ETag: W/&quot;c2841ad50a70a95a3c26c052913a82ce&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 3c9f7c8a-c32b-483a-a73b-33a4d73c9675
X-Runtime: 0.104454
Content-Length: 732
201 Created
```


```json
{
  "id": 263,
  "quantity": 1,
  "price": "19.99",
  "variant_id": 701,
  "vendor_id": 2308,
  "single_display_amount": "$19.99",
  "display_amount": "$19.99",
  "total": "19.99",
  "variant": {
    "id": 701,
    "name": "Product #7 - 5557",
    "sku": "SKU-8",
    "price": "19.99",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": false,
    "slug": "product-7-5557",
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
        "id": 229,
        "name": "Size-2",
        "presentation": "S",
        "option_type_name": "foo-size-2",
        "option_type_id": 229,
        "option_type_presentation": "Size"
      }
    ],
    "images": [

    ],
    "product_id": 484
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
DELETE /api/orders/R813795424/line_items/261
Accept: application/json
X-Spree-Order-Token: UDrhYkNewJ3b_ATIcT934g
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
X-Request-Id: e943b5b9-a1e8-4353-a41b-0f5949a8638e
X-Runtime: 0.109644
204 No Content
```




## Updating a line item


### Request

#### Endpoint

```plaintext
PUT /api/orders/R916267134/line_items/264
Accept: application/json
X-Spree-Order-Token: Du7DR9zu70juQAu-bz4vtA
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
ETag: W/&quot;faa7fb9a4759b578be57071815593987&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 4142917b-0bbb-43bc-8a25-22903597069f
X-Runtime: 0.102615
Content-Length: 591
200 OK
```


```json
{
  "id": 264,
  "quantity": 2,
  "price": "10.0",
  "variant_id": 702,
  "vendor_id": 2314,
  "single_display_amount": "$10.00",
  "display_amount": "$20.00",
  "total": "20.0",
  "variant": {
    "id": 702,
    "name": "Product #8 - 8643",
    "sku": "SKU-10",
    "price": "19.99",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": true,
    "slug": "product-8-8643",
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
    "product_id": 485
  },
  "vendor_name": "Vendor #23",
  "adjustments": [

  ]
}
```



# Navigation



## Returns navigation taxons


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
ETag: W/&quot;3ab86540662fa655bc3b46ced4078b17&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: ddbeaf32-90ed-41d9-89b1-a808b6fe44fb
X-Runtime: 0.012539
Content-Length: 134
200 OK
```


```json
[
  {
    "id": 599,
    "name": "Kids",
    "navigation_url": "/navigation/kids",
    "parent_id": 598,
    "lft": 2,
    "depth": 1,
    "highlight": false,
    "header_link": false
  }
]
```



# Orders



## Get my orders


### Request

#### Endpoint

```plaintext
GET /api/orders/mine
X-Spree-Token: ea1d8aab2414dc197f4b139b895f259331ab9eab6c1d806c
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
X-Request-Id: 497126ac-d49e-4fa9-9576-3ebc79abf918
X-Runtime: 0.019051
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
Date: Mon, 15 Jul 2019 14:43:38 GMT
Surrogate-Control: max-age=900
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;914558b81cbd330dea1e53475d4142ce&quot;
X-Request-Id: d15cd8c6-3f33-4b38-a8ca-5bbc5e2c99f0
X-Runtime: 0.161698
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
      "id": 478,
      "name": "Product #1 - 9398",
      "description": "As seen on TV!",
      "price": "19.99",
      "display_price": "$19.99",
      "available_on": "2018-07-15T14:43:38.030Z",
      "slug": "product-1-9398",
      "meta_description": null,
      "meta_keywords": null,
      "shipping_category_id": 295,
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
        "id": 693,
        "name": "Product #1 - 9398",
        "sku": "SKU-1",
        "price": "19.99",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-1-9398",
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
GET /api/products/product-2-4966
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
Date: Mon, 15 Jul 2019 14:43:38 GMT
Surrogate-Control: max-age=900
Surrogate-Key: product_id=1
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;0483bf7a3fa48f83b91bfd9bcadee39e&quot;
X-Request-Id: 462d3a45-8fe2-4b42-bc8b-448fe90d5b9c
X-Runtime: 0.086376
Content-Length: 828
200 OK
```


```json
{
  "id": 479,
  "name": "Product #2 - 4966",
  "description": "As seen on TV!",
  "price": "19.99",
  "display_price": "$19.99",
  "available_on": "2018-07-15T14:43:38.501Z",
  "slug": "product-2-4966",
  "meta_description": null,
  "meta_keywords": null,
  "shipping_category_id": 296,
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
    "id": 694,
    "name": "Product #2 - 4966",
    "sku": "SKU-2",
    "price": "19.99",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": true,
    "slug": "product-2-4966",
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
X-Request-Id: 17e9afad-e1d4-4c3d-a180-19df33b870e6
X-Runtime: 0.024002
Content-Length: 65
404 Not Found
```


```json
{
  "error": "The resource you were looking for could not be found."
}
```



# Store Credits API

Get user store_credits and current account balance for the current user

## returns a 200


### Request

#### Endpoint

```plaintext
GET api/store_credits/mine
X-Spree-Token: 5e46a278015ed1d915da0455cac3ccd8f6d2004c10997790
Accept: application/json
Host: example.org
Cookie: 
```

`GET api/store_credits/mine`

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
ETag: W/&quot;e923cb2372edf7a399aab7952839ea52&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: e10594d4-619c-4024-bd4e-127cd5967e2e
X-Runtime: 0.035880
Content-Length: 213
200 OK
```


```json
{
  "store_credits": [
    {
      "amount": "150.0",
      "amount_used": "0.0",
      "category": "Exchange",
      "created_at": "2019-07-15T14:43:39.020Z"
    }
  ],
  "current_balance": "150.0",
  "count": 1,
  "total_count": 1,
  "current_page": 1,
  "pages": 1,
  "per_page": 25
}
```



# Users

Validate user email and password. Does not handle any session and only return the user

## Gets the user account information


### Request

#### Endpoint

```plaintext
GET /api/users/mine
X-Spree-Token: 0882218809a2b994c9269c428396c61494e6f1ab9a829fab
Accept: application/json
Host: example.org
Cookie: 
```

`GET /api/users/mine`

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
X-Spree-Token: 0882218809a2b994c9269c428396c61494e6f1ab9a829fab
ETag: W/&quot;61144d602dd8edc372a45a12d47cc498&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: be691592-72bf-4ac8-a665-1e9a565751bc
X-Runtime: 0.061864
Content-Length: 98
200 OK
```


```json
{
  "email": "email2@example.com",
  "full_name": null,
  "subscribed?": null,
  "addresses": [

  ],
  "creditcards": [

  ]
}
```



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
user[email]=email1%40example.com&user[password]=secret
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
X-Spree-Token: 7343e7fe3aed0b64a99c32d2b722275f30bc4202db7631fe
ETag: W/&quot;a564b4cca6f65d6437858fed481799c7&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 8ff10c0c-fd28-4dbb-a4b3-0be07f2ea10f
X-Runtime: 0.109555
Content-Length: 551
200 OK
```


```json
{
  "id": 315,
  "email": "email1@example.com",
  "persistence_token": null,
  "perishable_token": null,
  "last_request_at": null,
  "login": "email1@example.com",
  "ship_address_id": null,
  "bill_address_id": null,
  "created_at": "2019-07-15T14:43:37.388Z",
  "updated_at": "2019-07-15T14:43:37.394Z",
  "spree_api_key": "7343e7fe3aed0b64a99c32d2b722275f30bc4202db7631fe",
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
X-Spree-Token: 8e4df6878ddbd783c77d09d3c08b79108bd73c0900fdd225
ETag: W/&quot;47dd60b69db710722555394257a2627a&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 862810dd-6ca8-43a5-9183-17e7d722b621
X-Runtime: 0.048503
Content-Length: 157
201 Created
```


```json
{
  "id": 317,
  "email": "test@example.com",
  "created_at": "2019-07-15T14:43:37.651Z",
  "updated_at": "2019-07-15T14:43:37.652Z",
  "bill_address": null,
  "ship_address": null
}
```



# Variant



## Fetching a variant


### Request

#### Endpoint

```plaintext
GET /api/variants/716
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
ETag: W/&quot;55382f8ba7ac9dabd61c5d45cf4eab16&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 4df25d7e-402e-4a27-a4c9-12f19cb4b389
X-Runtime: 0.105866
Content-Length: 1380
200 OK
```


```json
{
  "id": 716,
  "name": "Product #15 - 2841",
  "sku": "SKU-23",
  "price": "10.0",
  "weight": "0.0",
  "height": null,
  "width": null,
  "depth": null,
  "is_master": false,
  "slug": "product-15-2841",
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
      "id": 236,
      "name": "Size-9",
      "presentation": "S",
      "option_type_name": "foo-size-9",
      "option_type_id": 236,
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
      "attachment_updated_at": "2019-07-15T14:43:44.841Z",
      "attachment_width": 489,
      "attachment_height": 490,
      "alt": null,
      "viewable_type": "Spree::Variant",
      "viewable_id": 716,
      "mini_url": "/spree/products/2/mini/thinking-cat.jpg?1563201824",
      "small_url": "/spree/products/2/small/thinking-cat.jpg?1563201824",
      "product_url": "/spree/products/2/product/thinking-cat.jpg?1563201824",
      "large_url": "/spree/products/2/large/thinking-cat.jpg?1563201824"
    }
  ],
  "variant_properties": [

  ],
  "stock_items": [

  ],
  "prices": [
    {
      "id": 1391,
      "price": "10.0",
      "vendor_id": 2356,
      "display_price": "$10.00",
      "total_on_hand": 0,
      "country_iso": null,
      "final_sale": false
    },
    {
      "id": 1392,
      "price": "20.0",
      "vendor_id": 2357,
      "display_price": "$20.00",
      "total_on_hand": 0,
      "country_iso": null,
      "final_sale": false
    }
  ]
}
```



