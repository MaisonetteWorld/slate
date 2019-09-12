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
PUT /api/orders/R778868737/addresses/21
Accept: application/json
X-Spree-Order-Token: SxnB8e0xmpDcFIbSZ_ED9Q
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
ETag: W/&quot;9d4efc4c2d57c3f6bd24afeb6c3b837d&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 0cfd70a1-056b-407d-8125-5adff5a8ed66
X-Runtime: 0.065930
Vary: Origin
Content-Length: 507
200 OK
```


```json
{
  "id": 22,
  "firstname": "John the Tester",
  "lastname": null,
  "full_name": "John the Tester",
  "address1": "A Different Road",
  "address2": "Northwest",
  "city": "Herndon",
  "zipcode": "10021",
  "phone": "555-555-0199",
  "company": "Company",
  "alternative_phone": "555-555-0199",
  "country_id": 22,
  "country_iso": "US",
  "state_id": 22,
  "state_name": null,
  "state_text": "AL",
  "country": {
    "id": 22,
    "iso_name": "UNITED STATES",
    "iso": "US",
    "iso3": "USA",
    "name": "United States",
    "numcode": 840
  },
  "state": {
    "id": 22,
    "name": "Alabama",
    "abbr": "AL",
    "country_id": 22
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
X-Spree-Order-Token: 4YxX5kfdBkpBgYI8vY9HWA
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/braintree/transactions`

#### Parameters


```json
order_id=R786857237&payment_method_id=19&options[restart_checkout]=true&transaction[email]=maryellen.oga%40mckenziemcglynn.com&transaction[nonce]=fake-paypal-billing-agreement-nonce&transaction[phone]=555-555-0199&transaction[address_attributes][first_name]=John&transaction[address_attributes][last_name]=Stamm&transaction[address_attributes][address_line_1]=A+Different+Road&transaction[address_attributes][city]=Herndon&transaction[address_attributes][state_code]=AL&transaction[address_attributes][zip]=10030&transaction[address_attributes][country_code]=US&transaction[payment_type]=PayPalAccount
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
ETag: W/&quot;c9bbcc3577868621a421bb13a35ca088&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 66b7ae22-e8f0-454a-b4b3-b3781d03fbd1
X-Runtime: 0.252396
Vary: Origin
Content-Length: 4795
200 OK
```


```json
{
  "id": 16,
  "number": "R786857237",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2019-09-12T09:46:39.541-04:00",
  "updated_at": "2019-09-12T09:46:39.793-04:00",
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
  "token": "4YxX5kfdBkpBgYI8vY9HWA",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 19,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 34,
    "firstname": "John",
    "lastname": "Stamm",
    "full_name": "John Stamm",
    "address1": "A Different Road",
    "address2": null,
    "city": "Herndon",
    "zipcode": "10030",
    "phone": "555-555-0199",
    "company": null,
    "alternative_phone": null,
    "country_id": 27,
    "country_iso": "US",
    "state_id": 27,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 27,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 27,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 27
    }
  },
  "ship_address": {
    "id": 34,
    "firstname": "John",
    "lastname": "Stamm",
    "full_name": "John Stamm",
    "address1": "A Different Road",
    "address2": null,
    "city": "Herndon",
    "zipcode": "10030",
    "phone": "555-555-0199",
    "company": null,
    "alternative_phone": null,
    "country_id": 27,
    "country_iso": "US",
    "state_id": 27,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 27,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 27,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 27
    }
  },
  "line_items": [
    {
      "id": 16,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 98,
      "vendor_id": 157,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 98,
        "name": "Product #49 - 3742",
        "sku": "SKU-97",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-49-3742",
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
            "id": 49,
            "name": "Size-49",
            "presentation": "S",
            "option_type_name": "foo-size-49",
            "option_type_id": 49,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 49,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #157",
      "country_iso": "US",
      "adjustments": [

      ]
    }
  ],
  "payments": [
    {
      "id": 7,
      "source_type": "SolidusPaypalBraintree::Source",
      "source_id": 7,
      "amount": "110.0",
      "display_amount": "$110.00",
      "payment_method_id": 19,
      "state": "checkout",
      "avs_response": null,
      "created_at": "2019-09-12T09:46:39.641-04:00",
      "updated_at": "2019-09-12T09:46:39.641-04:00",
      "payment_method": {
        "id": 19,
        "name": "Braintree"
      },
      "source": {
        "id": 7,
        "payment_type": "PayPalAccount",
        "token": "bgx899",
        "created_at": "2019-09-12T09:46:39.640-04:00",
        "email": "jane.doe@paypal.com"
      }
    }
  ],
  "shipments": [
    {
      "id": 21,
      "tracking": null,
      "tracking_url": null,
      "number": "H80454844588",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R786857237",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 21,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 15,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 21,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 15,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 15,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 15,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 26,
              "name": "ShippingCategory #26"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 98,
          "quantity": 1,
          "states": {
            "on_hand": 1
          }
        }
      ],
      "adjustments": [

      ],
      "stock_location_address": "NY Warehouse, Washington, AL",
      "country_iso": "US",
      "international_shipping": false,
      "delivery_estimation": "Sep 16"
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
X-Spree-Order-Token: oosK3YPBQDTWyvFLw34AaA
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/braintree/transactions`

#### Parameters


```json
order_id=R431732570&payment_method_id=18&options[restart_checkout]=true&transaction[email]=maryellen.oga%40mckenziemcglynn.com&transaction[nonce]=fake-apple-pay-visa-nonce&transaction[phone]=555-555-0199&transaction[address_attributes][first_name]=John&transaction[address_attributes][last_name]=Stamm&transaction[address_attributes][address_line_1]=A+Different+Road&transaction[address_attributes][city]=Herndon&transaction[address_attributes][state_code]=AL&transaction[address_attributes][zip]=10028&transaction[address_attributes][country_code]=US&transaction[payment_type]=ApplePayCard
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
ETag: W/&quot;ac439b5851aea0dd04da6340256c21cf&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 1db4d5ca-3f22-44a8-9b2d-bc150dea312a
X-Runtime: 0.271982
Vary: Origin
Content-Length: 4841
200 OK
```


```json
{
  "id": 15,
  "number": "R431732570",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2019-09-12T09:46:38.994-04:00",
  "updated_at": "2019-09-12T09:46:39.279-04:00",
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
  "token": "oosK3YPBQDTWyvFLw34AaA",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 18,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 31,
    "firstname": "John",
    "lastname": "Stamm",
    "full_name": "John Stamm",
    "address1": "A Different Road",
    "address2": null,
    "city": "Herndon",
    "zipcode": "10028",
    "phone": "555-555-0199",
    "company": null,
    "alternative_phone": null,
    "country_id": 26,
    "country_iso": "US",
    "state_id": 26,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 26,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 26,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 26
    }
  },
  "ship_address": {
    "id": 31,
    "firstname": "John",
    "lastname": "Stamm",
    "full_name": "John Stamm",
    "address1": "A Different Road",
    "address2": null,
    "city": "Herndon",
    "zipcode": "10028",
    "phone": "555-555-0199",
    "company": null,
    "alternative_phone": null,
    "country_id": 26,
    "country_iso": "US",
    "state_id": 26,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 26,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 26,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 26
    }
  },
  "line_items": [
    {
      "id": 15,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 96,
      "vendor_id": 152,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 96,
        "name": "Product #48 - 2275",
        "sku": "SKU-95",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-48-2275",
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
            "id": 48,
            "name": "Size-48",
            "presentation": "S",
            "option_type_name": "foo-size-48",
            "option_type_id": 48,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 48,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #152",
      "country_iso": "US",
      "adjustments": [

      ]
    }
  ],
  "payments": [
    {
      "id": 6,
      "source_type": "SolidusPaypalBraintree::Source",
      "source_id": 6,
      "amount": "110.0",
      "display_amount": "$110.00",
      "payment_method_id": 18,
      "state": "checkout",
      "avs_response": null,
      "created_at": "2019-09-12T09:46:39.139-04:00",
      "updated_at": "2019-09-12T09:46:39.139-04:00",
      "payment_method": {
        "id": 18,
        "name": "Braintree"
      },
      "source": {
        "id": 6,
        "payment_type": "ApplePayCard",
        "token": "cg7hsk",
        "created_at": "2019-09-12T09:46:39.137-04:00",
        "cc_type": "Apple Pay - Visa",
        "last_digits": "1881",
        "month": "12",
        "year": "2020"
      }
    }
  ],
  "shipments": [
    {
      "id": 19,
      "tracking": null,
      "tracking_url": null,
      "number": "H23600426151",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R431732570",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 19,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 14,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 19,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 14,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 14,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 14,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 25,
              "name": "ShippingCategory #25"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 96,
          "quantity": 1,
          "states": {
            "on_hand": 1
          }
        }
      ],
      "adjustments": [

      ],
      "stock_location_address": "NY Warehouse, Washington, AL",
      "country_iso": "US",
      "international_shipping": false,
      "delivery_estimation": "Sep 16"
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
PUT /api/checkouts/R760933696/complete
Accept: application/json
X-Spree-Order-Token: 0t3ePkrSJNk7ggaPfdv0_g
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
ETag: W/&quot;565d91005d04d09d8c7cff8dab2acf31&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 3acdd3d6-18b3-4f82-9fd3-a9318d2af5b5
X-Runtime: 2.331311
Vary: Origin
Content-Length: 4940
200 OK
```


```json
{
  "id": 6,
  "number": "R760933696",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "complete",
  "adjustment_total": "0.0",
  "user_id": 24,
  "created_at": "2019-09-12T09:46:24.571-04:00",
  "updated_at": "2019-09-12T09:46:27.864-04:00",
  "completed_at": "2019-09-12T09:46:27.864-04:00",
  "payment_total": "110.0",
  "shipment_state": "ready",
  "payment_state": "paid",
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
  "token": "0t3ePkrSJNk7ggaPfdv0_g",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 5,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    },
    {
      "id": 6,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 10,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "PO Box 1337",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10010",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 9,
    "country_iso": "US",
    "state_id": 9,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 9,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 9,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 9
    }
  },
  "ship_address": {
    "id": 11,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "A Different Road",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10011",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 9,
    "country_iso": "US",
    "state_id": 9,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 9,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 9,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 9
    }
  },
  "line_items": [
    {
      "id": 6,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 30,
      "vendor_id": 48,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 30,
        "name": "Product #15 - 7058",
        "sku": "SKU-29",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-15-7058",
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
            "id": 15,
            "name": "Size-15",
            "presentation": "S",
            "option_type_name": "foo-size-15",
            "option_type_id": 15,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 15,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #48",
      "country_iso": "US",
      "adjustments": [

      ]
    }
  ],
  "payments": [
    {
      "id": 1,
      "source_type": "SolidusPaypalBraintree::Source",
      "source_id": 2,
      "amount": "110.0",
      "display_amount": "$110.00",
      "payment_method_id": 5,
      "state": "completed",
      "avs_response": "M",
      "created_at": "2019-09-12T09:46:24.674-04:00",
      "updated_at": "2019-09-12T09:46:27.635-04:00",
      "payment_method": {
        "id": 5,
        "name": "Braintree"
      },
      "source": {
        "id": 2,
        "payment_type": "CreditCard",
        "token": "c7sswv",
        "created_at": "2019-09-12T09:46:24.673-04:00",
        "cc_type": "Visa",
        "last_digits": "1881",
        "month": "12",
        "year": "2020"
      }
    }
  ],
  "shipments": [
    {
      "id": 10,
      "tracking": "U10000",
      "tracking_url": null,
      "number": "H64435022170",
      "cost": "100.0",
      "shipped_at": null,
      "state": "ready",
      "order_id": "R760933696",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 10,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 6,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 10,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 6,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 6,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 6,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 9,
              "name": "ShippingCategory #9"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 30,
          "quantity": 1,
          "states": {
            "on_hand": 1
          }
        }
      ],
      "adjustments": [

      ],
      "stock_location_address": "NY Warehouse, Washington, AL",
      "country_iso": "US",
      "international_shipping": false,
      "delivery_estimation": "Sep 16"
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
PATCH /api/checkouts/R793148067
Accept: application/json
X-Spree-Order-Token: 4d3Zq6N2TqGsSLIyV9mCvg
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=4&order[payment_attributes][][source_attributes][nonce]=fake-apple-pay-visa-nonce&order[payment_attributes][][source_attributes][payment_type]=ApplePayCard
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
ETag: W/&quot;1fd4e142ed5c71252ee9871f6265511b&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 8a5c331c-e00e-4381-b85f-7eb55b643945
X-Runtime: 0.098474
Vary: Origin
Content-Length: 4322
200 OK
```


```json
{
  "id": 5,
  "number": "R793148067",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 23,
  "created_at": "2019-09-12T09:46:24.067-04:00",
  "updated_at": "2019-09-12T09:46:24.300-04:00",
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
  "token": "4d3Zq6N2TqGsSLIyV9mCvg",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 4,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 8,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "PO Box 1337",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10008",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 8,
    "country_iso": "US",
    "state_id": 8,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 8,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 8,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 8
    }
  },
  "ship_address": {
    "id": 9,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "A Different Road",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10009",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 8,
    "country_iso": "US",
    "state_id": 8,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 8,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 8,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 8
    }
  },
  "line_items": [
    {
      "id": 5,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 28,
      "vendor_id": 43,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 28,
        "name": "Product #14 - 1305",
        "sku": "SKU-27",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-14-1305",
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
            "id": 14,
            "name": "Size-14",
            "presentation": "S",
            "option_type_name": "foo-size-14",
            "option_type_id": 14,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 14,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #43",
      "country_iso": "US",
      "adjustments": [

      ]
    }
  ],
  "payments": [

  ],
  "shipments": [
    {
      "id": 9,
      "tracking": null,
      "tracking_url": null,
      "number": "H78732460466",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R793148067",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 9,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 5,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 9,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 5,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 5,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 5,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 8,
              "name": "ShippingCategory #8"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 28,
          "quantity": 1,
          "states": {
            "on_hand": 1
          }
        }
      ],
      "adjustments": [

      ],
      "stock_location_address": "NY Warehouse, Washington, AL",
      "country_iso": "US",
      "international_shipping": false,
      "delivery_estimation": "Sep 16"
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
PATCH /api/checkouts/R677449130
Accept: application/json
X-Spree-Order-Token: XIYi1SJ-COycllXyUXROBw
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=3&order[payment_attributes][][source_attributes][nonce]=fake-paypal-billing-agreement-nonce&order[payment_attributes][][source_attributes][payment_type]=PayPalAccount
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
ETag: W/&quot;34cde6c138d48925957b70cf0bced6b9&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 89007b66-bdfc-49f3-a0ee-c549706f7a81
X-Runtime: 0.098593
Vary: Origin
Content-Length: 4322
200 OK
```


```json
{
  "id": 4,
  "number": "R677449130",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 22,
  "created_at": "2019-09-12T09:46:23.578-04:00",
  "updated_at": "2019-09-12T09:46:23.824-04:00",
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
  "token": "XIYi1SJ-COycllXyUXROBw",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 3,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 6,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "PO Box 1337",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10006",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 7,
    "country_iso": "US",
    "state_id": 7,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 7,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 7,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 7
    }
  },
  "ship_address": {
    "id": 7,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "A Different Road",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10007",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 7,
    "country_iso": "US",
    "state_id": 7,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 7,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 7,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 7
    }
  },
  "line_items": [
    {
      "id": 4,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 26,
      "vendor_id": 38,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 26,
        "name": "Product #13 - 4587",
        "sku": "SKU-25",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-13-4587",
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
            "id": 13,
            "name": "Size-13",
            "presentation": "S",
            "option_type_name": "foo-size-13",
            "option_type_id": 13,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 13,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #38",
      "country_iso": "US",
      "adjustments": [

      ]
    }
  ],
  "payments": [

  ],
  "shipments": [
    {
      "id": 7,
      "tracking": null,
      "tracking_url": null,
      "number": "H68444076341",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R677449130",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 7,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 4,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 7,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 4,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 4,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 4,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 7,
              "name": "ShippingCategory #7"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 26,
          "quantity": 1,
          "states": {
            "on_hand": 1
          }
        }
      ],
      "adjustments": [

      ],
      "stock_location_address": "NY Warehouse, Washington, AL",
      "country_iso": "US",
      "international_shipping": false,
      "delivery_estimation": "Sep 16"
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
PATCH /api/checkouts/R215930772
Accept: application/json
X-Spree-Order-Token: qrQFkI4Zy9Vyn3Gjqx9rCA
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=2&order[payment_attributes][][source_attributes][nonce]=fake-valid-visa-nonce&order[payment_attributes][][source_attributes][payment_type]=CreditCard
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
ETag: W/&quot;50a18133817433275fbc0e05b80c4945&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 28cc63a6-66e8-4a28-82d6-03ddb0f263fe
X-Runtime: 0.134616
Vary: Origin
Content-Length: 4322
200 OK
```


```json
{
  "id": 3,
  "number": "R215930772",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 21,
  "created_at": "2019-09-12T09:46:22.934-04:00",
  "updated_at": "2019-09-12T09:46:23.274-04:00",
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
  "token": "qrQFkI4Zy9Vyn3Gjqx9rCA",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 2,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 4,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "PO Box 1337",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10004",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 6,
    "country_iso": "US",
    "state_id": 6,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 6,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 6,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 6
    }
  },
  "ship_address": {
    "id": 5,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "A Different Road",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10005",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 6,
    "country_iso": "US",
    "state_id": 6,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 6,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 6,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 6
    }
  },
  "line_items": [
    {
      "id": 3,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 24,
      "vendor_id": 33,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 24,
        "name": "Product #12 - 4218",
        "sku": "SKU-23",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-12-4218",
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
            "id": 12,
            "name": "Size-12",
            "presentation": "S",
            "option_type_name": "foo-size-12",
            "option_type_id": 12,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 12,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #33",
      "country_iso": "US",
      "adjustments": [

      ]
    }
  ],
  "payments": [

  ],
  "shipments": [
    {
      "id": 5,
      "tracking": null,
      "tracking_url": null,
      "number": "H85247583408",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R215930772",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 5,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 3,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 5,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 3,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 3,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 3,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 6,
              "name": "ShippingCategory #6"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 24,
          "quantity": 1,
          "states": {
            "on_hand": 1
          }
        }
      ],
      "adjustments": [

      ],
      "stock_location_address": "NY Warehouse, Washington, AL",
      "country_iso": "US",
      "international_shipping": false,
      "delivery_estimation": "Sep 16"
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
PATCH /api/checkouts/R140725480
Accept: application/json
X-Spree-Order-Token: XWQt4WbjubAyfcFJJquMnA
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=1&order[payment_attributes][][source_attributes][wallet_payment_source_id]=1
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
ETag: W/&quot;607e0d47aae50e0afab4bbb66b346d5f&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 1d77d931-7bc3-43e6-8ba1-c624c3a9b668
X-Runtime: 0.117312
Vary: Origin
Content-Length: 4322
200 OK
```


```json
{
  "id": 2,
  "number": "R140725480",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 20,
  "created_at": "2019-09-12T09:46:22.246-04:00",
  "updated_at": "2019-09-12T09:46:22.636-04:00",
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
  "token": "XWQt4WbjubAyfcFJJquMnA",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 1,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 2,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "PO Box 1337",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10002",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 5,
    "country_iso": "US",
    "state_id": 5,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 5,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 5,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 5
    }
  },
  "ship_address": {
    "id": 3,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "A Different Road",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10003",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 5,
    "country_iso": "US",
    "state_id": 5,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 5,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 5,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 5
    }
  },
  "line_items": [
    {
      "id": 2,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 22,
      "vendor_id": 28,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 22,
        "name": "Product #11 - 1252",
        "sku": "SKU-21",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-11-1252",
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
            "id": 11,
            "name": "Size-11",
            "presentation": "S",
            "option_type_name": "foo-size-11",
            "option_type_id": 11,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 11,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #28",
      "country_iso": "US",
      "adjustments": [

      ]
    }
  ],
  "payments": [

  ],
  "shipments": [
    {
      "id": 3,
      "tracking": null,
      "tracking_url": null,
      "number": "H11352147024",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R140725480",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 3,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 2,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 3,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 2,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 2,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 2,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 5,
              "name": "ShippingCategory #5"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 22,
          "quantity": 1,
          "states": {
            "on_hand": 1
          }
        }
      ],
      "adjustments": [

      ],
      "stock_location_address": "NY Warehouse, Washington, AL",
      "country_iso": "US",
      "international_shipping": false,
      "delivery_estimation": "Sep 16"
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



