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
PUT /api/orders/R993398005/addresses/557
Accept: application/json
X-Spree-Order-Token: 9t6PYVCAMy1TKyEImvixsg
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
ETag: W/&quot;a7ef95263c5f0294b7243bebba07f5f6&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: c1fd8a8b-0ddb-4fd9-9232-f101affd9746
X-Runtime: 0.056248
Content-Length: 513
200 OK
```


```json
{
  "id": 558,
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
  "country_id": 341,
  "country_iso": "US",
  "state_id": 330,
  "state_name": null,
  "state_text": "AL",
  "country": {
    "id": 341,
    "iso_name": "UNITED STATES",
    "iso": "US",
    "iso3": "USA",
    "name": "United States",
    "numcode": 840
  },
  "state": {
    "id": 330,
    "name": "Alabama",
    "abbr": "AL",
    "country_id": 341
  }
}
```



# Checkout



## Processing the checkout payment step


### Request

#### Endpoint

```plaintext
PATCH /api/checkouts/R231436899
Accept: application/json
X-Spree-Order-Token: 1mUp7jbPcbwGk0ma9VYKcw
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
ETag: W/&quot;ba26dcae27c4c47b3308fa5cb1f35774&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 1360614e-5336-412e-99c5-8c03150bc4b5
X-Runtime: 0.162502
Content-Length: 3894
200 OK
```


```json
{
  "id": 277,
  "number": "R231436899",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 311,
  "created_at": "2019-07-09T11:51:54.835Z",
  "updated_at": "2019-07-09T11:51:55.203Z",
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
  "token": "1mUp7jbPcbwGk0ma9VYKcw",
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
    "id": 559,
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
    "country_id": 342,
    "country_iso": "US",
    "state_id": 331,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 342,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 331,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 342
    }
  },
  "ship_address": {
    "id": 560,
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
    "country_id": 342,
    "country_iso": "US",
    "state_id": 331,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 342,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 331,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 342
    }
  },
  "line_items": [
    {
      "id": 265,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 699,
      "vendor_id": 2298,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "variant": {
        "id": 699,
        "name": "Product #6 - 4936",
        "sku": "SKU-8",
        "price": "10.0",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-6-4936",
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
            "name": "Size-3",
            "presentation": "S",
            "option_type_name": "foo-size-3",
            "option_type_id": 229,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 481
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
      "id": 226,
      "tracking": null,
      "tracking_url": null,
      "number": "H16724588307",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R231436899",
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
              "id": 142,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 297,
              "name": "ShippingCategory #4"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 699,
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
PATCH /api/checkouts/R495048133
Accept: application/json
X-Spree-Order-Token: EsG9UkJy5lJ2NIVeandbEg
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=209&order[payment_attributes][][source_attributes][wallet_payment_source_id]=16
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
ETag: W/&quot;72061e860ffad0997cc2495b298d20cb&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: ad7249ec-2710-41cb-a9dd-31320b97a4be
X-Runtime: 0.083007
Content-Length: 3895
200 OK
```


```json
{
  "id": 278,
  "number": "R495048133",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 312,
  "created_at": "2019-07-09T11:51:55.496Z",
  "updated_at": "2019-07-09T11:51:55.712Z",
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
  "token": "EsG9UkJy5lJ2NIVeandbEg",
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
    "id": 561,
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
  },
  "ship_address": {
    "id": 562,
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
  },
  "line_items": [
    {
      "id": 266,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 701,
      "vendor_id": 2304,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "variant": {
        "id": 701,
        "name": "Product #7 - 6296",
        "sku": "SKU-10",
        "price": "10.0",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-7-6296",
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
            "name": "Size-4",
            "presentation": "S",
            "option_type_name": "foo-size-4",
            "option_type_id": 230,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 482
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
      "id": 228,
      "tracking": null,
      "tracking_url": null,
      "number": "H38488076722",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R495048133",
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
              "id": 143,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 298,
              "name": "ShippingCategory #5"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 701,
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
PATCH /api/checkouts/R211748251
Accept: application/json
X-Spree-Order-Token: E2FbsoLrzFLHcNZAQ_Hvdw
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=210&order[payment_attributes][][source_attributes][nonce]=fake-valid-visa-nonce&order[payment_attributes][][source_attributes][payment_type]=CreditCard
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
ETag: W/&quot;d1fafcb43a1b4da317a85baa3032af61&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: af44edc3-3713-4cbb-8e41-d4fc4407489f
X-Runtime: 0.087301
Content-Length: 3895
200 OK
```


```json
{
  "id": 279,
  "number": "R211748251",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 313,
  "created_at": "2019-07-09T11:51:55.996Z",
  "updated_at": "2019-07-09T11:51:56.221Z",
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
  "token": "E2FbsoLrzFLHcNZAQ_Hvdw",
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
    "id": 563,
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
    "country_id": 344,
    "country_iso": "US",
    "state_id": 333,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 344,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 333,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 344
    }
  },
  "ship_address": {
    "id": 564,
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
    "country_id": 344,
    "country_iso": "US",
    "state_id": 333,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 344,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 333,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 344
    }
  },
  "line_items": [
    {
      "id": 267,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 703,
      "vendor_id": 2310,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "variant": {
        "id": 703,
        "name": "Product #8 - 6757",
        "sku": "SKU-12",
        "price": "10.0",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-8-6757",
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
            "name": "Size-5",
            "presentation": "S",
            "option_type_name": "foo-size-5",
            "option_type_id": 231,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 483
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
      "id": 230,
      "tracking": null,
      "tracking_url": null,
      "number": "H61416430865",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R211748251",
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
              "id": 144,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 299,
              "name": "ShippingCategory #6"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 703,
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
PATCH /api/checkouts/R970572895
Accept: application/json
X-Spree-Order-Token: yq5IBoYqXqkesxT1Ho4Aag
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=211&order[payment_attributes][][source_attributes][nonce]=fake-apple-pay-visa-nonce&order[payment_attributes][][source_attributes][payment_type]=ApplePayCard
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
ETag: W/&quot;cf818c233f283492c0305ddf237c73cf&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: d07990a7-4542-42f8-be01-8fd1b530002c
X-Runtime: 0.087511
Content-Length: 3896
200 OK
```


```json
{
  "id": 280,
  "number": "R970572895",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 314,
  "created_at": "2019-07-09T11:51:56.476Z",
  "updated_at": "2019-07-09T11:51:56.678Z",
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
  "token": "yq5IBoYqXqkesxT1Ho4Aag",
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
    "id": 565,
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
    "country_id": 345,
    "country_iso": "US",
    "state_id": 334,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 345,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 334,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 345
    }
  },
  "ship_address": {
    "id": 566,
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
    "country_id": 345,
    "country_iso": "US",
    "state_id": 334,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 345,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 334,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 345
    }
  },
  "line_items": [
    {
      "id": 268,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 705,
      "vendor_id": 2316,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "variant": {
        "id": 705,
        "name": "Product #9 - 6031",
        "sku": "SKU-14",
        "price": "10.0",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-9-6031",
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
            "name": "Size-6",
            "presentation": "S",
            "option_type_name": "foo-size-6",
            "option_type_id": 232,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 484
      },
      "vendor_name": "Vendor #32",
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
      "number": "H57843542246",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R970572895",
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
              "id": 145,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 300,
              "name": "ShippingCategory #7"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 705,
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
PATCH /api/checkouts/R390739779
Accept: application/json
X-Spree-Order-Token: fTAPQMtvqWd-nNvs3nbKSA
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=212&order[payment_attributes][][source_attributes][nonce]=fake-paypal-billing-agreement-nonce&order[payment_attributes][][source_attributes][payment_type]=PayPalAccount
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
ETag: W/&quot;8469d6c20a1e80ef850715ea34f7ec5e&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: ccb53983-c9e2-453f-a6be-c9a9e23b1059
X-Runtime: 0.087110
Content-Length: 3898
200 OK
```


```json
{
  "id": 281,
  "number": "R390739779",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 315,
  "created_at": "2019-07-09T11:51:56.942Z",
  "updated_at": "2019-07-09T11:51:57.128Z",
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
  "token": "fTAPQMtvqWd-nNvs3nbKSA",
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
    "id": 567,
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
    "country_id": 346,
    "country_iso": "US",
    "state_id": 335,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 346,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 335,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 346
    }
  },
  "ship_address": {
    "id": 568,
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
    "country_id": 346,
    "country_iso": "US",
    "state_id": 335,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 346,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 335,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 346
    }
  },
  "line_items": [
    {
      "id": 269,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 707,
      "vendor_id": 2322,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "variant": {
        "id": 707,
        "name": "Product #10 - 3950",
        "sku": "SKU-16",
        "price": "10.0",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-10-3950",
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
            "name": "Size-7",
            "presentation": "S",
            "option_type_name": "foo-size-7",
            "option_type_id": 233,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 485
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
      "id": 234,
      "tracking": null,
      "tracking_url": null,
      "number": "H06575242810",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R390739779",
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
              "id": 146,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 301,
              "name": "ShippingCategory #8"
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
PATCH /api/checkouts/R028926586
Accept: application/json
X-Spree-Order-Token: GCSk5Vkq975gs2SWXMpqsw
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=213&order[payment_attributes][][source_attributes][wallet_payment_source_id]=17
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
ETag: W/&quot;29fda316584f5a4de9090be320a58bd0&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: d4183678-6ff3-4baa-8eee-1c72db10e740
X-Runtime: 0.079087
Content-Length: 3898
200 OK
```


```json
{
  "id": 282,
  "number": "R028926586",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 316,
  "created_at": "2019-07-09T11:51:57.394Z",
  "updated_at": "2019-07-09T11:51:57.642Z",
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
  "token": "GCSk5Vkq975gs2SWXMpqsw",
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
    "id": 569,
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
    "country_id": 347,
    "country_iso": "US",
    "state_id": 336,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 347,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 336,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 347
    }
  },
  "ship_address": {
    "id": 570,
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
    "country_id": 347,
    "country_iso": "US",
    "state_id": 336,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 347,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 336,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 347
    }
  },
  "line_items": [
    {
      "id": 270,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 709,
      "vendor_id": 2328,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "variant": {
        "id": 709,
        "name": "Product #11 - 1026",
        "sku": "SKU-18",
        "price": "10.0",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-11-1026",
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
            "name": "Size-8",
            "presentation": "S",
            "option_type_name": "foo-size-8",
            "option_type_id": 234,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 486
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
      "id": 236,
      "tracking": null,
      "tracking_url": null,
      "number": "H42028878784",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R028926586",
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
              "id": 147,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 302,
              "name": "ShippingCategory #9"
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



# LineItem

Representation of a single cart item for a specific variant with price of vendor

## Creating a line item


### Request

#### Endpoint

```plaintext
POST /api/orders/R543828223/line_items
Accept: application/json
X-Spree-Order-Token: Z6S7bcH2yJ_aoOODaODRtw
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/:order_number/line_items`

#### Parameters


```json
line_item[variant_id]=696&line_item[options][vendor_id]=2289
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
ETag: W/&quot;0a7961e4b15c9c532fc93970dfa6beb2&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: a6e7b940-44dd-4e39-b7a1-40d854a1e0cb
X-Runtime: 0.072667
Content-Length: 731
201 Created
```


```json
{
  "id": 263,
  "quantity": 1,
  "price": "19.99",
  "variant_id": 696,
  "vendor_id": 2289,
  "single_display_amount": "$19.99",
  "display_amount": "$19.99",
  "total": "19.99",
  "variant": {
    "id": 696,
    "name": "Product #4 - 6124",
    "sku": "SKU-5",
    "price": "19.99",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": false,
    "slug": "product-4-6124",
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
        "id": 228,
        "name": "Size-2",
        "presentation": "S",
        "option_type_name": "foo-size-2",
        "option_type_id": 228,
        "option_type_presentation": "Size"
      }
    ],
    "images": [

    ],
    "product_id": 479
  },
  "vendor_name": "Vendor #9",
  "adjustments": [

  ]
}
```



## Deleting a line item


### Request

#### Endpoint

```plaintext
DELETE /api/orders/R906370662/line_items/264
Accept: application/json
X-Spree-Order-Token: PdtxpDSCfQDescZiqlrxMQ
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
X-Request-Id: a39518d7-1f32-4cf8-af19-c4bb9cfa97e0
X-Runtime: 0.073050
204 No Content
```




## Updating a line item


### Request

#### Endpoint

```plaintext
PUT /api/orders/R200115980/line_items/261
Accept: application/json
X-Spree-Order-Token: o8V9L41RahAD7MyDgmvKyg
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
ETag: W/&quot;bb39af3c555f6923b38cf85411f67a6e&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 43553654-6e7e-490c-a9e1-630d412a1808
X-Runtime: 0.286878
Content-Length: 589
200 OK
```


```json
{
  "id": 261,
  "quantity": 2,
  "price": "10.0",
  "variant_id": 691,
  "vendor_id": 2281,
  "single_display_amount": "$10.00",
  "display_amount": "$20.00",
  "total": "20.0",
  "variant": {
    "id": 691,
    "name": "Product #1 - 8710",
    "sku": "SKU-1",
    "price": "19.99",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": true,
    "slug": "product-1-8710",
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
    "product_id": 476
  },
  "vendor_name": "Vendor #2",
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
X-Spree-Token: 87942cd1bf324d4b1384830930f9ebe046468f1d288c0029
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
X-Request-Id: 0c7f65ad-cd1c-40e8-9202-ca9e7787f4e1
X-Runtime: 0.020433
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
Date: Tue, 09 Jul 2019 11:51:57 GMT
Surrogate-Control: max-age=900
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;e655ee8fa2a2ac734d14ffa236068729&quot;
X-Request-Id: 795b0ae7-8103-457f-ac4b-aa1870455bcf
X-Runtime: 0.107179
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
      "id": 487,
      "name": "Product #12 - 2915",
      "description": "As seen on TV!",
      "price": "19.99",
      "display_price": "$19.99",
      "available_on": "2018-07-09T11:51:57.710Z",
      "slug": "product-12-2915",
      "meta_description": null,
      "meta_keywords": null,
      "shipping_category_id": 303,
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
        "id": 710,
        "name": "Product #12 - 2915",
        "sku": "SKU-20",
        "price": "19.99",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-12-2915",
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
GET /api/products/product-13-6507
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
Date: Tue, 09 Jul 2019 11:51:58 GMT
Surrogate-Control: max-age=900
Surrogate-Key: product_id=1
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;c354c1895d48e863ffd4a0cfb8bcf34a&quot;
X-Request-Id: 8f0eb713-afcb-416c-aac4-17aeaf07dbe0
X-Runtime: 0.053606
Content-Length: 833
200 OK
```


```json
{
  "id": 488,
  "name": "Product #13 - 6507",
  "description": "As seen on TV!",
  "price": "19.99",
  "display_price": "$19.99",
  "available_on": "2018-07-09T11:51:57.926Z",
  "slug": "product-13-6507",
  "meta_description": null,
  "meta_keywords": null,
  "shipping_category_id": 304,
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
    "id": 711,
    "name": "Product #13 - 6507",
    "sku": "SKU-21",
    "price": "19.99",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": true,
    "slug": "product-13-6507",
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
X-Request-Id: 973baf57-742c-411d-a878-3893c3248851
X-Runtime: 0.016384
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
ETag: W/&quot;1682b45ea159370fc43ad71f3859ea8c&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 6cf5aec6-d27e-42ab-9f71-6f20a565aead
X-Runtime: 0.008712
Content-Length: 193
200 OK
```


```json
[
  {
    "id": 597,
    "name": "Kids",
    "permalink": "category/kids",
    "parent_id": 595,
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
X-Request-Id: dbad275f-8624-4c41-aec0-f28bbe6f7928
X-Runtime: 0.004727
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
ETag: W/&quot;66c3e656e0577d6c326a37cd5e8be869&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: a978ed75-986f-424d-94aa-72a8bf4c1174
X-Runtime: 0.009909
Content-Length: 411
200 OK
```


```json
[
  {
    "id": 589,
    "name": "Ruby on Rails",
    "permalink": "brand/ruby-on-rails",
    "parent_id": 588,
    "depth": 1,
    "position": 0,
    "brand_taxon?": true,
    "brand_all": true,
    "brand_discover": false,
    "highlight": false,
    "header_link": false
  },
  {
    "id": 590,
    "name": "Ruby on Rails",
    "permalink": "brand/ruby-on-rails",
    "parent_id": 588,
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
ETag: W/&quot;86e6581a94912a8ac9ab66134e412afc&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 09666d12-73e4-49ac-b6af-3331e4ddf96b
X-Runtime: 0.009004
Content-Length: 211
200 OK
```


```json
[
  {
    "id": 594,
    "name": "Ruby on Rails",
    "permalink": "category/ruby-on-rails",
    "parent_id": 593,
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

Validate user email and password. Does not handle any session and only return the user

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
X-Spree-Token: 2fe5a8456543eeea6b11354f3bde6b2cbe4b8f054d2bdb6f
ETag: W/&quot;1a9f567d5636b5734f689c3385ac7b1a&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: cfdd9196-8a8d-47bb-aa11-a9eec17f3f5b
X-Runtime: 0.007414
Content-Length: 551
200 OK
```


```json
{
  "id": 309,
  "email": "email6@example.com",
  "persistence_token": null,
  "perishable_token": null,
  "last_request_at": null,
  "login": "email6@example.com",
  "ship_address_id": null,
  "bill_address_id": null,
  "created_at": "2019-07-09T11:51:54.583Z",
  "updated_at": "2019-07-09T11:51:54.587Z",
  "spree_api_key": "2fe5a8456543eeea6b11354f3bde6b2cbe4b8f054d2bdb6f",
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
X-Spree-Token: 4acfac67b44530f17d7d15eccd267aaf1596f77c5652e41b
ETag: W/&quot;80c152fbc14c5948eceacfb309e43d75&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: af83a4e8-356c-4bd9-9413-f006f23064a9
X-Runtime: 0.028372
Content-Length: 157
201 Created
```


```json
{
  "id": 310,
  "email": "test@example.com",
  "created_at": "2019-07-09T11:51:54.603Z",
  "updated_at": "2019-07-09T11:51:54.605Z",
  "bill_address": null,
  "ship_address": null
}
```



# Variant



## Fetching a variant


### Request

#### Endpoint

```plaintext
GET /api/variants/714
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
ETag: W/&quot;1e6c335e5d4bf41db190c31d3452473e&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: f8757dab-8335-472c-884c-acdca10ff6f3
X-Runtime: 0.078053
Content-Length: 1378
200 OK
```


```json
{
  "id": 714,
  "name": "Product #15 - 176",
  "sku": "SKU-23",
  "price": "10.0",
  "weight": "0.0",
  "height": null,
  "width": null,
  "depth": null,
  "is_master": false,
  "slug": "product-15-176",
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
      "id": 235,
      "name": "Size-9",
      "presentation": "S",
      "option_type_name": "foo-size-9",
      "option_type_id": 235,
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
      "attachment_updated_at": "2019-07-09T11:51:58.383Z",
      "attachment_width": 489,
      "attachment_height": 490,
      "alt": null,
      "viewable_type": "Spree::Variant",
      "viewable_id": 714,
      "mini_url": "/spree/products/2/mini/thinking-cat.jpg?1562673118",
      "small_url": "/spree/products/2/small/thinking-cat.jpg?1562673118",
      "product_url": "/spree/products/2/product/thinking-cat.jpg?1562673118",
      "large_url": "/spree/products/2/large/thinking-cat.jpg?1562673118"
    }
  ],
  "variant_properties": [

  ],
  "stock_items": [

  ],
  "prices": [
    {
      "id": 1387,
      "price": "10.0",
      "vendor_id": 2349,
      "display_price": "$10.00",
      "total_on_hand": 0,
      "country_iso": null,
      "final_sale": false
    },
    {
      "id": 1388,
      "price": "20.0",
      "vendor_id": 2350,
      "display_price": "$20.00",
      "total_on_hand": 0,
      "country_iso": null,
      "final_sale": false
    }
  ]
}
```



