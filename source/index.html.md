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
PUT /api/orders/R723755558/addresses/1047
Accept: application/json
X-Spree-Order-Token: 6ZJpgVH8_M7UQXnATnGitw
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
ETag: W/&quot;d05db24ed7e33c9e74b0504967fc17d8&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 94703160-1fc4-42a4-a50a-493fbd774dd4
X-Runtime: 0.054236
Content-Length: 514
200 OK
```


```json
{
  "id": 1048,
  "firstname": "John the Tester",
  "lastname": null,
  "full_name": "John the Tester",
  "address1": "A Different Road",
  "address2": "Northwest",
  "city": "Herndon",
  "zipcode": "10036",
  "phone": "555-555-0199",
  "company": "Company",
  "alternative_phone": "555-555-0199",
  "country_id": 500,
  "country_iso": "US",
  "state_id": 489,
  "state_name": null,
  "state_text": "AL",
  "country": {
    "id": 500,
    "iso_name": "UNITED STATES",
    "iso": "US",
    "iso3": "USA",
    "name": "United States",
    "numcode": 840
  },
  "state": {
    "id": 489,
    "name": "Alabama",
    "abbr": "AL",
    "country_id": 500
  }
}
```



# Braintree transactions



## Creating a PayPal express checkout transaction


### Request

#### Endpoint

```plaintext
POST /api/braintree/transactions
Accept: application/json
X-Spree-Order-Token: _HH9OtjtxHEyoCD8ximbJg
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/braintree/transactions`

#### Parameters


```json
order_id=R430125734&payment_method_id=417&options[restart_checkout]=true&transaction[email]=maryellen.oga%40mckenziemcglynn.com&transaction[nonce]=fake-paypal-billing-agreement-nonce&transaction[phone]=555-555-0199&transaction[address_attributes][first_name]=John&transaction[address_attributes][last_name]=Stamm&transaction[address_attributes][address_line_1]=A+Different+Road&transaction[address_attributes][city]=Herndon&transaction[address_attributes][state_code]=AL&transaction[address_attributes][zip]=10033&transaction[address_attributes][country_code]=US&transaction[payment_type]=PayPalAccount
```


| Name | Description |
|:-----|:------------|
| order_id *required* | The order number |
| payment_method_id *required* | The payment method id |
| options[restart_checkout] *required* | Whether the checkout should restart from the beginning (must be set for express checkouts) |
| transaction[email] *required* | The transaction user email |
| transaction[nonce] *required* | The transaction nonce |
| transaction[phone] *required* | The transaction user phone number |
| transaction[address_attributes][first_name] *required* | The transaction address first name |
| transaction[address_attributes][last_name] *required* | The transaction address last name |
| transaction[address_attributes][address_line_1] *required* | The transaction address line 1 |
| transaction[address_attributes][city] *required* | The transaction address city |
| transaction[address_attributes][state_code] *required* | The transaction address state code |
| transaction[address_attributes][zip] *required* | The transaction address zip code |
| transaction[address_attributes][country_code] *required* | The transaction address country code |
| transaction[payment_type] *required* | The payment type. Must be `PayPalAccount` |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
ETag: W/&quot;5045c4a3384c51ec1eaeb2509885d5b1&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 769838ba-7743-4cb7-a08a-1f9c5a8e280d
X-Runtime: 0.283056
Content-Length: 4695
200 OK
```


```json
{
  "id": 503,
  "number": "R430125734",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2019-08-05T19:32:46.577Z",
  "updated_at": "2019-08-05T19:32:46.850Z",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "maryellen.oga@mckenziemcglynn.com",
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
  "token": "_HH9OtjtxHEyoCD8ximbJg",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 417,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 1045,
    "firstname": "John",
    "lastname": "Stamm",
    "full_name": "John Stamm",
    "address1": "A Different Road",
    "address2": null,
    "city": "Herndon",
    "zipcode": "10033",
    "phone": "555-555-0199",
    "company": null,
    "alternative_phone": null,
    "country_id": 499,
    "country_iso": "US",
    "state_id": 488,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 499,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 488,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 499
    }
  },
  "ship_address": {
    "id": 1045,
    "firstname": "John",
    "lastname": "Stamm",
    "full_name": "John Stamm",
    "address1": "A Different Road",
    "address2": null,
    "city": "Herndon",
    "zipcode": "10033",
    "phone": "555-555-0199",
    "company": null,
    "alternative_phone": null,
    "country_id": 499,
    "country_iso": "US",
    "state_id": 488,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 499,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 488,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 499
    }
  },
  "line_items": [
    {
      "id": 435,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 1183,
      "vendor_id": 3487,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 1183,
        "name": "Product #27 - 9820",
        "sku": "SKU-46",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-27-9820",
        "description": "As seen on TV!",
        "track_inventory": true,
        "price": "10.0",
        "display_price": "$10.00",
        "options_text": "Size: S",
        "in_stock": true,
        "is_backorderable": true,
        "total_on_hand": 10,
        "is_destroyed": false,
        "option_values": [
          {
            "id": 486,
            "name": "Size-20",
            "presentation": "S",
            "option_type_name": "foo-size-20",
            "option_type_id": 486,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 709,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #118",
      "adjustments": [

      ]
    }
  ],
  "payments": [
    {
      "id": 202,
      "source_type": "SolidusPaypalBraintree::Source",
      "source_id": 61,
      "amount": "110.0",
      "display_amount": "$110.00",
      "payment_method_id": 417,
      "state": "checkout",
      "avs_response": null,
      "created_at": "2019-08-05T19:32:46.699Z",
      "updated_at": "2019-08-05T19:32:46.699Z",
      "payment_method": {
        "id": 417,
        "name": "Braintree"
      },
      "source": {
        "id": 61,
        "payment_type": "PayPalAccount",
        "token": "bgx899",
        "created_at": "2019-08-05T19:32:46.698Z",
        "email": "jane.doe@paypal.com"
      }
    }
  ],
  "shipments": [
    {
      "id": 357,
      "tracking": null,
      "tracking_url": null,
      "number": "H75773733033",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R430125734",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 341,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 336,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 341,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 336,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 336,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 245,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 447,
              "name": "ShippingCategory #23"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 1183,
          "quantity": 1,
          "states": {
            "on_hand": 1
          }
        }
      ],
      "adjustments": [

      ],
      "stock_location_address": "NY Warehouse, Washington, AL"
    }
  ],
  "adjustments": [

  ],
  "permissions": {
    "can_update": false
  },
  "credit_cards": [

  ],
  "subtotals": {
    "order_total": "110.0",
    "item_total": "10.0",
    "shipments_total": "100.0",
    "line_item_promotions": [

    ],
    "tax_adjustments": [

    ],
    "miscellaneous_adjustments": [

    ],
    "giftwrap_amount": 0
  }
}
```



## Creating an ApplePay one-click checkout transaction


### Request

#### Endpoint

```plaintext
POST /api/braintree/transactions
Accept: application/json
X-Spree-Order-Token: WfSq_tHAkkgM5KrblU3yKw
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/braintree/transactions`

#### Parameters


```json
order_id=R433317725&payment_method_id=416&options[restart_checkout]=true&transaction[email]=maryellen.oga%40mckenziemcglynn.com&transaction[nonce]=fake-apple-pay-visa-nonce&transaction[phone]=555-555-0199&transaction[address_attributes][first_name]=John&transaction[address_attributes][last_name]=Stamm&transaction[address_attributes][address_line_1]=A+Different+Road&transaction[address_attributes][city]=Herndon&transaction[address_attributes][state_code]=AL&transaction[address_attributes][zip]=10031&transaction[address_attributes][country_code]=US&transaction[payment_type]=ApplePayCard
```