## update address


### Request

#### Endpoint

```plaintext
PUT /api/checkouts/R474201752
Accept: application/json
X-Spree-Order-Token: VAG4ga9WAFIaqErZ58a5_g
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PUT /api/checkouts/:id`

#### Parameters


```json
order[ship_address_attributes][id]&order[ship_address_attributes][firstname]=John&order[ship_address_attributes][lastname]&order[ship_address_attributes][address1]=10+Lovely+Street&order[ship_address_attributes][address2]=Northwest&order[ship_address_attributes][city]=Herndon&order[ship_address_attributes][zipcode]=10001&order[ship_address_attributes][phone]=555-555-0199&order[ship_address_attributes][state_name]&order[ship_address_attributes][alternative_phone]=555-555-0199&order[ship_address_attributes][company]=Company&order[ship_address_attributes][state_id]=4&order[ship_address_attributes][country_id]=4&order[ship_address_attributes][created_at]&order[ship_address_attributes][updated_at]&order[use_billing]=true&hold_state=true
```


| Name | Description |
|:-----|:------------|
| id *required* | The order number |
| order[ship_address_attributes] *required* | Order ship address attributes |
| order[bill_address_attributes]  | Order bill address attributes |
| order[use_billing]  | when `true` set billing address equal to shipping |
| hold_state  | skip state transiction |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
ETag: W/&quot;4d94be16a730bdb56e3a6db7fbcf9aba&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: e4413e3b-fdb7-466d-b149-355aace5e1e5
X-Runtime: 0.218198
Vary: Origin
Content-Length: 4230
200 OK
```


```json
{
  "id": 1,
  "number": "R474201752",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "cart",
  "adjustment_total": "0.0",
  "user_id": 19,
  "created_at": "2019-09-12T09:46:21.573-04:00",
  "updated_at": "2019-09-12T09:46:21.847-04:00",
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
  "total_applicable_store_credit": 0,
  "display_total_available_store_credit": "$0.00",
  "display_store_credit_remaining_after_capture": "$0.00",
  "canceler_id": null,
  "display_item_total": "$10.00",
  "total_quantity": 1,
  "display_total": "$110.00",
  "display_ship_total": "$100.00",
  "display_tax_total": "$0.00",
  "token": "VAG4ga9WAFIaqErZ58a5_g",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [

  ],
  "bill_address": {
    "id": 1,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "10 Lovely Street",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10001",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 4,
    "country_iso": "US",
    "state_id": 4,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 4,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 4,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 4
    }
  },
  "ship_address": {
    "id": 1,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "10 Lovely Street",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10001",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 4,
    "country_iso": "US",
    "state_id": 4,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 4,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 4,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 4
    }
  },
  "line_items": [
    {
      "id": 1,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 20,
      "vendor_id": 23,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 20,
        "name": "Product #10 - 4425",
        "sku": "SKU-19",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-10-4425",
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
            "id": 10,
            "name": "Size-10",
            "presentation": "S",
            "option_type_name": "foo-size-10",
            "option_type_id": 10,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 10,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #23",
      "country_iso": "US",
      "adjustments": [

      ]
    }
  ],
  "payments": [

  ],
  "shipments": [
    {
      "id": 1,
      "tracking": "U10000",
      "tracking_url": null,
      "number": "H51880666000",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R474201752",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 1,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 1,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 1,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 1,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 1,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 1,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 4,
              "name": "ShippingCategory #4"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 20,
          "quantity": 1,
          "states": {
            "on_hand": 1
          }
        }
      ],
      "adjustments": [

      ],
      "stock_location_address": "NY Warehouse, Washington, AL",
      "country_iso": "US",
      "international_shipping": false,
      "delivery_estimation": "Sep 16"
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
POST /api/orders/R075504732/line_items
Accept: application/json
X-Spree-Order-Token: dPJZEQINuvTScZcOhQlzwA
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/:order_number/line_items`

#### Parameters


```json
line_item[variant_id]=90&line_item[options][vendor_id]=137
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
ETag: W/&quot;84d4486e4c17797230cd9bd9c28f61bc&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: c7dfb506-8c83-4c1e-bed3-07aa891e84ef
X-Runtime: 0.203470
Vary: Origin
Content-Length: 880
201 Created
```


```json
{
  "id": 12,
  "quantity": 1,
  "price": "19.99",
  "variant_id": 90,
  "vendor_id": 137,
  "single_display_amount": "$19.99",
  "display_amount": "$19.99",
  "total": "19.99",
  "on_sale": false,
  "final_sale": false,
  "backordered": null,
  "promotionable": true,
  "variant": {
    "id": 90,
    "name": "Product #45 - 9601",
    "sku": "SKU-89",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": false,
    "slug": "product-45-9601",
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
        "id": 45,
        "name": "Size-45",
        "presentation": "S",
        "option_type_name": "foo-size-45",
        "option_type_id": 45,
        "option_type_presentation": "Size"
      }
    ],
    "images": [

    ],
    "product_id": 45,
    "brand": null,
    "brand_slug": null,
    "brand_description": null
  },
  "vendor_name": "Vendor #137",
  "country_iso": null,
  "adjustments": [

  ]
}
```



## Deleting a line item


### Request

#### Endpoint

```plaintext
DELETE /api/orders/R672501403/line_items/14
Accept: application/json
X-Spree-Order-Token: 1l6g8FxRbAs7PLbxcXS2Tg
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
X-Request-Id: b5fb9368-9c06-48d1-bffd-27e4e3ae12b8
X-Runtime: 0.129362
Vary: Origin
204 No Content
```




## Updating a line item


### Request

#### Endpoint

```plaintext
PUT /api/orders/R253827212/line_items/13
Accept: application/json
X-Spree-Order-Token: MHg0CRmfsgq2dWnQepbDaA
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
ETag: W/&quot;df1eadaed19aacc2ec27c8a6ff6d45a6&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 0e706b25-9f6c-431d-ba73-26c7c1d37370
X-Runtime: 0.171320
Vary: Origin
Content-Length: 877
200 OK
```


```json
{
  "id": 13,
  "quantity": 2,
  "price": "10.0",
  "variant_id": 92,
  "vendor_id": 142,
  "single_display_amount": "$10.00",
  "display_amount": "$20.00",
  "total": "20.0",
  "on_sale": false,
  "final_sale": false,
  "backordered": null,
  "promotionable": true,
  "variant": {
    "id": 92,
    "name": "Product #46 - 5847",
    "sku": "SKU-91",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": false,
    "slug": "product-46-5847",
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
        "id": 46,
        "name": "Size-46",
        "presentation": "S",
        "option_type_name": "foo-size-46",
        "option_type_id": 46,
        "option_type_presentation": "Size"
      }
    ],
    "images": [

    ],
    "product_id": 46,
    "brand": null,
    "brand_slug": null,
    "brand_description": null
  },
  "vendor_name": "Vendor #142",
  "country_iso": "US",
  "adjustments": [

  ]
}
```



# Minis

Get a single mini, accessible by owner of the mini or admin

## Create a mini


### Request

#### Endpoint

```plaintext
POST /api/minis
Accept: application/json
Authorizat IO N: Bearer f0003187014bd4c7a6ad03807db597e47a9c193523d936e7
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/minis`

#### Parameters


```json
mini[name]=Winny&mini[user_id]=61&mini[birth_year]=2019&mini[birth_month]=1&mini[birth_day]=1
```


| Name | Description |
|:-----|:------------|
| mini[name] *required* | Mini name |
| mini[user_id]  | User ID must match that of the current_api_user unless the current_api_user is an admin.                 User ID will be inferred from the current_api_user unless explicitly provided |
| mini[birth_year] *required* | Mini birth year |
| mini[birth_month]  | Mini birth month |
| mini[birth_day]  | Mini birth day |
| mini[gender_boy]  | Mini gender boy |
| mini[gender_girl]  | Mini gender girl |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
ETag: W/&quot;ca2e2682d97dd2fbf876c27937071b38&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 357bc8e9-b101-46b5-955e-445d0544f8b5
X-Runtime: 0.008658
Vary: Origin
Content-Length: 121
201 Created
```


