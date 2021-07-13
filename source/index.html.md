---
title: Maisonette backend API documentation
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
PUT /api/orders/M852088043/addresses/13
Accept: application/json
X-Spree-Order-Token: DDpEcDQ4-tJLuRZGjnKxjg
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
ETag: W/&quot;bdde6a9e4227a6da82048aa495c065f8&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: f612f1e9-c6dc-4503-881a-8ec030b69c14
X-Runtime: 0.145382
Vary: Origin
Content-Length: 511
200 OK
```


```json
{
  "id": 14,
  "firstname": "John the Tester",
  "lastname": "Smith",
  "full_name": "John the Tester Smith",
  "address1": "A Different Road",
  "address2": "Northwest",
  "city": "Herndon",
  "zipcode": "10013",
  "phone": "555-555-0199",
  "company": "Company",
  "alternative_phone": "555-555-0199",
  "country_id": 3,
  "country_iso": "US",
  "state_id": 3,
  "state_name": null,
  "state_text": "AL",
  "country": {
    "id": 3,
    "iso_name": "UNITED STATES",
    "iso": "US",
    "iso3": "USA",
    "name": "United States",
    "numcode": 840
  },
  "state": {
    "id": 3,
    "name": "Alabama",
    "abbr": "AL",
    "country_id": 3
  }
}
```



# Braintree transactions

Please do not send billing address attributes at all if there is no billing address, otherwise you will get an order error


## Creating a PayPal express checkout transaction


### Request

#### Endpoint

```plaintext
POST /api/braintree/transactions
Accept: application/json
X-Spree-Order-Token: wAL7laY2tsuLGOwY1kkajg
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/braintree/transactions`

#### Parameters


```json
order_id=M504049876&payment_method_id=25&transaction[email]=maryellen.oga%40mckenziemcglynn.com&transaction[nonce]=fake-paypal-billing-agreement-nonce&transaction[phone]=555-555-0199&transaction[shipping_address_attributes][first_name]=John&transaction[shipping_address_attributes][last_name]=Stamm&transaction[shipping_address_attributes][address_line_1]=A+Different+Road&transaction[shipping_address_attributes][city]=Herndon&transaction[shipping_address_attributes][state_code]=AL&transaction[shipping_address_attributes][zip]=10077&transaction[shipping_address_attributes][country_code]=US&transaction[payment_type]=PayPalAccount&transaction[billing_address_attributes][first_name]=John&transaction[billing_address_attributes][last_name]=Stamm&transaction[billing_address_attributes][address_line_1]=A+Different+Road&transaction[billing_address_attributes][city]=Herndon&transaction[billing_address_attributes][state_code]=AL&transaction[billing_address_attributes][zip]=10077&transaction[billing_address_attributes][country_code]=US
```


| Name | Description |
|:-----|:------------|
| order_id *required* | The order number |
| payment_method_id *required* | The payment method id |
| transaction[device_data] *required* | The device_data |
| transaction[email] *required* | The transaction user email |
| transaction[nonce] *required* | The transaction nonce |
| transaction[phone] *required* | The transaction user phone number |
| transaction[shipping_address_attributes][first_name] *required* | The transaction shipping address first name |
| transaction[shipping_address_attributes][last_name] *required* | The transaction shipping address last name |
| transaction[shipping_address_attributes][address_line_1] *required* | The transaction shipping address line 1 |
| transaction[shipping_address_attributes][city] *required* | The transaction shipping address city |
| transaction[shipping_address_attributes][state_code] *required* | The transaction shipping address state code |
| transaction[shipping_address_attributes][zip] *required* | The transaction shipping address zip code |
| transaction[shipping_address_attributes][country_code] *required* | The transaction shipping address country code |
| transaction[payment_type] *required* | The payment type. Must be `PayPalAccount` |
| transaction[billing_address_attributes][first_name]  | The transaction billing address first name |
| transaction[billing_address_attributes][last_name]  | The transaction billing address last name |
| transaction[billing_address_attributes][address_line_1]  | The transaction billing address line 1 |
| transaction[billing_address_attributes][city]  | The transaction billing address city |
| transaction[billing_address_attributes][state_code]  | The transaction billing address state code |
| transaction[billing_address_attributes][zip]  | The transaction billing address zip code |
| transaction[billing_address_attributes][country_code]  | The transaction billing address country code |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
ETag: W/&quot;fbc92d15c2cad6d0d96a01c7b2749c56&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 6be466be-a260-41fb-b46b-3f68e8fab8c7
X-Runtime: 0.807782
Vary: Origin
Content-Length: 5273
200 OK
```


```json
{
  "id": 43,
  "number": "M504049876",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2021-07-13T07:59:22.005-04:00",
  "updated_at": "2021-07-13T07:59:22.716-04:00",
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
  "total_applicable_store_credit": 0,
  "display_total_available_store_credit": "$0.00",
  "display_store_credit_remaining_after_capture": "$0.00",
  "canceler_id": null,
  "gift_email": null,
  "gift_message": null,
  "is_gift": false,
  "use_store_credits": false,
  "first_order": false,
  "display_item_total": "$10.00",
  "total_quantity": 1,
  "display_total": "$110.00",
  "display_ship_total": "$100.00",
  "display_tax_total": "$0.00",
  "token": "wAL7laY2tsuLGOwY1kkajg",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order?order=M504049876&bzip=10077&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [
    {
      "id": 25,
      "name": "Braintree"
    }
  ],
  "bill_address": {
    "id": 80,
    "firstname": "John",
    "lastname": "Stamm",
    "full_name": "John Stamm",
    "address1": "A Different Road",
    "address2": null,
    "city": "Herndon",
    "zipcode": "10077",
    "phone": "555-555-0199",
    "company": null,
    "alternative_phone": null,
    "country_id": 62,
    "country_iso": "US",
    "state_id": 62,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 62,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 62,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 62
    }
  },
  "ship_address": {
    "id": 81,
    "firstname": "John",
    "lastname": "Stamm",
    "full_name": "John Stamm",
    "address1": "A Different Road",
    "address2": null,
    "city": "Herndon",
    "zipcode": "10077",
    "phone": "555-555-0199",
    "company": null,
    "alternative_phone": null,
    "country_id": 62,
    "country_iso": "US",
    "state_id": 62,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 62,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 62,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 62
    }
  },
  "line_items": [
    {
      "id": 40,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 195,
      "vendor_id": 380,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 195,
        "name": "Product #105 - 641",
        "sku": "SKU-194",
        "is_master": false,
        "slug": "product-105-641",
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
            "id": 90,
            "name": "Size-90",
            "presentation": "S",
            "option_type_name": "foo-size-90",
            "option_type_id": 90,
            "option_type_presentation": "Size",
            "position": 1
          }
        ],
        "images": [

        ],
        "videos": [

        ],
        "product_id": 105,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [

      ],
      "vendor_name": "Vendor #381",
      "country_iso": "US",
      "domestic_override": false,
      "adjustments": [

      ]
    }
  ],
  "payments": [
    {
      "id": 8,
      "source_type": "SolidusPaypalBraintree::Source",
      "source_id": 9,
      "amount": "110.0",
      "display_amount": "$110.00",
      "payment_method_id": 25,
      "state": "checkout",
      "avs_response": null,
      "created_at": "2021-07-13T07:59:22.281-04:00",
      "updated_at": "2021-07-13T07:59:22.281-04:00",
      "payment_method": {
        "id": 25,
        "name": "Braintree"
      },
      "source": {
        "id": 9,
        "payment_type": "PayPalAccount",
        "token": "bgx899",
        "created_at": "2021-07-13T07:59:22.278-04:00",
        "email": "jane.doe@paypal.com"
      }
    }
  ],
  "shipments": [
    {
      "id": 41,
      "tracking": null,
      "tracking_url": null,
      "number": "H66576784352",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M504049876",
      "stock_location_name": "NY Warehouse 77",
      "giftwrappable": false,
      "stock_location_id": 77,
      "giftwrap": null,
      "shipping_rates": [
        {
          "id": 38,
          "name": "UPS Ground",
          "admin_name": null,
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 30,
          "shipping_method_code": "UPS_GROUND",
          "extra_cost": "+$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 38,
        "name": "UPS Ground",
        "admin_name": null,
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 30,
        "shipping_method_code": "UPS_GROUND",
        "extra_cost": "+$100.00",
        "base_flat_rate_amount": 0.0
      },
      "shipping_methods": [
        {
          "id": 30,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 31,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 60,
              "name": "ShippingCategory #58"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 195,
          "quantity": 1,
          "states": {
            "on_hand": 1
          }
        }
      ],
      "adjustments": [

      ],
      "stock_location_address": "NY Warehouse 77, Washington, AL",
      "country_iso": "US",
      "international_shipping": false,
      "delivery_estimation": "Jul 15",
      "estimated_giftwrap_price": "5.0",
      "display_estimated_giftwrap_price": "$5.00"
    }
  ],
  "adjustments": [

  ],
  "permissions": {
    "can_update": false
  },
  "gift_card_total": "0.0",
  "applied_promotion_codes": [

  ],
  "subtotals": {
    "order_total": "110.0",
    "item_total": "10.0",
    "shipments_total": "100.0",
    "line_item_promotion_totals": [

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
X-Spree-Order-Token: eXBzLpVp3p0sQ_3Z3ZTjcg
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/braintree/transactions`

#### Parameters


```json
order_id=M261407571&payment_method_id=26&transaction[email]=maryellen.oga%40mckenziemcglynn.com&transaction[nonce]=fake-apple-pay-visa-nonce&transaction[phone]=555-555-0199&transaction[shipping_address_attributes][first_name]=John&transaction[shipping_address_attributes][last_name]=Stamm&transaction[shipping_address_attributes][address_line_1]=A+Different+Road&transaction[shipping_address_attributes][city]=Herndon&transaction[shipping_address_attributes][state_code]=AL&transaction[shipping_address_attributes][zip]=10079&transaction[shipping_address_attributes][country_code]=US&transaction[payment_type]=ApplePayCard
```