| Name | Description |
|:-----|:------------|
| order_id *required* | The order number |
| payment_method_id *required* | The payment method id |
| options[restart_checkout] *required* | Whether the checkout should restart from the beginning (must be set for express checkouts) |
| transaction[email] *required* | The transaction user email |
| transaction[nonce] *required* | The transaction nonce |
| transaction[phone] *required* | The transaction user phone number |
| transaction[address_attributes][first_name] *required* | The transaction address first name |
| transaction[address_attributes][last_name] *required* | The transaction address last name |
| transaction[address_attributes][address_line_1] *required* | The transaction address line 1 |
| transaction[address_attributes][city] *required* | The transaction address city |
| transaction[address_attributes][state_code] *required* | The transaction address state code |
| transaction[address_attributes][zip] *required* | The transaction address zip code |
| transaction[address_attributes][country_code] *required* | The transaction address country code |
| transaction[payment_type] *required* | The payment type. Must be `ApplePayCard` |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
ETag: W/&quot;c3d893b09eeee15b76e57f42b1b51b19&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: dcfcb4ab-097a-4121-8c04-f80bf3bc7e2d
X-Runtime: 0.320562
Content-Length: 4711
200 OK
```


```json
{
  "id": 502,
  "number": "R433317725",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2019-08-05T19:32:45.861Z",
  "updated_at": "2019-08-05T19:32:46.176Z",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "maryellen.oga@mckenziemcglynn.com",
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
  "token": "WfSq_tHAkkgM5KrblU3yKw",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 416,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 1042,
    "firstname": "John",
    "lastname": "Stamm",
    "full_name": "John Stamm",
    "address1": "A Different Road",
    "address2": null,
    "city": "Herndon",
    "zipcode": "10031",
    "phone": "555-555-0199",
    "company": null,
    "alternative_phone": null,
    "country_id": 498,
    "country_iso": "US",
    "state_id": 487,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 498,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 487,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 498
    }
  },
  "ship_address": {
    "id": 1042,
    "firstname": "John",
    "lastname": "Stamm",
    "full_name": "John Stamm",
    "address1": "A Different Road",
    "address2": null,
    "city": "Herndon",
    "zipcode": "10031",
    "phone": "555-555-0199",
    "company": null,
    "alternative_phone": null,
    "country_id": 498,
    "country_iso": "US",
    "state_id": 487,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 498,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 487,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 498
    }
  },
  "line_items": [
    {
      "id": 434,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 1181,
      "vendor_id": 3481,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 1181,
        "name": "Product #26 - 4549",
        "sku": "SKU-44",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-26-4549",
        "description": "As seen on TV!",
        "track_inventory": true,
        "price": "10.0",
        "display_price": "$10.00",
        "options_text": "Size: S",
        "in_stock": true,
        "is_backorderable": true,
        "total_on_hand": 10,
        "is_destroyed": false,
        "option_values": [
          {
            "id": 485,
            "name": "Size-19",
            "presentation": "S",
            "option_type_name": "foo-size-19",
            "option_type_id": 485,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 708,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #113",
      "adjustments": [

      ]
    }
  ],
  "payments": [
    {
      "id": 201,
      "source_type": "SolidusPaypalBraintree::Source",
      "source_id": 60,
      "amount": "110.0",
      "display_amount": "$110.00",
      "payment_method_id": 416,
      "state": "checkout",
      "avs_response": null,
      "created_at": "2019-08-05T19:32:46.015Z",
      "updated_at": "2019-08-05T19:32:46.015Z",
      "payment_method": {
        "id": 416,
        "name": "Braintree"
      },
      "source": {
        "id": 60,
        "payment_type": "ApplePayCard",
        "token": "cg7hsk",
        "created_at": "2019-08-05T19:32:46.014Z",
        "card_type": "Apple Pay - Visa",
        "last_4": "1881"
      }
    }
  ],
  "shipments": [
    {
      "id": 355,
      "tracking": null,
      "tracking_url": null,
      "number": "H21801640028",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R433317725",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 339,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 335,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 339,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 335,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 335,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 244,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 446,
              "name": "ShippingCategory #22"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 1181,
          "quantity": 1,
          "states": {
            "on_hand": 1
          }
        }
      ],
      "adjustments": [

      ],
      "stock_location_address": "NY Warehouse, Washington, AL"
    }
  ],
  "adjustments": [

  ],
  "permissions": {
    "can_update": false
  },
  "credit_cards": [

  ],
  "subtotals": {
    "order_total": "110.0",
    "item_total": "10.0",
    "shipments_total": "100.0",
    "line_item_promotions": [

    ],
    "tax_adjustments": [

    ],
    "miscellaneous_adjustments": [

    ],
    "giftwrap_amount": 0
  }
}
```



# Checkout



## Completing the checkout when the order includes a Braintree payment


### Request

#### Endpoint

```plaintext
PUT /api/checkouts/R290040064/complete
Accept: application/json
X-Spree-Order-Token: 3YyQGpwqKQo5e1IovKoCRA
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PUT /api/checkouts/:id/complete`

#### Parameters


```json
expected_total=110.0&braintree_device_data=fake+device+data
```


| Name | Description |
|:-----|:------------|
| id *required* | The order number |
| expected_total  | The amount the customer expects to pay |
| braintree_device_data  | The device_data generated by Braintree for Advanced Fraud Tools check |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
ETag: W/&quot;26d771179c7bf6077fca75ad242ce366&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 3eb0cdbb-3972-435b-9c64-1366bdb459f4
X-Runtime: 2.294268
Content-Length: 4834
200 OK
```


```json
{
  "id": 501,
  "number": "R290040064",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "complete",
  "adjustment_total": "0.0",
  "user_id": 584,
  "created_at": "2019-08-05T19:32:40.884Z",
  "updated_at": "2019-08-05T19:32:44.180Z",
  "completed_at": "2019-08-05T19:32:44.180Z",
  "payment_total": "110.0",
  "shipment_state": "ready",
  "payment_state": "paid",
  "email": "email26@example.com",
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
  "token": "3YyQGpwqKQo5e1IovKoCRA",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 414,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    },
    {
      "id": 415,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 1038,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "PO Box 1337",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10029",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 496,
    "country_iso": "US",
    "state_id": 485,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 496,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 485,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 496
    }
  },
  "ship_address": {
    "id": 1039,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "A Different Road",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10030",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 496,
    "country_iso": "US",
    "state_id": 485,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 496,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 485,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 496
    }
  },
  "line_items": [
    {
      "id": 433,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 1177,
      "vendor_id": 3467,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 1177,
        "name": "Product #24 - 1711",
        "sku": "SKU-40",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-24-1711",
        "description": "As seen on TV!",
        "track_inventory": true,
        "price": "10.0",
        "display_price": "$10.00",
        "options_text": "Size: S",
        "in_stock": true,
        "is_backorderable": true,
        "total_on_hand": 9,
        "is_destroyed": false,
        "option_values": [
          {
            "id": 483,
            "name": "Size-17",
            "presentation": "S",
            "option_type_name": "foo-size-17",
            "option_type_id": 483,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 706,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #101",
      "adjustments": [

      ]
    }
  ],
  "payments": [
    {
      "id": 200,
      "source_type": "SolidusPaypalBraintree::Source",
      "source_id": 59,
      "amount": "110.0",
      "display_amount": "$110.00",
      "payment_method_id": 414,
      "state": "completed",
      "avs_response": "M",
      "created_at": "2019-08-05T19:32:40.997Z",
      "updated_at": "2019-08-05T19:32:44.020Z",
      "payment_method": {
        "id": 414,
        "name": "Braintree"
      },
      "source": {
        "id": 59,
        "payment_type": "CreditCard",
        "token": "72qr2z",
        "created_at": "2019-08-05T19:32:40.995Z",
        "cc_type": "Visa",
        "last_digits": "1881"
      }
    }
  ],
  "shipments": [
    {
      "id": 353,
      "tracking": "U10000",
      "tracking_url": null,
      "number": "H80580841566",
      "cost": "100.0",
      "shipped_at": null,
      "state": "ready",
      "order_id": "R290040064",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 337,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 334,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 337,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 334,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 334,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 243,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 444,
              "name": "ShippingCategory #20"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 1177,
          "quantity": 1,
          "states": {
            "on_hand": 1
          }
        }
      ],
      "adjustments": [

      ],
      "stock_location_address": "NY Warehouse, Washington, AL"
    }
  ],
  "adjustments": [

  ],
  "permissions": {
    "can_update": false
  },
  "credit_cards": [

  ],
  "subtotals": {
    "order_total": "110.0",
    "item_total": "10.0",
    "shipments_total": "100.0",
    "line_item_promotions": [

    ],
    "tax_adjustments": [

    ],
    "miscellaneous_adjustments": [

    ],
    "giftwrap_amount": 0
  }
}
```



## Processing the checkout payment step with a not yet existing ApplePay payment


