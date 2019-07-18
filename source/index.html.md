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
PUT /api/orders/R202741903/addresses/592
Accept: application/json
X-Spree-Order-Token: P3H19iKOkbX4kiAWuIDC-Q
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
ETag: W/&quot;291082226568f7f5658556531007234a&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 2f68e722-85a5-4b51-b691-b3657fc52db8
X-Runtime: 0.046030
Content-Length: 513
200 OK
```


```json
{
  "id": 593,
  "firstname": "John the Tester",
  "lastname": null,
  "full_name": "John the Tester",
  "address1": "A Different Road",
  "address2": "Northwest",
  "city": "Herndon",
  "zipcode": "10016",
  "phone": "555-555-0199",
  "company": "Company",
  "alternative_phone": "555-555-0199",
  "country_id": 367,
  "country_iso": "US",
  "state_id": 356,
  "state_name": null,
  "state_text": "AL",
  "country": {
    "id": 367,
    "iso_name": "UNITED STATES",
    "iso": "US",
    "iso3": "USA",
    "name": "United States",
    "numcode": 840
  },
  "state": {
    "id": 356,
    "name": "Alabama",
    "abbr": "AL",
    "country_id": 367
  }
}
```



# Checkout



## Processing the checkout payment step


### Request

#### Endpoint

```plaintext
PATCH /api/checkouts/R724222559
Accept: application/json
X-Spree-Order-Token: Obn1tkk1TNyrKmfA-KU7xw
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
ETag: W/&quot;21c35a59be6e61c3b0ba2a0e1037d7f2&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 6a7d0d6d-3f02-49ff-aa2a-eaa46ec7c6ba
X-Runtime: 0.281334
Content-Length: 3893
200 OK
```


```json
{
  "id": 282,
  "number": "R724222559",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 323,
  "created_at": "2019-07-18T15:45:55.901Z",
  "updated_at": "2019-07-18T15:45:56.700Z",
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
  "token": "Obn1tkk1TNyrKmfA-KU7xw",
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
      "id": 278,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 723,
      "vendor_id": 2370,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "variant": {
        "id": 723,
        "name": "Product #1 - 6394",
        "sku": "SKU-1",
        "price": "10.0",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-1-6394",
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
        "product_id": 509
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
      "number": "H10430721126",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R724222559",
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
              "id": 306,
              "name": "ShippingCategory #1"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 723,
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
PATCH /api/checkouts/R915117443
Accept: application/json
X-Spree-Order-Token: 3gdUQSq9XQee4JKtypO6jQ
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=226&order[payment_attributes][][source_attributes][wallet_payment_source_id]=16
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
ETag: W/&quot;35f200d1ed5605b461b80f4a974c4849&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 9aab6bb2-9bb5-44a6-981a-eb512b294175
X-Runtime: 0.100801
Content-Length: 3893
200 OK
```


```json
{
  "id": 283,
  "number": "R915117443",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 324,
  "created_at": "2019-07-18T15:45:57.103Z",
  "updated_at": "2019-07-18T15:45:57.341Z",
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
  "token": "3gdUQSq9XQee4JKtypO6jQ",
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
      "id": 279,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 725,
      "vendor_id": 2376,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "variant": {
        "id": 725,
        "name": "Product #2 - 9551",
        "sku": "SKU-3",
        "price": "10.0",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-2-9551",
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
        "product_id": 510
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
      "number": "H84746726270",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R915117443",
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
              "id": 307,
              "name": "ShippingCategory #2"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 725,
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
PATCH /api/checkouts/R481620853
Accept: application/json
X-Spree-Order-Token: 6nHTuNwbBQoyFKW1UjufZQ
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=227&order[payment_attributes][][source_attributes][wallet_payment_source_id]=17
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
ETag: W/&quot;2464cf2d4e8867ab3b6f9c30b27ebd9a&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: ccadb96a-bc45-4eaf-b0dd-adc54466f3a9
X-Runtime: 0.074421
Content-Length: 3894
200 OK
```


```json
{
  "id": 284,
  "number": "R481620853",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 325,
  "created_at": "2019-07-18T15:45:57.646Z",
  "updated_at": "2019-07-18T15:45:57.871Z",
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
  "token": "6nHTuNwbBQoyFKW1UjufZQ",
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
    "country_id": 356,
    "country_iso": "US",
    "state_id": 345,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 356,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 345,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 356
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
    "country_id": 356,
    "country_iso": "US",
    "state_id": 345,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 356,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 345,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 356
    }
  },
  "line_items": [
    {
      "id": 280,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 727,
      "vendor_id": 2382,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "variant": {
        "id": 727,
        "name": "Product #3 - 6391",
        "sku": "SKU-5",
        "price": "10.0",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-3-6391",
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
        "product_id": 511
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
      "number": "H26286724860",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R481620853",
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
              "id": 308,
              "name": "ShippingCategory #3"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 727,
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
PATCH /api/checkouts/R776116046
Accept: application/json
X-Spree-Order-Token: vBzQ-JBtSfbMcQBTDQyNAQ
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=228&order[payment_attributes][][source_attributes][nonce]=fake-valid-visa-nonce&order[payment_attributes][][source_attributes][payment_type]=CreditCard
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
ETag: W/&quot;aa93b68a841b95eb6db539b3e3bd8d33&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: c882a55f-9ace-4eaf-8599-905c7c2aac77
X-Runtime: 0.083952
Content-Length: 3894
200 OK
```


```json
{
  "id": 285,
  "number": "R776116046",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 326,
  "created_at": "2019-07-18T15:45:58.128Z",
  "updated_at": "2019-07-18T15:45:58.372Z",
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
  "token": "vBzQ-JBtSfbMcQBTDQyNAQ",
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
      "id": 281,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 729,
      "vendor_id": 2388,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "variant": {
        "id": 729,
        "name": "Product #4 - 5938",
        "sku": "SKU-7",
        "price": "10.0",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-4-5938",
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
        "product_id": 512
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
      "number": "H47887275177",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R776116046",
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
              "id": 309,
              "name": "ShippingCategory #4"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 729,
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
PATCH /api/checkouts/R320875363
Accept: application/json
X-Spree-Order-Token: enXu5gRw1zvOajGA5APqtw
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
ETag: W/&quot;dede028046e1cb0ff9a40ebf27682a65&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: cbceb3c3-b35b-4c5e-858d-03d541b40486
X-Runtime: 0.080757
Content-Length: 3894
200 OK
```


```json
{
  "id": 286,
  "number": "R320875363",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 327,
  "created_at": "2019-07-18T15:45:58.631Z",
  "updated_at": "2019-07-18T15:45:58.846Z",
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
  "token": "enXu5gRw1zvOajGA5APqtw",
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
      "id": 282,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 731,
      "vendor_id": 2394,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "variant": {
        "id": 731,
        "name": "Product #5 - 1581",
        "sku": "SKU-9",
        "price": "10.0",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-5-1581",
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
        "product_id": 513
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
      "number": "H11036752226",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R320875363",
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
              "id": 310,
              "name": "ShippingCategory #5"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 731,
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
PATCH /api/checkouts/R424893385
Accept: application/json
X-Spree-Order-Token: 9-_fQBNrz35HNj4qRBjtFw
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=230&order[payment_attributes][][source_attributes][nonce]=fake-apple-pay-visa-nonce&order[payment_attributes][][source_attributes][payment_type]=ApplePayCard
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
ETag: W/&quot;b45e844d04184c3f9891982c8bf1eb64&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: e4ba25b0-0b52-438c-851f-46243f227a3d
X-Runtime: 0.087550
Content-Length: 3895
200 OK
```


```json
{
  "id": 287,
  "number": "R424893385",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 328,
  "created_at": "2019-07-18T15:45:59.090Z",
  "updated_at": "2019-07-18T15:45:59.303Z",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "email7@example.com",
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
  "token": "9-_fQBNrz35HNj4qRBjtFw",
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
      "id": 283,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 733,
      "vendor_id": 2400,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "variant": {
        "id": 733,
        "name": "Product #6 - 5352",
        "sku": "SKU-11",
        "price": "10.0",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-6-5352",
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
        "product_id": 514
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
      "number": "H30402475084",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R424893385",
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
              "id": 311,
              "name": "ShippingCategory #6"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 733,
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
POST /api/orders/R023994500/line_items
Accept: application/json
X-Spree-Order-Token: by5FFMB9vt8-23q_NuvOxQ
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/:order_number/line_items`

#### Parameters


```json
line_item[variant_id]=750&line_item[options][vendor_id]=2456
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
ETag: W/&quot;989879f7f66f4691c51704ea5f8eb32f&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 1a6e488f-2a6e-4f55-b3bb-f6fb8c40e779
X-Runtime: 0.084449
Content-Length: 735
201 Created
```


```json
{
  "id": 288,
  "quantity": 1,
  "price": "19.99",
  "variant_id": 750,
  "vendor_id": 2456,
  "single_display_amount": "$19.99",
  "display_amount": "$19.99",
  "total": "19.99",
  "variant": {
    "id": 750,
    "name": "Product #20 - 5268",
    "sku": "SKU-28",
    "price": "19.99",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": false,
    "slug": "product-20-5268",
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
    "product_id": 528
  },
  "vendor_name": "Vendor #72",
  "adjustments": [

  ]
}
```



## Deleting a line item


### Request

#### Endpoint

```plaintext
DELETE /api/orders/R121459885/line_items/286
Accept: application/json
X-Spree-Order-Token: MDfUoF8y8DjAKV9lRoK_Qw
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
X-Request-Id: 31b07c99-df97-4a53-ae97-1638f91f1475
X-Runtime: 0.058677
204 No Content
```




## Updating a line item


### Request

#### Endpoint

```plaintext
PUT /api/orders/R787756616/line_items/285
Accept: application/json
X-Spree-Order-Token: 7FshlF6vHaOhEWfqXeVY3g
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
ETag: W/&quot;22865f4e5a2b94b71b7dae3ff51668b0&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 2668f923-4c74-4f6a-a842-9ef7a6d3111e
X-Runtime: 0.092510
Content-Length: 593
200 OK
```


```json
{
  "id": 285,
  "quantity": 2,
  "price": "10.0",
  "variant_id": 744,
  "vendor_id": 2444,
  "single_display_amount": "$10.00",
  "display_amount": "$20.00",
  "total": "20.0",
  "variant": {
    "id": 744,
    "name": "Product #16 - 7090",
    "sku": "SKU-23",
    "price": "19.99",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": true,
    "slug": "product-16-7090",
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
    "product_id": 524
  },
  "vendor_name": "Vendor #62",
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
ETag: W/&quot;b4f00fd4b89d93adb5daaabd97603d99&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: cce9ecfe-a620-4e08-8c1f-d3cd2c2b9b12
X-Runtime: 0.090881
Content-Length: 134
200 OK
```


```json
[
  {
    "id": 625,
    "name": "Kids",
    "navigation_url": "/navigation/kids",
    "parent_id": 624,
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
X-Spree-Token: 8730cc6d373275b3bd62cfe4f12fa0505d4f7a9a5a5bd221
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
X-Request-Id: f99c5b7c-4bd9-491b-9c73-176c21c2c56d
X-Runtime: 0.058096
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

get products by taxon

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
Date: Thu, 18 Jul 2019 15:46:01 GMT
Surrogate-Control: max-age=900
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;e7da055ea174726bfdf7ed8bca92f950&quot;
X-Request-Id: 5dbe029e-70ed-4b15-a5df-a5bd9c3a840e
X-Runtime: 0.062183
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
      "id": 521,
      "name": "Product #13 - 6889",
      "description": "As seen on TV!",
      "price": "19.99",
      "display_price": "$19.99",
      "available_on": "2018-07-18T15:46:01.007Z",
      "slug": "product-13-6889",
      "meta_description": null,
      "meta_keywords": null,
      "shipping_category_id": 316,
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
        "id": 741,
        "name": "Product #13 - 6889",
        "sku": "SKU-20",
        "price": "19.99",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-13-6889",
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
GET /api/products/product-14-1100
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
Date: Thu, 18 Jul 2019 15:46:01 GMT
Surrogate-Control: max-age=900
Surrogate-Key: product_id=1
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;07d6f938f47fc10a63f855bd8c9a692e&quot;
X-Request-Id: 7bdf0918-6ccc-4a1e-9c22-c65ba239ef1e
X-Runtime: 0.041926
Content-Length: 833
200 OK
```


```json
{
  "id": 522,
  "name": "Product #14 - 1100",
  "description": "As seen on TV!",
  "price": "19.99",
  "display_price": "$19.99",
  "available_on": "2018-07-18T15:46:01.157Z",
  "slug": "product-14-1100",
  "meta_description": null,
  "meta_keywords": null,
  "shipping_category_id": 317,
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
    "id": 742,
    "name": "Product #14 - 1100",
    "sku": "SKU-21",
    "price": "19.99",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": true,
    "slug": "product-14-1100",
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
X-Request-Id: 7bd8a524-49dc-495d-a0d0-db7e46f2d5f7
X-Runtime: 0.042175
Content-Length: 65
404 Not Found
```


```json
{
  "error": "The resource you were looking for could not be found."
}
```



## returns associated products


### Request

#### Endpoint

```plaintext
GET /api/taxons/products?id=627
Host: example.org
Cookie: 
```

`GET /api/taxons/products`

#### Parameters


```json
id: 627
```


| Name | Description |
|:-----|:------------|
| permalink  |  permalink |
| id  |  id |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
ETag: W/&quot;23d61c5534bd5d1e447da66ca6c7857b&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 2c7536d6-bcaf-4a1d-a9ee-3c8a0eabb7c9
X-Runtime: 0.053707
Content-Length: 1090
200 OK
```


```json
{
  "count": 1,
  "total_count": 1,
  "current_page": 1,
  "pages": 1,
  "per_page": 500,
  "products": [
    {
      "id": 517,
      "name": "Product #9 - 1915",
      "description": "As seen on TV!",
      "price": "19.99",
      "display_price": "$19.99",
      "available_on": "2018-07-18T15:46:00.459Z",
      "slug": "product-9-1915",
      "meta_description": null,
      "meta_keywords": null,
      "shipping_category_id": 314,
      "taxon_ids": [
        627
      ],
      "total_on_hand": 0,
      "meta_title": null,
      "trends": [

      ],
      "brand": "Ruby on Rails",
      "brand_description": null,
      "has_variants": false,
      "master": {
        "id": 737,
        "name": "Product #9 - 1915",
        "sku": "SKU-16",
        "price": "19.99",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-9-1915",
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
        {
          "taxon_id": 627,
          "position": 1,
          "taxon": {
            "id": 627,
            "name": "Ruby on Rails",
            "pretty_name": "Ruby on Rails",
            "permalink": "ruby-on-rails",
            "parent_id": null,
            "taxonomy_id": 213
          }
        }
      ]
    }
  ]
}
```



## returns associated products


### Request

#### Endpoint

```plaintext
GET /api/taxons/products?permalink=ruby-on-rails
Host: example.org
Cookie: 
```

`GET /api/taxons/products`

#### Parameters


```json
permalink: ruby-on-rails
```


| Name | Description |
|:-----|:------------|
| permalink  |  permalink |
| id  |  id |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
ETag: W/&quot;415934d27dc00d5a39850201025c18e4&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 3cab204a-020b-4276-a582-aa42d5a43c42
X-Runtime: 0.044638
Content-Length: 1094
200 OK
```


```json
{
  "count": 1,
  "total_count": 1,
  "current_page": 1,
  "pages": 1,
  "per_page": 500,
  "products": [
    {
      "id": 519,
      "name": "Product #11 - 1988",
      "description": "As seen on TV!",
      "price": "19.99",
      "display_price": "$19.99",
      "available_on": "2018-07-18T15:46:00.755Z",
      "slug": "product-11-1988",
      "meta_description": null,
      "meta_keywords": null,
      "shipping_category_id": 315,
      "taxon_ids": [
        631
      ],
      "total_on_hand": 0,
      "meta_title": null,
      "trends": [

      ],
      "brand": "Ruby on Rails",
      "brand_description": null,
      "has_variants": false,
      "master": {
        "id": 739,
        "name": "Product #11 - 1988",
        "sku": "SKU-18",
        "price": "19.99",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-11-1988",
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
        {
          "taxon_id": 631,
          "position": 1,
          "taxon": {
            "id": 631,
            "name": "Ruby on Rails",
            "pretty_name": "Ruby on Rails",
            "permalink": "ruby-on-rails",
            "parent_id": null,
            "taxonomy_id": 215
          }
        }
      ]
    }
  ]
}
```



# Return Authorizations

Get user return authorizations

## Gets the user&#39;s return authorizations


### Request

#### Endpoint

```plaintext
GET /api/returns/mine
X-Spree-Token: fa879be3a3874598f2703f93a3615f2b95192e9cc58e1641
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
X-Request-Id: 4c99150e-c608-40e2-b584-ad06ff1b5749
X-Runtime: 0.014575
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
X-Spree-Token: b6fa65d0a13e7efc3314ec2b2a3a7f1e63d08ec180baa5f1
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
ETag: W/&quot;cf7afc8154d803dad1342e09e582af5e&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: ac35fb22-8ce9-4b1a-9d9f-dbff8b32af73
X-Runtime: 0.036380
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
      "created_at": "2019-07-18T15:45:59.415Z"
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
X-Spree-Token: 1c3cc86fcc547c1a97da2bfb304f402fc90f742c327aa93b
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
X-Spree-Token: 1c3cc86fcc547c1a97da2bfb304f402fc90f742c327aa93b
ETag: W/&quot;863033c0e7985125e75f9af192012eb0&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 53a692ef-870d-4049-bb93-04f0d5ecca60
X-Runtime: 0.010202
Content-Length: 98
200 OK
```


```json
{
  "email": "email12@example.com",
  "full_name": null,
  "subscribed": null,
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
user[email]=email11%40example.com&user[password]=secret
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
X-Spree-Token: b913a999d237fde59214a5c2d62b20f3241f15ca19dfd512
ETag: W/&quot;dd3c07a060a6de22b115648a7796de81&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 9b6d9d5b-17f3-4f50-afdd-74a0406a1afd
X-Runtime: 0.009298
Content-Length: 553
200 OK
```


```json
{
  "id": 332,
  "email": "email11@example.com",
  "persistence_token": null,
  "perishable_token": null,
  "last_request_at": null,
  "login": "email11@example.com",
  "ship_address_id": null,
  "bill_address_id": null,
  "created_at": "2019-07-18T15:46:01.427Z",
  "updated_at": "2019-07-18T15:46:01.432Z",
  "spree_api_key": "b913a999d237fde59214a5c2d62b20f3241f15ca19dfd512",
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
X-Spree-Token: 8c184ac9279cc10ace1073a5a706dfb3041f7e172360c3f0
ETag: W/&quot;b3c27e8536053504b89c3bceb31aa656&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: e6c8dad4-bfff-467d-9fcb-4d3d757cb5e4
X-Runtime: 0.030440
Content-Length: 157
201 Created
```


```json
{
  "id": 333,
  "email": "test@example.com",
  "created_at": "2019-07-18T15:46:01.455Z",
  "updated_at": "2019-07-18T15:46:01.458Z",
  "bill_address": null,
  "ship_address": null
}
```



# Variant



## Fetching a variant


### Request

#### Endpoint

```plaintext
GET /api/variants/735
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
ETag: W/&quot;8bfe1123e455c2d99cf262e42519e6c8&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 2259a878-f515-42e1-9629-a03f72837031
X-Runtime: 0.086769
Content-Length: 1454
200 OK
```


```json
{
  "id": 735,
  "name": "Product #7 - 3455",
  "sku": "SKU-13",
  "price": "10.0",
  "weight": "0.0",
  "height": null,
  "width": null,
  "depth": null,
  "is_master": false,
  "slug": "product-7-3455",
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
      "attachment_updated_at": "2019-07-18T15:45:59.690Z",
      "attachment_width": 489,
      "attachment_height": 490,
      "alt": null,
      "viewable_type": "Spree::Variant",
      "viewable_id": 735,
      "mini_url": "/spree/products/2/mini/thinking-cat.jpg?1563464759",
      "small_url": "/spree/products/2/small/thinking-cat.jpg?1563464759",
      "product_url": "/spree/products/2/product/thinking-cat.jpg?1563464759",
      "large_url": "/spree/products/2/large/thinking-cat.jpg?1563464759"
    }
  ],
  "variant_properties": [

  ],
  "stock_items": [

  ],
  "prices": [
    {
      "id": 1428,
      "vendor_id": 2409,
      "price": "10.0",
      "original_price": "10.0",
      "discount_percent": 0.0,
      "total_on_hand": 0,
      "country_iso": null,
      "final_sale": false,
      "on_sale": false
    },
    {
      "id": 1429,
      "vendor_id": 2410,
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