| Name | Description |
|:-----|:------------|
| order_id *required* | The order number |
| payment_method_id *required* | The payment method id |
| transaction[device_data] *required* | The device_data |
| transaction[email] *required* | The transaction user email |
| transaction[nonce] *required* | The transaction nonce |
| transaction[phone] *required* | The transaction user phone number |
| transaction[shipping_address_attributes][first_name] *required* | The transaction shipping address first name |
| transaction[shipping_address_attributes][last_name] *required* | The transaction shipping address last name |
| transaction[shipping_address_attributes][address_line_1] *required* | The transaction shipping address line 1 |
| transaction[shipping_address_attributes][city] *required* | The transaction shipping address city |
| transaction[shipping_address_attributes][state_code] *required* | The transaction shipping address state code |
| transaction[shipping_address_attributes][zip] *required* | The transaction shipping address zip code |
| transaction[shipping_address_attributes][country_code] *required* | The transaction shipping address country code |
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
ETag: W/&quot;e443d1c035a96f067c310c7046066b5e&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 7a4fc61e-15df-4225-9f3e-228522a6689f
X-Runtime: 0.760339
Vary: Origin
Content-Length: 5323
200 OK
```


```json
{
  "id": 44,
  "number": "M261407571",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2021-07-13T07:59:23.546-04:00",
  "updated_at": "2021-07-13T07:59:24.276-04:00",
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
  "total_applicable_store_credit": 0,
  "display_total_available_store_credit": "$0.00",
  "display_store_credit_remaining_after_capture": "$0.00",
  "canceler_id": null,
  "gift_email": null,
  "gift_message": null,
  "is_gift": false,
  "use_store_credits": false,
  "first_order": false,
  "display_item_total": "$10.00",
  "total_quantity": 1,
  "display_total": "$110.00",
  "display_ship_total": "$100.00",
  "display_tax_total": "$0.00",
  "token": "eXBzLpVp3p0sQ_3Z3ZTjcg",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order?order=M261407571&bzip=10079&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [
    {
      "id": 26,
      "name": "Braintree"
    }
  ],
  "bill_address": {
    "id": 84,
    "firstname": "John",
    "lastname": "Stamm",
    "full_name": "John Stamm",
    "address1": "A Different Road",
    "address2": null,
    "city": "Herndon",
    "zipcode": "10079",
    "phone": "555-555-0199",
    "company": null,
    "alternative_phone": null,
    "country_id": 63,
    "country_iso": "US",
    "state_id": 63,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 63,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 63,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 63
    }
  },
  "ship_address": {
    "id": 85,
    "firstname": "John",
    "lastname": "Stamm",
    "full_name": "John Stamm",
    "address1": "A Different Road",
    "address2": null,
    "city": "Herndon",
    "zipcode": "10079",
    "phone": "555-555-0199",
    "company": null,
    "alternative_phone": null,
    "country_id": 63,
    "country_iso": "US",
    "state_id": 63,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 63,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 63,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 63
    }
  },
  "line_items": [
    {
      "id": 41,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 197,
      "vendor_id": 385,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 197,
        "name": "Product #106 - 5772",
        "sku": "SKU-196",
        "is_master": false,
        "slug": "product-106-5772",
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
            "id": 91,
            "name": "Size-91",
            "presentation": "S",
            "option_type_name": "foo-size-91",
            "option_type_id": 91,
            "option_type_presentation": "Size",
            "position": 1
          }
        ],
        "images": [

        ],
        "videos": [

        ],
        "product_id": 106,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [

      ],
      "vendor_name": "Vendor #386",
      "country_iso": "US",
      "domestic_override": false,
      "adjustments": [

      ]
    }
  ],
  "payments": [
    {
      "id": 9,
      "source_type": "SolidusPaypalBraintree::Source",
      "source_id": 10,
      "amount": "110.0",
      "display_amount": "$110.00",
      "payment_method_id": 26,
      "state": "checkout",
      "avs_response": null,
      "created_at": "2021-07-13T07:59:23.815-04:00",
      "updated_at": "2021-07-13T07:59:23.815-04:00",
      "payment_method": {
        "id": 26,
        "name": "Braintree"
      },
      "source": {
        "id": 10,
        "payment_type": "ApplePayCard",
        "token": "cg7hsk",
        "created_at": "2021-07-13T07:59:23.813-04:00",
        "cc_type": "Apple Pay - Visa",
        "last_digits": "1881",
        "month": "12",
        "year": "2020"
      }
    }
  ],
  "shipments": [
    {
      "id": 43,
      "tracking": null,
      "tracking_url": null,
      "number": "H06505227148",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M261407571",
      "stock_location_name": "NY Warehouse 78",
      "giftwrappable": false,
      "stock_location_id": 78,
      "giftwrap": null,
      "shipping_rates": [
        {
          "id": 40,
          "name": "UPS Ground",
          "admin_name": null,
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 31,
          "shipping_method_code": "UPS_GROUND",
          "extra_cost": "+$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 40,
        "name": "UPS Ground",
        "admin_name": null,
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 31,
        "shipping_method_code": "UPS_GROUND",
        "extra_cost": "+$100.00",
        "base_flat_rate_amount": 0.0
      },
      "shipping_methods": [
        {
          "id": 31,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 32,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 61,
              "name": "ShippingCategory #59"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 197,
          "quantity": 1,
          "states": {
            "on_hand": 1
          }
        }
      ],
      "adjustments": [

      ],
      "stock_location_address": "NY Warehouse 78, Washington, AL",
      "country_iso": "US",
      "international_shipping": false,
      "delivery_estimation": "Jul 15",
      "estimated_giftwrap_price": "5.0",
      "display_estimated_giftwrap_price": "$5.00"
    }
  ],
  "adjustments": [

  ],
  "permissions": {
    "can_update": false
  },
  "gift_card_total": "0.0",
  "applied_promotion_codes": [

  ],
  "subtotals": {
    "order_total": "110.0",
    "item_total": "10.0",
    "shipments_total": "100.0",
    "line_item_promotion_totals": [

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
PUT /api/checkouts/M761896877/complete
Accept: application/json
X-Spree-Order-Token: WsrHnEi7xIo61qAC8I2FrQ
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
ETag: W/&quot;b8ddb92b040a9aef13273517f45f70e9&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 32f034bb-1b49-42fe-bce1-d8983c1d0ef3
X-Runtime: 0.771169
Vary: Origin
Content-Length: 5400
200 OK
```


```json
{
  "id": 28,
  "number": "M761896877",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "complete",
  "adjustment_total": "0.0",
  "user_id": 82,
  "created_at": "2021-07-13T07:59:04.741-04:00",
  "updated_at": "2021-07-13T07:59:05.459-04:00",
  "completed_at": "2021-07-13T07:59:05.459-04:00",
  "payment_total": "110.0",
  "shipment_state": "ready",
  "payment_state": "paid",
  "email": "email82@example.com",
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
  "gift_email": null,
  "gift_message": null,
  "is_gift": false,
  "use_store_credits": false,
  "first_order": true,
  "display_item_total": "$10.00",
  "total_quantity": 1,
  "display_total": "$110.00",
  "display_ship_total": "$100.00",
  "display_tax_total": "$0.00",
  "token": "WsrHnEi7xIo61qAC8I2FrQ",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order?order=M761896877&bzip=10045&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [
    {
      "id": 6,
      "name": "Braintree"
    },
    {
      "id": 7,
      "name": "Braintree"
    }
  ],
  "bill_address": {
    "id": 46,
    "firstname": "John",
    "lastname": "Smith",
    "full_name": "John Smith",
    "address1": "PO Box 1337",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10045",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 48,
    "country_iso": "US",
    "state_id": 48,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 48,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 48,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 48
    }
  },
  "ship_address": {
    "id": 47,
    "firstname": "John",
    "lastname": "Smith",
    "full_name": "John Smith",
    "address1": "A Different Road",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10046",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 48,
    "country_iso": "US",
    "state_id": 48,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 48,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 48,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 48
    }
  },
  "line_items": [
    {
      "id": 27,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 168,
      "vendor_id": 310,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "breadcrumb_taxons": [

      ],
      "variant": {
        "id": 168,
        "name": "Product #91 - 4197",
        "sku": "SKU-167",
        "is_master": false,
        "slug": "product-91-4197",
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
            "id": 77,
            "name": "Size-77",
            "presentation": "S",
            "option_type_name": "foo-size-77",
            "option_type_id": 77,
            "option_type_presentation": "Size",
            "position": 1
          }
        ],
        "images": [

        ],
        "videos": [

        ],
        "product_id": 91,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [

      ],
      "vendor_name": "Vendor #311",
      "country_iso": "US",
      "domestic_override": false,
      "adjustments": [

      ]
    }
  ],
  "payments": [
    {
      "id": 2,
      "source_type": "SolidusPaypalBraintree::Source",
      "source_id": 4,
      "amount": "110.0",
      "display_amount": "$110.00",
      "payment_method_id": 6,
      "state": "completed",
      "avs_response": "M",
      "created_at": "2021-07-13T07:59:04.943-04:00",
      "updated_at": "2021-07-13T07:59:05.174-04:00",
      "payment_method": {
        "id": 6,
        "name": "Braintree"
      },
      "source": {
        "id": 4,
        "payment_type": "CreditCard",
        "token": null,
        "created_at": "2021-07-13T07:59:04.941-04:00",
        "cc_type": null,
        "last_digits": null,
        "month": null,
        "year": null
      }
    }
  ],
  "shipments": [
    {
      "id": 23,
      "tracking": "U10000",
      "tracking_url": null,
      "number": "H77811444203",
      "cost": "100.0",
      "shipped_at": null,
      "state": "ready",
      "order_id": "M761896877",
      "stock_location_name": "NY Warehouse 59",
      "giftwrappable": false,
      "stock_location_id": 59,
      "giftwrap": null,
      "shipping_rates": [
        {
          "id": 21,
          "name": "UPS Ground",
          "admin_name": null,
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 18,
          "shipping_method_code": "UPS_GROUND",
          "extra_cost": "+$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 21,
        "name": "UPS Ground",
        "admin_name": null,
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 18,
        "shipping_method_code": "UPS_GROUND",
        "extra_cost": "+$100.00",
        "base_flat_rate_amount": 0.0
      },
      "shipping_methods": [
        {
          "id": 18,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 19,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 47,
              "name": "ShippingCategory #45"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 168,
          "quantity": 1,
          "states": {
            "on_hand": 1
          }
        }
      ],
      "adjustments": [

      ],
      "stock_location_address": "NY Warehouse 59, Washington, AL",
      "country_iso": "US",
      "international_shipping": false,
      "delivery_estimation": "Jul 15",
      "estimated_giftwrap_price": "5.0",
      "display_estimated_giftwrap_price": "$5.00"
    }
  ],
  "adjustments": [

  ],
  "permissions": {
    "can_update": false
  },
  "gift_card_total": "0.0",
  "applied_promotion_codes": [

  ],
  "subtotals": {
    "order_total": "110.0",
    "item_total": "10.0",
    "shipments_total": "100.0",
    "line_item_promotion_totals": [

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
PATCH /api/checkouts/M503463582
Accept: application/json
X-Spree-Order-Token: QF0cE1cb9ysJHl4gv2OOAA
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][source_attributes][device_data]=fake+device+data
```


| Name | Description |
|:-----|:------------|
| id *required* | The order number |
| order[payment_attributes] *required* | The payment attibutes |
| order[payment_attributes][payment_method_id] *required* | The payment method id |
| order[payment_attributes][source_attributes][nonce] *required* | The payment nonce |
| order[payment_attributes][source_attributes][device_data]  | The Braintree device data |
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
ETag: W/&quot;36681af74e3c83ee175106df4ab00703&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 04b84102-17d9-46d5-aeb8-92195610b44e
X-Runtime: 0.278886
Vary: Origin
Content-Length: 4843
200 OK
```


```json
{
  "id": 32,
  "number": "M503463582",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 88,
  "created_at": "2021-07-13T07:59:10.409-04:00",
  "updated_at": "2021-07-13T07:59:11.119-04:00",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "email88@example.com",
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
  "gift_email": null,
  "gift_message": null,
  "is_gift": false,
  "use_store_credits": false,
  "first_order": false,
  "display_item_total": "$10.00",
  "total_quantity": 1,
  "display_total": "$110.00",
  "display_ship_total": "$100.00",
  "display_tax_total": "$0.00",
  "token": "QF0cE1cb9ysJHl4gv2OOAA",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order?order=M503463582&bzip=10053&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [
    {
      "id": 11,
      "name": "Braintree"
    }
  ],
  "bill_address": {
    "id": 54,
    "firstname": "John",
    "lastname": "Smith",
    "full_name": "John Smith",
    "address1": "PO Box 1337",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10053",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 52,
    "country_iso": "US",
    "state_id": 52,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 52,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 52,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 52
    }
  },
  "ship_address": {
    "id": 55,
    "firstname": "John",
    "lastname": "Smith",
    "full_name": "John Smith",
    "address1": "A Different Road",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10054",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 52,
    "country_iso": "US",
    "state_id": 52,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 52,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 52,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 52
    }
  },
  "line_items": [
    {
      "id": 31,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 176,
      "vendor_id": 330,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 176,
        "name": "Product #95 - 1694",
        "sku": "SKU-175",
        "is_master": false,
        "slug": "product-95-1694",
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
            "id": 81,
            "name": "Size-81",
            "presentation": "S",
            "option_type_name": "foo-size-81",
            "option_type_id": 81,
            "option_type_presentation": "Size",
            "position": 1
          }
        ],
        "images": [

        ],
        "videos": [

        ],
        "product_id": 95,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [

      ],
      "vendor_name": "Vendor #331",
      "country_iso": "US",
      "domestic_override": false,
      "adjustments": [

      ]
    }
  ],
  "payments": [

  ],
  "shipments": [
    {
      "id": 31,
      "tracking": null,
      "tracking_url": null,
      "number": "H66235067776",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M503463582",
      "stock_location_name": "NY Warehouse 63",
      "giftwrappable": false,
      "stock_location_id": 63,
      "giftwrap": null,
      "shipping_rates": [
        {
          "id": 29,
          "name": "UPS Ground",
          "admin_name": null,
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 22,
          "shipping_method_code": "UPS_GROUND",
          "extra_cost": "+$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 29,
        "name": "UPS Ground",
        "admin_name": null,
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 22,
        "shipping_method_code": "UPS_GROUND",
        "extra_cost": "+$100.00",
        "base_flat_rate_amount": 0.0
      },
      "shipping_methods": [
        {
          "id": 22,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 23,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 51,
              "name": "ShippingCategory #49"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 176,
          "quantity": 1,
          "states": {
            "on_hand": 1
          }
        }
      ],
      "adjustments": [

      ],
      "stock_location_address": "NY Warehouse 63, Washington, AL",
      "country_iso": "US",
      "international_shipping": false,
      "delivery_estimation": "Jul 15",
      "estimated_giftwrap_price": "5.0",
      "display_estimated_giftwrap_price": "$5.00"
    }
  ],
  "adjustments": [

  ],
  "permissions": {
    "can_update": false
  },
  "gift_card_total": "0.0",
  "applied_promotion_codes": [

  ],
  "subtotals": {
    "order_total": "110.0",
    "item_total": "10.0",
    "shipments_total": "100.0",
    "line_item_promotion_totals": [

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
PATCH /api/checkouts/M820874018
Accept: application/json
X-Spree-Order-Token: 6TD-kzIFubwlSX8Fa8oung
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][source_attributes][device_data]=fake+device+data
```


| Name | Description |
|:-----|:------------|
| id *required* | The order number |
| order[payment_attributes] *required* | The payment attibutes |
| order[payment_attributes][payment_method_id] *required* | The payment method id |
| order[payment_attributes][source_attributes][nonce] *required* | The payment nonce |
| order[payment_attributes][source_attributes][device_data]  | The Braintree device data |
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
ETag: W/&quot;8d0627c7dbc4df7f3f29387d77013c0c&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 191e313c-b22d-45bf-8139-b652c1da8bdd
X-Runtime: 0.274469
Vary: Origin
Content-Length: 4843
200 OK
```


```json
{
  "id": 31,
  "number": "M820874018",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 87,
  "created_at": "2021-07-13T07:59:08.991-04:00",
  "updated_at": "2021-07-13T07:59:09.693-04:00",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "email87@example.com",
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
  "gift_email": null,
  "gift_message": null,
  "is_gift": false,
  "use_store_credits": false,
  "first_order": false,
  "display_item_total": "$10.00",
  "total_quantity": 1,
  "display_total": "$110.00",
  "display_ship_total": "$100.00",
  "display_tax_total": "$0.00",
  "token": "6TD-kzIFubwlSX8Fa8oung",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order?order=M820874018&bzip=10051&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [
    {
      "id": 10,
      "name": "Braintree"
    }
  ],
  "bill_address": {
    "id": 52,
    "firstname": "John",
    "lastname": "Smith",
    "full_name": "John Smith",
    "address1": "PO Box 1337",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10051",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 51,
    "country_iso": "US",
    "state_id": 51,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 51,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 51,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 51
    }
  },
  "ship_address": {
    "id": 53,
    "firstname": "John",
    "lastname": "Smith",
    "full_name": "John Smith",
    "address1": "A Different Road",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10052",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 51,
    "country_iso": "US",
    "state_id": 51,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 51,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 51,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 51
    }
  },
  "line_items": [
    {
      "id": 30,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 174,
      "vendor_id": 325,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 174,
        "name": "Product #94 - 1763",
        "sku": "SKU-173",
        "is_master": false,
        "slug": "product-94-1763",
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
            "id": 80,
            "name": "Size-80",
            "presentation": "S",
            "option_type_name": "foo-size-80",
            "option_type_id": 80,
            "option_type_presentation": "Size",
            "position": 1
          }
        ],
        "images": [

        ],
        "videos": [

        ],
        "product_id": 94,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [

      ],
      "vendor_name": "Vendor #326",
      "country_iso": "US",
      "domestic_override": false,
      "adjustments": [

      ]
    }
  ],
  "payments": [

  ],
  "shipments": [
    {
      "id": 29,
      "tracking": null,
      "tracking_url": null,
      "number": "H37066513050",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M820874018",
      "stock_location_name": "NY Warehouse 62",
      "giftwrappable": false,
      "stock_location_id": 62,
      "giftwrap": null,
      "shipping_rates": [
        {
          "id": 27,
          "name": "UPS Ground",
          "admin_name": null,
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 21,
          "shipping_method_code": "UPS_GROUND",
          "extra_cost": "+$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 27,
        "name": "UPS Ground",
        "admin_name": null,
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 21,
        "shipping_method_code": "UPS_GROUND",
        "extra_cost": "+$100.00",
        "base_flat_rate_amount": 0.0
      },
      "shipping_methods": [
        {
          "id": 21,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 22,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 50,
              "name": "ShippingCategory #48"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 174,
          "quantity": 1,
          "states": {
            "on_hand": 1
          }
        }
      ],
      "adjustments": [

      ],
      "stock_location_address": "NY Warehouse 62, Washington, AL",
      "country_iso": "US",
      "international_shipping": false,
      "delivery_estimation": "Jul 15",
      "estimated_giftwrap_price": "5.0",
      "display_estimated_giftwrap_price": "$5.00"
    }
  ],
  "adjustments": [

  ],
  "permissions": {
    "can_update": false
  },
  "gift_card_total": "0.0",
  "applied_promotion_codes": [

  ],
  "subtotals": {
    "order_total": "110.0",
    "item_total": "10.0",
    "shipments_total": "100.0",
    "line_item_promotion_totals": [

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
PATCH /api/checkouts/M638941748
Accept: application/json
X-Spree-Order-Token: iHpzeESJmOyiBnA8V0vqTQ
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][source_attributes][device_data]=fake+device+data
```


| Name | Description |
|:-----|:------------|
| id *required* | The order number |
| order[payment_attributes] *required* | The payment attibutes |
| order[payment_attributes][payment_method_id] *required* | The payment method id |
| order[payment_attributes][source_attributes][nonce] *required* | The payment nonce |
| order[payment_attributes][source_attributes][device_data]  | The Braintree device data |
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
ETag: W/&quot;63276c6da6ddf1fba15ad042e2ae8a93&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 178f885f-0112-41ef-9e17-ce631d19e7d7
X-Runtime: 0.329054
Vary: Origin
Content-Length: 4842
200 OK
```


```json
{
  "id": 30,
  "number": "M638941748",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 86,
  "created_at": "2021-07-13T07:59:07.580-04:00",
  "updated_at": "2021-07-13T07:59:08.252-04:00",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
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
  "order_total_after_store_credit": "110.0",
  "display_order_total_after_store_credit": "$110.00",
  "total_applicable_store_credit": 0,
  "display_total_available_store_credit": "$0.00",
  "display_store_credit_remaining_after_capture": "$0.00",
  "canceler_id": null,
  "gift_email": null,
  "gift_message": null,
  "is_gift": false,
  "use_store_credits": false,
  "first_order": false,
  "display_item_total": "$10.00",
  "total_quantity": 1,
  "display_total": "$110.00",
  "display_ship_total": "$100.00",
  "display_tax_total": "$0.00",
  "token": "iHpzeESJmOyiBnA8V0vqTQ",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order?order=M638941748&bzip=10049&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [
    {
      "id": 9,
      "name": "Braintree"
    }
  ],
  "bill_address": {
    "id": 50,
    "firstname": "John",
    "lastname": "Smith",
    "full_name": "John Smith",
    "address1": "PO Box 1337",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10049",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 50,
    "country_iso": "US",
    "state_id": 50,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 50,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 50,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 50
    }
  },
  "ship_address": {
    "id": 51,
    "firstname": "John",
    "lastname": "Smith",
    "full_name": "John Smith",
    "address1": "A Different Road",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10050",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 50,
    "country_iso": "US",
    "state_id": 50,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 50,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 50,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 50
    }
  },
  "line_items": [
    {
      "id": 29,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 172,
      "vendor_id": 320,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 172,
        "name": "Product #93 - 5170",
        "sku": "SKU-171",
        "is_master": false,
        "slug": "product-93-5170",
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
            "id": 79,
            "name": "Size-79",
            "presentation": "S",
            "option_type_name": "foo-size-79",
            "option_type_id": 79,
            "option_type_presentation": "Size",
            "position": 1
          }
        ],
        "images": [

        ],
        "videos": [

        ],
        "product_id": 93,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [

      ],
      "vendor_name": "Vendor #321",
      "country_iso": "US",
      "domestic_override": false,
      "adjustments": [

      ]
    }
  ],
  "payments": [

  ],
  "shipments": [
    {
      "id": 27,
      "tracking": null,
      "tracking_url": null,
      "number": "H08083051810",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M638941748",
      "stock_location_name": "NY Warehouse 61",
      "giftwrappable": false,
      "stock_location_id": 61,
      "giftwrap": null,
      "shipping_rates": [
        {
          "id": 25,
          "name": "UPS Ground",
          "admin_name": null,
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 20,
          "shipping_method_code": "UPS_GROUND",
          "extra_cost": "+$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 25,
        "name": "UPS Ground",
        "admin_name": null,
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 20,
        "shipping_method_code": "UPS_GROUND",
        "extra_cost": "+$100.00",
        "base_flat_rate_amount": 0.0
      },
      "shipping_methods": [
        {
          "id": 20,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 21,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 49,
              "name": "ShippingCategory #47"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 172,
          "quantity": 1,
          "states": {
            "on_hand": 1
          }
        }
      ],
      "adjustments": [

      ],
      "stock_location_address": "NY Warehouse 61, Washington, AL",
      "country_iso": "US",
      "international_shipping": false,
      "delivery_estimation": "Jul 15",
      "estimated_giftwrap_price": "5.0",
      "display_estimated_giftwrap_price": "$5.00"
    }
  ],
  "adjustments": [

  ],
  "permissions": {
    "can_update": false
  },
  "gift_card_total": "0.0",
  "applied_promotion_codes": [

  ],
  "subtotals": {
    "order_total": "110.0",
    "item_total": "10.0",
    "shipments_total": "100.0",
    "line_item_promotion_totals": [

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
PATCH /api/checkouts/M864950809
Accept: application/json
X-Spree-Order-Token: nOrVx17Fex9q1l0UoKVLUA
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][source_attributes][device_data]=fake+device+data
```


| Name | Description |
|:-----|:------------|
| id *required* | The order number |
| order[payment_attributes] *required* | The payment attibutes |
| order[payment_attributes][payment_method_id] *required* | The payment method id |
| order[payment_attributes][source_attributes][wallet_payment_source_id] *required* | The payment source id of a payment within the user’s payments wallet |
| order[payment_attributes][source_attributes][device_data]  | The Braintree device data |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
ETag: W/&quot;05329b5829a8d613d81016c5d33a7705&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 3f1bff11-b586-4e70-ae86-7e17dec1d11f
X-Runtime: 0.260709
Vary: Origin
Content-Length: 4842
200 OK
```


```json
{
  "id": 29,
  "number": "M864950809",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 84,
  "created_at": "2021-07-13T07:59:06.293-04:00",
  "updated_at": "2021-07-13T07:59:06.942-04:00",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "email84@example.com",
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
  "gift_email": null,
  "gift_message": null,
  "is_gift": false,
  "use_store_credits": false,
  "first_order": false,
  "display_item_total": "$10.00",
  "total_quantity": 1,
  "display_total": "$110.00",
  "display_ship_total": "$100.00",
  "display_tax_total": "$0.00",
  "token": "nOrVx17Fex9q1l0UoKVLUA",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order?order=M864950809&bzip=10047&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [
    {
      "id": 8,
      "name": "Braintree"
    }
  ],
  "bill_address": {
    "id": 48,
    "firstname": "John",
    "lastname": "Smith",
    "full_name": "John Smith",
    "address1": "PO Box 1337",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10047",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 49,
    "country_iso": "US",
    "state_id": 49,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 49,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 49,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 49
    }
  },
  "ship_address": {
    "id": 49,
    "firstname": "John",
    "lastname": "Smith",
    "full_name": "John Smith",
    "address1": "A Different Road",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10048",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 49,
    "country_iso": "US",
    "state_id": 49,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 49,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 49,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 49
    }
  },
  "line_items": [
    {
      "id": 28,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 170,
      "vendor_id": 315,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 170,
        "name": "Product #92 - 7006",
        "sku": "SKU-169",
        "is_master": false,
        "slug": "product-92-7006",
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
            "id": 78,
            "name": "Size-78",
            "presentation": "S",
            "option_type_name": "foo-size-78",
            "option_type_id": 78,
            "option_type_presentation": "Size",
            "position": 1
          }
        ],
        "images": [

        ],
        "videos": [

        ],
        "product_id": 92,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [

      ],
      "vendor_name": "Vendor #316",
      "country_iso": "US",
      "domestic_override": false,
      "adjustments": [

      ]
    }
  ],
  "payments": [

  ],
  "shipments": [
    {
      "id": 25,
      "tracking": null,
      "tracking_url": null,
      "number": "H07124046138",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M864950809",
      "stock_location_name": "NY Warehouse 60",
      "giftwrappable": false,
      "stock_location_id": 60,
      "giftwrap": null,
      "shipping_rates": [
        {
          "id": 23,
          "name": "UPS Ground",
          "admin_name": null,
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 19,
          "shipping_method_code": "UPS_GROUND",
          "extra_cost": "+$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 23,
        "name": "UPS Ground",
        "admin_name": null,
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 19,
        "shipping_method_code": "UPS_GROUND",
        "extra_cost": "+$100.00",
        "base_flat_rate_amount": 0.0
      },
      "shipping_methods": [
        {
          "id": 19,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 20,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 48,
              "name": "ShippingCategory #46"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 170,
          "quantity": 1,
          "states": {
            "on_hand": 1
          }
        }
      ],
      "adjustments": [

      ],
      "stock_location_address": "NY Warehouse 60, Washington, AL",
      "country_iso": "US",
      "international_shipping": false,
      "delivery_estimation": "Jul 15",
      "estimated_giftwrap_price": "5.0",
      "display_estimated_giftwrap_price": "$5.00"
    }
  ],
  "adjustments": [

  ],
  "permissions": {
    "can_update": false
  },
  "gift_card_total": "0.0",
  "applied_promotion_codes": [

  ],
  "subtotals": {
    "order_total": "110.0",
    "item_total": "10.0",
    "shipments_total": "100.0",
    "line_item_promotion_totals": [

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
PUT /api/checkouts/M854550423
Accept: application/json
X-Spree-Order-Token: skgvHwvYpDM7Edpz_uLqgQ
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PUT /api/checkouts/:id`

#### Parameters


```json
order[ship_address_attributes][id]&order[ship_address_attributes][firstname]=John&order[ship_address_attributes][lastname]=Smith&order[ship_address_attributes][address1]=10+Lovely+Street&order[ship_address_attributes][address2]=Northwest&order[ship_address_attributes][city]=Herndon&order[ship_address_attributes][zipcode]=10044&order[ship_address_attributes][phone]=555-555-0199&order[ship_address_attributes][state_name]&order[ship_address_attributes][alternative_phone]=555-555-0199&order[ship_address_attributes][company]=Company&order[ship_address_attributes][state_id]=47&order[ship_address_attributes][country_id]=47&order[ship_address_attributes][created_at]&order[ship_address_attributes][updated_at]&order[ship_address_attributes][easypost_address_id]&order[use_billing]=true&hold_state=true
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
ETag: W/&quot;baa03c2c7922e7e9b09a4a44aad25de9&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: b372f904-1b0f-4888-81b2-e8108459a828
X-Runtime: 0.280199
Vary: Origin
Content-Length: 4821
200 OK
```


```json
{
  "id": 27,
  "number": "M854550423",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "cart",
  "adjustment_total": "0.0",
  "user_id": 81,
  "created_at": "2021-07-13T07:59:03.786-04:00",
  "updated_at": "2021-07-13T07:59:04.020-04:00",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "email81@example.com",
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
  "gift_email": null,
  "gift_message": null,
  "is_gift": false,
  "use_store_credits": false,
  "first_order": false,
  "display_item_total": "$10.00",
  "total_quantity": 1,
  "display_total": "$110.00",
  "display_ship_total": "$100.00",
  "display_tax_total": "$0.00",
  "token": "skgvHwvYpDM7Edpz_uLqgQ",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order?order=M854550423&bzip=10044&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [

  ],
  "bill_address": {
    "id": 45,
    "firstname": "John",
    "lastname": "Smith",
    "full_name": "John Smith",
    "address1": "10 Lovely Street",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10044",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 47,
    "country_iso": "US",
    "state_id": 47,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 47,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 47,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 47
    }
  },
  "ship_address": {
    "id": 45,
    "firstname": "John",
    "lastname": "Smith",
    "full_name": "John Smith",
    "address1": "10 Lovely Street",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10044",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 47,
    "country_iso": "US",
    "state_id": 47,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 47,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 47,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 47
    }
  },
  "line_items": [
    {
      "id": 26,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 166,
      "vendor_id": 305,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 166,
        "name": "Product #90 - 2971",
        "sku": "SKU-165",
        "is_master": false,
        "slug": "product-90-2971",
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
            "id": 76,
            "name": "Size-76",
            "presentation": "S",
            "option_type_name": "foo-size-76",
            "option_type_id": 76,
            "option_type_presentation": "Size",
            "position": 1
          }
        ],
        "images": [

        ],
        "videos": [

        ],
        "product_id": 90,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [

      ],
      "vendor_name": "Vendor #306",
      "country_iso": "US",
      "domestic_override": false,
      "adjustments": [

      ]
    }
  ],
  "payments": [

  ],
  "shipments": [
    {
      "id": 22,
      "tracking": "U10000",
      "tracking_url": null,
      "number": "H32835427557",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M854550423",
      "stock_location_name": "NY Warehouse 58",
      "giftwrappable": false,
      "stock_location_id": 58,
      "giftwrap": null,
      "shipping_rates": [
        {
          "id": 20,
          "name": "UPS Ground",
          "admin_name": null,
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 17,
          "shipping_method_code": "UPS_GROUND",
          "extra_cost": "+$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 20,
        "name": "UPS Ground",
        "admin_name": null,
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 17,
        "shipping_method_code": "UPS_GROUND",
        "extra_cost": "+$100.00",
        "base_flat_rate_amount": 0.0
      },
      "shipping_methods": [
        {
          "id": 17,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 18,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 46,
              "name": "ShippingCategory #44"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 166,
          "quantity": 1,
          "states": {
            "on_hand": 1
          }
        }
      ],
      "adjustments": [

      ],
      "stock_location_address": "NY Warehouse 58, Washington, AL",
      "country_iso": "US",
      "international_shipping": false,
      "delivery_estimation": "Jul 15",
      "estimated_giftwrap_price": "5.0",
      "display_estimated_giftwrap_price": "$5.00"
    }
  ],
  "adjustments": [

  ],
  "permissions": {
    "can_update": false
  },
  "gift_card_total": "0.0",
  "applied_promotion_codes": [

  ],
  "subtotals": {
    "order_total": "110.0",
    "item_total": "10.0",
    "shipments_total": "100.0",
    "line_item_promotion_totals": [

    ],
    "tax_adjustments": [

    ],
    "miscellaneous_adjustments": [

    ],
    "giftwrap_amount": 0
  }
}
```



# Giftwrap

Create giftwrap related to shipment

## Create Giftwrap


### Request

#### Endpoint

```plaintext
POST /api/shipments/H41158377202/giftwrap
Accept: application/json
X-Spree-Order-Token: TfG9B0hJer64Mkjjry16Xw
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/shipments/:shipment_number/giftwrap`

#### Parameters


```json
order_number=M633737504
```


| Name | Description |
|:-----|:------------|
| order_number *required* |  order number |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
ETag: W/&quot;8899de3b4666d0585858e447929a27f9&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: f8691d81-69aa-43be-b23e-2c3884b564a3
X-Runtime: 0.127106
Vary: Origin
Content-Length: 74
201 Created
```


```json
{
  "id": 1,
  "giftwrap_cost": 2.5,
  "giftwrap_price": 4.0,
  "giftwrap_money": "$4.00"
}
```



## Delete Giftwrap


### Request

#### Endpoint

```plaintext
DELETE /api/shipments/H23534085320/giftwrap
Accept: application/json
X-Spree-Order-Token: bMuUEz53Db8t6TB7os0vaA
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`DELETE /api/shipments/:shipment_number/giftwrap`

#### Parameters


```json
order_number=M789988051
```


| Name | Description |
|:-----|:------------|
| order_number *required* |  order number |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Cache-Control: no-cache
X-Request-Id: b5d4b4a2-4fdd-4706-9c1f-9b5d755ae45c
X-Runtime: 0.062514
Vary: Origin
204 No Content
```




# LineItem

Representation of a single cart item for a specific variant with price of vendor

## Creating a line item


### Request

#### Endpoint

```plaintext
POST /api/orders/M274647192/line_items
Accept: application/json
Authorizat IO N: Bearer e335306fde218083d48e7ec5265102fcb66b48009fd0653e
X-Spree-Order-Token: n9uulyXNnqeCmiUQbPWi6w
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/:order_number/line_items`

#### Parameters


```json
line_item[variant_id]=37&line_item[options][vendor_id]=55&line_item[quantity]=1
```


| Name | Description |
|:-----|:------------|
| line_item[variant_id] *required* | Line item variant |
| line_item[options]  | Hash containing the vendor_id. It's used to set the price based on vendor |
| line_item[quantity]  | Line item quantity |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
ETag: W/&quot;fe5eafaf6dbf3bf51f48a5961adfe52f&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 7e3d5fe9-7625-422c-9e0e-1ea3857f6f8a
X-Runtime: 0.386331
Vary: Origin
Content-Length: 938
201 Created
```


```json
{
  "id": 6,
  "quantity": 1,
  "price": "19.99",
  "variant_id": 37,
  "vendor_id": 55,
  "single_display_amount": "$19.99",
  "display_amount": "$19.99",
  "total": "19.99",
  "on_sale": false,
  "final_sale": false,
  "backordered": null,
  "promotionable": true,
  "variant": {
    "id": 37,
    "name": "Product #19 - 8054",
    "sku": "SKU-36",
    "is_master": false,
    "slug": "product-19-8054",
    "description": "As seen on TV!",
    "track_inventory": true,
    "cost_price": "17.0",
    "price": "19.99",
    "display_price": "$19.99",
    "options_text": "Size: S",
    "in_stock": false,
    "is_backorderable": true,
    "total_on_hand": 0,
    "is_destroyed": false,
    "option_values": [
      {
        "id": 18,
        "name": "Size-18",
        "presentation": "S",
        "option_type_name": "foo-size-18",
        "option_type_id": 18,
        "option_type_presentation": "Size",
        "position": 1
      }
    ],
    "images": [

    ],
    "videos": [

    ],
    "product_id": 19,
    "lead_time": 2,
    "brand": null,
    "brand_slug": null,
    "brand_description": null
  },
  "monogram": null,
  "gift_cards": [

  ],
  "vendor_name": "Vendor #56",
  "country_iso": null,
  "domestic_override": null,
  "adjustments": [

  ]
}
```



## Creating a line item gift card


### Request

#### Endpoint

```plaintext
POST /api/orders/M569837035/line_items
Accept: application/json
Authorizat IO N: Bearer 31a50b24466713a8195d6fd4347d94421cb6bc1cacb7498c
X-Spree-Order-Token: 3uVXFhNOk9y_rsj4_14mBA
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/:order_number/line_items`

#### Parameters


```json
line_item[variant_id]=31&line_item[options][vendor_id]=46&line_item[options][gift_card_details][recipient_name]=Recipient+John&line_item[options][gift_card_details][recipient_email]=recipient%40email.com&line_item[options][gift_card_details][purchaser_name]=Purchaser+Bob&line_item[options][gift_card_details][gift_message]=Surprise&line_item[options][gift_card_details][send_email_at]=2021-07-13+07%3A58%3A18+-0400&line_item[quantity]=1
```


| Name | Description |
|:-----|:------------|
| line_item[variant_id] *required* | Line item variant |
| line_item[options]  | Hash containing the vendor_id and gift card details.
                          It's used to set the price based on vendor |
| line_item[quantity]  | Line item quantity |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
ETag: W/&quot;19072d2c628716cfceae139c369ca13f&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 4dca0156-80f8-4386-a898-672a301a8353
X-Runtime: 0.450370
Vary: Origin
Content-Length: 1074
201 Created
```


```json
{
  "id": 4,
  "quantity": 1,
  "price": "19.99",
  "variant_id": 31,
  "vendor_id": 46,
  "single_display_amount": "$19.99",
  "display_amount": "$19.99",
  "total": "19.99",
  "on_sale": false,
  "final_sale": false,
  "backordered": null,
  "promotionable": true,
  "variant": {
    "id": 31,
    "name": "Product #15 - 4793",
    "sku": "SKU-31",
    "is_master": false,
    "slug": "product-15-4793",
    "description": "As seen on TV!",
    "track_inventory": true,
    "cost_price": "17.0",
    "price": "19.99",
    "display_price": "$19.99",
    "options_text": "Size: S",
    "in_stock": false,
    "is_backorderable": true,
    "total_on_hand": 0,
    "is_destroyed": false,
    "option_values": [
      {
        "id": 15,
        "name": "Size-15",
        "presentation": "S",
        "option_type_name": "foo-size-15",
        "option_type_id": 15,
        "option_type_presentation": "Size",
        "position": 1
      }
    ],
    "images": [

    ],
    "videos": [

    ],
    "product_id": 15,
    "lead_time": 2,
    "brand": null,
    "brand_slug": null,
    "brand_description": null
  },
  "monogram": null,
  "gift_cards": [
    {
      "recipient_name": null,
      "recipient_email": null,
      "purchaser_name": null,
      "gift_message": null,
      "send_email_at": "2021-07-13T00:00:00.000-04:00"
    }
  ],
  "vendor_name": "Vendor #47",
  "country_iso": null,
  "domestic_override": null,
  "adjustments": [

  ]
}
```



## Deleting a line item


### Request

#### Endpoint

```plaintext
DELETE /api/orders/M839624567/line_items/2
Accept: application/json
Authorizat IO N: Bearer f11477b0775b19e0be383f49716c9ccd430910cb8308abff
X-Spree-Order-Token: vIqc8oPZ7wNg3-JIodikhQ
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
X-Request-Id: 88042b29-acd5-4f91-ae67-06e24f5d3171
X-Runtime: 0.248876
Vary: Origin
204 No Content
```




## Updating a line item


### Request

#### Endpoint

```plaintext
PUT /api/orders/M037851309/line_items/7
Accept: application/json
Authorizat IO N: Bearer 1ffb564f4d84f7f295aa7b5f417f00c218f08b84548a7114
X-Spree-Order-Token: sCi2g7FdkbDT6s0uIjJJYQ
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
ETag: W/&quot;6afaee64fb2c637f68414b0f61543605&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 2acad4f5-c5fc-4875-bd42-72718e576d0c
X-Runtime: 0.252309
Vary: Origin
Content-Length: 934
200 OK
```


