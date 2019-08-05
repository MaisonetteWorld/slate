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
PUT /api/orders/R305401437/addresses/1033
Accept: application/json
X-Spree-Order-Token: 3fEClUCeNWkgX5uaJ27YLw
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
ETag: W/&quot;cf469e008006085e10912b73d8d22770&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 4df44543-87b8-4596-a024-45abc45afd81
X-Runtime: 0.042391
Content-Length: 514
200 OK
```


```json
{
  "id": 1034,
  "firstname": "John the Tester",
  "lastname": null,
  "full_name": "John the Tester",
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
}
```



# Braintree transactions



## Creating a PayPal express checkout transaction


### Request

#### Endpoint

```plaintext
POST /api/braintree/transactions
Accept: application/json
X-Spree-Order-Token: LM_b1Xk3OXZx3UZqIw_vug
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/braintree/transactions`

#### Parameters


```json
order_id=R738563506&payment_method_id=408&options[restart_checkout]=true&transaction[email]=maryellen.oga%40mckenziemcglynn.com&transaction[nonce]=fake-paypal-billing-agreement-nonce&transaction[phone]=555-555-0199&transaction[address_attributes][first_name]=John&transaction[address_attributes][last_name]=Stamm&transaction[address_attributes][address_line_1]=A+Different+Road&transaction[address_attributes][city]=Herndon&transaction[address_attributes][state_code]=AL&transaction[address_attributes][zip]=10025&transaction[address_attributes][country_code]=US&transaction[payment_type]=PayPalAccount
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
ETag: W/&quot;486392499de43356933773e09b6f2400&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 30eff4c1-f834-4c26-ace4-be50566ee8cc
X-Runtime: 0.204169
Content-Length: 4694
200 OK
```


```json
{
  "id": 499,
  "number": "R738563506",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2019-08-05T15:21:17.785Z",
  "updated_at": "2019-08-05T15:21:17.992Z",
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
  "token": "LM_b1Xk3OXZx3UZqIw_vug",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 408,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 1037,
    "firstname": "John",
    "lastname": "Stamm",
    "full_name": "John Stamm",
    "address1": "A Different Road",
    "address2": null,
    "city": "Herndon",
    "zipcode": "10025",
    "phone": "555-555-0199",
    "company": null,
    "alternative_phone": null,
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
    "id": 1037,
    "firstname": "John",
    "lastname": "Stamm",
    "full_name": "John Stamm",
    "address1": "A Different Road",
    "address2": null,
    "city": "Herndon",
    "zipcode": "10025",
    "phone": "555-555-0199",
    "company": null,
    "alternative_phone": null,
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
      "id": 430,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 1171,
      "vendor_id": 3445,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 1171,
        "name": "Product #21 - 9413",
        "sku": "SKU-34",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-21-9413",
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
      "vendor_name": "Vendor #82",
      "adjustments": [

      ]
    }
  ],
  "payments": [
    {
      "id": 197,
      "source_type": "SolidusPaypalBraintree::Source",
      "source_id": 60,
      "amount": "110.0",
      "display_amount": "$110.00",
      "payment_method_id": 408,
      "state": "checkout",
      "avs_response": null,
      "created_at": "2019-08-05T15:21:17.893Z",
      "updated_at": "2019-08-05T15:21:17.893Z",
      "payment_method": {
        "id": 408,
        "name": "Braintree"
      },
      "source": {
        "id": 60,
        "payment_type": "PayPalAccount",
        "token": "bgx899",
        "created_at": "2019-08-05T15:21:17.892Z",
        "email": "jane.doe@paypal.com"
      }
    }
  ],
  "shipments": [
    {
      "id": 351,
      "tracking": null,
      "tracking_url": null,
      "number": "H07234004187",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R738563506",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 335,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 331,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 335,
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



## Creating an ApplePay one-click checkout transaction


### Request

#### Endpoint

```plaintext
POST /api/braintree/transactions
Accept: application/json
X-Spree-Order-Token: FCAF3mi56VuctsitMLoq1Q
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/braintree/transactions`

#### Parameters


```json
order_id=R707884065&payment_method_id=409&options[restart_checkout]=true&transaction[email]=maryellen.oga%40mckenziemcglynn.com&transaction[nonce]=fake-apple-pay-visa-nonce&transaction[phone]=555-555-0199&transaction[address_attributes][first_name]=John&transaction[address_attributes][last_name]=Stamm&transaction[address_attributes][address_line_1]=A+Different+Road&transaction[address_attributes][city]=Herndon&transaction[address_attributes][state_code]=AL&transaction[address_attributes][zip]=10027&transaction[address_attributes][country_code]=US&transaction[payment_type]=ApplePayCard
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
ETag: W/&quot;6feafbe27a9bcd14baa56d5799065f99&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: d2a06a47-3418-44af-8db6-f2370b62d80f
X-Runtime: 0.177054
Content-Length: 4710
200 OK
```


```json
{
  "id": 500,
  "number": "R707884065",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2019-08-05T15:21:18.229Z",
  "updated_at": "2019-08-05T15:21:18.399Z",
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
  "token": "FCAF3mi56VuctsitMLoq1Q",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 409,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 1040,
    "firstname": "John",
    "lastname": "Stamm",
    "full_name": "John Stamm",
    "address1": "A Different Road",
    "address2": null,
    "city": "Herndon",
    "zipcode": "10027",
    "phone": "555-555-0199",
    "company": null,
    "alternative_phone": null,
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
    "id": 1040,
    "firstname": "John",
    "lastname": "Stamm",
    "full_name": "John Stamm",
    "address1": "A Different Road",
    "address2": null,
    "city": "Herndon",
    "zipcode": "10027",
    "phone": "555-555-0199",
    "company": null,
    "alternative_phone": null,
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
      "id": 431,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 1173,
      "vendor_id": 3451,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 1173,
        "name": "Product #22 - 8366",
        "sku": "SKU-36",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-22-8366",
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
      "vendor_name": "Vendor #87",
      "adjustments": [

      ]
    }
  ],
  "payments": [
    {
      "id": 198,
      "source_type": "SolidusPaypalBraintree::Source",
      "source_id": 61,
      "amount": "110.0",
      "display_amount": "$110.00",
      "payment_method_id": 409,
      "state": "checkout",
      "avs_response": null,
      "created_at": "2019-08-05T15:21:18.302Z",
      "updated_at": "2019-08-05T15:21:18.302Z",
      "payment_method": {
        "id": 409,
        "name": "Braintree"
      },
      "source": {
        "id": 61,
        "payment_type": "ApplePayCard",
        "token": "cg7hsk",
        "created_at": "2019-08-05T15:21:18.301Z",
        "card_type": "Apple Pay - Visa",
        "last_4": "1881"
      }
    }
  ],
  "shipments": [
    {
      "id": 353,
      "tracking": null,
      "tracking_url": null,
      "number": "H05631628332",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R707884065",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 337,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 332,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 337,
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



# Checkout



## Completing the checkout when the order includes a Braintree payment


### Request

#### Endpoint

```plaintext
PUT /api/checkouts/R888274536/complete
Accept: application/json
X-Spree-Order-Token: Exy5gt-QA3RWnreng2cmXw
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
ETag: W/&quot;6e17128d5fccdff012f8c7f7f1a39b78&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 1a45c08b-1fb2-4474-ab21-259f6d90992d
X-Runtime: 2.370493
Content-Length: 4826
200 OK
```


```json
{
  "id": 487,
  "number": "R888274536",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "complete",
  "adjustment_total": "0.0",
  "user_id": 561,
  "created_at": "2019-08-05T15:21:08.989Z",
  "updated_at": "2019-08-05T15:21:12.475Z",
  "completed_at": "2019-08-05T15:21:12.475Z",
  "payment_total": "110.0",
  "shipment_state": "ready",
  "payment_state": "paid",
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
  "token": "Exy5gt-QA3RWnreng2cmXw",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 393,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    },
    {
      "id": 394,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 1010,
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
    "country_id": 482,
    "country_iso": "US",
    "state_id": 471,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 482,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 471,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 482
    }
  },
  "ship_address": {
    "id": 1011,
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
    "country_id": 482,
    "country_iso": "US",
    "state_id": 471,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 482,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 471,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 482
    }
  },
  "line_items": [
    {
      "id": 415,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 1145,
      "vendor_id": 3373,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 1145,
        "name": "Product #8 - 4224",
        "sku": "SKU-8",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-8-4224",
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
        "product_id": 690,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #21",
      "adjustments": [

      ]
    }
  ],
  "payments": [
    {
      "id": 193,
      "source_type": "SolidusPaypalBraintree::Source",
      "source_id": 55,
      "amount": "110.0",
      "display_amount": "$110.00",
      "payment_method_id": 393,
      "state": "completed",
      "avs_response": "M",
      "created_at": "2019-08-05T15:21:09.205Z",
      "updated_at": "2019-08-05T15:21:12.330Z",
      "payment_method": {
        "id": 393,
        "name": "Braintree"
      },
      "source": {
        "id": 55,
        "payment_type": "CreditCard",
        "token": "k3qvnk",
        "created_at": "2019-08-05T15:21:09.204Z",
        "cc_type": "Visa",
        "last_digits": "1881"
      }
    }
  ],
  "shipments": [
    {
      "id": 335,
      "tracking": "U10000",
      "tracking_url": null,
      "number": "H66588076810",
      "cost": "100.0",
      "shipped_at": null,
      "state": "ready",
      "order_id": "R888274536",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 319,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 320,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 319,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 320,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 320,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 225,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 430,
              "name": "ShippingCategory #6"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 1145,
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
PATCH /api/checkouts/R167800466
Accept: application/json
X-Spree-Order-Token: 3hAc-evciwmgCi9tcVvmOw
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=395&order[payment_attributes][][source_attributes][nonce]=fake-apple-pay-visa-nonce&order[payment_attributes][][source_attributes][payment_type]=ApplePayCard
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
ETag: W/&quot;f39eba574b576b8c6f19b0a6a650d31d&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: f88e07f1-7968-4750-ad3a-34bcfd1154b0
X-Runtime: 0.092428
Content-Length: 4249
200 OK
```


```json
{
  "id": 488,
  "number": "R167800466",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 562,
  "created_at": "2019-08-05T15:21:13.276Z",
  "updated_at": "2019-08-05T15:21:13.519Z",
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
  "token": "3hAc-evciwmgCi9tcVvmOw",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 395,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 1012,
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
  "ship_address": {
    "id": 1013,
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
  "line_items": [
    {
      "id": 416,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 1147,
      "vendor_id": 3379,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 1147,
        "name": "Product #9 - 584",
        "sku": "SKU-10",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-9-584",
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
            "id": 468,
            "name": "Size-2",
            "presentation": "S",
            "option_type_name": "foo-size-2",
            "option_type_id": 468,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 691,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
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
      "id": 337,
      "tracking": null,
      "tracking_url": null,
      "number": "H66334016556",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R167800466",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 321,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 321,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 321,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 321,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 321,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 226,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 431,
              "name": "ShippingCategory #7"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 1147,
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
PATCH /api/checkouts/R296640667
Accept: application/json
X-Spree-Order-Token: Z2dCdemmmmI-XStYNeDWBw
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=396&order[payment_attributes][][source_attributes][nonce]=fake-paypal-billing-agreement-nonce&order[payment_attributes][][source_attributes][payment_type]=PayPalAccount
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
ETag: W/&quot;60f06425ae669c1640588ea37f314ecf&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: badac75e-1a6c-4eec-a635-05824e1836d9
X-Runtime: 0.085004
Content-Length: 4253
200 OK
```


```json
{
  "id": 489,
  "number": "R296640667",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 563,
  "created_at": "2019-08-05T15:21:13.770Z",
  "updated_at": "2019-08-05T15:21:13.958Z",
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
  "token": "Z2dCdemmmmI-XStYNeDWBw",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 396,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 1014,
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
    "country_id": 484,
    "country_iso": "US",
    "state_id": 473,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 484,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 473,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 484
    }
  },
  "ship_address": {
    "id": 1015,
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
    "country_id": 484,
    "country_iso": "US",
    "state_id": 473,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 484,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 473,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 484
    }
  },
  "line_items": [
    {
      "id": 417,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 1149,
      "vendor_id": 3385,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 1149,
        "name": "Product #10 - 4516",
        "sku": "SKU-12",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-10-4516",
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
            "id": 469,
            "name": "Size-3",
            "presentation": "S",
            "option_type_name": "foo-size-3",
            "option_type_id": 469,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 692,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
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
      "id": 339,
      "tracking": null,
      "tracking_url": null,
      "number": "H81412811718",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R296640667",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 323,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 322,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 323,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 322,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 322,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 227,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 432,
              "name": "ShippingCategory #8"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 1149,
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
PATCH /api/checkouts/R374648671
Accept: application/json
X-Spree-Order-Token: vYzJJOcz7Zz3pRYGiL71rQ
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=397&order[payment_attributes][][source_attributes][nonce]=fake-valid-visa-nonce&order[payment_attributes][][source_attributes][payment_type]=CreditCard
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
ETag: W/&quot;4aa26261ae086a83370eb2fd0a99334d&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: dd153ddb-f10d-4927-a321-35a9d278cf70
X-Runtime: 0.087545
Content-Length: 4253
200 OK
```


```json
{
  "id": 490,
  "number": "R374648671",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 564,
  "created_at": "2019-08-05T15:21:14.198Z",
  "updated_at": "2019-08-05T15:21:14.371Z",
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
  "token": "vYzJJOcz7Zz3pRYGiL71rQ",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 397,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 1016,
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
    "country_id": 485,
    "country_iso": "US",
    "state_id": 474,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 485,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 474,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 485
    }
  },
  "ship_address": {
    "id": 1017,
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
    "country_id": 485,
    "country_iso": "US",
    "state_id": 474,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 485,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 474,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 485
    }
  },
  "line_items": [
    {
      "id": 418,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 1151,
      "vendor_id": 3391,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 1151,
        "name": "Product #11 - 7156",
        "sku": "SKU-14",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-11-7156",
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
        "product_id": 693,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
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
      "id": 341,
      "tracking": null,
      "tracking_url": null,
      "number": "H41841572857",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R374648671",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 325,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 323,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 325,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 323,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 323,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 228,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 433,
              "name": "ShippingCategory #9"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 1151,
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
PATCH /api/checkouts/R507754780
Accept: application/json
X-Spree-Order-Token: JbVBkGHRvfco2L6wa_IugA
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=398&order[payment_attributes][][source_attributes][wallet_payment_source_id]=31
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
ETag: W/&quot;ee6a45bb134a61596bfad1462476171a&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: c67b4a7d-a80d-4eda-b604-7a624114d543
X-Runtime: 0.089199
Content-Length: 4254
200 OK
```


```json
{
  "id": 491,
  "number": "R507754780",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 565,
  "created_at": "2019-08-05T15:21:14.627Z",
  "updated_at": "2019-08-05T15:21:14.794Z",
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
  "token": "JbVBkGHRvfco2L6wa_IugA",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 398,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
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
    "country_id": 486,
    "country_iso": "US",
    "state_id": 475,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 486,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 475,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 486
    }
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
    "country_id": 486,
    "country_iso": "US",
    "state_id": 475,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 486,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 475,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 486
    }
  },
  "line_items": [
    {
      "id": 419,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 1153,
      "vendor_id": 3397,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 1153,
        "name": "Product #12 - 2308",
        "sku": "SKU-16",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-12-2308",
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
            "id": 471,
            "name": "Size-5",
            "presentation": "S",
            "option_type_name": "foo-size-5",
            "option_type_id": 471,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 694,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
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
      "id": 343,
      "tracking": null,
      "tracking_url": null,
      "number": "H71075137781",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R507754780",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 327,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 324,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 327,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 324,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 324,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 229,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 434,
              "name": "ShippingCategory #10"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 1153,
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
POST /api/orders/R790470007/line_items
Accept: application/json
X-Spree-Order-Token: BvBsRsSgCUANxhhp_aK6rw
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/:order_number/line_items`

#### Parameters


```json
line_item[variant_id]=1163&line_item[options][vendor_id]=3422
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
ETag: W/&quot;af41a939ae72cdea8d9c3c5daa560216&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 0a791d5d-7276-4343-9fd8-83ffdfb102f4
X-Runtime: 0.069070
Content-Length: 851
201 Created
```


```json
{
  "id": 423,
  "quantity": 1,
  "price": "19.99",
  "variant_id": 1163,
  "vendor_id": 3422,
  "single_display_amount": "$19.99",
  "display_amount": "$19.99",
  "total": "19.99",
  "final_sale": false,
  "backordered": null,
  "promotionable": true,
  "variant": {
    "id": 1163,
    "name": "Product #17 - 383",
    "sku": "SKU-26",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": false,
    "slug": "product-17-383",
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
        "id": 476,
        "name": "Size-10",
        "presentation": "S",
        "option_type_name": "foo-size-10",
        "option_type_id": 476,
        "option_type_presentation": "Size"
      }
    ],
    "images": [

    ],
    "product_id": 699,
    "brand": null,
    "brand_slug": null,
    "brand_description": null
  },
  "vendor_name": "Vendor #62",
  "adjustments": [

  ]
}
```



## Deleting a line item


### Request

#### Endpoint

```plaintext
DELETE /api/orders/R171524011/line_items/421
Accept: application/json
X-Spree-Order-Token: 2E5BeU7qeWry4kj8PQoYpQ
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
X-Request-Id: 47336530-18b7-4189-a228-fd59133bf5b6
X-Runtime: 0.059578
204 No Content
```




## Updating a line item


### Request

#### Endpoint

```plaintext
PUT /api/orders/R161325201/line_items/420
Accept: application/json
X-Spree-Order-Token: bSTEL_RcHgQtkJitJ2h63A
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
ETag: W/&quot;2d157e9bc92c4284a0802f2dd2ff8b77&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 7ea267e2-cb6b-403b-ab18-f782d3840b34
X-Runtime: 0.081555
Content-Length: 848
200 OK
```


```json
{
  "id": 420,
  "quantity": 2,
  "price": "10.0",
  "variant_id": 1155,
  "vendor_id": 3403,
  "single_display_amount": "$10.00",
  "display_amount": "$20.00",
  "total": "20.0",
  "final_sale": false,
  "backordered": null,
  "promotionable": true,
  "variant": {
    "id": 1155,
    "name": "Product #13 - 1129",
    "sku": "SKU-18",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": false,
    "slug": "product-13-1129",
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
        "id": 472,
        "name": "Size-6",
        "presentation": "S",
        "option_type_name": "foo-size-6",
        "option_type_id": 472,
        "option_type_presentation": "Size"
      }
    ],
    "images": [

    ],
    "product_id": 695,
    "brand": null,
    "brand_slug": null,
    "brand_description": null
  },
  "vendor_name": "Vendor #46",
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
ETag: W/&quot;1411fe11cc558e0b91f5d31cac2bf1b6&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 300d050a-1cbf-4e00-a1cf-9b2ec918e72d
X-Runtime: 0.006266
Content-Length: 134
200 OK
```


```json
[
  {
    "id": 745,
    "name": "Kids",
    "navigation_url": "/navigation/kids",
    "parent_id": 744,
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
Authorization: Bearer c7f9c70d487b2a1aa9ac469cf406ce3e46e39facd6e3a83f
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
ETag: W/&quot;d6a75bb2381408d297cb18d4b77f06d3&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: c960d280-1afa-4109-9743-4caf5d2e015e
X-Runtime: 0.020143
Content-Length: 305
200 OK
```


```json
{
  "orders": [
    {
      "number": "R162847289",
      "completed_at": "2019-08-05T15:21:16.210Z",
      "total": "120.0",
      "state": "Complete",
      "shipment_state": "shipped",
      "shipments": [
        {
          "number": "H80125804741",
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
GET /api/orders/R201204606
Accept: application/json
Authorization: Bearer 1e164ad49e174e694c25d20367457d8ff5d19d3e5e7f8861
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
ETag: W/&quot;0ed74a15160ffd53c78c61e4c1667f2d&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 4a2bb4f5-c3b5-4104-9546-382791598b7f
X-Runtime: 0.128177
Content-Length: 9254
200 OK
```


```json
{
  "id": 497,
  "number": "R201204606",
  "item_total": "20.0",
  "total": "120.0",
  "ship_total": "100.0",
  "state": "complete",
  "adjustment_total": "0.0",
  "user_id": 572,
  "created_at": "2019-08-05T15:21:17.013Z",
  "updated_at": "2019-08-05T15:21:17.227Z",
  "completed_at": "2019-08-05T15:21:17.100Z",
  "payment_total": "120.0",
  "shipment_state": "shipped",
  "payment_state": "paid",
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
  "token": "JS735ea_VcI33jgJ2rqUKQ",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 403,
      "name": "Credit Card",
      "partial_name": "gateway",
      "method_type": "gateway"
    },
    {
      "id": 404,
      "name": "Credit Card",
      "partial_name": "gateway",
      "method_type": "gateway"
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
      "id": 428,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 1169,
      "vendor_id": 3439,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 1169,
        "name": "Product #20 - 3942",
        "sku": "SKU-32",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-20-3942",
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
      "vendor_name": "Vendor #77",
      "adjustments": [
        {
          "id": 95,
          "source_type": "Spree::TaxRate",
          "source_id": 17,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 428,
          "amount": "2.0",
          "label": "VAT 5%",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-08-05T15:21:17.203Z",
          "updated_at": "2019-08-05T15:21:17.213Z",
          "display_amount": "$2.00"
        },
        {
          "id": 89,
          "source_type": "Spree::PromotionAction",
          "source_id": 39,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 428,
          "amount": "5.0",
          "label": "foo",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-08-05T15:21:17.162Z",
          "updated_at": "2019-08-05T15:21:17.162Z",
          "display_amount": "$5.00"
        },
        {
          "id": 88,
          "source_type": "Spree::PromotionAction",
          "source_id": 39,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 428,
          "amount": "5.0",
          "label": "foo",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-08-05T15:21:17.156Z",
          "updated_at": "2019-08-05T15:21:17.156Z",
          "display_amount": "$5.00"
        }
      ]
    },
    {
      "id": 429,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 1169,
      "vendor_id": 3439,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 1169,
        "name": "Product #20 - 3942",
        "sku": "SKU-32",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-20-3942",
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
      "vendor_name": "Vendor #77",
      "adjustments": [
        {
          "id": 96,
          "source_type": "Spree::TaxRate",
          "source_id": 18,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 429,
          "amount": "1.5",
          "label": "VAT 5%",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-08-05T15:21:17.225Z",
          "updated_at": "2019-08-05T15:21:17.233Z",
          "display_amount": "$1.50"
        },
        {
          "id": 90,
          "source_type": "Spree::PromotionAction",
          "source_id": 39,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 429,
          "amount": "5.0",
          "label": "bar",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-08-05T15:21:17.168Z",
          "updated_at": "2019-08-05T15:21:17.168Z",
          "display_amount": "$5.00"
        }
      ]
    }
  ],
  "payments": [
    {
      "id": 196,
      "source_type": "Spree::CreditCard",
      "source_id": 169,
      "amount": "120.0",
      "display_amount": "$120.00",
      "payment_method_id": 403,
      "state": "completed",
      "avs_response": null,
      "created_at": "2019-08-05T15:21:17.116Z",
      "updated_at": "2019-08-05T15:21:17.116Z",
      "payment_method": {
        "id": 403,
        "name": "Credit Card"
      },
      "source": {
        "id": 169,
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
      "id": 349,
      "tracking": "U10000",
      "tracking_url": null,
      "number": "H22085781718",
      "cost": "100.0",
      "shipped_at": "2019-08-05T15:21:17.137Z",
      "state": "shipped",
      "order_id": "R201204606",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 333,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 330,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 333,
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
              "id": 237,
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
            "shipped": 1
          }
        },
        {
          "variant_id": 1169,
          "quantity": 1,
          "states": {
            "shipped": 1
          }
        }
      ],
      "adjustments": [
        {
          "id": 92,
          "source_type": "Spree::PromotionAction",
          "source_id": 39,
          "adjustable_type": "Spree::Shipment",
          "adjustable_id": 349,
          "amount": "-10.0",
          "label": "Shipping",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-08-05T15:21:17.180Z",
          "updated_at": "2019-08-05T15:21:17.180Z",
          "display_amount": "-$10.00"
        },
        {
          "id": 91,
          "source_type": "Spree::PromotionAction",
          "source_id": 39,
          "adjustable_type": "Spree::Shipment",
          "adjustable_id": 349,
          "amount": "-9.99",
          "label": "Shipping",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-08-05T15:21:17.174Z",
          "updated_at": "2019-08-05T15:21:17.174Z",
          "display_amount": "-$9.99"
        }
      ],
      "stock_location_address": "NY Warehouse, Washington, AL"
    }
  ],
  "adjustments": [
    {
      "id": 93,
      "source_type": "Spree::Promotion",
      "source_id": 57,
      "adjustable_type": "Spree::Order",
      "adjustable_id": 497,
      "amount": "20.0",
      "label": "adj1",
      "promotion_code_id": null,
      "finalized": false,
      "eligible": true,
      "created_at": "2019-08-05T15:21:17.184Z",
      "updated_at": "2019-08-05T15:21:17.184Z",
      "display_amount": "$20.00"
    },
    {
      "id": 94,
      "source_type": "Spree::Promotion",
      "source_id": 57,
      "adjustable_type": "Spree::Order",
      "adjustable_id": 497,
      "amount": "30.0",
      "label": "adj2",
      "promotion_code_id": null,
      "finalized": false,
      "eligible": true,
      "created_at": "2019-08-05T15:21:17.187Z",
      "updated_at": "2019-08-05T15:21:17.187Z",
      "display_amount": "$30.00"
    }
  ],
  "permissions": {
    "can_update": false
  },
  "credit_cards": [
    {
      "id": 169,
      "month": "12",
      "year": "2020",
      "cc_type": null,
      "last_digits": "1111",
      "name": "Spree Commerce",
      "address": {
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
GET /api/orders/R964404948
Accept: application/json
Authorization: 8e9c3006d7b8d4819732562b783f475ddccee0b265e114f6
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
X-Request-Id: 5ebfa806-a154-49f7-b759-77beb52341bb
X-Runtime: 0.009892
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
user[email]=email1%40example.com
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
X-Request-Id: a369671a-6b62-406e-a043-7d3d179185b9
X-Runtime: 0.021493
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
user[email]=email2%40example.com&user[password]=secret
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
Authorization: Bearer 9ce32c075d7e76c5921bdb00d1424e74893d214437ca2d95
ETag: W/&quot;62ee4ee0dea186bc017f0c3981e281d3&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 6213e3f2-6d9a-4201-b3fc-09aca67046d7
X-Runtime: 0.006663
Content-Length: 551
200 OK
```


```json
{
  "id": 559,
  "email": "email2@example.com",
  "persistence_token": null,
  "perishable_token": null,
  "last_request_at": null,
  "login": "email2@example.com",
  "ship_address_id": null,
  "bill_address_id": null,
  "created_at": "2019-08-05T15:21:08.679Z",
  "updated_at": "2019-08-05T15:21:08.680Z",
  "spree_api_key": "9ce32c075d7e76c5921bdb00d1424e74893d214437ca2d95",
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
X-Request-Id: 47617b73-7c2b-4d9c-b2f8-2935f876023a
X-Runtime: 0.002618
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
Date: Mon, 05 Aug 2019 15:21:08 GMT
Surrogate-Control: max-age=900
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;548d4e38fc9175410af1c5de0918c309&quot;
X-Request-Id: 2c27b57d-206e-41c0-8625-83f7d6ec644f
X-Runtime: 0.100670
Content-Length: 913
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
      "id": 687,
      "name": "Product #5 - 5448",
      "description": "As seen on TV!",
      "available_on": "2018-08-05T15:21:08.254Z",
      "slug": "product-5-5448",
      "meta_description": null,
      "meta_keywords": null,
      "shipping_category_id": 427,
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
        "id": 1141,
        "name": "Product #5 - 5448",
        "sku": "SKU-5",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-5-5448",
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
GET /api/products/product-6-9621
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
Date: Mon, 05 Aug 2019 15:21:08 GMT
Surrogate-Control: max-age=900
Surrogate-Key: product_id=1
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;487220f99935167b1c0076f7fffeffd5&quot;
X-Request-Id: 507f6aac-a312-4b46-bae3-23b5e3950a44
X-Runtime: 0.039062
Content-Length: 831
200 OK
```


```json
{
  "id": 688,
  "name": "Product #6 - 9621",
  "description": "As seen on TV!",
  "available_on": "2018-08-05T15:21:08.436Z",
  "slug": "product-6-9621",
  "meta_description": null,
  "meta_keywords": null,
  "shipping_category_id": 428,
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
    "id": 1142,
    "name": "Product #6 - 9621",
    "sku": "SKU-6",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": true,
    "slug": "product-6-9621",
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
X-Request-Id: 7c0f1468-50c7-4f1c-b561-36a6ed9eb52d
X-Runtime: 0.015176
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
ETag: W/&quot;509f5715df3fbde04f5264a10277364d&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 08042bfe-cc7d-4a15-a0ef-1f59ad53ec44
X-Runtime: 0.315656
Content-Length: 1103
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
      "id": 683,
      "name": "Product #1 - 8489",
      "description": "As seen on TV!",
      "available_on": "2018-08-05T15:21:07.201Z",
      "slug": "product-1-8489",
      "meta_description": null,
      "meta_keywords": null,
      "shipping_category_id": 425,
      "taxon_ids": [
        737
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
        "id": 1137,
        "name": "Product #1 - 8489",
        "sku": "SKU-1",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-1-8489",
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
          "taxon_id": 737,
          "position": 1,
          "taxon": {
            "id": 737,
            "name": "Ruby on Rails",
            "pretty_name": "Ruby on Rails",
            "permalink": "ruby-on-rails",
            "parent_id": null,
            "taxonomy_id": 328
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
GET /api/taxons/products?id=741
Host: example.org
Cookie: 
```

`GET /api/taxons/products`

#### Parameters


```json
id: 741
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
ETag: W/&quot;ab2e11b45ffb08da217b17b88d50bff9&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: ae219b3d-aa7e-4a74-970c-fc69baba85aa
X-Runtime: 0.036424
Content-Length: 1103
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
      "id": 685,
      "name": "Product #3 - 3259",
      "description": "As seen on TV!",
      "available_on": "2018-08-05T15:21:08.015Z",
      "slug": "product-3-3259",
      "meta_description": null,
      "meta_keywords": null,
      "shipping_category_id": 426,
      "taxon_ids": [
        741
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
        "id": 1139,
        "name": "Product #3 - 3259",
        "sku": "SKU-3",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-3-3259",
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
          "taxon_id": 741,
          "position": 1,
          "taxon": {
            "id": 741,
            "name": "Ruby on Rails",
            "pretty_name": "Ruby on Rails",
            "permalink": "ruby-on-rails",
            "parent_id": null,
            "taxonomy_id": 330
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
GET /api/returns/RA145518240
Authorization: Bearer 7e1598e61d2369227e914da956846604c59cbc6615c9e300
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
ETag: W/&quot;1c55eca231fcbefdfff1fd0a43de5b75&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 90f10287-309f-4649-b15f-34bb1bff1eae
X-Runtime: 0.039075
Content-Length: 2754
200 OK
```


```json
{
  "id": 20,
  "number": "RA145518240",
  "state": "authorized",
  "order_id": 504,
  "memo": "Items were broken",
  "created_at": "2019-08-05T15:21:19.870Z",
  "updated_at": "2019-08-05T15:21:19.870Z",
  "reason": {
    "id": 60,
    "name": "Defect #7",
    "active": true,
    "mutable": true,
    "created_at": "2019-08-05T15:21:19.867Z",
    "updated_at": "2019-08-05T15:21:19.867Z"
  },
  "order": {
    "id": 504,
    "number": "R925826519",
    "item_total": "10.0",
    "total": "110.0",
    "state": "complete",
    "adjustment_total": "0.0",
    "user_id": 586,
    "completed_at": "2019-08-05T15:21:19.814Z",
    "bill_address_id": 1047,
    "ship_address_id": 1048,
    "payment_total": "110.0",
    "shipment_state": "shipped",
    "payment_state": "paid",
    "email": "email28@example.com",
    "special_instructions": null,
    "created_at": "2019-08-05T15:21:19.758Z",
    "updated_at": "2019-08-05T15:21:19.855Z",
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
    "guest_token": "dWPaXmwmiFRKWmPvsgiSWg",
    "canceled_at": null,
    "canceler_id": null,
    "store_id": 543,
    "approver_name": null,
    "frontend_viewable": true
  },
  "ship_address": {
    "id": 1048,
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
  "bill_address": {
    "id": 1047,
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
  "return_items": [
    {
      "name": "Product #26 - 2119",
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
        "id": 416,
        "name": "Credit Card"
      },
      "source": {
        "id": 173,
        "month": "12",
        "year": "2020",
        "cc_type": null,
        "last_digits": "1111",
        "name": "Spree Commerce",
        "gateway_customer_profile_id": "BGS-221553",
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
Authorization: Bearer bc7ea9d161736889b89796669488dc0fbd02711a4ba334c0
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
ETag: W/&quot;758eb979360f5009b5e6cc4ebc1b82dd&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: f2c35b06-2fff-49b9-899b-70abaf136887
X-Runtime: 0.015383
Content-Length: 164
200 OK
```


```json
{
  "return_authorizations": [
    {
      "number": "RA788421473",
      "created_at": "2019-08-05T15:21:18.817Z",
      "return_amount": "10.0",
      "order_number": "R060443390",
      "state": "authorized"
    }
  ]
}
```



## returns a 200


### Request

#### Endpoint

```plaintext
GET /api/returns/RA805644468
Authorization: Bearer c0ac54ce6bdedf582399dce09f11999ecfc196fbf9156d63
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
ETag: W/&quot;82dae7b7135ed14b77c769d4e59d36b3&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: d9173a9d-3b54-4723-b24a-12101f6a8891
X-Runtime: 0.058039
Content-Length: 2677
200 OK
```


```json
{
  "id": 18,
  "number": "RA805644468",
  "state": "authorized",
  "order_id": 502,
  "memo": "Items were broken",
  "created_at": "2019-08-05T15:21:19.161Z",
  "updated_at": "2019-08-05T15:21:19.161Z",
  "reason": {
    "id": 56,
    "name": "Defect #3",
    "active": true,
    "mutable": true,
    "created_at": "2019-08-05T15:21:19.158Z",
    "updated_at": "2019-08-05T15:21:19.158Z"
  },
  "order": {
    "id": 502,
    "number": "R494175527",
    "item_total": "10.0",
    "total": "110.0",
    "state": "complete",
    "adjustment_total": "0.0",
    "user_id": 583,
    "completed_at": "2019-08-05T15:21:19.102Z",
    "bill_address_id": 1043,
    "ship_address_id": 1044,
    "payment_total": "110.0",
    "shipment_state": "shipped",
    "payment_state": "paid",
    "email": "email25@example.com",
    "special_instructions": null,
    "created_at": "2019-08-05T15:21:19.055Z",
    "updated_at": "2019-08-05T15:21:19.145Z",
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
    "guest_token": "jX2ewQPmQA3K8ZJsiwkMHg",
    "canceled_at": null,
    "canceler_id": null,
    "store_id": 541,
    "approver_name": null,
    "frontend_viewable": true
  },
  "ship_address": {
    "id": 1044,
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
    "country_id": 497,
    "country_iso": "US",
    "state_id": 486,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 497,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 486,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 497
    }
  },
  "bill_address": {
    "id": 1043,
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
    "country_id": 497,
    "country_iso": "US",
    "state_id": 486,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 497,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 486,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 497
    }
  },
  "return_items": [
    {
      "name": "Product #24 - 4476",
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
        "id": 412,
        "name": "Credit Card"
      },
      "source": {
        "id": 171,
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
GET /api/returns/RA480678545
Authorization: Bearer 0c89c31f98131e9e66b1d4c3a35ada4ea9107dd48c9ef96c
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
X-Request-Id: 11eb79a3-575e-4f89-b4cc-efc0837a8d44
X-Runtime: 0.006394
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
Authorization: Bearer cd45b00ec59c27d3098072ebe0c54a5f6310a65c6b028360
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
ETag: W/&quot;142f5a07b4d28c9edb29013832172e02&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: d2aabf14-5da5-4b01-9a25-cf17514ae443
X-Runtime: 0.032823
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
      "created_at": "2019-08-05T15:21:20.002Z"
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

Get user account details, stored addresses, and stored credit cards

## Gets the user account information


### Request

#### Endpoint

```plaintext
GET /api/users/mine
Authorization: Bearer 9d4473efc17393263662942cf7b5da7c1b6a6311368f7468
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
Authorization: Bearer 9d4473efc17393263662942cf7b5da7c1b6a6311368f7468
ETag: W/&quot;d12ec3411e5a51803b54b31500ac1490&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: b4eb6f2a-94fc-407d-9f38-3407afcc9244
X-Runtime: 0.015499
Content-Length: 125
200 OK
```


```json
{
  "email": "email17@example.com",
  "first_name": null,
  "last_name": null,
  "id": 574,
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
user[email]=email18%40example.com&user[password]=secret
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
Authorization: Bearer 05dc4619b7cc832981381b1a5f1abb15ef380164c7ad4354
ETag: W/&quot;60812bf3fd75eaf163aadf4219753981&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: cc2ce37f-28d0-4697-bc2e-54a8a968f2eb
X-Runtime: 0.004383
Content-Length: 553
200 OK
```


```json
{
  "id": 575,
  "email": "email18@example.com",
  "persistence_token": null,
  "perishable_token": null,
  "last_request_at": null,
  "login": "email18@example.com",
  "ship_address_id": null,
  "bill_address_id": null,
  "created_at": "2019-08-05T15:21:17.461Z",
  "updated_at": "2019-08-05T15:21:17.465Z",
  "spree_api_key": "05dc4619b7cc832981381b1a5f1abb15ef380164c7ad4354",
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
Authorization: Bearer 44282475359e7d41449aff3d0796fcaa2396ce9ffa54a15f
ETag: W/&quot;875426bf0f72a3fe0e7754de99a77aa2&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: a90825a8-faa9-42e8-8203-8f6a2e4d3b90
X-Runtime: 0.015486
Content-Length: 157
201 Created
```


```json
{
  "id": 576,
  "email": "test@example.com",
  "created_at": "2019-08-05T15:21:17.479Z",
  "updated_at": "2019-08-05T15:21:17.481Z",
  "bill_address": null,
  "ship_address": null
}
```



# Variant



## Fetching a variant


### Request

#### Endpoint

```plaintext
GET /api/variants/1183
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
ETag: W/&quot;fc3facfe38467d2ca948c7c4d17cc691&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 6d08159e-56db-48a9-b6fc-441477402371
X-Runtime: 0.087719
Content-Length: 1460
200 OK
```


```json
{
  "id": 1183,
  "name": "Product #27 - 4477",
  "sku": "SKU-46",
  "weight": "0.0",
  "height": null,
  "width": null,
  "depth": null,
  "is_master": false,
  "slug": "product-27-4477",
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
      "id": 486,
      "name": "Size-20",
      "presentation": "S",
      "option_type_name": "foo-size-20",
      "option_type_id": 486,
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
      "attachment_updated_at": "2019-08-05T15:21:20.257Z",
      "attachment_width": 489,
      "attachment_height": 490,
      "alt": null,
      "viewable_type": "Spree::Variant",
      "viewable_id": 1183,
      "mini_url": "/spree/products/2/mini/thinking-cat.jpg?1565018480",
      "small_url": "/spree/products/2/small/thinking-cat.jpg?1565018480",
      "product_url": "/spree/products/2/product/thinking-cat.jpg?1565018480",
      "large_url": "/spree/products/2/large/thinking-cat.jpg?1565018480"
    }
  ],
  "variant_properties": [

  ],
  "stock_items": [

  ],
  "prices": [
    {
      "id": 2283,
      "vendor_id": 3488,
      "price": "10.0",
      "original_price": "10.0",
      "discount_percent": 0.0,
      "total_on_hand": 0,
      "country_iso": null,
      "final_sale": false,
      "on_sale": false
    },
    {
      "id": 2284,
      "vendor_id": 3489,
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
Authorization: Bearer a74963e6080e6194a136ed0596694b05c00bebf4a04cd8d6
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
ETag: W/&quot;5537376ea0543f6cfa9a715a64919a56&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: e8cd5dfb-8e4d-4a58-8f85-1434ba5f5f04
X-Runtime: 0.011597
Content-Length: 199
200 OK
```


```json
[
  {
    "id": 34,
    "user_id": 579,
    "payment_source_type": "SolidusPaypalBraintree::Source",
    "payment_source_id": 59,
    "default": false,
    "created_at": "2019-08-05T15:21:17.591Z",
    "updated_at": "2019-08-05T15:21:17.591Z"
  }
]
```



## Remove the payment from the user wallet


### Request

#### Endpoint

```plaintext
DELETE /api/wallet_payment_sources/33
Accept: application/json
Authorization: Bearer b0ffa5665440b1d443b3108656baed8ea499456772c65171
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
X-Request-Id: a393ae50-942b-48ba-b4a2-2e25888f48d3
X-Runtime: 0.010780
204 No Content
```




## Set a wallet payment source as the default user payment method


### Request

#### Endpoint

```plaintext
POST /api/wallet_payment_sources/32/default
Accept: application/json
Authorization: Bearer 8a878efab2bd6b8f05879777651db9b16a14f37e10a200f9
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
X-Request-Id: ce3eae37-0227-485c-9ee4-ab52a21d29ad
X-Runtime: 0.030529
204 No Content
```