### Request

#### Endpoint

```plaintext
PATCH /api/checkouts/R699314194
Accept: application/json
X-Spree-Order-Token: ZYOlildmekMFXG4bZOnAsw
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=411&order[payment_attributes][][source_attributes][nonce]=fake-apple-pay-visa-nonce&order[payment_attributes][][source_attributes][payment_type]=ApplePayCard
```


| Name | Description |
|:-----|:------------|
| id *required* | The order number |
| order[payment_attributes] *required* | The payment attibutes |
| order[payment_attributes][payment_method_id] *required* | The payment method id |
| order[payment_attributes][source_attributes][nonce] *required* | The payment nonce |
| order[payment_attributes][source_attributes][payment_type] *required* | The payment type. Must be `ApplePayCard` |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
ETag: W/&quot;dc49da4606474f917a1f50b9a138b823&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: c6ccec7b-ecf8-4097-9292-be9b139a6ae8
X-Runtime: 0.138778
Content-Length: 4257
200 OK
```


```json
{
  "id": 498,
  "number": "R699314194",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 581,
  "created_at": "2019-08-05T19:32:38.738Z",
  "updated_at": "2019-08-05T19:32:39.043Z",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "email23@example.com",
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
  "token": "ZYOlildmekMFXG4bZOnAsw",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 411,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 1032,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "PO Box 1337",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10023",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 493,
    "country_iso": "US",
    "state_id": 482,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 493,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 482,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 493
    }
  },
  "ship_address": {
    "id": 1033,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "A Different Road",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10024",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 493,
    "country_iso": "US",
    "state_id": 482,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 493,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 482,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 493
    }
  },
  "line_items": [
    {
      "id": 430,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 1171,
      "vendor_id": 3449,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 1171,
        "name": "Product #21 - 3176",
        "sku": "SKU-34",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-21-3176",
        "description": "As seen on TV!",
        "track_inventory": true,
        "price": "10.0",
        "display_price": "$10.00",
        "options_text": "Size: S",
        "in_stock": true,
        "is_backorderable": true,
        "total_on_hand": 10,
        "is_destroyed": false,
        "option_values": [
          {
            "id": 480,
            "name": "Size-14",
            "presentation": "S",
            "option_type_name": "foo-size-14",
            "option_type_id": 480,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 703,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #86",
      "adjustments": [

      ]
    }
  ],
  "payments": [

  ],
  "shipments": [
    {
      "id": 348,
      "tracking": null,
      "tracking_url": null,
      "number": "H54782132850",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R699314194",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 332,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 331,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 332,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 331,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 331,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 240,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 441,
              "name": "ShippingCategory #17"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 1171,
          "quantity": 1,
          "states": {
            "on_hand": 1
          }
        }
      ],
      "adjustments": [

      ],
      "stock_location_address": "NY Warehouse, Washington, AL"
    }
  ],
  "adjustments": [

  ],
  "permissions": {
    "can_update": false
  },
  "credit_cards": [

  ],
  "subtotals": {
    "order_total": "110.0",
    "item_total": "10.0",
    "shipments_total": "100.0",
    "line_item_promotions": [

    ],
    "tax_adjustments": [

    ],
    "miscellaneous_adjustments": [

    ],
    "giftwrap_amount": 0
  }
}
```



## Processing the checkout payment step with a not yet existing PayPal payment


### Request

#### Endpoint

```plaintext
PATCH /api/checkouts/R040497382
Accept: application/json
X-Spree-Order-Token: vPXmgRdvjtggfct61mp4-g
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=413&order[payment_attributes][][source_attributes][nonce]=fake-paypal-billing-agreement-nonce&order[payment_attributes][][source_attributes][payment_type]=PayPalAccount
```


| Name | Description |
|:-----|:------------|
| id *required* | The order number |
| order[payment_attributes] *required* | The payment attibutes |
| order[payment_attributes][payment_method_id] *required* | The payment method id |
| order[payment_attributes][source_attributes][nonce] *required* | The payment nonce |
| order[payment_attributes][source_attributes][payment_type] *required* | The payment type. Must be `PayPalAccount` |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
ETag: W/&quot;1d62aebfd745b497f493648feed2b7f7&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 3372e018-a6ba-4e19-8d86-cf5e4fb5a1f6
X-Runtime: 0.144168
Content-Length: 4257
200 OK
```


```json
{
  "id": 500,
  "number": "R040497382",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 583,
  "created_at": "2019-08-05T19:32:40.173Z",
  "updated_at": "2019-08-05T19:32:40.465Z",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "email25@example.com",
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
  "token": "vPXmgRdvjtggfct61mp4-g",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 413,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 1036,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "PO Box 1337",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10027",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 495,
    "country_iso": "US",
    "state_id": 484,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 495,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 484,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 495
    }
  },
  "ship_address": {
    "id": 1037,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "A Different Road",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10028",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 495,
    "country_iso": "US",
    "state_id": 484,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 495,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 484,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 495
    }
  },
  "line_items": [
    {
      "id": 432,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 1175,
      "vendor_id": 3461,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 1175,
        "name": "Product #23 - 5288",
        "sku": "SKU-38",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-23-5288",
        "description": "As seen on TV!",
        "track_inventory": true,
        "price": "10.0",
        "display_price": "$10.00",
        "options_text": "Size: S",
        "in_stock": true,
        "is_backorderable": true,
        "total_on_hand": 10,
        "is_destroyed": false,
        "option_values": [
          {
            "id": 482,
            "name": "Size-16",
            "presentation": "S",
            "option_type_name": "foo-size-16",
            "option_type_id": 482,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 705,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #96",
      "adjustments": [

      ]
    }
  ],
  "payments": [

  ],
  "shipments": [
    {
      "id": 352,
      "tracking": null,
      "tracking_url": null,
      "number": "H58526705766",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R040497382",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 336,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 333,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 336,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 333,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 333,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 242,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 443,
              "name": "ShippingCategory #19"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 1175,
          "quantity": 1,
          "states": {
            "on_hand": 1
          }
        }
      ],
      "adjustments": [

      ],
      "stock_location_address": "NY Warehouse, Washington, AL"
    }
  ],
  "adjustments": [

  ],
  "permissions": {
    "can_update": false
  },
  "credit_cards": [

  ],
  "subtotals": {
    "order_total": "110.0",
    "item_total": "10.0",
    "shipments_total": "100.0",
    "line_item_promotions": [

    ],
    "tax_adjustments": [

    ],
    "miscellaneous_adjustments": [

    ],
    "giftwrap_amount": 0
  }
}
```



## Processing the checkout payment step with a not yet existing credit card payment


### Request

#### Endpoint

```plaintext
PATCH /api/checkouts/R961948263
Accept: application/json
X-Spree-Order-Token: X_1UN7KXjTRxd6o44RipxQ
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=412&order[payment_attributes][][source_attributes][nonce]=fake-valid-visa-nonce&order[payment_attributes][][source_attributes][payment_type]=CreditCard
```