```json
{
  "id": 7,
  "quantity": 2,
  "price": "10.0",
  "variant_id": 39,
  "vendor_id": 60,
  "single_display_amount": "$10.00",
  "display_amount": "$20.00",
  "total": "20.0",
  "on_sale": false,
  "final_sale": false,
  "backordered": null,
  "promotionable": true,
  "variant": {
    "id": 39,
    "name": "Product #20 - 170",
    "sku": "SKU-38",
    "is_master": false,
    "slug": "product-20-170",
    "description": "As seen on TV!",
    "track_inventory": true,
    "cost_price": "17.0",
    "price": "10.0",
    "display_price": "$10.00",
    "options_text": "Size: S",
    "in_stock": true,
    "is_backorderable": true,
    "total_on_hand": 10,
    "is_destroyed": false,
    "option_values": [
      {
        "id": 19,
        "name": "Size-19",
        "presentation": "S",
        "option_type_name": "foo-size-19",
        "option_type_id": 19,
        "option_type_presentation": "Size",
        "position": 1
      }
    ],
    "images": [

    ],
    "videos": [

    ],
    "product_id": 20,
    "lead_time": 2,
    "brand": null,
    "brand_slug": null,
    "brand_description": null
  },
  "monogram": null,
  "gift_cards": [

  ],
  "vendor_name": "Vendor #61",
  "country_iso": "US",
  "domestic_override": false,
  "adjustments": [

  ]
}
```



# Minis

Get a logged in users minis

## Create a mini


### Request

#### Endpoint

```plaintext
POST /api/minis
Accept: application/json
Authorizat IO N: Bearer 093e0678d1f8a4fcbfcb07178b4ab9f36e9c30f5c365d2a6
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/minis`

#### Parameters


```json
mini[name]=Winny&mini[user_id]=123&mini[birth_year]=2019&mini[birth_month]=1&mini[birth_day]=1
```


