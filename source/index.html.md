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
PUT /api/orders/R019965834/addresses/1143
Accept: application/json
X-Spree-Order-Token: XtSw419Jj4hY53-ax15r8A
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
ETag: W/&quot;46d9e625d52c060a2b5afd3442f76c6f&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 0acacc0f-feb3-4990-b2e9-a31b79188f19
X-Runtime: 0.069394
Content-Length: 514
200 OK
```


```json
{
  "id": 1144,
  "firstname": "John the Tester",
  "lastname": null,
  "full_name": "John the Tester",
  "address1": "A Different Road",
  "address2": "Northwest",
  "city": "Herndon",
  "zipcode": "10010",
  "phone": "555-555-0199",
  "company": "Company",
  "alternative_phone": "555-555-0199",
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
}
```



# Braintree transactions



## Creating a PayPal express checkout transaction


### Request

#### Endpoint

```plaintext
POST /api/braintree/transactions
Accept: application/json
X-Spree-Order-Token: 5VewcN21J2ksKpdco074MQ
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/braintree/transactions`

#### Parameters


```json
order_id=R258750894&payment_method_id=457&options[restart_checkout]=true&transaction[email]=maryellen.oga%40mckenziemcglynn.com&transaction[nonce]=fake-paypal-billing-agreement-nonce&transaction[phone]=555-555-0199&transaction[address_attributes][first_name]=John&transaction[address_attributes][last_name]=Stamm&transaction[address_attributes][address_line_1]=A+Different+Road&transaction[address_attributes][city]=Herndon&transaction[address_attributes][state_code]=AL&transaction[address_attributes][zip]=10025&transaction[address_attributes][country_code]=US&transaction[payment_type]=PayPalAccount
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
ETag: W/&quot;87606a1d589f39b3aa75f8e500a809fa&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: dee78f52-5363-412b-8df2-f21317b243d2
X-Runtime: 0.245403
Content-Length: 4694
200 OK
```


```json
{
  "id": 556,
  "number": "R258750894",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2019-08-06T09:27:51.951Z",
  "updated_at": "2019-08-06T09:27:52.174Z",
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
  "token": "5VewcN21J2ksKpdco074MQ",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 457,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 1162,
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
    "country_id": 541,
    "country_iso": "US",
    "state_id": 530,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 541,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 530,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 541
    }
  },
  "ship_address": {
    "id": 1162,
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
    "country_id": 541,
    "country_iso": "US",
    "state_id": 530,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 541,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 530,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 541
    }
  },
  "line_items": [
    {
      "id": 467,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 1312,
      "vendor_id": 3786,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 1312,
        "name": "Product #12 - 7422",
        "sku": "SKU-23",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-12-7422",
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
            "id": 597,
            "name": "Size-12",
            "presentation": "S",
            "option_type_name": "foo-size-12",
            "option_type_id": 534,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 791,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #63",
      "adjustments": [

      ]
    }
  ],
  "payments": [
    {
      "id": 217,
      "source_type": "SolidusPaypalBraintree::Source",
      "source_id": 75,
      "amount": "110.0",
      "display_amount": "$110.00",
      "payment_method_id": 457,
      "state": "checkout",
      "avs_response": null,
      "created_at": "2019-08-06T09:27:52.041Z",
      "updated_at": "2019-08-06T09:27:52.041Z",
      "payment_method": {
        "id": 457,
        "name": "Braintree"
      },
      "source": {
        "id": 75,
        "payment_type": "PayPalAccount",
        "token": "bgx899",
        "created_at": "2019-08-06T09:27:52.040Z",
        "email": "jane.doe@paypal.com"
      }
    }
  ],
  "shipments": [
    {
      "id": 398,
      "tracking": null,
      "tracking_url": null,
      "number": "H55740116360",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R258750894",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 371,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 364,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 371,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 364,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 364,
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
              "id": 491,
              "name": "ShippingCategory #12"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 1312,
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
X-Spree-Order-Token: 5tntxDz_CmkOxjCvYS9LPg
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/braintree/transactions`

#### Parameters


```json
order_id=R403548115&payment_method_id=456&options[restart_checkout]=true&transaction[email]=maryellen.oga%40mckenziemcglynn.com&transaction[nonce]=fake-apple-pay-visa-nonce&transaction[phone]=555-555-0199&transaction[address_attributes][first_name]=John&transaction[address_attributes][last_name]=Stamm&transaction[address_attributes][address_line_1]=A+Different+Road&transaction[address_attributes][city]=Herndon&transaction[address_attributes][state_code]=AL&transaction[address_attributes][zip]=10023&transaction[address_attributes][country_code]=US&transaction[payment_type]=ApplePayCard
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
ETag: W/&quot;2151b00829120a4cca8ddab3858fcaa8&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 036fca62-36f3-4950-9696-bfb9f9b473e3
X-Runtime: 0.257229
Content-Length: 4740
200 OK
```


```json
{
  "id": 555,
  "number": "R403548115",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2019-08-06T09:27:51.417Z",
  "updated_at": "2019-08-06T09:27:51.628Z",
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
  "token": "5tntxDz_CmkOxjCvYS9LPg",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 456,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 1159,
    "firstname": "John",
    "lastname": "Stamm",
    "full_name": "John Stamm",
    "address1": "A Different Road",
    "address2": null,
    "city": "Herndon",
    "zipcode": "10023",
    "phone": "555-555-0199",
    "company": null,
    "alternative_phone": null,
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
  "ship_address": {
    "id": 1159,
    "firstname": "John",
    "lastname": "Stamm",
    "full_name": "John Stamm",
    "address1": "A Different Road",
    "address2": null,
    "city": "Herndon",
    "zipcode": "10023",
    "phone": "555-555-0199",
    "company": null,
    "alternative_phone": null,
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
  "line_items": [
    {
      "id": 466,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 1310,
      "vendor_id": 3780,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 1310,
        "name": "Product #11 - 6422",
        "sku": "SKU-21",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-11-6422",
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
            "id": 596,
            "name": "Size-11",
            "presentation": "S",
            "option_type_name": "foo-size-11",
            "option_type_id": 533,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 790,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #58",
      "adjustments": [

      ]
    }
  ],
  "payments": [
    {
      "id": 216,
      "source_type": "SolidusPaypalBraintree::Source",
      "source_id": 74,
      "amount": "110.0",
      "display_amount": "$110.00",
      "payment_method_id": 456,
      "state": "checkout",
      "avs_response": null,
      "created_at": "2019-08-06T09:27:51.523Z",
      "updated_at": "2019-08-06T09:27:51.523Z",
      "payment_method": {
        "id": 456,
        "name": "Braintree"
      },
      "source": {
        "id": 74,
        "payment_type": "ApplePayCard",
        "token": "cg7hsk",
        "created_at": "2019-08-06T09:27:51.522Z",
        "cc_type": "Apple Pay - Visa",
        "last_digits": "1881",
        "month": "12",
        "year": "2020"
      }
    }
  ],
  "shipments": [
    {
      "id": 396,
      "tracking": null,
      "tracking_url": null,
      "number": "H14302675361",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R403548115",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 369,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 363,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 369,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 363,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 363,
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
              "id": 490,
              "name": "ShippingCategory #11"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 1310,
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
PUT /api/checkouts/R117785164/complete
Accept: application/json
X-Spree-Order-Token: 5hg6J0NJwrWX3B8sYs2YIA
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
ETag: W/&quot;9315f34b0517047568d8f667a05461d7&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 47002cee-3184-4d23-81fb-4689a0f2f54e
X-Runtime: 2.092102
Content-Length: 4860
200 OK
```


```json
{
  "id": 554,
  "number": "R117785164",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "complete",
  "adjustment_total": "0.0",
  "user_id": 641,
  "created_at": "2019-08-06T09:27:47.551Z",
  "updated_at": "2019-08-06T09:27:50.654Z",
  "completed_at": "2019-08-06T09:27:50.654Z",
  "payment_total": "110.0",
  "shipment_state": "ready",
  "payment_state": "paid",
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
  "token": "5hg6J0NJwrWX3B8sYs2YIA",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 454,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    },
    {
      "id": 455,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 1155,
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
    "country_id": 539,
    "country_iso": "US",
    "state_id": 528,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 539,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 528,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 539
    }
  },
  "ship_address": {
    "id": 1156,
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
    "country_id": 539,
    "country_iso": "US",
    "state_id": 528,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 539,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 528,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 539
    }
  },
  "line_items": [
    {
      "id": 465,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 1308,
      "vendor_id": 3774,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 1308,
        "name": "Product #10 - 2553",
        "sku": "SKU-19",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-10-2553",
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
            "id": 595,
            "name": "Size-10",
            "presentation": "S",
            "option_type_name": "foo-size-10",
            "option_type_id": 532,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 789,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #53",
      "adjustments": [

      ]
    }
  ],
  "payments": [
    {
      "id": 215,
      "source_type": "SolidusPaypalBraintree::Source",
      "source_id": 73,
      "amount": "110.0",
      "display_amount": "$110.00",
      "payment_method_id": 454,
      "state": "completed",
      "avs_response": "M",
      "created_at": "2019-08-06T09:27:47.626Z",
      "updated_at": "2019-08-06T09:27:50.524Z",
      "payment_method": {
        "id": 454,
        "name": "Braintree"
      },
      "source": {
        "id": 73,
        "payment_type": "CreditCard",
        "token": "93txj5",
        "created_at": "2019-08-06T09:27:47.625Z",
        "cc_type": "Visa",
        "last_digits": "1881",
        "month": "12",
        "year": "2020"
      }
    }
  ],
  "shipments": [
    {
      "id": 394,
      "tracking": "U10000",
      "tracking_url": null,
      "number": "H55701340020",
      "cost": "100.0",
      "shipped_at": null,
      "state": "ready",
      "order_id": "R117785164",
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
              "id": 242,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 489,
              "name": "ShippingCategory #10"
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



## Processing the checkout payment step with a not yet existing ApplePay payment


### Request

#### Endpoint

```plaintext
PATCH /api/checkouts/R977526529
Accept: application/json
X-Spree-Order-Token: XxCl93FCHjmsK68Wk-xeWA
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=453&order[payment_attributes][][source_attributes][nonce]=fake-apple-pay-visa-nonce&order[payment_attributes][][source_attributes][payment_type]=ApplePayCard
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
ETag: W/&quot;7b1ecda6297b074506e07758836e8ae9&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 04a527eb-02e8-47e4-8337-c9ce1f68c175
X-Runtime: 0.101122
Content-Length: 4252
200 OK
```


```json
{
  "id": 553,
  "number": "R977526529",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 640,
  "created_at": "2019-08-06T09:27:47.034Z",
  "updated_at": "2019-08-06T09:27:47.241Z",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "email21@example.com",
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
  "token": "XxCl93FCHjmsK68Wk-xeWA",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 453,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 1153,
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
  "ship_address": {
    "id": 1154,
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
  "line_items": [
    {
      "id": 464,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 1306,
      "vendor_id": 3768,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 1306,
        "name": "Product #9 - 8889",
        "sku": "SKU-17",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-9-8889",
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
            "name": "Size-9",
            "presentation": "S",
            "option_type_name": "foo-size-9",
            "option_type_id": 531,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 788,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #48",
      "adjustments": [

      ]
    }
  ],
  "payments": [

  ],
  "shipments": [
    {
      "id": 393,
      "tracking": null,
      "tracking_url": null,
      "number": "H63212861574",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R977526529",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 366,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 361,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 366,
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
              "id": 241,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 488,
              "name": "ShippingCategory #9"
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



## Processing the checkout payment step with a not yet existing PayPal payment


### Request

#### Endpoint

```plaintext
PATCH /api/checkouts/R874610292
Accept: application/json
X-Spree-Order-Token: 7c_aNs3IyFOtI5j79s08Ew
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=452&order[payment_attributes][][source_attributes][nonce]=fake-paypal-billing-agreement-nonce&order[payment_attributes][][source_attributes][payment_type]=PayPalAccount
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
ETag: W/&quot;1453490abbba92e4238b81bd545aa793&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: ecaf7336-8360-4e77-9b88-a58197444ba5
X-Runtime: 0.089575
Content-Length: 4252
200 OK
```


```json
{
  "id": 552,
  "number": "R874610292",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 639,
  "created_at": "2019-08-06T09:27:46.612Z",
  "updated_at": "2019-08-06T09:27:46.783Z",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "email20@example.com",
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
  "token": "7c_aNs3IyFOtI5j79s08Ew",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 452,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 1151,
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
    "country_id": 537,
    "country_iso": "US",
    "state_id": 526,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 537,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 526,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 537
    }
  },
  "ship_address": {
    "id": 1152,
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
    "country_id": 537,
    "country_iso": "US",
    "state_id": 526,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 537,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 526,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 537
    }
  },
  "line_items": [
    {
      "id": 463,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 1304,
      "vendor_id": 3762,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 1304,
        "name": "Product #8 - 9483",
        "sku": "SKU-15",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-8-9483",
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
            "name": "Size-8",
            "presentation": "S",
            "option_type_name": "foo-size-8",
            "option_type_id": 530,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 787,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #43",
      "adjustments": [

      ]
    }
  ],
  "payments": [

  ],
  "shipments": [
    {
      "id": 391,
      "tracking": null,
      "tracking_url": null,
      "number": "H35151434743",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R874610292",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 364,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 360,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 364,
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
              "id": 240,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 487,
              "name": "ShippingCategory #8"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 1304,
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
PATCH /api/checkouts/R729150770
Accept: application/json
X-Spree-Order-Token: YOMOFUzWScu_dqDRueEwdg
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=451&order[payment_attributes][][source_attributes][nonce]=fake-valid-visa-nonce&order[payment_attributes][][source_attributes][payment_type]=CreditCard
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
ETag: W/&quot;94608174cc08ee021c43856c53960caa&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: fca2974c-c645-4764-af54-818710e99b96
X-Runtime: 0.089247
Content-Length: 4252
200 OK
```


```json
{
  "id": 551,
  "number": "R729150770",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 638,
  "created_at": "2019-08-06T09:27:46.165Z",
  "updated_at": "2019-08-06T09:27:46.342Z",
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
  "token": "YOMOFUzWScu_dqDRueEwdg",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 451,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 1149,
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
    "country_id": 536,
    "country_iso": "US",
    "state_id": 525,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 536,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 525,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 536
    }
  },
  "ship_address": {
    "id": 1150,
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
    "country_id": 536,
    "country_iso": "US",
    "state_id": 525,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 536,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 525,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 536
    }
  },
  "line_items": [
    {
      "id": 462,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 1302,
      "vendor_id": 3756,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 1302,
        "name": "Product #7 - 7144",
        "sku": "SKU-13",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-7-7144",
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
            "name": "Size-7",
            "presentation": "S",
            "option_type_name": "foo-size-7",
            "option_type_id": 529,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 786,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #38",
      "adjustments": [

      ]
    }
  ],
  "payments": [

  ],
  "shipments": [
    {
      "id": 389,
      "tracking": null,
      "tracking_url": null,
      "number": "H12572834447",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R729150770",
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
              "id": 239,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 486,
              "name": "ShippingCategory #7"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 1302,
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
PATCH /api/checkouts/R804185710
Accept: application/json
X-Spree-Order-Token: KHzOm6t570e6PGZoq2xOjQ
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=450&order[payment_attributes][][source_attributes][wallet_payment_source_id]=45
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
ETag: W/&quot;d4d5b58263bdb3e6108e90619740df08&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: f4a1c027-c284-4149-844b-3210af4a7d17
X-Runtime: 0.117811
Content-Length: 4252
200 OK
```


```json
{
  "id": 550,
  "number": "R804185710",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 637,
  "created_at": "2019-08-06T09:27:45.656Z",
  "updated_at": "2019-08-06T09:27:45.892Z",
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
  "token": "KHzOm6t570e6PGZoq2xOjQ",
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
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 1147,
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
    "country_id": 535,
    "country_iso": "US",
    "state_id": 524,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 535,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 524,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 535
    }
  },
  "ship_address": {
    "id": 1148,
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
    "country_id": 535,
    "country_iso": "US",
    "state_id": 524,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 535,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 524,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 535
    }
  },
  "line_items": [
    {
      "id": 461,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 1300,
      "vendor_id": 3750,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 1300,
        "name": "Product #6 - 6054",
        "sku": "SKU-11",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-6-6054",
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
            "name": "Size-6",
            "presentation": "S",
            "option_type_name": "foo-size-6",
            "option_type_id": 528,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 785,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #33",
      "adjustments": [

      ]
    }
  ],
  "payments": [

  ],
  "shipments": [
    {
      "id": 387,
      "tracking": null,
      "tracking_url": null,
      "number": "H65431200774",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R804185710",
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
              "id": 238,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 485,
              "name": "ShippingCategory #6"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 1300,
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
POST /api/orders/R702696762/line_items
Accept: application/json
X-Spree-Order-Token: 8i3kyE0wNBvz1LFsEXwI-Q
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/:order_number/line_items`

#### Parameters


```json
line_item[variant_id]=1327&line_item[options][vendor_id]=3829
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
ETag: W/&quot;c6e6db1e5a3650e53131713c8a78fcdd&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: b750c343-699d-450f-81fd-e9e831f5321f
X-Runtime: 0.077041
Content-Length: 853
201 Created
```


```json
{
  "id": 470,
  "quantity": 1,
  "price": "19.99",
  "variant_id": 1327,
  "vendor_id": 3829,
  "single_display_amount": "$19.99",
  "display_amount": "$19.99",
  "total": "19.99",
  "final_sale": false,
  "backordered": null,
  "promotionable": true,
  "variant": {
    "id": 1327,
    "name": "Product #23 - 2290",
    "sku": "SKU-38",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": false,
    "slug": "product-23-2290",
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
        "id": 601,
        "name": "Size-16",
        "presentation": "S",
        "option_type_name": "foo-size-16",
        "option_type_id": 538,
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
  "vendor_name": "Vendor #98",
  "adjustments": [

  ]
}
```



## Deleting a line item


### Request

#### Endpoint

```plaintext
DELETE /api/orders/R604346012/line_items/471
Accept: application/json
X-Spree-Order-Token: iAae2ulMEvaJP5zIPb3ayw
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
X-Request-Id: 29f78d22-bb72-4eb7-87f9-f74579f798bb
X-Runtime: 0.044169
204 No Content
```




## Updating a line item


### Request

#### Endpoint

```plaintext
PUT /api/orders/R081330548/line_items/468
Accept: application/json
X-Spree-Order-Token: TK0iNL9kkDWu3uxU8Ex0SA
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
ETag: W/&quot;9fbf8d8786503c289c7b00000d584436&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 19df4137-c443-492e-a289-224e9e8b5abc
X-Runtime: 0.104623
Content-Length: 848
200 OK
```


```json
{
  "id": 468,
  "quantity": 2,
  "price": "10.0",
  "variant_id": 1321,
  "vendor_id": 3816,
  "single_display_amount": "$10.00",
  "display_amount": "$20.00",
  "total": "20.0",
  "final_sale": false,
  "backordered": null,
  "promotionable": true,
  "variant": {
    "id": 1321,
    "name": "Product #20 - 120",
    "sku": "SKU-32",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": false,
    "slug": "product-20-120",
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
        "id": 598,
        "name": "Size-13",
        "presentation": "S",
        "option_type_name": "foo-size-13",
        "option_type_id": 535,
        "option_type_presentation": "Size"
      }
    ],
    "images": [

    ],
    "product_id": 799,
    "brand": null,
    "brand_slug": null,
    "brand_description": null
  },
  "vendor_name": "Vendor #87",
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
X-Request-Id: 231b9e70-06c2-482b-ad4c-3806c16673f8
X-Runtime: 0.009823
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



## Get my orders


### Request

#### Endpoint

```plaintext
GET /api/orders/mine
Accept: application/json
Authorization: Bearer 496e5e823bb07945684c67802101db6bce606abc9a49b724
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
ETag: W/&quot;59f1bafb923d3ebdc69bf7be26677718&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: e49dcb0f-4da4-4ef6-9346-837cf69cd192
X-Runtime: 0.019360
Content-Length: 305
200 OK
```


```json
{
  "orders": [
    {
      "number": "R205535338",
      "completed_at": "2019-08-06T09:27:54.835Z",
      "total": "120.0",
      "state": "Complete",
      "shipment_state": "shipped",
      "shipments": [
        {
          "number": "H18620828430",
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
GET /api/orders/R445826534
Accept: application/json
Authorization: Bearer 241ef08dd867e7e3bcc5adc4fc7ded01776304d1d88c1a92
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
ETag: W/&quot;480e60bf4121c6ae9c97fd71a5a5cd24&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: d098f96c-bab6-4777-a76e-8c30606689b0
X-Runtime: 0.124165
Content-Length: 9256
200 OK
```


```json
{
  "id": 561,
  "number": "R445826534",
  "item_total": "20.0",
  "total": "120.0",
  "ship_total": "100.0",
  "state": "complete",
  "adjustment_total": "0.0",
  "user_id": 648,
  "created_at": "2019-08-06T09:27:55.127Z",
  "updated_at": "2019-08-06T09:27:55.347Z",
  "completed_at": "2019-08-06T09:27:55.188Z",
  "payment_total": "120.0",
  "shipment_state": "shipped",
  "payment_state": "paid",
  "email": "email29@example.com",
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
  "token": "7Bg3Cyxh1y0LNX96H91ilg",
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
      "name": "Credit Card",
      "partial_name": "gateway",
      "method_type": "gateway"
    },
    {
      "id": 461,
      "name": "Credit Card",
      "partial_name": "gateway",
      "method_type": "gateway"
    }
  ],
  "bill_address": {
    "id": 1171,
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
    "id": 1172,
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
      "id": 474,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 1333,
      "vendor_id": 3846,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 1333,
        "name": "Product #26 - 6047",
        "sku": "SKU-44",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-26-6047",
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
            "id": 604,
            "name": "Size-19",
            "presentation": "S",
            "option_type_name": "foo-size-19",
            "option_type_id": 541,
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
      "vendor_name": "Vendor #113",
      "adjustments": [
        {
          "id": 79,
          "source_type": "Spree::PromotionAction",
          "source_id": 38,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 474,
          "amount": "5.0",
          "label": "foo",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-08-06T09:27:55.255Z",
          "updated_at": "2019-08-06T09:27:55.255Z",
          "display_amount": "$5.00"
        },
        {
          "id": 80,
          "source_type": "Spree::PromotionAction",
          "source_id": 38,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 474,
          "amount": "5.0",
          "label": "foo",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-08-06T09:27:55.262Z",
          "updated_at": "2019-08-06T09:27:55.262Z",
          "display_amount": "$5.00"
        },
        {
          "id": 86,
          "source_type": "Spree::TaxRate",
          "source_id": 15,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 474,
          "amount": "2.0",
          "label": "VAT 5%",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-08-06T09:27:55.324Z",
          "updated_at": "2019-08-06T09:27:55.333Z",
          "display_amount": "$2.00"
        }
      ]
    },
    {
      "id": 475,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 1333,
      "vendor_id": 3846,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 1333,
        "name": "Product #26 - 6047",
        "sku": "SKU-44",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-26-6047",
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
            "id": 604,
            "name": "Size-19",
            "presentation": "S",
            "option_type_name": "foo-size-19",
            "option_type_id": 541,
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
      "vendor_name": "Vendor #113",
      "adjustments": [
        {
          "id": 81,
          "source_type": "Spree::PromotionAction",
          "source_id": 38,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 475,
          "amount": "5.0",
          "label": "bar",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-08-06T09:27:55.269Z",
          "updated_at": "2019-08-06T09:27:55.269Z",
          "display_amount": "$5.00"
        },
        {
          "id": 87,
          "source_type": "Spree::TaxRate",
          "source_id": 16,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 475,
          "amount": "1.5",
          "label": "VAT 5%",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-08-06T09:27:55.345Z",
          "updated_at": "2019-08-06T09:27:55.354Z",
          "display_amount": "$1.50"
        }
      ]
    }
  ],
  "payments": [
    {
      "id": 219,
      "source_type": "Spree::CreditCard",
      "source_id": 188,
      "amount": "120.0",
      "display_amount": "$120.00",
      "payment_method_id": 460,
      "state": "completed",
      "avs_response": null,
      "created_at": "2019-08-06T09:27:55.201Z",
      "updated_at": "2019-08-06T09:27:55.201Z",
      "payment_method": {
        "id": 460,
        "name": "Credit Card"
      },
      "source": {
        "id": 188,
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
      "id": 403,
      "tracking": "U10000",
      "tracking_url": null,
      "number": "H80128081517",
      "cost": "100.0",
      "shipped_at": "2019-08-06T09:27:55.219Z",
      "state": "shipped",
      "order_id": "R445826534",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 376,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 369,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 376,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 369,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 369,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 249,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 501,
              "name": "ShippingCategory #22"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 1333,
          "quantity": 1,
          "states": {
            "shipped": 1
          }
        },
        {
          "variant_id": 1333,
          "quantity": 1,
          "states": {
            "shipped": 1
          }
        }
      ],
      "adjustments": [
        {
          "id": 82,
          "source_type": "Spree::PromotionAction",
          "source_id": 38,
          "adjustable_type": "Spree::Shipment",
          "adjustable_id": 403,
          "amount": "-9.99",
          "label": "Shipping",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-08-06T09:27:55.276Z",
          "updated_at": "2019-08-06T09:27:55.276Z",
          "display_amount": "-$9.99"
        },
        {
          "id": 83,
          "source_type": "Spree::PromotionAction",
          "source_id": 38,
          "adjustable_type": "Spree::Shipment",
          "adjustable_id": 403,
          "amount": "-10.0",
          "label": "Shipping",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-08-06T09:27:55.282Z",
          "updated_at": "2019-08-06T09:27:55.282Z",
          "display_amount": "-$10.00"
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
      "adjustable_id": 561,
      "amount": "20.0",
      "label": "adj1",
      "promotion_code_id": null,
      "finalized": false,
      "eligible": true,
      "created_at": "2019-08-06T09:27:55.287Z",
      "updated_at": "2019-08-06T09:27:55.287Z",
      "display_amount": "$20.00"
    },
    {
      "id": 85,
      "source_type": "Spree::Promotion",
      "source_id": 56,
      "adjustable_type": "Spree::Order",
      "adjustable_id": 561,
      "amount": "30.0",
      "label": "adj2",
      "promotion_code_id": null,
      "finalized": false,
      "eligible": true,
      "created_at": "2019-08-06T09:27:55.290Z",
      "updated_at": "2019-08-06T09:27:55.290Z",
      "display_amount": "$30.00"
    }
  ],
  "permissions": {
    "can_update": false
  },
  "credit_cards": [
    {
      "id": 188,
      "month": "12",
      "year": "2020",
      "cc_type": null,
      "last_digits": "1111",
      "name": "Spree Commerce",
      "address": {
        "id": 1171,
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
GET /api/orders/R760663800
Accept: application/json
Authorization: 0dd03a4aa6c2caa5228fc61d6b3edf885111c19cc3420757
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
X-Request-Id: 3b3e028b-7405-43c0-9258-f4080b603679
X-Runtime: 0.010112
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
user[email]=email14%40example.com
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
X-Request-Id: ae0bf64c-14ab-41e0-a1c1-805d55d6d165
X-Runtime: 0.002761
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
user[email]=email12%40example.com&user[password]=secret
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
Authorization: Bearer bdf9d74175d5a3801271755ae8a4548089929de40a65b992
ETag: W/&quot;5d332450c3aaf44ce8468aa53f9b0616&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: f789315c-39d0-4d02-9cd5-4e93d3ff1521
X-Runtime: 0.007336
Content-Length: 553
200 OK
```


```json
{
  "id": 630,
  "email": "email12@example.com",
  "persistence_token": null,
  "perishable_token": null,
  "last_request_at": null,
  "login": "email12@example.com",
  "ship_address_id": null,
  "bill_address_id": null,
  "created_at": "2019-08-06T09:27:45.150Z",
  "updated_at": "2019-08-06T09:27:45.151Z",
  "spree_api_key": "bdf9d74175d5a3801271755ae8a4548089929de40a65b992",
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
X-Request-Id: 6376124c-fa5b-4ad2-b4e9-838646de57ed
X-Runtime: 0.022368
204 No Content
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
Date: Tue, 06 Aug 2019 09:27:52 GMT
Surrogate-Control: max-age=900
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;872130811054186a23dab76f5a488719&quot;
X-Request-Id: 4aca83bd-a020-44a9-bddc-3f71622bb452
X-Runtime: 0.085099
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
      "id": 792,
      "name": "Product #13 - 8692",
      "description": "As seen on TV!",
      "available_on": "2018-08-06T09:27:52.271Z",
      "slug": "product-13-8692",
      "meta_description": null,
      "meta_keywords": null,
      "shipping_category_id": 492,
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
        "id": 1313,
        "name": "Product #13 - 8692",
        "sku": "SKU-25",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-13-8692",
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
GET /api/products/product-14-1215
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
Date: Tue, 06 Aug 2019 09:27:52 GMT
Surrogate-Control: max-age=900
Surrogate-Key: product_id=1
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;a1c06c4fec00ce389db514c5d2de9fe5&quot;
X-Request-Id: 60cf3b91-4637-49ff-be81-9adbe7c38250
X-Runtime: 0.045225
Content-Length: 836
200 OK
```


```json
{
  "id": 793,
  "name": "Product #14 - 1215",
  "description": "As seen on TV!",
  "available_on": "2018-08-06T09:27:52.446Z",
  "slug": "product-14-1215",
  "meta_description": null,
  "meta_keywords": null,
  "shipping_category_id": 493,
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
    "id": 1314,
    "name": "Product #14 - 1215",
    "sku": "SKU-26",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": true,
    "slug": "product-14-1215",
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
X-Request-Id: 65540e56-c9c9-4ac1-8185-5fad6d596c37
X-Runtime: 0.013774
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
GET /api/taxons/products?id=760
Host: example.org
Cookie: 
```

`GET /api/taxons/products`

#### Parameters


```json
id: 760
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
ETag: W/&quot;443a7b6214a59f7459726cb87c5f7510&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: da221c32-2a95-4124-ab1a-48110498051e
X-Runtime: 0.044934
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
      "id": 795,
      "name": "Product #16 - 4284",
      "description": "As seen on TV!",
      "available_on": "2018-08-06T09:27:52.762Z",
      "slug": "product-16-4284",
      "meta_description": null,
      "meta_keywords": null,
      "shipping_category_id": 495,
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
        "id": 1316,
        "name": "Product #16 - 4284",
        "sku": "SKU-28",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-16-4284",
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
ETag: W/&quot;8ac5a7de067bd1fb241e1016f91bb159&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: b20de71f-8fc3-490b-9526-0a645b278c43
X-Runtime: 0.042807
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
      "id": 797,
      "name": "Product #18 - 5566",
      "description": "As seen on TV!",
      "available_on": "2018-08-06T09:27:53.053Z",
      "slug": "product-18-5566",
      "meta_description": null,
      "meta_keywords": null,
      "shipping_category_id": 496,
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
        "id": 1318,
        "name": "Product #18 - 5566",
        "sku": "SKU-30",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-18-5566",
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

Get a single user return authorziation

## Can get another user&#39;s return authorization


### Request

#### Endpoint

```plaintext
GET /api/returns/RA162730712
Authorization: Bearer 90757097bdfc0d3ccfa6da1f373b74d07041ecef1783ff01
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
ETag: W/&quot;e5c574d90e51fc816df2b265916a9116&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 29cf1638-b192-44c1-b7fe-043ae73a0808
X-Runtime: 0.034258
Content-Length: 2771
200 OK
```


```json
{
  "id": 19,
  "number": "RA162730712",
  "state": "authorized",
  "order_id": 547,
  "memo": "Items were broken",
  "created_at": "2019-08-06T09:27:44.331Z",
  "updated_at": "2019-08-06T09:27:44.331Z",
  "reason": {
    "id": 60,
    "name": "Defect #5",
    "active": true,
    "mutable": true,
    "created_at": "2019-08-06T09:27:44.328Z",
    "updated_at": "2019-08-06T09:27:44.328Z",
    "mirakl_code": null
  },
  "order": {
    "id": 547,
    "number": "R617738042",
    "item_total": "10.0",
    "total": "110.0",
    "state": "complete",
    "adjustment_total": "0.0",
    "user_id": 627,
    "completed_at": "2019-08-06T09:27:44.277Z",
    "bill_address_id": 1138,
    "ship_address_id": 1139,
    "payment_total": "110.0",
    "shipment_state": "shipped",
    "payment_state": "paid",
    "email": "email9@example.com",
    "special_instructions": null,
    "created_at": "2019-08-06T09:27:44.232Z",
    "updated_at": "2019-08-06T09:27:44.317Z",
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
    "guest_token": "5TN8UY5K1_HBcnesOUtcQw",
    "canceled_at": null,
    "canceler_id": null,
    "store_id": 586,
    "approver_name": null,
    "frontend_viewable": true
  },
  "ship_address": {
    "id": 1139,
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
    "country_id": 530,
    "country_iso": "US",
    "state_id": 519,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 530,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 519,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 530
    }
  },
  "bill_address": {
    "id": 1138,
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
    "country_id": 530,
    "country_iso": "US",
    "state_id": 519,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 530,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 519,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 530
    }
  },
  "return_items": [
    {
      "name": "Product #3 - 4341",
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
        "id": 443,
        "name": "Credit Card"
      },
      "source": {
        "id": 185,
        "month": "12",
        "year": "2020",
        "cc_type": null,
        "last_digits": "1111",
        "name": "Spree Commerce",
        "gateway_customer_profile_id": "BGS-050551",
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
Authorization: Bearer d6946be251d9e77ae3fc67b35dbc76eb7c39ca3cf857e690
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
ETag: W/&quot;864481c21ac75617511bb0c242b6a382&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 4cd75cf2-5312-40e6-a2cd-35b67c8e3574
X-Runtime: 0.006525
Content-Length: 164
200 OK
```


```json
{
  "return_authorizations": [
    {
      "number": "RA626725155",
      "created_at": "2019-08-06T09:27:44.686Z",
      "return_amount": "10.0",
      "order_number": "R765124647",
      "state": "authorized"
    }
  ]
}
```



## returns a 200


### Request

#### Endpoint

```plaintext
GET /api/returns/RA525610414
Authorization: Bearer 187b70ff69e4560c83943e986856a8938e3f990d677d88ff
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
ETag: W/&quot;6845a81a377d81af971d198a16b8851f&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: dbd0c940-53d8-4277-bcdb-aeb644923aef
X-Runtime: 0.065118
Content-Length: 2694
200 OK
```


```json
{
  "id": 17,
  "number": "RA525610414",
  "state": "authorized",
  "order_id": 545,
  "memo": "Items were broken",
  "created_at": "2019-08-06T09:27:43.633Z",
  "updated_at": "2019-08-06T09:27:43.633Z",
  "reason": {
    "id": 56,
    "name": "Defect #1",
    "active": true,
    "mutable": true,
    "created_at": "2019-08-06T09:27:43.611Z",
    "updated_at": "2019-08-06T09:27:43.611Z",
    "mirakl_code": null
  },
  "order": {
    "id": 545,
    "number": "R586612425",
    "item_total": "10.0",
    "total": "110.0",
    "state": "complete",
    "adjustment_total": "0.0",
    "user_id": 624,
    "completed_at": "2019-08-06T09:27:43.439Z",
    "bill_address_id": 1134,
    "ship_address_id": 1135,
    "payment_total": "110.0",
    "shipment_state": "shipped",
    "payment_state": "paid",
    "email": "email6@example.com",
    "special_instructions": null,
    "created_at": "2019-08-06T09:27:43.272Z",
    "updated_at": "2019-08-06T09:27:43.563Z",
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
    "guest_token": "CtkuQF4ZwJxh3KhWijbMiA",
    "canceled_at": null,
    "canceler_id": null,
    "store_id": 584,
    "approver_name": null,
    "frontend_viewable": true
  },
  "ship_address": {
    "id": 1135,
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
    "country_id": 528,
    "country_iso": "US",
    "state_id": 517,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 528,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 517,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 528
    }
  },
  "bill_address": {
    "id": 1134,
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
    "country_id": 528,
    "country_iso": "US",
    "state_id": 517,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 528,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 517,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 528
    }
  },
  "return_items": [
    {
      "name": "Product #1 - 7494",
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
        "id": 439,
        "name": "Credit Card"
      },
      "source": {
        "id": 183,
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
GET /api/returns/RA262746637
Authorization: Bearer 3cfaa1f91268ba89f3f89bc5506d00ab552406ae38299831
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
X-Request-Id: cac35314-7c2a-42af-bf72-7a4d5e04d761
X-Runtime: 0.008981
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
Authorization: Bearer b957e32949baa3948a0724729c0a4a1fc471f5f7cd62525d
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
ETag: W/&quot;9d10da1a1879c71909c17eb4c8cd09ee&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 7643d234-ad35-4559-aa9e-2d567b43227a
X-Runtime: 0.041100
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
      "created_at": "2019-08-06T09:27:42.442Z"
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
user[email]=email17%40example.com&user[password]=secret
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
Authorization: Bearer 1c666d64c0c9ea92da25d891f18100f25fa7dd1d73234cc7
ETag: W/&quot;fba5203f3b25f7dab4ac384a7df573a7&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: dede1ae1-fedc-47fc-8723-ae2e8cfe7f0b
X-Runtime: 0.004235
Content-Length: 553
200 OK
```


```json
{
  "id": 635,
  "email": "email17@example.com",
  "persistence_token": null,
  "perishable_token": null,
  "last_request_at": null,
  "login": "email17@example.com",
  "ship_address_id": null,
  "bill_address_id": null,
  "created_at": "2019-08-06T09:27:45.418Z",
  "updated_at": "2019-08-06T09:27:45.419Z",
  "spree_api_key": "1c666d64c0c9ea92da25d891f18100f25fa7dd1d73234cc7",
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
Authorization: Bearer f7ac6b92dc9b66a1ef3d9b0b790b8b4ee5e6d6cec6011584
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
Authorization: Bearer f7ac6b92dc9b66a1ef3d9b0b790b8b4ee5e6d6cec6011584
ETag: W/&quot;8d0d8e4d5752f3256003df85bddc5f7d&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 55cdd3d2-e7ae-42c5-83a9-39cbc30436da
X-Runtime: 0.026964
Content-Length: 1309
200 OK
```


```json
{
  "email": "email16@example.com",
  "first_name": null,
  "last_name": null,
  "id": 634,
  "subscribed": null,
  "addresses": [
    {
      "id": 1146,
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
      "country_id": 534,
      "country_iso": "US",
      "state_id": 523,
      "state_name": null,
      "state_text": "AL",
      "country_name": "United States",
      "default": true
    },
    {
      "id": 1145,
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
      "country_id": 534,
      "country_iso": "US",
      "state_id": 523,
      "state_name": null,
      "state_text": "AL",
      "country_name": "United States",
      "default": false
    }
  ],
  "payment_sources": [
    {
      "default": true,
      "id": 69,
      "payment_type": "CreditCard",
      "token": null,
      "created_at": "2019-08-06T09:27:45.360Z",
      "cc_type": null,
      "last_digits": null,
      "month": null,
      "year": null
    },
    {
      "default": false,
      "id": 70,
      "payment_type": "ApplePayCard",
      "token": null,
      "created_at": "2019-08-06T09:27:45.372Z",
      "cc_type": null,
      "last_digits": null,
      "month": null,
      "year": null
    },
    {
      "default": false,
      "id": 71,
      "payment_type": "PayPalAccount",
      "token": null,
      "created_at": "2019-08-06T09:27:45.383Z",
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
Authorization: Bearer c0cf790529933436f241ec25a983e832762cf25b4e6424b8
ETag: W/&quot;d4904add32630c104ebfbf4c1a9e671a&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: afa4faa1-8f13-4af7-9413-b5261fc15f02
X-Runtime: 0.015785
Content-Length: 157
201 Created
```


```json
{
  "id": 636,
  "email": "test@example.com",
  "created_at": "2019-08-06T09:27:45.433Z",
  "updated_at": "2019-08-06T09:27:45.435Z",
  "bill_address": null,
  "ship_address": null
}
```



# Variant



## Fetching a variant


### Request

#### Endpoint

```plaintext
GET /api/variants/1298
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
ETag: W/&quot;143941f2b983c18d88f9d0eb2a0d41db&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: b0b153d6-552d-4125-a7a0-16ae670a81a5
X-Runtime: 0.106641
Content-Length: 1455
200 OK
```


```json
{
  "id": 1298,
  "name": "Product #5 - 1256",
  "sku": "SKU-9",
  "weight": "0.0",
  "height": null,
  "width": null,
  "depth": null,
  "is_master": false,
  "slug": "product-5-1256",
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
      "id": 590,
      "name": "Size-5",
      "presentation": "S",
      "option_type_name": "foo-size-5",
      "option_type_id": 527,
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
      "attachment_updated_at": "2019-08-06T09:27:44.870Z",
      "attachment_width": 489,
      "attachment_height": 490,
      "alt": null,
      "viewable_type": "Spree::Variant",
      "viewable_id": 1298,
      "mini_url": "/spree/products/2/mini/thinking-cat.jpg?1565083664",
      "small_url": "/spree/products/2/small/thinking-cat.jpg?1565083664",
      "product_url": "/spree/products/2/product/thinking-cat.jpg?1565083664",
      "large_url": "/spree/products/2/large/thinking-cat.jpg?1565083664"
    }
  ],
  "variant_properties": [

  ],
  "stock_items": [

  ],
  "prices": [
    {
      "id": 2473,
      "vendor_id": 3745,
      "price": "10.0",
      "original_price": "10.0",
      "discount_percent": 0.0,
      "total_on_hand": 0,
      "country_iso": null,
      "final_sale": false,
      "on_sale": false
    },
    {
      "id": 2474,
      "vendor_id": 3746,
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
Authorization: Bearer 60f6817085be806d6193af458745b332c28de848ef4ebda9
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
ETag: W/&quot;4c5de02c9d476826d8842b0184933ead&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 36fda4a3-fc9f-4fbb-99e3-14a6121dba2a
X-Runtime: 0.012123
Content-Length: 199
200 OK
```


```json
[
  {
    "id": 40,
    "user_id": 620,
    "payment_source_type": "SolidusPaypalBraintree::Source",
    "payment_source_id": 67,
    "default": false,
    "created_at": "2019-08-06T09:27:42.257Z",
    "updated_at": "2019-08-06T09:27:42.257Z"
  }
]
```



## Remove the payment from the user wallet


### Request

#### Endpoint

```plaintext
DELETE /api/wallet_payment_sources/39
Accept: application/json
Authorization: Bearer f26ce7dfa43c744efa84dd18a4d7578e7e45d2f6ebdde846
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
X-Request-Id: ef2d16a7-db86-4894-af8d-211c3bc785ce
X-Runtime: 0.125095
204 No Content
```




## Set a wallet payment source as the default user payment method


### Request

#### Endpoint

```plaintext
POST /api/wallet_payment_sources/41/default
Accept: application/json
Authorization: Bearer fadbecd54019d2dd9f307c48dd99957fce7afc5e2a53d784
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
X-Request-Id: 45d94a17-abf6-4474-a28e-1d1f766b26d9
X-Runtime: 0.009091
204 No Content
```




