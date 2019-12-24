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
PUT /api/orders/M359479489/addresses/43
Accept: application/json
X-Spree-Order-Token: ywBh1ys0wZO1WyUSvG78lA
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
ETag: W/&quot;c38c8cb4dbc317aadb86fbb436b76a03&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 5a8c764b-991c-44b4-a726-ef06ebea1fb5
X-Runtime: 0.043533
Vary: Origin
Content-Length: 507
200 OK
```


```json
{
  "id": 44,
  "firstname": "John the Tester",
  "lastname": null,
  "full_name": "John the Tester",
  "address1": "A Different Road",
  "address2": "Northwest",
  "city": "Herndon",
  "zipcode": "10039",
  "phone": "555-555-0199",
  "company": "Company",
  "alternative_phone": "555-555-0199",
  "country_id": 29,
  "country_iso": "US",
  "state_id": 29,
  "state_name": null,
  "state_text": "AL",
  "country": {
    "id": 29,
    "iso_name": "UNITED STATES",
    "iso": "US",
    "iso3": "USA",
    "name": "United States",
    "numcode": 840
  },
  "state": {
    "id": 29,
    "name": "Alabama",
    "abbr": "AL",
    "country_id": 29
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
X-Spree-Order-Token: Rei3q68ohmk3vmqsQfZSlw
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/braintree/transactions`

#### Parameters


```json
order_id=M028361052&payment_method_id=16&options[restart_checkout]=true&transaction[email]=maryellen.oga%40mckenziemcglynn.com&transaction[nonce]=fake-paypal-billing-agreement-nonce&transaction[phone]=555-555-0199&transaction[shipping_address_attributes][first_name]=John&transaction[shipping_address_attributes][last_name]=Stamm&transaction[shipping_address_attributes][address_line_1]=A+Different+Road&transaction[shipping_address_attributes][city]=Herndon&transaction[shipping_address_attributes][state_code]=AL&transaction[shipping_address_attributes][zip]=10036&transaction[shipping_address_attributes][country_code]=US&transaction[payment_type]=PayPalAccount&transaction[billing_address_attributes][first_name]=John&transaction[billing_address_attributes][last_name]=Stamm&transaction[billing_address_attributes][address_line_1]=A+Different+Road&transaction[billing_address_attributes][city]=Herndon&transaction[billing_address_attributes][state_code]=AL&transaction[billing_address_attributes][zip]=10036&transaction[billing_address_attributes][country_code]=US
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
ETag: W/&quot;b926913f034f79028a3685361a7f28d7&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: a2958351-5c9a-46ae-ab47-2a663ebce945
X-Runtime: 0.224317
Vary: Origin
Content-Length: 5376
200 OK
```


```json
{
  "id": 19,
  "number": "M028361052",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2019-12-24T05:50:58.340-05:00",
  "updated_at": "2019-12-24T05:50:58.549-05:00",
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
  "display_item_total": "$10.00",
  "total_quantity": 1,
  "display_total": "$110.00",
  "display_ship_total": "$100.00",
  "display_tax_total": "$0.00",
  "token": "Rei3q68ohmk3vmqsQfZSlw",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order&order=M028361052&bzip=10036&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [
    {
      "id": 16,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 40,
    "firstname": "John",
    "lastname": "Stamm",
    "full_name": "John Stamm",
    "address1": "A Different Road",
    "address2": null,
    "city": "Herndon",
    "zipcode": "10036",
    "phone": "555-555-0199",
    "company": null,
    "alternative_phone": null,
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
    "state": {
      "id": 28,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 28
    }
  },
  "ship_address": {
    "id": 41,
    "firstname": "John",
    "lastname": "Stamm",
    "full_name": "John Stamm",
    "address1": "A Different Road",
    "address2": null,
    "city": "Herndon",
    "zipcode": "10036",
    "phone": "555-555-0199",
    "company": null,
    "alternative_phone": null,
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
    "state": {
      "id": 28,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 28
    }
  },
  "line_items": [
    {
      "id": 20,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 63,
      "vendor_id": 150,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 63,
        "name": "Product #37 - 5824",
        "sku": "SKU-62",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-37-5824",
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
            "id": 26,
            "name": "Size-26",
            "presentation": "S",
            "option_type_name": "foo-size-26",
            "option_type_id": 26,
            "option_type_presentation": "Size",
            "position": 1
          }
        ],
        "images": [

        ],
        "product_id": 37,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [

      ],
      "vendor_name": "Vendor #150",
      "country_iso": "US",
      "adjustments": [

      ]
    }
  ],
  "payments": [
    {
      "id": 7,
      "source_type": "SolidusPaypalBraintree::Source",
      "source_id": 4,
      "amount": "110.0",
      "display_amount": "$110.00",
      "payment_method_id": 16,
      "state": "checkout",
      "avs_response": null,
      "created_at": "2019-12-24T05:50:58.434-05:00",
      "updated_at": "2019-12-24T05:50:58.434-05:00",
      "payment_method": {
        "id": 16,
        "name": "Braintree"
      },
      "source": {
        "id": 4,
        "payment_type": "PayPalAccount",
        "token": "bgx899",
        "created_at": "2019-12-24T05:50:58.433-05:00",
        "email": "jane.doe@paypal.com"
      }
    }
  ],
  "shipments": [
    {
      "id": 26,
      "tracking": null,
      "tracking_url": null,
      "number": "H51766360841",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M028361052",
      "stock_location_name": "NY Warehouse",
      "giftwrappable": false,
      "stock_location_id": 35,
      "giftwrap": null,
      "shipping_rates": [
        {
          "id": 26,
          "name": "UPS Ground",
          "admin_name": null,
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 20,
          "shipping_method_code": "UPS_GROUND",
          "extra_cost": "",
          "is_flat_rate": false,
          "is_flat_rate_expedited": false,
          "is_free_shipping": false,
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 26,
        "name": "UPS Ground",
        "admin_name": null,
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 20,
        "shipping_method_code": "UPS_GROUND",
        "extra_cost": "",
        "is_flat_rate": false,
        "is_flat_rate_expedited": false,
        "is_free_shipping": false,
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 20,
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
              "id": 28,
              "name": "ShippingCategory #27"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 63,
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
      "delivery_estimation": "Dec 26"
    }
  ],
  "adjustments": [

  ],
  "permissions": {
    "can_update": false
  },
  "credit_cards": [

  ],
  "gift_card_total": "0.0",
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
X-Spree-Order-Token: gNtdNU6C1CZdqHzZn2c15w
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/braintree/transactions`

#### Parameters


```json
order_id=M509940580&payment_method_id=15&options[restart_checkout]=true&transaction[email]=maryellen.oga%40mckenziemcglynn.com&transaction[nonce]=fake-apple-pay-visa-nonce&transaction[phone]=555-555-0199&transaction[shipping_address_attributes][first_name]=John&transaction[shipping_address_attributes][last_name]=Stamm&transaction[shipping_address_attributes][address_line_1]=A+Different+Road&transaction[shipping_address_attributes][city]=Herndon&transaction[shipping_address_attributes][state_code]=AL&transaction[shipping_address_attributes][zip]=10034&transaction[shipping_address_attributes][country_code]=US&transaction[payment_type]=ApplePayCard
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
ETag: W/&quot;e7bfcdb38f7909fdccc1ab795c6c8793&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 555a209b-d40e-4e55-bbed-a8da54eaba2a
X-Runtime: 0.257905
Vary: Origin
Content-Length: 5422
200 OK
```


```json
{
  "id": 18,
  "number": "M509940580",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2019-12-24T05:50:57.832-05:00",
  "updated_at": "2019-12-24T05:50:58.054-05:00",
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
  "display_item_total": "$10.00",
  "total_quantity": 1,
  "display_total": "$110.00",
  "display_ship_total": "$100.00",
  "display_tax_total": "$0.00",
  "token": "gNtdNU6C1CZdqHzZn2c15w",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order&order=M509940580&bzip=10034&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [
    {
      "id": 15,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 36,
    "firstname": "John",
    "lastname": "Stamm",
    "full_name": "John Stamm",
    "address1": "A Different Road",
    "address2": null,
    "city": "Herndon",
    "zipcode": "10034",
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
    "id": 37,
    "firstname": "John",
    "lastname": "Stamm",
    "full_name": "John Stamm",
    "address1": "A Different Road",
    "address2": null,
    "city": "Herndon",
    "zipcode": "10034",
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
      "id": 19,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 61,
      "vendor_id": 145,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 61,
        "name": "Product #36 - 6933",
        "sku": "SKU-60",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-36-6933",
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
        "product_id": 36,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [

      ],
      "vendor_name": "Vendor #145",
      "country_iso": "US",
      "adjustments": [

      ]
    }
  ],
  "payments": [
    {
      "id": 6,
      "source_type": "SolidusPaypalBraintree::Source",
      "source_id": 3,
      "amount": "110.0",
      "display_amount": "$110.00",
      "payment_method_id": 15,
      "state": "checkout",
      "avs_response": null,
      "created_at": "2019-12-24T05:50:57.933-05:00",
      "updated_at": "2019-12-24T05:50:57.933-05:00",
      "payment_method": {
        "id": 15,
        "name": "Braintree"
      },
      "source": {
        "id": 3,
        "payment_type": "ApplePayCard",
        "token": "cg7hsk",
        "created_at": "2019-12-24T05:50:57.933-05:00",
        "cc_type": "Apple Pay - Visa",
        "last_digits": "1881",
        "month": "12",
        "year": "2020"
      }
    }
  ],
  "shipments": [
    {
      "id": 24,
      "tracking": null,
      "tracking_url": null,
      "number": "H74377777113",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M509940580",
      "stock_location_name": "NY Warehouse",
      "giftwrappable": false,
      "stock_location_id": 34,
      "giftwrap": null,
      "shipping_rates": [
        {
          "id": 24,
          "name": "UPS Ground",
          "admin_name": null,
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 19,
          "shipping_method_code": "UPS_GROUND",
          "extra_cost": "",
          "is_flat_rate": false,
          "is_flat_rate_expedited": false,
          "is_free_shipping": false,
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 24,
        "name": "UPS Ground",
        "admin_name": null,
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 19,
        "shipping_method_code": "UPS_GROUND",
        "extra_cost": "",
        "is_flat_rate": false,
        "is_flat_rate_expedited": false,
        "is_free_shipping": false,
        "display_cost": "$100.00"
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
              "id": 27,
              "name": "ShippingCategory #26"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 61,
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
      "delivery_estimation": "Dec 26"
    }
  ],
  "adjustments": [

  ],
  "permissions": {
    "can_update": false
  },
  "credit_cards": [

  ],
  "gift_card_total": "0.0",
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
PUT /api/checkouts/M284273837/complete
Accept: application/json
X-Spree-Order-Token: LPN98SbPB-ZgtTfJbE5BfA
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
ETag: W/&quot;4ca09b038bde1a3a2f2a93153a69ecfe&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 28067121-3809-4bd2-9e5c-ba128f18e7a0
X-Runtime: 0.490116
Vary: Origin
Content-Length: 5500
200 OK
```


```json
{
  "id": 1,
  "number": "M284273837",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "complete",
  "adjustment_total": "0.0",
  "user_id": 1,
  "created_at": "2019-12-24T05:50:48.485-05:00",
  "updated_at": "2019-12-24T05:50:49.010-05:00",
  "completed_at": "2019-12-24T05:50:49.010-05:00",
  "payment_total": "110.0",
  "shipment_state": "ready",
  "payment_state": "paid",
  "email": "email1@example.com",
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
  "display_item_total": "$10.00",
  "total_quantity": 1,
  "display_total": "$110.00",
  "display_ship_total": "$100.00",
  "display_tax_total": "$0.00",
  "token": "LPN98SbPB-ZgtTfJbE5BfA",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order&order=M284273837&bzip=10001&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [
    {
      "id": 1,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    },
    {
      "id": 2,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 1,
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
    "id": 2,
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
      "id": 1,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 4,
      "vendor_id": 9,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 4,
        "name": "Product #2 - 5967",
        "sku": "SKU-3",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-2-5967",
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
      "vendor_name": "Vendor #9",
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
      "state": "completed",
      "avs_response": "M",
      "created_at": "2019-12-24T05:50:48.714-05:00",
      "updated_at": "2019-12-24T05:50:48.877-05:00",
      "payment_method": {
        "id": 1,
        "name": "Braintree"
      },
      "source": {
        "id": 1,
        "payment_type": "CreditCard",
        "token": "4rptfz",
        "created_at": "2019-12-24T05:50:48.713-05:00",
        "cc_type": "Visa",
        "last_digits": "1881",
        "month": "12",
        "year": "2020"
      }
    }
  ],
  "shipments": [
    {
      "id": 1,
      "tracking": "U10000",
      "tracking_url": null,
      "number": "H71672272363",
      "cost": "100.0",
      "shipped_at": null,
      "state": "ready",
      "order_id": "M284273837",
      "stock_location_name": "NY Warehouse",
      "giftwrappable": false,
      "stock_location_id": 2,
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
          "extra_cost": "",
          "is_flat_rate": false,
          "is_flat_rate_expedited": false,
          "is_free_shipping": false,
          "display_cost": "$100.00"
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
      "stock_location_address": "NY Warehouse, Washington, AL",
      "country_iso": "US",
      "international_shipping": false,
      "delivery_estimation": "Dec 26"
    }
  ],
  "adjustments": [

  ],
  "permissions": {
    "can_update": false
  },
  "credit_cards": [

  ],
  "gift_card_total": "0.0",
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
PATCH /api/checkouts/M607933885
Accept: application/json
X-Spree-Order-Token: yb5YoGxPxoVm9tyt0RFjIQ
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=5&order[payment_attributes][][source_attributes][nonce]=fake-apple-pay-visa-nonce&order[payment_attributes][][source_attributes][payment_type]=ApplePayCard&order[payment_attributes][][source_attributes][reusable]=true
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
ETag: W/&quot;4bd703ff5492f691090e1ebcd5a7d4b2&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 266e0913-a7b9-4b2d-9bd6-119fed8dd2eb
X-Runtime: 0.127206
Vary: Origin
Content-Length: 4893
200 OK
```


```json
{
  "id": 5,
  "number": "M607933885",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 5,
  "created_at": "2019-12-24T05:50:50.809-05:00",
  "updated_at": "2019-12-24T05:50:51.010-05:00",
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
  "gift_email": null,
  "gift_message": null,
  "is_gift": false,
  "display_item_total": "$10.00",
  "total_quantity": 1,
  "display_total": "$110.00",
  "display_ship_total": "$100.00",
  "display_tax_total": "$0.00",
  "token": "yb5YoGxPxoVm9tyt0RFjIQ",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order&order=M607933885&bzip=10008&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [
    {
      "id": 5,
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
      "id": 5,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 12,
      "vendor_id": 29,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 12,
        "name": "Product #6 - 6088",
        "sku": "SKU-11",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-6-6088",
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
            "id": 6,
            "name": "Size-6",
            "presentation": "S",
            "option_type_name": "foo-size-6",
            "option_type_id": 6,
            "option_type_presentation": "Size",
            "position": 1
          }
        ],
        "images": [

        ],
        "product_id": 6,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [

      ],
      "vendor_name": "Vendor #29",
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
      "number": "H76251831121",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M607933885",
      "stock_location_name": "NY Warehouse",
      "giftwrappable": false,
      "stock_location_id": 6,
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
          "extra_cost": "",
          "is_flat_rate": false,
          "is_flat_rate_expedited": false,
          "is_free_shipping": false,
          "display_cost": "$100.00"
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
        "extra_cost": "",
        "is_flat_rate": false,
        "is_flat_rate_expedited": false,
        "is_free_shipping": false,
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
              "id": 6,
              "name": "ShippingCategory #6"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 12,
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
      "delivery_estimation": "Dec 26"
    }
  ],
  "adjustments": [

  ],
  "permissions": {
    "can_update": false
  },
  "credit_cards": [

  ],
  "gift_card_total": "0.0",
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
PATCH /api/checkouts/M691387372
Accept: application/json
X-Spree-Order-Token: u63hXSgssRUL4xQZmKce7A
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=3&order[payment_attributes][][source_attributes][nonce]=fake-paypal-billing-agreement-nonce&order[payment_attributes][][source_attributes][payment_type]=PayPalAccount&order[payment_attributes][][source_attributes][reusable]=true
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
ETag: W/&quot;478f9408564d457682a2a84adeadb439&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 6e479d49-bfe4-4a04-8f2f-9f48bd915e21
X-Runtime: 0.118922
Vary: Origin
Content-Length: 4889
200 OK
```


```json
{
  "id": 3,
  "number": "M691387372",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 3,
  "created_at": "2019-12-24T05:50:49.780-05:00",
  "updated_at": "2019-12-24T05:50:50.028-05:00",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
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
  "order_total_after_store_credit": "110.0",
  "display_order_total_after_store_credit": "$110.00",
  "total_applicable_store_credit": "0.0",
  "display_total_available_store_credit": "$0.00",
  "display_store_credit_remaining_after_capture": "$0.00",
  "canceler_id": null,
  "gift_email": null,
  "gift_message": null,
  "is_gift": false,
  "display_item_total": "$10.00",
  "total_quantity": 1,
  "display_total": "$110.00",
  "display_ship_total": "$100.00",
  "display_tax_total": "$0.00",
  "token": "u63hXSgssRUL4xQZmKce7A",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order&order=M691387372&bzip=10004&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [
    {
      "id": 3,
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
      "id": 3,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 8,
      "vendor_id": 19,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 8,
        "name": "Product #4 - 5684",
        "sku": "SKU-7",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-4-5684",
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
            "id": 4,
            "name": "Size-4",
            "presentation": "S",
            "option_type_name": "foo-size-4",
            "option_type_id": 4,
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

      ],
      "vendor_name": "Vendor #19",
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
      "number": "H41463152584",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M691387372",
      "stock_location_name": "NY Warehouse",
      "giftwrappable": false,
      "stock_location_id": 4,
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
          "extra_cost": "",
          "is_flat_rate": false,
          "is_flat_rate_expedited": false,
          "is_free_shipping": false,
          "display_cost": "$100.00"
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
        "extra_cost": "",
        "is_flat_rate": false,
        "is_flat_rate_expedited": false,
        "is_free_shipping": false,
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
              "id": 4,
              "name": "ShippingCategory #4"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 8,
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
      "delivery_estimation": "Dec 26"
    }
  ],
  "adjustments": [

  ],
  "permissions": {
    "can_update": false
  },
  "credit_cards": [

  ],
  "gift_card_total": "0.0",
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
PATCH /api/checkouts/M956606698
Accept: application/json
X-Spree-Order-Token: aO_-LI37HK8GbA2Y64TvWg
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=4&order[payment_attributes][][source_attributes][nonce]=fake-valid-visa-nonce&order[payment_attributes][][source_attributes][payment_type]=CreditCard&order[payment_attributes][][source_attributes][reusable]=true
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
ETag: W/&quot;382a6458d31c39e97349b46c36fbb256&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: b954e052-8e4e-433c-9c71-1fe31b8077d3
X-Runtime: 0.115642
Vary: Origin
Content-Length: 4892
200 OK
```


```json
{
  "id": 4,
  "number": "M956606698",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 4,
  "created_at": "2019-12-24T05:50:50.332-05:00",
  "updated_at": "2019-12-24T05:50:50.534-05:00",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
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
  "gift_email": null,
  "gift_message": null,
  "is_gift": false,
  "display_item_total": "$10.00",
  "total_quantity": 1,
  "display_total": "$110.00",
  "display_ship_total": "$100.00",
  "display_tax_total": "$0.00",
  "token": "aO_-LI37HK8GbA2Y64TvWg",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order&order=M956606698&bzip=10006&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [
    {
      "id": 4,
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
      "id": 4,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 10,
      "vendor_id": 24,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 10,
        "name": "Product #5 - 5312",
        "sku": "SKU-9",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-5-5312",
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
        "product_id": 5,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [

      ],
      "vendor_name": "Vendor #24",
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
      "number": "H60684551176",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M956606698",
      "stock_location_name": "NY Warehouse",
      "giftwrappable": false,
      "stock_location_id": 5,
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
          "extra_cost": "",
          "is_flat_rate": false,
          "is_flat_rate_expedited": false,
          "is_free_shipping": false,
          "display_cost": "$100.00"
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
        "extra_cost": "",
        "is_flat_rate": false,
        "is_flat_rate_expedited": false,
        "is_free_shipping": false,
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
              "id": 5,
              "name": "ShippingCategory #5"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 10,
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
      "delivery_estimation": "Dec 26"
    }
  ],
  "adjustments": [

  ],
  "permissions": {
    "can_update": false
  },
  "credit_cards": [

  ],
  "gift_card_total": "0.0",
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
PATCH /api/checkouts/M341124720
Accept: application/json
X-Spree-Order-Token: SNOKapTRikRsb-R2cR57Vw
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=6&order[payment_attributes][][source_attributes][wallet_payment_source_id]=2
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
ETag: W/&quot;cda77d9402ff771b21356cf2e19bff16&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: ceaa8927-6768-4def-9d3d-8ee6b4fcf151
X-Runtime: 0.119787
Vary: Origin
Content-Length: 4898
200 OK
```


```json
{
  "id": 6,
  "number": "M341124720",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 6,
  "created_at": "2019-12-24T05:50:51.292-05:00",
  "updated_at": "2019-12-24T05:50:51.502-05:00",
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
  "gift_email": null,
  "gift_message": null,
  "is_gift": false,
  "display_item_total": "$10.00",
  "total_quantity": 1,
  "display_total": "$110.00",
  "display_ship_total": "$100.00",
  "display_tax_total": "$0.00",
  "token": "SNOKapTRikRsb-R2cR57Vw",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order&order=M341124720&bzip=10010&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [
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
      "id": 6,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 14,
      "vendor_id": 34,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 14,
        "name": "Product #7 - 1525",
        "sku": "SKU-13",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-7-1525",
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
      "vendor_name": "Vendor #34",
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
      "number": "H17028500352",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M341124720",
      "stock_location_name": "NY Warehouse",
      "giftwrappable": false,
      "stock_location_id": 7,
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
          "extra_cost": "",
          "is_flat_rate": false,
          "is_flat_rate_expedited": false,
          "is_free_shipping": false,
          "display_cost": "$100.00"
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
        "extra_cost": "",
        "is_flat_rate": false,
        "is_flat_rate_expedited": false,
        "is_free_shipping": false,
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
              "id": 7,
              "name": "ShippingCategory #7"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 14,
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
      "delivery_estimation": "Dec 26"
    }
  ],
  "adjustments": [

  ],
  "permissions": {
    "can_update": false
  },
  "credit_cards": [

  ],
  "gift_card_total": "0.0",
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
PUT /api/checkouts/M120296621
Accept: application/json
X-Spree-Order-Token: EFhVZG9X8bmSuB3tCBcVdw
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PUT /api/checkouts/:id`

#### Parameters


```json
order[ship_address_attributes][id]&order[ship_address_attributes][firstname]=John&order[ship_address_attributes][lastname]&order[ship_address_attributes][address1]=10+Lovely+Street&order[ship_address_attributes][address2]=Northwest&order[ship_address_attributes][city]=Herndon&order[ship_address_attributes][zipcode]=10003&order[ship_address_attributes][phone]=555-555-0199&order[ship_address_attributes][state_name]&order[ship_address_attributes][alternative_phone]=555-555-0199&order[ship_address_attributes][company]=Company&order[ship_address_attributes][state_id]=3&order[ship_address_attributes][country_id]=3&order[ship_address_attributes][created_at]&order[ship_address_attributes][updated_at]&order[use_billing]=true&hold_state=true
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
ETag: W/&quot;bef188389ba61695031d21f6bc8c9a80&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: f8e78e81-937b-4732-97ae-1b73792138c3
X-Runtime: 0.115345
Vary: Origin
Content-Length: 4797
200 OK
```


```json
{
  "id": 2,
  "number": "M120296621",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "cart",
  "adjustment_total": "0.0",
  "user_id": 2,
  "created_at": "2019-12-24T05:50:49.430-05:00",
  "updated_at": "2019-12-24T05:50:49.500-05:00",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "email2@example.com",
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
  "display_item_total": "$10.00",
  "total_quantity": 1,
  "display_total": "$110.00",
  "display_ship_total": "$100.00",
  "display_tax_total": "$0.00",
  "token": "EFhVZG9X8bmSuB3tCBcVdw",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order&order=M120296621&bzip=10003&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [

  ],
  "bill_address": {
    "id": 3,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "10 Lovely Street",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10003",
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
  },
  "ship_address": {
    "id": 3,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "10 Lovely Street",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10003",
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
  },
  "line_items": [
    {
      "id": 2,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 6,
      "vendor_id": 14,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 6,
        "name": "Product #3 - 3948",
        "sku": "SKU-5",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-3-3948",
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
            "id": 3,
            "name": "Size-3",
            "presentation": "S",
            "option_type_name": "foo-size-3",
            "option_type_id": 3,
            "option_type_presentation": "Size",
            "position": 1
          }
        ],
        "images": [

        ],
        "product_id": 3,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [

      ],
      "vendor_name": "Vendor #14",
      "country_iso": "US",
      "adjustments": [

      ]
    }
  ],
  "payments": [

  ],
  "shipments": [
    {
      "id": 2,
      "tracking": "U10000",
      "tracking_url": null,
      "number": "H55455585447",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M120296621",
      "stock_location_name": "NY Warehouse",
      "giftwrappable": false,
      "stock_location_id": 3,
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
          "extra_cost": "",
          "is_flat_rate": false,
          "is_flat_rate_expedited": false,
          "is_free_shipping": false,
          "display_cost": "$100.00"
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
              "id": 3,
              "name": "ShippingCategory #3"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 6,
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
      "delivery_estimation": "Dec 26"
    }
  ],
  "adjustments": [

  ],
  "permissions": {
    "can_update": false
  },
  "credit_cards": [

  ],
  "gift_card_total": "0.0",
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



# Giftwrap

Create giftwrap related to shipment

## Create Giftwrap


### Request

#### Endpoint

```plaintext
POST /api/shipments/H72266158222/giftwrap
Accept: application/json
X-Spree-Order-Token: QeZNGns9t2pflX1MaK5hlw
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/shipments/:shipment_number/giftwrap`

#### Parameters


```json
order_number=M971113628
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
X-Request-Id: 790911aa-1271-4f1a-a0eb-b7f16e561d7e
X-Runtime: 0.050760
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
DELETE /api/shipments/H48568433857/giftwrap
Accept: application/json
X-Spree-Order-Token: 1QqbKMge4DtvLSwu3LBkBA
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`DELETE /api/shipments/:shipment_number/giftwrap`

#### Parameters


```json
order_number=M413852652
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
X-Request-Id: 74c783fd-ac4e-4d8b-8baa-cb092fe2334b
X-Runtime: 0.008986
Vary: Origin
204 No Content
```




# LineItem

Representation of a single cart item for a specific variant with price of vendor

## Creating a line item


### Request

#### Endpoint

```plaintext
POST /api/orders/M508565063/line_items
Accept: application/json
X-Spree-Order-Token: 3hsuiM2YsUXkMPcrLWnzhQ
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/:order_number/line_items`

#### Parameters


```json
line_item[variant_id]=49&line_item[options][vendor_id]=119
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
ETag: W/&quot;6d3099c08a69cf2f5e6359e70c87644e&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 836a40e1-9123-4bcf-aaed-bea6d5403f35
X-Runtime: 0.103340
Vary: Origin
Content-Length: 937
201 Created
```


```json
{
  "id": 14,
  "quantity": 1,
  "price": "19.99",
  "variant_id": 49,
  "vendor_id": 119,
  "single_display_amount": "$19.99",
  "display_amount": "$19.99",
  "total": "19.99",
  "on_sale": false,
  "final_sale": false,
  "backordered": null,
  "promotionable": true,
  "variant": {
    "id": 49,
    "name": "Product #30 - 810",
    "sku": "SKU-48",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": false,
    "slug": "product-30-810",
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
    "product_id": 30,
    "lead_time": 2,
    "brand": null,
    "brand_slug": null,
    "brand_description": null
  },
  "monogram": null,
  "gift_cards": [

  ],
  "vendor_name": "Vendor #119",
  "country_iso": null,
  "adjustments": [

  ]
}
```



## Creating a line item gift card


### Request

#### Endpoint

```plaintext
POST /api/orders/M963919286/line_items
Accept: application/json
X-Spree-Order-Token: qqrZu9MejXF2MyyUHLktgQ
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/:order_number/line_items`

#### Parameters


```json
line_item[variant_id]=57&line_item[options][vendor_id]=137&line_item[options][gift_card_details][recipient_name]=Recipient+John&line_item[options][gift_card_details][recipient_email]=recipient%40email.com&line_item[options][gift_card_details][purchaser_name]=Purchaser+Bob&line_item[options][gift_card_details][gift_message]=Surprise&line_item[options][gift_card_details][send_email_at]=2019-12-24+05%3A50%3A57+-0500
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
ETag: W/&quot;2e7d49a1a507a9e3ca23a74f4e629b1b&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: bfb8f15c-2d2a-498e-835b-56b759b2ae17
X-Runtime: 0.156792
Vary: Origin
Content-Length: 1075
201 Created
```


```json
{
  "id": 17,
  "quantity": 1,
  "price": "19.99",
  "variant_id": 57,
  "vendor_id": 137,
  "single_display_amount": "$19.99",
  "display_amount": "$19.99",
  "total": "19.99",
  "on_sale": false,
  "final_sale": false,
  "backordered": null,
  "promotionable": true,
  "variant": {
    "id": 57,
    "name": "Product #33 - 2897",
    "sku": "SKU-57",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": false,
    "slug": "product-33-2897",
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
    "product_id": 33,
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
      "send_email_at": "2019-12-24T00:00:00.000-05:00"
    }
  ],
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
DELETE /api/orders/M318801279/line_items/15
Accept: application/json
X-Spree-Order-Token: VvTeQadTjOxGYXWdTEclIw
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
X-Request-Id: eff95ebe-89c4-46d0-b6e0-60797528061b
X-Runtime: 0.061364
Vary: Origin
204 No Content
```




## Updating a line item


### Request

#### Endpoint

```plaintext
PUT /api/orders/M736630468/line_items/18
Accept: application/json
X-Spree-Order-Token: X7djnBp82_MGxgyFy1GJsQ
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
ETag: W/&quot;7ca495fd2087e27c9b02181b0e5622ef&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: bcadc694-492d-41c5-a339-8c80de3e608d
X-Runtime: 0.088753
Vary: Origin
Content-Length: 936
200 OK
```


```json
{
  "id": 18,
  "quantity": 2,
  "price": "10.0",
  "variant_id": 59,
  "vendor_id": 140,
  "single_display_amount": "$10.00",
  "display_amount": "$20.00",
  "total": "20.0",
  "on_sale": false,
  "final_sale": false,
  "backordered": null,
  "promotionable": true,
  "variant": {
    "id": 59,
    "name": "Product #35 - 1349",
    "sku": "SKU-58",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": false,
    "slug": "product-35-1349",
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
    "product_id": 35,
    "lead_time": 2,
    "brand": null,
    "brand_slug": null,
    "brand_description": null
  },
  "monogram": null,
  "gift_cards": [

  ],
  "vendor_name": "Vendor #140",
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
Authorizat IO N: Bearer 414be87f57b6df717c993bc92ad278658bb2621f72f05614
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/minis`

#### Parameters


```json
mini[name]=Winny&mini[user_id]=27&mini[birth_year]=2019&mini[birth_month]=1&mini[birth_day]=1
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
ETag: W/&quot;8ae58d6d7ad90f45d06a857a5fc30b1c&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: bac17e0d-9766-413b-9851-82018d255c31
X-Runtime: 0.009179
Vary: Origin
Content-Length: 163
201 Created
```


```json
{
  "id": 18,
  "user_id": 27,
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
Authorizat IO N: Bearer 8a9a990a1496c4ca165b4f7c5f3acf98360e410d6afd1d6f
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
X-Request-Id: fca13ccf-181f-4ef6-939b-ac66273eee5c
X-Runtime: 0.005448
Vary: Origin
204 No Content
```




## Get a single mini


### Request

#### Endpoint

```plaintext
GET /api/minis/17
Accept: application/json
Authorizat IO N: Bearer d5f865cfc62e19c264f87409c0c29b3fb69719548cf07d98
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
ETag: W/&quot;10b17f9c00166d479174565bd918ea8c&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 59c8a939-7c01-4998-bfe8-771379d704c8
X-Runtime: 0.008710
Vary: Origin
Content-Length: 168
200 OK
```


```json
{
  "id": 17,
  "user_id": 26,
  "name": "Mini",
  "birth_year": 2018,
  "birth_month": null,
  "birth_day": null,
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
Authorizat IO N: Bearer 3b0d612d717f74fe1c8822dd6ca1810e09f31ab3df4ff1f5
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
ETag: W/&quot;46f0aec2c35a6b2009d644dc5115268c&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: bcec6bfd-11a0-4667-91bb-a76802b2f5e3
X-Runtime: 0.062119
Vary: Origin
Content-Length: 1761
200 OK
```


```json
{
  "minis": [
    {
      "id": 10,
      "user_id": 21,
      "name": "Mini",
      "birth_year": 2018,
      "birth_month": null,
      "birth_day": null,
      "gender_boy": true,
      "gender_girl": true,
      "gender_taxons": [

      ],
      "age_range_taxons": [

      ]
    },
    {
      "id": 9,
      "user_id": 20,
      "name": "Mini",
      "birth_year": 2018,
      "birth_month": null,
      "birth_day": null,
      "gender_boy": true,
      "gender_girl": true,
      "gender_taxons": [

      ],
      "age_range_taxons": [

      ]
    },
    {
      "id": 8,
      "user_id": 19,
      "name": "Mini",
      "birth_year": 2018,
      "birth_month": null,
      "birth_day": null,
      "gender_boy": true,
      "gender_girl": true,
      "gender_taxons": [

      ],
      "age_range_taxons": [

      ]
    },
    {
      "id": 7,
      "user_id": 18,
      "name": "Mini",
      "birth_year": 2018,
      "birth_month": null,
      "birth_day": null,
      "gender_boy": true,
      "gender_girl": true,
      "gender_taxons": [

      ],
      "age_range_taxons": [

      ]
    },
    {
      "id": 6,
      "user_id": 17,
      "name": "Mini",
      "birth_year": 2018,
      "birth_month": null,
      "birth_day": null,
      "gender_boy": true,
      "gender_girl": true,
      "gender_taxons": [

      ],
      "age_range_taxons": [

      ]
    },
    {
      "id": 5,
      "user_id": 16,
      "name": "Mini",
      "birth_year": 2018,
      "birth_month": null,
      "birth_day": null,
      "gender_boy": true,
      "gender_girl": true,
      "gender_taxons": [

      ],
      "age_range_taxons": [

      ]
    },
    {
      "id": 4,
      "user_id": 15,
      "name": "Mini",
      "birth_year": 2018,
      "birth_month": null,
      "birth_day": null,
      "gender_boy": true,
      "gender_girl": true,
      "gender_taxons": [

      ],
      "age_range_taxons": [

      ]
    },
    {
      "id": 3,
      "user_id": 14,
      "name": "Mini",
      "birth_year": 2018,
      "birth_month": null,
      "birth_day": null,
      "gender_boy": true,
      "gender_girl": true,
      "gender_taxons": [

      ],
      "age_range_taxons": [

      ]
    },
    {
      "id": 2,
      "user_id": 13,
      "name": "Mini",
      "birth_year": 2018,
      "birth_month": null,
      "birth_day": null,
      "gender_boy": true,
      "gender_girl": true,
      "gender_taxons": [

      ],
      "age_range_taxons": [

      ]
    },
    {
      "id": 1,
      "user_id": 12,
      "name": "Mini",
      "birth_year": 2018,
      "birth_month": null,
      "birth_day": null,
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
Authorizat IO N: Bearer b63490f0a2783faebefab42c21bd10053499e402b974cbea
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
ETag: W/&quot;f80d0e3a7750ac1ee75f7bd9a262ea7e&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 30d6817d-ad44-4567-a00c-3c7f236b2c97
X-Runtime: 0.011999
Vary: Origin
Content-Length: 416
200 OK
```


```json
{
  "minis": [
    {
      "id": 16,
      "user_id": 25,
      "name": "Mini",
      "birth_year": 2018,
      "birth_month": null,
      "birth_day": null,
      "gender_boy": true,
      "gender_girl": true,
      "gender_taxons": [

      ],
      "age_range_taxons": [

      ]
    },
    {
      "id": 15,
      "user_id": 25,
      "name": "Mini",
      "birth_year": 2018,
      "birth_month": null,
      "birth_day": null,
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
PATCH /api/minis/11
Accept: application/json
Authorizat IO N: Bearer c7b29af456863d8bd0317a0ba1fcdf428c855a8ae4e0a1be
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
ETag: W/&quot;8abd4fdad2918f2dace83ebb397fe492&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 798cc063-2b1f-4adc-a4e1-bd461127c879
X-Runtime: 0.010715
Vary: Origin
Content-Length: 169
200 OK
```


```json
{
  "id": 11,
  "user_id": 23,
  "name": "Marge",
  "birth_year": 2018,
  "birth_month": null,
  "birth_day": null,
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
user_id&order_token&line_item[variant_id]=75&line_item[quantity]=1&line_item[vendor_id]=173&line_item[gift_card_details_attributes][recipient_name]=Recipient+John&line_item[gift_card_details_attributes][recipient_email]=recipient%40email.com&line_item[gift_card_details_attributes][purchaser_name]=Purchaser+Bob&line_item[gift_card_details_attributes][gift_message]=Surprise&line_item[gift_card_details_attributes][send_email_at]=2019-12-24
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
ETag: W/&quot;423cf42b21b5f340dc95aa7da709bc81&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 5fef94d2-e55a-40c2-a663-1f9a80d0daa2
X-Runtime: 0.102875
Vary: Origin
Content-Length: 2817
200 OK
```


```json
{
  "id": 23,
  "number": "M957568344",
  "item_total": "19.99",
  "total": "19.99",
  "ship_total": "0.0",
  "state": "cart",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2019-12-24T05:51:00.516-05:00",
  "updated_at": "2019-12-24T05:51:00.547-05:00",
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
  "display_item_total": "$19.99",
  "total_quantity": 1,
  "display_total": "$19.99",
  "display_ship_total": "$0.00",
  "display_tax_total": "$0.00",
  "token": "JxEFKVB52nbRlZY8h_Os8g",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order&order=M957568344&bzip=&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [

  ],
  "bill_address": null,
  "ship_address": null,
  "line_items": [
    {
      "id": 24,
      "quantity": 1,
      "price": "19.99",
      "variant_id": 75,
      "vendor_id": 173,
      "single_display_amount": "$19.99",
      "display_amount": "$19.99",
      "total": "19.99",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 75,
        "name": "Product #42 - 2592",
        "sku": "SKU-75",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-42-2592",
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
        "product_id": 42,
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
          "send_email_at": "2019-12-24T00:00:00.000-05:00"
        }
      ],
      "vendor_name": "Vendor #173",
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
  "gift_card_total": "0.0",
  "subtotals": {
    "order_total": "19.99",
    "item_total": "19.99",
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
user_id&order_token&line_item[variant_id]=67&line_item[quantity]=2&line_item[vendor_id]=154
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
ETag: W/&quot;7bedfa82f9f08bdfff2c39d557954c91&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 2dff61d4-d8d7-4dc3-aeab-811972e08e76
X-Runtime: 0.097257
Vary: Origin
Content-Length: 2635
200 OK
```


```json
{
  "id": 21,
  "number": "M100070484",
  "item_total": "39.98",
  "total": "39.98",
  "ship_total": "0.0",
  "state": "cart",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2019-12-24T05:50:59.729-05:00",
  "updated_at": "2019-12-24T05:50:59.763-05:00",
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
  "display_item_total": "$39.98",
  "total_quantity": 2,
  "display_total": "$39.98",
  "display_ship_total": "$0.00",
  "display_tax_total": "$0.00",
  "token": "J1pOAcPgMKFXcrfw3Pq3jw",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order&order=M100070484&bzip=&init=true",
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
      "variant_id": 67,
      "vendor_id": 154,
      "single_display_amount": "$19.99",
      "display_amount": "$39.98",
      "total": "39.98",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 67,
        "name": "Product #39 - 6840",
        "sku": "SKU-66",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-39-6840",
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
        "product_id": 39,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [

      ],
      "vendor_name": "Vendor #154",
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
  "gift_card_total": "0.0",
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
Authorizat IO N: Bearer f685191a47dc9a01712f2c6b8216b5a072a9fa7f7eb0a7bb
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
ETag: W/&quot;5cb9aa0b77ffade1773229cfd815ca3a&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 53744c36-3510-4548-ad1f-ae78ea139200
X-Runtime: 0.017318
Vary: Origin
Content-Length: 310
200 OK
```


```json
{
  "orders": [
    {
      "number": "M175886444",
      "completed_at": "2019-12-24T05:51:00.189-05:00",
      "total": "120.0",
      "state": "Complete",
      "shipment_state": "shipped",
      "shipments": [
        {
          "number": "H15114200225",
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
GET /api/orders/M864431969
Accept: application/json
Authorizat IO N: Bearer 0a1ac94302882b1d5ceabb5e94e08757b5482fd2db6adb55
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
ETag: W/&quot;6a528b9b324c0bc52064212ff9e49d71&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 697c17db-64fc-4327-8b54-2ea5473c91a5
X-Runtime: 0.162421
Vary: Origin
Content-Length: 10075
200 OK
```


```json
{
  "id": 24,
  "number": "M864431969",
  "item_total": "20.0",
  "total": "120.0",
  "ship_total": "100.0",
  "state": "complete",
  "adjustment_total": "0.0",
  "user_id": 46,
  "created_at": "2019-12-24T05:51:00.957-05:00",
  "updated_at": "2019-12-24T05:51:01.175-05:00",
  "completed_at": "2019-12-24T05:51:01.023-05:00",
  "payment_total": "120.0",
  "shipment_state": "shipped",
  "payment_state": "paid",
  "email": "email46@example.com",
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
  "gift_email": null,
  "gift_message": null,
  "is_gift": false,
  "display_item_total": "$20.00",
  "total_quantity": 2,
  "display_total": "$120.00",
  "display_ship_total": "$100.00",
  "display_tax_total": "$0.00",
  "token": "cBXLYeg1PVR-wLNdT_ff9A",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order&order=M864431969&bzip=10042&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [
    {
      "id": 19,
      "name": "Credit Card",
      "partial_name": "gateway",
      "method_type": "gateway"
    },
    {
      "id": 20,
      "name": "Credit Card",
      "partial_name": "gateway",
      "method_type": "gateway"
    }
  ],
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
    "country_id": 33,
    "country_iso": "US",
    "state_id": 33,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 33,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 33,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 33
    }
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
    "country_id": 33,
    "country_iso": "US",
    "state_id": 33,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 33,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 33,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 33
    }
  },
  "line_items": [
    {
      "id": 25,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 77,
      "vendor_id": 179,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 77,
        "name": "Product #44 - 4797",
        "sku": "SKU-76",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-44-4797",
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
        "product_id": 44,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [

      ],
      "vendor_name": "Vendor #179",
      "country_iso": "US",
      "adjustments": [
        {
          "id": 8,
          "source_type": "Spree::TaxRate",
          "source_id": 1,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 25,
          "amount": "2.0",
          "label": "VAT 5%",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-12-24T05:51:01.151-05:00",
          "updated_at": "2019-12-24T05:51:01.160-05:00",
          "display_amount": "$2.00"
        },
        {
          "id": 2,
          "source_type": "Spree::PromotionAction",
          "source_id": 3,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 25,
          "amount": "5.0",
          "label": "foo",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-12-24T05:51:01.091-05:00",
          "updated_at": "2019-12-24T05:51:01.091-05:00",
          "display_amount": "$5.00"
        },
        {
          "id": 1,
          "source_type": "Spree::PromotionAction",
          "source_id": 3,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 25,
          "amount": "5.0",
          "label": "foo",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-12-24T05:51:01.084-05:00",
          "updated_at": "2019-12-24T05:51:01.084-05:00",
          "display_amount": "$5.00"
        }
      ]
    },
    {
      "id": 26,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 79,
      "vendor_id": 179,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 79,
        "name": "Product #45 - 1029",
        "sku": "SKU-78",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-45-1029",
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
        "product_id": 45,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [

      ],
      "vendor_name": "Vendor #179",
      "country_iso": "US",
      "adjustments": [
        {
          "id": 9,
          "source_type": "Spree::TaxRate",
          "source_id": 2,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 26,
          "amount": "1.5",
          "label": "VAT 5%",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-12-24T05:51:01.172-05:00",
          "updated_at": "2019-12-24T05:51:01.181-05:00",
          "display_amount": "$1.50"
        },
        {
          "id": 3,
          "source_type": "Spree::PromotionAction",
          "source_id": 3,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 26,
          "amount": "5.0",
          "label": "bar",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-12-24T05:51:01.098-05:00",
          "updated_at": "2019-12-24T05:51:01.098-05:00",
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
      "payment_method_id": 19,
      "state": "completed",
      "avs_response": null,
      "created_at": "2019-12-24T05:51:01.035-05:00",
      "updated_at": "2019-12-24T05:51:01.035-05:00",
      "payment_method": {
        "id": 19,
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
      "id": 28,
      "tracking": "U10000",
      "tracking_url": null,
      "number": "H18070045783",
      "cost": "100.0",
      "shipped_at": "2019-12-24T05:51:01.054-05:00",
      "state": "shipped",
      "order_id": "M864431969",
      "stock_location_name": "NY Warehouse",
      "giftwrappable": false,
      "stock_location_id": 41,
      "giftwrap": null,
      "shipping_rates": [
        {
          "id": 28,
          "name": "UPS Ground",
          "admin_name": null,
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 22,
          "shipping_method_code": "UPS_GROUND",
          "extra_cost": "",
          "is_flat_rate": false,
          "is_flat_rate_expedited": false,
          "is_free_shipping": false,
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 28,
        "name": "UPS Ground",
        "admin_name": null,
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 22,
        "shipping_method_code": "UPS_GROUND",
        "extra_cost": "",
        "is_flat_rate": false,
        "is_flat_rate_expedited": false,
        "is_free_shipping": false,
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 22,
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
              "id": 32,
              "name": "ShippingCategory #30"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 77,
          "quantity": 1,
          "states": {
            "shipped": 1
          }
        },
        {
          "variant_id": 79,
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
          "source_id": 3,
          "adjustable_type": "Spree::Shipment",
          "adjustable_id": 28,
          "amount": "-10.0",
          "label": "Shipping",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-12-24T05:51:01.111-05:00",
          "updated_at": "2019-12-24T05:51:01.111-05:00",
          "display_amount": "-$10.00"
        },
        {
          "id": 4,
          "source_type": "Spree::PromotionAction",
          "source_id": 3,
          "adjustable_type": "Spree::Shipment",
          "adjustable_id": 28,
          "amount": "-9.99",
          "label": "Shipping",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-12-24T05:51:01.105-05:00",
          "updated_at": "2019-12-24T05:51:01.105-05:00",
          "display_amount": "-$9.99"
        }
      ],
      "stock_location_address": "NY Warehouse, Washington, AL",
      "country_iso": "US",
      "international_shipping": false,
      "delivery_estimation": "Dec 26"
    }
  ],
  "adjustments": [
    {
      "id": 6,
      "source_type": "Spree::Promotion",
      "source_id": 3,
      "adjustable_type": "Spree::Order",
      "adjustable_id": 24,
      "amount": "20.0",
      "label": "adj1",
      "promotion_code_id": null,
      "finalized": false,
      "eligible": true,
      "created_at": "2019-12-24T05:51:01.116-05:00",
      "updated_at": "2019-12-24T05:51:01.116-05:00",
      "display_amount": "$20.00"
    },
    {
      "id": 7,
      "source_type": "Spree::Promotion",
      "source_id": 3,
      "adjustable_type": "Spree::Order",
      "adjustable_id": 24,
      "amount": "30.0",
      "label": "adj2",
      "promotion_code_id": null,
      "finalized": false,
      "eligible": true,
      "created_at": "2019-12-24T05:51:01.119-05:00",
      "updated_at": "2019-12-24T05:51:01.119-05:00",
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
        "country_id": 33,
        "country_iso": "US",
        "state_id": 33,
        "state_name": null,
        "state_text": "AL",
        "country": {
          "id": 33,
          "iso_name": "UNITED STATES",
          "iso": "US",
          "iso3": "USA",
          "name": "United States",
          "numcode": 840
        },
        "state": {
          "id": 33,
          "name": "Alabama",
          "abbr": "AL",
          "country_id": 33
        }
      }
    }
  ],
  "gift_card_total": "0.0",
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
GET /api/orders/M614173589
Accept: application/json
Authorizat IO N: e7021d4e5f78c3313d915629bbff194c2d34bd919fac9098
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
X-Request-Id: 2c9b8a68-5d26-4877-aace-eb19f91c2deb
X-Runtime: 0.010787
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
user[email]=email57%40example.com
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
X-Request-Id: b91eb8dd-a0ab-43c2-99de-083008743ce2
X-Runtime: 0.002405
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
user[email]=email58%40example.com&user[password]=secret
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
Authorization: Bearer 8765d6e9cb5f7f25baaa83fef7da1214d89297644c44e7fc
ETag: W/&quot;cb4c730dc64b967dd1d458e5db5c9180&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 66782f45-5b05-47c9-8593-4d0119f04878
X-Runtime: 0.007213
Vary: Origin
Content-Length: 562
200 OK
```


```json
{
  "id": 59,
  "email": "email58@example.com",
  "persistence_token": null,
  "perishable_token": null,
  "last_request_at": null,
  "login": "email58@example.com",
  "ship_address_id": null,
  "bill_address_id": null,
  "created_at": "2019-12-24T05:51:02.638-05:00",
  "updated_at": "2019-12-24T05:51:02.639-05:00",
  "spree_api_key": "8765d6e9cb5f7f25baaa83fef7da1214d89297644c44e7fc",
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
X-Request-Id: 519a8b2b-313a-4857-8ff7-0288f9535b5c
X-Runtime: 0.020081
Vary: Origin
204 No Content
```




# Products

get products by taxon

## Fetch a single product by id


### Request

#### Endpoint

```plaintext
GET /api/products/product-27-519
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
Date: Tue, 24 Dec 2019 10:50:55 GMT
Surrogate-Control: max-age=900
Surrogate-Key: product_id=1
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;1419dd956254d55ef7342413bd7f3095&quot;
X-Request-Id: 511ae5cf-8212-4a48-a5a2-71bf8ade5c24
X-Runtime: 0.045395
Vary: Origin
Content-Length: 1535
200 OK
```


```json
{
  "id": 27,
  "name": "Product #27 - 519",
  "description": "As seen on TV!",
  "available_on": "2018-12-24T05:50:55.672-05:00",
  "slug": "product-27-519",
  "meta_description": null,
  "meta_keywords": null,
  "taxon_ids": [
    10
  ],
  "total_on_hand": 0,
  "meta_title": null,
  "display_price": "$19.99",
  "brand": null,
  "brand_slug": null,
  "brand_description": null,
  "gift_card": false,
  "trends": [

  ],
  "breadcrumb_taxons": [
    {
      "id": 8,
      "name": "Clothing",
      "taxonomy_id": 3,
      "created_at": "2019-12-24T05:50:55.596-05:00",
      "url": "/category/clothing",
      "position": 1
    },
    {
      "id": 9,
      "name": "Girl",
      "taxonomy_id": 3,
      "created_at": "2019-12-24T05:50:55.629-05:00",
      "url": "/category/clothing/girl",
      "position": 2
    },
    {
      "id": 10,
      "name": "Dresses",
      "taxonomy_id": 3,
      "created_at": "2019-12-24T05:50:55.650-05:00",
      "url": "/category/clothing/girl/dresses",
      "position": 3
    }
  ],
  "has_variants": false,
  "master": {
    "id": 43,
    "name": "Product #27 - 519",
    "sku": "SKU-43",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": true,
    "slug": "product-27-519",
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
        "taxonomy_id": 3,
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
Date: Tue, 24 Dec 2019 10:50:55 GMT
Surrogate-Control: max-age=900
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;de503e31d127f22010cdce7756991f95&quot;
X-Request-Id: 2d8b292b-2955-4e1e-961f-246a0599a5fc
X-Runtime: 0.044710
Vary: Origin
Content-Length: 934
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
      "id": 21,
      "name": "Product #21 - 2685",
      "description": "As seen on TV!",
      "available_on": "2018-12-24T05:50:55.040-05:00",
      "slug": "product-21-2685",
      "meta_description": null,
      "meta_keywords": null,
      "taxon_ids": [

      ],
      "total_on_hand": 0,
      "meta_title": null,
      "display_price": "$19.99",
      "brand": null,
      "brand_slug": null,
      "brand_description": null,
      "gift_card": false,
      "trends": [

      ],
      "breadcrumb_taxons": [

      ],
      "has_variants": false,
      "master": {
        "id": 37,
        "name": "Product #21 - 2685",
        "sku": "SKU-37",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-21-2685",
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
Date: Tue, 24 Dec 2019 10:50:55 GMT
Surrogate-Control: max-age=900
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;89c6f96f0aa845a897e2e56ff7f001cb&quot;
X-Request-Id: 936cb190-493c-4f02-92e4-6bbfaf65cee1
X-Runtime: 0.022720
Vary: Origin
Content-Length: 270
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
      "id": 22,
      "name": "Product #22 - 4612",
      "slug": "product-22-4612",
      "master_id": 38,
      "display_price": "$19.99",
      "brand": null,
      "brand_slug": null,
      "brand_description": null,
      "gift_card": false,
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
GET /api/products?ids=24%2C25%2C26
Host: example.org
Cookie: 
```

`GET /api/products`

#### Parameters


```json
ids: 24,25,26
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
Date: Tue, 24 Dec 2019 10:50:55 GMT
Surrogate-Control: max-age=900
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;2a8cb9a297c85ff2f7f95cf33a56ebcb&quot;
X-Request-Id: 1bb65d2f-8f8f-4a74-9a94-10e2824bcbb8
X-Runtime: 0.083530
Vary: Origin
Content-Length: 2640
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
      "id": 24,
      "name": "Product #24 - 3681",
      "description": "As seen on TV!",
      "available_on": "2018-12-24T05:50:55.325-05:00",
      "slug": "product-24-3681",
      "meta_description": null,
      "meta_keywords": null,
      "taxon_ids": [

      ],
      "total_on_hand": 0,
      "meta_title": null,
      "display_price": "$19.99",
      "brand": null,
      "brand_slug": null,
      "brand_description": null,
      "gift_card": false,
      "trends": [

      ],
      "breadcrumb_taxons": [

      ],
      "has_variants": false,
      "master": {
        "id": 40,
        "name": "Product #24 - 3681",
        "sku": "SKU-40",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-24-3681",
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
      "id": 25,
      "name": "Product #25 - 4851",
      "description": "As seen on TV!",
      "available_on": "2018-12-24T05:50:55.379-05:00",
      "slug": "product-25-4851",
      "meta_description": null,
      "meta_keywords": null,
      "taxon_ids": [

      ],
      "total_on_hand": 0,
      "meta_title": null,
      "display_price": "$19.99",
      "brand": null,
      "brand_slug": null,
      "brand_description": null,
      "gift_card": false,
      "trends": [

      ],
      "breadcrumb_taxons": [

      ],
      "has_variants": false,
      "master": {
        "id": 41,
        "name": "Product #25 - 4851",
        "sku": "SKU-41",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-25-4851",
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
      "id": 26,
      "name": "Product #26 - 1943",
      "description": "As seen on TV!",
      "available_on": "2018-12-24T05:50:55.437-05:00",
      "slug": "product-26-1943",
      "meta_description": null,
      "meta_keywords": null,
      "taxon_ids": [

      ],
      "total_on_hand": 0,
      "meta_title": null,
      "display_price": "$19.99",
      "brand": null,
      "brand_slug": null,
      "brand_description": null,
      "gift_card": false,
      "trends": [

      ],
      "breadcrumb_taxons": [

      ],
      "has_variants": false,
      "master": {
        "id": 42,
        "name": "Product #26 - 1943",
        "sku": "SKU-42",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-26-1943",
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
GET /api/taxons/products?id=3
Host: example.org
Cookie: 
```

`GET /api/taxons/products`

#### Parameters


```json
id: 3
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
ETag: W/&quot;5d0e2c611ef0ccfc8464efbbe97b81cb&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: e7bb6d82-5ef2-4d5e-a005-3699413598d9
X-Runtime: 0.055833
Vary: Origin
Content-Length: 1221
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
      "name": "Product #18 - 7152",
      "description": "As seen on TV!",
      "available_on": "2018-12-24T05:50:54.636-05:00",
      "slug": "product-18-7152",
      "meta_description": null,
      "meta_keywords": null,
      "taxon_ids": [
        3
      ],
      "total_on_hand": 0,
      "meta_title": null,
      "display_price": "$19.99",
      "brand": "Ruby on Rails - 1",
      "brand_slug": "ruby-on-rails-1",
      "brand_description": null,
      "gift_card": false,
      "trends": [

      ],
      "breadcrumb_taxons": [

      ],
      "has_variants": false,
      "master": {
        "id": 34,
        "name": "Product #18 - 7152",
        "sku": "SKU-34",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-18-7152",
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
          "taxon_id": 3,
          "position": 1,
          "taxon": {
            "id": 3,
            "name": "Ruby on Rails - 1",
            "pretty_name": "Ruby on Rails - 1",
            "permalink": "ruby-on-rails-1",
            "parent_id": null,
            "taxonomy_id": 1,
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
ETag: W/&quot;9a5527f3c1f75b8ab60d0bcd7d2dd5f0&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: cb99a8b8-2dd8-4ec4-8181-68337e04b12a
X-Runtime: 0.039002
Vary: Origin
Content-Length: 1221
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
      "name": "Product #20 - 9108",
      "description": "As seen on TV!",
      "available_on": "2018-12-24T05:50:54.906-05:00",
      "slug": "product-20-9108",
      "meta_description": null,
      "meta_keywords": null,
      "taxon_ids": [
        6
      ],
      "total_on_hand": 0,
      "meta_title": null,
      "display_price": "$19.99",
      "brand": "Ruby on Rails - 2",
      "brand_slug": "ruby-on-rails-2",
      "brand_description": null,
      "gift_card": false,
      "trends": [

      ],
      "breadcrumb_taxons": [

      ],
      "has_variants": false,
      "master": {
        "id": 36,
        "name": "Product #20 - 9108",
        "sku": "SKU-36",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-20-9108",
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
          "taxon_id": 6,
          "position": 1,
          "taxon": {
            "id": 6,
            "name": "Ruby on Rails - 2",
            "pretty_name": "Ruby on Rails - 2",
            "permalink": "ruby-on-rails-2",
            "parent_id": null,
            "taxonomy_id": 2,
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
X-Request-Id: e51b5da3-83e1-42f3-8506-1944bf95f355
X-Runtime: 0.010167
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

Get all recently viewed products using a user_id or session_id

## Get all recently viewed products


### Request

#### Endpoint

```plaintext
GET /api/recently_viewed?recently_viewed[session_id]=qlcchcstjp6auwr8924dz4cg5rrxvarvvetvqbp0057u90p69qvebim3novgldm50xvmmvqpuoek1n6bz7hanwf642bb82qm3mdaq0kj2lwt2lv5cjfyev0ol9fpsp60anu1hxid7ih5w873ke4m1smn5fy6ojsn73kq80otbtop1y4h4j115n2u41kwxayxqvo2vnrc02dyzdcbs7ozi5nzitn5r7j2mgyang9s8g6ixsa92i5ouu13pl12t3h&amp;recently_viewed[user_id]=61729
Accept: application/json
Host: example.org
Cookie: 
```

`GET /api/recently_viewed`

#### Parameters


```json
recently_viewed: {&quot;session_id&quot;=&gt;&quot;qlcchcstjp6auwr8924dz4cg5rrxvarvvetvqbp0057u90p69qvebim3novgldm50xvmmvqpuoek1n6bz7hanwf642bb82qm3mdaq0kj2lwt2lv5cjfyev0ol9fpsp60anu1hxid7ih5w873ke4m1smn5fy6ojsn73kq80otbtop1y4h4j115n2u41kwxayxqvo2vnrc02dyzdcbs7ozi5nzitn5r7j2mgyang9s8g6ixsa92i5ouu13pl12t3h&quot;, &quot;user_id&quot;=&gt;&quot;61729&quot;}
```


| Name | Description |
|:-----|:------------|
| recently_viewed[user_id]  | Either a user id or a session id are required |
| recently_viewed[session_id]  | Either a user id or a session id are required |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
ETag: W/&quot;30fee51eba7871865e6c6907d1bcc25a&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: cf35e702-b1d8-45ed-88e8-3601605c7a9e
X-Runtime: 0.022284
Vary: Origin
Content-Length: 119
200 OK
```


```json
[
  {
    "at": "2019-12-24T05:50:54.443-05:00",
    "variant_id": "var1"
  },
  {
    "at": "2019-12-24T05:55:54.443-05:00",
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
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/recently_viewed`

#### Parameters


```json
recently_viewed[session_id]=bd8e1x7lvez4mmpn4kiw4cfna78rhnexf3dpwjpgbzzmbd1y5c45z67oggbf361ugonbgglqt6df5f59zawda06wcpaj1va5leqpcg6y1f6rcvu2lrjsionjrody7yyt1umxb04gb01kft9ky8nzqlr64wnanezpxwynghu6zhjtmnbmrhn4cjftxto62pwxh02i1s6xuoovma1mw1en248odxgtvgyfyfhf4klifziojy7c69z2ujjil92574x&recently_viewed[user_id]=36219&recently_viewed[variant_id]=foo
```


| Name | Description |
|:-----|:------------|
| recently_viewed[user_id]  | Either a user id or a session id are required |
| recently_viewed[session_id]  | Either a user id or a session id are required |
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
X-Request-Id: 3bb87b98-5884-403e-ab3a-83f2f831626d
X-Runtime: 0.002877
Vary: Origin
204 No Content
```




# Return Authorizations

Get user return authorizations

## Can get another user&#39;s return authorization


### Request

#### Endpoint

```plaintext
GET /api/returns/RA543027046
Authorizat IO N: Bearer 7760d2458ffa9c6e5d0afce474b641fae8ce369d2b664aff
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
ETag: W/&quot;eb2a4d46bb4baacedc7764aa33d75d96&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 3c2da856-aee6-416b-9435-a2b25099462c
X-Runtime: 0.041805
Vary: Origin
Content-Length: 2924
200 OK
```


```json
{
  "id": 4,
  "number": "RA543027046",
  "state": "authorized",
  "order_id": 10,
  "memo": "Items were broken",
  "created_at": "2019-12-24T05:50:53.393-05:00",
  "updated_at": "2019-12-24T05:50:53.393-05:00",
  "amount": "10.0",
  "reason": {
    "id": 7,
    "name": "Defect #7",
    "active": true,
    "mutable": true,
    "created_at": "2019-12-24T05:50:53.390-05:00",
    "updated_at": "2019-12-24T05:50:53.390-05:00",
    "mirakl_code": null
  },
  "order": {
    "id": 10,
    "number": "M772149045",
    "item_total": "10.0",
    "total": "110.0",
    "state": "complete",
    "adjustment_total": "0.0",
    "user_id": 33,
    "completed_at": "2019-12-24T05:50:53.334-05:00",
    "bill_address_id": 18,
    "ship_address_id": 19,
    "payment_total": "110.0",
    "shipment_state": "shipped",
    "payment_state": "paid",
    "email": "email33@example.com",
    "special_instructions": null,
    "created_at": "2019-12-24T05:50:53.282-05:00",
    "updated_at": "2019-12-24T05:50:53.377-05:00",
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
    "guest_token": "Y-qgNCm8e3kj5f9RVYqvqg",
    "canceled_at": null,
    "canceler_id": null,
    "store_id": 10,
    "approver_name": null,
    "frontend_viewable": true,
    "is_gift": false,
    "gift_email": null,
    "gift_message": null,
    "gift_card_total": "0.0"
  },
  "ship_address": {
    "id": 19,
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
  "bill_address": {
    "id": 18,
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
  "return_items": [
    {
      "name": "Product #11 - 732",
      "brand": null,
      "brand_slug": null,
      "image": null,
      "product_slug": "product-11-732",
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
        "id": 4,
        "month": "12",
        "year": "2020",
        "cc_type": null,
        "last_digits": "1111",
        "name": "Spree Commerce",
        "gateway_customer_profile_id": "BGS-155032",
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
Authorizat IO N: Bearer a8521430cee487a7c8f3b772170f7eabe22c7a9d2f1f8c06
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
ETag: W/&quot;3c6f10c7b132480eaa273fcd35c06f4e&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: bb23fa4d-3eb3-47c0-ac76-38af5c868614
X-Runtime: 0.014195
Vary: Origin
Content-Length: 169
200 OK
```


```json
{
  "return_authorizations": [
    {
      "number": "RA480588013",
      "created_at": "2019-12-24T05:50:52.348-05:00",
      "return_amount": "10.0",
      "order_number": "M024817956",
      "state": "authorized"
    }
  ]
}
```



## returns a 200


### Request

#### Endpoint

```plaintext
GET /api/returns/RA447166143
Authorizat IO N: Bearer ce3667f447bd976481d8c14478776236f1c99cd5752a4825
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
ETag: W/&quot;3e9e09f712730948e73e267de88688e9&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 42ca9b11-5c0a-4479-bcdf-1656d7d6a72c
X-Runtime: 0.043091
Vary: Origin
Content-Length: 2833
200 OK
```


```json
{
  "id": 2,
  "number": "RA447166143",
  "state": "authorized",
  "order_id": 8,
  "memo": "Items were broken",
  "created_at": "2019-12-24T05:50:52.707-05:00",
  "updated_at": "2019-12-24T05:50:52.707-05:00",
  "amount": "10.0",
  "reason": {
    "id": 3,
    "name": "Defect #3",
    "active": true,
    "mutable": true,
    "created_at": "2019-12-24T05:50:52.704-05:00",
    "updated_at": "2019-12-24T05:50:52.704-05:00",
    "mirakl_code": null
  },
  "order": {
    "id": 8,
    "number": "M471377413",
    "item_total": "10.0",
    "total": "110.0",
    "state": "complete",
    "adjustment_total": "0.0",
    "user_id": 30,
    "completed_at": "2019-12-24T05:50:52.647-05:00",
    "bill_address_id": 14,
    "ship_address_id": 15,
    "payment_total": "110.0",
    "shipment_state": "shipped",
    "payment_state": "paid",
    "email": "email30@example.com",
    "special_instructions": null,
    "created_at": "2019-12-24T05:50:52.585-05:00",
    "updated_at": "2019-12-24T05:50:52.691-05:00",
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
    "guest_token": "eOH8A036Wu-NOTq-Die4IQ",
    "canceled_at": null,
    "canceler_id": null,
    "store_id": 8,
    "approver_name": null,
    "frontend_viewable": true,
    "is_gift": false,
    "gift_email": null,
    "gift_message": null,
    "gift_card_total": "0.0"
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
  "return_items": [
    {
      "name": "Product #9 - 6440",
      "brand": null,
      "brand_slug": null,
      "image": null,
      "product_slug": "product-9-6440",
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
GET /api/returns/RA323374325
Authorizat IO N: Bearer 12d581795537c33401a74846f579db7aaa8f12c067cbc554
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
X-Request-Id: b0a99e0f-aaeb-43ad-8a10-8bf943bc13b5
X-Runtime: 0.009890
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
stock_request[email]=reid_bergnaum%40dooleystroman.co.uk&stock_request[variant_id]=26
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
X-Request-Id: d5e35458-9f06-4e11-b753-49d2465555dd
X-Runtime: 0.003840
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
stock_request[email]=foo&stock_request[variant_id]=24
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
X-Request-Id: fefcb59a-91bd-4ab0-a2b7-70e17ce21ff8
X-Runtime: 0.025120
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
stock_request[email]=mora.lakin%40monahanemmerich.us&stock_request[variant_id]=28
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
X-Request-Id: e615ca04-3c68-4947-9048-b88cc168e926
X-Runtime: 0.003531
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
Authorizat IO N: Bearer 82e0953da62eb206ff3329bff54ee89c8a0a21135b5bb1f9
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
ETag: W/&quot;9a7465975935e6fab5371f7159d9f413&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: c060f253-ecf9-4343-aeee-ccbe14ef641a
X-Runtime: 0.031568
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
      "created_at": "2019-12-24T05:51:02.540-05:00"
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

Create a subscriber. Any user can create a subscriber of their own,                 admins can create subscribers for other users.

## Create a subscriber


### Request

#### Endpoint

```plaintext
POST /api/subscribers
Accept: application/json
Authorizat IO N: Bearer ec582a02f906d98a05721bf1e12c11673b9f3849ec4361ee
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/subscribers`

#### Parameters


```json
subscriber[email]=desirae.kuphal%40stamm.com&subscriber[user_id]=7&subscriber[first_name]=Randolph&subscriber[last_name]=Adams&subscriber[status]=subscribed
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
ETag: W/&quot;920eeb053917486cfd73587538ab9b28&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: b0ae4fa6-ee3f-4936-a63d-b2e8d12f474c
X-Runtime: 0.040988
Vary: Origin
Content-Length: 178
201 Created
```


```json
{
  "id": 1,
  "user_id": 7,
  "email": "desirae.kuphal@stamm.com",
  "first_name": "Randolph",
  "last_name": "Adams",
  "source": "",
  "status": "subscribed",
  "created_at": "2019-12-24T05:50:51.643-05:00"
}
```



## Delete a subscriber


### Request

#### Endpoint

```plaintext
DELETE /api/subscribers/4
Accept: application/json
Authorizat IO N: Bearer c7a56b2d051fce9920ded37635fb39b2ee37ba9d048c6d7e
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
X-Request-Id: 6ab80028-8ddf-4fc2-b5b1-2f7e1f35ab8d
X-Runtime: 0.006036
Vary: Origin
204 No Content
```




## Get a single subscriber by id


### Request

#### Endpoint

```plaintext
GET /api/subscribers/2
Accept: application/json
Authorizat IO N: Bearer c88d5bbe7a451b924a551bd5e9612e87917af6c9550f7c7c
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
ETag: W/&quot;e1c6fab7d739a042f155a99c68fabe9f&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 10074502-9a2d-4ac4-ba79-fdef68324ee3
X-Runtime: 0.007373
Vary: Origin
Content-Length: 182
200 OK
```


```json
{
  "id": 2,
  "user_id": 8,
  "email": "monserrate.paucek@gislason.biz",
  "first_name": "Lael",
  "last_name": "Kuvalis",
  "source": "",
  "status": "subscribed",
  "created_at": "2019-12-24T05:50:51.661-05:00"
}
```



## Get all subscribers


### Request

#### Endpoint

```plaintext
GET /api/subscribers
Accept: application/json
Authorizat IO N: Bearer ff25885fb980099947f33c5e084982e4fd6c98c2180852a9
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
ETag: W/&quot;8fe38d1e8edf4decd4b6b49a3dd0cbd1&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 324fba45-914f-4db1-a3b1-4b96c4716cfc
X-Runtime: 0.011203
Vary: Origin
Content-Length: 630
200 OK
```


```json
{
  "subscribers": [
    {
      "id": 5,
      "user_id": null,
      "email": "isela_bogan@sporer.us",
      "first_name": "Connie",
      "last_name": "Mosciski",
      "source": "",
      "status": "subscribed",
      "created_at": "2019-12-24T05:50:51.707-05:00"
    },
    {
      "id": 6,
      "user_id": null,
      "email": "edgardo@ullrich.name",
      "first_name": "Pearlie",
      "last_name": "Simonis",
      "source": "",
      "status": "subscribed",
      "created_at": "2019-12-24T05:50:51.708-05:00"
    },
    {
      "id": 7,
      "user_id": null,
      "email": "roselee@rosenbaumschowalter.name",
      "first_name": "Celina",
      "last_name": "Batz",
      "source": "",
      "status": "subscribed",
      "created_at": "2019-12-24T05:50:51.709-05:00"
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
PATCH /api/subscribers/3
Accept: application/json
Authorizat IO N: Bearer dcddf3c8a816ee76072b89014f5233c9208783c228781197
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
ETag: W/&quot;1af5c1bf7c03578c30789af10315eb4a&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 55f60f15-d5f1-498e-98aa-919121794386
X-Runtime: 0.007581
Vary: Origin
Content-Length: 171
200 OK
```


```json
{
  "id": 3,
  "user_id": 9,
  "email": "lynn@tromp.com",
  "first_name": "Delores",
  "last_name": "Bernier",
  "source": "",
  "status": "unsubscribed",
  "created_at": "2019-12-24T05:50:51.678-05:00"
}
```



# Taxons API

Returns taxons associated with the Navigation Taxonomy for display in the menu bar

## Get all taxons


### Request

#### Endpoint

```plaintext
GET /api/taxons
Host: example.org
Cookie: 
```

`GET /api/taxons`

#### Parameters



| Name | Description |
|:-----|:------------|
| without_children  | Use this parameter to disable returning descendant taxons |
| q[purchasable_boutiques]  | Use this parameter to only return boutiques with purchasable products |
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
ETag: W/&quot;4c20f1c5bdecbf11dcbd10a6795db254&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 8fad403c-4c96-4b0b-9141-c36eca45945f
X-Runtime: 0.037568
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
      "id": 13,
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
          "id": 14,
          "name": "Kids",
          "pretty_name": "Category -> Kids",
          "permalink": "category/kids",
          "parent_id": 13,
          "taxonomy_id": 5,
          "url_override": null
        }
      ]
    },
    {
      "id": 14,
      "name": "Kids",
      "pretty_name": "Category -> Kids",
      "permalink": "category/kids",
      "parent_id": 13,
      "taxonomy_id": 5,
      "url_override": null,
      "description": "Kids",
      "icon": "/assets/default_taxon.png",
      "taxons": [
        {
          "id": 15,
          "name": "Boys",
          "pretty_name": "Category -> Kids -> Boys",
          "permalink": "category/kids/boys",
          "parent_id": 14,
          "taxonomy_id": 5,
          "url_override": null
        },
        {
          "id": 18,
          "name": "Girls",
          "pretty_name": "Category -> Kids -> Girls",
          "permalink": "category/kids/girls",
          "parent_id": 14,
          "taxonomy_id": 5,
          "url_override": null
        }
      ]
    },
    {
      "id": 15,
      "name": "Boys",
      "pretty_name": "Category -> Kids -> Boys",
      "permalink": "category/kids/boys",
      "parent_id": 14,
      "taxonomy_id": 5,
      "url_override": null,
      "description": "Boys",
      "icon": "/assets/default_taxon.png",
      "taxons": [
        {
          "id": 16,
          "name": "Boys Tops",
          "pretty_name": "Category -> Kids -> Boys -> Boys Tops",
          "permalink": "category/kids/boys/boys-tops",
          "parent_id": 15,
          "taxonomy_id": 5,
          "url_override": null
        }
      ]
    },
    {
      "id": 16,
      "name": "Boys Tops",
      "pretty_name": "Category -> Kids -> Boys -> Boys Tops",
      "permalink": "category/kids/boys/boys-tops",
      "parent_id": 15,
      "taxonomy_id": 5,
      "url_override": null,
      "description": "Boys Tops",
      "icon": "/assets/default_taxon.png",
      "taxons": [
        {
          "id": 17,
          "name": "Boys Shirts",
          "pretty_name": "Category -> Kids -> Boys -> Boys Tops -> Boys Shirts",
          "permalink": "category/kids/boys/boys-tops/boys-shirts",
          "parent_id": 16,
          "taxonomy_id": 5,
          "url_override": null
        }
      ]
    },
    {
      "id": 17,
      "name": "Boys Shirts",
      "pretty_name": "Category -> Kids -> Boys -> Boys Tops -> Boys Shirts",
      "permalink": "category/kids/boys/boys-tops/boys-shirts",
      "parent_id": 16,
      "taxonomy_id": 5,
      "url_override": null,
      "description": "Boys Shirts",
      "icon": "/assets/default_taxon.png",
      "taxons": [

      ]
    },
    {
      "id": 18,
      "name": "Girls",
      "pretty_name": "Category -> Kids -> Girls",
      "permalink": "category/kids/girls",
      "parent_id": 14,
      "taxonomy_id": 5,
      "url_override": null,
      "description": "Girls",
      "icon": "/assets/default_taxon.png",
      "taxons": [
        {
          "id": 19,
          "name": "Girls Tops",
          "pretty_name": "Category -> Kids -> Girls -> Girls Tops",
          "permalink": "category/kids/girls/girls-tops",
          "parent_id": 18,
          "taxonomy_id": 5,
          "url_override": null
        }
      ]
    },
    {
      "id": 19,
      "name": "Girls Tops",
      "pretty_name": "Category -> Kids -> Girls -> Girls Tops",
      "permalink": "category/kids/girls/girls-tops",
      "parent_id": 18,
      "taxonomy_id": 5,
      "url_override": null,
      "description": "Girls Tops",
      "icon": "/assets/default_taxon.png",
      "taxons": [
        {
          "id": 20,
          "name": "Girls Shirts",
          "pretty_name": "Category -> Kids -> Girls -> Girls Tops -> Girls Shirts",
          "permalink": "category/kids/girls/girls-tops/girls-shirts",
          "parent_id": 19,
          "taxonomy_id": 5,
          "url_override": null
        }
      ]
    },
    {
      "id": 20,
      "name": "Girls Shirts",
      "pretty_name": "Category -> Kids -> Girls -> Girls Tops -> Girls Shirts",
      "permalink": "category/kids/girls/girls-tops/girls-shirts",
      "parent_id": 19,
      "taxonomy_id": 5,
      "url_override": null,
      "description": "Girls Shirts",
      "icon": "/assets/default_taxon.png",
      "taxons": [

      ]
    },
    {
      "id": 21,
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
          "id": 22,
          "name": "Ruby on Rails - 3",
          "pretty_name": "Brand -> Ruby on Rails - 3",
          "permalink": "brand/ruby-on-rails-3",
          "parent_id": 21,
          "taxonomy_id": 6,
          "url_override": null
        },
        {
          "id": 23,
          "name": "Ruby on Rails - 4",
          "pretty_name": "Brand -> Ruby on Rails - 4",
          "permalink": "brand/ruby-on-rails-4",
          "parent_id": 21,
          "taxonomy_id": 6,
          "url_override": null
        }
      ]
    },
    {
      "id": 22,
      "name": "Ruby on Rails - 3",
      "pretty_name": "Brand -> Ruby on Rails - 3",
      "permalink": "brand/ruby-on-rails-3",
      "parent_id": 21,
      "taxonomy_id": 6,
      "url_override": null,
      "description": "Ruby on Rails - 3",
      "icon": "/assets/default_taxon.png",
      "taxons": [

      ]
    },
    {
      "id": 23,
      "name": "Ruby on Rails - 4",
      "pretty_name": "Brand -> Ruby on Rails - 4",
      "permalink": "brand/ruby-on-rails-4",
      "parent_id": 21,
      "taxonomy_id": 6,
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
| q[purchasable_boutiques]  | Use this parameter to only return boutiques with purchasable products |
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
ETag: W/&quot;332e26757211c0b4681b9b87366b5f4e&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: eaec57ae-51b5-4ffe-b63e-ae64acc551d9
X-Runtime: 0.010713
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
      "id": 32,
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
      "id": 33,
      "name": "Ruby on Rails - 5",
      "pretty_name": "Brand -> Ruby on Rails - 5",
      "permalink": "brand/ruby-on-rails-5",
      "parent_id": 32,
      "taxonomy_id": 8,
      "url_override": null,
      "description": "Ruby on Rails - 5",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 34,
      "name": "Ruby on Rails - 6",
      "pretty_name": "Brand -> Ruby on Rails - 6",
      "permalink": "brand/ruby-on-rails-6",
      "parent_id": 32,
      "taxonomy_id": 8,
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
| q[purchasable_boutiques]  | Use this parameter to only return boutiques with purchasable products |
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
ETag: W/&quot;6009582c8d9eea6078ab91a74806d4e0&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: b7106dfb-0cca-4807-a6e5-fc40d2a54dd5
X-Runtime: 0.022884
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
      "id": 35,
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
      "id": 36,
      "name": "Kids",
      "pretty_name": "Category -> Kids",
      "permalink": "category/kids",
      "parent_id": 35,
      "taxonomy_id": 9,
      "url_override": null,
      "description": "Kids",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 37,
      "name": "Boys",
      "pretty_name": "Category -> Kids -> Boys",
      "permalink": "category/kids/boys",
      "parent_id": 36,
      "taxonomy_id": 9,
      "url_override": null,
      "description": "Boys",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 38,
      "name": "Boys Tops",
      "pretty_name": "Category -> Kids -> Boys -> Boys Tops",
      "permalink": "category/kids/boys/boys-tops",
      "parent_id": 37,
      "taxonomy_id": 9,
      "url_override": null,
      "description": "Boys Tops",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 39,
      "name": "Boys Shirts",
      "pretty_name": "Category -> Kids -> Boys -> Boys Tops -> Boys Shirts",
      "permalink": "category/kids/boys/boys-tops/boys-shirts",
      "parent_id": 38,
      "taxonomy_id": 9,
      "url_override": null,
      "description": "Boys Shirts",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 40,
      "name": "Girls",
      "pretty_name": "Category -> Kids -> Girls",
      "permalink": "category/kids/girls",
      "parent_id": 36,
      "taxonomy_id": 9,
      "url_override": null,
      "description": "Girls",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 41,
      "name": "Girls Tops",
      "pretty_name": "Category -> Kids -> Girls -> Girls Tops",
      "permalink": "category/kids/girls/girls-tops",
      "parent_id": 40,
      "taxonomy_id": 9,
      "url_override": null,
      "description": "Girls Tops",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 42,
      "name": "Girls Shirts",
      "pretty_name": "Category -> Kids -> Girls -> Girls Tops -> Girls Shirts",
      "permalink": "category/kids/girls/girls-tops/girls-shirts",
      "parent_id": 41,
      "taxonomy_id": 9,
      "url_override": null,
      "description": "Girls Shirts",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 43,
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
      "id": 44,
      "name": "Ruby on Rails - 7",
      "pretty_name": "Brand -> Ruby on Rails - 7",
      "permalink": "brand/ruby-on-rails-7",
      "parent_id": 43,
      "taxonomy_id": 10,
      "url_override": null,
      "description": "Ruby on Rails - 7",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 45,
      "name": "Ruby on Rails - 8",
      "pretty_name": "Brand -> Ruby on Rails - 8",
      "permalink": "brand/ruby-on-rails-8",
      "parent_id": 43,
      "taxonomy_id": 10,
      "url_override": null,
      "description": "Ruby on Rails - 8",
      "icon": "/assets/default_taxon.png"
    }
  ]
}
```



## Get navigation taxons


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
ETag: W/&quot;284c3da05619b9362a24f70523bdbabe&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: e43e6336-9090-4e05-b920-676f456f5c85
X-Runtime: 0.006076
Vary: Origin
Content-Length: 150
200 OK
```


```json
[
  {
    "id": 12,
    "name": "Kids",
    "navigation_url": "/navigation/kids",
    "parent_id": 11,
    "lft": 2,
    "depth": 1,
    "highlight": false,
    "header_link": false,
    "add_flair": false
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
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/users/login`

#### Parameters


```json
user[email]=email51%40example.com&user[password]=secret
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
Authorization: Bearer 0d23c23003ba3c0e2fe28e23e4d106dee15660136c78ac12
ETag: W/&quot;b06ccd1a4cdb7c28534ee08c500e6cf5&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: bbad252c-5792-4a0d-90d5-b91700b982ff
X-Runtime: 0.008860
Vary: Origin
Content-Length: 562
200 OK
```


```json
{
  "id": 51,
  "email": "email51@example.com",
  "persistence_token": null,
  "perishable_token": null,
  "last_request_at": null,
  "login": "email51@example.com",
  "ship_address_id": null,
  "bill_address_id": null,
  "created_at": "2019-12-24T05:51:02.128-05:00",
  "updated_at": "2019-12-24T05:51:02.129-05:00",
  "spree_api_key": "0d23c23003ba3c0e2fe28e23e4d106dee15660136c78ac12",
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
X-Spree-Order-Token: hjOKsVPwRrwnjGIWloC75A
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/users/login`

#### Parameters


```json
user[email]=email52%40example.com&user[password]=secret&order_number=M615471444
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
Authorization: Bearer f8fbb86f9c8f01e3b88e16fb723db6d2fdb3577f5e4f6248
ETag: W/&quot;73230a22d32a21b2f76719f00ad20637&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 5105f0d4-cd07-47ba-823d-2ac8246f3121
X-Runtime: 0.010972
Vary: Origin
Content-Length: 562
200 OK
```


```json
{
  "id": 52,
  "email": "email52@example.com",
  "persistence_token": null,
  "perishable_token": null,
  "last_request_at": null,
  "login": "email52@example.com",
  "ship_address_id": null,
  "bill_address_id": null,
  "created_at": "2019-12-24T05:51:02.145-05:00",
  "updated_at": "2019-12-24T05:51:02.146-05:00",
  "spree_api_key": "f8fbb86f9c8f01e3b88e16fb723db6d2fdb3577f5e4f6248",
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
Authorizat IO N: Bearer 0690a906964f629280656edc101bd68e96dc86598cfcc467
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
Authorization: Bearer 0690a906964f629280656edc101bd68e96dc86598cfcc467
ETag: W/&quot;55cc27bb3b96781340c688602bd0bcc6&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: f6b865c7-ecfe-46a1-9de6-ea48d8de6f82
X-Runtime: 0.020184
Vary: Origin
Content-Length: 1521
200 OK
```


```json
{
  "email": "email53@example.com",
  "first_name": null,
  "last_name": null,
  "id": 53,
  "subscribed": false,
  "addresses": [
    {
      "id": 54,
      "firstname": "John",
      "lastname": null,
      "full_name": "John",
      "address1": "A Different Road",
      "address2": "Northwest",
      "city": "Herndon",
      "zipcode": "10049",
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
      "default": true
    },
    {
      "id": 53,
      "firstname": "John",
      "lastname": null,
      "full_name": "John",
      "address1": "PO Box 1337",
      "address2": "Northwest",
      "city": "Herndon",
      "zipcode": "10048",
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
      "default": false
    }
  ],
  "payment_sources": [
    {
      "id": 3,
      "default": true,
      "source": {
        "id": 5,
        "payment_type": "CreditCard",
        "token": null,
        "created_at": "2019-12-24T05:51:02.430-05:00",
        "cc_type": null,
        "last_digits": null,
        "month": null,
        "year": null
      }
    },
    {
      "id": 4,
      "default": false,
      "source": {
        "id": 6,
        "payment_type": "ApplePayCard",
        "token": null,
        "created_at": "2019-12-24T05:51:02.445-05:00",
        "cc_type": null,
        "last_digits": null,
        "month": null,
        "year": null
      }
    },
    {
      "id": 5,
      "default": false,
      "source": {
        "id": 7,
        "payment_type": "PayPalAccount",
        "token": null,
        "created_at": "2019-12-24T05:51:02.459-05:00",
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
Authorization: Bearer 0f7bea6f85d76168ae7a13dd8513ab352de42eb40b9998ef
ETag: W/&quot;95598e2e92ca5f61bee082974a7aaf3b&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 1ae9dfad-e595-4dae-9420-6d6e120800cf
X-Runtime: 0.012282
Vary: Origin
Content-Length: 185
201 Created
```


```json
{
  "id": 54,
  "email": "test@example.com",
  "created_at": "2019-12-24T05:51:02.492-05:00",
  "updated_at": "2019-12-24T05:51:02.493-05:00",
  "subscribed": false,
  "bill_address": null,
  "ship_address": null
}
```



## Subscribe a user


### Request

#### Endpoint

```plaintext
PUT /api/users/50/subscribe
Authorizat IO N: Bearer 11342ef0883676ef16551af98272586d1d852d8be6e35ec9
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
Authorization: Bearer 11342ef0883676ef16551af98272586d1d852d8be6e35ec9
ETag: W/&quot;02de3977389f1080c021923d3fc29698&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: a753b406-b8d2-401e-aba5-9165623fc72a
X-Runtime: 0.011126
Vary: Origin
Content-Length: 187
200 OK
```


```json
{
  "id": 50,
  "email": "email50@example.com",
  "created_at": "2019-12-24T05:51:02.106-05:00",
  "updated_at": "2019-12-24T05:51:02.108-05:00",
  "subscribed": true,
  "bill_address": null,
  "ship_address": null
}
```



## Unsubscribe a user


### Request

#### Endpoint

```plaintext
PUT /api/users/49/unsubscribe
Authorizat IO N: Bearer 82b44de1e4afed75dfb32c9e92358261e75a4e2234a962aa
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
Authorization: Bearer 82b44de1e4afed75dfb32c9e92358261e75a4e2234a962aa
ETag: W/&quot;26f548e6bb7420c95866f9e3aec6a607&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 98549aeb-d15e-4efd-8707-c1cd88445c92
X-Runtime: 0.026573
Vary: Origin
Content-Length: 188
200 OK
```


```json
{
  "id": 49,
  "email": "email49@example.com",
  "created_at": "2019-12-24T05:51:02.069-05:00",
  "updated_at": "2019-12-24T05:51:02.071-05:00",
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
GET /api/variants/2
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
ETag: W/&quot;3d55416c98efe5e7d3f6046e653349bc&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 50ccb080-da7d-4b68-9c01-4bf7f4ca35a2
X-Runtime: 0.241577
Vary: Origin
Content-Length: 1921
200 OK
```


```json
{
  "id": 2,
  "name": "Product #1 - 8823",
  "sku": "SKU-1",
  "weight": "0.0",
  "height": null,
  "width": null,
  "depth": null,
  "is_master": false,
  "slug": "product-1-8823",
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
    {
      "id": 1,
      "position": 1,
      "attachment_content_type": "image/jpeg",
      "attachment_file_name": "thinking-cat.jpg",
      "type": "Spree::Image",
      "attachment_updated_at": "2019-12-24T05:50:47.787-05:00",
      "attachment_width": 489,
      "attachment_height": 490,
      "alt": null,
      "viewable_type": "Spree::Variant",
      "viewable_id": 2,
      "mini_url": "/spree/products/1/mini/thinking-cat.jpg?1577184647",
      "small_url": "/spree/products/1/small/thinking-cat.jpg?1577184647",
      "product_url": "/spree/products/1/product/thinking-cat.jpg?1577184647",
      "large_url": "/spree/products/1/large/thinking-cat.jpg?1577184647"
    }
  ],
  "variant_properties": [

  ],
  "stock_items": [

  ],
  "prices": [
    {
      "id": 2,
      "vendor_id": 4,
      "price": "10.0",
      "original_price": "10.0",
      "discount_percent": 0.0,
      "total_on_hand": 0,
      "country_iso": null,
      "final_sale": false,
      "on_sale": false,
      "offer_settings": {
        "cost_price": null
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
      "id": 3,
      "vendor_id": 5,
      "price": "20.0",
      "original_price": "20.0",
      "discount_percent": 0.0,
      "total_on_hand": 0,
      "country_iso": null,
      "final_sale": false,
      "on_sale": false,
      "offer_settings": {
        "cost_price": null
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
Authorizat IO N: Bearer abaec47905e605ed665f414e27932eaf979a75fdafb8d29b
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
ETag: W/&quot;963ac3c52567bc0bd0e3275af764ed9a&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 53ce327f-4b09-4097-ab5e-11939e8be1e1
X-Runtime: 0.032231
Vary: Origin
Content-Length: 206
200 OK
```


```json
[
  {
    "id": 6,
    "user_id": 78,
    "payment_source_type": "SolidusPaypalBraintree::Source",
    "payment_source_id": 8,
    "default": false,
    "created_at": "2019-12-24T05:51:03.799-05:00",
    "updated_at": "2019-12-24T05:51:03.799-05:00"
  }
]
```



## Remove the payment from the user wallet


### Request

#### Endpoint

```plaintext
DELETE /api/wallet_payment_sources/8
Accept: application/json
Authorizat IO N: Bearer dc8840a4674831985d3a45c56663cbecfc05ecbb615d064b
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
X-Request-Id: 454aa22f-d3b4-4b8b-8cae-7d206c6a117f
X-Runtime: 0.011033
Vary: Origin
204 No Content
```




## Set a wallet payment source as the default user payment method


### Request

#### Endpoint

```plaintext
POST /api/wallet_payment_sources/7/default
Accept: application/json
Authorizat IO N: Bearer 705f5333eb514902a49e1c00d123abe3c3230da9b08d1a66
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
X-Request-Id: 0ac2daf4-4baa-4573-b027-5157de0326c5
X-Runtime: 0.008642
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
Authorizat IO N: Bearer 32266f991f9ae8a5816e9532e33c5f11a5ead92c3ea7c3fe
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/wished_products`

#### Parameters


```json
wished_product[wishlist_id]=40&wished_product[variant_id]=149&wished_product[quantity]=2&wished_product[remark]=Foo+bar
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
ETag: W/&quot;dd33fe4dadbe3ee779135b1b19fb5334&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 6f944ff0-f0f7-4065-9dc6-e73714fa5b2f
X-Runtime: 0.010964
Vary: Origin
Content-Length: 75
201 Created
```


```json
{
  "id": 31,
  "wishlist_id": 40,
  "variant_id": 149,
  "quantity": 2,
  "remark": "Foo bar"
}
```



## Delete a wished product


### Request

#### Endpoint

```plaintext
DELETE /api/wished_products/19
Accept: application/json
Authorizat IO N: Bearer 26b49ba69f935c4a70af4f17da140d5ab351d3dbe0240932
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
X-Request-Id: 24b36653-10e0-48c5-80bc-a1f7d0f3f025
X-Runtime: 0.010963
Vary: Origin
204 No Content
```




## Get a single wished product


### Request

#### Endpoint

```plaintext
GET /api/wished_products/16
Accept: application/json
Authorizat IO N: Bearer 5e6c9ed562ff9d1010f0508eb6c3a4622f53580d90af3f7c
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
ETag: W/&quot;fa0ef30b199c456b67e860aa6614477a&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 3e0dcd1c-2a1c-431d-99c1-7d35fe37f06d
X-Runtime: 0.009600
Vary: Origin
Content-Length: 70
200 OK
```


```json
{
  "id": 16,
  "wishlist_id": 35,
  "variant_id": 117,
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
Authorizat IO N: Bearer 0ead6d3c57130d40366ae7a68fa8253d6f9bec796769a21d
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
ETag: W/&quot;2d36f9bda28a13da2f03ceae111789fc&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 8ebdb8ed-dcb5-479b-a625-f78c8b8b04e5
X-Runtime: 0.032792
Vary: Origin
Content-Length: 301
200 OK
```


```json
{
  "wished_products": [
    {
      "id": 10,
      "wishlist_id": 29,
      "variant_id": 105,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 11,
      "wishlist_id": 30,
      "variant_id": 107,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 12,
      "wishlist_id": 31,
      "variant_id": 109,
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
Authorizat IO N: Bearer 55b68f77fe62671eb3f4d5918a0651620226e29c8569db0b
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
ETag: W/&quot;fb7768ce06454d89ece72010cae12b81&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 2fd9a874-43ad-4c31-8663-6a93a780bd0e
X-Runtime: 0.078839
Vary: Origin
Content-Length: 2149
200 OK
```


```json
{
  "wished_products": [
    {
      "id": 13,
      "wishlist_id": 32,
      "variant_id": 111,
      "quantity": 1,
      "remark": null,
      "variant": {
        "id": 111,
        "name": "Product #61 - 3759",
        "sku": "SKU-110",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-61-3759",
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
      "variant_id": 113,
      "quantity": 1,
      "remark": null,
      "variant": {
        "id": 113,
        "name": "Product #62 - 254",
        "sku": "SKU-112",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-62-254",
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
      "wishlist_id": 34,
      "variant_id": 115,
      "quantity": 1,
      "remark": null,
      "variant": {
        "id": 115,
        "name": "Product #63 - 36",
        "sku": "SKU-114",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-63-36",
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
Authorizat IO N: Bearer f27ebcf24cc94e5fde81cd9b58d4ecbedcfaa55beb2b79a9
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
ETag: W/&quot;e813af4afa507f579db6baf25d727988&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: eb726158-d0e9-4cc8-9f26-148f8cc80b47
X-Runtime: 0.076662
Vary: Origin
Content-Length: 2095
200 OK
```


```json
{
  "wished_products": [
    {
      "id": 28,
      "wishlist_id": 39,
      "variant_id": 143,
      "quantity": 1,
      "remark": null,
      "variant": {
        "id": 143,
        "name": "Product #77 - 9962",
        "sku": "SKU-142",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-77-9962",
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
            "id": 66,
            "name": "Size-66",
            "presentation": "S",
            "option_type_name": "foo-size-66",
            "option_type_id": 66,
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
      "id": 29,
      "wishlist_id": 39,
      "variant_id": 145,
      "quantity": 1,
      "remark": null,
      "variant": {
        "id": 145,
        "name": "Product #78 - 9868",
        "sku": "SKU-144",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-78-9868",
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
      "wishlist_id": 39,
      "variant_id": 147,
      "quantity": 1,
      "remark": null,
      "variant": {
        "id": 147,
        "name": "Product #79 - 5944",
        "sku": "SKU-146",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-79-5944",
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
            "id": 68,
            "name": "Size-68",
            "presentation": "S",
            "option_type_name": "foo-size-68",
            "option_type_id": 68,
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
Authorizat IO N: Bearer 357b3473d1e4eab5fa35cab0808a59ab7ac0e2f95634ef82
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
ETag: W/&quot;855752c65137167a3e029651bb8fe977&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: a043e67f-2831-4a90-9a82-1d5cb70f913c
X-Runtime: 0.009264
Vary: Origin
Content-Length: 301
200 OK
```


```json
{
  "wished_products": [
    {
      "id": 25,
      "wishlist_id": 38,
      "variant_id": 137,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 26,
      "wishlist_id": 38,
      "variant_id": 139,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 27,
      "wishlist_id": 38,
      "variant_id": 141,
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
PATCH /api/wished_products/22
Accept: application/json
Authorizat IO N: Bearer aa5058e6ec68a3cd1092e54f3eba528c47feb209a6b8ff98
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/wished_products/:id`

#### Parameters


```json
wished_product[wishlist_id]=37&wished_product[variant_id]=135&wished_product[quantity]=2&wished_product[remark]=Foo+bar
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
ETag: W/&quot;694221ca1f5c76f9f3bdeb1ed81cd3ab&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: f3e32bbf-621c-438a-a34a-48a84c82e23d
X-Runtime: 0.011618
Vary: Origin
Content-Length: 75
200 OK
```


```json
{
  "id": 22,
  "wishlist_id": 37,
  "variant_id": 135,
  "quantity": 2,
  "remark": "Foo bar"
}
```



# Wishlists

Get a user's default wishlist. This will create a default wishlist if one does not exist.

## Create a wishlist


### Request

#### Endpoint

```plaintext
POST /api/wishlists
Accept: application/json
Authorizat IO N: Bearer e88a43b778e66e0baf69921c5a8645add66edf445835c469
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/wishlists`

#### Parameters


```json
wishlist[name]&wishlist[user_id]=63&wishlist[is_default]=true&wishlist[is_public]=false
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
ETag: W/&quot;0cea04f0addd5b0b3c3ebd76d6f35d38&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: ff1db8a7-4177-4f37-8a1f-5f9ba78dac3d
X-Runtime: 0.010766
Vary: Origin
Content-Length: 100
201 Created
```


```json
{
  "id": 15,
  "user_id": 63,
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
DELETE /api/wishlists/28
Accept: application/json
Authorizat IO N: Bearer 4e62b70f3114164a5e3429def9cda63d8986cd990f785620
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
X-Request-Id: 4304d930-dbe8-41a3-8e3a-ffce9ce70c03
X-Runtime: 0.011312
Vary: Origin
204 No Content
```




## Get a single wishlist


### Request

#### Endpoint

```plaintext
GET /api/wishlists/17
Accept: application/json
Authorizat IO N: Bearer 2cf07774211f651aa8fe3537f496017198f0dd3976c15831
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
ETag: W/&quot;e25a5eef4c1da485d7d623d7fb506b4c&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 20d348c9-06da-47a5-8f64-0f071475ab1c
X-Runtime: 0.009168
Vary: Origin
Content-Length: 309
200 OK
```


```json
{
  "id": 17,
  "user_id": 65,
  "name": "Wishlist #16",
  "is_public": false,
  "is_default": true,
  "wished_products": [
    {
      "id": 7,
      "wishlist_id": 17,
      "variant_id": 99,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 8,
      "wishlist_id": 17,
      "variant_id": 101,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 9,
      "wishlist_id": 17,
      "variant_id": 103,
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
Authorizat IO N: Bearer 1ea57b7cacfd4acf16e7a771512cf3edb8866198f3e42467
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
ETag: W/&quot;12525de0609f80155ed20a79da74cceb&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: ec785870-b0ce-4715-bdc2-bb497fcae408
X-Runtime: 0.010388
Vary: Origin
Content-Length: 894
200 OK
```


```json
{
  "wishlists": [
    {
      "id": 18,
      "user_id": 66,
      "name": "Wishlist #17",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 19,
      "user_id": 67,
      "name": "Wishlist #18",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 20,
      "user_id": 68,
      "name": "Wishlist #19",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 21,
      "user_id": 69,
      "name": "Wishlist #20",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 22,
      "user_id": 70,
      "name": "Wishlist #21",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 23,
      "user_id": 71,
      "name": "Wishlist #22",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 24,
      "user_id": 72,
      "name": "Wishlist #23",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 25,
      "user_id": 73,
      "name": "Wishlist #24",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 26,
      "user_id": 74,
      "name": "Wishlist #25",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 27,
      "user_id": 75,
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
Authorizat IO N: Bearer 8a3e8e16f9ea9ad61711af912d96915c8d8d235a6d6a6c08
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
ETag: W/&quot;3029c2c0b857f07f89fe3199832fcff6&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 76279dc0-7b07-4a0e-aff3-3a5d636ec357
X-Runtime: 0.033209
Vary: Origin
Content-Length: 302
200 OK
```


```json
{
  "id": 1,
  "user_id": 60,
  "name": "Wishlist #1",
  "is_public": false,
  "is_default": true,
  "wished_products": [
    {
      "id": 1,
      "wishlist_id": 1,
      "variant_id": 87,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 2,
      "wishlist_id": 1,
      "variant_id": 89,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 3,
      "wishlist_id": 1,
      "variant_id": 91,
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
Authorizat IO N: Bearer 83d4a52848833c25c68141cd8f4f36283db38e6c442e700c
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
ETag: W/&quot;8791fa2d11c53ab6833f7e26f653774d&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 25bd6c9b-e1c7-41a1-82ad-cfe8c6234e37
X-Runtime: 0.009483
Vary: Origin
Content-Length: 893
200 OK
```


```json
{
  "wishlists": [
    {
      "id": 5,
      "user_id": 62,
      "name": "Wishlist #5",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 6,
      "user_id": 62,
      "name": "Wishlist #6",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 7,
      "user_id": 62,
      "name": "Wishlist #7",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 8,
      "user_id": 62,
      "name": "Wishlist #8",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 9,
      "user_id": 62,
      "name": "Wishlist #9",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 10,
      "user_id": 62,
      "name": "Wishlist #10",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 11,
      "user_id": 62,
      "name": "Wishlist #11",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 12,
      "user_id": 62,
      "name": "Wishlist #12",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 13,
      "user_id": 62,
      "name": "Wishlist #13",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 14,
      "user_id": 62,
      "name": "Wishlist #14",
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
Authorizat IO N: Bearer 80e8928bb335a15500afd089d757a541d7dcf050449712ca
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/wishlists/:id`

#### Parameters


```json
wishlist[name]=Another+Wishlist&wishlist[user_id]=64&wishlist[is_default]=true&wishlist[is_public]=false
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
ETag: W/&quot;fb2555555777664cb30d8af63e65b6ac&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 07a84d8a-76e7-40ab-b07a-7415a9c0a898
X-Runtime: 0.012629
Vary: Origin
Content-Length: 311
200 OK
```


```json
{
  "id": 16,
  "user_id": 64,
  "name": "Another Wishlist",
  "is_public": false,
  "is_default": true,
  "wished_products": [
    {
      "id": 4,
      "wishlist_id": 16,
      "variant_id": 93,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 5,
      "wishlist_id": 16,
      "variant_id": 95,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 6,
      "wishlist_id": 16,
      "variant_id": 97,
      "quantity": 1,
      "remark": null
    }
  ]
}
```



