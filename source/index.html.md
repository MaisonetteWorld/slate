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
PUT /api/orders/R939740239/addresses/596
Accept: application/json
X-Spree-Order-Token: pUcEsORmfh2JGsJ1WrAk2w
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
ETag: W/&quot;0f212e21c56f8de7ca36718efdacfd2d&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: eba0fe25-fd80-4de4-9b6e-c12ebda72d7f
X-Runtime: 0.041564
Content-Length: 513
200 OK
```


```json
{
  "id": 597,
  "firstname": "John the Tester",
  "lastname": null,
  "full_name": "John the Tester",
  "address1": "A Different Road",
  "address2": "Northwest",
  "city": "Herndon",
  "zipcode": "10020",
  "phone": "555-555-0199",
  "company": "Company",
  "alternative_phone": "555-555-0199",
  "country_id": 358,
  "country_iso": "US",
  "state_id": 347,
  "state_name": null,
  "state_text": "AL",
  "country": {
    "id": 358,
    "iso_name": "UNITED STATES",
    "iso": "US",
    "iso3": "USA",
    "name": "United States",
    "numcode": 840
  },
  "state": {
    "id": 347,
    "name": "Alabama",
    "abbr": "AL",
    "country_id": 358
  }
}
```



# Checkout



## Processing the checkout payment step


### Request

#### Endpoint

```plaintext
PATCH /api/checkouts/R488531239
Accept: application/json
X-Spree-Order-Token: u7wWqvJmH_qOVsuRjdS_jg
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=225&order[payment_attributes][][source_attributes][wallet_payment_source_id]=15
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
ETag: W/&quot;6b6ad536501d5ff76af4fe1253d2f887&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: f11beb1d-ee8f-49a0-8aff-7bcbeca1797c
X-Runtime: 0.316665
Content-Length: 3893
200 OK
```


```json
{
  "id": 282,
  "number": "R488531239",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 322,
  "created_at": "2019-07-16T16:09:29.205Z",
  "updated_at": "2019-07-16T16:09:29.943Z",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "email1@example.com",
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
  "token": "u7wWqvJmH_qOVsuRjdS_jg",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 225,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 577,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "PO Box 1337",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10001",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 348,
    "country_iso": "US",
    "state_id": 337,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 348,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 337,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 348
    }
  },
  "ship_address": {
    "id": 578,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "A Different Road",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10002",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 348,
    "country_iso": "US",
    "state_id": 337,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 348,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 337,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 348
    }
  },
  "line_items": [
    {
      "id": 278,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 707,
      "vendor_id": 2326,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "variant": {
        "id": 707,
        "name": "Product #1 - 3819",
        "sku": "SKU-1",
        "price": "10.0",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-1-3819",
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
            "id": 226,
            "name": "Size-1",
            "presentation": "S",
            "option_type_name": "foo-size-1",
            "option_type_id": 226,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 493
      },
      "vendor_name": "Vendor #2",
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
      "number": "H13510174443",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R488531239",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 233,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 215,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 233,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 215,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 215,
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
              "id": 300,
              "name": "ShippingCategory #1"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 707,
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
PATCH /api/checkouts/R113832994
Accept: application/json
X-Spree-Order-Token: 21xMvvIygbTJiSTRQ1oBeg
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=226&order[payment_attributes][][source_attributes][nonce]=fake-apple-pay-visa-nonce&order[payment_attributes][][source_attributes][payment_type]=ApplePayCard
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
ETag: W/&quot;2c1921901f160dc73171ee5c76c0f826&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 1624002e-33e8-479f-b110-2e8d4bc52b25
X-Runtime: 0.086660
Content-Length: 3893
200 OK
```


```json
{
  "id": 283,
  "number": "R113832994",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 323,
  "created_at": "2019-07-16T16:09:30.251Z",
  "updated_at": "2019-07-16T16:09:30.465Z",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "email2@example.com",
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
  "token": "21xMvvIygbTJiSTRQ1oBeg",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 226,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 579,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "PO Box 1337",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10003",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 349,
    "country_iso": "US",
    "state_id": 338,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 349,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 338,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 349
    }
  },
  "ship_address": {
    "id": 580,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "A Different Road",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10004",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 349,
    "country_iso": "US",
    "state_id": 338,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 349,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 338,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 349
    }
  },
  "line_items": [
    {
      "id": 279,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 709,
      "vendor_id": 2332,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "variant": {
        "id": 709,
        "name": "Product #2 - 2272",
        "sku": "SKU-3",
        "price": "10.0",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-2-2272",
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
            "id": 227,
            "name": "Size-2",
            "presentation": "S",
            "option_type_name": "foo-size-2",
            "option_type_id": 227,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 494
      },
      "vendor_name": "Vendor #7",
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
      "number": "H83017343304",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R113832994",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 235,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 216,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 235,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 216,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 216,
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
              "id": 301,
              "name": "ShippingCategory #2"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 709,
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
PATCH /api/checkouts/R235303175
Accept: application/json
X-Spree-Order-Token: SgMbDUjVssyWRStWjdM0BA
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=227&order[payment_attributes][][source_attributes][wallet_payment_source_id]=16
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
ETag: W/&quot;a3fec3251bdff26854d30e4a5ae55f0d&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: bb245dce-b70b-4500-8caa-f929be8c73ff
X-Runtime: 0.096910
Content-Length: 3894
200 OK
```


```json
{
  "id": 284,
  "number": "R235303175",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 324,
  "created_at": "2019-07-16T16:09:30.736Z",
  "updated_at": "2019-07-16T16:09:30.956Z",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "email3@example.com",
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
  "token": "SgMbDUjVssyWRStWjdM0BA",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 227,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 581,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "PO Box 1337",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10005",
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
    "id": 582,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "A Different Road",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10006",
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
      "id": 280,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 711,
      "vendor_id": 2338,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "variant": {
        "id": 711,
        "name": "Product #3 - 3172",
        "sku": "SKU-5",
        "price": "10.0",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-3-3172",
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
            "id": 228,
            "name": "Size-3",
            "presentation": "S",
            "option_type_name": "foo-size-3",
            "option_type_id": 228,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 495
      },
      "vendor_name": "Vendor #12",
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
      "number": "H67441803061",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R235303175",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 237,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 217,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 237,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 217,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 217,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 149,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 302,
              "name": "ShippingCategory #3"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 711,
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
PATCH /api/checkouts/R866043298
Accept: application/json
X-Spree-Order-Token: hwzKpsu1e40TzSgWm6GR_g
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=228&order[payment_attributes][][source_attributes][nonce]=fake-paypal-billing-agreement-nonce&order[payment_attributes][][source_attributes][payment_type]=PayPalAccount
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
ETag: W/&quot;dbc54fd003b898dee2f23b649d72f64d&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: ce0d90d8-2ebb-4d61-b885-2a86f61be1a2
X-Runtime: 0.080939
Content-Length: 3894
200 OK
```


```json
{
  "id": 285,
  "number": "R866043298",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 325,
  "created_at": "2019-07-16T16:09:31.208Z",
  "updated_at": "2019-07-16T16:09:31.414Z",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "email4@example.com",
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
  "token": "hwzKpsu1e40TzSgWm6GR_g",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 228,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 583,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "PO Box 1337",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10007",
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
    "id": 584,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "A Different Road",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10008",
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
      "id": 281,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 713,
      "vendor_id": 2344,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "variant": {
        "id": 713,
        "name": "Product #4 - 1980",
        "sku": "SKU-7",
        "price": "10.0",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-4-1980",
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
            "id": 229,
            "name": "Size-4",
            "presentation": "S",
            "option_type_name": "foo-size-4",
            "option_type_id": 229,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 496
      },
      "vendor_name": "Vendor #17",
      "adjustments": [

      ]
    }
  ],
  "payments": [

  ],
  "shipments": [
    {
      "id": 238,
      "tracking": null,
      "tracking_url": null,
      "number": "H75502655847",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R866043298",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 239,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 218,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 239,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 218,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 218,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 150,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 303,
              "name": "ShippingCategory #4"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 713,
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
PATCH /api/checkouts/R313590258
Accept: application/json
X-Spree-Order-Token: gwEKjicLLkHjjC-KAmLBXA
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=229&order[payment_attributes][][source_attributes][wallet_payment_source_id]=17
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
ETag: W/&quot;da04eca37f3ae1362db5ced0b7752cbd&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 252c0214-c719-4ede-b188-6d918b898292
X-Runtime: 0.089219
Content-Length: 3894
200 OK
```


```json
{
  "id": 286,
  "number": "R313590258",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 326,
  "created_at": "2019-07-16T16:09:31.665Z",
  "updated_at": "2019-07-16T16:09:31.866Z",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "email5@example.com",
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
  "token": "gwEKjicLLkHjjC-KAmLBXA",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 229,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 585,
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
    "id": 586,
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
      "id": 282,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 715,
      "vendor_id": 2350,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "variant": {
        "id": 715,
        "name": "Product #5 - 6765",
        "sku": "SKU-9",
        "price": "10.0",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-5-6765",
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
            "name": "Size-5",
            "presentation": "S",
            "option_type_name": "foo-size-5",
            "option_type_id": 230,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 497
      },
      "vendor_name": "Vendor #22",
      "adjustments": [

      ]
    }
  ],
  "payments": [

  ],
  "shipments": [
    {
      "id": 240,
      "tracking": null,
      "tracking_url": null,
      "number": "H21667144846",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R313590258",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 241,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 219,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 241,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 219,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 219,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 151,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 304,
              "name": "ShippingCategory #5"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 715,
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
PATCH /api/checkouts/R315848117
Accept: application/json
X-Spree-Order-Token: XCctyJqr1d-sNlzfsjDl8g
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=230&order[payment_attributes][][source_attributes][nonce]=fake-valid-visa-nonce&order[payment_attributes][][source_attributes][payment_type]=CreditCard
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
ETag: W/&quot;d2b97162f3c27a08133727f528122bf6&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: c418e195-8db9-481e-9482-1c2c94cfe2e4
X-Runtime: 0.121758
Content-Length: 3895
200 OK
```


```json
{
  "id": 287,
  "number": "R315848117",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 327,
  "created_at": "2019-07-16T16:09:32.146Z",
  "updated_at": "2019-07-16T16:09:32.418Z",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "email6@example.com",
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
  "token": "XCctyJqr1d-sNlzfsjDl8g",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 230,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 587,
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
    "id": 588,
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
      "id": 283,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 717,
      "vendor_id": 2356,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "variant": {
        "id": 717,
        "name": "Product #6 - 1004",
        "sku": "SKU-11",
        "price": "10.0",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-6-1004",
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
            "name": "Size-6",
            "presentation": "S",
            "option_type_name": "foo-size-6",
            "option_type_id": 231,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 498
      },
      "vendor_name": "Vendor #27",
      "adjustments": [

      ]
    }
  ],
  "payments": [

  ],
  "shipments": [
    {
      "id": 242,
      "tracking": null,
      "tracking_url": null,
      "number": "H16282833145",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R315848117",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 243,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 220,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 243,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 220,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 220,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 152,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 305,
              "name": "ShippingCategory #6"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 717,
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
POST /api/orders/R481274641/line_items
Accept: application/json
X-Spree-Order-Token: fIfmN3bswNxqusOaoACYNw
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/:order_number/line_items`

#### Parameters


```json
line_item[variant_id]=725&line_item[options][vendor_id]=2379
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
ETag: W/&quot;25bd6aefd52d111c766a5ec3768e89b6&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 7d8185fa-e32a-4172-ae5d-58b6c6657e59
X-Runtime: 0.074186
Content-Length: 735
201 Created
```


```json
{
  "id": 286,
  "quantity": 1,
  "price": "19.99",
  "variant_id": 725,
  "vendor_id": 2379,
  "single_display_amount": "$19.99",
  "display_amount": "$19.99",
  "total": "19.99",
  "variant": {
    "id": 725,
    "name": "Product #11 - 5157",
    "sku": "SKU-19",
    "price": "19.99",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": false,
    "slug": "product-11-5157",
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
        "id": 234,
        "name": "Size-9",
        "presentation": "S",
        "option_type_name": "foo-size-9",
        "option_type_id": 234,
        "option_type_presentation": "Size"
      }
    ],
    "images": [

    ],
    "product_id": 503
  },
  "vendor_name": "Vendor #46",
  "adjustments": [

  ]
}
```



## Deleting a line item


### Request

#### Endpoint

```plaintext
DELETE /api/orders/R973187725/line_items/284
Accept: application/json
X-Spree-Order-Token: sE3RY6hHVKZoQxT6cE_Qfw
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
X-Request-Id: a52f5fb8-2ed9-44fe-ad57-158c676f4339
X-Runtime: 0.059598
204 No Content
```




## Updating a line item


### Request

#### Endpoint

```plaintext
PUT /api/orders/R733347469/line_items/287
Accept: application/json
X-Spree-Order-Token: 1xJuBEEPzOzS6uFeWGOfYw
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
ETag: W/&quot;6007943c09e23224ef085eb9f24099e9&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 4b7e4a73-286d-470e-ab7e-fa2f2fb5722d
X-Runtime: 0.066678
Content-Length: 593
200 OK
```


```json
{
  "id": 287,
  "quantity": 2,
  "price": "10.0",
  "variant_id": 726,
  "vendor_id": 2385,
  "single_display_amount": "$10.00",
  "display_amount": "$20.00",
  "total": "20.0",
  "variant": {
    "id": 726,
    "name": "Product #12 - 6345",
    "sku": "SKU-21",
    "price": "19.99",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": true,
    "slug": "product-12-6345",
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
    "product_id": 504
  },
  "vendor_name": "Vendor #51",
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
X-Request-Id: ccb62eb1-58c6-4b2e-9899-d4d4f6ab5fcc
X-Runtime: 0.008768
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
X-Spree-Token: bd69ca578aabc8992face5ca86fee25588392b2cf9cf10e9
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
X-Request-Id: 6e253e99-faa2-4ff1-bba7-1fd250828f34
X-Runtime: 0.018887
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
Date: Tue, 16 Jul 2019 16:09:34 GMT
Surrogate-Control: max-age=900
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;aaa9520aa73bbdab0fd1c9f49ba70823&quot;
X-Request-Id: 02e12444-7e37-4c80-bdb3-9c3e83d6bf07
X-Runtime: 0.042968
Content-Length: 915
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
      "id": 508,
      "name": "Product #16 - 1355",
      "description": "As seen on TV!",
      "price": "19.99",
      "display_price": "$19.99",
      "available_on": "2018-07-16T16:09:34.566Z",
      "slug": "product-16-1355",
      "meta_description": null,
      "meta_keywords": null,
      "shipping_category_id": 313,
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
        "id": 730,
        "name": "Product #16 - 1355",
        "sku": "SKU-25",
        "price": "19.99",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-16-1355",
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
GET /api/products/product-14-2415
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
Date: Tue, 16 Jul 2019 16:09:34 GMT
Surrogate-Control: max-age=900
Surrogate-Key: product_id=1
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;381c6a9f6b816222c9c89be78877d46b&quot;
X-Request-Id: 80153b97-c2b8-4e87-a947-5088c8db0e39
X-Runtime: 0.072910
Content-Length: 833
200 OK
```


```json
{
  "id": 506,
  "name": "Product #14 - 2415",
  "description": "As seen on TV!",
  "price": "19.99",
  "display_price": "$19.99",
  "available_on": "2018-07-16T16:09:34.318Z",
  "slug": "product-14-2415",
  "meta_description": null,
  "meta_keywords": null,
  "shipping_category_id": 311,
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
    "id": 728,
    "name": "Product #14 - 2415",
    "sku": "SKU-23",
    "price": "19.99",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": true,
    "slug": "product-14-2415",
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
X-Request-Id: 1e1695d1-4f2a-44a2-8081-26f8bfbef408
X-Runtime: 0.016643
Content-Length: 65
404 Not Found
```


```json
{
  "error": "The resource you were looking for could not be found."
}
```



# Return Authorizations

Get user return authorizations

## Gets the user&#39;s return authorizations


### Request

#### Endpoint

```plaintext
GET /api/returns/mine
X-Spree-Token: 8566856f65df427b2ada9c0853b86c3e4b7b1e2482d3516e
Accept: application/json
Host: example.org
Cookie: 
```

`GET /api/returns/mine`

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
ETag: W/&quot;985923112f65e92fe62dd54c4f1b019f&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 1fbe079d-4337-4087-8ae2-600dac861b4f
X-Runtime: 0.014069
Content-Length: 28
200 OK
```


```json
{
  "return_authorizations": [

  ]
}
```



# Store Credits API

Get user store_credits and current account balance for the current user

## returns a 200


### Request

#### Endpoint

```plaintext
GET api/store_credits/mine
X-Spree-Token: e1decadd8564a8ec2737f9e9c5037343c35638c0690c57f4
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
ETag: W/&quot;46804186e8c8599ac55b44145925e776&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 01e39a14-8d5c-4cee-9114-5bece3164436
X-Runtime: 0.045100
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
      "created_at": "2019-07-16T16:09:34.789Z"
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
X-Spree-Token: e66447631571f92c5f9665352ca46315db80b2133dbb927c
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
X-Spree-Token: e66447631571f92c5f9665352ca46315db80b2133dbb927c
ETag: W/&quot;dfb248a4f6c651ca47b6b61f7b82c7ff&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 7914c1c1-e77d-4e08-8d59-3131f0e78a82
X-Runtime: 0.008998
Content-Length: 99
200 OK
```


```json
{
  "email": "email16@example.com",
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
user[email]=email15%40example.com&user[password]=secret
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
X-Spree-Token: 88740cd4ec5688fa0055621188eeea796ee5ac3ab2edab0a
ETag: W/&quot;12b5de3c7d1ecdc380d383c325e17189&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 9f58eecd-347d-41b2-a9c9-b6a38ef43904
X-Runtime: 0.009968
Content-Length: 553
200 OK
```


```json
{
  "id": 336,
  "email": "email15@example.com",
  "persistence_token": null,
  "perishable_token": null,
  "last_request_at": null,
  "login": "email15@example.com",
  "ship_address_id": null,
  "bill_address_id": null,
  "created_at": "2019-07-16T16:09:34.864Z",
  "updated_at": "2019-07-16T16:09:34.868Z",
  "spree_api_key": "88740cd4ec5688fa0055621188eeea796ee5ac3ab2edab0a",
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
X-Spree-Token: 3af66282d848580b6349bea68a363e6dcdefafa10390b1ab
ETag: W/&quot;929cc3191997fd525c081673a8053b2c&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: c4c9ec6e-ea22-49f0-b443-aac92d284293
X-Runtime: 0.024103
Content-Length: 157
201 Created
```


```json
{
  "id": 337,
  "email": "test@example.com",
  "created_at": "2019-07-16T16:09:34.888Z",
  "updated_at": "2019-07-16T16:09:34.890Z",
  "bill_address": null,
  "ship_address": null
}
```



# Variant



## Fetching a variant


### Request

#### Endpoint

```plaintext
GET /api/variants/719
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
ETag: W/&quot;745cf4b84aa8e6594431c263605fba87&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: dab90c4b-b4a4-4537-b6c3-779be685aaac
X-Runtime: 0.087541
Content-Length: 1454
200 OK
```


```json
{
  "id": 719,
  "name": "Product #7 - 6941",
  "sku": "SKU-13",
  "price": "10.0",
  "weight": "0.0",
  "height": null,
  "width": null,
  "depth": null,
  "is_master": false,
  "slug": "product-7-6941",
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
      "id": 232,
      "name": "Size-7",
      "presentation": "S",
      "option_type_name": "foo-size-7",
      "option_type_id": 232,
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
      "attachment_updated_at": "2019-07-16T16:09:32.682Z",
      "attachment_width": 489,
      "attachment_height": 490,
      "alt": null,
      "viewable_type": "Spree::Variant",
      "viewable_id": 719,
      "mini_url": "/spree/products/2/mini/thinking-cat.jpg?1563293372",
      "small_url": "/spree/products/2/small/thinking-cat.jpg?1563293372",
      "product_url": "/spree/products/2/product/thinking-cat.jpg?1563293372",
      "large_url": "/spree/products/2/large/thinking-cat.jpg?1563293372"
    }
  ],
  "variant_properties": [

  ],
  "stock_items": [

  ],
  "prices": [
    {
      "id": 1396,
      "vendor_id": 2365,
      "price": "10.0",
      "original_price": "10.0",
      "discount_percent": 0.0,
      "total_on_hand": 0,
      "country_iso": null,
      "final_sale": false,
      "on_sale": false
    },
    {
      "id": 1397,
      "vendor_id": 2366,
      "price": "20.0",
      "original_price": "20.0",
      "discount_percent": 0.0,
      "total_on_hand": 0,
      "country_iso": null,
      "final_sale": false,
      "on_sale": false
    }
  ]
}
```



