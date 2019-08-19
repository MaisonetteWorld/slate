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
PUT /api/orders/R091882634/addresses/1401
Accept: application/json
X-Spree-Order-Token: GhMiKWJhBCIrzSfnc04yuQ
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
ETag: W/&quot;cdec2cd77ab0e268543ca464e9584be7&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 91e757e4-1cc8-41ed-93dc-6af7171bec42
X-Runtime: 0.081314
Content-Length: 514
200 OK
```


```json
{
  "id": 1402,
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
  "country_id": 588,
  "country_iso": "US",
  "state_id": 577,
  "state_name": null,
  "state_text": "AL",
  "country": {
    "id": 588,
    "iso_name": "UNITED STATES",
    "iso": "US",
    "iso3": "USA",
    "name": "United States",
    "numcode": 840
  },
  "state": {
    "id": 577,
    "name": "Alabama",
    "abbr": "AL",
    "country_id": 588
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
X-Spree-Order-Token: 6FthmJ3vMLk9LUzERpr__A
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/braintree/transactions`

#### Parameters


```json
order_id=R068747387&payment_method_id=521&options[restart_checkout]=true&transaction[email]=maryellen.oga%40mckenziemcglynn.com&transaction[nonce]=fake-paypal-billing-agreement-nonce&transaction[phone]=555-555-0199&transaction[address_attributes][first_name]=John&transaction[address_attributes][last_name]=Stamm&transaction[address_attributes][address_line_1]=A+Different+Road&transaction[address_attributes][city]=Herndon&transaction[address_attributes][state_code]=AL&transaction[address_attributes][zip]=10019&transaction[address_attributes][country_code]=US&transaction[payment_type]=PayPalAccount
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
ETag: W/&quot;debdcb5f64d4edda293726ca445251c4&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 72d17798-caa5-45f5-9a4a-bc2d544729c2
X-Runtime: 0.252906
Content-Length: 4761
200 OK
```


```json
{
  "id": 704,
  "number": "R068747387",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2019-08-19T20:05:16.811Z",
  "updated_at": "2019-08-19T20:05:17.031Z",
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
  "token": "6FthmJ3vMLk9LUzERpr__A",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 521,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 1421,
    "firstname": "John",
    "lastname": "Stamm",
    "full_name": "John Stamm",
    "address1": "A Different Road",
    "address2": null,
    "city": "Herndon",
    "zipcode": "10019",
    "phone": "555-555-0199",
    "company": null,
    "alternative_phone": null,
    "country_id": 598,
    "country_iso": "US",
    "state_id": 587,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 598,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 587,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 598
    }
  },
  "ship_address": {
    "id": 1421,
    "firstname": "John",
    "lastname": "Stamm",
    "full_name": "John Stamm",
    "address1": "A Different Road",
    "address2": null,
    "city": "Herndon",
    "zipcode": "10019",
    "phone": "555-555-0199",
    "company": null,
    "alternative_phone": null,
    "country_id": 598,
    "country_iso": "US",
    "state_id": 587,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 598,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 587,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 598
    }
  },
  "line_items": [
    {
      "id": 575,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 1589,
      "vendor_id": 4412,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 1589,
        "name": "Product #19 - 658",
        "sku": "SKU-30",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-19-658",
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
            "id": 697,
            "name": "Size-12",
            "presentation": "S",
            "option_type_name": "foo-size-12",
            "option_type_id": 634,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 968,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #74",
      "country_iso": "US",
      "adjustments": [

      ]
    }
  ],
  "payments": [
    {
      "id": 250,
      "source_type": "SolidusPaypalBraintree::Source",
      "source_id": 71,
      "amount": "110.0",
      "display_amount": "$110.00",
      "payment_method_id": 521,
      "state": "checkout",
      "avs_response": null,
      "created_at": "2019-08-19T20:05:16.918Z",
      "updated_at": "2019-08-19T20:05:16.918Z",
      "payment_method": {
        "id": 521,
        "name": "Braintree"
      },
      "source": {
        "id": 71,
        "payment_type": "PayPalAccount",
        "token": "bgx899",
        "created_at": "2019-08-19T20:05:16.917Z",
        "email": "jane.doe@paypal.com"
      }
    }
  ],
  "shipments": [
    {
      "id": 473,
      "tracking": null,
      "tracking_url": null,
      "number": "H33556755004",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R068747387",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 434,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 428,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 434,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 428,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 428,
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
              "id": 541,
              "name": "ShippingCategory #15"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 1589,
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
X-Spree-Order-Token: Swd7uIdCFu2ZfJz7KPevGg
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/braintree/transactions`

#### Parameters


```json
order_id=R410077971&payment_method_id=522&options[restart_checkout]=true&transaction[email]=maryellen.oga%40mckenziemcglynn.com&transaction[nonce]=fake-apple-pay-visa-nonce&transaction[phone]=555-555-0199&transaction[address_attributes][first_name]=John&transaction[address_attributes][last_name]=Stamm&transaction[address_attributes][address_line_1]=A+Different+Road&transaction[address_attributes][city]=Herndon&transaction[address_attributes][state_code]=AL&transaction[address_attributes][zip]=10021&transaction[address_attributes][country_code]=US&transaction[payment_type]=ApplePayCard
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
ETag: W/&quot;5bf0daebe37b55e1509281382b2a0f3c&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: e3091817-01e2-4552-b335-2fd71110453a
X-Runtime: 0.223636
Content-Length: 4809
200 OK
```


```json
{
  "id": 705,
  "number": "R410077971",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2019-08-19T20:05:17.347Z",
  "updated_at": "2019-08-19T20:05:17.559Z",
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
  "token": "Swd7uIdCFu2ZfJz7KPevGg",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 522,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 1424,
    "firstname": "John",
    "lastname": "Stamm",
    "full_name": "John Stamm",
    "address1": "A Different Road",
    "address2": null,
    "city": "Herndon",
    "zipcode": "10021",
    "phone": "555-555-0199",
    "company": null,
    "alternative_phone": null,
    "country_id": 599,
    "country_iso": "US",
    "state_id": 588,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 599,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 588,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 599
    }
  },
  "ship_address": {
    "id": 1424,
    "firstname": "John",
    "lastname": "Stamm",
    "full_name": "John Stamm",
    "address1": "A Different Road",
    "address2": null,
    "city": "Herndon",
    "zipcode": "10021",
    "phone": "555-555-0199",
    "company": null,
    "alternative_phone": null,
    "country_id": 599,
    "country_iso": "US",
    "state_id": 588,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 599,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 588,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 599
    }
  },
  "line_items": [
    {
      "id": 576,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 1591,
      "vendor_id": 4418,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 1591,
        "name": "Product #20 - 4173",
        "sku": "SKU-32",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-20-4173",
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
            "id": 698,
            "name": "Size-13",
            "presentation": "S",
            "option_type_name": "foo-size-13",
            "option_type_id": 635,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 969,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #79",
      "country_iso": "US",
      "adjustments": [

      ]
    }
  ],
  "payments": [
    {
      "id": 251,
      "source_type": "SolidusPaypalBraintree::Source",
      "source_id": 72,
      "amount": "110.0",
      "display_amount": "$110.00",
      "payment_method_id": 522,
      "state": "checkout",
      "avs_response": null,
      "created_at": "2019-08-19T20:05:17.447Z",
      "updated_at": "2019-08-19T20:05:17.447Z",
      "payment_method": {
        "id": 522,
        "name": "Braintree"
      },
      "source": {
        "id": 72,
        "payment_type": "ApplePayCard",
        "token": "cg7hsk",
        "created_at": "2019-08-19T20:05:17.446Z",
        "cc_type": "Apple Pay - Visa",
        "last_digits": "1881",
        "month": "12",
        "year": "2020"
      }
    }
  ],
  "shipments": [
    {
      "id": 475,
      "tracking": null,
      "tracking_url": null,
      "number": "H54207853356",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R410077971",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 436,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 429,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 436,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 429,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 429,
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
              "id": 542,
              "name": "ShippingCategory #16"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 1591,
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
PUT /api/checkouts/R613798631/complete
Accept: application/json
X-Spree-Order-Token: ZtDE3h9LKv3_XDkJb_fSYQ
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
ETag: W/&quot;7986e4d965b0a6baa8cd5f68a6fcc336&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 5d015202-309d-4dd2-a752-5697a587c231
X-Runtime: 2.327219
Content-Length: 4927
200 OK
```


```json
{
  "id": 699,
  "number": "R613798631",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "complete",
  "adjustment_total": "0.0",
  "user_id": 775,
  "created_at": "2019-08-19T20:05:10.284Z",
  "updated_at": "2019-08-19T20:05:13.744Z",
  "completed_at": "2019-08-19T20:05:13.744Z",
  "payment_total": "110.0",
  "shipment_state": "ready",
  "payment_state": "paid",
  "email": "email10@example.com",
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
  "token": "ZtDE3h9LKv3_XDkJb_fSYQ",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 515,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    },
    {
      "id": 516,
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
    "zipcode": "10009",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 593,
    "country_iso": "US",
    "state_id": 582,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 593,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 582,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 593
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
    "zipcode": "10010",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 593,
    "country_iso": "US",
    "state_id": 582,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 593,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 582,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 593
    }
  },
  "line_items": [
    {
      "id": 570,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 1579,
      "vendor_id": 4382,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 1579,
        "name": "Product #14 - 6111",
        "sku": "SKU-20",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-14-6111",
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
            "id": 692,
            "name": "Size-7",
            "presentation": "S",
            "option_type_name": "foo-size-7",
            "option_type_id": 629,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 963,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #49",
      "country_iso": "US",
      "adjustments": [

      ]
    }
  ],
  "payments": [
    {
      "id": 249,
      "source_type": "SolidusPaypalBraintree::Source",
      "source_id": 69,
      "amount": "110.0",
      "display_amount": "$110.00",
      "payment_method_id": 515,
      "state": "completed",
      "avs_response": "M",
      "created_at": "2019-08-19T20:05:10.383Z",
      "updated_at": "2019-08-19T20:05:13.576Z",
      "payment_method": {
        "id": 515,
        "name": "Braintree"
      },
      "source": {
        "id": 69,
        "payment_type": "CreditCard",
        "token": "8297dq",
        "created_at": "2019-08-19T20:05:10.381Z",
        "cc_type": "Visa",
        "last_digits": "1881",
        "month": "12",
        "year": "2020"
      }
    }
  ],
  "shipments": [
    {
      "id": 463,
      "tracking": "U10000",
      "tracking_url": null,
      "number": "H62230741676",
      "cost": "100.0",
      "shipped_at": null,
      "state": "ready",
      "order_id": "R613798631",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 424,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 423,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 424,
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
              "id": 253,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 536,
              "name": "ShippingCategory #10"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 1579,
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
PATCH /api/checkouts/R287543233
Accept: application/json
X-Spree-Order-Token: P2K8RB7sP5cN3ioC_6XDng
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=519&order[payment_attributes][][source_attributes][nonce]=fake-apple-pay-visa-nonce&order[payment_attributes][][source_attributes][payment_type]=ApplePayCard
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
ETag: W/&quot;2af1ffa98d0bf52ad3c8ab9f88434dba&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: a0f1dfed-9b1c-4684-9d14-8ca94ba2ab31
X-Runtime: 0.112942
Content-Length: 4326
200 OK
```


```json
{
  "id": 702,
  "number": "R287543233",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 778,
  "created_at": "2019-08-19T20:05:15.711Z",
  "updated_at": "2019-08-19T20:05:15.923Z",
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
  "token": "P2K8RB7sP5cN3ioC_6XDng",
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
    "id": 1415,
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
    "country_id": 596,
    "country_iso": "US",
    "state_id": 585,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 596,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 585,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 596
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
    "zipcode": "10016",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 596,
    "country_iso": "US",
    "state_id": 585,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 596,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 585,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 596
    }
  },
  "line_items": [
    {
      "id": 573,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 1585,
      "vendor_id": 4400,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 1585,
        "name": "Product #17 - 9013",
        "sku": "SKU-26",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-17-9013",
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
            "id": 695,
            "name": "Size-10",
            "presentation": "S",
            "option_type_name": "foo-size-10",
            "option_type_id": 632,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 966,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #64",
      "country_iso": "US",
      "adjustments": [

      ]
    }
  ],
  "payments": [

  ],
  "shipments": [
    {
      "id": 469,
      "tracking": null,
      "tracking_url": null,
      "number": "H00554442878",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R287543233",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 430,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 426,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 430,
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
              "id": 256,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 539,
              "name": "ShippingCategory #13"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 1585,
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
PATCH /api/checkouts/R512144812
Accept: application/json
X-Spree-Order-Token: 61ffrmJWkG-EmNCZMFvQYQ
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=517&order[payment_attributes][][source_attributes][nonce]=fake-paypal-billing-agreement-nonce&order[payment_attributes][][source_attributes][payment_type]=PayPalAccount
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
ETag: W/&quot;337231683c5273778e5afbb38c8ec5b2&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 5229131c-91bb-4fc6-b140-ba9055a4501b
X-Runtime: 0.108808
Content-Length: 4324
200 OK
```


```json
{
  "id": 700,
  "number": "R512144812",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 776,
  "created_at": "2019-08-19T20:05:14.575Z",
  "updated_at": "2019-08-19T20:05:14.853Z",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "email11@example.com",
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
  "token": "61ffrmJWkG-EmNCZMFvQYQ",
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
    "id": 1411,
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
    "country_id": 594,
    "country_iso": "US",
    "state_id": 583,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 594,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 583,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 594
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
    "zipcode": "10012",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 594,
    "country_iso": "US",
    "state_id": 583,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 594,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 583,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 594
    }
  },
  "line_items": [
    {
      "id": 571,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 1581,
      "vendor_id": 4388,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 1581,
        "name": "Product #15 - 1000",
        "sku": "SKU-22",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-15-1000",
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
            "id": 693,
            "name": "Size-8",
            "presentation": "S",
            "option_type_name": "foo-size-8",
            "option_type_id": 630,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 964,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #54",
      "country_iso": "US",
      "adjustments": [

      ]
    }
  ],
  "payments": [

  ],
  "shipments": [
    {
      "id": 465,
      "tracking": null,
      "tracking_url": null,
      "number": "H66276675440",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R512144812",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 426,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 424,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 426,
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
              "id": 254,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 537,
              "name": "ShippingCategory #11"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 1581,
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
PATCH /api/checkouts/R220893823
Accept: application/json
X-Spree-Order-Token: Ch4761k0CmwM-P9cFx2Miw
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
ETag: W/&quot;621a4b6354b6dbbca8ca13721153c854&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: fc2ffa05-ff68-4dcf-8937-722d0faff268
X-Runtime: 0.136021
Content-Length: 4324
200 OK
```


```json
{
  "id": 701,
  "number": "R220893823",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 777,
  "created_at": "2019-08-19T20:05:15.157Z",
  "updated_at": "2019-08-19T20:05:15.399Z",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
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
  "token": "Ch4761k0CmwM-P9cFx2Miw",
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
    "id": 1413,
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
    "country_id": 595,
    "country_iso": "US",
    "state_id": 584,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 595,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 584,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 595
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
    "zipcode": "10014",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 595,
    "country_iso": "US",
    "state_id": 584,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 595,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 584,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 595
    }
  },
  "line_items": [
    {
      "id": 572,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 1583,
      "vendor_id": 4394,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 1583,
        "name": "Product #16 - 1750",
        "sku": "SKU-24",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-16-1750",
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
            "id": 694,
            "name": "Size-9",
            "presentation": "S",
            "option_type_name": "foo-size-9",
            "option_type_id": 631,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 965,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #59",
      "country_iso": "US",
      "adjustments": [

      ]
    }
  ],
  "payments": [

  ],
  "shipments": [
    {
      "id": 467,
      "tracking": null,
      "tracking_url": null,
      "number": "H02186053884",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R220893823",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 428,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 425,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 428,
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
              "id": 255,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 538,
              "name": "ShippingCategory #12"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 1583,
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
PATCH /api/checkouts/R834535631
Accept: application/json
X-Spree-Order-Token: QMJIR-taosD88gvG-1C9vw
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=520&order[payment_attributes][][source_attributes][wallet_payment_source_id]=43
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
ETag: W/&quot;593f048be9186132c81499957aeb43c6&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: deb8b5f1-f9f8-4ca6-ab97-09b7e6531532
X-Runtime: 0.133400
Content-Length: 4326
200 OK
```


```json
{
  "id": 703,
  "number": "R834535631",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 779,
  "created_at": "2019-08-19T20:05:16.235Z",
  "updated_at": "2019-08-19T20:05:16.471Z",
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
  "token": "QMJIR-taosD88gvG-1C9vw",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 520,
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
    "zipcode": "10017",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 597,
    "country_iso": "US",
    "state_id": 586,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 597,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 586,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 597
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
    "zipcode": "10018",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 597,
    "country_iso": "US",
    "state_id": 586,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 597,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 586,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 597
    }
  },
  "line_items": [
    {
      "id": 574,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 1587,
      "vendor_id": 4406,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 1587,
        "name": "Product #18 - 3223",
        "sku": "SKU-28",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-18-3223",
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
            "id": 696,
            "name": "Size-11",
            "presentation": "S",
            "option_type_name": "foo-size-11",
            "option_type_id": 633,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 967,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #69",
      "country_iso": "US",
      "adjustments": [

      ]
    }
  ],
  "payments": [

  ],
  "shipments": [
    {
      "id": 471,
      "tracking": null,
      "tracking_url": null,
      "number": "H55152830315",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R834535631",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 432,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 427,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 432,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 427,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 427,
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
              "id": 540,
              "name": "ShippingCategory #14"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 1587,
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
POST /api/orders/R495082591/line_items
Accept: application/json
X-Spree-Order-Token: oRLaGb1ww5GugFKLhW0xgw
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/:order_number/line_items`

#### Parameters


```json
line_item[variant_id]=1575&line_item[options][vendor_id]=4371
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
ETag: W/&quot;d25f99579ec5db9d2c87db2ad20888ef&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 0d84fd69-6b2c-41ac-907a-a664610fd1b4
X-Runtime: 0.093570
Content-Length: 870
201 Created
```


```json
{
  "id": 568,
  "quantity": 1,
  "price": "19.99",
  "variant_id": 1575,
  "vendor_id": 4371,
  "single_display_amount": "$19.99",
  "display_amount": "$19.99",
  "total": "19.99",
  "final_sale": false,
  "backordered": null,
  "promotionable": true,
  "variant": {
    "id": 1575,
    "name": "Product #12 - 5035",
    "sku": "SKU-16",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": false,
    "slug": "product-12-5035",
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
        "id": 690,
        "name": "Size-5",
        "presentation": "S",
        "option_type_name": "foo-size-5",
        "option_type_id": 627,
        "option_type_presentation": "Size"
      }
    ],
    "images": [

    ],
    "product_id": 961,
    "brand": null,
    "brand_slug": null,
    "brand_description": null
  },
  "vendor_name": "Vendor #39",
  "country_iso": null,
  "adjustments": [

  ]
}
```



## Deleting a line item


### Request

#### Endpoint

```plaintext
DELETE /api/orders/R677583147/line_items/566
Accept: application/json
X-Spree-Order-Token: O4op9VeiiKNp87Oxtvtqfw
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
X-Request-Id: 3e96e125-5b7c-4cf5-81da-ceb17f69d55f
X-Runtime: 0.106105
204 No Content
```




## Updating a line item


### Request

#### Endpoint

```plaintext
PUT /api/orders/R086647668/line_items/569
Accept: application/json
X-Spree-Order-Token: pKh__KVhv2HFUvfig_MyNg
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
ETag: W/&quot;d662ebb7c5236eb646154de29b89cc50&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: ea5ea003-5e13-4f56-b133-02958ff4cd23
X-Runtime: 0.108706
Content-Length: 867
200 OK
```


```json
{
  "id": 569,
  "quantity": 2,
  "price": "10.0",
  "variant_id": 1577,
  "vendor_id": 4376,
  "single_display_amount": "$10.00",
  "display_amount": "$20.00",
  "total": "20.0",
  "final_sale": false,
  "backordered": null,
  "promotionable": true,
  "variant": {
    "id": 1577,
    "name": "Product #13 - 3442",
    "sku": "SKU-18",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": false,
    "slug": "product-13-3442",
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
        "id": 691,
        "name": "Size-6",
        "presentation": "S",
        "option_type_name": "foo-size-6",
        "option_type_id": 628,
        "option_type_presentation": "Size"
      }
    ],
    "images": [

    ],
    "product_id": 962,
    "brand": null,
    "brand_slug": null,
    "brand_description": null
  },
  "vendor_name": "Vendor #44",
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
ETag: W/&quot;4460c2dd8c5e3e1b2fb4fc0bfb640bc3&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 5825cd2f-7917-49df-8252-0e4b62a07e53
X-Runtime: 0.005844
Content-Length: 134
200 OK
```


```json
[
  {
    "id": 661,
    "name": "Kids",
    "navigation_url": "/navigation/kids",
    "parent_id": 660,
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
user_id&order_token&line_item[variant_id]=1601&line_item[quantity]=2&line_item[vendor_id]=4441
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
ETag: W/&quot;4be9229350c2278436cd53514e81090a&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 9de187ad-dda2-41f6-a5ad-5f728e8d619a
X-Runtime: 0.125812
Content-Length: 2325
200 OK
```


```json
{
  "id": 709,
  "number": "R659183202",
  "item_total": "39.98",
  "total": "39.98",
  "ship_total": "0.0",
  "state": "cart",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2019-08-19T20:05:19.706Z",
  "updated_at": "2019-08-19T20:05:19.742Z",
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
  "token": "ccXVlRaswUNoEeUH1dgFZA",
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
      "id": 583,
      "quantity": 2,
      "price": "19.99",
      "variant_id": 1601,
      "vendor_id": 4441,
      "single_display_amount": "$19.99",
      "display_amount": "$39.98",
      "total": "39.98",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 1601,
        "name": "Product #25 - 6927",
        "sku": "SKU-42",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-25-6927",
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
            "id": 703,
            "name": "Size-18",
            "presentation": "S",
            "option_type_name": "foo-size-18",
            "option_type_id": 640,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 974,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #98",
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
Authorization: Bearer 12548ca9a8ee5a38cf6d0176f2872ec8712693ec1fe1b809
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
ETag: W/&quot;e2316c29df6769ba8203009a7feb76d4&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: a2707b2e-c881-4f50-8c83-7f860ef22b58
X-Runtime: 0.027411
Content-Length: 305
200 OK
```


```json
{
  "orders": [
    {
      "number": "R839240567",
      "completed_at": "2019-08-19T20:05:17.963Z",
      "total": "120.0",
      "state": "Complete",
      "shipment_state": "shipped",
      "shipments": [
        {
          "number": "H31761876817",
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
GET /api/orders/R462858315
Accept: application/json
Authorization: Bearer b5df6121f18591517865dabc9cb938d9767643a5715d3dfe
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
ETag: W/&quot;81d7420daa945dc92c8ed2278da0158a&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 2c90a320-de48-425c-9fa9-86a2c54264ea
X-Runtime: 0.162357
Content-Length: 9342
200 OK
```


```json
{
  "id": 707,
  "number": "R462858315",
  "item_total": "20.0",
  "total": "120.0",
  "ship_total": "100.0",
  "state": "complete",
  "adjustment_total": "0.0",
  "user_id": 783,
  "created_at": "2019-08-19T20:05:18.415Z",
  "updated_at": "2019-08-19T20:05:18.666Z",
  "completed_at": "2019-08-19T20:05:18.481Z",
  "payment_total": "120.0",
  "shipment_state": "shipped",
  "payment_state": "paid",
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
  "token": "RTaOpTVo1PzKrqcVQOojqA",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 525,
      "name": "Credit Card",
      "partial_name": "gateway",
      "method_type": "gateway"
    },
    {
      "id": 526,
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
    "country_id": 601,
    "country_iso": "US",
    "state_id": 590,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 601,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 590,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 601
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
    "country_id": 601,
    "country_iso": "US",
    "state_id": 590,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 601,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 590,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 601
    }
  },
  "line_items": [
    {
      "id": 579,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 1595,
      "vendor_id": 4430,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 1595,
        "name": "Product #22 - 7718",
        "sku": "SKU-36",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-22-7718",
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
            "id": 700,
            "name": "Size-15",
            "presentation": "S",
            "option_type_name": "foo-size-15",
            "option_type_id": 637,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 971,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #89",
      "country_iso": "US",
      "adjustments": [
        {
          "id": 86,
          "source_type": "Spree::TaxRate",
          "source_id": 15,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 579,
          "amount": "2.0",
          "label": "VAT 5%",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-08-19T20:05:18.642Z",
          "updated_at": "2019-08-19T20:05:18.651Z",
          "display_amount": "$2.00"
        },
        {
          "id": 80,
          "source_type": "Spree::PromotionAction",
          "source_id": 38,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 579,
          "amount": "5.0",
          "label": "foo",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-08-19T20:05:18.562Z",
          "updated_at": "2019-08-19T20:05:18.562Z",
          "display_amount": "$5.00"
        },
        {
          "id": 79,
          "source_type": "Spree::PromotionAction",
          "source_id": 38,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 579,
          "amount": "5.0",
          "label": "foo",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-08-19T20:05:18.556Z",
          "updated_at": "2019-08-19T20:05:18.556Z",
          "display_amount": "$5.00"
        }
      ]
    },
    {
      "id": 580,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 1595,
      "vendor_id": 4430,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 1595,
        "name": "Product #22 - 7718",
        "sku": "SKU-36",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-22-7718",
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
            "id": 700,
            "name": "Size-15",
            "presentation": "S",
            "option_type_name": "foo-size-15",
            "option_type_id": 637,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 971,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #89",
      "country_iso": "US",
      "adjustments": [
        {
          "id": 87,
          "source_type": "Spree::TaxRate",
          "source_id": 16,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 580,
          "amount": "1.5",
          "label": "VAT 5%",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-08-19T20:05:18.663Z",
          "updated_at": "2019-08-19T20:05:18.679Z",
          "display_amount": "$1.50"
        },
        {
          "id": 81,
          "source_type": "Spree::PromotionAction",
          "source_id": 38,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 580,
          "amount": "5.0",
          "label": "bar",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-08-19T20:05:18.570Z",
          "updated_at": "2019-08-19T20:05:18.570Z",
          "display_amount": "$5.00"
        }
      ]
    }
  ],
  "payments": [
    {
      "id": 253,
      "source_type": "Spree::CreditCard",
      "source_id": 222,
      "amount": "120.0",
      "display_amount": "$120.00",
      "payment_method_id": 525,
      "state": "completed",
      "avs_response": null,
      "created_at": "2019-08-19T20:05:18.502Z",
      "updated_at": "2019-08-19T20:05:18.502Z",
      "payment_method": {
        "id": 525,
        "name": "Credit Card"
      },
      "source": {
        "id": 222,
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
      "id": 477,
      "tracking": "U10000",
      "tracking_url": null,
      "number": "H27805782860",
      "cost": "100.0",
      "shipped_at": "2019-08-19T20:05:18.523Z",
      "state": "shipped",
      "order_id": "R462858315",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 438,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 431,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 438,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 431,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 431,
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
              "id": 544,
              "name": "ShippingCategory #18"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 1595,
          "quantity": 1,
          "states": {
            "shipped": 1
          }
        },
        {
          "variant_id": 1595,
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
          "adjustable_id": 477,
          "amount": "-10.0",
          "label": "Shipping",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-08-19T20:05:18.596Z",
          "updated_at": "2019-08-19T20:05:18.596Z",
          "display_amount": "-$10.00"
        },
        {
          "id": 82,
          "source_type": "Spree::PromotionAction",
          "source_id": 38,
          "adjustable_type": "Spree::Shipment",
          "adjustable_id": 477,
          "amount": "-9.99",
          "label": "Shipping",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-08-19T20:05:18.583Z",
          "updated_at": "2019-08-19T20:05:18.583Z",
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
      "created_at": "2019-08-19T20:05:18.604Z",
      "updated_at": "2019-08-19T20:05:18.604Z",
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
      "created_at": "2019-08-19T20:05:18.607Z",
      "updated_at": "2019-08-19T20:05:18.607Z",
      "display_amount": "$30.00"
    }
  ],
  "permissions": {
    "can_update": false
  },
  "credit_cards": [
    {
      "id": 222,
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
        "country_id": 601,
        "country_iso": "US",
        "state_id": 590,
        "state_name": null,
        "state_text": "AL",
        "country": {
          "id": 601,
          "iso_name": "UNITED STATES",
          "iso": "US",
          "iso3": "USA",
          "name": "United States",
          "numcode": 840
        },
        "state": {
          "id": 590,
          "name": "Alabama",
          "abbr": "AL",
          "country_id": 601
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
GET /api/orders/R260466243
Accept: application/json
Authorization: 16a0f5f558266f857885846d447b7fc0b473ff1c46c76ca3
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
X-Request-Id: 7da281ec-4df2-4ce8-a31a-c0e6236cf9e5
X-Runtime: 0.009190
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
user[email]=email24%40example.com
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
X-Request-Id: 08b4b88b-5299-4ccc-b728-600bdfe99642
X-Runtime: 0.002965
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
user[email]=email25%40example.com&user[password]=secret
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
Authorization: Bearer 1b2840e65b8b1e2f96855fdae68a1d36c0d175f2a20c8ceb
ETag: W/&quot;b1644694f891a854b03b64aed30b3d59&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: d1ab5b47-b1b2-495a-ac77-538276eb5914
X-Runtime: 0.004183
Content-Length: 553
200 OK
```


```json
{
  "id": 791,
  "email": "email25@example.com",
  "persistence_token": null,
  "perishable_token": null,
  "last_request_at": null,
  "login": "email25@example.com",
  "ship_address_id": null,
  "bill_address_id": null,
  "created_at": "2019-08-19T20:05:20.017Z",
  "updated_at": "2019-08-19T20:05:20.018Z",
  "spree_api_key": "1b2840e65b8b1e2f96855fdae68a1d36c0d175f2a20c8ceb",
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
X-Request-Id: e8c588a2-00de-4fe6-8e11-1fd0ba2ec438
X-Runtime: 0.027215
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
Date: Mon, 19 Aug 2019 20:05:06 GMT
Surrogate-Control: max-age=900
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;91f3d6c803c690738b1b21297a42705f&quot;
X-Request-Id: c8d0d82b-491d-4d3c-be58-f42c9ba4cf72
X-Runtime: 0.331223
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
      "id": 950,
      "name": "Product #1 - 1701",
      "description": "As seen on TV!",
      "available_on": "2018-08-19T20:05:05.675Z",
      "slug": "product-1-1701",
      "meta_description": null,
      "meta_keywords": null,
      "shipping_category_id": 527,
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
        "id": 1559,
        "name": "Product #1 - 1701",
        "sku": "SKU-1",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-1-1701",
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
GET /api/products/product-6-1300
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
Date: Mon, 19 Aug 2019 20:05:07 GMT
Surrogate-Control: max-age=900
Surrogate-Key: product_id=1
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;00aa7b0552dd0a981ce6d13f9a1fa29c&quot;
X-Request-Id: 609d39af-77f3-4b76-a9ac-1d31d2dc1165
X-Runtime: 0.052966
Content-Length: 831
200 OK
```


```json
{
  "id": 955,
  "name": "Product #6 - 1300",
  "description": "As seen on TV!",
  "available_on": "2018-08-19T20:05:07.154Z",
  "slug": "product-6-1300",
  "meta_description": null,
  "meta_keywords": null,
  "shipping_category_id": 530,
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
    "id": 1564,
    "name": "Product #6 - 1300",
    "sku": "SKU-6",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": true,
    "slug": "product-6-1300",
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
X-Request-Id: 55972cba-de91-41b0-9338-808b21dade97
X-Runtime: 0.022136
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
GET /api/taxons/products?id=653
Host: example.org
Cookie: 
```

`GET /api/taxons/products`

#### Parameters


```json
id: 653
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
ETag: W/&quot;a99d327d43e935425ea98bd8c85c922a&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 2283ecb5-d382-448a-a320-693a17b720d8
X-Runtime: 0.044616
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
      "id": 951,
      "name": "Product #2 - 4838",
      "description": "As seen on TV!",
      "available_on": "2018-08-19T20:05:06.476Z",
      "slug": "product-2-4838",
      "meta_description": null,
      "meta_keywords": null,
      "shipping_category_id": 528,
      "taxon_ids": [
        653
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
        "id": 1560,
        "name": "Product #2 - 4838",
        "sku": "SKU-2",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-2-4838",
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
          "taxon_id": 653,
          "position": 1,
          "taxon": {
            "id": 653,
            "name": "Ruby on Rails",
            "pretty_name": "Ruby on Rails",
            "permalink": "ruby-on-rails",
            "parent_id": null,
            "taxonomy_id": 232
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
ETag: W/&quot;f72853ea16947faad03b930bd01337ce&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: b50b58b9-468e-4e09-8854-530bb219a719
X-Runtime: 0.035338
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
      "id": 953,
      "name": "Product #4 - 6027",
      "description": "As seen on TV!",
      "available_on": "2018-08-19T20:05:06.897Z",
      "slug": "product-4-6027",
      "meta_description": null,
      "meta_keywords": null,
      "shipping_category_id": 529,
      "taxon_ids": [
        657
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
        "id": 1562,
        "name": "Product #4 - 6027",
        "sku": "SKU-4",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-4-6027",
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
          "taxon_id": 657,
          "position": 1,
          "taxon": {
            "id": 657,
            "name": "Ruby on Rails",
            "pretty_name": "Ruby on Rails",
            "permalink": "ruby-on-rails",
            "parent_id": null,
            "taxonomy_id": 234
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
GET /api/returns/RA380620433
Authorization: Bearer cd068d0b6c4f7d619135aacd24aca214c1742d82c0253b68
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
ETag: W/&quot;425286bed8f726aad1485d1fcf9edac2&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 9e557a30-300d-423e-b930-17052868b1af
X-Runtime: 0.053484
Content-Length: 2773
200 OK
```


```json
{
  "id": 22,
  "number": "RA380620433",
  "state": "authorized",
  "order_id": 711,
  "memo": "Items were broken",
  "created_at": "2019-08-19T20:05:20.924Z",
  "updated_at": "2019-08-19T20:05:20.924Z",
  "reason": {
    "id": 64,
    "name": "Defect #3",
    "active": true,
    "mutable": true,
    "created_at": "2019-08-19T20:05:20.921Z",
    "updated_at": "2019-08-19T20:05:20.921Z",
    "mirakl_code": null
  },
  "order": {
    "id": 711,
    "number": "R580716201",
    "item_total": "10.0",
    "total": "110.0",
    "state": "complete",
    "adjustment_total": "0.0",
    "user_id": 793,
    "completed_at": "2019-08-19T20:05:20.849Z",
    "bill_address_id": 1435,
    "ship_address_id": 1436,
    "payment_total": "110.0",
    "shipment_state": "shipped",
    "payment_state": "paid",
    "email": "email27@example.com",
    "special_instructions": null,
    "created_at": "2019-08-19T20:05:20.802Z",
    "updated_at": "2019-08-19T20:05:20.909Z",
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
    "guest_token": "zUjtGZPsZZlbYxbHLXp0gg",
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
    "country_id": 606,
    "country_iso": "US",
    "state_id": 595,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 606,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 595,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 606
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
    "country_id": 606,
    "country_iso": "US",
    "state_id": 595,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 606,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 595,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 606
    }
  },
  "return_items": [
    {
      "name": "Product #27 - 4794",
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
        "id": 534,
        "name": "Credit Card"
      },
      "source": {
        "id": 225,
        "month": "12",
        "year": "2020",
        "cc_type": null,
        "last_digits": "1111",
        "name": "Spree Commerce",
        "gateway_customer_profile_id": "BGS-300054",
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
Authorization: Bearer 46bf01f2610e4bba84273bb4601dfa9c60b22eea458067df
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
ETag: W/&quot;47570ce5b2b79e9c19c7c731440e34a0&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 40d13a75-f92b-465b-9921-b02db1b934f4
X-Runtime: 0.012236
Content-Length: 164
200 OK
```


```json
{
  "return_authorizations": [
    {
      "number": "RA885423325",
      "created_at": "2019-08-19T20:05:21.751Z",
      "return_amount": "10.0",
      "order_number": "R537315182",
      "state": "authorized"
    }
  ]
}
```



## returns a 200


### Request

#### Endpoint

```plaintext
GET /api/returns/RA136061316
Authorization: Bearer fd276e9471220ffbfc2514bc762bc5e9ff2900deb216793e
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
ETag: W/&quot;9b12a08d9dd7219e8434b73e8de92837&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: f3ebb335-8f09-4b14-8f99-7a8e32e81041
X-Runtime: 0.063220
Content-Length: 2696
200 OK
```


```json
{
  "id": 21,
  "number": "RA136061316",
  "state": "authorized",
  "order_id": 710,
  "memo": "Items were broken",
  "created_at": "2019-08-19T20:05:20.431Z",
  "updated_at": "2019-08-19T20:05:20.431Z",
  "reason": {
    "id": 62,
    "name": "Defect #1",
    "active": true,
    "mutable": true,
    "created_at": "2019-08-19T20:05:20.423Z",
    "updated_at": "2019-08-19T20:05:20.423Z",
    "mirakl_code": null
  },
  "order": {
    "id": 710,
    "number": "R851897714",
    "item_total": "10.0",
    "total": "110.0",
    "state": "complete",
    "adjustment_total": "0.0",
    "user_id": 792,
    "completed_at": "2019-08-19T20:05:20.319Z",
    "bill_address_id": 1433,
    "ship_address_id": 1434,
    "payment_total": "110.0",
    "shipment_state": "shipped",
    "payment_state": "paid",
    "email": "email26@example.com",
    "special_instructions": null,
    "created_at": "2019-08-19T20:05:20.251Z",
    "updated_at": "2019-08-19T20:05:20.376Z",
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
    "guest_token": "fxlNkduN7Fmc1ccpSc3kwQ",
    "canceled_at": null,
    "canceler_id": null,
    "store_id": 749,
    "approver_name": null,
    "frontend_viewable": true
  },
  "ship_address": {
    "id": 1434,
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
    "country_id": 605,
    "country_iso": "US",
    "state_id": 594,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 605,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 594,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 605
    }
  },
  "bill_address": {
    "id": 1433,
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
    "country_id": 605,
    "country_iso": "US",
    "state_id": 594,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 605,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 594,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 605
    }
  },
  "return_items": [
    {
      "name": "Product #26 - 9179",
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
        "id": 532,
        "name": "Credit Card"
      },
      "source": {
        "id": 224,
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
GET /api/returns/RA507838415
Authorization: Bearer 49ee62a0946a6a95c1cb4a479a4b573dbd8cbc8d1f535806
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
X-Request-Id: b964c47f-7761-4dd4-b02e-43b7327b9cb0
X-Runtime: 0.006031
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
Authorization: Bearer c7f45c2d898da52ca4cc00b9c8a59a059d45d1bc4c9f6cfa
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
ETag: W/&quot;dc7fd6de829b657c44c7cc8733858e5c&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 11b10c2e-c4f1-466f-bab5-f469063bb61b
X-Runtime: 0.036225
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
      "created_at": "2019-08-19T20:05:07.455Z"
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
Authorization: Bearer 4a7fdf7a7f87e61a9c93fc28d76fad9954cefd2dc2d73464
ETag: W/&quot;69756275a23622d3a311ad3c84ae4a7c&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: cd92de22-465a-44f4-b148-171a5856767d
X-Runtime: 0.005051
Content-Length: 553
200 OK
```


```json
{
  "id": 788,
  "email": "email22@example.com",
  "persistence_token": null,
  "perishable_token": null,
  "last_request_at": null,
  "login": "email22@example.com",
  "ship_address_id": null,
  "bill_address_id": null,
  "created_at": "2019-08-19T20:05:19.954Z",
  "updated_at": "2019-08-19T20:05:19.956Z",
  "spree_api_key": "4a7fdf7a7f87e61a9c93fc28d76fad9954cefd2dc2d73464",
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
Authorization: Bearer 8b53441119a86ae1f778943e32faabf4c2f15dc055f90bd6
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
Authorization: Bearer 8b53441119a86ae1f778943e32faabf4c2f15dc055f90bd6
ETag: W/&quot;3527216879fbac85a89dd68c82528d91&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: c6d8c7fc-59fa-490c-a459-eaffe62b7502
X-Runtime: 0.019335
Content-Length: 1309
200 OK
```


```json
{
  "email": "email21@example.com",
  "first_name": null,
  "last_name": null,
  "id": 787,
  "subscribed": null,
  "addresses": [
    {
      "id": 1432,
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
      "country_id": 604,
      "country_iso": "US",
      "state_id": 593,
      "state_name": null,
      "state_text": "AL",
      "country_name": "United States",
      "default": true
    },
    {
      "id": 1431,
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
      "country_id": 604,
      "country_iso": "US",
      "state_id": 593,
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
      "created_at": "2019-08-19T20:05:19.904Z",
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
      "created_at": "2019-08-19T20:05:19.917Z",
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
      "created_at": "2019-08-19T20:05:19.928Z",
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
Authorization: Bearer 728708d6ef1b00dda6fd03026f4aa1cec70dd5a3d9dec0cc
ETag: W/&quot;8e267b12a3a2c54689195607561baa7d&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: e95800d9-e2f2-4aff-93ce-c766ca57c88f
X-Runtime: 0.028523
Content-Length: 157
201 Created
```


```json
{
  "id": 786,
  "email": "test@example.com",
  "created_at": "2019-08-19T20:05:19.821Z",
  "updated_at": "2019-08-19T20:05:19.823Z",
  "bill_address": null,
  "ship_address": null
}
```



# Variant



## Fetching a variant


### Request

#### Endpoint

```plaintext
GET /api/variants/1567
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
ETag: W/&quot;3e9e6ee44ca085cf2b757a925b50bb02&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: c8792643-3fc0-43fa-b6a7-c91d36338174
X-Runtime: 0.087182
Content-Length: 1460
200 OK
```


```json
{
  "id": 1567,
  "name": "Product #8 - 7347",
  "sku": "SKU-8",
  "weight": "0.0",
  "height": null,
  "width": null,
  "depth": null,
  "is_master": false,
  "slug": "product-8-7347",
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
      "id": 686,
      "name": "Size-1",
      "presentation": "S",
      "option_type_name": "foo-size-1",
      "option_type_id": 623,
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
      "attachment_updated_at": "2019-08-19T20:05:08.164Z",
      "attachment_width": 489,
      "attachment_height": 490,
      "alt": null,
      "viewable_type": "Spree::Variant",
      "viewable_id": 1567,
      "mini_url": "/spree/products/13/mini/thinking-cat.jpg?1566245108",
      "small_url": "/spree/products/13/small/thinking-cat.jpg?1566245108",
      "product_url": "/spree/products/13/product/thinking-cat.jpg?1566245108",
      "large_url": "/spree/products/13/large/thinking-cat.jpg?1566245108"
    }
  ],
  "variant_properties": [

  ],
  "stock_items": [

  ],
  "prices": [
    {
      "id": 2966,
      "vendor_id": 4353,
      "price": "10.0",
      "original_price": "10.0",
      "discount_percent": 0.0,
      "total_on_hand": 0,
      "country_iso": null,
      "final_sale": false,
      "on_sale": false
    },
    {
      "id": 2967,
      "vendor_id": 4354,
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
Authorization: Bearer 4a1fc8c8ac94e07e9919147231fd6c8f74b2a6bc6b86854e
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
ETag: W/&quot;b8800bc96b3a2b50289a72ddf1cd91e0&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 04463586-c692-4d9e-ac15-a0eb4b9e3574
X-Runtime: 0.031044
Content-Length: 199
200 OK
```


```json
[
  {
    "id": 39,
    "user_id": 768,
    "payment_source_type": "SolidusPaypalBraintree::Source",
    "payment_source_id": 66,
    "default": false,
    "created_at": "2019-08-19T20:05:07.629Z",
    "updated_at": "2019-08-19T20:05:07.629Z"
  }
]
```



## Remove the payment from the user wallet


### Request

#### Endpoint

```plaintext
DELETE /api/wallet_payment_sources/40
Accept: application/json
Authorization: Bearer 2a8100c344d98f7e68347837eba417dd4db716ee36560edb
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
X-Request-Id: 72fc8fb5-a1b5-4d70-b9cf-499fa85f74cf
X-Runtime: 0.019373
204 No Content
```




## Set a wallet payment source as the default user payment method


### Request

#### Endpoint

```plaintext
POST /api/wallet_payment_sources/41/default
Accept: application/json
Authorization: Bearer 57885b395d1045452fed61b5e73cd5dadee50a3df580b3c2
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
X-Request-Id: 9c9fe4b4-5f5e-4e34-811b-3f2a403ac61d
X-Runtime: 0.008344
204 No Content
```




