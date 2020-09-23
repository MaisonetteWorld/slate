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
PUT /api/orders/M186567334/addresses/27
Accept: application/json
X-Spree-Order-Token: r1p66QOxRGgkbJuMvBD6bQ
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
ETag: W/&quot;faa6f29447b2783a79ae86437ac6aa9c&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 4f4b3ca4-354a-47c4-974e-af2562086ea2
X-Runtime: 0.050637
Vary: Origin
Content-Length: 516
200 OK
```


```json
{
  "id": 28,
  "firstname": "John the Tester",
  "lastname": "Smith",
  "full_name": "John the Tester Smith",
  "address1": "A Different Road",
  "address2": "Northwest",
  "city": "Herndon",
  "zipcode": "10027",
  "phone": "555-555-0199",
  "company": "Company",
  "alternative_phone": "555-555-0199",
  "country_id": 36,
  "country_iso": "US",
  "state_id": 36,
  "state_name": null,
  "state_text": "AL",
  "country": {
    "id": 36,
    "iso_name": "UNITED STATES",
    "iso": "US",
    "iso3": "USA",
    "name": "United States",
    "numcode": 840
  },
  "state": {
    "id": 36,
    "name": "Alabama",
    "abbr": "AL",
    "country_id": 36
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
X-Spree-Order-Token: ZtQRZ5AolfR6COe6rnyQyQ
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/braintree/transactions`

#### Parameters


```json
order_id=M981262853&payment_method_id=22&options[restart_checkout]=true&transaction[email]=maryellen.oga%40mckenziemcglynn.com&transaction[nonce]=fake-paypal-billing-agreement-nonce&transaction[phone]=555-555-0199&transaction[shipping_address_attributes][first_name]=John&transaction[shipping_address_attributes][last_name]=Stamm&transaction[shipping_address_attributes][address_line_1]=A+Different+Road&transaction[shipping_address_attributes][city]=Herndon&transaction[shipping_address_attributes][state_code]=AL&transaction[shipping_address_attributes][zip]=10052&transaction[shipping_address_attributes][country_code]=US&transaction[payment_type]=PayPalAccount&transaction[billing_address_attributes][first_name]=John&transaction[billing_address_attributes][last_name]=Stamm&transaction[billing_address_attributes][address_line_1]=A+Different+Road&transaction[billing_address_attributes][city]=Herndon&transaction[billing_address_attributes][state_code]=AL&transaction[billing_address_attributes][zip]=10052&transaction[billing_address_attributes][country_code]=US
```


| Name | Description |
|:-----|:------------|
| order_id *required* | The order number |
| payment_method_id *required* | The payment method id |
| options[restart_checkout] *required* | Whether the checkout should restart from the beginning (must be set for express checkouts) |
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
ETag: W/&quot;1a8af279e4c8f14a61a7b92331bdd1ad&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 8957ed49-143a-4cc5-8ea4-666a888c9c2b
X-Runtime: 0.389390
Vary: Origin
Content-Length: 5219
200 OK
```


```json
{
  "id": 31,
  "number": "M981262853",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2020-09-23T07:16:35.646-04:00",
  "updated_at": "2020-09-23T07:16:36.008-04:00",
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
  "token": "ZtQRZ5AolfR6COe6rnyQyQ",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order?order=M981262853&bzip=10052&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [
    {
      "id": 22,
      "name": "Braintree"
    }
  ],
  "bill_address": {
    "id": 57,
    "firstname": "John",
    "lastname": "Stamm",
    "full_name": "John Stamm",
    "address1": "A Different Road",
    "address2": null,
    "city": "Herndon",
    "zipcode": "10052",
    "phone": "555-555-0199",
    "company": null,
    "alternative_phone": null,
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
    "id": 58,
    "firstname": "John",
    "lastname": "Stamm",
    "full_name": "John Stamm",
    "address1": "A Different Road",
    "address2": null,
    "city": "Herndon",
    "zipcode": "10052",
    "phone": "555-555-0199",
    "company": null,
    "alternative_phone": null,
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
      "id": 35,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 169,
      "vendor_id": 326,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 169,
        "name": "Product #90 - 4708",
        "sku": "SKU-168",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-90-4708",
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
        "product_id": 90,
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
      "adjustments": [

      ]
    }
  ],
  "payments": [
    {
      "id": 7,
      "source_type": "SolidusPaypalBraintree::Source",
      "source_id": 10,
      "amount": "110.0",
      "display_amount": "$110.00",
      "payment_method_id": 22,
      "state": "checkout",
      "avs_response": null,
      "created_at": "2020-09-23T07:16:35.785-04:00",
      "updated_at": "2020-09-23T07:16:35.785-04:00",
      "payment_method": {
        "id": 22,
        "name": "Braintree"
      },
      "source": {
        "id": 10,
        "payment_type": "PayPalAccount",
        "token": "bgx899",
        "created_at": "2020-09-23T07:16:35.784-04:00",
        "email": "jane.doe@paypal.com"
      }
    }
  ],
  "shipments": [
    {
      "id": 36,
      "tracking": null,
      "tracking_url": null,
      "number": "H14440114850",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M981262853",
      "stock_location_name": "NY Warehouse 63",
      "giftwrappable": false,
      "stock_location_id": 63,
      "giftwrap": null,
      "shipping_rates": [
        {
          "id": 36,
          "name": "UPS Ground",
          "admin_name": null,
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 26,
          "shipping_method_code": "UPS_GROUND",
          "extra_cost": "+$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 36,
        "name": "UPS Ground",
        "admin_name": null,
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 26,
        "shipping_method_code": "UPS_GROUND",
        "extra_cost": "+$100.00",
        "base_flat_rate_amount": 0.0
      },
      "shipping_methods": [
        {
          "id": 26,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 28,
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
          "variant_id": 169,
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
      "delivery_estimation": "Sep 25"
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
X-Spree-Order-Token: iCrtgJqQVJv9HdnYpEwX0g
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/braintree/transactions`

#### Parameters


```json
order_id=M603528771&payment_method_id=21&options[restart_checkout]=true&transaction[email]=maryellen.oga%40mckenziemcglynn.com&transaction[nonce]=fake-apple-pay-visa-nonce&transaction[phone]=555-555-0199&transaction[shipping_address_attributes][first_name]=John&transaction[shipping_address_attributes][last_name]=Stamm&transaction[shipping_address_attributes][address_line_1]=A+Different+Road&transaction[shipping_address_attributes][city]=Herndon&transaction[shipping_address_attributes][state_code]=AL&transaction[shipping_address_attributes][zip]=10050&transaction[shipping_address_attributes][country_code]=US&transaction[payment_type]=ApplePayCard
```


| Name | Description |
|:-----|:------------|
| order_id *required* | The order number |
| payment_method_id *required* | The payment method id |
| options[restart_checkout] *required* | Whether the checkout should restart from the beginning (must be set for express checkouts) |
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
ETag: W/&quot;63f8a7a1e63a35a744e5387b12a8a34f&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 4e8ae7bd-e6e3-4fdc-bab2-4025603d3cf2
X-Runtime: 0.379453
Vary: Origin
Content-Length: 5263
200 OK
```


```json
{
  "id": 30,
  "number": "M603528771",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2020-09-23T07:16:34.861-04:00",
  "updated_at": "2020-09-23T07:16:35.209-04:00",
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
  "token": "iCrtgJqQVJv9HdnYpEwX0g",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order?order=M603528771&bzip=10050&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [
    {
      "id": 21,
      "name": "Braintree"
    }
  ],
  "bill_address": {
    "id": 53,
    "firstname": "John",
    "lastname": "Stamm",
    "full_name": "John Stamm",
    "address1": "A Different Road",
    "address2": null,
    "city": "Herndon",
    "zipcode": "10050",
    "phone": "555-555-0199",
    "company": null,
    "alternative_phone": null,
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
    "id": 54,
    "firstname": "John",
    "lastname": "Stamm",
    "full_name": "John Stamm",
    "address1": "A Different Road",
    "address2": null,
    "city": "Herndon",
    "zipcode": "10050",
    "phone": "555-555-0199",
    "company": null,
    "alternative_phone": null,
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
      "id": 34,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 167,
      "vendor_id": 321,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 167,
        "name": "Product #89 - 7226",
        "sku": "SKU-166",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-89-7226",
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
        "product_id": 89,
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
      "adjustments": [

      ]
    }
  ],
  "payments": [
    {
      "id": 6,
      "source_type": "SolidusPaypalBraintree::Source",
      "source_id": 9,
      "amount": "110.0",
      "display_amount": "$110.00",
      "payment_method_id": 21,
      "state": "checkout",
      "avs_response": null,
      "created_at": "2020-09-23T07:16:35.007-04:00",
      "updated_at": "2020-09-23T07:16:35.007-04:00",
      "payment_method": {
        "id": 21,
        "name": "Braintree"
      },
      "source": {
        "id": 9,
        "payment_type": "ApplePayCard",
        "token": "cg7hsk",
        "created_at": "2020-09-23T07:16:35.006-04:00",
        "cc_type": "Apple Pay - Visa",
        "last_digits": "1881",
        "month": "12",
        "year": "2020"
      }
    }
  ],
  "shipments": [
    {
      "id": 34,
      "tracking": null,
      "tracking_url": null,
      "number": "H81114687400",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M603528771",
      "stock_location_name": "NY Warehouse 62",
      "giftwrappable": false,
      "stock_location_id": 62,
      "giftwrap": null,
      "shipping_rates": [
        {
          "id": 34,
          "name": "UPS Ground",
          "admin_name": null,
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 25,
          "shipping_method_code": "UPS_GROUND",
          "extra_cost": "+$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 34,
        "name": "UPS Ground",
        "admin_name": null,
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 25,
        "shipping_method_code": "UPS_GROUND",
        "extra_cost": "+$100.00",
        "base_flat_rate_amount": 0.0
      },
      "shipping_methods": [
        {
          "id": 25,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 27,
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
          "variant_id": 167,
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
      "delivery_estimation": "Sep 25"
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
PUT /api/checkouts/M490113741/complete
Accept: application/json
X-Spree-Order-Token: HKxN30Cqds2Cvcc7BSAA2w
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
ETag: W/&quot;5eaa8fe50c4c23de1c6e1abf4aaae9a3&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: fa87b9e3-4e8b-423f-aae1-3727e16cf7db
X-Runtime: 0.469200
Vary: Origin
Content-Length: 5315
200 OK
```


```json
{
  "id": 2,
  "number": "M490113741",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "complete",
  "adjustment_total": "0.0",
  "user_id": 32,
  "created_at": "2020-09-23T07:16:08.889-04:00",
  "updated_at": "2020-09-23T07:16:09.375-04:00",
  "completed_at": "2020-09-23T07:16:09.375-04:00",
  "payment_total": "110.0",
  "shipment_state": "ready",
  "payment_state": "paid",
  "email": "email32@example.com",
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
  "token": "HKxN30Cqds2Cvcc7BSAA2w",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order?order=M490113741&bzip=10002&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [
    {
      "id": 4,
      "name": "Braintree"
    },
    {
      "id": 5,
      "name": "Braintree"
    }
  ],
  "bill_address": {
    "id": 2,
    "firstname": "John",
    "lastname": "Smith",
    "full_name": "John Smith",
    "address1": "PO Box 1337",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10002",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 11,
    "country_iso": "US",
    "state_id": 11,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 11,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 11,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 11
    }
  },
  "ship_address": {
    "id": 3,
    "firstname": "John",
    "lastname": "Smith",
    "full_name": "John Smith",
    "address1": "A Different Road",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10003",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 11,
    "country_iso": "US",
    "state_id": 11,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 11,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 11,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 11
    }
  },
  "line_items": [
    {
      "id": 2,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 33,
      "vendor_id": 56,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 33,
        "name": "Product #22 - 5629",
        "sku": "SKU-32",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-22-5629",
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
            "id": 11,
            "name": "Size-11",
            "presentation": "S",
            "option_type_name": "foo-size-11",
            "option_type_id": 11,
            "option_type_presentation": "Size",
            "position": 1
          }
        ],
        "images": [

        ],
        "product_id": 22,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [

      ],
      "vendor_name": "Vendor #56",
      "country_iso": "US",
      "adjustments": [

      ]
    }
  ],
  "payments": [
    {
      "id": 1,
      "source_type": "SolidusPaypalBraintree::Source",
      "source_id": 4,
      "amount": "110.0",
      "display_amount": "$110.00",
      "payment_method_id": 4,
      "state": "completed",
      "avs_response": "M",
      "created_at": "2020-09-23T07:16:09.010-04:00",
      "updated_at": "2020-09-23T07:16:09.174-04:00",
      "payment_method": {
        "id": 4,
        "name": "Braintree"
      },
      "source": {
        "id": 4,
        "payment_type": "CreditCard",
        "token": "4rptfz",
        "created_at": "2020-09-23T07:16:09.009-04:00",
        "cc_type": "Visa",
        "last_digits": "1881",
        "month": "12",
        "year": "2020"
      }
    }
  ],
  "shipments": [
    {
      "id": 2,
      "tracking": "U10000",
      "tracking_url": null,
      "number": "H28115418856",
      "cost": "100.0",
      "shipped_at": null,
      "state": "ready",
      "order_id": "M490113741",
      "stock_location_name": "NY Warehouse 11",
      "giftwrappable": false,
      "stock_location_id": 11,
      "giftwrap": null,
      "shipping_rates": [
        {
          "id": 2,
          "name": "UPS Ground",
          "admin_name": null,
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 2,
          "shipping_method_code": "UPS_GROUND",
          "extra_cost": "+$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 2,
        "name": "UPS Ground",
        "admin_name": null,
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 2,
        "shipping_method_code": "UPS_GROUND",
        "extra_cost": "+$100.00",
        "base_flat_rate_amount": 0.0
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
              "id": 11,
              "name": "ShippingCategory #11"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 33,
          "quantity": 1,
          "states": {
            "on_hand": 1
          }
        }
      ],
      "adjustments": [

      ],
      "stock_location_address": "NY Warehouse 11, Washington, AL",
      "country_iso": "US",
      "international_shipping": false,
      "delivery_estimation": "Sep 25"
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
PATCH /api/checkouts/M890173564
Accept: application/json
X-Spree-Order-Token: 0qPOZyrTC8yGgDzRZ2z1fA
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=8&order[payment_attributes][][source_attributes][nonce]=fake-apple-pay-visa-nonce&order[payment_attributes][][source_attributes][payment_type]=ApplePayCard&order[payment_attributes][][source_attributes][reusable]=true
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
ETag: W/&quot;3c71615536b80f3d022b2dd1f8f749d5&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: d975a521-a5c1-4061-841e-6cf21126a3d3
X-Runtime: 0.158986
Vary: Origin
Content-Length: 4770
200 OK
```


```json
{
  "id": 5,
  "number": "M890173564",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 35,
  "created_at": "2020-09-23T07:16:11.361-04:00",
  "updated_at": "2020-09-23T07:16:11.729-04:00",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "email35@example.com",
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
  "token": "0qPOZyrTC8yGgDzRZ2z1fA",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order?order=M890173564&bzip=10008&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [
    {
      "id": 8,
      "name": "Braintree"
    }
  ],
  "bill_address": {
    "id": 8,
    "firstname": "John",
    "lastname": "Smith",
    "full_name": "John Smith",
    "address1": "PO Box 1337",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10008",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 14,
    "country_iso": "US",
    "state_id": 14,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 14,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 14,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 14
    }
  },
  "ship_address": {
    "id": 9,
    "firstname": "John",
    "lastname": "Smith",
    "full_name": "John Smith",
    "address1": "A Different Road",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10009",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 14,
    "country_iso": "US",
    "state_id": 14,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 14,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 14,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 14
    }
  },
  "line_items": [
    {
      "id": 5,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 39,
      "vendor_id": 71,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 39,
        "name": "Product #25 - 4699",
        "sku": "SKU-38",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-25-4699",
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
            "option_type_presentation": "Size",
            "position": 1
          }
        ],
        "images": [

        ],
        "product_id": 25,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [

      ],
      "vendor_name": "Vendor #71",
      "country_iso": "US",
      "adjustments": [

      ]
    }
  ],
  "payments": [

  ],
  "shipments": [
    {
      "id": 8,
      "tracking": null,
      "tracking_url": null,
      "number": "H12871256175",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M890173564",
      "stock_location_name": "NY Warehouse 14",
      "giftwrappable": false,
      "stock_location_id": 14,
      "giftwrap": null,
      "shipping_rates": [
        {
          "id": 8,
          "name": "UPS Ground",
          "admin_name": null,
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 5,
          "shipping_method_code": "UPS_GROUND",
          "extra_cost": "+$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 8,
        "name": "UPS Ground",
        "admin_name": null,
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 5,
        "shipping_method_code": "UPS_GROUND",
        "extra_cost": "+$100.00",
        "base_flat_rate_amount": 0.0
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
              "id": 14,
              "name": "ShippingCategory #14"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 39,
          "quantity": 1,
          "states": {
            "on_hand": 1
          }
        }
      ],
      "adjustments": [

      ],
      "stock_location_address": "NY Warehouse 14, Washington, AL",
      "country_iso": "US",
      "international_shipping": false,
      "delivery_estimation": "Sep 25"
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
PATCH /api/checkouts/M002076236
Accept: application/json
X-Spree-Order-Token: 4ijCkps-9DPDYYk-kuG1Aw
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=6&order[payment_attributes][][source_attributes][nonce]=fake-paypal-billing-agreement-nonce&order[payment_attributes][][source_attributes][payment_type]=PayPalAccount&order[payment_attributes][][source_attributes][reusable]=true
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
ETag: W/&quot;a4cbf9b9fcb09b18e5c6752a00f9b3a5&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 754afbae-8e1d-43d2-8123-77f4560ff4e4
X-Runtime: 0.119254
Vary: Origin
Content-Length: 4770
200 OK
```


```json
{
  "id": 3,
  "number": "M002076236",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 33,
  "created_at": "2020-09-23T07:16:09.836-04:00",
  "updated_at": "2020-09-23T07:16:10.252-04:00",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "email33@example.com",
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
  "token": "4ijCkps-9DPDYYk-kuG1Aw",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order?order=M002076236&bzip=10004&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [
    {
      "id": 6,
      "name": "Braintree"
    }
  ],
  "bill_address": {
    "id": 4,
    "firstname": "John",
    "lastname": "Smith",
    "full_name": "John Smith",
    "address1": "PO Box 1337",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10004",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 12,
    "country_iso": "US",
    "state_id": 12,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 12,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 12,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 12
    }
  },
  "ship_address": {
    "id": 5,
    "firstname": "John",
    "lastname": "Smith",
    "full_name": "John Smith",
    "address1": "A Different Road",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10005",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 12,
    "country_iso": "US",
    "state_id": 12,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 12,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 12,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 12
    }
  },
  "line_items": [
    {
      "id": 3,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 35,
      "vendor_id": 61,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 35,
        "name": "Product #23 - 1098",
        "sku": "SKU-34",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-23-1098",
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
            "option_type_presentation": "Size",
            "position": 1
          }
        ],
        "images": [

        ],
        "product_id": 23,
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
      "adjustments": [

      ]
    }
  ],
  "payments": [

  ],
  "shipments": [
    {
      "id": 4,
      "tracking": null,
      "tracking_url": null,
      "number": "H34537642531",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M002076236",
      "stock_location_name": "NY Warehouse 12",
      "giftwrappable": false,
      "stock_location_id": 12,
      "giftwrap": null,
      "shipping_rates": [
        {
          "id": 4,
          "name": "UPS Ground",
          "admin_name": null,
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 3,
          "shipping_method_code": "UPS_GROUND",
          "extra_cost": "+$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 4,
        "name": "UPS Ground",
        "admin_name": null,
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 3,
        "shipping_method_code": "UPS_GROUND",
        "extra_cost": "+$100.00",
        "base_flat_rate_amount": 0.0
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
              "id": 12,
              "name": "ShippingCategory #12"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 35,
          "quantity": 1,
          "states": {
            "on_hand": 1
          }
        }
      ],
      "adjustments": [

      ],
      "stock_location_address": "NY Warehouse 12, Washington, AL",
      "country_iso": "US",
      "international_shipping": false,
      "delivery_estimation": "Sep 25"
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
PATCH /api/checkouts/M973580439
Accept: application/json
X-Spree-Order-Token: W2HMTIdB8AW0BUkUSRxcvA
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=7&order[payment_attributes][][source_attributes][nonce]=fake-valid-visa-nonce&order[payment_attributes][][source_attributes][payment_type]=CreditCard&order[payment_attributes][][source_attributes][reusable]=true
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
ETag: W/&quot;38ad7663c63322af39cb9405752178df&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 731dcdf0-9dca-401e-9325-131228bf0235
X-Runtime: 0.125651
Vary: Origin
Content-Length: 4768
200 OK
```


```json
{
  "id": 4,
  "number": "M973580439",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 34,
  "created_at": "2020-09-23T07:16:10.593-04:00",
  "updated_at": "2020-09-23T07:16:10.964-04:00",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "email34@example.com",
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
  "token": "W2HMTIdB8AW0BUkUSRxcvA",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order?order=M973580439&bzip=10006&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [
    {
      "id": 7,
      "name": "Braintree"
    }
  ],
  "bill_address": {
    "id": 6,
    "firstname": "John",
    "lastname": "Smith",
    "full_name": "John Smith",
    "address1": "PO Box 1337",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10006",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 13,
    "country_iso": "US",
    "state_id": 13,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 13,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 13,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 13
    }
  },
  "ship_address": {
    "id": 7,
    "firstname": "John",
    "lastname": "Smith",
    "full_name": "John Smith",
    "address1": "A Different Road",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10007",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 13,
    "country_iso": "US",
    "state_id": 13,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 13,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 13,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 13
    }
  },
  "line_items": [
    {
      "id": 4,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 37,
      "vendor_id": 66,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 37,
        "name": "Product #24 - 363",
        "sku": "SKU-36",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-24-363",
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
            "option_type_presentation": "Size",
            "position": 1
          }
        ],
        "images": [

        ],
        "product_id": 24,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [

      ],
      "vendor_name": "Vendor #66",
      "country_iso": "US",
      "adjustments": [

      ]
    }
  ],
  "payments": [

  ],
  "shipments": [
    {
      "id": 6,
      "tracking": null,
      "tracking_url": null,
      "number": "H43256364118",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M973580439",
      "stock_location_name": "NY Warehouse 13",
      "giftwrappable": false,
      "stock_location_id": 13,
      "giftwrap": null,
      "shipping_rates": [
        {
          "id": 6,
          "name": "UPS Ground",
          "admin_name": null,
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 4,
          "shipping_method_code": "UPS_GROUND",
          "extra_cost": "+$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 6,
        "name": "UPS Ground",
        "admin_name": null,
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 4,
        "shipping_method_code": "UPS_GROUND",
        "extra_cost": "+$100.00",
        "base_flat_rate_amount": 0.0
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
              "id": 13,
              "name": "ShippingCategory #13"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 37,
          "quantity": 1,
          "states": {
            "on_hand": 1
          }
        }
      ],
      "adjustments": [

      ],
      "stock_location_address": "NY Warehouse 13, Washington, AL",
      "country_iso": "US",
      "international_shipping": false,
      "delivery_estimation": "Sep 25"
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
PATCH /api/checkouts/M617813570
Accept: application/json
X-Spree-Order-Token: XockAsJ_wxv6MV0r9j4blg
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=9&order[payment_attributes][][source_attributes][wallet_payment_source_id]=5
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
ETag: W/&quot;37ee553586f07be938fe52fa5659bc4d&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 9544aa4c-f297-4d5a-b973-040c0e986067
X-Runtime: 0.172043
Vary: Origin
Content-Length: 4775
200 OK
```


```json
{
  "id": 6,
  "number": "M617813570",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 36,
  "created_at": "2020-09-23T07:16:12.089-04:00",
  "updated_at": "2020-09-23T07:16:12.457-04:00",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "email36@example.com",
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
  "token": "XockAsJ_wxv6MV0r9j4blg",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order?order=M617813570&bzip=10010&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [
    {
      "id": 9,
      "name": "Braintree"
    }
  ],
  "bill_address": {
    "id": 10,
    "firstname": "John",
    "lastname": "Smith",
    "full_name": "John Smith",
    "address1": "PO Box 1337",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10010",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 15,
    "country_iso": "US",
    "state_id": 15,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 15,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 15,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 15
    }
  },
  "ship_address": {
    "id": 11,
    "firstname": "John",
    "lastname": "Smith",
    "full_name": "John Smith",
    "address1": "A Different Road",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10011",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 15,
    "country_iso": "US",
    "state_id": 15,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 15,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 15,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 15
    }
  },
  "line_items": [
    {
      "id": 6,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 41,
      "vendor_id": 76,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 41,
        "name": "Product #26 - 7982",
        "sku": "SKU-40",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-26-7982",
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
        "product_id": 26,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [

      ],
      "vendor_name": "Vendor #76",
      "country_iso": "US",
      "adjustments": [

      ]
    }
  ],
  "payments": [

  ],
  "shipments": [
    {
      "id": 10,
      "tracking": null,
      "tracking_url": null,
      "number": "H01446547606",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M617813570",
      "stock_location_name": "NY Warehouse 15",
      "giftwrappable": false,
      "stock_location_id": 15,
      "giftwrap": null,
      "shipping_rates": [
        {
          "id": 10,
          "name": "UPS Ground",
          "admin_name": null,
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 6,
          "shipping_method_code": "UPS_GROUND",
          "extra_cost": "+$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 10,
        "name": "UPS Ground",
        "admin_name": null,
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 6,
        "shipping_method_code": "UPS_GROUND",
        "extra_cost": "+$100.00",
        "base_flat_rate_amount": 0.0
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
              "id": 15,
              "name": "ShippingCategory #15"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 41,
          "quantity": 1,
          "states": {
            "on_hand": 1
          }
        }
      ],
      "adjustments": [

      ],
      "stock_location_address": "NY Warehouse 15, Washington, AL",
      "country_iso": "US",
      "international_shipping": false,
      "delivery_estimation": "Sep 25"
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
PUT /api/checkouts/M578219207
Accept: application/json
X-Spree-Order-Token: iLWNKT4zPHK4SrLZmxzJHg
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PUT /api/checkouts/:id`

#### Parameters


```json
order[ship_address_attributes][id]&order[ship_address_attributes][firstname]=John&order[ship_address_attributes][lastname]=Smith&order[ship_address_attributes][address1]=10+Lovely+Street&order[ship_address_attributes][address2]=Northwest&order[ship_address_attributes][city]=Herndon&order[ship_address_attributes][zipcode]=10001&order[ship_address_attributes][phone]=555-555-0199&order[ship_address_attributes][state_name]&order[ship_address_attributes][alternative_phone]=555-555-0199&order[ship_address_attributes][company]=Company&order[ship_address_attributes][state_id]=10&order[ship_address_attributes][country_id]=10&order[ship_address_attributes][created_at]&order[ship_address_attributes][updated_at]&order[use_billing]=true&hold_state=true
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
ETag: W/&quot;8d5e80f8e41b979c626534003e33a2de&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 56ecd42a-eae6-4e8f-afad-e2ac080a6fdc
X-Runtime: 0.239264
Vary: Origin
Content-Length: 4745
200 OK
```


```json
{
  "id": 1,
  "number": "M578219207",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "cart",
  "adjustment_total": "0.0",
  "user_id": 31,
  "created_at": "2020-09-23T07:16:07.995-04:00",
  "updated_at": "2020-09-23T07:16:08.285-04:00",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "email31@example.com",
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
  "token": "iLWNKT4zPHK4SrLZmxzJHg",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order?order=M578219207&bzip=10001&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [

  ],
  "bill_address": {
    "id": 1,
    "firstname": "John",
    "lastname": "Smith",
    "full_name": "John Smith",
    "address1": "10 Lovely Street",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10001",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 10,
    "country_iso": "US",
    "state_id": 10,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 10,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 10,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 10
    }
  },
  "ship_address": {
    "id": 1,
    "firstname": "John",
    "lastname": "Smith",
    "full_name": "John Smith",
    "address1": "10 Lovely Street",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10001",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 10,
    "country_iso": "US",
    "state_id": 10,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 10,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 10,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 10
    }
  },
  "line_items": [
    {
      "id": 1,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 31,
      "vendor_id": 51,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 31,
        "name": "Product #21 - 2395",
        "sku": "SKU-30",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-21-2395",
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
            "option_type_presentation": "Size",
            "position": 1
          }
        ],
        "images": [

        ],
        "product_id": 21,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [

      ],
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
      "id": 1,
      "tracking": "U10000",
      "tracking_url": null,
      "number": "H31226762355",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M578219207",
      "stock_location_name": "NY Warehouse 10",
      "giftwrappable": false,
      "stock_location_id": 10,
      "giftwrap": null,
      "shipping_rates": [
        {
          "id": 1,
          "name": "UPS Ground",
          "admin_name": null,
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 1,
          "shipping_method_code": "UPS_GROUND",
          "extra_cost": "+$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 1,
        "name": "UPS Ground",
        "admin_name": null,
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 1,
        "shipping_method_code": "UPS_GROUND",
        "extra_cost": "+$100.00",
        "base_flat_rate_amount": 0.0
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
              "id": 10,
              "name": "ShippingCategory #10"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 31,
          "quantity": 1,
          "states": {
            "on_hand": 1
          }
        }
      ],
      "adjustments": [

      ],
      "stock_location_address": "NY Warehouse 10, Washington, AL",
      "country_iso": "US",
      "international_shipping": false,
      "delivery_estimation": "Sep 25"
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

Delete giftwrap related to shipment

## Create Giftwrap


### Request

#### Endpoint

```plaintext
POST /api/shipments/H14525080543/giftwrap
Accept: application/json
X-Spree-Order-Token: jPopOH892M1YbQEVWyaDeA
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/shipments/:shipment_number/giftwrap`

#### Parameters


```json
order_number=M095407693
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
ETag: W/&quot;11d45af477139e8881a13a1750caf383&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: e025ecc1-e4db-448b-83a1-2e4eec8dbe70
X-Runtime: 0.045924
Vary: Origin
Content-Length: 74
201 Created
```


```json
{
  "id": 2,
  "giftwrap_cost": 2.5,
  "giftwrap_price": 4.0,
  "giftwrap_money": "$4.00"
}
```



## Delete Giftwrap


### Request

#### Endpoint

```plaintext
DELETE /api/shipments/H71500082808/giftwrap
Accept: application/json
X-Spree-Order-Token: j90mKR8QfGy-zSOSPqq-2A
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`DELETE /api/shipments/:shipment_number/giftwrap`

#### Parameters


```json
order_number=M500631972
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
X-Request-Id: 4f3430f4-3967-4c49-bce5-1741ce4b99cc
X-Runtime: 0.073252
Vary: Origin
204 No Content
```




# LineItem

Representation of a single cart item for a specific variant with price of vendor

## Creating a line item


### Request

#### Endpoint

```plaintext
POST /api/orders/M655023917/line_items
Accept: application/json
X-Spree-Order-Token: ivDSnHx0FCZ85S5xB4vkSQ
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/:order_number/line_items`

#### Parameters


```json
line_item[variant_id]=109&line_item[options][vendor_id]=183
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
ETag: W/&quot;23aee6813eb0386d35d5ebceafac49c6&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 830faea6-d010-4f01-87c6-f23281a64919
X-Runtime: 0.118386
Vary: Origin
Content-Length: 942
201 Created
```


```json
{
  "id": 13,
  "quantity": 1,
  "price": "19.99",
  "variant_id": 109,
  "vendor_id": 183,
  "single_display_amount": "$19.99",
  "display_amount": "$19.99",
  "total": "19.99",
  "on_sale": false,
  "final_sale": false,
  "backordered": null,
  "promotionable": true,
  "variant": {
    "id": 109,
    "name": "Product #60 - 7513",
    "sku": "SKU-108",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": false,
    "slug": "product-60-7513",
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
        "id": 49,
        "name": "Size-49",
        "presentation": "S",
        "option_type_name": "foo-size-49",
        "option_type_id": 49,
        "option_type_presentation": "Size",
        "position": 1
      }
    ],
    "images": [

    ],
    "product_id": 60,
    "lead_time": 2,
    "brand": null,
    "brand_slug": null,
    "brand_description": null
  },
  "monogram": null,
  "gift_cards": [

  ],
  "vendor_name": "Vendor #183",
  "country_iso": null,
  "adjustments": [

  ]
}
```



## Creating a line item gift card


### Request

#### Endpoint

```plaintext
POST /api/orders/M830348571/line_items
Accept: application/json
X-Spree-Order-Token: iXbEAbdbGLP3m0XBAhe03Q
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/:order_number/line_items`

#### Parameters


```json
line_item[variant_id]=103&line_item[options][vendor_id]=174&line_item[options][gift_card_details][recipient_name]=Recipient+John&line_item[options][gift_card_details][recipient_email]=recipient%40email.com&line_item[options][gift_card_details][purchaser_name]=Purchaser+Bob&line_item[options][gift_card_details][gift_message]=Surprise&line_item[options][gift_card_details][send_email_at]=2020-09-23+07%3A16%3A20+-0400
```


| Name | Description |
|:-----|:------------|
| line_item[variant_id] *required* | Line item variant |
| line_item[options]  | Hash containing the vendor_id and gift card details.
                          It's used to set the price based on vendor |
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
ETag: W/&quot;a045c993f3e22e93a7d86bcab52f850b&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: f8d84c43-e9ea-4200-bebc-4a397fa055d3
X-Runtime: 0.366445
Vary: Origin
Content-Length: 1078
201 Created
```


```json
{
  "id": 11,
  "quantity": 1,
  "price": "19.99",
  "variant_id": 103,
  "vendor_id": 174,
  "single_display_amount": "$19.99",
  "display_amount": "$19.99",
  "total": "19.99",
  "on_sale": false,
  "final_sale": false,
  "backordered": null,
  "promotionable": true,
  "variant": {
    "id": 103,
    "name": "Product #56 - 8517",
    "sku": "SKU-103",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": false,
    "slug": "product-56-8517",
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
    "product_id": 56,
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
      "send_email_at": "2020-09-23T00:00:00.000-04:00"
    }
  ],
  "vendor_name": "Vendor #174",
  "country_iso": null,
  "adjustments": [

  ]
}
```



## Deleting a line item


### Request

#### Endpoint

```plaintext
DELETE /api/orders/M575678598/line_items/14
Accept: application/json
X-Spree-Order-Token: dvfLRPy1DiNJoe5cod-mfg
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
X-Request-Id: bd5b9240-10c8-47b3-92db-f5a40bf97f88
X-Runtime: 0.081078
Vary: Origin
204 No Content
```




## Updating a line item


### Request

#### Endpoint

```plaintext
PUT /api/orders/M864411935/line_items/9
Accept: application/json
X-Spree-Order-Token: qRBRGe5JNTMGTCG1JhcZ3w
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
ETag: W/&quot;d0480195ce36db9da14bd56ae0b6f086&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 597934db-a253-4582-9bf9-8b0fc4fe5f86
X-Runtime: 0.147513
Vary: Origin
Content-Length: 935
200 OK
```


```json
{
  "id": 9,
  "quantity": 2,
  "price": "10.0",
  "variant_id": 97,
  "vendor_id": 161,
  "single_display_amount": "$10.00",
  "display_amount": "$20.00",
  "total": "20.0",
  "on_sale": false,
  "final_sale": false,
  "backordered": null,
  "promotionable": true,
  "variant": {
    "id": 97,
    "name": "Product #54 - 8760",
    "sku": "SKU-96",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": false,
    "slug": "product-54-8760",
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
        "id": 43,
        "name": "Size-43",
        "presentation": "S",
        "option_type_name": "foo-size-43",
        "option_type_id": 43,
        "option_type_presentation": "Size",
        "position": 1
      }
    ],
    "images": [

    ],
    "product_id": 54,
    "lead_time": 2,
    "brand": null,
    "brand_slug": null,
    "brand_description": null
  },
  "monogram": null,
  "gift_cards": [

  ],
  "vendor_name": "Vendor #161",
  "country_iso": "US",
  "adjustments": [

  ]
}
```



# Minis

Update a mini. Users can update their own minis, admins can update minis for others.

## Create a mini


### Request

#### Endpoint

```plaintext
POST /api/minis
Accept: application/json
Authorizat IO N: Bearer 5a638b1f7d4f1f1fb50eaa797262a6dd7977b6c6260acbb8
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/minis`

#### Parameters


```json
mini[name]=Winny&mini[user_id]=52&mini[birth_year]=2019&mini[birth_month]=1&mini[birth_day]=1
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
ETag: W/&quot;a7009b30d54246581de520ecffdd0ba9&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: eaec6ac9-5aef-4104-b8a1-e7f779b0ef7b
X-Runtime: 0.017797
Vary: Origin
Content-Length: 163
201 Created
```


```json
{
  "id": 13,
  "user_id": 52,
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
DELETE /api/minis/2
Accept: application/json
Authorizat IO N: Bearer fffc5a22f45ba835f78fd4e2164fafebc5b1eb6549962753
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
X-Request-Id: 3adec8b7-b5bd-49ab-a5de-d1c93ba1917b
X-Runtime: 0.008989
Vary: Origin
204 No Content
```




## Get a single mini


### Request

#### Endpoint

```plaintext
GET /api/minis/14
Accept: application/json
Authorizat IO N: Bearer c2f630e2fae062977baac017e176fa4303dce31f0e16dd00
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
ETag: W/&quot;9c236d27101b60187fb043a002cbaf9d&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: daec393d-a488-4b34-a4fc-510f7bc07c20
X-Runtime: 0.013014
Vary: Origin
Content-Length: 163
200 OK
```


```json
{
  "id": 14,
  "user_id": 53,
  "name": "Mini",
  "birth_year": 2020,
  "birth_month": 9,
  "birth_day": 22,
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
Authorizat IO N: Bearer 89b3fcc438f0806d5c6934c08d6bdeddb013591c5ef4b619
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
ETag: W/&quot;9b908f546bf80d910d2c7e1b763a2e9c&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: c810b075-a577-49ac-8084-7cf2924f9a48
X-Runtime: 0.067208
Vary: Origin
Content-Length: 1713
200 OK
```


```json
{
  "minis": [
    {
      "id": 12,
      "user_id": 50,
      "name": "Mini",
      "birth_year": 2020,
      "birth_month": 9,
      "birth_day": 22,
      "gender_boy": true,
      "gender_girl": true,
      "gender_taxons": [

      ],
      "age_range_taxons": [

      ]
    },
    {
      "id": 11,
      "user_id": 49,
      "name": "Mini",
      "birth_year": 2020,
      "birth_month": 9,
      "birth_day": 22,
      "gender_boy": true,
      "gender_girl": true,
      "gender_taxons": [

      ],
      "age_range_taxons": [

      ]
    },
    {
      "id": 10,
      "user_id": 48,
      "name": "Mini",
      "birth_year": 2020,
      "birth_month": 9,
      "birth_day": 22,
      "gender_boy": true,
      "gender_girl": true,
      "gender_taxons": [

      ],
      "age_range_taxons": [

      ]
    },
    {
      "id": 9,
      "user_id": 47,
      "name": "Mini",
      "birth_year": 2020,
      "birth_month": 9,
      "birth_day": 22,
      "gender_boy": true,
      "gender_girl": true,
      "gender_taxons": [

      ],
      "age_range_taxons": [

      ]
    },
    {
      "id": 8,
      "user_id": 46,
      "name": "Mini",
      "birth_year": 2020,
      "birth_month": 9,
      "birth_day": 22,
      "gender_boy": true,
      "gender_girl": true,
      "gender_taxons": [

      ],
      "age_range_taxons": [

      ]
    },
    {
      "id": 7,
      "user_id": 45,
      "name": "Mini",
      "birth_year": 2020,
      "birth_month": 9,
      "birth_day": 22,
      "gender_boy": true,
      "gender_girl": true,
      "gender_taxons": [

      ],
      "age_range_taxons": [

      ]
    },
    {
      "id": 6,
      "user_id": 44,
      "name": "Mini",
      "birth_year": 2020,
      "birth_month": 9,
      "birth_day": 22,
      "gender_boy": true,
      "gender_girl": true,
      "gender_taxons": [

      ],
      "age_range_taxons": [

      ]
    },
    {
      "id": 5,
      "user_id": 43,
      "name": "Mini",
      "birth_year": 2020,
      "birth_month": 9,
      "birth_day": 22,
      "gender_boy": true,
      "gender_girl": true,
      "gender_taxons": [

      ],
      "age_range_taxons": [

      ]
    },
    {
      "id": 4,
      "user_id": 42,
      "name": "Mini",
      "birth_year": 2020,
      "birth_month": 9,
      "birth_day": 22,
      "gender_boy": true,
      "gender_girl": true,
      "gender_taxons": [

      ],
      "age_range_taxons": [

      ]
    },
    {
      "id": 3,
      "user_id": 41,
      "name": "Mini",
      "birth_year": 2020,
      "birth_month": 9,
      "birth_day": 22,
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
Authorizat IO N: Bearer 10979f971dc2bcaf3faedeaaf6665941bfe55e46f8b2bc7e
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
ETag: W/&quot;43008b595c38881968dfc2243cb744ce&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 5be01ab0-5940-4d3f-981a-84357a91151c
X-Runtime: 0.017665
Vary: Origin
Content-Length: 406
200 OK
```


```json
{
  "minis": [
    {
      "id": 19,
      "user_id": 55,
      "name": "Mini",
      "birth_year": 2020,
      "birth_month": 9,
      "birth_day": 22,
      "gender_boy": true,
      "gender_girl": true,
      "gender_taxons": [

      ],
      "age_range_taxons": [

      ]
    },
    {
      "id": 18,
      "user_id": 55,
      "name": "Mini",
      "birth_year": 2020,
      "birth_month": 9,
      "birth_day": 22,
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
PATCH /api/minis/1
Accept: application/json
Authorizat IO N: Bearer 1482a17c25253cb2481a4982c9701d89ef5bb388c64a4cda
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
ETag: W/&quot;5be5279b125f91dc78c53eb66e72b4a3&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: be35e936-5065-4173-8941-db78530df5bf
X-Runtime: 0.043688
Vary: Origin
Content-Length: 163
200 OK
```


```json
{
  "id": 1,
  "user_id": 39,
  "name": "Marge",
  "birth_year": 2020,
  "birth_month": 9,
  "birth_day": 22,
  "gender_boy": true,
  "gender_girl": true,
  "gender_taxons": [

  ],
  "age_range_taxons": [

  ]
}
```



# Orders



## Add a gift card item to a cart


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
user_id&order_token&line_item[variant_id]=129&line_item[quantity]=1&line_item[vendor_id]=237&line_item[gift_card_details_attributes][recipient_name]=Recipient+John&line_item[gift_card_details_attributes][recipient_email]=recipient%40email.com&line_item[gift_card_details_attributes][purchaser_name]=Purchaser+Bob&line_item[gift_card_details_attributes][gift_message]=Surprise&line_item[gift_card_details_attributes][send_email_at]=2020-09-23
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
ETag: W/&quot;c7df16c4228c91b6be75aa10c666f120&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 8657c6d2-e668-44bd-9821-739aac9edf22
X-Runtime: 0.160124
Vary: Origin
Content-Length: 2874
200 OK
```


```json
{
  "id": 18,
  "number": "M007993788",
  "item_total": "19.99",
  "total": "19.99",
  "ship_total": "0.0",
  "state": "cart",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2020-09-23T07:16:26.861-04:00",
  "updated_at": "2020-09-23T07:16:26.924-04:00",
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
  "order_total_after_store_credit": "19.99",
  "display_order_total_after_store_credit": "$19.99",
  "total_applicable_store_credit": 0.0,
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
  "token": "Q0dGvJt9yeOQeOqQPbmJDQ",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order?order=M007993788&bzip=&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [

  ],
  "bill_address": null,
  "ship_address": null,
  "line_items": [
    {
      "id": 19,
      "quantity": 1,
      "price": "19.99",
      "variant_id": 129,
      "vendor_id": 237,
      "single_display_amount": "$19.99",
      "display_amount": "$19.99",
      "total": "19.99",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 129,
        "name": "Product #69 - 72",
        "sku": "SKU-129",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-69-72",
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
        "product_id": 69,
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
          "send_email_at": "2020-09-23T00:00:00.000-04:00"
        }
      ],
      "vendor_name": "Vendor #237",
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
user_id&order_token&line_item[variant_id]=133&line_item[quantity]=2&line_item[vendor_id]=242
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
ETag: W/&quot;3897a42dfb95e0bae098d572162fc1bd&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: b89396ee-1020-432a-89d4-33c608b5d356
X-Runtime: 0.108664
Vary: Origin
Content-Length: 2696
200 OK
```


```json
{
  "id": 19,
  "number": "M639790304",
  "item_total": "39.98",
  "total": "39.98",
  "ship_total": "0.0",
  "state": "cart",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2020-09-23T07:16:27.391-04:00",
  "updated_at": "2020-09-23T07:16:27.434-04:00",
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
  "token": "hFiolZ2n5c8VoiKZh_f4gA",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order?order=M639790304&bzip=&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [

  ],
  "bill_address": null,
  "ship_address": null,
  "line_items": [
    {
      "id": 20,
      "quantity": 2,
      "price": "19.99",
      "variant_id": 133,
      "vendor_id": 242,
      "single_display_amount": "$19.99",
      "display_amount": "$39.98",
      "total": "39.98",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 133,
        "name": "Product #72 - 6279",
        "sku": "SKU-132",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-72-6279",
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
        "product_id": 72,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [

      ],
      "vendor_name": "Vendor #242",
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
user_id&order_token&line_item[variant_id]=137&line_item[quantity]=2&line_item[vendor_id]=250
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
ETag: W/&quot;3875dea5300f6384a5b094e9f637e795&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: ff965871-c465-48e7-8d8f-2c172b1c1d04
X-Runtime: 0.156893
Vary: Origin
Content-Length: 2696
200 OK
```


```json
{
  "id": 20,
  "number": "M231798697",
  "item_total": "39.98",
  "total": "39.98",
  "ship_total": "0.0",
  "state": "cart",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2020-09-23T07:16:28.068-04:00",
  "updated_at": "2020-09-23T07:16:28.160-04:00",
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
  "token": "MnesLGn2mUhyBtmXQBjqGg",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order?order=M231798697&bzip=&init=true",
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
      "variant_id": 137,
      "vendor_id": 250,
      "single_display_amount": "$19.99",
      "display_amount": "$39.98",
      "total": "39.98",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 137,
        "name": "Product #74 - 8512",
        "sku": "SKU-136",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-74-8512",
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
            "id": 63,
            "name": "Size-63",
            "presentation": "S",
            "option_type_name": "foo-size-63",
            "option_type_id": 63,
            "option_type_presentation": "Size",
            "position": 1
          }
        ],
        "images": [

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
      "vendor_name": "Vendor #250",
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
Authorizat IO N: Bearer 8c52b9c4d0900374c283d3d531fa8fd192e304731ac15f63
X-Spree-Order-Token: 
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/cart`

#### Parameters


```json
user_id&order_token&line_item[variant_id]=141&line_item[quantity]=2&line_item[vendor_id]=258&user_token=Bearer+8c52b9c4d0900374c283d3d531fa8fd192e304731ac15f63
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
ETag: W/&quot;cf714067793f9d71c3681dfdeea710a3&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: e7cf6748-c216-4bc8-89b1-56ebe047e60d
X-Runtime: 0.117241
Vary: Origin
Content-Length: 2708
200 OK
```


```json
{
  "id": 21,
  "number": "M826483728",
  "item_total": "39.98",
  "total": "39.98",
  "ship_total": "0.0",
  "state": "cart",
  "adjustment_total": "0.0",
  "user_id": 89,
  "created_at": "2020-09-23T07:16:28.614-04:00",
  "updated_at": "2020-09-23T07:16:28.657-04:00",
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
  "token": "y7CmtJSKSATSpVMQe4prNA",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order?order=M826483728&bzip=&init=true",
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
      "variant_id": 141,
      "vendor_id": 258,
      "single_display_amount": "$19.99",
      "display_amount": "$39.98",
      "total": "39.98",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 141,
        "name": "Product #76 - 5243",
        "sku": "SKU-140",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-76-5243",
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
        "product_id": 76,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [

      ],
      "vendor_name": "Vendor #258",
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
X-Spree-Order-Token: sQdOE4EJFxyhV72SbQ5KMA
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/cart`

#### Parameters


```json
user_id&order_token=sQdOE4EJFxyhV72SbQ5KMA&line_item[variant_id]=149&line_item[quantity]=2&line_item[vendor_id]=274
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
ETag: W/&quot;917195d83d25dbcd10409e4855fa9570&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: fc9ed235-965e-4a57-adb8-d6c81c640aea
X-Runtime: 0.107775
Vary: Origin
Content-Length: 2695
200 OK
```


```json
{
  "id": 23,
  "number": "M168172153",
  "item_total": "39.98",
  "total": "39.98",
  "ship_total": "0.0",
  "state": "cart",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2020-09-23T07:16:29.874-04:00",
  "updated_at": "2020-09-23T07:16:29.916-04:00",
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
  "token": "xvyOaMfj2lZa_ul8RRUhBA",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order?order=M168172153&bzip=&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [

  ],
  "bill_address": null,
  "ship_address": null,
  "line_items": [
    {
      "id": 25,
      "quantity": 2,
      "price": "19.99",
      "variant_id": 149,
      "vendor_id": 274,
      "single_display_amount": "$19.99",
      "display_amount": "$39.98",
      "total": "39.98",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 149,
        "name": "Product #80 - 3730",
        "sku": "SKU-148",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-80-3730",
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
        "product_id": 80,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [

      ],
      "vendor_name": "Vendor #274",
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
Authorizat IO N: Bearer 22359894d8828bd87b2e58d225e38c5defa1ca047def0f5e
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
X-Request-Id: 7c88744e-477e-417e-b1d6-64613e0cf037
X-Runtime: 0.017661
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
GET /api/orders/M675460066
Accept: application/json
Authorizat IO N: Bearer 3fac8e011ba49c6e18dd14a3783825e9bf6f96ca7a85ab78
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
ETag: W/&quot;fb0935b58459b453624fccd2e2aa3fe6&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 00f39338-6548-4faf-987c-3dc6306bc373
X-Runtime: 0.136028
Vary: Origin
Content-Length: 7915
200 OK
```


```json
{
  "id": 24,
  "number": "M675460066",
  "item_total": "20.0",
  "total": "118.0",
  "ship_total": "100.0",
  "state": "payment",
  "adjustment_total": "-2.0",
  "user_id": 91,
  "created_at": "2020-09-23T07:16:30.586-04:00",
  "updated_at": "2020-09-23T07:16:31.348-04:00",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "email89@example.com",
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
  "token": "D1nGsZ8LwYF8eBZkvVEakQ",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order?order=M675460066&bzip=10038&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [

  ],
  "bill_address": {
    "id": 39,
    "firstname": "John",
    "lastname": "Smith",
    "full_name": "John Smith",
    "address1": "PO Box 1337",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10038",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 45,
    "country_iso": "US",
    "state_id": 45,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 45,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 45,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 45
    }
  },
  "ship_address": {
    "id": 40,
    "firstname": "John",
    "lastname": "Smith",
    "full_name": "John Smith",
    "address1": "A Different Road",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10039",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 45,
    "country_iso": "US",
    "state_id": 45,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 45,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 45,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 45
    }
  },
  "line_items": [
    {
      "id": 26,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 151,
      "vendor_id": 281,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "9.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 151,
        "name": "Product #81 - 9277",
        "sku": "SKU-150",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-81-9277",
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
            "id": 70,
            "name": "Size-70",
            "presentation": "S",
            "option_type_name": "foo-size-70",
            "option_type_id": 70,
            "option_type_presentation": "Size",
            "position": 1
          }
        ],
        "images": [

        ],
        "product_id": 81,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [

      ],
      "vendor_name": "Vendor #281",
      "country_iso": "US",
      "adjustments": [
        {
          "id": 3,
          "source_type": "Spree::PromotionAction",
          "source_id": 3,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 26,
          "amount": "-1.0",
          "label": "Promotion (10% off)",
          "promotion_code_id": 3,
          "finalized": false,
          "eligible": true,
          "created_at": "2020-09-23T07:16:31.151-04:00",
          "updated_at": "2020-09-23T07:16:31.151-04:00",
          "display_amount": "-$1.00"
        }
      ]
    },
    {
      "id": 27,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 153,
      "vendor_id": 281,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "9.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 153,
        "name": "Product #82 - 833",
        "sku": "SKU-152",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-82-833",
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
        "product_id": 82,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [

      ],
      "vendor_name": "Vendor #281",
      "country_iso": "US",
      "adjustments": [
        {
          "id": 4,
          "source_type": "Spree::PromotionAction",
          "source_id": 3,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 27,
          "amount": "-1.0",
          "label": "Promotion (10% off)",
          "promotion_code_id": 3,
          "finalized": false,
          "eligible": true,
          "created_at": "2020-09-23T07:16:31.162-04:00",
          "updated_at": "2020-09-23T07:16:31.162-04:00",
          "display_amount": "-$1.00"
        }
      ]
    }
  ],
  "payments": [

  ],
  "shipments": [
    {
      "id": 26,
      "tracking": null,
      "tracking_url": null,
      "number": "H08160685510",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M675460066",
      "stock_location_name": "NY Warehouse 52",
      "giftwrappable": false,
      "stock_location_id": 52,
      "giftwrap": null,
      "shipping_rates": [
        {
          "id": 26,
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
        "id": 26,
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
              "id": 17,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 43,
              "name": "ShippingCategory #41"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 151,
          "quantity": 1,
          "states": {
            "on_hand": 1
          }
        },
        {
          "variant_id": 153,
          "quantity": 1,
          "states": {
            "on_hand": 1
          }
        }
      ],
      "adjustments": [
        {
          "id": 6,
          "source_type": "Spree::PromotionAction",
          "source_id": 4,
          "adjustable_type": "Spree::Shipment",
          "adjustable_id": 26,
          "amount": "-10.0",
          "label": "Shipping",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2020-09-23T07:16:31.240-04:00",
          "updated_at": "2020-09-23T07:16:31.240-04:00",
          "display_amount": "-$10.00"
        },
        {
          "id": 5,
          "source_type": "Spree::PromotionAction",
          "source_id": 4,
          "adjustable_type": "Spree::Shipment",
          "adjustable_id": 26,
          "amount": "-9.99",
          "label": "Shipping",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2020-09-23T07:16:31.232-04:00",
          "updated_at": "2020-09-23T07:16:31.232-04:00",
          "display_amount": "-$9.99"
        }
      ],
      "stock_location_address": "NY Warehouse 52, Washington, AL",
      "country_iso": "US",
      "international_shipping": false,
      "delivery_estimation": "Sep 25"
    }
  ],
  "adjustments": [
    {
      "id": 7,
      "source_type": "Spree::Promotion",
      "source_id": 4,
      "adjustable_type": "Spree::Order",
      "adjustable_id": 24,
      "amount": "20.0",
      "label": "adj1",
      "promotion_code_id": null,
      "finalized": false,
      "eligible": true,
      "created_at": "2020-09-23T07:16:31.247-04:00",
      "updated_at": "2020-09-23T07:16:31.247-04:00",
      "display_amount": "$20.00"
    },
    {
      "id": 8,
      "source_type": "Spree::Promotion",
      "source_id": 4,
      "adjustable_type": "Spree::Order",
      "adjustable_id": 24,
      "amount": "30.0",
      "label": "adj2",
      "promotion_code_id": null,
      "finalized": false,
      "eligible": true,
      "created_at": "2020-09-23T07:16:31.252-04:00",
      "updated_at": "2020-09-23T07:16:31.252-04:00",
      "display_amount": "$30.00"
    }
  ],
  "permissions": {
    "can_update": true
  },
  "gift_card_total": "0.0",
  "applied_promotion_codes": [
    {
      "id": 3,
      "promotion_id": 3,
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
        "source_id": 3,
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
GET /api/orders/M457264684
Accept: application/json
Authorizat IO N: 29eaa66b59283634b5cc10c16da01fcf1d123d511fb7f440
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
X-Request-Id: b8be3bd2-fa51-43c3-af43-89f8099d0f87
X-Runtime: 0.011830
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

Send an email with password reset instructions

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
user[email]=email1%40example.com
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
X-Request-Id: c4d397f4-4e59-413a-a295-b8aa6037cb5d
X-Runtime: 0.120548
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
Authorization: Bearer 1cb9091e74551202ef4c6944a38e0eacdce5b6cbbfe71382
ETag: W/&quot;040509cb307f738473e2a4a0a2f19296&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 36c4a14e-1cc4-4e0b-b961-90ec9b5e3850
X-Runtime: 0.045488
Vary: Origin
Content-Length: 559
200 OK
```


```json
{
  "id": 2,
  "email": "email2@example.com",
  "persistence_token": null,
  "perishable_token": null,
  "last_request_at": null,
  "login": "email2@example.com",
  "ship_address_id": null,
  "bill_address_id": null,
  "created_at": "2020-09-23T07:16:03.171-04:00",
  "updated_at": "2020-09-23T07:16:03.174-04:00",
  "spree_api_key": "1cb9091e74551202ef4c6944a38e0eacdce5b6cbbfe71382",
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
X-Request-Id: 41cc462d-b365-4f04-ace7-7583f70cc226
X-Runtime: 0.003621
Vary: Origin
204 No Content
```




# Products

Get all products, queryable by ransack

## Fetch a single product by id


### Request

#### Endpoint

```plaintext
GET /api/products/product-16-5321
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
Date: Wed, 23 Sep 2020 11:16:06 GMT
Surrogate-Control: max-age=900
Surrogate-Key: product_id=1
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;ac01dd60e73c6746cbbc7c24e662f46e&quot;
X-Request-Id: 9ff59861-d496-4da3-9b27-9d8379530b46
X-Runtime: 0.080267
Vary: Origin
Content-Length: 1613
200 OK
```


```json
{
  "id": 16,
  "name": "Product #16 - 5321",
  "description": "As seen on TV!",
  "available_on": "2019-09-23T07:16:06.381-04:00",
  "slug": "product-16-5321",
  "meta_description": null,
  "meta_keywords": null,
  "taxon_ids": [
    10
  ],
  "total_on_hand": 0,
  "meta_title": null,
  "display_price": "$0.00",
  "brand": null,
  "brand_slug": null,
  "brand_url": null,
  "brand_description": null,
  "gift_card": false,
  "is_registry": false,
  "discontinued": false,
  "available": true,
  "trends": [

  ],
  "breadcrumb_taxons": [
    {
      "id": 8,
      "name": "Clothing",
      "taxonomy_id": 4,
      "created_at": "2020-09-23T07:16:06.328-04:00",
      "url": "/category/clothing",
      "position": 1
    },
    {
      "id": 9,
      "name": "Girl",
      "taxonomy_id": 4,
      "created_at": "2020-09-23T07:16:06.346-04:00",
      "url": "/category/clothing/girl",
      "position": 2
    },
    {
      "id": 10,
      "name": "Dresses",
      "taxonomy_id": 4,
      "created_at": "2020-09-23T07:16:06.364-04:00",
      "url": "/category/clothing/girl/dresses",
      "position": 3
    }
  ],
  "has_variants": false,
  "master": {
    "id": 25,
    "name": "Product #16 - 5321",
    "sku": "SKU-25",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": true,
    "slug": "product-16-5321",
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
      "taxon_id": 10,
      "position": 1,
      "taxon": {
        "id": 10,
        "name": "Dresses",
        "pretty_name": "Category -> Clothing -> Girl -> Dresses",
        "permalink": "category/clothing/girl/dresses",
        "parent_id": 9,
        "taxonomy_id": 4,
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
Date: Wed, 23 Sep 2020 11:16:05 GMT
Surrogate-Control: max-age=900
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;0600a521df40ec45866d20c858f1c8cf&quot;
X-Request-Id: 50936b2a-8d11-4e5a-9614-cce301526fac
X-Runtime: 0.084786
Vary: Origin
Content-Length: 1296
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
      "id": 10,
      "name": "Product #10 - 5028",
      "description": "As seen on TV!",
      "available_on": "2019-09-23T07:16:05.409-04:00",
      "slug": "product-10-5028",
      "meta_description": null,
      "meta_keywords": null,
      "taxon_ids": [
        2
      ],
      "total_on_hand": 0,
      "meta_title": null,
      "display_price": "$0.00",
      "brand": "Maison You",
      "brand_slug": "maison-you",
      "brand_url": "/brand/maison-you",
      "brand_description": "Maison You",
      "gift_card": false,
      "is_registry": false,
      "discontinued": false,
      "available": true,
      "trends": [

      ],
      "breadcrumb_taxons": [

      ],
      "has_variants": false,
      "master": {
        "id": 19,
        "name": "Product #10 - 5028",
        "sku": "SKU-19",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-10-5028",
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
          "taxon_id": 2,
          "position": 1,
          "taxon": {
            "id": 2,
            "name": "Maison You",
            "pretty_name": "Brand -> Maison You",
            "permalink": "brand/maison-you",
            "parent_id": 1,
            "taxonomy_id": 1,
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
Date: Wed, 23 Sep 2020 11:16:06 GMT
Surrogate-Control: max-age=900
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;c1ba839b0a03ee8e78c17308ec80c17b&quot;
X-Request-Id: 313792ca-0272-4230-abaa-78ad011fc4e8
X-Runtime: 0.030503
Vary: Origin
Content-Length: 383
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
      "id": 15,
      "name": "Product #15 - 5332",
      "slug": "product-15-5332",
      "master_id": 24,
      "display_price": "$0.00",
      "brand": "Maison You",
      "brand_slug": "maison-you",
      "brand_url": "/brand/maison-you",
      "brand_description": "Maison You",
      "gift_card": false,
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
GET /api/products?ids=12%2C13%2C14
Host: example.org
Cookie: 
```

`GET /api/products`

#### Parameters


```json
ids: 12,13,14
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
Date: Wed, 23 Sep 2020 11:16:06 GMT
Surrogate-Control: max-age=900
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;25d692494ca5dc4d388e83faeab72e89&quot;
X-Request-Id: 959a6893-e73a-4935-adfc-9056f0cd1990
X-Runtime: 0.097475
Vary: Origin
Content-Length: 2862
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
      "id": 12,
      "name": "Product #12 - 5526",
      "description": "As seen on TV!",
      "available_on": "2019-09-23T07:16:05.812-04:00",
      "slug": "product-12-5526",
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
      "is_registry": false,
      "discontinued": false,
      "available": true,
      "trends": [

      ],
      "breadcrumb_taxons": [

      ],
      "has_variants": false,
      "master": {
        "id": 21,
        "name": "Product #12 - 5526",
        "sku": "SKU-21",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-12-5526",
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
    },
    {
      "id": 13,
      "name": "Product #13 - 1473",
      "description": "As seen on TV!",
      "available_on": "2019-09-23T07:16:05.879-04:00",
      "slug": "product-13-1473",
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
      "is_registry": false,
      "discontinued": false,
      "available": true,
      "trends": [

      ],
      "breadcrumb_taxons": [

      ],
      "has_variants": false,
      "master": {
        "id": 22,
        "name": "Product #13 - 1473",
        "sku": "SKU-22",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-13-1473",
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
    },
    {
      "id": 14,
      "name": "Product #14 - 7794",
      "description": "As seen on TV!",
      "available_on": "2019-09-23T07:16:05.947-04:00",
      "slug": "product-14-7794",
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
      "is_registry": false,
      "discontinued": false,
      "available": true,
      "trends": [

      ],
      "breadcrumb_taxons": [

      ],
      "has_variants": false,
      "master": {
        "id": 23,
        "name": "Product #14 - 7794",
        "sku": "SKU-23",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-14-7794",
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



## Fetch products by taxon id


### Request

#### Endpoint

```plaintext
GET /api/taxons/products?id=13
Host: example.org
Cookie: 
```

`GET /api/taxons/products`

#### Parameters


```json
id: 13
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
ETag: W/&quot;a54d306f0f04418ff2d2d3af3c0d72ba&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 128470fd-0d21-45e5-b01e-525cd407d7ae
X-Runtime: 0.058325
Vary: Origin
Content-Length: 1327
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
      "id": 18,
      "name": "Product #18 - 4948",
      "description": "As seen on TV!",
      "available_on": "2019-09-23T07:16:06.737-04:00",
      "slug": "product-18-4948",
      "meta_description": null,
      "meta_keywords": null,
      "taxon_ids": [
        13
      ],
      "total_on_hand": 0,
      "meta_title": null,
      "display_price": "$0.00",
      "brand": "Ruby on Rails - 1",
      "brand_slug": "ruby-on-rails-1",
      "brand_url": "/ruby-on-rails-1",
      "brand_description": "Ruby on Rails - 1",
      "gift_card": false,
      "is_registry": false,
      "discontinued": false,
      "available": true,
      "trends": [

      ],
      "breadcrumb_taxons": [

      ],
      "has_variants": false,
      "master": {
        "id": 27,
        "name": "Product #18 - 4948",
        "sku": "SKU-27",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-18-4948",
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
          "taxon_id": 13,
          "position": 1,
          "taxon": {
            "id": 13,
            "name": "Ruby on Rails - 1",
            "pretty_name": "Ruby on Rails - 1",
            "permalink": "ruby-on-rails-1",
            "parent_id": null,
            "taxonomy_id": 5,
            "url_override": null,
            "description": "Ruby on Rails - 1",
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
GET /api/taxons/products?permalink=ruby-on-rails-2
Host: example.org
Cookie: 
```

`GET /api/taxons/products`

#### Parameters


```json
permalink: ruby-on-rails-2
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
ETag: W/&quot;299e61428b7cee35627cda9e93b297b9&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: e3899ed6-9904-4002-a15e-8dcd98c63283
X-Runtime: 0.051954
Vary: Origin
Content-Length: 1327
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
      "id": 20,
      "name": "Product #20 - 8805",
      "description": "As seen on TV!",
      "available_on": "2019-09-23T07:16:07.055-04:00",
      "slug": "product-20-8805",
      "meta_description": null,
      "meta_keywords": null,
      "taxon_ids": [
        16
      ],
      "total_on_hand": 0,
      "meta_title": null,
      "display_price": "$0.00",
      "brand": "Ruby on Rails - 2",
      "brand_slug": "ruby-on-rails-2",
      "brand_url": "/ruby-on-rails-2",
      "brand_description": "Ruby on Rails - 2",
      "gift_card": false,
      "is_registry": false,
      "discontinued": false,
      "available": true,
      "trends": [

      ],
      "breadcrumb_taxons": [

      ],
      "has_variants": false,
      "master": {
        "id": 29,
        "name": "Product #20 - 8805",
        "sku": "SKU-29",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-20-8805",
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
          "taxon_id": 16,
          "position": 1,
          "taxon": {
            "id": 16,
            "name": "Ruby on Rails - 2",
            "pretty_name": "Ruby on Rails - 2",
            "permalink": "ruby-on-rails-2",
            "parent_id": null,
            "taxonomy_id": 6,
            "url_override": null,
            "description": "Ruby on Rails - 2",
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
Authorizat IO N: Bearer 667806251aa14f1cf825014baea9155657169f75c6854896
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
X-Request-Id: 3a84c665-1d0c-4971-ba03-0986a6b0d9ff
X-Runtime: 0.034617
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
X-Request-Id: cb38a76f-beb3-4f95-955d-b18281777aa5
X-Runtime: 0.014889
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

Get all recently viewed products using a session_id

## Get all recently viewed products


### Request

#### Endpoint

```plaintext
GET /api/recently_viewed?recently_viewed[session_id]=l2wxgcf5scscdmqm8o9baehfbvgcohc2h1ednqszs061493ss07bd5jyy5a1lg2afodcfijtuuzfp8iyjb9hqmny37qauvvhml4qkggzhqm7p6pd5g7koq0erqh4f3vuyxlgseru9cr6cu4lqjsaexoio8zrcxud5i8mszktkjmxlusxeaie0f4gqqm0hpk7yap447aubrc2jthvq5peqxmamcuyl17uf77odc6rpm4da4fooqg33s6kd7yzszq
Accept: application/json
Authorizat IO N: Bearer d22b9e569a36f0f30d65e402fa5e2f9fd72889c5fd0e5a36
Host: example.org
Cookie: 
```

`GET /api/recently_viewed`

#### Parameters


```json
recently_viewed: {&quot;session_id&quot;=&gt;&quot;l2wxgcf5scscdmqm8o9baehfbvgcohc2h1ednqszs061493ss07bd5jyy5a1lg2afodcfijtuuzfp8iyjb9hqmny37qauvvhml4qkggzhqm7p6pd5g7koq0erqh4f3vuyxlgseru9cr6cu4lqjsaexoio8zrcxud5i8mszktkjmxlusxeaie0f4gqqm0hpk7yap447aubrc2jthvq5peqxmamcuyl17uf77odc6rpm4da4fooqg33s6kd7yzszq&quot;}
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
ETag: W/&quot;7dc1a8b05cd3ff0e430fddd74091198c&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 17f7353d-60ce-4e24-87f3-cb3fef53872d
X-Runtime: 0.028329
Vary: Origin
Content-Length: 119
200 OK
```


```json
[
  {
    "at": "2020-09-23T07:16:25.551-04:00",
    "variant_id": "var1"
  },
  {
    "at": "2020-09-23T07:21:25.551-04:00",
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
Authorizat IO N: Bearer db441b09a77d4805c4fdfc8edbbb9c92f82ecc627c6fc94d
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/recently_viewed`

#### Parameters


```json
recently_viewed[session_id]=7maoamtggixk4tujvxba1tyffqox21bgpw8p3t8vabqgqhxamtrz4dpap3of2qr6s98g2p991wrd9a2adqwjfg6nvi16773pxa6lve21krikau8mliwdjzhztq9jsgf7vka2rur79joguk72f510s94utrgyhsslb26j2lbtkdudh8idleap8v1518z5ag4fwd3l89fv1y79lv2swjo4yzhxtz6oh2fjnqfasbmqb7pir9gagcatotrysyqt808&recently_viewed[variant_id]=foo
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
X-Request-Id: 4bf68f50-4f5d-43cd-8841-feb79031a5af
X-Runtime: 0.005248
Vary: Origin
204 No Content
```




# Return Authorizations

Get a single user return authorziation

## Can get another user&#39;s return authorization


### Request

#### Endpoint

```plaintext
GET /api/returns/RA886585411
Authorizat IO N: Bearer d0e82df38500b3aa8c5009041cad9bc3764d328f949ad792
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
ETag: W/&quot;8adc8708b12f22d6739e312fe6c5097d&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: b33dab59-d8de-4f0a-9d7f-33709de3f258
X-Runtime: 0.039991
Vary: Origin
Content-Length: 3051
200 OK
```


```json
{
  "id": 3,
  "number": "RA886585411",
  "state": "authorized",
  "order_id": 28,
  "memo": "Items were broken",
  "created_at": "2020-09-23T07:16:34.048-04:00",
  "updated_at": "2020-09-23T07:16:34.048-04:00",
  "amount": "10.0",
  "reason": {
    "id": 5,
    "name": "Defect #5",
    "active": true,
    "mutable": true,
    "created_at": "2020-09-23T07:16:34.044-04:00",
    "updated_at": "2020-09-23T07:16:34.044-04:00",
    "mirakl_code": null
  },
  "order": {
    "id": 28,
    "number": "M238455739",
    "item_total": "10.0",
    "total": "110.0",
    "state": "complete",
    "adjustment_total": "0.0",
    "user_id": 97,
    "completed_at": "2020-09-23T07:16:33.961-04:00",
    "bill_address_id": 47,
    "ship_address_id": 48,
    "payment_total": "110.0",
    "shipment_state": "shipped",
    "payment_state": "paid",
    "email": "email95@example.com",
    "special_instructions": null,
    "created_at": "2020-09-23T07:16:33.881-04:00",
    "updated_at": "2020-09-23T07:16:34.027-04:00",
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
    "guest_token": "IsX6zy7NwuunhMBUYKWR5w",
    "canceled_at": null,
    "canceler_id": null,
    "store_id": 27,
    "approver_name": null,
    "frontend_viewable": true,
    "migrated": false,
    "is_gift": false,
    "gift_email": null,
    "gift_message": null,
    "gift_card_total": "0.0",
    "gift_confirmation_delivered_at": null,
    "use_store_credits": false,
    "first_order": false
  },
  "ship_address": {
    "id": 48,
    "firstname": "John",
    "lastname": "Smith",
    "full_name": "John Smith",
    "address1": "A Different Road",
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
  "bill_address": {
    "id": 47,
    "firstname": "John",
    "lastname": "Smith",
    "full_name": "John Smith",
    "address1": "PO Box 1337",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10046",
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
  "return_items": [
    {
      "name": "Product #87 - 5632",
      "brand": null,
      "brand_slug": null,
      "image": null,
      "product_slug": "product-87-5632",
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
        "year": "2021",
        "cc_type": null,
        "last_digits": "1111",
        "name": "Spree Commerce",
        "gateway_customer_profile_id": "BGS-015554",
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
Authorizat IO N: Bearer 49b045c57b4935e2a8fa55e06de413ec17f80710eb1373f6
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
ETag: W/&quot;d442c7ca3a4e2a7fcee7b40aead3c016&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 5f529dbc-fc2b-4809-bdf8-1610497913f1
X-Runtime: 0.007643
Vary: Origin
Content-Length: 169
200 OK
```


```json
{
  "return_authorizations": [
    {
      "number": "RA578625267",
      "created_at": "2020-09-23T07:16:34.551-04:00",
      "return_amount": "10.0",
      "order_number": "M985226027",
      "state": "authorized"
    }
  ]
}
```



## returns a 200


### Request

#### Endpoint

```plaintext
GET /api/returns/RA566823436
Authorizat IO N: Bearer 0e467114a20fbdff474c788908acc3db2409357ee2018764
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
ETag: W/&quot;d6fcecb88748f5ce17ff237ea6b64664&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 9ada8457-bea5-4e37-a94a-8499bb516a98
X-Runtime: 0.062731
Vary: Origin
Content-Length: 2974
200 OK
```


```json
{
  "id": 1,
  "number": "RA566823436",
  "state": "authorized",
  "order_id": 26,
  "memo": "Items were broken",
  "created_at": "2020-09-23T07:16:33.035-04:00",
  "updated_at": "2020-09-23T07:16:33.035-04:00",
  "amount": "10.0",
  "reason": {
    "id": 1,
    "name": "Defect #1",
    "active": true,
    "mutable": true,
    "created_at": "2020-09-23T07:16:33.025-04:00",
    "updated_at": "2020-09-23T07:16:33.025-04:00",
    "mirakl_code": null
  },
  "order": {
    "id": 26,
    "number": "M537500899",
    "item_total": "10.0",
    "total": "110.0",
    "state": "complete",
    "adjustment_total": "0.0",
    "user_id": 94,
    "completed_at": "2020-09-23T07:16:32.869-04:00",
    "bill_address_id": 43,
    "ship_address_id": 44,
    "payment_total": "110.0",
    "shipment_state": "shipped",
    "payment_state": "paid",
    "email": "email92@example.com",
    "special_instructions": null,
    "created_at": "2020-09-23T07:16:32.771-04:00",
    "updated_at": "2020-09-23T07:16:32.982-04:00",
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
    "guest_token": "pt64mDIVsiB3SIKe7a5puw",
    "canceled_at": null,
    "canceler_id": null,
    "store_id": 25,
    "approver_name": null,
    "frontend_viewable": true,
    "migrated": false,
    "is_gift": false,
    "gift_email": null,
    "gift_message": null,
    "gift_card_total": "0.0",
    "gift_confirmation_delivered_at": null,
    "use_store_credits": false,
    "first_order": false
  },
  "ship_address": {
    "id": 44,
    "firstname": "John",
    "lastname": "Smith",
    "full_name": "John Smith",
    "address1": "A Different Road",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10043",
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
  "bill_address": {
    "id": 43,
    "firstname": "John",
    "lastname": "Smith",
    "full_name": "John Smith",
    "address1": "PO Box 1337",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10042",
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
  "return_items": [
    {
      "name": "Product #85 - 8776",
      "brand": null,
      "brand_slug": null,
      "image": null,
      "product_slug": "product-85-8776",
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
        "id": 13,
        "name": "Credit Card"
      },
      "source": {
        "id": 1,
        "month": "12",
        "year": "2021",
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
GET /api/returns/RA427485406
Authorizat IO N: Bearer 67c8b4038662825e906132487d290ab8d2e123222ea0a55b
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
X-Request-Id: 0d7a55fd-7a74-43a0-ace4-67e6881a5e03
X-Runtime: 0.007216
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
stock_request[email]=isobel_nikolaus%40stark.co.uk&stock_request[variant_id]=171
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
X-Request-Id: b545fac6-7174-46cd-a88e-830f7ea9d001
X-Runtime: 0.038600
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
stock_request[email]=foo&stock_request[variant_id]=173
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
X-Request-Id: c37dff99-b622-451a-a1a7-e60af0ed2a07
X-Runtime: 0.006168
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
stock_request[email]=telma.collier%40ankunding.info&stock_request[variant_id]=175
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
X-Request-Id: 1e68288a-55a0-4572-bf33-29b20e34c05d
X-Runtime: 0.005762
Vary: Origin
Content-Length: 30
422 Unprocessable Entity
```


```json
{
  "success": false,
  "message": [

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
Authorizat IO N: Bearer e110385ca637a741ef19aba57d83d219d73c4b611406f3db
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
ETag: W/&quot;1df1dfb433fccb2a73c60e075057f000&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 6df6a890-0e16-4e33-b122-5b4a4b3c39de
X-Runtime: 0.054579
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
      "created_at": "2020-09-23T07:16:12.702-04:00"
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

Unsubscribe a subscriber by email, this does not destroy the record.

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
subscriber[email]=augustina.oreilly%40shields.com&subscriber[first_name]=Kallie&subscriber[last_name]=Wilkinson&subscriber[source]=Illum+ut+et+nostrum+nihil+sunt.&subscriber[list_id]=gvv8qb
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
ETag: W/&quot;188af3d9556bb6c12619c113652710e9&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 37017fd8-7904-4947-818a-7f9413c5867a
X-Runtime: 0.013369
Vary: Origin
Content-Length: 251
201 Created
```


```json
{
  "id": 6,
  "user_id": null,
  "list_id": "gvv8qb",
  "email": "augustina.oreilly@shields.com",
  "first_name": "Kallie",
  "last_name": "Wilkinson",
  "source": "Illum ut et nostrum nihil sunt.",
  "phone": null,
  "status": "subscribed",
  "created_at": "2020-09-23T07:16:07.462-04:00"
}
```



## Create a subscriber for the associated user


### Request

#### Endpoint

```plaintext
POST /api/subscribers
Accept: application/json
Authorizat IO N: Bearer 92cd31130ebeb42918dbed892e04f3858dafbc21a74c559f
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/subscribers`

#### Parameters


```json
subscriber[email]&subscriber[first_name]=Elaina&subscriber[last_name]=Heaney&subscriber[source]=Qui+sunt+placeat+sed+consequuntur+ducimus+blanditiis.&subscriber[list_id]=md6z7b
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
ETag: W/&quot;b4a4a9a8d30c4737c611a6004347fc82&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: c14e7568-cef1-468c-8527-2d856172ab3b
X-Runtime: 0.015330
Vary: Origin
Content-Length: 258
201 Created
```


```json
{
  "id": 7,
  "user_id": 30,
  "list_id": "md6z7b",
  "email": "email30@example.com",
  "first_name": "Elaina",
  "last_name": "Heaney",
  "source": "Qui sunt placeat sed consequuntur ducimus blanditiis.",
  "phone": null,
  "status": "subscribed",
  "created_at": "2020-09-23T07:16:07.495-04:00"
}
```



## Get all subscribers


### Request

#### Endpoint

```plaintext
GET /api/subscribers
Accept: application/json
Authorizat IO N: Bearer 9062fc0c0c0e12f6d0e13257148c7952d298a0fcc352ebd0
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
ETag: W/&quot;eca744539c5e50e802a040b600fc74a5&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 35c40a8b-eb3c-4304-8e51-ba9a32d3f832
X-Runtime: 0.024271
Vary: Origin
Content-Length: 727
200 OK
```


```json
{
  "subscribers": [
    {
      "id": 2,
      "user_id": null,
      "list_id": "f4emmu",
      "email": "deloise_stoltenberg@hegmann.us",
      "first_name": "Augustine",
      "last_name": "Spencer",
      "source": null,
      "phone": null,
      "status": "subscribed",
      "created_at": "2020-09-23T07:16:07.350-04:00"
    },
    {
      "id": 3,
      "user_id": null,
      "list_id": "kaeego",
      "email": "millie_weber@mayert.ca",
      "first_name": "Audry",
      "last_name": "Beer",
      "source": null,
      "phone": null,
      "status": "subscribed",
      "created_at": "2020-09-23T07:16:07.354-04:00"
    },
    {
      "id": 4,
      "user_id": null,
      "list_id": "cq61ii",
      "email": "suzi@stanton.us",
      "first_name": "Scotty",
      "last_name": "O'Conner",
      "source": null,
      "phone": null,
      "status": "subscribed",
      "created_at": "2020-09-23T07:16:07.358-04:00"
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
PATCH /api/subscribers/5
Accept: application/json
Authorizat IO N: Bearer bc97cca02b663d3ec00a6e0e4adcb82300bc8f903d4d39e8
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/subscribers/:id`

#### Parameters


```json
subscriber[source]=Aperiam+voluptatem+magni+soluta+aut+nesciunt.
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
ETag: W/&quot;5a5316054f76ffe1e3a0946d012d9029&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: fb8448b9-78a8-4be0-86ff-1f28eb3b189b
X-Runtime: 0.019366
Vary: Origin
Content-Length: 260
200 OK
```


```json
{
  "id": 5,
  "user_id": 29,
  "list_id": "twfhx1",
  "email": "email29@example.com",
  "first_name": "Kori",
  "last_name": "Collins",
  "source": "Aperiam voluptatem magni soluta aut nesciunt.",
  "phone": null,
  "status": "subscribed_and_synced",
  "created_at": "2020-09-23T07:16:07.424-04:00"
}
```



## unsubscribe a known subscriber


### Request

#### Endpoint

```plaintext
DELETE /api/subscribers
Accept: application/json
Authorizat IO N: Bearer 41cc1c131d5550e41121df45fc8a67ee5558add274587bf1
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`DELETE /api/subscribers`

#### Parameters


```json
subscriber[email]=email26%40example.com&subscriber[list_id]=tqjhkt
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
X-Request-Id: b34554a4-f102-4092-ae57-a961b92d26a0
X-Runtime: 0.032239
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
Authorizat IO N: Bearer b47d0de519f20f459153c82efc80f9d4055d3d0c7ec791d5
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`DELETE /api/subscribers`

#### Parameters


```json
subscriber[email]=royce%40gaylord.co.uk&subscriber[list_id]=lvy0rj
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
X-Request-Id: 6e0a1f2d-7861-4c73-8623-4de65fda6cee
X-Runtime: 0.005414
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
Authorizat IO N: Bearer b54d08a402b748ee99cd8a2e5533c088d25cd4a47290398b
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
X-Request-Id: 1274840c-a310-479c-b1e6-cf0b78861d81
X-Runtime: 0.035335
Vary: Origin
Content-Length: 2
200 OK
```


```json
[

]
```



# Taxons API

Return all taxons

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
ETag: W/&quot;148a85ed32d768fe93d985f00b8fa45e&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: dd382c11-c268-44a3-9bf6-2eb17e491776
X-Runtime: 0.037730
Vary: Origin
Content-Length: 4438
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
      "id": 17,
      "name": "Category",
      "pretty_name": "Category",
      "permalink": "category",
      "parent_id": null,
      "taxonomy_id": 7,
      "url_override": null,
      "description": "Category",
      "icon": "/assets/default_taxon.png",
      "taxons": [
        {
          "id": 18,
          "name": "Kids",
          "pretty_name": "Category -> Kids",
          "permalink": "category/kids",
          "parent_id": 17,
          "taxonomy_id": 7,
          "url_override": null
        }
      ]
    },
    {
      "id": 18,
      "name": "Kids",
      "pretty_name": "Category -> Kids",
      "permalink": "category/kids",
      "parent_id": 17,
      "taxonomy_id": 7,
      "url_override": null,
      "description": "Kids",
      "icon": "/assets/default_taxon.png",
      "taxons": [
        {
          "id": 19,
          "name": "Boys",
          "pretty_name": "Category -> Kids -> Boys",
          "permalink": "category/kids/boys",
          "parent_id": 18,
          "taxonomy_id": 7,
          "url_override": null
        },
        {
          "id": 22,
          "name": "Girls",
          "pretty_name": "Category -> Kids -> Girls",
          "permalink": "category/kids/girls",
          "parent_id": 18,
          "taxonomy_id": 7,
          "url_override": null
        }
      ]
    },
    {
      "id": 19,
      "name": "Boys",
      "pretty_name": "Category -> Kids -> Boys",
      "permalink": "category/kids/boys",
      "parent_id": 18,
      "taxonomy_id": 7,
      "url_override": null,
      "description": "Boys",
      "icon": "/assets/default_taxon.png",
      "taxons": [
        {
          "id": 20,
          "name": "Boys Tops",
          "pretty_name": "Category -> Kids -> Boys -> Boys Tops",
          "permalink": "category/kids/boys/boys-tops",
          "parent_id": 19,
          "taxonomy_id": 7,
          "url_override": null
        }
      ]
    },
    {
      "id": 20,
      "name": "Boys Tops",
      "pretty_name": "Category -> Kids -> Boys -> Boys Tops",
      "permalink": "category/kids/boys/boys-tops",
      "parent_id": 19,
      "taxonomy_id": 7,
      "url_override": null,
      "description": "Boys Tops",
      "icon": "/assets/default_taxon.png",
      "taxons": [
        {
          "id": 21,
          "name": "Boys Shirts",
          "pretty_name": "Category -> Kids -> Boys -> Boys Tops -> Boys Shirts",
          "permalink": "category/kids/boys/boys-tops/boys-shirts",
          "parent_id": 20,
          "taxonomy_id": 7,
          "url_override": null
        }
      ]
    },
    {
      "id": 21,
      "name": "Boys Shirts",
      "pretty_name": "Category -> Kids -> Boys -> Boys Tops -> Boys Shirts",
      "permalink": "category/kids/boys/boys-tops/boys-shirts",
      "parent_id": 20,
      "taxonomy_id": 7,
      "url_override": null,
      "description": "Boys Shirts",
      "icon": "/assets/default_taxon.png",
      "taxons": [

      ]
    },
    {
      "id": 22,
      "name": "Girls",
      "pretty_name": "Category -> Kids -> Girls",
      "permalink": "category/kids/girls",
      "parent_id": 18,
      "taxonomy_id": 7,
      "url_override": null,
      "description": "Girls",
      "icon": "/assets/default_taxon.png",
      "taxons": [
        {
          "id": 23,
          "name": "Girls Tops",
          "pretty_name": "Category -> Kids -> Girls -> Girls Tops",
          "permalink": "category/kids/girls/girls-tops",
          "parent_id": 22,
          "taxonomy_id": 7,
          "url_override": null
        }
      ]
    },
    {
      "id": 23,
      "name": "Girls Tops",
      "pretty_name": "Category -> Kids -> Girls -> Girls Tops",
      "permalink": "category/kids/girls/girls-tops",
      "parent_id": 22,
      "taxonomy_id": 7,
      "url_override": null,
      "description": "Girls Tops",
      "icon": "/assets/default_taxon.png",
      "taxons": [
        {
          "id": 24,
          "name": "Girls Shirts",
          "pretty_name": "Category -> Kids -> Girls -> Girls Tops -> Girls Shirts",
          "permalink": "category/kids/girls/girls-tops/girls-shirts",
          "parent_id": 23,
          "taxonomy_id": 7,
          "url_override": null
        }
      ]
    },
    {
      "id": 24,
      "name": "Girls Shirts",
      "pretty_name": "Category -> Kids -> Girls -> Girls Tops -> Girls Shirts",
      "permalink": "category/kids/girls/girls-tops/girls-shirts",
      "parent_id": 23,
      "taxonomy_id": 7,
      "url_override": null,
      "description": "Girls Shirts",
      "icon": "/assets/default_taxon.png",
      "taxons": [

      ]
    },
    {
      "id": 25,
      "name": "Brand",
      "pretty_name": "Brand",
      "permalink": "brand",
      "parent_id": null,
      "taxonomy_id": 8,
      "url_override": null,
      "description": "Brand",
      "icon": "/assets/default_taxon.png",
      "taxons": [
        {
          "id": 26,
          "name": "Ruby on Rails - 3",
          "pretty_name": "Brand -> Ruby on Rails - 3",
          "permalink": "brand/ruby-on-rails-3",
          "parent_id": 25,
          "taxonomy_id": 8,
          "url_override": null
        },
        {
          "id": 27,
          "name": "Ruby on Rails - 4",
          "pretty_name": "Brand -> Ruby on Rails - 4",
          "permalink": "brand/ruby-on-rails-4",
          "parent_id": 25,
          "taxonomy_id": 8,
          "url_override": null
        }
      ]
    },
    {
      "id": 26,
      "name": "Ruby on Rails - 3",
      "pretty_name": "Brand -> Ruby on Rails - 3",
      "permalink": "brand/ruby-on-rails-3",
      "parent_id": 25,
      "taxonomy_id": 8,
      "url_override": null,
      "description": "Ruby on Rails - 3",
      "icon": "/assets/default_taxon.png",
      "taxons": [

      ]
    },
    {
      "id": 27,
      "name": "Ruby on Rails - 4",
      "pretty_name": "Brand -> Ruby on Rails - 4",
      "permalink": "brand/ruby-on-rails-4",
      "parent_id": 25,
      "taxonomy_id": 8,
      "url_override": null,
      "description": "Ruby on Rails - 4",
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
ETag: W/&quot;c904677c905dd885a0c7131da65fea97&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: ccb84f79-42bf-4191-8e55-aaced76fa72d
X-Runtime: 0.014244
Vary: Origin
Content-Length: 742
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
      "id": 36,
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
      "id": 37,
      "name": "Ruby on Rails - 5",
      "pretty_name": "Brand -> Ruby on Rails - 5",
      "permalink": "brand/ruby-on-rails-5",
      "parent_id": 36,
      "taxonomy_id": 10,
      "url_override": null,
      "description": "Ruby on Rails - 5",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 38,
      "name": "Ruby on Rails - 6",
      "pretty_name": "Brand -> Ruby on Rails - 6",
      "permalink": "brand/ruby-on-rails-6",
      "parent_id": 36,
      "taxonomy_id": 10,
      "url_override": null,
      "description": "Ruby on Rails - 6",
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
ETag: W/&quot;9e4879e9d636d6b0bb6a06fdcfe43526&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 1dd52bab-419f-45da-804d-a60fddb84f35
X-Runtime: 0.029798
Vary: Origin
Content-Length: 2670
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
      "id": 39,
      "name": "Category",
      "pretty_name": "Category",
      "permalink": "category",
      "parent_id": null,
      "taxonomy_id": 11,
      "url_override": null,
      "description": "Category",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 40,
      "name": "Kids",
      "pretty_name": "Category -> Kids",
      "permalink": "category/kids",
      "parent_id": 39,
      "taxonomy_id": 11,
      "url_override": null,
      "description": "Kids",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 41,
      "name": "Boys",
      "pretty_name": "Category -> Kids -> Boys",
      "permalink": "category/kids/boys",
      "parent_id": 40,
      "taxonomy_id": 11,
      "url_override": null,
      "description": "Boys",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 42,
      "name": "Boys Tops",
      "pretty_name": "Category -> Kids -> Boys -> Boys Tops",
      "permalink": "category/kids/boys/boys-tops",
      "parent_id": 41,
      "taxonomy_id": 11,
      "url_override": null,
      "description": "Boys Tops",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 43,
      "name": "Boys Shirts",
      "pretty_name": "Category -> Kids -> Boys -> Boys Tops -> Boys Shirts",
      "permalink": "category/kids/boys/boys-tops/boys-shirts",
      "parent_id": 42,
      "taxonomy_id": 11,
      "url_override": null,
      "description": "Boys Shirts",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 44,
      "name": "Girls",
      "pretty_name": "Category -> Kids -> Girls",
      "permalink": "category/kids/girls",
      "parent_id": 40,
      "taxonomy_id": 11,
      "url_override": null,
      "description": "Girls",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 45,
      "name": "Girls Tops",
      "pretty_name": "Category -> Kids -> Girls -> Girls Tops",
      "permalink": "category/kids/girls/girls-tops",
      "parent_id": 44,
      "taxonomy_id": 11,
      "url_override": null,
      "description": "Girls Tops",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 46,
      "name": "Girls Shirts",
      "pretty_name": "Category -> Kids -> Girls -> Girls Tops -> Girls Shirts",
      "permalink": "category/kids/girls/girls-tops/girls-shirts",
      "parent_id": 45,
      "taxonomy_id": 11,
      "url_override": null,
      "description": "Girls Shirts",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 47,
      "name": "Brand",
      "pretty_name": "Brand",
      "permalink": "brand",
      "parent_id": null,
      "taxonomy_id": 12,
      "url_override": null,
      "description": "Brand",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 48,
      "name": "Ruby on Rails - 7",
      "pretty_name": "Brand -> Ruby on Rails - 7",
      "permalink": "brand/ruby-on-rails-7",
      "parent_id": 47,
      "taxonomy_id": 12,
      "url_override": null,
      "description": "Ruby on Rails - 7",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 49,
      "name": "Ruby on Rails - 8",
      "pretty_name": "Brand -> Ruby on Rails - 8",
      "permalink": "brand/ruby-on-rails-8",
      "parent_id": 47,
      "taxonomy_id": 12,
      "url_override": null,
      "description": "Ruby on Rails - 8",
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
ETag: W/&quot;1570725e2664c5d18e02643cb66318a2&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: d5f25081-5f29-4ad5-a871-6bcdcb31a71c
X-Runtime: 0.021240
Vary: Origin
Content-Length: 561
200 OK
```


```json
[
  {
    "id": 57,
    "parent_id": 56,
    "position": 0,
    "name": "brand_x",
    "permalink": "brand/brand_x",
    "taxonomy_id": 16,
    "lft": 6,
    "rgt": 7,
    "icon_file_name": null,
    "icon_content_type": null,
    "icon_file_size": null,
    "icon_updated_at": null,
    "description": null,
    "created_at": "2020-09-23T07:16:14.394-04:00",
    "updated_at": "2020-09-23T07:16:14.454-04:00",
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
    "short_description": null
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
ETag: W/&quot;e54796c9d918ab3de8b9a2fe1d3770e9&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 56c7c454-eb19-4e27-945a-3e8da6ba8fde
X-Runtime: 0.008488
Vary: Origin
Content-Length: 144
200 OK
```


```json
[
  {
    "id": 59,
    "name": "Kids",
    "navigation_url": "/shop/kids",
    "parent_id": 58,
    "lft": 2,
    "depth": 1,
    "highlight": false,
    "header_link": false,
    "add_flair": false
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
ETag: W/&quot;a0459852a4025c125678d048ba0d1713&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: a0bf9335-cee5-4427-aa75-f78d8d225d3d
X-Runtime: 0.013386
Vary: Origin
Content-Length: 561
200 OK
```


```json
[
  {
    "id": 53,
    "parent_id": 52,
    "position": 0,
    "name": "brand_x",
    "permalink": "brand/brand_x",
    "taxonomy_id": 14,
    "lft": 6,
    "rgt": 7,
    "icon_file_name": null,
    "icon_content_type": null,
    "icon_file_size": null,
    "icon_updated_at": null,
    "description": null,
    "created_at": "2020-09-23T07:16:13.964-04:00",
    "updated_at": "2020-09-23T07:16:14.024-04:00",
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
    "short_description": null
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
user[email]=email70%40example.com&user[password]=secret
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
Authorization: Bearer ec50249276a3d6dabab7a700650269ab41b578ac82d7d189
ETag: W/&quot;a78dc2fdcae61509ce4e8d0edb3b2c39&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: cfa71fbf-04f9-4a4f-8ea8-1a9fe552831f
X-Runtime: 0.015670
Vary: Origin
Content-Length: 562
200 OK
```


```json
{
  "id": 70,
  "email": "email70@example.com",
  "persistence_token": null,
  "perishable_token": null,
  "last_request_at": null,
  "login": "email70@example.com",
  "ship_address_id": null,
  "bill_address_id": null,
  "created_at": "2020-09-23T07:16:18.750-04:00",
  "updated_at": "2020-09-23T07:16:18.753-04:00",
  "spree_api_key": "ec50249276a3d6dabab7a700650269ab41b578ac82d7d189",
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
X-Spree-Order-Token: 5OXND77hLwUN8yXA2d7bpg
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/users/login`

#### Parameters


```json
user[email]=email71%40example.com&user[password]=secret&order_number=M731181249
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
Authorization: Bearer 7de751d1cbf8cb61db766de726b4261806ea2a9941d3decd
ETag: W/&quot;5f611b35d9233ef8830622b70d773fb5&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 401abe72-ea48-4048-81d8-076fc8b73b18
X-Runtime: 0.018057
Vary: Origin
Content-Length: 562
200 OK
```


```json
{
  "id": 71,
  "email": "email71@example.com",
  "persistence_token": null,
  "perishable_token": null,
  "last_request_at": null,
  "login": "email71@example.com",
  "ship_address_id": null,
  "bill_address_id": null,
  "created_at": "2020-09-23T07:16:18.782-04:00",
  "updated_at": "2020-09-23T07:16:18.784-04:00",
  "spree_api_key": "7de751d1cbf8cb61db766de726b4261806ea2a9941d3decd",
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
Authorizat IO N: Bearer e4237f071ab1a95ac60cafd61b4a5b13f6abb6bec9c7a817
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
Authorization: Bearer e4237f071ab1a95ac60cafd61b4a5b13f6abb6bec9c7a817
ETag: W/&quot;7c43ea469447dc3e20285ae556127c59&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 7eaac9a2-f221-4dd2-8125-75076b2be7d3
X-Runtime: 0.031365
Vary: Origin
Content-Length: 1539
200 OK
```


```json
{
  "email": "email74@example.com",
  "first_name": null,
  "last_name": null,
  "id": 74,
  "subscribed": false,
  "addresses": [
    {
      "id": 15,
      "firstname": "John",
      "lastname": "Smith",
      "full_name": "John Smith",
      "address1": "A Different Road",
      "address2": "Northwest",
      "city": "Herndon",
      "zipcode": "10015",
      "phone": "555-555-0199",
      "company": "Company",
      "alternative_phone": "555-555-0199",
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
      "default": true
    },
    {
      "id": 14,
      "firstname": "John",
      "lastname": "Smith",
      "full_name": "John Smith",
      "address1": "PO Box 1337",
      "address2": "Northwest",
      "city": "Herndon",
      "zipcode": "10014",
      "phone": "555-555-0199",
      "company": "Company",
      "alternative_phone": "555-555-0199",
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
      "default": false
    }
  ],
  "payment_sources": [
    {
      "id": 6,
      "default": true,
      "source": {
        "id": 6,
        "payment_type": "CreditCard",
        "token": null,
        "created_at": "2020-09-23T07:16:19.311-04:00",
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
        "id": 7,
        "payment_type": "ApplePayCard",
        "token": null,
        "created_at": "2020-09-23T07:16:19.333-04:00",
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
        "id": 8,
        "payment_type": "PayPalAccount",
        "token": null,
        "created_at": "2020-09-23T07:16:19.346-04:00",
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
Authorization: Bearer b006c6420a253a8ed6f308587f934c71da8820722fed5e0d
ETag: W/&quot;3462d369b1e6b7d07ad04e6208d3eee3&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: d0f0cf92-1039-4c67-909a-c6a2ce065481
X-Runtime: 0.023804
Vary: Origin
Content-Length: 185
201 Created
```


```json
{
  "id": 75,
  "email": "test@example.com",
  "created_at": "2020-09-23T07:16:19.395-04:00",
  "updated_at": "2020-09-23T07:16:19.397-04:00",
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
X-Spree-Order-Token: w9Y7Bvblf6DCYq2qA6o8XA
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/users`

#### Parameters


```json
user[email]=test%40example.com&user[password]=test123&user[password_confirmation]=test123&order_number=M971685358
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
Authorization: Bearer 8b083222678c76dbecc7e501feaad0e6b0863e2e26c47c0e
ETag: W/&quot;940365a6b66ffa95ead436233d0cd461&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 66364c21-d389-4c6c-a61b-95bee5bc40a0
X-Runtime: 0.026483
Vary: Origin
Content-Length: 185
201 Created
```


```json
{
  "id": 76,
  "email": "test@example.com",
  "created_at": "2020-09-23T07:16:19.735-04:00",
  "updated_at": "2020-09-23T07:16:19.736-04:00",
  "subscribed": false,
  "bill_address": null,
  "ship_address": null
}
```



## Subscribe a user


### Request

#### Endpoint

```plaintext
PUT /api/users/72/subscribe
Accept: application/json
Authorizat IO N: Bearer c8eb34367cf9670ce1458d8e588ea13a93d3831b95078ca4
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
Authorization: Bearer c8eb34367cf9670ce1458d8e588ea13a93d3831b95078ca4
ETag: W/&quot;96ebc868240d29928d2750c92e425e42&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 6a285f52-9da8-4e21-9b00-b60920897f01
X-Runtime: 0.034386
Vary: Origin
Content-Length: 187
200 OK
```


```json
{
  "id": 72,
  "email": "email72@example.com",
  "created_at": "2020-09-23T07:16:19.173-04:00",
  "updated_at": "2020-09-23T07:16:19.175-04:00",
  "subscribed": true,
  "bill_address": null,
  "ship_address": null
}
```



## Unsubscribe a user


### Request

#### Endpoint

```plaintext
PUT /api/users/73/unsubscribe
Accept: application/json
Authorizat IO N: Bearer 87d1e0a25abff4cee0c7954cac89cbb611d93e19bcd3ecb6
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
Authorization: Bearer 87d1e0a25abff4cee0c7954cac89cbb611d93e19bcd3ecb6
ETag: W/&quot;bf94bf287a4580385d25a787a67642fe&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: b7feebca-0bca-455b-96ac-2d1646fdbb8e
X-Runtime: 0.019795
Vary: Origin
Content-Length: 188
200 OK
```


```json
{
  "id": 73,
  "email": "email73@example.com",
  "created_at": "2020-09-23T07:16:19.228-04:00",
  "updated_at": "2020-09-23T07:16:19.230-04:00",
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
GET /api/variants/113
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
ETag: W/&quot;9e50be92868c79dda427aac332890325&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: e6437a28-fe11-4d57-a41d-9a1e5614f9ee
X-Runtime: 0.084228
Vary: Origin
Content-Length: 2096
200 OK
```


```json
{
  "id": 113,
  "name": "Product #62 - 9372",
  "sku": "SKU-112",
  "weight": "0.0",
  "height": null,
  "width": null,
  "depth": null,
  "is_master": false,
  "slug": "product-62-9372",
  "description": "As seen on TV!",
  "track_inventory": true,
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
      "id": 51,
      "name": "Size-51",
      "presentation": "S",
      "option_type_name": "foo-size-51",
      "option_type_id": 51,
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
      "attachment_updated_at": "2020-09-23T07:16:22.913-04:00",
      "attachment_width": 489,
      "attachment_height": 490,
      "alt": null,
      "viewable_type": "Spree::Variant",
      "viewable_id": 113,
      "mini_url": "/spree/products/1/mini/thinking-cat.jpg?1600859782",
      "small_url": "/spree/products/1/small/thinking-cat.jpg?1600859782",
      "product_url": "/spree/products/1/product/thinking-cat.jpg?1600859782",
      "large_url": "/spree/products/1/large/thinking-cat.jpg?1600859782"
    }
  ],
  "variant_properties": [

  ],
  "stock_items": [

  ],
  "prices": [
    {
      "id": 81,
      "vendor_id": 195,
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
      "vendor_id": 196,
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
GET /api/variants/115
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
ETag: W/&quot;c229b31659a2a17388973c5a62da9b64&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: b7c22c49-ed52-4ac6-b335-456197f183fd
X-Runtime: 0.071390
Vary: Origin
Content-Length: 2733
200 OK
```


```json
{
  "id": 115,
  "name": "Product #63 - 9235",
  "sku": "SKU-114",
  "weight": "0.0",
  "height": null,
  "width": null,
  "depth": null,
  "is_master": false,
  "slug": "product-63-9235",
  "description": "As seen on TV!",
  "track_inventory": true,
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
      "id": 52,
      "name": "Size-52",
      "presentation": "S",
      "option_type_name": "foo-size-52",
      "option_type_id": 52,
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
      "attachment_updated_at": "2020-09-23T07:16:23.416-04:00",
      "attachment_width": 489,
      "attachment_height": 490,
      "alt": null,
      "viewable_type": "Spree::Variant",
      "viewable_id": 115,
      "mini_url": "/spree/products/2/mini/thinking-cat.jpg?1600859783",
      "small_url": "/spree/products/2/small/thinking-cat.jpg?1600859783",
      "product_url": "/spree/products/2/product/thinking-cat.jpg?1600859783",
      "large_url": "/spree/products/2/large/thinking-cat.jpg?1600859783"
    }
  ],
  "variant_properties": [

  ],
  "stock_items": [

  ],
  "prices": [
    {
      "id": 84,
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
      "id": 85,
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
GET /api/variants/117
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
ETag: W/&quot;54a632bc38ec771857d695e8b865129d&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 8911cab0-d189-4059-ad96-d6be4b8f7ffa
X-Runtime: 0.058259
Vary: Origin
Content-Length: 2437
200 OK
```


```json
{
  "id": 117,
  "name": "Product #64 - 643",
  "sku": "SKU-116",
  "weight": "0.0",
  "height": null,
  "width": null,
  "depth": null,
  "is_master": false,
  "slug": "product-64-643",
  "description": "As seen on TV!",
  "track_inventory": true,
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
      "id": 3,
      "position": 1,
      "attachment_content_type": "image/jpeg",
      "attachment_file_name": "thinking-cat.jpg",
      "type": "Spree::Image",
      "attachment_updated_at": "2020-09-23T07:16:23.917-04:00",
      "attachment_width": 489,
      "attachment_height": 490,
      "alt": null,
      "viewable_type": "Spree::Variant",
      "viewable_id": 117,
      "mini_url": "/spree/products/3/mini/thinking-cat.jpg?1600859783",
      "small_url": "/spree/products/3/small/thinking-cat.jpg?1600859783",
      "product_url": "/spree/products/3/product/thinking-cat.jpg?1600859783",
      "large_url": "/spree/products/3/large/thinking-cat.jpg?1600859783"
    }
  ],
  "variant_properties": [

  ],
  "stock_items": [

  ],
  "prices": [
    {
      "id": 87,
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
      "id": 88,
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



# Wallet payment sources



## Get user wallet payment sources


### Request

#### Endpoint

```plaintext
GET /api/wallet_payment_sources
Accept: application/json
Authorizat IO N: Bearer 6c560a557048564fb8dafa6db5bdbcc435820c4c8dc5db4b
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
ETag: W/&quot;bb65f63694d137cdd96ce3b2468b00aa&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: e5a67d68-5628-4b32-a832-7c0f6f49fc51
X-Runtime: 0.017451
Vary: Origin
Content-Length: 205
200 OK
```


```json
[
  {
    "id": 2,
    "user_id": 5,
    "payment_source_type": "SolidusPaypalBraintree::Source",
    "payment_source_id": 2,
    "default": false,
    "created_at": "2020-09-23T07:16:03.376-04:00",
    "updated_at": "2020-09-23T07:16:03.376-04:00"
  }
]
```



## Remove the payment from the user wallet


### Request

#### Endpoint

```plaintext
DELETE /api/wallet_payment_sources/3
Accept: application/json
Authorizat IO N: Bearer a0b837a5221634120043cdc79cdd9826981fb6eec7642efc
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
X-Request-Id: e48179f8-7542-4d93-b492-27e6401473f5
X-Runtime: 0.019800
Vary: Origin
204 No Content
```




## Set a wallet payment source as the default user payment method


### Request

#### Endpoint

```plaintext
POST /api/wallet_payment_sources/1/default
Accept: application/json
Authorizat IO N: Bearer 941b4725d900bcbca30e2f53a6918492f131be092d142c67
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
X-Request-Id: 7e975d10-ed30-4ddd-b869-6acfdb1e5568
X-Runtime: 0.047198
Vary: Origin
204 No Content
```




# Wished Products

Get all wishlists associated with the current api user

## Create a wished product


### Request

#### Endpoint

```plaintext
POST /api/wished_products
Accept: application/json
Authorizat IO N: Bearer 930f4f7e612e2cf9704be3377b2323558c4ebfa1cf516041
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/wished_products`

#### Parameters


```json
wished_product[wishlist_id]=39&wished_product[variant_id]=85&wished_product[quantity]=2&wished_product[remark]=Foo+bar
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
ETag: W/&quot;b8c220d8d89b1e131eca511fc3d83c04&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: c1fd71a5-8398-4ce5-9844-c8c467821156
X-Runtime: 0.014918
Vary: Origin
Content-Length: 119
201 Created
```


```json
{
  "id": 28,
  "wishlist_id": 39,
  "variant_id": 85,
  "quantity": 2,
  "remark": "Foo bar",
  "created_at": "2020-09-23T07:16:18.322-04:00"
}
```



## Delete a wished product


### Request

#### Endpoint

```plaintext
DELETE /api/wished_products/16
Accept: application/json
Authorizat IO N: Bearer ae86c42a075613c8ce725b614eade09ac7450a988c87306e
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
X-Request-Id: 99ef6c36-0c6f-42c1-b404-03fa3a9691f0
X-Runtime: 0.014438
Vary: Origin
204 No Content
```




## Get a single wished product


### Request

#### Endpoint

```plaintext
GET /api/wished_products/29
Accept: application/json
Authorizat IO N: Bearer dba5678b01ada9e8771731269f57b0e33bf7a5cc6f0cce63
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
ETag: W/&quot;a40744e663b90bfaaea254c892ec441a&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 1b6ab3df-729a-4fee-a277-ee71555ceaef
X-Runtime: 0.015047
Vary: Origin
Content-Length: 114
200 OK
```


```json
{
  "id": 29,
  "wishlist_id": 40,
  "variant_id": 87,
  "quantity": 1,
  "remark": null,
  "created_at": "2020-09-23T07:16:18.484-04:00"
}
```



## Get all wished products


### Request

#### Endpoint

```plaintext
GET /api/wished_products
Accept: application/json
Authorizat IO N: Bearer c48177b5393feafced7a6916940a76fa0954d4e635615f3c
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
ETag: W/&quot;0df3b33f4ddfe31c1d1818c859a9df43&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: fb114582-3535-4655-8601-31835dd65d35
X-Runtime: 0.011316
Vary: Origin
Content-Length: 433
200 OK
```


```json
{
  "wished_products": [
    {
      "id": 21,
      "wishlist_id": 34,
      "variant_id": 69,
      "quantity": 1,
      "remark": null,
      "created_at": "2020-09-23T07:16:16.816-04:00"
    },
    {
      "id": 20,
      "wishlist_id": 33,
      "variant_id": 67,
      "quantity": 1,
      "remark": null,
      "created_at": "2020-09-23T07:16:16.691-04:00"
    },
    {
      "id": 19,
      "wishlist_id": 32,
      "variant_id": 65,
      "quantity": 1,
      "remark": null,
      "created_at": "2020-09-23T07:16:16.567-04:00"
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
Authorizat IO N: Bearer dcbbc5d1d0cd8ac6d46a261b2ed4552cad0d69db0dc95bc1
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
ETag: W/&quot;d89ac9ed963a6470fe65930496293c72&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 481bac55-03bf-4ff2-bd34-cd9fcaa834e8
X-Runtime: 0.125723
Vary: Origin
Content-Length: 2344
200 OK
```


```json
{
  "wished_products": [
    {
      "id": 13,
      "wishlist_id": 30,
      "variant_id": 53,
      "quantity": 1,
      "remark": null,
      "created_at": "2020-09-23T07:16:15.620-04:00",
      "variant": {
        "id": 53,
        "name": "Product #32 - 6447",
        "sku": "SKU-52",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-32-6447",
        "description": "As seen on TV!",
        "track_inventory": true,
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
            "id": 21,
            "name": "Size-21",
            "presentation": "S",
            "option_type_name": "foo-size-21",
            "option_type_id": 21,
            "option_type_presentation": "Size",
            "position": 1
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
      "id": 14,
      "wishlist_id": 30,
      "variant_id": 55,
      "quantity": 1,
      "remark": null,
      "created_at": "2020-09-23T07:16:15.736-04:00",
      "variant": {
        "id": 55,
        "name": "Product #33 - 5049",
        "sku": "SKU-54",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-33-5049",
        "description": "As seen on TV!",
        "track_inventory": true,
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
            "id": 22,
            "name": "Size-22",
            "presentation": "S",
            "option_type_name": "foo-size-22",
            "option_type_id": 22,
            "option_type_presentation": "Size",
            "position": 1
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
      "id": 15,
      "wishlist_id": 30,
      "variant_id": 57,
      "quantity": 1,
      "remark": null,
      "created_at": "2020-09-23T07:16:15.875-04:00",
      "variant": {
        "id": 57,
        "name": "Product #34 - 9093",
        "sku": "SKU-56",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-34-9093",
        "description": "As seen on TV!",
        "track_inventory": true,
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
            "id": 23,
            "name": "Size-23",
            "presentation": "S",
            "option_type_name": "foo-size-23",
            "option_type_id": 23,
            "option_type_presentation": "Size",
            "position": 1
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
GET /api/wished_products?with_variant=true
Accept: application/json
Authorizat IO N: Bearer 7872acc64fd9ff43041e42d156e43a943249ca6edd97cba0
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
ETag: W/&quot;40e45676b60ab68a646237ac3f314c13&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 284bee62-3604-4472-8cdb-a236acb14873
X-Runtime: 0.114090
Vary: Origin
Content-Length: 2404
200 OK
```


```json
{
  "wished_products": [
    {
      "id": 24,
      "wishlist_id": 37,
      "variant_id": 75,
      "quantity": 1,
      "remark": null,
      "created_at": "2020-09-23T07:16:17.291-04:00",
      "variant": {
        "id": 75,
        "name": "Product #43 - 7434",
        "sku": "SKU-74",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-43-7434",
        "description": "As seen on TV!",
        "track_inventory": true,
        "cost_price": "17.0",
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
            "id": 32,
            "name": "Size-32",
            "presentation": "S",
            "option_type_name": "foo-size-32",
            "option_type_id": 32,
            "option_type_presentation": "Size",
            "position": 1
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
      "id": 23,
      "wishlist_id": 36,
      "variant_id": 73,
      "quantity": 1,
      "remark": null,
      "created_at": "2020-09-23T07:16:17.158-04:00",
      "variant": {
        "id": 73,
        "name": "Product #42 - 2391",
        "sku": "SKU-72",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-42-2391",
        "description": "As seen on TV!",
        "track_inventory": true,
        "cost_price": "17.0",
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
            "id": 31,
            "name": "Size-31",
            "presentation": "S",
            "option_type_name": "foo-size-31",
            "option_type_id": 31,
            "option_type_presentation": "Size",
            "position": 1
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
      "id": 22,
      "wishlist_id": 35,
      "variant_id": 71,
      "quantity": 1,
      "remark": null,
      "created_at": "2020-09-23T07:16:17.016-04:00",
      "variant": {
        "id": 71,
        "name": "Product #41 - 1389",
        "sku": "SKU-70",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-41-1389",
        "description": "As seen on TV!",
        "track_inventory": true,
        "cost_price": "17.0",
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
            "id": 30,
            "name": "Size-30",
            "presentation": "S",
            "option_type_name": "foo-size-30",
            "option_type_id": 30,
            "option_type_presentation": "Size",
            "position": 1
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
Authorizat IO N: Bearer 5f5d35c25f5482d03ac2d2cf78f935615e9c1277ce9cd25c
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
ETag: W/&quot;7ad487e3a55dcdd5e7964b791eec9041&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 49a7634e-944e-428d-8b3c-eae0ba14a1bd
X-Runtime: 0.037900
Vary: Origin
Content-Length: 433
200 OK
```


```json
{
  "wished_products": [
    {
      "id": 10,
      "wishlist_id": 29,
      "variant_id": 47,
      "quantity": 1,
      "remark": null,
      "created_at": "2020-09-23T07:16:15.156-04:00"
    },
    {
      "id": 11,
      "wishlist_id": 29,
      "variant_id": 49,
      "quantity": 1,
      "remark": null,
      "created_at": "2020-09-23T07:16:15.291-04:00"
    },
    {
      "id": 12,
      "wishlist_id": 29,
      "variant_id": 51,
      "quantity": 1,
      "remark": null,
      "created_at": "2020-09-23T07:16:15.401-04:00"
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
PATCH /api/wished_products/25
Accept: application/json
Authorizat IO N: Bearer abe480999149d201c04d5c11c00361fddeb7aa86f794aa88
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/wished_products/:id`

#### Parameters


```json
wished_product[wishlist_id]=38&wished_product[variant_id]=83&wished_product[quantity]=2&wished_product[remark]=Foo+bar
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
ETag: W/&quot;bffa04598b3b13732b01090bfbc3473e&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: fd01c256-00ff-4d6a-8d82-7587dfe752e1
X-Runtime: 0.015128
Vary: Origin
Content-Length: 119
200 OK
```


```json
{
  "id": 25,
  "wishlist_id": 38,
  "variant_id": 83,
  "quantity": 2,
  "remark": "Foo bar",
  "created_at": "2020-09-23T07:16:17.675-04:00"
}
```



# Wishlists

Get a users wishlists

## Create a wishlist


### Request

#### Endpoint

```plaintext
POST /api/wishlists
Accept: application/json
Authorizat IO N: Bearer c7579dc3d9ffb17ca982e5d134fe6ad75afa87632e06a003
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/wishlists`

#### Parameters


```json
wishlist[name]&wishlist[user_id]=9&wishlist[is_default]=true&wishlist[is_public]=false
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
ETag: W/&quot;8830525278069d07ff1fbb8bebaa23a5&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 6b9db60c-bc5a-4087-8380-35966d30de94
X-Runtime: 0.046750
Vary: Origin
Content-Length: 99
201 Created
```


```json
{
  "id": 14,
  "user_id": 9,
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
DELETE /api/wishlists/15
Accept: application/json
Authorizat IO N: Bearer a4dea3cff4fc7fbd2e8d496a1b6eb9fdcfa008c27e716ccd
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
X-Request-Id: d70e147a-662e-495b-85a4-6ea0e9238ad2
X-Runtime: 0.013676
Vary: Origin
204 No Content
```




## Get a single wishlist


### Request

#### Endpoint

```plaintext
GET /api/wishlists/17
Accept: application/json
Authorizat IO N: Bearer 15bbd039cba763e015c030c34eb4b32026d0b0e3c498b2c4
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
ETag: W/&quot;b10c3f5d95644d6ef2537a2af14153ea&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 89755833-929f-4cdb-8139-5738f0da928b
X-Runtime: 0.011201
Vary: Origin
Content-Length: 441
200 OK
```


```json
{
  "id": 17,
  "user_id": 12,
  "name": "Wishlist #15",
  "is_public": false,
  "is_default": true,
  "wished_products": [
    {
      "id": 4,
      "wishlist_id": 17,
      "variant_id": 8,
      "quantity": 1,
      "remark": null,
      "created_at": "2020-09-23T07:16:04.604-04:00"
    },
    {
      "id": 5,
      "wishlist_id": 17,
      "variant_id": 10,
      "quantity": 1,
      "remark": null,
      "created_at": "2020-09-23T07:16:04.738-04:00"
    },
    {
      "id": 6,
      "wishlist_id": 17,
      "variant_id": 12,
      "quantity": 1,
      "remark": null,
      "created_at": "2020-09-23T07:16:04.844-04:00"
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
Authorizat IO N: Bearer 80d509f7e37389b08f4925a72784e96bdfada492d93726e3
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
ETag: W/&quot;9dc1098366e1e04648e96865d8435731&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 621b0018-be38-4247-a1c5-085c1a1dd84b
X-Runtime: 0.011895
Vary: Origin
Content-Length: 894
200 OK
```


```json
{
  "wishlists": [
    {
      "id": 18,
      "user_id": 13,
      "name": "Wishlist #16",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 19,
      "user_id": 14,
      "name": "Wishlist #17",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 20,
      "user_id": 15,
      "name": "Wishlist #18",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 21,
      "user_id": 16,
      "name": "Wishlist #19",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 22,
      "user_id": 17,
      "name": "Wishlist #20",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 23,
      "user_id": 18,
      "name": "Wishlist #21",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 24,
      "user_id": 19,
      "name": "Wishlist #22",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 25,
      "user_id": 20,
      "name": "Wishlist #23",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 26,
      "user_id": 21,
      "name": "Wishlist #24",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 27,
      "user_id": 22,
      "name": "Wishlist #25",
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
Authorizat IO N: Bearer ec90ae288b83cb1c55416df5e6e8b036546a69cf455877f4
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
ETag: W/&quot;50033719cfa9af09495a92fd900b0355&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 9e2cc4b9-8887-4e94-b932-d798817b58ef
X-Runtime: 0.008742
Vary: Origin
Content-Length: 442
200 OK
```


```json
{
  "id": 28,
  "user_id": 24,
  "name": "Wishlist #26",
  "is_public": false,
  "is_default": true,
  "wished_products": [
    {
      "id": 7,
      "wishlist_id": 28,
      "variant_id": 14,
      "quantity": 1,
      "remark": null,
      "created_at": "2020-09-23T07:16:05.143-04:00"
    },
    {
      "id": 8,
      "wishlist_id": 28,
      "variant_id": 16,
      "quantity": 1,
      "remark": null,
      "created_at": "2020-09-23T07:16:05.244-04:00"
    },
    {
      "id": 9,
      "wishlist_id": 28,
      "variant_id": 18,
      "quantity": 1,
      "remark": null,
      "created_at": "2020-09-23T07:16:05.348-04:00"
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
Authorizat IO N: Bearer 3f4d80cc02a53f3628b40e879ad7acc608debea3911f708c
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
ETag: W/&quot;1bd8480c0c9c623a28b2fa65978a623c&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: e3d6236b-6312-4b5a-b235-af0ae67afb3d
X-Runtime: 0.066289
Vary: Origin
Content-Length: 881
200 OK
```


```json
{
  "wishlists": [
    {
      "id": 4,
      "user_id": 8,
      "name": "Wishlist #4",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 5,
      "user_id": 8,
      "name": "Wishlist #5",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 6,
      "user_id": 8,
      "name": "Wishlist #6",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 7,
      "user_id": 8,
      "name": "Wishlist #7",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 8,
      "user_id": 8,
      "name": "Wishlist #8",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 9,
      "user_id": 8,
      "name": "Wishlist #9",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 10,
      "user_id": 8,
      "name": "Wishlist #10",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 11,
      "user_id": 8,
      "name": "Wishlist #11",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 12,
      "user_id": 8,
      "name": "Wishlist #12",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 13,
      "user_id": 8,
      "name": "Wishlist #13",
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
Authorizat IO N: Bearer e7b721bf1bbd55d95ce6ca0ff2500323119ffe868eb8347d
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/wishlists/:id`

#### Parameters


```json
wishlist[name]=Another+Wishlist&wishlist[user_id]=11&wishlist[is_default]=true&wishlist[is_public]=false
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
ETag: W/&quot;60161cc9d4cda8de7d3fcc132a24b460&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 4a17764d-27f5-4337-9a33-fe6c38b20e0c
X-Runtime: 0.015505
Vary: Origin
Content-Length: 443
200 OK
```


```json
{
  "id": 16,
  "user_id": 11,
  "name": "Another Wishlist",
  "is_public": false,
  "is_default": true,
  "wished_products": [
    {
      "id": 1,
      "wishlist_id": 16,
      "variant_id": 2,
      "quantity": 1,
      "remark": null,
      "created_at": "2020-09-23T07:16:04.220-04:00"
    },
    {
      "id": 2,
      "wishlist_id": 16,
      "variant_id": 4,
      "quantity": 1,
      "remark": null,
      "created_at": "2020-09-23T07:16:04.325-04:00"
    },
    {
      "id": 3,
      "wishlist_id": 16,
      "variant_id": 6,
      "quantity": 1,
      "remark": null,
      "created_at": "2020-09-23T07:16:04.427-04:00"
    }
  ]
}
```



