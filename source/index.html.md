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
PUT /api/orders/R234659612/addresses/612
Accept: application/json
X-Spree-Order-Token: IR0SC6gA2gLHCpPRxdAu2g
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
ETag: W/&quot;289cec3d30c56bb599942908a823274a&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 0af6cc15-d02e-4d44-bc83-643d47aa44cc
X-Runtime: 0.056016
Content-Length: 513
200 OK
```


```json
{
  "id": 613,
  "firstname": "John the Tester",
  "lastname": null,
  "full_name": "John the Tester",
  "address1": "A Different Road",
  "address2": "Northwest",
  "city": "Herndon",
  "zipcode": "10014",
  "phone": "555-555-0199",
  "company": "Company",
  "alternative_phone": "555-555-0199",
  "country_id": 372,
  "country_iso": "US",
  "state_id": 361,
  "state_name": null,
  "state_text": "AL",
  "country": {
    "id": 372,
    "iso_name": "UNITED STATES",
    "iso": "US",
    "iso3": "USA",
    "name": "United States",
    "numcode": 840
  },
  "state": {
    "id": 361,
    "name": "Alabama",
    "abbr": "AL",
    "country_id": 372
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
X-Spree-Order-Token: r3VFMEFxqRlTOg-gryRn_Q
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/braintree/transactions`

#### Parameters


```json
order_id=R824939674&payment_method_id=246&options[restart_checkout]=true&transaction[email]=maryellen.oga%40mckenziemcglynn.com&transaction[nonce]=fake-paypal-billing-agreement-nonce&transaction[phone]=555-555-0199&transaction[address_attributes][first_name]=John&transaction[address_attributes][last_name]=Stamm&transaction[address_attributes][address_line_1]=A+Different+Road&transaction[address_attributes][city]=Herndon&transaction[address_attributes][state_code]=AL&transaction[address_attributes][zip]=10003&transaction[address_attributes][country_code]=US&transaction[payment_type]=PayPalAccount
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
ETag: W/&quot;92add9c2e00ba0663942d82df056b0f9&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 716bbfb3-7fd7-44aa-81a6-f8730787c528
X-Runtime: 0.290344
Content-Length: 4301
200 OK
```


```json
{
  "id": 289,
  "number": "R824939674",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2019-07-22T12:35:45.731Z",
  "updated_at": "2019-07-22T12:35:46.050Z",
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
  "token": "r3VFMEFxqRlTOg-gryRn_Q",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 246,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 602,
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
    "id": 602,
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
      "id": 285,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 854,
      "vendor_id": 2643,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "variant": {
        "id": 854,
        "name": "Product #2 - 8668",
        "sku": "SKU-3",
        "price": "10.0",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-2-8668",
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
            "id": 370,
            "name": "Size-2",
            "presentation": "S",
            "option_type_name": "foo-size-2",
            "option_type_id": 370,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 496
      },
      "vendor_name": "Vendor #7",
      "adjustments": [

      ]
    }
  ],
  "payments": [
    {
      "id": 125,
      "source_type": "SolidusPaypalBraintree::Source",
      "source_id": 37,
      "amount": "110.0",
      "display_amount": "$110.00",
      "payment_method_id": 246,
      "state": "checkout",
      "avs_response": null,
      "created_at": "2019-07-22T12:35:45.852Z",
      "updated_at": "2019-07-22T12:35:45.852Z",
      "payment_method": {
        "id": 246,
        "name": "Braintree"
      },
      "source": {
        "id": 37,
        "payment_type": "PayPalAccount",
        "token": "79gcvv",
        "created_at": "2019-07-22T12:35:45.850Z"
      }
    }
  ],
  "shipments": [
    {
      "id": 244,
      "tracking": null,
      "tracking_url": null,
      "number": "H56626361400",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R824939674",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 245,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 222,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 245,
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
              "id": 313,
              "name": "ShippingCategory #2"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 854,
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



## Creating an ApplePay one-click checkout transaction


### Request

#### Endpoint

```plaintext
POST /api/braintree/transactions
Accept: application/json
X-Spree-Order-Token: t6HywDclKVgEJe6QjcWROQ
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/braintree/transactions`

#### Parameters


```json
order_id=R251877221&payment_method_id=245&options[restart_checkout]=true&transaction[email]=maryellen.oga%40mckenziemcglynn.com&transaction[nonce]=fake-apple-pay-visa-nonce&transaction[phone]=555-555-0199&transaction[address_attributes][first_name]=John&transaction[address_attributes][last_name]=Stamm&transaction[address_attributes][address_line_1]=A+Different+Road&transaction[address_attributes][city]=Herndon&transaction[address_attributes][state_code]=AL&transaction[address_attributes][zip]=10001&transaction[address_attributes][country_code]=US&transaction[payment_type]=ApplePayCard
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
ETag: W/&quot;008d9048035d0d0adf43071e0a1bc81d&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: a5b3ce24-f84b-4aff-bb14-473ad1d4a47b
X-Runtime: 0.569259
Content-Length: 4300
200 OK
```


```json
{
  "id": 288,
  "number": "R251877221",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2019-07-22T12:35:44.513Z",
  "updated_at": "2019-07-22T12:35:45.341Z",
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
  "token": "t6HywDclKVgEJe6QjcWROQ",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 245,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 599,
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
    "id": 599,
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
      "id": 284,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 852,
      "vendor_id": 2637,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "variant": {
        "id": 852,
        "name": "Product #1 - 3770",
        "sku": "SKU-1",
        "price": "10.0",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-1-3770",
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
            "id": 369,
            "name": "Size-1",
            "presentation": "S",
            "option_type_name": "foo-size-1",
            "option_type_id": 369,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 495
      },
      "vendor_name": "Vendor #2",
      "adjustments": [

      ]
    }
  ],
  "payments": [
    {
      "id": 124,
      "source_type": "SolidusPaypalBraintree::Source",
      "source_id": 36,
      "amount": "110.0",
      "display_amount": "$110.00",
      "payment_method_id": 245,
      "state": "checkout",
      "avs_response": null,
      "created_at": "2019-07-22T12:35:45.043Z",
      "updated_at": "2019-07-22T12:35:45.043Z",
      "payment_method": {
        "id": 245,
        "name": "Braintree"
      },
      "source": {
        "id": 36,
        "payment_type": "ApplePayCard",
        "token": "6b64ck",
        "created_at": "2019-07-22T12:35:45.042Z"
      }
    }
  ],
  "shipments": [
    {
      "id": 242,
      "tracking": null,
      "tracking_url": null,
      "number": "H01504405507",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R251877221",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 243,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 221,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 243,
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
              "id": 312,
              "name": "ShippingCategory #1"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 852,
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



# Checkout



## Processing the checkout payment step with a not yet existing ApplePay payment


### Request

#### Endpoint

```plaintext
PATCH /api/checkouts/R706765758
Accept: application/json
X-Spree-Order-Token: 6nGUsNwEJsdb4sRVPbSjFA
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=252&order[payment_attributes][][source_attributes][nonce]=fake-apple-pay-visa-nonce&order[payment_attributes][][source_attributes][payment_type]=ApplePayCard
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
ETag: W/&quot;311868e9334da35ff4a3f97e027fc42b&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 459f5be3-8110-49d0-bdcf-fce4bb6c0fe2
X-Runtime: 0.170007
Content-Length: 3901
200 OK
```


```json
{
  "id": 295,
  "number": "R706765758",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 355,
  "created_at": "2019-07-22T12:35:51.692Z",
  "updated_at": "2019-07-22T12:35:52.058Z",
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
  "token": "6nGUsNwEJsdb4sRVPbSjFA",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 252,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 614,
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
    "country_id": 373,
    "country_iso": "US",
    "state_id": 362,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 373,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 362,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 373
    }
  },
  "ship_address": {
    "id": 615,
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
    "country_id": 373,
    "country_iso": "US",
    "state_id": 362,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 373,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 362,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 373
    }
  },
  "line_items": [
    {
      "id": 291,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 877,
      "vendor_id": 2712,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "variant": {
        "id": 877,
        "name": "Product #17 - 3454",
        "sku": "SKU-26",
        "price": "10.0",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-17-3454",
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
            "id": 378,
            "name": "Size-10",
            "presentation": "S",
            "option_type_name": "foo-size-10",
            "option_type_id": 378,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 511
      },
      "vendor_name": "Vendor #65",
      "adjustments": [

      ]
    }
  ],
  "payments": [

  ],
  "shipments": [
    {
      "id": 250,
      "tracking": null,
      "tracking_url": null,
      "number": "H13821757473",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R706765758",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 251,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 227,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 251,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 227,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 227,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 159,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 324,
              "name": "ShippingCategory #13"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 877,
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



## Processing the checkout payment step with a not yet existing PayPal payment


### Request

#### Endpoint

```plaintext
PATCH /api/checkouts/R281736693
Accept: application/json
X-Spree-Order-Token: Foh_mTZ1LwK0TvuULFTNTg
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=253&order[payment_attributes][][source_attributes][nonce]=fake-paypal-billing-agreement-nonce&order[payment_attributes][][source_attributes][payment_type]=PayPalAccount
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
ETag: W/&quot;3a35e612d5611be0ba10156d53d8b1a3&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: c9efdacf-1513-4521-af62-2e21cfa97d97
X-Runtime: 0.127253
Content-Length: 3901
200 OK
```


```json
{
  "id": 296,
  "number": "R281736693",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 356,
  "created_at": "2019-07-22T12:35:52.449Z",
  "updated_at": "2019-07-22T12:35:52.759Z",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "email17@example.com",
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
  "token": "Foh_mTZ1LwK0TvuULFTNTg",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 253,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 616,
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
    "country_id": 374,
    "country_iso": "US",
    "state_id": 363,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 374,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 363,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 374
    }
  },
  "ship_address": {
    "id": 617,
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
    "country_id": 374,
    "country_iso": "US",
    "state_id": 363,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 374,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 363,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 374
    }
  },
  "line_items": [
    {
      "id": 292,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 879,
      "vendor_id": 2718,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "variant": {
        "id": 879,
        "name": "Product #18 - 7912",
        "sku": "SKU-28",
        "price": "10.0",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-18-7912",
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
            "id": 379,
            "name": "Size-11",
            "presentation": "S",
            "option_type_name": "foo-size-11",
            "option_type_id": 379,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 512
      },
      "vendor_name": "Vendor #70",
      "adjustments": [

      ]
    }
  ],
  "payments": [

  ],
  "shipments": [
    {
      "id": 252,
      "tracking": null,
      "tracking_url": null,
      "number": "H07635653513",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R281736693",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 253,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 228,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 253,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 228,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 228,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 160,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 325,
              "name": "ShippingCategory #14"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 879,
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



## Processing the checkout payment step with a not yet existing credit card payment


### Request

#### Endpoint

```plaintext
PATCH /api/checkouts/R135636579
Accept: application/json
X-Spree-Order-Token: FHJpVEqg6fWhB6A25cvXgw
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=254&order[payment_attributes][][source_attributes][nonce]=fake-valid-visa-nonce&order[payment_attributes][][source_attributes][payment_type]=CreditCard
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
ETag: W/&quot;607704d03fddb711304af5fe507b21b4&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 5dbf3f54-f45e-4e16-bd1b-11046893b4f3
X-Runtime: 0.125998
Content-Length: 3901
200 OK
```


```json
{
  "id": 297,
  "number": "R135636579",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 357,
  "created_at": "2019-07-22T12:35:53.141Z",
  "updated_at": "2019-07-22T12:35:53.479Z",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "email18@example.com",
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
  "token": "FHJpVEqg6fWhB6A25cvXgw",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 254,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 618,
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
    "country_id": 375,
    "country_iso": "US",
    "state_id": 364,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 375,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 364,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 375
    }
  },
  "ship_address": {
    "id": 619,
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
    "country_id": 375,
    "country_iso": "US",
    "state_id": 364,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 375,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 364,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 375
    }
  },
  "line_items": [
    {
      "id": 293,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 881,
      "vendor_id": 2724,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "variant": {
        "id": 881,
        "name": "Product #19 - 4066",
        "sku": "SKU-30",
        "price": "10.0",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-19-4066",
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
            "id": 380,
            "name": "Size-12",
            "presentation": "S",
            "option_type_name": "foo-size-12",
            "option_type_id": 380,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 513
      },
      "vendor_name": "Vendor #75",
      "adjustments": [

      ]
    }
  ],
  "payments": [

  ],
  "shipments": [
    {
      "id": 254,
      "tracking": null,
      "tracking_url": null,
      "number": "H73422281601",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R135636579",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 255,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 229,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 255,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 229,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 229,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 161,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 326,
              "name": "ShippingCategory #15"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 881,
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



## Processing the checkout payment step with an already existing payment


### Request

#### Endpoint

```plaintext
PATCH /api/checkouts/R665331961
Accept: application/json
X-Spree-Order-Token: vme6K_GYUmPFl-35h-Z1Sg
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=255&order[payment_attributes][][source_attributes][wallet_payment_source_id]=28
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
ETag: W/&quot;3ba4c316c21209359ef2430bcd3b580f&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 2c4aaf08-fcc3-4fff-a8b0-4e313b868d6c
X-Runtime: 0.103044
Content-Length: 3901
200 OK
```


```json
{
  "id": 298,
  "number": "R665331961",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 358,
  "created_at": "2019-07-22T12:35:53.876Z",
  "updated_at": "2019-07-22T12:35:54.170Z",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "email19@example.com",
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
  "token": "vme6K_GYUmPFl-35h-Z1Sg",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 255,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 620,
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
    "country_id": 376,
    "country_iso": "US",
    "state_id": 365,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 376,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 365,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 376
    }
  },
  "ship_address": {
    "id": 621,
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
    "country_id": 376,
    "country_iso": "US",
    "state_id": 365,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 376,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 365,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 376
    }
  },
  "line_items": [
    {
      "id": 294,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 883,
      "vendor_id": 2730,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "variant": {
        "id": 883,
        "name": "Product #20 - 2621",
        "sku": "SKU-32",
        "price": "10.0",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-20-2621",
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
            "id": 381,
            "name": "Size-13",
            "presentation": "S",
            "option_type_name": "foo-size-13",
            "option_type_id": 381,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 514
      },
      "vendor_name": "Vendor #80",
      "adjustments": [

      ]
    }
  ],
  "payments": [

  ],
  "shipments": [
    {
      "id": 256,
      "tracking": null,
      "tracking_url": null,
      "number": "H53576758004",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R665331961",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 257,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 230,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 257,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 230,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 230,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 162,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 327,
              "name": "ShippingCategory #16"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 883,
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
POST /api/orders/R884849463/line_items
Accept: application/json
X-Spree-Order-Token: tOhP5fFeZVkbhzpbirsFIg
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/:order_number/line_items`

#### Parameters


```json
line_item[variant_id]=867&line_item[options][vendor_id]=2680
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
ETag: W/&quot;0b517d6792ef776ac28803eea6cf077b&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: d93094a0-379c-445b-8f0f-831f0962a39b
X-Runtime: 0.113893
Content-Length: 734
201 Created
```


```json
{
  "id": 287,
  "quantity": 1,
  "price": "19.99",
  "variant_id": 867,
  "vendor_id": 2680,
  "single_display_amount": "$19.99",
  "display_amount": "$19.99",
  "total": "19.99",
  "variant": {
    "id": 867,
    "name": "Product #12 - 3912",
    "sku": "SKU-16",
    "price": "19.99",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": false,
    "slug": "product-12-3912",
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
        "id": 373,
        "name": "Size-5",
        "presentation": "S",
        "option_type_name": "foo-size-5",
        "option_type_id": 373,
        "option_type_presentation": "Size"
      }
    ],
    "images": [

    ],
    "product_id": 506
  },
  "vendor_name": "Vendor #37",
  "adjustments": [

  ]
}
```



## Deleting a line item


### Request

#### Endpoint

```plaintext
DELETE /api/orders/R283722098/line_items/289
Accept: application/json
X-Spree-Order-Token: 4Tx6fqWc-fv3MB_HA383aQ
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
X-Request-Id: 0a1e401b-73c0-4400-8889-e05886080a62
X-Runtime: 0.089773
204 No Content
```




## Updating a line item


### Request

#### Endpoint

```plaintext
PUT /api/orders/R767284293/line_items/288
Accept: application/json
X-Spree-Order-Token: -hnbfJfqpNIwTmp_Ju7ZFA
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
ETag: W/&quot;74e74adc4c4396ac305c6e85564bb33c&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 8e05703b-8faa-4227-8af4-79883e41f5a0
X-Runtime: 0.155619
Content-Length: 729
200 OK
```


```json
{
  "id": 288,
  "quantity": 2,
  "price": "10.0",
  "variant_id": 869,
  "vendor_id": 2685,
  "single_display_amount": "$10.00",
  "display_amount": "$20.00",
  "total": "20.0",
  "variant": {
    "id": 869,
    "name": "Product #13 - 225",
    "sku": "SKU-18",
    "price": "10.0",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": false,
    "slug": "product-13-225",
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
        "id": 374,
        "name": "Size-6",
        "presentation": "S",
        "option_type_name": "foo-size-6",
        "option_type_id": 374,
        "option_type_presentation": "Size"
      }
    ],
    "images": [

    ],
    "product_id": 507
  },
  "vendor_name": "Vendor #42",
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
X-Request-Id: 69720f33-741e-4485-90d0-80b5b42067f3
X-Runtime: 0.008299
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



## Get my orders


### Request

#### Endpoint

```plaintext
GET /api/orders/mine
X-Spree-Token: 0b76e796105e671b315ae2c008d78633d088df337b964cbe
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
X-Request-Id: 89e1974e-4577-4a79-b4cf-c34346826e55
X-Runtime: 0.175130
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
Date: Mon, 22 Jul 2019 12:35:46 GMT
Surrogate-Control: max-age=900
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;c376a2707d3102cbee1deb05ec1934b7&quot;
X-Request-Id: 4ba2fff2-f3c6-424b-9930-73de255381fd
X-Runtime: 0.110759
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
      "id": 497,
      "name": "Product #3 - 8146",
      "description": "As seen on TV!",
      "price": "19.99",
      "display_price": "$19.99",
      "available_on": "2018-07-22T12:35:46.124Z",
      "slug": "product-3-8146",
      "meta_description": null,
      "meta_keywords": null,
      "shipping_category_id": 314,
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
        "id": 855,
        "name": "Product #3 - 8146",
        "sku": "SKU-5",
        "price": "19.99",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-3-8146",
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
GET /api/products/product-4-9562
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
Date: Mon, 22 Jul 2019 12:35:46 GMT
Surrogate-Control: max-age=900
Surrogate-Key: product_id=1
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;1b4fee965df8219f52daa95b4cda75af&quot;
X-Request-Id: a0d95725-f95a-4395-8b19-d4932cd59a87
X-Runtime: 0.055781
Content-Length: 828
200 OK
```


```json
{
  "id": 498,
  "name": "Product #4 - 9562",
  "description": "As seen on TV!",
  "price": "19.99",
  "display_price": "$19.99",
  "available_on": "2018-07-22T12:35:46.356Z",
  "slug": "product-4-9562",
  "meta_description": null,
  "meta_keywords": null,
  "shipping_category_id": 315,
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
    "id": 856,
    "name": "Product #4 - 9562",
    "sku": "SKU-6",
    "price": "19.99",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": true,
    "slug": "product-4-9562",
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
X-Request-Id: 850ca6f2-7a5b-452a-8f2a-28bab93e3ef7
X-Runtime: 0.023972
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
ETag: W/&quot;6123c40fa3358265a623a5905fa9d9d0&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 6b96497f-0273-4ff7-93fc-d8a4cd4c77cf
X-Runtime: 0.066713
Content-Length: 1085
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
      "id": 500,
      "name": "Product #6 - 396",
      "description": "As seen on TV!",
      "price": "19.99",
      "display_price": "$19.99",
      "available_on": "2018-07-22T12:35:46.767Z",
      "slug": "product-6-396",
      "meta_description": null,
      "meta_keywords": null,
      "shipping_category_id": 317,
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
        "id": 858,
        "name": "Product #6 - 396",
        "sku": "SKU-8",
        "price": "19.99",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-6-396",
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
ETag: W/&quot;7ce36a43f0785a39ac5d2ce617ef71f1&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: b24f0767-449b-4142-b67e-3248722f13e3
X-Runtime: 0.056613
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
      "id": 502,
      "name": "Product #8 - 1868",
      "description": "As seen on TV!",
      "price": "19.99",
      "display_price": "$19.99",
      "available_on": "2018-07-22T12:35:47.216Z",
      "slug": "product-8-1868",
      "meta_description": null,
      "meta_keywords": null,
      "shipping_category_id": 318,
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
        "id": 860,
        "name": "Product #8 - 1868",
        "sku": "SKU-10",
        "price": "19.99",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-8-1868",
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

## Gets the user&#39;s return authorizations


### Request

#### Endpoint

```plaintext
GET /api/returns/mine
X-Spree-Token: 8c5793074c21707f67c8ffe7ffca1282e309789b0602545b
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
ETag: W/&quot;ae0755cfbcd084771cf459a8f641ae30&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: c624bca3-2789-4e8c-9a45-88274680f9ff
X-Runtime: 0.019804
Content-Length: 164
200 OK
```


```json
{
  "return_authorizations": [
    {
      "number": "RA831771867",
      "created_at": "2019-07-22T12:35:50.250Z",
      "return_amount": "10.0",
      "order_number": "R282744920",
      "state": "authorized"
    }
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
X-Spree-Token: 7cb1ba878bfe09872b1f8ffe08552b2dbdf47282cd5fc2d9
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
ETag: W/&quot;0f7d1a684d2afbdefbfb7e901bf45d7c&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 41ab9466-da81-4d7a-b219-84ac877894d7
X-Runtime: 0.048904
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
      "created_at": "2019-07-22T12:35:50.481Z"
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
X-Spree-Token: d9fb963d86335f932fe3f53f2d4029bb8fc0dfac27e689d9
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
X-Spree-Token: d9fb963d86335f932fe3f53f2d4029bb8fc0dfac27e689d9
ETag: W/&quot;7bcc1df11f8a1b97e83fbcba9ad7c482&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: dc71af28-4d08-4bdd-97a1-da4ffe7575bd
X-Runtime: 0.036158
Content-Length: 97
200 OK
```


```json
{
  "email": "email7@example.com",
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
user[email]=email8%40example.com&user[password]=secret
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
X-Spree-Token: 2cc14c6898b1bea117e58eace97472a3757edbbdf82266d8
ETag: W/&quot;a76fa2b59e35eb8c3bf89230188e331a&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: e3a981c9-956f-4a88-925d-85d51f516735
X-Runtime: 0.007505
Content-Length: 551
200 OK
```


```json
{
  "id": 347,
  "email": "email8@example.com",
  "persistence_token": null,
  "perishable_token": null,
  "last_request_at": null,
  "login": "email8@example.com",
  "ship_address_id": null,
  "bill_address_id": null,
  "created_at": "2019-07-22T12:35:49.511Z",
  "updated_at": "2019-07-22T12:35:49.519Z",
  "spree_api_key": "2cc14c6898b1bea117e58eace97472a3757edbbdf82266d8",
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
X-Spree-Token: bcd423a015cfa4ad0e2a3ea540f3cf1191ab428a34c29af8
ETag: W/&quot;0ec4d13fd59325ecd1c569bd4436ceee&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 2e63e65f-1614-4d74-ad08-a9c74d6bf430
X-Runtime: 0.024622
Content-Length: 157
201 Created
```


```json
{
  "id": 346,
  "email": "test@example.com",
  "created_at": "2019-07-22T12:35:49.486Z",
  "updated_at": "2019-07-22T12:35:49.489Z",
  "bill_address": null,
  "ship_address": null
}
```



# Variant



## Fetching a variant


### Request

#### Endpoint

```plaintext
GET /api/variants/875
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
ETag: W/&quot;20720ae17439dc56b59e373db9362c45&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: de2a4c01-5162-4fb0-bd45-9642418b10ce
X-Runtime: 0.126104
Content-Length: 1456
200 OK
```


```json
{
  "id": 875,
  "name": "Product #16 - 8942",
  "sku": "SKU-24",
  "price": "10.0",
  "weight": "0.0",
  "height": null,
  "width": null,
  "depth": null,
  "is_master": false,
  "slug": "product-16-8942",
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
      "id": 377,
      "name": "Size-9",
      "presentation": "S",
      "option_type_name": "foo-size-9",
      "option_type_id": 377,
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
      "attachment_updated_at": "2019-07-22T12:35:50.858Z",
      "attachment_width": 489,
      "attachment_height": 490,
      "alt": null,
      "viewable_type": "Spree::Variant",
      "viewable_id": 875,
      "mini_url": "/spree/products/2/mini/thinking-cat.jpg?1563798950",
      "small_url": "/spree/products/2/small/thinking-cat.jpg?1563798950",
      "product_url": "/spree/products/2/product/thinking-cat.jpg?1563798950",
      "large_url": "/spree/products/2/large/thinking-cat.jpg?1563798950"
    }
  ],
  "variant_properties": [

  ],
  "stock_items": [

  ],
  "prices": [
    {
      "id": 1707,
      "vendor_id": 2707,
      "price": "10.0",
      "original_price": "10.0",
      "discount_percent": 0.0,
      "total_on_hand": 0,
      "country_iso": null,
      "final_sale": false,
      "on_sale": false
    },
    {
      "id": 1708,
      "vendor_id": 2708,
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
X-Spree-Token: fb4e52c09347cfeee7bbb4f1b9e4d634477819adfebd1944
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
ETag: W/&quot;257b51733a8a8a4d2b5ebd760e88172b&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: e2e8cf54-9e78-42f3-94aa-b5fa1c75ec8d
X-Runtime: 0.034877
Content-Length: 199
200 OK
```


```json
[
  {
    "id": 25,
    "user_id": 348,
    "payment_source_type": "SolidusPaypalBraintree::Source",
    "payment_source_id": 38,
    "default": false,
    "created_at": "2019-07-22T12:35:49.562Z",
    "updated_at": "2019-07-22T12:35:49.562Z"
  }
]
```



## Remove the payment from the user wallet


### Request

#### Endpoint

```plaintext
DELETE /api/wallet_payment_sources/27
Accept: application/json
X-Spree-Token: 35c618bb0ce84eda23903f951bcb07ab6de251593303cb3e
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
X-Request-Id: 7bf66da9-829e-4eac-a62c-72bde7cee1a7
X-Runtime: 0.015188
204 No Content
```




## Set a wallet payment source as the default user payment method


### Request

#### Endpoint

```plaintext
POST /api/wallet_payment_sources/26/default
Accept: application/json
X-Spree-Token: 46f26097d94e0a03c12b59d1af184bf86df51bdca6da498e
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
X-Request-Id: 58c8c040-1cd2-4f21-91fc-b06e02b5da9d
X-Runtime: 0.013838
204 No Content
```




