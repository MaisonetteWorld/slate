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
PUT /api/orders/R381759613/addresses/705
Accept: application/json
X-Spree-Order-Token: 27u8s5wMpndZoBb-OTVSPg
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
ETag: W/&quot;7007e03f0e211d622c69cbc3697a2832&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 39186aec-b765-49d7-817e-34cc1930f53a
X-Runtime: 0.041749
Content-Length: 513
200 OK
```


```json
{
  "id": 706,
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
  "country_id": 399,
  "country_iso": "US",
  "state_id": 388,
  "state_name": null,
  "state_text": "AL",
  "country": {
    "id": 399,
    "iso_name": "UNITED STATES",
    "iso": "US",
    "iso3": "USA",
    "name": "United States",
    "numcode": 840
  },
  "state": {
    "id": 388,
    "name": "Alabama",
    "abbr": "AL",
    "country_id": 399
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
X-Spree-Order-Token: gib5-aQvszi6Q3q-GNklYw
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/braintree/transactions`

#### Parameters


```json
order_id=R614385533&payment_method_id=336&options[restart_checkout]=true&transaction[email]=maryellen.oga%40mckenziemcglynn.com&transaction[nonce]=fake-paypal-billing-agreement-nonce&transaction[phone]=555-555-0199&transaction[address_attributes][first_name]=John&transaction[address_attributes][last_name]=Stamm&transaction[address_attributes][address_line_1]=A+Different+Road&transaction[address_attributes][city]=Herndon&transaction[address_attributes][state_code]=AL&transaction[address_attributes][zip]=10035&transaction[address_attributes][country_code]=US&transaction[payment_type]=PayPalAccount
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
ETag: W/&quot;e58948de000255b31d00486382252f60&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 454b0296-48cd-4a17-b222-1e21969878cd
X-Runtime: 0.221556
Content-Length: 4581
200 OK
```


```json
{
  "id": 348,
  "number": "R614385533",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2019-07-29T15:54:38.653Z",
  "updated_at": "2019-07-29T15:54:38.873Z",
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
  "token": "gib5-aQvszi6Q3q-GNklYw",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 336,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 736,
    "firstname": "John",
    "lastname": "Stamm",
    "full_name": "John Stamm",
    "address1": "A Different Road",
    "address2": null,
    "city": "Herndon",
    "zipcode": "10035",
    "phone": "555-555-0199",
    "company": null,
    "alternative_phone": null,
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
  "ship_address": {
    "id": 736,
    "firstname": "John",
    "lastname": "Stamm",
    "full_name": "John Stamm",
    "address1": "A Different Road",
    "address2": null,
    "city": "Herndon",
    "zipcode": "10035",
    "phone": "555-555-0199",
    "company": null,
    "alternative_phone": null,
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
  "line_items": [
    {
      "id": 357,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 985,
      "vendor_id": 2991,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "variant": {
        "id": 985,
        "name": "Product #27 - 990",
        "sku": "SKU-46",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-27-990",
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
            "id": 434,
            "name": "Size-20",
            "presentation": "S",
            "option_type_name": "foo-size-20",
            "option_type_id": 434,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 565,
        "brand": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #118",
      "adjustments": [

      ]
    }
  ],
  "payments": [
    {
      "id": 164,
      "source_type": "SolidusPaypalBraintree::Source",
      "source_id": 59,
      "amount": "110.0",
      "display_amount": "$110.00",
      "payment_method_id": 336,
      "state": "checkout",
      "avs_response": null,
      "created_at": "2019-07-29T15:54:38.744Z",
      "updated_at": "2019-07-29T15:54:38.744Z",
      "payment_method": {
        "id": 336,
        "name": "Braintree"
      },
      "source": {
        "id": 59,
        "payment_type": "PayPalAccount",
        "token": "79gcvv",
        "created_at": "2019-07-29T15:54:38.743Z"
      }
    }
  ],
  "shipments": [
    {
      "id": 292,
      "tracking": null,
      "tracking_url": null,
      "number": "H75280007585",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R614385533",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 293,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 263,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 293,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 263,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 263,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 208,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 366,
              "name": "ShippingCategory #23"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 985,
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
X-Spree-Order-Token: fvlF0RQFLLIxLoVSRYMvbQ
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/braintree/transactions`

#### Parameters


```json
order_id=R728528373&payment_method_id=335&options[restart_checkout]=true&transaction[email]=maryellen.oga%40mckenziemcglynn.com&transaction[nonce]=fake-apple-pay-visa-nonce&transaction[phone]=555-555-0199&transaction[address_attributes][first_name]=John&transaction[address_attributes][last_name]=Stamm&transaction[address_attributes][address_line_1]=A+Different+Road&transaction[address_attributes][city]=Herndon&transaction[address_attributes][state_code]=AL&transaction[address_attributes][zip]=10033&transaction[address_attributes][country_code]=US&transaction[payment_type]=ApplePayCard
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
ETag: W/&quot;8be26feefcc05b10b2f667403a6254e7&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: d4ce85b0-520c-4ef8-bfd2-3b7e294eecf8
X-Runtime: 0.217943
Content-Length: 4582
200 OK
```


```json
{
  "id": 347,
  "number": "R728528373",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2019-07-29T15:54:38.181Z",
  "updated_at": "2019-07-29T15:54:38.401Z",
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
  "token": "fvlF0RQFLLIxLoVSRYMvbQ",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 335,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 733,
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
  "ship_address": {
    "id": 733,
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
  "line_items": [
    {
      "id": 356,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 983,
      "vendor_id": 2985,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "variant": {
        "id": 983,
        "name": "Product #26 - 6995",
        "sku": "SKU-44",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-26-6995",
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
            "id": 433,
            "name": "Size-19",
            "presentation": "S",
            "option_type_name": "foo-size-19",
            "option_type_id": 433,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 564,
        "brand": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #113",
      "adjustments": [

      ]
    }
  ],
  "payments": [
    {
      "id": 163,
      "source_type": "SolidusPaypalBraintree::Source",
      "source_id": 58,
      "amount": "110.0",
      "display_amount": "$110.00",
      "payment_method_id": 335,
      "state": "checkout",
      "avs_response": null,
      "created_at": "2019-07-29T15:54:38.289Z",
      "updated_at": "2019-07-29T15:54:38.289Z",
      "payment_method": {
        "id": 335,
        "name": "Braintree"
      },
      "source": {
        "id": 58,
        "payment_type": "ApplePayCard",
        "token": "6b64ck",
        "created_at": "2019-07-29T15:54:38.289Z"
      }
    }
  ],
  "shipments": [
    {
      "id": 290,
      "tracking": null,
      "tracking_url": null,
      "number": "H24814104603",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R728528373",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 291,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 262,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 291,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 262,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 262,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 207,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 365,
              "name": "ShippingCategory #22"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 983,
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
PUT /api/checkouts/R172832050/complete
Accept: application/json
X-Spree-Order-Token: 00uFmlpki0ANPvNdtna8tg
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
ETag: W/&quot;09ee8455887abc4cb85cf9880a3d6625&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 83e74dc0-2efa-41ec-8c66-eaa752f43a60
X-Runtime: 1.642406
Content-Length: 4713
200 OK
```


```json
{
  "id": 342,
  "number": "R172832050",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "complete",
  "adjustment_total": "0.0",
  "user_id": 406,
  "created_at": "2019-07-29T15:54:32.574Z",
  "updated_at": "2019-07-29T15:54:35.743Z",
  "completed_at": "2019-07-29T15:54:35.743Z",
  "payment_total": "110.0",
  "shipment_state": "ready",
  "payment_state": "paid",
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
  "token": "00uFmlpki0ANPvNdtna8tg",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 322,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    },
    {
      "id": 323,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 721,
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
    "id": 722,
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
      "id": 351,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 971,
      "vendor_id": 2943,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "variant": {
        "id": 971,
        "name": "Product #20 - 2908",
        "sku": "SKU-32",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-20-2908",
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
            "id": 427,
            "name": "Size-13",
            "presentation": "S",
            "option_type_name": "foo-size-13",
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
      "vendor_name": "Vendor #77",
      "adjustments": [

      ]
    }
  ],
  "payments": [
    {
      "id": 158,
      "source_type": "SolidusPaypalBraintree::Source",
      "source_id": 54,
      "amount": "110.0",
      "display_amount": "$110.00",
      "payment_method_id": 322,
      "state": "completed",
      "avs_response": "M",
      "created_at": "2019-07-29T15:54:32.647Z",
      "updated_at": "2019-07-29T15:54:35.624Z",
      "payment_method": {
        "id": 322,
        "name": "Braintree"
      },
      "source": {
        "id": 54,
        "payment_type": "CreditCard",
        "token": "6wwqwz",
        "created_at": "2019-07-29T15:54:32.646Z"
      }
    }
  ],
  "shipments": [
    {
      "id": 284,
      "tracking": "U10000",
      "tracking_url": null,
      "number": "H31701616247",
      "cost": "100.0",
      "shipped_at": null,
      "state": "ready",
      "order_id": "R172832050",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 285,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 257,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 285,
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



## Processing the checkout payment step with a not yet existing ApplePay payment


### Request

#### Endpoint

```plaintext
PATCH /api/checkouts/R045273835
Accept: application/json
X-Spree-Order-Token: atdzxaC9CR8rmJyjKKP1yA
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=321&order[payment_attributes][][source_attributes][nonce]=fake-apple-pay-visa-nonce&order[payment_attributes][][source_attributes][payment_type]=ApplePayCard
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
ETag: W/&quot;c0fb6a11be5538c0bc3d2cf8810c1cf0&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: b48e4db1-f5d5-46ed-b0b7-518b54398872
X-Runtime: 0.106847
Content-Length: 4175
200 OK
```


```json
{
  "id": 341,
  "number": "R045273835",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 405,
  "created_at": "2019-07-29T15:54:32.055Z",
  "updated_at": "2019-07-29T15:54:32.268Z",
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
  "token": "atdzxaC9CR8rmJyjKKP1yA",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 321,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 719,
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
    "country_id": 411,
    "country_iso": "US",
    "state_id": 400,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 411,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 400,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 411
    }
  },
  "ship_address": {
    "id": 720,
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
    "country_id": 411,
    "country_iso": "US",
    "state_id": 400,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 411,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 400,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 411
    }
  },
  "line_items": [
    {
      "id": 350,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 969,
      "vendor_id": 2937,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "variant": {
        "id": 969,
        "name": "Product #19 - 1927",
        "sku": "SKU-30",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-19-1927",
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
            "id": 426,
            "name": "Size-12",
            "presentation": "S",
            "option_type_name": "foo-size-12",
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
      "vendor_name": "Vendor #72",
      "adjustments": [

      ]
    }
  ],
  "payments": [

  ],
  "shipments": [
    {
      "id": 283,
      "tracking": null,
      "tracking_url": null,
      "number": "H86081578020",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R045273835",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 284,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 256,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 284,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 256,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 256,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 201,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 358,
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



## Processing the checkout payment step with a not yet existing PayPal payment


### Request

#### Endpoint

```plaintext
PATCH /api/checkouts/R845885964
Accept: application/json
X-Spree-Order-Token: ET5wNZWSCH9VrNgL6DMUZw
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=320&order[payment_attributes][][source_attributes][nonce]=fake-paypal-billing-agreement-nonce&order[payment_attributes][][source_attributes][payment_type]=PayPalAccount
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
ETag: W/&quot;234e749024e68e27b7c8e073b54f1c61&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 56ecfe61-af13-41c3-ba69-dd528f58e73b
X-Runtime: 0.121018
Content-Length: 4175
200 OK
```


```json
{
  "id": 340,
  "number": "R845885964",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 404,
  "created_at": "2019-07-29T15:54:31.518Z",
  "updated_at": "2019-07-29T15:54:31.725Z",
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
  "token": "ET5wNZWSCH9VrNgL6DMUZw",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 320,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 717,
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
    "country_id": 410,
    "country_iso": "US",
    "state_id": 399,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 410,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 399,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 410
    }
  },
  "ship_address": {
    "id": 718,
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
    "country_id": 410,
    "country_iso": "US",
    "state_id": 399,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 410,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 399,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 410
    }
  },
  "line_items": [
    {
      "id": 349,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 967,
      "vendor_id": 2931,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "variant": {
        "id": 967,
        "name": "Product #18 - 8337",
        "sku": "SKU-28",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-18-8337",
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
            "id": 425,
            "name": "Size-11",
            "presentation": "S",
            "option_type_name": "foo-size-11",
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
      "vendor_name": "Vendor #67",
      "adjustments": [

      ]
    }
  ],
  "payments": [

  ],
  "shipments": [
    {
      "id": 281,
      "tracking": null,
      "tracking_url": null,
      "number": "H86887772547",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R845885964",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 282,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 255,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 282,
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
              "id": 200,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 357,
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



## Processing the checkout payment step with a not yet existing credit card payment


### Request

#### Endpoint

```plaintext
PATCH /api/checkouts/R155952831
Accept: application/json
X-Spree-Order-Token: U4PmQre7e8RonIMwtNl2rA
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=319&order[payment_attributes][][source_attributes][nonce]=fake-valid-visa-nonce&order[payment_attributes][][source_attributes][payment_type]=CreditCard
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
ETag: W/&quot;9c50f0fd72846434f64ddcc7ff3d2da4&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 9b980ec4-c941-465b-a03a-2161c1ed7363
X-Runtime: 0.091050
Content-Length: 4175
200 OK
```


```json
{
  "id": 339,
  "number": "R155952831",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 403,
  "created_at": "2019-07-29T15:54:31.052Z",
  "updated_at": "2019-07-29T15:54:31.250Z",
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
  "token": "U4PmQre7e8RonIMwtNl2rA",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 319,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 715,
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
    "country_id": 409,
    "country_iso": "US",
    "state_id": 398,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 409,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 398,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 409
    }
  },
  "ship_address": {
    "id": 716,
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
    "country_id": 409,
    "country_iso": "US",
    "state_id": 398,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 409,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 398,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 409
    }
  },
  "line_items": [
    {
      "id": 348,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 965,
      "vendor_id": 2925,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "variant": {
        "id": 965,
        "name": "Product #17 - 6060",
        "sku": "SKU-26",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-17-6060",
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
            "id": 424,
            "name": "Size-10",
            "presentation": "S",
            "option_type_name": "foo-size-10",
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
      "vendor_name": "Vendor #62",
      "adjustments": [

      ]
    }
  ],
  "payments": [

  ],
  "shipments": [
    {
      "id": 279,
      "tracking": null,
      "tracking_url": null,
      "number": "H63068004087",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R155952831",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 280,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 254,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 280,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 254,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 254,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 199,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 356,
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



## Processing the checkout payment step with an already existing payment


### Request

#### Endpoint

```plaintext
PATCH /api/checkouts/R170372037
Accept: application/json
X-Spree-Order-Token: RnxwYxTvv54OvJb85D3SDA
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=318&order[payment_attributes][][source_attributes][wallet_payment_source_id]=30
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
ETag: W/&quot;f10d4cfea1709cea91f3f415c7d4e58a&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: cbd54b7b-b82a-4af8-986c-940f930c8708
X-Runtime: 0.094036
Content-Length: 4173
200 OK
```


```json
{
  "id": 338,
  "number": "R170372037",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 402,
  "created_at": "2019-07-29T15:54:30.518Z",
  "updated_at": "2019-07-29T15:54:30.803Z",
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
  "token": "RnxwYxTvv54OvJb85D3SDA",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 318,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 713,
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
    "country_id": 408,
    "country_iso": "US",
    "state_id": 397,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 408,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 397,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 408
    }
  },
  "ship_address": {
    "id": 714,
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
    "country_id": 408,
    "country_iso": "US",
    "state_id": 397,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 408,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 397,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 408
    }
  },
  "line_items": [
    {
      "id": 347,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 963,
      "vendor_id": 2919,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "variant": {
        "id": 963,
        "name": "Product #16 - 4421",
        "sku": "SKU-24",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-16-4421",
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
            "id": 423,
            "name": "Size-9",
            "presentation": "S",
            "option_type_name": "foo-size-9",
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
      "vendor_name": "Vendor #57",
      "adjustments": [

      ]
    }
  ],
  "payments": [

  ],
  "shipments": [
    {
      "id": 277,
      "tracking": null,
      "tracking_url": null,
      "number": "H71367741730",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R170372037",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 278,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 253,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 278,
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
              "id": 198,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 355,
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



# LineItem

Representation of a single cart item for a specific variant with price of vendor

## Creating a line item


### Request

#### Endpoint

```plaintext
POST /api/orders/R830892662/line_items
Accept: application/json
X-Spree-Order-Token: QdvAhEoMe0KaFDOjsbKPsg
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/:order_number/line_items`

#### Parameters


```json
line_item[variant_id]=946&line_item[options][vendor_id]=2866
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
ETag: W/&quot;f41a646081994924b42120afa85d141f&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 85aec228-015c-484a-8601-284fecb0f122
X-Runtime: 0.091273
Content-Length: 769
201 Created
```


```json
{
  "id": 339,
  "quantity": 1,
  "price": "19.99",
  "variant_id": 946,
  "vendor_id": 2866,
  "single_display_amount": "$19.99",
  "display_amount": "$19.99",
  "total": "19.99",
  "variant": {
    "id": 946,
    "name": "Product #4 - 9463",
    "sku": "SKU-7",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": false,
    "slug": "product-4-9463",
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
        "id": 418,
        "name": "Size-4",
        "presentation": "S",
        "option_type_name": "foo-size-4",
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
  "vendor_name": "Vendor #13",
  "adjustments": [

  ]
}
```



## Deleting a line item


### Request

#### Endpoint

```plaintext
DELETE /api/orders/R785542806/line_items/337
Accept: application/json
X-Spree-Order-Token: Ms3oufJwENm7EhwgVW7DEQ
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
X-Request-Id: ef21b5bc-2d7e-4bb0-a173-f8ea3b94bbeb
X-Runtime: 0.120841
204 No Content
```




## Updating a line item


### Request

#### Endpoint

```plaintext
PUT /api/orders/R857679484/line_items/340
Accept: application/json
X-Spree-Order-Token: uVKQk85D1UurbkHcGe0Ang
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
ETag: W/&quot;ee18daf26a4553f7ef76fb456d398aa5&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: b4919dd0-890f-4fee-801d-ed698416b808
X-Runtime: 0.083239
Content-Length: 766
200 OK
```


```json
{
  "id": 340,
  "quantity": 2,
  "price": "10.0",
  "variant_id": 948,
  "vendor_id": 2871,
  "single_display_amount": "$10.00",
  "display_amount": "$20.00",
  "total": "20.0",
  "variant": {
    "id": 948,
    "name": "Product #5 - 3873",
    "sku": "SKU-9",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": false,
    "slug": "product-5-3873",
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
        "id": 419,
        "name": "Size-5",
        "presentation": "S",
        "option_type_name": "foo-size-5",
        "option_type_id": 419,
        "option_type_presentation": "Size"
      }
    ],
    "images": [

    ],
    "product_id": 543,
    "brand": null,
    "brand_description": null
  },
  "vendor_name": "Vendor #18",
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
ETag: W/&quot;22682ebdcb3335cc24186683e383e174&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 77b19507-b630-425d-9a04-ba69ef2011b8
X-Runtime: 0.008211
Content-Length: 134
200 OK
```


```json
[
  {
    "id": 619,
    "name": "Kids",
    "navigation_url": "/navigation/kids",
    "parent_id": 618,
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
Authorization: Bearer b9817d9206753a165334f36f878d43fa940d425ceb0c81d9
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
ETag: W/&quot;2d966b4aeb5895d036ef34bb4333427c&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 480997c3-23af-4936-89a1-f9d49bc08802
X-Runtime: 0.016708
Content-Length: 305
200 OK
```


```json
{
  "orders": [
    {
      "number": "R809061294",
      "completed_at": "2019-07-29T15:54:29.163Z",
      "total": "120.0",
      "state": "Complete",
      "shipment_state": "shipped",
      "shipments": [
        {
          "number": "H14603753087",
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
GET /api/orders/R720988382
Accept: application/json
Authorization: Bearer f95164ee12a2f4d4fb07c15969c1a72cc04b28463b60419d
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
ETag: W/&quot;883fbbf185bd5b05326e7d9084aae250&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 317cc613-d33c-461f-bd81-de9eee257430
X-Runtime: 0.161486
Content-Length: 9077
200 OK
```


```json
{
  "id": 336,
  "number": "R720988382",
  "item_total": "20.0",
  "total": "120.0",
  "ship_total": "100.0",
  "state": "complete",
  "adjustment_total": "0.0",
  "user_id": 398,
  "created_at": "2019-07-29T15:54:28.473Z",
  "updated_at": "2019-07-29T15:54:28.679Z",
  "completed_at": "2019-07-29T15:54:28.535Z",
  "payment_total": "120.0",
  "shipment_state": "shipped",
  "payment_state": "paid",
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
  "token": "L2fzqZkXFbeZI91j--R6qQ",
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
      "name": "Credit Card",
      "partial_name": "gateway",
      "method_type": "gateway"
    },
    {
      "id": 315,
      "name": "Credit Card",
      "partial_name": "gateway",
      "method_type": "gateway"
    }
  ],
  "bill_address": {
    "id": 709,
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
    "id": 710,
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
      "id": 343,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 952,
      "vendor_id": 2883,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "variant": {
        "id": 952,
        "name": "Product #7 - 554",
        "sku": "SKU-13",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-7-554",
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
            "id": 421,
            "name": "Size-7",
            "presentation": "S",
            "option_type_name": "foo-size-7",
            "option_type_id": 421,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 545,
        "brand": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #28",
      "adjustments": [
        {
          "id": 95,
          "source_type": "Spree::TaxRate",
          "source_id": 17,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 343,
          "amount": "2.0",
          "label": "VAT 5%",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-07-29T15:54:28.642Z",
          "updated_at": "2019-07-29T15:54:28.656Z",
          "display_amount": "$2.00"
        },
        {
          "id": 89,
          "source_type": "Spree::PromotionAction",
          "source_id": 39,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 343,
          "amount": "5.0",
          "label": "foo",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-07-29T15:54:28.596Z",
          "updated_at": "2019-07-29T15:54:28.596Z",
          "display_amount": "$5.00"
        },
        {
          "id": 88,
          "source_type": "Spree::PromotionAction",
          "source_id": 39,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 343,
          "amount": "5.0",
          "label": "foo",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-07-29T15:54:28.589Z",
          "updated_at": "2019-07-29T15:54:28.589Z",
          "display_amount": "$5.00"
        }
      ]
    },
    {
      "id": 344,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 952,
      "vendor_id": 2883,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "variant": {
        "id": 952,
        "name": "Product #7 - 554",
        "sku": "SKU-13",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-7-554",
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
            "id": 421,
            "name": "Size-7",
            "presentation": "S",
            "option_type_name": "foo-size-7",
            "option_type_id": 421,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 545,
        "brand": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #28",
      "adjustments": [
        {
          "id": 96,
          "source_type": "Spree::TaxRate",
          "source_id": 18,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 344,
          "amount": "1.5",
          "label": "VAT 5%",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-07-29T15:54:28.675Z",
          "updated_at": "2019-07-29T15:54:28.687Z",
          "display_amount": "$1.50"
        },
        {
          "id": 90,
          "source_type": "Spree::PromotionAction",
          "source_id": 39,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 344,
          "amount": "5.0",
          "label": "bar",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-07-29T15:54:28.603Z",
          "updated_at": "2019-07-29T15:54:28.603Z",
          "display_amount": "$5.00"
        }
      ]
    }
  ],
  "payments": [
    {
      "id": 156,
      "source_type": "Spree::CreditCard",
      "source_id": 127,
      "amount": "120.0",
      "display_amount": "$120.00",
      "payment_method_id": 314,
      "state": "completed",
      "avs_response": null,
      "created_at": "2019-07-29T15:54:28.548Z",
      "updated_at": "2019-07-29T15:54:28.548Z",
      "payment_method": {
        "id": 314,
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
      "id": 274,
      "tracking": "U10000",
      "tracking_url": null,
      "number": "H27446872656",
      "cost": "100.0",
      "shipped_at": "2019-07-29T15:54:28.568Z",
      "state": "shipped",
      "order_id": "R720988382",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 275,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 251,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 275,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 251,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 251,
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
              "id": 348,
              "name": "ShippingCategory #5"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 952,
          "quantity": 1,
          "states": {
            "shipped": 1
          }
        },
        {
          "variant_id": 952,
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
          "adjustable_id": 274,
          "amount": "-10.0",
          "label": "Shipping",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-07-29T15:54:28.617Z",
          "updated_at": "2019-07-29T15:54:28.617Z",
          "display_amount": "-$10.00"
        },
        {
          "id": 91,
          "source_type": "Spree::PromotionAction",
          "source_id": 39,
          "adjustable_type": "Spree::Shipment",
          "adjustable_id": 274,
          "amount": "-9.99",
          "label": "Shipping",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-07-29T15:54:28.610Z",
          "updated_at": "2019-07-29T15:54:28.610Z",
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
      "adjustable_id": 336,
      "amount": "20.0",
      "label": "adj1",
      "promotion_code_id": null,
      "finalized": false,
      "eligible": true,
      "created_at": "2019-07-29T15:54:28.621Z",
      "updated_at": "2019-07-29T15:54:28.621Z",
      "display_amount": "$20.00"
    },
    {
      "id": 94,
      "source_type": "Spree::Promotion",
      "source_id": 57,
      "adjustable_type": "Spree::Order",
      "adjustable_id": 336,
      "amount": "30.0",
      "label": "adj2",
      "promotion_code_id": null,
      "finalized": false,
      "eligible": true,
      "created_at": "2019-07-29T15:54:28.624Z",
      "updated_at": "2019-07-29T15:54:28.624Z",
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
        "id": 709,
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
GET /api/orders/R853398680
Accept: application/json
Authorization: 7a9de4851d0955c7434404ce1b23b5483c507bd92524aadc
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
X-Request-Id: 4ea48bf8-a337-404d-9fb8-c4f9746dc19d
X-Runtime: 0.015556
Content-Length: 58
401 Unauthorized
```


```json
{
  "error": "You are not authorized to perform that action."
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
Date: Mon, 29 Jul 2019 15:54:29 GMT
Surrogate-Control: max-age=900
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;e9bb9807802de25767f629b2586cb8b2&quot;
X-Request-Id: a6a188c9-41e2-4274-b4cc-f1a75cf2f202
X-Runtime: 0.066492
Content-Length: 899
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
      "id": 551,
      "name": "Product #13 - 7381",
      "description": "As seen on TV!",
      "available_on": "2018-07-29T15:54:29.867Z",
      "slug": "product-13-7381",
      "meta_description": null,
      "meta_keywords": null,
      "shipping_category_id": 352,
      "taxon_ids": [

      ],
      "total_on_hand": 0,
      "meta_title": null,
      "display_price": "$19.99",
      "trends": [

      ],
      "brand": null,
      "brand_description": null,
      "has_variants": false,
      "master": {
        "id": 959,
        "name": "Product #13 - 7381",
        "sku": "SKU-21",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-13-7381",
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
GET /api/products/product-14-2768
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
Date: Mon, 29 Jul 2019 15:54:30 GMT
Surrogate-Control: max-age=900
Surrogate-Key: product_id=1
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;c4636995f3e56ec5ddf962983680f738&quot;
X-Request-Id: 31358f46-3ecb-4c75-bdcf-b15afcb231b5
X-Runtime: 0.039034
Content-Length: 817
200 OK
```


```json
{
  "id": 552,
  "name": "Product #14 - 2768",
  "description": "As seen on TV!",
  "available_on": "2018-07-29T15:54:30.014Z",
  "slug": "product-14-2768",
  "meta_description": null,
  "meta_keywords": null,
  "shipping_category_id": 353,
  "taxon_ids": [

  ],
  "total_on_hand": 0,
  "meta_title": null,
  "display_price": "$19.99",
  "trends": [

  ],
  "brand": null,
  "brand_description": null,
  "has_variants": false,
  "master": {
    "id": 960,
    "name": "Product #14 - 2768",
    "sku": "SKU-22",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": true,
    "slug": "product-14-2768",
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
X-Request-Id: ad02b6bc-6ef5-4074-a612-51a1383cec80
X-Runtime: 0.017781
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
GET /api/taxons/products?id=611
Host: example.org
Cookie: 
```

`GET /api/taxons/products`

#### Parameters


```json
id: 611
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
ETag: W/&quot;7cb7611b8a37128a568ed1d10c52fbe5&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 5e76317d-b385-4832-9295-0ce2a044c357
X-Runtime: 0.057898
Content-Length: 1070
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
      "id": 547,
      "name": "Product #9 - 372",
      "description": "As seen on TV!",
      "available_on": "2018-07-29T15:54:29.289Z",
      "slug": "product-9-372",
      "meta_description": null,
      "meta_keywords": null,
      "shipping_category_id": 350,
      "taxon_ids": [
        611
      ],
      "total_on_hand": 0,
      "meta_title": null,
      "display_price": "$19.99",
      "trends": [

      ],
      "brand": "Ruby on Rails",
      "brand_description": null,
      "has_variants": false,
      "master": {
        "id": 955,
        "name": "Product #9 - 372",
        "sku": "SKU-17",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-9-372",
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
          "taxon_id": 611,
          "position": 1,
          "taxon": {
            "id": 611,
            "name": "Ruby on Rails",
            "pretty_name": "Ruby on Rails",
            "permalink": "ruby-on-rails",
            "parent_id": null,
            "taxonomy_id": 205
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
ETag: W/&quot;1c3bc06cd24e7e176ceca61296fe3c9e&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 70a51eb2-e77c-4f6c-bff3-c94c4132c6e8
X-Runtime: 0.040114
Content-Length: 1074
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
      "id": 549,
      "name": "Product #11 - 979",
      "description": "As seen on TV!",
      "available_on": "2018-07-29T15:54:29.613Z",
      "slug": "product-11-979",
      "meta_description": null,
      "meta_keywords": null,
      "shipping_category_id": 351,
      "taxon_ids": [
        615
      ],
      "total_on_hand": 0,
      "meta_title": null,
      "display_price": "$19.99",
      "trends": [

      ],
      "brand": "Ruby on Rails",
      "brand_description": null,
      "has_variants": false,
      "master": {
        "id": 957,
        "name": "Product #11 - 979",
        "sku": "SKU-19",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-11-979",
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
          "taxon_id": 615,
          "position": 1,
          "taxon": {
            "id": 615,
            "name": "Ruby on Rails",
            "pretty_name": "Ruby on Rails",
            "permalink": "ruby-on-rails",
            "parent_id": null,
            "taxonomy_id": 207
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
GET /api/returns/RA608621425
Authorization: Bearer 749a5ebaaac24c0e76e9445b1ab4c700abcf51d4581d25a8
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
ETag: W/&quot;4368ccc5d302bff99780582a77e88689&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: ec1cd12d-1d26-48b2-887e-dde3e2fc32af
X-Runtime: 0.036981
Content-Length: 2566
200 OK
```


```json
{
  "id": 20,
  "number": "RA608621425",
  "state": "authorized",
  "order_id": 346,
  "memo": "Items were broken",
  "created_at": "2019-07-29T15:54:37.318Z",
  "updated_at": "2019-07-29T15:54:37.318Z",
  "reason": {
    "id": 60,
    "name": "Defect #7",
    "active": true,
    "mutable": true,
    "created_at": "2019-07-29T15:54:37.314Z",
    "updated_at": "2019-07-29T15:54:37.314Z"
  },
  "order": {
    "id": 346,
    "number": "R927291840",
    "item_total": "10.0",
    "total": "110.0",
    "state": "complete",
    "adjustment_total": "0.0",
    "user_id": 411,
    "completed_at": "2019-07-29T15:54:37.261Z",
    "bill_address_id": 729,
    "ship_address_id": 730,
    "payment_total": "110.0",
    "shipment_state": "shipped",
    "payment_state": "paid",
    "email": "email22@example.com",
    "special_instructions": null,
    "created_at": "2019-07-29T15:54:37.207Z",
    "updated_at": "2019-07-29T15:54:37.303Z",
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
    "guest_token": "lrA6BT32H86ci26mn39xbg",
    "canceled_at": null,
    "canceler_id": null,
    "store_id": 378,
    "approver_name": null,
    "frontend_viewable": true
  },
  "ship_address": {
    "id": 730,
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
  "bill_address": {
    "id": 729,
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
  "return_items": [
    {
      "name": "Product #24 - 1321",
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
        "id": 330,
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
Authorization: Bearer 14626d05eda8f30583df191bdfb39c85e294531d0158b3fb
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
ETag: W/&quot;3e1393354b5961e9d7ad8d34f9e09c90&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: fbd69960-24d3-4660-b3b8-1d94e15fe0a2
X-Runtime: 0.014646
Content-Length: 164
200 OK
```


```json
{
  "return_authorizations": [
    {
      "number": "RA305082388",
      "created_at": "2019-07-29T15:54:36.206Z",
      "return_amount": "10.0",
      "order_number": "R436590566",
      "state": "authorized"
    }
  ]
}
```



## returns a 200


### Request

#### Endpoint

```plaintext
GET /api/returns/RA206161573
Authorization: Bearer bf7e3adb0c59dcafbbb7c51ad27e0784290cd3875dce7672
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
ETag: W/&quot;456e717948cdc3a1796acbc2f43b0597&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 3df31251-77d7-4268-974b-b1a28595e0bb
X-Runtime: 0.046645
Content-Length: 2566
200 OK
```


```json
{
  "id": 18,
  "number": "RA206161573",
  "state": "authorized",
  "order_id": 344,
  "memo": "Items were broken",
  "created_at": "2019-07-29T15:54:36.604Z",
  "updated_at": "2019-07-29T15:54:36.604Z",
  "reason": {
    "id": 56,
    "name": "Defect #3",
    "active": true,
    "mutable": true,
    "created_at": "2019-07-29T15:54:36.599Z",
    "updated_at": "2019-07-29T15:54:36.599Z"
  },
  "order": {
    "id": 344,
    "number": "R215819345",
    "item_total": "10.0",
    "total": "110.0",
    "state": "complete",
    "adjustment_total": "0.0",
    "user_id": 408,
    "completed_at": "2019-07-29T15:54:36.530Z",
    "bill_address_id": 725,
    "ship_address_id": 726,
    "payment_total": "110.0",
    "shipment_state": "shipped",
    "payment_state": "paid",
    "email": "email19@example.com",
    "special_instructions": null,
    "created_at": "2019-07-29T15:54:36.467Z",
    "updated_at": "2019-07-29T15:54:36.585Z",
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
    "guest_token": "EzunFMeFKzNWsoYVw91icw",
    "canceled_at": null,
    "canceler_id": null,
    "store_id": 376,
    "approver_name": null,
    "frontend_viewable": true
  },
  "ship_address": {
    "id": 726,
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
  "bill_address": {
    "id": 725,
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
  "return_items": [
    {
      "name": "Product #22 - 2198",
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
        "id": 326,
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
GET /api/returns/RA004758447
Authorization: Bearer f2b30a5f4cf91c0f9e3f3c7af546da590ad01aa6285419fa
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
X-Request-Id: 33b02e56-9ad9-460f-9f18-cc002c5d656a
X-Runtime: 0.007356
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
Authorization: Bearer 49c2e49eb29f82de34106596c1328b3d829c8a6e8f3d5bbc
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
ETag: W/&quot;0ae46c31ff254ebc09a8d115a5007eeb&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 7889cbd5-b191-47e5-a841-fd9a384d9b53
X-Runtime: 0.030880
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
      "created_at": "2019-07-29T15:54:30.262Z"
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
Authorization: Bearer b7f3a441156d4e47395b64db5db0411405c67ece188b1329
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
Authorization: Bearer b7f3a441156d4e47395b64db5db0411405c67ece188b1329
ETag: W/&quot;f1f5537ae4021fabb59edc17cc310fa8&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 680c9c12-6863-432d-94b4-2fafd1639ad2
X-Runtime: 0.121636
Content-Length: 124
200 OK
```


```json
{
  "email": "email1@example.com",
  "first_name": null,
  "last_name": null,
  "id": 389,
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
Authorization: Bearer 4bd7b807fc2e3ba77db5c832eb3c841405be34e72449b0bc
ETag: W/&quot;77c3670858802b1dedb871faa41ef5b1&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 5db9a8bc-4338-45f7-bff7-1d8380a4269b
X-Runtime: 0.005300
Content-Length: 551
200 OK
```


```json
{
  "id": 391,
  "email": "email2@example.com",
  "persistence_token": null,
  "perishable_token": null,
  "last_request_at": null,
  "login": "email2@example.com",
  "ship_address_id": null,
  "bill_address_id": null,
  "created_at": "2019-07-29T15:54:25.557Z",
  "updated_at": "2019-07-29T15:54:25.561Z",
  "spree_api_key": "4bd7b807fc2e3ba77db5c832eb3c841405be34e72449b0bc",
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
Authorization: Bearer c05db90b3eaee2ea56e8f8e5dcbe41b0929c5c718f89e62d
ETag: W/&quot;b719c293df86d49ad038ee13115b12c7&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: fa09089f-33b8-417a-b551-f6891157e2c4
X-Runtime: 0.053695
Content-Length: 157
201 Created
```


```json
{
  "id": 390,
  "email": "test@example.com",
  "created_at": "2019-07-29T15:54:25.536Z",
  "updated_at": "2019-07-29T15:54:25.538Z",
  "bill_address": null,
  "ship_address": null
}
```



# Variant



## Fetching a variant


### Request

#### Endpoint

```plaintext
GET /api/variants/981
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
ETag: W/&quot;e14563f0b4cdb4e638eca8ce67b5ce67&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 5ce9c137-81ce-45aa-9f90-d05a791ff9ea
X-Runtime: 0.102926
Content-Length: 1458
200 OK
```


```json
{
  "id": 981,
  "name": "Product #25 - 7393",
  "sku": "SKU-42",
  "weight": "0.0",
  "height": null,
  "width": null,
  "depth": null,
  "is_master": false,
  "slug": "product-25-7393",
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
      "id": 432,
      "name": "Size-18",
      "presentation": "S",
      "option_type_name": "foo-size-18",
      "option_type_id": 432,
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
      "attachment_updated_at": "2019-07-29T15:54:37.691Z",
      "attachment_width": 489,
      "attachment_height": 490,
      "alt": null,
      "viewable_type": "Spree::Variant",
      "viewable_id": 981,
      "mini_url": "/spree/products/2/mini/thinking-cat.jpg?1564415677",
      "small_url": "/spree/products/2/small/thinking-cat.jpg?1564415677",
      "product_url": "/spree/products/2/product/thinking-cat.jpg?1564415677",
      "large_url": "/spree/products/2/large/thinking-cat.jpg?1564415677"
    }
  ],
  "variant_properties": [

  ],
  "stock_items": [

  ],
  "prices": [
    {
      "id": 1906,
      "vendor_id": 2980,
      "price": "10.0",
      "original_price": "10.0",
      "discount_percent": 0.0,
      "total_on_hand": 0,
      "country_iso": null,
      "final_sale": false,
      "on_sale": false
    },
    {
      "id": 1907,
      "vendor_id": 2981,
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
Authorization: Bearer 6236dab9d5ed8214cab9717041f9ea0cf58d9cf14f553aac
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
ETag: W/&quot;aa1b8a94177abdf0941ca49c0e830598&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 438439f3-1ffe-4ca1-a625-64ff3adbb5f5
X-Runtime: 0.012752
Content-Length: 199
200 OK
```


```json
[
  {
    "id": 33,
    "user_id": 414,
    "payment_source_type": "SolidusPaypalBraintree::Source",
    "payment_source_id": 56,
    "default": false,
    "created_at": "2019-07-29T15:54:37.469Z",
    "updated_at": "2019-07-29T15:54:37.469Z"
  }
]
```



## Remove the payment from the user wallet


### Request

#### Endpoint

```plaintext
DELETE /api/wallet_payment_sources/32
Accept: application/json
Authorization: Bearer 21b98ea37c5a1fb750d0c70529350c1db5048a6455fae4b5
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
X-Request-Id: f11b34a6-db0f-470e-8b5e-f6eb8983a553
X-Runtime: 0.029859
204 No Content
```




## Set a wallet payment source as the default user payment method


### Request

#### Endpoint

```plaintext
POST /api/wallet_payment_sources/34/default
Accept: application/json
Authorization: Bearer f9e2e3b37e0c53177a3dd6b6131c5ef78051eb5e74a7d1bb
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
X-Request-Id: d9fe0111-98c3-44c1-a949-f51c9a574bf6
X-Runtime: 0.010442
204 No Content
```