| Name | Description |
|:-----|:------------|
| mini[name] *required* | Mini name |
| mini[user_id]  | User ID must match that of the current_api_user unless the current_api_user is an admin.                 User ID will be inferred from the current_api_user unless explicitly provided |
| mini[birth_year] *required* | Mini birth year |
| mini[birth_month] *required* | Mini birth month |
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
ETag: W/&quot;d7f0ebd098c08e69c74e56be0ddae9d2&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: ac2ff078-d22a-40ac-b903-bd45534fc261
X-Runtime: 0.056884
Vary: Origin
Content-Length: 163
201 Created
```


```json
{
  "id": 6,
  "user_id": 123,
  "name": "Winny",
  "birth_year": 2019,
  "birth_month": 1,
  "birth_day": 1,
  "gender_boy": true,
  "gender_girl": true,
  "gender_taxons": [

  ],
  "age_range_taxons": [

  ]
}
```



## Delete a mini


### Request

#### Endpoint

```plaintext
DELETE /api/minis/9
Accept: application/json
Authorizat IO N: Bearer d591ca7a0d5cc647855eeae196e76f20987154cfd37dd9e1
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
X-Request-Id: 7514815e-e090-47c8-af1b-6b5c25b67bae
X-Runtime: 0.041298
Vary: Origin
204 No Content
```




## Get a single mini


### Request

#### Endpoint

```plaintext
GET /api/minis/7
Accept: application/json
Authorizat IO N: Bearer 0af09b2f8086b23893a02203a09af7109191e586629e788c
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
ETag: W/&quot;e3a59dbd09f566b2cbe95f80587a8823&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: d02d1314-0831-4295-bb9a-a7e583219e7f
X-Runtime: 0.051886
Vary: Origin
Content-Length: 163
200 OK
```


```json
{
  "id": 7,
  "user_id": 124,
  "name": "Mini",
  "birth_year": 2021,
  "birth_month": 7,
  "birth_day": 12,
  "gender_boy": true,
  "gender_girl": true,
  "gender_taxons": [

  ],
  "age_range_taxons": [

  ]
}
```



## Get all minis


### Request

#### Endpoint

```plaintext
GET /api/minis
Accept: application/json
Authorizat IO N: Bearer 0ad241799d9bcd00696eb8e2b70fa378fe667ed13b6c6d35
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
ETag: W/&quot;445b17d76e971734731bcf0d42b53c8d&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 97e4ebf8-2a25-4c45-a9b5-ca8fc98ef280
X-Runtime: 0.093610
Vary: Origin
Content-Length: 1730
200 OK
```


```json
{
  "minis": [
    {
      "id": 19,
      "user_id": 136,
      "name": "Mini",
      "birth_year": 2021,
      "birth_month": 7,
      "birth_day": 12,
      "gender_boy": true,
      "gender_girl": true,
      "gender_taxons": [

      ],
      "age_range_taxons": [

      ]
    },
    {
      "id": 18,
      "user_id": 135,
      "name": "Mini",
      "birth_year": 2021,
      "birth_month": 7,
      "birth_day": 12,
      "gender_boy": true,
      "gender_girl": true,
      "gender_taxons": [

      ],
      "age_range_taxons": [

      ]
    },
    {
      "id": 17,
      "user_id": 134,
      "name": "Mini",
      "birth_year": 2021,
      "birth_month": 7,
      "birth_day": 12,
      "gender_boy": true,
      "gender_girl": true,
      "gender_taxons": [

      ],
      "age_range_taxons": [

      ]
    },
    {
      "id": 16,
      "user_id": 133,
      "name": "Mini",
      "birth_year": 2021,
      "birth_month": 7,
      "birth_day": 12,
      "gender_boy": true,
      "gender_girl": true,
      "gender_taxons": [

      ],
      "age_range_taxons": [

      ]
    },
    {
      "id": 15,
      "user_id": 132,
      "name": "Mini",
      "birth_year": 2021,
      "birth_month": 7,
      "birth_day": 12,
      "gender_boy": true,
      "gender_girl": true,
      "gender_taxons": [

      ],
      "age_range_taxons": [

      ]
    },
    {
      "id": 14,
      "user_id": 131,
      "name": "Mini",
      "birth_year": 2021,
      "birth_month": 7,
      "birth_day": 12,
      "gender_boy": true,
      "gender_girl": true,
      "gender_taxons": [

      ],
      "age_range_taxons": [

      ]
    },
    {
      "id": 13,
      "user_id": 130,
      "name": "Mini",
      "birth_year": 2021,
      "birth_month": 7,
      "birth_day": 12,
      "gender_boy": true,
      "gender_girl": true,
      "gender_taxons": [

      ],
      "age_range_taxons": [

      ]
    },
    {
      "id": 12,
      "user_id": 129,
      "name": "Mini",
      "birth_year": 2021,
      "birth_month": 7,
      "birth_day": 12,
      "gender_boy": true,
      "gender_girl": true,
      "gender_taxons": [

      ],
      "age_range_taxons": [

      ]
    },
    {
      "id": 11,
      "user_id": 128,
      "name": "Mini",
      "birth_year": 2021,
      "birth_month": 7,
      "birth_day": 12,
      "gender_boy": true,
      "gender_girl": true,
      "gender_taxons": [

      ],
      "age_range_taxons": [

      ]
    },
    {
      "id": 10,
      "user_id": 127,
      "name": "Mini",
      "birth_year": 2021,
      "birth_month": 7,
      "birth_day": 12,
      "gender_boy": true,
      "gender_girl": true,
      "gender_taxons": [

      ],
      "age_range_taxons": [

      ]
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
Authorizat IO N: Bearer 99e2ab103dcdd874099d85e2ff0ba3842340126bc40474c5
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
ETag: W/&quot;20811c93dc5fc169c4c09dd436fdb544&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 15029b7c-27cf-46ae-a80c-ffaf541ab72a
X-Runtime: 0.070352
Vary: Origin
Content-Length: 406
200 OK
```


```json
{
  "minis": [
    {
      "id": 5,
      "user_id": 122,
      "name": "Mini",
      "birth_year": 2021,
      "birth_month": 7,
      "birth_day": 12,
      "gender_boy": true,
      "gender_girl": true,
      "gender_taxons": [

      ],
      "age_range_taxons": [

      ]
    },
    {
      "id": 4,
      "user_id": 122,
      "name": "Mini",
      "birth_year": 2021,
      "birth_month": 7,
      "birth_day": 12,
      "gender_boy": true,
      "gender_girl": true,
      "gender_taxons": [

      ],
      "age_range_taxons": [

      ]
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
PATCH /api/minis/8
Accept: application/json
Authorizat IO N: Bearer 93842703e4079e2e47fa4112163c615a335a5812c67c8481
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
ETag: W/&quot;01a509d5d790386920c0e7aab34add96&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: cfd01b1a-e2b8-44ce-96b1-a9673da2bcf0
X-Runtime: 0.056585
Vary: Origin
Content-Length: 164
200 OK
```


```json
{
  "id": 8,
  "user_id": 125,
  "name": "Marge",
  "birth_year": 2021,
  "birth_month": 7,
  "birth_day": 12,
  "gender_boy": true,
  "gender_girl": true,
  "gender_taxons": [

  ],
  "age_range_taxons": [

  ]
}
```



# OMS Appeasement

Create an appeasement for braintree

## Create an appeasement with 1 refund on braintree/store_credit/gift_card


### Request

#### Endpoint

```plaintext
POST /api/oms/appeasements
Accept: application/json
Authorizat IO N: Bearer f8fee3b8e199960f1c7762e24e396fadc101dd9ddb712458
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/oms/appeasements`

#### Parameters


```json
appeasement[total]=30.0&appeasement[refunds][][reimbursement_method]=braintree&appeasement[refunds][][amount]=10&appeasement[refunds][][payment_number]=C3MFVXPY&appeasement[refunds][][transaction_id]=ABC123&appeasement[refunds][][reimbursement_method]=gift_card&appeasement[refunds][][gift_card_email]=admin%40example.com&appeasement[refunds][][amount]=10&appeasement[refunds][][reimbursement_method]=store_credit&appeasement[refunds][][amount]=10&appeasement%5Binfo%5D%5B%5D[order_item_summary_id]=line_item_1&appeasement%5Binfo%5D%5B%5D[label]=Never+Worked&appeasement%5Binfo%5D%5B%5D[amount]=30&appeasement%5Brefunds%5D%5B%5D[amount]=30
```


| Name | Description |
|:-----|:------------|
| appeasement[total] *required* | Total amount of the appeasement |
| appeasement[info] *required* | Array of adjustment to create on the order |
| appeasement[info][][order_item_summary_id] *required* | Reference of line item to link the adjustments |
| appeasement[info][][label] *required* | Refund adjustment label |
| appeasement[info][][amount] *required* | Adjustment amount |
| appeasement[refunds] *required* | Array of refund or credit to create on the reimbursement |
| appeasement[refunds][][reimbursement_method] *required* | It can be braintree/store_credit/gift_card |
| appeasement[refunds][][amount] *required* | Amount of the refund/credit |
| appeasement[refunds][][payment_id] *required* | Payment ID of the transaction(only for braintree) |
| appeasement[refunds][][transaction_id] *required* | Transaction id of refund(only for braintree) |
| appeasement[refunds][][gift_card_email] *required* | Gift card email(only for gift_card) |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
ETag: W/&quot;aac42df3830539f3652e152bcc32435f&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: d4c8712d-ff21-4f8f-be1b-174cd01de52e
X-Runtime: 0.410403
Vary: Origin
Content-Length: 270
201 Created
```


```json
{
  "appeasement": {
    "id": 1,
    "number": "RI325518382",
    "reimbursement_status": "reimbursed",
    "customer_return_id": null,
    "order_id": 16,
    "total": "30.0",
    "created_at": "2021-07-13T07:58:42.926-04:00",
    "updated_at": "2021-07-13T07:58:43.083-04:00",
    "mirakl_order_line_reimbursement_id": null
  }
}
```



# OMS Cancellation

Create an cancellation for braintree

## Create an cancel with 1 refund on braintree/store_credit/gift_card


### Request

#### Endpoint

```plaintext
POST /api/oms/cancellations
Accept: application/json
Authorizat IO N: Bearer 0bb7377ea8b6444d6f93e722376c0bd19c7690af001526cc
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/oms/cancellations`

#### Parameters


```json
cancel[total]=10.0&cancel[refunds][][reimbursement_method]=braintree&cancel[refunds][][amount]=10&cancel[refunds][][payment_number]=V5DYSXYJ&cancel[refunds][][transaction_id]=ABC123&cancel[refunds][][reimbursement_method]=gift_card&cancel[refunds][][gift_card_email]=admin%40example.com&cancel[refunds][][amount]=10&cancel[refunds][][reimbursement_method]=store_credit&cancel[refunds][][amount]=10&cancel%5Binfo%5D%5B%5D[order_item_summary_id]=line_item_1&cancel%5Binfo%5D%5B%5D[label]=Never+Worked&cancel%5Binfo%5D%5B%5D[quantity]=1
```


| Name | Description |
|:-----|:------------|
| cancel[total] *required* | Total amount of the cancellation |
| cancel[reason_external_id] *required* | Refund reason id |
| cancel[info] *required* | Array of adjustment to create on the order |
| cancel[info][][order_item_summary_id] *required* | Reference of line item to link the adjustments |
| cancel[info][][label] *required* | Refund label |
| cancel[info][][quantity] *required* | Quantity of line item to cancel |
| cancel[refunds] *required* | Array of refund or credit to create on the reimbursement |
| cancel[refunds][][reimbursement_method] *required* | It can be braintree/store_credit/gift_card |
| cancel[refunds][][amount] *required* | Amount of the refund/credit |
| cancel[refunds][][payment_id] *required* | Payment ID of the transaction(only for braintree) |
| cancel[refunds][][transaction_id] *required* | Transaction id of refund(only for braintree) |
| cancel[refunds][][gift_card_email] *required* | Gift card email(only for gift_card) |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
ETag: W/&quot;28ca67ac1b0c2b3b73c31c9732df3f03&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 14d35b5b-6142-4f1e-afa5-1389349f8cb4
X-Runtime: 0.274247
Vary: Origin
Content-Length: 265
201 Created
```


```json
{
  "cancel": {
    "id": 2,
    "number": "RI310426842",
    "reimbursement_status": "reimbursed",
    "customer_return_id": null,
    "order_id": 39,
    "total": "10.0",
    "created_at": "2021-07-13T07:59:20.071-04:00",
    "updated_at": "2021-07-13T07:59:20.162-04:00",
    "mirakl_order_line_reimbursement_id": null
  }
}
```



# OMS Carton

Create a carton for provided order item summaries

## Create a carton containing the provided inventory_units


### Request

#### Endpoint

```plaintext
POST /api/oms/cartons
Accept: application/json
Authorizat IO N: Bearer 1ff21bf975739034c78665efebf53da6c9600e14d3f00978
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/oms/cartons`

#### Parameters


```json
carton[tracking]=https%3A%2F%2Ftracking.code&carton[shipping_carrier_code]=SHIPPING_CARRIER_CODE&carton[shipment_number]=H65871380702&carton%5Bitems%5D%5B%5D[order_item_summary_ref]=line_item_1&carton%5Bitems%5D%5B%5D[quantity]=1
```


| Name | Description |
|:-----|:------------|
| carton[tracking] *required* | Tracking code of the carton |
| carton[shipping_carrier_code] *required* | Shipping carrier code |
| carton[shipment_number] *required* | Solidus Shipment number |
| carton[items] *required* | Array of adjustment to create on the order |
| carton[items][][order_item_summary_ref] *required* | Reference of line item to take the inventory_units to put in the carton |
| carton[items][][quantity] *required* | Quantity of line item to put in the carton |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
ETag: W/&quot;68356f22121c1015ef4ed76a405d8203&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: dfbe3471-b641-41f7-8675-ff37a39138a1
X-Runtime: 0.279775
Vary: Origin
Content-Length: 386
201 Created
```


```json
{
  "carton": {
    "id": 1,
    "number": "C53617428673",
    "external_number": "H65871380702",
    "stock_location_id": 2,
    "address_id": 2,
    "shipping_method_id": 1,
    "tracking": "https://tracking.code",
    "shipped_at": null,
    "created_at": "2021-07-13T07:58:12.309-04:00",
    "updated_at": "2021-07-13T07:58:12.309-04:00",
    "imported_from_shipment_id": 1,
    "shipping_carrier_code": "SHIPPING_CARRIER_CODE",
    "override_tracking_url": null
  }
}
```



## Update a carton and its shipments with the provided params


### Request

#### Endpoint

```plaintext
PUT /api/oms/cartons
Accept: application/json
Authorizat IO N: Bearer 530906b7bf75db77bf5cb053dfedf1911dde2407347d1597
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PUT /api/oms/cartons`

#### Parameters


```json
tracking=012345&shipping_carrier_code=carrier_code&override_tracking_url=http%3A%2F%2Ftracking.info
```


| Name | Description |
|:-----|:------------|
| tracking *required* | The tracking code that will be used to find the correct carton to update |
| shipping_carrier_code  | The shipping carrier code to update |
| override_tracking_url  | The tracking URL override |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
ETag: W/&quot;7ca6346e7197a4b856752d6dffd92c81&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 8355dcf5-ca50-4c11-9576-5dc512162f7c
X-Runtime: 0.079205
Vary: Origin
Content-Length: 908
200 OK
```


```json
{
  "carton": {
    "id": 2,
    "tracking": "012345",
    "shipping_carrier_code": "carrier_code",
    "override_tracking_url": "http://tracking.info",
    "address_id": 7,
    "stock_location_id": 4,
    "shipping_method_id": 3,
    "number": "C73384742665",
    "external_number": null,
    "shipped_at": "2021-07-13T07:58:12.464-04:00",
    "created_at": "2021-07-13T07:58:12.821-04:00",
    "updated_at": "2021-07-13T07:58:12.952-04:00",
    "imported_from_shipment_id": null
  },
  "shipments": [
    {
      "id": 3,
      "tracking": "012345",
      "shipping_carrier_code": "carrier_code",
      "override_tracking_url": "http://tracking.info",
      "cost": "100.0",
      "state": "pending",
      "number": "H78035201053",
      "shipped_at": null,
      "order_id": 4,
      "deprecated_address_id": null,
      "created_at": "2021-07-13T07:58:12.827-04:00",
      "updated_at": "2021-07-13T07:58:12.932-04:00",
      "stock_location_id": 4,
      "adjustment_total": "0.0",
      "additional_tax_total": "0.0",
      "promo_total": "0.0",
      "included_tax_total": "0.0",
      "easypost_error": null,
      "delivery_estimation": null
    }
  ]
}
```



# OMS Promotion Codes

Create a code for a promotion that matches value and type. It creates a new promotion if not found

## Create a promotion code for a new $10 off promotion


### Request

#### Endpoint

```plaintext
POST /api/oms/promotion_codes
Accept: application/json
Authorizat IO N: Bearer 6b8a9f18e7c8d9468d08f2ac3fb3057a12de2558dfb30e9e
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/oms/promotion_codes`

#### Parameters


```json
promotion_code[recipient_email]=john%40example.com&promotion_code[type]=flat&promotion_code[value]=10
```


| Name | Description |
|:-----|:------------|
| promotion_code[recipient_email] *required* | E-mail that will receive the code |
| promotion_code[type] *required* | The type of the promotion calculator. Accepted values are: flat, percent |
| promotion_code[value] *required* | The value amount or percent used by the promotion calculator |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
ETag: W/&quot;a2ae5d8c19071dc223c78461b4811304&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 0c3d3a40-28a2-4cb7-be0f-9b3340863b8f
X-Runtime: 0.068085
Vary: Origin
Content-Length: 203
201 Created
```


```json
{
  "promotion_code": {
    "id": 8,
    "promotion_id": 10,
    "value": "bbbjbclv",
    "created_at": "2021-07-13T07:59:13.830-04:00",
    "updated_at": "2021-07-13T07:59:13.830-04:00",
    "promotion_code_batch_id": null,
    "expires_at": null
  }
}
```



## Create a promotion code for an existing $10 off promotion


### Request

#### Endpoint

```plaintext
POST /api/oms/promotion_codes
Accept: application/json
Authorizat IO N: Bearer d67cf8e7c335d123bf6442dda3ada758f3c9b8653b9589f6
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/oms/promotion_codes`

#### Parameters


```json
promotion_code[recipient_email]=john%40example.com&promotion_code[type]=flat&promotion_code[value]=10.5
```


| Name | Description |
|:-----|:------------|
| promotion_code[recipient_email] *required* | E-mail that will receive the code |
| promotion_code[type] *required* | The type of the promotion calculator. Accepted values are: flat, percent |
| promotion_code[value] *required* | The value amount or percent used by the promotion calculator |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
ETag: W/&quot;ba67e015de8c6bca7e5fa893e8d41100&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 4b4c0872-d7a6-4a91-a282-a1be98e75007
X-Runtime: 0.069578
Vary: Origin
Content-Length: 202
201 Created
```


```json
{
  "promotion_code": {
    "id": 6,
    "promotion_id": 8,
    "value": "vlcqbgmn",
    "created_at": "2021-07-13T07:59:13.586-04:00",
    "updated_at": "2021-07-13T07:59:13.586-04:00",
    "promotion_code_batch_id": null,
    "expires_at": null
  }
}
```



## Create a promotion code for an existing 20% off promotion


### Request

#### Endpoint

```plaintext
POST /api/oms/promotion_codes
Accept: application/json
Authorizat IO N: Bearer ab7aa1d97c1dcda7e16fa248669c2327739fb63d5eb123fc
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/oms/promotion_codes`

#### Parameters


```json
promotion_code[recipient_email]=john%40example.com&promotion_code[type]=percent&promotion_code[value]=20
```


| Name | Description |
|:-----|:------------|
| promotion_code[recipient_email] *required* | E-mail that will receive the code |
| promotion_code[type] *required* | The type of the promotion calculator. Accepted values are: flat, percent |
| promotion_code[value] *required* | The value amount or percent used by the promotion calculator |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
ETag: W/&quot;689b066431956fa1e0b9f99e20b25a97&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: b8e775d7-d34b-499a-937e-509abaee4e1b
X-Runtime: 0.056758
Vary: Origin
Content-Length: 202
201 Created
```


```json
{
  "promotion_code": {
    "id": 7,
    "promotion_id": 9,
    "value": "lawexnsi",
    "created_at": "2021-07-13T07:59:13.713-04:00",
    "updated_at": "2021-07-13T07:59:13.713-04:00",
    "promotion_code_batch_id": null,
    "expires_at": null
  }
}
```



## Returns error when an invalid type is provided


### Request

#### Endpoint

```plaintext
POST /api/oms/promotion_codes
Accept: application/json
Authorizat IO N: Bearer 532a0958e5f789b172b61f09f3ddecaa55f7c72d46173116
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/oms/promotion_codes`

#### Parameters


```json
promotion_code[recipient_email]=john%40example.com&promotion_code[type]=wrong&promotion_code[value]=10
```


| Name | Description |
|:-----|:------------|
| promotion_code[recipient_email] *required* | E-mail that will receive the code |
| promotion_code[type] *required* | The type of the promotion calculator. Accepted values are: flat, percent |
| promotion_code[value] *required* | The value amount or percent used by the promotion calculator |



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
X-Request-Id: ec2b03f7-21d0-4406-a864-0dfb27b3de51
X-Runtime: 0.041710
Vary: Origin
Content-Length: 84
422 Unprocessable Entity
```


```json
{
  "error": "The informed type (wrong) is invalid. The valid types are: flat, percent"
}
```



# OMS Promotion Eligible

Check which line items in the order are eligible for the coupon_code

## Return the eligible items for that coupon code


### Request

#### Endpoint

```plaintext
GET /api/oms/promotion_eligibility?order_number=M180965075&amp;coupon_code=code3
Accept: application/json
Authorizat IO N: Bearer 00dbc166de181d5110318c5682fc9df16890b258f8d00c86
Host: example.org
Cookie: 
```

`GET /api/oms/promotion_eligibility`

#### Parameters


```json
order_number: M180965075
coupon_code: code3
```


| Name | Description |
|:-----|:------------|
| order_number *required* | Order number to check |
| coupon_code *required* | Coupon Code to apply |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
ETag: W/&quot;97d83f1ff1e1abd792bec80f1a8a6edd&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 21e7f300-7839-426a-98e3-8e612409ecf9
X-Runtime: 0.182051
Vary: Origin
Content-Length: 94
200 OK
```


```json
{
  "success": true,
  "items": [
    {
      "type": "Spree::LineItem",
      "id": 39,
      "order_item_summary_ref": "SF001"
    }
  ]
}
```



# OMS Return

Create a return authorization

## Create an return authorization


### Request

#### Endpoint

```plaintext
POST /api/oms/returns
Accept: application/json
Authorizat IO N: Bearer 2b7c7fb054fdadfc60414de1bc564f99831891de793ec1c5
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/oms/returns`

#### Parameters


```json
return[total]=10.0&return[tracking_url]=https%3A%2F%2Ftracking.url%2Fcarrier&return%5Binfo%5D%5B%5D[order_item_summary_ref]=line_item_1&return%5Binfo%5D%5B%5D[quantity]=2&return%5Binfo%5D%5B%5D[return_reason_external_id]=Z2lkOi8vZW52ZjFkZTllNDg5YmE4OGNiMTU5NjhiOTdmNDBmNTllOGVmMGRhNWNhMDNhZDFmMzdmYzEzYTJhYTQ1YTI1MTJhOS1tYWlzb25ldHRlLWJhY2tlbmQvT3JkZXJNYW5hZ2VtZW50OjpSZWFzb24vY2ViMzExYjEtYWIzMC00ZmIyLWIwMzUtODYxZTA5ZGJmOTQ1
```


| Name | Description |
|:-----|:------------|
| return[total] *required* | Total amount of the return |
| return[tracking_url] *required* | Tracking url of return authorization |
| return[info] *required* | Array of adjustment to create on the order |
| return[info][][order_item_summary_ref] *required* | Reference of line item to link the adjustments |
| return[info][][quantity] *required* | number of item to return for that line item |
| return[info][][return_reason_external_id] *required* | Return reason external id |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
ETag: W/&quot;633c64bc8b38999f63693cadfe4f82a2&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: dea13df6-c60e-468a-8f1a-4e1d3e468f83
X-Runtime: 0.256738
Vary: Origin
Content-Length: 300
201 Created
```


```json
{
  "return": {
    "id": 1,
    "number": "RA835807135",
    "state": "authorized",
    "order_id": 14,
    "memo": null,
    "created_at": "2021-07-13T07:58:36.574-04:00",
    "updated_at": "2021-07-13T07:58:36.574-04:00",
    "stock_location_id": 33,
    "return_reason_id": null,
    "gift_recipient_email": null,
    "tracking_url": "https://tracking.url/carrier"
  }
}
```



# Orders



## Add a gift card item to a cart


### Request

#### Endpoint

```plaintext
POST /api/orders/cart
Accept: application/json
Authorizat IO N: Bearer ebb682b14a39318e2eab2fde8df5ca68a8d932eaa98e5c15
X-Spree-Order-Token: 
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/cart`

#### Parameters


```json
user_id&order_token&line_item[variant_id]=132&line_item[quantity]=1&line_item[vendor_id]=237&line_item[gift_card_details_attributes][recipient_name]=Recipient+John&line_item[gift_card_details_attributes][recipient_email]=recipient%40email.com&line_item[gift_card_details_attributes][purchaser_name]=Purchaser+Bob&line_item[gift_card_details_attributes][gift_message]=Surprise&line_item[gift_card_details_attributes][send_email_at]=2021-07-13
```


| Name | Description |
|:-----|:------------|
| user_id  | Specify the user_id here if there is one. Calls to this endpoint without a user_id will                          create an order with a nil user |
| order_token  | Spree will look for an order with the order token if it is provided. If an order with                              the specified token is not found, Spree will create a new order with an autogenerated                              guest token that should be stored in cookies and returned with subsequent calls. The                              order token can be passed as a parameter or a header. If passed as both a header and                              parameter, the header will take precedence. |
| line_item[variant_id] *required* | Specify the variant id |
| line_item[quantity] *required* | Specify the quantity requested, must be greater than 0 |
| line_item[vendor_id] *required* | Specify the vendor id, from the price chosen |
| line_item[gift_card_details_attributes]  | Line item gift card details attributes |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
ETag: W/&quot;fcfc6dd5f855297e3f2ba731a1f95fa7&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: b426529b-ff1f-4340-aacf-3dfdafd8816f
X-Runtime: 0.348294
Vary: Origin
Content-Length: 2892
200 OK
```


```json
{
  "id": 18,
  "number": "M037989847",
  "item_total": "19.99",
  "total": "19.99",
  "ship_total": "0.0",
  "state": "cart",
  "adjustment_total": "0.0",
  "user_id": 74,
  "created_at": "2021-07-13T07:58:50.912-04:00",
  "updated_at": "2021-07-13T07:58:51.006-04:00",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "email74@example.com",
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
  "order_total_after_store_credit": "19.99",
  "display_order_total_after_store_credit": "$19.99",
  "total_applicable_store_credit": 0,
  "display_total_available_store_credit": "$0.00",
  "display_store_credit_remaining_after_capture": "$0.00",
  "canceler_id": null,
  "gift_email": null,
  "gift_message": null,
  "is_gift": false,
  "use_store_credits": false,
  "first_order": false,
  "display_item_total": "$19.99",
  "total_quantity": 1,
  "display_total": "$19.99",
  "display_ship_total": "$0.00",
  "display_tax_total": "$0.00",
  "token": "XKXwbo2cj_IH_lWNtjOwaw",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order?order=M037989847&bzip=&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [

  ],
  "bill_address": null,
  "ship_address": null,
  "line_items": [
    {
      "id": 13,
      "quantity": 1,
      "price": "19.99",
      "variant_id": 132,
      "vendor_id": 237,
      "single_display_amount": "$19.99",
      "display_amount": "$19.99",
      "total": "19.99",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 132,
        "name": "Product #72 - 1555",
        "sku": "SKU-132",
        "is_master": false,
        "slug": "product-72-1555",
        "description": "As seen on TV!",
        "track_inventory": true,
        "cost_price": "17.0",
        "price": "19.99",
        "display_price": "$19.99",
        "options_text": "Size: S",
        "in_stock": true,
        "is_backorderable": false,
        "total_on_hand": 10,
        "is_destroyed": false,
        "option_values": [
          {
            "id": 59,
            "name": "Size-59",
            "presentation": "S",
            "option_type_name": "foo-size-59",
            "option_type_id": 59,
            "option_type_presentation": "Size",
            "position": 1
          }
        ],
        "images": [

        ],
        "videos": [

        ],
        "product_id": 72,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [
        {
          "recipient_name": "Recipient John",
          "recipient_email": "recipient@email.com",
          "purchaser_name": "Purchaser Bob",
          "gift_message": "Surprise",
          "send_email_at": "2021-07-13T00:00:00.000-04:00"
        }
      ],
      "vendor_name": "Vendor #238",
      "country_iso": null,
      "domestic_override": null,
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
    "can_update": true
  },
  "gift_card_total": "0.0",
  "applied_promotion_codes": [

  ],
  "subtotals": {
    "order_total": "19.99",
    "item_total": "19.99",
    "shipments_total": "0.0",
    "line_item_promotion_totals": [

    ],
    "tax_adjustments": [

    ],
    "miscellaneous_adjustments": [

    ],
    "giftwrap_amount": 0
  }
}
```



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
user_id&order_token&line_item[variant_id]=144&line_item[quantity]=2&line_item[vendor_id]=258
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
ETag: W/&quot;e32a3ae263830440ae9d92b5cd355e15&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 073a7615-0e3f-4dcd-833f-8ae44146c7a1
X-Runtime: 0.219946
Vary: Origin
Content-Length: 2678
200 OK
```


```json
{
  "id": 21,
  "number": "M913847901",
  "item_total": "39.98",
  "total": "39.98",
  "ship_total": "0.0",
  "state": "cart",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2021-07-13T07:58:56.799-04:00",
  "updated_at": "2021-07-13T07:58:56.874-04:00",
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
  "gift_email": null,
  "gift_message": null,
  "is_gift": false,
  "use_store_credits": false,
  "first_order": false,
  "display_item_total": "$39.98",
  "total_quantity": 2,
  "display_total": "$39.98",
  "display_ship_total": "$0.00",
  "display_tax_total": "$0.00",
  "token": "hg7PWhePG1nPQxCzw4aBEw",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order?order=M913847901&bzip=&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [

  ],
  "bill_address": null,
  "ship_address": null,
  "line_items": [
    {
      "id": 18,
      "quantity": 2,
      "price": "19.99",
      "variant_id": 144,
      "vendor_id": 258,
      "single_display_amount": "$19.99",
      "display_amount": "$39.98",
      "total": "39.98",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 144,
        "name": "Product #79 - 1249",
        "sku": "SKU-143",
        "is_master": false,
        "slug": "product-79-1249",
        "description": "As seen on TV!",
        "track_inventory": true,
        "price": "19.99",
        "display_price": "$19.99",
        "options_text": "Size: S",
        "in_stock": true,
        "is_backorderable": false,
        "total_on_hand": 10,
        "is_destroyed": false,
        "option_values": [
          {
            "id": 65,
            "name": "Size-65",
            "presentation": "S",
            "option_type_name": "foo-size-65",
            "option_type_id": 65,
            "option_type_presentation": "Size",
            "position": 1
          }
        ],
        "images": [

        ],
        "videos": [

        ],
        "product_id": 79,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [

      ],
      "vendor_name": "Vendor #259",
      "country_iso": null,
      "domestic_override": null,
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
  "gift_card_total": "0.0",
  "applied_promotion_codes": [

  ],
  "subtotals": {
    "order_total": "39.98",
    "item_total": "39.98",
    "shipments_total": "0.0",
    "line_item_promotion_totals": [

    ],
    "tax_adjustments": [

    ],
    "miscellaneous_adjustments": [

    ],
    "giftwrap_amount": 0
  }
}
```



## Add an item to a cart related to the user


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
user_id&order_token&line_item[variant_id]=156&line_item[quantity]=2&line_item[vendor_id]=280
```


| Name | Description |
|:-----|:------------|
| user_id  | Specify the user_id here if there is one. Calls to this endpoint without a user_id will                          create an order with a nil user |
| order_token  | Spree will look for an order with the order token if it is provided. If an order with                              the specified token is not found, Spree will create a new order with an autogenerated                              guest token that should be stored in cookies and returned with subsequent calls. The                              order token can be passed as a parameter or a header. If passed as both a header and                              parameter, the header will take precedence. |
| line_item[variant_id] *required* | Specify the variant id |
| line_item[quantity] *required* | Specify the quantity requested, must be greater than 0 |
| line_item[vendor_id] *required* | Specify the vendor id, from the price chosen |
| token  | Specify the spree_api_key here if there is one. Calls to this endpoint without a it will \
                         create an order with a nil user |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
ETag: W/&quot;e13e49d8039c6a0892dbb4c3897b7e03&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: ab7609c1-43ea-41e3-977d-e027b789bd8e
X-Runtime: 0.226584
Vary: Origin
Content-Length: 2678
200 OK
```


```json
{
  "id": 24,
  "number": "M215624334",
  "item_total": "39.98",
  "total": "39.98",
  "ship_total": "0.0",
  "state": "cart",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2021-07-13T07:59:00.446-04:00",
  "updated_at": "2021-07-13T07:59:00.526-04:00",
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
  "gift_email": null,
  "gift_message": null,
  "is_gift": false,
  "use_store_credits": false,
  "first_order": false,
  "display_item_total": "$39.98",
  "total_quantity": 2,
  "display_total": "$39.98",
  "display_ship_total": "$0.00",
  "display_tax_total": "$0.00",
  "token": "c7s1g0UGgn49dpDRlvHjcw",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order?order=M215624334&bzip=&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [

  ],
  "bill_address": null,
  "ship_address": null,
  "line_items": [
    {
      "id": 22,
      "quantity": 2,
      "price": "19.99",
      "variant_id": 156,
      "vendor_id": 280,
      "single_display_amount": "$19.99",
      "display_amount": "$39.98",
      "total": "39.98",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 156,
        "name": "Product #85 - 2578",
        "sku": "SKU-155",
        "is_master": false,
        "slug": "product-85-2578",
        "description": "As seen on TV!",
        "track_inventory": true,
        "price": "19.99",
        "display_price": "$19.99",
        "options_text": "Size: S",
        "in_stock": true,
        "is_backorderable": false,
        "total_on_hand": 10,
        "is_destroyed": false,
        "option_values": [
          {
            "id": 71,
            "name": "Size-71",
            "presentation": "S",
            "option_type_name": "foo-size-71",
            "option_type_id": 71,
            "option_type_presentation": "Size",
            "position": 1
          }
        ],
        "images": [

        ],
        "videos": [

        ],
        "product_id": 85,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [

      ],
      "vendor_name": "Vendor #281",
      "country_iso": null,
      "domestic_override": null,
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
  "gift_card_total": "0.0",
  "applied_promotion_codes": [

  ],
  "subtotals": {
    "order_total": "39.98",
    "item_total": "39.98",
    "shipments_total": "0.0",
    "line_item_promotion_totals": [

    ],
    "tax_adjustments": [

    ],
    "miscellaneous_adjustments": [

    ],
    "giftwrap_amount": 0
  }
}
```



## Add an item to a cart related to the user


### Request

#### Endpoint

```plaintext
POST /api/orders/cart
Accept: application/json
Authorizat IO N: Bearer a68b4b8b2e263c88635081aaf10da8cadfd51290c7f1cd0d
X-Spree-Order-Token: 
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/cart`

#### Parameters


```json
user_id&order_token&line_item[variant_id]=160&line_item[quantity]=2&line_item[vendor_id]=288&user_token=Bearer+a68b4b8b2e263c88635081aaf10da8cadfd51290c7f1cd0d
```


| Name | Description |
|:-----|:------------|
| user_id  | Specify the user_id here if there is one. Calls to this endpoint without a user_id will                          create an order with a nil user |
| order_token  | Spree will look for an order with the order token if it is provided. If an order with                              the specified token is not found, Spree will create a new order with an autogenerated                              guest token that should be stored in cookies and returned with subsequent calls. The                              order token can be passed as a parameter or a header. If passed as both a header and                              parameter, the header will take precedence. |
| line_item[variant_id] *required* | Specify the variant id |
| line_item[quantity] *required* | Specify the quantity requested, must be greater than 0 |
| line_item[vendor_id] *required* | Specify the vendor id, from the price chosen |
| user_token  | Specify the spree_api_key here if there is one. Calls to this endpoint without a it will \
                              create an order with a nil user |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
ETag: W/&quot;e439a6a57b93f06db298e2b95eeed7d2&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 9beb0c36-f65c-493c-bdcc-802a7546a8df
X-Runtime: 0.243278
Vary: Origin
Content-Length: 2690
200 OK
```


```json
{
  "id": 25,
  "number": "M821256852",
  "item_total": "39.98",
  "total": "39.98",
  "ship_total": "0.0",
  "state": "cart",
  "adjustment_total": "0.0",
  "user_id": 79,
  "created_at": "2021-07-13T07:59:01.432-04:00",
  "updated_at": "2021-07-13T07:59:01.512-04:00",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "email79@example.com",
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
  "total_applicable_store_credit": 0,
  "display_total_available_store_credit": "$0.00",
  "display_store_credit_remaining_after_capture": "$0.00",
  "canceler_id": null,
  "gift_email": null,
  "gift_message": null,
  "is_gift": false,
  "use_store_credits": false,
  "first_order": false,
  "display_item_total": "$39.98",
  "total_quantity": 2,
  "display_total": "$39.98",
  "display_ship_total": "$0.00",
  "display_tax_total": "$0.00",
  "token": "8eUMHRavG0nw93M4sVCB9w",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order?order=M821256852&bzip=&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [

  ],
  "bill_address": null,
  "ship_address": null,
  "line_items": [
    {
      "id": 23,
      "quantity": 2,
      "price": "19.99",
      "variant_id": 160,
      "vendor_id": 288,
      "single_display_amount": "$19.99",
      "display_amount": "$39.98",
      "total": "39.98",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 160,
        "name": "Product #87 - 3023",
        "sku": "SKU-159",
        "is_master": false,
        "slug": "product-87-3023",
        "description": "As seen on TV!",
        "track_inventory": true,
        "price": "19.99",
        "display_price": "$19.99",
        "options_text": "Size: S",
        "in_stock": true,
        "is_backorderable": false,
        "total_on_hand": 10,
        "is_destroyed": false,
        "option_values": [
          {
            "id": 73,
            "name": "Size-73",
            "presentation": "S",
            "option_type_name": "foo-size-73",
            "option_type_id": 73,
            "option_type_presentation": "Size",
            "position": 1
          }
        ],
        "images": [

        ],
        "videos": [

        ],
        "product_id": 87,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [

      ],
      "vendor_name": "Vendor #289",
      "country_iso": null,
      "domestic_override": null,
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
    "can_update": true
  },
  "gift_card_total": "0.0",
  "applied_promotion_codes": [

  ],
  "subtotals": {
    "order_total": "39.98",
    "item_total": "39.98",
    "shipments_total": "0.0",
    "line_item_promotion_totals": [

    ],
    "tax_adjustments": [

    ],
    "miscellaneous_adjustments": [

    ],
    "giftwrap_amount": 0
  }
}
```



## Add an item to a order


### Request

#### Endpoint

```plaintext
POST /api/orders/cart
Accept: application/json
Authorizat IO N: 
X-Spree-Order-Token: yzsVGmBiQhmXz7zaJuUjpQ
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/cart`

#### Parameters


```json
user_id&order_token=yzsVGmBiQhmXz7zaJuUjpQ&line_item[variant_id]=152&line_item[quantity]=2&line_item[vendor_id]=274
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
ETag: W/&quot;bf31b11cf1cd4d47d7d05db4a6f9aa99&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: cc8f76d3-51c2-43f0-b2f5-c5c243d52506
X-Runtime: 0.223230
Vary: Origin
Content-Length: 2677
200 OK
```


```json
{
  "id": 23,
  "number": "M807216616",
  "item_total": "39.98",
  "total": "39.98",
  "ship_total": "0.0",
  "state": "cart",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2021-07-13T07:58:59.483-04:00",
  "updated_at": "2021-07-13T07:58:59.560-04:00",
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
  "gift_email": null,
  "gift_message": null,
  "is_gift": false,
  "use_store_credits": false,
  "first_order": false,
  "display_item_total": "$39.98",
  "total_quantity": 2,
  "display_total": "$39.98",
  "display_ship_total": "$0.00",
  "display_tax_total": "$0.00",
  "token": "zvHsUV7Pm8n78o1x4tJ0pg",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order?order=M807216616&bzip=&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [

  ],
  "bill_address": null,
  "ship_address": null,
  "line_items": [
    {
      "id": 21,
      "quantity": 2,
      "price": "19.99",
      "variant_id": 152,
      "vendor_id": 274,
      "single_display_amount": "$19.99",
      "display_amount": "$39.98",
      "total": "39.98",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 152,
        "name": "Product #83 - 2021",
        "sku": "SKU-151",
        "is_master": false,
        "slug": "product-83-2021",
        "description": "As seen on TV!",
        "track_inventory": true,
        "price": "19.99",
        "display_price": "$19.99",
        "options_text": "Size: S",
        "in_stock": true,
        "is_backorderable": true,
        "total_on_hand": 10,
        "is_destroyed": false,
        "option_values": [
          {
            "id": 69,
            "name": "Size-69",
            "presentation": "S",
            "option_type_name": "foo-size-69",
            "option_type_id": 69,
            "option_type_presentation": "Size",
            "position": 1
          }
        ],
        "images": [

        ],
        "videos": [

        ],
        "product_id": 83,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [

      ],
      "vendor_name": "Vendor #275",
      "country_iso": null,
      "domestic_override": null,
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
  "gift_card_total": "0.0",
  "applied_promotion_codes": [

  ],
  "subtotals": {
    "order_total": "39.98",
    "item_total": "39.98",
    "shipments_total": "0.0",
    "line_item_promotion_totals": [

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
Authorizat IO N: Bearer d9e093e0c1a2bbf696b17e9c9b0d3aadf88ec86f0b969fa1
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
X-Request-Id: d3397423-f369-4701-8760-b5a922d896d0
X-Runtime: 0.046180
Vary: Origin
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



## it returns a 200


### Request

#### Endpoint

```plaintext
GET /api/orders/M502665406
Accept: application/json
Authorizat IO N: Bearer 0843a05ae4f0a409937cce773cef7ce9d5c888b6c7175092
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
ETag: W/&quot;0242b84c851844ace202ae42685063be&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: fd058121-cd64-4d0d-9b50-ca32fcd44dd1
X-Runtime: 0.361623
Vary: Origin
Content-Length: 7959
200 OK
```


```json
{
  "id": 19,
  "number": "M502665406",
  "item_total": "20.0",
  "total": "118.0",
  "ship_total": "100.0",
  "state": "payment",
  "adjustment_total": "-2.0",
  "user_id": 75,
  "created_at": "2021-07-13T07:58:52.142-04:00",
  "updated_at": "2021-07-13T07:58:53.412-04:00",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "email75@example.com",
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
  "order_total_after_store_credit": "118.0",
  "display_order_total_after_store_credit": "$118.00",
  "total_applicable_store_credit": 0,
  "display_total_available_store_credit": "$0.00",
  "display_store_credit_remaining_after_capture": "$0.00",
  "canceler_id": null,
  "gift_email": null,
  "gift_message": null,
  "is_gift": false,
  "use_store_credits": false,
  "first_order": false,
  "display_item_total": "$20.00",
  "total_quantity": 2,
  "display_total": "$118.00",
  "display_ship_total": "$100.00",
  "display_tax_total": "$0.00",
  "token": "51lJygWJYuhZaIn6enLWLg",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order?order=M502665406&bzip=10036&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [

  ],
  "bill_address": {
    "id": 37,
    "firstname": "John",
    "lastname": "Smith",
    "full_name": "John Smith",
    "address1": "PO Box 1337",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10036",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 40,
    "country_iso": "US",
    "state_id": 40,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 40,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 40,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 40
    }
  },
  "ship_address": {
    "id": 38,
    "firstname": "John",
    "lastname": "Smith",
    "full_name": "John Smith",
    "address1": "A Different Road",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10037",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 40,
    "country_iso": "US",
    "state_id": 40,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 40,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 40,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 40
    }
  },
  "line_items": [
    {
      "id": 14,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 134,
      "vendor_id": 243,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "9.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 134,
        "name": "Product #74 - 2971",
        "sku": "SKU-133",
        "is_master": false,
        "slug": "product-74-2971",
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
            "id": 60,
            "name": "Size-60",
            "presentation": "S",
            "option_type_name": "foo-size-60",
            "option_type_id": 60,
            "option_type_presentation": "Size",
            "position": 1
          }
        ],
        "images": [

        ],
        "videos": [

        ],
        "product_id": 74,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [

      ],
      "vendor_name": "Vendor #244",
      "country_iso": "US",
      "domestic_override": false,
      "adjustments": [
        {
          "id": 4,
          "source_type": "Spree::PromotionAction",
          "source_id": 4,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 14,
          "amount": "-1.0",
          "label": "Promotion (10% off)",
          "promotion_code_id": 4,
          "finalized": false,
          "eligible": true,
          "created_at": "2021-07-13T07:58:53.120-04:00",
          "updated_at": "2021-07-13T07:58:53.120-04:00",
          "display_amount": "-$1.00"
        }
      ]
    },
    {
      "id": 15,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 136,
      "vendor_id": 243,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "9.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 136,
        "name": "Product #75 - 2223",
        "sku": "SKU-135",
        "is_master": false,
        "slug": "product-75-2223",
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
            "id": 61,
            "name": "Size-61",
            "presentation": "S",
            "option_type_name": "foo-size-61",
            "option_type_id": 61,
            "option_type_presentation": "Size",
            "position": 1
          }
        ],
        "images": [

        ],
        "videos": [

        ],
        "product_id": 75,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [

      ],
      "vendor_name": "Vendor #244",
      "country_iso": "US",
      "domestic_override": false,
      "adjustments": [
        {
          "id": 5,
          "source_type": "Spree::PromotionAction",
          "source_id": 4,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 15,
          "amount": "-1.0",
          "label": "Promotion (10% off)",
          "promotion_code_id": 4,
          "finalized": false,
          "eligible": true,
          "created_at": "2021-07-13T07:58:53.138-04:00",
          "updated_at": "2021-07-13T07:58:53.138-04:00",
          "display_amount": "-$1.00"
        }
      ]
    }
  ],
  "payments": [

  ],
  "shipments": [
    {
      "id": 15,
      "tracking": null,
      "tracking_url": null,
      "number": "H86070420743",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M502665406",
      "stock_location_name": "NY Warehouse 48",
      "giftwrappable": false,
      "stock_location_id": 48,
      "giftwrap": null,
      "shipping_rates": [
        {
          "id": 13,
          "name": "UPS Ground",
          "admin_name": null,
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 13,
          "shipping_method_code": "UPS_GROUND",
          "extra_cost": "+$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 13,
        "name": "UPS Ground",
        "admin_name": null,
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 13,
        "shipping_method_code": "UPS_GROUND",
        "extra_cost": "+$100.00",
        "base_flat_rate_amount": 0.0
      },
      "shipping_methods": [
        {
          "id": 13,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 10,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 39,
              "name": "ShippingCategory #37"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 134,
          "quantity": 1,
          "states": {
            "on_hand": 1
          }
        },
        {
          "variant_id": 136,
          "quantity": 1,
          "states": {
            "on_hand": 1
          }
        }
      ],
      "adjustments": [
        {
          "id": 7,
          "source_type": "Spree::PromotionAction",
          "source_id": 5,
          "adjustable_type": "Spree::Shipment",
          "adjustable_id": 15,
          "amount": "-10.0",
          "label": "Shipping",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2021-07-13T07:58:53.274-04:00",
          "updated_at": "2021-07-13T07:58:53.274-04:00",
          "display_amount": "-$10.00"
        },
        {
          "id": 6,
          "source_type": "Spree::PromotionAction",
          "source_id": 5,
          "adjustable_type": "Spree::Shipment",
          "adjustable_id": 15,
          "amount": "-9.99",
          "label": "Shipping",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2021-07-13T07:58:53.260-04:00",
          "updated_at": "2021-07-13T07:58:53.260-04:00",
          "display_amount": "-$9.99"
        }
      ],
      "stock_location_address": "NY Warehouse 48, Washington, AL",
      "country_iso": "US",
      "international_shipping": false,
      "delivery_estimation": "Jul 15",
      "estimated_giftwrap_price": "5.0",
      "display_estimated_giftwrap_price": "$5.00"
    }
  ],
  "adjustments": [
    {
      "id": 8,
      "source_type": "Spree::Promotion",
      "source_id": 5,
      "adjustable_type": "Spree::Order",
      "adjustable_id": 19,
      "amount": "20.0",
      "label": "adj1",
      "promotion_code_id": null,
      "finalized": false,
      "eligible": true,
      "created_at": "2021-07-13T07:58:53.285-04:00",
      "updated_at": "2021-07-13T07:58:53.285-04:00",
      "display_amount": "$20.00"
    },
    {
      "id": 9,
      "source_type": "Spree::Promotion",
      "source_id": 5,
      "adjustable_type": "Spree::Order",
      "adjustable_id": 19,
      "amount": "30.0",
      "label": "adj2",
      "promotion_code_id": null,
      "finalized": false,
      "eligible": true,
      "created_at": "2021-07-13T07:58:53.292-04:00",
      "updated_at": "2021-07-13T07:58:53.292-04:00",
      "display_amount": "$30.00"
    }
  ],
  "permissions": {
    "can_update": true
  },
  "gift_card_total": "0.0",
  "applied_promotion_codes": [
    {
      "id": 4,
      "promotion_id": 4,
      "value": "code1",
      "expires_at": null
    }
  ],
  "subtotals": {
    "order_total": "118.0",
    "item_total": "20.0",
    "shipments_total": "80.01",
    "line_item_promotion_totals": [
      {
        "source_id": 4,
        "label": "Promotion (10% off)",
        "total": "-2.0"
      }
    ],
    "tax_adjustments": [
      {
        "label": "VAT 5%",
        "amount": "1.8"
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
GET /api/orders/M346065572
Accept: application/json
Authorizat IO N: 02421952543bfdeb7aa22c0d0aa11fc4e597f706f92ed39e
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
X-Request-Id: 6c5096e1-abc6-4dcc-b962-259ab804f221
X-Runtime: 0.066127
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
Accept: application/json
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/users/password`

#### Parameters


```json
user[email]=email115%40example.com
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
Content-Type: application/json
Cache-Control: no-cache
X-Request-Id: 3ea7ec21-1493-44bf-9a06-0ab6cf6a38f7
X-Runtime: 0.041516
Vary: Origin
Content-Length: 0
200 OK
```




## Login


### Request

#### Endpoint

```plaintext
POST /api/users/login
Accept: application/json
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/users/login`

#### Parameters


```json
user[email]=email114%40example.com&user[password]=secret
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
Authorization: Bearer 68ff2be807d20c55f10dc12fd239987b01602f7286fd1178
ETag: W/&quot;51e692da6a3f5d01c4594dbb496af78d&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: b0d6a0e3-dc03-4537-a3e2-0435f3247f70
X-Runtime: 0.046408
Vary: Origin
Content-Length: 565
200 OK
```


```json
{
  "id": 116,
  "email": "email114@example.com",
  "persistence_token": null,
  "perishable_token": null,
  "last_request_at": null,
  "login": "email114@example.com",
  "ship_address_id": null,
  "bill_address_id": null,
  "created_at": "2021-07-13T07:59:21.305-04:00",
  "updated_at": "2021-07-13T07:59:21.308-04:00",
  "spree_api_key": "68ff2be807d20c55f10dc12fd239987b01602f7286fd1178",
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
X-Request-Id: f6355b05-3265-43d8-8d50-fefd56324393
X-Runtime: 0.028521
Vary: Origin
204 No Content
```




# Products

get products by taxon

## Fetch a single product by id


### Request

#### Endpoint

```plaintext
GET /api/products/product-64-3339
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
Date: Tue, 13 Jul 2021 11:58:40 GMT
Surrogate-Control: max-age=900
Surrogate-Key: product_id=1
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;b63827ea4de71fa42dfb9525a33d10a8&quot;
X-Request-Id: e04b0c02-5269-4465-9985-f0ed068b8f5a
X-Runtime: 0.142683
Vary: Origin
Content-Length: 1602
200 OK
```


```json
{
  "id": 64,
  "name": "Product #64 - 3339",
  "description": "As seen on TV!",
  "available_on": "2020-07-13T07:58:40.529-04:00",
  "slug": "product-64-3339",
  "meta_description": null,
  "meta_keywords": null,
  "taxon_ids": [
    59
  ],
  "total_on_hand": 0,
  "meta_title": null,
  "display_price": "$0.00",
  "brand": null,
  "brand_slug": null,
  "brand_url": null,
  "brand_description": null,
  "gift_card": false,
  "concierge_only": false,
  "is_registry": false,
  "discontinued": false,
  "available": true,
  "trends": [

  ],
  "breadcrumb_taxons": [
    {
      "id": 57,
      "name": "Clothing",
      "taxonomy_id": 17,
      "created_at": "2021-07-13T07:58:40.408-04:00",
      "url": "/category/clothing",
      "position": 1
    },
    {
      "id": 58,
      "name": "Girl",
      "taxonomy_id": 17,
      "created_at": "2021-07-13T07:58:40.452-04:00",
      "url": "/category/clothing/girl",
      "position": 2
    },
    {
      "id": 59,
      "name": "Dresses",
      "taxonomy_id": 17,
      "created_at": "2021-07-13T07:58:40.491-04:00",
      "url": "/category/clothing/girl/dresses",
      "position": 3
    }
  ],
  "has_variants": false,
  "master": {
    "id": 115,
    "name": "Product #64 - 3339",
    "sku": "SKU-115",
    "is_master": true,
    "slug": "product-64-3339",
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

    ],
    "videos": [

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
      "taxon_id": 59,
      "position": 1,
      "taxon": {
        "id": 59,
        "name": "Dresses",
        "pretty_name": "Category -> Clothing -> Girl -> Dresses",
        "permalink": "category/clothing/girl/dresses",
        "parent_id": 58,
        "taxonomy_id": 17,
        "url_override": null,
        "description": "Dresses",
        "icon": "/assets/default_taxon.png"
      }
    }
  ]
}
```



## Fetch all products


### Request

#### Endpoint

```plaintext
GET /api/products
Host: example.org
Cookie: 
```

`GET /api/products`

#### Parameters



| Name | Description |
|:-----|:------------|
| simple  | Any value passed here will trigger the simple view |
| ids  | Comma separated string of product ids |
| q[name_cont]  | Search by anything accessible through ransack |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Date: Tue, 13 Jul 2021 11:58:38 GMT
Surrogate-Control: max-age=900
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;f2244b0049d08fa9540e8058c1b827b8&quot;
X-Request-Id: 0737e4e6-0866-48c5-99d1-8e5e37d63643
X-Runtime: 0.132115
Vary: Origin
Content-Length: 1283
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
      "id": 58,
      "name": "Product #58 - 4196",
      "description": "As seen on TV!",
      "available_on": "2020-07-13T07:58:38.539-04:00",
      "slug": "product-58-4196",
      "meta_description": null,
      "meta_keywords": null,
      "taxon_ids": [
        51
      ],
      "total_on_hand": 0,
      "meta_title": null,
      "display_price": "$0.00",
      "brand": "Maison You",
      "brand_slug": "maison-you",
      "brand_url": "/brand/maison-you",
      "brand_description": "Maison You",
      "gift_card": false,
      "concierge_only": false,
      "is_registry": false,
      "discontinued": false,
      "available": true,
      "trends": [

      ],
      "breadcrumb_taxons": [

      ],
      "has_variants": false,
      "master": {
        "id": 109,
        "name": "Product #58 - 4196",
        "sku": "SKU-109",
        "is_master": true,
        "slug": "product-58-4196",
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

        ],
        "videos": [

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
          "taxon_id": 51,
          "position": 1,
          "taxon": {
            "id": 51,
            "name": "Maison You",
            "pretty_name": "Brand -> Maison You",
            "permalink": "brand/maison-you",
            "parent_id": 50,
            "taxonomy_id": 14,
            "url_override": null,
            "description": "Maison You",
            "icon": "/assets/default_taxon.png"
          }
        }
      ]
    }
  ]
}
```



## Fetch all products, simple view


### Request

#### Endpoint

```plaintext
GET /api/products?simple=true
Host: example.org
Cookie: 
```

`GET /api/products`

#### Parameters


```json
simple: true
```


| Name | Description |
|:-----|:------------|
| simple  | Any value passed here will trigger the simple view |
| ids  | Comma separated string of product ids |
| q[name_cont]  | Search by anything accessible through ransack |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Date: Tue, 13 Jul 2021 11:58:40 GMT
Surrogate-Control: max-age=900
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;00d7668b98267efac5423fb4321b532c&quot;
X-Request-Id: 7853905f-4acd-4009-810d-074a8a2c5c73
X-Runtime: 0.083736
Vary: Origin
Content-Length: 407
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
      "id": 63,
      "name": "Product #63 - 8146",
      "slug": "product-63-8146",
      "master_id": 114,
      "display_price": "$0.00",
      "brand": "Maison You",
      "brand_slug": "maison-you",
      "brand_url": "/brand/maison-you",
      "brand_description": "Maison You",
      "gift_card": false,
      "concierge_only": false,
      "is_registry": false,
      "discontinued": false,
      "available": true,
      "images": [

      ]
    }
  ]
}
```



## Fetch multiple products by id


### Request

#### Endpoint

```plaintext
GET /api/products?ids=60%2C61%2C62
Host: example.org
Cookie: 
```

`GET /api/products`

#### Parameters


```json
ids: 60,61,62
```


| Name | Description |
|:-----|:------------|
| simple  | Any value passed here will trigger the simple view |
| ids  | Comma separated string of product ids |
| q[name_cont]  | Search by anything accessible through ransack |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Date: Tue, 13 Jul 2021 11:58:39 GMT
Surrogate-Control: max-age=900
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;1015839e257aa679ad989c38782ace9c&quot;
X-Request-Id: ed83c481-f3d4-4cda-9e18-a02715d1899d
X-Runtime: 0.224879
Vary: Origin
Content-Length: 2808
200 OK
```


```json
{
  "count": 3,
  "total_count": 3,
  "current_page": 1,
  "pages": 1,
  "per_page": 25,
  "products": [
    {
      "id": 60,
      "name": "Product #60 - 1503",
      "description": "As seen on TV!",
      "available_on": "2020-07-13T07:58:39.275-04:00",
      "slug": "product-60-1503",
      "meta_description": null,
      "meta_keywords": null,
      "taxon_ids": [

      ],
      "total_on_hand": 0,
      "meta_title": null,
      "display_price": "$0.00",
      "brand": null,
      "brand_slug": null,
      "brand_url": null,
      "brand_description": null,
      "gift_card": false,
      "concierge_only": false,
      "is_registry": false,
      "discontinued": false,
      "available": true,
      "trends": [

      ],
      "breadcrumb_taxons": [

      ],
      "has_variants": false,
      "master": {
        "id": 111,
        "name": "Product #60 - 1503",
        "sku": "SKU-111",
        "is_master": true,
        "slug": "product-60-1503",
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

        ],
        "videos": [

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
    },
    {
      "id": 61,
      "name": "Product #61 - 3162",
      "description": "As seen on TV!",
      "available_on": "2020-07-13T07:58:39.426-04:00",
      "slug": "product-61-3162",
      "meta_description": null,
      "meta_keywords": null,
      "taxon_ids": [

      ],
      "total_on_hand": 0,
      "meta_title": null,
      "display_price": "$0.00",
      "brand": null,
      "brand_slug": null,
      "brand_url": null,
      "brand_description": null,
      "gift_card": false,
      "concierge_only": false,
      "is_registry": false,
      "discontinued": false,
      "available": true,
      "trends": [

      ],
      "breadcrumb_taxons": [

      ],
      "has_variants": false,
      "master": {
        "id": 112,
        "name": "Product #61 - 3162",
        "sku": "SKU-112",
        "is_master": true,
        "slug": "product-61-3162",
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

        ],
        "videos": [

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
    },
    {
      "id": 62,
      "name": "Product #62 - 9624",
      "description": "As seen on TV!",
      "available_on": "2020-07-13T07:58:39.577-04:00",
      "slug": "product-62-9624",
      "meta_description": null,
      "meta_keywords": null,
      "taxon_ids": [

      ],
      "total_on_hand": 0,
      "meta_title": null,
      "display_price": "$0.00",
      "brand": null,
      "brand_slug": null,
      "brand_url": null,
      "brand_description": null,
      "gift_card": false,
      "concierge_only": false,
      "is_registry": false,
      "discontinued": false,
      "available": true,
      "trends": [

      ],
      "breadcrumb_taxons": [

      ],
      "has_variants": false,
      "master": {
        "id": 113,
        "name": "Product #62 - 9624",
        "sku": "SKU-113",
        "is_master": true,
        "slug": "product-62-9624",
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

        ],
        "videos": [

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



## Fetch products by taxon id


### Request

#### Endpoint

```plaintext
GET /api/taxons/products?id=46
Host: example.org
Cookie: 
```

`GET /api/taxons/products`

#### Parameters


```json
id: 46
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
ETag: W/&quot;f4e3fb91ff4e89d4c1bd48d31304598f&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 8cfa530b-8786-45c5-9269-d915e74bd94a
X-Runtime: 0.135046
Vary: Origin
Content-Length: 1306
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
      "id": 55,
      "name": "Product #55 - 904",
      "description": "As seen on TV!",
      "available_on": "2020-07-13T07:58:37.490-04:00",
      "slug": "product-55-904",
      "meta_description": null,
      "meta_keywords": null,
      "taxon_ids": [
        46
      ],
      "total_on_hand": 0,
      "meta_title": null,
      "display_price": "$0.00",
      "brand": "Ruby on Rails - 7",
      "brand_slug": "ruby-on-rails-7",
      "brand_url": "/ruby-on-rails-7",
      "brand_description": "Ruby on Rails - 7",
      "gift_card": false,
      "concierge_only": false,
      "is_registry": false,
      "discontinued": false,
      "available": true,
      "trends": [

      ],
      "breadcrumb_taxons": [

      ],
      "has_variants": false,
      "master": {
        "id": 106,
        "name": "Product #55 - 904",
        "sku": "SKU-106",
        "is_master": true,
        "slug": "product-55-904",
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

        ],
        "videos": [

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
          "taxon_id": 46,
          "position": 1,
          "taxon": {
            "id": 46,
            "name": "Ruby on Rails - 7",
            "pretty_name": "Ruby on Rails - 7",
            "permalink": "ruby-on-rails-7",
            "parent_id": null,
            "taxonomy_id": 12,
            "url_override": null,
            "description": "Ruby on Rails - 7",
            "icon": "/assets/default_taxon.png"
          }
        }
      ]
    }
  ]
}
```



## Fetch products by taxon permalink


### Request

#### Endpoint

```plaintext
GET /api/taxons/products?permalink=ruby-on-rails-8
Host: example.org
Cookie: 
```

`GET /api/taxons/products`

#### Parameters


```json
permalink: ruby-on-rails-8
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
ETag: W/&quot;4d81b781b69eae79f4dea2c9edf0149d&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 23f77172-bb3a-46d9-b81f-e1822baf54fe
X-Runtime: 0.124006
Vary: Origin
Content-Length: 1310
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
      "id": 57,
      "name": "Product #57 - 1706",
      "description": "As seen on TV!",
      "available_on": "2020-07-13T07:58:38.157-04:00",
      "slug": "product-57-1706",
      "meta_description": null,
      "meta_keywords": null,
      "taxon_ids": [
        49
      ],
      "total_on_hand": 0,
      "meta_title": null,
      "display_price": "$0.00",
      "brand": "Ruby on Rails - 8",
      "brand_slug": "ruby-on-rails-8",
      "brand_url": "/ruby-on-rails-8",
      "brand_description": "Ruby on Rails - 8",
      "gift_card": false,
      "concierge_only": false,
      "is_registry": false,
      "discontinued": false,
      "available": true,
      "trends": [

      ],
      "breadcrumb_taxons": [

      ],
      "has_variants": false,
      "master": {
        "id": 108,
        "name": "Product #57 - 1706",
        "sku": "SKU-108",
        "is_master": true,
        "slug": "product-57-1706",
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

        ],
        "videos": [

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
          "taxon_id": 49,
          "position": 1,
          "taxon": {
            "id": 49,
            "name": "Ruby on Rails - 8",
            "pretty_name": "Ruby on Rails - 8",
            "permalink": "ruby-on-rails-8",
            "parent_id": null,
            "taxonomy_id": 13,
            "url_override": null,
            "description": "Ruby on Rails - 8",
            "icon": "/assets/default_taxon.png"
          }
        }
      ]
    }
  ]
}
```



## Get all products info


### Request

#### Endpoint

```plaintext
GET /api/sitemap/products
Accept: application/json
Authorizat IO N: Bearer 55db508ef019bc27b33b3f9f973eb5095fb64fc175188bfb
Host: example.org
Cookie: 
```

`GET /api/sitemap/products`

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
ETag: W/&quot;4f53cda18c2baa0c0354bb5f9a3ecbe5&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 7b868e40-773f-4a3d-bfa7-98526ceb5add
X-Runtime: 0.049873
Vary: Origin
Content-Length: 2
200 OK
```


