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
PUT /api/orders/R772913298/addresses/578
Accept: application/json
X-Spree-Order-Token: I2xXPGYFh49gdk7Kh-IdvA
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
ETag: W/&quot;d12455edfbc8b75c494c12398ecdc366&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 398cb71c-7819-4665-9125-97002f1905f8
X-Runtime: 0.195821
Content-Length: 513
200 OK
```


```json
{
  "id": 579,
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
}
```



# Checkout



## Processing the checkout payment step


### Request

#### Endpoint

```plaintext
PATCH /api/checkouts/R637573447
Accept: application/json
X-Spree-Order-Token: z9665mW6EpS3TkP2qpsGkg
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=227&order[payment_attributes][][source_attributes][wallet_payment_source_id]=15
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
ETag: W/&quot;373ae2760b4bf373bdc67d360e69c520&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 1f402b12-537e-4988-9c0e-893f42e95f86
X-Runtime: 0.117184
Content-Length: 3897
200 OK
```


```json
{
  "id": 287,
  "number": "R637573447",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 329,
  "created_at": "2019-07-17T23:09:17.012Z",
  "updated_at": "2019-07-17T23:09:17.352Z",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "email8@example.com",
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
  "token": "z9665mW6EpS3TkP2qpsGkg",
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
    "id": 588,
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
    "country_id": 357,
    "country_iso": "US",
    "state_id": 346,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 357,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 346,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 357
    }
  },
  "ship_address": {
    "id": 589,
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
    "country_id": 357,
    "country_iso": "US",
    "state_id": 346,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 357,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 346,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 357
    }
  },
  "line_items": [
    {
      "id": 283,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 720,
      "vendor_id": 2369,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "variant": {
        "id": 720,
        "name": "Product #11 - 5366",
        "sku": "SKU-14",
        "price": "10.0",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-11-5366",
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
        "product_id": 503
      },
      "vendor_name": "Vendor #37",
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
      "number": "H12623381455",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R637573447",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 237,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 219,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 237,
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
              "id": 308,
              "name": "ShippingCategory #9"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 720,
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
PATCH /api/checkouts/R901167082
Accept: application/json
X-Spree-Order-Token: TeldaY2dK8I8Z8V58LI41Q
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=228&order[payment_attributes][][source_attributes][nonce]=fake-apple-pay-visa-nonce&order[payment_attributes][][source_attributes][payment_type]=ApplePayCard
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
ETag: W/&quot;505feaa740845adeb731ab8a8716642f&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: cb1b00a2-0594-40c8-853b-4c732bcfcc5b
X-Runtime: 0.099471
Content-Length: 3898
200 OK
```


```json
{
  "id": 288,
  "number": "R901167082",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 330,
  "created_at": "2019-07-17T23:09:17.629Z",
  "updated_at": "2019-07-17T23:09:17.856Z",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "email9@example.com",
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
  "token": "TeldaY2dK8I8Z8V58LI41Q",
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
    "id": 590,
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
  },
  "ship_address": {
    "id": 591,
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
  },
  "line_items": [
    {
      "id": 284,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 722,
      "vendor_id": 2375,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "variant": {
        "id": 722,
        "name": "Product #12 - 3380",
        "sku": "SKU-16",
        "price": "10.0",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-12-3380",
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
        "product_id": 504
      },
      "vendor_name": "Vendor #42",
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
      "number": "H35754730355",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R901167082",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 239,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 220,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 239,
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
              "id": 309,
              "name": "ShippingCategory #10"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 722,
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
PATCH /api/checkouts/R489634685
Accept: application/json
X-Spree-Order-Token: y4tBQuzWmxtCGAwWTN9kig
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=229&order[payment_attributes][][source_attributes][nonce]=fake-paypal-billing-agreement-nonce&order[payment_attributes][][source_attributes][payment_type]=PayPalAccount
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
ETag: W/&quot;046d178f17aeaaaa537ffa7f9e345640&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: c1c884e7-0668-4463-a716-f3dfe798a9b2
X-Runtime: 0.075404
Content-Length: 3899
200 OK
```


```json
{
  "id": 289,
  "number": "R489634685",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 331,
  "created_at": "2019-07-17T23:09:18.136Z",
  "updated_at": "2019-07-17T23:09:18.337Z",
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
  "token": "y4tBQuzWmxtCGAwWTN9kig",
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
    "id": 592,
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
    "country_id": 359,
    "country_iso": "US",
    "state_id": 348,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 359,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 348,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 359
    }
  },
  "ship_address": {
    "id": 593,
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
    "country_id": 359,
    "country_iso": "US",
    "state_id": 348,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 359,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 348,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 359
    }
  },
  "line_items": [
    {
      "id": 285,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 724,
      "vendor_id": 2381,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "variant": {
        "id": 724,
        "name": "Product #13 - 9788",
        "sku": "SKU-18",
        "price": "10.0",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-13-9788",
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
        "product_id": 505
      },
      "vendor_name": "Vendor #47",
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
      "number": "H53567384872",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R489634685",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 241,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 221,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 241,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 221,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 221,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 153,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 310,
              "name": "ShippingCategory #11"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 724,
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
PATCH /api/checkouts/R616683307
Accept: application/json
X-Spree-Order-Token: uA2aTPIK-Yh05s9Eu4mGrg
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
ETag: W/&quot;140f26ffcf31f9ecca1c207214a3ae6f&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 1e7cf319-bbe2-48c7-8284-04c9c1d6756b
X-Runtime: 0.109258
Content-Length: 3899
200 OK
```


```json
{
  "id": 290,
  "number": "R616683307",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 332,
  "created_at": "2019-07-17T23:09:18.594Z",
  "updated_at": "2019-07-17T23:09:18.811Z",
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
  "token": "uA2aTPIK-Yh05s9Eu4mGrg",
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
    "id": 594,
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
    "country_id": 360,
    "country_iso": "US",
    "state_id": 349,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 360,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 349,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 360
    }
  },
  "ship_address": {
    "id": 595,
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
    "country_id": 360,
    "country_iso": "US",
    "state_id": 349,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 360,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 349,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 360
    }
  },
  "line_items": [
    {
      "id": 286,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 726,
      "vendor_id": 2387,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "variant": {
        "id": 726,
        "name": "Product #14 - 3893",
        "sku": "SKU-20",
        "price": "10.0",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-14-3893",
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
            "name": "Size-7",
            "presentation": "S",
            "option_type_name": "foo-size-7",
            "option_type_id": 232,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 506
      },
      "vendor_name": "Vendor #52",
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
      "number": "H38687623745",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R616683307",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 243,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 222,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 243,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 222,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 222,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 154,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 311,
              "name": "ShippingCategory #12"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 726,
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
PATCH /api/checkouts/R739254452
Accept: application/json
X-Spree-Order-Token: ggoPBbD0e-jZkGws-WRlMA
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=231&order[payment_attributes][][source_attributes][wallet_payment_source_id]=16
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
ETag: W/&quot;4ee90c5ae3d8919ac8a1f9dac4cb77a9&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: f2918f3c-d58c-4115-bd64-82d4725feea4
X-Runtime: 0.079796
Content-Length: 3899
200 OK
```


```json
{
  "id": 291,
  "number": "R739254452",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 333,
  "created_at": "2019-07-17T23:09:19.097Z",
  "updated_at": "2019-07-17T23:09:19.304Z",
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
  "token": "ggoPBbD0e-jZkGws-WRlMA",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 231,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 596,
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
    "country_id": 361,
    "country_iso": "US",
    "state_id": 350,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 361,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 350,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 361
    }
  },
  "ship_address": {
    "id": 597,
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
    "country_id": 361,
    "country_iso": "US",
    "state_id": 350,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 361,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 350,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 361
    }
  },
  "line_items": [
    {
      "id": 287,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 728,
      "vendor_id": 2393,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "variant": {
        "id": 728,
        "name": "Product #15 - 9113",
        "sku": "SKU-22",
        "price": "10.0",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-15-9113",
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
            "name": "Size-8",
            "presentation": "S",
            "option_type_name": "foo-size-8",
            "option_type_id": 233,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 507
      },
      "vendor_name": "Vendor #57",
      "adjustments": [

      ]
    }
  ],
  "payments": [

  ],
  "shipments": [
    {
      "id": 244,
      "tracking": null,
      "tracking_url": null,
      "number": "H74885663526",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R739254452",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 245,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 223,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 245,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 223,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 223,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 155,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 312,
              "name": "ShippingCategory #13"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 728,
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
PATCH /api/checkouts/R358119093
Accept: application/json
X-Spree-Order-Token: HYCUyjhBu6QKBNMwttThrA
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=232&order[payment_attributes][][source_attributes][wallet_payment_source_id]=17
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
ETag: W/&quot;e9b212df8a51df5a4dd274a80b5d208c&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 58566eb4-a3e6-4c09-bba6-cdb412e102a5
X-Runtime: 0.077138
Content-Length: 3899
200 OK
```


```json
{
  "id": 292,
  "number": "R358119093",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 334,
  "created_at": "2019-07-17T23:09:19.543Z",
  "updated_at": "2019-07-17T23:09:19.757Z",
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
  "token": "HYCUyjhBu6QKBNMwttThrA",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 232,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 598,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "PO Box 1337",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10021",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 362,
    "country_iso": "US",
    "state_id": 351,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 362,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 351,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 362
    }
  },
  "ship_address": {
    "id": 599,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "A Different Road",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10022",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 362,
    "country_iso": "US",
    "state_id": 351,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 362,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 351,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 362
    }
  },
  "line_items": [
    {
      "id": 288,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 730,
      "vendor_id": 2399,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "variant": {
        "id": 730,
        "name": "Product #16 - 9878",
        "sku": "SKU-24",
        "price": "10.0",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-16-9878",
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
            "name": "Size-9",
            "presentation": "S",
            "option_type_name": "foo-size-9",
            "option_type_id": 234,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 508
      },
      "vendor_name": "Vendor #62",
      "adjustments": [

      ]
    }
  ],
  "payments": [

  ],
  "shipments": [
    {
      "id": 246,
      "tracking": null,
      "tracking_url": null,
      "number": "H24636200836",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R358119093",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 247,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 224,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 247,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 224,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 224,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 156,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 313,
              "name": "ShippingCategory #14"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 730,
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
POST /api/orders/R103320674/line_items
Accept: application/json
X-Spree-Order-Token: 3hbeZTUGwxERUAssADlhcw
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/:order_number/line_items`

#### Parameters


```json
line_item[variant_id]=712&line_item[options][vendor_id]=2339
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
ETag: W/&quot;cd52113a131a842da370c1d0b333f31f&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 4a15bd89-d074-4caf-9fa0-c0857dff2ed9
X-Runtime: 0.061208
Content-Length: 732
201 Created
```


```json
{
  "id": 281,
  "quantity": 1,
  "price": "19.99",
  "variant_id": 712,
  "vendor_id": 2339,
  "single_display_amount": "$19.99",
  "display_amount": "$19.99",
  "total": "19.99",
  "variant": {
    "id": 712,
    "name": "Product #5 - 3992",
    "sku": "SKU-6",
    "price": "19.99",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": false,
    "slug": "product-5-3992",
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
    "product_id": 497
  },
  "vendor_name": "Vendor #12",
  "adjustments": [

  ]
}
```



## Deleting a line item


### Request

#### Endpoint

```plaintext
DELETE /api/orders/R085607601/line_items/278
Accept: application/json
X-Spree-Order-Token: hXMZe8z1YTIelfFLmdDRvQ
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
X-Request-Id: 94aaecf8-2cb8-450b-9be2-f331e982569f
X-Runtime: 0.160666
204 No Content
```




## Updating a line item


### Request

#### Endpoint

```plaintext
PUT /api/orders/R074117783/line_items/279
Accept: application/json
X-Spree-Order-Token: PAoZNdsbsVwTxzaLq1JdcQ
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
ETag: W/&quot;0d6cc5b766042ca72e7a030388da45d2&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 747e4d49-9174-49df-9adc-a0e72b4dbc4c
X-Runtime: 0.089022
Content-Length: 589
200 OK
```


```json
{
  "id": 279,
  "quantity": 2,
  "price": "10.0",
  "variant_id": 707,
  "vendor_id": 2331,
  "single_display_amount": "$10.00",
  "display_amount": "$20.00",
  "total": "20.0",
  "variant": {
    "id": 707,
    "name": "Product #2 - 2490",
    "sku": "SKU-2",
    "price": "19.99",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": true,
    "slug": "product-2-2490",
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
    "product_id": 494
  },
  "vendor_name": "Vendor #5",
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
X-Request-Id: 0e08f3b9-d156-4ad1-a8a5-b8cbf7b6263c
X-Runtime: 0.008592
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
X-Spree-Token: 1018de4264676cb2f638b3ad3f948492a563adac0ae86677
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
X-Request-Id: 32622ae5-b6a7-45df-b7db-f1b7abfe9724
X-Runtime: 0.015921
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
Date: Wed, 17 Jul 2019 23:09:16 GMT
Surrogate-Control: max-age=900
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;37a385b2ec73711311fba004daa38c45&quot;
X-Request-Id: 56c7bffe-fe6c-49eb-8a49-2ab9d66dcb2c
X-Runtime: 0.042120
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
      "id": 502,
      "name": "Product #10 - 5030",
      "description": "As seen on TV!",
      "price": "19.99",
      "display_price": "$19.99",
      "available_on": "2018-07-17T23:09:16.523Z",
      "slug": "product-10-5030",
      "meta_description": null,
      "meta_keywords": null,
      "shipping_category_id": 307,
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
        "id": 718,
        "name": "Product #10 - 5030",
        "sku": "SKU-13",
        "price": "19.99",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-10-5030",
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
GET /api/products/product-8-1596
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
Date: Wed, 17 Jul 2019 23:09:16 GMT
Surrogate-Control: max-age=900
Surrogate-Key: product_id=1
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;9d8feb3271c5e180f102f8bc1a679658&quot;
X-Request-Id: 2513d399-3960-4ac2-8ad9-3f433f64c392
X-Runtime: 0.068008
Content-Length: 829
200 OK
```


```json
{
  "id": 500,
  "name": "Product #8 - 1596",
  "description": "As seen on TV!",
  "price": "19.99",
  "display_price": "$19.99",
  "available_on": "2018-07-17T23:09:16.295Z",
  "slug": "product-8-1596",
  "meta_description": null,
  "meta_keywords": null,
  "shipping_category_id": 305,
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
    "id": 716,
    "name": "Product #8 - 1596",
    "sku": "SKU-11",
    "price": "19.99",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": true,
    "slug": "product-8-1596",
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
X-Request-Id: 79d7d125-6dd2-4270-9285-41234bc5cdd4
X-Runtime: 0.015257
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
X-Spree-Token: f8a3a8c33c49ee0f67310eeaa67257ef3be0aa4f33290d56
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
X-Request-Id: 70412028-9e82-46d5-9d8e-34d0533bbaec
X-Runtime: 0.014045
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
X-Spree-Token: deb54754607664aa6e6716cd4bdc319ac46df6aef96fb7f5
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
ETag: W/&quot;fb668f8054562461c10914bae516c6da&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: b0681138-c313-4e0e-a843-c589e81e4985
X-Runtime: 0.033855
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
      "created_at": "2019-07-17T23:09:16.745Z"
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

Create a new user and return a header X-Spree-Token to be used for further user related request

## Gets the user account information


### Request

#### Endpoint

```plaintext
GET /api/users/mine
X-Spree-Token: 2105b6be334a86ee344b378ab490ba8ff2495a514fa0cc93
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
X-Spree-Token: 2105b6be334a86ee344b378ab490ba8ff2495a514fa0cc93
ETag: W/&quot;bfd124848078a34e451875f4b9d35dbe&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 5ee10b7b-70f6-45d0-977d-25a5335aa2b9
X-Runtime: 0.010133
Content-Length: 99
200 OK
```


```json
{
  "email": "email15@example.com",
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
user[email]=email16%40example.com&user[password]=secret
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
X-Spree-Token: b2f9befb2bde2842211c0d70abefc586627f66dac748aa12
ETag: W/&quot;d96f4820fa6adfde7d1429a0f9754045&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: e9eb7dd2-3209-492c-a2ab-4d20f570bb2f
X-Runtime: 0.005836
Content-Length: 553
200 OK
```


```json
{
  "id": 338,
  "email": "email16@example.com",
  "persistence_token": null,
  "perishable_token": null,
  "last_request_at": null,
  "login": "email16@example.com",
  "ship_address_id": null,
  "bill_address_id": null,
  "created_at": "2019-07-17T23:09:19.896Z",
  "updated_at": "2019-07-17T23:09:19.899Z",
  "spree_api_key": "b2f9befb2bde2842211c0d70abefc586627f66dac748aa12",
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
| user[first_name]  | User first name |
| user[last_name]  | User last name |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
X-Spree-Token: 175feddbf501f260050ddac88bc6dfb6d4d62e89176b5654
ETag: W/&quot;71ebc1b86b609b9090fb7059821218fa&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 27c2f205-1be8-4d3c-8808-266264bc70a9
X-Runtime: 0.025931
Content-Length: 157
201 Created
```


```json
{
  "id": 336,
  "email": "test@example.com",
  "created_at": "2019-07-17T23:09:19.853Z",
  "updated_at": "2019-07-17T23:09:19.854Z",
  "bill_address": null,
  "ship_address": null
}
```



# Variant



## Fetching a variant


### Request

#### Endpoint

```plaintext
GET /api/variants/715
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
ETag: W/&quot;5a56222ec16901e3e70c1ca64f089e50&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 37b16cfb-9581-455f-8971-a1cc1b062131
X-Runtime: 0.084765
Content-Length: 1449
200 OK
```


```json
{
  "id": 715,
  "name": "Product #7 - 18",
  "sku": "SKU-9",
  "price": "10.0",
  "weight": "0.0",
  "height": null,
  "width": null,
  "depth": null,
  "is_master": false,
  "slug": "product-7-18",
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
      "id": 228,
      "name": "Size-3",
      "presentation": "S",
      "option_type_name": "foo-size-3",
      "option_type_id": 228,
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
      "attachment_updated_at": "2019-07-17T23:09:16.027Z",
      "attachment_width": 489,
      "attachment_height": 490,
      "alt": null,
      "viewable_type": "Spree::Variant",
      "viewable_id": 715,
      "mini_url": "/spree/products/2/mini/thinking-cat.jpg?1563404956",
      "small_url": "/spree/products/2/small/thinking-cat.jpg?1563404956",
      "product_url": "/spree/products/2/product/thinking-cat.jpg?1563404956",
      "large_url": "/spree/products/2/large/thinking-cat.jpg?1563404956"
    }
  ],
  "variant_properties": [

  ],
  "stock_items": [

  ],
  "prices": [
    {
      "id": 1387,
      "vendor_id": 2352,
      "price": "10.0",
      "original_price": "10.0",
      "discount_percent": 0.0,
      "total_on_hand": 0,
      "country_iso": null,
      "final_sale": false,
      "on_sale": false
    },
    {
      "id": 1388,
      "vendor_id": 2353,
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