| Name | Description |
|:-----|:------------|
| id *required* | The order number |
| order[payment_attributes] *required* | The payment attibutes |
| order[payment_attributes][payment_method_id] *required* | The payment method id |
| order[payment_attributes][source_attributes][nonce] *required* | The payment nonce |
| order[payment_attributes][source_attributes][payment_type] *required* | The payment type. Must be `CreditCard` |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
ETag: W/&quot;d338a3a3ad227e3f5a3a74c2640dd542&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 64db230a-c434-48a1-9498-d3522d615335
X-Runtime: 0.138120
Content-Length: 4257
200 OK
```


```json
{
  "id": 499,
  "number": "R961948263",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 582,
  "created_at": "2019-08-05T19:32:39.463Z",
  "updated_at": "2019-08-05T19:32:39.752Z",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "email24@example.com",
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
  "token": "X_1UN7KXjTRxd6o44RipxQ",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 412,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 1034,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "PO Box 1337",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10025",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 494,
    "country_iso": "US",
    "state_id": 483,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 494,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 483,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 494
    }
  },
  "ship_address": {
    "id": 1035,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "A Different Road",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10026",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 494,
    "country_iso": "US",
    "state_id": 483,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 494,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 483,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 494
    }
  },
  "line_items": [
    {
      "id": 431,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 1173,
      "vendor_id": 3455,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 1173,
        "name": "Product #22 - 5128",
        "sku": "SKU-36",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-22-5128",
        "description": "As seen on TV!",
        "track_inventory": true,
        "price": "10.0",
        "display_price": "$10.00",
        "options_text": "Size: S",
        "in_stock": true,
        "is_backorderable": true,
        "total_on_hand": 10,
        "is_destroyed": false,
        "option_values": [
          {
            "id": 481,
            "name": "Size-15",
            "presentation": "S",
            "option_type_name": "foo-size-15",
            "option_type_id": 481,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 704,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #91",
      "adjustments": [

      ]
    }
  ],
  "payments": [

  ],
  "shipments": [
    {
      "id": 350,
      "tracking": null,
      "tracking_url": null,
      "number": "H21600112512",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R961948263",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 334,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 332,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 334,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 332,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 332,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 241,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 442,
              "name": "ShippingCategory #18"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 1173,
          "quantity": 1,
          "states": {
            "on_hand": 1
          }
        }
      ],
      "adjustments": [

      ],
      "stock_location_address": "NY Warehouse, Washington, AL"
    }
  ],
  "adjustments": [

  ],
  "permissions": {
    "can_update": false
  },
  "credit_cards": [

  ],
  "subtotals": {
    "order_total": "110.0",
    "item_total": "10.0",
    "shipments_total": "100.0",
    "line_item_promotions": [

    ],
    "tax_adjustments": [

    ],
    "miscellaneous_adjustments": [

    ],
    "giftwrap_amount": 0
  }
}
```



## Processing the checkout payment step with an already existing payment


### Request

#### Endpoint

```plaintext
PATCH /api/checkouts/R279500370
Accept: application/json
X-Spree-Order-Token: rvggBjWROtIm3AKV_IXLOw
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=410&order[payment_attributes][][source_attributes][wallet_payment_source_id]=33
```


| Name | Description |
|:-----|:------------|
| id *required* | The order number |
| order[payment_attributes] *required* | The payment attibutes |
| order[payment_attributes][payment_method_id] *required* | The payment method id |
| order[payment_attributes][source_attributes][wallet_payment_source_id] *required* | The payment source id of a payment within the user’s payments wallet |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
ETag: W/&quot;6cad80395a4576049c987ed7dfea7018&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: b55ffc4b-2edd-4223-85c0-96311b81e915
X-Runtime: 0.157567
Content-Length: 4257
200 OK
```


```json
{
  "id": 497,
  "number": "R279500370",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 580,
  "created_at": "2019-08-05T19:32:37.940Z",
  "updated_at": "2019-08-05T19:32:38.299Z",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "email22@example.com",
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
  "token": "rvggBjWROtIm3AKV_IXLOw",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 410,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 1030,
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
    "country_id": 492,
    "country_iso": "US",
    "state_id": 481,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 492,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 481,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 492
    }
  },
  "ship_address": {
    "id": 1031,
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
    "country_id": 492,
    "country_iso": "US",
    "state_id": 481,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 492,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 481,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 492
    }
  },
  "line_items": [
    {
      "id": 429,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 1169,
      "vendor_id": 3443,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 1169,
        "name": "Product #20 - 3608",
        "sku": "SKU-32",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-20-3608",
        "description": "As seen on TV!",
        "track_inventory": true,
        "price": "10.0",
        "display_price": "$10.00",
        "options_text": "Size: S",
        "in_stock": true,
        "is_backorderable": true,
        "total_on_hand": 10,
        "is_destroyed": false,
        "option_values": [
          {
            "id": 479,
            "name": "Size-13",
            "presentation": "S",
            "option_type_name": "foo-size-13",
            "option_type_id": 479,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 702,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #81",
      "adjustments": [

      ]
    }
  ],
  "payments": [

  ],
  "shipments": [
    {
      "id": 346,
      "tracking": null,
      "tracking_url": null,
      "number": "H50201462728",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R279500370",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 330,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 330,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 330,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 330,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 330,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 239,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 440,
              "name": "ShippingCategory #16"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 1169,
          "quantity": 1,
          "states": {
            "on_hand": 1
          }
        }
      ],
      "adjustments": [

      ],
      "stock_location_address": "NY Warehouse, Washington, AL"
    }
  ],
  "adjustments": [

  ],
  "permissions": {
    "can_update": false
  },
  "credit_cards": [

  ],
  "subtotals": {
    "order_total": "110.0",
    "item_total": "10.0",
    "shipments_total": "100.0",
    "line_item_promotions": [

    ],
    "tax_adjustments": [

    ],
    "miscellaneous_adjustments": [

    ],
    "giftwrap_amount": 0
  }
}
```



# LineItem

Representation of a single cart item for a specific variant with price of vendor

## Creating a line item


### Request

#### Endpoint

```plaintext
POST /api/orders/R833072767/line_items
Accept: application/json
X-Spree-Order-Token: GqWLy1iTyk_C4TbWjUDaYg
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/:order_number/line_items`

#### Parameters


```json
line_item[variant_id]=1144&line_item[options][vendor_id]=3362
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
ETag: W/&quot;f34d375a403ca86131b2c6decab2b610&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 78651b8c-a600-4ee6-857f-d3f6d63d7e60
X-Runtime: 0.129627
Content-Length: 848
201 Created
```


```json
{
  "id": 417,
  "quantity": 1,
  "price": "19.99",
  "variant_id": 1144,
  "vendor_id": 3362,
  "single_display_amount": "$19.99",
  "display_amount": "$19.99",
  "total": "19.99",
  "final_sale": false,
  "backordered": null,
  "promotionable": true,
  "variant": {
    "id": 1144,
    "name": "Product #4 - 3501",
    "sku": "SKU-7",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": false,
    "slug": "product-4-3501",
    "description": "As seen on TV!",
    "track_inventory": true,
    "price": "19.99",
    "display_price": "$19.99",
    "options_text": "Size: S",
    "in_stock": false,
    "is_backorderable": true,
    "total_on_hand": 0,
    "is_destroyed": false,
    "option_values": [
      {
        "id": 470,
        "name": "Size-4",
        "presentation": "S",
        "option_type_name": "foo-size-4",
        "option_type_id": 470,
        "option_type_presentation": "Size"
      }
    ],
    "images": [

    ],
    "product_id": 686,
    "brand": null,
    "brand_slug": null,
    "brand_description": null
  },
  "vendor_name": "Vendor #13",
  "adjustments": [

  ]
}
```



## Deleting a line item


### Request

#### Endpoint

```plaintext
DELETE /api/orders/R141293972/line_items/418
Accept: application/json
X-Spree-Order-Token: ZvHCuZyzL5ktdYMOusixpA
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
X-Request-Id: ebcfb87e-01ff-471b-8813-a8c95967af1e
X-Runtime: 0.087565
204 No Content
```




## Updating a line item


### Request

#### Endpoint

```plaintext
PUT /api/orders/R317571918/line_items/415
Accept: application/json
X-Spree-Order-Token: xF1e3ni9ntDSLHD1nfBdKQ
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
ETag: W/&quot;cf969ffc72aa65b4dea0cefc2339fce4&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: ce22c8b3-5f18-4628-902a-e77a5f9b6175
X-Runtime: 0.611173
Content-Length: 842
200 OK
```


```json
{
  "id": 415,
  "quantity": 2,
  "price": "10.0",
  "variant_id": 1138,
  "vendor_id": 3349,
  "single_display_amount": "$10.00",
  "display_amount": "$20.00",
  "total": "20.0",
  "final_sale": false,
  "backordered": null,
  "promotionable": true,
  "variant": {
    "id": 1138,
    "name": "Product #1 - 970",
    "sku": "SKU-1",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": false,
    "slug": "product-1-970",
    "description": "As seen on TV!",
    "track_inventory": true,
    "price": "10.0",
    "display_price": "$10.00",
    "options_text": "Size: S",
    "in_stock": true,
    "is_backorderable": true,
    "total_on_hand": 10,
    "is_destroyed": false,
    "option_values": [
      {
        "id": 467,
        "name": "Size-1",
        "presentation": "S",
        "option_type_name": "foo-size-1",
        "option_type_id": 467,
        "option_type_presentation": "Size"
      }
    ],
    "images": [

    ],
    "product_id": 683,
    "brand": null,
    "brand_slug": null,
    "brand_description": null
  },
  "vendor_name": "Vendor #2",
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
ETag: W/&quot;456fe2b1e937f801436c22998a605f5a&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 6206c077-be51-4aca-9422-3523717838de
X-Runtime: 0.011145
Content-Length: 134
200 OK
```


