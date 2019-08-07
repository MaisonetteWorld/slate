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
PUT /api/orders/R050883285/addresses/1183
Accept: application/json
X-Spree-Order-Token: DxTqrryptZDCo8a47Mz3Xg
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
ETag: W/&quot;072ce1702a1edeaba40c1bf562f94d83&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 8eb96378-8594-46aa-af5e-71f1186aff6a
X-Runtime: 0.090409
Content-Length: 514
200 OK
```


```json
{
  "id": 1184,
  "firstname": "John the Tester",
  "lastname": null,
  "full_name": "John the Tester",
  "address1": "A Different Road",
  "address2": "Northwest",
  "city": "Herndon",
  "zipcode": "10034",
  "phone": "555-555-0199",
  "company": "Company",
  "alternative_phone": "555-555-0199",
  "country_id": 564,
  "country_iso": "US",
  "state_id": 553,
  "state_name": null,
  "state_text": "AL",
  "country": {
    "id": 564,
    "iso_name": "UNITED STATES",
    "iso": "US",
    "iso3": "USA",
    "name": "United States",
    "numcode": 840
  },
  "state": {
    "id": 553,
    "name": "Alabama",
    "abbr": "AL",
    "country_id": 564
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
X-Spree-Order-Token: wDr0uSJgKooviqsMV8KC3Q
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/braintree/transactions`

#### Parameters


```json
order_id=R367060717&payment_method_id=466&options[restart_checkout]=true&transaction[email]=maryellen.oga%40mckenziemcglynn.com&transaction[nonce]=fake-paypal-billing-agreement-nonce&transaction[phone]=555-555-0199&transaction[address_attributes][first_name]=John&transaction[address_attributes][last_name]=Stamm&transaction[address_attributes][address_line_1]=A+Different+Road&transaction[address_attributes][city]=Herndon&transaction[address_attributes][state_code]=AL&transaction[address_attributes][zip]=10035&transaction[address_attributes][country_code]=US&transaction[payment_type]=PayPalAccount
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
ETag: W/&quot;7164e5f5718c62f1c50e1ae4f42b6b28&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 04b07393-709d-4277-b4a4-95d186f64e3b
X-Runtime: 0.315839
Content-Length: 4695
200 OK
```


```json
{
  "id": 569,
  "number": "R367060717",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2019-08-07T13:20:13.789Z",
  "updated_at": "2019-08-07T13:20:14.077Z",
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
  "token": "wDr0uSJgKooviqsMV8KC3Q",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 466,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 1187,
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
    "country_id": 565,
    "country_iso": "US",
    "state_id": 554,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 565,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 554,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 565
    }
  },
  "ship_address": {
    "id": 1187,
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
    "country_id": 565,
    "country_iso": "US",
    "state_id": 554,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 565,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 554,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 565
    }
  },
  "line_items": [
    {
      "id": 482,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 1358,
      "vendor_id": 3925,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 1358,
        "name": "Product #26 - 3892",
        "sku": "SKU-44",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-26-3892",
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
        "product_id": 826,
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
      "id": 221,
      "source_type": "SolidusPaypalBraintree::Source",
      "source_id": 74,
      "amount": "110.0",
      "display_amount": "$110.00",
      "payment_method_id": 466,
      "state": "checkout",
      "avs_response": null,
      "created_at": "2019-08-07T13:20:13.902Z",
      "updated_at": "2019-08-07T13:20:13.902Z",
      "payment_method": {
        "id": 466,
        "name": "Braintree"
      },
      "source": {
        "id": 74,
        "payment_type": "PayPalAccount",
        "token": "bgx899",
        "created_at": "2019-08-07T13:20:13.900Z",
        "email": "jane.doe@paypal.com"
      }
    }
  ],
  "shipments": [
    {
      "id": 408,
      "tracking": null,
      "tracking_url": null,
      "number": "H26045656424",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R367060717",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 379,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 373,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 379,
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
              "id": 515,
              "name": "ShippingCategory #22"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 1358,
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
X-Spree-Order-Token: vs14SQtRv-xeCbLD0Gsu2Q
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/braintree/transactions`

#### Parameters


```json
order_id=R959926663&payment_method_id=467&options[restart_checkout]=true&transaction[email]=maryellen.oga%40mckenziemcglynn.com&transaction[nonce]=fake-apple-pay-visa-nonce&transaction[phone]=555-555-0199&transaction[address_attributes][first_name]=John&transaction[address_attributes][last_name]=Stamm&transaction[address_attributes][address_line_1]=A+Different+Road&transaction[address_attributes][city]=Herndon&transaction[address_attributes][state_code]=AL&transaction[address_attributes][zip]=10037&transaction[address_attributes][country_code]=US&transaction[payment_type]=ApplePayCard
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
ETag: W/&quot;813998da4acb68d539b7ff33cb8d0850&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: cecc5d20-69a0-4d14-8da4-ed387b221eb3
X-Runtime: 0.228807
Content-Length: 4741
200 OK
```


```json
{
  "id": 570,
  "number": "R959926663",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2019-08-07T13:20:14.441Z",
  "updated_at": "2019-08-07T13:20:14.664Z",
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
  "token": "vs14SQtRv-xeCbLD0Gsu2Q",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 467,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 1190,
    "firstname": "John",
    "lastname": "Stamm",
    "full_name": "John Stamm",
    "address1": "A Different Road",
    "address2": null,
    "city": "Herndon",
    "zipcode": "10037",
    "phone": "555-555-0199",
    "company": null,
    "alternative_phone": null,
    "country_id": 566,
    "country_iso": "US",
    "state_id": 555,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 566,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 555,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 566
    }
  },
  "ship_address": {
    "id": 1190,
    "firstname": "John",
    "lastname": "Stamm",
    "full_name": "John Stamm",
    "address1": "A Different Road",
    "address2": null,
    "city": "Herndon",
    "zipcode": "10037",
    "phone": "555-555-0199",
    "company": null,
    "alternative_phone": null,
    "country_id": 566,
    "country_iso": "US",
    "state_id": 555,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 566,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 555,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 566
    }
  },
  "line_items": [
    {
      "id": 483,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 1360,
      "vendor_id": 3931,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 1360,
        "name": "Product #27 - 3801",
        "sku": "SKU-46",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-27-3801",
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
        "product_id": 827,
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
      "source_id": 75,
      "amount": "110.0",
      "display_amount": "$110.00",
      "payment_method_id": 467,
      "state": "checkout",
      "avs_response": null,
      "created_at": "2019-08-07T13:20:14.538Z",
      "updated_at": "2019-08-07T13:20:14.538Z",
      "payment_method": {
        "id": 467,
        "name": "Braintree"
      },
      "source": {
        "id": 75,
        "payment_type": "ApplePayCard",
        "token": "cg7hsk",
        "created_at": "2019-08-07T13:20:14.537Z",
        "cc_type": "Apple Pay - Visa",
        "last_digits": "1881",
        "month": "12",
        "year": "2020"
      }
    }
  ],
  "shipments": [
    {
      "id": 410,
      "tracking": null,
      "tracking_url": null,
      "number": "H24683340677",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R959926663",
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
              "id": 516,
              "name": "ShippingCategory #23"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 1360,
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
PUT /api/checkouts/R793122290/complete
Accept: application/json
X-Spree-Order-Token: SIuH-1pE-wkrmrIa30pKMg
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
ETag: W/&quot;b7838a58cca6ab7f82458f1891aeaabc&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 89d61554-f7a4-4b1c-9acd-845da114b0fc
X-Runtime: 2.509401
Content-Length: 4850
200 OK
```


```json
{
  "id": 553,
  "number": "R793122290",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "complete",
  "adjustment_total": "0.0",
  "user_id": 630,
  "created_at": "2019-08-07T13:19:58.504Z",
  "updated_at": "2019-08-07T13:20:02.403Z",
  "completed_at": "2019-08-07T13:20:02.403Z",
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
  "token": "SIuH-1pE-wkrmrIa30pKMg",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 443,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    },
    {
      "id": 444,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 1150,
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
    "country_id": 542,
    "country_iso": "US",
    "state_id": 531,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 542,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 531,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 542
    }
  },
  "ship_address": {
    "id": 1151,
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
    "country_id": 542,
    "country_iso": "US",
    "state_id": 531,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 542,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 531,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 542
    }
  },
  "line_items": [
    {
      "id": 463,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 1315,
      "vendor_id": 3793,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 1315,
        "name": "Product #1 - 998",
        "sku": "SKU-1",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-1-998",
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
        "product_id": 801,
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
      "source_id": 69,
      "amount": "110.0",
      "display_amount": "$110.00",
      "payment_method_id": 443,
      "state": "completed",
      "avs_response": "M",
      "created_at": "2019-08-07T13:19:58.715Z",
      "updated_at": "2019-08-07T13:20:02.246Z",
      "payment_method": {
        "id": 443,
        "name": "Braintree"
      },
      "source": {
        "id": 69,
        "payment_type": "CreditCard",
        "token": "9whb59",
        "created_at": "2019-08-07T13:19:58.714Z",
        "cc_type": "Visa",
        "last_digits": "1881",
        "month": "12",
        "year": "2020"
      }
    }
  ],
  "shipments": [
    {
      "id": 388,
      "tracking": "U10000",
      "tracking_url": null,
      "number": "H11342747507",
      "cost": "100.0",
      "shipped_at": null,
      "state": "ready",
      "order_id": "R793122290",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 359,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 358,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 359,
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
              "id": 494,
              "name": "ShippingCategory #1"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 1315,
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
PATCH /api/checkouts/R600876294
Accept: application/json
X-Spree-Order-Token: YowN3nX1OiKLKVqt0DimxQ
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=447&order[payment_attributes][][source_attributes][nonce]=fake-apple-pay-visa-nonce&order[payment_attributes][][source_attributes][payment_type]=ApplePayCard
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
ETag: W/&quot;8707278ff30ec5f11b9b1eafd9f832f9&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 202e0f04-b911-4236-b572-6ef5d035cdd1
X-Runtime: 0.101406
Content-Length: 4250
200 OK
```


```json
{
  "id": 556,
  "number": "R600876294",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 633,
  "created_at": "2019-08-07T13:20:04.482Z",
  "updated_at": "2019-08-07T13:20:04.726Z",
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
  "token": "YowN3nX1OiKLKVqt0DimxQ",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 447,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 1156,
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
    "country_id": 545,
    "country_iso": "US",
    "state_id": 534,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 545,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 534,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 545
    }
  },
  "ship_address": {
    "id": 1157,
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
    "country_id": 545,
    "country_iso": "US",
    "state_id": 534,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 545,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 534,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 545
    }
  },
  "line_items": [
    {
      "id": 466,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 1321,
      "vendor_id": 3811,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 1321,
        "name": "Product #4 - 6597",
        "sku": "SKU-7",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-4-6597",
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
        "product_id": 804,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
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
      "id": 394,
      "tracking": null,
      "tracking_url": null,
      "number": "H75884468343",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R600876294",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 365,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 361,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 365,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 361,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 361,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 238,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 497,
              "name": "ShippingCategory #4"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 1321,
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
PATCH /api/checkouts/R800936980
Accept: application/json
X-Spree-Order-Token: Q-vE2aDj0p4F0T1IY65A7Q
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=448&order[payment_attributes][][source_attributes][nonce]=fake-paypal-billing-agreement-nonce&order[payment_attributes][][source_attributes][payment_type]=PayPalAccount
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
ETag: W/&quot;3ed370b7847f35087425c8b1b67befce&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: c9f479eb-1389-4756-8ba3-8bb71e3d8b5b
X-Runtime: 0.099989
Content-Length: 4250
200 OK
```


```json
{
  "id": 557,
  "number": "R800936980",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 634,
  "created_at": "2019-08-07T13:20:05.018Z",
  "updated_at": "2019-08-07T13:20:05.250Z",
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
  "token": "Q-vE2aDj0p4F0T1IY65A7Q",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 448,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 1158,
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
    "country_id": 546,
    "country_iso": "US",
    "state_id": 535,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 546,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 535,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 546
    }
  },
  "ship_address": {
    "id": 1159,
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
    "country_id": 546,
    "country_iso": "US",
    "state_id": 535,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 546,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 535,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 546
    }
  },
  "line_items": [
    {
      "id": 467,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 1323,
      "vendor_id": 3817,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 1323,
        "name": "Product #5 - 5414",
        "sku": "SKU-9",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-5-5414",
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
            "id": 594,
            "name": "Size-5",
            "presentation": "S",
            "option_type_name": "foo-size-5",
            "option_type_id": 531,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 805,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
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
      "id": 396,
      "tracking": null,
      "tracking_url": null,
      "number": "H03005814302",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R800936980",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 367,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 362,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 367,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 362,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 362,
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
              "id": 498,
              "name": "ShippingCategory #5"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 1323,
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
PATCH /api/checkouts/R024390329
Accept: application/json
X-Spree-Order-Token: bSbuQ4tsKUBJ3DJtBchTGA
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=446&order[payment_attributes][][source_attributes][nonce]=fake-valid-visa-nonce&order[payment_attributes][][source_attributes][payment_type]=CreditCard
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
ETag: W/&quot;06398c667a5ab413fa2730901d52c31a&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 51e7d440-1877-45c8-9d07-cc7231590f44
X-Runtime: 0.102784
Content-Length: 4250
200 OK
```


```json
{
  "id": 555,
  "number": "R024390329",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 632,
  "created_at": "2019-08-07T13:20:03.937Z",
  "updated_at": "2019-08-07T13:20:04.137Z",
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
  "token": "bSbuQ4tsKUBJ3DJtBchTGA",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 446,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 1154,
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
    "country_id": 544,
    "country_iso": "US",
    "state_id": 533,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 544,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 533,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 544
    }
  },
  "ship_address": {
    "id": 1155,
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
    "country_id": 544,
    "country_iso": "US",
    "state_id": 533,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 544,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 533,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 544
    }
  },
  "line_items": [
    {
      "id": 465,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 1319,
      "vendor_id": 3805,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 1319,
        "name": "Product #3 - 3079",
        "sku": "SKU-5",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-3-3079",
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
            "id": 592,
            "name": "Size-3",
            "presentation": "S",
            "option_type_name": "foo-size-3",
            "option_type_id": 529,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 803,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
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
      "id": 392,
      "tracking": null,
      "tracking_url": null,
      "number": "H18646703434",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R024390329",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 363,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 360,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 363,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 360,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 360,
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
              "id": 496,
              "name": "ShippingCategory #3"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 1319,
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
PATCH /api/checkouts/R652825701
Accept: application/json
X-Spree-Order-Token: _awcqsp2VlSlKnr9Omlh0A
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=445&order[payment_attributes][][source_attributes][wallet_payment_source_id]=43
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
ETag: W/&quot;4623e5ad490973b2ab1470c83d6fc440&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 78b514f4-06bf-4a10-bb1e-d1879d02999b
X-Runtime: 0.125426
Content-Length: 4249
200 OK
```


```json
{
  "id": 554,
  "number": "R652825701",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 631,
  "created_at": "2019-08-07T13:20:03.282Z",
  "updated_at": "2019-08-07T13:20:03.614Z",
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
  "token": "_awcqsp2VlSlKnr9Omlh0A",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 445,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 1152,
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
    "country_id": 543,
    "country_iso": "US",
    "state_id": 532,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 543,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 532,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 543
    }
  },
  "ship_address": {
    "id": 1153,
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
    "country_id": 543,
    "country_iso": "US",
    "state_id": 532,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 543,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 532,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 543
    }
  },
  "line_items": [
    {
      "id": 464,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 1317,
      "vendor_id": 3799,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 1317,
        "name": "Product #2 - 3472",
        "sku": "SKU-3",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-2-3472",
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
        "product_id": 802,
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

  ],
  "shipments": [
    {
      "id": 390,
      "tracking": null,
      "tracking_url": null,
      "number": "H63646555471",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R652825701",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 361,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 359,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 361,
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
              "id": 495,
              "name": "ShippingCategory #2"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 1317,
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
POST /api/orders/R632650141/line_items
Accept: application/json
X-Spree-Order-Token: 5fzC38ZUD6SEq33pPG8Q7w
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/:order_number/line_items`

#### Parameters


```json
line_item[variant_id]=1331&line_item[options][vendor_id]=3838
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
ETag: W/&quot;37986bf6bfdb7cc78f389d3a59866b31&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: cd9b3ed6-5d85-4c13-8fcc-fefb33264de3
X-Runtime: 0.110114
Content-Length: 849
201 Created
```


```json
{
  "id": 469,
  "quantity": 1,
  "price": "19.99",
  "variant_id": 1331,
  "vendor_id": 3838,
  "single_display_amount": "$19.99",
  "display_amount": "$19.99",
  "total": "19.99",
  "final_sale": false,
  "backordered": null,
  "promotionable": true,
  "variant": {
    "id": 1331,
    "name": "Product #9 - 6105",
    "sku": "SKU-17",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": false,
    "slug": "product-9-6105",
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
        "id": 598,
        "name": "Size-9",
        "presentation": "S",
        "option_type_name": "foo-size-9",
        "option_type_id": 535,
        "option_type_presentation": "Size"
      }
    ],
    "images": [

    ],
    "product_id": 809,
    "brand": null,
    "brand_slug": null,
    "brand_description": null
  },
  "vendor_name": "Vendor #40",
  "adjustments": [

  ]
}
```



## Deleting a line item


### Request

#### Endpoint

```plaintext
DELETE /api/orders/R302858866/line_items/471
Accept: application/json
X-Spree-Order-Token: 3NhNVayrLqvxn8n3Xdd1Aw
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
X-Request-Id: 0fd320af-251d-4707-96d3-30fc4bd2c733
X-Runtime: 0.054391
204 No Content
```




## Updating a line item


### Request

#### Endpoint

```plaintext
PUT /api/orders/R374754596/line_items/470
Accept: application/json
X-Spree-Order-Token: whNwifoFjL4KiuIOpnCzIQ
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
ETag: W/&quot;a66484fd57d6a3f30b4b3352ebc38912&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: b2282f26-987a-4f01-96b5-097ecf335d24
X-Runtime: 0.172051
Content-Length: 848
200 OK
```


```json
{
  "id": 470,
  "quantity": 2,
  "price": "10.0",
  "variant_id": 1333,
  "vendor_id": 3843,
  "single_display_amount": "$10.00",
  "display_amount": "$20.00",
  "total": "20.0",
  "final_sale": false,
  "backordered": null,
  "promotionable": true,
  "variant": {
    "id": 1333,
    "name": "Product #10 - 341",
    "sku": "SKU-19",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": false,
    "slug": "product-10-341",
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
        "id": 599,
        "name": "Size-10",
        "presentation": "S",
        "option_type_name": "foo-size-10",
        "option_type_id": 536,
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
  "vendor_name": "Vendor #45",
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
ETag: W/&quot;fb05cae6e640307713db50403f9e237b&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: f6597502-c933-48a9-9293-0ea1d1407413
X-Runtime: 0.010289
Content-Length: 134
200 OK
```


```json
[
  {
    "id": 758,
    "name": "Kids",
    "navigation_url": "/navigation/kids",
    "parent_id": 757,
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
Authorization: Bearer 47b4d6f30da4751a8aec1e7508904eaff3bdcdc79194ab67
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
ETag: W/&quot;32ce1bb42aa325d840fe9e4f8e6bb1c8&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 3ae9f513-ed58-464c-ae67-ce212530918c
X-Runtime: 0.036767
Content-Length: 305
200 OK
```


```json
{
  "orders": [
    {
      "number": "R422695084",
      "completed_at": "2019-08-07T13:20:13.225Z",
      "total": "120.0",
      "state": "Complete",
      "shipment_state": "shipped",
      "shipments": [
        {
          "number": "H51152660367",
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
GET /api/orders/R396340323
Accept: application/json
Authorization: Bearer d2fd1e9a8ae69a909b0fc2a1f0cdd0714d74c8bbb0c6fad5
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
ETag: W/&quot;b9aa8b63aec260747c7c5cdd282f466c&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 70d886ee-a1d0-4c70-8f4d-aee4bc012573
X-Runtime: 0.230384
Content-Length: 9256
200 OK
```


```json
{
  "id": 566,
  "number": "R396340323",
  "item_total": "20.0",
  "total": "120.0",
  "ship_total": "100.0",
  "state": "complete",
  "adjustment_total": "0.0",
  "user_id": 654,
  "created_at": "2019-08-07T13:20:12.207Z",
  "updated_at": "2019-08-07T13:20:12.506Z",
  "completed_at": "2019-08-07T13:20:12.292Z",
  "payment_total": "120.0",
  "shipment_state": "shipped",
  "payment_state": "paid",
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
  "token": "DcdjzyH9WvO6fTUZ6eY14w",
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
      "name": "Credit Card",
      "partial_name": "gateway",
      "method_type": "gateway"
    },
    {
      "id": 463,
      "name": "Credit Card",
      "partial_name": "gateway",
      "method_type": "gateway"
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
    "zipcode": "10029",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 562,
    "country_iso": "US",
    "state_id": 551,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 562,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 551,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 562
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
    "zipcode": "10030",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 562,
    "country_iso": "US",
    "state_id": 551,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 562,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 551,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 562
    }
  },
  "line_items": [
    {
      "id": 478,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 1354,
      "vendor_id": 3913,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 1354,
        "name": "Product #24 - 9300",
        "sku": "SKU-40",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-24-9300",
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
        "product_id": 824,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #103",
      "adjustments": [
        {
          "id": 95,
          "source_type": "Spree::TaxRate",
          "source_id": 17,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 478,
          "amount": "2.0",
          "label": "VAT 5%",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-08-07T13:20:12.458Z",
          "updated_at": "2019-08-07T13:20:12.474Z",
          "display_amount": "$2.00"
        },
        {
          "id": 89,
          "source_type": "Spree::PromotionAction",
          "source_id": 39,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 478,
          "amount": "5.0",
          "label": "foo",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-08-07T13:20:12.385Z",
          "updated_at": "2019-08-07T13:20:12.385Z",
          "display_amount": "$5.00"
        },
        {
          "id": 88,
          "source_type": "Spree::PromotionAction",
          "source_id": 39,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 478,
          "amount": "5.0",
          "label": "foo",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-08-07T13:20:12.372Z",
          "updated_at": "2019-08-07T13:20:12.372Z",
          "display_amount": "$5.00"
        }
      ]
    },
    {
      "id": 479,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 1354,
      "vendor_id": 3913,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 1354,
        "name": "Product #24 - 9300",
        "sku": "SKU-40",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-24-9300",
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
        "product_id": 824,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #103",
      "adjustments": [
        {
          "id": 96,
          "source_type": "Spree::TaxRate",
          "source_id": 18,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 479,
          "amount": "1.5",
          "label": "VAT 5%",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-08-07T13:20:12.501Z",
          "updated_at": "2019-08-07T13:20:12.519Z",
          "display_amount": "$1.50"
        },
        {
          "id": 90,
          "source_type": "Spree::PromotionAction",
          "source_id": 39,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 479,
          "amount": "5.0",
          "label": "bar",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-08-07T13:20:12.398Z",
          "updated_at": "2019-08-07T13:20:12.398Z",
          "display_amount": "$5.00"
        }
      ]
    }
  ],
  "payments": [
    {
      "id": 219,
      "source_type": "Spree::CreditCard",
      "source_id": 190,
      "amount": "120.0",
      "display_amount": "$120.00",
      "payment_method_id": 462,
      "state": "completed",
      "avs_response": null,
      "created_at": "2019-08-07T13:20:12.316Z",
      "updated_at": "2019-08-07T13:20:12.316Z",
      "payment_method": {
        "id": 462,
        "name": "Credit Card"
      },
      "source": {
        "id": 190,
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
      "id": 405,
      "tracking": "U10000",
      "tracking_url": null,
      "number": "H66885781426",
      "cost": "100.0",
      "shipped_at": "2019-08-07T13:20:12.343Z",
      "state": "shipped",
      "order_id": "R396340323",
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
              "id": 250,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 513,
              "name": "ShippingCategory #20"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 1354,
          "quantity": 1,
          "states": {
            "shipped": 1
          }
        },
        {
          "variant_id": 1354,
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
          "adjustable_id": 405,
          "amount": "-10.0",
          "label": "Shipping",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-08-07T13:20:12.424Z",
          "updated_at": "2019-08-07T13:20:12.424Z",
          "display_amount": "-$10.00"
        },
        {
          "id": 91,
          "source_type": "Spree::PromotionAction",
          "source_id": 39,
          "adjustable_type": "Spree::Shipment",
          "adjustable_id": 405,
          "amount": "-9.99",
          "label": "Shipping",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-08-07T13:20:12.411Z",
          "updated_at": "2019-08-07T13:20:12.411Z",
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
      "adjustable_id": 566,
      "amount": "20.0",
      "label": "adj1",
      "promotion_code_id": null,
      "finalized": false,
      "eligible": true,
      "created_at": "2019-08-07T13:20:12.432Z",
      "updated_at": "2019-08-07T13:20:12.432Z",
      "display_amount": "$20.00"
    },
    {
      "id": 94,
      "source_type": "Spree::Promotion",
      "source_id": 57,
      "adjustable_type": "Spree::Order",
      "adjustable_id": 566,
      "amount": "30.0",
      "label": "adj2",
      "promotion_code_id": null,
      "finalized": false,
      "eligible": true,
      "created_at": "2019-08-07T13:20:12.438Z",
      "updated_at": "2019-08-07T13:20:12.438Z",
      "display_amount": "$30.00"
    }
  ],
  "permissions": {
    "can_update": false
  },
  "credit_cards": [
    {
      "id": 190,
      "month": "12",
      "year": "2020",
      "cc_type": null,
      "last_digits": "1111",
      "name": "Spree Commerce",
      "address": {
        "id": 1178,
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
        "country_id": 562,
        "country_iso": "US",
        "state_id": 551,
        "state_name": null,
        "state_text": "AL",
        "country": {
          "id": 562,
          "iso_name": "UNITED STATES",
          "iso": "US",
          "iso3": "USA",
          "name": "United States",
          "numcode": 840
        },
        "state": {
          "id": 551,
          "name": "Alabama",
          "abbr": "AL",
          "country_id": 562
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
GET /api/orders/R959571963
Accept: application/json
Authorization: 8d143d24e60b0f0df9c715b34c3c7546c1d022fea6affa6a
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
X-Request-Id: 3c00c56f-4fd4-449d-8504-88ca08b4dccc
X-Runtime: 0.028373
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
user[email]=email22%40example.com
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
X-Request-Id: 195704cb-32d7-4617-8b1c-1aedaaadcfdd
X-Runtime: 0.021531
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
user[email]=email23%40example.com&user[password]=secret
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
Authorization: Bearer da9372a0aea6a586d7c02dc8b85c9899c710b2eb4deaceda
ETag: W/&quot;44c77da34597e888e69b580fa99850d7&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 9bd9bc6e-1749-477f-b054-7286b53df2c3
X-Runtime: 0.004855
Content-Length: 553
200 OK
```


```json
{
  "id": 650,
  "email": "email23@example.com",
  "persistence_token": null,
  "perishable_token": null,
  "last_request_at": null,
  "login": "email23@example.com",
  "ship_address_id": null,
  "bill_address_id": null,
  "created_at": "2019-08-07T13:20:09.871Z",
  "updated_at": "2019-08-07T13:20:09.873Z",
  "spree_api_key": "da9372a0aea6a586d7c02dc8b85c9899c710b2eb4deaceda",
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
X-Request-Id: ef5c4185-c7d8-4cff-991f-d248a09e7d31
X-Runtime: 0.003382
204 No Content
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
Date: Wed, 07 Aug 2019 13:20:11 GMT
Surrogate-Control: max-age=900
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;0967c95da08b10195cf09ff7135fa789&quot;
X-Request-Id: fec2fdb6-bfe4-40a2-9b91-5d5b19eaa016
X-Runtime: 0.049329
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
      "id": 822,
      "name": "Product #22 - 1504",
      "description": "As seen on TV!",
      "available_on": "2018-08-07T13:20:11.116Z",
      "slug": "product-22-1504",
      "meta_description": null,
      "meta_keywords": null,
      "shipping_category_id": 511,
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
        "id": 1350,
        "name": "Product #22 - 1504",
        "sku": "SKU-37",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-22-1504",
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
GET /api/products/product-16-5844
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
Date: Wed, 07 Aug 2019 13:20:10 GMT
Surrogate-Control: max-age=900
Surrogate-Key: product_id=1
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;6bd28d06051de9c07d618d81ec5cdb24&quot;
X-Request-Id: c5694b8e-c05a-4a12-b7f3-03873fc29e06
X-Runtime: 0.086575
Content-Length: 836
200 OK
```


```json
{
  "id": 816,
  "name": "Product #16 - 5844",
  "description": "As seen on TV!",
  "available_on": "2018-08-07T13:20:09.899Z",
  "slug": "product-16-5844",
  "meta_description": null,
  "meta_keywords": null,
  "shipping_category_id": 507,
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
    "id": 1344,
    "name": "Product #16 - 5844",
    "sku": "SKU-31",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": true,
    "slug": "product-16-5844",
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
X-Request-Id: 1a73aefe-504c-4624-a3c7-703f71e7096b
X-Runtime: 0.019706
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
ETag: W/&quot;e604ff7b2a9b6130f5cfc4688022ffdd&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: ace8daeb-c376-4beb-999b-ffa4d9b37c5c
X-Runtime: 0.096041
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
      "id": 818,
      "name": "Product #18 - 5747",
      "description": "As seen on TV!",
      "available_on": "2018-08-07T13:20:10.267Z",
      "slug": "product-18-5747",
      "meta_description": null,
      "meta_keywords": null,
      "shipping_category_id": 509,
      "taxon_ids": [
        760
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
        "id": 1346,
        "name": "Product #18 - 5747",
        "sku": "SKU-33",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-18-5747",
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
          "taxon_id": 760,
          "position": 1,
          "taxon": {
            "id": 760,
            "name": "Ruby on Rails",
            "pretty_name": "Ruby on Rails",
            "permalink": "ruby-on-rails",
            "parent_id": null,
            "taxonomy_id": 338
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
GET /api/taxons/products?id=764
Host: example.org
Cookie: 
```

`GET /api/taxons/products`

#### Parameters


```json
id: 764
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
ETag: W/&quot;e00c6ded89970cf897588b0003b11af0&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: d8b804ef-178c-47ca-96e5-9744ad62c907
X-Runtime: 0.066888
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
      "id": 820,
      "name": "Product #20 - 1127",
      "description": "As seen on TV!",
      "available_on": "2018-08-07T13:20:10.775Z",
      "slug": "product-20-1127",
      "meta_description": null,
      "meta_keywords": null,
      "shipping_category_id": 510,
      "taxon_ids": [
        764
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
        "id": 1348,
        "name": "Product #20 - 1127",
        "sku": "SKU-35",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-20-1127",
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
          "taxon_id": 764,
          "position": 1,
          "taxon": {
            "id": 764,
            "name": "Ruby on Rails",
            "pretty_name": "Ruby on Rails",
            "permalink": "ruby-on-rails",
            "parent_id": null,
            "taxonomy_id": 340
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
GET /api/returns/RA722555200
Authorization: Bearer 05152c0f6d6fbb53098044de583674c49b97d3deea0c6f6d
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
ETag: W/&quot;60d30a0afdf8fc1a1ad2640ac7b418f6&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 583f037e-d746-4262-86eb-b60245127a5c
X-Runtime: 0.049614
Content-Length: 2773
200 OK
```


```json
{
  "id": 20,
  "number": "RA722555200",
  "state": "authorized",
  "order_id": 564,
  "memo": "Items were broken",
  "created_at": "2019-08-07T13:20:09.604Z",
  "updated_at": "2019-08-07T13:20:09.604Z",
  "reason": {
    "id": 62,
    "name": "Defect #7",
    "active": true,
    "mutable": true,
    "created_at": "2019-08-07T13:20:09.599Z",
    "updated_at": "2019-08-07T13:20:09.599Z",
    "mirakl_code": null
  },
  "order": {
    "id": 564,
    "number": "R720857585",
    "item_total": "10.0",
    "total": "110.0",
    "state": "complete",
    "adjustment_total": "0.0",
    "user_id": 645,
    "completed_at": "2019-08-07T13:20:09.510Z",
    "bill_address_id": 1174,
    "ship_address_id": 1175,
    "payment_total": "110.0",
    "shipment_state": "shipped",
    "payment_state": "paid",
    "email": "email18@example.com",
    "special_instructions": null,
    "created_at": "2019-08-07T13:20:09.432Z",
    "updated_at": "2019-08-07T13:20:09.578Z",
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
    "guest_token": "m4GcK1aToWt5UrHuZ3gz-w",
    "canceled_at": null,
    "canceler_id": null,
    "store_id": 603,
    "approver_name": null,
    "frontend_viewable": true
  },
  "ship_address": {
    "id": 1175,
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
  "bill_address": {
    "id": 1174,
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
  "return_items": [
    {
      "name": "Product #15 - 7241",
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
        "id": 458,
        "name": "Credit Card"
      },
      "source": {
        "id": 188,
        "month": "12",
        "year": "2020",
        "cc_type": null,
        "last_digits": "1111",
        "name": "Spree Commerce",
        "gateway_customer_profile_id": "BGS-415551",
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
Authorization: Bearer 9667ef896a308e51046c750ff6e6a4d7cadbd01f868cf276
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
ETag: W/&quot;c694a8cbbbe46a6778d5c574a3a933f7&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: a69dafbc-0195-42c0-9e0e-a7cb7c5eaf3d
X-Runtime: 0.015742
Content-Length: 164
200 OK
```


```json
{
  "return_authorizations": [
    {
      "number": "RA100462688",
      "created_at": "2019-08-07T13:20:08.205Z",
      "return_amount": "10.0",
      "order_number": "R065858336",
      "state": "authorized"
    }
  ]
}
```



## returns a 200


### Request

#### Endpoint

```plaintext
GET /api/returns/RA053180200
Authorization: Bearer 3e10acc48f2f99f307966a9f35a8a5e16e21c021ba662b54
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
ETag: W/&quot;360fd8a83dae34ff332ec136f9fde728&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: e5883e4c-604a-44a9-a2c5-7452ffc1e8d9
X-Runtime: 0.065939
Content-Length: 2696
200 OK
```


```json
{
  "id": 18,
  "number": "RA053180200",
  "state": "authorized",
  "order_id": 562,
  "memo": "Items were broken",
  "created_at": "2019-08-07T13:20:08.626Z",
  "updated_at": "2019-08-07T13:20:08.626Z",
  "reason": {
    "id": 58,
    "name": "Defect #3",
    "active": true,
    "mutable": true,
    "created_at": "2019-08-07T13:20:08.622Z",
    "updated_at": "2019-08-07T13:20:08.622Z",
    "mirakl_code": null
  },
  "order": {
    "id": 562,
    "number": "R426603795",
    "item_total": "10.0",
    "total": "110.0",
    "state": "complete",
    "adjustment_total": "0.0",
    "user_id": 642,
    "completed_at": "2019-08-07T13:20:08.558Z",
    "bill_address_id": 1170,
    "ship_address_id": 1171,
    "payment_total": "110.0",
    "shipment_state": "shipped",
    "payment_state": "paid",
    "email": "email15@example.com",
    "special_instructions": null,
    "created_at": "2019-08-07T13:20:08.498Z",
    "updated_at": "2019-08-07T13:20:08.608Z",
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
    "guest_token": "ST7bY1jarEOIoOkIe3GMFA",
    "canceled_at": null,
    "canceler_id": null,
    "store_id": 601,
    "approver_name": null,
    "frontend_viewable": true
  },
  "ship_address": {
    "id": 1171,
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
  "bill_address": {
    "id": 1170,
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
  "return_items": [
    {
      "name": "Product #13 - 3188",
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
        "id": 454,
        "name": "Credit Card"
      },
      "source": {
        "id": 186,
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
GET /api/returns/RA271446481
Authorization: Bearer 069335b144bcb99d6f986f7460096e8be8dab777b72776ed
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
X-Request-Id: 7a04f01a-da8d-44e7-aac4-8004a24f9bd9
X-Runtime: 0.012711
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
Authorization: Bearer d40cda66e0531b574edadd6c0604f940a6069a046dac2404
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
ETag: W/&quot;48d0849d1673a71f51c9859daaf1cb1d&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 51d1bb8e-8a0d-496f-8524-57fb744ceba6
X-Runtime: 0.039283
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
      "created_at": "2019-08-07T13:20:09.766Z"
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
user[email]=email10%40example.com&user[password]=secret
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
Authorization: Bearer 977e02f242160bb18626b4f48c0f91d5657d7e8435d30ce3
ETag: W/&quot;7f1e1502e9e7ddb3a8e96d750b56d90d&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 73cef0ad-5ee5-4124-a3e4-ad8ebe1c809a
X-Runtime: 0.005554
Content-Length: 553
200 OK
```


```json
{
  "id": 637,
  "email": "email10@example.com",
  "persistence_token": null,
  "perishable_token": null,
  "last_request_at": null,
  "login": "email10@example.com",
  "ship_address_id": null,
  "bill_address_id": null,
  "created_at": "2019-08-07T13:20:06.087Z",
  "updated_at": "2019-08-07T13:20:06.088Z",
  "spree_api_key": "977e02f242160bb18626b4f48c0f91d5657d7e8435d30ce3",
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
Authorization: Bearer 2757c12ee84abf495c655f2a5f822edbcecafbd5fc5ba160
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
Authorization: Bearer 2757c12ee84abf495c655f2a5f822edbcecafbd5fc5ba160
ETag: W/&quot;9f64e1817599a41dc5002199819c59ee&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 86c843ac-5117-49bf-91b3-dc25945d907c
X-Runtime: 0.028849
Content-Length: 1308
200 OK
```


```json
{
  "email": "email9@example.com",
  "first_name": null,
  "last_name": null,
  "id": 636,
  "subscribed": null,
  "addresses": [
    {
      "id": 1161,
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
      "country_id": 548,
      "country_iso": "US",
      "state_id": 537,
      "state_name": null,
      "state_text": "AL",
      "country_name": "United States",
      "default": true
    },
    {
      "id": 1160,
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
      "country_id": 548,
      "country_iso": "US",
      "state_id": 537,
      "state_name": null,
      "state_text": "AL",
      "country_name": "United States",
      "default": false
    }
  ],
  "payment_sources": [
    {
      "default": true,
      "id": 71,
      "payment_type": "CreditCard",
      "token": null,
      "created_at": "2019-08-07T13:20:06.013Z",
      "cc_type": null,
      "last_digits": null,
      "month": null,
      "year": null
    },
    {
      "default": false,
      "id": 72,
      "payment_type": "ApplePayCard",
      "token": null,
      "created_at": "2019-08-07T13:20:06.030Z",
      "cc_type": null,
      "last_digits": null,
      "month": null,
      "year": null
    },
    {
      "default": false,
      "id": 73,
      "payment_type": "PayPalAccount",
      "token": null,
      "created_at": "2019-08-07T13:20:06.048Z",
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
Authorization: Bearer df14084de3d33efb533d0aa52ba2b6341589112f6dbfd0d7
ETag: W/&quot;d2a1700c64e86456f448d296eec7a506&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 288b4817-a75f-4c10-b364-3bf582e6312f
X-Runtime: 0.028751
Content-Length: 157
201 Created
```


```json
{
  "id": 635,
  "email": "test@example.com",
  "created_at": "2019-08-07T13:20:05.932Z",
  "updated_at": "2019-08-07T13:20:05.934Z",
  "bill_address": null,
  "ship_address": null
}
```



# Variant



## Fetching a variant


### Request

#### Endpoint

```plaintext
GET /api/variants/1325
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
ETag: W/&quot;07a078b7d9b74fcc157fe19edabea95c&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 945a1885-6324-422e-9f9d-f195d13d8b8e
X-Runtime: 0.093141
Content-Length: 1461
200 OK
```


```json
{
  "id": 1325,
  "name": "Product #6 - 6931",
  "sku": "SKU-11",
  "weight": "0.0",
  "height": null,
  "width": null,
  "depth": null,
  "is_master": false,
  "slug": "product-6-6931",
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
      "id": 595,
      "name": "Size-6",
      "presentation": "S",
      "option_type_name": "foo-size-6",
      "option_type_id": 532,
      "option_type_presentation": "Size"
    }
  ],
  "images": [
    {
      "id": 13,
      "position": 1,
      "attachment_content_type": "image/jpeg",
      "attachment_file_name": "thinking-cat.jpg",
      "type": "Spree::Image",
      "attachment_updated_at": "2019-08-07T13:20:05.538Z",
      "attachment_width": 489,
      "attachment_height": 490,
      "alt": null,
      "viewable_type": "Spree::Variant",
      "viewable_id": 1325,
      "mini_url": "/spree/products/13/mini/thinking-cat.jpg?1565184005",
      "small_url": "/spree/products/13/small/thinking-cat.jpg?1565184005",
      "product_url": "/spree/products/13/product/thinking-cat.jpg?1565184005",
      "large_url": "/spree/products/13/large/thinking-cat.jpg?1565184005"
    }
  ],
  "variant_properties": [

  ],
  "stock_items": [

  ],
  "prices": [
    {
      "id": 2525,
      "vendor_id": 3826,
      "price": "10.0",
      "original_price": "10.0",
      "discount_percent": 0.0,
      "total_on_hand": 0,
      "country_iso": null,
      "final_sale": false,
      "on_sale": false
    },
    {
      "id": 2526,
      "vendor_id": 3827,
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
Authorization: Bearer 53c2a7d6ccb09d81698f11ac2ed2bf9d32dd18fc332c0bb6
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
ETag: W/&quot;0faffeb2a51ec4d79406b5b62268ca06&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: f1b44c57-3be8-4921-a154-45fafa2afb2d
X-Runtime: 0.014998
Content-Length: 199
200 OK
```


```json
[
  {
    "id": 40,
    "user_id": 628,
    "payment_source_type": "SolidusPaypalBraintree::Source",
    "payment_source_id": 67,
    "default": false,
    "created_at": "2019-08-07T13:19:57.756Z",
    "updated_at": "2019-08-07T13:19:57.756Z"
  }
]
```



## Remove the payment from the user wallet


### Request

#### Endpoint

```plaintext
DELETE /api/wallet_payment_sources/41
Accept: application/json
Authorization: Bearer 33dab6844df49acdbbffe921b8feea0396a5fd58bb65a639
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
X-Request-Id: a4e1fb2c-9fed-4132-a8d4-555241a3dc7a
X-Runtime: 0.014294
204 No Content
```




## Set a wallet payment source as the default user payment method


### Request

#### Endpoint

```plaintext
POST /api/wallet_payment_sources/39/default
Accept: application/json
Authorization: Bearer 3b62c4e2063ea3be9ea02e578c8dfb5201dc5f2e2910b0d5
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
X-Request-Id: 9f367bec-5925-4ab4-8ca5-5435871d9404
X-Runtime: 0.117035
204 No Content
```