```json
{
  "id": 2,
  "user_id": 61,
  "name": "Winny",
  "birth_year": 2019,
  "birth_month": 1,
  "birth_day": 1,
  "gender_boy": true,
  "gender_girl": true
}
```



## Delete a mini


### Request

#### Endpoint

```plaintext
DELETE /api/minis/18
Accept: application/json
Authorizat IO N: Bearer 23d9be174369e841068981f3bb2af1d2b0754a733447d142
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`DELETE /api/minis/:id`

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
X-Request-Id: 27f5c50b-678b-404c-9b4f-3ae5f6709259
X-Runtime: 0.009256
Vary: Origin
204 No Content
```




## Get a single mini


### Request

#### Endpoint

```plaintext
GET /api/minis/1
Accept: application/json
Authorizat IO N: Bearer 2fd685a7d11481370e0699f06997ca07106752bf504194a5
Host: example.org
Cookie: 
```

`GET /api/minis/:id`

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
ETag: W/&quot;21a89b3ffd32b1b28baf7abf9982ec71&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: bb58e45d-8d93-48e6-a596-23e972da4191
X-Runtime: 0.029280
Vary: Origin
Content-Length: 126
200 OK
```


```json
{
  "id": 1,
  "user_id": 60,
  "name": "Mini",
  "birth_year": 2018,
  "birth_month": null,
  "birth_day": null,
  "gender_boy": true,
  "gender_girl": true
}
```



## Get all minis


### Request

#### Endpoint

```plaintext
GET /api/minis
Accept: application/json
Authorizat IO N: Bearer fbcda976d3652b4f1468f80e594a4333fcb10a4e5efefad1
Host: example.org
Cookie: 
```

`GET /api/minis`

#### Parameters



| Name | Description |
|:-----|:------------|
| q[user_id_eq]  | Anything accessible by ransack can be passed in as query params |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
ETag: W/&quot;2db486d366d5335cca8812793ce6c3ef&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 03dd722a-4b11-4075-9d91-2310668656ff
X-Runtime: 0.014150
Vary: Origin
Content-Length: 1353
200 OK
```


```json
{
  "minis": [
    {
      "id": 3,
      "user_id": 62,
      "name": "Mini",
      "birth_year": 2018,
      "birth_month": null,
      "birth_day": null,
      "gender_boy": true,
      "gender_girl": true
    },
    {
      "id": 4,
      "user_id": 63,
      "name": "Mini",
      "birth_year": 2018,
      "birth_month": null,
      "birth_day": null,
      "gender_boy": true,
      "gender_girl": true
    },
    {
      "id": 5,
      "user_id": 64,
      "name": "Mini",
      "birth_year": 2018,
      "birth_month": null,
      "birth_day": null,
      "gender_boy": true,
      "gender_girl": true
    },
    {
      "id": 6,
      "user_id": 65,
      "name": "Mini",
      "birth_year": 2018,
      "birth_month": null,
      "birth_day": null,
      "gender_boy": true,
      "gender_girl": true
    },
    {
      "id": 7,
      "user_id": 66,
      "name": "Mini",
      "birth_year": 2018,
      "birth_month": null,
      "birth_day": null,
      "gender_boy": true,
      "gender_girl": true
    },
    {
      "id": 8,
      "user_id": 67,
      "name": "Mini",
      "birth_year": 2018,
      "birth_month": null,
      "birth_day": null,
      "gender_boy": true,
      "gender_girl": true
    },
    {
      "id": 9,
      "user_id": 68,
      "name": "Mini",
      "birth_year": 2018,
      "birth_month": null,
      "birth_day": null,
      "gender_boy": true,
      "gender_girl": true
    },
    {
      "id": 10,
      "user_id": 69,
      "name": "Mini",
      "birth_year": 2018,
      "birth_month": null,
      "birth_day": null,
      "gender_boy": true,
      "gender_girl": true
    },
    {
      "id": 11,
      "user_id": 70,
      "name": "Mini",
      "birth_year": 2018,
      "birth_month": null,
      "birth_day": null,
      "gender_boy": true,
      "gender_girl": true
    },
    {
      "id": 12,
      "user_id": 71,
      "name": "Mini",
      "birth_year": 2018,
      "birth_month": null,
      "birth_day": null,
      "gender_boy": true,
      "gender_girl": true
    }
  ],
  "count": 10,
  "total_count": 10,
  "current_page": 1,
  "pages": 1,
  "per_page": 25
}
```



## Get my minis


### Request

#### Endpoint

```plaintext
GET /api/minis/mine
Accept: application/json
Authorizat IO N: Bearer 99c2f7a6436b392e30ce0e8901abfe001cdc18bc74150749
Host: example.org
Cookie: 
```

`GET /api/minis/mine`

#### Parameters



| Name | Description |
|:-----|:------------|
| q[user_id_eq]  | Anything accessible by ransack can be passed in as query params |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
ETag: W/&quot;57cbbe8dce0f66fa02b44b163be925fc&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 5d240d2b-d98c-4154-a08a-3bfeabb8eb86
X-Runtime: 0.011451
Vary: Origin
Content-Length: 334
200 OK
```


```json
{
  "minis": [
    {
      "id": 16,
      "user_id": 74,
      "name": "Mini",
      "birth_year": 2018,
      "birth_month": null,
      "birth_day": null,
      "gender_boy": true,
      "gender_girl": true
    },
    {
      "id": 17,
      "user_id": 74,
      "name": "Mini",
      "birth_year": 2018,
      "birth_month": null,
      "birth_day": null,
      "gender_boy": true,
      "gender_girl": true
    }
  ],
  "count": 2,
  "total_count": 2,
  "current_page": 1,
  "pages": 1,
  "per_page": 25
}
```



## Update a mini


### Request

#### Endpoint

```plaintext
PATCH /api/minis/19
Accept: application/json
Authorizat IO N: Bearer 601f3e104b44da532cc39488b6c01153011ce35fdbb2ca8a
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/minis/:id`

#### Parameters


```json
mini[name]=Marge
```


| Name | Description |
|:-----|:------------|
| mini[name]  | Mini name |
| mini[user_id]  | User ID must match that of the current_api_user unless the current_api_user is an admin.                 User ID will be inferred from the current_api_user unless explicitly provided |
| mini[birth_year]  | Mini birth year |
| mini[birth_month]  | Mini birth month |
| mini[birth_day]  | Mini birth day |
| mini[gender_boy]  | Mini gender boy |
| mini[gender_girl]  | Mini gender girl |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
ETag: W/&quot;ccfdcc1d4341b78082979c32a19c33eb&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 0020574f-87fa-401a-98ae-c17f954c9a53
X-Runtime: 0.010073
Vary: Origin
Content-Length: 128
200 OK
```


```json
{
  "id": 19,
  "user_id": 76,
  "name": "Marge",
  "birth_year": 2018,
  "birth_month": null,
  "birth_day": null,
  "gender_boy": true,
  "gender_girl": true
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
ETag: W/&quot;64cbc6c193ee705aee4d1b87854336d5&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 6a1007aa-0d5a-4f89-930c-b33c87d9b074
X-Runtime: 0.026928
Vary: Origin
Content-Length: 130
200 OK
```


```json
[
  {
    "id": 2,
    "name": "Kids",
    "navigation_url": "/navigation/kids",
    "parent_id": 1,
    "lft": 2,
    "depth": 1,
    "highlight": false,
    "header_link": false
  }
]
```



# Orders



## Add an item to a cart


### Request

#### Endpoint

```plaintext
POST /api/orders/cart
Accept: application/json
Authorizat IO N: 
X-Spree-Order-Token: 
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/cart`

#### Parameters


```json
user_id&order_token&line_item[variant_id]=111&line_item[quantity]=2&line_item[vendor_id]=187
```