```json
[

]
```



## Product not found


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
X-Request-Id: e9ff1cf6-e6d3-4303-be28-b72256444d96
X-Runtime: 0.045179
Vary: Origin
Content-Length: 65
404 Not Found
```


```json
{
  "error": "The resource you were looking for could not be found."
}
```



# Recently Viewed Products

Store a recently viewed variant with a logged in user or session token

## Get all recently viewed products


### Request

#### Endpoint

```plaintext
GET /api/recently_viewed?recently_viewed[session_id]=9xo23so3r8b3vksz61tpwvr7mq9m9hi9ldyc59jld8fzew8o0gl8f0f8rs2mhehdwymfebt4sxmbjrxcn4rcmmptl4sqxv6s79qxgeos2z41o5qwudm4r9zxu5o15roy0vufh062wm2j5dmappdc883ju2od4igptji7caez1itcs3bq08tcb83p8lmfwfb98seeuitj2g6toveyu4z0x9rsn77u312xf03us6hgxr0dpwzrq46fxm1mbcc8pvx
Accept: application/json
Authorizat IO N: Bearer 5af347b397a2545e259af2e74217113de846cf8d376c162e
Host: example.org
Cookie: 
```

`GET /api/recently_viewed`

#### Parameters


```json
recently_viewed: {&quot;session_id&quot;=&gt;&quot;9xo23so3r8b3vksz61tpwvr7mq9m9hi9ldyc59jld8fzew8o0gl8f0f8rs2mhehdwymfebt4sxmbjrxcn4rcmmptl4sqxv6s79qxgeos2z41o5qwudm4r9zxu5o15roy0vufh062wm2j5dmappdc883ju2od4igptji7caez1itcs3bq08tcb83p8lmfwfb98seeuitj2g6toveyu4z0x9rsn77u312xf03us6hgxr0dpwzrq46fxm1mbcc8pvx&quot;}
```


| Name | Description |
|:-----|:------------|
| recently_viewed[session_id]  | A session id is required unless providing an Auth token |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
ETag: W/&quot;df9a7bb07acffab8938fbf163e83ce32&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: ec36a0d2-01dc-428a-bad4-33ceebb1be39
X-Runtime: 0.031486
Vary: Origin
Content-Length: 119
200 OK
```


```json
[
  {
    "at": "2021-07-13T07:58:34.197-04:00",
    "variant_id": "var1"
  },
  {
    "at": "2021-07-13T08:03:34.197-04:00",
    "variant_id": "var2"
  }
]
```



## Store a recently viewed variant


### Request

#### Endpoint

```plaintext
POST /api/recently_viewed
Accept: application/json
Authorizat IO N: Bearer 888920c3e25374c8a44db4be1698e54944b9d2f088a3c4f3
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/recently_viewed`

#### Parameters


```json
recently_viewed[session_id]=pzbnjjhvd1du4wiqmmdui1a0akjfmgsr6dgi7tra058e61ez6x2h16a6f0zkfaj9gxosjao7x6jn5jlcuzswysz0bptysqmwo1s8ouozpxp1x6uflnhuocv00f8ordwt6oe9mb6slojaamijiek9237af8lfbixewx76562q9agmt6ei24pm6tyb30abnz4wkij4olun7ud80fl0m4jd9phswguv2fhou07bl66edq99fi8o0ud8g29pq5bl93s&recently_viewed[variant_id]=foo
```


