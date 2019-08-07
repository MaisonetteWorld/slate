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
PUT /api/orders/R268749670/addresses/1189
Accept: application/json
X-Spree-Order-Token: oXUkyrLVqYQYSZaQyBooBQ
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
ETag: W/&quot;7a1639df9d2699503c5219b90ce5c70a&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 7dcba6d5-1128-48c2-9aa5-7612037d2d1d
X-Runtime: 0.044401
Content-Length: 514
200 OK
```


```json
{
  "id": 1190,
  "firstname": "John the Tester",
  "lastname": null,
  "full_name": "John the Tester",
  "address1": "A Different Road",
  "address2": "Northwest",
  "city": "Herndon",
  "zipcode": "10038",
  "phone": "555-555-0199",
  "company": "Company",
  "alternative_phone": "555-555-0199",
  "country_id": 557,
  "country_iso": "US",
  "state_id": 546,
  "state_name": null,
  "state_text": "AL",
  "country": {
    "id": 557,
    "iso_name": "UNITED STATES",
    "iso": "US",
    "iso3": "USA",
    "name": "United States",
    "numcode": 840
  },
  "state": {
    "id": 546,
    "name": "Alabama",
    "abbr": "AL",
    "country_id": 557
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
X-Spree-Order-Token: TTKcOj9VE2FTiUQBpXHY6Q
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/braintree/transactions`

#### Parameters


```json
order_id=R761133257&payment_method_id=441&options[restart_checkout]=true&transaction[email]=maryellen.oga%40mckenziemcglynn.com&transaction[nonce]=fake-paypal-billing-agreement-nonce&transaction[phone]=555-555-0199&transaction[address_attributes][first_name]=John&transaction[address_attributes][last_name]=Stamm&transaction[address_attributes][address_line_1]=A+Different+Road&transaction[address_attributes][city]=Herndon&transaction[address_attributes][state_code]=AL&transaction[address_attributes][zip]=10003&transaction[address_attributes][country_code]=US&transaction[payment_type]=PayPalAccount
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
ETag: W/&quot;88e405ffd551ee15ab34676822602aa6&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 5974d872-59ef-4b64-a80f-16c9196d9434
X-Runtime: 0.260912
Content-Length: 4687
200 OK
```


```json
{
  "id": 554,
  "number": "R761133257",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2019-08-07T09:37:55.229Z",
  "updated_at": "2019-08-07T09:37:55.481Z",
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
  "token": "TTKcOj9VE2FTiUQBpXHY6Q",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 441,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 1155,
    "firstname": "John",
    "lastname": "Stamm",
    "full_name": "John Stamm",
    "address1": "A Different Road",
    "address2": null,
    "city": "Herndon",
    "zipcode": "10003",
    "phone": "555-555-0199",
    "company": null,
    "alternative_phone": null,
    "country_id": 534,
    "country_iso": "US",
    "state_id": 523,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 534,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 523,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 534
    }
  },
  "ship_address": {
    "id": 1155,
    "firstname": "John",
    "lastname": "Stamm",
    "full_name": "John Stamm",
    "address1": "A Different Road",
    "address2": null,
    "city": "Herndon",
    "zipcode": "10003",
    "phone": "555-555-0199",
    "company": null,
    "alternative_phone": null,
    "country_id": 534,
    "country_iso": "US",
    "state_id": 523,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 534,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 523,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 534
    }
  },
  "line_items": [
    {
      "id": 464,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 1308,
      "vendor_id": 3763,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 1308,
        "name": "Product #2 - 6550",
        "sku": "SKU-3",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-2-6550",
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
            "id": 591,
            "name": "Size-2",
            "presentation": "S",
            "option_type_name": "foo-size-2",
            "option_type_id": 528,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 793,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #7",
      "adjustments": [

      ]
    }
  ],
  "payments": [
    {
      "id": 214,
      "source_type": "SolidusPaypalBraintree::Source",
      "source_id": 67,
      "amount": "110.0",
      "display_amount": "$110.00",
      "payment_method_id": 441,
      "state": "checkout",
      "avs_response": null,
      "created_at": "2019-08-07T09:37:55.323Z",
      "updated_at": "2019-08-07T09:37:55.323Z",
      "payment_method": {
        "id": 441,
        "name": "Braintree"
      },
      "source": {
        "id": 67,
        "payment_type": "PayPalAccount",
        "token": "bgx899",
        "created_at": "2019-08-07T09:37:55.322Z",
        "email": "jane.doe@paypal.com"
      }
    }
  ],
  "shipments": [
    {
      "id": 391,
      "tracking": null,
      "tracking_url": null,
      "number": "H02420261105",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R761133257",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 362,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 359,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 362,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 359,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 359,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 236,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 486,
              "name": "ShippingCategory #2"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 1308,
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
X-Spree-Order-Token: yBVnuzT8KMlTwhZiW9rH7A
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/braintree/transactions`

#### Parameters


```json
order_id=R932275614&payment_method_id=440&options[restart_checkout]=true&transaction[email]=maryellen.oga%40mckenziemcglynn.com&transaction[nonce]=fake-apple-pay-visa-nonce&transaction[phone]=555-555-0199&transaction[address_attributes][first_name]=John&transaction[address_attributes][last_name]=Stamm&transaction[address_attributes][address_line_1]=A+Different+Road&transaction[address_attributes][city]=Herndon&transaction[address_attributes][state_code]=AL&transaction[address_attributes][zip]=10001&transaction[address_attributes][country_code]=US&transaction[payment_type]=ApplePayCard
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
ETag: W/&quot;e3abae8396b9e95f721d606dceb08044&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 3eb4241e-874c-451e-a800-2118ec764e10
X-Runtime: 0.585071
Content-Length: 4733
200 OK
```


```json
{
  "id": 553,
  "number": "R932275614",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2019-08-07T09:37:53.999Z",
  "updated_at": "2019-08-07T09:37:54.871Z",
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
  "token": "yBVnuzT8KMlTwhZiW9rH7A",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 440,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 1152,
    "firstname": "John",
    "lastname": "Stamm",
    "full_name": "John Stamm",
    "address1": "A Different Road",
    "address2": null,
    "city": "Herndon",
    "zipcode": "10001",
    "phone": "555-555-0199",
    "company": null,
    "alternative_phone": null,
    "country_id": 533,
    "country_iso": "US",
    "state_id": 522,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 533,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 522,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 533
    }
  },
  "ship_address": {
    "id": 1152,
    "firstname": "John",
    "lastname": "Stamm",
    "full_name": "John Stamm",
    "address1": "A Different Road",
    "address2": null,
    "city": "Herndon",
    "zipcode": "10001",
    "phone": "555-555-0199",
    "company": null,
    "alternative_phone": null,
    "country_id": 533,
    "country_iso": "US",
    "state_id": 522,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 533,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 522,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 533
    }
  },
  "line_items": [
    {
      "id": 463,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 1306,
      "vendor_id": 3757,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 1306,
        "name": "Product #1 - 7807",
        "sku": "SKU-1",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-1-7807",
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
            "id": 590,
            "name": "Size-1",
            "presentation": "S",
            "option_type_name": "foo-size-1",
            "option_type_id": 527,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 792,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #2",
      "adjustments": [

      ]
    }
  ],
  "payments": [
    {
      "id": 213,
      "source_type": "SolidusPaypalBraintree::Source",
      "source_id": 66,
      "amount": "110.0",
      "display_amount": "$110.00",
      "payment_method_id": 440,
      "state": "checkout",
      "avs_response": null,
      "created_at": "2019-08-07T09:37:54.635Z",
      "updated_at": "2019-08-07T09:37:54.635Z",
      "payment_method": {
        "id": 440,
        "name": "Braintree"
      },
      "source": {
        "id": 66,
        "payment_type": "ApplePayCard",
        "token": "cg7hsk",
        "created_at": "2019-08-07T09:37:54.633Z",
        "cc_type": "Apple Pay - Visa",
        "last_digits": "1881",
        "month": "12",
        "year": "2020"
      }
    }
  ],
  "shipments": [
    {
      "id": 389,
      "tracking": null,
      "tracking_url": null,
      "number": "H86525115067",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R932275614",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 360,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 358,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 360,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 358,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 358,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 235,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 485,
              "name": "ShippingCategory #1"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 1306,
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
PUT /api/checkouts/R019680306/complete
Accept: application/json
X-Spree-Order-Token: VbEMoahHpOqWeC0SutlKJw
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
ETag: W/&quot;b01a7c39b1a6159bfc2494f9354a7283&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 9dd9b377-9343-493e-900b-3a0775487acf
X-Runtime: 2.170654
Content-Length: 4861
200 OK
```


```json
{
  "id": 569,
  "number": "R019680306",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "complete",
  "adjustment_total": "0.0",
  "user_id": 654,
  "created_at": "2019-08-07T09:38:05.947Z",
  "updated_at": "2019-08-07T09:38:09.174Z",
  "completed_at": "2019-08-07T09:38:09.174Z",
  "payment_total": "110.0",
  "shipment_state": "ready",
  "payment_state": "paid",
  "email": "email28@example.com",
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
  "token": "VbEMoahHpOqWeC0SutlKJw",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 463,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    },
    {
      "id": 464,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 1184,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "PO Box 1337",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10033",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 555,
    "country_iso": "US",
    "state_id": 544,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 555,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 544,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 555
    }
  },
  "ship_address": {
    "id": 1185,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "A Different Road",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10034",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 555,
    "country_iso": "US",
    "state_id": 544,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 555,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 544,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 555
    }
  },
  "line_items": [
    {
      "id": 483,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 1351,
      "vendor_id": 3895,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 1351,
        "name": "Product #27 - 3706",
        "sku": "SKU-46",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-27-3706",
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
            "id": 609,
            "name": "Size-20",
            "presentation": "S",
            "option_type_name": "foo-size-20",
            "option_type_id": 546,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 818,
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
      "id": 222,
      "source_type": "SolidusPaypalBraintree::Source",
      "source_id": 72,
      "amount": "110.0",
      "display_amount": "$110.00",
      "payment_method_id": 463,
      "state": "completed",
      "avs_response": "M",
      "created_at": "2019-08-07T09:38:06.034Z",
      "updated_at": "2019-08-07T09:38:09.048Z",
      "payment_method": {
        "id": 463,
        "name": "Braintree"
      },
      "source": {
        "id": 72,
        "payment_type": "CreditCard",
        "token": "8kfdwz",
        "created_at": "2019-08-07T09:38:06.032Z",
        "cc_type": "Visa",
        "last_digits": "1881",
        "month": "12",
        "year": "2020"
      }
    }
  ],
  "shipments": [
    {
      "id": 410,
      "tracking": "U10000",
      "tracking_url": null,
      "number": "H88811537585",
      "cost": "100.0",
      "shipped_at": null,
      "state": "ready",
      "order_id": "R019680306",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 381,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 374,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 381,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 374,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 374,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 255,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 507,
              "name": "ShippingCategory #23"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 1351,
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
PATCH /api/checkouts/R099334208
Accept: application/json
X-Spree-Order-Token: BnfW01g7lVNN9bR5ePK0WQ
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=461&order[payment_attributes][][source_attributes][nonce]=fake-apple-pay-visa-nonce&order[payment_attributes][][source_attributes][payment_type]=ApplePayCard
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
ETag: W/&quot;0fcab1b47d12c722deffd701e08516bb&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 9a2b0f94-67f6-4094-b6fe-9f1d552ea2e8
X-Runtime: 0.126616
Content-Length: 4258
200 OK
```


```json
{
  "id": 567,
  "number": "R099334208",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 652,
  "created_at": "2019-08-07T09:38:04.729Z",
  "updated_at": "2019-08-07T09:38:04.972Z",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
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
  "token": "BnfW01g7lVNN9bR5ePK0WQ",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 461,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 1180,
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
    "country_id": 553,
    "country_iso": "US",
    "state_id": 542,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 553,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 542,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 553
    }
  },
  "ship_address": {
    "id": 1181,
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
    "country_id": 553,
    "country_iso": "US",
    "state_id": 542,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 553,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 542,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 553
    }
  },
  "line_items": [
    {
      "id": 481,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 1347,
      "vendor_id": 3883,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 1347,
        "name": "Product #25 - 5829",
        "sku": "SKU-42",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-25-5829",
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
            "id": 607,
            "name": "Size-18",
            "presentation": "S",
            "option_type_name": "foo-size-18",
            "option_type_id": 544,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 816,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #108",
      "adjustments": [

      ]
    }
  ],
  "payments": [

  ],
  "shipments": [
    {
      "id": 407,
      "tracking": null,
      "tracking_url": null,
      "number": "H35333573024",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R099334208",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 378,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 372,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 378,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 372,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 372,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 253,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 505,
              "name": "ShippingCategory #21"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 1347,
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
PATCH /api/checkouts/R182846104
Accept: application/json
X-Spree-Order-Token: kYZQDhmXJY3BiDVJ44RTyw
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=460&order[payment_attributes][][source_attributes][nonce]=fake-paypal-billing-agreement-nonce&order[payment_attributes][][source_attributes][payment_type]=PayPalAccount
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
ETag: W/&quot;f7b1939e64bf95a1e445f2c7f0b22ca9&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: f31cd277-e8fd-4418-b6cc-be845eba6746
X-Runtime: 0.121600
Content-Length: 4258
200 OK
```


```json
{
  "id": 566,
  "number": "R182846104",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 651,
  "created_at": "2019-08-07T09:38:04.125Z",
  "updated_at": "2019-08-07T09:38:04.372Z",
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
  "token": "kYZQDhmXJY3BiDVJ44RTyw",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 460,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 1178,
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
    "country_id": 552,
    "country_iso": "US",
    "state_id": 541,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 552,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 541,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 552
    }
  },
  "ship_address": {
    "id": 1179,
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
    "country_id": 552,
    "country_iso": "US",
    "state_id": 541,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 552,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 541,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 552
    }
  },
  "line_items": [
    {
      "id": 480,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 1345,
      "vendor_id": 3877,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 1345,
        "name": "Product #24 - 7534",
        "sku": "SKU-40",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-24-7534",
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
            "id": 606,
            "name": "Size-17",
            "presentation": "S",
            "option_type_name": "foo-size-17",
            "option_type_id": 543,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 815,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #103",
      "adjustments": [

      ]
    }
  ],
  "payments": [

  ],
  "shipments": [
    {
      "id": 405,
      "tracking": null,
      "tracking_url": null,
      "number": "H50475883277",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R182846104",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 376,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 371,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 376,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 371,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 371,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 252,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 504,
              "name": "ShippingCategory #20"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 1345,
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
PATCH /api/checkouts/R924389851
Accept: application/json
X-Spree-Order-Token: f2PYypjfJirISaeUquBFTA
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=459&order[payment_attributes][][source_attributes][nonce]=fake-valid-visa-nonce&order[payment_attributes][][source_attributes][payment_type]=CreditCard
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
ETag: W/&quot;f5375d2eae13b0ba54d13f8f575c9128&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 710ef5e2-b6b2-4138-a783-d9f689d51db0
X-Runtime: 0.113978
Content-Length: 4257
200 OK
```


```json
{
  "id": 565,
  "number": "R924389851",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 650,
  "created_at": "2019-08-07T09:38:03.543Z",
  "updated_at": "2019-08-07T09:38:03.779Z",
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
  "token": "f2PYypjfJirISaeUquBFTA",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 459,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 1176,
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
    "country_id": 551,
    "country_iso": "US",
    "state_id": 540,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 551,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 540,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 551
    }
  },
  "ship_address": {
    "id": 1177,
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
    "country_id": 551,
    "country_iso": "US",
    "state_id": 540,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 551,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 540,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 551
    }
  },
  "line_items": [
    {
      "id": 479,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 1343,
      "vendor_id": 3871,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 1343,
        "name": "Product #23 - 2475",
        "sku": "SKU-38",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-23-2475",
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
            "id": 605,
            "name": "Size-16",
            "presentation": "S",
            "option_type_name": "foo-size-16",
            "option_type_id": 542,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 814,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #98",
      "adjustments": [

      ]
    }
  ],
  "payments": [

  ],
  "shipments": [
    {
      "id": 403,
      "tracking": null,
      "tracking_url": null,
      "number": "H68882634478",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R924389851",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 374,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 370,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 374,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 370,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 370,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 251,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 503,
              "name": "ShippingCategory #19"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 1343,
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
PATCH /api/checkouts/R396207996
Accept: application/json
X-Spree-Order-Token: T3Ud1zQDxALqFPSmmDrPZw
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=462&order[payment_attributes][][source_attributes][wallet_payment_source_id]=42
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
ETag: W/&quot;26b77633e033674a0bb9a9df0d10ddcf&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 1995487b-b945-42ac-a845-3425496cad42
X-Runtime: 0.118032
Content-Length: 4256
200 OK
```


```json
{
  "id": 568,
  "number": "R396207996",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 653,
  "created_at": "2019-08-07T09:38:05.333Z",
  "updated_at": "2019-08-07T09:38:05.573Z",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "email27@example.com",
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
  "token": "T3Ud1zQDxALqFPSmmDrPZw",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 462,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 1182,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "PO Box 1337",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10031",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 554,
    "country_iso": "US",
    "state_id": 543,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 554,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 543,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 554
    }
  },
  "ship_address": {
    "id": 1183,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "A Different Road",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10032",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 554,
    "country_iso": "US",
    "state_id": 543,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 554,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 543,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 554
    }
  },
  "line_items": [
    {
      "id": 482,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 1349,
      "vendor_id": 3889,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 1349,
        "name": "Product #26 - 513",
        "sku": "SKU-44",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-26-513",
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
            "id": 608,
            "name": "Size-19",
            "presentation": "S",
            "option_type_name": "foo-size-19",
            "option_type_id": 545,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 817,
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

  ],
  "shipments": [
    {
      "id": 409,
      "tracking": null,
      "tracking_url": null,
      "number": "H00315066787",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R396207996",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 380,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 373,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 380,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 373,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 373,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 254,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 506,
              "name": "ShippingCategory #22"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 1349,
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
POST /api/orders/R290771194/line_items
Accept: application/json
X-Spree-Order-Token: Ik9y_R3NhjUjqFg87YbRuw
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/:order_number/line_items`

#### Parameters


```json
line_item[variant_id]=1318&line_item[options][vendor_id]=3788
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
ETag: W/&quot;a05c6a8a748be97d22f646ce0cde018d&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 4975254b-547d-4c06-8db3-1ed8effb4cc8
X-Runtime: 0.097641
Content-Length: 849
201 Created
```


```json
{
  "id": 468,
  "quantity": 1,
  "price": "19.99",
  "variant_id": 1318,
  "vendor_id": 3788,
  "single_display_amount": "$19.99",
  "display_amount": "$19.99",
  "total": "19.99",
  "final_sale": false,
  "backordered": null,
  "promotionable": true,
  "variant": {
    "id": 1318,
    "name": "Product #7 - 9540",
    "sku": "SKU-13",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": false,
    "slug": "product-7-9540",
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
        "id": 596,
        "name": "Size-7",
        "presentation": "S",
        "option_type_name": "foo-size-7",
        "option_type_id": 533,
        "option_type_presentation": "Size"
      }
    ],
    "images": [

    ],
    "product_id": 798,
    "brand": null,
    "brand_slug": null,
    "brand_description": null
  },
  "vendor_name": "Vendor #28",
  "adjustments": [

  ]
}
```



## Deleting a line item


### Request

#### Endpoint

```plaintext
DELETE /api/orders/R179599643/line_items/465
Accept: application/json
X-Spree-Order-Token: q61-iKrdzw0jfuUxCb1K7w
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
X-Request-Id: db436cac-a187-42c3-a35d-fa2e2e963f6d
X-Runtime: 0.069079
204 No Content
```




## Updating a line item


### Request

#### Endpoint

```plaintext
PUT /api/orders/R115037822/line_items/466
Accept: application/json
X-Spree-Order-Token: _Xjgbavbov5ZqVhzyJSM0A
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
ETag: W/&quot;bea3bcb174e840d38a3202b5ef33aa11&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 7fbb7411-8ed1-4eca-bed0-cff2e5f9442b
X-Runtime: 0.121857
Content-Length: 845
200 OK
```


```json
{
  "id": 466,
  "quantity": 2,
  "price": "10.0",
  "variant_id": 1312,
  "vendor_id": 3775,
  "single_display_amount": "$10.00",
  "display_amount": "$20.00",
  "total": "20.0",
  "final_sale": false,
  "backordered": null,
  "promotionable": true,
  "variant": {
    "id": 1312,
    "name": "Product #4 - 8584",
    "sku": "SKU-7",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": false,
    "slug": "product-4-8584",
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
        "id": 593,
        "name": "Size-4",
        "presentation": "S",
        "option_type_name": "foo-size-4",
        "option_type_id": 530,
        "option_type_presentation": "Size"
      }
    ],
    "images": [

    ],
    "product_id": 795,
    "brand": null,
    "brand_slug": null,
    "brand_description": null
  },
  "vendor_name": "Vendor #17",
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
ETag: W/&quot;e2957629678655a450a7420a8a3e9233&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 5e6a21e0-2035-4201-9ac0-d1ae2acc5081
X-Runtime: 0.011265
Content-Length: 134
200 OK
```


```json
[
  {
    "id": 766,
    "name": "Kids",
    "navigation_url": "/navigation/kids",
    "parent_id": 765,
    "lft": 2,
    "depth": 1,
    "highlight": false,
    "header_link": false
  }
]
```



# Orders

Return an order, scoped to the current user

## Get my orders


### Request

#### Endpoint

```plaintext
GET /api/orders/mine
Accept: application/json
Authorization: Bearer fe7cf22b6c865797497b21cb44718ed79f90ac061e0639db
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
ETag: W/&quot;bdcf158f8033b1ff15f262254e779c15&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 9e665eb3-e05b-4dba-916e-87fb18d6ad20
X-Runtime: 0.016880
Content-Length: 305
200 OK
```


```json
{
  "orders": [
    {
      "number": "R141677840",
      "completed_at": "2019-08-07T09:38:02.247Z",
      "total": "120.0",
      "state": "Complete",
      "shipment_state": "shipped",
      "shipments": [
        {
          "number": "H24703384883",
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
GET /api/orders/R169872970
Accept: application/json
Authorization: Bearer cccb22723dee83377267e354dac73e194da40bc230f8ca73
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
ETag: W/&quot;468babec2cca70a8a791e95091dd0c33&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 45a28282-424d-4b4c-b407-646862c52830
X-Runtime: 0.175622
Content-Length: 9254
200 OK
```


```json
{
  "id": 562,
  "number": "R169872970",
  "item_total": "20.0",
  "total": "120.0",
  "ship_total": "100.0",
  "state": "complete",
  "adjustment_total": "0.0",
  "user_id": 638,
  "created_at": "2019-08-07T09:38:00.989Z",
  "updated_at": "2019-08-07T09:38:01.263Z",
  "completed_at": "2019-08-07T09:38:01.065Z",
  "payment_total": "120.0",
  "shipment_state": "shipped",
  "payment_state": "paid",
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
  "token": "4sJJ8Y8eY3l3eBpr8fjEQg",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 450,
      "name": "Credit Card",
      "partial_name": "gateway",
      "method_type": "gateway"
    },
    {
      "id": 451,
      "name": "Credit Card",
      "partial_name": "gateway",
      "method_type": "gateway"
    }
  ],
  "bill_address": {
    "id": 1170,
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
    "country_id": 547,
    "country_iso": "US",
    "state_id": 536,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 547,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 536,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 547
    }
  },
  "ship_address": {
    "id": 1171,
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
    "country_id": 547,
    "country_iso": "US",
    "state_id": 536,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 547,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 536,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 547
    }
  },
  "line_items": [
    {
      "id": 473,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 1335,
      "vendor_id": 3845,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 1335,
        "name": "Product #19 - 6041",
        "sku": "SKU-30",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-19-6041",
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
            "id": 601,
            "name": "Size-12",
            "presentation": "S",
            "option_type_name": "foo-size-12",
            "option_type_id": 538,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 810,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #76",
      "adjustments": [
        {
          "id": 86,
          "source_type": "Spree::TaxRate",
          "source_id": 15,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 473,
          "amount": "2.0",
          "label": "VAT 5%",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-08-07T09:38:01.234Z",
          "updated_at": "2019-08-07T09:38:01.245Z",
          "display_amount": "$2.00"
        },
        {
          "id": 80,
          "source_type": "Spree::PromotionAction",
          "source_id": 38,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 473,
          "amount": "5.0",
          "label": "foo",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-08-07T09:38:01.157Z",
          "updated_at": "2019-08-07T09:38:01.157Z",
          "display_amount": "$5.00"
        },
        {
          "id": 79,
          "source_type": "Spree::PromotionAction",
          "source_id": 38,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 473,
          "amount": "5.0",
          "label": "foo",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-08-07T09:38:01.147Z",
          "updated_at": "2019-08-07T09:38:01.147Z",
          "display_amount": "$5.00"
        }
      ]
    },
    {
      "id": 474,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 1335,
      "vendor_id": 3845,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 1335,
        "name": "Product #19 - 6041",
        "sku": "SKU-30",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-19-6041",
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
            "id": 601,
            "name": "Size-12",
            "presentation": "S",
            "option_type_name": "foo-size-12",
            "option_type_id": 538,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 810,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #76",
      "adjustments": [
        {
          "id": 87,
          "source_type": "Spree::TaxRate",
          "source_id": 16,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 474,
          "amount": "1.5",
          "label": "VAT 5%",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-08-07T09:38:01.260Z",
          "updated_at": "2019-08-07T09:38:01.272Z",
          "display_amount": "$1.50"
        },
        {
          "id": 81,
          "source_type": "Spree::PromotionAction",
          "source_id": 38,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 474,
          "amount": "5.0",
          "label": "bar",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-08-07T09:38:01.166Z",
          "updated_at": "2019-08-07T09:38:01.166Z",
          "display_amount": "$5.00"
        }
      ]
    }
  ],
  "payments": [
    {
      "id": 219,
      "source_type": "Spree::CreditCard",
      "source_id": 189,
      "amount": "120.0",
      "display_amount": "$120.00",
      "payment_method_id": 450,
      "state": "completed",
      "avs_response": null,
      "created_at": "2019-08-07T09:38:01.082Z",
      "updated_at": "2019-08-07T09:38:01.082Z",
      "payment_method": {
        "id": 450,
        "name": "Credit Card"
      },
      "source": {
        "id": 189,
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
      "id": 399,
      "tracking": "U10000",
      "tracking_url": null,
      "number": "H03250787462",
      "cost": "100.0",
      "shipped_at": "2019-08-07T09:38:01.107Z",
      "state": "shipped",
      "order_id": "R169872970",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 370,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 367,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 370,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 367,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 367,
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
              "id": 499,
              "name": "ShippingCategory #15"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 1335,
          "quantity": 1,
          "states": {
            "shipped": 1
          }
        },
        {
          "variant_id": 1335,
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
          "adjustable_id": 399,
          "amount": "-10.0",
          "label": "Shipping",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-08-07T09:38:01.181Z",
          "updated_at": "2019-08-07T09:38:01.181Z",
          "display_amount": "-$10.00"
        },
        {
          "id": 82,
          "source_type": "Spree::PromotionAction",
          "source_id": 38,
          "adjustable_type": "Spree::Shipment",
          "adjustable_id": 399,
          "amount": "-9.99",
          "label": "Shipping",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-08-07T09:38:01.174Z",
          "updated_at": "2019-08-07T09:38:01.174Z",
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
      "adjustable_id": 562,
      "amount": "20.0",
      "label": "adj1",
      "promotion_code_id": null,
      "finalized": false,
      "eligible": true,
      "created_at": "2019-08-07T09:38:01.187Z",
      "updated_at": "2019-08-07T09:38:01.187Z",
      "display_amount": "$20.00"
    },
    {
      "id": 85,
      "source_type": "Spree::Promotion",
      "source_id": 56,
      "adjustable_type": "Spree::Order",
      "adjustable_id": 562,
      "amount": "30.0",
      "label": "adj2",
      "promotion_code_id": null,
      "finalized": false,
      "eligible": true,
      "created_at": "2019-08-07T09:38:01.193Z",
      "updated_at": "2019-08-07T09:38:01.193Z",
      "display_amount": "$30.00"
    }
  ],
  "permissions": {
    "can_update": false
  },
  "credit_cards": [
    {
      "id": 189,
      "month": "12",
      "year": "2020",
      "cc_type": null,
      "last_digits": "1111",
      "name": "Spree Commerce",
      "address": {
        "id": 1170,
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
        "country_id": 547,
        "country_iso": "US",
        "state_id": 536,
        "state_name": null,
        "state_text": "AL",
        "country": {
          "id": 547,
          "iso_name": "UNITED STATES",
          "iso": "US",
          "iso3": "USA",
          "name": "United States",
          "numcode": 840
        },
        "state": {
          "id": 536,
          "name": "Alabama",
          "abbr": "AL",
          "country_id": 547
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
GET /api/orders/R713270624
Accept: application/json
Authorization: 2a58abc24b63ad360705a757f5fa30176096555b9316c18e
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
X-Request-Id: f591fff9-d61e-4bfc-baa8-82c8f32f50d8
X-Runtime: 0.011372
Content-Length: 58
401 Unauthorized
```


```json
{
  "error": "You are not authorized to perform that action."
}
```



# Passwords

Validate user email and password. Does not handle any session and only return the user

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
user[email]=email23%40example.com
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
X-Request-Id: df392a0c-0e19-48bd-8c49-8a10ceb40911
X-Runtime: 0.003437
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
Authorization: Bearer 39908200bf7c10a48514530bb4652af85bc57958a2ce9e10
ETag: W/&quot;ca4c3e118f1ce9afe7982174a62d555f&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 03c40f03-3cab-4418-9c55-19f44c65df72
X-Runtime: 0.010139
Content-Length: 553
200 OK
```


```json
{
  "id": 647,
  "email": "email21@example.com",
  "persistence_token": null,
  "perishable_token": null,
  "last_request_at": null,
  "login": "email21@example.com",
  "ship_address_id": null,
  "bill_address_id": null,
  "created_at": "2019-08-07T09:38:03.247Z",
  "updated_at": "2019-08-07T09:38:03.249Z",
  "spree_api_key": "39908200bf7c10a48514530bb4652af85bc57958a2ce9e10",
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
X-Request-Id: 3f92a92d-b967-4d5d-9153-1b7d299fe920
X-Runtime: 0.022277
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
Date: Wed, 07 Aug 2019 09:38:00 GMT
Surrogate-Control: max-age=900
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;7537becefcd10e79cf8f66b8790afee5&quot;
X-Request-Id: 95201cc8-0df7-4dbf-bc0a-3c9a61bf7998
X-Runtime: 0.080625
Content-Length: 918
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
      "id": 807,
      "name": "Product #16 - 2011",
      "description": "As seen on TV!",
      "available_on": "2018-08-07T09:38:00.102Z",
      "slug": "product-16-2011",
      "meta_description": null,
      "meta_keywords": null,
      "shipping_category_id": 496,
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
        "id": 1331,
        "name": "Product #16 - 2011",
        "sku": "SKU-27",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-16-2011",
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
GET /api/products/product-17-9551
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
Date: Wed, 07 Aug 2019 09:38:00 GMT
Surrogate-Control: max-age=900
Surrogate-Key: product_id=1
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;5059be061d2a89f705515405693f6bc7&quot;
X-Request-Id: 5baa8681-46fa-4728-9b01-2ac386d05f6d
X-Runtime: 0.050680
Content-Length: 836
200 OK
```


```json
{
  "id": 808,
  "name": "Product #17 - 9551",
  "description": "As seen on TV!",
  "available_on": "2018-08-07T09:38:00.303Z",
  "slug": "product-17-9551",
  "meta_description": null,
  "meta_keywords": null,
  "shipping_category_id": 497,
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
    "id": 1332,
    "name": "Product #17 - 9551",
    "sku": "SKU-28",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": true,
    "slug": "product-17-9551",
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
X-Request-Id: 5f2b397e-a892-4790-9c90-1a136639fa38
X-Runtime: 0.030066
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
ETag: W/&quot;30ef8ff5c586c8d1a27847bb7ca216c4&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 1a47072d-136b-4dd1-8c6c-495996759b78
X-Runtime: 0.075441
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
      "id": 803,
      "name": "Product #12 - 8908",
      "description": "As seen on TV!",
      "available_on": "2018-08-07T09:37:59.313Z",
      "slug": "product-12-8908",
      "meta_description": null,
      "meta_keywords": null,
      "shipping_category_id": 494,
      "taxon_ids": [
        758
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
        "id": 1327,
        "name": "Product #12 - 8908",
        "sku": "SKU-23",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-12-8908",
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
          "taxon_id": 758,
          "position": 1,
          "taxon": {
            "id": 758,
            "name": "Ruby on Rails",
            "pretty_name": "Ruby on Rails",
            "permalink": "ruby-on-rails",
            "parent_id": null,
            "taxonomy_id": 337
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
GET /api/taxons/products?id=762
Host: example.org
Cookie: 
```

`GET /api/taxons/products`

#### Parameters


```json
id: 762
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
ETag: W/&quot;5da00bbf0bc39db5d8b7c62627b3b3df&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 60fb3402-92b7-4a96-b957-55fee8d691d7
X-Runtime: 0.051651
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
      "id": 805,
      "name": "Product #14 - 4813",
      "description": "As seen on TV!",
      "available_on": "2018-08-07T09:37:59.758Z",
      "slug": "product-14-4813",
      "meta_description": null,
      "meta_keywords": null,
      "shipping_category_id": 495,
      "taxon_ids": [
        762
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
        "id": 1329,
        "name": "Product #14 - 4813",
        "sku": "SKU-25",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-14-4813",
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
          "taxon_id": 762,
          "position": 1,
          "taxon": {
            "id": 762,
            "name": "Ruby on Rails",
            "pretty_name": "Ruby on Rails",
            "permalink": "ruby-on-rails",
            "parent_id": null,
            "taxonomy_id": 339
          }
        }
      ]
    }
  ]
}
```



# Return Authorizations

Get a single user return authorziation

## Can get another user&#39;s return authorization


### Request

#### Endpoint

```plaintext
GET /api/returns/RA464380556
Authorization: Bearer cea4ce7d753196b130ce970965086b8a751fcf141d8b8023
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
ETag: W/&quot;28c2e0f95a480f0e431b94065756fccd&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 260e3571-991f-4006-8c53-f310973d4085
X-Runtime: 0.047474
Content-Length: 2772
200 OK
```


```json
{
  "id": 19,
  "number": "RA464380556",
  "state": "authorized",
  "order_id": 560,
  "memo": "Items were broken",
  "created_at": "2019-08-07T09:37:58.679Z",
  "updated_at": "2019-08-07T09:37:58.679Z",
  "reason": {
    "id": 60,
    "name": "Defect #5",
    "active": true,
    "mutable": true,
    "created_at": "2019-08-07T09:37:58.674Z",
    "updated_at": "2019-08-07T09:37:58.674Z",
    "mirakl_code": null
  },
  "order": {
    "id": 560,
    "number": "R921294367",
    "item_total": "10.0",
    "total": "110.0",
    "state": "complete",
    "adjustment_total": "0.0",
    "user_id": 635,
    "completed_at": "2019-08-07T09:37:58.594Z",
    "bill_address_id": 1166,
    "ship_address_id": 1167,
    "payment_total": "110.0",
    "shipment_state": "shipped",
    "payment_state": "paid",
    "email": "email9@example.com",
    "special_instructions": null,
    "created_at": "2019-08-07T09:37:58.521Z",
    "updated_at": "2019-08-07T09:37:58.657Z",
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
    "guest_token": "THcDebN_4Nb3IZf-sjWhSA",
    "canceled_at": null,
    "canceler_id": null,
    "store_id": 599,
    "approver_name": null,
    "frontend_viewable": true
  },
  "ship_address": {
    "id": 1167,
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
    "country_id": 540,
    "country_iso": "US",
    "state_id": 529,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 540,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 529,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 540
    }
  },
  "bill_address": {
    "id": 1166,
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
    "country_id": 540,
    "country_iso": "US",
    "state_id": 529,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 540,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 529,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 540
    }
  },
  "return_items": [
    {
      "name": "Product #10 - 1156",
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
        "id": 446,
        "name": "Credit Card"
      },
      "source": {
        "id": 187,
        "month": "12",
        "year": "2020",
        "cc_type": null,
        "last_digits": "1111",
        "name": "Spree Commerce",
        "gateway_customer_profile_id": "BGS-133345",
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
Authorization: Bearer df2e0a4296dc7f7faaf5ab4e1e336a9db527e04e727d92c0
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
ETag: W/&quot;2bf0a7e53d23c39e8f0e4b71b7f07655&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 03fba6d6-019a-4e9f-bef3-777800bb0586
X-Runtime: 0.010931
Content-Length: 164
200 OK
```


```json
{
  "return_authorizations": [
    {
      "number": "RA424482557",
      "created_at": "2019-08-07T09:37:59.194Z",
      "return_amount": "10.0",
      "order_number": "R614050123",
      "state": "authorized"
    }
  ]
}
```



## returns a 200


### Request

#### Endpoint

```plaintext
GET /api/returns/RA280608457
Authorization: Bearer c1a419302e1ae1b0bf652135ff9e5507cdc83e7a8f31171a
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
ETag: W/&quot;a1be028d2c78d066d24cbe81fd49a1d1&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 7780d860-8cb0-4adf-95d0-14c59fe60a49
X-Runtime: 0.075276
Content-Length: 2694
200 OK
```


```json
{
  "id": 17,
  "number": "RA280608457",
  "state": "authorized",
  "order_id": 558,
  "memo": "Items were broken",
  "created_at": "2019-08-07T09:37:57.653Z",
  "updated_at": "2019-08-07T09:37:57.653Z",
  "reason": {
    "id": 56,
    "name": "Defect #1",
    "active": true,
    "mutable": true,
    "created_at": "2019-08-07T09:37:57.641Z",
    "updated_at": "2019-08-07T09:37:57.641Z",
    "mirakl_code": null
  },
  "order": {
    "id": 558,
    "number": "R467338233",
    "item_total": "10.0",
    "total": "110.0",
    "state": "complete",
    "adjustment_total": "0.0",
    "user_id": 632,
    "completed_at": "2019-08-07T09:37:57.477Z",
    "bill_address_id": 1162,
    "ship_address_id": 1163,
    "payment_total": "110.0",
    "shipment_state": "shipped",
    "payment_state": "paid",
    "email": "email6@example.com",
    "special_instructions": null,
    "created_at": "2019-08-07T09:37:57.417Z",
    "updated_at": "2019-08-07T09:37:57.597Z",
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
    "guest_token": "GlPSqMDPzmh0vcANFr34JQ",
    "canceled_at": null,
    "canceler_id": null,
    "store_id": 597,
    "approver_name": null,
    "frontend_viewable": true
  },
  "ship_address": {
    "id": 1163,
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
    "country_id": 538,
    "country_iso": "US",
    "state_id": 527,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 538,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 527,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 538
    }
  },
  "bill_address": {
    "id": 1162,
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
    "country_id": 538,
    "country_iso": "US",
    "state_id": 527,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 538,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 527,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 538
    }
  },
  "return_items": [
    {
      "name": "Product #8 - 6705",
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
        "id": 442,
        "name": "Credit Card"
      },
      "source": {
        "id": 185,
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
GET /api/returns/RA283770518
Authorization: Bearer 4673618eaf4a15768b6d6b27447fef7b18dc90d8a7d8b1b3
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
X-Request-Id: ecffc497-be31-44b1-84ac-10c70ebd7dc5
X-Runtime: 0.011876
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
Authorization: Bearer 2eb54c20a003556665066777c65e1eee63f2400fc65d1fc0
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
ETag: W/&quot;0bb1a198642ecd4c3c56f7f3bb0c01d8&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 00d0d9ad-0597-4160-8581-0faf79241787
X-Runtime: 0.034836
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
      "created_at": "2019-08-07T09:38:02.527Z"
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



## Login

Validate user email and password. Does not handle any session and only return the user

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
user[email]=email29%40example.com&user[password]=secret
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
Authorization: Bearer 709740af5569805995239fea7bc7c0a30b474552b68d8d59
ETag: W/&quot;801a3bba74a4b50020476884406a85fc&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 9b1cb560-a402-4177-9d15-5ffc2bbfcacd
X-Runtime: 0.005600
Content-Length: 553
200 OK
```


```json
{
  "id": 655,
  "email": "email29@example.com",
  "persistence_token": null,
  "perishable_token": null,
  "last_request_at": null,
  "login": "email29@example.com",
  "ship_address_id": null,
  "bill_address_id": null,
  "created_at": "2019-08-07T09:38:09.727Z",
  "updated_at": "2019-08-07T09:38:09.729Z",
  "spree_api_key": "709740af5569805995239fea7bc7c0a30b474552b68d8d59",
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



## Mine

Get user account details, stored addresses, and stored credit cards

### Request

#### Endpoint

```plaintext
GET /api/users/mine
Authorization: Bearer cae9dc3bf5840a24755c444e59163780edd7e9ba819a7d12
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
Authorization: Bearer cae9dc3bf5840a24755c444e59163780edd7e9ba819a7d12
ETag: W/&quot;4d1afa6ebb6d0de33b5580e4102e1ac0&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: fbcabf0f-4012-4d3a-8725-98173eb5d94e
X-Runtime: 0.029383
Content-Length: 1309
200 OK
```


```json
{
  "email": "email30@example.com",
  "first_name": null,
  "last_name": null,
  "id": 656,
  "subscribed": null,
  "addresses": [
    {
      "id": 1187,
      "firstname": "John",
      "lastname": null,
      "full_name": "John",
      "address1": "A Different Road",
      "address2": "Northwest",
      "city": "Herndon",
      "zipcode": "10036",
      "phone": "555-555-0199",
      "company": "Company",
      "alternative_phone": "555-555-0199",
      "country_id": 556,
      "country_iso": "US",
      "state_id": 545,
      "state_name": null,
      "state_text": "AL",
      "country_name": "United States",
      "default": true
    },
    {
      "id": 1186,
      "firstname": "John",
      "lastname": null,
      "full_name": "John",
      "address1": "PO Box 1337",
      "address2": "Northwest",
      "city": "Herndon",
      "zipcode": "10035",
      "phone": "555-555-0199",
      "company": "Company",
      "alternative_phone": "555-555-0199",
      "country_id": 556,
      "country_iso": "US",
      "state_id": 545,
      "state_name": null,
      "state_text": "AL",
      "country_name": "United States",
      "default": false
    }
  ],
  "payment_sources": [
    {
      "default": true,
      "id": 73,
      "payment_type": "CreditCard",
      "token": null,
      "created_at": "2019-08-07T09:38:09.788Z",
      "cc_type": null,
      "last_digits": null,
      "month": null,
      "year": null
    },
    {
      "default": false,
      "id": 74,
      "payment_type": "ApplePayCard",
      "token": null,
      "created_at": "2019-08-07T09:38:09.802Z",
      "cc_type": null,
      "last_digits": null,
      "month": null,
      "year": null
    },
    {
      "default": false,
      "id": 75,
      "payment_type": "PayPalAccount",
      "token": null,
      "created_at": "2019-08-07T09:38:09.815Z",
      "email": null
    }
  ]
}
```



## Signup

Create a new user and return a bearer header to be used for further user related request

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
Authorization: Bearer 8bca054b4e3e76968b6becc87d07f51e729bfe6edd75ea16
ETag: W/&quot;1082305f9ad2e9782b82fb40e43e45bb&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 3b1b7026-7138-432a-afea-bbc53034f249
X-Runtime: 0.017851
Content-Length: 157
201 Created
```


```json
{
  "id": 657,
  "email": "test@example.com",
  "created_at": "2019-08-07T09:38:09.858Z",
  "updated_at": "2019-08-07T09:38:09.859Z",
  "bill_address": null,
  "ship_address": null
}
```



# Variant



## Fetching a variant


### Request

#### Endpoint

```plaintext
GET /api/variants/1341
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
ETag: W/&quot;6befb03dd6e89d0d3e479314d675b456&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: d6cec824-d99c-4506-861b-ba11d5242203
X-Runtime: 0.100020
Content-Length: 1460
200 OK
```


```json
{
  "id": 1341,
  "name": "Product #22 - 5048",
  "sku": "SKU-36",
  "weight": "0.0",
  "height": null,
  "width": null,
  "depth": null,
  "is_master": false,
  "slug": "product-22-5048",
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
      "id": 604,
      "name": "Size-15",
      "presentation": "S",
      "option_type_name": "foo-size-15",
      "option_type_id": 541,
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
      "attachment_updated_at": "2019-08-07T09:38:02.826Z",
      "attachment_width": 489,
      "attachment_height": 490,
      "alt": null,
      "viewable_type": "Spree::Variant",
      "viewable_id": 1341,
      "mini_url": "/spree/products/2/mini/thinking-cat.jpg?1565170682",
      "small_url": "/spree/products/2/small/thinking-cat.jpg?1565170682",
      "product_url": "/spree/products/2/product/thinking-cat.jpg?1565170682",
      "large_url": "/spree/products/2/large/thinking-cat.jpg?1565170682"
    }
  ],
  "variant_properties": [

  ],
  "stock_items": [

  ],
  "prices": [
    {
      "id": 2556,
      "vendor_id": 3866,
      "price": "10.0",
      "original_price": "10.0",
      "discount_percent": 0.0,
      "total_on_hand": 0,
      "country_iso": null,
      "final_sale": false,
      "on_sale": false
    },
    {
      "id": 2557,
      "vendor_id": 3867,
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
Authorization: Bearer 8bfe1c404b3780037b3276a261827bc130ec50ee47975923
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
ETag: W/&quot;423039ebd4f2703eddde52f798588e48&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: dcf5ec77-8cc6-4115-a1dd-ec945e218c6e
X-Runtime: 0.036763
Content-Length: 199
200 OK
```


```json
[
  {
    "id": 39,
    "user_id": 642,
    "payment_source_type": "SolidusPaypalBraintree::Source",
    "payment_source_id": 68,
    "default": false,
    "created_at": "2019-08-07T09:38:02.365Z",
    "updated_at": "2019-08-07T09:38:02.365Z"
  }
]
```



## Remove the payment from the user wallet


### Request

#### Endpoint

```plaintext
DELETE /api/wallet_payment_sources/40
Accept: application/json
Authorization: Bearer 99db8c618b9c4a7a36d58e848a3a0dd2e6c764b74a8a4d80
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
X-Request-Id: 038d3ea6-30e8-4384-818e-e08f0ee05944
X-Runtime: 0.014850
204 No Content
```




## Set a wallet payment source as the default user payment method


### Request

#### Endpoint

```plaintext
POST /api/wallet_payment_sources/41/default
Accept: application/json
Authorization: Bearer f8e850fb2f765dbfde42482fa828697f909967169f782dd6
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
X-Request-Id: 1f31fd64-c3f6-426c-9e83-365955edd6e4
X-Runtime: 0.010523
204 No Content
```




