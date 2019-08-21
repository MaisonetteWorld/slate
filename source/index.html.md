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
PUT /api/orders/R800671325/addresses/1407
Accept: application/json
X-Spree-Order-Token: EOIEZkHy-OWOw33uZkRlOA
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
ETag: W/&quot;838afc71a46ef7fd17e3c483a8cd92a5&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 55035379-c19d-4732-b252-297878956392
X-Runtime: 0.044987
Content-Length: 514
200 OK
```


```json
{
  "id": 1408,
  "firstname": "John the Tester",
  "lastname": null,
  "full_name": "John the Tester",
  "address1": "A Different Road",
  "address2": "Northwest",
  "city": "Herndon",
  "zipcode": "10006",
  "phone": "555-555-0199",
  "company": "Company",
  "alternative_phone": "555-555-0199",
  "country_id": 680,
  "country_iso": "US",
  "state_id": 669,
  "state_name": null,
  "state_text": "AL",
  "country": {
    "id": 680,
    "iso_name": "UNITED STATES",
    "iso": "US",
    "iso3": "USA",
    "name": "United States",
    "numcode": 840
  },
  "state": {
    "id": 669,
    "name": "Alabama",
    "abbr": "AL",
    "country_id": 680
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
X-Spree-Order-Token: rBtjfCl5Kl9FYa9o-aRTCQ
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/braintree/transactions`

#### Parameters


```json
order_id=R093603441&payment_method_id=512&options[restart_checkout]=true&transaction[email]=maryellen.oga%40mckenziemcglynn.com&transaction[nonce]=fake-paypal-billing-agreement-nonce&transaction[phone]=555-555-0199&transaction[address_attributes][first_name]=John&transaction[address_attributes][last_name]=Stamm&transaction[address_attributes][address_line_1]=A+Different+Road&transaction[address_attributes][city]=Herndon&transaction[address_attributes][state_code]=AL&transaction[address_attributes][zip]=10001&transaction[address_attributes][country_code]=US&transaction[payment_type]=PayPalAccount
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
ETag: W/&quot;f1e562c7e884f98f1d0d75048edfd5c4&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 142cf6c1-66f9-4ad0-a7c1-d5b9a06e7b65
X-Runtime: 0.552311
Content-Length: 4757
200 OK
```


```json
{
  "id": 695,
  "number": "R093603441",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2019-08-21T14:01:20.276Z",
  "updated_at": "2019-08-21T14:01:20.978Z",
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
  "token": "rBtjfCl5Kl9FYa9o-aRTCQ",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 512,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 1402,
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
    "country_id": 673,
    "country_iso": "US",
    "state_id": 662,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 673,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 662,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 673
    }
  },
  "ship_address": {
    "id": 1402,
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
    "country_id": 673,
    "country_iso": "US",
    "state_id": 662,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 673,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 662,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 673
    }
  },
  "line_items": [
    {
      "id": 566,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 1710,
      "vendor_id": 4190,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 1710,
        "name": "Product #1 - 2851",
        "sku": "SKU-1",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-1-2851",
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
            "id": 843,
            "name": "Size-1",
            "presentation": "S",
            "option_type_name": "foo-size-1",
            "option_type_id": 778,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 1052,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #2",
      "country_iso": "US",
      "adjustments": [

      ]
    }
  ],
  "payments": [
    {
      "id": 249,
      "source_type": "SolidusPaypalBraintree::Source",
      "source_id": 66,
      "amount": "110.0",
      "display_amount": "$110.00",
      "payment_method_id": 512,
      "state": "checkout",
      "avs_response": null,
      "created_at": "2019-08-21T14:01:20.755Z",
      "updated_at": "2019-08-21T14:01:20.755Z",
      "payment_method": {
        "id": 512,
        "name": "Braintree"
      },
      "source": {
        "id": 66,
        "payment_type": "PayPalAccount",
        "token": "bgx899",
        "created_at": "2019-08-21T14:01:20.754Z",
        "email": "jane.doe@paypal.com"
      }
    }
  ],
  "shipments": [
    {
      "id": 461,
      "tracking": null,
      "tracking_url": null,
      "number": "H48407811142",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R093603441",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 422,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 420,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 422,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 420,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 420,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 256,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 617,
              "name": "ShippingCategory #1"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 1710,
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
      "international_shipping": false
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
X-Spree-Order-Token: Q_Ox87d7Ahhxf5mqCghQtw
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/braintree/transactions`

#### Parameters


```json
order_id=R879769274&payment_method_id=513&options[restart_checkout]=true&transaction[email]=maryellen.oga%40mckenziemcglynn.com&transaction[nonce]=fake-apple-pay-visa-nonce&transaction[phone]=555-555-0199&transaction[address_attributes][first_name]=John&transaction[address_attributes][last_name]=Stamm&transaction[address_attributes][address_line_1]=A+Different+Road&transaction[address_attributes][city]=Herndon&transaction[address_attributes][state_code]=AL&transaction[address_attributes][zip]=10003&transaction[address_attributes][country_code]=US&transaction[payment_type]=ApplePayCard
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
ETag: W/&quot;f6c83c7f2bb46b0f5ea33632a8011f41&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: e44d80f9-aae4-4000-bb01-866b3ad5675e
X-Runtime: 0.203211
Content-Length: 4803
200 OK
```


```json
{
  "id": 696,
  "number": "R879769274",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2019-08-21T14:01:21.363Z",
  "updated_at": "2019-08-21T14:01:21.561Z",
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
  "token": "Q_Ox87d7Ahhxf5mqCghQtw",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 513,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 1405,
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
    "country_id": 674,
    "country_iso": "US",
    "state_id": 663,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 674,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 663,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 674
    }
  },
  "ship_address": {
    "id": 1405,
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
    "country_id": 674,
    "country_iso": "US",
    "state_id": 663,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 674,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 663,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 674
    }
  },
  "line_items": [
    {
      "id": 567,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 1712,
      "vendor_id": 4195,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 1712,
        "name": "Product #2 - 9165",
        "sku": "SKU-3",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-2-9165",
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
            "id": 844,
            "name": "Size-2",
            "presentation": "S",
            "option_type_name": "foo-size-2",
            "option_type_id": 779,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 1053,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #7",
      "country_iso": "US",
      "adjustments": [

      ]
    }
  ],
  "payments": [
    {
      "id": 250,
      "source_type": "SolidusPaypalBraintree::Source",
      "source_id": 67,
      "amount": "110.0",
      "display_amount": "$110.00",
      "payment_method_id": 513,
      "state": "checkout",
      "avs_response": null,
      "created_at": "2019-08-21T14:01:21.451Z",
      "updated_at": "2019-08-21T14:01:21.451Z",
      "payment_method": {
        "id": 513,
        "name": "Braintree"
      },
      "source": {
        "id": 67,
        "payment_type": "ApplePayCard",
        "token": "cg7hsk",
        "created_at": "2019-08-21T14:01:21.450Z",
        "cc_type": "Apple Pay - Visa",
        "last_digits": "1881",
        "month": "12",
        "year": "2020"
      }
    }
  ],
  "shipments": [
    {
      "id": 463,
      "tracking": null,
      "tracking_url": null,
      "number": "H26603258038",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R879769274",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 424,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 421,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 424,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 421,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 421,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 257,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 618,
              "name": "ShippingCategory #2"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 1712,
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
      "international_shipping": false
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
PUT /api/checkouts/R680235169/complete
Accept: application/json
X-Spree-Order-Token: QfVnTZ6H57wrpAxH5eAoQA
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
ETag: W/&quot;4550765c741d8a2d2a46425c0f6eb06e&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 22d9c128-ddb6-491d-b95b-9757f3186b2d
X-Runtime: 2.171142
Content-Length: 4926
200 OK
```


```json
{
  "id": 698,
  "number": "R680235169",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "complete",
  "adjustment_total": "0.0",
  "user_id": 769,
  "created_at": "2019-08-21T14:01:23.049Z",
  "updated_at": "2019-08-21T14:01:26.237Z",
  "completed_at": "2019-08-21T14:01:26.237Z",
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
  "token": "QfVnTZ6H57wrpAxH5eAoQA",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 514,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    },
    {
      "id": 515,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 1409,
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
    "country_id": 681,
    "country_iso": "US",
    "state_id": 670,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 681,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 670,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 681
    }
  },
  "ship_address": {
    "id": 1410,
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
    "country_id": 681,
    "country_iso": "US",
    "state_id": 670,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 681,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 670,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 681
    }
  },
  "line_items": [
    {
      "id": 568,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 1721,
      "vendor_id": 4219,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 1721,
        "name": "Product #10 - 5159",
        "sku": "SKU-12",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-10-5159",
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
            "id": 845,
            "name": "Size-3",
            "presentation": "S",
            "option_type_name": "foo-size-3",
            "option_type_id": 780,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 1061,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #31",
      "country_iso": "US",
      "adjustments": [

      ]
    }
  ],
  "payments": [
    {
      "id": 251,
      "source_type": "SolidusPaypalBraintree::Source",
      "source_id": 68,
      "amount": "110.0",
      "display_amount": "$110.00",
      "payment_method_id": 514,
      "state": "completed",
      "avs_response": "M",
      "created_at": "2019-08-21T14:01:23.147Z",
      "updated_at": "2019-08-21T14:01:26.084Z",
      "payment_method": {
        "id": 514,
        "name": "Braintree"
      },
      "source": {
        "id": 68,
        "payment_type": "CreditCard",
        "token": "jg6v4q",
        "created_at": "2019-08-21T14:01:23.146Z",
        "cc_type": "Visa",
        "last_digits": "1881",
        "month": "12",
        "year": "2020"
      }
    }
  ],
  "shipments": [
    {
      "id": 464,
      "tracking": "U10000",
      "tracking_url": null,
      "number": "H62873756426",
      "cost": "100.0",
      "shipped_at": null,
      "state": "ready",
      "order_id": "R680235169",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 425,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 422,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 425,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 422,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 422,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 258,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 624,
              "name": "ShippingCategory #8"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 1721,
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
      "international_shipping": false
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
PATCH /api/checkouts/R418211770
Accept: application/json
X-Spree-Order-Token: dqBVyGZBl7laixOluDNVIw
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=517&order[payment_attributes][][source_attributes][nonce]=fake-apple-pay-visa-nonce&order[payment_attributes][][source_attributes][payment_type]=ApplePayCard
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
ETag: W/&quot;4a74fb137d4acb0c8d9394beeb243f89&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 1622a26f-8993-4d16-88b2-203b7d32b0bf
X-Runtime: 0.100593
Content-Length: 4324
200 OK
```


```json
{
  "id": 700,
  "number": "R418211770",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 771,
  "created_at": "2019-08-21T14:01:27.563Z",
  "updated_at": "2019-08-21T14:01:27.785Z",
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
  "token": "dqBVyGZBl7laixOluDNVIw",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 517,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 1413,
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
    "country_id": 683,
    "country_iso": "US",
    "state_id": 672,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 683,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 672,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 683
    }
  },
  "ship_address": {
    "id": 1414,
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
    "country_id": 683,
    "country_iso": "US",
    "state_id": 672,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 683,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 672,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 683
    }
  },
  "line_items": [
    {
      "id": 570,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 1725,
      "vendor_id": 4229,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 1725,
        "name": "Product #12 - 8542",
        "sku": "SKU-16",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-12-8542",
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
            "id": 847,
            "name": "Size-5",
            "presentation": "S",
            "option_type_name": "foo-size-5",
            "option_type_id": 782,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 1063,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #41",
      "country_iso": "US",
      "adjustments": [

      ]
    }
  ],
  "payments": [

  ],
  "shipments": [
    {
      "id": 468,
      "tracking": null,
      "tracking_url": null,
      "number": "H48432565628",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R418211770",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 429,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 424,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 429,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 424,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 424,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 260,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 626,
              "name": "ShippingCategory #10"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 1725,
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
      "international_shipping": false
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
PATCH /api/checkouts/R822066001
Accept: application/json
X-Spree-Order-Token: UsZQsh7pKtTgXIlif41qFg
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=519&order[payment_attributes][][source_attributes][nonce]=fake-paypal-billing-agreement-nonce&order[payment_attributes][][source_attributes][payment_type]=PayPalAccount
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
ETag: W/&quot;b8031f4392ed251352c3a16061898c32&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 078fe58d-f7fc-477b-b59d-a3814028cd95
X-Runtime: 0.099887
Content-Length: 4324
200 OK
```


```json
{
  "id": 702,
  "number": "R822066001",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 773,
  "created_at": "2019-08-21T14:01:28.578Z",
  "updated_at": "2019-08-21T14:01:28.789Z",
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
  "token": "UsZQsh7pKtTgXIlif41qFg",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 519,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 1417,
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
    "country_id": 685,
    "country_iso": "US",
    "state_id": 674,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 685,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 674,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 685
    }
  },
  "ship_address": {
    "id": 1418,
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
    "country_id": 685,
    "country_iso": "US",
    "state_id": 674,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 685,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 674,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 685
    }
  },
  "line_items": [
    {
      "id": 572,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 1729,
      "vendor_id": 4239,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 1729,
        "name": "Product #14 - 9974",
        "sku": "SKU-20",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-14-9974",
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
            "id": 849,
            "name": "Size-7",
            "presentation": "S",
            "option_type_name": "foo-size-7",
            "option_type_id": 784,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 1065,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #51",
      "country_iso": "US",
      "adjustments": [

      ]
    }
  ],
  "payments": [

  ],
  "shipments": [
    {
      "id": 472,
      "tracking": null,
      "tracking_url": null,
      "number": "H38432336720",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R822066001",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 433,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 426,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 433,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 426,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 426,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 262,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 628,
              "name": "ShippingCategory #12"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 1729,
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
      "international_shipping": false
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
PATCH /api/checkouts/R457551445
Accept: application/json
X-Spree-Order-Token: NgWh8GFISwK0RJxUdtKlfw
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=518&order[payment_attributes][][source_attributes][nonce]=fake-valid-visa-nonce&order[payment_attributes][][source_attributes][payment_type]=CreditCard
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
ETag: W/&quot;6d5e25e773fae353f9dc50b397ceca5f&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 4d1376f8-ba13-488d-9afd-effaedf4091c
X-Runtime: 0.108024
Content-Length: 4324
200 OK
```


```json
{
  "id": 701,
  "number": "R457551445",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 772,
  "created_at": "2019-08-21T14:01:28.062Z",
  "updated_at": "2019-08-21T14:01:28.302Z",
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
  "token": "NgWh8GFISwK0RJxUdtKlfw",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 518,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 1415,
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
    "country_id": 684,
    "country_iso": "US",
    "state_id": 673,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 684,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 673,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 684
    }
  },
  "ship_address": {
    "id": 1416,
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
    "country_id": 684,
    "country_iso": "US",
    "state_id": 673,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 684,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 673,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 684
    }
  },
  "line_items": [
    {
      "id": 571,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 1727,
      "vendor_id": 4234,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 1727,
        "name": "Product #13 - 9980",
        "sku": "SKU-18",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-13-9980",
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
            "id": 848,
            "name": "Size-6",
            "presentation": "S",
            "option_type_name": "foo-size-6",
            "option_type_id": 783,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 1064,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #46",
      "country_iso": "US",
      "adjustments": [

      ]
    }
  ],
  "payments": [

  ],
  "shipments": [
    {
      "id": 470,
      "tracking": null,
      "tracking_url": null,
      "number": "H42060477063",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R457551445",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 431,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 425,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 431,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 425,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 425,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 261,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 627,
              "name": "ShippingCategory #11"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 1727,
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
      "international_shipping": false
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
PATCH /api/checkouts/R558453018
Accept: application/json
X-Spree-Order-Token: 2P68fGAhNa6ZOg3Vsfsj_Q
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=516&order[payment_attributes][][source_attributes][wallet_payment_source_id]=40
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
ETag: W/&quot;3885e3a4a211a395f2c81d5222b47f5c&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: d7160ef9-d216-44e2-b676-c2a34030c590
X-Runtime: 0.106902
Content-Length: 4323
200 OK
```


```json
{
  "id": 699,
  "number": "R558453018",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 770,
  "created_at": "2019-08-21T14:01:27.048Z",
  "updated_at": "2019-08-21T14:01:27.277Z",
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
  "token": "2P68fGAhNa6ZOg3Vsfsj_Q",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 516,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 1411,
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
    "country_id": 682,
    "country_iso": "US",
    "state_id": 671,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 682,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 671,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 682
    }
  },
  "ship_address": {
    "id": 1412,
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
    "country_id": 682,
    "country_iso": "US",
    "state_id": 671,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 682,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 671,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 682
    }
  },
  "line_items": [
    {
      "id": 569,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 1723,
      "vendor_id": 4224,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 1723,
        "name": "Product #11 - 6197",
        "sku": "SKU-14",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-11-6197",
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
            "id": 846,
            "name": "Size-4",
            "presentation": "S",
            "option_type_name": "foo-size-4",
            "option_type_id": 781,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 1062,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #36",
      "country_iso": "US",
      "adjustments": [

      ]
    }
  ],
  "payments": [

  ],
  "shipments": [
    {
      "id": 466,
      "tracking": null,
      "tracking_url": null,
      "number": "H72277741487",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R558453018",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 427,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 423,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 427,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 423,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 423,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 259,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 625,
              "name": "ShippingCategory #9"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 1723,
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
      "international_shipping": false
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
POST /api/orders/R874518807/line_items
Accept: application/json
X-Spree-Order-Token: ZDTMxrZ5yj678e8U9z28kQ
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/:order_number/line_items`

#### Parameters


```json
line_item[variant_id]=1739&line_item[options][vendor_id]=4262
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
ETag: W/&quot;fa9eb93b0372820c2fd716064f942b85&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 5dd39d7d-9da5-472c-a705-cc3fab383068
X-Runtime: 0.094060
Content-Length: 873
201 Created
```


```json
{
  "id": 575,
  "quantity": 1,
  "price": "19.99",
  "variant_id": 1739,
  "vendor_id": 4262,
  "single_display_amount": "$19.99",
  "display_amount": "$19.99",
  "total": "19.99",
  "final_sale": false,
  "backordered": null,
  "promotionable": true,
  "variant": {
    "id": 1739,
    "name": "Product #19 - 1595",
    "sku": "SKU-30",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": false,
    "slug": "product-19-1595",
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
        "id": 854,
        "name": "Size-12",
        "presentation": "S",
        "option_type_name": "foo-size-12",
        "option_type_id": 789,
        "option_type_presentation": "Size"
      }
    ],
    "images": [

    ],
    "product_id": 1070,
    "brand": null,
    "brand_slug": null,
    "brand_description": null
  },
  "vendor_name": "Vendor #74",
  "country_iso": null,
  "adjustments": [

  ]
}
```



## Deleting a line item


### Request

#### Endpoint

```plaintext
DELETE /api/orders/R892507534/line_items/576
Accept: application/json
X-Spree-Order-Token: -8JzmbWKR_AnAsd2Szko0w
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
X-Request-Id: 13f162d2-9672-46cf-b5a5-01d2b83dba5d
X-Runtime: 0.064849
204 No Content
```




## Updating a line item


### Request

#### Endpoint

```plaintext
PUT /api/orders/R205079027/line_items/573
Accept: application/json
X-Spree-Order-Token: EWdA2GttYkpy5plCFtlFlQ
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
ETag: W/&quot;396a5116e48044fecc3575499f55daf2&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: bc10890d-dec0-4241-a953-d734314f713a
X-Runtime: 0.103637
Content-Length: 868
200 OK
```


```json
{
  "id": 573,
  "quantity": 2,
  "price": "10.0",
  "variant_id": 1733,
  "vendor_id": 4251,
  "single_display_amount": "$10.00",
  "display_amount": "$20.00",
  "total": "20.0",
  "final_sale": false,
  "backordered": null,
  "promotionable": true,
  "variant": {
    "id": 1733,
    "name": "Product #16 - 9751",
    "sku": "SKU-24",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": false,
    "slug": "product-16-9751",
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
        "id": 851,
        "name": "Size-9",
        "presentation": "S",
        "option_type_name": "foo-size-9",
        "option_type_id": 786,
        "option_type_presentation": "Size"
      }
    ],
    "images": [

    ],
    "product_id": 1067,
    "brand": null,
    "brand_slug": null,
    "brand_description": null
  },
  "vendor_name": "Vendor #63",
  "country_iso": "US",
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
ETag: W/&quot;36624ae9f45ad9a194d320f3ea87ac47&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: f6c4a9b2-d1e9-4ccc-b351-7981fd73bd02
X-Runtime: 0.007074
Content-Length: 134
200 OK
```


```json
[
  {
    "id": 724,
    "name": "Kids",
    "navigation_url": "/navigation/kids",
    "parent_id": 723,
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
Authorization: 
X-Spree-Order-Token: 
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/cart`

#### Parameters


```json
user_id&order_token&line_item[variant_id]=1745&line_item[quantity]=2&line_item[vendor_id]=4271
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
ETag: W/&quot;728d59a3e747ac4450e2149ecdf465f5&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: c2d3c528-5270-4640-9028-b29939f20d61
X-Runtime: 0.104753
Content-Length: 2326
200 OK
```


```json
{
  "id": 706,
  "number": "R893884682",
  "item_total": "39.98",
  "total": "39.98",
  "ship_total": "0.0",
  "state": "cart",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2019-08-21T14:01:31.425Z",
  "updated_at": "2019-08-21T14:01:31.456Z",
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
  "token": "CzsR112S36zCLXthxXn5DQ",
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
      "id": 577,
      "quantity": 2,
      "price": "19.99",
      "variant_id": 1745,
      "vendor_id": 4271,
      "single_display_amount": "$19.99",
      "display_amount": "$39.98",
      "total": "39.98",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 1745,
        "name": "Product #22 - 2033",
        "sku": "SKU-36",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-22-2033",
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
            "id": 857,
            "name": "Size-15",
            "presentation": "S",
            "option_type_name": "foo-size-15",
            "option_type_id": 792,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 1073,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #83",
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
Authorization: Bearer 153057c5175821bed9d7c3a470e6198cb5fb61c915945752
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
ETag: W/&quot;098d90e6e97a9cd3c2e06b37f7da20f3&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: acb6547e-7c55-429c-a2b3-f9e05f05befb
X-Runtime: 0.017178
Content-Length: 305
200 OK
```


```json
{
  "orders": [
    {
      "number": "R734374513",
      "completed_at": "2019-08-21T14:01:33.028Z",
      "total": "120.0",
      "state": "Complete",
      "shipment_state": "shipped",
      "shipments": [
        {
          "number": "H34720743147",
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
GET /api/orders/R854070240
Accept: application/json
Authorization: Bearer 731c12c219e5842796edb9a83f2007aa8121cf4827fa2da1
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
ETag: W/&quot;97738b86d7c8f34669ff27699b3c8c2e&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 8fd3b8a3-4eff-4abc-a3b3-9c69b049f4c5
X-Runtime: 0.146480
Content-Length: 9344
200 OK
```


```json
{
  "id": 707,
  "number": "R854070240",
  "item_total": "20.0",
  "total": "120.0",
  "ship_total": "100.0",
  "state": "complete",
  "adjustment_total": "0.0",
  "user_id": 785,
  "created_at": "2019-08-21T14:01:31.765Z",
  "updated_at": "2019-08-21T14:01:32.098Z",
  "completed_at": "2019-08-21T14:01:31.842Z",
  "payment_total": "120.0",
  "shipment_state": "shipped",
  "payment_state": "paid",
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
  "token": "BznAYacZGK_yHaxoXkweBQ",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 523,
      "name": "Credit Card",
      "partial_name": "gateway",
      "method_type": "gateway"
    },
    {
      "id": 524,
      "name": "Credit Card",
      "partial_name": "gateway",
      "method_type": "gateway"
    }
  ],
  "bill_address": {
    "id": 1427,
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
    "country_id": 692,
    "country_iso": "US",
    "state_id": 681,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 692,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 681,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 692
    }
  },
  "ship_address": {
    "id": 1428,
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
    "country_id": 692,
    "country_iso": "US",
    "state_id": 681,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 692,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 681,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 692
    }
  },
  "line_items": [
    {
      "id": 578,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 1747,
      "vendor_id": 4279,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 1747,
        "name": "Product #23 - 4180",
        "sku": "SKU-38",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-23-4180",
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
            "id": 858,
            "name": "Size-16",
            "presentation": "S",
            "option_type_name": "foo-size-16",
            "option_type_id": 793,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 1074,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #91",
      "country_iso": "US",
      "adjustments": [
        {
          "id": 86,
          "source_type": "Spree::TaxRate",
          "source_id": 15,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 578,
          "amount": "2.0",
          "label": "VAT 5%",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-08-21T14:01:32.070Z",
          "updated_at": "2019-08-21T14:01:32.081Z",
          "display_amount": "$2.00"
        },
        {
          "id": 80,
          "source_type": "Spree::PromotionAction",
          "source_id": 38,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 578,
          "amount": "5.0",
          "label": "foo",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-08-21T14:01:31.998Z",
          "updated_at": "2019-08-21T14:01:31.998Z",
          "display_amount": "$5.00"
        },
        {
          "id": 79,
          "source_type": "Spree::PromotionAction",
          "source_id": 38,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 578,
          "amount": "5.0",
          "label": "foo",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-08-21T14:01:31.989Z",
          "updated_at": "2019-08-21T14:01:31.989Z",
          "display_amount": "$5.00"
        }
      ]
    },
    {
      "id": 579,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 1747,
      "vendor_id": 4279,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 1747,
        "name": "Product #23 - 4180",
        "sku": "SKU-38",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-23-4180",
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
            "id": 858,
            "name": "Size-16",
            "presentation": "S",
            "option_type_name": "foo-size-16",
            "option_type_id": 793,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 1074,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #91",
      "country_iso": "US",
      "adjustments": [
        {
          "id": 87,
          "source_type": "Spree::TaxRate",
          "source_id": 16,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 579,
          "amount": "1.5",
          "label": "VAT 5%",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-08-21T14:01:32.096Z",
          "updated_at": "2019-08-21T14:01:32.106Z",
          "display_amount": "$1.50"
        },
        {
          "id": 81,
          "source_type": "Spree::PromotionAction",
          "source_id": 38,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 579,
          "amount": "5.0",
          "label": "bar",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-08-21T14:01:32.006Z",
          "updated_at": "2019-08-21T14:01:32.006Z",
          "display_amount": "$5.00"
        }
      ]
    }
  ],
  "payments": [
    {
      "id": 252,
      "source_type": "Spree::CreditCard",
      "source_id": 221,
      "amount": "120.0",
      "display_amount": "$120.00",
      "payment_method_id": 523,
      "state": "completed",
      "avs_response": null,
      "created_at": "2019-08-21T14:01:31.904Z",
      "updated_at": "2019-08-21T14:01:31.904Z",
      "payment_method": {
        "id": 523,
        "name": "Credit Card"
      },
      "source": {
        "id": 221,
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
      "id": 476,
      "tracking": "U10000",
      "tracking_url": null,
      "number": "H83013320357",
      "cost": "100.0",
      "shipped_at": "2019-08-21T14:01:31.928Z",
      "state": "shipped",
      "order_id": "R854070240",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 437,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 430,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 437,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 430,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 430,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 266,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 634,
              "name": "ShippingCategory #18"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 1747,
          "quantity": 1,
          "states": {
            "shipped": 1
          }
        },
        {
          "variant_id": 1747,
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
          "adjustable_id": 476,
          "amount": "-10.0",
          "label": "Shipping",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-08-21T14:01:32.022Z",
          "updated_at": "2019-08-21T14:01:32.022Z",
          "display_amount": "-$10.00"
        },
        {
          "id": 82,
          "source_type": "Spree::PromotionAction",
          "source_id": 38,
          "adjustable_type": "Spree::Shipment",
          "adjustable_id": 476,
          "amount": "-9.99",
          "label": "Shipping",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-08-21T14:01:32.014Z",
          "updated_at": "2019-08-21T14:01:32.014Z",
          "display_amount": "-$9.99"
        }
      ],
      "stock_location_address": "NY Warehouse, Washington, AL",
      "country_iso": "US",
      "international_shipping": false
    }
  ],
  "adjustments": [
    {
      "id": 84,
      "source_type": "Spree::Promotion",
      "source_id": 56,
      "adjustable_type": "Spree::Order",
      "adjustable_id": 707,
      "amount": "20.0",
      "label": "adj1",
      "promotion_code_id": null,
      "finalized": false,
      "eligible": true,
      "created_at": "2019-08-21T14:01:32.027Z",
      "updated_at": "2019-08-21T14:01:32.027Z",
      "display_amount": "$20.00"
    },
    {
      "id": 85,
      "source_type": "Spree::Promotion",
      "source_id": 56,
      "adjustable_type": "Spree::Order",
      "adjustable_id": 707,
      "amount": "30.0",
      "label": "adj2",
      "promotion_code_id": null,
      "finalized": false,
      "eligible": true,
      "created_at": "2019-08-21T14:01:32.031Z",
      "updated_at": "2019-08-21T14:01:32.031Z",
      "display_amount": "$30.00"
    }
  ],
  "permissions": {
    "can_update": false
  },
  "credit_cards": [
    {
      "id": 221,
      "month": "12",
      "year": "2020",
      "cc_type": null,
      "last_digits": "1111",
      "name": "Spree Commerce",
      "address": {
        "id": 1427,
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
        "country_id": 692,
        "country_iso": "US",
        "state_id": 681,
        "state_name": null,
        "state_text": "AL",
        "country": {
          "id": 692,
          "iso_name": "UNITED STATES",
          "iso": "US",
          "iso3": "USA",
          "name": "United States",
          "numcode": 840
        },
        "state": {
          "id": 681,
          "name": "Alabama",
          "abbr": "AL",
          "country_id": 692
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
GET /api/orders/R580375678
Accept: application/json
Authorization: 39739883bb1b283102f57df83fce9d41fb40a45f2b29846c
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
X-Request-Id: 60db5ba2-0288-4368-a666-109dd8049edf
X-Runtime: 0.011217
Content-Length: 58
401 Unauthorized
```


```json
{
  "error": "You are not authorized to perform that action."
}
```



# Passwords

Reset password by token

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
user[email]=email10%40example.com
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
X-Request-Id: f3bb0c0e-2d6f-45fa-888f-a2f3f7b29efc
X-Runtime: 0.003809
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
user[email]=email11%40example.com&user[password]=secret
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
Authorization: Bearer 643756108c6d5b7bce2a2d8c56e1b1f1b2fced174269324f
ETag: W/&quot;7b7b4c7d4912141e4d16d2da38bca7f5&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 03f5f018-c937-4cd3-a22a-3e7358b88e8b
X-Runtime: 0.008625
Content-Length: 553
200 OK
```


```json
{
  "id": 776,
  "email": "email11@example.com",
  "persistence_token": null,
  "perishable_token": null,
  "last_request_at": null,
  "login": "email11@example.com",
  "ship_address_id": null,
  "bill_address_id": null,
  "created_at": "2019-08-21T14:01:29.408Z",
  "updated_at": "2019-08-21T14:01:29.410Z",
  "spree_api_key": "643756108c6d5b7bce2a2d8c56e1b1f1b2fced174269324f",
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
X-Request-Id: aed2700a-241f-445d-b2a1-26e3a56e0297
X-Runtime: 0.022185
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
Date: Wed, 21 Aug 2019 14:01:21 GMT
Surrogate-Control: max-age=900
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;63a1502162bb7f6d224526e3d678c02d&quot;
X-Request-Id: 99e7a975-126b-4c80-b22d-493b38ff4cc1
X-Runtime: 0.089039
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
      "id": 1054,
      "name": "Product #3 - 9583",
      "description": "As seen on TV!",
      "available_on": "2018-08-21T14:01:21.639Z",
      "slug": "product-3-9583",
      "meta_description": null,
      "meta_keywords": null,
      "shipping_category_id": 619,
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
        "id": 1713,
        "name": "Product #3 - 9583",
        "sku": "SKU-5",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-3-9583",
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
GET /api/products/product-4-5912
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
Date: Wed, 21 Aug 2019 14:01:21 GMT
Surrogate-Control: max-age=900
Surrogate-Key: product_id=1
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;cc4023718c707c646b547490d21ad7b8&quot;
X-Request-Id: e053ac0e-ed21-4109-a24a-7c012e1b94c4
X-Runtime: 0.043639
Content-Length: 832
200 OK
```


```json
{
  "id": 1055,
  "name": "Product #4 - 5912",
  "description": "As seen on TV!",
  "available_on": "2018-08-21T14:01:21.822Z",
  "slug": "product-4-5912",
  "meta_description": null,
  "meta_keywords": null,
  "shipping_category_id": 620,
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
    "id": 1714,
    "name": "Product #4 - 5912",
    "sku": "SKU-6",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": true,
    "slug": "product-4-5912",
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
X-Request-Id: a3442c2f-e9b4-41e0-afe5-40068ec405a9
X-Runtime: 0.016089
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
GET /api/taxons/products?id=716
Host: example.org
Cookie: 
```

`GET /api/taxons/products`

#### Parameters


```json
id: 716
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
ETag: W/&quot;b8a55eacd86baa6206ec70b2ae806e7a&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 5d719e65-a258-4515-b9fc-c008f79b1abf
X-Runtime: 0.055177
Content-Length: 1104
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
      "id": 1057,
      "name": "Product #6 - 7127",
      "description": "As seen on TV!",
      "available_on": "2018-08-21T14:01:22.106Z",
      "slug": "product-6-7127",
      "meta_description": null,
      "meta_keywords": null,
      "shipping_category_id": 622,
      "taxon_ids": [
        716
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
        "id": 1716,
        "name": "Product #6 - 7127",
        "sku": "SKU-8",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-6-7127",
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
          "taxon_id": 716,
          "position": 1,
          "taxon": {
            "id": 716,
            "name": "Ruby on Rails",
            "pretty_name": "Ruby on Rails",
            "permalink": "ruby-on-rails",
            "parent_id": null,
            "taxonomy_id": 257
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
ETag: W/&quot;b604ce547dfa4f3b8fb3144878fc75bd&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: ff23bb9d-a7b8-4a73-89d4-c427d7b9d8a8
X-Runtime: 0.043902
Content-Length: 1105
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
      "id": 1059,
      "name": "Product #8 - 6340",
      "description": "As seen on TV!",
      "available_on": "2018-08-21T14:01:22.471Z",
      "slug": "product-8-6340",
      "meta_description": null,
      "meta_keywords": null,
      "shipping_category_id": 623,
      "taxon_ids": [
        720
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
        "id": 1718,
        "name": "Product #8 - 6340",
        "sku": "SKU-10",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-8-6340",
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
          "taxon_id": 720,
          "position": 1,
          "taxon": {
            "id": 720,
            "name": "Ruby on Rails",
            "pretty_name": "Ruby on Rails",
            "permalink": "ruby-on-rails",
            "parent_id": null,
            "taxonomy_id": 259
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
GET /api/returns/RA051021641
Authorization: Bearer f63e9eb24b558f431374e856ad5f88a44cc1051d50b40569
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
ETag: W/&quot;7c46c5ba007f6a578ecf08fe23ff34fb&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 38c5ea89-fc13-4660-b528-f5ca6731727c
X-Runtime: 0.043098
Content-Length: 2773
200 OK
```


```json
{
  "id": 23,
  "number": "RA051021641",
  "state": "authorized",
  "order_id": 712,
  "memo": "Items were broken",
  "created_at": "2019-08-21T14:01:34.338Z",
  "updated_at": "2019-08-21T14:01:34.338Z",
  "reason": {
    "id": 66,
    "name": "Defect #5",
    "active": true,
    "mutable": true,
    "created_at": "2019-08-21T14:01:34.334Z",
    "updated_at": "2019-08-21T14:01:34.334Z",
    "mirakl_code": null
  },
  "order": {
    "id": 712,
    "number": "R090230228",
    "item_total": "10.0",
    "total": "110.0",
    "state": "complete",
    "adjustment_total": "0.0",
    "user_id": 791,
    "completed_at": "2019-08-21T14:01:34.270Z",
    "bill_address_id": 1437,
    "ship_address_id": 1438,
    "payment_total": "110.0",
    "shipment_state": "shipped",
    "payment_state": "paid",
    "email": "email25@example.com",
    "special_instructions": null,
    "created_at": "2019-08-21T14:01:34.212Z",
    "updated_at": "2019-08-21T14:01:34.319Z",
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
    "guest_token": "HGjhCH7jrgSwnbZ20ZrPFQ",
    "canceled_at": null,
    "canceler_id": null,
    "store_id": 751,
    "approver_name": null,
    "frontend_viewable": true
  },
  "ship_address": {
    "id": 1438,
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
    "country_id": 697,
    "country_iso": "US",
    "state_id": 686,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 697,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 686,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 697
    }
  },
  "bill_address": {
    "id": 1437,
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
    "country_id": 697,
    "country_iso": "US",
    "state_id": 686,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 697,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 686,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 697
    }
  },
  "return_items": [
    {
      "name": "Product #28 - 5227",
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
        "id": 533,
        "name": "Credit Card"
      },
      "source": {
        "id": 226,
        "month": "12",
        "year": "2020",
        "cc_type": null,
        "last_digits": "1111",
        "name": "Spree Commerce",
        "gateway_customer_profile_id": "BGS-153430",
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
Authorization: Bearer d382ba41d29e3b0b377e43af888aa150296afb795567e185
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
ETag: W/&quot;e397f278319096927daed791aa9ce21a&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 2efb7836-c994-440f-8f2b-e11d75bbf9ca
X-Runtime: 0.015246
Content-Length: 164
200 OK
```


```json
{
  "return_authorizations": [
    {
      "number": "RA055357828",
      "created_at": "2019-08-21T14:01:33.518Z",
      "return_amount": "10.0",
      "order_number": "R979286441",
      "state": "authorized"
    }
  ]
}
```



## returns a 200


### Request

#### Endpoint

```plaintext
GET /api/returns/RA022830536
Authorization: Bearer f8842618414291f26b5b989ce916010f6abbf7b152277766
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
ETag: W/&quot;be8d41fd3e90e4098268f0d303a97d60&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 5b572587-77ee-4576-a60c-e7e9ed73ba31
X-Runtime: 0.051937
Content-Length: 2696
200 OK
```


```json
{
  "id": 22,
  "number": "RA022830536",
  "state": "authorized",
  "order_id": 711,
  "memo": "Items were broken",
  "created_at": "2019-08-21T14:01:33.949Z",
  "updated_at": "2019-08-21T14:01:33.949Z",
  "reason": {
    "id": 64,
    "name": "Defect #3",
    "active": true,
    "mutable": true,
    "created_at": "2019-08-21T14:01:33.943Z",
    "updated_at": "2019-08-21T14:01:33.943Z",
    "mirakl_code": null
  },
  "order": {
    "id": 711,
    "number": "R160934625",
    "item_total": "10.0",
    "total": "110.0",
    "state": "complete",
    "adjustment_total": "0.0",
    "user_id": 790,
    "completed_at": "2019-08-21T14:01:33.865Z",
    "bill_address_id": 1435,
    "ship_address_id": 1436,
    "payment_total": "110.0",
    "shipment_state": "shipped",
    "payment_state": "paid",
    "email": "email24@example.com",
    "special_instructions": null,
    "created_at": "2019-08-21T14:01:33.805Z",
    "updated_at": "2019-08-21T14:01:33.926Z",
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
    "guest_token": "BzCI37sGY3cAArFSrWcYjQ",
    "canceled_at": null,
    "canceler_id": null,
    "store_id": 750,
    "approver_name": null,
    "frontend_viewable": true
  },
  "ship_address": {
    "id": 1436,
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
    "country_id": 696,
    "country_iso": "US",
    "state_id": 685,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 696,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 685,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 696
    }
  },
  "bill_address": {
    "id": 1435,
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
    "country_id": 696,
    "country_iso": "US",
    "state_id": 685,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 696,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 685,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 696
    }
  },
  "return_items": [
    {
      "name": "Product #27 - 5260",
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
        "id": 531,
        "name": "Credit Card"
      },
      "source": {
        "id": 225,
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
GET /api/returns/RA835821827
Authorization: Bearer 138317b65e3c59b3eead2670a38c10a08bfe02a15a5650d3
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
X-Request-Id: 48e657a2-82b8-4fa0-88b3-bd9e44c13758
X-Runtime: 0.010312
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
Authorization: Bearer 02efd4cba9d0eb97738f2ed9f5403e5ee2ed58d3ee435812
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
ETag: W/&quot;264021412c6840ef20578da022d0124f&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 624e7379-e7cb-4298-bd3d-f09b77bc3af6
X-Runtime: 0.034708
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
      "created_at": "2019-08-21T14:01:29.648Z"
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
Authorization: Bearer 82e3ebec0c0686d6bd0375cd85a9c27392d9ec39e1fa8bda
ETag: W/&quot;7525f7c486f618b1da9e5e86f9adbd2a&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: cc9b2cfe-fefe-4073-bd3f-aee54f3146e3
X-Runtime: 0.005805
Content-Length: 553
200 OK
```


```json
{
  "id": 777,
  "email": "email12@example.com",
  "persistence_token": null,
  "perishable_token": null,
  "last_request_at": null,
  "login": "email12@example.com",
  "ship_address_id": null,
  "bill_address_id": null,
  "created_at": "2019-08-21T14:01:29.425Z",
  "updated_at": "2019-08-21T14:01:29.427Z",
  "spree_api_key": "82e3ebec0c0686d6bd0375cd85a9c27392d9ec39e1fa8bda",
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
Authorization: Bearer 589c5eb3985e8114e4e0b10823680afd38b3466447b1f97d
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
Authorization: Bearer 589c5eb3985e8114e4e0b10823680afd38b3466447b1f97d
ETag: W/&quot;ce544d3205408254428ae25e10dd8e13&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 2bf1785e-f800-4bb3-8cb3-c3cb6f77d033
X-Runtime: 0.037828
Content-Length: 1309
200 OK
```


```json
{
  "email": "email13@example.com",
  "first_name": null,
  "last_name": null,
  "id": 778,
  "subscribed": null,
  "addresses": [
    {
      "id": 1420,
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
      "country_id": 687,
      "country_iso": "US",
      "state_id": 676,
      "state_name": null,
      "state_text": "AL",
      "country_name": "United States",
      "default": true
    },
    {
      "id": 1419,
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
      "country_id": 687,
      "country_iso": "US",
      "state_id": 676,
      "state_name": null,
      "state_text": "AL",
      "country_name": "United States",
      "default": false
    }
  ],
  "payment_sources": [
    {
      "default": true,
      "id": 70,
      "payment_type": "CreditCard",
      "token": null,
      "created_at": "2019-08-21T14:01:29.496Z",
      "cc_type": null,
      "last_digits": null,
      "month": null,
      "year": null
    },
    {
      "default": false,
      "id": 71,
      "payment_type": "ApplePayCard",
      "token": null,
      "created_at": "2019-08-21T14:01:29.518Z",
      "cc_type": null,
      "last_digits": null,
      "month": null,
      "year": null
    },
    {
      "default": false,
      "id": 72,
      "payment_type": "PayPalAccount",
      "token": null,
      "created_at": "2019-08-21T14:01:29.536Z",
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
Authorization: Bearer 648b3358d766fe77b8d3555b351f1e1496e3e2f92dc4262a
ETag: W/&quot;cbcb8e2ba7509f28f7b52222cb0c51d3&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: a26a152d-6e61-42b5-b106-7540e333e1c0
X-Runtime: 0.018750
Content-Length: 157
201 Created
```


```json
{
  "id": 779,
  "email": "test@example.com",
  "created_at": "2019-08-21T14:01:29.588Z",
  "updated_at": "2019-08-21T14:01:29.590Z",
  "bill_address": null,
  "ship_address": null
}
```



# Variant



## Fetching a variant


### Request

#### Endpoint

```plaintext
GET /api/variants/1731
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
ETag: W/&quot;493aa9227b743970e4660eac8183c05f&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: cd3248ee-6cbf-4c18-8dfe-e0a6817ab6ab
X-Runtime: 0.102063
Content-Length: 1463
200 OK
```


```json
{
  "id": 1731,
  "name": "Product #15 - 7473",
  "sku": "SKU-22",
  "weight": "0.0",
  "height": null,
  "width": null,
  "depth": null,
  "is_master": false,
  "slug": "product-15-7473",
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
      "id": 850,
      "name": "Size-8",
      "presentation": "S",
      "option_type_name": "foo-size-8",
      "option_type_id": 785,
      "option_type_presentation": "Size"
    }
  ],
  "images": [
    {
      "id": 23,
      "position": 1,
      "attachment_content_type": "image/jpeg",
      "attachment_file_name": "thinking-cat.jpg",
      "type": "Spree::Image",
      "attachment_updated_at": "2019-08-21T14:01:29.056Z",
      "attachment_width": 489,
      "attachment_height": 490,
      "alt": null,
      "viewable_type": "Spree::Variant",
      "viewable_id": 1731,
      "mini_url": "/spree/products/23/mini/thinking-cat.jpg?1566396089",
      "small_url": "/spree/products/23/small/thinking-cat.jpg?1566396089",
      "product_url": "/spree/products/23/product/thinking-cat.jpg?1566396089",
      "large_url": "/spree/products/23/large/thinking-cat.jpg?1566396089"
    }
  ],
  "variant_properties": [

  ],
  "stock_items": [

  ],
  "prices": [
    {
      "id": 1554,
      "vendor_id": 4246,
      "price": "10.0",
      "original_price": "10.0",
      "discount_percent": 0.0,
      "total_on_hand": 0,
      "country_iso": null,
      "final_sale": false,
      "on_sale": false
    },
    {
      "id": 1555,
      "vendor_id": 4247,
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
Authorization: Bearer 9184c36c8780d44d2bf312b3c6e02de16cc120bd1a5f02cc
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
ETag: W/&quot;8db0452d933f4e26fabdf5e08c4e49d7&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 20107392-fbf1-46ab-9b7e-1e4e1b06e063
X-Runtime: 0.013428
Content-Length: 199
200 OK
```


```json
[
  {
    "id": 46,
    "user_id": 797,
    "payment_source_type": "SolidusPaypalBraintree::Source",
    "payment_source_id": 75,
    "default": false,
    "created_at": "2019-08-21T14:01:34.948Z",
    "updated_at": "2019-08-21T14:01:34.948Z"
  }
]
```



## Remove the payment from the user wallet


### Request

#### Endpoint

```plaintext
DELETE /api/wallet_payment_sources/44
Accept: application/json
Authorization: Bearer d582f36c0cd0645394e3390eb73ae7a40ce1142fdc76dd94
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
X-Request-Id: ca898435-74c8-4334-8e67-ab3c1a3ebf64
X-Runtime: 0.031420
204 No Content
```




## Set a wallet payment source as the default user payment method


### Request

#### Endpoint

```plaintext
POST /api/wallet_payment_sources/45/default
Accept: application/json
Authorization: Bearer 0beba697edafeb17d5bf8839c58a085ff0edaa3c43b63148
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
X-Request-Id: da791360-ca41-4bfc-b83a-458ce885b02d
X-Runtime: 0.010797
204 No Content
```




