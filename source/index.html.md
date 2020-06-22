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
PUT /api/orders/M190190721/addresses/10
Accept: application/json
X-Spree-Order-Token: Qfijnho5lH6sHumfiTIKDg
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
ETag: W/&quot;013feec17cacf1eebcc78fb5b08a9eb4&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 2a95cf65-acec-4bb2-8d3e-1c41ad5d08c0
X-Runtime: 0.104167
Vary: Origin
Content-Length: 502
200 OK
```


```json
{
  "id": 11,
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
X-Spree-Order-Token: wb9L65TJqLxiF3u8C9D4Gg
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/braintree/transactions`

#### Parameters


```json
order_id=M133389676&payment_method_id=2&options[restart_checkout]=true&transaction[email]=maryellen.oga%40mckenziemcglynn.com&transaction[nonce]=fake-paypal-billing-agreement-nonce&transaction[phone]=555-555-0199&transaction[shipping_address_attributes][first_name]=John&transaction[shipping_address_attributes][last_name]=Stamm&transaction[shipping_address_attributes][address_line_1]=A+Different+Road&transaction[shipping_address_attributes][city]=Herndon&transaction[shipping_address_attributes][state_code]=AL&transaction[shipping_address_attributes][zip]=10003&transaction[shipping_address_attributes][country_code]=US&transaction[payment_type]=PayPalAccount&transaction[billing_address_attributes][first_name]=John&transaction[billing_address_attributes][last_name]=Stamm&transaction[billing_address_attributes][address_line_1]=A+Different+Road&transaction[billing_address_attributes][city]=Herndon&transaction[billing_address_attributes][state_code]=AL&transaction[billing_address_attributes][zip]=10003&transaction[billing_address_attributes][country_code]=US
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
ETag: W/&quot;77e4df59bf557387d9f6b7dbc2126c2b&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 90cb66bc-d142-483e-8935-bd1e2d2b10f8
X-Runtime: 0.829043
Vary: Origin
Content-Length: 5252
200 OK
```


```json
{
  "id": 2,
  "number": "M133389676",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2020-06-22T09:28:56.592-04:00",
  "updated_at": "2020-06-22T09:28:57.402-04:00",
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
  "token": "wb9L65TJqLxiF3u8C9D4Gg",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order?order=M133389676&bzip=10003&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [
    {
      "id": 2,
      "name": "Braintree"
    }
  ],
  "bill_address": {
    "id": 7,
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
    "country_id": 2,
    "country_iso": "US",
    "state_id": 2,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 2,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 2,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 2
    }
  },
  "ship_address": {
    "id": 8,
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
    "country_id": 2,
    "country_iso": "US",
    "state_id": 2,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 2,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 2,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 2
    }
  },
  "line_items": [
    {
      "id": 2,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 4,
      "vendor_id": 7,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 4,
        "name": "Product #2 - 5485",
        "sku": "SKU-3",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-2-5485",
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
            "id": 2,
            "name": "Size-2",
            "presentation": "S",
            "option_type_name": "foo-size-2",
            "option_type_id": 2,
            "option_type_presentation": "Size",
            "position": 1
          }
        ],
        "images": [

        ],
        "product_id": 2,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [

      ],
      "vendor_name": "Vendor #7",
      "country_iso": "US",
      "adjustments": [

      ]
    }
  ],
  "payments": [
    {
      "id": 2,
      "source_type": "SolidusPaypalBraintree::Source",
      "source_id": 2,
      "amount": "110.0",
      "display_amount": "$110.00",
      "payment_method_id": 2,
      "state": "checkout",
      "avs_response": null,
      "created_at": "2020-06-22T09:28:56.938-04:00",
      "updated_at": "2020-06-22T09:28:56.938-04:00",
      "payment_method": {
        "id": 2,
        "name": "Braintree"
      },
      "source": {
        "id": 2,
        "payment_type": "PayPalAccount",
        "token": "bgx899",
        "created_at": "2020-06-22T09:28:56.935-04:00",
        "email": "jane.doe@paypal.com"
      }
    }
  ],
  "shipments": [
    {
      "id": 4,
      "tracking": null,
      "tracking_url": null,
      "number": "H30357718324",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M133389676",
      "stock_location_name": "NY Warehouse 2",
      "giftwrappable": false,
      "stock_location_id": 2,
      "giftwrap": null,
      "shipping_rates": [
        {
          "id": 4,
          "name": "UPS Ground",
          "admin_name": null,
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 2,
          "shipping_method_code": "UPS_GROUND",
          "extra_cost": "",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 4,
        "name": "UPS Ground",
        "admin_name": null,
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 2,
        "shipping_method_code": "UPS_GROUND",
        "extra_cost": "",
        "is_flat_rate": false,
        "is_flat_rate_expedited": false,
        "is_free_shipping": false,
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
              "id": 2,
              "name": "ShippingCategory #2"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 4,
          "quantity": 1,
          "states": {
            "on_hand": 1
          }
        }
      ],
      "adjustments": [

      ],
      "stock_location_address": "NY Warehouse 2, Washington, AL",
      "country_iso": "US",
      "international_shipping": false,
      "delivery_estimation": "Jun 24"
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
X-Spree-Order-Token: kftxL_QLdM5JLNda-z7OLA
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/braintree/transactions`

#### Parameters


```json
order_id=M396827852&payment_method_id=1&options[restart_checkout]=true&transaction[email]=maryellen.oga%40mckenziemcglynn.com&transaction[nonce]=fake-apple-pay-visa-nonce&transaction[phone]=555-555-0199&transaction[shipping_address_attributes][first_name]=John&transaction[shipping_address_attributes][last_name]=Stamm&transaction[shipping_address_attributes][address_line_1]=A+Different+Road&transaction[shipping_address_attributes][city]=Herndon&transaction[shipping_address_attributes][state_code]=AL&transaction[shipping_address_attributes][zip]=10001&transaction[shipping_address_attributes][country_code]=US&transaction[payment_type]=ApplePayCard
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
ETag: W/&quot;a96d0c2d882f7a4327c2ac8bb5939cbb&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 42432f33-ef7d-495f-a0ba-c0a2c1109bac
X-Runtime: 1.434486
Vary: Origin
Content-Length: 5298
200 OK
```


```json
{
  "id": 1,
  "number": "M396827852",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2020-06-22T09:28:53.850-04:00",
  "updated_at": "2020-06-22T09:28:55.381-04:00",
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
  "token": "kftxL_QLdM5JLNda-z7OLA",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order?order=M396827852&bzip=10001&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [
    {
      "id": 1,
      "name": "Braintree"
    }
  ],
  "bill_address": {
    "id": 3,
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
    "country_id": 1,
    "country_iso": "US",
    "state_id": 1,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 1,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 1,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 1
    }
  },
  "ship_address": {
    "id": 4,
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
    "country_id": 1,
    "country_iso": "US",
    "state_id": 1,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 1,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 1,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 1
    }
  },
  "line_items": [
    {
      "id": 1,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 2,
      "vendor_id": 2,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 2,
        "name": "Product #1 - 9914",
        "sku": "SKU-1",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-1-9914",
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
            "id": 1,
            "name": "Size-1",
            "presentation": "S",
            "option_type_name": "foo-size-1",
            "option_type_id": 1,
            "option_type_presentation": "Size",
            "position": 1
          }
        ],
        "images": [

        ],
        "product_id": 1,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [

      ],
      "vendor_name": "Vendor #2",
      "country_iso": "US",
      "adjustments": [

      ]
    }
  ],
  "payments": [
    {
      "id": 1,
      "source_type": "SolidusPaypalBraintree::Source",
      "source_id": 1,
      "amount": "110.0",
      "display_amount": "$110.00",
      "payment_method_id": 1,
      "state": "checkout",
      "avs_response": null,
      "created_at": "2020-06-22T09:28:54.717-04:00",
      "updated_at": "2020-06-22T09:28:54.717-04:00",
      "payment_method": {
        "id": 1,
        "name": "Braintree"
      },
      "source": {
        "id": 1,
        "payment_type": "ApplePayCard",
        "token": "cg7hsk",
        "created_at": "2020-06-22T09:28:54.713-04:00",
        "cc_type": "Apple Pay - Visa",
        "last_digits": "1881",
        "month": "12",
        "year": "2020"
      }
    }
  ],
  "shipments": [
    {
      "id": 2,
      "tracking": null,
      "tracking_url": null,
      "number": "H80182406317",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M396827852",
      "stock_location_name": "NY Warehouse 1",
      "giftwrappable": false,
      "stock_location_id": 1,
      "giftwrap": null,
      "shipping_rates": [
        {
          "id": 2,
          "name": "UPS Ground",
          "admin_name": null,
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 1,
          "shipping_method_code": "UPS_GROUND",
          "extra_cost": "",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 2,
        "name": "UPS Ground",
        "admin_name": null,
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 1,
        "shipping_method_code": "UPS_GROUND",
        "extra_cost": "",
        "is_flat_rate": false,
        "is_flat_rate_expedited": false,
        "is_free_shipping": false,
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
              "id": 1,
              "name": "ShippingCategory #1"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 2,
          "quantity": 1,
          "states": {
            "on_hand": 1
          }
        }
      ],
      "adjustments": [

      ],
      "stock_location_address": "NY Warehouse 1, Washington, AL",
      "country_iso": "US",
      "international_shipping": false,
      "delivery_estimation": "Jun 24"
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
PUT /api/checkouts/M188328507/complete
Accept: application/json
X-Spree-Order-Token: jpoKPwpDtUEBRspQrzhmXw
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
ETag: W/&quot;36258b51de6e1179a737562205017c82&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 5196d432-532c-4c77-85aa-e8d10c222c11
X-Runtime: 1.057166
Vary: Origin
Content-Length: 5386
200 OK
```


```json
{
  "id": 9,
  "number": "M188328507",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "complete",
  "adjustment_total": "0.0",
  "user_id": 49,
  "created_at": "2020-06-22T09:29:13.061-04:00",
  "updated_at": "2020-06-22T09:29:14.145-04:00",
  "completed_at": "2020-06-22T09:29:14.145-04:00",
  "payment_total": "110.0",
  "shipment_state": "ready",
  "payment_state": "paid",
  "email": "email49@example.com",
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
  "token": "jpoKPwpDtUEBRspQrzhmXw",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order?order=M188328507&bzip=10016&init=true",
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
    "id": 21,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "PO Box 1337",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10016",
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
    "id": 22,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "A Different Road",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10017",
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
      "id": 10,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 42,
      "vendor_id": 70,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 42,
        "name": "Product #21 - 5567",
        "sku": "SKU-41",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-21-5567",
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
        "product_id": 21,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [

      ],
      "vendor_name": "Vendor #70",
      "country_iso": "US",
      "adjustments": [

      ]
    }
  ],
  "payments": [
    {
      "id": 3,
      "source_type": "SolidusPaypalBraintree::Source",
      "source_id": 6,
      "amount": "110.0",
      "display_amount": "$110.00",
      "payment_method_id": 6,
      "state": "completed",
      "avs_response": "M",
      "created_at": "2020-06-22T09:29:13.336-04:00",
      "updated_at": "2020-06-22T09:29:13.695-04:00",
      "payment_method": {
        "id": 6,
        "name": "Braintree"
      },
      "source": {
        "id": 6,
        "payment_type": "CreditCard",
        "token": "4rptfz",
        "created_at": "2020-06-22T09:29:13.333-04:00",
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
      "number": "H52433536215",
      "cost": "100.0",
      "shipped_at": null,
      "state": "ready",
      "order_id": "M188328507",
      "stock_location_name": "NY Warehouse 11",
      "giftwrappable": false,
      "stock_location_id": 11,
      "giftwrap": null,
      "shipping_rates": [
        {
          "id": 10,
          "name": "UPS Ground",
          "admin_name": null,
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 8,
          "shipping_method_code": "UPS_GROUND",
          "extra_cost": "",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 10,
        "name": "UPS Ground",
        "admin_name": null,
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 8,
        "shipping_method_code": "UPS_GROUND",
        "extra_cost": "",
        "is_flat_rate": false,
        "is_flat_rate_expedited": false,
        "is_free_shipping": false,
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 8,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 8,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 11,
              "name": "ShippingCategory #10"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 42,
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
      "delivery_estimation": "Jun 24"
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
PATCH /api/checkouts/M009071876
Accept: application/json
X-Spree-Order-Token: 634Qi_xbacRaOPUmlkNevg
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=9&order[payment_attributes][][source_attributes][nonce]=fake-apple-pay-visa-nonce&order[payment_attributes][][source_attributes][payment_type]=ApplePayCard&order[payment_attributes][][source_attributes][reusable]=true
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
ETag: W/&quot;ad5c69000fd3831b0a2b50518fe1a8af&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: b868e877-809a-414a-9937-dd0414c1e66d
X-Runtime: 0.334958
Vary: Origin
Content-Length: 4846
200 OK
```


```json
{
  "id": 11,
  "number": "M009071876",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 51,
  "created_at": "2020-06-22T09:29:17.126-04:00",
  "updated_at": "2020-06-22T09:29:17.985-04:00",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "email51@example.com",
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
  "token": "634Qi_xbacRaOPUmlkNevg",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order?order=M009071876&bzip=10020&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [
    {
      "id": 9,
      "name": "Braintree"
    }
  ],
  "bill_address": {
    "id": 25,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "PO Box 1337",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10020",
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
    "id": 26,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "A Different Road",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10021",
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
      "id": 12,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 46,
      "vendor_id": 80,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 46,
        "name": "Product #23 - 4726",
        "sku": "SKU-45",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-23-4726",
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
        "product_id": 23,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [

      ],
      "vendor_name": "Vendor #80",
      "country_iso": "US",
      "adjustments": [

      ]
    }
  ],
  "payments": [

  ],
  "shipments": [
    {
      "id": 14,
      "tracking": null,
      "tracking_url": null,
      "number": "H70638610270",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M009071876",
      "stock_location_name": "NY Warehouse 13",
      "giftwrappable": false,
      "stock_location_id": 13,
      "giftwrap": null,
      "shipping_rates": [
        {
          "id": 14,
          "name": "UPS Ground",
          "admin_name": null,
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 10,
          "shipping_method_code": "UPS_GROUND",
          "extra_cost": "",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 14,
        "name": "UPS Ground",
        "admin_name": null,
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 10,
        "shipping_method_code": "UPS_GROUND",
        "extra_cost": "",
        "is_flat_rate": false,
        "is_flat_rate_expedited": false,
        "is_free_shipping": false,
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 10,
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
              "id": 13,
              "name": "ShippingCategory #12"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 46,
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
      "delivery_estimation": "Jun 24"
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
PATCH /api/checkouts/M255964091
Accept: application/json
X-Spree-Order-Token: 7GavN-GkC38CF3FNWMGzvA
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=10&order[payment_attributes][][source_attributes][nonce]=fake-paypal-billing-agreement-nonce&order[payment_attributes][][source_attributes][payment_type]=PayPalAccount&order[payment_attributes][][source_attributes][reusable]=true
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
ETag: W/&quot;6da7d8f3378077ec99d7aa39d89d2016&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: c00559e0-5ab6-408b-87d6-e621977b2b43
X-Runtime: 0.355783
Vary: Origin
Content-Length: 4847
200 OK
```


```json
{
  "id": 12,
  "number": "M255964091",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 52,
  "created_at": "2020-06-22T09:29:19.021-04:00",
  "updated_at": "2020-06-22T09:29:19.843-04:00",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "email52@example.com",
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
  "token": "7GavN-GkC38CF3FNWMGzvA",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order?order=M255964091&bzip=10022&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [
    {
      "id": 10,
      "name": "Braintree"
    }
  ],
  "bill_address": {
    "id": 27,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "PO Box 1337",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10022",
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
    "id": 28,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "A Different Road",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10023",
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
      "id": 13,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 48,
      "vendor_id": 85,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 48,
        "name": "Product #24 - 6247",
        "sku": "SKU-47",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-24-6247",
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
            "id": 24,
            "name": "Size-24",
            "presentation": "S",
            "option_type_name": "foo-size-24",
            "option_type_id": 24,
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
      "vendor_name": "Vendor #85",
      "country_iso": "US",
      "adjustments": [

      ]
    }
  ],
  "payments": [

  ],
  "shipments": [
    {
      "id": 16,
      "tracking": null,
      "tracking_url": null,
      "number": "H62578634537",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M255964091",
      "stock_location_name": "NY Warehouse 14",
      "giftwrappable": false,
      "stock_location_id": 14,
      "giftwrap": null,
      "shipping_rates": [
        {
          "id": 16,
          "name": "UPS Ground",
          "admin_name": null,
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 11,
          "shipping_method_code": "UPS_GROUND",
          "extra_cost": "",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 16,
        "name": "UPS Ground",
        "admin_name": null,
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 11,
        "shipping_method_code": "UPS_GROUND",
        "extra_cost": "",
        "is_flat_rate": false,
        "is_flat_rate_expedited": false,
        "is_free_shipping": false,
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 11,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 11,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 14,
              "name": "ShippingCategory #13"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 48,
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
      "delivery_estimation": "Jun 24"
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
PATCH /api/checkouts/M945702168
Accept: application/json
X-Spree-Order-Token: AS5S47icO9G44Fc2sf64Lw
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=11&order[payment_attributes][][source_attributes][nonce]=fake-valid-visa-nonce&order[payment_attributes][][source_attributes][payment_type]=CreditCard&order[payment_attributes][][source_attributes][reusable]=true
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
ETag: W/&quot;f37eb924c77bfb8b8696fb30c6ac848f&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: ffd974b7-595b-4c2e-9a62-3f8dac072428
X-Runtime: 0.512614
Vary: Origin
Content-Length: 4847
200 OK
```


```json
{
  "id": 13,
  "number": "M945702168",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 53,
  "created_at": "2020-06-22T09:29:20.896-04:00",
  "updated_at": "2020-06-22T09:29:22.003-04:00",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "email53@example.com",
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
  "token": "AS5S47icO9G44Fc2sf64Lw",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order?order=M945702168&bzip=10024&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [
    {
      "id": 11,
      "name": "Braintree"
    }
  ],
  "bill_address": {
    "id": 29,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "PO Box 1337",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10024",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 16,
    "country_iso": "US",
    "state_id": 16,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 16,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 16,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 16
    }
  },
  "ship_address": {
    "id": 30,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "A Different Road",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10025",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 16,
    "country_iso": "US",
    "state_id": 16,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 16,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 16,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 16
    }
  },
  "line_items": [
    {
      "id": 14,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 50,
      "vendor_id": 90,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 50,
        "name": "Product #25 - 7370",
        "sku": "SKU-49",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-25-7370",
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
            "id": 25,
            "name": "Size-25",
            "presentation": "S",
            "option_type_name": "foo-size-25",
            "option_type_id": 25,
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
      "vendor_name": "Vendor #90",
      "country_iso": "US",
      "adjustments": [

      ]
    }
  ],
  "payments": [

  ],
  "shipments": [
    {
      "id": 18,
      "tracking": null,
      "tracking_url": null,
      "number": "H64847885425",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M945702168",
      "stock_location_name": "NY Warehouse 15",
      "giftwrappable": false,
      "stock_location_id": 15,
      "giftwrap": null,
      "shipping_rates": [
        {
          "id": 18,
          "name": "UPS Ground",
          "admin_name": null,
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 12,
          "shipping_method_code": "UPS_GROUND",
          "extra_cost": "",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 18,
        "name": "UPS Ground",
        "admin_name": null,
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 12,
        "shipping_method_code": "UPS_GROUND",
        "extra_cost": "",
        "is_flat_rate": false,
        "is_flat_rate_expedited": false,
        "is_free_shipping": false,
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 12,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 12,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 15,
              "name": "ShippingCategory #14"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 50,
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
      "delivery_estimation": "Jun 24"
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
PATCH /api/checkouts/M994466396
Accept: application/json
X-Spree-Order-Token: W3hPwF7nn6o6-bJpxwzsPA
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=8&order[payment_attributes][][source_attributes][wallet_payment_source_id]=5
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
ETag: W/&quot;c925a4260c7503d5ef4e7bf045fd28c5&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 9c0ed919-ffe3-4cb8-88b3-fa3fb17c6a9e
X-Runtime: 0.339537
Vary: Origin
Content-Length: 4842
200 OK
```


```json
{
  "id": 10,
  "number": "M994466396",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 50,
  "created_at": "2020-06-22T09:29:15.161-04:00",
  "updated_at": "2020-06-22T09:29:16.094-04:00",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "email50@example.com",
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
  "token": "W3hPwF7nn6o6-bJpxwzsPA",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order?order=M994466396&bzip=10018&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [
    {
      "id": 8,
      "name": "Braintree"
    }
  ],
  "bill_address": {
    "id": 23,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "PO Box 1337",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10018",
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
    "id": 24,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "A Different Road",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10019",
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
      "id": 11,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 44,
      "vendor_id": 75,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 44,
        "name": "Product #22 - 2922",
        "sku": "SKU-43",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-22-2922",
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
        "product_id": 22,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [

      ],
      "vendor_name": "Vendor #75",
      "country_iso": "US",
      "adjustments": [

      ]
    }
  ],
  "payments": [

  ],
  "shipments": [
    {
      "id": 12,
      "tracking": null,
      "tracking_url": null,
      "number": "H86265782246",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M994466396",
      "stock_location_name": "NY Warehouse 12",
      "giftwrappable": false,
      "stock_location_id": 12,
      "giftwrap": null,
      "shipping_rates": [
        {
          "id": 12,
          "name": "UPS Ground",
          "admin_name": null,
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 9,
          "shipping_method_code": "UPS_GROUND",
          "extra_cost": "",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 12,
        "name": "UPS Ground",
        "admin_name": null,
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 9,
        "shipping_method_code": "UPS_GROUND",
        "extra_cost": "",
        "is_flat_rate": false,
        "is_flat_rate_expedited": false,
        "is_free_shipping": false,
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 9,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 9,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 12,
              "name": "ShippingCategory #11"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 44,
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
      "delivery_estimation": "Jun 24"
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
PUT /api/checkouts/M372712536
Accept: application/json
X-Spree-Order-Token: Mr4q9wkLlLkRYWMoIhgGhQ
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PUT /api/checkouts/:id`

#### Parameters


```json
order[ship_address_attributes][id]&order[ship_address_attributes][firstname]=John&order[ship_address_attributes][lastname]&order[ship_address_attributes][address1]=10+Lovely+Street&order[ship_address_attributes][address2]=Northwest&order[ship_address_attributes][city]=Herndon&order[ship_address_attributes][zipcode]=10015&order[ship_address_attributes][phone]=555-555-0199&order[ship_address_attributes][state_name]&order[ship_address_attributes][alternative_phone]=555-555-0199&order[ship_address_attributes][company]=Company&order[ship_address_attributes][state_id]=11&order[ship_address_attributes][country_id]=11&order[ship_address_attributes][created_at]&order[ship_address_attributes][updated_at]&order[use_billing]=true&hold_state=true
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
ETag: W/&quot;aeac9bcd7b62912c19e3a7a48cc0dbc8&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 27e7ecb4-6595-4152-9294-71d675e1085e
X-Runtime: 0.383995
Vary: Origin
Content-Length: 4811
200 OK
```


```json
{
  "id": 8,
  "number": "M372712536",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "cart",
  "adjustment_total": "0.0",
  "user_id": 48,
  "created_at": "2020-06-22T09:29:11.700-04:00",
  "updated_at": "2020-06-22T09:29:12.026-04:00",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "email48@example.com",
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
  "token": "Mr4q9wkLlLkRYWMoIhgGhQ",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order?order=M372712536&bzip=10015&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [

  ],
  "bill_address": {
    "id": 20,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "10 Lovely Street",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10015",
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
    "id": 20,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "10 Lovely Street",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10015",
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
      "id": 9,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 40,
      "vendor_id": 65,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 40,
        "name": "Product #20 - 2586",
        "sku": "SKU-39",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-20-2586",
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
            "id": 20,
            "name": "Size-20",
            "presentation": "S",
            "option_type_name": "foo-size-20",
            "option_type_id": 20,
            "option_type_presentation": "Size",
            "position": 1
          }
        ],
        "images": [

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
      "vendor_name": "Vendor #65",
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
      "tracking": "U10000",
      "tracking_url": null,
      "number": "H05872043461",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M372712536",
      "stock_location_name": "NY Warehouse 10",
      "giftwrappable": false,
      "stock_location_id": 10,
      "giftwrap": null,
      "shipping_rates": [
        {
          "id": 9,
          "name": "UPS Ground",
          "admin_name": null,
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 7,
          "shipping_method_code": "UPS_GROUND",
          "extra_cost": "",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 9,
        "name": "UPS Ground",
        "admin_name": null,
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 7,
        "shipping_method_code": "UPS_GROUND",
        "extra_cost": "",
        "is_flat_rate": false,
        "is_flat_rate_expedited": false,
        "is_free_shipping": false,
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 7,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 7,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 10,
              "name": "ShippingCategory #9"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 40,
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
      "delivery_estimation": "Jun 24"
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
POST /api/shipments/H30473863206/giftwrap
Accept: application/json
X-Spree-Order-Token: kSI9siD7RSmg2VTbbhXpWw
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/shipments/:shipment_number/giftwrap`

#### Parameters


```json
order_number=M338580766
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
X-Request-Id: 819d7d42-b73f-4dc2-abb0-976cd8415a1e
X-Runtime: 0.117819
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
DELETE /api/shipments/H44665800482/giftwrap
Accept: application/json
X-Spree-Order-Token: TPNT6_1jGDRGd2xid1jzIw
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`DELETE /api/shipments/:shipment_number/giftwrap`

#### Parameters


```json
order_number=M869913071
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
X-Request-Id: 53c77462-34ed-4b0c-85f8-6d0b08619d21
X-Runtime: 0.135485
Vary: Origin
204 No Content
```




# LineItem

Representation of a single cart item for a specific variant with price of vendor

## Creating a line item


### Request

#### Endpoint

```plaintext
POST /api/orders/M221903089/line_items
Accept: application/json
X-Spree-Order-Token: gRRJAE7LeDQmKsqfF5Rzmg
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/:order_number/line_items`

#### Parameters


```json
line_item[variant_id]=20&line_item[options][vendor_id]=39
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
ETag: W/&quot;e905fbc36e2a1d74f2cd32234e9b3812&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: acb19716-a31d-4872-852f-2f314dbfcb35
X-Runtime: 0.285168
Vary: Origin
Content-Length: 936
201 Created
```


```json
{
  "id": 8,
  "quantity": 1,
  "price": "19.99",
  "variant_id": 20,
  "vendor_id": 39,
  "single_display_amount": "$19.99",
  "display_amount": "$19.99",
  "total": "19.99",
  "on_sale": false,
  "final_sale": false,
  "backordered": null,
  "promotionable": true,
  "variant": {
    "id": 20,
    "name": "Product #10 - 9699",
    "sku": "SKU-19",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": false,
    "slug": "product-10-9699",
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
    "product_id": 10,
    "lead_time": 2,
    "brand": null,
    "brand_slug": null,
    "brand_description": null
  },
  "monogram": null,
  "gift_cards": [

  ],
  "vendor_name": "Vendor #39",
  "country_iso": null,
  "adjustments": [

  ]
}
```



## Creating a line item gift card


### Request

#### Endpoint

```plaintext
POST /api/orders/M767211486/line_items
Accept: application/json
X-Spree-Order-Token: WInWYDDdYlonIGisMCiuKQ
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/:order_number/line_items`

#### Parameters


```json
line_item[variant_id]=10&line_item[options][vendor_id]=20&line_item[options][gift_card_details][recipient_name]=Recipient+John&line_item[options][gift_card_details][recipient_email]=recipient%40email.com&line_item[options][gift_card_details][purchaser_name]=Purchaser+Bob&line_item[options][gift_card_details][gift_message]=Surprise&line_item[options][gift_card_details][send_email_at]=2020-06-22+09%3A29%3A01+-0400
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
ETag: W/&quot;32dd4e73a3adb41197aaf6219b4ec725&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 4d39c704-c2bc-4ea9-bbb3-fa33a66bdd2f
X-Runtime: 0.518777
Vary: Origin
Content-Length: 1065
201 Created
```


```json
{
  "id": 4,
  "quantity": 1,
  "price": "19.99",
  "variant_id": 10,
  "vendor_id": 20,
  "single_display_amount": "$19.99",
  "display_amount": "$19.99",
  "total": "19.99",
  "on_sale": false,
  "final_sale": false,
  "backordered": null,
  "promotionable": true,
  "variant": {
    "id": 10,
    "name": "Product #4 - 5003",
    "sku": "SKU-10",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": false,
    "slug": "product-4-5003",
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
        "id": 5,
        "name": "Size-5",
        "presentation": "S",
        "option_type_name": "foo-size-5",
        "option_type_id": 5,
        "option_type_presentation": "Size",
        "position": 1
      }
    ],
    "images": [

    ],
    "product_id": 4,
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
      "send_email_at": "2020-06-22T00:00:00.000-04:00"
    }
  ],
  "vendor_name": "Vendor #20",
  "country_iso": null,
  "adjustments": [

  ]
}
```



## Deleting a line item


### Request

#### Endpoint

```plaintext
DELETE /api/orders/M636807948/line_items/5
Accept: application/json
X-Spree-Order-Token: wWCFyQiN-NhK6ELiTVGmJw
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
X-Request-Id: ffd16c2a-8ed9-4eba-8063-7963229eacd2
X-Runtime: 0.227802
Vary: Origin
204 No Content
```




## Updating a line item


### Request

#### Endpoint

```plaintext
PUT /api/orders/M422573374/line_items/6
Accept: application/json
X-Spree-Order-Token: Xn3NNOeKBFWyprN56mmXRw
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
ETag: W/&quot;1452ff52c295d96788b37e438c69cebb&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 246f8570-d42f-465f-94ce-0b0e26e7526e
X-Runtime: 0.389475
Vary: Origin
Content-Length: 926
200 OK
```


```json
{
  "id": 6,
  "quantity": 2,
  "price": "10.0",
  "variant_id": 14,
  "vendor_id": 28,
  "single_display_amount": "$10.00",
  "display_amount": "$20.00",
  "total": "20.0",
  "on_sale": false,
  "final_sale": false,
  "backordered": null,
  "promotionable": true,
  "variant": {
    "id": 14,
    "name": "Product #7 - 9900",
    "sku": "SKU-13",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": false,
    "slug": "product-7-9900",
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
        "id": 7,
        "name": "Size-7",
        "presentation": "S",
        "option_type_name": "foo-size-7",
        "option_type_id": 7,
        "option_type_presentation": "Size",
        "position": 1
      }
    ],
    "images": [

    ],
    "product_id": 7,
    "lead_time": 2,
    "brand": null,
    "brand_slug": null,
    "brand_description": null
  },
  "monogram": null,
  "gift_cards": [

  ],
  "vendor_name": "Vendor #28",
  "country_iso": "US",
  "adjustments": [

  ]
}
```



# Minis

Get all minis, only accessible to admin users

## Create a mini


### Request

#### Endpoint

```plaintext
POST /api/minis
Accept: application/json
Authorizat IO N: Bearer f9acca2a346e11f1dd22b83f98615b62b60c19f6fb3918e8
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/minis`

#### Parameters


```json
mini[name]=Winny&mini[user_id]=18&mini[birth_year]=2019&mini[birth_month]=1&mini[birth_day]=1
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
ETag: W/&quot;f800d35f0b2b295fa7171b290abada8c&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 80b290b5-8880-4b1f-87f6-aeded419ba28
X-Runtime: 0.033299
Vary: Origin
Content-Length: 163
201 Created
```


```json
{
  "id": 13,
  "user_id": 18,
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
DELETE /api/minis/19
Accept: application/json
Authorizat IO N: Bearer 9db45a5dab74af602b0578f2532dd0a59fbe48677348a086
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
X-Request-Id: 2edcca69-a683-4aee-b2ca-96372f3ccfed
X-Runtime: 0.019248
Vary: Origin
204 No Content
```




## Get a single mini


### Request

#### Endpoint

```plaintext
GET /api/minis/11
Accept: application/json
Authorizat IO N: Bearer 847474aabbbadcc343b0b6a95a35cfb84ff6bd5a91f50b4c
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
ETag: W/&quot;d55dbfa730863fef927be7f12f555aa1&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: d2c33029-c520-4571-9c7c-92bd1ead6eb0
X-Runtime: 0.032536
Vary: Origin
Content-Length: 163
200 OK
```


```json
{
  "id": 11,
  "user_id": 16,
  "name": "Mini",
  "birth_year": 2020,
  "birth_month": 6,
  "birth_day": 21,
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
Authorizat IO N: Bearer eefd964921b90d8fc1f787f24c08a359ac0c3fb342fda72c
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
ETag: W/&quot;d4017422fb0cc1401e4eebb59a0d7ecf&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: e7d93510-7e14-4c44-92b0-854e1ec27451
X-Runtime: 0.199146
Vary: Origin
Content-Length: 1706
200 OK
```


```json
{
  "minis": [
    {
      "id": 10,
      "user_id": 14,
      "name": "Mini",
      "birth_year": 2020,
      "birth_month": 6,
      "birth_day": 21,
      "gender_boy": true,
      "gender_girl": true,
      "gender_taxons": [

      ],
      "age_range_taxons": [

      ]
    },
    {
      "id": 9,
      "user_id": 13,
      "name": "Mini",
      "birth_year": 2020,
      "birth_month": 6,
      "birth_day": 21,
      "gender_boy": true,
      "gender_girl": true,
      "gender_taxons": [

      ],
      "age_range_taxons": [

      ]
    },
    {
      "id": 8,
      "user_id": 12,
      "name": "Mini",
      "birth_year": 2020,
      "birth_month": 6,
      "birth_day": 21,
      "gender_boy": true,
      "gender_girl": true,
      "gender_taxons": [

      ],
      "age_range_taxons": [

      ]
    },
    {
      "id": 7,
      "user_id": 11,
      "name": "Mini",
      "birth_year": 2020,
      "birth_month": 6,
      "birth_day": 21,
      "gender_boy": true,
      "gender_girl": true,
      "gender_taxons": [

      ],
      "age_range_taxons": [

      ]
    },
    {
      "id": 6,
      "user_id": 10,
      "name": "Mini",
      "birth_year": 2020,
      "birth_month": 6,
      "birth_day": 21,
      "gender_boy": true,
      "gender_girl": true,
      "gender_taxons": [

      ],
      "age_range_taxons": [

      ]
    },
    {
      "id": 5,
      "user_id": 9,
      "name": "Mini",
      "birth_year": 2020,
      "birth_month": 6,
      "birth_day": 21,
      "gender_boy": true,
      "gender_girl": true,
      "gender_taxons": [

      ],
      "age_range_taxons": [

      ]
    },
    {
      "id": 4,
      "user_id": 8,
      "name": "Mini",
      "birth_year": 2020,
      "birth_month": 6,
      "birth_day": 21,
      "gender_boy": true,
      "gender_girl": true,
      "gender_taxons": [

      ],
      "age_range_taxons": [

      ]
    },
    {
      "id": 3,
      "user_id": 7,
      "name": "Mini",
      "birth_year": 2020,
      "birth_month": 6,
      "birth_day": 21,
      "gender_boy": true,
      "gender_girl": true,
      "gender_taxons": [

      ],
      "age_range_taxons": [

      ]
    },
    {
      "id": 2,
      "user_id": 6,
      "name": "Mini",
      "birth_year": 2020,
      "birth_month": 6,
      "birth_day": 21,
      "gender_boy": true,
      "gender_girl": true,
      "gender_taxons": [

      ],
      "age_range_taxons": [

      ]
    },
    {
      "id": 1,
      "user_id": 5,
      "name": "Mini",
      "birth_year": 2020,
      "birth_month": 6,
      "birth_day": 21,
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
Authorizat IO N: Bearer b7dfcfed139cc31b078c9b862fc26769d71d9cf1c9eab196
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
ETag: W/&quot;97dc1257a45d1c84d677347701373b66&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 210e28c1-163a-4661-8de5-cd4415f637ad
X-Runtime: 0.041312
Vary: Origin
Content-Length: 406
200 OK
```


```json
{
  "minis": [
    {
      "id": 18,
      "user_id": 20,
      "name": "Mini",
      "birth_year": 2020,
      "birth_month": 6,
      "birth_day": 21,
      "gender_boy": true,
      "gender_girl": true,
      "gender_taxons": [

      ],
      "age_range_taxons": [

      ]
    },
    {
      "id": 17,
      "user_id": 20,
      "name": "Mini",
      "birth_year": 2020,
      "birth_month": 6,
      "birth_day": 21,
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
PATCH /api/minis/12
Accept: application/json
Authorizat IO N: Bearer 792b96abd722edc84b1396db12c28caa8dadd6bfdfcc0f6d
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
ETag: W/&quot;27bc148cb468f9663e3a5377d5073031&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 83101e51-2f92-420c-b12a-70d0256ffe92
X-Runtime: 0.036083
Vary: Origin
Content-Length: 164
200 OK
```


```json
{
  "id": 12,
  "user_id": 17,
  "name": "Marge",
  "birth_year": 2020,
  "birth_month": 6,
  "birth_day": 21,
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
user_id&order_token&line_item[variant_id]=111&line_item[quantity]=1&line_item[vendor_id]=179&line_item[gift_card_details_attributes][recipient_name]=Recipient+John&line_item[gift_card_details_attributes][recipient_email]=recipient%40email.com&line_item[gift_card_details_attributes][purchaser_name]=Purchaser+Bob&line_item[gift_card_details_attributes][gift_message]=Surprise&line_item[gift_card_details_attributes][send_email_at]=2020-06-22
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
ETag: W/&quot;2d8f7220cff46e233274f20c5530bbde&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 0c37f24b-3cb8-4ecf-989b-28a33abc9b0b
X-Runtime: 0.414754
Vary: Origin
Content-Length: 2878
200 OK
```


```json
{
  "id": 14,
  "number": "M023157792",
  "item_total": "19.99",
  "total": "19.99",
  "ship_total": "0.0",
  "state": "cart",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2020-06-22T09:29:39.049-04:00",
  "updated_at": "2020-06-22T09:29:39.186-04:00",
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
  "token": "YeW_t2dgnTm2_9z1I1jBiQ",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order?order=M023157792&bzip=&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [

  ],
  "bill_address": null,
  "ship_address": null,
  "line_items": [
    {
      "id": 15,
      "quantity": 1,
      "price": "19.99",
      "variant_id": 111,
      "vendor_id": 179,
      "single_display_amount": "$19.99",
      "display_amount": "$19.99",
      "total": "19.99",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 111,
        "name": "Product #60 - 7730",
        "sku": "SKU-111",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-60-7730",
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
            "id": 50,
            "name": "Size-50",
            "presentation": "S",
            "option_type_name": "foo-size-50",
            "option_type_id": 50,
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
        {
          "recipient_name": "Recipient John",
          "recipient_email": "recipient@email.com",
          "purchaser_name": "Purchaser Bob",
          "gift_message": "Surprise",
          "send_email_at": "2020-06-22T00:00:00.000-04:00"
        }
      ],
      "vendor_name": "Vendor #179",
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
user_id&order_token&line_item[variant_id]=115&line_item[quantity]=2&line_item[vendor_id]=184
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
ETag: W/&quot;bed8a6adf4e4b4efdc32e46168329e2b&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 78bd9020-5905-46ec-8599-070ce44ddf85
X-Runtime: 0.338226
Vary: Origin
Content-Length: 2696
200 OK
```


```json
{
  "id": 15,
  "number": "M696384437",
  "item_total": "39.98",
  "total": "39.98",
  "ship_total": "0.0",
  "state": "cart",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2020-06-22T09:29:40.884-04:00",
  "updated_at": "2020-06-22T09:29:41.005-04:00",
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
  "token": "cNLaa1xLm6Dxze4A6xYVRg",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order?order=M696384437&bzip=&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [

  ],
  "bill_address": null,
  "ship_address": null,
  "line_items": [
    {
      "id": 16,
      "quantity": 2,
      "price": "19.99",
      "variant_id": 115,
      "vendor_id": 184,
      "single_display_amount": "$19.99",
      "display_amount": "$39.98",
      "total": "39.98",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 115,
        "name": "Product #63 - 6590",
        "sku": "SKU-114",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-63-6590",
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

        ],
        "product_id": 63,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [

      ],
      "vendor_name": "Vendor #184",
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
user_id&order_token&line_item[variant_id]=127&line_item[quantity]=2&line_item[vendor_id]=206
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
ETag: W/&quot;7dca1ab401b83a55a181c90f187f22a6&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 45139973-d2ef-4139-9f8a-3b5c51d28a2c
X-Runtime: 0.308343
Vary: Origin
Content-Length: 2696
200 OK
```


```json
{
  "id": 18,
  "number": "M687806029",
  "item_total": "39.98",
  "total": "39.98",
  "ship_total": "0.0",
  "state": "cart",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2020-06-22T09:29:45.844-04:00",
  "updated_at": "2020-06-22T09:29:45.973-04:00",
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
  "token": "9EV4lGxSfapOjwuJ5V58XA",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order?order=M687806029&bzip=&init=true",
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
      "variant_id": 127,
      "vendor_id": 206,
      "single_display_amount": "$19.99",
      "display_amount": "$39.98",
      "total": "39.98",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 127,
        "name": "Product #69 - 2401",
        "sku": "SKU-126",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-69-2401",
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
            "id": 58,
            "name": "Size-58",
            "presentation": "S",
            "option_type_name": "foo-size-58",
            "option_type_id": 58,
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

      ],
      "vendor_name": "Vendor #206",
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
Authorizat IO N: Bearer b37779c818962bd5491632209dbc555edf09b747d35c7008
X-Spree-Order-Token: 
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/cart`

#### Parameters


```json
user_id&order_token&line_item[variant_id]=131&line_item[quantity]=2&line_item[vendor_id]=214&user_token=Bearer+b37779c818962bd5491632209dbc555edf09b747d35c7008
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
ETag: W/&quot;abaa7efb6933a4cef69544ba6ebc0f0d&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: e7cbb84e-a6ca-4942-a868-c0cfd5ab84cc
X-Runtime: 0.361783
Vary: Origin
Content-Length: 2708
200 OK
```


```json
{
  "id": 19,
  "number": "M376449544",
  "item_total": "39.98",
  "total": "39.98",
  "ship_total": "0.0",
  "state": "cart",
  "adjustment_total": "0.0",
  "user_id": 72,
  "created_at": "2020-06-22T09:29:47.202-04:00",
  "updated_at": "2020-06-22T09:29:47.351-04:00",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "email72@example.com",
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
  "token": "hy8yQU6b3jm4fQUMdzqlFg",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order?order=M376449544&bzip=&init=true",
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
      "variant_id": 131,
      "vendor_id": 214,
      "single_display_amount": "$19.99",
      "display_amount": "$39.98",
      "total": "39.98",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 131,
        "name": "Product #71 - 2249",
        "sku": "SKU-130",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-71-2249",
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
        "product_id": 71,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [

      ],
      "vendor_name": "Vendor #214",
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
X-Spree-Order-Token: b85nrZPuzP8X1P-FQ05lOg
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/cart`

#### Parameters


```json
user_id&order_token=b85nrZPuzP8X1P-FQ05lOg&line_item[variant_id]=123&line_item[quantity]=2&line_item[vendor_id]=200
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
ETag: W/&quot;03888e9e7191ddb12b3d5dce49f1cdd7&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 73e86f75-aaef-48ba-b888-a26306befc2e
X-Runtime: 0.356243
Vary: Origin
Content-Length: 2695
200 OK
```


```json
{
  "id": 17,
  "number": "M809375619",
  "item_total": "39.98",
  "total": "39.98",
  "ship_total": "0.0",
  "state": "cart",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2020-06-22T09:29:44.481-04:00",
  "updated_at": "2020-06-22T09:29:44.611-04:00",
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
  "token": "nlmPyVa0mrq4YPrzJhF9Qg",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order?order=M809375619&bzip=&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [

  ],
  "bill_address": null,
  "ship_address": null,
  "line_items": [
    {
      "id": 19,
      "quantity": 2,
      "price": "19.99",
      "variant_id": 123,
      "vendor_id": 200,
      "single_display_amount": "$19.99",
      "display_amount": "$39.98",
      "total": "39.98",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 123,
        "name": "Product #67 - 8457",
        "sku": "SKU-122",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-67-8457",
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

        ],
        "product_id": 67,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [

      ],
      "vendor_name": "Vendor #200",
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
Authorizat IO N: Bearer cd088a6f75bf2fdec9677c047b5c06d8bf1aadaeed49b16f
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
X-Request-Id: 389494aa-6f34-4187-98f4-d7df30f78ebe
X-Runtime: 0.034148
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
GET /api/orders/M485122892
Accept: application/json
Authorizat IO N: Bearer 5ff1de6ac7bf4f85c57f60f949275f35b1664e0bea406a08
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
ETag: W/&quot;ad59adabd2c0a0e544e5097c845533df&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 9ad0894a-6e0f-437f-a362-7c5e57ab6f60
X-Runtime: 0.380545
Vary: Origin
Content-Length: 7980
200 OK
```


```json
{
  "id": 21,
  "number": "M485122892",
  "item_total": "20.0",
  "total": "118.0",
  "ship_total": "100.0",
  "state": "payment",
  "adjustment_total": "-2.0",
  "user_id": 74,
  "created_at": "2020-06-22T09:29:51.240-04:00",
  "updated_at": "2020-06-22T09:29:52.911-04:00",
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
  "token": "rORa-kOJR3BfJ-rXElbDUg",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order?order=M485122892&bzip=10030&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [

  ],
  "bill_address": {
    "id": 35,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "PO Box 1337",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10030",
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
    "id": 36,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "A Different Road",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10031",
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
      "id": 24,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 137,
      "vendor_id": 231,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "9.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 137,
        "name": "Product #74 - 107",
        "sku": "SKU-136",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-74-107",
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
      "vendor_name": "Vendor #231",
      "country_iso": "US",
      "adjustments": [
        {
          "id": 1,
          "source_type": "Spree::PromotionAction",
          "source_id": 3,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 24,
          "amount": "-1.0",
          "label": "Promotion (10% off)",
          "promotion_code_id": 3,
          "finalized": false,
          "eligible": true,
          "created_at": "2020-06-22T09:29:52.451-04:00",
          "updated_at": "2020-06-22T09:29:52.451-04:00",
          "display_amount": "-$1.00"
        }
      ]
    },
    {
      "id": 25,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 139,
      "vendor_id": 231,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "9.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 139,
        "name": "Product #75 - 7142",
        "sku": "SKU-138",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-75-7142",
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
            "id": 64,
            "name": "Size-64",
            "presentation": "S",
            "option_type_name": "foo-size-64",
            "option_type_id": 64,
            "option_type_presentation": "Size",
            "position": 1
          }
        ],
        "images": [

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
      "vendor_name": "Vendor #231",
      "country_iso": "US",
      "adjustments": [
        {
          "id": 2,
          "source_type": "Spree::PromotionAction",
          "source_id": 3,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 25,
          "amount": "-1.0",
          "label": "Promotion (10% off)",
          "promotion_code_id": 3,
          "finalized": false,
          "eligible": true,
          "created_at": "2020-06-22T09:29:52.481-04:00",
          "updated_at": "2020-06-22T09:29:52.481-04:00",
          "display_amount": "-$1.00"
        }
      ]
    }
  ],
  "payments": [

  ],
  "shipments": [
    {
      "id": 24,
      "tracking": null,
      "tracking_url": null,
      "number": "H48520542318",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M485122892",
      "stock_location_name": "NY Warehouse 40",
      "giftwrappable": false,
      "stock_location_id": 40,
      "giftwrap": null,
      "shipping_rates": [
        {
          "id": 24,
          "name": "UPS Ground",
          "admin_name": null,
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 15,
          "shipping_method_code": "UPS_GROUND",
          "extra_cost": "",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 24,
        "name": "UPS Ground",
        "admin_name": null,
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 15,
        "shipping_method_code": "UPS_GROUND",
        "extra_cost": "",
        "is_flat_rate": false,
        "is_flat_rate_expedited": false,
        "is_free_shipping": false,
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
              "id": 36,
              "name": "ShippingCategory #34"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 137,
          "quantity": 1,
          "states": {
            "on_hand": 1
          }
        },
        {
          "variant_id": 139,
          "quantity": 1,
          "states": {
            "on_hand": 1
          }
        }
      ],
      "adjustments": [
        {
          "id": 4,
          "source_type": "Spree::PromotionAction",
          "source_id": 4,
          "adjustable_type": "Spree::Shipment",
          "adjustable_id": 24,
          "amount": "-10.0",
          "label": "Shipping",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2020-06-22T09:29:52.708-04:00",
          "updated_at": "2020-06-22T09:29:52.708-04:00",
          "display_amount": "-$10.00"
        },
        {
          "id": 3,
          "source_type": "Spree::PromotionAction",
          "source_id": 4,
          "adjustable_type": "Spree::Shipment",
          "adjustable_id": 24,
          "amount": "-9.99",
          "label": "Shipping",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2020-06-22T09:29:52.686-04:00",
          "updated_at": "2020-06-22T09:29:52.686-04:00",
          "display_amount": "-$9.99"
        }
      ],
      "stock_location_address": "NY Warehouse 40, Washington, AL",
      "country_iso": "US",
      "international_shipping": false,
      "delivery_estimation": "Jun 24"
    }
  ],
  "adjustments": [
    {
      "id": 5,
      "source_type": "Spree::Promotion",
      "source_id": 4,
      "adjustable_type": "Spree::Order",
      "adjustable_id": 21,
      "amount": "20.0",
      "label": "adj1",
      "promotion_code_id": null,
      "finalized": false,
      "eligible": true,
      "created_at": "2020-06-22T09:29:52.725-04:00",
      "updated_at": "2020-06-22T09:29:52.725-04:00",
      "display_amount": "$20.00"
    },
    {
      "id": 6,
      "source_type": "Spree::Promotion",
      "source_id": 4,
      "adjustable_type": "Spree::Order",
      "adjustable_id": 21,
      "amount": "30.0",
      "label": "adj2",
      "promotion_code_id": null,
      "finalized": false,
      "eligible": true,
      "created_at": "2020-06-22T09:29:52.736-04:00",
      "updated_at": "2020-06-22T09:29:52.736-04:00",
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
GET /api/orders/M636611353
Accept: application/json
Authorizat IO N: 5ffaaa824dff334707e2292e0d6a4751c7c8b175fc6f7f39
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
X-Request-Id: 07350c72-5c85-444c-b6c2-f1974bd5151d
X-Runtime: 0.025616
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
Content-Type: application/json
Cache-Control: no-cache
X-Request-Id: 6c307c48-c40f-4e47-ad21-71aef47d9546
X-Runtime: 0.007696
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
Authorization: Bearer 8fa1d06ccad6d18a4f79f93679e46df11a5871b8ca5db022
ETag: W/&quot;7cd58ca188411ee88ebdb64c672a8c09&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: d12da828-9afb-4cd1-a2d2-37b22650b361
X-Runtime: 0.043528
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
  "created_at": "2020-06-22T09:29:22.446-04:00",
  "updated_at": "2020-06-22T09:29:22.451-04:00",
  "spree_api_key": "8fa1d06ccad6d18a4f79f93679e46df11a5871b8ca5db022",
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
X-Request-Id: 65602bd3-6f1b-4cb6-af56-aadcbbecba42
X-Runtime: 0.052097
Vary: Origin
204 No Content
```




# Products

Get all products, queryable by ransack

## Fetch a single product by id


### Request

#### Endpoint

```plaintext
GET /api/products/product-36-5308
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
Date: Mon, 22 Jun 2020 13:29:27 GMT
Surrogate-Control: max-age=900
Surrogate-Key: product_id=1
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;c8e19134f1345cd113a4aef3b5183af8&quot;
X-Request-Id: c5058c36-5b7a-45bc-b7c6-c335fbbb223e
X-Runtime: 0.154644
Vary: Origin
Content-Length: 1616
200 OK
```


```json
{
  "id": 36,
  "name": "Product #36 - 5308",
  "description": "As seen on TV!",
  "available_on": "2019-06-22T09:29:27.494-04:00",
  "slug": "product-36-5308",
  "meta_description": null,
  "meta_keywords": null,
  "taxon_ids": [
    16
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
      "id": 14,
      "name": "Clothing",
      "taxonomy_id": 6,
      "created_at": "2020-06-22T09:29:27.278-04:00",
      "url": "/category/clothing",
      "position": 1
    },
    {
      "id": 15,
      "name": "Girl",
      "taxonomy_id": 6,
      "created_at": "2020-06-22T09:29:27.346-04:00",
      "url": "/category/clothing/girl",
      "position": 2
    },
    {
      "id": 16,
      "name": "Dresses",
      "taxonomy_id": 6,
      "created_at": "2020-06-22T09:29:27.439-04:00",
      "url": "/category/clothing/girl/dresses",
      "position": 3
    }
  ],
  "has_variants": false,
  "master": {
    "id": 61,
    "name": "Product #36 - 5308",
    "sku": "SKU-61",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": true,
    "slug": "product-36-5308",
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
        "name": "Dresses",
        "pretty_name": "Category -> Clothing -> Girl -> Dresses",
        "permalink": "category/clothing/girl/dresses",
        "parent_id": 15,
        "taxonomy_id": 6,
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
Date: Mon, 22 Jun 2020 13:29:23 GMT
Surrogate-Control: max-age=900
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;0c7376db113e210311c97b916c9a4730&quot;
X-Request-Id: 620224bb-82a8-43c3-8883-8b923ac1d7a1
X-Runtime: 0.209686
Vary: Origin
Content-Length: 1288
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
      "id": 26,
      "name": "Product #26 - 7763",
      "description": "As seen on TV!",
      "available_on": "2019-06-22T09:29:22.744-04:00",
      "slug": "product-26-7763",
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
        "id": 51,
        "name": "Product #26 - 7763",
        "sku": "SKU-51",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-26-7763",
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
Date: Mon, 22 Jun 2020 13:29:25 GMT
Surrogate-Control: max-age=900
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;fc21644cefb4b3f9cd485805da85e281&quot;
X-Request-Id: fab6121c-5194-4f7d-a688-542c544f0092
X-Runtime: 0.111689
Vary: Origin
Content-Length: 375
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
      "id": 31,
      "name": "Product #31 - 1836",
      "slug": "product-31-1836",
      "master_id": 56,
      "display_price": "$0.00",
      "brand": "Maison You",
      "brand_slug": "maison-you",
      "brand_url": "/brand/maison-you",
      "brand_description": null,
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
GET /api/products?ids=28%2C29%2C30
Host: example.org
Cookie: 
```

`GET /api/products`

#### Parameters


```json
ids: 28,29,30
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
Date: Mon, 22 Jun 2020 13:29:24 GMT
Surrogate-Control: max-age=900
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;9f6a8c178f5b7e52a8a976a560a749f8&quot;
X-Request-Id: b16eb1a6-8f1a-432b-a5e8-fc53c7198ad3
X-Runtime: 0.286754
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
      "id": 28,
      "name": "Product #28 - 5846",
      "description": "As seen on TV!",
      "available_on": "2019-06-22T09:29:23.803-04:00",
      "slug": "product-28-5846",
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
        "id": 53,
        "name": "Product #28 - 5846",
        "sku": "SKU-53",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-28-5846",
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
      "id": 29,
      "name": "Product #29 - 9721",
      "description": "As seen on TV!",
      "available_on": "2019-06-22T09:29:24.012-04:00",
      "slug": "product-29-9721",
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
        "id": 54,
        "name": "Product #29 - 9721",
        "sku": "SKU-54",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-29-9721",
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
      "id": 30,
      "name": "Product #30 - 3715",
      "description": "As seen on TV!",
      "available_on": "2019-06-22T09:29:24.278-04:00",
      "slug": "product-30-3715",
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
        "id": 55,
        "name": "Product #30 - 3715",
        "sku": "SKU-55",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-30-3715",
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
GET /api/taxons/products?id=12
Host: example.org
Cookie: 
```

`GET /api/taxons/products`

#### Parameters


```json
id: 12
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
ETag: W/&quot;677b306b08bb20bcd805e1215d5a71dc&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 067941ae-43eb-4749-aed8-3bd7d8608925
X-Runtime: 0.144612
Vary: Origin
Content-Length: 1312
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
      "id": 35,
      "name": "Product #35 - 4314",
      "description": "As seen on TV!",
      "available_on": "2019-06-22T09:29:26.793-04:00",
      "slug": "product-35-4314",
      "meta_description": null,
      "meta_keywords": null,
      "taxon_ids": [
        12
      ],
      "total_on_hand": 0,
      "meta_title": null,
      "display_price": "$0.00",
      "brand": "Ruby on Rails - 2",
      "brand_slug": "ruby-on-rails-2",
      "brand_url": "/ruby-on-rails-2",
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
        "id": 60,
        "name": "Product #35 - 4314",
        "sku": "SKU-60",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-35-4314",
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
          "taxon_id": 12,
          "position": 1,
          "taxon": {
            "id": 12,
            "name": "Ruby on Rails - 2",
            "pretty_name": "Ruby on Rails - 2",
            "permalink": "ruby-on-rails-2",
            "parent_id": null,
            "taxonomy_id": 5,
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



## Fetch products by taxon permalink


### Request

#### Endpoint

```plaintext
GET /api/taxons/products?permalink=ruby-on-rails-1
Host: example.org
Cookie: 
```

`GET /api/taxons/products`

#### Parameters


```json
permalink: ruby-on-rails-1
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
ETag: W/&quot;3022995d7190fa0bb8e4f06e0e794af6&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: c27319a9-ff4a-4e50-b15d-61b58a10804b
X-Runtime: 0.158585
Vary: Origin
Content-Length: 1309
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
      "id": 33,
      "name": "Product #33 - 5931",
      "description": "As seen on TV!",
      "available_on": "2019-06-22T09:29:25.833-04:00",
      "slug": "product-33-5931",
      "meta_description": null,
      "meta_keywords": null,
      "taxon_ids": [
        9
      ],
      "total_on_hand": 0,
      "meta_title": null,
      "display_price": "$0.00",
      "brand": "Ruby on Rails - 1",
      "brand_slug": "ruby-on-rails-1",
      "brand_url": "/ruby-on-rails-1",
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
        "id": 58,
        "name": "Product #33 - 5931",
        "sku": "SKU-58",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-33-5931",
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
          "taxon_id": 9,
          "position": 1,
          "taxon": {
            "id": 9,
            "name": "Ruby on Rails - 1",
            "pretty_name": "Ruby on Rails - 1",
            "permalink": "ruby-on-rails-1",
            "parent_id": null,
            "taxonomy_id": 4,
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



## Get all products info


### Request

#### Endpoint

```plaintext
GET /api/sitemap/products
Accept: application/json
Authorizat IO N: Bearer 80dec0433b36ef9393b67ff112a4e3f799f927c82d0261b7
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
X-Request-Id: fc1d7151-ec96-475d-a5b2-5267001a7244
X-Runtime: 0.064745
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
X-Request-Id: f6e3dfbd-dbba-4c58-a7aa-220754544a3a
X-Runtime: 0.036873
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
GET /api/recently_viewed?recently_viewed[session_id]=cfpwsfbalr0511e8d0bmriz4fyn9fqdbblyhp0cj8xle11k731tmjffntc04o1jvkv18lkymbvmf5n07g8wiqahp1cei7xyobn4djwnrmtpgk0stsuaaif3rfkptm6ik879e0jon4txoplizx6f7d4nsh0i6tyh52lqg1jw22eisbim2bpf6sz5pelscm6t2uxa2o87ssi6428mgl1ghjhzaf4alf407st2w6hzu2lp4l80odxs8uw8bv818fl6
Accept: application/json
Authorizat IO N: Bearer d7142308d01e4af209cf3a3966be22e254edea6b7c418d63
Host: example.org
Cookie: 
```

`GET /api/recently_viewed`

#### Parameters


```json
recently_viewed: {&quot;session_id&quot;=&gt;&quot;cfpwsfbalr0511e8d0bmriz4fyn9fqdbblyhp0cj8xle11k731tmjffntc04o1jvkv18lkymbvmf5n07g8wiqahp1cei7xyobn4djwnrmtpgk0stsuaaif3rfkptm6ik879e0jon4txoplizx6f7d4nsh0i6tyh52lqg1jw22eisbim2bpf6sz5pelscm6t2uxa2o87ssi6428mgl1ghjhzaf4alf407st2w6hzu2lp4l80odxs8uw8bv818fl6&quot;}
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
ETag: W/&quot;0f2ac7ecee7750c64495957258a8a4fe&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 6d456ed2-3142-430d-84c8-2a452d44854d
X-Runtime: 0.012107
Vary: Origin
Content-Length: 119
200 OK
```


```json
[
  {
    "at": "2020-06-22T09:29:56.631-04:00",
    "variant_id": "var1"
  },
  {
    "at": "2020-06-22T09:34:56.631-04:00",
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
Authorizat IO N: Bearer 53a237252c8c77e1716074f66ce4b6c5fe05a7681a5df1e4
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/recently_viewed`

#### Parameters


```json
recently_viewed[session_id]=xlku3w4jkhigo8ow3cnzjdth9xzd0rv0hlwnn724foi6gddtjv6s3gdjtub1aobvpnmjhpulg9b8m0zs0ptapwhgzqv40f7j69aqsk0sfgvfezc0vfp2qh3p2aipy1h8cx4q26skaiu9egv85qcp76sc810tbeofz5wj92sa25v8ywojhtai5dhazm5un9vq2jqenvk0gt7cs31dpyt69x4vbahmamoa6d3nhtw4wtjxtnyiokgzyi2jashvs6v&recently_viewed[variant_id]=foo
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
X-Request-Id: bc708dc9-f160-4601-b2cd-30f2b21dbcf1
X-Runtime: 0.054814
Vary: Origin
204 No Content
```




# Return Authorizations

Get user return authorizations

## Can get another user&#39;s return authorization


### Request

#### Endpoint

```plaintext
GET /api/returns/RA056342576
Authorizat IO N: Bearer 2e10102b049e4866e40c27faa68b150b5f3cc5cc0bec9f7f
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
ETag: W/&quot;42166ec35f5987c4197d02a1fb001eb8&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 891227c8-0f77-4a75-8263-5d3e161ae38f
X-Runtime: 0.126218
Vary: Origin
Content-Length: 3033
200 OK
```


```json
{
  "id": 3,
  "number": "RA056342576",
  "state": "authorized",
  "order_id": 28,
  "memo": "Items were broken",
  "created_at": "2020-06-22T09:30:12.051-04:00",
  "updated_at": "2020-06-22T09:30:12.051-04:00",
  "amount": "10.0",
  "reason": {
    "id": 5,
    "name": "Defect #5",
    "active": true,
    "mutable": true,
    "created_at": "2020-06-22T09:30:12.028-04:00",
    "updated_at": "2020-06-22T09:30:12.028-04:00",
    "mirakl_code": null
  },
  "order": {
    "id": 28,
    "number": "M622521311",
    "item_total": "10.0",
    "total": "110.0",
    "state": "complete",
    "adjustment_total": "0.0",
    "user_id": 91,
    "completed_at": "2020-06-22T09:30:11.780-04:00",
    "bill_address_id": 49,
    "ship_address_id": 50,
    "payment_total": "110.0",
    "shipment_state": "shipped",
    "payment_state": "paid",
    "email": "email91@example.com",
    "special_instructions": null,
    "created_at": "2020-06-22T09:30:11.507-04:00",
    "updated_at": "2020-06-22T09:30:11.963-04:00",
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
    "guest_token": "l7SXXC7q8HomMuI9E_qHsg",
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
    "id": 50,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "A Different Road",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10045",
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
    "id": 49,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "PO Box 1337",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10044",
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
      "name": "Product #88 - 1650",
      "brand": null,
      "brand_slug": null,
      "image": null,
      "product_slug": "product-88-1650",
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
        "id": 16,
        "name": "Credit Card"
      },
      "source": {
        "id": 3,
        "month": "12",
        "year": "2021",
        "cc_type": null,
        "last_digits": "1111",
        "name": "Spree Commerce",
        "gateway_customer_profile_id": "BGS-015430",
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
Authorizat IO N: Bearer 527f4cf959d9914a6a444b9d6551a627006b03b28ea7167c
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
ETag: W/&quot;c72b006df57eaa8779f0d0cc60812ecb&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 4b5de8ec-b518-4efc-9d01-2294e38ee65b
X-Runtime: 0.033561
Vary: Origin
Content-Length: 169
200 OK
```


```json
{
  "return_authorizations": [
    {
      "number": "RA122084585",
      "created_at": "2020-06-22T09:30:09.227-04:00",
      "return_amount": "10.0",
      "order_number": "M347890629",
      "state": "authorized"
    }
  ]
}
```



## returns a 200


### Request

#### Endpoint

```plaintext
GET /api/returns/RA417638813
Authorizat IO N: Bearer f547cb011dc000e5cdc00e5641515f1d9a475c6392a025b8
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
ETag: W/&quot;c2a1d04b85f49ca7f4f103df3bd0bdab&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: a38eff4b-d927-4051-85b1-8f03f3a120f1
X-Runtime: 0.176481
Vary: Origin
Content-Length: 2956
200 OK
```


```json
{
  "id": 2,
  "number": "RA417638813",
  "state": "authorized",
  "order_id": 27,
  "memo": "Items were broken",
  "created_at": "2020-06-22T09:30:10.529-04:00",
  "updated_at": "2020-06-22T09:30:10.529-04:00",
  "amount": "10.0",
  "reason": {
    "id": 3,
    "name": "Defect #3",
    "active": true,
    "mutable": true,
    "created_at": "2020-06-22T09:30:10.517-04:00",
    "updated_at": "2020-06-22T09:30:10.517-04:00",
    "mirakl_code": null
  },
  "order": {
    "id": 27,
    "number": "M799194642",
    "item_total": "10.0",
    "total": "110.0",
    "state": "complete",
    "adjustment_total": "0.0",
    "user_id": 90,
    "completed_at": "2020-06-22T09:30:10.287-04:00",
    "bill_address_id": 47,
    "ship_address_id": 48,
    "payment_total": "110.0",
    "shipment_state": "shipped",
    "payment_state": "paid",
    "email": "email90@example.com",
    "special_instructions": null,
    "created_at": "2020-06-22T09:30:10.056-04:00",
    "updated_at": "2020-06-22T09:30:10.463-04:00",
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
    "guest_token": "YybO7sAv2CHcISIysZfF3g",
    "canceled_at": null,
    "canceler_id": null,
    "store_id": 26,
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
    "lastname": null,
    "full_name": "John",
    "address1": "A Different Road",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10043",
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
  "bill_address": {
    "id": 47,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "PO Box 1337",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10042",
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
  "return_items": [
    {
      "name": "Product #87 - 5281",
      "brand": null,
      "brand_slug": null,
      "image": null,
      "product_slug": "product-87-5281",
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
        "id": 14,
        "name": "Credit Card"
      },
      "source": {
        "id": 2,
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
GET /api/returns/RA223618246
Authorizat IO N: Bearer 2ce263327a43f984e84eb49fdc1e49d720ff338f471c7e39
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
X-Request-Id: 33001356-0a61-4d21-a1c5-948356824a72
X-Runtime: 0.024851
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
stock_request[email]=kerri.schimmel%40bayerraynor.biz&stock_request[variant_id]=159
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
X-Request-Id: 2afd82fc-4558-44d3-9ddb-56584574a7fd
X-Runtime: 0.019685
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
stock_request[email]=foo&stock_request[variant_id]=157
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
X-Request-Id: b1e869bc-bd4c-4d2b-a86a-25d99a3b74c9
X-Runtime: 0.033700
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
stock_request[email]=larita%40rowehamill.biz&stock_request[variant_id]=155
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
X-Request-Id: df7c41e7-ee62-417e-850b-384dcdbe67f1
X-Runtime: 0.054628
Vary: Origin
Content-Length: 93
422 Unprocessable Entity
```


```json
{
  "success": false,
  "message": [
    "Email This email is already on the waitlist for this product."
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
Authorizat IO N: Bearer b6b14ab8450c078db285250e6820c8bc924d96705246aeb3
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
ETag: W/&quot;b09721bb06095189af33d85113f3b140&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: a737cd8f-238e-4a2b-a729-4e8c8fade93f
X-Runtime: 0.268740
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
      "created_at": "2020-06-22T09:28:51.723-04:00"
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
Authorizat IO N: Bearer 
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/subscribers`

#### Parameters


```json
subscriber[email]=jed%40mcclure.com&subscriber[first_name]=Rebecka&subscriber[last_name]=Gleichner&subscriber[source]=Quia+velit+nemo+qui+quibusdam+perferendis+nam+nisi+exercitationem.&subscriber[list_id]=2gzs28
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
ETag: W/&quot;bf059a8d90e42ddb26624114e63b84f0&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 9fa4ddb3-6545-4bc7-b3e0-25c3a31cdf57
X-Runtime: 0.025655
Vary: Origin
Content-Length: 273
201 Created
```


```json
{
  "id": 2,
  "user_id": null,
  "list_id": "2gzs28",
  "email": "jed@mcclure.com",
  "first_name": "Rebecka",
  "last_name": "Gleichner",
  "source": "Quia velit nemo qui quibusdam perferendis nam nisi exercitationem.",
  "phone": null,
  "status": "subscribed",
  "created_at": "2020-06-22T09:30:07.556-04:00"
}
```



## Create a subscriber for the associated user


### Request

#### Endpoint

```plaintext
POST /api/subscribers
Accept: application/json
Authorizat IO N: Bearer 265469bc64d5f990982949f82f244e7e48da45f5fac2852a
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/subscribers`

#### Parameters


```json
subscriber[email]&subscriber[first_name]=Breana&subscriber[last_name]=Wyman&subscriber[source]=Illo+voluptas+rerum+placeat+corporis.&subscriber[list_id]=hoj7f0
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
ETag: W/&quot;adcccae99c7fb4f4a80787a95b4c7371&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: aac17b0d-60e4-4f15-8d02-c8e1a3ab343b
X-Runtime: 0.029439
Vary: Origin
Content-Length: 241
201 Created
```


```json
{
  "id": 3,
  "user_id": 85,
  "list_id": "hoj7f0",
  "email": "email85@example.com",
  "first_name": "Breana",
  "last_name": "Wyman",
  "source": "Illo voluptas rerum placeat corporis.",
  "phone": null,
  "status": "subscribed",
  "created_at": "2020-06-22T09:30:07.616-04:00"
}
```



## Get all subscribers


### Request

#### Endpoint

```plaintext
GET /api/subscribers
Accept: application/json
Authorizat IO N: Bearer 34c03fc2fe5bb6260dddb56ce1e5ad7d9bdf7131a6eb9760
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
ETag: W/&quot;421297af5b97150de0b8f322509fcbec&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: bd51d084-e92a-4c71-b839-b9ffb665cf7a
X-Runtime: 0.028655
Vary: Origin
Content-Length: 738
200 OK
```


```json
{
  "subscribers": [
    {
      "id": 5,
      "user_id": null,
      "list_id": "i3jxiz",
      "email": "ethyl_mohr@fisherwillms.ca",
      "first_name": "Shawnee",
      "last_name": "Bauch",
      "source": null,
      "phone": null,
      "status": "subscribed",
      "created_at": "2020-06-22T09:30:07.759-04:00"
    },
    {
      "id": 6,
      "user_id": null,
      "list_id": "yxt1ha",
      "email": "tanisha.goldner@kihngutmann.name",
      "first_name": "Sylvia",
      "last_name": "Fahey",
      "source": null,
      "phone": null,
      "status": "subscribed",
      "created_at": "2020-06-22T09:30:07.770-04:00"
    },
    {
      "id": 7,
      "user_id": null,
      "list_id": "vkkfot",
      "email": "florida.ohara@gerlach.us",
      "first_name": "Herman",
      "last_name": "Hirthe",
      "source": null,
      "phone": null,
      "status": "subscribed",
      "created_at": "2020-06-22T09:30:07.781-04:00"
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
PATCH /api/subscribers/1
Accept: application/json
Authorizat IO N: Bearer addffd04fe11106adc6a10cf1fac80b078a67e70b5722a7b
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/subscribers/:id`

#### Parameters


```json
subscriber[source]=Animi+qui+velit+ratione+qui+aspernatur.
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
ETag: W/&quot;affb610e6eb00d8bf5cad2801d809223&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 6ffa6cc0-940f-4aed-b256-3a6ee00de5e0
X-Runtime: 0.104813
Vary: Origin
Content-Length: 253
200 OK
```


```json
{
  "id": 1,
  "user_id": 84,
  "list_id": "d6dhau",
  "email": "email84@example.com",
  "first_name": "Noella",
  "last_name": "King",
  "source": "Animi qui velit ratione qui aspernatur.",
  "phone": null,
  "status": "subscribed_and_synced",
  "created_at": "2020-06-22T09:30:07.417-04:00"
}
```



## unsubscribe a known subscriber


### Request

#### Endpoint

```plaintext
DELETE /api/subscribers
Accept: application/json
Authorizat IO N: Bearer 86008b03dc19dbef8a41f864909307d022d1211de6c133fb
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`DELETE /api/subscribers`

#### Parameters


```json
subscriber[email]=email86%40example.com&subscriber[list_id]=m1gztp
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
X-Request-Id: c3a75c1f-7e75-4d1e-b791-c482e4153967
X-Runtime: 0.027108
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
Authorizat IO N: Bearer 7f99cc7460ebe0cc8131ee517be6438d5fae0dc45e8cb51b
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`DELETE /api/subscribers`

#### Parameters


```json
subscriber[email]=chet.jaskolski%40blanda.com&subscriber[list_id]=8odcim
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
X-Request-Id: cd0811ee-b070-4ef3-bdf0-3607c64260fc
X-Runtime: 0.012951
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
Authorizat IO N: Bearer 25a6a4e5467fd8eb32adac8aaaf97bd5fbd595258d7914f8
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
X-Request-Id: b9c2b6b1-ab73-4871-b811-e5c4445932f5
X-Runtime: 0.061294
Vary: Origin
Content-Length: 2
200 OK
```


```json
[

]
```



# Taxons API

Return all brand taxons that have products in stock

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
ETag: W/&quot;6e06307915c3942eb90c90f74f5b0171&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: c228e27f-524f-4ce2-a14d-a5c088276211
X-Runtime: 0.111275
Vary: Origin
Content-Length: 4458
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
      "id": 27,
      "name": "Category",
      "pretty_name": "Category",
      "permalink": "category",
      "parent_id": null,
      "taxonomy_id": 12,
      "url_override": null,
      "description": "Category",
      "icon": "/assets/default_taxon.png",
      "taxons": [
        {
          "id": 28,
          "name": "Kids",
          "pretty_name": "Category -> Kids",
          "permalink": "category/kids",
          "parent_id": 27,
          "taxonomy_id": 12,
          "url_override": null
        }
      ]
    },
    {
      "id": 28,
      "name": "Kids",
      "pretty_name": "Category -> Kids",
      "permalink": "category/kids",
      "parent_id": 27,
      "taxonomy_id": 12,
      "url_override": null,
      "description": "Kids",
      "icon": "/assets/default_taxon.png",
      "taxons": [
        {
          "id": 29,
          "name": "Boys",
          "pretty_name": "Category -> Kids -> Boys",
          "permalink": "category/kids/boys",
          "parent_id": 28,
          "taxonomy_id": 12,
          "url_override": null
        },
        {
          "id": 32,
          "name": "Girls",
          "pretty_name": "Category -> Kids -> Girls",
          "permalink": "category/kids/girls",
          "parent_id": 28,
          "taxonomy_id": 12,
          "url_override": null
        }
      ]
    },
    {
      "id": 29,
      "name": "Boys",
      "pretty_name": "Category -> Kids -> Boys",
      "permalink": "category/kids/boys",
      "parent_id": 28,
      "taxonomy_id": 12,
      "url_override": null,
      "description": "Boys",
      "icon": "/assets/default_taxon.png",
      "taxons": [
        {
          "id": 30,
          "name": "Boys Tops",
          "pretty_name": "Category -> Kids -> Boys -> Boys Tops",
          "permalink": "category/kids/boys/boys-tops",
          "parent_id": 29,
          "taxonomy_id": 12,
          "url_override": null
        }
      ]
    },
    {
      "id": 30,
      "name": "Boys Tops",
      "pretty_name": "Category -> Kids -> Boys -> Boys Tops",
      "permalink": "category/kids/boys/boys-tops",
      "parent_id": 29,
      "taxonomy_id": 12,
      "url_override": null,
      "description": "Boys Tops",
      "icon": "/assets/default_taxon.png",
      "taxons": [
        {
          "id": 31,
          "name": "Boys Shirts",
          "pretty_name": "Category -> Kids -> Boys -> Boys Tops -> Boys Shirts",
          "permalink": "category/kids/boys/boys-tops/boys-shirts",
          "parent_id": 30,
          "taxonomy_id": 12,
          "url_override": null
        }
      ]
    },
    {
      "id": 31,
      "name": "Boys Shirts",
      "pretty_name": "Category -> Kids -> Boys -> Boys Tops -> Boys Shirts",
      "permalink": "category/kids/boys/boys-tops/boys-shirts",
      "parent_id": 30,
      "taxonomy_id": 12,
      "url_override": null,
      "description": "Boys Shirts",
      "icon": "/assets/default_taxon.png",
      "taxons": [

      ]
    },
    {
      "id": 32,
      "name": "Girls",
      "pretty_name": "Category -> Kids -> Girls",
      "permalink": "category/kids/girls",
      "parent_id": 28,
      "taxonomy_id": 12,
      "url_override": null,
      "description": "Girls",
      "icon": "/assets/default_taxon.png",
      "taxons": [
        {
          "id": 33,
          "name": "Girls Tops",
          "pretty_name": "Category -> Kids -> Girls -> Girls Tops",
          "permalink": "category/kids/girls/girls-tops",
          "parent_id": 32,
          "taxonomy_id": 12,
          "url_override": null
        }
      ]
    },
    {
      "id": 33,
      "name": "Girls Tops",
      "pretty_name": "Category -> Kids -> Girls -> Girls Tops",
      "permalink": "category/kids/girls/girls-tops",
      "parent_id": 32,
      "taxonomy_id": 12,
      "url_override": null,
      "description": "Girls Tops",
      "icon": "/assets/default_taxon.png",
      "taxons": [
        {
          "id": 34,
          "name": "Girls Shirts",
          "pretty_name": "Category -> Kids -> Girls -> Girls Tops -> Girls Shirts",
          "permalink": "category/kids/girls/girls-tops/girls-shirts",
          "parent_id": 33,
          "taxonomy_id": 12,
          "url_override": null
        }
      ]
    },
    {
      "id": 34,
      "name": "Girls Shirts",
      "pretty_name": "Category -> Kids -> Girls -> Girls Tops -> Girls Shirts",
      "permalink": "category/kids/girls/girls-tops/girls-shirts",
      "parent_id": 33,
      "taxonomy_id": 12,
      "url_override": null,
      "description": "Girls Shirts",
      "icon": "/assets/default_taxon.png",
      "taxons": [

      ]
    },
    {
      "id": 35,
      "name": "Brand",
      "pretty_name": "Brand",
      "permalink": "brand",
      "parent_id": null,
      "taxonomy_id": 13,
      "url_override": null,
      "description": "Brand",
      "icon": "/assets/default_taxon.png",
      "taxons": [
        {
          "id": 36,
          "name": "Ruby on Rails - 3",
          "pretty_name": "Brand -> Ruby on Rails - 3",
          "permalink": "brand/ruby-on-rails-3",
          "parent_id": 35,
          "taxonomy_id": 13,
          "url_override": null
        },
        {
          "id": 37,
          "name": "Ruby on Rails - 4",
          "pretty_name": "Brand -> Ruby on Rails - 4",
          "permalink": "brand/ruby-on-rails-4",
          "parent_id": 35,
          "taxonomy_id": 13,
          "url_override": null
        }
      ]
    },
    {
      "id": 36,
      "name": "Ruby on Rails - 3",
      "pretty_name": "Brand -> Ruby on Rails - 3",
      "permalink": "brand/ruby-on-rails-3",
      "parent_id": 35,
      "taxonomy_id": 13,
      "url_override": null,
      "description": "Ruby on Rails - 3",
      "icon": "/assets/default_taxon.png",
      "taxons": [

      ]
    },
    {
      "id": 37,
      "name": "Ruby on Rails - 4",
      "pretty_name": "Brand -> Ruby on Rails - 4",
      "permalink": "brand/ruby-on-rails-4",
      "parent_id": 35,
      "taxonomy_id": 13,
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
ETag: W/&quot;2371b74d262068556e7b58f838714e3d&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 05a16aa8-1afd-41d1-9422-dd036a9f8a82
X-Runtime: 0.033264
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
      "id": 46,
      "name": "Brand",
      "pretty_name": "Brand",
      "permalink": "brand",
      "parent_id": null,
      "taxonomy_id": 15,
      "url_override": null,
      "description": "Brand",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 47,
      "name": "Ruby on Rails - 5",
      "pretty_name": "Brand -> Ruby on Rails - 5",
      "permalink": "brand/ruby-on-rails-5",
      "parent_id": 46,
      "taxonomy_id": 15,
      "url_override": null,
      "description": "Ruby on Rails - 5",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 48,
      "name": "Ruby on Rails - 6",
      "pretty_name": "Brand -> Ruby on Rails - 6",
      "permalink": "brand/ruby-on-rails-6",
      "parent_id": 46,
      "taxonomy_id": 15,
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
ETag: W/&quot;4738453e91697209a517d927753561d2&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: e9f73956-48f8-4820-9346-9bb70c0d8a1e
X-Runtime: 0.076864
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
      "id": 49,
      "name": "Category",
      "pretty_name": "Category",
      "permalink": "category",
      "parent_id": null,
      "taxonomy_id": 16,
      "url_override": null,
      "description": "Category",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 50,
      "name": "Kids",
      "pretty_name": "Category -> Kids",
      "permalink": "category/kids",
      "parent_id": 49,
      "taxonomy_id": 16,
      "url_override": null,
      "description": "Kids",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 51,
      "name": "Boys",
      "pretty_name": "Category -> Kids -> Boys",
      "permalink": "category/kids/boys",
      "parent_id": 50,
      "taxonomy_id": 16,
      "url_override": null,
      "description": "Boys",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 52,
      "name": "Boys Tops",
      "pretty_name": "Category -> Kids -> Boys -> Boys Tops",
      "permalink": "category/kids/boys/boys-tops",
      "parent_id": 51,
      "taxonomy_id": 16,
      "url_override": null,
      "description": "Boys Tops",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 53,
      "name": "Boys Shirts",
      "pretty_name": "Category -> Kids -> Boys -> Boys Tops -> Boys Shirts",
      "permalink": "category/kids/boys/boys-tops/boys-shirts",
      "parent_id": 52,
      "taxonomy_id": 16,
      "url_override": null,
      "description": "Boys Shirts",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 54,
      "name": "Girls",
      "pretty_name": "Category -> Kids -> Girls",
      "permalink": "category/kids/girls",
      "parent_id": 50,
      "taxonomy_id": 16,
      "url_override": null,
      "description": "Girls",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 55,
      "name": "Girls Tops",
      "pretty_name": "Category -> Kids -> Girls -> Girls Tops",
      "permalink": "category/kids/girls/girls-tops",
      "parent_id": 54,
      "taxonomy_id": 16,
      "url_override": null,
      "description": "Girls Tops",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 56,
      "name": "Girls Shirts",
      "pretty_name": "Category -> Kids -> Girls -> Girls Tops -> Girls Shirts",
      "permalink": "category/kids/girls/girls-tops/girls-shirts",
      "parent_id": 55,
      "taxonomy_id": 16,
      "url_override": null,
      "description": "Girls Shirts",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 57,
      "name": "Brand",
      "pretty_name": "Brand",
      "permalink": "brand",
      "parent_id": null,
      "taxonomy_id": 17,
      "url_override": null,
      "description": "Brand",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 58,
      "name": "Ruby on Rails - 7",
      "pretty_name": "Brand -> Ruby on Rails - 7",
      "permalink": "brand/ruby-on-rails-7",
      "parent_id": 57,
      "taxonomy_id": 17,
      "url_override": null,
      "description": "Ruby on Rails - 7",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 59,
      "name": "Ruby on Rails - 8",
      "pretty_name": "Brand -> Ruby on Rails - 8",
      "permalink": "brand/ruby-on-rails-8",
      "parent_id": 57,
      "taxonomy_id": 17,
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
ETag: W/&quot;6ed80722c9cb1ae6ff5685eac02b4676&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 0a3d0828-fd03-4925-9d15-520f503d2ea5
X-Runtime: 0.032622
Vary: Origin
Content-Length: 536
200 OK
```


```json
[
  {
    "id": 26,
    "parent_id": 25,
    "position": 0,
    "name": "brand_x",
    "permalink": "brand/brand_x",
    "taxonomy_id": 11,
    "lft": 6,
    "rgt": 7,
    "icon_file_name": null,
    "icon_content_type": null,
    "icon_file_size": null,
    "icon_updated_at": null,
    "description": null,
    "created_at": "2020-06-22T09:30:00.454-04:00",
    "updated_at": "2020-06-22T09:30:00.624-04:00",
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
    "google_product_category": null
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
ETag: W/&quot;c19c7c80140718f82118476deb5d5458&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 4c896b7d-4030-4720-8cfd-46eea2652931
X-Runtime: 0.020155
Vary: Origin
Content-Length: 144
200 OK
```


```json
[
  {
    "id": 22,
    "name": "Kids",
    "navigation_url": "/shop/kids",
    "parent_id": 21,
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
ETag: W/&quot;30f1702b2c20eef65472129e7c9d4ce5&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 203fdca4-2834-4d11-b918-4836305734d0
X-Runtime: 0.034196
Vary: Origin
Content-Length: 535
200 OK
```


```json
[
  {
    "id": 20,
    "parent_id": 19,
    "position": 0,
    "name": "brand_x",
    "permalink": "brand/brand_x",
    "taxonomy_id": 8,
    "lft": 6,
    "rgt": 7,
    "icon_file_name": null,
    "icon_content_type": null,
    "icon_file_size": null,
    "icon_updated_at": null,
    "description": null,
    "created_at": "2020-06-22T09:29:59.158-04:00",
    "updated_at": "2020-06-22T09:29:59.329-04:00",
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
    "google_product_category": null
  }
]
```



# Users

Unsubscribe a user. If the user is already in an unsubscribed state no records will be changed

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
user[email]=email97%40example.com&user[password]=secret
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
Authorization: Bearer 3d648bbf53e804be289c1c2451374a92278f5fea120cb6e6
ETag: W/&quot;655631ba588af4b856a56fffb5f0c396&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: bf11b4ac-b726-41b8-bcef-944f4244eca5
X-Runtime: 0.030703
Vary: Origin
Content-Length: 562
200 OK
```


```json
{
  "id": 97,
  "email": "email97@example.com",
  "persistence_token": null,
  "perishable_token": null,
  "last_request_at": null,
  "login": "email97@example.com",
  "ship_address_id": null,
  "bill_address_id": null,
  "created_at": "2020-06-22T09:30:13.972-04:00",
  "updated_at": "2020-06-22T09:30:13.977-04:00",
  "spree_api_key": "3d648bbf53e804be289c1c2451374a92278f5fea120cb6e6",
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
X-Spree-Order-Token: j4lGnJIr6fg0Ou2XfFYkkA
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/users/login`

#### Parameters


```json
user[email]=email98%40example.com&user[password]=secret&order_number=M956919400
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
Authorization: Bearer 1d9ad446688ecaf0345daec8334b429a889e6298928e0df0
ETag: W/&quot;417b2c100345c94418ef8adee1d81101&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: d0da688e-3ad3-499f-a53f-dae0be580f74
X-Runtime: 0.051604
Vary: Origin
Content-Length: 562
200 OK
```


```json
{
  "id": 98,
  "email": "email98@example.com",
  "persistence_token": null,
  "perishable_token": null,
  "last_request_at": null,
  "login": "email98@example.com",
  "ship_address_id": null,
  "bill_address_id": null,
  "created_at": "2020-06-22T09:30:14.032-04:00",
  "updated_at": "2020-06-22T09:30:14.037-04:00",
  "spree_api_key": "1d9ad446688ecaf0345daec8334b429a889e6298928e0df0",
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
Authorizat IO N: Bearer d3c9101af3a1fecaf6a1961ffee14e5bd18572f5211d314b
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
Authorization: Bearer d3c9101af3a1fecaf6a1961ffee14e5bd18572f5211d314b
ETag: W/&quot;b6e593c818c5b375103910993407ba88&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 9924856e-f382-4b29-a3b8-6919d89c4929
X-Runtime: 0.112501
Vary: Origin
Content-Length: 1522
200 OK
```


```json
{
  "email": "email99@example.com",
  "first_name": null,
  "last_name": null,
  "id": 99,
  "subscribed": false,
  "addresses": [
    {
      "id": 56,
      "firstname": "John",
      "lastname": null,
      "full_name": "John",
      "address1": "A Different Road",
      "address2": "Northwest",
      "city": "Herndon",
      "zipcode": "10051",
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
      "default": true
    },
    {
      "id": 55,
      "firstname": "John",
      "lastname": null,
      "full_name": "John",
      "address1": "PO Box 1337",
      "address2": "Northwest",
      "city": "Herndon",
      "zipcode": "10050",
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
        "created_at": "2020-06-22T09:30:15.304-04:00",
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
        "created_at": "2020-06-22T09:30:15.348-04:00",
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
        "created_at": "2020-06-22T09:30:15.393-04:00",
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
Authorization: Bearer fe2f63bd5df6f4a6444a386a0a9305694064994dbcd30ea6
ETag: W/&quot;64c75f9d5c4b1607baa0bedf196661be&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 3de891d4-ad84-47bd-b882-d139ee30de0c
X-Runtime: 0.089046
Vary: Origin
Content-Length: 186
201 Created
```


```json
{
  "id": 100,
  "email": "test@example.com",
  "created_at": "2020-06-22T09:30:15.565-04:00",
  "updated_at": "2020-06-22T09:30:15.573-04:00",
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
X-Spree-Order-Token: -Rtbs1h5c2mc4wK1fRj3EQ
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/users`

#### Parameters


```json
user[email]=test%40example.com&user[password]=test123&user[password_confirmation]=test123&order_number=M860565310
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
Authorization: Bearer 24945a6c758249b31ec3bb86e628f2f73f9b935bbf4dd62f
ETag: W/&quot;f8dd746c1cf4874a60a1692c8fb4cd31&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: b64e8fc3-71dd-4aea-aeed-61885d17d564
X-Runtime: 0.075499
Vary: Origin
Content-Length: 186
201 Created
```


```json
{
  "id": 101,
  "email": "test@example.com",
  "created_at": "2020-06-22T09:30:16.893-04:00",
  "updated_at": "2020-06-22T09:30:16.898-04:00",
  "subscribed": false,
  "bill_address": null,
  "ship_address": null
}
```



## Subscribe a user


### Request

#### Endpoint

```plaintext
PUT /api/users/96/subscribe
Accept: application/json
Authorizat IO N: Bearer 38052f86ac03ea551eaacd24f1ba63d18fdeac0d80e70b5d
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
Authorization: Bearer 38052f86ac03ea551eaacd24f1ba63d18fdeac0d80e70b5d
ETag: W/&quot;a3f68bb575e967835b7365a062badfc7&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 76d6dbf5-844a-4271-9b5f-d5d49c2e8e53
X-Runtime: 0.046555
Vary: Origin
Content-Length: 187
200 OK
```


```json
{
  "id": 96,
  "email": "email96@example.com",
  "created_at": "2020-06-22T09:30:13.888-04:00",
  "updated_at": "2020-06-22T09:30:13.893-04:00",
  "subscribed": true,
  "bill_address": null,
  "ship_address": null
}
```



## Unsubscribe a user


### Request

#### Endpoint

```plaintext
PUT /api/users/95/unsubscribe
Accept: application/json
Authorizat IO N: Bearer d463da629dd5be371d0eb9014948b527935d3aac38a3b96d
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
Authorization: Bearer d463da629dd5be371d0eb9014948b527935d3aac38a3b96d
ETag: W/&quot;796ed8527f8e96c5f6841e345c89feeb&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: a9dacfb3-654b-4d33-9270-4b2f8097b338
X-Runtime: 0.077183
Vary: Origin
Content-Length: 188
200 OK
```


```json
{
  "id": 95,
  "email": "email95@example.com",
  "created_at": "2020-06-22T09:30:13.765-04:00",
  "updated_at": "2020-06-22T09:30:13.770-04:00",
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
GET /api/variants/145
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
ETag: W/&quot;e9a95595e5d91af94e016996c56f36fd&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: d0926c9b-bd7b-44da-a6bf-be81b78c2ee3
X-Runtime: 0.244841
Vary: Origin
Content-Length: 2020
200 OK
```


```json
{
  "id": 145,
  "name": "Product #78 - 7254",
  "sku": "SKU-144",
  "weight": "0.0",
  "height": null,
  "width": null,
  "depth": null,
  "is_master": false,
  "slug": "product-78-7254",
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
      "id": 67,
      "name": "Size-67",
      "presentation": "S",
      "option_type_name": "foo-size-67",
      "option_type_id": 67,
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
      "attachment_updated_at": "2020-06-22T09:29:57.334-04:00",
      "attachment_width": 489,
      "attachment_height": 490,
      "alt": null,
      "viewable_type": "Spree::Variant",
      "viewable_id": 145,
      "mini_url": "/spree/products/1/mini/thinking-cat.jpg?1592832597",
      "small_url": "/spree/products/1/small/thinking-cat.jpg?1592832597",
      "product_url": "/spree/products/1/product/thinking-cat.jpg?1592832597",
      "large_url": "/spree/products/1/large/thinking-cat.jpg?1592832597"
    }
  ],
  "variant_properties": [

  ],
  "stock_items": [

  ],
  "prices": [
    {
      "id": 106,
      "vendor_id": 249,
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
        "monogrammable": null
      }
    },
    {
      "id": 107,
      "vendor_id": 250,
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
Authorizat IO N: Bearer 0b4526290a7be41c2f47d9147682ae2267e0c88c98a6279c
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
ETag: W/&quot;c9b0d65fe37b55fa7d0aeebf0b857776&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: afcf8b13-e1db-4cf7-80f1-3ac19168e099
X-Runtime: 0.028606
Vary: Origin
Content-Length: 206
200 OK
```


```json
[
  {
    "id": 3,
    "user_id": 24,
    "payment_source_type": "SolidusPaypalBraintree::Source",
    "payment_source_id": 5,
    "default": false,
    "created_at": "2020-06-22T09:28:59.039-04:00",
    "updated_at": "2020-06-22T09:28:59.039-04:00"
  }
]
```



## Remove the payment from the user wallet


### Request

#### Endpoint

```plaintext
DELETE /api/wallet_payment_sources/2
Accept: application/json
Authorizat IO N: Bearer 8bc2ec4625659256fe3db7fdb0c94ecffc41f8005c7ddcf8
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
X-Request-Id: 9637f5ca-05d1-4830-8e78-550f6fe15605
X-Runtime: 0.041859
Vary: Origin
204 No Content
```




## Set a wallet payment source as the default user payment method


### Request

#### Endpoint

```plaintext
POST /api/wallet_payment_sources/1/default
Accept: application/json
Authorizat IO N: Bearer dd5062af74611c3a039142901c552244cccba781549833db
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
X-Request-Id: c1b261a8-cf56-4941-9d3a-bbfafbc699a8
X-Runtime: 0.070150
Vary: Origin
204 No Content
```




# Wished Products

Update a wished product. Users can update their own wished products, admins can update any.

## Create a wished product


### Request

#### Endpoint

```plaintext
POST /api/wished_products
Accept: application/json
Authorizat IO N: Bearer 83e3a71158fa34bbeb95682fc443fb1b5d40142eca3d99ac
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/wished_products`

#### Parameters


```json
wished_product[wishlist_id]=37&wished_product[variant_id]=89&wished_product[quantity]=2&wished_product[remark]=Foo+bar
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
ETag: W/&quot;dfd0246695c864692ab0e817d29d1744&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 7de6d78b-7668-486d-bbf1-589347fe0d00
X-Runtime: 0.035346
Vary: Origin
Content-Length: 119
201 Created
```


```json
{
  "id": 22,
  "wishlist_id": 37,
  "variant_id": 89,
  "quantity": 2,
  "remark": "Foo bar",
  "created_at": "2020-06-22T09:29:34.103-04:00"
}
```



## Delete a wished product


### Request

#### Endpoint

```plaintext
DELETE /api/wished_products/23
Accept: application/json
Authorizat IO N: Bearer fc3d8805c033eac58a39ee3852dcfd17e73ca989769cf110
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
X-Request-Id: 0a46d60c-ef49-454f-8f8f-a84c17d29a2d
X-Runtime: 0.030025
Vary: Origin
204 No Content
```




## Get a single wished product


### Request

#### Endpoint

```plaintext
GET /api/wished_products/19
Accept: application/json
Authorizat IO N: Bearer de7c0eb6a302148d49f5d4d4c4f3d0bd5d7b33fc3fdf5a22
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
ETag: W/&quot;b09fb5a7eaa525a4446a0527150963fe&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: a4c3fdf8-9359-4780-a2c0-2d528bf465b2
X-Runtime: 0.027037
Vary: Origin
Content-Length: 114
200 OK
```


```json
{
  "id": 19,
  "wishlist_id": 36,
  "variant_id": 83,
  "quantity": 1,
  "remark": null,
  "created_at": "2020-06-22T09:29:32.900-04:00"
}
```



## Get all wished products


### Request

#### Endpoint

```plaintext
GET /api/wished_products
Accept: application/json
Authorizat IO N: Bearer 24bbf5c0fadd62b9a6b126e4a23c5d74c74fc1b32461487c
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
ETag: W/&quot;1c13e3bd0eaa69f8ccbf88d1baaa55f1&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 57ff4bf5-c98e-4d46-a069-77d823019807
X-Runtime: 0.028297
Vary: Origin
Content-Length: 433
200 OK
```


```json
{
  "wished_products": [
    {
      "id": 15,
      "wishlist_id": 32,
      "variant_id": 75,
      "quantity": 1,
      "remark": null,
      "created_at": "2020-06-22T09:29:30.751-04:00"
    },
    {
      "id": 14,
      "wishlist_id": 31,
      "variant_id": 73,
      "quantity": 1,
      "remark": null,
      "created_at": "2020-06-22T09:29:30.333-04:00"
    },
    {
      "id": 13,
      "wishlist_id": 30,
      "variant_id": 71,
      "quantity": 1,
      "remark": null,
      "created_at": "2020-06-22T09:29:29.983-04:00"
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
Authorizat IO N: Bearer 837d0ca774ed8f5209fd726dc4f0135e23f29eee8bc9eef5
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
ETag: W/&quot;682e522ce9f4054afd1fb669cdf39ddf&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 9f92ba48-cd1e-4766-831f-fcb796d23484
X-Runtime: 0.273522
Vary: Origin
Content-Length: 2402
200 OK
```


```json
{
  "wished_products": [
    {
      "id": 18,
      "wishlist_id": 35,
      "variant_id": 81,
      "quantity": 1,
      "remark": null,
      "created_at": "2020-06-22T09:29:32.097-04:00",
      "variant": {
        "id": 81,
        "name": "Product #46 - 7865",
        "sku": "SKU-80",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-46-7865",
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
            "id": 35,
            "name": "Size-35",
            "presentation": "S",
            "option_type_name": "foo-size-35",
            "option_type_id": 35,
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
      "id": 17,
      "wishlist_id": 34,
      "variant_id": 79,
      "quantity": 1,
      "remark": null,
      "created_at": "2020-06-22T09:29:31.714-04:00",
      "variant": {
        "id": 79,
        "name": "Product #45 - 150",
        "sku": "SKU-78",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-45-150",
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
            "id": 34,
            "name": "Size-34",
            "presentation": "S",
            "option_type_name": "foo-size-34",
            "option_type_id": 34,
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
      "id": 16,
      "wishlist_id": 33,
      "variant_id": 77,
      "quantity": 1,
      "remark": null,
      "created_at": "2020-06-22T09:29:31.303-04:00",
      "variant": {
        "id": 77,
        "name": "Product #44 - 9252",
        "sku": "SKU-76",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-44-9252",
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
            "id": 33,
            "name": "Size-33",
            "presentation": "S",
            "option_type_name": "foo-size-33",
            "option_type_id": 33,
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
GET /api/wished_products/mine?with_variant=true
Accept: application/json
Authorizat IO N: Bearer 0b2f79b97b07d6c72e0888d4612c22e8816962bb59c59fe3
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
ETag: W/&quot;5552085c2bf3d75ecbc279790f7d02e8&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 33201427-ca48-48d3-8bf7-109a17842ba3
X-Runtime: 0.314549
Vary: Origin
Content-Length: 2349
200 OK
```


```json
{
  "wished_products": [
    {
      "id": 29,
      "wishlist_id": 40,
      "variant_id": 103,
      "quantity": 1,
      "remark": null,
      "created_at": "2020-06-22T09:29:36.913-04:00",
      "variant": {
        "id": 103,
        "name": "Product #57 - 3581",
        "sku": "SKU-102",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-57-3581",
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
      "variant_id": 105,
      "quantity": 1,
      "remark": null,
      "created_at": "2020-06-22T09:29:37.242-04:00",
      "variant": {
        "id": 105,
        "name": "Product #58 - 68",
        "sku": "SKU-104",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-58-68",
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
            "id": 47,
            "name": "Size-47",
            "presentation": "S",
            "option_type_name": "foo-size-47",
            "option_type_id": 47,
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
      "id": 31,
      "wishlist_id": 40,
      "variant_id": 107,
      "quantity": 1,
      "remark": null,
      "created_at": "2020-06-22T09:29:37.586-04:00",
      "variant": {
        "id": 107,
        "name": "Product #59 - 9814",
        "sku": "SKU-106",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-59-9814",
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
            "id": 48,
            "name": "Size-48",
            "presentation": "S",
            "option_type_name": "foo-size-48",
            "option_type_id": 48,
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
Authorizat IO N: Bearer 9b43742fbadebb2cb381cb56dd94a6fdfd1997db463e6f3a
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
ETag: W/&quot;f0d8f16e13e970b852b22b1f83d2a653&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 93159176-9909-4366-8593-28892ddbd97d
X-Runtime: 0.027289
Vary: Origin
Content-Length: 434
200 OK
```


```json
{
  "wished_products": [
    {
      "id": 26,
      "wishlist_id": 39,
      "variant_id": 97,
      "quantity": 1,
      "remark": null,
      "created_at": "2020-06-22T09:29:35.779-04:00"
    },
    {
      "id": 27,
      "wishlist_id": 39,
      "variant_id": 99,
      "quantity": 1,
      "remark": null,
      "created_at": "2020-06-22T09:29:36.088-04:00"
    },
    {
      "id": 28,
      "wishlist_id": 39,
      "variant_id": 101,
      "quantity": 1,
      "remark": null,
      "created_at": "2020-06-22T09:29:36.390-04:00"
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
PATCH /api/wished_products/10
Accept: application/json
Authorizat IO N: Bearer b859e81556bb98486100919ad53a5ae486bc36b40c8d9ab3
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/wished_products/:id`

#### Parameters


```json
wished_product[wishlist_id]=29&wished_product[variant_id]=69&wished_product[quantity]=2&wished_product[remark]=Foo+bar
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
ETag: W/&quot;580cdcc8f3a06ac4ac965d1c80fd7cfb&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 095486e2-623e-4fcc-8850-c9f2ff4bf7f3
X-Runtime: 0.117956
Vary: Origin
Content-Length: 119
200 OK
```


```json
{
  "id": 10,
  "wishlist_id": 29,
  "variant_id": 69,
  "quantity": 2,
  "remark": "Foo bar",
  "created_at": "2020-06-22T09:29:28.467-04:00"
}
```



# Wishlists

Get all wishlists, only accessible to admin users

## Create a wishlist


### Request

#### Endpoint

```plaintext
POST /api/wishlists
Accept: application/json
Authorizat IO N: Bearer 82b9f14497c01fef158ac0d20a2e47c68f7f032362a66aab
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/wishlists`

#### Parameters


```json
wishlist[name]&wishlist[user_id]=44&wishlist[is_default]=true&wishlist[is_public]=false
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
ETag: W/&quot;fac06c64057df3fc7ae5a67030063c2b&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 51d4ec3f-bb54-474e-8a01-0dc854321323
X-Runtime: 0.038120
Vary: Origin
Content-Length: 100
201 Created
```


```json
{
  "id": 25,
  "user_id": 44,
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
DELETE /api/wishlists/26
Accept: application/json
Authorizat IO N: Bearer 45e59b0b97be508cd90b5546c1869dd2c1fd311a87fea0e5
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
X-Request-Id: 0b7ffd80-7119-4d74-b790-978e864570af
X-Runtime: 0.030838
Vary: Origin
204 No Content
```




## Get a single wishlist


### Request

#### Endpoint

```plaintext
GET /api/wishlists/24
Accept: application/json
Authorizat IO N: Bearer 29f5666450e5e9ad66e5855e4bdd184ecdf62fcb49286cd7
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
ETag: W/&quot;d3e919102448c75dc89c80d63ac9cbaa&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 5276210c-14f1-458f-87f0-1d2ee40d1afb
X-Runtime: 0.036051
Vary: Origin
Content-Length: 442
200 OK
```


```json
{
  "id": 24,
  "user_id": 43,
  "name": "Wishlist #24",
  "is_public": false,
  "is_default": true,
  "wished_products": [
    {
      "id": 1,
      "wishlist_id": 24,
      "variant_id": 22,
      "quantity": 1,
      "remark": null,
      "created_at": "2020-06-22T09:29:07.951-04:00"
    },
    {
      "id": 2,
      "wishlist_id": 24,
      "variant_id": 24,
      "quantity": 1,
      "remark": null,
      "created_at": "2020-06-22T09:29:08.272-04:00"
    },
    {
      "id": 3,
      "wishlist_id": 24,
      "variant_id": 26,
      "quantity": 1,
      "remark": null,
      "created_at": "2020-06-22T09:29:08.605-04:00"
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
Authorizat IO N: Bearer 8293cbc15140b3c005722c814b084e4874c5895e2e8d8633
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
ETag: W/&quot;09cbc3a1f270fa86c860819af710e2dd&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 3bb4ba83-4cba-43a0-9a77-5da9051854a7
X-Runtime: 0.074498
Vary: Origin
Content-Length: 876
200 OK
```


```json
{
  "wishlists": [
    {
      "id": 1,
      "user_id": 30,
      "name": "Wishlist #1",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 2,
      "user_id": 31,
      "name": "Wishlist #2",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 3,
      "user_id": 32,
      "name": "Wishlist #3",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 4,
      "user_id": 33,
      "name": "Wishlist #4",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 5,
      "user_id": 34,
      "name": "Wishlist #5",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 6,
      "user_id": 35,
      "name": "Wishlist #6",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 7,
      "user_id": 36,
      "name": "Wishlist #7",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 8,
      "user_id": 37,
      "name": "Wishlist #8",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 9,
      "user_id": 38,
      "name": "Wishlist #9",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 10,
      "user_id": 39,
      "name": "Wishlist #10",
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
Authorizat IO N: Bearer b801561223419ea7f2a3fd9926dc8718863c7e27d26cf706
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
ETag: W/&quot;7d49dbdea5a1a0dfa089664b849b3182&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 878437a0-ba25-44ad-bf20-e01e4a457782
X-Runtime: 0.023893
Vary: Origin
Content-Length: 442
200 OK
```


```json
{
  "id": 28,
  "user_id": 47,
  "name": "Wishlist #26",
  "is_public": false,
  "is_default": true,
  "wished_products": [
    {
      "id": 7,
      "wishlist_id": 28,
      "variant_id": 34,
      "quantity": 1,
      "remark": null,
      "created_at": "2020-06-22T09:29:10.310-04:00"
    },
    {
      "id": 8,
      "wishlist_id": 28,
      "variant_id": 36,
      "quantity": 1,
      "remark": null,
      "created_at": "2020-06-22T09:29:10.647-04:00"
    },
    {
      "id": 9,
      "wishlist_id": 28,
      "variant_id": 38,
      "quantity": 1,
      "remark": null,
      "created_at": "2020-06-22T09:29:10.955-04:00"
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
Authorizat IO N: Bearer e894cef6595e996bda1e1225c5a9230b41f9fba4e466b7b0
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
ETag: W/&quot;bde9c0037284acd24b26f08333893aa7&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 6cd4285d-7e0f-400e-bbc3-7c6c305ff768
X-Runtime: 0.026998
Vary: Origin
Content-Length: 903
200 OK
```


```json
{
  "wishlists": [
    {
      "id": 14,
      "user_id": 42,
      "name": "Wishlist #14",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 15,
      "user_id": 42,
      "name": "Wishlist #15",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 16,
      "user_id": 42,
      "name": "Wishlist #16",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 17,
      "user_id": 42,
      "name": "Wishlist #17",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 18,
      "user_id": 42,
      "name": "Wishlist #18",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 19,
      "user_id": 42,
      "name": "Wishlist #19",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 20,
      "user_id": 42,
      "name": "Wishlist #20",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 21,
      "user_id": 42,
      "name": "Wishlist #21",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 22,
      "user_id": 42,
      "name": "Wishlist #22",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 23,
      "user_id": 42,
      "name": "Wishlist #23",
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
PATCH /api/wishlists/27
Accept: application/json
Authorizat IO N: Bearer 6aa2b07078de8ec2e24b3c57781f55eb43a77f5937b2ac03
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/wishlists/:id`

#### Parameters


```json
wishlist[name]=Another+Wishlist&wishlist[user_id]=46&wishlist[is_default]=true&wishlist[is_public]=false
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
ETag: W/&quot;842b7eb1a8364ddf0d934c1296bd4b51&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 8c25cf19-4658-4e9f-8817-d578ee1ff006
X-Runtime: 0.041137
Vary: Origin
Content-Length: 446
200 OK
```


```json
{
  "id": 27,
  "user_id": 46,
  "name": "Another Wishlist",
  "is_public": false,
  "is_default": true,
  "wished_products": [
    {
      "id": 4,
      "wishlist_id": 27,
      "variant_id": 28,
      "quantity": 1,
      "remark": null,
      "created_at": "2020-06-22T09:29:09.186-04:00"
    },
    {
      "id": 5,
      "wishlist_id": 27,
      "variant_id": 30,
      "quantity": 1,
      "remark": null,
      "created_at": "2020-06-22T09:29:09.526-04:00"
    },
    {
      "id": 6,
      "wishlist_id": 27,
      "variant_id": 32,
      "quantity": 1,
      "remark": null,
      "created_at": "2020-06-22T09:29:09.826-04:00"
    }
  ]
}
```