| Name | Description |
|:-----|:------------|
| recently_viewed[session_id]  | Either a logged in user or a session id are required |
| recently_viewed[variant_id] *required* | Recently viewed variant |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Cache-Control: no-cache
X-Request-Id: afb27ed4-e1e8-4943-8e8e-742dc6e5a996
X-Runtime: 0.039193
Vary: Origin
204 No Content
```




# Return Authorizations

Get user return authorizations

## Can get another user&#39;s return authorization


### Request

#### Endpoint

```plaintext
GET /api/returns/RA451502307
Authorizat IO N: Bearer bb274da0535e91bc0c6d75ff1adfe9c8f06c776db4befaa4
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
ETag: W/&quot;858100745bf2cfba783cdd12bcf8b2a2&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 4d10821d-4b6f-44af-846b-920b588739f5
X-Runtime: 0.121954
Vary: Origin
Content-Length: 3119
200 OK
```


```json
{
  "id": 5,
  "number": "RA451502307",
  "state": "authorized",
  "order_id": 38,
  "memo": "Items were broken",
  "created_at": "2021-07-13T07:59:18.844-04:00",
  "updated_at": "2021-07-13T07:59:18.844-04:00",
  "amount": "10.0",
  "reason": {
    "id": 8,
    "name": "Defect #7",
    "active": true,
    "mutable": true,
    "created_at": "2021-07-13T07:59:18.822-04:00",
    "updated_at": "2021-07-13T07:59:18.822-04:00",
    "mirakl_code": null
  },
  "order": {
    "id": 38,
    "number": "M054292063",
    "item_total": "10.0",
    "total": "110.0",
    "state": "complete",
    "adjustment_total": "0.0",
    "user_id": 107,
    "completed_at": "2021-07-13T07:59:18.560-04:00",
    "bill_address_id": 68,
    "ship_address_id": 69,
    "payment_total": "110.0",
    "shipment_state": "shipped",
    "payment_state": "paid",
    "email": "email105@example.com",
    "special_instructions": null,
    "created_at": "2021-07-13T07:59:18.389-04:00",
    "updated_at": "2021-07-13T07:59:18.931-04:00",
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
    "guest_token": "YubN7HgPR-MYtVA0R6z3VQ",
    "canceled_at": null,
    "canceler_id": null,
    "store_id": 37,
    "approver_name": null,
    "frontend_viewable": true,
    "migrated": false,
    "is_gift": false,
    "gift_email": null,
    "gift_message": null,
    "gift_card_total": "0.0",
    "gift_confirmation_delivered_at": null,
    "use_store_credits": false,
    "first_order": false,
    "maisonette_customer_id": "fcc9b07e-0ae6-4463-a25e-3deea530ddaf"
  },
  "ship_address": {
    "id": 69,
    "firstname": "John",
    "lastname": "Smith",
    "full_name": "John Smith",
    "address1": "A Different Road",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10068",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 59,
    "country_iso": "US",
    "state_id": 59,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 59,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 59,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 59
    }
  },
  "bill_address": {
    "id": 68,
    "firstname": "John",
    "lastname": "Smith",
    "full_name": "John Smith",
    "address1": "PO Box 1337",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10067",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 59,
    "country_iso": "US",
    "state_id": 59,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 59,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 59,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 59
    }
  },
  "return_items": [
    {
      "name": "Product #101 - 5698",
      "brand": null,
      "brand_slug": null,
      "image": null,
      "product_slug": "product-101-5698",
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
        "id": 21,
        "name": "Credit Card"
      },
      "source": {
        "id": 5,
        "month": "12",
        "year": "2022",
        "cc_type": null,
        "last_digits": "1111",
        "name": "Spree Commerce",
        "gateway_customer_profile_id": "BGS-554330",
        "gateway_payment_profile_id": null
      }
    }
  ],
  "refunded_total": "0.0",
  "subtotals": {
    "order_total": "110.0",
    "item_total": "10.0",
    "shipments_total": "100.0",
    "line_item_promotion_totals": [

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
Authorizat IO N: Bearer 68f1cceb08483265f79178820062ccd1b195b413454902cf
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
ETag: W/&quot;c9150360f45a22ed8551491665ebbd90&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: b9190e9a-1c5b-4410-9257-607f0e893314
X-Runtime: 0.063393
Vary: Origin
Content-Length: 169
200 OK
```


```json
{
  "return_authorizations": [
    {
      "number": "RA144732854",
      "created_at": "2021-07-13T07:59:15.013-04:00",
      "return_amount": "10.0",
      "order_number": "M472943149",
      "state": "authorized"
    }
  ]
}
```



## returns a 200


### Request

#### Endpoint

```plaintext
GET /api/returns/RA221283638
Authorizat IO N: Bearer 999c1531f994c77e5038e48223ef0f5c121c6495c15ae6bb
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
ETag: W/&quot;5ba77fbf60c8f01fc9342e58092c9497&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: f7c83fd6-6327-4182-9846-c4220e578913
X-Runtime: 0.163958
Vary: Origin
Content-Length: 3040
200 OK
```


```json
{
  "id": 3,
  "number": "RA221283638",
  "state": "authorized",
  "order_id": 36,
  "memo": "Items were broken",
  "created_at": "2021-07-13T07:59:16.341-04:00",
  "updated_at": "2021-07-13T07:59:16.341-04:00",
  "amount": "10.0",
  "reason": {
    "id": 4,
    "name": "Defect #3",
    "active": true,
    "mutable": true,
    "created_at": "2021-07-13T07:59:16.313-04:00",
    "updated_at": "2021-07-13T07:59:16.313-04:00",
    "mirakl_code": null
  },
  "order": {
    "id": 36,
    "number": "M544192632",
    "item_total": "10.0",
    "total": "110.0",
    "state": "complete",
    "adjustment_total": "0.0",
    "user_id": 104,
    "completed_at": "2021-07-13T07:59:16.107-04:00",
    "bill_address_id": 64,
    "ship_address_id": 65,
    "payment_total": "110.0",
    "shipment_state": "shipped",
    "payment_state": "paid",
    "email": "email102@example.com",
    "special_instructions": null,
    "created_at": "2021-07-13T07:59:15.893-04:00",
    "updated_at": "2021-07-13T07:59:16.487-04:00",
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
    "guest_token": "di3V0CfDl3vR_HT-iFP50g",
    "canceled_at": null,
    "canceler_id": null,
    "store_id": 35,
    "approver_name": null,
    "frontend_viewable": true,
    "migrated": false,
    "is_gift": false,
    "gift_email": null,
    "gift_message": null,
    "gift_card_total": "0.0",
    "gift_confirmation_delivered_at": null,
    "use_store_credits": false,
    "first_order": false,
    "maisonette_customer_id": "adf9470e-2d72-4de8-b0dd-db6fa19d323b"
  },
  "ship_address": {
    "id": 65,
    "firstname": "John",
    "lastname": "Smith",
    "full_name": "John Smith",
    "address1": "A Different Road",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10064",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 57,
    "country_iso": "US",
    "state_id": 57,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 57,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 57,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 57
    }
  },
  "bill_address": {
    "id": 64,
    "firstname": "John",
    "lastname": "Smith",
    "full_name": "John Smith",
    "address1": "PO Box 1337",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10063",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 57,
    "country_iso": "US",
    "state_id": 57,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 57,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 57,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 57
    }
  },
  "return_items": [
    {
      "name": "Product #99 - 4114",
      "brand": null,
      "brand_slug": null,
      "image": null,
      "product_slug": "product-99-4114",
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
        "id": 17,
        "name": "Credit Card"
      },
      "source": {
        "id": 3,
        "month": "12",
        "year": "2022",
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
    "line_item_promotion_totals": [

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
GET /api/returns/RA815377076
Authorizat IO N: Bearer 0b0dd05119bcec06d37cf6e897b650d74eca51c1fa3d0d90
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
X-Request-Id: 8d874dbb-fb8b-4259-86a6-a290654374dc
X-Runtime: 0.040063
Vary: Origin
Content-Length: 65
404 Not Found
```


```json
{
  "error": "The resource you were looking for could not be found."
}
```



# Stock Requests

Create a new stock request, accessible without an api key

## Create a stock request


### Request

#### Endpoint

```plaintext
POST /api/stock_requests
Accept: application/json
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/stock_requests`

#### Parameters


```json
stock_request[email]=selena%40little.ca&stock_request[variant_id]=99
```


| Name | Description |
|:-----|:------------|
| stock_request[email] *required* | Stock request email |
| stock_request[variant_id] *required* | Stock request variant |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json
Cache-Control: no-cache
X-Request-Id: 83d8ec95-e348-40cd-ab02-0d1b7d1601ff
X-Runtime: 0.045187
Vary: Origin
Content-Length: 0
201 Created
```




## With a bad email


### Request

#### Endpoint

```plaintext
POST /api/stock_requests
Accept: application/json
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/stock_requests`

#### Parameters


```json
stock_request[email]=foo&stock_request[variant_id]=97
```


| Name | Description |
|:-----|:------------|
| stock_request[email] *required* | Stock request email |
| stock_request[variant_id] *required* | Stock request variant |



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
X-Request-Id: 5a2036ff-8bfc-46e7-b7a0-0285502db9b5
X-Runtime: 0.033291
Vary: Origin
Content-Length: 48
422 Unprocessable Entity
```


```json
{
  "success": false,
  "message": [
    "Email is invalid"
  ]
}
```



## With a duplicate email and product


### Request

#### Endpoint

```plaintext
POST /api/stock_requests
Accept: application/json
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/stock_requests`

#### Parameters


```json
stock_request[email]=michel%40schinnerleannon.ca&stock_request[variant_id]=95
```


| Name | Description |
|:-----|:------------|
| stock_request[email] *required* | Stock request email |
| stock_request[variant_id] *required* | Stock request variant |



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
X-Request-Id: 5626bf75-da8a-4859-bef7-38ce777e2029
X-Runtime: 0.043948
Vary: Origin
Content-Length: 80
422 Unprocessable Entity
```


```json
{
  "success": false,
  "message": "Email is already on the waitlist for this product."
}
```



# Store Credits API

Get user store_credits and current account balance for the current user

## returns a 200


### Request

#### Endpoint

```plaintext
GET api/store_credits/mine
Authorizat IO N: Bearer 8b29bbe63e26b818fb9debc7745bfaf48c34faf992004f10
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
ETag: W/&quot;3bad46f5275febaa4a4ff99a2d79131a&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 78e0fa13-1e40-4886-b46f-fb1c8c0c64ec
X-Runtime: 0.053624
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
      "created_at": "2021-07-13T07:58:34.390-04:00"
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

Get all subscribers, only accessible to admin users

## Create a subscriber


### Request

#### Endpoint

```plaintext
POST /api/subscribers
Accept: application/json
Authorizat IO N: Bearer 
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/subscribers`

#### Parameters


```json
subscriber[email]=laverna_hintz%40gislason.name&subscriber[first_name]=Gretta&subscriber[last_name]=Stark&subscriber[source]=Modi+suscipit+dolor+aut+ut+et+quam+qui.&subscriber[list_id]=xx3xrg
```


| Name | Description |
|:-----|:------------|
| subscriber[email] *required* | Subscriber email |
| subscriber[first_name]  | Subscriber first name |
| subscriber[last_name]  | Subscriber last name |
| subscriber[source]  | Subscriber source |
| subscriber[list_id]  | If not provided, spree will use the default Klaviyo list id |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
ETag: W/&quot;84ac4b97fc6d8d7533d0b64e9f1276cd&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 2cb40924-edc1-4426-8220-4a0fc366348d
X-Runtime: 0.071026
Vary: Origin
Content-Length: 253
201 Created
```


```json
{
  "id": 5,
  "user_id": null,
  "list_id": "xx3xrg",
  "email": "laverna_hintz@gislason.name",
  "first_name": "Gretta",
  "last_name": "Stark",
  "source": "Modi suscipit dolor aut ut et quam qui.",
  "phone": null,
  "status": "subscribed",
  "created_at": "2021-07-13T07:58:36.958-04:00"
}
```



## Create a subscriber for the associated user


### Request

#### Endpoint

```plaintext
POST /api/subscribers
Accept: application/json
Authorizat IO N: Bearer 8d1ff90b15f7fe15bab21121d0d776af21549142da688404
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/subscribers`

#### Parameters


```json
subscriber[email]&subscriber[first_name]=Tamesha&subscriber[last_name]=Blick&subscriber[source]=Possimus+quasi+ut+fugit+architecto+unde.&subscriber[list_id]=adul0g
```


| Name | Description |
|:-----|:------------|
| subscriber[email] *required* | Subscriber email |
| subscriber[first_name]  | Subscriber first name |
| subscriber[last_name]  | Subscriber last name |
| subscriber[source]  | Subscriber source |
| subscriber[list_id]  | If not provided, spree will use the default Klaviyo list id |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
ETag: W/&quot;51916f36fa2dd5fc18333843ad111ff4&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 2b953293-c790-47b8-9df6-93b7943caadf
X-Runtime: 0.040084
Vary: Origin
Content-Length: 245
201 Created
```


```json
{
  "id": 6,
  "user_id": 62,
  "list_id": "adul0g",
  "email": "email62@example.com",
  "first_name": "Tamesha",
  "last_name": "Blick",
  "source": "Possimus quasi ut fugit architecto unde.",
  "phone": null,
  "status": "subscribed",
  "created_at": "2021-07-13T07:58:37.020-04:00"
}
```



## Get all subscribers


### Request

#### Endpoint

```plaintext
GET /api/subscribers
Accept: application/json
Authorizat IO N: Bearer 746aa60f442e5f7a0fc198e94891ad24039910f170e65ea3
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
ETag: W/&quot;a4764f593700128b060ea93568061a3d&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 6e8321fd-5d90-4a01-81ac-ba4c34310854
X-Runtime: 0.049542
Vary: Origin
Content-Length: 762
200 OK
```


```json
{
  "subscribers": [
    {
      "id": 1,
      "user_id": null,
      "list_id": "2a2psl",
      "email": "dominique_koepp@kreiger.info",
      "first_name": "Carissa",
      "last_name": "Dibbert",
      "source": "Registration",
      "phone": null,
      "status": "subscribed",
      "created_at": "2021-07-13T07:58:36.711-04:00"
    },
    {
      "id": 2,
      "user_id": null,
      "list_id": "c2t2n1",
      "email": "yoshiko@jast.biz",
      "first_name": "Cayla",
      "last_name": "Schaden",
      "source": "Registration",
      "phone": null,
      "status": "subscribed",
      "created_at": "2021-07-13T07:58:36.720-04:00"
    },
    {
      "id": 3,
      "user_id": null,
      "list_id": "kw7vgl",
      "email": "lamar.ziemann@vandervort.co.uk",
      "first_name": "Jamaal",
      "last_name": "Zieme",
      "source": "Registration",
      "phone": null,
      "status": "subscribed",
      "created_at": "2021-07-13T07:58:36.727-04:00"
    }
  ],
  "count": 3,
  "total_count": 3,
  "current_page": 1,
  "pages": 1,
  "per_page": 25
}
```



## Update a subscriber


### Request

#### Endpoint

```plaintext
PATCH /api/subscribers/4
Accept: application/json
Authorizat IO N: Bearer e2b00a859046743d0490dc577d9046751f15412143c8621e
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/subscribers/:id`

#### Parameters


```json
subscriber[source]=Minus+velit+qui+sed+quo+quia+totam+quia.
```


| Name | Description |
|:-----|:------------|
| subscriber[email] *required* | Subscriber email |
| subscriber[first_name]  | Subscriber first name |
| subscriber[last_name]  | Subscriber last name |
| subscriber[source]  | Subscriber source |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
ETag: W/&quot;4704658892c182fb06ef74f8e0ea07bf&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: fd703279-c4b9-4637-9fbd-53550a79f55e
X-Runtime: 0.050085
Vary: Origin
Content-Length: 256
200 OK
```


```json
{
  "id": 4,
  "user_id": 61,
  "list_id": "k0uha9",
  "email": "email61@example.com",
  "first_name": "Whitney",
  "last_name": "Kulas",
  "source": "Minus velit qui sed quo quia totam quia.",
  "phone": null,
  "status": "subscribed_and_synced",
  "created_at": "2021-07-13T07:58:36.831-04:00"
}
```



## unsubscribe a known subscriber


### Request

#### Endpoint

```plaintext
DELETE /api/subscribers
Accept: application/json
Authorizat IO N: Bearer a1208054997cb95e869f61aa47d60951689707c74b34cc75
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`DELETE /api/subscribers`

#### Parameters


```json
subscriber[email]=email63%40example.com&subscriber[list_id]=c35qk1
```


| Name | Description |
|:-----|:------------|
| subscriber[email]  | Subscriber email |
| subscriber[list_id]  | If not provided, spree will use the default Klaviyo list id |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json
Cache-Control: no-cache
X-Request-Id: f4eea4e3-b606-44ca-b01f-b674f66a9f74
X-Runtime: 0.042030
Vary: Origin
Content-Length: 0
200 OK
```




## unsubscribe an email that doesn&#39;t exist


### Request

#### Endpoint

```plaintext
DELETE /api/subscribers
Accept: application/json
Authorizat IO N: Bearer d1ec98ba6ab0b1dbb91e92f5c69cfca63758c4d3a289d2e9
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`DELETE /api/subscribers`

#### Parameters


```json
subscriber[email]=stephaine%40koepp.biz&subscriber[list_id]=v1ujws
```


| Name | Description |
|:-----|:------------|
| subscriber[email]  | Subscriber email |
| subscriber[list_id]  | If not provided, spree will use the default Klaviyo list id |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Cache-Control: no-cache
X-Request-Id: 520a79a1-55a1-4a2f-8d6f-8d8064e2cbbb
X-Runtime: 0.034549
Vary: Origin
204 No Content
```




# Taxons

Get taxons info

## Get all taxons info


### Request

#### Endpoint

```plaintext
GET /api/sitemap/taxons
Accept: application/json
Authorizat IO N: Bearer c1ee0659e6ca0892f2e6c0d568e4bd0329414accebfc7389
Host: example.org
Cookie: 
```

`GET /api/sitemap/taxons`

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
ETag: W/&quot;4f53cda18c2baa0c0354bb5f9a3ecbe5&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: a73b7942-8887-4a90-a8bd-09a7a28f4645
X-Runtime: 0.046490
Vary: Origin
Content-Length: 2
200 OK
```


```json
[

]
```



# Taxons API

Return brand taxons that have products in stock with the provided category taxon

## Get all taxons


### Request

#### Endpoint

```plaintext
GET /api/taxons
Accept: application/json
Host: example.org
Cookie: 
```

`GET /api/taxons`

#### Parameters



| Name | Description |
|:-----|:------------|
| without_children  | Use this parameter to disable returning descendant taxons |
| q[purchasable_brands]  | Use this parameter to only return brands with purchasable products |
| q[taxonomy_name_eq]  | Optional parameter to filter by taxonomy name |
| q[name_eq]  | Use this parameter to query taxons by name |
| q[permalink_eq]  | Use this parameter to query taxons by permalink |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
ETag: W/&quot;aa9e8dc6b677fdf2fc2fca49e038fb85&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 96d834e5-80c8-4b17-be12-a31f5972f9c9
X-Runtime: 0.085588
Vary: Origin
Content-Length: 4435
200 OK
```


```json
{
  "count": 11,
  "total_count": 11,
  "current_page": 1,
  "pages": 1,
  "per_page": 500,
  "taxons": [
    {
      "id": 9,
      "name": "Category",
      "pretty_name": "Category",
      "permalink": "category",
      "parent_id": null,
      "taxonomy_id": 5,
      "url_override": null,
      "description": "Category",
      "icon": "/assets/default_taxon.png",
      "taxons": [
        {
          "id": 10,
          "name": "Kids",
          "pretty_name": "Category -> Kids",
          "permalink": "category/kids",
          "parent_id": 9,
          "taxonomy_id": 5,
          "url_override": null
        }
      ]
    },
    {
      "id": 10,
      "name": "Kids",
      "pretty_name": "Category -> Kids",
      "permalink": "category/kids",
      "parent_id": 9,
      "taxonomy_id": 5,
      "url_override": null,
      "description": "Kids",
      "icon": "/assets/default_taxon.png",
      "taxons": [
        {
          "id": 11,
          "name": "Boys",
          "pretty_name": "Category -> Kids -> Boys",
          "permalink": "category/kids/boys",
          "parent_id": 10,
          "taxonomy_id": 5,
          "url_override": null
        },
        {
          "id": 14,
          "name": "Girls",
          "pretty_name": "Category -> Kids -> Girls",
          "permalink": "category/kids/girls",
          "parent_id": 10,
          "taxonomy_id": 5,
          "url_override": null
        }
      ]
    },
    {
      "id": 11,
      "name": "Boys",
      "pretty_name": "Category -> Kids -> Boys",
      "permalink": "category/kids/boys",
      "parent_id": 10,
      "taxonomy_id": 5,
      "url_override": null,
      "description": "Boys",
      "icon": "/assets/default_taxon.png",
      "taxons": [
        {
          "id": 12,
          "name": "Boys Tops",
          "pretty_name": "Category -> Kids -> Boys -> Boys Tops",
          "permalink": "category/kids/boys/boys-tops",
          "parent_id": 11,
          "taxonomy_id": 5,
          "url_override": null
        }
      ]
    },
    {
      "id": 12,
      "name": "Boys Tops",
      "pretty_name": "Category -> Kids -> Boys -> Boys Tops",
      "permalink": "category/kids/boys/boys-tops",
      "parent_id": 11,
      "taxonomy_id": 5,
      "url_override": null,
      "description": "Boys Tops",
      "icon": "/assets/default_taxon.png",
      "taxons": [
        {
          "id": 13,
          "name": "Boys Shirts",
          "pretty_name": "Category -> Kids -> Boys -> Boys Tops -> Boys Shirts",
          "permalink": "category/kids/boys/boys-tops/boys-shirts",
          "parent_id": 12,
          "taxonomy_id": 5,
          "url_override": null
        }
      ]
    },
    {
      "id": 13,
      "name": "Boys Shirts",
      "pretty_name": "Category -> Kids -> Boys -> Boys Tops -> Boys Shirts",
      "permalink": "category/kids/boys/boys-tops/boys-shirts",
      "parent_id": 12,
      "taxonomy_id": 5,
      "url_override": null,
      "description": "Boys Shirts",
      "icon": "/assets/default_taxon.png",
      "taxons": [

      ]
    },
    {
      "id": 14,
      "name": "Girls",
      "pretty_name": "Category -> Kids -> Girls",
      "permalink": "category/kids/girls",
      "parent_id": 10,
      "taxonomy_id": 5,
      "url_override": null,
      "description": "Girls",
      "icon": "/assets/default_taxon.png",
      "taxons": [
        {
          "id": 15,
          "name": "Girls Tops",
          "pretty_name": "Category -> Kids -> Girls -> Girls Tops",
          "permalink": "category/kids/girls/girls-tops",
          "parent_id": 14,
          "taxonomy_id": 5,
          "url_override": null
        }
      ]
    },
    {
      "id": 15,
      "name": "Girls Tops",
      "pretty_name": "Category -> Kids -> Girls -> Girls Tops",
      "permalink": "category/kids/girls/girls-tops",
      "parent_id": 14,
      "taxonomy_id": 5,
      "url_override": null,
      "description": "Girls Tops",
      "icon": "/assets/default_taxon.png",
      "taxons": [
        {
          "id": 16,
          "name": "Girls Shirts",
          "pretty_name": "Category -> Kids -> Girls -> Girls Tops -> Girls Shirts",
          "permalink": "category/kids/girls/girls-tops/girls-shirts",
          "parent_id": 15,
          "taxonomy_id": 5,
          "url_override": null
        }
      ]
    },
    {
      "id": 16,
      "name": "Girls Shirts",
      "pretty_name": "Category -> Kids -> Girls -> Girls Tops -> Girls Shirts",
      "permalink": "category/kids/girls/girls-tops/girls-shirts",
      "parent_id": 15,
      "taxonomy_id": 5,
      "url_override": null,
      "description": "Girls Shirts",
      "icon": "/assets/default_taxon.png",
      "taxons": [

      ]
    },
    {
      "id": 17,
      "name": "Brand",
      "pretty_name": "Brand",
      "permalink": "brand",
      "parent_id": null,
      "taxonomy_id": 6,
      "url_override": null,
      "description": "Brand",
      "icon": "/assets/default_taxon.png",
      "taxons": [
        {
          "id": 18,
          "name": "Ruby on Rails - 1",
          "pretty_name": "Brand -> Ruby on Rails - 1",
          "permalink": "brand/ruby-on-rails-1",
          "parent_id": 17,
          "taxonomy_id": 6,
          "url_override": null
        },
        {
          "id": 19,
          "name": "Ruby on Rails - 2",
          "pretty_name": "Brand -> Ruby on Rails - 2",
          "permalink": "brand/ruby-on-rails-2",
          "parent_id": 17,
          "taxonomy_id": 6,
          "url_override": null
        }
      ]
    },
    {
      "id": 18,
      "name": "Ruby on Rails - 1",
      "pretty_name": "Brand -> Ruby on Rails - 1",
      "permalink": "brand/ruby-on-rails-1",
      "parent_id": 17,
      "taxonomy_id": 6,
      "url_override": null,
      "description": "Ruby on Rails - 1",
      "icon": "/assets/default_taxon.png",
      "taxons": [

      ]
    },
    {
      "id": 19,
      "name": "Ruby on Rails - 2",
      "pretty_name": "Brand -> Ruby on Rails - 2",
      "permalink": "brand/ruby-on-rails-2",
      "parent_id": 17,
      "taxonomy_id": 6,
      "url_override": null,
      "description": "Ruby on Rails - 2",
      "icon": "/assets/default_taxon.png",
      "taxons": [

      ]
    }
  ]
}
```



## Get all taxons from a specific taxonomy


### Request

#### Endpoint

```plaintext
GET /api/taxons?without_children=true&amp;q[taxonomy_name_eq]=Brand
Accept: application/json
Host: example.org
Cookie: 
```

`GET /api/taxons`

#### Parameters


```json
without_children: true
q: {&quot;taxonomy_name_eq&quot;=&gt;&quot;Brand&quot;}
```


| Name | Description |
|:-----|:------------|
| without_children  | Use this parameter to disable returning descendant taxons |
| q[purchasable_brands]  | Use this parameter to only return brands with purchasable products |
| q[taxonomy_name_eq]  | Optional parameter to filter by taxonomy name |
| q[name_eq]  | Use this parameter to query taxons by name |
| q[permalink_eq]  | Use this parameter to query taxons by permalink |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
ETag: W/&quot;5e728c2328c0a3d1a3be44f75f45758d&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 653f3d5b-98ab-4d3a-aaef-5d0314e2a368
X-Runtime: 0.046686
Vary: Origin
Content-Length: 739
200 OK
```


```json
{
  "count": 3,
  "total_count": 3,
  "current_page": 1,
  "pages": 1,
  "per_page": 500,
  "taxons": [
    {
      "id": 28,
      "name": "Brand",
      "pretty_name": "Brand",
      "permalink": "brand",
      "parent_id": null,
      "taxonomy_id": 8,
      "url_override": null,
      "description": "Brand",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 29,
      "name": "Ruby on Rails - 3",
      "pretty_name": "Brand -> Ruby on Rails - 3",
      "permalink": "brand/ruby-on-rails-3",
      "parent_id": 28,
      "taxonomy_id": 8,
      "url_override": null,
      "description": "Ruby on Rails - 3",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 30,
      "name": "Ruby on Rails - 4",
      "pretty_name": "Brand -> Ruby on Rails - 4",
      "permalink": "brand/ruby-on-rails-4",
      "parent_id": 28,
      "taxonomy_id": 8,
      "url_override": null,
      "description": "Ruby on Rails - 4",
      "icon": "/assets/default_taxon.png"
    }
  ]
}
```



## Get all taxons without children


### Request

#### Endpoint

```plaintext
GET /api/taxons?without_children=true
Accept: application/json
Host: example.org
Cookie: 
```

`GET /api/taxons`

#### Parameters


```json
without_children: true
```


| Name | Description |
|:-----|:------------|
| without_children  | Use this parameter to disable returning descendant taxons |
| q[purchasable_brands]  | Use this parameter to only return brands with purchasable products |
| q[taxonomy_name_eq]  | Optional parameter to filter by taxonomy name |
| q[name_eq]  | Use this parameter to query taxons by name |
| q[permalink_eq]  | Use this parameter to query taxons by permalink |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
ETag: W/&quot;3415b34636087df85fcc8278be16e6ec&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 444b9aef-3dda-4d82-896e-d9ffe85ce40a
X-Runtime: 0.064684
Vary: Origin
Content-Length: 2662
200 OK
```


```json
{
  "count": 11,
  "total_count": 11,
  "current_page": 1,
  "pages": 1,
  "per_page": 500,
  "taxons": [
    {
      "id": 31,
      "name": "Category",
      "pretty_name": "Category",
      "permalink": "category",
      "parent_id": null,
      "taxonomy_id": 9,
      "url_override": null,
      "description": "Category",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 32,
      "name": "Kids",
      "pretty_name": "Category -> Kids",
      "permalink": "category/kids",
      "parent_id": 31,
      "taxonomy_id": 9,
      "url_override": null,
      "description": "Kids",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 33,
      "name": "Boys",
      "pretty_name": "Category -> Kids -> Boys",
      "permalink": "category/kids/boys",
      "parent_id": 32,
      "taxonomy_id": 9,
      "url_override": null,
      "description": "Boys",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 34,
      "name": "Boys Tops",
      "pretty_name": "Category -> Kids -> Boys -> Boys Tops",
      "permalink": "category/kids/boys/boys-tops",
      "parent_id": 33,
      "taxonomy_id": 9,
      "url_override": null,
      "description": "Boys Tops",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 35,
      "name": "Boys Shirts",
      "pretty_name": "Category -> Kids -> Boys -> Boys Tops -> Boys Shirts",
      "permalink": "category/kids/boys/boys-tops/boys-shirts",
      "parent_id": 34,
      "taxonomy_id": 9,
      "url_override": null,
      "description": "Boys Shirts",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 36,
      "name": "Girls",
      "pretty_name": "Category -> Kids -> Girls",
      "permalink": "category/kids/girls",
      "parent_id": 32,
      "taxonomy_id": 9,
      "url_override": null,
      "description": "Girls",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 37,
      "name": "Girls Tops",
      "pretty_name": "Category -> Kids -> Girls -> Girls Tops",
      "permalink": "category/kids/girls/girls-tops",
      "parent_id": 36,
      "taxonomy_id": 9,
      "url_override": null,
      "description": "Girls Tops",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 38,
      "name": "Girls Shirts",
      "pretty_name": "Category -> Kids -> Girls -> Girls Tops -> Girls Shirts",
      "permalink": "category/kids/girls/girls-tops/girls-shirts",
      "parent_id": 37,
      "taxonomy_id": 9,
      "url_override": null,
      "description": "Girls Shirts",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 39,
      "name": "Brand",
      "pretty_name": "Brand",
      "permalink": "brand",
      "parent_id": null,
      "taxonomy_id": 10,
      "url_override": null,
      "description": "Brand",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 40,
      "name": "Ruby on Rails - 5",
      "pretty_name": "Brand -> Ruby on Rails - 5",
      "permalink": "brand/ruby-on-rails-5",
      "parent_id": 39,
      "taxonomy_id": 10,
      "url_override": null,
      "description": "Ruby on Rails - 5",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 41,
      "name": "Ruby on Rails - 6",
      "pretty_name": "Brand -> Ruby on Rails - 6",
      "permalink": "brand/ruby-on-rails-6",
      "parent_id": 39,
      "taxonomy_id": 10,
      "url_override": null,
      "description": "Ruby on Rails - 6",
      "icon": "/assets/default_taxon.png"
    }
  ]
}
```



## Get brands by category


### Request

#### Endpoint

```plaintext
GET /api/taxons/brands_by_category/baby
Accept: application/json
Host: example.org
Cookie: 
```

`GET /api/taxons/brands_by_category/:taxon_name`

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
ETag: W/&quot;04edd7e10038636d74bdbb4b308cc3d0&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 49115691-43b6-4559-bd5b-dff8ce765e9a
X-Runtime: 0.059165
Vary: Origin
Content-Length: 587
200 OK
```


```json
[
  {
    "id": 4,
    "parent_id": 3,
    "position": 0,
    "name": "brand_x",
    "permalink": "brand/brand_x",
    "taxonomy_id": 2,
    "lft": 6,
    "rgt": 7,
    "icon_file_name": null,
    "icon_content_type": null,
    "icon_file_size": null,
    "icon_updated_at": null,
    "description": null,
    "created_at": "2021-07-13T07:58:22.841-04:00",
    "updated_at": "2021-07-13T07:58:22.961-04:00",
    "meta_title": null,
    "meta_description": null,
    "meta_keywords": null,
    "depth": 1,
    "hidden": false,
    "highlight": false,
    "header_link": false,
    "url_override": null,
    "add_flair": false,
    "track_insights": false,
    "google_product_category": null,
    "short_description": null,
    "view_all_url_override": null
  }
]
```



## Get navigation taxons


### Request

#### Endpoint

```plaintext
GET /api/taxons/nav
Accept: application/json
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
ETag: W/&quot;66130e2347f24ddafc1d74d3011d6aab&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: cbda594e-ea1c-4f60-aec5-f719603d1c7d
X-Runtime: 0.038856
Vary: Origin
Content-Length: 199
200 OK
```


```json
[
  {
    "id": 43,
    "name": "Kids",
    "navigation_url": "/shop/kids",
    "parent_id": 42,
    "lft": 2,
    "depth": 1,
    "highlight": false,
    "header_link": false,
    "add_flair": false,
    "view_all_url_override": null,
    "icon_url_original": false
  }
]
```



## Get purchasable brands


### Request

#### Endpoint

```plaintext
GET /api/taxons/brands
Accept: application/json
Host: example.org
Cookie: 
```

`GET /api/taxons/brands`

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
ETag: W/&quot;4648d76fe50b888200701501bb0d38c3&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 6dac6473-9785-4b33-a214-8371c7fc7f49
X-Runtime: 0.046390
Vary: Origin
Content-Length: 587
200 OK
```


```json
[
  {
    "id": 8,
    "parent_id": 7,
    "position": 0,
    "name": "brand_x",
    "permalink": "brand/brand_x",
    "taxonomy_id": 4,
    "lft": 6,
    "rgt": 7,
    "icon_file_name": null,
    "icon_content_type": null,
    "icon_file_size": null,
    "icon_updated_at": null,
    "description": null,
    "created_at": "2021-07-13T07:58:23.705-04:00",
    "updated_at": "2021-07-13T07:58:23.812-04:00",
    "meta_title": null,
    "meta_description": null,
    "meta_keywords": null,
    "depth": 1,
    "hidden": false,
    "highlight": false,
    "header_link": false,
    "url_override": null,
    "add_flair": false,
    "track_insights": false,
    "google_product_category": null,
    "short_description": null,
    "view_all_url_override": null
  }
]
```



# Users



## Login

Validate user email and password. Does not handle any session and only return the user

### Request

#### Endpoint

```plaintext
POST /api/users/login
Accept: application/json
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/users/login`

#### Parameters


```json
user[email]=email89%40example.com&user[password]=secret
```


| Name | Description |
|:-----|:------------|
| user[email] *required* | User email |
| user[password] *required* | User password |
| order_number  | Include the order number of a an existing guest cart if intending to merge |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
Authorization: Bearer 8e59daa91a499346189cab8fbbb444e714fdeac15738c092
ETag: W/&quot;845528e6e69f5e630cf11bbcdbbcd104&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: e18addd0-3649-43eb-88d9-20ccbeb1161b
X-Runtime: 0.050103
Vary: Origin
Content-Length: 562
200 OK
```


```json
{
  "id": 91,
  "email": "email89@example.com",
  "persistence_token": null,
  "perishable_token": null,
  "last_request_at": null,
  "login": "email89@example.com",
  "ship_address_id": null,
  "bill_address_id": null,
  "created_at": "2021-07-13T07:59:12.117-04:00",
  "updated_at": "2021-07-13T07:59:12.121-04:00",
  "spree_api_key": "8e59daa91a499346189cab8fbbb444e714fdeac15738c092",
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



## Login and merge guest cart

Log in and merge an existing guest cart with any existing carts associated with the user

### Request

#### Endpoint

```plaintext
POST /api/users/login
Accept: application/json
X-Spree-Order-Token: KrnKROQXnyUfFMWrt1OMLA
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/users/login`

#### Parameters


```json
user[email]=email90%40example.com&user[password]=secret&order_number=M627631796
```


| Name | Description |
|:-----|:------------|
| user[email] *required* | User email |
| user[password] *required* | User password |
| order_number  | Include the order number of a an existing guest cart if intending to merge |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
Authorization: Bearer e14bc8a4de3f189c27a3b42922f9d399820efb411fb9e880
ETag: W/&quot;f48ede1249d37dc3f02ff231c6cb6720&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 977d0888-45b0-4efb-a5f1-bd94e6a4dbab
X-Runtime: 0.054840
Vary: Origin
Content-Length: 562
200 OK
```


```json
{
  "id": 92,
  "email": "email90@example.com",
  "persistence_token": null,
  "perishable_token": null,
  "last_request_at": null,
  "login": "email90@example.com",
  "ship_address_id": null,
  "bill_address_id": null,
  "created_at": "2021-07-13T07:59:12.187-04:00",
  "updated_at": "2021-07-13T07:59:12.190-04:00",
  "spree_api_key": "e14bc8a4de3f189c27a3b42922f9d399820efb411fb9e880",
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
Accept: application/json
Authorizat IO N: Bearer b7a6184f6ad270e5c719968b00ad751d90960e821d0ea20e
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
Authorization: Bearer b7a6184f6ad270e5c719968b00ad751d90960e821d0ea20e
ETag: W/&quot;5eff8a0e646640843a9dff5c2b9a170d&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 7fe8fcbc-862f-4ecb-b586-2b970019c383
X-Runtime: 0.074210
Vary: Origin
Content-Length: 1539
200 OK
```


```json
{
  "email": "email91@example.com",
  "first_name": null,
  "last_name": null,
  "id": 93,
  "subscribed": false,
  "addresses": [
    {
      "id": 61,
      "firstname": "John",
      "lastname": "Smith",
      "full_name": "John Smith",
      "address1": "A Different Road",
      "address2": "Northwest",
      "city": "Herndon",
      "zipcode": "10060",
      "phone": "555-555-0199",
      "company": "Company",
      "alternative_phone": "555-555-0199",
      "country_id": 55,
      "country_iso": "US",
      "state_id": 55,
      "state_name": null,
      "state_text": "AL",
      "country": {
        "id": 55,
        "iso_name": "UNITED STATES",
        "iso": "US",
        "iso3": "USA",
        "name": "United States",
        "numcode": 840
      },
      "default": true
    },
    {
      "id": 60,
      "firstname": "John",
      "lastname": "Smith",
      "full_name": "John Smith",
      "address1": "PO Box 1337",
      "address2": "Northwest",
      "city": "Herndon",
      "zipcode": "10059",
      "phone": "555-555-0199",
      "company": "Company",
      "alternative_phone": "555-555-0199",
      "country_id": 55,
      "country_iso": "US",
      "state_id": 55,
      "state_name": null,
      "state_text": "AL",
      "country": {
        "id": 55,
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
      "id": 5,
      "default": true,
      "source": {
        "id": 6,
        "payment_type": "CreditCard",
        "token": null,
        "created_at": "2021-07-13T07:59:13.042-04:00",
        "cc_type": null,
        "last_digits": null,
        "month": null,
        "year": null
      }
    },
    {
      "id": 6,
      "default": false,
      "source": {
        "id": 7,
        "payment_type": "ApplePayCard",
        "token": null,
        "created_at": "2021-07-13T07:59:13.081-04:00",
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
        "id": 8,
        "payment_type": "PayPalAccount",
        "token": null,
        "created_at": "2021-07-13T07:59:13.120-04:00",
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
Accept: application/json
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
| order_number  | Include the order number of a an existing guest cart if intending to merge |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
Authorization: Bearer 78ed4e52fd8a53cd749a3daa02084259f1f34897e6fec232
ETag: W/&quot;99cbfa87104e4d8ccc8b882ad913df3b&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 98b9b52e-9c8e-4b30-ae36-1f672167aa11
X-Runtime: 0.076451
Vary: Origin
Content-Length: 185
201 Created
```


```json
{
  "id": 89,
  "email": "test@example.com",
  "created_at": "2021-07-13T07:59:11.339-04:00",
  "updated_at": "2021-07-13T07:59:11.342-04:00",
  "subscribed": false,
  "bill_address": null,
  "ship_address": null
}
```



## Signup and merge guest cart

Create a user and merge an existing guest cart with any existing carts associated with the user

### Request

#### Endpoint

```plaintext
POST /api/users
Accept: application/json
X-Spree-Order-Token: QNVtNo00giqTsCsiG1G8QQ
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/users`

#### Parameters


```json
user[email]=test%40example.com&user[password]=test123&user[password_confirmation]=test123&order_number=M144371025
```


| Name | Description |
|:-----|:------------|
| user[email] *required* | User email |
| user[password] *required* | User password |
| user[password_confirmation] *required* | User password confirmation |
| user[first_name]  | User first name |
| user[last_name]  | User last name |
| subscribe  | If set to 'true', this will create a subscriber associated with the new user |
| order_number  | Include the order number of a an existing guest cart if intending to merge |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
Authorization: Bearer a5135535844befdb3605c68a76018ed640b3584b29dea246
ETag: W/&quot;5a995fda560121abd90f95cdb841d544&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: da5e76fc-d1ab-439b-aee1-5f81876c0293
X-Runtime: 0.069648
Vary: Origin
Content-Length: 185
201 Created
```


```json
{
  "id": 90,
  "email": "test@example.com",
  "created_at": "2021-07-13T07:59:12.075-04:00",
  "updated_at": "2021-07-13T07:59:12.078-04:00",
  "subscribed": false,
  "bill_address": null,
  "ship_address": null
}
```



## Subscribe a user


### Request

#### Endpoint

```plaintext
PUT /api/users/97/subscribe
Accept: application/json
Authorizat IO N: Bearer b51e854f77160b5f1cb1e7fc23b7926592249e38ab4883df
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
Authorization: Bearer b51e854f77160b5f1cb1e7fc23b7926592249e38ab4883df
ETag: W/&quot;0da3adf9a7ecf13637da78fdb6657671&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 380d79e8-4f32-4802-9dd3-b96e433b3bdb
X-Runtime: 0.056482
Vary: Origin
Content-Length: 187
200 OK
```


```json
{
  "id": 97,
  "email": "email95@example.com",
  "created_at": "2021-07-13T07:59:13.214-04:00",
  "updated_at": "2021-07-13T07:59:13.217-04:00",
  "subscribed": true,
  "bill_address": null,
  "ship_address": null
}
```



## Unsubscribe a user


### Request

#### Endpoint

```plaintext
PUT /api/users/98/unsubscribe
Accept: application/json
Authorizat IO N: Bearer a260c77cc45cd6fe3e4081c6e57c79c1d11527a9de1bd69e
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
Authorization: Bearer a260c77cc45cd6fe3e4081c6e57c79c1d11527a9de1bd69e
ETag: W/&quot;6c9b295f1deb3da01d878a9dc329bf30&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 3b5c1b34-56cb-4af4-bd87-375d43b16653
X-Runtime: 0.089232
Vary: Origin
Content-Length: 188
200 OK
```


```json
{
  "id": 98,
  "email": "email96@example.com",
  "created_at": "2021-07-13T07:59:13.302-04:00",
  "updated_at": "2021-07-13T07:59:13.305-04:00",
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
GET /api/variants/120
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
ETag: W/&quot;7845c477ede49b1a7de382d4bb649661&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 909be7ac-8f5f-4984-915a-7153a08bf07f
X-Runtime: 0.144575
Vary: Origin
Content-Length: 2351
200 OK
```


```json
{
  "id": 120,
  "name": "Product #67 - 620",
  "sku": "SKU-119",
  "is_master": false,
  "slug": "product-67-620",
  "description": "As seen on TV!",
  "track_inventory": true,
  "height": null,
  "width": null,
  "depth": null,
  "weight": null,
  "lead_time": 2,
  "is_registry": false,
  "discontinued": false,
  "price": "10.0",
  "display_price": "$10.00",
  "options_text": "Size: S",
  "in_stock": false,
  "is_backorderable": false,
  "total_on_hand": 0,
  "is_destroyed": false,
  "option_values": [
    {
      "id": 53,
      "name": "Size-53",
      "presentation": "S",
      "option_type_name": "foo-size-53",
      "option_type_id": 53,
      "option_type_presentation": "Size",
      "position": 1
    }
  ],
  "images": [
    {
      "id": 1,
      "position": 1,
      "attachment_content_type": "image/jpeg",
      "attachment_file_name": "thinking-cat.jpg",
      "type": "Spree::Image",
      "attachment_updated_at": "2021-07-13T07:58:43.786-04:00",
      "attachment_width": 489,
      "attachment_height": 490,
      "alt": null,
      "viewable_type": "Spree::Variant",
      "viewable_id": 120,
      "mini_url": "/spree/products/1/mini/thinking-cat.jpg?1626177523",
      "small_url": "/spree/products/1/small/thinking-cat.jpg?1626177523",
      "product_url": "/spree/products/1/product/thinking-cat.jpg?1626177523",
      "large_url": "/spree/products/1/large/thinking-cat.jpg?1626177523",
      "product_large_url": "/spree/products/1/product_large/thinking-cat.jpg?1626177523",
      "product_retina_url": "/spree/products/1/product_retina/thinking-cat.jpg?1626177523",
      "product_zoom_url": "/spree/products/1/product_zoom/thinking-cat.jpg?1626177523"
    }
  ],
  "videos": [

  ],
  "variant_properties": [

  ],
  "stock_items": [

  ],
  "prices": [
    {
      "id": 81,
      "vendor_id": 202,
      "price": "10.0",
      "original_price": "10.0",
      "discount_percent": 0.0,
      "total_on_hand": 0,
      "country_iso": null,
      "final_sale": false,
      "on_sale": false,
      "offer_settings": {
        "cost_price": null,
        "is_registry": null
      },
      "monogram": {
        "monogrammable_only": null,
        "monogram_price": null,
        "monogram_cost_price": null,
        "monogram_lead_time": null,
        "monogram_max_text_length": null,
        "monogram_customizations": null,
        "display_monogram_customizations": null,
        "monogrammable": null
      }
    },
    {
      "id": 82,
      "vendor_id": 203,
      "price": "20.0",
      "original_price": "20.0",
      "discount_percent": 0.0,
      "total_on_hand": 0,
      "country_iso": null,
      "final_sale": false,
      "on_sale": false,
      "offer_settings": {
        "cost_price": null,
        "is_registry": null
      },
      "monogram": {
        "monogrammable_only": null,
        "monogram_price": null,
        "monogram_cost_price": null,
        "monogram_lead_time": null,
        "monogram_max_text_length": null,
        "monogram_customizations": null,
        "display_monogram_customizations": null,
        "monogrammable": null
      }
    }
  ]
}
```



## Fetching a variant with Monogram Customization


### Request

#### Endpoint

```plaintext
GET /api/variants/126
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
ETag: W/&quot;01617fbb3243f6e35d2145fbd7bfa7a6&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: fe29aea1-06c8-4905-8197-692adfceb89f
X-Runtime: 0.133080
Vary: Origin
Content-Length: 2990
200 OK
```


```json
{
  "id": 126,
  "name": "Product #70 - 6585",
  "sku": "SKU-125",
  "is_master": false,
  "slug": "product-70-6585",
  "description": "As seen on TV!",
  "track_inventory": true,
  "height": null,
  "width": null,
  "depth": null,
  "weight": null,
  "lead_time": 2,
  "is_registry": false,
  "discontinued": false,
  "price": "10.0",
  "display_price": "$10.00",
  "options_text": "Size: S",
  "in_stock": false,
  "is_backorderable": false,
  "total_on_hand": 0,
  "is_destroyed": false,
  "option_values": [
    {
      "id": 56,
      "name": "Size-56",
      "presentation": "S",
      "option_type_name": "foo-size-56",
      "option_type_id": 56,
      "option_type_presentation": "Size",
      "position": 1
    }
  ],
  "images": [
    {
      "id": 4,
      "position": 1,
      "attachment_content_type": "image/jpeg",
      "attachment_file_name": "thinking-cat.jpg",
      "type": "Spree::Image",
      "attachment_updated_at": "2021-07-13T07:58:47.498-04:00",
      "attachment_width": 489,
      "attachment_height": 490,
      "alt": null,
      "viewable_type": "Spree::Variant",
      "viewable_id": 126,
      "mini_url": "/spree/products/4/mini/thinking-cat.jpg?1626177527",
      "small_url": "/spree/products/4/small/thinking-cat.jpg?1626177527",
      "product_url": "/spree/products/4/product/thinking-cat.jpg?1626177527",
      "large_url": "/spree/products/4/large/thinking-cat.jpg?1626177527",
      "product_large_url": "/spree/products/4/product_large/thinking-cat.jpg?1626177527",
      "product_retina_url": "/spree/products/4/product_retina/thinking-cat.jpg?1626177527",
      "product_zoom_url": "/spree/products/4/product_zoom/thinking-cat.jpg?1626177527"
    }
  ],
  "videos": [

  ],
  "variant_properties": [

  ],
  "stock_items": [

  ],
  "prices": [
    {
      "id": 90,
      "vendor_id": 223,
      "price": "10.0",
      "original_price": "10.0",
      "discount_percent": 0.0,
      "total_on_hand": 0,
      "country_iso": null,
      "final_sale": false,
      "on_sale": false,
      "offer_settings": {
        "cost_price": null,
        "is_registry": null
      },
      "monogram": {
        "monogrammable_only": null,
        "monogram_price": null,
        "monogram_cost_price": null,
        "monogram_lead_time": null,
        "monogram_max_text_length": null,
        "monogram_customizations": null,
        "display_monogram_customizations": null,
        "monogrammable": null
      }
    },
    {
      "id": 91,
      "vendor_id": 224,
      "price": "20.0",
      "original_price": "20.0",
      "discount_percent": 0.0,
      "total_on_hand": 0,
      "country_iso": null,
      "final_sale": false,
      "on_sale": false,
      "offer_settings": {
        "cost_price": null,
        "is_registry": false
      },
      "monogram": {
        "monogrammable_only": false,
        "monogram_price": "5.5",
        "monogram_cost_price": "2.25",
        "monogram_lead_time": null,
        "monogram_max_text_length": 20,
        "monogram_customizations": {
          "fonts": [
            {
              "name": "Monogram Font 1",
              "value": "serif"
            },
            {
              "name": "Monogram Font 1 Title",
              "value": "Toy Soilder"
            },
            {
              "name": "Monogram Font 2",
              "value": "Times"
            },
            {
              "name": "Monogram Font 2 Title",
              "value": "Emerson"
            }
          ],
          "colors": [
            {
              "name": "Monogram Color 1",
              "value": "#ffffff"
            },
            {
              "name": "Monogram Color 1 Title",
              "value": "White"
            },
            {
              "name": "Monogram Color 2",
              "value": "#FF0000"
            },
            {
              "name": "Monogram Color 2 Title",
              "value": "Red"
            }
          ]
        },
        "display_monogram_customizations": {
          "colors": {
            "Monogram Color 1": {
              "value": "#ffffff",
              "name": "White"
            },
            "Monogram Color 2": {
              "value": "#FF0000",
              "name": "Red"
            }
          },
          "fonts": {
            "Monogram Font 1": {
              "value": "serif",
              "name": "Toy Soilder"
            },
            "Monogram Font 2": {
              "value": "Times",
              "name": "Emerson"
            }
          }
        },
        "monogrammable": true
      }
    }
  ]
}
```



## Fetching a variant with Monogram Customization and color is not required


### Request

#### Endpoint

```plaintext
GET /api/variants/128
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
ETag: W/&quot;e84a74e4e8d632d449f4629c369817fe&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: a12d72ab-6ce3-4bd4-9e2c-81edee4f3b79
X-Runtime: 0.140439
Vary: Origin
Content-Length: 2696
200 OK
```


```json
{
  "id": 128,
  "name": "Product #71 - 5382",
  "sku": "SKU-127",
  "is_master": false,
  "slug": "product-71-5382",
  "description": "As seen on TV!",
  "track_inventory": true,
  "height": null,
  "width": null,
  "depth": null,
  "weight": null,
  "lead_time": 2,
  "is_registry": false,
  "discontinued": false,
  "price": "10.0",
  "display_price": "$10.00",
  "options_text": "Size: S",
  "in_stock": false,
  "is_backorderable": false,
  "total_on_hand": 0,
  "is_destroyed": false,
  "option_values": [
    {
      "id": 57,
      "name": "Size-57",
      "presentation": "S",
      "option_type_name": "foo-size-57",
      "option_type_id": 57,
      "option_type_presentation": "Size",
      "position": 1
    }
  ],
  "images": [
    {
      "id": 5,
      "position": 1,
      "attachment_content_type": "image/jpeg",
      "attachment_file_name": "thinking-cat.jpg",
      "type": "Spree::Image",
      "attachment_updated_at": "2021-07-13T07:58:49.050-04:00",
      "attachment_width": 489,
      "attachment_height": 490,
      "alt": null,
      "viewable_type": "Spree::Variant",
      "viewable_id": 128,
      "mini_url": "/spree/products/5/mini/thinking-cat.jpg?1626177529",
      "small_url": "/spree/products/5/small/thinking-cat.jpg?1626177529",
      "product_url": "/spree/products/5/product/thinking-cat.jpg?1626177529",
      "large_url": "/spree/products/5/large/thinking-cat.jpg?1626177529",
      "product_large_url": "/spree/products/5/product_large/thinking-cat.jpg?1626177529",
      "product_retina_url": "/spree/products/5/product_retina/thinking-cat.jpg?1626177529",
      "product_zoom_url": "/spree/products/5/product_zoom/thinking-cat.jpg?1626177529"
    }
  ],
  "videos": [

  ],
  "variant_properties": [

  ],
  "stock_items": [

  ],
  "prices": [
    {
      "id": 93,
      "vendor_id": 230,
      "price": "10.0",
      "original_price": "10.0",
      "discount_percent": 0.0,
      "total_on_hand": 0,
      "country_iso": null,
      "final_sale": false,
      "on_sale": false,
      "offer_settings": {
        "cost_price": null,
        "is_registry": null
      },
      "monogram": {
        "monogrammable_only": null,
        "monogram_price": null,
        "monogram_cost_price": null,
        "monogram_lead_time": null,
        "monogram_max_text_length": null,
        "monogram_customizations": null,
        "display_monogram_customizations": null,
        "monogrammable": null
      }
    },
    {
      "id": 94,
      "vendor_id": 231,
      "price": "20.0",
      "original_price": "20.0",
      "discount_percent": 0.0,
      "total_on_hand": 0,
      "country_iso": null,
      "final_sale": false,
      "on_sale": false,
      "offer_settings": {
        "cost_price": null,
        "is_registry": false
      },
      "monogram": {
        "monogrammable_only": false,
        "monogram_price": "5.5",
        "monogram_cost_price": "2.25",
        "monogram_lead_time": null,
        "monogram_max_text_length": 20,
        "monogram_customizations": {
          "fonts": [
            {
              "name": "Monogram Font 1",
              "value": "serif"
            },
            {
              "name": "Monogram Font 1 Title",
              "value": "Toy Soilder"
            },
            {
              "name": "Monogram Font 2",
              "value": "Times"
            },
            {
              "name": "Monogram Font 2 Title",
              "value": "Emerson"
            }
          ],
          "colors": [

          ]
        },
        "display_monogram_customizations": {
          "colors": {
          },
          "fonts": {
            "Monogram Font 1": {
              "value": "serif",
              "name": "Toy Soilder"
            },
            "Monogram Font 2": {
              "value": "Times",
              "name": "Emerson"
            }
          }
        },
        "monogrammable": true
      }
    }
  ]
}
```



## Fetching a variant with dimensions


### Request

#### Endpoint

```plaintext
GET /api/variants/124
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
ETag: W/&quot;186020dafaf7ed019b24e8559027884e&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 9e195241-b770-410e-b42b-c1b3d5f8be6f
X-Runtime: 0.144456
Vary: Origin
Content-Length: 2367
200 OK
```


```json
{
  "id": 124,
  "name": "Product #69 - 8656",
  "sku": "SKU-123",
  "is_master": false,
  "slug": "product-69-8656",
  "description": "As seen on TV!",
  "track_inventory": true,
  "height": "5.0\"",
  "width": "2.5\"",
  "depth": "1.2\"",
  "weight": "2.5 lbs",
  "lead_time": 2,
  "is_registry": false,
  "discontinued": false,
  "price": "10.0",
  "display_price": "$10.00",
  "options_text": "Size: S",
  "in_stock": false,
  "is_backorderable": false,
  "total_on_hand": 0,
  "is_destroyed": false,
  "option_values": [
    {
      "id": 55,
      "name": "Size-55",
      "presentation": "S",
      "option_type_name": "foo-size-55",
      "option_type_id": 55,
      "option_type_presentation": "Size",
      "position": 1
    }
  ],
  "images": [
    {
      "id": 3,
      "position": 1,
      "attachment_content_type": "image/jpeg",
      "attachment_file_name": "thinking-cat.jpg",
      "type": "Spree::Image",
      "attachment_updated_at": "2021-07-13T07:58:46.240-04:00",
      "attachment_width": 489,
      "attachment_height": 490,
      "alt": null,
      "viewable_type": "Spree::Variant",
      "viewable_id": 124,
      "mini_url": "/spree/products/3/mini/thinking-cat.jpg?1626177526",
      "small_url": "/spree/products/3/small/thinking-cat.jpg?1626177526",
      "product_url": "/spree/products/3/product/thinking-cat.jpg?1626177526",
      "large_url": "/spree/products/3/large/thinking-cat.jpg?1626177526",
      "product_large_url": "/spree/products/3/product_large/thinking-cat.jpg?1626177526",
      "product_retina_url": "/spree/products/3/product_retina/thinking-cat.jpg?1626177526",
      "product_zoom_url": "/spree/products/3/product_zoom/thinking-cat.jpg?1626177526"
    }
  ],
  "videos": [

  ],
  "variant_properties": [

  ],
  "stock_items": [

  ],
  "prices": [
    {
      "id": 87,
      "vendor_id": 216,
      "price": "10.0",
      "original_price": "10.0",
      "discount_percent": 0.0,
      "total_on_hand": 0,
      "country_iso": null,
      "final_sale": false,
      "on_sale": false,
      "offer_settings": {
        "cost_price": null,
        "is_registry": null
      },
      "monogram": {
        "monogrammable_only": null,
        "monogram_price": null,
        "monogram_cost_price": null,
        "monogram_lead_time": null,
        "monogram_max_text_length": null,
        "monogram_customizations": null,
        "display_monogram_customizations": null,
        "monogrammable": null
      }
    },
    {
      "id": 88,
      "vendor_id": 217,
      "price": "20.0",
      "original_price": "20.0",
      "discount_percent": 0.0,
      "total_on_hand": 0,
      "country_iso": null,
      "final_sale": false,
      "on_sale": false,
      "offer_settings": {
        "cost_price": null,
        "is_registry": null
      },
      "monogram": {
        "monogrammable_only": null,
        "monogram_price": null,
        "monogram_cost_price": null,
        "monogram_lead_time": null,
        "monogram_max_text_length": null,
        "monogram_customizations": null,
        "display_monogram_customizations": null,
        "monogrammable": null
      }
    }
  ]
}
```



## Fetching a variant without dimensions


### Request

#### Endpoint

```plaintext
GET /api/variants/122
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
ETag: W/&quot;220600afa21985d8393034477633ce13&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: d1a3f630-72ff-4fd6-9f1f-dff4b63cdce5
X-Runtime: 0.131458
Vary: Origin
Content-Length: 2353
200 OK
```


```json
{
  "id": 122,
  "name": "Product #68 - 3118",
  "sku": "SKU-121",
  "is_master": false,
  "slug": "product-68-3118",
  "description": "As seen on TV!",
  "track_inventory": true,
  "height": null,
  "width": null,
  "depth": null,
  "weight": null,
  "lead_time": 2,
  "is_registry": false,
  "discontinued": false,
  "price": "10.0",
  "display_price": "$10.00",
  "options_text": "Size: S",
  "in_stock": false,
  "is_backorderable": false,
  "total_on_hand": 0,
  "is_destroyed": false,
  "option_values": [
    {
      "id": 54,
      "name": "Size-54",
      "presentation": "S",
      "option_type_name": "foo-size-54",
      "option_type_id": 54,
      "option_type_presentation": "Size",
      "position": 1
    }
  ],
  "images": [
    {
      "id": 2,
      "position": 1,
      "attachment_content_type": "image/jpeg",
      "attachment_file_name": "thinking-cat.jpg",
      "type": "Spree::Image",
      "attachment_updated_at": "2021-07-13T07:58:45.040-04:00",
      "attachment_width": 489,
      "attachment_height": 490,
      "alt": null,
      "viewable_type": "Spree::Variant",
      "viewable_id": 122,
      "mini_url": "/spree/products/2/mini/thinking-cat.jpg?1626177525",
      "small_url": "/spree/products/2/small/thinking-cat.jpg?1626177525",
      "product_url": "/spree/products/2/product/thinking-cat.jpg?1626177525",
      "large_url": "/spree/products/2/large/thinking-cat.jpg?1626177525",
      "product_large_url": "/spree/products/2/product_large/thinking-cat.jpg?1626177525",
      "product_retina_url": "/spree/products/2/product_retina/thinking-cat.jpg?1626177525",
      "product_zoom_url": "/spree/products/2/product_zoom/thinking-cat.jpg?1626177525"
    }
  ],
  "videos": [

  ],
  "variant_properties": [

  ],
  "stock_items": [

  ],
  "prices": [
    {
      "id": 84,
      "vendor_id": 209,
      "price": "10.0",
      "original_price": "10.0",
      "discount_percent": 0.0,
      "total_on_hand": 0,
      "country_iso": null,
      "final_sale": false,
      "on_sale": false,
      "offer_settings": {
        "cost_price": null,
        "is_registry": null
      },
      "monogram": {
        "monogrammable_only": null,
        "monogram_price": null,
        "monogram_cost_price": null,
        "monogram_lead_time": null,
        "monogram_max_text_length": null,
        "monogram_customizations": null,
        "display_monogram_customizations": null,
        "monogrammable": null
      }
    },
    {
      "id": 85,
      "vendor_id": 210,
      "price": "20.0",
      "original_price": "20.0",
      "discount_percent": 0.0,
      "total_on_hand": 0,
      "country_iso": null,
      "final_sale": false,
      "on_sale": false,
      "offer_settings": {
        "cost_price": null,
        "is_registry": null
      },
      "monogram": {
        "monogrammable_only": null,
        "monogram_price": null,
        "monogram_cost_price": null,
        "monogram_lead_time": null,
        "monogram_max_text_length": null,
        "monogram_customizations": null,
        "display_monogram_customizations": null,
        "monogrammable": null
      }
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
Authorizat IO N: Bearer df497aae08e06e5631ca6ba3e44c1ea2c97cb5ae261559d2
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
ETag: W/&quot;4d0991ff9f7fb5e8c34b70d807fe5cfa&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: b69ae2bd-4430-4a5c-898d-bb85589d6d7c
X-Runtime: 0.041134
Vary: Origin
Content-Length: 206
200 OK
```


```json
[
  {
    "id": 2,
    "user_id": 67,
    "payment_source_type": "SolidusPaypalBraintree::Source",
    "payment_source_id": 2,
    "default": false,
    "created_at": "2021-07-13T07:58:41.271-04:00",
    "updated_at": "2021-07-13T07:58:41.271-04:00"
  }
]
```



## Remove the payment from the user wallet


### Request

#### Endpoint

```plaintext
DELETE /api/wallet_payment_sources/3
Accept: application/json
Authorizat IO N: Bearer 2a3643320b42cadcb0a460a3789f714ad8618ef1d2cdf333
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
X-Request-Id: da5714eb-c0bc-41bd-b519-98f83db2bacf
X-Runtime: 0.043201
Vary: Origin
204 No Content
```




## Set a wallet payment source as the default user payment method


### Request

#### Endpoint

```plaintext
POST /api/wallet_payment_sources/1/default
Accept: application/json
Authorizat IO N: Bearer 130f7ccf9a0ad5b3317274d9bd671e57f2043d3a05784c8e
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
X-Request-Id: c130ce0b-98f5-46ed-b620-55ecce523907
X-Runtime: 0.058980
Vary: Origin
204 No Content
```




# Wished Products

Get all wished products, only accessible to admin users

## Create a wished product


### Request

#### Endpoint

```plaintext
POST /api/wished_products
Accept: application/json
Authorizat IO N: Bearer 1af0028b9827c919d55a223afeb39479a91acc5ee186d566
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/wished_products`

#### Parameters


```json
wished_product[wishlist_id]=38&wished_product[variant_id]=81&wished_product[quantity]=2&wished_product[remark]=Foo+bar
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
ETag: W/&quot;5913cd08ff41e96e3e87e6ef29f4ea43&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: fda4dfdc-eda3-4ee7-bbab-5140cb6d6757
X-Runtime: 0.051727
Vary: Origin
Content-Length: 119
201 Created
```


```json
{
  "id": 25,
  "wishlist_id": 38,
  "variant_id": 81,
  "quantity": 2,
  "remark": "Foo bar",
  "created_at": "2021-07-13T07:58:32.277-04:00"
}
```



## Delete a wished product


### Request

#### Endpoint

```plaintext
DELETE /api/wished_products/19
Accept: application/json
Authorizat IO N: Bearer 4d40071247346eba68d42939d381de671e398a7f411562ec
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
X-Request-Id: b12ecf77-ac02-4691-bf22-e3cba9cd31c8
X-Runtime: 0.040906
Vary: Origin
204 No Content
```




## Get a single wished product


### Request

#### Endpoint

```plaintext
GET /api/wished_products/16
Accept: application/json
Authorizat IO N: Bearer c98d89755246fd807c8fec51bb93baff7d397e1f3092f9e3
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
ETag: W/&quot;b0a78fa40ee4bd1214f978facd9acc28&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 1ee11dac-3a9b-4f8e-91c2-6b80de6ee2a4
X-Runtime: 0.041998
Vary: Origin
Content-Length: 114
200 OK
```


```json
{
  "id": 16,
  "wishlist_id": 35,
  "variant_id": 61,
  "quantity": 1,
  "remark": null,
  "created_at": "2021-07-13T07:58:29.417-04:00"
}
```



## Get all wished products


### Request

#### Endpoint

```plaintext
GET /api/wished_products
Accept: application/json
Authorizat IO N: Bearer 6ceff8f396aac52821eb89bf9de238e1ffe7a01a515c3399
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
ETag: W/&quot;0d6f8b05f7fa5d728567b08076b8b3c5&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 4b643953-57bd-4c16-b346-65dd48db4d57
X-Runtime: 0.050841
Vary: Origin
Content-Length: 433
200 OK
```


```json
{
  "wished_products": [
    {
      "id": 12,
      "wishlist_id": 31,
      "variant_id": 53,
      "quantity": 1,
      "remark": null,
      "created_at": "2021-07-13T07:58:27.996-04:00"
    },
    {
      "id": 11,
      "wishlist_id": 30,
      "variant_id": 51,
      "quantity": 1,
      "remark": null,
      "created_at": "2021-07-13T07:58:27.740-04:00"
    },
    {
      "id": 10,
      "wishlist_id": 29,
      "variant_id": 49,
      "quantity": 1,
      "remark": null,
      "created_at": "2021-07-13T07:58:27.462-04:00"
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
Authorizat IO N: Bearer a4d5479967bf70016890c1d8da098915b1b8ab1aff265210
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
ETag: W/&quot;8c99f61aba459b5a1a46d72c35bc6f6b&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 32b78ca7-7677-476c-ac19-eab0a21e3171
X-Runtime: 0.208755
Vary: Origin
Content-Length: 2437
200 OK
```


```json
{
  "wished_products": [
    {
      "id": 15,
      "wishlist_id": 34,
      "variant_id": 59,
      "quantity": 1,
      "remark": null,
      "created_at": "2021-07-13T07:58:28.883-04:00",
      "variant": {
        "id": 59,
        "name": "Product #30 - 3777",
        "sku": "SKU-58",
        "is_master": false,
        "slug": "product-30-3777",
        "description": "As seen on TV!",
        "track_inventory": true,
        "cost_price": "17.0",
        "height": null,
        "width": null,
        "depth": null,
        "weight": null,
        "lead_time": 2,
        "is_registry": false,
        "discontinued": false,
        "price": null,
        "display_price": "",
        "options_text": "Size: S",
        "in_stock": false,
        "is_backorderable": false,
        "total_on_hand": 0,
        "is_destroyed": false,
        "option_values": [
          {
            "id": 29,
            "name": "Size-29",
            "presentation": "S",
            "option_type_name": "foo-size-29",
            "option_type_id": 29,
            "option_type_presentation": "Size",
            "position": 1
          }
        ],
        "images": [

        ],
        "videos": [

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
      "id": 14,
      "wishlist_id": 33,
      "variant_id": 57,
      "quantity": 1,
      "remark": null,
      "created_at": "2021-07-13T07:58:28.629-04:00",
      "variant": {
        "id": 57,
        "name": "Product #29 - 7499",
        "sku": "SKU-56",
        "is_master": false,
        "slug": "product-29-7499",
        "description": "As seen on TV!",
        "track_inventory": true,
        "cost_price": "17.0",
        "height": null,
        "width": null,
        "depth": null,
        "weight": null,
        "lead_time": 2,
        "is_registry": false,
        "discontinued": false,
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
            "option_type_presentation": "Size",
            "position": 1
          }
        ],
        "images": [

        ],
        "videos": [

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
      "id": 13,
      "wishlist_id": 32,
      "variant_id": 55,
      "quantity": 1,
      "remark": null,
      "created_at": "2021-07-13T07:58:28.362-04:00",
      "variant": {
        "id": 55,
        "name": "Product #28 - 4691",
        "sku": "SKU-54",
        "is_master": false,
        "slug": "product-28-4691",
        "description": "As seen on TV!",
        "track_inventory": true,
        "cost_price": "17.0",
        "height": null,
        "width": null,
        "depth": null,
        "weight": null,
        "lead_time": 2,
        "is_registry": false,
        "discontinued": false,
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
            "option_type_presentation": "Size",
            "position": 1
          }
        ],
        "images": [

        ],
        "videos": [

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
Authorizat IO N: Bearer c512edb8c80bb665a1b6225a948407562e4c3945ef0f8e19
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
ETag: W/&quot;7960c85ff07117f37a1b65581e22012e&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 75e46050-f8b2-46e5-9900-3c071002a01d
X-Runtime: 0.194216
Vary: Origin
Content-Length: 2377
200 OK
```


```json
{
  "wished_products": [
    {
      "id": 29,
      "wishlist_id": 40,
      "variant_id": 89,
      "quantity": 1,
      "remark": null,
      "created_at": "2021-07-13T07:58:33.419-04:00",
      "variant": {
        "id": 89,
        "name": "Product #45 - 6922",
        "sku": "SKU-88",
        "is_master": false,
        "slug": "product-45-6922",
        "description": "As seen on TV!",
        "track_inventory": true,
        "height": null,
        "width": null,
        "depth": null,
        "weight": null,
        "lead_time": 2,
        "is_registry": false,
        "discontinued": false,
        "price": null,
        "display_price": "",
        "options_text": "Size: S",
        "in_stock": false,
        "is_backorderable": false,
        "total_on_hand": 0,
        "is_destroyed": false,
        "option_values": [
          {
            "id": 44,
            "name": "Size-44",
            "presentation": "S",
            "option_type_name": "foo-size-44",
            "option_type_id": 44,
            "option_type_presentation": "Size",
            "position": 1
          }
        ],
        "images": [

        ],
        "videos": [

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
      "id": 30,
      "wishlist_id": 40,
      "variant_id": 91,
      "quantity": 1,
      "remark": null,
      "created_at": "2021-07-13T07:58:33.656-04:00",
      "variant": {
        "id": 91,
        "name": "Product #46 - 2708",
        "sku": "SKU-90",
        "is_master": false,
        "slug": "product-46-2708",
        "description": "As seen on TV!",
        "track_inventory": true,
        "height": null,
        "width": null,
        "depth": null,
        "weight": null,
        "lead_time": 2,
        "is_registry": false,
        "discontinued": false,
        "price": null,
        "display_price": "",
        "options_text": "Size: S",
        "in_stock": false,
        "is_backorderable": false,
        "total_on_hand": 0,
        "is_destroyed": false,
        "option_values": [
          {
            "id": 45,
            "name": "Size-45",
            "presentation": "S",
            "option_type_name": "foo-size-45",
            "option_type_id": 45,
            "option_type_presentation": "Size",
            "position": 1
          }
        ],
        "images": [

        ],
        "videos": [

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
      "id": 31,
      "wishlist_id": 40,
      "variant_id": 93,
      "quantity": 1,
      "remark": null,
      "created_at": "2021-07-13T07:58:33.919-04:00",
      "variant": {
        "id": 93,
        "name": "Product #47 - 5807",
        "sku": "SKU-92",
        "is_master": false,
        "slug": "product-47-5807",
        "description": "As seen on TV!",
        "track_inventory": true,
        "height": null,
        "width": null,
        "depth": null,
        "weight": null,
        "lead_time": 2,
        "is_registry": false,
        "discontinued": false,
        "price": null,
        "display_price": "",
        "options_text": "Size: S",
        "in_stock": false,
        "is_backorderable": false,
        "total_on_hand": 0,
        "is_destroyed": false,
        "option_values": [
          {
            "id": 46,
            "name": "Size-46",
            "presentation": "S",
            "option_type_name": "foo-size-46",
            "option_type_id": 46,
            "option_type_presentation": "Size",
            "position": 1
          }
        ],
        "images": [

        ],
        "videos": [

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
Authorizat IO N: Bearer d41bb2df122a6765203468c0f6997e055ebe483afea1103b
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
ETag: W/&quot;d2d5a3fb41e846da05bbd6ea4318a348&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 1682d6be-e9a8-449b-a158-17e65f49aa77
X-Runtime: 0.038583
Vary: Origin
Content-Length: 433
200 OK
```


```json
{
  "wished_products": [
    {
      "id": 26,
      "wishlist_id": 39,
      "variant_id": 83,
      "quantity": 1,
      "remark": null,
      "created_at": "2021-07-13T07:58:32.588-04:00"
    },
    {
      "id": 27,
      "wishlist_id": 39,
      "variant_id": 85,
      "quantity": 1,
      "remark": null,
      "created_at": "2021-07-13T07:58:32.845-04:00"
    },
    {
      "id": 28,
      "wishlist_id": 39,
      "variant_id": 87,
      "quantity": 1,
      "remark": null,
      "created_at": "2021-07-13T07:58:33.090-04:00"
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
PATCH /api/wished_products/22
Accept: application/json
Authorizat IO N: Bearer 38d7ed012f4ae692b8608696b76be937dee4645ccc193849
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/wished_products/:id`

#### Parameters


```json
wished_product[wishlist_id]=37&wished_product[variant_id]=79&wished_product[quantity]=2&wished_product[remark]=Foo+bar
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
ETag: W/&quot;c7278004e9c80d49dd52d914116d41fd&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 3b41c163-22d5-476a-9e0c-a455c8a08357
X-Runtime: 0.052511
Vary: Origin
Content-Length: 119
200 OK
```


```json
{
  "id": 22,
  "wishlist_id": 37,
  "variant_id": 79,
  "quantity": 2,
  "remark": "Foo bar",
  "created_at": "2021-07-13T07:58:31.089-04:00"
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
Authorizat IO N: Bearer dad230b31098c4ec39b0660ba7ec2d16071c82f3ea0ff19f
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/wishlists`

#### Parameters


```json
wishlist[name]&wishlist[user_id]=22&wishlist[is_default]=true&wishlist[is_public]=false
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
ETag: W/&quot;83d3945f5a3788b00ce82459bc44c831&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 8257a069-68ba-4d2b-bc16-2e43280e4418
X-Runtime: 0.052844
Vary: Origin
Content-Length: 100
201 Created
```


```json
{
  "id": 13,
  "user_id": 22,
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
DELETE /api/wishlists/12
Accept: application/json
Authorizat IO N: Bearer a3ac8f573cf0e2b7c1aad4e0f454a0784b4b26613b338834
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
X-Request-Id: bccfdc39-7203-43a1-8fb3-e57a270322f4
X-Runtime: 0.053450
Vary: Origin
204 No Content
```




## Get a single wishlist


### Request

#### Endpoint

```plaintext
GET /api/wishlists/1
Accept: application/json
Authorizat IO N: Bearer b1ab58f560baebcf7c40abbf40c184e8508953aa2a9bf9b7
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
ETag: W/&quot;5555cf405a2e2d9cb1eb77bfd05fddab&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 39cf68dd-3136-4425-a39a-b328a4db5b26
X-Runtime: 0.095781
Vary: Origin
Content-Length: 434
200 OK
```


```json
{
  "id": 1,
  "user_id": 9,
  "name": "Wishlist #1",
  "is_public": false,
  "is_default": true,
  "wished_products": [
    {
      "id": 1,
      "wishlist_id": 1,
      "variant_id": 7,
      "quantity": 1,
      "remark": null,
      "created_at": "2021-07-13T07:58:13.501-04:00"
    },
    {
      "id": 2,
      "wishlist_id": 1,
      "variant_id": 9,
      "quantity": 1,
      "remark": null,
      "created_at": "2021-07-13T07:58:13.760-04:00"
    },
    {
      "id": 3,
      "wishlist_id": 1,
      "variant_id": 11,
      "quantity": 1,
      "remark": null,
      "created_at": "2021-07-13T07:58:13.992-04:00"
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
Authorizat IO N: Bearer f35c15fdc0970109d16d2de8163d5238a5a41353dbf23d6d
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
ETag: W/&quot;fc6531205a166bc0ad765a1028140103&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: a1fa8c2a-3492-41b1-afe3-eba88385c7fc
X-Runtime: 0.054012
Vary: Origin
Content-Length: 878
200 OK
```


```json
{
  "wishlists": [
    {
      "id": 2,
      "user_id": 10,
      "name": "Wishlist #2",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 3,
      "user_id": 11,
      "name": "Wishlist #3",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 4,
      "user_id": 12,
      "name": "Wishlist #4",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 5,
      "user_id": 13,
      "name": "Wishlist #5",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 6,
      "user_id": 14,
      "name": "Wishlist #6",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 7,
      "user_id": 15,
      "name": "Wishlist #7",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 8,
      "user_id": 16,
      "name": "Wishlist #8",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 9,
      "user_id": 17,
      "name": "Wishlist #9",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 10,
      "user_id": 18,
      "name": "Wishlist #10",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 11,
      "user_id": 19,
      "name": "Wishlist #11",
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
Authorizat IO N: Bearer a3f243284adc3f3b9032efdfc06a7fb8a45247d7d22f31d5
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
ETag: W/&quot;fa04f5b32b71e1a2cacbb30c5fcd6736&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: c298732e-91ff-41ab-9ab0-540e2e5413cb
X-Runtime: 0.046278
Vary: Origin
Content-Length: 442
200 OK
```


```json
{
  "id": 14,
  "user_id": 23,
  "name": "Wishlist #12",
  "is_public": false,
  "is_default": true,
  "wished_products": [
    {
      "id": 4,
      "wishlist_id": 14,
      "variant_id": 13,
      "quantity": 1,
      "remark": null,
      "created_at": "2021-07-13T07:58:14.940-04:00"
    },
    {
      "id": 5,
      "wishlist_id": 14,
      "variant_id": 15,
      "quantity": 1,
      "remark": null,
      "created_at": "2021-07-13T07:58:15.196-04:00"
    },
    {
      "id": 6,
      "wishlist_id": 14,
      "variant_id": 17,
      "quantity": 1,
      "remark": null,
      "created_at": "2021-07-13T07:58:15.439-04:00"
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
Authorizat IO N: Bearer 14a80f12d88dc0d7ee5b5ec96b68a16930c5b5a2cde88d9c
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
ETag: W/&quot;2fea9bf6f2ea721fef2fd3610c6565a9&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: fd22fd09-e925-4b52-8547-32aa63a76f5a
X-Runtime: 0.038460
Vary: Origin
Content-Length: 903
200 OK
```


```json
{
  "wishlists": [
    {
      "id": 19,
      "user_id": 26,
      "name": "Wishlist #17",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 20,
      "user_id": 26,
      "name": "Wishlist #18",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 21,
      "user_id": 26,
      "name": "Wishlist #19",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 22,
      "user_id": 26,
      "name": "Wishlist #20",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 23,
      "user_id": 26,
      "name": "Wishlist #21",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 24,
      "user_id": 26,
      "name": "Wishlist #22",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 25,
      "user_id": 26,
      "name": "Wishlist #23",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 26,
      "user_id": 26,
      "name": "Wishlist #24",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 27,
      "user_id": 26,
      "name": "Wishlist #25",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 28,
      "user_id": 26,
      "name": "Wishlist #26",
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
PATCH /api/wishlists/15
Accept: application/json
Authorizat IO N: Bearer 1762ab85e0f3424647d5ef92f3337c43d9ed2360c2c900d9
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/wishlists/:id`

#### Parameters


```json
wishlist[name]=Another+Wishlist&wishlist[user_id]=24&wishlist[is_default]=true&wishlist[is_public]=false
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
ETag: W/&quot;14aa5ffe50ad821df9ceeefcf0c72224&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: af219504-834f-4043-aa11-de48235b1ffb
X-Runtime: 0.049529
Vary: Origin
Content-Length: 446
200 OK
```


```json
{
  "id": 15,
  "user_id": 24,
  "name": "Another Wishlist",
  "is_public": false,
  "is_default": true,
  "wished_products": [
    {
      "id": 7,
      "wishlist_id": 15,
      "variant_id": 19,
      "quantity": 1,
      "remark": null,
      "created_at": "2021-07-13T07:58:15.906-04:00"
    },
    {
      "id": 8,
      "wishlist_id": 15,
      "variant_id": 21,
      "quantity": 1,
      "remark": null,
      "created_at": "2021-07-13T07:58:16.240-04:00"
    },
    {
      "id": 9,
      "wishlist_id": 15,
      "variant_id": 23,
      "quantity": 1,
      "remark": null,
      "created_at": "2021-07-13T07:58:16.532-04:00"
    }
  ]
}
```



