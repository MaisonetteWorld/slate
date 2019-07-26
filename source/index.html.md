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
PUT /api/orders/R059135265/addresses/713
Accept: application/json
X-Spree-Order-Token: 4Mi5Khmh3woqvYxmlBoGrA
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
ETag: W/&quot;ae300f14a67763f7ec1de61f1d203822&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 541f3f40-962b-434a-ae93-1a017b24b459
X-Runtime: 0.224825
Content-Length: 513
200 OK
```


```json
{
  "id": 714,
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
  "country_id": 400,
  "country_iso": "US",
  "state_id": 389,
  "state_name": null,
  "state_text": "AL",
  "country": {
    "id": 400,
    "iso_name": "UNITED STATES",
    "iso": "US",
    "iso3": "USA",
    "name": "United States",
    "numcode": 840
  },
  "state": {
    "id": 389,
    "name": "Alabama",
    "abbr": "AL",
    "country_id": 400
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
X-Spree-Order-Token: ECW08vKgaSBRV-aewYI6GQ
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/braintree/transactions`

#### Parameters


```json
order_id=R997539055&payment_method_id=304&options[restart_checkout]=true&transaction[email]=maryellen.oga%40mckenziemcglynn.com&transaction[nonce]=fake-paypal-billing-agreement-nonce&transaction[phone]=555-555-0199&transaction[address_attributes][first_name]=John&transaction[address_attributes][last_name]=Stamm&transaction[address_attributes][address_line_1]=A+Different+Road&transaction[address_attributes][city]=Herndon&transaction[address_attributes][state_code]=AL&transaction[address_attributes][zip]=10005&transaction[address_attributes][country_code]=US&transaction[payment_type]=PayPalAccount
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
ETag: W/&quot;3cac2a66cb84f430a99fc4b3e019d94a&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: ce45a0cd-0462-4829-ba13-c466ad5b9238
X-Runtime: 0.194212
Content-Length: 4575
200 OK
```


```json
{
  "id": 340,
  "number": "R997539055",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2019-07-26T16:37:26.652Z",
  "updated_at": "2019-07-26T16:37:26.853Z",
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
  "token": "ECW08vKgaSBRV-aewYI6GQ",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 304,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 720,
    "firstname": "John",
    "lastname": "Stamm",
    "full_name": "John Stamm",
    "address1": "A Different Road",
    "address2": null,
    "city": "Herndon",
    "zipcode": "10005",
    "phone": "555-555-0199",
    "company": null,
    "alternative_phone": null,
    "country_id": 402,
    "country_iso": "US",
    "state_id": 391,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 402,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 391,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 402
    }
  },
  "ship_address": {
    "id": 720,
    "firstname": "John",
    "lastname": "Stamm",
    "full_name": "John Stamm",
    "address1": "A Different Road",
    "address2": null,
    "city": "Herndon",
    "zipcode": "10005",
    "phone": "555-555-0199",
    "company": null,
    "alternative_phone": null,
    "country_id": 402,
    "country_iso": "US",
    "state_id": 391,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 402,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 391,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 402
    }
  },
  "line_items": [
    {
      "id": 343,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 946,
      "vendor_id": 2878,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "variant": {
        "id": 946,
        "name": "Product #2 - 2951",
        "sku": "SKU-3",
        "price": "10.0",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-2-2951",
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
            "id": 418,
            "name": "Size-2",
            "presentation": "S",
            "option_type_name": "foo-size-2",
            "option_type_id": 418,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 542,
        "brand": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #7",
      "adjustments": [

      ]
    }
  ],
  "payments": [
    {
      "id": 156,
      "source_type": "SolidusPaypalBraintree::Source",
      "source_id": 45,
      "amount": "110.0",
      "display_amount": "$110.00",
      "payment_method_id": 304,
      "state": "checkout",
      "avs_response": null,
      "created_at": "2019-07-26T16:37:26.738Z",
      "updated_at": "2019-07-26T16:37:26.738Z",
      "payment_method": {
        "id": 304,
        "name": "Braintree"
      },
      "source": {
        "id": 45,
        "payment_type": "PayPalAccount",
        "token": "79gcvv",
        "created_at": "2019-07-26T16:37:26.737Z"
      }
    }
  ],
  "shipments": [
    {
      "id": 278,
      "tracking": null,
      "tracking_url": null,
      "number": "H48047755367",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R997539055",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 279,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 253,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 279,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 253,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 253,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 194,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 349,
              "name": "ShippingCategory #2"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 946,
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
X-Spree-Order-Token: ckW0maieZvKUi0SVaa3NRQ
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/braintree/transactions`

#### Parameters


```json
order_id=R101827494&payment_method_id=303&options[restart_checkout]=true&transaction[email]=maryellen.oga%40mckenziemcglynn.com&transaction[nonce]=fake-apple-pay-visa-nonce&transaction[phone]=555-555-0199&transaction[address_attributes][first_name]=John&transaction[address_attributes][last_name]=Stamm&transaction[address_attributes][address_line_1]=A+Different+Road&transaction[address_attributes][city]=Herndon&transaction[address_attributes][state_code]=AL&transaction[address_attributes][zip]=10003&transaction[address_attributes][country_code]=US&transaction[payment_type]=ApplePayCard
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
ETag: W/&quot;90692f691b2ece52fc7e22c3460c072b&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 52adcbec-dba2-46ab-9036-bc75587472ad
X-Runtime: 0.444120
Content-Length: 4574
200 OK
```


```json
{
  "id": 339,
  "number": "R101827494",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2019-07-26T16:37:25.766Z",
  "updated_at": "2019-07-26T16:37:26.336Z",
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
  "token": "ckW0maieZvKUi0SVaa3NRQ",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 303,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 717,
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
    "country_id": 401,
    "country_iso": "US",
    "state_id": 390,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 401,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 390,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 401
    }
  },
  "ship_address": {
    "id": 717,
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
    "country_id": 401,
    "country_iso": "US",
    "state_id": 390,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 401,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 390,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 401
    }
  },
  "line_items": [
    {
      "id": 342,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 944,
      "vendor_id": 2872,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "variant": {
        "id": 944,
        "name": "Product #1 - 5749",
        "sku": "SKU-1",
        "price": "10.0",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-1-5749",
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
            "id": 417,
            "name": "Size-1",
            "presentation": "S",
            "option_type_name": "foo-size-1",
            "option_type_id": 417,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 541,
        "brand": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #2",
      "adjustments": [

      ]
    }
  ],
  "payments": [
    {
      "id": 155,
      "source_type": "SolidusPaypalBraintree::Source",
      "source_id": 44,
      "amount": "110.0",
      "display_amount": "$110.00",
      "payment_method_id": 303,
      "state": "checkout",
      "avs_response": null,
      "created_at": "2019-07-26T16:37:26.069Z",
      "updated_at": "2019-07-26T16:37:26.069Z",
      "payment_method": {
        "id": 303,
        "name": "Braintree"
      },
      "source": {
        "id": 44,
        "payment_type": "ApplePayCard",
        "token": "6b64ck",
        "created_at": "2019-07-26T16:37:26.068Z"
      }
    }
  ],
  "shipments": [
    {
      "id": 276,
      "tracking": null,
      "tracking_url": null,
      "number": "H87284014528",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R101827494",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 277,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 252,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 277,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 252,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 252,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 193,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 348,
              "name": "ShippingCategory #1"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 944,
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
PUT /api/checkouts/R260417804/complete
Accept: application/json
X-Spree-Order-Token: KhaUmiVY_K7sm6_53rQ1OQ
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
ETag: W/&quot;f55c273d6d55cc84fa7963a26fbe1d2a&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: a106953a-16a6-4ffe-97ed-e511920eaae5
X-Runtime: 1.708622
Content-Length: 4711
200 OK
```


```json
{
  "id": 344,
  "number": "R260417804",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "complete",
  "adjustment_total": "0.0",
  "user_id": 408,
  "created_at": "2019-07-26T16:37:30.402Z",
  "updated_at": "2019-07-26T16:37:33.528Z",
  "completed_at": "2019-07-26T16:37:33.528Z",
  "payment_total": "110.0",
  "shipment_state": "ready",
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
  "token": "KhaUmiVY_K7sm6_53rQ1OQ",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 311,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    },
    {
      "id": 312,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 727,
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
    "country_id": 412,
    "country_iso": "US",
    "state_id": 401,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 412,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 401,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 412
    }
  },
  "ship_address": {
    "id": 728,
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
    "country_id": 412,
    "country_iso": "US",
    "state_id": 401,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 412,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 401,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 412
    }
  },
  "line_items": [
    {
      "id": 350,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 963,
      "vendor_id": 2934,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "variant": {
        "id": 963,
        "name": "Product #14 - 1437",
        "sku": "SKU-20",
        "price": "10.0",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-14-1437",
        "description": "As seen on TV!",
        "track_inventory": true,
        "display_price": "$10.00",
        "options_text": "Size: S",
        "in_stock": true,
        "is_backorderable": true,
        "total_on_hand": 9,
        "is_destroyed": false,
        "option_values": [
          {
            "id": 423,
            "name": "Size-7",
            "presentation": "S",
            "option_type_name": "foo-size-7",
            "option_type_id": 423,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 554,
        "brand": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #53",
      "adjustments": [

      ]
    }
  ],
  "payments": [
    {
      "id": 160,
      "source_type": "SolidusPaypalBraintree::Source",
      "source_id": 46,
      "amount": "110.0",
      "display_amount": "$110.00",
      "payment_method_id": 311,
      "state": "completed",
      "avs_response": "M",
      "created_at": "2019-07-26T16:37:30.476Z",
      "updated_at": "2019-07-26T16:37:33.376Z",
      "payment_method": {
        "id": 311,
        "name": "Braintree"
      },
      "source": {
        "id": 46,
        "payment_type": "CreditCard",
        "token": "j9fcjq",
        "created_at": "2019-07-26T16:37:30.475Z"
      }
    }
  ],
  "shipments": [
    {
      "id": 282,
      "tracking": "U10000",
      "tracking_url": null,
      "number": "H73631458553",
      "cost": "100.0",
      "shipped_at": null,
      "state": "ready",
      "order_id": "R260417804",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 283,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 257,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 283,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 257,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 257,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 202,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 359,
              "name": "ShippingCategory #12"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 963,
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
PATCH /api/checkouts/R228807561
Accept: application/json
X-Spree-Order-Token: r5HeXB8GiIYD65ppgqjeIQ
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=313&order[payment_attributes][][source_attributes][nonce]=fake-apple-pay-visa-nonce&order[payment_attributes][][source_attributes][payment_type]=ApplePayCard
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
ETag: W/&quot;51b14eade65bf54114324d0abf06ccfc&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 9b2f6460-70af-423f-8440-3bf6611fd587
X-Runtime: 0.101996
Content-Length: 4173
200 OK
```


```json
{
  "id": 345,
  "number": "R228807561",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 409,
  "created_at": "2019-07-26T16:37:33.819Z",
  "updated_at": "2019-07-26T16:37:34.067Z",
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
  "token": "r5HeXB8GiIYD65ppgqjeIQ",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 313,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 729,
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
    "country_id": 413,
    "country_iso": "US",
    "state_id": 402,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 413,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 402,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 413
    }
  },
  "ship_address": {
    "id": 730,
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
    "country_id": 413,
    "country_iso": "US",
    "state_id": 402,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 413,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 402,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 413
    }
  },
  "line_items": [
    {
      "id": 351,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 965,
      "vendor_id": 2940,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "variant": {
        "id": 965,
        "name": "Product #15 - 7306",
        "sku": "SKU-22",
        "price": "10.0",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-15-7306",
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
            "id": 424,
            "name": "Size-8",
            "presentation": "S",
            "option_type_name": "foo-size-8",
            "option_type_id": 424,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 555,
        "brand": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #58",
      "adjustments": [

      ]
    }
  ],
  "payments": [

  ],
  "shipments": [
    {
      "id": 284,
      "tracking": null,
      "tracking_url": null,
      "number": "H03761773520",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R228807561",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 285,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 258,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 285,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 258,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 258,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 203,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 360,
              "name": "ShippingCategory #13"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 965,
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
PATCH /api/checkouts/R507909705
Accept: application/json
X-Spree-Order-Token: vNxMYn5LjukXnGYU-MBeLg
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=315&order[payment_attributes][][source_attributes][nonce]=fake-paypal-billing-agreement-nonce&order[payment_attributes][][source_attributes][payment_type]=PayPalAccount
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
ETag: W/&quot;137e4e3d629a6b11e4d4a9963cc1e495&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 15b1553f-0e34-4b0b-91fd-2d7c3fd04ec0
X-Runtime: 0.089109
Content-Length: 4173
200 OK
```


```json
{
  "id": 347,
  "number": "R507909705",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 411,
  "created_at": "2019-07-26T16:37:34.928Z",
  "updated_at": "2019-07-26T16:37:35.155Z",
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
  "token": "vNxMYn5LjukXnGYU-MBeLg",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 315,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 733,
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
    "country_id": 415,
    "country_iso": "US",
    "state_id": 404,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 415,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 404,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 415
    }
  },
  "ship_address": {
    "id": 734,
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
    "country_id": 415,
    "country_iso": "US",
    "state_id": 404,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 415,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 404,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 415
    }
  },
  "line_items": [
    {
      "id": 353,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 969,
      "vendor_id": 2952,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "variant": {
        "id": 969,
        "name": "Product #17 - 570",
        "sku": "SKU-26",
        "price": "10.0",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-17-570",
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
            "id": 426,
            "name": "Size-10",
            "presentation": "S",
            "option_type_name": "foo-size-10",
            "option_type_id": 426,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 557,
        "brand": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #68",
      "adjustments": [

      ]
    }
  ],
  "payments": [

  ],
  "shipments": [
    {
      "id": 288,
      "tracking": null,
      "tracking_url": null,
      "number": "H53335225087",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R507909705",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 289,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 260,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 289,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 260,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 260,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 205,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 362,
              "name": "ShippingCategory #15"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 969,
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
PATCH /api/checkouts/R954274789
Accept: application/json
X-Spree-Order-Token: MZLLT9qMc9cnKhp0sOyxYA
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=314&order[payment_attributes][][source_attributes][nonce]=fake-valid-visa-nonce&order[payment_attributes][][source_attributes][payment_type]=CreditCard
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
ETag: W/&quot;ee7374572081c32e613dc71e6dfbea5a&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: c51f7f36-3713-4d4f-b40a-e0de250c9b48
X-Runtime: 0.101705
Content-Length: 4173
200 OK
```


```json
{
  "id": 346,
  "number": "R954274789",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 410,
  "created_at": "2019-07-26T16:37:34.361Z",
  "updated_at": "2019-07-26T16:37:34.649Z",
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
  "token": "MZLLT9qMc9cnKhp0sOyxYA",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 314,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 731,
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
    "country_id": 414,
    "country_iso": "US",
    "state_id": 403,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 414,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 403,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 414
    }
  },
  "ship_address": {
    "id": 732,
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
    "country_id": 414,
    "country_iso": "US",
    "state_id": 403,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 414,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 403,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 414
    }
  },
  "line_items": [
    {
      "id": 352,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 967,
      "vendor_id": 2946,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "variant": {
        "id": 967,
        "name": "Product #16 - 7284",
        "sku": "SKU-24",
        "price": "10.0",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-16-7284",
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
            "id": 425,
            "name": "Size-9",
            "presentation": "S",
            "option_type_name": "foo-size-9",
            "option_type_id": 425,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 556,
        "brand": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #63",
      "adjustments": [

      ]
    }
  ],
  "payments": [

  ],
  "shipments": [
    {
      "id": 286,
      "tracking": null,
      "tracking_url": null,
      "number": "H28847111638",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R954274789",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 287,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 259,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 287,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 259,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 259,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 204,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 361,
              "name": "ShippingCategory #14"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 967,
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
PATCH /api/checkouts/R064523042
Accept: application/json
X-Spree-Order-Token: -3PFb0_qQ8kF73QORYdWqQ
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=316&order[payment_attributes][][source_attributes][wallet_payment_source_id]=31
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
ETag: W/&quot;1a16f001e6ad7e0ad9a37b5a83feb6b6&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 991708be-978e-419e-acd1-48c0302edd48
X-Runtime: 0.089846
Content-Length: 4175
200 OK
```


```json
{
  "id": 348,
  "number": "R064523042",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 412,
  "created_at": "2019-07-26T16:37:35.424Z",
  "updated_at": "2019-07-26T16:37:35.646Z",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
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
  "token": "-3PFb0_qQ8kF73QORYdWqQ",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 316,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 735,
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
    "country_id": 416,
    "country_iso": "US",
    "state_id": 405,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 416,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 405,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 416
    }
  },
  "ship_address": {
    "id": 736,
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
    "country_id": 416,
    "country_iso": "US",
    "state_id": 405,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 416,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 405,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 416
    }
  },
  "line_items": [
    {
      "id": 354,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 971,
      "vendor_id": 2958,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "variant": {
        "id": 971,
        "name": "Product #18 - 8822",
        "sku": "SKU-28",
        "price": "10.0",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-18-8822",
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
            "id": 427,
            "name": "Size-11",
            "presentation": "S",
            "option_type_name": "foo-size-11",
            "option_type_id": 427,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 558,
        "brand": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #73",
      "adjustments": [

      ]
    }
  ],
  "payments": [

  ],
  "shipments": [
    {
      "id": 290,
      "tracking": null,
      "tracking_url": null,
      "number": "H67181608572",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R064523042",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 291,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 261,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 291,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 261,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 261,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 206,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 363,
              "name": "ShippingCategory #16"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 971,
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
POST /api/orders/R419511353/line_items
Accept: application/json
X-Spree-Order-Token: G03AwS9RJ3NxvJb9ayqYgg
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/:order_number/line_items`

#### Parameters


```json
line_item[variant_id]=989&line_item[options][vendor_id]=3011
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
ETag: W/&quot;f4c1b71289137e4d2ce91ef2e1e4c7ac&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: ce8cbb50-66b9-4302-a428-cd4e8a9aaaa9
X-Runtime: 0.077904
Content-Length: 773
201 Created
```


```json
{
  "id": 362,
  "quantity": 1,
  "price": "19.99",
  "variant_id": 989,
  "vendor_id": 3011,
  "single_display_amount": "$19.99",
  "display_amount": "$19.99",
  "total": "19.99",
  "variant": {
    "id": 989,
    "name": "Product #27 - 266",
    "sku": "SKU-46",
    "price": "19.99",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": false,
    "slug": "product-27-266",
    "description": "As seen on TV!",
    "track_inventory": true,
    "display_price": "$19.99",
    "options_text": "Size: S",
    "in_stock": false,
    "is_backorderable": true,
    "total_on_hand": 0,
    "is_destroyed": false,
    "option_values": [
      {
        "id": 436,
        "name": "Size-20",
        "presentation": "S",
        "option_type_name": "foo-size-20",
        "option_type_id": 436,
        "option_type_presentation": "Size"
      }
    ],
    "images": [

    ],
    "product_id": 567,
    "brand": null,
    "brand_description": null
  },
  "vendor_name": "Vendor #118",
  "adjustments": [

  ]
}
```



## Deleting a line item


### Request

#### Endpoint

```plaintext
DELETE /api/orders/R334108172/line_items/360
Accept: application/json
X-Spree-Order-Token: LFS9c1dt2-saZTlUsZX-iw
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
X-Request-Id: 8c1328cf-ccaf-461a-b5a8-4a058d090708
X-Runtime: 0.052288
204 No Content
```




## Updating a line item


### Request

#### Endpoint

```plaintext
PUT /api/orders/R104514765/line_items/359
Accept: application/json
X-Spree-Order-Token: rTCBYCzI7_domashZuc25w
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
ETag: W/&quot;e5d1935b2d97a60bba796fd212bac47c&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 82d00ae1-dfb6-4052-bfdb-de0c3a0124ce
X-Runtime: 0.085461
Content-Length: 772
200 OK
```


```json
{
  "id": 359,
  "quantity": 2,
  "price": "10.0",
  "variant_id": 981,
  "vendor_id": 2992,
  "single_display_amount": "$10.00",
  "display_amount": "$20.00",
  "total": "20.0",
  "variant": {
    "id": 981,
    "name": "Product #23 - 9056",
    "sku": "SKU-38",
    "price": "10.0",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": false,
    "slug": "product-23-9056",
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
        "id": 432,
        "name": "Size-16",
        "presentation": "S",
        "option_type_name": "foo-size-16",
        "option_type_id": 432,
        "option_type_presentation": "Size"
      }
    ],
    "images": [

    ],
    "product_id": 563,
    "brand": null,
    "brand_description": null
  },
  "vendor_name": "Vendor #102",
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
ETag: W/&quot;a8385ad5ad62d506d2b6bae2659295ee&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 7e28f5d7-74e8-4516-9470-b9df6d441349
X-Runtime: 0.007936
Content-Length: 134
200 OK
```


```json
[
  {
    "id": 633,
    "name": "Kids",
    "navigation_url": "/navigation/kids",
    "parent_id": 632,
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
X-Spree-Token: 53e883f55c59aa066833361d41780db8ffc2e1df9a154870
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
ETag: W/&quot;7e3305964d22157b8354ab393e4e7984&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 2e1ecf8c-a416-40d2-89bd-d6f6c8a7f1bc
X-Runtime: 0.018464
Content-Length: 305
200 OK
```


```json
{
  "orders": [
    {
      "number": "R270099463",
      "completed_at": "2019-07-26T16:37:28.328Z",
      "total": "120.0",
      "state": "Complete",
      "shipment_state": "shipped",
      "shipments": [
        {
          "number": "H23748304865",
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
GET /api/orders/R799215082
Accept: application/json
X-Spree-Token: c543784dd1d50957c65dd4637cac55e98415e13d8c85df45
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
ETag: W/&quot;090017a8b7b708568b8ac73eea322af5&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 6873634e-092d-4ba3-bc21-2b96baaaf3ed
X-Runtime: 0.125530
Content-Length: 9079
200 OK
```


```json
{
  "id": 342,
  "number": "R799215082",
  "item_total": "20.0",
  "total": "120.0",
  "ship_total": "100.0",
  "state": "complete",
  "adjustment_total": "0.0",
  "user_id": 401,
  "created_at": "2019-07-26T16:37:27.727Z",
  "updated_at": "2019-07-26T16:37:27.913Z",
  "completed_at": "2019-07-26T16:37:27.788Z",
  "payment_total": "120.0",
  "shipment_state": "shipped",
  "payment_state": "paid",
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
  "token": "rId4JF8TB3UQISNQ3yOybg",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 307,
      "name": "Credit Card",
      "partial_name": "gateway",
      "method_type": "gateway"
    },
    {
      "id": 308,
      "name": "Credit Card",
      "partial_name": "gateway",
      "method_type": "gateway"
    }
  ],
  "bill_address": {
    "id": 723,
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
    "country_id": 404,
    "country_iso": "US",
    "state_id": 393,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 404,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 393,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 404
    }
  },
  "ship_address": {
    "id": 724,
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
    "country_id": 404,
    "country_iso": "US",
    "state_id": 393,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 404,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 393,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 404
    }
  },
  "line_items": [
    {
      "id": 346,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 950,
      "vendor_id": 2890,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "variant": {
        "id": 950,
        "name": "Product #4 - 4304",
        "sku": "SKU-7",
        "price": "10.0",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-4-4304",
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
            "id": 420,
            "name": "Size-4",
            "presentation": "S",
            "option_type_name": "foo-size-4",
            "option_type_id": 420,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 544,
        "brand": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #17",
      "adjustments": [
        {
          "id": 95,
          "source_type": "Spree::TaxRate",
          "source_id": 17,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 346,
          "amount": "2.0",
          "label": "VAT 5%",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-07-26T16:37:27.889Z",
          "updated_at": "2019-07-26T16:37:27.899Z",
          "display_amount": "$2.00"
        },
        {
          "id": 89,
          "source_type": "Spree::PromotionAction",
          "source_id": 39,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 346,
          "amount": "5.0",
          "label": "foo",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-07-26T16:37:27.844Z",
          "updated_at": "2019-07-26T16:37:27.844Z",
          "display_amount": "$5.00"
        },
        {
          "id": 88,
          "source_type": "Spree::PromotionAction",
          "source_id": 39,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 346,
          "amount": "5.0",
          "label": "foo",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-07-26T16:37:27.838Z",
          "updated_at": "2019-07-26T16:37:27.838Z",
          "display_amount": "$5.00"
        }
      ]
    },
    {
      "id": 347,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 950,
      "vendor_id": 2890,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "variant": {
        "id": 950,
        "name": "Product #4 - 4304",
        "sku": "SKU-7",
        "price": "10.0",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-4-4304",
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
            "id": 420,
            "name": "Size-4",
            "presentation": "S",
            "option_type_name": "foo-size-4",
            "option_type_id": 420,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 544,
        "brand": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #17",
      "adjustments": [
        {
          "id": 96,
          "source_type": "Spree::TaxRate",
          "source_id": 18,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 347,
          "amount": "1.5",
          "label": "VAT 5%",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-07-26T16:37:27.911Z",
          "updated_at": "2019-07-26T16:37:27.920Z",
          "display_amount": "$1.50"
        },
        {
          "id": 90,
          "source_type": "Spree::PromotionAction",
          "source_id": 39,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 347,
          "amount": "5.0",
          "label": "bar",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-07-26T16:37:27.851Z",
          "updated_at": "2019-07-26T16:37:27.851Z",
          "display_amount": "$5.00"
        }
      ]
    }
  ],
  "payments": [
    {
      "id": 158,
      "source_type": "Spree::CreditCard",
      "source_id": 127,
      "amount": "120.0",
      "display_amount": "$120.00",
      "payment_method_id": 307,
      "state": "completed",
      "avs_response": null,
      "created_at": "2019-07-26T16:37:27.800Z",
      "updated_at": "2019-07-26T16:37:27.800Z",
      "payment_method": {
        "id": 307,
        "name": "Credit Card"
      },
      "source": {
        "id": 127,
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
      "id": 280,
      "tracking": "U10000",
      "tracking_url": null,
      "number": "H58825340258",
      "cost": "100.0",
      "shipped_at": "2019-07-26T16:37:27.818Z",
      "state": "shipped",
      "order_id": "R799215082",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 281,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 255,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 281,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 255,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 255,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 198,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 351,
              "name": "ShippingCategory #4"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 950,
          "quantity": 1,
          "states": {
            "shipped": 1
          }
        },
        {
          "variant_id": 950,
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
          "adjustable_id": 280,
          "amount": "-10.0",
          "label": "Shipping",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-07-26T16:37:27.865Z",
          "updated_at": "2019-07-26T16:37:27.865Z",
          "display_amount": "-$10.00"
        },
        {
          "id": 91,
          "source_type": "Spree::PromotionAction",
          "source_id": 39,
          "adjustable_type": "Spree::Shipment",
          "adjustable_id": 280,
          "amount": "-9.99",
          "label": "Shipping",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-07-26T16:37:27.858Z",
          "updated_at": "2019-07-26T16:37:27.858Z",
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
      "source_id": 62,
      "adjustable_type": "Spree::Order",
      "adjustable_id": 342,
      "amount": "20.0",
      "label": "adj1",
      "promotion_code_id": null,
      "finalized": false,
      "eligible": true,
      "created_at": "2019-07-26T16:37:27.869Z",
      "updated_at": "2019-07-26T16:37:27.869Z",
      "display_amount": "$20.00"
    },
    {
      "id": 94,
      "source_type": "Spree::Promotion",
      "source_id": 62,
      "adjustable_type": "Spree::Order",
      "adjustable_id": 342,
      "amount": "30.0",
      "label": "adj2",
      "promotion_code_id": null,
      "finalized": false,
      "eligible": true,
      "created_at": "2019-07-26T16:37:27.872Z",
      "updated_at": "2019-07-26T16:37:27.872Z",
      "display_amount": "$30.00"
    }
  ],
  "permissions": {
    "can_update": false
  },
  "credit_cards": [
    {
      "id": 127,
      "month": "12",
      "year": "2020",
      "cc_type": null,
      "last_digits": "1111",
      "name": "Spree Commerce",
      "address": {
        "id": 723,
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
        "country_id": 404,
        "country_iso": "US",
        "state_id": 393,
        "state_name": null,
        "state_text": "AL",
        "country": {
          "id": 404,
          "iso_name": "UNITED STATES",
          "iso": "US",
          "iso3": "USA",
          "name": "United States",
          "numcode": 840
        },
        "state": {
          "id": 393,
          "name": "Alabama",
          "abbr": "AL",
          "country_id": 404
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
GET /api/orders/R085089841
Accept: application/json
X-Spree-Token: 4c216103bce35dcd51c344132a0e07db7cc5b9e0a1cf107a
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
X-Request-Id: 9dfff9cc-6a49-4f75-85b9-e2e6cda1b8e8
X-Runtime: 0.029274
Content-Length: 58
401 Unauthorized
```


```json
{
  "error": "You are not authorized to perform that action."
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
Date: Fri, 26 Jul 2019 16:37:29 GMT
Surrogate-Control: max-age=900
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;094fed611cc591f9719677dd9f276806&quot;
X-Request-Id: 584628d8-a2fc-48f5-baec-f670b0a65467
X-Runtime: 0.042731
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
      "id": 552,
      "name": "Product #12 - 1716",
      "description": "As seen on TV!",
      "price": "19.99",
      "display_price": "$19.99",
      "available_on": "2018-07-26T16:37:29.425Z",
      "slug": "product-12-1716",
      "meta_description": null,
      "meta_keywords": null,
      "shipping_category_id": 357,
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
        "id": 959,
        "name": "Product #12 - 1716",
        "sku": "SKU-17",
        "price": "19.99",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-12-1716",
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
GET /api/products/product-6-5914
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
Date: Fri, 26 Jul 2019 16:37:28 GMT
Surrogate-Control: max-age=900
Surrogate-Key: product_id=1
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;17f48241f4ef4930d388cdd99935cf1a&quot;
X-Request-Id: 4d644ba1-8e8c-4e5b-8d92-7ec1c033f11c
X-Runtime: 0.087387
Content-Length: 829
200 OK
```


```json
{
  "id": 546,
  "name": "Product #6 - 5914",
  "description": "As seen on TV!",
  "price": "19.99",
  "display_price": "$19.99",
  "available_on": "2018-07-26T16:37:28.508Z",
  "slug": "product-6-5914",
  "meta_description": null,
  "meta_keywords": null,
  "shipping_category_id": 353,
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
    "id": 953,
    "name": "Product #6 - 5914",
    "sku": "SKU-11",
    "price": "19.99",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": true,
    "slug": "product-6-5914",
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
X-Request-Id: 14435f47-ea34-4707-bdba-12b6d1d8efeb
X-Runtime: 0.018498
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
GET /api/taxons/products?id=625
Host: example.org
Cookie: 
```

`GET /api/taxons/products`

#### Parameters


```json
id: 625
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
ETag: W/&quot;f272c5acff34e4b46e31ee24c57d09ea&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 34dfbbdb-cf87-42b7-bb72-f6d4c122e8d4
X-Runtime: 0.056554
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
      "id": 548,
      "name": "Product #8 - 7027",
      "description": "As seen on TV!",
      "price": "19.99",
      "display_price": "$19.99",
      "available_on": "2018-07-26T16:37:28.834Z",
      "slug": "product-8-7027",
      "meta_description": null,
      "meta_keywords": null,
      "shipping_category_id": 355,
      "taxon_ids": [
        625
      ],
      "total_on_hand": 0,
      "meta_title": null,
      "trends": [

      ],
      "brand": "Ruby on Rails",
      "brand_description": null,
      "has_variants": false,
      "master": {
        "id": 955,
        "name": "Product #8 - 7027",
        "sku": "SKU-13",
        "price": "19.99",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-8-7027",
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
          "taxon_id": 625,
          "position": 1,
          "taxon": {
            "id": 625,
            "name": "Ruby on Rails",
            "pretty_name": "Ruby on Rails",
            "permalink": "ruby-on-rails",
            "parent_id": null,
            "taxonomy_id": 212
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
ETag: W/&quot;36ab3ab9d948dc7d9a3c48a95959cf9a&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 0e04da2a-fa4f-4b6e-8353-61223c7a8080
X-Runtime: 0.041268
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
      "id": 550,
      "name": "Product #10 - 6997",
      "description": "As seen on TV!",
      "price": "19.99",
      "display_price": "$19.99",
      "available_on": "2018-07-26T16:37:29.162Z",
      "slug": "product-10-6997",
      "meta_description": null,
      "meta_keywords": null,
      "shipping_category_id": 356,
      "taxon_ids": [
        629
      ],
      "total_on_hand": 0,
      "meta_title": null,
      "trends": [

      ],
      "brand": "Ruby on Rails",
      "brand_description": null,
      "has_variants": false,
      "master": {
        "id": 957,
        "name": "Product #10 - 6997",
        "sku": "SKU-15",
        "price": "19.99",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-10-6997",
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
          "taxon_id": 629,
          "position": 1,
          "taxon": {
            "id": 629,
            "name": "Ruby on Rails",
            "pretty_name": "Ruby on Rails",
            "permalink": "ruby-on-rails",
            "parent_id": null,
            "taxonomy_id": 214
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
GET /api/returns/RA012047224
X-Spree-Token: 58ebd49e13c12245ed0c68bed9972357ce038a128a880948
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
ETag: W/&quot;794c177c288a5ce23967215983b964ea&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: c3da9706-29c1-463c-9bd7-2d1edd5757a8
X-Runtime: 0.038121
Content-Length: 2565
200 OK
```


```json
{
  "id": 19,
  "number": "RA012047224",
  "state": "authorized",
  "order_id": 351,
  "memo": "Items were broken",
  "created_at": "2019-07-26T16:37:36.844Z",
  "updated_at": "2019-07-26T16:37:36.844Z",
  "reason": {
    "id": 58,
    "name": "Defect #5",
    "active": true,
    "mutable": true,
    "created_at": "2019-07-26T16:37:36.841Z",
    "updated_at": "2019-07-26T16:37:36.841Z"
  },
  "order": {
    "id": 351,
    "number": "R370126997",
    "item_total": "10.0",
    "total": "110.0",
    "state": "complete",
    "adjustment_total": "0.0",
    "user_id": 415,
    "completed_at": "2019-07-26T16:37:36.785Z",
    "bill_address_id": 741,
    "ship_address_id": 742,
    "payment_total": "110.0",
    "shipment_state": "shipped",
    "payment_state": "paid",
    "email": "email19@example.com",
    "special_instructions": null,
    "created_at": "2019-07-26T16:37:36.730Z",
    "updated_at": "2019-07-26T16:37:36.831Z",
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
    "guest_token": "QYajJrCnEoF2mGaZi-0CZg",
    "canceled_at": null,
    "canceler_id": null,
    "store_id": 383,
    "approver_name": null,
    "frontend_viewable": true
  },
  "ship_address": {
    "id": 742,
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
    "country_id": 419,
    "country_iso": "US",
    "state_id": 408,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 419,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 408,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 419
    }
  },
  "bill_address": {
    "id": 741,
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
    "country_id": 419,
    "country_iso": "US",
    "state_id": 408,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 419,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 408,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 419
    }
  },
  "return_items": [
    {
      "name": "Product #21 - 369",
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
        "id": 321,
        "name": "Credit Card"
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
X-Spree-Token: ce36527512dcb0bf2091b57b5e23fc7aed874b6e664bbc25
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
ETag: W/&quot;76f56a62da7e67c93b4eded2284d589c&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: b93b5f70-63a1-40d4-aaac-c091e8d7d007
X-Runtime: 0.018153
Content-Length: 164
200 OK
```


```json
{
  "return_authorizations": [
    {
      "number": "RA458172418",
      "created_at": "2019-07-26T16:37:36.053Z",
      "return_amount": "10.0",
      "order_number": "R985222697",
      "state": "authorized"
    }
  ]
}
```



## returns a 200


### Request

#### Endpoint

```plaintext
GET /api/returns/RA661370230
X-Spree-Token: 60eadba32f7e37ab37b2ad41cf22a9f9602bc8b21d15a1fa
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
ETag: W/&quot;e00e8129fcfeac42d9ac97f637f57b47&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: bdeb5537-45bf-4e2f-abd1-477d59aa5a59
X-Runtime: 0.049037
Content-Length: 2565
200 OK
```


```json
{
  "id": 18,
  "number": "RA661370230",
  "state": "authorized",
  "order_id": 350,
  "memo": "Items were broken",
  "created_at": "2019-07-26T16:37:36.461Z",
  "updated_at": "2019-07-26T16:37:36.461Z",
  "reason": {
    "id": 56,
    "name": "Defect #3",
    "active": true,
    "mutable": true,
    "created_at": "2019-07-26T16:37:36.458Z",
    "updated_at": "2019-07-26T16:37:36.458Z"
  },
  "order": {
    "id": 350,
    "number": "R080169324",
    "item_total": "10.0",
    "total": "110.0",
    "state": "complete",
    "adjustment_total": "0.0",
    "user_id": 414,
    "completed_at": "2019-07-26T16:37:36.398Z",
    "bill_address_id": 739,
    "ship_address_id": 740,
    "payment_total": "110.0",
    "shipment_state": "shipped",
    "payment_state": "paid",
    "email": "email18@example.com",
    "special_instructions": null,
    "created_at": "2019-07-26T16:37:36.332Z",
    "updated_at": "2019-07-26T16:37:36.447Z",
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
    "guest_token": "w4pG6PSBffszKHInX-Sn4g",
    "canceled_at": null,
    "canceler_id": null,
    "store_id": 382,
    "approver_name": null,
    "frontend_viewable": true
  },
  "ship_address": {
    "id": 740,
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
    "country_id": 418,
    "country_iso": "US",
    "state_id": 407,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 418,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 407,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 418
    }
  },
  "bill_address": {
    "id": 739,
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
    "country_id": 418,
    "country_iso": "US",
    "state_id": 407,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 418,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 407,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 418
    }
  },
  "return_items": [
    {
      "name": "Product #20 - 440",
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
        "id": 319,
        "name": "Credit Card"
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
GET /api/returns/RA051154133
X-Spree-Token: 07c98b48d9b38b0000efacc0ab3100155931d04dc17d55c1
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
X-Request-Id: 316122f4-3823-4d0c-9ea5-e8e602f63e9e
X-Runtime: 0.007425
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
X-Spree-Token: 78d99db4f8c0e8f86aed490cb22a3afab9d9a3447cfcc186
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
ETag: W/&quot;be779ba38067cdc5fca440eadeeb546f&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 63fde453-5352-48b7-a174-1339e1bbf576
X-Runtime: 0.038406
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
      "created_at": "2019-07-26T16:37:30.141Z"
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
X-Spree-Token: 801382aa156e85e767f51b522849d5ae6b32a6c7aca740a7
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
X-Spree-Token: 801382aa156e85e767f51b522849d5ae6b32a6c7aca740a7
ETag: W/&quot;30dbb153afe8c46ef0f26f2792b6d117&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: b7ec9f19-ded9-4a86-8517-b368bfda5907
X-Runtime: 0.029298
Content-Length: 124
200 OK
```


```json
{
  "email": "email8@example.com",
  "first_name": null,
  "last_name": null,
  "id": 403,
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
user[email]=email9%40example.com&user[password]=secret
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
X-Spree-Token: db59aeffcd36719052bde0ed00ac8760a463010227d78c75
ETag: W/&quot;f5f3dc672cdb8fbec10517bdb37b403b&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 06213c66-aa31-4d33-85a9-4462dcf21f10
X-Runtime: 0.005605
Content-Length: 551
200 OK
```


```json
{
  "id": 405,
  "email": "email9@example.com",
  "persistence_token": null,
  "perishable_token": null,
  "last_request_at": null,
  "login": "email9@example.com",
  "ship_address_id": null,
  "bill_address_id": null,
  "created_at": "2019-07-26T16:37:28.488Z",
  "updated_at": "2019-07-26T16:37:28.492Z",
  "spree_api_key": "db59aeffcd36719052bde0ed00ac8760a463010227d78c75",
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
X-Spree-Token: be7656f4be293858da3291b9ab17f6aa27734d20db3ceb53
ETag: W/&quot;a1d6e52a6cad19ccd6f8d8ecd8a60ea1&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 0c7b6f16-74b3-464b-89b1-c2cd1dfdea59
X-Runtime: 0.029028
Content-Length: 157
201 Created
```


```json
{
  "id": 404,
  "email": "test@example.com",
  "created_at": "2019-07-26T16:37:28.463Z",
  "updated_at": "2019-07-26T16:37:28.465Z",
  "bill_address": null,
  "ship_address": null
}
```



# Variant



## Fetching a variant


### Request

#### Endpoint

```plaintext
GET /api/variants/961
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
ETag: W/&quot;ce8f33a23d312c437dc6741e22cc32bf&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: e6967283-037b-4b25-9829-21a78e6f982f
X-Runtime: 0.091098
Content-Length: 1454
200 OK
```


```json
{
  "id": 961,
  "name": "Product #13 - 950",
  "sku": "SKU-18",
  "price": "10.0",
  "weight": "0.0",
  "height": null,
  "width": null,
  "depth": null,
  "is_master": false,
  "slug": "product-13-950",
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
      "id": 422,
      "name": "Size-6",
      "presentation": "S",
      "option_type_name": "foo-size-6",
      "option_type_id": 422,
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
      "attachment_updated_at": "2019-07-26T16:37:29.789Z",
      "attachment_width": 489,
      "attachment_height": 490,
      "alt": null,
      "viewable_type": "Spree::Variant",
      "viewable_id": 961,
      "mini_url": "/spree/products/2/mini/thinking-cat.jpg?1564159049",
      "small_url": "/spree/products/2/small/thinking-cat.jpg?1564159049",
      "product_url": "/spree/products/2/product/thinking-cat.jpg?1564159049",
      "large_url": "/spree/products/2/large/thinking-cat.jpg?1564159049"
    }
  ],
  "variant_properties": [

  ],
  "stock_items": [

  ],
  "prices": [
    {
      "id": 1868,
      "vendor_id": 2929,
      "price": "10.0",
      "original_price": "10.0",
      "discount_percent": 0.0,
      "total_on_hand": 0,
      "country_iso": null,
      "final_sale": false,
      "on_sale": false
    },
    {
      "id": 1869,
      "vendor_id": 2930,
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
X-Spree-Token: c2c6eeb7966967772253caec2a148810a80b7938b6d826ca
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
ETag: W/&quot;37fd3cc7b490a061bf1eb49de4953b09&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 8d185a5e-4cda-41e8-af8f-5d27a0050b5f
X-Runtime: 0.014535
Content-Length: 199
200 OK
```


```json
[
  {
    "id": 33,
    "user_id": 420,
    "payment_source_type": "SolidusPaypalBraintree::Source",
    "payment_source_id": 49,
    "default": false,
    "created_at": "2019-07-26T16:37:37.340Z",
    "updated_at": "2019-07-26T16:37:37.340Z"
  }
]
```



## Remove the payment from the user wallet


### Request

#### Endpoint

```plaintext
DELETE /api/wallet_payment_sources/34
Accept: application/json
X-Spree-Token: d539765f22bec04fe258daaca2ce60b041df72fb251631f3
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
X-Request-Id: c55b0505-2634-4075-a962-dd8b67e835d2
X-Runtime: 0.014402
204 No Content
```




## Set a wallet payment source as the default user payment method


### Request

#### Endpoint

```plaintext
POST /api/wallet_payment_sources/32/default
Accept: application/json
X-Spree-Token: 521e15e2f429f1e04ef3a3b94d003807c2b78661a3a5597b
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
X-Request-Id: 5dd8f127-16b9-4b40-96d0-7f40f8aa2b24
X-Runtime: 0.036856
204 No Content
```