```json
[
  {
    "id": 737,
    "name": "Kids",
    "navigation_url": "/navigation/kids",
    "parent_id": 736,
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
Accept: application/json
Authorization: Bearer 41961215cc5d98e94d94d2afc61f21e15bead8b95ca16844
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
ETag: W/&quot;3439cac7cc6aced2c7646348c11628a7&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 5e88c08c-d106-49c4-b77d-6769608ab512
X-Runtime: 0.028679
Content-Length: 305
200 OK
```


```json
{
  "orders": [
    {
      "number": "R755375022",
      "completed_at": "2019-08-05T19:32:35.838Z",
      "total": "120.0",
      "state": "Complete",
      "shipment_state": "shipped",
      "shipments": [
        {
          "number": "H18857133538",
          "state": "shipped",
          "tracking": "U10000",
          "tracking_url": null
        }
      ]
    }
  ],
  "count": 1,
  "total_count": 1,
  "current_page": 1,
  "pages": 1,
  "per_page": 25
}
```



## it returns a 200


### Request

#### Endpoint

```plaintext
GET /api/orders/R461802178
Accept: application/json
Authorization: Bearer 9b8580f4f2103b83f8b2352c9d07042d6b132d710e06fd44
Host: example.org
Cookie: 
```

`GET /api/orders/:number`

#### Parameters



