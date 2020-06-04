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
PUT /api/orders/M829787486/addresses/26
Accept: application/json
X-Spree-Order-Token: uxmXknmU3If4wmmbVGPjHw
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
ETag: W/&quot;25202d8278a7b89af97253058b89d772&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 3792c5f9-c79d-4766-8e49-d8da8eea9905
X-Runtime: 0.070404
Vary: Origin
Content-Length: 507
200 OK
```


```json
{
  "id": 27,
  "firstname": "John the Tester",
  "lastname": null,
  "full_name": "John the Tester",
  "address1": "A Different Road",
  "address2": "Northwest",
  "city": "Herndon",
  "zipcode": "10026",
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
X-Spree-Order-Token: bMNMbeNZDd7vXjtEynvvbw
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/braintree/transactions`

#### Parameters


```json
order_id=M194042346&payment_method_id=19&options[restart_checkout]=true&transaction[email]=maryellen.oga%40mckenziemcglynn.com&transaction[nonce]=fake-paypal-billing-agreement-nonce&transaction[phone]=555-555-0199&transaction[shipping_address_attributes][first_name]=John&transaction[shipping_address_attributes][last_name]=Stamm&transaction[shipping_address_attributes][address_line_1]=A+Different+Road&transaction[shipping_address_attributes][city]=Herndon&transaction[shipping_address_attributes][state_code]=AL&transaction[shipping_address_attributes][zip]=10046&transaction[shipping_address_attributes][country_code]=US&transaction[payment_type]=PayPalAccount&transaction[billing_address_attributes][first_name]=John&transaction[billing_address_attributes][last_name]=Stamm&transaction[billing_address_attributes][address_line_1]=A+Different+Road&transaction[billing_address_attributes][city]=Herndon&transaction[billing_address_attributes][state_code]=AL&transaction[billing_address_attributes][zip]=10046&transaction[billing_address_attributes][country_code]=US
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
ETag: W/&quot;74d1a8efc747b7d089bd8ff93c02da1e&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 3b9698e7-cd81-4f5d-ae8d-5cdf9c4ce1e0
X-Runtime: 0.337342
Vary: Origin
Content-Length: 5300
200 OK
```


```json
{
  "id": 28,
  "number": "M194042346",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2020-06-04T11:40:19.360-04:00",
  "updated_at": "2020-06-04T11:40:19.662-04:00",
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
  "token": "bMNMbeNZDd7vXjtEynvvbw",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order?order=M194042346&bzip=10046&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [
    {
      "id": 19,
      "name": "Braintree"
    }
  ],
  "bill_address": {
    "id": 51,
    "firstname": "John",
    "lastname": "Stamm",
    "full_name": "John Stamm",
    "address1": "A Different Road",
    "address2": null,
    "city": "Herndon",
    "zipcode": "10046",
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
    "id": 52,
    "firstname": "John",
    "lastname": "Stamm",
    "full_name": "John Stamm",
    "address1": "A Different Road",
    "address2": null,
    "city": "Herndon",
    "zipcode": "10046",
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
      "id": 33,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 167,
      "vendor_id": 308,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 167,
        "name": "Product #89 - 8938",
        "sku": "SKU-166",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-89-8938",
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
      "vendor_name": "Vendor #308",
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
      "created_at": "2020-06-04T11:40:19.473-04:00",
      "updated_at": "2020-06-04T11:40:19.473-04:00",
      "payment_method": {
        "id": 19,
        "name": "Braintree"
      },
      "source": {
        "id": 7,
        "payment_type": "PayPalAccount",
        "token": "bgx899",
        "created_at": "2020-06-04T11:40:19.472-04:00",
        "email": "jane.doe@paypal.com"
      }
    }
  ],
  "shipments": [
    {
      "id": 32,
      "tracking": null,
      "tracking_url": null,
      "number": "H53776534376",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M194042346",
      "stock_location_name": "NY Warehouse 59",
      "giftwrappable": false,
      "stock_location_id": 59,
      "giftwrap": null,
      "shipping_rates": [
        {
          "id": 32,
          "name": "UPS Ground",
          "admin_name": null,
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 22,
          "shipping_method_code": "UPS_GROUND",
          "extra_cost": "",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 32,
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
              "id": 26,
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
      "stock_location_address": "NY Warehouse 59, Washington, AL",
      "country_iso": "US",
      "international_shipping": false,
      "delivery_estimation": "Jun 08"
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
X-Spree-Order-Token: 25gI33IqfOjguj0Gw_nueg
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/braintree/transactions`

#### Parameters


```json
order_id=M387305237&payment_method_id=18&options[restart_checkout]=true&transaction[email]=maryellen.oga%40mckenziemcglynn.com&transaction[nonce]=fake-apple-pay-visa-nonce&transaction[phone]=555-555-0199&transaction[shipping_address_attributes][first_name]=John&transaction[shipping_address_attributes][last_name]=Stamm&transaction[shipping_address_attributes][address_line_1]=A+Different+Road&transaction[shipping_address_attributes][city]=Herndon&transaction[shipping_address_attributes][state_code]=AL&transaction[shipping_address_attributes][zip]=10044&transaction[shipping_address_attributes][country_code]=US&transaction[payment_type]=ApplePayCard
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
ETag: W/&quot;ee707bcfded51cb36ef18306239337fe&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 16da6f4a-f2e4-4049-a3e2-d96ec8fd84df
X-Runtime: 0.375629
Vary: Origin
Content-Length: 5346
200 OK
```


```json
{
  "id": 27,
  "number": "M387305237",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2020-06-04T11:40:18.662-04:00",
  "updated_at": "2020-06-04T11:40:18.979-04:00",
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
  "token": "25gI33IqfOjguj0Gw_nueg",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order?order=M387305237&bzip=10044&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [
    {
      "id": 18,
      "name": "Braintree"
    }
  ],
  "bill_address": {
    "id": 47,
    "firstname": "John",
    "lastname": "Stamm",
    "full_name": "John Stamm",
    "address1": "A Different Road",
    "address2": null,
    "city": "Herndon",
    "zipcode": "10044",
    "phone": "555-555-0199",
    "company": null,
    "alternative_phone": null,
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
    "id": 48,
    "firstname": "John",
    "lastname": "Stamm",
    "full_name": "John Stamm",
    "address1": "A Different Road",
    "address2": null,
    "city": "Herndon",
    "zipcode": "10044",
    "phone": "555-555-0199",
    "company": null,
    "alternative_phone": null,
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
      "id": 32,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 165,
      "vendor_id": 303,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 165,
        "name": "Product #88 - 7615",
        "sku": "SKU-164",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-88-7615",
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
        "product_id": 88,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [

      ],
      "vendor_name": "Vendor #303",
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
      "created_at": "2020-06-04T11:40:18.799-04:00",
      "updated_at": "2020-06-04T11:40:18.799-04:00",
      "payment_method": {
        "id": 18,
        "name": "Braintree"
      },
      "source": {
        "id": 6,
        "payment_type": "ApplePayCard",
        "token": "cg7hsk",
        "created_at": "2020-06-04T11:40:18.798-04:00",
        "cc_type": "Apple Pay - Visa",
        "last_digits": "1881",
        "month": "12",
        "year": "2020"
      }
    }
  ],
  "shipments": [
    {
      "id": 30,
      "tracking": null,
      "tracking_url": null,
      "number": "H18288282872",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M387305237",
      "stock_location_name": "NY Warehouse 58",
      "giftwrappable": false,
      "stock_location_id": 58,
      "giftwrap": null,
      "shipping_rates": [
        {
          "id": 30,
          "name": "UPS Ground",
          "admin_name": null,
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 21,
          "shipping_method_code": "UPS_GROUND",
          "extra_cost": "",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 30,
        "name": "UPS Ground",
        "admin_name": null,
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 21,
        "shipping_method_code": "UPS_GROUND",
        "extra_cost": "",
        "is_flat_rate": false,
        "is_flat_rate_expedited": false,
        "is_free_shipping": false,
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 21,
          "code": "UPS_GROUND",
          "name": "UPS Ground",
          "zones": [
            {
              "id": 25,
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
          "variant_id": 165,
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
      "delivery_estimation": "Jun 08"
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
PUT /api/checkouts/M928032145/complete
Accept: application/json
X-Spree-Order-Token: h5XVLartrosAVTpxZlGhKw
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
ETag: W/&quot;c3384ea28991c621cf4c6f67b17f6f90&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 2bc425a1-7540-4668-88ab-ca93ad17bc8a
X-Runtime: 0.396295
Vary: Origin
Content-Length: 5397
200 OK
```


```json
{
  "id": 22,
  "number": "M928032145",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "complete",
  "adjustment_total": "0.0",
  "user_id": 56,
  "created_at": "2020-06-04T11:40:09.635-04:00",
  "updated_at": "2020-06-04T11:40:10.050-04:00",
  "completed_at": "2020-06-04T11:40:10.050-04:00",
  "payment_total": "110.0",
  "shipment_state": "ready",
  "payment_state": "paid",
  "email": "email54@example.com",
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
  "token": "h5XVLartrosAVTpxZlGhKw",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order?order=M928032145&bzip=10034&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [
    {
      "id": 12,
      "name": "Braintree"
    },
    {
      "id": 13,
      "name": "Braintree"
    }
  ],
  "bill_address": {
    "id": 35,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "PO Box 1337",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10034",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 34,
    "country_iso": "US",
    "state_id": 34,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 34,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 34,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 34
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
    "zipcode": "10035",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 34,
    "country_iso": "US",
    "state_id": 34,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 34,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 34,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 34
    }
  },
  "line_items": [
    {
      "id": 27,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 91,
      "vendor_id": 203,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 91,
        "name": "Product #51 - 6186",
        "sku": "SKU-90",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-51-6186",
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
            "id": 40,
            "name": "Size-40",
            "presentation": "S",
            "option_type_name": "foo-size-40",
            "option_type_id": 40,
            "option_type_presentation": "Size",
            "position": 1
          }
        ],
        "images": [

        ],
        "product_id": 51,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [

      ],
      "vendor_name": "Vendor #203",
      "country_iso": "US",
      "adjustments": [

      ]
    }
  ],
  "payments": [
    {
      "id": 5,
      "source_type": "SolidusPaypalBraintree::Source",
      "source_id": 4,
      "amount": "110.0",
      "display_amount": "$110.00",
      "payment_method_id": 12,
      "state": "completed",
      "avs_response": "M",
      "created_at": "2020-06-04T11:40:09.734-04:00",
      "updated_at": "2020-06-04T11:40:09.887-04:00",
      "payment_method": {
        "id": 12,
        "name": "Braintree"
      },
      "source": {
        "id": 4,
        "payment_type": "CreditCard",
        "token": "4rptfz",
        "created_at": "2020-06-04T11:40:09.733-04:00",
        "cc_type": "Visa",
        "last_digits": "1881",
        "month": "12",
        "year": "2020"
      }
    }
  ],
  "shipments": [
    {
      "id": 20,
      "tracking": "U10000",
      "tracking_url": null,
      "number": "H31611347161",
      "cost": "100.0",
      "shipped_at": null,
      "state": "ready",
      "order_id": "M928032145",
      "stock_location_name": "NY Warehouse 42",
      "giftwrappable": false,
      "stock_location_id": 42,
      "giftwrap": null,
      "shipping_rates": [
        {
          "id": 20,
          "name": "UPS Ground",
          "admin_name": null,
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 16,
          "shipping_method_code": "UPS_GROUND",
          "extra_cost": "",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 20,
        "name": "UPS Ground",
        "admin_name": null,
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 16,
        "shipping_method_code": "UPS_GROUND",
        "extra_cost": "",
        "is_flat_rate": false,
        "is_flat_rate_expedited": false,
        "is_free_shipping": false,
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 16,
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
          "variant_id": 91,
          "quantity": 1,
          "states": {
            "on_hand": 1
          }
        }
      ],
      "adjustments": [

      ],
      "stock_location_address": "NY Warehouse 42, Washington, AL",
      "country_iso": "US",
      "international_shipping": false,
      "delivery_estimation": "Jun 08"
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
PATCH /api/checkouts/M234757640
Accept: application/json
X-Spree-Order-Token: C4v2dK-WIlbhrMb6CJyM2Q
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=16&order[payment_attributes][][source_attributes][nonce]=fake-apple-pay-visa-nonce&order[payment_attributes][][source_attributes][payment_type]=ApplePayCard&order[payment_attributes][][source_attributes][reusable]=true
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
ETag: W/&quot;24650ba7400197979d00f2e7e61d638d&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 8c44ac27-53cf-4ca3-bd7e-84e884c48d42
X-Runtime: 0.136666
Vary: Origin
Content-Length: 4849
200 OK
```


```json
{
  "id": 25,
  "number": "M234757640",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 59,
  "created_at": "2020-06-04T11:40:12.045-04:00",
  "updated_at": "2020-06-04T11:40:12.363-04:00",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "email57@example.com",
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
  "token": "C4v2dK-WIlbhrMb6CJyM2Q",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order?order=M234757640&bzip=10040&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [
    {
      "id": 16,
      "name": "Braintree"
    }
  ],
  "bill_address": {
    "id": 41,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "PO Box 1337",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10040",
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
    "id": 42,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "A Different Road",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10041",
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
      "id": 30,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 97,
      "vendor_id": 218,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 97,
        "name": "Product #54 - 5514",
        "sku": "SKU-96",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-54-5514",
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
      "vendor_name": "Vendor #218",
      "country_iso": "US",
      "adjustments": [

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
      "number": "H88758776354",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M234757640",
      "stock_location_name": "NY Warehouse 45",
      "giftwrappable": false,
      "stock_location_id": 45,
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
          "extra_cost": "",
          "display_cost": "$100.00"
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
              "id": 23,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 35,
              "name": "ShippingCategory #33"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 97,
          "quantity": 1,
          "states": {
            "on_hand": 1
          }
        }
      ],
      "adjustments": [

      ],
      "stock_location_address": "NY Warehouse 45, Washington, AL",
      "country_iso": "US",
      "international_shipping": false,
      "delivery_estimation": "Jun 08"
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
PATCH /api/checkouts/M859796366
Accept: application/json
X-Spree-Order-Token: -3q26iWqfbVS2Vx8SXQbFw
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=15&order[payment_attributes][][source_attributes][nonce]=fake-paypal-billing-agreement-nonce&order[payment_attributes][][source_attributes][payment_type]=PayPalAccount&order[payment_attributes][][source_attributes][reusable]=true
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
ETag: W/&quot;fdca7e71af6210126a3c67e0d37c0561&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: fead5d9c-67e1-4251-9fb9-b438c4f27e51
X-Runtime: 0.157574
Vary: Origin
Content-Length: 4849
200 OK
```


```json
{
  "id": 24,
  "number": "M859796366",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 58,
  "created_at": "2020-06-04T11:40:11.159-04:00",
  "updated_at": "2020-06-04T11:40:11.673-04:00",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "email56@example.com",
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
  "token": "-3q26iWqfbVS2Vx8SXQbFw",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order?order=M859796366&bzip=10038&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [
    {
      "id": 15,
      "name": "Braintree"
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
    "zipcode": "10038",
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
  },
  "ship_address": {
    "id": 40,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "A Different Road",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10039",
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
  },
  "line_items": [
    {
      "id": 29,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 95,
      "vendor_id": 213,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 95,
        "name": "Product #53 - 4878",
        "sku": "SKU-94",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-53-4878",
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
            "id": 42,
            "name": "Size-42",
            "presentation": "S",
            "option_type_name": "foo-size-42",
            "option_type_id": 42,
            "option_type_presentation": "Size",
            "position": 1
          }
        ],
        "images": [

        ],
        "product_id": 53,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [

      ],
      "vendor_name": "Vendor #213",
      "country_iso": "US",
      "adjustments": [

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
      "number": "H65143410155",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M859796366",
      "stock_location_name": "NY Warehouse 44",
      "giftwrappable": false,
      "stock_location_id": 44,
      "giftwrap": null,
      "shipping_rates": [
        {
          "id": 24,
          "name": "UPS Ground",
          "admin_name": null,
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 18,
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
        "shipping_method_id": 18,
        "shipping_method_code": "UPS_GROUND",
        "extra_cost": "",
        "is_flat_rate": false,
        "is_flat_rate_expedited": false,
        "is_free_shipping": false,
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 18,
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
              "id": 34,
              "name": "ShippingCategory #32"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 95,
          "quantity": 1,
          "states": {
            "on_hand": 1
          }
        }
      ],
      "adjustments": [

      ],
      "stock_location_address": "NY Warehouse 44, Washington, AL",
      "country_iso": "US",
      "international_shipping": false,
      "delivery_estimation": "Jun 08"
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
PATCH /api/checkouts/M718569721
Accept: application/json
X-Spree-Order-Token: O0MY_gJTc_uS6xwsw4wKqQ
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=14&order[payment_attributes][][source_attributes][nonce]=fake-valid-visa-nonce&order[payment_attributes][][source_attributes][payment_type]=CreditCard&order[payment_attributes][][source_attributes][reusable]=true
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
ETag: W/&quot;a86081e1261b19a5f5ee4325846c15fd&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 5d03c846-c60c-45ee-a5c7-782dba97cbbf
X-Runtime: 0.161436
Vary: Origin
Content-Length: 4849
200 OK
```


```json
{
  "id": 23,
  "number": "M718569721",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 57,
  "created_at": "2020-06-04T11:40:10.439-04:00",
  "updated_at": "2020-06-04T11:40:10.749-04:00",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "email55@example.com",
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
  "token": "O0MY_gJTc_uS6xwsw4wKqQ",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order?order=M718569721&bzip=10036&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [
    {
      "id": 14,
      "name": "Braintree"
    }
  ],
  "bill_address": {
    "id": 37,
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
    "country_id": 35,
    "country_iso": "US",
    "state_id": 35,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 35,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 35,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 35
    }
  },
  "ship_address": {
    "id": 38,
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
    "country_id": 35,
    "country_iso": "US",
    "state_id": 35,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 35,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 35,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 35
    }
  },
  "line_items": [
    {
      "id": 28,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 93,
      "vendor_id": 208,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 93,
        "name": "Product #52 - 9662",
        "sku": "SKU-92",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-52-9662",
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
            "id": 41,
            "name": "Size-41",
            "presentation": "S",
            "option_type_name": "foo-size-41",
            "option_type_id": 41,
            "option_type_presentation": "Size",
            "position": 1
          }
        ],
        "images": [

        ],
        "product_id": 52,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [

      ],
      "vendor_name": "Vendor #208",
      "country_iso": "US",
      "adjustments": [

      ]
    }
  ],
  "payments": [

  ],
  "shipments": [
    {
      "id": 22,
      "tracking": null,
      "tracking_url": null,
      "number": "H21086422556",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M718569721",
      "stock_location_name": "NY Warehouse 43",
      "giftwrappable": false,
      "stock_location_id": 43,
      "giftwrap": null,
      "shipping_rates": [
        {
          "id": 22,
          "name": "UPS Ground",
          "admin_name": null,
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 17,
          "shipping_method_code": "UPS_GROUND",
          "extra_cost": "",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 22,
        "name": "UPS Ground",
        "admin_name": null,
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 17,
        "shipping_method_code": "UPS_GROUND",
        "extra_cost": "",
        "is_flat_rate": false,
        "is_flat_rate_expedited": false,
        "is_free_shipping": false,
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 17,
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
              "id": 33,
              "name": "ShippingCategory #31"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 93,
          "quantity": 1,
          "states": {
            "on_hand": 1
          }
        }
      ],
      "adjustments": [

      ],
      "stock_location_address": "NY Warehouse 43, Washington, AL",
      "country_iso": "US",
      "international_shipping": false,
      "delivery_estimation": "Jun 08"
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
PATCH /api/checkouts/M858209397
Accept: application/json
X-Spree-Order-Token: m01mJgYTQFFGcwZPzFvphA
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=17&order[payment_attributes][][source_attributes][wallet_payment_source_id]=5
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
ETag: W/&quot;c1e19141a997ca69f6beb43c83657fe0&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: d945c53b-c4de-4607-b715-75228974ac14
X-Runtime: 0.137113
Vary: Origin
Content-Length: 4849
200 OK
```


```json
{
  "id": 26,
  "number": "M858209397",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 60,
  "created_at": "2020-06-04T11:40:12.730-04:00",
  "updated_at": "2020-06-04T11:40:13.072-04:00",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "email58@example.com",
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
  "token": "m01mJgYTQFFGcwZPzFvphA",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order?order=M858209397&bzip=10042&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [
    {
      "id": 17,
      "name": "Braintree"
    }
  ],
  "bill_address": {
    "id": 43,
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
    "country_id": 38,
    "country_iso": "US",
    "state_id": 38,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 38,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 38,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 38
    }
  },
  "ship_address": {
    "id": 44,
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
    "country_id": 38,
    "country_iso": "US",
    "state_id": 38,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 38,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 38,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 38
    }
  },
  "line_items": [
    {
      "id": 31,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 99,
      "vendor_id": 223,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 99,
        "name": "Product #55 - 2293",
        "sku": "SKU-98",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-55-2293",
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
        "product_id": 55,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [

      ],
      "vendor_name": "Vendor #223",
      "country_iso": "US",
      "adjustments": [

      ]
    }
  ],
  "payments": [

  ],
  "shipments": [
    {
      "id": 28,
      "tracking": null,
      "tracking_url": null,
      "number": "H63781022435",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M858209397",
      "stock_location_name": "NY Warehouse 46",
      "giftwrappable": false,
      "stock_location_id": 46,
      "giftwrap": null,
      "shipping_rates": [
        {
          "id": 28,
          "name": "UPS Ground",
          "admin_name": null,
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 20,
          "shipping_method_code": "UPS_GROUND",
          "extra_cost": "",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 28,
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
              "id": 24,
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
          "variant_id": 99,
          "quantity": 1,
          "states": {
            "on_hand": 1
          }
        }
      ],
      "adjustments": [

      ],
      "stock_location_address": "NY Warehouse 46, Washington, AL",
      "country_iso": "US",
      "international_shipping": false,
      "delivery_estimation": "Jun 08"
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
PUT /api/checkouts/M860450317
Accept: application/json
X-Spree-Order-Token: 8dKI4Od54iM2jLem9Saq2A
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PUT /api/checkouts/:id`

#### Parameters


```json
order[ship_address_attributes][id]&order[ship_address_attributes][firstname]=John&order[ship_address_attributes][lastname]&order[ship_address_attributes][address1]=10+Lovely+Street&order[ship_address_attributes][address2]=Northwest&order[ship_address_attributes][city]=Herndon&order[ship_address_attributes][zipcode]=10033&order[ship_address_attributes][phone]=555-555-0199&order[ship_address_attributes][state_name]&order[ship_address_attributes][alternative_phone]=555-555-0199&order[ship_address_attributes][company]=Company&order[ship_address_attributes][state_id]=33&order[ship_address_attributes][country_id]=33&order[ship_address_attributes][created_at]&order[ship_address_attributes][updated_at]&order[use_billing]=true&hold_state=true
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
ETag: W/&quot;796876d7cd0ab789f552ccfdef61c95f&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: d5238a06-fdc7-4aed-a624-82ac84e0b125
X-Runtime: 0.149567
Vary: Origin
Content-Length: 4823
200 OK
```


```json
{
  "id": 21,
  "number": "M860450317",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "cart",
  "adjustment_total": "0.0",
  "user_id": 55,
  "created_at": "2020-06-04T11:40:09.137-04:00",
  "updated_at": "2020-06-04T11:40:09.246-04:00",
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
  "token": "8dKI4Od54iM2jLem9Saq2A",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order?order=M860450317&bzip=10033&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [

  ],
  "bill_address": {
    "id": 34,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "10 Lovely Street",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10033",
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
    "id": 34,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "10 Lovely Street",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10033",
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
      "id": 26,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 89,
      "vendor_id": 198,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 89,
        "name": "Product #50 - 2674",
        "sku": "SKU-88",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-50-2674",
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
            "id": 39,
            "name": "Size-39",
            "presentation": "S",
            "option_type_name": "foo-size-39",
            "option_type_id": 39,
            "option_type_presentation": "Size",
            "position": 1
          }
        ],
        "images": [

        ],
        "product_id": 50,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [

      ],
      "vendor_name": "Vendor #198",
      "country_iso": "US",
      "adjustments": [

      ]
    }
  ],
  "payments": [

  ],
  "shipments": [
    {
      "id": 19,
      "tracking": "U10000",
      "tracking_url": null,
      "number": "H21781036781",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M860450317",
      "stock_location_name": "NY Warehouse 41",
      "giftwrappable": false,
      "stock_location_id": 41,
      "giftwrap": null,
      "shipping_rates": [
        {
          "id": 19,
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
        "id": 19,
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
              "id": 19,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 31,
              "name": "ShippingCategory #29"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 89,
          "quantity": 1,
          "states": {
            "on_hand": 1
          }
        }
      ],
      "adjustments": [

      ],
      "stock_location_address": "NY Warehouse 41, Washington, AL",
      "country_iso": "US",
      "international_shipping": false,
      "delivery_estimation": "Jun 08"
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
POST /api/shipments/H14817861625/giftwrap
Accept: application/json
X-Spree-Order-Token: ybEYKBZZ2tgVU7ZGr8LulQ
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/shipments/:shipment_number/giftwrap`

#### Parameters


```json
order_number=M009428798
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
X-Request-Id: 6f8d4101-c5fc-4b29-b18f-51e7dc33b682
X-Runtime: 0.043696
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
DELETE /api/shipments/H34245580416/giftwrap
Accept: application/json
X-Spree-Order-Token: Ue7nZ9fkSiDjmpYE7nu5hQ
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`DELETE /api/shipments/:shipment_number/giftwrap`

#### Parameters


```json
order_number=M312755007
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
X-Request-Id: 0fdf2c7b-af1d-4920-bc73-19fd0ffbb97b
X-Runtime: 0.043470
Vary: Origin
204 No Content
```




# LineItem

Representation of a single cart item for a specific variant with price of vendor

## Creating a line item


### Request

#### Endpoint

```plaintext
POST /api/orders/M618667325/line_items
Accept: application/json
X-Spree-Order-Token: lxldN1VOji5jlgsU-RSphQ
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/:order_number/line_items`

#### Parameters


```json
line_item[variant_id]=16&line_item[options][vendor_id]=29
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
ETag: W/&quot;19cac61ed2c1e1d755964ad539f66eba&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 5130cb75-d695-4300-9253-abf7ca4c4e94
X-Runtime: 0.142937
Vary: Origin
Content-Length: 929
201 Created
```


```json
{
  "id": 6,
  "quantity": 1,
  "price": "19.99",
  "variant_id": 16,
  "vendor_id": 29,
  "single_display_amount": "$19.99",
  "display_amount": "$19.99",
  "total": "19.99",
  "on_sale": false,
  "final_sale": false,
  "backordered": null,
  "promotionable": true,
  "variant": {
    "id": 16,
    "name": "Product #8 - 9958",
    "sku": "SKU-15",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": false,
    "slug": "product-8-9958",
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
        "id": 8,
        "name": "Size-8",
        "presentation": "S",
        "option_type_name": "foo-size-8",
        "option_type_id": 8,
        "option_type_presentation": "Size",
        "position": 1
      }
    ],
    "images": [

    ],
    "product_id": 8,
    "lead_time": 2,
    "brand": null,
    "brand_slug": null,
    "brand_description": null
  },
  "monogram": null,
  "gift_cards": [

  ],
  "vendor_name": "Vendor #29",
  "country_iso": null,
  "adjustments": [

  ]
}
```



## Creating a line item gift card


### Request

#### Endpoint

```plaintext
POST /api/orders/M019406968/line_items
Accept: application/json
X-Spree-Order-Token: M9WU6vF0JIDvKRC0rzozRg
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/:order_number/line_items`

#### Parameters


```json
line_item[variant_id]=8&line_item[options][vendor_id]=15&line_item[options][gift_card_details][recipient_name]=Recipient+John&line_item[options][gift_card_details][recipient_email]=recipient%40email.com&line_item[options][gift_card_details][purchaser_name]=Purchaser+Bob&line_item[options][gift_card_details][gift_message]=Surprise&line_item[options][gift_card_details][send_email_at]=2020-06-04+11%3A39%3A51+-0400
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
ETag: W/&quot;ae0260525d4c152e9fe1be9b405fb054&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: c0daefcf-88cd-4008-a9a5-752ee2a4c03a
X-Runtime: 0.262341
Vary: Origin
Content-Length: 1062
201 Created
```


```json
{
  "id": 3,
  "quantity": 1,
  "price": "19.99",
  "variant_id": 8,
  "vendor_id": 15,
  "single_display_amount": "$19.99",
  "display_amount": "$19.99",
  "total": "19.99",
  "on_sale": false,
  "final_sale": false,
  "backordered": null,
  "promotionable": true,
  "variant": {
    "id": 8,
    "name": "Product #3 - 6859",
    "sku": "SKU-8",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": false,
    "slug": "product-3-6859",
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
    "product_id": 3,
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
      "send_email_at": "2020-06-04T00:00:00.000-04:00"
    }
  ],
  "vendor_name": "Vendor #15",
  "country_iso": null,
  "adjustments": [

  ]
}
```



## Deleting a line item


### Request

#### Endpoint

```plaintext
DELETE /api/orders/M718075019/line_items/1
Accept: application/json
X-Spree-Order-Token: wu7K4bFhKEhWpLHnPw4lwQ
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
X-Request-Id: 94b138d0-a34b-4fcb-b734-f8bd96e1e929
X-Runtime: 0.175537
Vary: Origin
204 No Content
```




## Updating a line item


### Request

#### Endpoint

```plaintext
PUT /api/orders/M922370651/line_items/4
Accept: application/json
X-Spree-Order-Token: PUKPZUU19WkcWlTE-vcpEw
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
ETag: W/&quot;548460e5ba2a282576fc82cf9000de4c&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: eb55b860-c922-4eb7-8e1d-e29c2f32e04c
X-Runtime: 0.120125
Vary: Origin
Content-Length: 925
200 OK
```


```json
{
  "id": 4,
  "quantity": 2,
  "price": "10.0",
  "variant_id": 10,
  "vendor_id": 18,
  "single_display_amount": "$10.00",
  "display_amount": "$20.00",
  "total": "20.0",
  "on_sale": false,
  "final_sale": false,
  "backordered": null,
  "promotionable": true,
  "variant": {
    "id": 10,
    "name": "Product #5 - 9789",
    "sku": "SKU-9",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": false,
    "slug": "product-5-9789",
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
  "vendor_name": "Vendor #18",
  "country_iso": "US",
  "adjustments": [

  ]
}
```



# Minis

Create a mini. Any user can create a mini of their own, admins can create minis for other users.

## Create a mini


### Request

#### Endpoint

```plaintext
POST /api/minis
Accept: application/json
Authorizat IO N: Bearer 2a179d6efd70d0b404ce2c4b135048a241ca8c622bcffe7c
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/minis`

#### Parameters


```json
mini[name]=Winny&mini[user_id]=1&mini[birth_year]=2019&mini[birth_month]=1&mini[birth_day]=1
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
ETag: W/&quot;83bfabb32acca65bd859bcbebd668b07&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: a0a656fb-cbdd-478b-89ab-7e6bd6de1974
X-Runtime: 0.345035
Vary: Origin
Content-Length: 161
201 Created
```


```json
{
  "id": 1,
  "user_id": 1,
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
Authorizat IO N: Bearer 019c013d6b0883c5628519273bd8ba7ae98b1e5de397d092
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
X-Request-Id: 5a08ca97-fd77-406b-af0d-4402366ad445
X-Runtime: 0.007951
Vary: Origin
204 No Content
```




## Get a single mini


### Request

#### Endpoint

```plaintext
GET /api/minis/12
Accept: application/json
Authorizat IO N: Bearer c2a9b2f9ed97901e6ebb5ca32689409b25ef9bdb35a2c168
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
ETag: W/&quot;bdf902b27d843c43618a86eb04ba7687&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 6f162d19-6984-4ed6-8abc-72d6f0e13dd9
X-Runtime: 0.012567
Vary: Origin
Content-Length: 162
200 OK
```


```json
{
  "id": 12,
  "user_id": 13,
  "name": "Mini",
  "birth_year": 2020,
  "birth_month": 6,
  "birth_day": 3,
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
Authorizat IO N: Bearer 552de3e33acf87c574b2d1947daef0d83ddbc978f64def0e
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
ETag: W/&quot;5b499524af73c7e9dbb7a2928c8568c9&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 54ef79cc-a12a-4d1c-a28f-9cc1507d236a
X-Runtime: 0.042179
Vary: Origin
Content-Length: 1694
200 OK
```


```json
{
  "minis": [
    {
      "id": 11,
      "user_id": 11,
      "name": "Mini",
      "birth_year": 2020,
      "birth_month": 6,
      "birth_day": 3,
      "gender_boy": true,
      "gender_girl": true,
      "gender_taxons": [

      ],
      "age_range_taxons": [

      ]
    },
    {
      "id": 10,
      "user_id": 10,
      "name": "Mini",
      "birth_year": 2020,
      "birth_month": 6,
      "birth_day": 3,
      "gender_boy": true,
      "gender_girl": true,
      "gender_taxons": [

      ],
      "age_range_taxons": [

      ]
    },
    {
      "id": 9,
      "user_id": 9,
      "name": "Mini",
      "birth_year": 2020,
      "birth_month": 6,
      "birth_day": 3,
      "gender_boy": true,
      "gender_girl": true,
      "gender_taxons": [

      ],
      "age_range_taxons": [

      ]
    },
    {
      "id": 8,
      "user_id": 8,
      "name": "Mini",
      "birth_year": 2020,
      "birth_month": 6,
      "birth_day": 3,
      "gender_boy": true,
      "gender_girl": true,
      "gender_taxons": [

      ],
      "age_range_taxons": [

      ]
    },
    {
      "id": 7,
      "user_id": 7,
      "name": "Mini",
      "birth_year": 2020,
      "birth_month": 6,
      "birth_day": 3,
      "gender_boy": true,
      "gender_girl": true,
      "gender_taxons": [

      ],
      "age_range_taxons": [

      ]
    },
    {
      "id": 6,
      "user_id": 6,
      "name": "Mini",
      "birth_year": 2020,
      "birth_month": 6,
      "birth_day": 3,
      "gender_boy": true,
      "gender_girl": true,
      "gender_taxons": [

      ],
      "age_range_taxons": [

      ]
    },
    {
      "id": 5,
      "user_id": 5,
      "name": "Mini",
      "birth_year": 2020,
      "birth_month": 6,
      "birth_day": 3,
      "gender_boy": true,
      "gender_girl": true,
      "gender_taxons": [

      ],
      "age_range_taxons": [

      ]
    },
    {
      "id": 4,
      "user_id": 4,
      "name": "Mini",
      "birth_year": 2020,
      "birth_month": 6,
      "birth_day": 3,
      "gender_boy": true,
      "gender_girl": true,
      "gender_taxons": [

      ],
      "age_range_taxons": [

      ]
    },
    {
      "id": 3,
      "user_id": 3,
      "name": "Mini",
      "birth_year": 2020,
      "birth_month": 6,
      "birth_day": 3,
      "gender_boy": true,
      "gender_girl": true,
      "gender_taxons": [

      ],
      "age_range_taxons": [

      ]
    },
    {
      "id": 2,
      "user_id": 2,
      "name": "Mini",
      "birth_year": 2020,
      "birth_month": 6,
      "birth_day": 3,
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
Authorizat IO N: Bearer c956d65b2ce37b27d0d52a19c38941d3537aa886df5ba910
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
ETag: W/&quot;3719a35ee3add912d3a509dada0ae648&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: eedab63a-eccb-42c4-bf65-0783c5d5bd67
X-Runtime: 0.016248
Vary: Origin
Content-Length: 404
200 OK
```


```json
{
  "minis": [
    {
      "id": 18,
      "user_id": 16,
      "name": "Mini",
      "birth_year": 2020,
      "birth_month": 6,
      "birth_day": 3,
      "gender_boy": true,
      "gender_girl": true,
      "gender_taxons": [

      ],
      "age_range_taxons": [

      ]
    },
    {
      "id": 17,
      "user_id": 16,
      "name": "Mini",
      "birth_year": 2020,
      "birth_month": 6,
      "birth_day": 3,
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
PATCH /api/minis/13
Accept: application/json
Authorizat IO N: Bearer 262c3ac2512fa8212b0a752e1159c613bd03fc7d33d8eea0
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
ETag: W/&quot;7e0c0b2c5107ff34e8bbb3be90d8e017&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 0b4cc160-7533-43d1-8102-cef803c176ec
X-Runtime: 0.013928
Vary: Origin
Content-Length: 163
200 OK
```


```json
{
  "id": 13,
  "user_id": 14,
  "name": "Marge",
  "birth_year": 2020,
  "birth_month": 6,
  "birth_day": 3,
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
user_id&order_token&line_item[variant_id]=79&line_item[quantity]=1&line_item[vendor_id]=166&line_item[gift_card_details_attributes][recipient_name]=Recipient+John&line_item[gift_card_details_attributes][recipient_email]=recipient%40email.com&line_item[gift_card_details_attributes][purchaser_name]=Purchaser+Bob&line_item[gift_card_details_attributes][gift_message]=Surprise&line_item[gift_card_details_attributes][send_email_at]=2020-06-04
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
ETag: W/&quot;7854e9a5bcebadd59b7982802ae536c6&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: ab218a36-39e7-43be-a150-f84fa3571e71
X-Runtime: 0.132714
Vary: Origin
Content-Length: 2875
200 OK
```


```json
{
  "id": 17,
  "number": "M627699111",
  "item_total": "19.99",
  "total": "19.99",
  "ship_total": "0.0",
  "state": "cart",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2020-06-04T11:40:05.409-04:00",
  "updated_at": "2020-06-04T11:40:05.461-04:00",
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
  "token": "RrIdxqSwED3__ovwdATnVA",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order?order=M627699111&bzip=&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [

  ],
  "bill_address": null,
  "ship_address": null,
  "line_items": [
    {
      "id": 23,
      "quantity": 1,
      "price": "19.99",
      "variant_id": 79,
      "vendor_id": 166,
      "single_display_amount": "$19.99",
      "display_amount": "$19.99",
      "total": "19.99",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 79,
        "name": "Product #44 - 8454",
        "sku": "SKU-79",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-44-8454",
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
        "product_id": 44,
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
          "send_email_at": "2020-06-04T00:00:00.000-04:00"
        }
      ],
      "vendor_name": "Vendor #166",
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
user_id&order_token&line_item[variant_id]=59&line_item[quantity]=2&line_item[vendor_id]=125
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
ETag: W/&quot;bafa833017a5830f78ba933c715f2f9e&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 8237ce06-240a-4a4c-b4dc-0bb3ba1c4353
X-Runtime: 0.110252
Vary: Origin
Content-Length: 2691
200 OK
```


```json
{
  "id": 12,
  "number": "M651520676",
  "item_total": "39.98",
  "total": "39.98",
  "ship_total": "0.0",
  "state": "cart",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2020-06-04T11:40:02.814-04:00",
  "updated_at": "2020-06-04T11:40:02.859-04:00",
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
  "token": "nFnmafOz16BEz4pTUidXdA",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order?order=M651520676&bzip=&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [

  ],
  "bill_address": null,
  "ship_address": null,
  "line_items": [
    {
      "id": 17,
      "quantity": 2,
      "price": "19.99",
      "variant_id": 59,
      "vendor_id": 125,
      "single_display_amount": "$19.99",
      "display_amount": "$39.98",
      "total": "39.98",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 59,
        "name": "Product #35 - 787",
        "sku": "SKU-58",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-35-787",
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
      "vendor_name": "Vendor #125",
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
user_id&order_token&line_item[variant_id]=71&line_item[quantity]=2&line_item[vendor_id]=147
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
ETag: W/&quot;1f72615aa5a98fde90921c26cd5cb135&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 823e09ae-5753-4912-bb38-626da67ffa1e
X-Runtime: 0.102203
Vary: Origin
Content-Length: 2693
200 OK
```


```json
{
  "id": 15,
  "number": "M770759787",
  "item_total": "39.98",
  "total": "39.98",
  "ship_total": "0.0",
  "state": "cart",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2020-06-04T11:40:04.478-04:00",
  "updated_at": "2020-06-04T11:40:04.518-04:00",
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
  "token": "_YN9l3ODWDO9CejuBcTc9Q",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order?order=M770759787&bzip=&init=true",
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
      "variant_id": 71,
      "vendor_id": 147,
      "single_display_amount": "$19.99",
      "display_amount": "$39.98",
      "total": "39.98",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 71,
        "name": "Product #41 - 1759",
        "sku": "SKU-70",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-41-1759",
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
        "product_id": 41,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [

      ],
      "vendor_name": "Vendor #147",
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
Authorizat IO N: Bearer 3cb0fa2285105e70e0f2dc4d0b9b419546c0ca102f5a0c3e
X-Spree-Order-Token: 
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/cart`

#### Parameters


```json
user_id&order_token&line_item[variant_id]=75&line_item[quantity]=2&line_item[vendor_id]=155&user_token=Bearer+3cb0fa2285105e70e0f2dc4d0b9b419546c0ca102f5a0c3e
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
ETag: W/&quot;db191d4e8ea457e6f3b33193d25513f9&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 49e86405-accd-4eb6-9a0f-e714af2494bb
X-Runtime: 0.113792
Vary: Origin
Content-Length: 2705
200 OK
```


```json
{
  "id": 16,
  "number": "M129893416",
  "item_total": "39.98",
  "total": "39.98",
  "ship_total": "0.0",
  "state": "cart",
  "adjustment_total": "0.0",
  "user_id": 33,
  "created_at": "2020-06-04T11:40:04.965-04:00",
  "updated_at": "2020-06-04T11:40:05.006-04:00",
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
  "token": "VTviHWFNi4apQXnIeSCFgA",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order?order=M129893416&bzip=&init=true",
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
      "variant_id": 75,
      "vendor_id": 155,
      "single_display_amount": "$19.99",
      "display_amount": "$39.98",
      "total": "39.98",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 75,
        "name": "Product #43 - 5382",
        "sku": "SKU-74",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-43-5382",
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
        "product_id": 43,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [

      ],
      "vendor_name": "Vendor #155",
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
X-Spree-Order-Token: uBm0E106ZvAVIZL8Ov7wTg
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/cart`

#### Parameters


```json
user_id&order_token=uBm0E106ZvAVIZL8Ov7wTg&line_item[variant_id]=67&line_item[quantity]=2&line_item[vendor_id]=141
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
ETag: W/&quot;ae928383bf9ef756a681aa9f4574df88&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: a1643a4c-a971-4c16-9b7a-3406b91bad90
X-Runtime: 0.117851
Vary: Origin
Content-Length: 2692
200 OK
```


```json
{
  "id": 14,
  "number": "M617213552",
  "item_total": "39.98",
  "total": "39.98",
  "ship_total": "0.0",
  "state": "cart",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2020-06-04T11:40:03.996-04:00",
  "updated_at": "2020-06-04T11:40:04.038-04:00",
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
  "token": "yOtLgG00NuUO58-tqZY77A",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order?order=M617213552&bzip=&init=true",
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
      "variant_id": 67,
      "vendor_id": 141,
      "single_display_amount": "$19.99",
      "display_amount": "$39.98",
      "total": "39.98",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 67,
        "name": "Product #39 - 9585",
        "sku": "SKU-66",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-39-9585",
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
      "vendor_name": "Vendor #141",
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
Authorizat IO N: Bearer ce4ea35786c7f681f5e51af60ae2d0eb3a1e912d1fb8e695
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
X-Request-Id: 665058fb-7c27-4940-a713-17b997ceddcf
X-Runtime: 0.019342
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
GET /api/orders/M954706500
Accept: application/json
Authorizat IO N: Bearer e279c92a55dae810d1c0cb5cc1a297e4611031921794a065
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
ETag: W/&quot;1b8ee6d5fbb0022f14278f7a9a95c37b&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 5527768c-7db1-4572-b2dc-e96c901b9401
X-Runtime: 0.199452
Vary: Origin
Content-Length: 7974
200 OK
```


```json
{
  "id": 10,
  "number": "M954706500",
  "item_total": "20.0",
  "total": "118.0",
  "ship_total": "100.0",
  "state": "payment",
  "adjustment_total": "-2.0",
  "user_id": 29,
  "created_at": "2020-06-04T11:40:00.404-04:00",
  "updated_at": "2020-06-04T11:40:01.027-04:00",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
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
  "token": "4gi8QhqQktILJTZzJxisfA",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order?order=M954706500&bzip=10019&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [

  ],
  "bill_address": {
    "id": 19,
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
    "country_id": 20,
    "country_iso": "US",
    "state_id": 20,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 20,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 20,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 20
    }
  },
  "ship_address": {
    "id": 20,
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
    "country_id": 20,
    "country_iso": "US",
    "state_id": 20,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 20,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 20,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 20
    }
  },
  "line_items": [
    {
      "id": 13,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 49,
      "vendor_id": 110,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "9.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 49,
        "name": "Product #30 - 4916",
        "sku": "SKU-48",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-30-4916",
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
      "vendor_name": "Vendor #110",
      "country_iso": "US",
      "adjustments": [
        {
          "id": 1,
          "source_type": "Spree::PromotionAction",
          "source_id": 2,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 13,
          "amount": "-1.0",
          "label": "Promotion (10% off)",
          "promotion_code_id": 2,
          "finalized": false,
          "eligible": true,
          "created_at": "2020-06-04T11:40:00.856-04:00",
          "updated_at": "2020-06-04T11:40:00.856-04:00",
          "display_amount": "-$1.00"
        }
      ]
    },
    {
      "id": 14,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 51,
      "vendor_id": 110,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "9.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 51,
        "name": "Product #31 - 3529",
        "sku": "SKU-50",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-31-3529",
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
        "product_id": 31,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [

      ],
      "vendor_name": "Vendor #110",
      "country_iso": "US",
      "adjustments": [
        {
          "id": 2,
          "source_type": "Spree::PromotionAction",
          "source_id": 2,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 14,
          "amount": "-1.0",
          "label": "Promotion (10% off)",
          "promotion_code_id": 2,
          "finalized": false,
          "eligible": true,
          "created_at": "2020-06-04T11:40:00.868-04:00",
          "updated_at": "2020-06-04T11:40:00.868-04:00",
          "display_amount": "-$1.00"
        }
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
      "number": "H20508083213",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M954706500",
      "stock_location_name": "NY Warehouse 24",
      "giftwrappable": false,
      "stock_location_id": 24,
      "giftwrap": null,
      "shipping_rates": [
        {
          "id": 12,
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
        "id": 12,
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
              "id": 20,
              "name": "ShippingCategory #19"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 49,
          "quantity": 1,
          "states": {
            "on_hand": 1
          }
        },
        {
          "variant_id": 51,
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
          "source_id": 3,
          "adjustable_type": "Spree::Shipment",
          "adjustable_id": 12,
          "amount": "-10.0",
          "label": "Shipping",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2020-06-04T11:40:00.946-04:00",
          "updated_at": "2020-06-04T11:40:00.946-04:00",
          "display_amount": "-$10.00"
        },
        {
          "id": 3,
          "source_type": "Spree::PromotionAction",
          "source_id": 3,
          "adjustable_type": "Spree::Shipment",
          "adjustable_id": 12,
          "amount": "-9.99",
          "label": "Shipping",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2020-06-04T11:40:00.938-04:00",
          "updated_at": "2020-06-04T11:40:00.938-04:00",
          "display_amount": "-$9.99"
        }
      ],
      "stock_location_address": "NY Warehouse 24, Washington, AL",
      "country_iso": "US",
      "international_shipping": false,
      "delivery_estimation": "Jun 08"
    }
  ],
  "adjustments": [
    {
      "id": 5,
      "source_type": "Spree::Promotion",
      "source_id": 3,
      "adjustable_type": "Spree::Order",
      "adjustable_id": 10,
      "amount": "20.0",
      "label": "adj1",
      "promotion_code_id": null,
      "finalized": false,
      "eligible": true,
      "created_at": "2020-06-04T11:40:00.952-04:00",
      "updated_at": "2020-06-04T11:40:00.952-04:00",
      "display_amount": "$20.00"
    },
    {
      "id": 6,
      "source_type": "Spree::Promotion",
      "source_id": 3,
      "adjustable_type": "Spree::Order",
      "adjustable_id": 10,
      "amount": "30.0",
      "label": "adj2",
      "promotion_code_id": null,
      "finalized": false,
      "eligible": true,
      "created_at": "2020-06-04T11:40:00.956-04:00",
      "updated_at": "2020-06-04T11:40:00.956-04:00",
      "display_amount": "$30.00"
    }
  ],
  "permissions": {
    "can_update": true
  },
  "gift_card_total": "0.0",
  "applied_promotion_codes": [
    {
      "id": 2,
      "promotion_id": 2,
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
        "source_id": 2,
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
GET /api/orders/M931953069
Accept: application/json
Authorizat IO N: c7b3eb9c174d95f7c8f20b4c6d66e94f934cb3989c7ce055
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
X-Request-Id: 35c040a3-701e-4bc0-8069-86f562296653
X-Runtime: 0.012098
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
Accept: application/json
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/users/password`

#### Parameters


```json
user[email]=email42%40example.com
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
X-Request-Id: 882045ef-c52f-496e-b303-5a9fa027aa7d
X-Runtime: 0.003126
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
user[email]=email41%40example.com&user[password]=secret
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
Authorization: Bearer a045df55b652a2b79d287844395e10d50b52de343fd73bc2
ETag: W/&quot;07a6beadb7f51ae76339c390e682f5c1&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 8c079b91-143a-479f-961b-e2ee5e9f862b
X-Runtime: 0.015071
Vary: Origin
Content-Length: 562
200 OK
```


```json
{
  "id": 41,
  "email": "email41@example.com",
  "persistence_token": null,
  "perishable_token": null,
  "last_request_at": null,
  "login": "email41@example.com",
  "ship_address_id": null,
  "bill_address_id": null,
  "created_at": "2020-06-04T11:40:07.561-04:00",
  "updated_at": "2020-06-04T11:40:07.563-04:00",
  "spree_api_key": "a045df55b652a2b79d287844395e10d50b52de343fd73bc2",
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
X-Request-Id: b7b30af2-c228-4cc1-9395-f1eaf18de83e
X-Runtime: 0.024352
Vary: Origin
204 No Content
```




# Products

get products by taxon

## Fetch a single product by id


### Request

#### Endpoint

```plaintext
GET /api/products/product-24-1021
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
Date: Thu, 04 Jun 2020 15:39:58 GMT
Surrogate-Control: max-age=900
Surrogate-Key: product_id=1
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;52cb1b2e0ed71cc11ee2261e3bf2ec09&quot;
X-Request-Id: ae28aa84-ef5f-4da7-a18a-c06fc1e00718
X-Runtime: 0.064089
Vary: Origin
Content-Length: 1616
200 OK
```


```json
{
  "id": 24,
  "name": "Product #24 - 1021",
  "description": "As seen on TV!",
  "available_on": "2019-06-04T11:39:58.346-04:00",
  "slug": "product-24-1021",
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
      "created_at": "2020-06-04T11:39:58.288-04:00",
      "url": "/category/clothing",
      "position": 1
    },
    {
      "id": 15,
      "name": "Girl",
      "taxonomy_id": 6,
      "created_at": "2020-06-04T11:39:58.308-04:00",
      "url": "/category/clothing/girl",
      "position": 2
    },
    {
      "id": 16,
      "name": "Dresses",
      "taxonomy_id": 6,
      "created_at": "2020-06-04T11:39:58.327-04:00",
      "url": "/category/clothing/girl/dresses",
      "position": 3
    }
  ],
  "has_variants": false,
  "master": {
    "id": 37,
    "name": "Product #24 - 1021",
    "sku": "SKU-37",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": true,
    "slug": "product-24-1021",
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
Date: Thu, 04 Jun 2020 15:39:57 GMT
Surrogate-Control: max-age=900
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;e17cb11d2cdcfe4c0e12f95b3ede5b71&quot;
X-Request-Id: 0e92c64b-0fd5-4fd8-9e5a-bbd9a9e0f906
X-Runtime: 0.062228
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
      "id": 18,
      "name": "Product #18 - 9356",
      "description": "As seen on TV!",
      "available_on": "2019-06-04T11:39:57.327-04:00",
      "slug": "product-18-9356",
      "meta_description": null,
      "meta_keywords": null,
      "taxon_ids": [
        8
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
        "id": 31,
        "name": "Product #18 - 9356",
        "sku": "SKU-31",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-18-9356",
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
            "name": "Maison You",
            "pretty_name": "Brand -> Maison You",
            "permalink": "brand/maison-you",
            "parent_id": 7,
            "taxonomy_id": 3,
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
Date: Thu, 04 Jun 2020 15:39:57 GMT
Surrogate-Control: max-age=900
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;f393f5c592cbd0d69d68291e08f30a3b&quot;
X-Request-Id: 3e088b57-4ebf-4ba4-9ee3-563d18e7307e
X-Runtime: 0.033847
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
      "id": 19,
      "name": "Product #19 - 9117",
      "slug": "product-19-9117",
      "master_id": 32,
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
GET /api/products?ids=21%2C22%2C23
Host: example.org
Cookie: 
```

`GET /api/products`

#### Parameters


```json
ids: 21,22,23
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
Date: Thu, 04 Jun 2020 15:39:58 GMT
Surrogate-Control: max-age=900
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;63a79be06df8f5a63d08c2e68b5f5678&quot;
X-Request-Id: ad931507-ba27-4975-831d-583dc85ae428
X-Runtime: 0.110800
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
      "id": 21,
      "name": "Product #21 - 3942",
      "description": "As seen on TV!",
      "available_on": "2019-06-04T11:39:57.919-04:00",
      "slug": "product-21-3942",
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
        "id": 34,
        "name": "Product #21 - 3942",
        "sku": "SKU-34",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-21-3942",
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
      "id": 22,
      "name": "Product #22 - 4541",
      "description": "As seen on TV!",
      "available_on": "2019-06-04T11:39:58.002-04:00",
      "slug": "product-22-4541",
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
        "id": 35,
        "name": "Product #22 - 4541",
        "sku": "SKU-35",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-22-4541",
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
      "id": 23,
      "name": "Product #23 - 6230",
      "description": "As seen on TV!",
      "available_on": "2019-06-04T11:39:58.077-04:00",
      "slug": "product-23-6230",
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
        "id": 36,
        "name": "Product #23 - 6230",
        "sku": "SKU-36",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-23-6230",
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
GET /api/taxons/products?id=6
Host: example.org
Cookie: 
```

`GET /api/taxons/products`

#### Parameters


```json
id: 6
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
ETag: W/&quot;cf0650e8ec978f9010ff0606ed3a1a9f&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 6550b43c-4f01-4548-a8d3-a6104fcad056
X-Runtime: 0.050076
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
      "id": 17,
      "name": "Product #17 - 1718",
      "description": "As seen on TV!",
      "available_on": "2019-06-04T11:39:57.155-04:00",
      "slug": "product-17-1718",
      "meta_description": null,
      "meta_keywords": null,
      "taxon_ids": [
        6
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
        "id": 30,
        "name": "Product #17 - 1718",
        "sku": "SKU-30",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-17-1718",
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
ETag: W/&quot;3b30a76182ec88eb2cb1bcc4130117ca&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 5fca4d99-f420-4199-ac22-ee4519f44048
X-Runtime: 0.080861
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
      "id": 15,
      "name": "Product #15 - 6908",
      "description": "As seen on TV!",
      "available_on": "2019-06-04T11:39:56.787-04:00",
      "slug": "product-15-6908",
      "meta_description": null,
      "meta_keywords": null,
      "taxon_ids": [
        3
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
        "id": 28,
        "name": "Product #15 - 6908",
        "sku": "SKU-28",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-15-6908",
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



## Get all products info


### Request

#### Endpoint

```plaintext
GET /api/sitemap/products
Accept: application/json
Authorizat IO N: Bearer 422e0c1efc3f54d7106be066082ecaf19e9922115256b2ae
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
X-Request-Id: d341a87f-d766-4953-9100-d5f7df8cfa5e
X-Runtime: 0.033406
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
X-Request-Id: 3ddacd3d-5500-48c0-bf73-53c45f5a5ef9
X-Runtime: 0.012158
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
GET /api/recently_viewed?recently_viewed[session_id]=7znrxgpeid8moj9a82x007ve0kimpkgc5x18d6qsb7j2f83xi7dms6uibyir6jfm1q79tp95fkirl3a7sbzrcc8syvts6q23oauc6wts37s76ao4w14n6tw0mvp74f9h3op799rfthtjkw249gif3626hfx4x2ua93o6lxjtu7p6fnmmqe0pouz64025fjr882okbh25ebv9omezt6pdql6qgwe57rw9gypi8350zrvn8fste5yx5sn4662flx4
Accept: application/json
Authorizat IO N: Bearer 39cc1c517a9904003a7f2a21e496d80ddacb7d47d263c35f
Host: example.org
Cookie: 
```

`GET /api/recently_viewed`

#### Parameters


```json
recently_viewed: {&quot;session_id&quot;=&gt;&quot;7znrxgpeid8moj9a82x007ve0kimpkgc5x18d6qsb7j2f83xi7dms6uibyir6jfm1q79tp95fkirl3a7sbzrcc8syvts6q23oauc6wts37s76ao4w14n6tw0mvp74f9h3op799rfthtjkw249gif3626hfx4x2ua93o6lxjtu7p6fnmmqe0pouz64025fjr882okbh25ebv9omezt6pdql6qgwe57rw9gypi8350zrvn8fste5yx5sn4662flx4&quot;}
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
ETag: W/&quot;2dd46adad7f753aae4869a4bfc06bf51&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: aa1f87af-4211-45cd-96df-8758ede4b5cb
X-Runtime: 0.027554
Vary: Origin
Content-Length: 119
200 OK
```


```json
[
  {
    "at": "2020-06-04T11:40:07.608-04:00",
    "variant_id": "var1"
  },
  {
    "at": "2020-06-04T11:45:07.608-04:00",
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
Authorizat IO N: Bearer 5a0eb092d52cd5740ee9c051f5f8f19df321426628287189
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/recently_viewed`

#### Parameters


```json
recently_viewed[session_id]=qvf664nzmktpj3h0o8mc29v77ddxfqu9ppbvpao6yk25pbsmtpm64np4wzsicxkaz9tw6iwzettge227a64ibw0gj0h1shfrl4rmpxm2hczk2zh65schwv7632t09dwvxcz11428cvf4an5leyhrogvau74um06rtzz40mngfjq3mw81jo35s7px0cjcmx3joiw7538718vod8pm5lrhxe85ukf2pxa2xrhw0xokrakg9ogol5x172p7kelqjn7&recently_viewed[variant_id]=foo
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
X-Request-Id: db85780c-698c-46af-a5d5-daabd434ac12
X-Runtime: 0.005144
Vary: Origin
204 No Content
```




# Return Authorizations

Get a single user return authorziation

## Can get another user&#39;s return authorization


### Request

#### Endpoint

```plaintext
GET /api/returns/RA024885313
Authorizat IO N: Bearer 4eedf2b503be11a8dfcd311fbee74132f5bbdb4f9ff00f7a
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
ETag: W/&quot;f790b1cafb71d1b14ae3256c5ffe777a&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 154e3d96-d3c0-45cc-b712-f149d0077f36
X-Runtime: 0.055273
Vary: Origin
Content-Length: 3017
200 OK
```


```json
{
  "id": 3,
  "number": "RA024885313",
  "state": "authorized",
  "order_id": 7,
  "memo": "Items were broken",
  "created_at": "2020-06-04T11:39:56.022-04:00",
  "updated_at": "2020-06-04T11:39:56.022-04:00",
  "amount": "10.0",
  "reason": {
    "id": 5,
    "name": "Defect #5",
    "active": true,
    "mutable": true,
    "created_at": "2020-06-04T11:39:56.018-04:00",
    "updated_at": "2020-06-04T11:39:56.018-04:00",
    "mirakl_code": null
  },
  "order": {
    "id": 7,
    "number": "M825230688",
    "item_total": "10.0",
    "total": "110.0",
    "state": "complete",
    "adjustment_total": "0.0",
    "user_id": 25,
    "completed_at": "2020-06-04T11:39:55.934-04:00",
    "bill_address_id": 13,
    "ship_address_id": 14,
    "payment_total": "110.0",
    "shipment_state": "shipped",
    "payment_state": "paid",
    "email": "email25@example.com",
    "special_instructions": null,
    "created_at": "2020-06-04T11:39:55.846-04:00",
    "updated_at": "2020-06-04T11:39:55.999-04:00",
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
    "guest_token": "s-ID3sAJdcyNpXubPCDBZQ",
    "canceled_at": null,
    "canceler_id": null,
    "store_id": 7,
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
    "id": 14,
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
  "bill_address": {
    "id": 13,
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
  "return_items": [
    {
      "name": "Product #12 - 727",
      "brand": null,
      "brand_slug": null,
      "image": null,
      "product_slug": "product-12-727",
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
        "id": 5,
        "name": "Credit Card"
      },
      "source": {
        "id": 3,
        "month": "12",
        "year": "2021",
        "cc_type": null,
        "last_digits": "1111",
        "name": "Spree Commerce",
        "gateway_customer_profile_id": "BGS-400344",
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
Authorizat IO N: Bearer 57dfa9c8b9fe5afbb8103b6938cd232bfe7e2f2486ffdfbb
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
ETag: W/&quot;4548645029a41538cc6129c96999e451&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: e7e6c012-9ec1-411d-bfb4-63f5489c082a
X-Runtime: 0.007630
Vary: Origin
Content-Length: 169
200 OK
```


```json
{
  "return_authorizations": [
    {
      "number": "RA865004777",
      "created_at": "2020-06-04T11:39:56.548-04:00",
      "return_amount": "10.0",
      "order_number": "M243762616",
      "state": "authorized"
    }
  ]
}
```



## returns a 200


### Request

#### Endpoint

```plaintext
GET /api/returns/RA758601510
Authorizat IO N: Bearer 05d9bd3ae0e390b088a9b640eeb2fea0ff6bc748115ff966
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
ETag: W/&quot;6f627fc839635d844afe9de0e9506f0f&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 51888d89-2d53-4cf4-b34b-4961f8d52190
X-Runtime: 0.098385
Vary: Origin
Content-Length: 2940
200 OK
```


```json
{
  "id": 1,
  "number": "RA758601510",
  "state": "authorized",
  "order_id": 5,
  "memo": "Items were broken",
  "created_at": "2020-06-04T11:39:54.742-04:00",
  "updated_at": "2020-06-04T11:39:54.742-04:00",
  "amount": "10.0",
  "reason": {
    "id": 1,
    "name": "Defect #1",
    "active": true,
    "mutable": true,
    "created_at": "2020-06-04T11:39:54.728-04:00",
    "updated_at": "2020-06-04T11:39:54.728-04:00",
    "mirakl_code": null
  },
  "order": {
    "id": 5,
    "number": "M843225482",
    "item_total": "10.0",
    "total": "110.0",
    "state": "complete",
    "adjustment_total": "0.0",
    "user_id": 22,
    "completed_at": "2020-06-04T11:39:54.442-04:00",
    "bill_address_id": 9,
    "ship_address_id": 10,
    "payment_total": "110.0",
    "shipment_state": "shipped",
    "payment_state": "paid",
    "email": "email22@example.com",
    "special_instructions": null,
    "created_at": "2020-06-04T11:39:54.347-04:00",
    "updated_at": "2020-06-04T11:39:54.649-04:00",
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
    "guest_token": "LyHejoB9O-Iz3o7pHBwI2g",
    "canceled_at": null,
    "canceler_id": null,
    "store_id": 5,
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
    "id": 10,
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
  "bill_address": {
    "id": 9,
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
  "return_items": [
    {
      "name": "Product #10 - 9021",
      "brand": null,
      "brand_slug": null,
      "image": null,
      "product_slug": "product-10-9021",
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
        "id": 1,
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
GET /api/returns/RA065358656
Authorizat IO N: Bearer 8311a47e14339823a95d752588edbda373479e23be0d6ebf
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
X-Request-Id: 36f41085-9001-42b4-a33e-8f5edd1605f4
X-Runtime: 0.011279
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
stock_request[email]=latia%40cremincollier.info&stock_request[variant_id]=43
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
X-Request-Id: 3ecb723d-bbd6-4529-ac27-90b36c9a4504
X-Runtime: 0.006201
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
stock_request[email]=foo&stock_request[variant_id]=39
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
X-Request-Id: e763fcb4-2034-4173-b315-0c4a01a46338
X-Runtime: 0.031593
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
stock_request[email]=marylyn_langworth%40walterabbott.name&stock_request[variant_id]=41
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
X-Request-Id: d95d97db-4613-4f1a-b43c-d0377e3b09d1
X-Runtime: 0.005787
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
Authorizat IO N: Bearer e00df5ab890ac502e23a0152488b31914c994444756c08bc
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
ETag: W/&quot;68dae0bfce55eb46b726ba9f5c328d6f&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: a9ed9c36-7202-4e7b-b955-42a3c8b56ea5
X-Runtime: 0.036626
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
      "created_at": "2020-06-04T11:40:07.782-04:00"
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
subscriber[email]=kerrie_grant%40barrows.biz&subscriber[first_name]=Alta&subscriber[last_name]=Schiller&subscriber[source]=Et+rerum+consequatur+provident+vel+dignissimos+fugit+voluptas.&subscriber[list_id]=cl2mab
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
ETag: W/&quot;a44e1819c7409d0db3a9dd4a8fbbccbc&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: ce044b73-7152-4b6a-8d82-98716a12b0ce
X-Runtime: 0.019580
Vary: Origin
Content-Length: 274
201 Created
```


```json
{
  "id": 2,
  "user_id": null,
  "list_id": "cl2mab",
  "email": "kerrie_grant@barrows.biz",
  "first_name": "Alta",
  "last_name": "Schiller",
  "source": "Et rerum consequatur provident vel dignissimos fugit voluptas.",
  "phone": null,
  "status": "subscribed",
  "created_at": "2020-06-04T11:40:07.390-04:00"
}
```



## Create a subscriber for the associated user


### Request

#### Endpoint

```plaintext
POST /api/subscribers
Accept: application/json
Authorizat IO N: Bearer 467ceadb4dc4ae7101e6aae8bc02d92a3c929dcfe192beb5
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/subscribers`

#### Parameters


```json
subscriber[email]&subscriber[first_name]=Lakenya&subscriber[last_name]=Weimann&subscriber[source]=Tenetur+omnis+est+ut+fugit.&subscriber[list_id]=0kc0l1
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
ETag: W/&quot;95a37f327a5bc8f7f2a986580aec39c5&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 5f71d1a1-b164-4e3f-8672-765ada0534f5
X-Runtime: 0.010815
Vary: Origin
Content-Length: 234
201 Created
```


```json
{
  "id": 3,
  "user_id": 37,
  "list_id": "0kc0l1",
  "email": "email37@example.com",
  "first_name": "Lakenya",
  "last_name": "Weimann",
  "source": "Tenetur omnis est ut fugit.",
  "phone": null,
  "status": "subscribed",
  "created_at": "2020-06-04T11:40:07.441-04:00"
}
```



## Get all subscribers


### Request

#### Endpoint

```plaintext
GET /api/subscribers
Accept: application/json
Authorizat IO N: Bearer cc7c770f988cb35f90a2d5d0aa412aa42c1850fe77518ccd
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
ETag: W/&quot;812bd25bf73cba40c2f094131fe5331a&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 7910de13-8786-47b8-85ad-78842f37b23a
X-Runtime: 0.011667
Vary: Origin
Content-Length: 734
200 OK
```


```json
{
  "subscribers": [
    {
      "id": 4,
      "user_id": null,
      "list_id": "17g2zc",
      "email": "jefferey@boyleluettgen.biz",
      "first_name": "Berry",
      "last_name": "Gutmann",
      "source": null,
      "phone": null,
      "status": "subscribed",
      "created_at": "2020-06-04T11:40:07.452-04:00"
    },
    {
      "id": 5,
      "user_id": null,
      "list_id": "mb9qld",
      "email": "donn_williamson@morissette.us",
      "first_name": "Dick",
      "last_name": "Orn",
      "source": null,
      "phone": null,
      "status": "subscribed",
      "created_at": "2020-06-04T11:40:07.456-04:00"
    },
    {
      "id": 6,
      "user_id": null,
      "list_id": "eov6jk",
      "email": "leana_leuschke@padberg.ca",
      "first_name": "Chester",
      "last_name": "Ruecker",
      "source": null,
      "phone": null,
      "status": "subscribed",
      "created_at": "2020-06-04T11:40:07.460-04:00"
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
PATCH /api/subscribers/7
Accept: application/json
Authorizat IO N: Bearer 8516afe39228209236bf60e3e76b18b64c727ec179bc1c3e
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/subscribers/:id`

#### Parameters


```json
subscriber[source]=Ipsum+alias+magni+nemo+ut+aut+qui+corrupti+placeat.
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
ETag: W/&quot;58aeca00afd192d21529a10e4cb66e67&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 87f5bbdc-9c55-4eba-9390-20f4d7c375a4
X-Runtime: 0.011797
Vary: Origin
Content-Length: 266
200 OK
```


```json
{
  "id": 7,
  "user_id": 39,
  "list_id": "egtjpi",
  "email": "email39@example.com",
  "first_name": "Malka",
  "last_name": "Littel",
  "source": "Ipsum alias magni nemo ut aut qui corrupti placeat.",
  "phone": null,
  "status": "subscribed_and_synced",
  "created_at": "2020-06-04T11:40:07.504-04:00"
}
```



## unsubscribe a known subscriber


### Request

#### Endpoint

```plaintext
DELETE /api/subscribers
Accept: application/json
Authorizat IO N: Bearer 43ddaffa63a7b5e4c73ae919c2f1cdda5cd9a579c0ea626a
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`DELETE /api/subscribers`

#### Parameters


```json
subscriber[email]=email35%40example.com&subscriber[list_id]=o038nq
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
X-Request-Id: 7e2bc5ff-7316-4e57-9c02-2d55ea9b0da7
X-Runtime: 0.037827
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
Authorizat IO N: Bearer 2dcb89d6c06ddda6eb112a9d79fc1160e35bc3f6b82ec593
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`DELETE /api/subscribers`

#### Parameters


```json
subscriber[email]=madelaine.senger%40witting.ca&subscriber[list_id]=wqm0hh
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
X-Request-Id: dc1dc9d8-3896-4b20-bbac-db7c659e1eea
X-Runtime: 0.008192
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
Authorizat IO N: Bearer f3a8442489c85260fb825cdbc37d58dd4a0c4cdf5f27255b
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
X-Request-Id: 0e6bf6f5-c17a-4316-b385-822c2ed91b56
X-Runtime: 0.034423
Vary: Origin
Content-Length: 2
200 OK
```


```json
[

]
```



# Taxons API

Returns taxons associated with the Navigation Taxonomy for display in the menu bar

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
X-Request-Id: 6918b73d-2a00-4170-83a7-c70a59d5dfff
X-Runtime: 0.035299
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
ETag: W/&quot;f564dce211f60c93a4776b2b8b45bf9f&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 1b795caa-ae37-41ab-ac7a-bcb84fc0f0f1
X-Runtime: 0.023847
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
ETag: W/&quot;5ffa4357a8ecb9e2371349dd2e36a677&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: a98f3616-148a-4994-8b9a-b0a71053d505
X-Runtime: 0.029680
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
      "id": 38,
      "name": "Category",
      "pretty_name": "Category",
      "permalink": "category",
      "parent_id": null,
      "taxonomy_id": 14,
      "url_override": null,
      "description": "Category",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 39,
      "name": "Kids",
      "pretty_name": "Category -> Kids",
      "permalink": "category/kids",
      "parent_id": 38,
      "taxonomy_id": 14,
      "url_override": null,
      "description": "Kids",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 40,
      "name": "Boys",
      "pretty_name": "Category -> Kids -> Boys",
      "permalink": "category/kids/boys",
      "parent_id": 39,
      "taxonomy_id": 14,
      "url_override": null,
      "description": "Boys",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 41,
      "name": "Boys Tops",
      "pretty_name": "Category -> Kids -> Boys -> Boys Tops",
      "permalink": "category/kids/boys/boys-tops",
      "parent_id": 40,
      "taxonomy_id": 14,
      "url_override": null,
      "description": "Boys Tops",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 42,
      "name": "Boys Shirts",
      "pretty_name": "Category -> Kids -> Boys -> Boys Tops -> Boys Shirts",
      "permalink": "category/kids/boys/boys-tops/boys-shirts",
      "parent_id": 41,
      "taxonomy_id": 14,
      "url_override": null,
      "description": "Boys Shirts",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 43,
      "name": "Girls",
      "pretty_name": "Category -> Kids -> Girls",
      "permalink": "category/kids/girls",
      "parent_id": 39,
      "taxonomy_id": 14,
      "url_override": null,
      "description": "Girls",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 44,
      "name": "Girls Tops",
      "pretty_name": "Category -> Kids -> Girls -> Girls Tops",
      "permalink": "category/kids/girls/girls-tops",
      "parent_id": 43,
      "taxonomy_id": 14,
      "url_override": null,
      "description": "Girls Tops",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 45,
      "name": "Girls Shirts",
      "pretty_name": "Category -> Kids -> Girls -> Girls Tops -> Girls Shirts",
      "permalink": "category/kids/girls/girls-tops/girls-shirts",
      "parent_id": 44,
      "taxonomy_id": 14,
      "url_override": null,
      "description": "Girls Shirts",
      "icon": "/assets/default_taxon.png"
    },
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
ETag: W/&quot;3823858ff665864115575265dc37687f&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 18036726-ed06-4b44-a911-c03c6cc69ea6
X-Runtime: 0.016798
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
    "created_at": "2020-06-04T11:40:06.267-04:00",
    "updated_at": "2020-06-04T11:40:06.325-04:00",
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
ETag: W/&quot;046a925d761b8725ba1bc4c9857a65a7&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: cf9e3b28-8fc6-430a-bdb1-36bc7fb7fa94
X-Runtime: 0.007841
Vary: Origin
Content-Length: 144
200 OK
```


```json
[
  {
    "id": 18,
    "name": "Kids",
    "navigation_url": "/shop/kids",
    "parent_id": 17,
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
ETag: W/&quot;fd3b268576ed3fcbfa4e3088638bedd3&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: bbe5b7a3-95cd-46eb-a80d-aa7d59cdffad
X-Runtime: 0.013058
Vary: Origin
Content-Length: 535
200 OK
```


```json
[
  {
    "id": 22,
    "parent_id": 21,
    "position": 0,
    "name": "brand_x",
    "permalink": "brand/brand_x",
    "taxonomy_id": 9,
    "lft": 6,
    "rgt": 7,
    "icon_file_name": null,
    "icon_content_type": null,
    "icon_file_size": null,
    "icon_updated_at": null,
    "description": null,
    "created_at": "2020-06-04T11:40:05.883-04:00",
    "updated_at": "2020-06-04T11:40:05.941-04:00",
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
user[email]=email48%40example.com&user[password]=secret
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
Authorization: Bearer 856995f5bedd90b767d2f9185b745e8158a5020bce51191d
ETag: W/&quot;f958f86c8047816d41307bff9b2746a0&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 9e532e0f-5f8f-44da-827c-23c48196a8b6
X-Runtime: 0.011661
Vary: Origin
Content-Length: 562
200 OK
```


```json
{
  "id": 48,
  "email": "email48@example.com",
  "persistence_token": null,
  "perishable_token": null,
  "last_request_at": null,
  "login": "email48@example.com",
  "ship_address_id": null,
  "bill_address_id": null,
  "created_at": "2020-06-04T11:40:07.856-04:00",
  "updated_at": "2020-06-04T11:40:07.858-04:00",
  "spree_api_key": "856995f5bedd90b767d2f9185b745e8158a5020bce51191d",
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
X-Spree-Order-Token: afEbdUI_qkUjn0JE9BU_Wg
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/users/login`

#### Parameters


```json
user[email]=email49%40example.com&user[password]=secret&order_number=M020352429
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
Authorization: Bearer de16ac740dcd0e04eab8f57bf2a1e4272c99c95cfb055c08
ETag: W/&quot;c99011676baac732e976bf84dec4a2e1&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: ccea0df6-d3bb-44c4-8e75-7f0be676c9b5
X-Runtime: 0.015516
Vary: Origin
Content-Length: 562
200 OK
```


```json
{
  "id": 49,
  "email": "email49@example.com",
  "persistence_token": null,
  "perishable_token": null,
  "last_request_at": null,
  "login": "email49@example.com",
  "ship_address_id": null,
  "bill_address_id": null,
  "created_at": "2020-06-04T11:40:07.880-04:00",
  "updated_at": "2020-06-04T11:40:07.882-04:00",
  "spree_api_key": "de16ac740dcd0e04eab8f57bf2a1e4272c99c95cfb055c08",
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
Authorizat IO N: Bearer c5e6b2ab3c6b9fd36320466c0baf13eb9fcfcb1c0fa7680c
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
Authorization: Bearer c5e6b2ab3c6b9fd36320466c0baf13eb9fcfcb1c0fa7680c
ETag: W/&quot;7aa7bbccdd1b68c50aa1d8b2f9e7c8f9&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: f307525d-0ec9-49c7-8cee-b0a92a092e50
X-Runtime: 0.029260
Vary: Origin
Content-Length: 1521
200 OK
```


```json
{
  "email": "email51@example.com",
  "first_name": null,
  "last_name": null,
  "id": 51,
  "subscribed": false,
  "addresses": [
    {
      "id": 31,
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
      "country_id": 31,
      "country_iso": "US",
      "state_id": 31,
      "state_name": null,
      "state_text": "AL",
      "country": {
        "id": 31,
        "iso_name": "UNITED STATES",
        "iso": "US",
        "iso3": "USA",
        "name": "United States",
        "numcode": 840
      },
      "default": true
    },
    {
      "id": 30,
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
      "country_id": 31,
      "country_iso": "US",
      "state_id": 31,
      "state_name": null,
      "state_text": "AL",
      "country": {
        "id": 31,
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
      "id": 1,
      "default": true,
      "source": {
        "id": 1,
        "payment_type": "CreditCard",
        "token": null,
        "created_at": "2020-06-04T11:40:08.357-04:00",
        "cc_type": null,
        "last_digits": null,
        "month": null,
        "year": null
      }
    },
    {
      "id": 2,
      "default": false,
      "source": {
        "id": 2,
        "payment_type": "ApplePayCard",
        "token": null,
        "created_at": "2020-06-04T11:40:08.377-04:00",
        "cc_type": null,
        "last_digits": null,
        "month": null,
        "year": null
      }
    },
    {
      "id": 3,
      "default": false,
      "source": {
        "id": 3,
        "payment_type": "PayPalAccount",
        "token": null,
        "created_at": "2020-06-04T11:40:08.387-04:00",
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
Authorization: Bearer 0d91afc41366bdd9efe3aa1a5934043e14a9e9a121a178be
ETag: W/&quot;53d8ff28bfcef2ba79fff628f6f7d1d4&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 28a79974-b2e2-42d0-b25c-4293ea5ffd90
X-Runtime: 0.023354
Vary: Origin
Content-Length: 185
201 Created
```


```json
{
  "id": 53,
  "email": "test@example.com",
  "created_at": "2020-06-04T11:40:08.472-04:00",
  "updated_at": "2020-06-04T11:40:08.474-04:00",
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
X-Spree-Order-Token: vgjDEyW-2VN0-jAqUoigNw
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/users`

#### Parameters


```json
user[email]=test%40example.com&user[password]=test123&user[password_confirmation]=test123&order_number=M612918290
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
Authorization: Bearer bd4ebe2d11b4779f65982d2c2475c64b26134d0c77a4092f
ETag: W/&quot;273359653180ca797edfe38f8b3ce7f2&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: a799e77d-0293-4ff7-9988-6cb4a4af1517
X-Runtime: 0.027679
Vary: Origin
Content-Length: 185
201 Created
```


```json
{
  "id": 54,
  "email": "test@example.com",
  "created_at": "2020-06-04T11:40:08.846-04:00",
  "updated_at": "2020-06-04T11:40:08.848-04:00",
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
Accept: application/json
Authorizat IO N: Bearer 19933cf21e3d083207cf7758fcb614a2b3706449be760053
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
Authorization: Bearer 19933cf21e3d083207cf7758fcb614a2b3706449be760053
ETag: W/&quot;ad03a766c4a6e222eadbe6ff6db74238&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 07ea93b7-3300-45b1-b14c-214122ff966d
X-Runtime: 0.033603
Vary: Origin
Content-Length: 187
200 OK
```


```json
{
  "id": 50,
  "email": "email50@example.com",
  "created_at": "2020-06-04T11:40:08.243-04:00",
  "updated_at": "2020-06-04T11:40:08.246-04:00",
  "subscribed": true,
  "bill_address": null,
  "ship_address": null
}
```



## Unsubscribe a user


### Request

#### Endpoint

```plaintext
PUT /api/users/52/unsubscribe
Accept: application/json
Authorizat IO N: Bearer e96cc5871e1ea8a5a02df29911fe733a3fec19cee3c7e4a2
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
Authorization: Bearer e96cc5871e1ea8a5a02df29911fe733a3fec19cee3c7e4a2
ETag: W/&quot;8e80feeeebd1c333ad8a27c18785b7bc&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 3088ce2f-2117-47f6-9581-694d6df21940
X-Runtime: 0.017650
Vary: Origin
Content-Length: 188
200 OK
```


```json
{
  "id": 52,
  "email": "email52@example.com",
  "created_at": "2020-06-04T11:40:08.432-04:00",
  "updated_at": "2020-06-04T11:40:08.434-04:00",
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
GET /api/variants/18
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
ETag: W/&quot;24a64a461a3cf9c31635dca5eac652c2&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: cf34308e-029a-46a7-b140-d644cb7515eb
X-Runtime: 0.091332
Vary: Origin
Content-Length: 2007
200 OK
```


```json
{
  "id": 18,
  "name": "Product #9 - 3966",
  "sku": "SKU-17",
  "weight": "0.0",
  "height": null,
  "width": null,
  "depth": null,
  "is_master": false,
  "slug": "product-9-3966",
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
      "id": 9,
      "name": "Size-9",
      "presentation": "S",
      "option_type_name": "foo-size-9",
      "option_type_id": 9,
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
      "attachment_updated_at": "2020-06-04T11:39:53.774-04:00",
      "attachment_width": 489,
      "attachment_height": 490,
      "alt": null,
      "viewable_type": "Spree::Variant",
      "viewable_id": 18,
      "mini_url": "/spree/products/1/mini/thinking-cat.jpg?1591285193",
      "small_url": "/spree/products/1/small/thinking-cat.jpg?1591285193",
      "product_url": "/spree/products/1/product/thinking-cat.jpg?1591285193",
      "large_url": "/spree/products/1/large/thinking-cat.jpg?1591285193"
    }
  ],
  "variant_properties": [

  ],
  "stock_items": [

  ],
  "prices": [
    {
      "id": 16,
      "vendor_id": 36,
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
      "id": 17,
      "vendor_id": 37,
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
Authorizat IO N: Bearer adb04ec14d075ba446d444b8e6b9ec9c7ee481473cc806c6
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
ETag: W/&quot;e90c27c1b67a1c142462e832339eaf8e&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 0c70e065-7188-40b5-8fa9-dee6a41cceb6
X-Runtime: 0.014204
Vary: Origin
Content-Length: 208
200 OK
```


```json
[
  {
    "id": 8,
    "user_id": 101,
    "payment_source_type": "SolidusPaypalBraintree::Source",
    "payment_source_id": 10,
    "default": false,
    "created_at": "2020-06-04T11:40:21.079-04:00",
    "updated_at": "2020-06-04T11:40:21.079-04:00"
  }
]
```



## Remove the payment from the user wallet


### Request

#### Endpoint

```plaintext
DELETE /api/wallet_payment_sources/6
Accept: application/json
Authorizat IO N: Bearer 277ea540819b212c943efb2ed517f319ae2253c9ae20befb
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
X-Request-Id: 66db9580-d793-42f8-90eb-5a7d8a0ad911
X-Runtime: 0.035005
Vary: Origin
204 No Content
```




## Set a wallet payment source as the default user payment method


### Request

#### Endpoint

```plaintext
POST /api/wallet_payment_sources/7/default
Accept: application/json
Authorizat IO N: Bearer 83d67040e6fda33dae3519ba364d75a47f9e4211fedceade
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
X-Request-Id: f93a361f-31e9-45dd-b684-2d585ae70bc9
X-Runtime: 0.011143
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
Authorizat IO N: Bearer ecfb8045c49f83584ec5a2d05b971b57e3d6239d124e0a03
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/wished_products`

#### Parameters


```json
wished_product[wishlist_id]=39&wished_product[variant_id]=157&wished_product[quantity]=2&wished_product[remark]=Foo+bar
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
ETag: W/&quot;1921e3ffcd1a24d2076bae1abe8021f3&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 99ffb33f-f74d-4e71-8606-3c18ed68f787
X-Runtime: 0.013693
Vary: Origin
Content-Length: 120
201 Created
```


```json
{
  "id": 28,
  "wishlist_id": 39,
  "variant_id": 157,
  "quantity": 2,
  "remark": "Foo bar",
  "created_at": "2020-06-04T11:40:17.918-04:00"
}
```



## Delete a wished product


### Request

#### Endpoint

```plaintext
DELETE /api/wished_products/29
Accept: application/json
Authorizat IO N: Bearer 60e7b6c1bcefb0dd2e8403e9b1942dbd2cda74e70dc6a989
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
X-Request-Id: 6f7604ba-cd64-4bca-8360-1f330e22fc59
X-Runtime: 0.013011
Vary: Origin
204 No Content
```




## Get a single wished product


### Request

#### Endpoint

```plaintext
GET /api/wished_products/25
Accept: application/json
Authorizat IO N: Bearer e29a5cfe70d283bba8d575e2f3dddae51db6c61fecfc40df
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
ETag: W/&quot;93c3c251dd8ddb356dd61609db5e5d60&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 5d5463ee-cdb0-476a-bb17-d1e9e2e7bf27
X-Runtime: 0.021031
Vary: Origin
Content-Length: 115
200 OK
```


```json
{
  "id": 25,
  "wishlist_id": 38,
  "variant_id": 151,
  "quantity": 1,
  "remark": null,
  "created_at": "2020-06-04T11:40:17.509-04:00"
}
```



## Get all wished products


### Request

#### Endpoint

```plaintext
GET /api/wished_products
Accept: application/json
Authorizat IO N: Bearer c3e7d5d9466058eadaf40bc6f22ef91704a456d6401b20cd
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
ETag: W/&quot;109dec2fa6591e7dca8bbcb92a1c2839&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: f693f766-bca8-4c0b-b092-3c4fe3e0626d
X-Runtime: 0.040855
Vary: Origin
Content-Length: 436
200 OK
```


```json
{
  "wished_products": [
    {
      "id": 12,
      "wishlist_id": 31,
      "variant_id": 123,
      "quantity": 1,
      "remark": null,
      "created_at": "2020-06-04T11:40:15.189-04:00"
    },
    {
      "id": 11,
      "wishlist_id": 30,
      "variant_id": 121,
      "quantity": 1,
      "remark": null,
      "created_at": "2020-06-04T11:40:15.060-04:00"
    },
    {
      "id": 10,
      "wishlist_id": 29,
      "variant_id": 119,
      "quantity": 1,
      "remark": null,
      "created_at": "2020-06-04T11:40:14.894-04:00"
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
Authorizat IO N: Bearer ed3d8e9a8c040ca7df4a9b4800b4bd2a271d0732bd4ff493
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
ETag: W/&quot;8b6771036ce6351bd65586d981221d57&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: ea6b09df-1a4a-4eab-8e7c-c33fb588da60
X-Runtime: 0.084618
Vary: Origin
Content-Length: 2413
200 OK
```


```json
{
  "wished_products": [
    {
      "id": 15,
      "wishlist_id": 34,
      "variant_id": 129,
      "quantity": 1,
      "remark": null,
      "created_at": "2020-06-04T11:40:15.841-04:00",
      "variant": {
        "id": 129,
        "name": "Product #70 - 7275",
        "sku": "SKU-128",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-70-7275",
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
      "variant_id": 127,
      "quantity": 1,
      "remark": null,
      "created_at": "2020-06-04T11:40:15.679-04:00",
      "variant": {
        "id": 127,
        "name": "Product #69 - 6891",
        "sku": "SKU-126",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-69-6891",
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
      "variant_id": 125,
      "quantity": 1,
      "remark": null,
      "created_at": "2020-06-04T11:40:15.490-04:00",
      "variant": {
        "id": 125,
        "name": "Product #68 - 5805",
        "sku": "SKU-124",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-68-5805",
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
Authorizat IO N: Bearer ea11f606f4525b7cd31b7d3c1fc2373b5b030767b2f4fc7a
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
ETag: W/&quot;65328dc95759b934ccc11fd84dc45dc3&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 9ae28f59-f171-48d8-b57e-bf2042521f95
X-Runtime: 0.090871
Vary: Origin
Content-Length: 2351
200 OK
```


```json
{
  "wished_products": [
    {
      "id": 22,
      "wishlist_id": 37,
      "variant_id": 145,
      "quantity": 1,
      "remark": null,
      "created_at": "2020-06-04T11:40:17.006-04:00",
      "variant": {
        "id": 145,
        "name": "Product #78 - 2253",
        "sku": "SKU-144",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-78-2253",
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
      "id": 23,
      "wishlist_id": 37,
      "variant_id": 147,
      "quantity": 1,
      "remark": null,
      "created_at": "2020-06-04T11:40:17.153-04:00",
      "variant": {
        "id": 147,
        "name": "Product #79 - 484",
        "sku": "SKU-146",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-79-484",
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
    },
    {
      "id": 24,
      "wishlist_id": 37,
      "variant_id": 149,
      "quantity": 1,
      "remark": null,
      "created_at": "2020-06-04T11:40:17.263-04:00",
      "variant": {
        "id": 149,
        "name": "Product #80 - 5447",
        "sku": "SKU-148",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-80-5447",
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
Authorizat IO N: Bearer 3337fe8cfa706e4ab77355087059acc14aa39737a06dad54
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
ETag: W/&quot;6da28a73cc98b7c5fae20e445ba339e0&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 6d0e0f1c-6871-4dec-9d96-7bf36bb82baa
X-Runtime: 0.012661
Vary: Origin
Content-Length: 436
200 OK
```


```json
{
  "wished_products": [
    {
      "id": 19,
      "wishlist_id": 36,
      "variant_id": 139,
      "quantity": 1,
      "remark": null,
      "created_at": "2020-06-04T11:40:16.617-04:00"
    },
    {
      "id": 20,
      "wishlist_id": 36,
      "variant_id": 141,
      "quantity": 1,
      "remark": null,
      "created_at": "2020-06-04T11:40:16.728-04:00"
    },
    {
      "id": 21,
      "wishlist_id": 36,
      "variant_id": 143,
      "quantity": 1,
      "remark": null,
      "created_at": "2020-06-04T11:40:16.841-04:00"
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
PATCH /api/wished_products/16
Accept: application/json
Authorizat IO N: Bearer bac4fd7990bbb8867a58b1be5795cae2b5f5dbcc23499d51
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/wished_products/:id`

#### Parameters


```json
wished_product[wishlist_id]=35&wished_product[variant_id]=137&wished_product[quantity]=2&wished_product[remark]=Foo+bar
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
ETag: W/&quot;61e190954615ae2a19b4003a8e12aab9&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 878a5b0c-0700-46a5-a1dd-a3d6629e924d
X-Runtime: 0.016651
Vary: Origin
Content-Length: 120
200 OK
```


```json
{
  "id": 16,
  "wishlist_id": 35,
  "variant_id": 137,
  "quantity": 2,
  "remark": "Foo bar",
  "created_at": "2020-06-04T11:40:16.110-04:00"
}
```



# Wishlists

Update a wishlist. Users can update their own wishlists, admins can create wishlists for others.

## Create a wishlist


### Request

#### Endpoint

```plaintext
POST /api/wishlists
Accept: application/json
Authorizat IO N: Bearer 23d88baae9917d690495ade3f8c9ee1202e6397e0b395ee2
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/wishlists`

#### Parameters


```json
wishlist[name]&wishlist[user_id]=75&wishlist[is_default]=true&wishlist[is_public]=false
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
ETag: W/&quot;781bb4fb5b3fcf84b940eacd23c918be&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 02dde1e0-b0ff-4e6d-8d17-62c3fb221c16
X-Runtime: 0.015225
Vary: Origin
Content-Length: 100
201 Created
```


```json
{
  "id": 14,
  "user_id": 75,
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
DELETE /api/wishlists/2
Accept: application/json
Authorizat IO N: Bearer 7b64be525f8f0ddac3c375bcb32b7f6c87a92828bc732e6d
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
X-Request-Id: 3bff65c3-6bbc-448b-8a43-a89fb371cfbf
X-Runtime: 0.014054
Vary: Origin
204 No Content
```




## Get a single wishlist


### Request

#### Endpoint

```plaintext
GET /api/wishlists/15
Accept: application/json
Authorizat IO N: Bearer 1fc1ec60a32da1b9b4037925f6ede4f6780e755a3346eefd
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
ETag: W/&quot;8ff1ff24f1c930fb3b1dedc4b10fe245&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 4bb1fd89-2705-458a-948b-ef8194c76a05
X-Runtime: 0.011387
Vary: Origin
Content-Length: 445
200 OK
```


```json
{
  "id": 15,
  "user_id": 76,
  "name": "Wishlist #13",
  "is_public": false,
  "is_default": true,
  "wished_products": [
    {
      "id": 7,
      "wishlist_id": 15,
      "variant_id": 113,
      "quantity": 1,
      "remark": null,
      "created_at": "2020-06-04T11:40:14.433-04:00"
    },
    {
      "id": 8,
      "wishlist_id": 15,
      "variant_id": 115,
      "quantity": 1,
      "remark": null,
      "created_at": "2020-06-04T11:40:14.542-04:00"
    },
    {
      "id": 9,
      "wishlist_id": 15,
      "variant_id": 117,
      "quantity": 1,
      "remark": null,
      "created_at": "2020-06-04T11:40:14.652-04:00"
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
Authorizat IO N: Bearer 7e9dda96852bc85e1122453a31860aa93fe6c944c69245d3
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
ETag: W/&quot;473bb861b9079f35e9b18844ed426092&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: caa651a3-c2c8-4ff3-b171-6263c164c177
X-Runtime: 0.014030
Vary: Origin
Content-Length: 879
200 OK
```


```json
{
  "wishlists": [
    {
      "id": 3,
      "user_id": 63,
      "name": "Wishlist #2",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 4,
      "user_id": 64,
      "name": "Wishlist #3",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 5,
      "user_id": 65,
      "name": "Wishlist #4",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 6,
      "user_id": 66,
      "name": "Wishlist #5",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 7,
      "user_id": 67,
      "name": "Wishlist #6",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 8,
      "user_id": 68,
      "name": "Wishlist #7",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 9,
      "user_id": 69,
      "name": "Wishlist #8",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 10,
      "user_id": 70,
      "name": "Wishlist #9",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 11,
      "user_id": 71,
      "name": "Wishlist #10",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 12,
      "user_id": 72,
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
Authorizat IO N: Bearer 8833fa996bbad28d9557fc732d7d66f471d6607985c5bdaa
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
ETag: W/&quot;c4a1dfd178a7740030930382790959b2&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 5b3d65d3-5c17-4fda-8f6c-d0275bfac3aa
X-Runtime: 0.010692
Vary: Origin
Content-Length: 445
200 OK
```


```json
{
  "id": 13,
  "user_id": 74,
  "name": "Wishlist #12",
  "is_public": false,
  "is_default": true,
  "wished_products": [
    {
      "id": 4,
      "wishlist_id": 13,
      "variant_id": 107,
      "quantity": 1,
      "remark": null,
      "created_at": "2020-06-04T11:40:14.006-04:00"
    },
    {
      "id": 5,
      "wishlist_id": 13,
      "variant_id": 109,
      "quantity": 1,
      "remark": null,
      "created_at": "2020-06-04T11:40:14.116-04:00"
    },
    {
      "id": 6,
      "wishlist_id": 13,
      "variant_id": 111,
      "quantity": 1,
      "remark": null,
      "created_at": "2020-06-04T11:40:14.230-04:00"
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
Authorizat IO N: Bearer 286526ed21e309dea392b221a7d99383c9a536c0bff19da8
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
ETag: W/&quot;7e4cc5fd8f3187ed965ed0b94b21b1f6&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 245f133e-8741-4f5d-a6cb-88f4a236f4d1
X-Runtime: 0.012227
Vary: Origin
Content-Length: 903
200 OK
```


```json
{
  "wishlists": [
    {
      "id": 19,
      "user_id": 78,
      "name": "Wishlist #17",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 20,
      "user_id": 78,
      "name": "Wishlist #18",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 21,
      "user_id": 78,
      "name": "Wishlist #19",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 22,
      "user_id": 78,
      "name": "Wishlist #20",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 23,
      "user_id": 78,
      "name": "Wishlist #21",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 24,
      "user_id": 78,
      "name": "Wishlist #22",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 25,
      "user_id": 78,
      "name": "Wishlist #23",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 26,
      "user_id": 78,
      "name": "Wishlist #24",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 27,
      "user_id": 78,
      "name": "Wishlist #25",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 28,
      "user_id": 78,
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
PATCH /api/wishlists/1
Accept: application/json
Authorizat IO N: Bearer 77873d4dd4707e7f9c920d3a33976d0945451b6b5bbb94d0
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/wishlists/:id`

#### Parameters


```json
wishlist[name]=Another+Wishlist&wishlist[user_id]=61&wishlist[is_default]=true&wishlist[is_public]=false
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
ETag: W/&quot;e5314b439e6341b1506788ac64ef18c1&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 021b8d4e-bd87-49e1-9c2b-4d5fd9a18bd1
X-Runtime: 0.045608
Vary: Origin
Content-Length: 445
200 OK
```


```json
{
  "id": 1,
  "user_id": 61,
  "name": "Another Wishlist",
  "is_public": false,
  "is_default": true,
  "wished_products": [
    {
      "id": 1,
      "wishlist_id": 1,
      "variant_id": 101,
      "quantity": 1,
      "remark": null,
      "created_at": "2020-06-04T11:40:13.363-04:00"
    },
    {
      "id": 2,
      "wishlist_id": 1,
      "variant_id": 103,
      "quantity": 1,
      "remark": null,
      "created_at": "2020-06-04T11:40:13.470-04:00"
    },
    {
      "id": 3,
      "wishlist_id": 1,
      "variant_id": 105,
      "quantity": 1,
      "remark": null,
      "created_at": "2020-06-04T11:40:13.582-04:00"
    }
  ]
}
```



