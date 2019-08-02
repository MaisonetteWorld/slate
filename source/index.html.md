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
PUT /api/orders/R185181745/addresses/847
Accept: application/json
X-Spree-Order-Token: b_Fz8Kf5AmOY5JH6A5iCUA
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
ETag: W/&quot;f2c121fd2f8c196b901f9e5d83fa46af&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: db46b4d4-d4e0-4fc4-a55e-746db8df0639
X-Runtime: 0.040695
Content-Length: 513
200 OK
```


```json
{
  "id": 848,
  "firstname": "John the Tester",
  "lastname": null,
  "full_name": "John the Tester",
  "address1": "A Different Road",
  "address2": "Northwest",
  "city": "Herndon",
  "zipcode": "10018",
  "phone": "555-555-0199",
  "company": "Company",
  "alternative_phone": "555-555-0199",
  "country_id": 458,
  "country_iso": "US",
  "state_id": 447,
  "state_name": null,
  "state_text": "AL",
  "country": {
    "id": 458,
    "iso_name": "UNITED STATES",
    "iso": "US",
    "iso3": "USA",
    "name": "United States",
    "numcode": 840
  },
  "state": {
    "id": 447,
    "name": "Alabama",
    "abbr": "AL",
    "country_id": 458
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
X-Spree-Order-Token: RiSIWLLwnGQx1nKq_z5OqA
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/braintree/transactions`

#### Parameters


```json
order_id=R774109697&payment_method_id=405&options[restart_checkout]=true&transaction[email]=maryellen.oga%40mckenziemcglynn.com&transaction[nonce]=fake-paypal-billing-agreement-nonce&transaction[phone]=555-555-0199&transaction[address_attributes][first_name]=John&transaction[address_attributes][last_name]=Stamm&transaction[address_attributes][address_line_1]=A+Different+Road&transaction[address_attributes][city]=Herndon&transaction[address_attributes][state_code]=AL&transaction[address_attributes][zip]=10035&transaction[address_attributes][country_code]=US&transaction[payment_type]=PayPalAccount
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
ETag: W/&quot;1096d3a2e2e8082d8aad1b8220380429&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 88a275ff-8012-4b75-8118-d3b7c5e9b120
X-Runtime: 0.200324
Content-Length: 4693
200 OK
```


```json
{
  "id": 414,
  "number": "R774109697",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2019-08-02T08:45:48.161Z",
  "updated_at": "2019-08-02T08:45:48.355Z",
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
  "token": "RiSIWLLwnGQx1nKq_z5OqA",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 405,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 868,
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
    "country_id": 467,
    "country_iso": "US",
    "state_id": 456,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 467,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 456,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 467
    }
  },
  "ship_address": {
    "id": 868,
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
    "country_id": 467,
    "country_iso": "US",
    "state_id": 456,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 467,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 456,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 467
    }
  },
  "line_items": [
    {
      "id": 417,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 1133,
      "vendor_id": 3385,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 1133,
        "name": "Product #27 - 6149",
        "sku": "SKU-46",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-27-6149",
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
            "id": 474,
            "name": "Size-20",
            "presentation": "S",
            "option_type_name": "foo-size-20",
            "option_type_id": 474,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 671,
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
      "id": 196,
      "source_type": "SolidusPaypalBraintree::Source",
      "source_id": 61,
      "amount": "110.0",
      "display_amount": "$110.00",
      "payment_method_id": 405,
      "state": "checkout",
      "avs_response": null,
      "created_at": "2019-08-02T08:45:48.244Z",
      "updated_at": "2019-08-02T08:45:48.244Z",
      "payment_method": {
        "id": 405,
        "name": "Braintree"
      },
      "source": {
        "id": 61,
        "payment_type": "PayPalAccount",
        "token": "bgx899",
        "created_at": "2019-08-02T08:45:48.243Z",
        "email": "jane.doe@paypal.com"
      }
    }
  ],
  "shipments": [
    {
      "id": 343,
      "tracking": null,
      "tracking_url": null,
      "number": "H45682704453",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R774109697",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 329,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 299,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 329,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 299,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 299,
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
              "id": 413,
              "name": "ShippingCategory #23"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 1133,
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
X-Spree-Order-Token: SxKNnwx7hgxTNhJWbizE-Q
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/braintree/transactions`

#### Parameters


```json
order_id=R533590358&payment_method_id=404&options[restart_checkout]=true&transaction[email]=maryellen.oga%40mckenziemcglynn.com&transaction[nonce]=fake-apple-pay-visa-nonce&transaction[phone]=555-555-0199&transaction[address_attributes][first_name]=John&transaction[address_attributes][last_name]=Stamm&transaction[address_attributes][address_line_1]=A+Different+Road&transaction[address_attributes][city]=Herndon&transaction[address_attributes][state_code]=AL&transaction[address_attributes][zip]=10033&transaction[address_attributes][country_code]=US&transaction[payment_type]=ApplePayCard
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
ETag: W/&quot;8ab53e5dc62fca9c86645b739c306d07&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 4eaa9530-7881-4b8f-9e55-e2483f4a46aa
X-Runtime: 0.283262
Content-Length: 4709
200 OK
```


```json
{
  "id": 413,
  "number": "R533590358",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2019-08-02T08:45:47.582Z",
  "updated_at": "2019-08-02T08:45:47.833Z",
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
  "token": "SxKNnwx7hgxTNhJWbizE-Q",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 404,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 865,
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
    "country_id": 466,
    "country_iso": "US",
    "state_id": 455,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 466,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 455,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 466
    }
  },
  "ship_address": {
    "id": 865,
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
    "country_id": 466,
    "country_iso": "US",
    "state_id": 455,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 466,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 455,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 466
    }
  },
  "line_items": [
    {
      "id": 416,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 1131,
      "vendor_id": 3379,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 1131,
        "name": "Product #26 - 4502",
        "sku": "SKU-44",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-26-4502",
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
            "id": 473,
            "name": "Size-19",
            "presentation": "S",
            "option_type_name": "foo-size-19",
            "option_type_id": 473,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 670,
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
      "id": 195,
      "source_type": "SolidusPaypalBraintree::Source",
      "source_id": 60,
      "amount": "110.0",
      "display_amount": "$110.00",
      "payment_method_id": 404,
      "state": "checkout",
      "avs_response": null,
      "created_at": "2019-08-02T08:45:47.704Z",
      "updated_at": "2019-08-02T08:45:47.704Z",
      "payment_method": {
        "id": 404,
        "name": "Braintree"
      },
      "source": {
        "id": 60,
        "payment_type": "ApplePayCard",
        "token": "cg7hsk",
        "created_at": "2019-08-02T08:45:47.704Z",
        "card_type": "Apple Pay - Visa",
        "last_4": "1881"
      }
    }
  ],
  "shipments": [
    {
      "id": 341,
      "tracking": null,
      "tracking_url": null,
      "number": "H24283360842",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R533590358",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 327,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 298,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 327,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 298,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 298,
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
              "id": 412,
              "name": "ShippingCategory #22"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 1131,
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
PUT /api/checkouts/R713183005/complete
Accept: application/json
X-Spree-Order-Token: X0RRDATP95URplRJ2V84Zg
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
ETag: W/&quot;dbb079a56061357590b182c60e9d3401&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 7888d7ff-f3b7-499f-aa18-087a2be85feb
X-Runtime: 2.148341
Content-Length: 4828
200 OK
```


```json
{
  "id": 404,
  "number": "R713183005",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "complete",
  "adjustment_total": "0.0",
  "user_id": 475,
  "created_at": "2019-08-02T08:45:40.283Z",
  "updated_at": "2019-08-02T08:45:43.477Z",
  "completed_at": "2019-08-02T08:45:43.477Z",
  "payment_total": "110.0",
  "shipment_state": "ready",
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
  "token": "X0RRDATP95URplRJ2V84Zg",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 391,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    },
    {
      "id": 392,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 844,
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
    "country_id": 457,
    "country_iso": "US",
    "state_id": 446,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 457,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 446,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 457
    }
  },
  "ship_address": {
    "id": 845,
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
    "country_id": 457,
    "country_iso": "US",
    "state_id": 446,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 457,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 446,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 457
    }
  },
  "line_items": [
    {
      "id": 407,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 1111,
      "vendor_id": 3321,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 1111,
        "name": "Product #16 - 6471",
        "sku": "SKU-24",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-16-6471",
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
            "id": 463,
            "name": "Size-9",
            "presentation": "S",
            "option_type_name": "foo-size-9",
            "option_type_id": 463,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 660,
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
      "id": 190,
      "source_type": "SolidusPaypalBraintree::Source",
      "source_id": 56,
      "amount": "110.0",
      "display_amount": "$110.00",
      "payment_method_id": 391,
      "state": "completed",
      "avs_response": "M",
      "created_at": "2019-08-02T08:45:40.359Z",
      "updated_at": "2019-08-02T08:45:43.366Z",
      "payment_method": {
        "id": 391,
        "name": "Braintree"
      },
      "source": {
        "id": 56,
        "payment_type": "CreditCard",
        "token": "h2zgd5",
        "created_at": "2019-08-02T08:45:40.358Z",
        "cc_type": "Visa",
        "last_digits": "1881"
      }
    }
  ],
  "shipments": [
    {
      "id": 332,
      "tracking": "U10000",
      "tracking_url": null,
      "number": "H58386033486",
      "cost": "100.0",
      "shipped_at": null,
      "state": "ready",
      "order_id": "R713183005",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 318,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 290,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 318,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 290,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 290,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 217,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 404,
              "name": "ShippingCategory #14"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 1111,
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
PATCH /api/checkouts/R634898862
Accept: application/json
X-Spree-Order-Token: kfZq099i5TILVvCrwy1YSg
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=387&order[payment_attributes][][source_attributes][nonce]=fake-apple-pay-visa-nonce&order[payment_attributes][][source_attributes][payment_type]=ApplePayCard
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
ETag: W/&quot;97e16b7141858d590204507a8c927c8f&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 93c86c27-f0e1-4ab8-89b7-7c275df40c2f
X-Runtime: 0.150067
Content-Length: 4252
200 OK
```


```json
{
  "id": 400,
  "number": "R634898862",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 471,
  "created_at": "2019-08-02T08:45:38.163Z",
  "updated_at": "2019-08-02T08:45:38.524Z",
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
  "token": "kfZq099i5TILVvCrwy1YSg",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 387,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 836,
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
    "country_id": 453,
    "country_iso": "US",
    "state_id": 442,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 453,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 442,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 453
    }
  },
  "ship_address": {
    "id": 837,
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
    "country_id": 453,
    "country_iso": "US",
    "state_id": 442,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 453,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 442,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 453
    }
  },
  "line_items": [
    {
      "id": 403,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 1103,
      "vendor_id": 3297,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 1103,
        "name": "Product #12 - 1968",
        "sku": "SKU-16",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-12-1968",
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
            "id": 459,
            "name": "Size-5",
            "presentation": "S",
            "option_type_name": "foo-size-5",
            "option_type_id": 459,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 656,
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
      "id": 325,
      "tracking": null,
      "tracking_url": null,
      "number": "H34626553465",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R634898862",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 311,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 286,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 311,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 286,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 286,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 213,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 400,
              "name": "ShippingCategory #10"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 1103,
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
PATCH /api/checkouts/R165451139
Accept: application/json
X-Spree-Order-Token: 5P564zTT5biPZ-Sjg8F7ZQ
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=388&order[payment_attributes][][source_attributes][nonce]=fake-paypal-billing-agreement-nonce&order[payment_attributes][][source_attributes][payment_type]=PayPalAccount
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
ETag: W/&quot;d69e6f625acd66236cf53816022a245c&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 83b20d43-8413-48ec-9847-c552eeaa7702
X-Runtime: 0.105381
Content-Length: 4252
200 OK
```


```json
{
  "id": 401,
  "number": "R165451139",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 472,
  "created_at": "2019-08-02T08:45:38.802Z",
  "updated_at": "2019-08-02T08:45:39.012Z",
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
  "token": "5P564zTT5biPZ-Sjg8F7ZQ",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 388,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 838,
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
    "country_id": 454,
    "country_iso": "US",
    "state_id": 443,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 454,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 443,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 454
    }
  },
  "ship_address": {
    "id": 839,
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
    "country_id": 454,
    "country_iso": "US",
    "state_id": 443,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 454,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 443,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 454
    }
  },
  "line_items": [
    {
      "id": 404,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 1105,
      "vendor_id": 3303,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 1105,
        "name": "Product #13 - 7047",
        "sku": "SKU-18",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-13-7047",
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
            "id": 460,
            "name": "Size-6",
            "presentation": "S",
            "option_type_name": "foo-size-6",
            "option_type_id": 460,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 657,
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
      "id": 327,
      "tracking": null,
      "tracking_url": null,
      "number": "H71838308362",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R165451139",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 313,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 287,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 313,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 287,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 287,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 214,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 401,
              "name": "ShippingCategory #11"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 1105,
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
PATCH /api/checkouts/R762071312
Accept: application/json
X-Spree-Order-Token: NLeB_kbnHEHjPHHxhWgAWA
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=389&order[payment_attributes][][source_attributes][nonce]=fake-valid-visa-nonce&order[payment_attributes][][source_attributes][payment_type]=CreditCard
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
ETag: W/&quot;796abde2495d94e766295af7502aa2da&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: f6f2b51c-2443-4637-9f13-fbf1041da830
X-Runtime: 0.101610
Content-Length: 4252
200 OK
```


```json
{
  "id": 402,
  "number": "R762071312",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 473,
  "created_at": "2019-08-02T08:45:39.309Z",
  "updated_at": "2019-08-02T08:45:39.499Z",
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
  "token": "NLeB_kbnHEHjPHHxhWgAWA",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 389,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 840,
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
    "country_id": 455,
    "country_iso": "US",
    "state_id": 444,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 455,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 444,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 455
    }
  },
  "ship_address": {
    "id": 841,
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
    "country_id": 455,
    "country_iso": "US",
    "state_id": 444,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 455,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 444,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 455
    }
  },
  "line_items": [
    {
      "id": 405,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 1107,
      "vendor_id": 3309,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 1107,
        "name": "Product #14 - 4138",
        "sku": "SKU-20",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-14-4138",
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
            "id": 461,
            "name": "Size-7",
            "presentation": "S",
            "option_type_name": "foo-size-7",
            "option_type_id": 461,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 658,
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

  ],
  "shipments": [
    {
      "id": 329,
      "tracking": null,
      "tracking_url": null,
      "number": "H45800148470",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R762071312",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 315,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 288,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 315,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 288,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 288,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 215,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 402,
              "name": "ShippingCategory #12"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 1107,
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
PATCH /api/checkouts/R354828877
Accept: application/json
X-Spree-Order-Token: nE_uk8vyOV2SZxMUl_dXoA
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=390&order[payment_attributes][][source_attributes][wallet_payment_source_id]=30
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
ETag: W/&quot;a93a6931a4062b790aab12284adc3e9e&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: e9cc89e1-27a3-4001-b7d6-d8a59028adb6
X-Runtime: 0.122296
Content-Length: 4252
200 OK
```


```json
{
  "id": 403,
  "number": "R354828877",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 474,
  "created_at": "2019-08-02T08:45:39.766Z",
  "updated_at": "2019-08-02T08:45:39.980Z",
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
  "token": "nE_uk8vyOV2SZxMUl_dXoA",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 390,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 842,
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
    "country_id": 456,
    "country_iso": "US",
    "state_id": 445,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 456,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 445,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 456
    }
  },
  "ship_address": {
    "id": 843,
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
    "country_id": 456,
    "country_iso": "US",
    "state_id": 445,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 456,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 445,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 456
    }
  },
  "line_items": [
    {
      "id": 406,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 1109,
      "vendor_id": 3315,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 1109,
        "name": "Product #15 - 5057",
        "sku": "SKU-22",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-15-5057",
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
            "id": 462,
            "name": "Size-8",
            "presentation": "S",
            "option_type_name": "foo-size-8",
            "option_type_id": 462,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 659,
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

  ],
  "shipments": [
    {
      "id": 331,
      "tracking": null,
      "tracking_url": null,
      "number": "H23522456121",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R354828877",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 317,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 289,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 317,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 289,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 289,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 216,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 403,
              "name": "ShippingCategory #13"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 1109,
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
POST /api/orders/R793331766/line_items
Accept: application/json
X-Spree-Order-Token: aYUpcGMv5MDXzEX3a5qWyw
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/:order_number/line_items`

#### Parameters


```json
line_item[variant_id]=1121&line_item[options][vendor_id]=3346
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
ETag: W/&quot;55ab86ec949dbf3466ccd48307d12eec&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: fd4b9fb9-c032-43f0-af88-af3f67ff5014
X-Runtime: 0.080940
Content-Length: 853
201 Created
```


```json
{
  "id": 411,
  "quantity": 1,
  "price": "19.99",
  "variant_id": 1121,
  "vendor_id": 3346,
  "single_display_amount": "$19.99",
  "display_amount": "$19.99",
  "total": "19.99",
  "final_sale": false,
  "backordered": null,
  "promotionable": true,
  "variant": {
    "id": 1121,
    "name": "Product #21 - 3305",
    "sku": "SKU-34",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": false,
    "slug": "product-21-3305",
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
        "id": 468,
        "name": "Size-14",
        "presentation": "S",
        "option_type_name": "foo-size-14",
        "option_type_id": 468,
        "option_type_presentation": "Size"
      }
    ],
    "images": [

    ],
    "product_id": 665,
    "brand": null,
    "brand_slug": null,
    "brand_description": null
  },
  "vendor_name": "Vendor #84",
  "adjustments": [

  ]
}
```



## Deleting a line item


### Request

#### Endpoint

```plaintext
DELETE /api/orders/R938997054/line_items/408
Accept: application/json
X-Spree-Order-Token: 2kUQECHYQsUYql8FRD88gg
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
X-Request-Id: 12cffb5c-f457-452a-8e25-7615e839c62e
X-Runtime: 0.058275
204 No Content
```




## Updating a line item


### Request

#### Endpoint

```plaintext
PUT /api/orders/R671459718/line_items/409
Accept: application/json
X-Spree-Order-Token: F3D9uzF3RM3CCQXstJX-rA
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
ETag: W/&quot;07c201df04003ca7b63aaac4a925cbef&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: f1f0299e-25f8-4aa4-b75b-45b5319d35cf
X-Runtime: 0.117079
Content-Length: 850
200 OK
```


```json
{
  "id": 409,
  "quantity": 2,
  "price": "10.0",
  "variant_id": 1115,
  "vendor_id": 3333,
  "single_display_amount": "$10.00",
  "display_amount": "$20.00",
  "total": "20.0",
  "final_sale": false,
  "backordered": null,
  "promotionable": true,
  "variant": {
    "id": 1115,
    "name": "Product #18 - 2778",
    "sku": "SKU-28",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": false,
    "slug": "product-18-2778",
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
        "id": 465,
        "name": "Size-11",
        "presentation": "S",
        "option_type_name": "foo-size-11",
        "option_type_id": 465,
        "option_type_presentation": "Size"
      }
    ],
    "images": [

    ],
    "product_id": 662,
    "brand": null,
    "brand_slug": null,
    "brand_description": null
  },
  "vendor_name": "Vendor #73",
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
X-Request-Id: c25838ee-f5dd-4c16-b4fb-ac6d1073b829
X-Runtime: 0.006605
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

Return an order, scoped to the current user

## Get my orders


### Request

#### Endpoint

```plaintext
GET /api/orders/mine
Accept: application/json
Authorization: Bearer 967da44580c8564e5cc85deb6d00434ed7ce3553a422fada
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
ETag: W/&quot;5d52037be1dbb92c62fe07e28c95c2c4&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 26884dcd-205c-43a0-a907-d29b344610b6
X-Runtime: 0.022082
Content-Length: 305
200 OK
```


```json
{
  "orders": [
    {
      "number": "R801675788",
      "completed_at": "2019-08-02T08:45:37.217Z",
      "total": "120.0",
      "state": "Complete",
      "shipment_state": "shipped",
      "shipments": [
        {
          "number": "H14325440868",
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
GET /api/orders/R666996643
Accept: application/json
Authorization: Bearer 07cbff5cf2b95c064d25792dbf829bdeae285b138dd790ed
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
ETag: W/&quot;41b72298837beb6ca4dd03b835695b69&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: e2e99581-c3a8-4917-8121-f237528e019d
X-Runtime: 0.200697
Content-Length: 9241
200 OK
```


```json
{
  "id": 398,
  "number": "R666996643",
  "item_total": "20.0",
  "total": "120.0",
  "ship_total": "100.0",
  "state": "complete",
  "adjustment_total": "0.0",
  "user_id": 469,
  "created_at": "2019-08-02T08:45:36.443Z",
  "updated_at": "2019-08-02T08:45:36.642Z",
  "completed_at": "2019-08-02T08:45:36.511Z",
  "payment_total": "120.0",
  "shipment_state": "shipped",
  "payment_state": "paid",
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
  "token": "LxpJOuBOD6zfp6tbgm2O0Q",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 383,
      "name": "Credit Card",
      "partial_name": "gateway",
      "method_type": "gateway"
    },
    {
      "id": 384,
      "name": "Credit Card",
      "partial_name": "gateway",
      "method_type": "gateway"
    }
  ],
  "bill_address": {
    "id": 832,
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
    "country_id": 450,
    "country_iso": "US",
    "state_id": 439,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 450,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 439,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 450
    }
  },
  "ship_address": {
    "id": 833,
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
    "country_id": 450,
    "country_iso": "US",
    "state_id": 439,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 450,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 439,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 450
    }
  },
  "line_items": [
    {
      "id": 399,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 1097,
      "vendor_id": 3277,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 1097,
        "name": "Product #9 - 9777",
        "sku": "SKU-10",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-9-9777",
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
            "id": 456,
            "name": "Size-2",
            "presentation": "S",
            "option_type_name": "foo-size-2",
            "option_type_id": 456,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 653,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #26",
      "adjustments": [
        {
          "id": 95,
          "source_type": "Spree::TaxRate",
          "source_id": 17,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 399,
          "amount": "2.0",
          "label": "VAT 5%",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-08-02T08:45:36.617Z",
          "updated_at": "2019-08-02T08:45:36.627Z",
          "display_amount": "$2.00"
        },
        {
          "id": 89,
          "source_type": "Spree::PromotionAction",
          "source_id": 39,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 399,
          "amount": "5.0",
          "label": "foo",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-08-02T08:45:36.572Z",
          "updated_at": "2019-08-02T08:45:36.572Z",
          "display_amount": "$5.00"
        },
        {
          "id": 88,
          "source_type": "Spree::PromotionAction",
          "source_id": 39,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 399,
          "amount": "5.0",
          "label": "foo",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-08-02T08:45:36.565Z",
          "updated_at": "2019-08-02T08:45:36.565Z",
          "display_amount": "$5.00"
        }
      ]
    },
    {
      "id": 400,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 1097,
      "vendor_id": 3277,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 1097,
        "name": "Product #9 - 9777",
        "sku": "SKU-10",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-9-9777",
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
            "id": 456,
            "name": "Size-2",
            "presentation": "S",
            "option_type_name": "foo-size-2",
            "option_type_id": 456,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 653,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #26",
      "adjustments": [
        {
          "id": 96,
          "source_type": "Spree::TaxRate",
          "source_id": 18,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 400,
          "amount": "1.5",
          "label": "VAT 5%",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-08-02T08:45:36.640Z",
          "updated_at": "2019-08-02T08:45:36.651Z",
          "display_amount": "$1.50"
        },
        {
          "id": 90,
          "source_type": "Spree::PromotionAction",
          "source_id": 39,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 400,
          "amount": "5.0",
          "label": "bar",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-08-02T08:45:36.579Z",
          "updated_at": "2019-08-02T08:45:36.579Z",
          "display_amount": "$5.00"
        }
      ]
    }
  ],
  "payments": [
    {
      "id": 188,
      "source_type": "Spree::CreditCard",
      "source_id": 162,
      "amount": "120.0",
      "display_amount": "$120.00",
      "payment_method_id": 383,
      "state": "completed",
      "avs_response": null,
      "created_at": "2019-08-02T08:45:36.525Z",
      "updated_at": "2019-08-02T08:45:36.525Z",
      "payment_method": {
        "id": 383,
        "name": "Credit Card"
      },
      "source": {
        "id": 162,
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
      "id": 322,
      "tracking": "U10000",
      "tracking_url": null,
      "number": "H12586342560",
      "cost": "100.0",
      "shipped_at": "2019-08-02T08:45:36.545Z",
      "state": "shipped",
      "order_id": "R666996643",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 308,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 284,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 308,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 284,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 284,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 209,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 397,
              "name": "ShippingCategory #7"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 1097,
          "quantity": 1,
          "states": {
            "shipped": 1
          }
        },
        {
          "variant_id": 1097,
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
          "adjustable_id": 322,
          "amount": "-10.0",
          "label": "Shipping",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-08-02T08:45:36.593Z",
          "updated_at": "2019-08-02T08:45:36.593Z",
          "display_amount": "-$10.00"
        },
        {
          "id": 91,
          "source_type": "Spree::PromotionAction",
          "source_id": 39,
          "adjustable_type": "Spree::Shipment",
          "adjustable_id": 322,
          "amount": "-9.99",
          "label": "Shipping",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-08-02T08:45:36.586Z",
          "updated_at": "2019-08-02T08:45:36.586Z",
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
      "adjustable_id": 398,
      "amount": "20.0",
      "label": "adj1",
      "promotion_code_id": null,
      "finalized": false,
      "eligible": true,
      "created_at": "2019-08-02T08:45:36.598Z",
      "updated_at": "2019-08-02T08:45:36.598Z",
      "display_amount": "$20.00"
    },
    {
      "id": 94,
      "source_type": "Spree::Promotion",
      "source_id": 57,
      "adjustable_type": "Spree::Order",
      "adjustable_id": 398,
      "amount": "30.0",
      "label": "adj2",
      "promotion_code_id": null,
      "finalized": false,
      "eligible": true,
      "created_at": "2019-08-02T08:45:36.601Z",
      "updated_at": "2019-08-02T08:45:36.601Z",
      "display_amount": "$30.00"
    }
  ],
  "permissions": {
    "can_update": false
  },
  "credit_cards": [
    {
      "id": 162,
      "month": "12",
      "year": "2020",
      "cc_type": null,
      "last_digits": "1111",
      "name": "Spree Commerce",
      "address": {
        "id": 832,
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
        "country_id": 450,
        "country_iso": "US",
        "state_id": 439,
        "state_name": null,
        "state_text": "AL",
        "country": {
          "id": 450,
          "iso_name": "UNITED STATES",
          "iso": "US",
          "iso3": "USA",
          "name": "United States",
          "numcode": 840
        },
        "state": {
          "id": 439,
          "name": "Alabama",
          "abbr": "AL",
          "country_id": 450
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
GET /api/orders/R341046524
Accept: application/json
Authorization: b90475a27af6973492919be80b8ff0ba0b568f06fb2af76a
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
X-Request-Id: 6ae175ce-4cd4-46b4-b4c1-bea8db025cfe
X-Runtime: 0.015373
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
user[email]=email21%40example.com
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
X-Request-Id: b4763b35-5180-4c66-bcc5-33dff231f6a1
X-Runtime: 0.023124
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
user[email]=email22%40example.com&user[password]=secret
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
Authorization: Bearer 8ee0aa7466c6c92c7602fb95ee541dcbc599b9b857c8c229
ETag: W/&quot;d78c4a1f5a9289ea79b08421986a1766&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: aadfb956-23ef-4420-9f7c-de99a164f4e7
X-Runtime: 0.004744
Content-Length: 553
200 OK
```


```json
{
  "id": 489,
  "email": "email22@example.com",
  "persistence_token": null,
  "perishable_token": null,
  "last_request_at": null,
  "login": "email22@example.com",
  "ship_address_id": null,
  "bill_address_id": null,
  "created_at": "2019-08-02T08:45:45.783Z",
  "updated_at": "2019-08-02T08:45:45.784Z",
  "spree_api_key": "8ee0aa7466c6c92c7602fb95ee541dcbc599b9b857c8c229",
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
X-Request-Id: cc56ddf9-241a-4edb-bd32-e01a454f515d
X-Runtime: 0.003288
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
Date: Fri, 02 Aug 2019 08:45:33 GMT
Surrogate-Control: max-age=900
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;e2295aba801967f43b1f310d86ea397f&quot;
X-Request-Id: e3c1322b-81cc-40de-9b2c-16ce6c67fc86
X-Runtime: 0.313953
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
      "id": 645,
      "name": "Product #1 - 3284",
      "description": "As seen on TV!",
      "available_on": "2018-08-02T08:45:33.435Z",
      "slug": "product-1-3284",
      "meta_description": null,
      "meta_keywords": null,
      "shipping_category_id": 391,
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
        "id": 1087,
        "name": "Product #1 - 3284",
        "sku": "SKU-1",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-1-3284",
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
GET /api/products/product-6-8290
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
Date: Fri, 02 Aug 2019 08:45:35 GMT
Surrogate-Control: max-age=900
Surrogate-Key: product_id=1
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;773b4a786a6b9ef1f846f1228c2f1aff&quot;
X-Request-Id: ffc1bcb1-7457-4c03-8419-2e06b7eb96e8
X-Runtime: 0.046647
Content-Length: 831
200 OK
```


```json
{
  "id": 650,
  "name": "Product #6 - 8290",
  "description": "As seen on TV!",
  "available_on": "2018-08-02T08:45:35.073Z",
  "slug": "product-6-8290",
  "meta_description": null,
  "meta_keywords": null,
  "shipping_category_id": 394,
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
    "id": 1092,
    "name": "Product #6 - 8290",
    "sku": "SKU-6",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": true,
    "slug": "product-6-8290",
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
X-Request-Id: 04a39c06-2229-4938-9823-2fdfe4b3de8a
X-Runtime: 0.024861
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
ETag: W/&quot;854da2ed91282ca1c311c122d94322b9&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 004ff766-710b-4b3c-9d20-ad85ac45c163
X-Runtime: 0.128991
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
      "id": 646,
      "name": "Product #2 - 6575",
      "description": "As seen on TV!",
      "available_on": "2018-08-02T08:45:34.177Z",
      "slug": "product-2-6575",
      "meta_description": null,
      "meta_keywords": null,
      "shipping_category_id": 392,
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
        "id": 1088,
        "name": "Product #2 - 6575",
        "sku": "SKU-2",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-2-6575",
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
ETag: W/&quot;1fd54c8d6818de8356f47f1493b14b4b&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: f31fdd02-402f-4adf-9470-10199d0df72f
X-Runtime: 0.050079
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
      "id": 648,
      "name": "Product #4 - 8039",
      "description": "As seen on TV!",
      "available_on": "2018-08-02T08:45:34.776Z",
      "slug": "product-4-8039",
      "meta_description": null,
      "meta_keywords": null,
      "shipping_category_id": 393,
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
        "id": 1090,
        "name": "Product #4 - 8039",
        "sku": "SKU-4",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-4-8039",
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

Get a single user return authorziation

## Can get another user&#39;s return authorization


### Request

#### Endpoint

```plaintext
GET /api/returns/RA760208630
Authorization: Bearer 872bebe09f1989ac9a60986491650eb623cfaf103281f0d6
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
ETag: W/&quot;90018568e3e38a5bcd1c3fd1cb68c5c4&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: b1feadeb-8042-409e-a6b9-af0589537e5b
X-Runtime: 0.039407
Content-Length: 2750
200 OK
```


```json
{
  "id": 18,
  "number": "RA760208630",
  "state": "authorized",
  "order_id": 410,
  "memo": "Items were broken",
  "created_at": "2019-08-02T08:45:46.606Z",
  "updated_at": "2019-08-02T08:45:46.606Z",
  "reason": {
    "id": 56,
    "name": "Defect #3",
    "active": true,
    "mutable": true,
    "created_at": "2019-08-02T08:45:46.603Z",
    "updated_at": "2019-08-02T08:45:46.603Z"
  },
  "order": {
    "id": 410,
    "number": "R333786204",
    "item_total": "10.0",
    "total": "110.0",
    "state": "complete",
    "adjustment_total": "0.0",
    "user_id": 492,
    "completed_at": "2019-08-02T08:45:46.547Z",
    "bill_address_id": 857,
    "ship_address_id": 858,
    "payment_total": "110.0",
    "shipment_state": "shipped",
    "payment_state": "paid",
    "email": "email25@example.com",
    "special_instructions": null,
    "created_at": "2019-08-02T08:45:46.490Z",
    "updated_at": "2019-08-02T08:45:46.592Z",
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
    "guest_token": "-vNZzkAwx9oW6_rgP91rsQ",
    "canceled_at": null,
    "canceler_id": null,
    "store_id": 444,
    "approver_name": null,
    "frontend_viewable": true
  },
  "ship_address": {
    "id": 858,
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
    "country_id": 463,
    "country_iso": "US",
    "state_id": 452,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 463,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 452,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 463
    }
  },
  "bill_address": {
    "id": 857,
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
    "country_id": 463,
    "country_iso": "US",
    "state_id": 452,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 463,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 452,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 463
    }
  },
  "return_items": [
    {
      "name": "Product #23 - 3125",
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
        "id": 165,
        "month": "12",
        "year": "2020",
        "cc_type": null,
        "last_digits": "1111",
        "name": "Spree Commerce",
        "gateway_customer_profile_id": "BGS-402315",
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
Authorization: Bearer 25789bba049307c55d41dcf9c09424c2664619d781715b20
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
ETag: W/&quot;73914ceca7223babaae7bc15274a903d&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 5dd12dc7-9eeb-4265-8c71-0f0fe34a9f95
X-Runtime: 0.007583
Content-Length: 164
200 OK
```


```json
{
  "return_authorizations": [
    {
      "number": "RA581677627",
      "created_at": "2019-08-02T08:45:47.368Z",
      "return_amount": "10.0",
      "order_number": "R689118190",
      "state": "authorized"
    }
  ]
}
```



## returns a 200


### Request

#### Endpoint

```plaintext
GET /api/returns/RA067330251
Authorization: Bearer 4a753b199b2be2daa93d43e1e53a69eaa4034cafcec2bbc9
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
ETag: W/&quot;3bb4274ab40654dd278ce8d41de71120&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 0e7c7cec-5cb2-49ba-98c7-bf6386a718eb
X-Runtime: 0.058994
Content-Length: 2673
200 OK
```


```json
{
  "id": 17,
  "number": "RA067330251",
  "state": "authorized",
  "order_id": 409,
  "memo": "Items were broken",
  "created_at": "2019-08-02T08:45:46.179Z",
  "updated_at": "2019-08-02T08:45:46.179Z",
  "reason": {
    "id": 54,
    "name": "Defect #1",
    "active": true,
    "mutable": true,
    "created_at": "2019-08-02T08:45:46.170Z",
    "updated_at": "2019-08-02T08:45:46.170Z"
  },
  "order": {
    "id": 409,
    "number": "R321439081",
    "item_total": "10.0",
    "total": "110.0",
    "state": "complete",
    "adjustment_total": "0.0",
    "user_id": 491,
    "completed_at": "2019-08-02T08:45:46.086Z",
    "bill_address_id": 855,
    "ship_address_id": 856,
    "payment_total": "110.0",
    "shipment_state": "shipped",
    "payment_state": "paid",
    "email": "email24@example.com",
    "special_instructions": null,
    "created_at": "2019-08-02T08:45:46.032Z",
    "updated_at": "2019-08-02T08:45:46.134Z",
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
    "guest_token": "YeLrFrvz4oaNqxOj0Mz4dw",
    "canceled_at": null,
    "canceler_id": null,
    "store_id": 443,
    "approver_name": null,
    "frontend_viewable": true
  },
  "ship_address": {
    "id": 856,
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
    "country_id": 462,
    "country_iso": "US",
    "state_id": 451,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 462,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 451,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 462
    }
  },
  "bill_address": {
    "id": 855,
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
    "country_id": 462,
    "country_iso": "US",
    "state_id": 451,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 462,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 451,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 462
    }
  },
  "return_items": [
    {
      "name": "Product #22 - 8181",
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
        "id": 396,
        "name": "Credit Card"
      },
      "source": {
        "id": 164,
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
GET /api/returns/RA242518543
Authorization: Bearer a0ada77c537db19d434396eb5f48b361d5c4cbdabc20f820
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
X-Request-Id: 1539ae45-aab1-4a7a-9b83-5e90c015f079
X-Runtime: 0.007627
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
Authorization: Bearer 6197f4b38396818ba030afdd7abeba9aed6601df0216c9d5
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
ETag: W/&quot;09cac4d98ce096f6bb0b7b364c9b527f&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: e9e3005f-70d6-45f2-92f8-4608482aaaea
X-Runtime: 0.031767
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
      "created_at": "2019-08-02T08:45:44.113Z"
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
Authorization: Bearer 73d70dfb2fa10fce44faa9dff48652fa0fa17f59fc005ad8
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
Authorization: Bearer 73d70dfb2fa10fce44faa9dff48652fa0fa17f59fc005ad8
ETag: W/&quot;e97d4e7f00a15d47209240ebfb588c03&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 7d8ce56a-e4ed-40f0-a695-ac336b8579e5
X-Runtime: 0.008966
Content-Length: 125
200 OK
```


```json
{
  "email": "email14@example.com",
  "first_name": null,
  "last_name": null,
  "id": 481,
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
user[email]=email13%40example.com&user[password]=secret
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
Authorization: Bearer 8d2e06c8a0db6571ab360831bdd6777d2a8d9e15911a9ea4
ETag: W/&quot;6a0e7ef5f7324c0678372517f15c6925&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 75e0396b-ab1a-4405-b91a-7f72d286b69e
X-Runtime: 0.007742
Content-Length: 553
200 OK
```


```json
{
  "id": 479,
  "email": "email13@example.com",
  "persistence_token": null,
  "perishable_token": null,
  "last_request_at": null,
  "login": "email13@example.com",
  "ship_address_id": null,
  "bill_address_id": null,
  "created_at": "2019-08-02T08:45:44.258Z",
  "updated_at": "2019-08-02T08:45:44.262Z",
  "spree_api_key": "8d2e06c8a0db6571ab360831bdd6777d2a8d9e15911a9ea4",
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
Authorization: Bearer 70c00348d7bb35dd7174467512aac807730f22786625b4bd
ETag: W/&quot;ed076f308990128f84b0437403363f98&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 76cc14c7-a3bb-446a-8f9e-3126814f7d89
X-Runtime: 0.026128
Content-Length: 157
201 Created
```


```json
{
  "id": 480,
  "email": "test@example.com",
  "created_at": "2019-08-02T08:45:44.280Z",
  "updated_at": "2019-08-02T08:45:44.282Z",
  "bill_address": null,
  "ship_address": null
}
```



# Variant



## Fetching a variant


### Request

#### Endpoint

```plaintext
GET /api/variants/1101
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
ETag: W/&quot;5d3bad2e738c63c75dd1539ee47d2692&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 1e5b9790-0d78-4499-be39-d64885485c6f
X-Runtime: 0.098016
Content-Length: 1458
200 OK
```


```json
{
  "id": 1101,
  "name": "Product #11 - 3751",
  "sku": "SKU-14",
  "weight": "0.0",
  "height": null,
  "width": null,
  "depth": null,
  "is_master": false,
  "slug": "product-11-3751",
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
      "id": 458,
      "name": "Size-4",
      "presentation": "S",
      "option_type_name": "foo-size-4",
      "option_type_id": 458,
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
      "attachment_updated_at": "2019-08-02T08:45:37.581Z",
      "attachment_width": 489,
      "attachment_height": 490,
      "alt": null,
      "viewable_type": "Spree::Variant",
      "viewable_id": 1101,
      "mini_url": "/spree/products/2/mini/thinking-cat.jpg?1564735537",
      "small_url": "/spree/products/2/small/thinking-cat.jpg?1564735537",
      "product_url": "/spree/products/2/product/thinking-cat.jpg?1564735537",
      "large_url": "/spree/products/2/large/thinking-cat.jpg?1564735537"
    }
  ],
  "variant_properties": [

  ],
  "stock_items": [

  ],
  "prices": [
    {
      "id": 2126,
      "vendor_id": 3292,
      "price": "10.0",
      "original_price": "10.0",
      "discount_percent": 0.0,
      "total_on_hand": 0,
      "country_iso": null,
      "final_sale": false,
      "on_sale": false
    },
    {
      "id": 2127,
      "vendor_id": 3293,
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
Authorization: Bearer 65926c5aca23c4e6c9f75768c11da1577c5e0e4fa6c898ca
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
ETag: W/&quot;a46012c12d1469972191d3ed768d8197&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 79c5407f-8ee0-4155-a6f9-a91775d50d68
X-Runtime: 0.015230
Content-Length: 199
200 OK
```


```json
[
  {
    "id": 33,
    "user_id": 483,
    "payment_source_type": "SolidusPaypalBraintree::Source",
    "payment_source_id": 58,
    "default": false,
    "created_at": "2019-08-02T08:45:44.403Z",
    "updated_at": "2019-08-02T08:45:44.403Z"
  }
]
```



## Remove the payment from the user wallet


### Request

#### Endpoint

```plaintext
DELETE /api/wallet_payment_sources/34
Accept: application/json
Authorization: Bearer 540cd83046219630296a7c4eb9bc1a2b1efc7c81d7981310
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
X-Request-Id: f045cc2a-bdce-4b52-9480-87eaa4f656df
X-Runtime: 0.015379
204 No Content
```




## Set a wallet payment source as the default user payment method


### Request

#### Endpoint

```plaintext
POST /api/wallet_payment_sources/32/default
Accept: application/json
Authorization: Bearer d12914bd2aaad5857368866443e95a8372d06172687697cf
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
X-Request-Id: 1605c3d2-8cfc-4883-bc65-ee450c517999
X-Runtime: 0.034087
204 No Content
```