| Name | Description |
|:-----|:------------|
| user_id  | Specify the user_id here if there is one. Calls to this endpoint without a user_id will                          create an order with a nil user |
| order_token  | Spree will look for an order with the order token if it is provided. If an order with                              the specified token is not found, Spree will create a new order with an autogenerated                              guest token that should be stored in cookies and returned with subsequent calls. The                              order token can be passed as a parameter or a header. If passed as both a header and                              parameter, the header will take precedence. |
| line_item[variant_id] *required* | Specify the variant id |
| line_item[quantity] *required* | Specify the quantity requested, must be greater than 0 |
| line_item[vendor_id] *required* | Specify the vendor id, from the price chosen |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
ETag: W/&quot;e153ef489563e11fe1ab668c7fcef8a4&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 463e2bd7-46b6-42f5-8ab3-6f49219da1d8
X-Runtime: 0.093596
Vary: Origin
Content-Length: 2345
200 OK
```


```json
{
  "id": 17,
  "number": "R576525439",
  "item_total": "39.98",
  "total": "39.98",
  "ship_total": "0.0",
  "state": "cart",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2019-09-12T09:46:42.211-04:00",
  "updated_at": "2019-09-12T09:46:42.242-04:00",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": null,
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
  "order_total_after_store_credit": "39.98",
  "display_order_total_after_store_credit": "$39.98",
  "total_applicable_store_credit": 0.0,
  "display_total_available_store_credit": "$0.00",
  "display_store_credit_remaining_after_capture": "$0.00",
  "canceler_id": null,
  "display_item_total": "$39.98",
  "total_quantity": 2,
  "display_total": "$39.98",
  "display_ship_total": "$0.00",
  "display_tax_total": "$0.00",
  "token": "bqMq-N-t_fN7Y8OQ3eKxpQ",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [

  ],
  "bill_address": null,
  "ship_address": null,
  "line_items": [
    {
      "id": 17,
      "quantity": 2,
      "price": "19.99",
      "variant_id": 111,
      "vendor_id": 187,
      "single_display_amount": "$19.99",
      "display_amount": "$39.98",
      "total": "39.98",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 111,
        "name": "Product #59 - 6979",
        "sku": "SKU-110",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-59-6979",
        "description": "As seen on TV!",
        "track_inventory": true,
        "price": "19.99",
        "display_price": "$19.99",
        "options_text": "Size: S",
        "in_stock": false,
        "is_backorderable": false,
        "total_on_hand": 0,
        "is_destroyed": false,
        "option_values": [
          {
            "id": 52,
            "name": "Size-52",
            "presentation": "S",
            "option_type_name": "foo-size-52",
            "option_type_id": 52,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 59,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #187",
      "country_iso": null,
      "adjustments": [

      ]
    }
  ],
  "payments": [

  ],
  "shipments": [

  ],
  "adjustments": [

  ],
  "permissions": {
    "can_update": false
  },
  "credit_cards": [

  ],
  "subtotals": {
    "order_total": "39.98",
    "item_total": "39.98",
    "shipments_total": "0.0",
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



## Get my orders


### Request

#### Endpoint

```plaintext
GET /api/orders/mine
Accept: application/json
Authorizat IO N: Bearer c9e8ff1cb3b35f1de29ab2dfab403bbabd84a237f0ec54b1
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
ETag: W/&quot;370bba21303f6d32b5625677bdb59803&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 358943a2-c1ed-481f-9b07-693c4ef2f522
X-Runtime: 0.021851
Vary: Origin
Content-Length: 310
200 OK
```


```json
{
  "orders": [
    {
      "number": "R596733870",
      "completed_at": "2019-09-12T09:46:42.582-04:00",
      "total": "120.0",
      "state": "Complete",
      "shipment_state": "shipped",
      "shipments": [
        {
          "number": "H32617232608",
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
GET /api/orders/R351928015
Accept: application/json
Authorizat IO N: Bearer 09f570c6acfd939043b8712452461c400f0b83090bfba76a
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
ETag: W/&quot;36bff4f5d7dcba15d8f57ab6b5c42f49&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: bf4cab94-ffe3-4be1-8ae4-c54fb268a04e
X-Runtime: 0.184435
Vary: Origin
Content-Length: 9443
200 OK
```


```json
{
  "id": 19,
  "number": "R351928015",
  "item_total": "20.0",
  "total": "120.0",
  "ship_total": "100.0",
  "state": "complete",
  "adjustment_total": "0.0",
  "user_id": 87,
  "created_at": "2019-09-12T09:46:42.970-04:00",
  "updated_at": "2019-09-12T09:46:43.408-04:00",
  "completed_at": "2019-09-12T09:46:43.104-04:00",
  "payment_total": "120.0",
  "shipment_state": "shipped",
  "payment_state": "paid",
  "email": "email86@example.com",
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
  "token": "m5Jl9F0Z5sHwZrLy3_YXtg",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 25,
      "name": "Credit Card",
      "partial_name": "gateway",
      "method_type": "gateway"
    },
    {
      "id": 26,
      "name": "Credit Card",
      "partial_name": "gateway",
      "method_type": "gateway"
    }
  ],
  "bill_address": {
    "id": 39,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "PO Box 1337",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10036",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 37,
    "country_iso": "US",
    "state_id": 37,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 37,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 37,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 37
    }
  },
  "ship_address": {
    "id": 40,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "A Different Road",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10037",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 37,
    "country_iso": "US",
    "state_id": 37,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 37,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 37,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 37
    }
  },
  "line_items": [
    {
      "id": 20,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 115,
      "vendor_id": 200,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 115,
        "name": "Product #61 - 4892",
        "sku": "SKU-114",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-61-4892",
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
            "id": 54,
            "name": "Size-54",
            "presentation": "S",
            "option_type_name": "foo-size-54",
            "option_type_id": 54,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 61,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #200",
      "country_iso": "US",
      "adjustments": [
        {
          "id": 8,
          "source_type": "Spree::TaxRate",
          "source_id": 1,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 20,
          "amount": "2.0",
          "label": "VAT 5%",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-09-12T09:46:43.359-04:00",
          "updated_at": "2019-09-12T09:46:43.379-04:00",
          "display_amount": "$2.00"
        },
        {
          "id": 2,
          "source_type": "Spree::PromotionAction",
          "source_id": 1,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 20,
          "amount": "5.0",
          "label": "foo",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-09-12T09:46:43.238-04:00",
          "updated_at": "2019-09-12T09:46:43.238-04:00",
          "display_amount": "$5.00"
        },
        {
          "id": 1,
          "source_type": "Spree::PromotionAction",
          "source_id": 1,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 20,
          "amount": "5.0",
          "label": "foo",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-09-12T09:46:43.223-04:00",
          "updated_at": "2019-09-12T09:46:43.223-04:00",
          "display_amount": "$5.00"
        }
      ]
    },
    {
      "id": 21,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 115,
      "vendor_id": 200,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 115,
        "name": "Product #61 - 4892",
        "sku": "SKU-114",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-61-4892",
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
            "id": 54,
            "name": "Size-54",
            "presentation": "S",
            "option_type_name": "foo-size-54",
            "option_type_id": 54,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 61,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #200",
      "country_iso": "US",
      "adjustments": [
        {
          "id": 9,
          "source_type": "Spree::TaxRate",
          "source_id": 2,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 21,
          "amount": "1.5",
          "label": "VAT 5%",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-09-12T09:46:43.403-04:00",
          "updated_at": "2019-09-12T09:46:43.427-04:00",
          "display_amount": "$1.50"
        },
        {
          "id": 3,
          "source_type": "Spree::PromotionAction",
          "source_id": 1,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 21,
          "amount": "5.0",
          "label": "bar",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-09-12T09:46:43.252-04:00",
          "updated_at": "2019-09-12T09:46:43.252-04:00",
          "display_amount": "$5.00"
        }
      ]
    }
  ],
  "payments": [
    {
      "id": 9,
      "source_type": "Spree::CreditCard",
      "source_id": 6,
      "amount": "120.0",
      "display_amount": "$120.00",
      "payment_method_id": 25,
      "state": "completed",
      "avs_response": null,
      "created_at": "2019-09-12T09:46:43.121-04:00",
      "updated_at": "2019-09-12T09:46:43.121-04:00",
      "payment_method": {
        "id": 25,
        "name": "Credit Card"
      },
      "source": {
        "id": 6,
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
      "id": 23,
      "tracking": "U10000",
      "tracking_url": null,
      "number": "H82750067137",
      "cost": "100.0",
      "shipped_at": "2019-09-12T09:46:43.149-04:00",
      "state": "shipped",
      "order_id": "R351928015",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 23,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 17,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 23,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 17,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 17,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 17,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 35,
              "name": "ShippingCategory #35"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 115,
          "quantity": 1,
          "states": {
            "shipped": 1
          }
        },
        {
          "variant_id": 115,
          "quantity": 1,
          "states": {
            "shipped": 1
          }
        }
      ],
      "adjustments": [
        {
          "id": 5,
          "source_type": "Spree::PromotionAction",
          "source_id": 1,
          "adjustable_type": "Spree::Shipment",
          "adjustable_id": 23,
          "amount": "-10.0",
          "label": "Shipping",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-09-12T09:46:43.282-04:00",
          "updated_at": "2019-09-12T09:46:43.282-04:00",
          "display_amount": "-$10.00"
        },
        {
          "id": 4,
          "source_type": "Spree::PromotionAction",
          "source_id": 1,
          "adjustable_type": "Spree::Shipment",
          "adjustable_id": 23,
          "amount": "-9.99",
          "label": "Shipping",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-09-12T09:46:43.266-04:00",
          "updated_at": "2019-09-12T09:46:43.266-04:00",
          "display_amount": "-$9.99"
        }
      ],
      "stock_location_address": "NY Warehouse, Washington, AL",
      "country_iso": "US",
      "international_shipping": false,
      "delivery_estimation": "Sep 16"
    }
  ],
  "adjustments": [
    {
      "id": 6,
      "source_type": "Spree::Promotion",
      "source_id": 1,
      "adjustable_type": "Spree::Order",
      "adjustable_id": 19,
      "amount": "20.0",
      "label": "adj1",
      "promotion_code_id": null,
      "finalized": false,
      "eligible": true,
      "created_at": "2019-09-12T09:46:43.294-04:00",
      "updated_at": "2019-09-12T09:46:43.294-04:00",
      "display_amount": "$20.00"
    },
    {
      "id": 7,
      "source_type": "Spree::Promotion",
      "source_id": 1,
      "adjustable_type": "Spree::Order",
      "adjustable_id": 19,
      "amount": "30.0",
      "label": "adj2",
      "promotion_code_id": null,
      "finalized": false,
      "eligible": true,
      "created_at": "2019-09-12T09:46:43.302-04:00",
      "updated_at": "2019-09-12T09:46:43.302-04:00",
      "display_amount": "$30.00"
    }
  ],
  "permissions": {
    "can_update": false
  },
  "credit_cards": [
    {
      "id": 6,
      "month": "12",
      "year": "2020",
      "cc_type": null,
      "last_digits": "1111",
      "name": "Spree Commerce",
      "address": {
        "id": 39,
        "firstname": "John",
        "lastname": null,
        "full_name": "John",
        "address1": "PO Box 1337",
        "address2": "Northwest",
        "city": "Herndon",
        "zipcode": "10036",
        "phone": "555-555-0199",
        "company": "Company",
        "alternative_phone": "555-555-0199",
        "country_id": 37,
        "country_iso": "US",
        "state_id": 37,
        "state_name": null,
        "state_text": "AL",
        "country": {
          "id": 37,
          "iso_name": "UNITED STATES",
          "iso": "US",
          "iso3": "USA",
          "name": "United States",
          "numcode": 840
        },
        "state": {
          "id": 37,
          "name": "Alabama",
          "abbr": "AL",
          "country_id": 37
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
GET /api/orders/R985631125
Accept: application/json
Authorizat IO N: d2a538eebd80aa5836ec039ad9302bdf3b0204cba9f19689
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
X-Request-Id: 6fb9da75-3b66-4f8b-8e5d-6dda801780be
X-Runtime: 0.011606
Vary: Origin
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
user[email]=email56%40example.com
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
X-Request-Id: 4e9ab137-f153-4b4e-97c4-5ee14a73ff2f
X-Runtime: 0.005080
Vary: Origin
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
user[email]=email54%40example.com&user[password]=secret
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
Authorization: Bearer 03e4994f6ea3522460f34bad594c681a4558a4068072cfbe
ETag: W/&quot;2d7bb834f2527300d73cf86058523d9a&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: f6913786-c980-40ef-a050-275b4eb19556
X-Runtime: 0.012180
Vary: Origin
Content-Length: 562
200 OK
```


```json
{
  "id": 54,
  "email": "email54@example.com",
  "persistence_token": null,
  "perishable_token": null,
  "last_request_at": null,
  "login": "email54@example.com",
  "ship_address_id": null,
  "bill_address_id": null,
  "created_at": "2019-09-12T09:46:38.313-04:00",
  "updated_at": "2019-09-12T09:46:38.316-04:00",
  "spree_api_key": "03e4994f6ea3522460f34bad594c681a4558a4068072cfbe",
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
X-Request-Id: 7a01f4f9-3562-45c7-9cbc-c6fc9e372e2f
X-Runtime: 0.031901
Vary: Origin
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
Date: Thu, 12 Sep 2019 13:46:41 GMT
Surrogate-Control: max-age=900
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;11653d76e221b560871fe6743b7a8aeb&quot;
X-Request-Id: af730c9c-e38c-4559-94a7-6b2daf67ade1
X-Runtime: 0.040497
Vary: Origin
Content-Length: 944
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
      "id": 56,
      "name": "Product #56 - 9010",
      "description": "As seen on TV!",
      "available_on": "2018-09-12T09:46:41.279-04:00",
      "slug": "product-56-9010",
      "meta_description": null,
      "meta_keywords": null,
      "shipping_category_id": 31,
      "taxon_ids": [

      ],
      "total_on_hand": 0,
      "meta_title": null,
      "display_price": "$19.99",
      "trends": [

      ],
      "breadcrumb_taxons": {
      },
      "brand": null,
      "brand_slug": null,
      "brand_description": null,
      "has_variants": false,
      "master": {
        "id": 105,
        "name": "Product #56 - 9010",
        "sku": "SKU-105",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-56-9010",
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
GET /api/products/product-50-5946
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
Date: Thu, 12 Sep 2019 13:46:40 GMT
Surrogate-Control: max-age=900
Surrogate-Key: product_id=1
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;bcfb09fdc3ab1563ad6834b19f9965ab&quot;
X-Request-Id: 8ed203fb-f18f-4059-b9b1-7b7a6e48da6d
X-Runtime: 0.098993
Vary: Origin
Content-Length: 860
200 OK
```


```json
{
  "id": 50,
  "name": "Product #50 - 5946",
  "description": "As seen on TV!",
  "available_on": "2018-09-12T09:46:40.066-04:00",
  "slug": "product-50-5946",
  "meta_description": null,
  "meta_keywords": null,
  "shipping_category_id": 27,
  "taxon_ids": [

  ],
  "total_on_hand": 0,
  "meta_title": null,
  "display_price": "$19.99",
  "trends": [

  ],
  "breadcrumb_taxons": {
  },
  "brand": null,
  "brand_slug": null,
  "brand_description": null,
  "has_variants": false,
  "master": {
    "id": 99,
    "name": "Product #50 - 5946",
    "sku": "SKU-99",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": true,
    "slug": "product-50-5946",
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
X-Request-Id: 9fba3fc4-9a2a-44e8-833a-07f93f1af36c
X-Runtime: 0.014177
Vary: Origin
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
ETag: W/&quot;15209b65d4860f52078a2b96a8f26001&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 5cff87ba-dca9-4122-a285-82e4f50d8401
X-Runtime: 0.090160
Vary: Origin
Content-Length: 1126
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
      "id": 52,
      "name": "Product #52 - 4321",
      "description": "As seen on TV!",
      "available_on": "2018-09-12T09:46:40.418-04:00",
      "slug": "product-52-4321",
      "meta_description": null,
      "meta_keywords": null,
      "shipping_category_id": 29,
      "taxon_ids": [
        4
      ],
      "total_on_hand": 0,
      "meta_title": null,
      "display_price": "$19.99",
      "trends": [

      ],
      "breadcrumb_taxons": {
      },
      "brand": "Ruby on Rails",
      "brand_slug": "ruby-on-rails",
      "brand_description": null,
      "has_variants": false,
      "master": {
        "id": 101,
        "name": "Product #52 - 4321",
        "sku": "SKU-101",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-52-4321",
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
          "taxon_id": 4,
          "position": 1,
          "taxon": {
            "id": 4,
            "name": "Ruby on Rails",
            "pretty_name": "Ruby on Rails",
            "permalink": "ruby-on-rails",
            "parent_id": null,
            "taxonomy_id": 2
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
GET /api/taxons/products?id=8
Host: example.org
Cookie: 
```

`GET /api/taxons/products`

#### Parameters


```json
id: 8
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
ETag: W/&quot;56b37147a377788b6b4c4ca0a47274fd&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: e7dfed50-4f32-4f46-a4b3-86a2257e0727
X-Runtime: 0.072523
Vary: Origin
Content-Length: 1126
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
      "id": 54,
      "name": "Product #54 - 1463",
      "description": "As seen on TV!",
      "available_on": "2018-09-12T09:46:40.831-04:00",
      "slug": "product-54-1463",
      "meta_description": null,
      "meta_keywords": null,
      "shipping_category_id": 30,
      "taxon_ids": [
        8
      ],
      "total_on_hand": 0,
      "meta_title": null,
      "display_price": "$19.99",
      "trends": [

      ],
      "breadcrumb_taxons": {
      },
      "brand": "Ruby on Rails",
      "brand_slug": "ruby-on-rails",
      "brand_description": null,
      "has_variants": false,
      "master": {
        "id": 103,
        "name": "Product #54 - 1463",
        "sku": "SKU-103",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-54-1463",
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
          "taxon_id": 8,
          "position": 1,
          "taxon": {
            "id": 8,
            "name": "Ruby on Rails",
            "pretty_name": "Ruby on Rails",
            "permalink": "ruby-on-rails",
            "parent_id": null,
            "taxonomy_id": 4
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
GET /api/returns/RA720837066
Authorizat IO N: Bearer b924a2bf420e51607315bbd3a9c69ec50ec15856332f0748
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
ETag: W/&quot;720690cdb7c8766b4ed32b69b6d2ec4b&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: e2d8741b-3bd7-4aab-8b3a-5804ac21b9dc
X-Runtime: 0.062100
Vary: Origin
Content-Length: 2777
200 OK
```


```json
{
  "id": 2,
  "number": "RA720837066",
  "state": "authorized",
  "order_id": 8,
  "memo": "Items were broken",
  "created_at": "2019-09-12T09:46:33.908-04:00",
  "updated_at": "2019-09-12T09:46:33.908-04:00",
  "reason": {
    "id": 3,
    "name": "Defect #3",
    "active": true,
    "mutable": true,
    "created_at": "2019-09-12T09:46:33.902-04:00",
    "updated_at": "2019-09-12T09:46:33.902-04:00",
    "mirakl_code": null
  },
  "order": {
    "id": 8,
    "number": "R978783835",
    "item_total": "10.0",
    "total": "110.0",
    "state": "complete",
    "adjustment_total": "0.0",
    "user_id": 40,
    "completed_at": "2019-09-12T09:46:33.791-04:00",
    "bill_address_id": 14,
    "ship_address_id": 15,
    "payment_total": "110.0",
    "shipment_state": "shipped",
    "payment_state": "paid",
    "email": "email40@example.com",
    "special_instructions": null,
    "created_at": "2019-09-12T09:46:33.675-04:00",
    "updated_at": "2019-09-12T09:46:33.873-04:00",
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
    "guest_token": "V-koumm0j9dBdWGI-PIuoA",
    "canceled_at": null,
    "canceler_id": null,
    "store_id": 8,
    "approver_name": null,
    "frontend_viewable": true
  },
  "ship_address": {
    "id": 15,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "A Different Road",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10015",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 19,
    "country_iso": "US",
    "state_id": 19,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 19,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 19,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 19
    }
  },
  "bill_address": {
    "id": 14,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "PO Box 1337",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10014",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 19,
    "country_iso": "US",
    "state_id": 19,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 19,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 19,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 19
    }
  },
  "return_items": [
    {
      "name": "Product #40 - 4975",
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
        "id": 9,
        "name": "Credit Card"
      },
      "source": {
        "id": 2,
        "month": "12",
        "year": "2020",
        "cc_type": null,
        "last_digits": "1111",
        "name": "Spree Commerce",
        "gateway_customer_profile_id": "BGS-101301",
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
Authorizat IO N: Bearer 34f9438617213842a05ce8357e8784167139514e8eed2ca4
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
ETag: W/&quot;e9408c3dc0bfbcdd8867f37deb2c895b&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 82a2df43-b482-4e05-8126-c2edc86bac9e
X-Runtime: 0.013391
Vary: Origin
Content-Length: 169
200 OK
```


```json
{
  "return_authorizations": [
    {
      "number": "RA655604332",
      "created_at": "2019-09-12T09:46:35.329-04:00",
      "return_amount": "10.0",
      "order_number": "R945593855",
      "state": "authorized"
    }
  ]
}
```



## returns a 200


### Request

#### Endpoint

```plaintext
GET /api/returns/RA783287815
Authorizat IO N: Bearer a7f15028a4b7b5152710091361b2c927050952660e6f2195
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
ETag: W/&quot;ef877b6781802d09a4acf72a2e85ca24&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: d99c6220-fe47-48a8-b103-29a882cf1c5a
X-Runtime: 0.099044
Vary: Origin
Content-Length: 2700
200 OK
```


```json
{
  "id": 1,
  "number": "RA783287815",
  "state": "authorized",
  "order_id": 7,
  "memo": "Items were broken",
  "created_at": "2019-09-12T09:46:33.136-04:00",
  "updated_at": "2019-09-12T09:46:33.136-04:00",
  "reason": {
    "id": 1,
    "name": "Defect #1",
    "active": true,
    "mutable": true,
    "created_at": "2019-09-12T09:46:33.120-04:00",
    "updated_at": "2019-09-12T09:46:33.120-04:00",
    "mirakl_code": null
  },
  "order": {
    "id": 7,
    "number": "R064389650",
    "item_total": "10.0",
    "total": "110.0",
    "state": "complete",
    "adjustment_total": "0.0",
    "user_id": 39,
    "completed_at": "2019-09-12T09:46:32.868-04:00",
    "bill_address_id": 12,
    "ship_address_id": 13,
    "payment_total": "110.0",
    "shipment_state": "shipped",
    "payment_state": "paid",
    "email": "email39@example.com",
    "special_instructions": null,
    "created_at": "2019-09-12T09:46:32.750-04:00",
    "updated_at": "2019-09-12T09:46:33.052-04:00",
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
    "guest_token": "zT5gzU60x-psYxLzBsRFig",
    "canceled_at": null,
    "canceler_id": null,
    "store_id": 7,
    "approver_name": null,
    "frontend_viewable": true
  },
  "ship_address": {
    "id": 13,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "A Different Road",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10013",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 18,
    "country_iso": "US",
    "state_id": 18,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 18,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 18,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 18
    }
  },
  "bill_address": {
    "id": 12,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "PO Box 1337",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10012",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 18,
    "country_iso": "US",
    "state_id": 18,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 18,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 18,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 18
    }
  },
  "return_items": [
    {
      "name": "Product #39 - 7733",
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
        "id": 7,
        "name": "Credit Card"
      },
      "source": {
        "id": 1,
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
GET /api/returns/RA603524854
Authorizat IO N: Bearer b132a8912c6e06a64528ade67226feef5744cfa565d0ce59
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
X-Request-Id: 1050d0f0-b886-4f75-9d4a-5471a620f04f
X-Runtime: 0.017124
Vary: Origin
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
Authorizat IO N: Bearer a1f8a964b5db0721a96ce5b98c419b9b051a5ccfdce24378
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
ETag: W/&quot;9a63e6709f48c8be034d433c7c05a1ae&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: a61aeef0-5b6d-494d-a360-3e677c18d8d4
X-Runtime: 0.032596
Vary: Origin
Content-Length: 218
200 OK
```


```json
{
  "store_credits": [
    {
      "amount": "150.0",
      "amount_used": "0.0",
      "category": "Exchange",
      "created_at": "2019-09-12T09:46:41.447-04:00"
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



# Subscribers

Update a subscriber. Users can update their own subscriber, admins can update minis for others.

## Create a subscriber


### Request

#### Endpoint

```plaintext
POST /api/subscribers
Accept: application/json
Authorizat IO N: Bearer 8810104dbaff58d94e60030a1d8697792a18ad53939f62b0
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/subscribers`

#### Parameters


```json
subscriber[email]=floria.barton%40wyman.info&subscriber[user_id]=46&subscriber[first_name]=Ashleigh&subscriber[last_name]=Abernathy&subscriber[status]=subscribed
```


| Name | Description |
|:-----|:------------|
| subscriber[email] *required* | Subscriber email |
| subscriber[user_id]  | User ID must match that of the current_api_user unless the current_api_user is an admin.                 User ID will be inferred from the current_api_user unless explicitly provided |
| subscriber[first_name]  | Subscriber first name |
| subscriber[last_name]  | Subscriber last name |
| subscriber[source]  | Subscriber source |
| subscriber[status]  | Default status is 'subscribed', the other available statuses are 'unsubscribed',                          'subscribed_and_synced', 'unsubscribed_and_synced' |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
ETag: W/&quot;c91f8b56a08ab0d9f0406e47b8ed787b&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: d54f0e5c-3e5c-4b86-865f-f1b5ba454b0e
X-Runtime: 0.013341
Vary: Origin
Content-Length: 183
201 Created
```


```json
{
  "id": 2,
  "user_id": 46,
  "email": "floria.barton@wyman.info",
  "first_name": "Ashleigh",
  "last_name": "Abernathy",
  "source": "",
  "status": "subscribed",
  "created_at": "2019-09-12T09:46:35.632-04:00"
}
```



## Delete a subscriber


### Request

#### Endpoint

```plaintext
DELETE /api/subscribers/3
Accept: application/json
Authorizat IO N: Bearer 2178b5a056a4793b968c41e0b4f9d657b8c125a11eeb5338
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`DELETE /api/subscribers/:id`

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
X-Request-Id: 55c3f81d-4d51-4041-9b7f-92ab92e05729
X-Runtime: 0.010961
Vary: Origin
204 No Content
```




## Get a single subscriber by id


### Request

#### Endpoint

```plaintext
GET /api/subscribers/4
Accept: application/json
Authorizat IO N: Bearer e7b89dad738faed16a6aaa46a850beb056d65847a14eff78
Host: example.org
Cookie: 
```

`GET /api/subscribers/:id`

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
ETag: W/&quot;ca46f2579b19c4b4cfa7b8c3e8592e40&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: b5fabe71-2705-440c-879f-219b4f4e7629
X-Runtime: 0.012222
Vary: Origin
Content-Length: 179
200 OK
```


```json
{
  "id": 4,
  "user_id": 48,
  "email": "monique@kohler.info",
  "first_name": "Clementina",
  "last_name": "Shanahan",
  "source": "",
  "status": "subscribed",
  "created_at": "2019-09-12T09:46:35.702-04:00"
}
```



## Get all subscribers


### Request

#### Endpoint

```plaintext
GET /api/subscribers
Accept: application/json
Authorizat IO N: Bearer 9384ced917904e39b4b88852b904f761b92c332dc61377a1
Host: example.org
Cookie: 
```

`GET /api/subscribers`

#### Parameters



| Name | Description |
|:-----|:------------|
| q[user_id_eq]  | Anything accessible by ransack can be passed in as query params |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
ETag: W/&quot;55df3b6cf914450cd985349f049d6851&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: a528deae-3df3-43fc-a0fe-4cf02dc7ffca
X-Runtime: 0.017290
Vary: Origin
Content-Length: 636
200 OK
```


```json
{
  "subscribers": [
    {
      "id": 5,
      "user_id": null,
      "email": "nell_jakubowski@littledubuque.ca",
      "first_name": "Deedee",
      "last_name": "Schuster",
      "source": "",
      "status": "subscribed",
      "created_at": "2019-09-12T09:46:35.721-04:00"
    },
    {
      "id": 6,
      "user_id": null,
      "email": "angla_feeney@brakus.us",
      "first_name": "Shayne",
      "last_name": "Kozey",
      "source": "",
      "status": "subscribed",
      "created_at": "2019-09-12T09:46:35.724-04:00"
    },
    {
      "id": 7,
      "user_id": null,
      "email": "jeremiah@breitenberg.co.uk",
      "first_name": "Loraine",
      "last_name": "Thiel",
      "source": "",
      "status": "subscribed",
      "created_at": "2019-09-12T09:46:35.726-04:00"
    }
  ],
  "count": 3,
  "total_count": 3,
  "current_page": 1,
  "pages": 1,
  "per_page": 25
}
```



## Update a mini


### Request

#### Endpoint

```plaintext
PATCH /api/subscribers/1
Accept: application/json
Authorizat IO N: Bearer 9fab2243a48a6f6b297dfddd2215f38fba7e453476456448
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/subscribers/:id`

#### Parameters


```json
subscriber[status]=unsubscribed
```


| Name | Description |
|:-----|:------------|
| subscriber[email] *required* | Subscriber email |
| subscriber[user_id]  | User ID must match that of the current_api_user unless the current_api_user is an admin.                 User ID will be inferred from the current_api_user unless explicitly provided |
| subscriber[first_name]  | Subscriber first name |
| subscriber[last_name]  | Subscriber last name |
| subscriber[source]  | Subscriber source |
| subscriber[status]  | Default status is 'subscribed', the other available statuses are 'unsubscribed',                          'subscribed_and_synced', 'unsubscribed_and_synced' |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
ETag: W/&quot;c083bdeaece20bbad6dfa52e7e2b5668&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 8cb99ec7-a720-46cf-98a6-442f4379bbe8
X-Runtime: 0.048032
Vary: Origin
Content-Length: 182
200 OK
```


```json
{
  "id": 1,
  "user_id": 45,
  "email": "edelmira@konopelski.info",
  "first_name": "Robin",
  "last_name": "Romaguera",
  "source": "",
  "status": "unsubscribed",
  "created_at": "2019-09-12T09:46:35.544-04:00"
}
```



# Users

Subscribe a user. If the user does not already have an associated subscriber, this will create one.                 If the user is already in a subscribed state, this will not change any records

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
user[email]=email81%40example.com&user[password]=secret
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
Authorization: Bearer 02e62d2e5e22cdcfc29a98340e79caecc6fbf3e67d476067
ETag: W/&quot;80db88f9253c605f0feb868e5284b4fb&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 48e88798-2080-4587-bb36-f841ce9c48ec
X-Runtime: 0.004347
Vary: Origin
Content-Length: 562
200 OK
```


```json
{
  "id": 82,
  "email": "email81@example.com",
  "persistence_token": null,
  "perishable_token": null,
  "last_request_at": null,
  "login": "email81@example.com",
  "ship_address_id": null,
  "bill_address_id": null,
  "created_at": "2019-09-12T09:46:40.023-04:00",
  "updated_at": "2019-09-12T09:46:40.025-04:00",
  "spree_api_key": "02e62d2e5e22cdcfc29a98340e79caecc6fbf3e67d476067",
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
Authorizat IO N: Bearer 65b4790abe2b9b11cb973a5d37ada2f60631c6f25feb1d4d
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
Authorization: Bearer 65b4790abe2b9b11cb973a5d37ada2f60631c6f25feb1d4d
ETag: W/&quot;3f1f5842340a554e231cf10f84f4a2f0&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 96611541-887b-49d0-929f-50050c7fa89f
X-Runtime: 0.020616
Vary: Origin
Content-Length: 1522
200 OK
```


```json
{
  "email": "email80@example.com",
  "first_name": null,
  "last_name": null,
  "id": 81,
  "subscribed": false,
  "addresses": [
    {
      "id": 36,
      "firstname": "John",
      "lastname": null,
      "full_name": "John",
      "address1": "A Different Road",
      "address2": "Northwest",
      "city": "Herndon",
      "zipcode": "10033",
      "phone": "555-555-0199",
      "company": "Company",
      "alternative_phone": "555-555-0199",
      "country_id": 28,
      "country_iso": "US",
      "state_id": 28,
      "state_name": null,
      "state_text": "AL",
      "country": {
        "id": 28,
        "iso_name": "UNITED STATES",
        "iso": "US",
        "iso3": "USA",
        "name": "United States",
        "numcode": 840
      },
      "default": true
    },
    {
      "id": 35,
      "firstname": "John",
      "lastname": null,
      "full_name": "John",
      "address1": "PO Box 1337",
      "address2": "Northwest",
      "city": "Herndon",
      "zipcode": "10032",
      "phone": "555-555-0199",
      "company": "Company",
      "alternative_phone": "555-555-0199",
      "country_id": 28,
      "country_iso": "US",
      "state_id": 28,
      "state_name": null,
      "state_text": "AL",
      "country": {
        "id": 28,
        "iso_name": "UNITED STATES",
        "iso": "US",
        "iso3": "USA",
        "name": "United States",
        "numcode": 840
      },
      "default": false
    }
  ],
  "payment_sources": [
    {
      "id": 6,
      "default": true,
      "source": {
        "id": 8,
        "payment_type": "CreditCard",
        "token": null,
        "created_at": "2019-09-12T09:46:39.967-04:00",
        "cc_type": null,
        "last_digits": null,
        "month": null,
        "year": null
      }
    },
    {
      "id": 7,
      "default": false,
      "source": {
        "id": 9,
        "payment_type": "ApplePayCard",
        "token": null,
        "created_at": "2019-09-12T09:46:39.981-04:00",
        "cc_type": null,
        "last_digits": null,
        "month": null,
        "year": null
      }
    },
    {
      "id": 8,
      "default": false,
      "source": {
        "id": 10,
        "payment_type": "PayPalAccount",
        "token": null,
        "created_at": "2019-09-12T09:46:39.995-04:00",
        "email": null
      }
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
| subscribe  | If set to 'true', this will create a subscriber associated with the new user |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
Authorization: Bearer a192ff6552eae17a2cb37ac0fabd7d0e0b15a71e1ed59d67
ETag: W/&quot;4d4c6b6baa9c7c08bf25d85ca08c81f0&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 9d5c2400-542f-48c5-b1e8-5738cb2f1b94
X-Runtime: 0.012794
Vary: Origin
Content-Length: 185
201 Created
```


```json
{
  "id": 80,
  "email": "test@example.com",
  "created_at": "2019-09-12T09:46:39.917-04:00",
  "updated_at": "2019-09-12T09:46:39.918-04:00",
  "subscribed": false,
  "bill_address": null,
  "ship_address": null
}
```



## Subscribe a user


### Request

#### Endpoint

```plaintext
PUT /api/users/79/subscribe
Authorizat IO N: Bearer e00d020023ece4538eee762d29d879f49d519d64cc26e2b3
Accept: application/json
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PUT /api/users/:id/subscribe`

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
Authorization: Bearer e00d020023ece4538eee762d29d879f49d519d64cc26e2b3
ETag: W/&quot;b30eae18c0e5b609d3e23f179e4992c9&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 0e48beb2-0c0d-4d81-baae-3618c054a7b7
X-Runtime: 0.023403
Vary: Origin
Content-Length: 187
200 OK
```


```json
{
  "id": 79,
  "email": "email79@example.com",
  "created_at": "2019-09-12T09:46:39.878-04:00",
  "updated_at": "2019-09-12T09:46:39.880-04:00",
  "subscribed": true,
  "bill_address": null,
  "ship_address": null
}
```



## Unsubscribe a user


### Request

#### Endpoint

```plaintext
PUT /api/users/83/unsubscribe
Authorizat IO N: Bearer 619b6a13a4392ffa1a1fb5b17aadbf650f4a6d99c72f8c9e
Accept: application/json
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PUT /api/users/:id/unsubscribe`

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
Authorization: Bearer 619b6a13a4392ffa1a1fb5b17aadbf650f4a6d99c72f8c9e
ETag: W/&quot;6bc1170d3da5a7d42152131141de2085&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: ebf876df-e814-42d8-a0ea-91664551a38b
X-Runtime: 0.014881
Vary: Origin
Content-Length: 188
200 OK
```


```json
{
  "id": 83,
  "email": "email82@example.com",
  "created_at": "2019-09-12T09:46:40.037-04:00",
  "updated_at": "2019-09-12T09:46:40.039-04:00",
  "subscribed": false,
  "bill_address": null,
  "ship_address": null
}
```



# Variant



## Fetching a variant


### Request

#### Endpoint

```plaintext
GET /api/variants/107
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
ETag: W/&quot;14d7c8f1c882f73471e80533cefdd3e1&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 2c24075e-19f4-4096-ba54-2fe6dab9f8f5
X-Runtime: 0.085327
Vary: Origin
Content-Length: 1456
200 OK
```


```json
{
  "id": 107,
  "name": "Product #57 - 5442",
  "sku": "SKU-106",
  "weight": "0.0",
  "height": null,
  "width": null,
  "depth": null,
  "is_master": false,
  "slug": "product-57-5442",
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
      "id": 50,
      "name": "Size-50",
      "presentation": "S",
      "option_type_name": "foo-size-50",
      "option_type_id": 50,
      "option_type_presentation": "Size"
    }
  ],
  "images": [
    {
      "id": 1,
      "position": 1,
      "attachment_content_type": "image/jpeg",
      "attachment_file_name": "thinking-cat.jpg",
      "type": "Spree::Image",
      "attachment_updated_at": "2019-09-12T09:46:41.693-04:00",
      "attachment_width": 489,
      "attachment_height": 490,
      "alt": null,
      "viewable_type": "Spree::Variant",
      "viewable_id": 107,
      "mini_url": "/spree/products/1/mini/thinking-cat.jpg?1568296001",
      "small_url": "/spree/products/1/small/thinking-cat.jpg?1568296001",
      "product_url": "/spree/products/1/product/thinking-cat.jpg?1568296001",
      "large_url": "/spree/products/1/large/thinking-cat.jpg?1568296001"
    }
  ],
  "variant_properties": [

  ],
  "stock_items": [

  ],
  "prices": [
    {
      "id": 74,
      "vendor_id": 183,
      "price": "10.0",
      "original_price": "10.0",
      "discount_percent": 0.0,
      "total_on_hand": 0,
      "country_iso": null,
      "final_sale": false,
      "on_sale": false
    },
    {
      "id": 75,
      "vendor_id": 184,
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
Authorizat IO N: Bearer e4e97812e2f59d45b19fbfa4144ec43cb93ec3bc420edab1
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
ETag: W/&quot;01f82633f25f1c110de8b7023e3174a6&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 81d9c245-df63-4bfd-88e4-799426849d3e
X-Runtime: 0.014708
Vary: Origin
Content-Length: 206
200 OK
```


```json
[
  {
    "id": 4,
    "user_id": 58,
    "payment_source_type": "SolidusPaypalBraintree::Source",
    "payment_source_id": 4,
    "default": false,
    "created_at": "2019-09-12T09:46:38.502-04:00",
    "updated_at": "2019-09-12T09:46:38.502-04:00"
  }
]
```



## Remove the payment from the user wallet


### Request

#### Endpoint

```plaintext
DELETE /api/wallet_payment_sources/3
Accept: application/json
Authorizat IO N: Bearer 1759a5fe8804cdfc4d73ae8cb9647c0ce756c1db09756c02
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
X-Request-Id: 47b103f5-372d-4ef5-b627-4d8cfe46f885
X-Runtime: 0.034164
Vary: Origin
204 No Content
```




## Set a wallet payment source as the default user payment method


### Request

#### Endpoint

```plaintext
POST /api/wallet_payment_sources/5/default
Accept: application/json
Authorizat IO N: Bearer 60062c9f90b07e64a13c0e2e37977b8374daae9c20e9df69
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
X-Request-Id: 2c9789d9-4d63-476d-b07c-2851967d1e2d
X-Runtime: 0.009918
Vary: Origin
204 No Content
```




# Wished Products

Get a single wished product, accessible by owner of the wished product

## Create a wished product


### Request

#### Endpoint

```plaintext
POST /api/wished_products
Accept: application/json
Authorizat IO N: Bearer 54a6e2ed03f6e51d919a53ea8116fe43b95a4e1a13d7cf31
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/wished_products`

#### Parameters


```json
wished_product[wishlist_id]=40&wished_product[variant_id]=76&wished_product[quantity]=2&wished_product[remark]=Foo+bar
```


| Name | Description |
|:-----|:------------|
| wished_product[wishlist_id]  | Optional. If the wishlist_id is not provided, the product will be created for the spree_api_user's               default wishlist. Admin users can pass another user's wishlist_id |
| wished_product[variant_id] *required* | Wished product variant |
| wished_product[quantity]  | Wished product quantity |
| wished_product[remark]  | Wished product remark |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
ETag: W/&quot;855a6d1256d8ac88e0ad235e27a10b0c&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 76d2db99-7a1c-4c91-b09e-f25d89a5580d
X-Runtime: 0.021610
Vary: Origin
Content-Length: 74
201 Created
```


```json
{
  "id": 31,
  "wishlist_id": 40,
  "variant_id": 76,
  "quantity": 2,
  "remark": "Foo bar"
}
```



## Delete a wished product


### Request

#### Endpoint

```plaintext
DELETE /api/wished_products/28
Accept: application/json
Authorizat IO N: Bearer ad61745d92216c73da1c61f111322ec4a3d419b4bcf98242
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`DELETE /api/wished_products/:id`

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
X-Request-Id: 54b1750c-ea8f-4be8-9c1e-1760bf71edaa
X-Runtime: 0.018767
Vary: Origin
204 No Content
```




## Get a single wished product


### Request

#### Endpoint

```plaintext
GET /api/wished_products/10
Accept: application/json
Authorizat IO N: Bearer 7c93883db874f8fbc0d3b4aa4c81195d57d5c08e9be3b9b6
Host: example.org
Cookie: 
```

`GET /api/wished_products/:id`

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
ETag: W/&quot;f52dce59901848b980e0473049337bcf&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: ebf6de5d-9773-48af-8e77-97ca498aa1ba
X-Runtime: 0.032975
Vary: Origin
Content-Length: 69
200 OK
```


```json
{
  "id": 10,
  "wishlist_id": 29,
  "variant_id": 32,
  "quantity": 1,
  "remark": null
}
```



## Get all wished products


### Request

#### Endpoint

```plaintext
GET /api/wished_products
Accept: application/json
Authorizat IO N: Bearer bb9073520af1d378f04f46d1622d86227093a808364b708e
Host: example.org
Cookie: 
```

`GET /api/wished_products`

#### Parameters



| Name | Description |
|:-----|:------------|
| q[wishlist_user_id_eq]  | Anything accessible by ransack can be passed in as query params |
| q[wishlist_id_eq]  | Anything accessible by ransack can be passed in as query params |
| with_variant  | Include this parameter if you would like the variant to be returned in the                              response with the wished product |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
ETag: W/&quot;9d1e2542a460f0037bc9659151c1ff0c&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 3fa18476-a92e-4f08-90bd-817bc33e43af
X-Runtime: 0.013840
Vary: Origin
Content-Length: 298
200 OK
```


```json
{
  "wished_products": [
    {
      "id": 16,
      "wishlist_id": 31,
      "variant_id": 46,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 17,
      "wishlist_id": 32,
      "variant_id": 48,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 18,
      "wishlist_id": 33,
      "variant_id": 50,
      "quantity": 1,
      "remark": null
    }
  ],
  "count": 3,
  "total_count": 3,
  "current_page": 1,
  "pages": 1,
  "per_page": 25
}
```



## Get all wished products with variants


### Request

#### Endpoint

```plaintext
GET /api/wished_products?with_variant=true
Accept: application/json
Authorizat IO N: Bearer c0fde4b62a71692c1b3c00c1450018059fdbb50de2fa3797
Host: example.org
Cookie: 
```

`GET /api/wished_products`

#### Parameters


```json
with_variant: true
```


| Name | Description |
|:-----|:------------|
| q[wishlist_user_id_eq]  | Anything accessible by ransack can be passed in as query params |
| q[wishlist_id_eq]  | Anything accessible by ransack can be passed in as query params |
| with_variant  | Include this parameter if you would like the variant to be returned in the                              response with the wished product |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
ETag: W/&quot;25fc1906eecef2698982e58acd09b03f&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: e415e03d-7c30-4fad-afa8-e048b7fc6ac4
X-Runtime: 0.149990
Vary: Origin
Content-Length: 2105
200 OK
```


```json
{
  "wished_products": [
    {
      "id": 19,
      "wishlist_id": 34,
      "variant_id": 52,
      "quantity": 1,
      "remark": null,
      "variant": {
        "id": 52,
        "name": "Product #26 - 7911",
        "sku": "SKU-51",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-26-7911",
        "description": "As seen on TV!",
        "track_inventory": true,
        "cost_price": "17.0",
        "lead_time": 2,
        "price": null,
        "display_price": "",
        "options_text": "Size: S",
        "in_stock": false,
        "is_backorderable": false,
        "total_on_hand": 0,
        "is_destroyed": false,
        "option_values": [
          {
            "id": 26,
            "name": "Size-26",
            "presentation": "S",
            "option_type_name": "foo-size-26",
            "option_type_id": 26,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "variant_properties": [

        ],
        "stock_items": [

        ],
        "prices": [

        ]
      }
    },
    {
      "id": 20,
      "wishlist_id": 35,
      "variant_id": 54,
      "quantity": 1,
      "remark": null,
      "variant": {
        "id": 54,
        "name": "Product #27 - 166",
        "sku": "SKU-53",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-27-166",
        "description": "As seen on TV!",
        "track_inventory": true,
        "cost_price": "17.0",
        "lead_time": 2,
        "price": null,
        "display_price": "",
        "options_text": "Size: S",
        "in_stock": false,
        "is_backorderable": false,
        "total_on_hand": 0,
        "is_destroyed": false,
        "option_values": [
          {
            "id": 27,
            "name": "Size-27",
            "presentation": "S",
            "option_type_name": "foo-size-27",
            "option_type_id": 27,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "variant_properties": [

        ],
        "stock_items": [

        ],
        "prices": [

        ]
      }
    },
    {
      "id": 21,
      "wishlist_id": 36,
      "variant_id": 56,
      "quantity": 1,
      "remark": null,
      "variant": {
        "id": 56,
        "name": "Product #28 - 2699",
        "sku": "SKU-55",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-28-2699",
        "description": "As seen on TV!",
        "track_inventory": true,
        "cost_price": "17.0",
        "lead_time": 2,
        "price": null,
        "display_price": "",
        "options_text": "Size: S",
        "in_stock": false,
        "is_backorderable": false,
        "total_on_hand": 0,
        "is_destroyed": false,
        "option_values": [
          {
            "id": 28,
            "name": "Size-28",
            "presentation": "S",
            "option_type_name": "foo-size-28",
            "option_type_id": 28,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "variant_properties": [

        ],
        "stock_items": [

        ],
        "prices": [

        ]
      }
    }
  ],
  "count": 3,
  "total_count": 3,
  "current_page": 1,
  "pages": 1,
  "per_page": 25
}
```



## Get all wished products with variants


### Request

#### Endpoint

```plaintext
GET /api/wished_products/mine?with_variant=true
Accept: application/json
Authorizat IO N: Bearer df431ddd6eedfb70f28dbd77d5e9091e8b4129c69e71e2ec
Host: example.org
Cookie: 
```

`GET /api/wished_products/mine`

#### Parameters


```json
with_variant: true
```


| Name | Description |
|:-----|:------------|
| q[wishlist_id_eq]  | Anything accessible by ransack can be passed in as query params |
| with_variant  | Include this parameter if you would like the variant to be returned in the                              response with the wished product |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
ETag: W/&quot;9fa570b9d50325883f040f119c72ccc1&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 1be19851-f27f-49ff-80d9-bf55786b9d68
X-Runtime: 0.137340
Vary: Origin
Content-Length: 2047
200 OK
```


```json
{
  "wished_products": [
    {
      "id": 25,
      "wishlist_id": 38,
      "variant_id": 64,
      "quantity": 1,
      "remark": null,
      "variant": {
        "id": 64,
        "name": "Product #32 - 1913",
        "sku": "SKU-63",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-32-1913",
        "description": "As seen on TV!",
        "track_inventory": true,
        "lead_time": 2,
        "price": null,
        "display_price": "",
        "options_text": "Size: S",
        "in_stock": false,
        "is_backorderable": false,
        "total_on_hand": 0,
        "is_destroyed": false,
        "option_values": [
          {
            "id": 32,
            "name": "Size-32",
            "presentation": "S",
            "option_type_name": "foo-size-32",
            "option_type_id": 32,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "variant_properties": [

        ],
        "stock_items": [

        ],
        "prices": [

        ]
      }
    },
    {
      "id": 26,
      "wishlist_id": 38,
      "variant_id": 66,
      "quantity": 1,
      "remark": null,
      "variant": {
        "id": 66,
        "name": "Product #33 - 8875",
        "sku": "SKU-65",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-33-8875",
        "description": "As seen on TV!",
        "track_inventory": true,
        "lead_time": 2,
        "price": null,
        "display_price": "",
        "options_text": "Size: S",
        "in_stock": false,
        "is_backorderable": false,
        "total_on_hand": 0,
        "is_destroyed": false,
        "option_values": [
          {
            "id": 33,
            "name": "Size-33",
            "presentation": "S",
            "option_type_name": "foo-size-33",
            "option_type_id": 33,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "variant_properties": [

        ],
        "stock_items": [

        ],
        "prices": [

        ]
      }
    },
    {
      "id": 27,
      "wishlist_id": 38,
      "variant_id": 68,
      "quantity": 1,
      "remark": null,
      "variant": {
        "id": 68,
        "name": "Product #34 - 6406",
        "sku": "SKU-67",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-34-6406",
        "description": "As seen on TV!",
        "track_inventory": true,
        "lead_time": 2,
        "price": null,
        "display_price": "",
        "options_text": "Size: S",
        "in_stock": false,
        "is_backorderable": false,
        "total_on_hand": 0,
        "is_destroyed": false,
        "option_values": [
          {
            "id": 34,
            "name": "Size-34",
            "presentation": "S",
            "option_type_name": "foo-size-34",
            "option_type_id": 34,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "variant_properties": [

        ],
        "stock_items": [

        ],
        "prices": [

        ]
      }
    }
  ],
  "count": 3,
  "total_count": 3,
  "current_page": 1,
  "pages": 1,
  "per_page": 25
}
```



## Get my wished products


### Request

#### Endpoint

```plaintext
GET /api/wished_products/mine
Accept: application/json
Authorizat IO N: Bearer 5780cc49ea7b204f8ba80f89926f44e7b89e6630a1ecc0a6
Host: example.org
Cookie: 
```

`GET /api/wished_products/mine`

#### Parameters



| Name | Description |
|:-----|:------------|
| q[wishlist_id_eq]  | Anything accessible by ransack can be passed in as query params |
| with_variant  | Include this parameter if you would like the variant to be returned in the                              response with the wished product |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
ETag: W/&quot;b175316d602ca069e9843becb257a074&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 5b362da0-6f8e-4f9f-90d5-515ca96577db
X-Runtime: 0.009586
Vary: Origin
Content-Length: 298
200 OK
```


```json
{
  "wished_products": [
    {
      "id": 22,
      "wishlist_id": 37,
      "variant_id": 58,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 23,
      "wishlist_id": 37,
      "variant_id": 60,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 24,
      "wishlist_id": 37,
      "variant_id": 62,
      "quantity": 1,
      "remark": null
    }
  ],
  "count": 3,
  "total_count": 3,
  "current_page": 1,
  "pages": 1,
  "per_page": 25
}
```



## Update a wishlist


### Request

#### Endpoint

```plaintext
PATCH /api/wished_products/13
Accept: application/json
Authorizat IO N: Bearer 18b6e59ac057de10766d246c0868ffdd7d7cc3f234dfaf33
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/wished_products/:id`

#### Parameters


```json
wished_product[wishlist_id]=30&wished_product[variant_id]=44&wished_product[quantity]=2&wished_product[remark]=Foo+bar
```


| Name | Description |
|:-----|:------------|
| wished_product[wishlist_id]  | Optional. If the wishlist_id is not provided, the product will be created for the spree_api_user's               default wishlist. Admin users can pass another user's wishlist_id |
| wished_product[variant_id] *required* | Wished product variant |
| wished_product[quantity]  | Wished product quantity |
| wished_product[remark]  | Wished product remark |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
ETag: W/&quot;ccbeb4173bbf3dbd937a316d0ad9c39b&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 4d1a2431-c80c-4250-820b-d6aeda1e95b4
X-Runtime: 0.014274
Vary: Origin
Content-Length: 74
200 OK
```


```json
{
  "id": 13,
  "wishlist_id": 30,
  "variant_id": 44,
  "quantity": 2,
  "remark": "Foo bar"
}
```



# Wishlists

Get a single wishlist, accessible by owner of the list, or if it is public

## Create a wishlist


### Request

#### Endpoint

```plaintext
POST /api/wishlists
Accept: application/json
Authorizat IO N: Bearer c15df943e202ebdaebab87709476f720089811905e9be879
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/wishlists`

#### Parameters


```json
wishlist[name]&wishlist[user_id]=18&wishlist[is_default]=true&wishlist[is_public]=false
```


| Name | Description |
|:-----|:------------|
| wishlist[name] *required* | The first wishlist created is given the name "My Wishlist".               Subsequent wishlists must be given a new name. |
| wishlist[user_id]  | User ID must match that of the current_api_user unless the current_api_user is an admin.               User ID will be inferred from the current_api_user unless explicitly provided |
| wishlist[is_default]  | The first wishlist created will automatically be set to default. Subsequent lists will have is_default               set to false. If you pass is_default true it will set all other user wishlists to is_default: false. |
| wishlist[is_public]  | Wishlist is public |
| wishlist[wished_products_attributes]  | You can create a new wishlist with wished products in one step by passing them as nested attributes.               This should be an array of objects. |
| wishlist[wished_products_attributes][variant_id]  | Pass the variant id for a wished product as a nested attribute. |
| wishlist[wished_products_attributes][quantity]  | Pass the quantity for a wished product as a nested attribute |
| wishlist[wished_products_attributes][remark]  | Pass the remark for the specific wished product as a nested attribute. |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
ETag: W/&quot;9580625352b855336d553dc1046ab6ab&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 79389de1-556a-435f-a01c-9d4401b2daa5
X-Runtime: 0.014952
Vary: Origin
Content-Length: 100
201 Created
```


```json
{
  "id": 28,
  "user_id": 18,
  "name": "My Wishlist",
  "is_public": false,
  "is_default": true,
  "wished_products": [

  ]
}
```



## Delete a wishlist


### Request

#### Endpoint

```plaintext
DELETE /api/wishlists/27
Accept: application/json
Authorizat IO N: Bearer ce445ceb2707a1324fd96f6f54398a8a1a2a1b261618c4fb
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`DELETE /api/wishlists/:id`

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
X-Request-Id: b241308f-a16e-4cb1-bcd1-6bf8fe2d7b67
X-Runtime: 0.026164
Vary: Origin
204 No Content
```




## Get a single wishlist


### Request

#### Endpoint

```plaintext
GET /api/wishlists/1
Accept: application/json
Authorizat IO N: Bearer daafb0435de8e1dc2b0b6df31c5e34d69871b04d39f43d8d
Host: example.org
Cookie: 
```

`GET /api/wishlists/:id`

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
ETag: W/&quot;04e8318ea453bcee48ff0e5fe6047963&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 7763f00f-b196-4db9-a678-ce3b8c9260dd
X-Runtime: 0.138002
Vary: Origin
Content-Length: 298
200 OK
```


```json
{
  "id": 1,
  "user_id": 1,
  "name": "Wishlist #1",
  "is_public": false,
  "is_default": true,
  "wished_products": [
    {
      "id": 1,
      "wishlist_id": 1,
      "variant_id": 2,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 2,
      "wishlist_id": 1,
      "variant_id": 4,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 3,
      "wishlist_id": 1,
      "variant_id": 6,
      "quantity": 1,
      "remark": null
    }
  ]
}
```



## Get all wishlists


### Request

#### Endpoint

```plaintext
GET /api/wishlists
Accept: application/json
Authorizat IO N: Bearer aae26c01243e5b991d7af045831c237a868048d83caa5922
Host: example.org
Cookie: 
```

`GET /api/wishlists`

#### Parameters



| Name | Description |
|:-----|:------------|
| q[user_id_eq]  | Anything accessible by ransack can be passed in as query params |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
ETag: W/&quot;5bf333e8fcc1a3852e08adbab76e6c4f&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 45970080-c639-4594-9d0c-5510938f1d99
X-Runtime: 0.009759
Vary: Origin
Content-Length: 890
200 OK
```


```json
{
  "wishlists": [
    {
      "id": 17,
      "user_id": 6,
      "name": "Wishlist #17",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 18,
      "user_id": 7,
      "name": "Wishlist #18",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 19,
      "user_id": 8,
      "name": "Wishlist #19",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 20,
      "user_id": 9,
      "name": "Wishlist #20",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 21,
      "user_id": 10,
      "name": "Wishlist #21",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 22,
      "user_id": 11,
      "name": "Wishlist #22",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 23,
      "user_id": 12,
      "name": "Wishlist #23",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 24,
      "user_id": 13,
      "name": "Wishlist #24",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 25,
      "user_id": 14,
      "name": "Wishlist #25",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 26,
      "user_id": 15,
      "name": "Wishlist #26",
      "is_public": false,
      "is_default": true
    }
  ],
  "count": 10,
  "total_count": 10,
  "current_page": 1,
  "pages": 1,
  "per_page": 25
}
```



## Get my default wishlist


### Request

#### Endpoint

```plaintext
GET /api/wishlist
Accept: application/json
Authorizat IO N: Bearer 5c00d59cac897c890402fee45ad5e7258c41bff3554655e4
Host: example.org
Cookie: 
```

`GET /api/wishlist`

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
ETag: W/&quot;5cfcf904e25fbcef1ea4560da17daa9b&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 77f3117b-da47-4ef8-85a8-3e0d94bf4adf
X-Runtime: 0.009414
Vary: Origin
Content-Length: 300
200 OK
```


```json
{
  "id": 2,
  "user_id": 2,
  "name": "Wishlist #2",
  "is_public": false,
  "is_default": true,
  "wished_products": [
    {
      "id": 4,
      "wishlist_id": 2,
      "variant_id": 8,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 5,
      "wishlist_id": 2,
      "variant_id": 10,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 6,
      "wishlist_id": 2,
      "variant_id": 12,
      "quantity": 1,
      "remark": null
    }
  ]
}
```



## Get my wishlists


### Request

#### Endpoint

```plaintext
GET /api/wishlists/mine
Accept: application/json
Authorizat IO N: Bearer 99ccb0ebb477f4eb061367e83b3513c853318cb468252f99
Host: example.org
Cookie: 
```

`GET /api/wishlists/mine`

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
ETag: W/&quot;c5744a54cc03a93cb69133e83c436845&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: c38b46ca-20e6-4449-b883-45dcdf654b06
X-Runtime: 0.011701
Vary: Origin
Content-Length: 885
200 OK
```


```json
{
  "wishlists": [
    {
      "id": 6,
      "user_id": 4,
      "name": "Wishlist #6",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 7,
      "user_id": 4,
      "name": "Wishlist #7",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 8,
      "user_id": 4,
      "name": "Wishlist #8",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 9,
      "user_id": 4,
      "name": "Wishlist #9",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 10,
      "user_id": 4,
      "name": "Wishlist #10",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 11,
      "user_id": 4,
      "name": "Wishlist #11",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 12,
      "user_id": 4,
      "name": "Wishlist #12",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 13,
      "user_id": 4,
      "name": "Wishlist #13",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 14,
      "user_id": 4,
      "name": "Wishlist #14",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 15,
      "user_id": 4,
      "name": "Wishlist #15",
      "is_public": false,
      "is_default": false
    }
  ],
  "count": 10,
  "total_count": 10,
  "current_page": 1,
  "pages": 1,
  "per_page": 25
}
```



## Update a wishlist


### Request

#### Endpoint

```plaintext
PATCH /api/wishlists/16
Accept: application/json
Authorizat IO N: Bearer e8bdceb295d044619f9839b150923141d0f296ea750985ce
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/wishlists/:id`

#### Parameters


```json
wishlist[name]=Another+Wishlist&wishlist[user_id]=5&wishlist[is_default]=true&wishlist[is_public]=false
```


| Name | Description |
|:-----|:------------|
| wishlist[name] *required* | The first wishlist created is given the name "My Wishlist".               Subsequent wishlists must be given a new name. |
| wishlist[user_id]  | User ID must match that of the current_api_user unless the current_api_user is an admin.               User ID will be inferred from the current_api_user unless explicitly provided |
| wishlist[is_default]  | The first wishlist created will automatically be set to default. Subsequent lists will have is_default               set to false. If you pass is_default true it will set all other user wishlists to is_default: false. |
| wishlist[is_public]  | Wishlist is public |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
ETag: W/&quot;d874b993dae9db203e3b34442d1d188d&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: a2642438-36f6-4aef-8b5e-8c7a09d4e055
X-Runtime: 0.017463
Vary: Origin
Content-Length: 310
200 OK
```


```json
{
  "id": 16,
  "user_id": 5,
  "name": "Another Wishlist",
  "is_public": false,
  "is_default": true,
  "wished_products": [
    {
      "id": 7,
      "wishlist_id": 16,
      "variant_id": 14,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 8,
      "wishlist_id": 16,
      "variant_id": 16,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 9,
      "wishlist_id": 16,
      "variant_id": 18,
      "quantity": 1,
      "remark": null
    }
  ]
}
```



