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
PUT /api/orders/M066555901/addresses/2
Accept: application/json
X-Spree-Order-Token: HXGtA8pxW-v-61qycSP-yQ
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
ETag: W/&quot;531b07d9aec3b0759e560a271f141f77&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: ccece6cf-694e-4fb4-b5a0-a62121af5d97
X-Runtime: 0.074456
Vary: Origin
Content-Length: 501
200 OK
```


```json
{
  "id": 3,
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
X-Spree-Order-Token: XdVfXEJpgsZ-JevIUj6OSA
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/braintree/transactions`

#### Parameters


```json
order_id=M230792216&payment_method_id=27&options[restart_checkout]=true&transaction[email]=maryellen.oga%40mckenziemcglynn.com&transaction[nonce]=fake-paypal-billing-agreement-nonce&transaction[phone]=555-555-0199&transaction[shipping_address_attributes][first_name]=John&transaction[shipping_address_attributes][last_name]=Stamm&transaction[shipping_address_attributes][address_line_1]=A+Different+Road&transaction[shipping_address_attributes][city]=Herndon&transaction[shipping_address_attributes][state_code]=AL&transaction[shipping_address_attributes][zip]=10046&transaction[shipping_address_attributes][country_code]=US&transaction[payment_type]=PayPalAccount&transaction[billing_address_attributes][first_name]=John&transaction[billing_address_attributes][last_name]=Stamm&transaction[billing_address_attributes][address_line_1]=A+Different+Road&transaction[billing_address_attributes][city]=Herndon&transaction[billing_address_attributes][state_code]=AL&transaction[billing_address_attributes][zip]=10046&transaction[billing_address_attributes][country_code]=US
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
ETag: W/&quot;678574887d8c3c2feb69133231115fa3&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 92f1379b-a2e0-4274-839b-0d9e4a3d0f8a
X-Runtime: 0.270724
Vary: Origin
Content-Length: 5380
200 OK
```


```json
{
  "id": 25,
  "number": "M230792216",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2020-01-14T07:43:31.127-05:00",
  "updated_at": "2020-01-14T07:43:31.369-05:00",
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
  "token": "XdVfXEJpgsZ-JevIUj6OSA",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order&order=M230792216&bzip=10046&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [
    {
      "id": 27,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 49,
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
    "country_id": 46,
    "country_iso": "US",
    "state_id": 46,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 46,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 46,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 46
    }
  },
  "ship_address": {
    "id": 50,
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
    "country_id": 46,
    "country_iso": "US",
    "state_id": 46,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 46,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 46,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 46
    }
  },
  "line_items": [
    {
      "id": 28,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 147,
      "vendor_id": 265,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 147,
        "name": "Product #79 - 5516",
        "sku": "SKU-146",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-79-5516",
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
        "product_id": 79,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [

      ],
      "vendor_name": "Vendor #265",
      "country_iso": "US",
      "adjustments": [

      ]
    }
  ],
  "payments": [
    {
      "id": 9,
      "source_type": "SolidusPaypalBraintree::Source",
      "source_id": 9,
      "amount": "110.0",
      "display_amount": "$110.00",
      "payment_method_id": 27,
      "state": "checkout",
      "avs_response": null,
      "created_at": "2020-01-14T07:43:31.237-05:00",
      "updated_at": "2020-01-14T07:43:31.237-05:00",
      "payment_method": {
        "id": 27,
        "name": "Braintree"
      },
      "source": {
        "id": 9,
        "payment_type": "PayPalAccount",
        "token": "bgx899",
        "created_at": "2020-01-14T07:43:31.236-05:00",
        "email": "jane.doe@paypal.com"
      }
    }
  ],
  "shipments": [
    {
      "id": 28,
      "tracking": null,
      "tracking_url": null,
      "number": "H55376572867",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M230792216",
      "stock_location_name": "NY Warehouse",
      "giftwrappable": false,
      "stock_location_id": 53,
      "giftwrap": null,
      "shipping_rates": [
        {
          "id": 28,
          "name": "UPS Ground",
          "admin_name": null,
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 23,
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
        "shipping_method_id": 23,
        "shipping_method_code": "UPS_GROUND",
        "extra_cost": "",
        "is_flat_rate": false,
        "is_flat_rate_expedited": false,
        "is_free_shipping": false,
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 23,
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
              "id": 44,
              "name": "ShippingCategory #42"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 147,
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
      "delivery_estimation": "Jan 16"
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
X-Spree-Order-Token: NpB87Up0VHPccBP_HmsZwA
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/braintree/transactions`

#### Parameters


```json
order_id=M872235295&payment_method_id=28&options[restart_checkout]=true&transaction[email]=maryellen.oga%40mckenziemcglynn.com&transaction[nonce]=fake-apple-pay-visa-nonce&transaction[phone]=555-555-0199&transaction[shipping_address_attributes][first_name]=John&transaction[shipping_address_attributes][last_name]=Stamm&transaction[shipping_address_attributes][address_line_1]=A+Different+Road&transaction[shipping_address_attributes][city]=Herndon&transaction[shipping_address_attributes][state_code]=AL&transaction[shipping_address_attributes][zip]=10048&transaction[shipping_address_attributes][country_code]=US&transaction[payment_type]=ApplePayCard
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
ETag: W/&quot;94d19f54bdcdb093b0635553cc868997&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: e904f0e3-c34e-477f-b3a6-d9bb85643f11
X-Runtime: 0.222280
Vary: Origin
Content-Length: 5429
200 OK
```


```json
{
  "id": 26,
  "number": "M872235295",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2020-01-14T07:43:31.645-05:00",
  "updated_at": "2020-01-14T07:43:31.842-05:00",
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
  "token": "NpB87Up0VHPccBP_HmsZwA",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order&order=M872235295&bzip=10048&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [
    {
      "id": 28,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
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
    "zipcode": "10048",
    "phone": "555-555-0199",
    "company": null,
    "alternative_phone": null,
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
    "id": 54,
    "firstname": "John",
    "lastname": "Stamm",
    "full_name": "John Stamm",
    "address1": "A Different Road",
    "address2": null,
    "city": "Herndon",
    "zipcode": "10048",
    "phone": "555-555-0199",
    "company": null,
    "alternative_phone": null,
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
      "id": 29,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 149,
      "vendor_id": 270,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 149,
        "name": "Product #80 - 8491",
        "sku": "SKU-148",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-80-8491",
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
      "vendor_name": "Vendor #270",
      "country_iso": "US",
      "adjustments": [

      ]
    }
  ],
  "payments": [
    {
      "id": 10,
      "source_type": "SolidusPaypalBraintree::Source",
      "source_id": 10,
      "amount": "110.0",
      "display_amount": "$110.00",
      "payment_method_id": 28,
      "state": "checkout",
      "avs_response": null,
      "created_at": "2020-01-14T07:43:31.727-05:00",
      "updated_at": "2020-01-14T07:43:31.727-05:00",
      "payment_method": {
        "id": 28,
        "name": "Braintree"
      },
      "source": {
        "id": 10,
        "payment_type": "ApplePayCard",
        "token": "cg7hsk",
        "created_at": "2020-01-14T07:43:31.726-05:00",
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
      "number": "H44374573063",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M872235295",
      "stock_location_name": "NY Warehouse",
      "giftwrappable": false,
      "stock_location_id": 54,
      "giftwrap": null,
      "shipping_rates": [
        {
          "id": 30,
          "name": "UPS Ground",
          "admin_name": null,
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 24,
          "shipping_method_code": "UPS_GROUND",
          "extra_cost": "",
          "is_flat_rate": false,
          "is_flat_rate_expedited": false,
          "is_free_shipping": false,
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 30,
        "name": "UPS Ground",
        "admin_name": null,
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 24,
        "shipping_method_code": "UPS_GROUND",
        "extra_cost": "",
        "is_flat_rate": false,
        "is_flat_rate_expedited": false,
        "is_free_shipping": false,
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 24,
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
              "id": 45,
              "name": "ShippingCategory #43"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 149,
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
      "delivery_estimation": "Jan 16"
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
PUT /api/checkouts/M363816863/complete
Accept: application/json
X-Spree-Order-Token: AZcd33iKw-UO0V63CMrj9g
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
ETag: W/&quot;dfd13fdbc65156cf858028e6ce68cc98&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: ed5be4bd-7045-4f3d-a9a1-71448b09e381
X-Runtime: 0.469179
Vary: Origin
Content-Length: 5530
200 OK
```


```json
{
  "id": 6,
  "number": "M363816863",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "complete",
  "adjustment_total": "0.0",
  "user_id": 35,
  "created_at": "2020-01-14T07:43:18.227-05:00",
  "updated_at": "2020-01-14T07:43:18.717-05:00",
  "completed_at": "2020-01-14T07:43:18.717-05:00",
  "payment_total": "110.0",
  "shipment_state": "ready",
  "payment_state": "paid",
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
  "display_item_total": "$10.00",
  "total_quantity": 1,
  "display_total": "$110.00",
  "display_ship_total": "$100.00",
  "display_tax_total": "$0.00",
  "token": "AZcd33iKw-UO0V63CMrj9g",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order&order=M363816863&bzip=10010&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [
    {
      "id": 4,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    },
    {
      "id": 5,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 11,
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
    "id": 12,
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
      "id": 4,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 39,
      "vendor_id": 76,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 39,
        "name": "Product #25 - 2012",
        "sku": "SKU-38",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-25-2012",
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
      "vendor_name": "Vendor #76",
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
      "created_at": "2020-01-14T07:43:18.367-05:00",
      "updated_at": "2020-01-14T07:43:18.589-05:00",
      "payment_method": {
        "id": 4,
        "name": "Braintree"
      },
      "source": {
        "id": 4,
        "payment_type": "CreditCard",
        "token": "4rptfz",
        "created_at": "2020-01-14T07:43:18.365-05:00",
        "cc_type": "Visa",
        "last_digits": "1881",
        "month": "12",
        "year": "2020"
      }
    }
  ],
  "shipments": [
    {
      "id": 6,
      "tracking": "U10000",
      "tracking_url": null,
      "number": "H14534762717",
      "cost": "100.0",
      "shipped_at": null,
      "state": "ready",
      "order_id": "M363816863",
      "stock_location_name": "NY Warehouse",
      "giftwrappable": false,
      "stock_location_id": 17,
      "giftwrap": null,
      "shipping_rates": [
        {
          "id": 6,
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
        "id": 6,
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
              "id": 4,
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
      "stock_location_address": "NY Warehouse, Washington, AL",
      "country_iso": "US",
      "international_shipping": false,
      "delivery_estimation": "Jan 16"
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
PATCH /api/checkouts/M206757045
Accept: application/json
X-Spree-Order-Token: rBfzT0J0O-2aADNYbENf4g
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
ETag: W/&quot;f86c660382a66c3d6d1cb121f2dc3b66&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 4fc91c34-6a60-4634-80df-cb3f442e892b
X-Runtime: 0.177810
Vary: Origin
Content-Length: 4920
200 OK
```


```json
{
  "id": 9,
  "number": "M206757045",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 38,
  "created_at": "2020-01-14T07:43:20.152-05:00",
  "updated_at": "2020-01-14T07:43:20.467-05:00",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "email38@example.com",
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
  "token": "rBfzT0J0O-2aADNYbENf4g",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order&order=M206757045&bzip=10016&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [
    {
      "id": 8,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 17,
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
  "ship_address": {
    "id": 18,
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
  "line_items": [
    {
      "id": 7,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 45,
      "vendor_id": 91,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 45,
        "name": "Product #28 - 4297",
        "sku": "SKU-44",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-28-4297",
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
            "id": 17,
            "name": "Size-17",
            "presentation": "S",
            "option_type_name": "foo-size-17",
            "option_type_id": 17,
            "option_type_presentation": "Size",
            "position": 1
          }
        ],
        "images": [

        ],
        "product_id": 28,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [

      ],
      "vendor_name": "Vendor #91",
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
      "number": "H06618086428",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M206757045",
      "stock_location_name": "NY Warehouse",
      "giftwrappable": false,
      "stock_location_id": 20,
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
          "is_flat_rate": false,
          "is_flat_rate_expedited": false,
          "is_free_shipping": false,
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
              "id": 7,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 17,
              "name": "ShippingCategory #17"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 45,
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
      "delivery_estimation": "Jan 16"
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
PATCH /api/checkouts/M835914494
Accept: application/json
X-Spree-Order-Token: JNRQc4ZtDnP70KpXCqijtQ
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
ETag: W/&quot;55afa76bca8cb3ed5558b552e1dc8265&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: e4dd63ef-6065-46d9-82ca-302e60cc4f10
X-Runtime: 0.118560
Vary: Origin
Content-Length: 4917
200 OK
```


```json
{
  "id": 7,
  "number": "M835914494",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 36,
  "created_at": "2020-01-14T07:43:19.095-05:00",
  "updated_at": "2020-01-14T07:43:19.356-05:00",
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
  "display_item_total": "$10.00",
  "total_quantity": 1,
  "display_total": "$110.00",
  "display_ship_total": "$100.00",
  "display_tax_total": "$0.00",
  "token": "JNRQc4ZtDnP70KpXCqijtQ",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order&order=M835914494&bzip=10012&init=true",
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
    "id": 13,
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
    "id": 14,
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
      "id": 5,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 41,
      "vendor_id": 81,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 41,
        "name": "Product #26 - 5407",
        "sku": "SKU-40",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-26-5407",
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
      "vendor_name": "Vendor #81",
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
      "number": "H06012141478",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M835914494",
      "stock_location_name": "NY Warehouse",
      "giftwrappable": false,
      "stock_location_id": 18,
      "giftwrap": null,
      "shipping_rates": [
        {
          "id": 8,
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
        }
      ],
      "selected_shipping_rate": {
        "id": 8,
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
              "id": 5,
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
      "stock_location_address": "NY Warehouse, Washington, AL",
      "country_iso": "US",
      "international_shipping": false,
      "delivery_estimation": "Jan 16"
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
PATCH /api/checkouts/M235980666
Accept: application/json
X-Spree-Order-Token: 8MM_jEo6ID9tByBn5t2KrA
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
ETag: W/&quot;2803e529317aaf55e65e772fc448165c&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 0a00427c-fa76-48c1-8f71-29ac98a852ef
X-Runtime: 0.126492
Vary: Origin
Content-Length: 4920
200 OK
```


```json
{
  "id": 8,
  "number": "M235980666",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 37,
  "created_at": "2020-01-14T07:43:19.646-05:00",
  "updated_at": "2020-01-14T07:43:19.852-05:00",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "email37@example.com",
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
  "token": "8MM_jEo6ID9tByBn5t2KrA",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order&order=M235980666&bzip=10014&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [
    {
      "id": 7,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 15,
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
    "country_id": 17,
    "country_iso": "US",
    "state_id": 17,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 17,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 17,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 17
    }
  },
  "ship_address": {
    "id": 16,
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
    "country_id": 17,
    "country_iso": "US",
    "state_id": 17,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 17,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 17,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 17
    }
  },
  "line_items": [
    {
      "id": 6,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 43,
      "vendor_id": 86,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 43,
        "name": "Product #27 - 9220",
        "sku": "SKU-42",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-27-9220",
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
            "id": 16,
            "name": "Size-16",
            "presentation": "S",
            "option_type_name": "foo-size-16",
            "option_type_id": 16,
            "option_type_presentation": "Size",
            "position": 1
          }
        ],
        "images": [

        ],
        "product_id": 27,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [

      ],
      "vendor_name": "Vendor #86",
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
      "number": "H76375871722",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M235980666",
      "stock_location_name": "NY Warehouse",
      "giftwrappable": false,
      "stock_location_id": 19,
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
              "id": 6,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 16,
              "name": "ShippingCategory #16"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 43,
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
      "delivery_estimation": "Jan 16"
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
PATCH /api/checkouts/M940562048
Accept: application/json
X-Spree-Order-Token: wmDIKobwON7bc4QEIw9DZQ
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
ETag: W/&quot;a952db4c14f7d1c82ba039884d4b5fb1&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 79c4346f-9493-4dc1-b7ce-549e630d9a09
X-Runtime: 0.138440
Vary: Origin
Content-Length: 4924
200 OK
```


```json
{
  "id": 10,
  "number": "M940562048",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 39,
  "created_at": "2020-01-14T07:43:20.795-05:00",
  "updated_at": "2020-01-14T07:43:21.020-05:00",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "email39@example.com",
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
  "token": "wmDIKobwON7bc4QEIw9DZQ",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order&order=M940562048&bzip=10018&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [
    {
      "id": 9,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 19,
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
  "ship_address": {
    "id": 20,
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
  "line_items": [
    {
      "id": 8,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 47,
      "vendor_id": 96,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 47,
        "name": "Product #29 - 2099",
        "sku": "SKU-46",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-29-2099",
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
        "product_id": 29,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [

      ],
      "vendor_name": "Vendor #96",
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
      "number": "H62775601305",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M940562048",
      "stock_location_name": "NY Warehouse",
      "giftwrappable": false,
      "stock_location_id": 21,
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
          "is_flat_rate": false,
          "is_flat_rate_expedited": false,
          "is_free_shipping": false,
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
              "id": 8,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 18,
              "name": "ShippingCategory #18"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 47,
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
      "delivery_estimation": "Jan 16"
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
PUT /api/checkouts/M454359878
Accept: application/json
X-Spree-Order-Token: O-_m0cLvJkun35ROhYLV0w
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PUT /api/checkouts/:id`

#### Parameters


```json
order[ship_address_attributes][id]&order[ship_address_attributes][firstname]=John&order[ship_address_attributes][lastname]&order[ship_address_attributes][address1]=10+Lovely+Street&order[ship_address_attributes][address2]=Northwest&order[ship_address_attributes][city]=Herndon&order[ship_address_attributes][zipcode]=10009&order[ship_address_attributes][phone]=555-555-0199&order[ship_address_attributes][state_name]&order[ship_address_attributes][alternative_phone]=555-555-0199&order[ship_address_attributes][company]=Company&order[ship_address_attributes][state_id]=14&order[ship_address_attributes][country_id]=14&order[ship_address_attributes][created_at]&order[ship_address_attributes][updated_at]&order[use_billing]=true&hold_state=true
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
ETag: W/&quot;01151e128a421d3bce62bf528eb9d837&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 73d81945-7f58-4b2a-9baa-7e6f0a1988e4
X-Runtime: 0.179725
Vary: Origin
Content-Length: 4825
200 OK
```


```json
{
  "id": 5,
  "number": "M454359878",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "cart",
  "adjustment_total": "0.0",
  "user_id": 34,
  "created_at": "2020-01-14T07:43:17.784-05:00",
  "updated_at": "2020-01-14T07:43:17.866-05:00",
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
  "token": "O-_m0cLvJkun35ROhYLV0w",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order&order=M454359878&bzip=10009&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [

  ],
  "bill_address": {
    "id": 10,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "10 Lovely Street",
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
  "ship_address": {
    "id": 10,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "10 Lovely Street",
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
      "id": 3,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 37,
      "vendor_id": 71,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 37,
        "name": "Product #24 - 5726",
        "sku": "SKU-36",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-24-5726",
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
      "id": 5,
      "tracking": "U10000",
      "tracking_url": null,
      "number": "H54271337126",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M454359878",
      "stock_location_name": "NY Warehouse",
      "giftwrappable": false,
      "stock_location_id": 16,
      "giftwrap": null,
      "shipping_rates": [
        {
          "id": 5,
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
        "id": 5,
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
              "id": 3,
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
      "stock_location_address": "NY Warehouse, Washington, AL",
      "country_iso": "US",
      "international_shipping": false,
      "delivery_estimation": "Jan 16"
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
POST /api/shipments/H84454510846/giftwrap
Accept: application/json
X-Spree-Order-Token: _dfnHsmRX1vJFvDJcm8EjQ
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/shipments/:shipment_number/giftwrap`

#### Parameters


```json
order_number=M016393410
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
X-Request-Id: 7035c483-006e-4f4a-84f5-9a61288fc8ac
X-Runtime: 0.077677
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
DELETE /api/shipments/H68648486086/giftwrap
Accept: application/json
X-Spree-Order-Token: 4-VTAm1jWXa90sXbk8SHFQ
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`DELETE /api/shipments/:shipment_number/giftwrap`

#### Parameters


```json
order_number=M421544188
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
X-Request-Id: 32e0f861-64f9-47eb-8dba-8ddb817d08c6
X-Runtime: 0.017828
Vary: Origin
204 No Content
```




# LineItem

Representation of a single cart item for a specific variant with price of vendor

## Creating a line item


### Request

#### Endpoint

```plaintext
POST /api/orders/M202259854/line_items
Accept: application/json
X-Spree-Order-Token: 2SQj4lMaHER-sqf7xAx64w
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/:order_number/line_items`

#### Parameters


```json
line_item[variant_id]=127&line_item[options][vendor_id]=217
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
ETag: W/&quot;97cff5bb3d59957673f2a18763eb4690&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 8b6177ac-f8b2-41db-9505-f98c3ad2a364
X-Runtime: 0.078008
Vary: Origin
Content-Length: 942
201 Created
```


```json
{
  "id": 21,
  "quantity": 1,
  "price": "19.99",
  "variant_id": 127,
  "vendor_id": 217,
  "single_display_amount": "$19.99",
  "display_amount": "$19.99",
  "total": "19.99",
  "on_sale": false,
  "final_sale": false,
  "backordered": null,
  "promotionable": true,
  "variant": {
    "id": 127,
    "name": "Product #69 - 5463",
    "sku": "SKU-126",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": false,
    "slug": "product-69-5463",
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
  "vendor_name": "Vendor #217",
  "country_iso": null,
  "adjustments": [

  ]
}
```



## Creating a line item gift card


### Request

#### Endpoint

```plaintext
POST /api/orders/M454997540/line_items
Accept: application/json
X-Spree-Order-Token: TkeUXx6XV314OrO3KAaeVA
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/:order_number/line_items`

#### Parameters


```json
line_item[variant_id]=121&line_item[options][vendor_id]=208&line_item[options][gift_card_details][recipient_name]=Recipient+John&line_item[options][gift_card_details][recipient_email]=recipient%40email.com&line_item[options][gift_card_details][purchaser_name]=Purchaser+Bob&line_item[options][gift_card_details][gift_message]=Surprise&line_item[options][gift_card_details][send_email_at]=2020-01-14+07%3A43%3A27+-0500
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
ETag: W/&quot;25367c69d3ad1889bf1f854e7e87486c&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 4d4a34e7-d12a-4803-a5af-b80f6788aff0
X-Runtime: 0.107659
Vary: Origin
Content-Length: 1078
201 Created
```


```json
{
  "id": 19,
  "quantity": 1,
  "price": "19.99",
  "variant_id": 121,
  "vendor_id": 208,
  "single_display_amount": "$19.99",
  "display_amount": "$19.99",
  "total": "19.99",
  "on_sale": false,
  "final_sale": false,
  "backordered": null,
  "promotionable": true,
  "variant": {
    "id": 121,
    "name": "Product #65 - 2337",
    "sku": "SKU-121",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": false,
    "slug": "product-65-2337",
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

    ],
    "product_id": 65,
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
      "send_email_at": "2020-01-14T00:00:00.000-05:00"
    }
  ],
  "vendor_name": "Vendor #208",
  "country_iso": null,
  "adjustments": [

  ]
}
```



## Deleting a line item


### Request

#### Endpoint

```plaintext
DELETE /api/orders/M093326691/line_items/22
Accept: application/json
X-Spree-Order-Token: hk7TM2ucW-sH3HhD45MbSQ
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
X-Request-Id: cb3731e2-51fe-4f86-a724-4a8e763bf1ec
X-Runtime: 0.055065
Vary: Origin
204 No Content
```




## Updating a line item


### Request

#### Endpoint

```plaintext
PUT /api/orders/M974227396/line_items/23
Accept: application/json
X-Spree-Order-Token: k8fE3D6EejHeZ7HbcIJ9tg
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
ETag: W/&quot;bc7addff97cba6d3abe89bc3d4cd9b2e&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: c34d60ad-a53e-4f27-8786-eddac98c4db4
X-Runtime: 0.098715
Vary: Origin
Content-Length: 939
200 OK
```


```json
{
  "id": 23,
  "quantity": 2,
  "price": "10.0",
  "variant_id": 131,
  "vendor_id": 227,
  "single_display_amount": "$10.00",
  "display_amount": "$20.00",
  "total": "20.0",
  "on_sale": false,
  "final_sale": false,
  "backordered": null,
  "promotionable": true,
  "variant": {
    "id": 131,
    "name": "Product #71 - 4365",
    "sku": "SKU-130",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": false,
    "slug": "product-71-4365",
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
    "product_id": 71,
    "lead_time": 2,
    "brand": null,
    "brand_slug": null,
    "brand_description": null
  },
  "monogram": null,
  "gift_cards": [

  ],
  "vendor_name": "Vendor #227",
  "country_iso": "US",
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
Authorizat IO N: Bearer e78c32a8e47afd024744b7b92f71913fb9b325d9050a5d6e
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/minis`

#### Parameters


```json
mini[name]=Winny&mini[user_id]=87&mini[birth_year]=2019&mini[birth_month]=1&mini[birth_day]=1
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
ETag: W/&quot;5ed5baf7a1557756e0f4023d887db445&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 0ec92816-a0d5-43e9-824a-63666e5b03ce
X-Runtime: 0.011710
Vary: Origin
Content-Length: 163
201 Created
```


```json
{
  "id": 19,
  "user_id": 87,
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
DELETE /api/minis/6
Accept: application/json
Authorizat IO N: Bearer 17a524502c20f335d6e4eb68b534544ca79587d99267966c
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
X-Request-Id: ebe9c2c4-c898-433f-b5eb-983e7ba83df8
X-Runtime: 0.006758
Vary: Origin
204 No Content
```




## Get a single mini


### Request

#### Endpoint

```plaintext
GET /api/minis/7
Accept: application/json
Authorizat IO N: Bearer 313b780a1b5f12cdc34a68d8a505db8cf02024f134fae6e4
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
ETag: W/&quot;34fe62bd65626e91701012ac9b6201f3&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 7344d138-3388-4118-9c38-37895b85af53
X-Runtime: 0.009747
Vary: Origin
Content-Length: 162
200 OK
```


```json
{
  "id": 7,
  "user_id": 74,
  "name": "Mini",
  "birth_year": 2020,
  "birth_month": 1,
  "birth_day": 13,
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
Authorizat IO N: Bearer 7ae087a92af7fa9e1d3af087681a33f703a8a1bf4ef5cb92
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
ETag: W/&quot;0fc2ac7cb11498f6b686a5f566b606fb&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: f22f8f53-9c20-4107-8750-3f0e4706611c
X-Runtime: 0.038551
Vary: Origin
Content-Length: 1719
200 OK
```


```json
{
  "minis": [
    {
      "id": 18,
      "user_id": 85,
      "name": "Mini",
      "birth_year": 2020,
      "birth_month": 1,
      "birth_day": 13,
      "gender_boy": true,
      "gender_girl": true,
      "gender_taxons": [

      ],
      "age_range_taxons": [

      ]
    },
    {
      "id": 17,
      "user_id": 84,
      "name": "Mini",
      "birth_year": 2020,
      "birth_month": 1,
      "birth_day": 13,
      "gender_boy": true,
      "gender_girl": true,
      "gender_taxons": [

      ],
      "age_range_taxons": [

      ]
    },
    {
      "id": 16,
      "user_id": 83,
      "name": "Mini",
      "birth_year": 2020,
      "birth_month": 1,
      "birth_day": 13,
      "gender_boy": true,
      "gender_girl": true,
      "gender_taxons": [

      ],
      "age_range_taxons": [

      ]
    },
    {
      "id": 15,
      "user_id": 82,
      "name": "Mini",
      "birth_year": 2020,
      "birth_month": 1,
      "birth_day": 13,
      "gender_boy": true,
      "gender_girl": true,
      "gender_taxons": [

      ],
      "age_range_taxons": [

      ]
    },
    {
      "id": 14,
      "user_id": 81,
      "name": "Mini",
      "birth_year": 2020,
      "birth_month": 1,
      "birth_day": 13,
      "gender_boy": true,
      "gender_girl": true,
      "gender_taxons": [

      ],
      "age_range_taxons": [

      ]
    },
    {
      "id": 13,
      "user_id": 80,
      "name": "Mini",
      "birth_year": 2020,
      "birth_month": 1,
      "birth_day": 13,
      "gender_boy": true,
      "gender_girl": true,
      "gender_taxons": [

      ],
      "age_range_taxons": [

      ]
    },
    {
      "id": 12,
      "user_id": 79,
      "name": "Mini",
      "birth_year": 2020,
      "birth_month": 1,
      "birth_day": 13,
      "gender_boy": true,
      "gender_girl": true,
      "gender_taxons": [

      ],
      "age_range_taxons": [

      ]
    },
    {
      "id": 11,
      "user_id": 78,
      "name": "Mini",
      "birth_year": 2020,
      "birth_month": 1,
      "birth_day": 13,
      "gender_boy": true,
      "gender_girl": true,
      "gender_taxons": [

      ],
      "age_range_taxons": [

      ]
    },
    {
      "id": 10,
      "user_id": 77,
      "name": "Mini",
      "birth_year": 2020,
      "birth_month": 1,
      "birth_day": 13,
      "gender_boy": true,
      "gender_girl": true,
      "gender_taxons": [

      ],
      "age_range_taxons": [

      ]
    },
    {
      "id": 9,
      "user_id": 76,
      "name": "Mini",
      "birth_year": 2020,
      "birth_month": 1,
      "birth_day": 13,
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
Authorizat IO N: Bearer 8823614ab1bef9ca59bde2af1688ea2f57f6821b260dcc07
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
ETag: W/&quot;02191ced78b06f5f9913cef217ed0030&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 856f591a-cb51-44c4-ac32-81d696e134b0
X-Runtime: 0.042828
Vary: Origin
Content-Length: 404
200 OK
```


```json
{
  "minis": [
    {
      "id": 5,
      "user_id": 72,
      "name": "Mini",
      "birth_year": 2020,
      "birth_month": 1,
      "birth_day": 13,
      "gender_boy": true,
      "gender_girl": true,
      "gender_taxons": [

      ],
      "age_range_taxons": [

      ]
    },
    {
      "id": 4,
      "user_id": 72,
      "name": "Mini",
      "birth_year": 2020,
      "birth_month": 1,
      "birth_day": 13,
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
Authorizat IO N: Bearer 48602f070b0f5319f506a49e71e885694139643d3d24f0af
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
ETag: W/&quot;d1c4a51744e0a325c06f0769e9070d4f&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 39fc9457-6843-4827-9d55-15b4753ac32a
X-Runtime: 0.010742
Vary: Origin
Content-Length: 163
200 OK
```


```json
{
  "id": 8,
  "user_id": 75,
  "name": "Marge",
  "birth_year": 2020,
  "birth_month": 1,
  "birth_day": 13,
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
user_id&order_token&line_item[variant_id]=99&line_item[quantity]=1&line_item[vendor_id]=162&line_item[gift_card_details_attributes][recipient_name]=Recipient+John&line_item[gift_card_details_attributes][recipient_email]=recipient%40email.com&line_item[gift_card_details_attributes][purchaser_name]=Purchaser+Bob&line_item[gift_card_details_attributes][gift_message]=Surprise&line_item[gift_card_details_attributes][send_email_at]=2020-01-14
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
ETag: W/&quot;c6aa4f3a4b799c968374bd4118e12c09&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 9f86f322-384c-459b-bc95-efd2ca74823b
X-Runtime: 0.173656
Vary: Origin
Content-Length: 2817
200 OK
```


```json
{
  "id": 12,
  "number": "M217169730",
  "item_total": "19.99",
  "total": "19.99",
  "ship_total": "0.0",
  "state": "cart",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2020-01-14T07:43:24.624-05:00",
  "updated_at": "2020-01-14T07:43:24.658-05:00",
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
  "token": "fv1cTJ1Kk96_1ie0hVaXbg",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order&order=M217169730&bzip=&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [

  ],
  "bill_address": null,
  "ship_address": null,
  "line_items": [
    {
      "id": 10,
      "quantity": 1,
      "price": "19.99",
      "variant_id": 99,
      "vendor_id": 162,
      "single_display_amount": "$19.99",
      "display_amount": "$19.99",
      "total": "19.99",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 99,
        "name": "Product #54 - 9923",
        "sku": "SKU-99",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-54-9923",
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
        "product_id": 54,
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
          "send_email_at": "2020-01-14T00:00:00.000-05:00"
        }
      ],
      "vendor_name": "Vendor #162",
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
user_id&order_token&line_item[variant_id]=107&line_item[quantity]=2&line_item[vendor_id]=175
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
ETag: W/&quot;0307ee008706d8710c16ad7ce77f3c37&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 24f18097-9f0b-4161-9584-4c5401dc47b7
X-Runtime: 0.085231
Vary: Origin
Content-Length: 2638
200 OK
```


```json
{
  "id": 14,
  "number": "M686717564",
  "item_total": "39.98",
  "total": "39.98",
  "ship_total": "0.0",
  "state": "cart",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2020-01-14T07:43:25.709-05:00",
  "updated_at": "2020-01-14T07:43:25.741-05:00",
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
  "token": "BjOqtrw-tbfTXr-Dqv9LfQ",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order&order=M686717564&bzip=&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [

  ],
  "bill_address": null,
  "ship_address": null,
  "line_items": [
    {
      "id": 13,
      "quantity": 2,
      "price": "19.99",
      "variant_id": 107,
      "vendor_id": 175,
      "single_display_amount": "$19.99",
      "display_amount": "$39.98",
      "total": "39.98",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 107,
        "name": "Product #59 - 7689",
        "sku": "SKU-106",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-59-7689",
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
        "product_id": 59,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [

      ],
      "vendor_name": "Vendor #175",
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
Authorizat IO N: Bearer edb5f8a851dcc62328598d95c9319775ed755efb5ef31829
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
ETag: W/&quot;e3b7158ce900e2bdc01b46bd141c2943&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 0c1a10f3-57b2-4569-be7d-952f6506dece
X-Runtime: 0.023522
Vary: Origin
Content-Length: 310
200 OK
```


```json
{
  "orders": [
    {
      "number": "M548944137",
      "completed_at": "2020-01-14T07:43:25.247-05:00",
      "total": "120.0",
      "state": "Complete",
      "shipment_state": "shipped",
      "shipments": [
        {
          "number": "H61685812178",
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
GET /api/orders/M514470096
Accept: application/json
Authorizat IO N: Bearer 4ea836750399bbf9a5ef8eb241c2fa2395d56b84fee7f3e0
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
ETag: W/&quot;395c303c0f92425b9e84a20578a9a10b&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: e4954858-4034-4cc8-bee9-ba80d01d9f56
X-Runtime: 0.138611
Vary: Origin
Content-Length: 10092
200 OK
```


```json
{
  "id": 16,
  "number": "M514470096",
  "item_total": "20.0",
  "total": "120.0",
  "ship_total": "100.0",
  "state": "complete",
  "adjustment_total": "0.0",
  "user_id": 63,
  "created_at": "2020-01-14T07:43:26.656-05:00",
  "updated_at": "2020-01-14T07:43:26.841-05:00",
  "completed_at": "2020-01-14T07:43:26.721-05:00",
  "payment_total": "120.0",
  "shipment_state": "shipped",
  "payment_state": "paid",
  "email": "email62@example.com",
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
  "token": "JlcAqkKFC-TnJnanuRZBFA",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order&order=M514470096&bzip=10028&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [
    {
      "id": 17,
      "name": "Credit Card",
      "partial_name": "gateway",
      "method_type": "gateway"
    },
    {
      "id": 18,
      "name": "Credit Card",
      "partial_name": "gateway",
      "method_type": "gateway"
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
    "zipcode": "10028",
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
    "id": 30,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "A Different Road",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10029",
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
      "id": 16,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 113,
      "vendor_id": 192,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 113,
        "name": "Product #62 - 3735",
        "sku": "SKU-112",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-62-3735",
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
        "product_id": 62,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [

      ],
      "vendor_name": "Vendor #192",
      "country_iso": "US",
      "adjustments": [
        {
          "id": 19,
          "source_type": "Spree::TaxRate",
          "source_id": 3,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 16,
          "amount": "2.0",
          "label": "VAT 5%",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2020-01-14T07:43:26.818-05:00",
          "updated_at": "2020-01-14T07:43:26.827-05:00",
          "display_amount": "$2.00"
        },
        {
          "id": 13,
          "source_type": "Spree::PromotionAction",
          "source_id": 3,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 16,
          "amount": "5.0",
          "label": "foo",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2020-01-14T07:43:26.777-05:00",
          "updated_at": "2020-01-14T07:43:26.777-05:00",
          "display_amount": "$5.00"
        },
        {
          "id": 12,
          "source_type": "Spree::PromotionAction",
          "source_id": 3,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 16,
          "amount": "5.0",
          "label": "foo",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2020-01-14T07:43:26.771-05:00",
          "updated_at": "2020-01-14T07:43:26.771-05:00",
          "display_amount": "$5.00"
        }
      ]
    },
    {
      "id": 17,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 115,
      "vendor_id": 192,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 115,
        "name": "Product #63 - 4102",
        "sku": "SKU-114",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-63-4102",
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
      "vendor_name": "Vendor #192",
      "country_iso": "US",
      "adjustments": [
        {
          "id": 20,
          "source_type": "Spree::TaxRate",
          "source_id": 4,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 17,
          "amount": "1.5",
          "label": "VAT 5%",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2020-01-14T07:43:26.838-05:00",
          "updated_at": "2020-01-14T07:43:26.847-05:00",
          "display_amount": "$1.50"
        },
        {
          "id": 14,
          "source_type": "Spree::PromotionAction",
          "source_id": 3,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 17,
          "amount": "5.0",
          "label": "bar",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2020-01-14T07:43:26.783-05:00",
          "updated_at": "2020-01-14T07:43:26.783-05:00",
          "display_amount": "$5.00"
        }
      ]
    }
  ],
  "payments": [
    {
      "id": 4,
      "source_type": "Spree::CreditCard",
      "source_id": 3,
      "amount": "120.0",
      "display_amount": "$120.00",
      "payment_method_id": 17,
      "state": "completed",
      "avs_response": null,
      "created_at": "2020-01-14T07:43:26.732-05:00",
      "updated_at": "2020-01-14T07:43:26.732-05:00",
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
        "name": "Spree Commerce"
      }
    }
  ],
  "shipments": [
    {
      "id": 18,
      "tracking": "U10000",
      "tracking_url": null,
      "number": "H62226630772",
      "cost": "100.0",
      "shipped_at": "2020-01-14T07:43:26.752-05:00",
      "state": "shipped",
      "order_id": "M514470096",
      "stock_location_name": "NY Warehouse",
      "giftwrappable": false,
      "stock_location_id": 37,
      "giftwrap": null,
      "shipping_rates": [
        {
          "id": 18,
          "name": "UPS Ground",
          "admin_name": null,
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 14,
          "shipping_method_code": "UPS_GROUND",
          "extra_cost": "",
          "is_flat_rate": false,
          "is_flat_rate_expedited": false,
          "is_free_shipping": false,
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 18,
        "name": "UPS Ground",
        "admin_name": null,
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 14,
        "shipping_method_code": "UPS_GROUND",
        "extra_cost": "",
        "is_flat_rate": false,
        "is_flat_rate_expedited": false,
        "is_free_shipping": false,
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
              "id": 32,
              "name": "ShippingCategory #31"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 113,
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
          "id": 16,
          "source_type": "Spree::PromotionAction",
          "source_id": 3,
          "adjustable_type": "Spree::Shipment",
          "adjustable_id": 18,
          "amount": "-10.0",
          "label": "Shipping",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2020-01-14T07:43:26.796-05:00",
          "updated_at": "2020-01-14T07:43:26.796-05:00",
          "display_amount": "-$10.00"
        },
        {
          "id": 15,
          "source_type": "Spree::PromotionAction",
          "source_id": 3,
          "adjustable_type": "Spree::Shipment",
          "adjustable_id": 18,
          "amount": "-9.99",
          "label": "Shipping",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2020-01-14T07:43:26.790-05:00",
          "updated_at": "2020-01-14T07:43:26.790-05:00",
          "display_amount": "-$9.99"
        }
      ],
      "stock_location_address": "NY Warehouse, Washington, AL",
      "country_iso": "US",
      "international_shipping": false,
      "delivery_estimation": "Jan 16"
    }
  ],
  "adjustments": [
    {
      "id": 17,
      "source_type": "Spree::Promotion",
      "source_id": 3,
      "adjustable_type": "Spree::Order",
      "adjustable_id": 16,
      "amount": "20.0",
      "label": "adj1",
      "promotion_code_id": null,
      "finalized": false,
      "eligible": true,
      "created_at": "2020-01-14T07:43:26.800-05:00",
      "updated_at": "2020-01-14T07:43:26.800-05:00",
      "display_amount": "$20.00"
    },
    {
      "id": 18,
      "source_type": "Spree::Promotion",
      "source_id": 3,
      "adjustable_type": "Spree::Order",
      "adjustable_id": 16,
      "amount": "30.0",
      "label": "adj2",
      "promotion_code_id": null,
      "finalized": false,
      "eligible": true,
      "created_at": "2020-01-14T07:43:26.803-05:00",
      "updated_at": "2020-01-14T07:43:26.803-05:00",
      "display_amount": "$30.00"
    }
  ],
  "permissions": {
    "can_update": false
  },
  "credit_cards": [
    {
      "id": 3,
      "month": "12",
      "year": "2021",
      "cc_type": null,
      "last_digits": "1111",
      "name": "Spree Commerce",
      "address": {
        "id": 29,
        "firstname": "John",
        "lastname": null,
        "full_name": "John",
        "address1": "PO Box 1337",
        "address2": "Northwest",
        "city": "Herndon",
        "zipcode": "10028",
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
GET /api/orders/M736519764
Accept: application/json
Authorizat IO N: 956887499667f4e2a6f17165330ab8dbc2a4969c0236577b
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
X-Request-Id: 0ea5f7e3-4bc8-4b90-84a4-0c8b3e2d5e97
X-Runtime: 0.009989
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
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/users/password`

#### Parameters


```json
user[email]=email67%40example.com
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
X-Request-Id: be200b64-4b6b-45f2-8a00-a77178ec9d51
X-Runtime: 0.021887
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
user[email]=email69%40example.com&user[password]=secret
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
Authorization: Bearer 4f2b2f4d1bb70747d7c161322576313cfea1688c58ade9df
ETag: W/&quot;a639c2efee6795c8d20ebe959c5cfc30&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: dc6f7907-c3ed-4bd6-933a-0d4c272e1ef1
X-Runtime: 0.007646
Vary: Origin
Content-Length: 562
200 OK
```


```json
{
  "id": 70,
  "email": "email69@example.com",
  "persistence_token": null,
  "perishable_token": null,
  "last_request_at": null,
  "login": "email69@example.com",
  "ship_address_id": null,
  "bill_address_id": null,
  "created_at": "2020-01-14T07:43:29.171-05:00",
  "updated_at": "2020-01-14T07:43:29.173-05:00",
  "spree_api_key": "4f2b2f4d1bb70747d7c161322576313cfea1688c58ade9df",
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
X-Request-Id: 451933c7-12fe-4c24-b2b5-3bad637b7635
X-Runtime: 0.002795
Vary: Origin
204 No Content
```




# Products

get product by slug

## Fetch a single product by id


### Request

#### Endpoint

```plaintext
GET /api/products/product-13-3938
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
Date: Tue, 14 Jan 2020 12:43:16 GMT
Surrogate-Control: max-age=900
Surrogate-Key: product_id=1
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;7f71ab90af110fda0f15e7eeae093831&quot;
X-Request-Id: f29ba4c7-bd01-4885-86a0-53eec6728517
X-Runtime: 0.063009
Vary: Origin
Content-Length: 1559
200 OK
```


```json
{
  "id": 13,
  "name": "Product #13 - 3938",
  "description": "As seen on TV!",
  "available_on": "2019-01-14T07:43:16.141-05:00",
  "slug": "product-13-3938",
  "meta_description": null,
  "meta_keywords": null,
  "taxon_ids": [
    39
  ],
  "total_on_hand": 0,
  "meta_title": null,
  "display_price": "$19.99",
  "brand": null,
  "brand_slug": null,
  "brand_url": null,
  "brand_description": null,
  "gift_card": false,
  "trends": [

  ],
  "breadcrumb_taxons": [
    {
      "id": 37,
      "name": "Clothing",
      "taxonomy_id": 8,
      "created_at": "2020-01-14T07:43:16.077-05:00",
      "url": "/category/clothing",
      "position": 1
    },
    {
      "id": 38,
      "name": "Girl",
      "taxonomy_id": 8,
      "created_at": "2020-01-14T07:43:16.098-05:00",
      "url": "/category/clothing/girl",
      "position": 2
    },
    {
      "id": 39,
      "name": "Dresses",
      "taxonomy_id": 8,
      "created_at": "2020-01-14T07:43:16.119-05:00",
      "url": "/category/clothing/girl/dresses",
      "position": 3
    }
  ],
  "has_variants": false,
  "master": {
    "id": 25,
    "name": "Product #13 - 3938",
    "sku": "SKU-25",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": true,
    "slug": "product-13-3938",
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
      "taxon_id": 39,
      "position": 1,
      "taxon": {
        "id": 39,
        "name": "Dresses",
        "pretty_name": "Category -> Clothing -> Girl -> Dresses",
        "permalink": "category/clothing/girl/dresses",
        "parent_id": 38,
        "taxonomy_id": 8,
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
Date: Tue, 14 Jan 2020 12:43:17 GMT
Surrogate-Control: max-age=900
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;693447a9b463df69f347a050b786c824&quot;
X-Request-Id: 2e48f5c9-3289-427d-af51-fcd5da782b32
X-Runtime: 0.040341
Vary: Origin
Content-Length: 1235
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
      "name": "Product #18 - 9799",
      "description": "As seen on TV!",
      "available_on": "2019-01-14T07:43:16.897-05:00",
      "slug": "product-18-9799",
      "meta_description": null,
      "meta_keywords": null,
      "taxon_ids": [
        47
      ],
      "total_on_hand": 0,
      "meta_title": null,
      "display_price": "$19.99",
      "brand": "Maison You",
      "brand_slug": "maison-you",
      "brand_url": "/brand/maisonyou",
      "brand_description": null,
      "gift_card": false,
      "trends": [

      ],
      "breadcrumb_taxons": [

      ],
      "has_variants": false,
      "master": {
        "id": 30,
        "name": "Product #18 - 9799",
        "sku": "SKU-30",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-18-9799",
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
          "taxon_id": 47,
          "position": 1,
          "taxon": {
            "id": 47,
            "name": "Maison You",
            "pretty_name": "Brand -> Maison You",
            "permalink": "brand/maison-you",
            "parent_id": 46,
            "taxonomy_id": 11,
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
Date: Tue, 14 Jan 2020 12:43:17 GMT
Surrogate-Control: max-age=900
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;2bc37032208b4abd30641f3befeeca39&quot;
X-Request-Id: 6c6a469c-5e13-4359-b164-77a17e920292
X-Runtime: 0.030841
Vary: Origin
Content-Length: 317
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
      "id": 23,
      "name": "Product #23 - 1145",
      "slug": "product-23-1145",
      "master_id": 35,
      "display_price": "$19.99",
      "brand": "Maison You",
      "brand_slug": "maison-you",
      "brand_url": "/brand/maisonyou",
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
GET /api/products?ids=20%2C21%2C22
Host: example.org
Cookie: 
```

`GET /api/products`

#### Parameters


```json
ids: 20,21,22
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
Date: Tue, 14 Jan 2020 12:43:17 GMT
Surrogate-Control: max-age=900
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;f43e0a8ba6941f0d7672e08e0c95019e&quot;
X-Request-Id: a5fdbb43-0c09-4675-9ff0-2dea36f6cf35
X-Runtime: 0.077589
Vary: Origin
Content-Length: 2691
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
      "id": 20,
      "name": "Product #20 - 8082",
      "description": "As seen on TV!",
      "available_on": "2019-01-14T07:43:17.203-05:00",
      "slug": "product-20-8082",
      "meta_description": null,
      "meta_keywords": null,
      "taxon_ids": [

      ],
      "total_on_hand": 0,
      "meta_title": null,
      "display_price": "$19.99",
      "brand": null,
      "brand_slug": null,
      "brand_url": null,
      "brand_description": null,
      "gift_card": false,
      "trends": [

      ],
      "breadcrumb_taxons": [

      ],
      "has_variants": false,
      "master": {
        "id": 32,
        "name": "Product #20 - 8082",
        "sku": "SKU-32",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-20-8082",
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
      "id": 21,
      "name": "Product #21 - 4437",
      "description": "As seen on TV!",
      "available_on": "2019-01-14T07:43:17.258-05:00",
      "slug": "product-21-4437",
      "meta_description": null,
      "meta_keywords": null,
      "taxon_ids": [

      ],
      "total_on_hand": 0,
      "meta_title": null,
      "display_price": "$19.99",
      "brand": null,
      "brand_slug": null,
      "brand_url": null,
      "brand_description": null,
      "gift_card": false,
      "trends": [

      ],
      "breadcrumb_taxons": [

      ],
      "has_variants": false,
      "master": {
        "id": 33,
        "name": "Product #21 - 4437",
        "sku": "SKU-33",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-21-4437",
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
      "name": "Product #22 - 2747",
      "description": "As seen on TV!",
      "available_on": "2019-01-14T07:43:17.311-05:00",
      "slug": "product-22-2747",
      "meta_description": null,
      "meta_keywords": null,
      "taxon_ids": [

      ],
      "total_on_hand": 0,
      "meta_title": null,
      "display_price": "$19.99",
      "brand": null,
      "brand_slug": null,
      "brand_url": null,
      "brand_description": null,
      "gift_card": false,
      "trends": [

      ],
      "breadcrumb_taxons": [

      ],
      "has_variants": false,
      "master": {
        "id": 34,
        "name": "Product #22 - 2747",
        "sku": "SKU-34",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-22-2747",
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
GET /api/taxons/products?id=45
Host: example.org
Cookie: 
```

`GET /api/taxons/products`

#### Parameters


```json
id: 45
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
ETag: W/&quot;92402d5012082190ea7129a5d3434ec9&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: c32168f4-4f82-49f7-bed9-1ca9b9e99a3a
X-Runtime: 0.039703
Vary: Origin
Content-Length: 1253
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
      "name": "Product #17 - 1311",
      "description": "As seen on TV!",
      "available_on": "2019-01-14T07:43:16.741-05:00",
      "slug": "product-17-1311",
      "meta_description": null,
      "meta_keywords": null,
      "taxon_ids": [
        45
      ],
      "total_on_hand": 0,
      "meta_title": null,
      "display_price": "$19.99",
      "brand": "Ruby on Rails - 8",
      "brand_slug": "ruby-on-rails-8",
      "brand_url": "/rubyonrails8",
      "brand_description": null,
      "gift_card": false,
      "trends": [

      ],
      "breadcrumb_taxons": [

      ],
      "has_variants": false,
      "master": {
        "id": 29,
        "name": "Product #17 - 1311",
        "sku": "SKU-29",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-17-1311",
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
          "taxon_id": 45,
          "position": 1,
          "taxon": {
            "id": 45,
            "name": "Ruby on Rails - 8",
            "pretty_name": "Ruby on Rails - 8",
            "permalink": "ruby-on-rails-8",
            "parent_id": null,
            "taxonomy_id": 10,
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



## Fetch products by taxon permalink


### Request

#### Endpoint

```plaintext
GET /api/taxons/products?permalink=ruby-on-rails-7
Host: example.org
Cookie: 
```

`GET /api/taxons/products`

#### Parameters


```json
permalink: ruby-on-rails-7
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
ETag: W/&quot;97a0e93cfa5c060ae9e13de57b98745b&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 12494110-3206-493c-838e-bd297e6e9879
X-Runtime: 0.045942
Vary: Origin
Content-Length: 1252
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
      "name": "Product #15 - 8967",
      "description": "As seen on TV!",
      "available_on": "2019-01-14T07:43:16.475-05:00",
      "slug": "product-15-8967",
      "meta_description": null,
      "meta_keywords": null,
      "taxon_ids": [
        42
      ],
      "total_on_hand": 0,
      "meta_title": null,
      "display_price": "$19.99",
      "brand": "Ruby on Rails - 7",
      "brand_slug": "ruby-on-rails-7",
      "brand_url": "/rubyonrails7",
      "brand_description": null,
      "gift_card": false,
      "trends": [

      ],
      "breadcrumb_taxons": [

      ],
      "has_variants": false,
      "master": {
        "id": 27,
        "name": "Product #15 - 8967",
        "sku": "SKU-27",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-15-8967",
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
          "taxon_id": 42,
          "position": 1,
          "taxon": {
            "id": 42,
            "name": "Ruby on Rails - 7",
            "pretty_name": "Ruby on Rails - 7",
            "permalink": "ruby-on-rails-7",
            "parent_id": null,
            "taxonomy_id": 9,
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



## Get all products info


### Request

#### Endpoint

```plaintext
GET /api/sitemap/products
Accept: application/json
Authorizat IO N: Bearer de2c5c809aa66165d0b03e861b1b33960e8047eeb8cb3da5
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
X-Request-Id: 05ae1ec9-3702-43ae-9dc5-835bfa2f994d
X-Runtime: 0.030890
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
X-Request-Id: 9164ef81-7e82-43a9-8aff-0f9c147cb0dc
X-Runtime: 0.014789
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

Store a recently viewed variant by user_id or session_id

## Get all recently viewed products


### Request

#### Endpoint

```plaintext
GET /api/recently_viewed?recently_viewed[session_id]=7iuod7jaz73rfjp2ct3z5ssq40ot2ct19lvdtq6xiygek3bbyfelrd72bv7ssiufus63f5xumnz29cu951whth1cvxkeyelxlgtf5yedtkvv7c70zfckomopvonwk85wma393uk34d326nmxqip68f650cgyxfowxnxs59gbpt7lvurdj4oraefcenzm1w925gtzeu88jxnofio7w5gnakronupdb6n6kfojck70u8z0trx1ur7o6kltkw8cgrr&amp;recently_viewed[user_id]=73905
Accept: application/json
Host: example.org
Cookie: 
```

`GET /api/recently_viewed`

#### Parameters


```json
recently_viewed: {&quot;session_id&quot;=&gt;&quot;7iuod7jaz73rfjp2ct3z5ssq40ot2ct19lvdtq6xiygek3bbyfelrd72bv7ssiufus63f5xumnz29cu951whth1cvxkeyelxlgtf5yedtkvv7c70zfckomopvonwk85wma393uk34d326nmxqip68f650cgyxfowxnxs59gbpt7lvurdj4oraefcenzm1w925gtzeu88jxnofio7w5gnakronupdb6n6kfojck70u8z0trx1ur7o6kltkw8cgrr&quot;, &quot;user_id&quot;=&gt;&quot;73905&quot;}
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
ETag: W/&quot;94d2e27f4f3d5242e0dc1f5157ecbe20&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: cb088a44-66d4-49a5-b274-7a5041ca2ea6
X-Runtime: 0.008156
Vary: Origin
Content-Length: 119
200 OK
```


```json
[
  {
    "at": "2020-01-14T07:43:14.131-05:00",
    "variant_id": "var1"
  },
  {
    "at": "2020-01-14T07:48:14.131-05:00",
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
recently_viewed[session_id]=t5pkfj1dmnw9xnn526g1awe182s8g25odmi4qlxgm5xgard47he5wu2jddkwa47fvs6m8hku26orqzzx8srquvz2jplfhyq9uuxqxve4843kg57txlo2h5w7cmg8nls1pw2f0gj8coa47hzltc3pv4fd65xfcnmb8k33ceium9ohe15fnah87lnqfieh9f452xl4oexpgqqllf2jcydz5z4bpteb5qwofrya28dy2n6b7279n9288jtbj3mc27g&recently_viewed[user_id]=68058&recently_viewed[variant_id]=foo
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
X-Request-Id: e953ab88-1032-4773-b158-65e0717a893d
X-Runtime: 0.027797
Vary: Origin
204 No Content
```




# Return Authorizations

Get a single user return authorziation

## Can get another user&#39;s return authorization


### Request

#### Endpoint

```plaintext
GET /api/returns/RA168627373
Authorizat IO N: Bearer 1bf425366f542a2bba0805132fa3d370256726218c24e934
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
ETag: W/&quot;9783418e1a5951f5faf6ba287965db54&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 5d106d33-d09c-4def-adeb-e4cc16ee5708
X-Runtime: 0.033680
Vary: Origin
Content-Length: 2926
200 OK
```


```json
{
  "id": 2,
  "number": "RA168627373",
  "state": "authorized",
  "order_id": 22,
  "memo": "Items were broken",
  "created_at": "2020-01-14T07:43:30.199-05:00",
  "updated_at": "2020-01-14T07:43:30.199-05:00",
  "amount": "10.0",
  "reason": {
    "id": 3,
    "name": "Defect #3",
    "active": true,
    "mutable": true,
    "created_at": "2020-01-14T07:43:30.196-05:00",
    "updated_at": "2020-01-14T07:43:30.196-05:00",
    "mirakl_code": null
  },
  "order": {
    "id": 22,
    "number": "M504503154",
    "item_total": "10.0",
    "total": "110.0",
    "state": "complete",
    "adjustment_total": "0.0",
    "user_id": 89,
    "completed_at": "2020-01-14T07:43:30.127-05:00",
    "bill_address_id": 41,
    "ship_address_id": 42,
    "payment_total": "110.0",
    "shipment_state": "shipped",
    "payment_state": "paid",
    "email": "email88@example.com",
    "special_instructions": null,
    "created_at": "2020-01-14T07:43:30.072-05:00",
    "updated_at": "2020-01-14T07:43:30.183-05:00",
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
    "guest_token": "KI9gJmiOe6IdI624vccNFQ",
    "canceled_at": null,
    "canceler_id": null,
    "store_id": 22,
    "approver_name": null,
    "frontend_viewable": true,
    "is_gift": false,
    "gift_email": null,
    "gift_message": null,
    "gift_card_total": "0.0"
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
    "country_id": 43,
    "country_iso": "US",
    "state_id": 43,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 43,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 43,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 43
    }
  },
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
    "country_id": 43,
    "country_iso": "US",
    "state_id": 43,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 43,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 43,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 43
    }
  },
  "return_items": [
    {
      "name": "Product #76 - 4240",
      "brand": null,
      "brand_slug": null,
      "image": null,
      "product_slug": "product-76-4240",
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
        "year": "2021",
        "cc_type": null,
        "last_digits": "1111",
        "name": "Spree Commerce",
        "gateway_customer_profile_id": "BGS-424141",
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
Authorizat IO N: Bearer 6386e7809d47552ad4c8938d8b4fa130877006b97abb2085
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
ETag: W/&quot;c63fe0d53d543a41a2a0f5b8b86bcb96&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 8333cde3-b2fe-47de-aad3-04963ceb32d5
X-Runtime: 0.006781
Vary: Origin
Content-Length: 169
200 OK
```


```json
{
  "return_authorizations": [
    {
      "number": "RA135077514",
      "created_at": "2020-01-14T07:43:30.868-05:00",
      "return_amount": "10.0",
      "order_number": "M744468142",
      "state": "authorized"
    }
  ]
}
```



## returns a 200


### Request

#### Endpoint

```plaintext
GET /api/returns/RA882283560
Authorizat IO N: Bearer 68d048755c93e18c70b3881c66fb39a11724747b62ba4cd1
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
ETag: W/&quot;9f2f74beb6dc35d40329510f147f2fd0&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 92273f7a-2543-4f55-9a84-07c16ced2a5c
X-Runtime: 0.050349
Vary: Origin
Content-Length: 2849
200 OK
```


```json
{
  "id": 1,
  "number": "RA882283560",
  "state": "authorized",
  "order_id": 21,
  "memo": "Items were broken",
  "created_at": "2020-01-14T07:43:29.794-05:00",
  "updated_at": "2020-01-14T07:43:29.794-05:00",
  "amount": "10.0",
  "reason": {
    "id": 1,
    "name": "Defect #1",
    "active": true,
    "mutable": true,
    "created_at": "2020-01-14T07:43:29.785-05:00",
    "updated_at": "2020-01-14T07:43:29.785-05:00",
    "mirakl_code": null
  },
  "order": {
    "id": 21,
    "number": "M673420575",
    "item_total": "10.0",
    "total": "110.0",
    "state": "complete",
    "adjustment_total": "0.0",
    "user_id": 88,
    "completed_at": "2020-01-14T07:43:29.707-05:00",
    "bill_address_id": 39,
    "ship_address_id": 40,
    "payment_total": "110.0",
    "shipment_state": "shipped",
    "payment_state": "paid",
    "email": "email87@example.com",
    "special_instructions": null,
    "created_at": "2020-01-14T07:43:29.655-05:00",
    "updated_at": "2020-01-14T07:43:29.750-05:00",
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
    "guest_token": "_E-l0hbQ4_WlbdanqMSnxg",
    "canceled_at": null,
    "canceler_id": null,
    "store_id": 21,
    "approver_name": null,
    "frontend_viewable": true,
    "is_gift": false,
    "gift_email": null,
    "gift_message": null,
    "gift_card_total": "0.0"
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
    "country_id": 42,
    "country_iso": "US",
    "state_id": 42,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 42,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 42,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 42
    }
  },
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
    "country_id": 42,
    "country_iso": "US",
    "state_id": 42,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 42,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 42,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 42
    }
  },
  "return_items": [
    {
      "name": "Product #75 - 5688",
      "brand": null,
      "brand_slug": null,
      "image": null,
      "product_slug": "product-75-5688",
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
        "id": 19,
        "name": "Credit Card"
      },
      "source": {
        "id": 4,
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
GET /api/returns/RA848634461
Authorizat IO N: Bearer 5fd369cba0be538c4b3b2fc27edb3ba72dfbf9840b721c7c
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
X-Request-Id: b0086f76-14a6-41d1-8c1e-810607f7551d
X-Runtime: 0.006178
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
stock_request[email]=doreen_wehner%40hane.name&stock_request[variant_id]=135
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
X-Request-Id: a8590d36-3e22-4dd2-b698-943e57df3be1
X-Runtime: 0.004919
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
stock_request[email]=foo&stock_request[variant_id]=137
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
X-Request-Id: 3a9090a9-faf4-410c-b28f-43d49dd160af
X-Runtime: 0.005018
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
stock_request[email]=brinda.hauck%40quitzontillman.com&stock_request[variant_id]=133
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
X-Request-Id: 960e0b6a-a771-4d78-99fc-029f7b2bb394
X-Runtime: 0.026386
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
Authorizat IO N: Bearer b2d18c673bfba8fcc29156c0d8fa7b34fe69f0691254805d
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
ETag: W/&quot;74b7a17df7013918ac437f32fc0588c1&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 0b8062e4-d1a1-444b-a8ac-455eb96ef927
X-Runtime: 0.036492
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
      "created_at": "2020-01-14T07:43:14.035-05:00"
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

Get a single subscriber, accessible by user of the subscriber or admin

## Create a subscriber


### Request

#### Endpoint

```plaintext
POST /api/subscribers
Accept: application/json
Authorizat IO N: Bearer 55a11511a1939651349d3b983b89a0e1b73617db57cc38bd
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/subscribers`

#### Parameters


```json
subscriber[email]=zandra_konopelski%40klocko.biz&subscriber[user_id]=24&subscriber[first_name]=Cherie&subscriber[last_name]=Cassin&subscriber[status]=subscribed
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
ETag: W/&quot;ad8e8778736a44be1464f6cdd14bd649&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: d2c6d338-ed96-4bcc-ab91-f79f3ba796cb
X-Runtime: 0.006806
Vary: Origin
Content-Length: 182
201 Created
```


```json
{
  "id": 7,
  "user_id": 24,
  "email": "zandra_konopelski@klocko.biz",
  "first_name": "Cherie",
  "last_name": "Cassin",
  "source": "",
  "status": "subscribed",
  "created_at": "2020-01-14T07:43:13.529-05:00"
}
```



## Delete a subscriber


### Request

#### Endpoint

```plaintext
DELETE /api/subscribers/6
Accept: application/json
Authorizat IO N: Bearer 4c3f20637772f104812d3fa49d82a7893bd45b4225ec4f20
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
X-Request-Id: daf1f2ef-d001-46b5-b637-af22c1740347
X-Runtime: 0.006065
Vary: Origin
204 No Content
```




## Get a single subscriber by id


### Request

#### Endpoint

```plaintext
GET /api/subscribers/1
Accept: application/json
Authorizat IO N: Bearer f86bdd9c3ef239da5f2547c86718a068ab3d241b2cc25e59
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
ETag: W/&quot;6324f77bf3b1cdbe0e9bb3d6cad14b6e&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 785b9347-196c-4fa2-a248-aa12d26ae323
X-Runtime: 0.030757
Vary: Origin
Content-Length: 189
200 OK
```


```json
{
  "id": 1,
  "user_id": 20,
  "email": "jesica_ebert@walkerschamberger.us",
  "first_name": "Shirely",
  "last_name": "Bartell",
  "source": "",
  "status": "subscribed",
  "created_at": "2020-01-14T07:43:13.420-05:00"
}
```



## Get all subscribers


### Request

#### Endpoint

```plaintext
GET /api/subscribers
Accept: application/json
Authorizat IO N: Bearer e816f046ded1d97ee2cf2dd6da284bd85c4f4ad77dd867b4
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
ETag: W/&quot;b72a5b23ff3ea4cc1b31a7284793d509&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 672dbca4-b841-4c9d-b691-4cabaf412ac1
X-Runtime: 0.009375
Vary: Origin
Content-Length: 621
200 OK
```


```json
{
  "subscribers": [
    {
      "id": 2,
      "user_id": null,
      "email": "willard@altenwerth.us",
      "first_name": "Magan",
      "last_name": "Fahey",
      "source": "",
      "status": "subscribed",
      "created_at": "2020-01-14T07:43:13.456-05:00"
    },
    {
      "id": 3,
      "user_id": null,
      "email": "leann.raynor@huel.info",
      "first_name": "Lavone",
      "last_name": "Feil",
      "source": "",
      "status": "subscribed",
      "created_at": "2020-01-14T07:43:13.457-05:00"
    },
    {
      "id": 4,
      "user_id": null,
      "email": "reita.raynor@schmidtmoen.us",
      "first_name": "Shaun",
      "last_name": "Treutel",
      "source": "",
      "status": "subscribed",
      "created_at": "2020-01-14T07:43:13.458-05:00"
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
PATCH /api/subscribers/5
Accept: application/json
Authorizat IO N: Bearer 881b000ec5ccace0f9881604ad10f8ee447eb360e3a41c52
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
ETag: W/&quot;aba0a7a4988a358f9a7b9e9f7bf9496a&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: a0eb456a-5d76-48bb-8b33-44eb12289014
X-Runtime: 0.008354
Vary: Origin
Content-Length: 191
200 OK
```


```json
{
  "id": 5,
  "user_id": 22,
  "email": "tameika_metz@schilleraltenwerth.com",
  "first_name": "Tamie",
  "last_name": "O'Keefe",
  "source": "",
  "status": "unsubscribed",
  "created_at": "2020-01-14T07:43:13.490-05:00"
}
```



# Taxons

Get taxons info

## Get all taxons info


### Request

#### Endpoint

```plaintext
GET /api/sitemap/taxons
Accept: application/json
Authorizat IO N: Bearer 56c727485cc118c225d4e160b12061824fe775fda0120ada
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
X-Request-Id: b16fa025-67e6-4a27-a46f-776275c20804
X-Runtime: 0.030223
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
ETag: W/&quot;ce9eeb42b8c459e2e1550d813c16a33e&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: aa7de04e-b5a7-4b7c-ae09-7206e51539c8
X-Runtime: 0.035933
Vary: Origin
Content-Length: 4404
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
      "id": 1,
      "name": "Category",
      "pretty_name": "Category",
      "permalink": "category",
      "parent_id": null,
      "taxonomy_id": 1,
      "url_override": null,
      "description": "Category",
      "icon": "/assets/default_taxon.png",
      "taxons": [
        {
          "id": 2,
          "name": "Kids",
          "pretty_name": "Category -> Kids",
          "permalink": "category/kids",
          "parent_id": 1,
          "taxonomy_id": 1,
          "url_override": null
        }
      ]
    },
    {
      "id": 2,
      "name": "Kids",
      "pretty_name": "Category -> Kids",
      "permalink": "category/kids",
      "parent_id": 1,
      "taxonomy_id": 1,
      "url_override": null,
      "description": "Kids",
      "icon": "/assets/default_taxon.png",
      "taxons": [
        {
          "id": 3,
          "name": "Boys",
          "pretty_name": "Category -> Kids -> Boys",
          "permalink": "category/kids/boys",
          "parent_id": 2,
          "taxonomy_id": 1,
          "url_override": null
        },
        {
          "id": 6,
          "name": "Girls",
          "pretty_name": "Category -> Kids -> Girls",
          "permalink": "category/kids/girls",
          "parent_id": 2,
          "taxonomy_id": 1,
          "url_override": null
        }
      ]
    },
    {
      "id": 3,
      "name": "Boys",
      "pretty_name": "Category -> Kids -> Boys",
      "permalink": "category/kids/boys",
      "parent_id": 2,
      "taxonomy_id": 1,
      "url_override": null,
      "description": "Boys",
      "icon": "/assets/default_taxon.png",
      "taxons": [
        {
          "id": 4,
          "name": "Boys Tops",
          "pretty_name": "Category -> Kids -> Boys -> Boys Tops",
          "permalink": "category/kids/boys/boys-tops",
          "parent_id": 3,
          "taxonomy_id": 1,
          "url_override": null
        }
      ]
    },
    {
      "id": 4,
      "name": "Boys Tops",
      "pretty_name": "Category -> Kids -> Boys -> Boys Tops",
      "permalink": "category/kids/boys/boys-tops",
      "parent_id": 3,
      "taxonomy_id": 1,
      "url_override": null,
      "description": "Boys Tops",
      "icon": "/assets/default_taxon.png",
      "taxons": [
        {
          "id": 5,
          "name": "Boys Shirts",
          "pretty_name": "Category -> Kids -> Boys -> Boys Tops -> Boys Shirts",
          "permalink": "category/kids/boys/boys-tops/boys-shirts",
          "parent_id": 4,
          "taxonomy_id": 1,
          "url_override": null
        }
      ]
    },
    {
      "id": 5,
      "name": "Boys Shirts",
      "pretty_name": "Category -> Kids -> Boys -> Boys Tops -> Boys Shirts",
      "permalink": "category/kids/boys/boys-tops/boys-shirts",
      "parent_id": 4,
      "taxonomy_id": 1,
      "url_override": null,
      "description": "Boys Shirts",
      "icon": "/assets/default_taxon.png",
      "taxons": [

      ]
    },
    {
      "id": 6,
      "name": "Girls",
      "pretty_name": "Category -> Kids -> Girls",
      "permalink": "category/kids/girls",
      "parent_id": 2,
      "taxonomy_id": 1,
      "url_override": null,
      "description": "Girls",
      "icon": "/assets/default_taxon.png",
      "taxons": [
        {
          "id": 7,
          "name": "Girls Tops",
          "pretty_name": "Category -> Kids -> Girls -> Girls Tops",
          "permalink": "category/kids/girls/girls-tops",
          "parent_id": 6,
          "taxonomy_id": 1,
          "url_override": null
        }
      ]
    },
    {
      "id": 7,
      "name": "Girls Tops",
      "pretty_name": "Category -> Kids -> Girls -> Girls Tops",
      "permalink": "category/kids/girls/girls-tops",
      "parent_id": 6,
      "taxonomy_id": 1,
      "url_override": null,
      "description": "Girls Tops",
      "icon": "/assets/default_taxon.png",
      "taxons": [
        {
          "id": 8,
          "name": "Girls Shirts",
          "pretty_name": "Category -> Kids -> Girls -> Girls Tops -> Girls Shirts",
          "permalink": "category/kids/girls/girls-tops/girls-shirts",
          "parent_id": 7,
          "taxonomy_id": 1,
          "url_override": null
        }
      ]
    },
    {
      "id": 8,
      "name": "Girls Shirts",
      "pretty_name": "Category -> Kids -> Girls -> Girls Tops -> Girls Shirts",
      "permalink": "category/kids/girls/girls-tops/girls-shirts",
      "parent_id": 7,
      "taxonomy_id": 1,
      "url_override": null,
      "description": "Girls Shirts",
      "icon": "/assets/default_taxon.png",
      "taxons": [

      ]
    },
    {
      "id": 9,
      "name": "Brand",
      "pretty_name": "Brand",
      "permalink": "brand",
      "parent_id": null,
      "taxonomy_id": 2,
      "url_override": null,
      "description": "Brand",
      "icon": "/assets/default_taxon.png",
      "taxons": [
        {
          "id": 10,
          "name": "Ruby on Rails - 1",
          "pretty_name": "Brand -> Ruby on Rails - 1",
          "permalink": "brand/ruby-on-rails-1",
          "parent_id": 9,
          "taxonomy_id": 2,
          "url_override": null
        },
        {
          "id": 11,
          "name": "Ruby on Rails - 2",
          "pretty_name": "Brand -> Ruby on Rails - 2",
          "permalink": "brand/ruby-on-rails-2",
          "parent_id": 9,
          "taxonomy_id": 2,
          "url_override": null
        }
      ]
    },
    {
      "id": 10,
      "name": "Ruby on Rails - 1",
      "pretty_name": "Brand -> Ruby on Rails - 1",
      "permalink": "brand/ruby-on-rails-1",
      "parent_id": 9,
      "taxonomy_id": 2,
      "url_override": null,
      "description": "Ruby on Rails - 1",
      "icon": "/assets/default_taxon.png",
      "taxons": [

      ]
    },
    {
      "id": 11,
      "name": "Ruby on Rails - 2",
      "pretty_name": "Brand -> Ruby on Rails - 2",
      "permalink": "brand/ruby-on-rails-2",
      "parent_id": 9,
      "taxonomy_id": 2,
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
ETag: W/&quot;82c7b36db27945f20df85fa5c129afdf&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 2d823856-1a1b-44c5-8ec8-f3ff88766241
X-Runtime: 0.011252
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
      "id": 31,
      "name": "Brand",
      "pretty_name": "Brand",
      "permalink": "brand",
      "parent_id": null,
      "taxonomy_id": 6,
      "url_override": null,
      "description": "Brand",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 32,
      "name": "Ruby on Rails - 5",
      "pretty_name": "Brand -> Ruby on Rails - 5",
      "permalink": "brand/ruby-on-rails-5",
      "parent_id": 31,
      "taxonomy_id": 6,
      "url_override": null,
      "description": "Ruby on Rails - 5",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 33,
      "name": "Ruby on Rails - 6",
      "pretty_name": "Brand -> Ruby on Rails - 6",
      "permalink": "brand/ruby-on-rails-6",
      "parent_id": 31,
      "taxonomy_id": 6,
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
ETag: W/&quot;b7c3395696fe81122163d8e2a29dd128&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: fb860e6d-7d47-45f8-9970-eefc19e6b075
X-Runtime: 0.022884
Vary: Origin
Content-Length: 2659
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
      "id": 12,
      "name": "Category",
      "pretty_name": "Category",
      "permalink": "category",
      "parent_id": null,
      "taxonomy_id": 3,
      "url_override": null,
      "description": "Category",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 13,
      "name": "Kids",
      "pretty_name": "Category -> Kids",
      "permalink": "category/kids",
      "parent_id": 12,
      "taxonomy_id": 3,
      "url_override": null,
      "description": "Kids",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 14,
      "name": "Boys",
      "pretty_name": "Category -> Kids -> Boys",
      "permalink": "category/kids/boys",
      "parent_id": 13,
      "taxonomy_id": 3,
      "url_override": null,
      "description": "Boys",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 15,
      "name": "Boys Tops",
      "pretty_name": "Category -> Kids -> Boys -> Boys Tops",
      "permalink": "category/kids/boys/boys-tops",
      "parent_id": 14,
      "taxonomy_id": 3,
      "url_override": null,
      "description": "Boys Tops",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 16,
      "name": "Boys Shirts",
      "pretty_name": "Category -> Kids -> Boys -> Boys Tops -> Boys Shirts",
      "permalink": "category/kids/boys/boys-tops/boys-shirts",
      "parent_id": 15,
      "taxonomy_id": 3,
      "url_override": null,
      "description": "Boys Shirts",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 17,
      "name": "Girls",
      "pretty_name": "Category -> Kids -> Girls",
      "permalink": "category/kids/girls",
      "parent_id": 13,
      "taxonomy_id": 3,
      "url_override": null,
      "description": "Girls",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 18,
      "name": "Girls Tops",
      "pretty_name": "Category -> Kids -> Girls -> Girls Tops",
      "permalink": "category/kids/girls/girls-tops",
      "parent_id": 17,
      "taxonomy_id": 3,
      "url_override": null,
      "description": "Girls Tops",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 19,
      "name": "Girls Shirts",
      "pretty_name": "Category -> Kids -> Girls -> Girls Tops -> Girls Shirts",
      "permalink": "category/kids/girls/girls-tops/girls-shirts",
      "parent_id": 18,
      "taxonomy_id": 3,
      "url_override": null,
      "description": "Girls Shirts",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 20,
      "name": "Brand",
      "pretty_name": "Brand",
      "permalink": "brand",
      "parent_id": null,
      "taxonomy_id": 4,
      "url_override": null,
      "description": "Brand",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 21,
      "name": "Ruby on Rails - 3",
      "pretty_name": "Brand -> Ruby on Rails - 3",
      "permalink": "brand/ruby-on-rails-3",
      "parent_id": 20,
      "taxonomy_id": 4,
      "url_override": null,
      "description": "Ruby on Rails - 3",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 22,
      "name": "Ruby on Rails - 4",
      "pretty_name": "Brand -> Ruby on Rails - 4",
      "permalink": "brand/ruby-on-rails-4",
      "parent_id": 20,
      "taxonomy_id": 4,
      "url_override": null,
      "description": "Ruby on Rails - 4",
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
ETag: W/&quot;6edfc0672ad1848ddeed0e55a9431dc1&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 3de4a5e2-b038-46ce-9763-82cb290c2d24
X-Runtime: 0.005712
Vary: Origin
Content-Length: 144
200 OK
```


```json
[
  {
    "id": 35,
    "name": "Kids",
    "navigation_url": "/shop/kids",
    "parent_id": 34,
    "lft": 2,
    "depth": 1,
    "highlight": false,
    "header_link": false,
    "add_flair": false
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
Authorization: Bearer 0d0c57443d74f2f2e886862b7f21ad634d392d01e92b8729
ETag: W/&quot;d0a93e026b14a38c33d46a14e4e155d8&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: defed4fb-d50f-48d0-a993-9d759a810383
X-Runtime: 0.012218
Vary: Origin
Content-Length: 562
200 OK
```


```json
{
  "id": 55,
  "email": "email54@example.com",
  "persistence_token": null,
  "perishable_token": null,
  "last_request_at": null,
  "login": "email54@example.com",
  "ship_address_id": null,
  "bill_address_id": null,
  "created_at": "2020-01-14T07:43:23.921-05:00",
  "updated_at": "2020-01-14T07:43:23.923-05:00",
  "spree_api_key": "0d0c57443d74f2f2e886862b7f21ad634d392d01e92b8729",
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
X-Spree-Order-Token: QIgI0_XkzMjoFSF89aF3lQ
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/users/login`

#### Parameters


```json
user[email]=email55%40example.com&user[password]=secret&order_number=M923597926
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
Authorization: Bearer b0cc5fc3264958a01d3783d23761a6c60f3d838c00cd6ae8
ETag: W/&quot;7511dec7e75d0686110093dd62ef6473&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: f2915c62-004f-4ec1-b5d1-64b12344002f
X-Runtime: 0.011167
Vary: Origin
Content-Length: 562
200 OK
```


```json
{
  "id": 56,
  "email": "email55@example.com",
  "persistence_token": null,
  "perishable_token": null,
  "last_request_at": null,
  "login": "email55@example.com",
  "ship_address_id": null,
  "bill_address_id": null,
  "created_at": "2020-01-14T07:43:23.941-05:00",
  "updated_at": "2020-01-14T07:43:23.943-05:00",
  "spree_api_key": "b0cc5fc3264958a01d3783d23761a6c60f3d838c00cd6ae8",
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
Authorizat IO N: Bearer 5ec01b53fe469ecf5f4e07482e4242a60e9892d1897d7476
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
Authorization: Bearer 5ec01b53fe469ecf5f4e07482e4242a60e9892d1897d7476
ETag: W/&quot;899d24202abd76ae662a4ba19d0175e7&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: d2339fda-cc15-4a87-9249-05fd8e6da08a
X-Runtime: 0.020340
Vary: Origin
Content-Length: 1521
200 OK
```


```json
{
  "email": "email58@example.com",
  "first_name": null,
  "last_name": null,
  "id": 59,
  "subscribed": false,
  "addresses": [
    {
      "id": 24,
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
      "default": true
    },
    {
      "id": 23,
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
        "created_at": "2020-01-14T07:43:24.285-05:00",
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
        "created_at": "2020-01-14T07:43:24.300-05:00",
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
        "created_at": "2020-01-14T07:43:24.315-05:00",
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
Authorization: Bearer 01b80dc721741ebfaa7ee88fc8eca2921ac8aa3d55acf0ca
ETag: W/&quot;4bec14b0ff82c95cc790ef59f1f9a8a4&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 583a8e76-caee-46d4-b08e-7784e0932656
X-Runtime: 0.028625
Vary: Origin
Content-Length: 185
201 Created
```


```json
{
  "id": 54,
  "email": "test@example.com",
  "created_at": "2020-01-14T07:43:23.895-05:00",
  "updated_at": "2020-01-14T07:43:23.897-05:00",
  "subscribed": false,
  "bill_address": null,
  "ship_address": null
}
```



## Subscribe a user


### Request

#### Endpoint

```plaintext
PUT /api/users/58/subscribe
Authorizat IO N: Bearer 18d379b5845420ffdc014b8bc3b4f25b946c9a0ea795aa91
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
Authorization: Bearer 18d379b5845420ffdc014b8bc3b4f25b946c9a0ea795aa91
ETag: W/&quot;f80932797a03b5f4d8154991ceaf16a0&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: acf88b2b-9df2-45ae-b4a7-a3481e6e35fb
X-Runtime: 0.010939
Vary: Origin
Content-Length: 187
200 OK
```


```json
{
  "id": 58,
  "email": "email57@example.com",
  "created_at": "2020-01-14T07:43:24.224-05:00",
  "updated_at": "2020-01-14T07:43:24.225-05:00",
  "subscribed": true,
  "bill_address": null,
  "ship_address": null
}
```



## Unsubscribe a user


### Request

#### Endpoint

```plaintext
PUT /api/users/57/unsubscribe
Authorizat IO N: Bearer 580949df6b49ae49f2274ff47fe21c3c2464834cbd64c8d8
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
Authorization: Bearer 580949df6b49ae49f2274ff47fe21c3c2464834cbd64c8d8
ETag: W/&quot;e821e1f4b4d4e7cc35448772e57b97a0&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 7a90a429-92a6-4539-bd2a-aed334d8044b
X-Runtime: 0.011221
Vary: Origin
Content-Length: 188
200 OK
```


```json
{
  "id": 57,
  "email": "email56@example.com",
  "created_at": "2020-01-14T07:43:24.202-05:00",
  "updated_at": "2020-01-14T07:43:24.203-05:00",
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
GET /api/variants/20
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
ETag: W/&quot;a150fffbbba783e339a104b3a23c3092&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 84fcf694-cab3-47e5-9a29-5c5739d02f2a
X-Runtime: 0.116475
Vary: Origin
Content-Length: 1934
200 OK
```


```json
{
  "id": 20,
  "name": "Product #10 - 7149",
  "sku": "SKU-19",
  "weight": "0.0",
  "height": null,
  "width": null,
  "depth": null,
  "is_master": false,
  "slug": "product-10-7149",
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
    {
      "id": 1,
      "position": 1,
      "attachment_content_type": "image/jpeg",
      "attachment_file_name": "thinking-cat.jpg",
      "type": "Spree::Image",
      "attachment_updated_at": "2020-01-14T07:43:13.712-05:00",
      "attachment_width": 489,
      "attachment_height": 490,
      "alt": null,
      "viewable_type": "Spree::Variant",
      "viewable_id": 20,
      "mini_url": "/spree/products/1/mini/thinking-cat.jpg?1579005793",
      "small_url": "/spree/products/1/small/thinking-cat.jpg?1579005793",
      "product_url": "/spree/products/1/product/thinking-cat.jpg?1579005793",
      "large_url": "/spree/products/1/large/thinking-cat.jpg?1579005793"
    }
  ],
  "variant_properties": [

  ],
  "stock_items": [

  ],
  "prices": [
    {
      "id": 11,
      "vendor_id": 25,
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
      "id": 12,
      "vendor_id": 26,
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
Authorizat IO N: Bearer b5088813a4cbee362b50d892041011ae6e28b5ddfb760f44
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
ETag: W/&quot;baa32103bd5ecc5bbf5c653b5cb5c3bd&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 620dd8e6-cdda-418b-9dcb-29ca6af4bf68
X-Runtime: 0.034027
Vary: Origin
Content-Length: 206
200 OK
```


```json
[
  {
    "id": 1,
    "user_id": 27,
    "payment_source_type": "SolidusPaypalBraintree::Source",
    "payment_source_id": 1,
    "default": false,
    "created_at": "2020-01-14T07:43:14.200-05:00",
    "updated_at": "2020-01-14T07:43:14.200-05:00"
  }
]
```



## Remove the payment from the user wallet


### Request

#### Endpoint

```plaintext
DELETE /api/wallet_payment_sources/3
Accept: application/json
Authorizat IO N: Bearer fb6aefb7c7fea5f8f270ccb03df7b1931a7803c0fe4a3231
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
X-Request-Id: 892b854c-d213-4138-a3cd-66c53a31d67d
X-Runtime: 0.011219
Vary: Origin
204 No Content
```




## Set a wallet payment source as the default user payment method


### Request

#### Endpoint

```plaintext
POST /api/wallet_payment_sources/2/default
Accept: application/json
Authorizat IO N: Bearer 77716987db46db96f03d01dd41222183eb6351d1fa18400d
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
X-Request-Id: a1d4f585-78d7-4f0b-986e-6ecf584db1f0
X-Runtime: 0.010352
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
Authorizat IO N: Bearer 28bd3b7105c8c4b8156b2d3d7be79a98f4d60b9905af656e
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
ETag: W/&quot;1953e6f885af6256a79b36ce58df3c2d&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 70889216-23fd-4fa8-a8da-b4266d1f3cda
X-Runtime: 0.012072
Vary: Origin
Content-Length: 74
201 Created
```


```json
{
  "id": 28,
  "wishlist_id": 39,
  "variant_id": 85,
  "quantity": 2,
  "remark": "Foo bar"
}
```



## Delete a wished product


### Request

#### Endpoint

```plaintext
DELETE /api/wished_products/25
Accept: application/json
Authorizat IO N: Bearer b7396939ffd6679f3a5832fbc980c581c711156407afb843
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
X-Request-Id: 15961fd4-06a7-4dd2-97a4-1b0ed9f23587
X-Runtime: 0.011294
Vary: Origin
204 No Content
```




## Get a single wished product


### Request

#### Endpoint

```plaintext
GET /api/wished_products/16
Accept: application/json
Authorizat IO N: Bearer c5f335ea757606b23dfa52bd39b90c820c5c85ed1a91eacd
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
ETag: W/&quot;cfd2f3d271333a9875ce9a3a2bbcaa00&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: b2b1eaf2-804e-403f-a0f2-53e7c59e792b
X-Runtime: 0.009744
Vary: Origin
Content-Length: 69
200 OK
```


```json
{
  "id": 16,
  "wishlist_id": 31,
  "variant_id": 61,
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
Authorizat IO N: Bearer e27f10a75998ca77c95f545908055032c1b12e30b63bb0d5
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
ETag: W/&quot;5fe2403b90a74b83bf2bb0e4773ec2af&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 65dc8fa9-d50c-4475-ad03-a87fdd442170
X-Runtime: 0.010481
Vary: Origin
Content-Length: 298
200 OK
```


```json
{
  "wished_products": [
    {
      "id": 19,
      "wishlist_id": 32,
      "variant_id": 67,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 20,
      "wishlist_id": 33,
      "variant_id": 69,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 21,
      "wishlist_id": 34,
      "variant_id": 71,
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
GET /api/wished_products/mine?with_variant=true
Accept: application/json
Authorizat IO N: Bearer 6390b55398bf673760e2767f385ae073d23071bd54ac5c88
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
ETag: W/&quot;868edeae8e07e6befafd7d50711f3881&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 690135ac-84d4-4c14-bd1f-79cf8ffb4cc2
X-Runtime: 0.079774
Vary: Origin
Content-Length: 2086
200 OK
```


```json
{
  "wished_products": [
    {
      "id": 13,
      "wishlist_id": 30,
      "variant_id": 55,
      "quantity": 1,
      "remark": null,
      "variant": {
        "id": 55,
        "name": "Product #33 - 2082",
        "sku": "SKU-54",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-33-2082",
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
      "id": 14,
      "wishlist_id": 30,
      "variant_id": 57,
      "quantity": 1,
      "remark": null,
      "variant": {
        "id": 57,
        "name": "Product #34 - 1091",
        "sku": "SKU-56",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-34-1091",
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
    },
    {
      "id": 15,
      "wishlist_id": 30,
      "variant_id": 59,
      "quantity": 1,
      "remark": null,
      "variant": {
        "id": 59,
        "name": "Product #35 - 1163",
        "sku": "SKU-58",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-35-1163",
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
Authorizat IO N: Bearer 3b9b6fc07367becd60be36939919c0cbb7db355a6a673f95
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
ETag: W/&quot;5510186eb6f8c5bb3c61b4493aa7e912&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: ae1808b9-ef60-4ff1-a777-020b5042c843
X-Runtime: 0.144042
Vary: Origin
Content-Length: 2146
200 OK
```


```json
{
  "wished_products": [
    {
      "id": 22,
      "wishlist_id": 35,
      "variant_id": 73,
      "quantity": 1,
      "remark": null,
      "variant": {
        "id": 73,
        "name": "Product #42 - 9395",
        "sku": "SKU-72",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-42-9395",
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
      "id": 23,
      "wishlist_id": 36,
      "variant_id": 75,
      "quantity": 1,
      "remark": null,
      "variant": {
        "id": 75,
        "name": "Product #43 - 7188",
        "sku": "SKU-74",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-43-7188",
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
      "id": 24,
      "wishlist_id": 37,
      "variant_id": 77,
      "quantity": 1,
      "remark": null,
      "variant": {
        "id": 77,
        "name": "Product #44 - 5469",
        "sku": "SKU-76",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-44-5469",
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



## Get my wished products


### Request

#### Endpoint

```plaintext
GET /api/wished_products/mine
Accept: application/json
Authorizat IO N: Bearer e34e7d2fefb3543a1b3ed22276437f77d5d4d7e08df68874
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
ETag: W/&quot;68cf217c5e87c4bf82889729728a722b&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 74da97fb-ead8-43df-87bc-e91820c52d03
X-Runtime: 0.034148
Vary: Origin
Content-Length: 298
200 OK
```


```json
{
  "wished_products": [
    {
      "id": 10,
      "wishlist_id": 29,
      "variant_id": 49,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 11,
      "wishlist_id": 29,
      "variant_id": 51,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 12,
      "wishlist_id": 29,
      "variant_id": 53,
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
PATCH /api/wished_products/29
Accept: application/json
Authorizat IO N: Bearer a540d8b603924866ae078d42035e790880c4dcdc6cbb8f20
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/wished_products/:id`

#### Parameters


```json
wished_product[wishlist_id]=40&wished_product[variant_id]=93&wished_product[quantity]=2&wished_product[remark]=Foo+bar
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
ETag: W/&quot;3063099edf41f8fde73b0b3122898cf2&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 7c2b19b5-dc36-4381-bc20-a0cb5b13a8d3
X-Runtime: 0.010880
Vary: Origin
Content-Length: 74
200 OK
```


```json
{
  "id": 29,
  "wishlist_id": 40,
  "variant_id": 93,
  "quantity": 2,
  "remark": "Foo bar"
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
Authorizat IO N: Bearer 9a00bc4347b969e299012ccf96a87a45ffde54a3aabe398f
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/wishlists`

#### Parameters


```json
wishlist[name]&wishlist[user_id]=15&wishlist[is_default]=true&wishlist[is_public]=false
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
ETag: W/&quot;145419db3084ed0c74a95c271eaf8fbc&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 3359c031-5a75-478d-97ea-cfd4b294ee27
X-Runtime: 0.011655
Vary: Origin
Content-Length: 100
201 Created
```


```json
{
  "id": 14,
  "user_id": 15,
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
DELETE /api/wishlists/13
Accept: application/json
Authorizat IO N: Bearer 76869c8e55dea83f72adcc5bbeaad51403a6987709a754f7
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
X-Request-Id: c230f2a9-096e-4ff5-9536-c64163c3e684
X-Runtime: 0.019469
Vary: Origin
204 No Content
```




## Get a single wishlist


### Request

#### Endpoint

```plaintext
GET /api/wishlists/12
Accept: application/json
Authorizat IO N: Bearer 5c91d9044b1bdcf7c695d8bcfbb9b7eda8564c87a211b89b
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
ETag: W/&quot;f92642239fb0dc0d35194f14304938c6&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: a6981f7a-91bb-41a3-94f5-3f2a42186aee
X-Runtime: 0.009240
Vary: Origin
Content-Length: 306
200 OK
```


```json
{
  "id": 12,
  "user_id": 13,
  "name": "Wishlist #12",
  "is_public": false,
  "is_default": true,
  "wished_products": [
    {
      "id": 4,
      "wishlist_id": 12,
      "variant_id": 8,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 5,
      "wishlist_id": 12,
      "variant_id": 10,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 6,
      "wishlist_id": 12,
      "variant_id": 12,
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
Authorizat IO N: Bearer 719742967fc745616a1f84199779e88cabc654bad28aa2da
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
ETag: W/&quot;a60fc47796db36777aa82843e33d4863&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 3662ce05-59af-492c-b301-569edfa09cbe
X-Runtime: 0.151790
Vary: Origin
Content-Length: 867
200 OK
```


```json
{
  "wishlists": [
    {
      "id": 1,
      "user_id": 1,
      "name": "Wishlist #1",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 2,
      "user_id": 2,
      "name": "Wishlist #2",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 3,
      "user_id": 3,
      "name": "Wishlist #3",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 4,
      "user_id": 4,
      "name": "Wishlist #4",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 5,
      "user_id": 5,
      "name": "Wishlist #5",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 6,
      "user_id": 6,
      "name": "Wishlist #6",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 7,
      "user_id": 7,
      "name": "Wishlist #7",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 8,
      "user_id": 8,
      "name": "Wishlist #8",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 9,
      "user_id": 9,
      "name": "Wishlist #9",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 10,
      "user_id": 10,
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
Authorizat IO N: Bearer 1f17dda0a994656a7e221139f5998b02cb2bc0ac81c2ee91
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
ETag: W/&quot;f59383008cf63035e73c759168776241&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 498a875a-f819-4fde-8ce0-08d07b902b0a
X-Runtime: 0.010778
Vary: Origin
Content-Length: 304
200 OK
```


```json
{
  "id": 11,
  "user_id": 12,
  "name": "Wishlist #11",
  "is_public": false,
  "is_default": true,
  "wished_products": [
    {
      "id": 1,
      "wishlist_id": 11,
      "variant_id": 2,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 2,
      "wishlist_id": 11,
      "variant_id": 4,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 3,
      "wishlist_id": 11,
      "variant_id": 6,
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
Authorizat IO N: Bearer bb1eb4d14ea1c7e363c3b142219a0f83aa055cf056baaf02
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
ETag: W/&quot;9bc44f56ed5d66719c18c39a833ca758&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 72dcfa7b-8d2a-42a7-b474-0f4350f18580
X-Runtime: 0.009594
Vary: Origin
Content-Length: 903
200 OK
```


```json
{
  "wishlists": [
    {
      "id": 19,
      "user_id": 18,
      "name": "Wishlist #17",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 20,
      "user_id": 18,
      "name": "Wishlist #18",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 21,
      "user_id": 18,
      "name": "Wishlist #19",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 22,
      "user_id": 18,
      "name": "Wishlist #20",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 23,
      "user_id": 18,
      "name": "Wishlist #21",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 24,
      "user_id": 18,
      "name": "Wishlist #22",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 25,
      "user_id": 18,
      "name": "Wishlist #23",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 26,
      "user_id": 18,
      "name": "Wishlist #24",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 27,
      "user_id": 18,
      "name": "Wishlist #25",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 28,
      "user_id": 18,
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
Authorizat IO N: Bearer a25060bd0035dd41318ec73846a75eed9900f2b4852d4b8d
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/wishlists/:id`

#### Parameters


```json
wishlist[name]=Another+Wishlist&wishlist[user_id]=16&wishlist[is_default]=true&wishlist[is_public]=false
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
ETag: W/&quot;ca8cf814c803ff6fe9dd4621bcc22db4&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 4f087581-76f2-468a-bf32-de01538e5246
X-Runtime: 0.012542
Vary: Origin
Content-Length: 311
200 OK
```


```json
{
  "id": 15,
  "user_id": 16,
  "name": "Another Wishlist",
  "is_public": false,
  "is_default": true,
  "wished_products": [
    {
      "id": 7,
      "wishlist_id": 15,
      "variant_id": 14,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 8,
      "wishlist_id": 15,
      "variant_id": 16,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 9,
      "wishlist_id": 15,
      "variant_id": 18,
      "quantity": 1,
      "remark": null
    }
  ]
}
```