| Name | Description |
|:-----|:------------|
| number *required* | Specify the order number |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
ETag: W/&quot;c532a642e6bd31fbb5bd84c894f0dc03&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: f573b905-f262-447f-b336-a88d94a12caf
X-Runtime: 0.222482
Content-Length: 9254
200 OK
```


```json
{
  "id": 495,
  "number": "R461802178",
  "item_total": "20.0",
  "total": "120.0",
  "ship_total": "100.0",
  "state": "complete",
  "adjustment_total": "0.0",
  "user_id": 574,
  "created_at": "2019-08-05T19:32:36.340Z",
  "updated_at": "2019-08-05T19:32:36.712Z",
  "completed_at": "2019-08-05T19:32:36.438Z",
  "payment_total": "120.0",
  "shipment_state": "shipped",
  "payment_state": "paid",
  "email": "email16@example.com",
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
  "order_total_after_store_credit": "120.0",
  "display_order_total_after_store_credit": "$120.00",
  "total_applicable_store_credit": "0.0",
  "display_total_available_store_credit": "$0.00",
  "display_store_credit_remaining_after_capture": "$0.00",
  "canceler_id": null,
  "display_item_total": "$20.00",
  "total_quantity": 2,
  "display_total": "$120.00",
  "display_ship_total": "$100.00",
  "display_tax_total": "$0.00",
  "token": "0nuGzmkUwiHCup7kHaaU2g",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 406,
      "name": "Credit Card",
      "partial_name": "gateway",
      "method_type": "gateway"
    },
    {
      "id": 407,
      "name": "Credit Card",
      "partial_name": "gateway",
      "method_type": "gateway"
    }
  ],
  "bill_address": {
    "id": 1026,
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
    "country_id": 490,
    "country_iso": "US",
    "state_id": 479,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 490,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 479,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 490
    }
  },
  "ship_address": {
    "id": 1027,
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
    "country_id": 490,
    "country_iso": "US",
    "state_id": 479,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 490,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 479,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 490
    }
  },
  "line_items": [
    {
      "id": 425,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 1165,
      "vendor_id": 3431,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 1165,
        "name": "Product #18 - 6835",
        "sku": "SKU-28",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-18-6835",
        "description": "As seen on TV!",
        "track_inventory": true,
        "price": "10.0",
        "display_price": "$10.00",
        "options_text": "Size: S",
        "in_stock": true,
        "is_backorderable": true,
        "total_on_hand": 10,
        "is_destroyed": false,
        "option_values": [
          {
            "id": 477,
            "name": "Size-11",
            "presentation": "S",
            "option_type_name": "foo-size-11",
            "option_type_id": 477,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 700,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #71",
      "adjustments": [
        {
          "id": 86,
          "source_type": "Spree::TaxRate",
          "source_id": 15,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 425,
          "amount": "2.0",
          "label": "VAT 5%",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-08-05T19:32:36.665Z",
          "updated_at": "2019-08-05T19:32:36.682Z",
          "display_amount": "$2.00"
        },
        {
          "id": 80,
          "source_type": "Spree::PromotionAction",
          "source_id": 38,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 425,
          "amount": "5.0",
          "label": "foo",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-08-05T19:32:36.565Z",
          "updated_at": "2019-08-05T19:32:36.565Z",
          "display_amount": "$5.00"
        },
        {
          "id": 79,
          "source_type": "Spree::PromotionAction",
          "source_id": 38,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 425,
          "amount": "5.0",
          "label": "foo",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-08-05T19:32:36.552Z",
          "updated_at": "2019-08-05T19:32:36.552Z",
          "display_amount": "$5.00"
        }
      ]
    },
    {
      "id": 426,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 1165,
      "vendor_id": 3431,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 1165,
        "name": "Product #18 - 6835",
        "sku": "SKU-28",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-18-6835",
        "description": "As seen on TV!",
        "track_inventory": true,
        "price": "10.0",
        "display_price": "$10.00",
        "options_text": "Size: S",
        "in_stock": true,
        "is_backorderable": true,
        "total_on_hand": 10,
        "is_destroyed": false,
        "option_values": [
          {
            "id": 477,
            "name": "Size-11",
            "presentation": "S",
            "option_type_name": "foo-size-11",
            "option_type_id": 477,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 700,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #71",
      "adjustments": [
        {
          "id": 87,
          "source_type": "Spree::TaxRate",
          "source_id": 16,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 426,
          "amount": "1.5",
          "label": "VAT 5%",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-08-05T19:32:36.707Z",
          "updated_at": "2019-08-05T19:32:36.725Z",
          "display_amount": "$1.50"
        },
        {
          "id": 81,
          "source_type": "Spree::PromotionAction",
          "source_id": 38,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 426,
          "amount": "5.0",
          "label": "bar",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-08-05T19:32:36.577Z",
          "updated_at": "2019-08-05T19:32:36.577Z",
          "display_amount": "$5.00"
        }
      ]
    }
  ],
  "payments": [
    {
      "id": 198,
      "source_type": "Spree::CreditCard",
      "source_id": 172,
      "amount": "120.0",
      "display_amount": "$120.00",
      "payment_method_id": 406,
      "state": "completed",
      "avs_response": null,
      "created_at": "2019-08-05T19:32:36.457Z",
      "updated_at": "2019-08-05T19:32:36.457Z",
      "payment_method": {
        "id": 406,
        "name": "Credit Card"
      },
      "source": {
        "id": 172,
        "month": "12",
        "year": "2020",
        "cc_type": null,
        "last_digits": "1111",
        "name": "Spree Commerce"
      }
    }
  ],
  "shipments": [
    {
      "id": 343,
      "tracking": "U10000",
      "tracking_url": null,
      "number": "H55651805275",
      "cost": "100.0",
      "shipped_at": "2019-08-05T19:32:36.491Z",
      "state": "shipped",
      "order_id": "R461802178",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 327,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 328,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 327,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 328,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 328,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 233,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 438,
              "name": "ShippingCategory #14"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 1165,
          "quantity": 1,
          "states": {
            "shipped": 1
          }
        },
        {
          "variant_id": 1165,
          "quantity": 1,
          "states": {
            "shipped": 1
          }
        }
      ],
      "adjustments": [
        {
          "id": 83,
          "source_type": "Spree::PromotionAction",
          "source_id": 38,
          "adjustable_type": "Spree::Shipment",
          "adjustable_id": 343,
          "amount": "-10.0",
          "label": "Shipping",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-08-05T19:32:36.604Z",
          "updated_at": "2019-08-05T19:32:36.604Z",
          "display_amount": "-$10.00"
        },
        {
          "id": 82,
          "source_type": "Spree::PromotionAction",
          "source_id": 38,
          "adjustable_type": "Spree::Shipment",
          "adjustable_id": 343,
          "amount": "-9.99",
          "label": "Shipping",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-08-05T19:32:36.591Z",
          "updated_at": "2019-08-05T19:32:36.591Z",
          "display_amount": "-$9.99"
        }
      ],
      "stock_location_address": "NY Warehouse, Washington, AL"
    }
  ],
  "adjustments": [
    {
      "id": 84,
      "source_type": "Spree::Promotion",
      "source_id": 56,
      "adjustable_type": "Spree::Order",
      "adjustable_id": 495,
      "amount": "20.0",
      "label": "adj1",
      "promotion_code_id": null,
      "finalized": false,
      "eligible": true,
      "created_at": "2019-08-05T19:32:36.613Z",
      "updated_at": "2019-08-05T19:32:36.613Z",
      "display_amount": "$20.00"
    },
    {
      "id": 85,
      "source_type": "Spree::Promotion",
      "source_id": 56,
      "adjustable_type": "Spree::Order",
      "adjustable_id": 495,
      "amount": "30.0",
      "label": "adj2",
      "promotion_code_id": null,
      "finalized": false,
      "eligible": true,
      "created_at": "2019-08-05T19:32:36.619Z",
      "updated_at": "2019-08-05T19:32:36.619Z",
      "display_amount": "$30.00"
    }
  ],
  "permissions": {
    "can_update": false
  },
  "credit_cards": [
    {
      "id": 172,
      "month": "12",
      "year": "2020",
      "cc_type": null,
      "last_digits": "1111",
      "name": "Spree Commerce",
      "address": {
        "id": 1026,
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
        "country_id": 490,
        "country_iso": "US",
        "state_id": 479,
        "state_name": null,
        "state_text": "AL",
        "country": {
          "id": 490,
          "iso_name": "UNITED STATES",
          "iso": "US",
          "iso3": "USA",
          "name": "United States",
          "numcode": 840
        },
        "state": {
          "id": 479,
          "name": "Alabama",
          "abbr": "AL",
          "country_id": 490
        }
      }
    }
  ],
  "subtotals": {
    "order_total": "120.0",
    "item_total": "20.0",
    "shipments_total": "80.01",
    "line_item_promotions": [
      {
        "label": "foo",
        "amount": "10.0"
      },
      {
        "label": "bar",
        "amount": "5.0"
      }
    ],
    "tax_adjustments": [
      {
        "label": "VAT 5%",
        "amount": "3.5"
      }
    ],
    "miscellaneous_adjustments": [
      {
        "label": "adj1",
        "amount": "20.0"
      },
      {
        "label": "adj2",
        "amount": "30.0"
      }
    ],
    "giftwrap_amount": 0
  }
}
```



## it returns a 401


### Request

#### Endpoint

```plaintext
GET /api/orders/R272536246
Accept: application/json
Authorization: 4e92480f467860c69fef67ab7fa0b8552b6f1986f666ddcf
Host: example.org
Cookie: 
```

`GET /api/orders/:number`

#### Parameters



| Name | Description |
|:-----|:------------|
| number *required* | Specify the order number |



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
X-Request-Id: d7c28637-6b94-4ce1-a9e6-ce1659333de6
X-Runtime: 0.014136
Content-Length: 58
401 Unauthorized
```


```json
{
  "error": "You are not authorized to perform that action."
}
```



# Passwords

Send an email with password reset instructions

## Forgot Password


### Request

#### Endpoint

```plaintext
POST /api/users/password
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/users/password`

#### Parameters


```json
user[email]=email19%40example.com
```


| Name | Description |
|:-----|:------------|
| user[email] *required* | User email |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: text/html
Cache-Control: no-cache
X-Request-Id: 7f02cf56-f597-461a-b261-4539791d6b74
X-Runtime: 0.021685
Content-Length: 0
200 OK
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
user[email]=email21%40example.com&user[password]=secret
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
Authorization: Bearer 339f34bcc1732012cb894b05aeb3062d207365a51f67237b
ETag: W/&quot;9d1fcd2ed212aef47a14c432fcdc9a1e&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 70e6d1e2-57e6-4ca4-9544-1f1fbd73d397
X-Runtime: 0.006971
Content-Length: 553
200 OK
```


```json
{
  "id": 579,
  "email": "email21@example.com",
  "persistence_token": null,
  "perishable_token": null,
  "last_request_at": null,
  "login": "email21@example.com",
  "ship_address_id": null,
  "bill_address_id": null,
  "created_at": "2019-08-05T19:32:37.620Z",
  "updated_at": "2019-08-05T19:32:37.622Z",
  "spree_api_key": "339f34bcc1732012cb894b05aeb3062d207365a51f67237b",
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



## Password Reset


### Request

#### Endpoint

```plaintext
PUT /api/users/password
Accept: application/json
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PUT /api/users/password`

#### Parameters


```json
user[password]=password&user[password_confirmation]=password&user[reset_password_token]=123123123
```


| Name | Description |
|:-----|:------------|
| user[password] *required* | User password |
| user[password_confirmation] *required* | User password confirmation |
| user[reset_password_token] *required* | User reset password token |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Cache-Control: no-cache
X-Request-Id: 45016357-970e-470f-91bf-450010dd6099
X-Runtime: 0.004415
204 No Content
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
Date: Mon, 05 Aug 2019 19:32:35 GMT
Surrogate-Control: max-age=900
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;ae6d0dbf3a45a4a16e17458e95c67024&quot;
X-Request-Id: 1d2149e8-bb05-47fe-9481-db8fb445fc28
X-Runtime: 0.105904
Content-Length: 914
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
      "id": 696,
      "name": "Product #14 - 446",
      "description": "As seen on TV!",
      "available_on": "2018-08-05T19:32:34.861Z",
      "slug": "product-14-446",
      "meta_description": null,
      "meta_keywords": null,
      "shipping_category_id": 434,
      "taxon_ids": [

      ],
      "total_on_hand": 0,
      "meta_title": null,
      "display_price": "$19.99",
      "trends": [

      ],
      "brand": null,
      "brand_slug": null,
      "brand_description": null,
      "has_variants": false,
      "master": {
        "id": 1159,
        "name": "Product #14 - 446",
        "sku": "SKU-23",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-14-446",
        "description": "As seen on TV!",
        "track_inventory": true,
        "price": "19.99",
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
GET /api/products/product-15-4639
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
Date: Mon, 05 Aug 2019 19:32:35 GMT
Surrogate-Control: max-age=900
Surrogate-Key: product_id=1
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;447ef4445e33cd058a14c037aaf52414&quot;
X-Request-Id: 5ece93c8-3561-45de-b401-112d5497dfef
X-Runtime: 0.057707
Content-Length: 836
200 OK
```


```json
{
  "id": 697,
  "name": "Product #15 - 4639",
  "description": "As seen on TV!",
  "available_on": "2018-08-05T19:32:35.099Z",
  "slug": "product-15-4639",
  "meta_description": null,
  "meta_keywords": null,
  "shipping_category_id": 435,
  "taxon_ids": [

  ],
  "total_on_hand": 0,
  "meta_title": null,
  "display_price": "$19.99",
  "trends": [

  ],
  "brand": null,
  "brand_slug": null,
  "brand_description": null,
  "has_variants": false,
  "master": {
    "id": 1160,
    "name": "Product #15 - 4639",
    "sku": "SKU-24",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": true,
    "slug": "product-15-4639",
    "description": "As seen on TV!",
    "track_inventory": true,
    "price": "19.99",
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
X-Request-Id: 0e9ca2ff-65c6-4eca-9241-14d3a84190cf
X-Runtime: 0.020310
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
ETag: W/&quot;e7e71062af2e2d1330cf69605a6de22a&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: bf5f3f72-eef5-4ccd-8be8-90e4f421c588
X-Runtime: 0.087009
Content-Length: 1108
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
      "id": 692,
      "name": "Product #10 - 9369",
      "description": "As seen on TV!",
      "available_on": "2018-08-05T19:32:34.007Z",
      "slug": "product-10-9369",
      "meta_description": null,
      "meta_keywords": null,
      "shipping_category_id": 432,
      "taxon_ids": [
        739
      ],
      "total_on_hand": 0,
      "meta_title": null,
      "display_price": "$19.99",
      "trends": [

      ],
      "brand": "Ruby on Rails",
      "brand_slug": "ruby-on-rails",
      "brand_description": null,
      "has_variants": false,
      "master": {
        "id": 1155,
        "name": "Product #10 - 9369",
        "sku": "SKU-19",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-10-9369",
        "description": "As seen on TV!",
        "track_inventory": true,
        "price": "19.99",
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
          "taxon_id": 739,
          "position": 1,
          "taxon": {
            "id": 739,
            "name": "Ruby on Rails",
            "pretty_name": "Ruby on Rails",
            "permalink": "ruby-on-rails",
            "parent_id": null,
            "taxonomy_id": 329
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
GET /api/taxons/products?id=743
Host: example.org
Cookie: 
```

`GET /api/taxons/products`

#### Parameters


```json
id: 743
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
ETag: W/&quot;cf778ece38082b97210b7f92fd7470ce&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 28f390fe-6ea7-475d-adaa-91bc948dde39
X-Runtime: 0.057958
Content-Length: 1108
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
      "id": 694,
      "name": "Product #12 - 6610",
      "description": "As seen on TV!",
      "available_on": "2018-08-05T19:32:34.472Z",
      "slug": "product-12-6610",
      "meta_description": null,
      "meta_keywords": null,
      "shipping_category_id": 433,
      "taxon_ids": [
        743
      ],
      "total_on_hand": 0,
      "meta_title": null,
      "display_price": "$19.99",
      "trends": [

      ],
      "brand": "Ruby on Rails",
      "brand_slug": "ruby-on-rails",
      "brand_description": null,
      "has_variants": false,
      "master": {
        "id": 1157,
        "name": "Product #12 - 6610",
        "sku": "SKU-21",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-12-6610",
        "description": "As seen on TV!",
        "track_inventory": true,
        "price": "19.99",
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
          "taxon_id": 743,
          "position": 1,
          "taxon": {
            "id": 743,
            "name": "Ruby on Rails",
            "pretty_name": "Ruby on Rails",
            "permalink": "ruby-on-rails",
            "parent_id": null,
            "taxonomy_id": 331
          }
        }
      ]
    }
  ]
}
```



# Return Authorizations

Get user return authorizations

## Can get another user&#39;s return authorization


### Request

#### Endpoint

```plaintext
GET /api/returns/RA624568277
Authorization: Bearer b4a1819e927fbd98b08977e83ffaf1589eb0fd70acb254bb
Accept: application/json
Host: example.org
Cookie: 
```

`GET /api/returns/:number`

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
ETag: W/&quot;9e75549919d641630fdd588feed6dd6a&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: a3ce28e0-950f-48d3-ba10-d606710a703e
X-Runtime: 0.045304
Content-Length: 2753
200 OK
```


```json
{
  "id": 20,
  "number": "RA624568277",
  "state": "authorized",
  "order_id": 493,
  "memo": "Items were broken",
  "created_at": "2019-08-05T19:32:33.771Z",
  "updated_at": "2019-08-05T19:32:33.771Z",
  "reason": {
    "id": 60,
    "name": "Defect #7",
    "active": true,
    "mutable": true,
    "created_at": "2019-08-05T19:32:33.766Z",
    "updated_at": "2019-08-05T19:32:33.766Z"
  },
  "order": {
    "id": 493,
    "number": "R898553179",
    "item_total": "10.0",
    "total": "110.0",
    "state": "complete",
    "adjustment_total": "0.0",
    "user_id": 568,
    "completed_at": "2019-08-05T19:32:33.682Z",
    "bill_address_id": 1022,
    "ship_address_id": 1023,
    "payment_total": "110.0",
    "shipment_state": "shipped",
    "payment_state": "paid",
    "email": "email11@example.com",
    "special_instructions": null,
    "created_at": "2019-08-05T19:32:33.595Z",
    "updated_at": "2019-08-05T19:32:33.745Z",
    "currency": "USD",
    "last_ip_address": null,
    "created_by_id": null,
    "shipment_total": "100.0",
    "additional_tax_total": "0.0",
    "promo_total": "0.0",
    "channel": "spree",
    "included_tax_total": "0.0",
    "item_count": 1,
    "approver_id": null,
    "approved_at": null,
    "confirmation_delivered": false,
    "guest_token": "YaORf129MAAhwDyE9XFtLw",
    "canceled_at": null,
    "canceler_id": null,
    "store_id": 532,
    "approver_name": null,
    "frontend_viewable": true
  },
  "ship_address": {
    "id": 1023,
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
    "country_id": 483,
    "country_iso": "US",
    "state_id": 472,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 483,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 472,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 483
    }
  },
  "bill_address": {
    "id": 1022,
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
    "country_id": 483,
    "country_iso": "US",
    "state_id": 472,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 483,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 472,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 483
    }
  },
  "return_items": [
    {
      "name": "Product #9 - 5031",
      "brand": null,
      "image": null,
      "cost": "10.0",
      "option_values": [
        {
          "type": "Size",
          "value": "S"
        }
      ]
    }
  ],
  "payments": [
    {
      "payment_method": {
        "id": 402,
        "name": "Credit Card"
      },
      "source": {
        "id": 170,
        "month": "12",
        "year": "2020",
        "cc_type": null,
        "last_digits": "1111",
        "name": "Spree Commerce",
        "gateway_customer_profile_id": "BGS-130411",
        "gateway_payment_profile_id": null
      }
    }
  ],
  "refunded_total": "0.0",
  "subtotals": {
    "order_total": "110.0",
    "item_total": "10.0",
    "shipments_total": "100.0",
    "line_item_promotions": [

    ],
    "tax_adjustments": [

    ],
    "miscellaneous_adjustments": [

    ],
    "giftwrap_amount": 0
  }
}
```



## Gets the user&#39;s return authorizations


### Request

#### Endpoint

```plaintext
GET /api/returns/mine
Authorization: Bearer 10acb445eac2a6fab05d0a4956368c4a35f9f61cf117ac47
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
ETag: W/&quot;79f23e519db21686b827468630ef5a25&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 22a20cc3-5c7d-4bb4-9828-8427b45e94e7
X-Runtime: 0.023528
Content-Length: 164
200 OK
```


```json
{
  "return_authorizations": [
    {
      "number": "RA338800131",
      "created_at": "2019-08-05T19:32:32.060Z",
      "return_amount": "10.0",
      "order_number": "R441993850",
      "state": "authorized"
    }
  ]
}
```



## returns a 200


### Request

#### Endpoint

```plaintext
GET /api/returns/RA000464328
Authorization: Bearer 2a49eff7d58486a26ee29937c9909dae44c62f80399fbc13
Accept: application/json
Host: example.org
Cookie: 
```

`GET /api/returns/:number`

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
ETag: W/&quot;1c869c1d29288dd7dfcccc6193eec318&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 331d0f24-053a-42e9-a7a7-d90571301676
X-Runtime: 0.076296
Content-Length: 2675
200 OK
```


```json
{
  "id": 18,
  "number": "RA000464328",
  "state": "authorized",
  "order_id": 491,
  "memo": "Items were broken",
  "created_at": "2019-08-05T19:32:32.687Z",
  "updated_at": "2019-08-05T19:32:32.687Z",
  "reason": {
    "id": 56,
    "name": "Defect #3",
    "active": true,
    "mutable": true,
    "created_at": "2019-08-05T19:32:32.682Z",
    "updated_at": "2019-08-05T19:32:32.682Z"
  },
  "order": {
    "id": 491,
    "number": "R833284013",
    "item_total": "10.0",
    "total": "110.0",
    "state": "complete",
    "adjustment_total": "0.0",
    "user_id": 565,
    "completed_at": "2019-08-05T19:32:32.558Z",
    "bill_address_id": 1018,
    "ship_address_id": 1019,
    "payment_total": "110.0",
    "shipment_state": "shipped",
    "payment_state": "paid",
    "email": "email8@example.com",
    "special_instructions": null,
    "created_at": "2019-08-05T19:32:32.474Z",
    "updated_at": "2019-08-05T19:32:32.635Z",
    "currency": "USD",
    "last_ip_address": null,
    "created_by_id": null,
    "shipment_total": "100.0",
    "additional_tax_total": "0.0",
    "promo_total": "0.0",
    "channel": "spree",
    "included_tax_total": "0.0",
    "item_count": 1,
    "approver_id": null,
    "approved_at": null,
    "confirmation_delivered": false,
    "guest_token": "Lkq5WyB-56-kF3lQ0c70JA",
    "canceled_at": null,
    "canceler_id": null,
    "store_id": 530,
    "approver_name": null,
    "frontend_viewable": true
  },
  "ship_address": {
    "id": 1019,
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
    "country_id": 481,
    "country_iso": "US",
    "state_id": 470,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 481,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 470,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 481
    }
  },
  "bill_address": {
    "id": 1018,
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
    "country_id": 481,
    "country_iso": "US",
    "state_id": 470,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 481,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 470,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 481
    }
  },
  "return_items": [
    {
      "name": "Product #7 - 1739",
      "brand": null,
      "image": null,
      "cost": "10.0",
      "option_values": [
        {
          "type": "Size",
          "value": "S"
        }
      ]
    }
  ],
  "payments": [
    {
      "payment_method": {
        "id": 398,
        "name": "Credit Card"
      },
      "source": {
        "id": 168,
        "month": "12",
        "year": "2020",
        "cc_type": null,
        "last_digits": "1111",
        "name": "Spree Commerce"
      }
    }
  ],
  "refunded_total": "0.0",
  "subtotals": {
    "order_total": "110.0",
    "item_total": "10.0",
    "shipments_total": "100.0",
    "line_item_promotions": [

    ],
    "tax_adjustments": [

    ],
    "miscellaneous_adjustments": [

    ],
    "giftwrap_amount": 0
  }
}
```



## returns a 404


### Request

#### Endpoint

```plaintext
GET /api/returns/RA513556856
Authorization: Bearer 3c209a2ff0218a9c57ee3a97224cb026e6e644d734a7a8f4
Accept: application/json
Host: example.org
Cookie: 
```

`GET /api/returns/:number`

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
X-Request-Id: 4fd968e2-9c24-4399-8c2a-f0a4011fd24b
X-Runtime: 0.015012
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
Authorization: Bearer 08c4443670ac7352f555d3bc3ef3e7e1f147b89387495260
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
ETag: W/&quot;6038c9a60cfd3bb8f7dabafedb7104d6&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: ca465c50-9d91-420d-ac1a-2c4b1bc3146d
X-Runtime: 0.039873
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
      "created_at": "2019-08-05T19:32:45.477Z"
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

Create a new user and return a bearer header to be used for further user related request

## Gets the user account information


### Request

#### Endpoint

```plaintext
GET /api/users/mine
Authorization: Bearer d001d815ad6988a6700db74a851aa6ef285eb025c284a806
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
Authorization: Bearer d001d815ad6988a6700db74a851aa6ef285eb025c284a806
ETag: W/&quot;c817d477b4aa5eb47f39a2a7e9dc5032&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 91ba9535-c98c-480a-ab21-3bc7ec7ca793
X-Runtime: 0.008858
Content-Length: 125
200 OK
```


```json
{
  "email": "email13@example.com",
  "first_name": null,
  "last_name": null,
  "id": 571,
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
user[email]=email14%40example.com&user[password]=secret
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
Authorization: Bearer 1fdc538ac715cf8cd7602b9513f5ec4506651787d762343c
ETag: W/&quot;f914dd0c3449141b8d0c4acd73f157dd&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 416dfa48-4f22-47ba-9520-05cc4b863770
X-Runtime: 0.008371
Content-Length: 553
200 OK
```


```json
{
  "id": 572,
  "email": "email14@example.com",
  "persistence_token": null,
  "perishable_token": null,
  "last_request_at": null,
  "login": "email14@example.com",
  "ship_address_id": null,
  "bill_address_id": null,
  "created_at": "2019-08-05T19:32:33.941Z",
  "updated_at": "2019-08-05T19:32:33.947Z",
  "spree_api_key": "1fdc538ac715cf8cd7602b9513f5ec4506651787d762343c",
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
Authorization: Bearer abdbbdc88454a1e7a94677f64f21c20e38991713b8980d10
ETag: W/&quot;5217b02e7f25e49b7b623b2b4e20d62c&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: ff401b15-13a2-4a0b-a002-743c9da27c34
X-Runtime: 0.043264
Content-Length: 157
201 Created
```


```json
{
  "id": 570,
  "email": "test@example.com",
  "created_at": "2019-08-05T19:32:33.882Z",
  "updated_at": "2019-08-05T19:32:33.885Z",
  "bill_address": null,
  "ship_address": null
}
```



# Variant



## Fetching a variant


### Request

#### Endpoint

```plaintext
GET /api/variants/1179
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
ETag: W/&quot;3e61ac4a32de5a56fe2dd123eac83f8d&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 4447647d-515a-4100-9f1d-a1f26eebf683
X-Runtime: 0.114333
Content-Length: 1460
200 OK
```


```json
{
  "id": 1179,
  "name": "Product #25 - 9567",
  "sku": "SKU-42",
  "weight": "0.0",
  "height": null,
  "width": null,
  "depth": null,
  "is_master": false,
  "slug": "product-25-9567",
  "description": "As seen on TV!",
  "track_inventory": true,
  "lead_time": 2,
  "price": "10.0",
  "display_price": "$10.00",
  "options_text": "Size: S",
  "in_stock": false,
  "is_backorderable": false,
  "total_on_hand": 0,
  "is_destroyed": false,
  "option_values": [
    {
      "id": 484,
      "name": "Size-18",
      "presentation": "S",
      "option_type_name": "foo-size-18",
      "option_type_id": 484,
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
      "attachment_updated_at": "2019-08-05T19:32:45.061Z",
      "attachment_width": 489,
      "attachment_height": 490,
      "alt": null,
      "viewable_type": "Spree::Variant",
      "viewable_id": 1179,
      "mini_url": "/spree/products/2/mini/thinking-cat.jpg?1565033565",
      "small_url": "/spree/products/2/small/thinking-cat.jpg?1565033565",
      "product_url": "/spree/products/2/product/thinking-cat.jpg?1565033565",
      "large_url": "/spree/products/2/large/thinking-cat.jpg?1565033565"
    }
  ],
  "variant_properties": [

  ],
  "stock_items": [

  ],
  "prices": [
    {
      "id": 2275,
      "vendor_id": 3476,
      "price": "10.0",
      "original_price": "10.0",
      "discount_percent": 0.0,
      "total_on_hand": 0,
      "country_iso": null,
      "final_sale": false,
      "on_sale": false
    },
    {
      "id": 2276,
      "vendor_id": 3477,
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



# Wallet payment sources



## Get user wallet payment sources


### Request

#### Endpoint

```plaintext
GET /api/wallet_payment_sources
Accept: application/json
Authorization: Bearer bf5d6c89ad9aca005d2fedc7c6ccc41de9449b00483215cd
Host: example.org
Cookie: 
```

`GET /api/wallet_payment_sources`

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
ETag: W/&quot;b2d570108f0b136514507144b4195d14&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 5dbc55f8-2210-448c-a315-86b9f3f34812
X-Runtime: 0.036865
Content-Length: 199
200 OK
```


```json
[
  {
    "id": 30,
    "user_id": 561,
    "payment_source_type": "SolidusPaypalBraintree::Source",
    "payment_source_id": 55,
    "default": false,
    "created_at": "2019-08-05T19:32:31.337Z",
    "updated_at": "2019-08-05T19:32:31.337Z"
  }
]
```



## Remove the payment from the user wallet


### Request

#### Endpoint

```plaintext
DELETE /api/wallet_payment_sources/31
Accept: application/json
Authorization: Bearer 3b8315697d3208559cddb3d417a0f36e699e26b1c1fece09
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`DELETE /api/wallet_payment_sources/:id`

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
X-Request-Id: ecee69c2-b9c5-4388-a531-34877e9fd036
X-Runtime: 0.019793
204 No Content
```




## Set a wallet payment source as the default user payment method


### Request

#### Endpoint

```plaintext
POST /api/wallet_payment_sources/32/default
Accept: application/json
Authorization: Bearer 99cd1e5e34de3ec6faab4b6b49be221c903c732bba10adf2
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/wallet_payment_sources/:id/default`

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
X-Request-Id: 99e8556d-ee64-48ff-9778-412c1d8717c3
X-Runtime: 0.016622
204 No Content
```




