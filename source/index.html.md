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
PUT /api/orders/M432536209/addresses/18
Accept: application/json
X-Spree-Order-Token: 8CAF2LEj89Xx0V3LYaSsUg
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
ETag: W/&quot;1a2de21dcb4671788b3182ea39b3d1f0&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: ca5e958c-9848-4dae-8853-e77d32e3d4a6
X-Runtime: 0.052612
Vary: Origin
Content-Length: 507
200 OK
```


```json
{
  "id": 19,
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
X-Spree-Order-Token: l25pbcNqobmwB7RVXrzjbw
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/braintree/transactions`

#### Parameters


```json
order_id=M483416033&payment_method_id=21&options[restart_checkout]=true&transaction[email]=maryellen.oga%40mckenziemcglynn.com&transaction[nonce]=fake-paypal-billing-agreement-nonce&transaction[phone]=555-555-0199&transaction[shipping_address_attributes][first_name]=John&transaction[shipping_address_attributes][last_name]=Stamm&transaction[shipping_address_attributes][address_line_1]=A+Different+Road&transaction[shipping_address_attributes][city]=Herndon&transaction[shipping_address_attributes][state_code]=AL&transaction[shipping_address_attributes][zip]=10035&transaction[shipping_address_attributes][country_code]=US&transaction[payment_type]=PayPalAccount&transaction[billing_address_attributes][first_name]=John&transaction[billing_address_attributes][last_name]=Stamm&transaction[billing_address_attributes][address_line_1]=A+Different+Road&transaction[billing_address_attributes][city]=Herndon&transaction[billing_address_attributes][state_code]=AL&transaction[billing_address_attributes][zip]=10035&transaction[billing_address_attributes][country_code]=US
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
ETag: W/&quot;cc8bbf0e29e0fd9331f15862a4bec195&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 026a7895-7eb2-4e73-9b94-17eb7c8dc605
X-Runtime: 0.387761
Vary: Origin
Content-Length: 5380
200 OK
```


```json
{
  "id": 19,
  "number": "M483416033",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2020-01-02T11:00:31.062-05:00",
  "updated_at": "2020-01-02T11:00:31.404-05:00",
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
  "token": "l25pbcNqobmwB7RVXrzjbw",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order&order=M483416033&bzip=10035&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [
    {
      "id": 21,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 38,
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
    "id": 39,
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
      "id": 22,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 135,
      "vendor_id": 235,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 135,
        "name": "Product #73 - 2030",
        "sku": "SKU-134",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-73-2030",
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
            "id": 62,
            "name": "Size-62",
            "presentation": "S",
            "option_type_name": "foo-size-62",
            "option_type_id": 62,
            "option_type_presentation": "Size",
            "position": 1
          }
        ],
        "images": [

        ],
        "product_id": 73,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [

      ],
      "vendor_name": "Vendor #235",
      "country_iso": "US",
      "adjustments": [

      ]
    }
  ],
  "payments": [
    {
      "id": 8,
      "source_type": "SolidusPaypalBraintree::Source",
      "source_id": 7,
      "amount": "110.0",
      "display_amount": "$110.00",
      "payment_method_id": 21,
      "state": "checkout",
      "avs_response": null,
      "created_at": "2020-01-02T11:00:31.193-05:00",
      "updated_at": "2020-01-02T11:00:31.193-05:00",
      "payment_method": {
        "id": 21,
        "name": "Braintree"
      },
      "source": {
        "id": 7,
        "payment_type": "PayPalAccount",
        "token": "bgx899",
        "created_at": "2020-01-02T11:00:31.192-05:00",
        "email": "jane.doe@paypal.com"
      }
    }
  ],
  "shipments": [
    {
      "id": 18,
      "tracking": null,
      "tracking_url": null,
      "number": "H46546604167",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M483416033",
      "stock_location_name": "NY Warehouse",
      "giftwrappable": false,
      "stock_location_id": 47,
      "giftwrap": null,
      "shipping_rates": [
        {
          "id": 18,
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
        }
      ],
      "selected_shipping_rate": {
        "id": 18,
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
              "id": 19,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 38,
              "name": "ShippingCategory #36"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 135,
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
      "delivery_estimation": "Jan 06"
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
X-Spree-Order-Token: skd6PZ_dukiO2UWCe4_EwA
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/braintree/transactions`

#### Parameters


```json
order_id=M580523482&payment_method_id=22&options[restart_checkout]=true&transaction[email]=maryellen.oga%40mckenziemcglynn.com&transaction[nonce]=fake-apple-pay-visa-nonce&transaction[phone]=555-555-0199&transaction[shipping_address_attributes][first_name]=John&transaction[shipping_address_attributes][last_name]=Stamm&transaction[shipping_address_attributes][address_line_1]=A+Different+Road&transaction[shipping_address_attributes][city]=Herndon&transaction[shipping_address_attributes][state_code]=AL&transaction[shipping_address_attributes][zip]=10037&transaction[shipping_address_attributes][country_code]=US&transaction[payment_type]=ApplePayCard
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
ETag: W/&quot;8fb31f9561197f76ad13c5234c6615c7&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: a972a73b-8ce2-445c-b3ac-678562a1e531
X-Runtime: 0.283760
Vary: Origin
Content-Length: 5424
200 OK
```


```json
{
  "id": 20,
  "number": "M580523482",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2020-01-02T11:00:31.789-05:00",
  "updated_at": "2020-01-02T11:00:32.075-05:00",
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
  "token": "skd6PZ_dukiO2UWCe4_EwA",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order&order=M580523482&bzip=10037&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [
    {
      "id": 22,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 42,
    "firstname": "John",
    "lastname": "Stamm",
    "full_name": "John Stamm",
    "address1": "A Different Road",
    "address2": null,
    "city": "Herndon",
    "zipcode": "10037",
    "phone": "555-555-0199",
    "company": null,
    "alternative_phone": null,
    "country_id": 41,
    "country_iso": "US",
    "state_id": 41,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 41,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 41,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 41
    }
  },
  "ship_address": {
    "id": 43,
    "firstname": "John",
    "lastname": "Stamm",
    "full_name": "John Stamm",
    "address1": "A Different Road",
    "address2": null,
    "city": "Herndon",
    "zipcode": "10037",
    "phone": "555-555-0199",
    "company": null,
    "alternative_phone": null,
    "country_id": 41,
    "country_iso": "US",
    "state_id": 41,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 41,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 41,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 41
    }
  },
  "line_items": [
    {
      "id": 23,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 137,
      "vendor_id": 240,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 137,
        "name": "Product #74 - 542",
        "sku": "SKU-136",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-74-542",
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
      "vendor_name": "Vendor #240",
      "country_iso": "US",
      "adjustments": [

      ]
    }
  ],
  "payments": [
    {
      "id": 9,
      "source_type": "SolidusPaypalBraintree::Source",
      "source_id": 8,
      "amount": "110.0",
      "display_amount": "$110.00",
      "payment_method_id": 22,
      "state": "checkout",
      "avs_response": null,
      "created_at": "2020-01-02T11:00:31.933-05:00",
      "updated_at": "2020-01-02T11:00:31.933-05:00",
      "payment_method": {
        "id": 22,
        "name": "Braintree"
      },
      "source": {
        "id": 8,
        "payment_type": "ApplePayCard",
        "token": "cg7hsk",
        "created_at": "2020-01-02T11:00:31.932-05:00",
        "cc_type": "Apple Pay - Visa",
        "last_digits": "1881",
        "month": "12",
        "year": "2020"
      }
    }
  ],
  "shipments": [
    {
      "id": 20,
      "tracking": null,
      "tracking_url": null,
      "number": "H41303078430",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M580523482",
      "stock_location_name": "NY Warehouse",
      "giftwrappable": false,
      "stock_location_id": 48,
      "giftwrap": null,
      "shipping_rates": [
        {
          "id": 20,
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
        }
      ],
      "selected_shipping_rate": {
        "id": 20,
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
              "id": 20,
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
          "variant_id": 137,
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
      "delivery_estimation": "Jan 06"
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
PUT /api/checkouts/M328968303/complete
Accept: application/json
X-Spree-Order-Token: i9eo7kSanreJpDOwJ0rwMg
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
ETag: W/&quot;273daac0096bee2f2c4fc02b0abde334&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 9224f690-6a9c-454c-881b-b2ffc42c4401
X-Runtime: 0.499149
Vary: Origin
Content-Length: 5550
200 OK
```


```json
{
  "id": 21,
  "number": "M328968303",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "complete",
  "adjustment_total": "0.0",
  "user_id": 91,
  "created_at": "2020-01-02T11:00:32.482-05:00",
  "updated_at": "2020-01-02T11:00:32.851-05:00",
  "completed_at": "2020-01-02T11:00:32.851-05:00",
  "payment_total": "110.0",
  "shipment_state": "ready",
  "payment_state": "paid",
  "email": "email90@example.com",
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
  "token": "i9eo7kSanreJpDOwJ0rwMg",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order&order=M328968303&bzip=10039&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [
    {
      "id": 23,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    },
    {
      "id": 24,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 44,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "PO Box 1337",
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
  "ship_address": {
    "id": 45,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "A Different Road",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10040",
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
  "line_items": [
    {
      "id": 24,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 139,
      "vendor_id": 245,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 139,
        "name": "Product #75 - 9695",
        "sku": "SKU-138",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-75-9695",
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
      "vendor_name": "Vendor #245",
      "country_iso": "US",
      "adjustments": [

      ]
    }
  ],
  "payments": [
    {
      "id": 10,
      "source_type": "SolidusPaypalBraintree::Source",
      "source_id": 9,
      "amount": "110.0",
      "display_amount": "$110.00",
      "payment_method_id": 23,
      "state": "completed",
      "avs_response": "M",
      "created_at": "2020-01-02T11:00:32.583-05:00",
      "updated_at": "2020-01-02T11:00:32.705-05:00",
      "payment_method": {
        "id": 23,
        "name": "Braintree"
      },
      "source": {
        "id": 9,
        "payment_type": "CreditCard",
        "token": "4rptfz",
        "created_at": "2020-01-02T11:00:32.582-05:00",
        "cc_type": "Visa",
        "last_digits": "1881",
        "month": "12",
        "year": "2020"
      }
    }
  ],
  "shipments": [
    {
      "id": 21,
      "tracking": "U10000",
      "tracking_url": null,
      "number": "H74741557647",
      "cost": "100.0",
      "shipped_at": null,
      "state": "ready",
      "order_id": "M328968303",
      "stock_location_name": "NY Warehouse",
      "giftwrappable": false,
      "stock_location_id": 49,
      "giftwrap": null,
      "shipping_rates": [
        {
          "id": 21,
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
        "id": 21,
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
              "id": 21,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 40,
              "name": "ShippingCategory #38"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 139,
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
      "delivery_estimation": "Jan 06"
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
PATCH /api/checkouts/M389124466
Accept: application/json
X-Spree-Order-Token: 2BCF78LVWxE4PMHELsyfhA
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=26&order[payment_attributes][][source_attributes][nonce]=fake-apple-pay-visa-nonce&order[payment_attributes][][source_attributes][payment_type]=ApplePayCard&order[payment_attributes][][source_attributes][reusable]=true
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
ETag: W/&quot;cbdf124fe6733d3c633ff6e4cb1b2b58&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 7768df26-8946-4ae4-8e0c-d43093fef9be
X-Runtime: 0.159453
Vary: Origin
Content-Length: 4933
200 OK
```


```json
{
  "id": 23,
  "number": "M389124466",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 93,
  "created_at": "2020-01-02T11:00:34.222-05:00",
  "updated_at": "2020-01-02T11:00:34.507-05:00",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "email92@example.com",
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
  "token": "2BCF78LVWxE4PMHELsyfhA",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order&order=M389124466&bzip=10043&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [
    {
      "id": 26,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 48,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "PO Box 1337",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10043",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 44,
    "country_iso": "US",
    "state_id": 44,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 44,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 44,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 44
    }
  },
  "ship_address": {
    "id": 49,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "A Different Road",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10044",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 44,
    "country_iso": "US",
    "state_id": 44,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 44,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 44,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 44
    }
  },
  "line_items": [
    {
      "id": 26,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 143,
      "vendor_id": 255,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 143,
        "name": "Product #77 - 8676",
        "sku": "SKU-142",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-77-8676",
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
        "product_id": 77,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [

      ],
      "vendor_name": "Vendor #255",
      "country_iso": "US",
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
      "number": "H38876824532",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M389124466",
      "stock_location_name": "NY Warehouse",
      "giftwrappable": false,
      "stock_location_id": 51,
      "giftwrap": null,
      "shipping_rates": [
        {
          "id": 25,
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
        }
      ],
      "selected_shipping_rate": {
        "id": 25,
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
              "id": 23,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 42,
              "name": "ShippingCategory #40"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 143,
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
      "delivery_estimation": "Jan 06"
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
PATCH /api/checkouts/M161057620
Accept: application/json
X-Spree-Order-Token: DubbP2pDGQJkxR7hpjnTdw
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=27&order[payment_attributes][][source_attributes][nonce]=fake-paypal-billing-agreement-nonce&order[payment_attributes][][source_attributes][payment_type]=PayPalAccount&order[payment_attributes][][source_attributes][reusable]=true
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
ETag: W/&quot;db97842f97e03c2c1a25f25d4c74041f&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 5953f0bd-5788-406a-8b46-750ee0ef4080
X-Runtime: 0.143613
Vary: Origin
Content-Length: 4933
200 OK
```


```json
{
  "id": 24,
  "number": "M161057620",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 94,
  "created_at": "2020-01-02T11:00:34.868-05:00",
  "updated_at": "2020-01-02T11:00:35.124-05:00",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "email93@example.com",
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
  "token": "DubbP2pDGQJkxR7hpjnTdw",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order&order=M161057620&bzip=10045&init=true",
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
    "id": 50,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "PO Box 1337",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10045",
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
    "id": 51,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "A Different Road",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10046",
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
      "id": 27,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 145,
      "vendor_id": 260,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 145,
        "name": "Product #78 - 1695",
        "sku": "SKU-144",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-78-1695",
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
        "product_id": 78,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [

      ],
      "vendor_name": "Vendor #260",
      "country_iso": "US",
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
      "number": "H17425307820",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M161057620",
      "stock_location_name": "NY Warehouse",
      "giftwrappable": false,
      "stock_location_id": 52,
      "giftwrap": null,
      "shipping_rates": [
        {
          "id": 27,
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
        "id": 27,
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
              "id": 24,
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
          "variant_id": 145,
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
      "delivery_estimation": "Jan 06"
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
PATCH /api/checkouts/M387674130
Accept: application/json
X-Spree-Order-Token: 9BLV22-2PEUD7S_Y1ihxtA
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=28&order[payment_attributes][][source_attributes][nonce]=fake-valid-visa-nonce&order[payment_attributes][][source_attributes][payment_type]=CreditCard&order[payment_attributes][][source_attributes][reusable]=true
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
ETag: W/&quot;3f5a95fa4165d477a69d032dd60dd9d0&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 2815b733-6e04-476a-b881-6f82ef732cd3
X-Runtime: 0.157368
Vary: Origin
Content-Length: 4931
200 OK
```


```json
{
  "id": 25,
  "number": "M387674130",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 95,
  "created_at": "2020-01-02T11:00:35.472-05:00",
  "updated_at": "2020-01-02T11:00:35.748-05:00",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "email94@example.com",
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
  "token": "9BLV22-2PEUD7S_Y1ihxtA",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order&order=M387674130&bzip=10047&init=true",
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
    "id": 52,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "PO Box 1337",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10047",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
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
    "id": 53,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "A Different Road",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10048",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
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
        "name": "Product #79 - 946",
        "sku": "SKU-146",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-79-946",
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

  ],
  "shipments": [
    {
      "id": 29,
      "tracking": null,
      "tracking_url": null,
      "number": "H56185168806",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M387674130",
      "stock_location_name": "NY Warehouse",
      "giftwrappable": false,
      "stock_location_id": 53,
      "giftwrap": null,
      "shipping_rates": [
        {
          "id": 29,
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
        "id": 29,
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
      "delivery_estimation": "Jan 06"
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
PATCH /api/checkouts/M308694376
Accept: application/json
X-Spree-Order-Token: wP5fD59g7rTGgIOobcBFIw
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=25&order[payment_attributes][][source_attributes][wallet_payment_source_id]=8
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
ETag: W/&quot;7c26fb547cca8b4e3f6da75ec721a0fe&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 258130c3-d72a-44cc-b4eb-6a10a508fd60
X-Runtime: 0.214950
Vary: Origin
Content-Length: 4933
200 OK
```


```json
{
  "id": 22,
  "number": "M308694376",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 92,
  "created_at": "2020-01-02T11:00:33.388-05:00",
  "updated_at": "2020-01-02T11:00:33.803-05:00",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "email91@example.com",
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
  "token": "wP5fD59g7rTGgIOobcBFIw",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order&order=M308694376&bzip=10041&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [
    {
      "id": 25,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 46,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "PO Box 1337",
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
  "ship_address": {
    "id": 47,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "A Different Road",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10042",
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
  "line_items": [
    {
      "id": 25,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 141,
      "vendor_id": 250,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 141,
        "name": "Product #76 - 5780",
        "sku": "SKU-140",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-76-5780",
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
      "vendor_name": "Vendor #250",
      "country_iso": "US",
      "adjustments": [

      ]
    }
  ],
  "payments": [

  ],
  "shipments": [
    {
      "id": 23,
      "tracking": null,
      "tracking_url": null,
      "number": "H75787807732",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M308694376",
      "stock_location_name": "NY Warehouse",
      "giftwrappable": false,
      "stock_location_id": 50,
      "giftwrap": null,
      "shipping_rates": [
        {
          "id": 23,
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
        "id": 23,
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
              "id": 22,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 41,
              "name": "ShippingCategory #39"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 141,
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
      "delivery_estimation": "Jan 06"
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
PUT /api/checkouts/M100196570
Accept: application/json
X-Spree-Order-Token: G3bqDRfC5796hThsAp99eQ
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PUT /api/checkouts/:id`

#### Parameters


```json
order[ship_address_attributes][id]&order[ship_address_attributes][firstname]=John&order[ship_address_attributes][lastname]&order[ship_address_attributes][address1]=10+Lovely+Street&order[ship_address_attributes][address2]=Northwest&order[ship_address_attributes][city]=Herndon&order[ship_address_attributes][zipcode]=10049&order[ship_address_attributes][phone]=555-555-0199&order[ship_address_attributes][state_name]&order[ship_address_attributes][alternative_phone]=555-555-0199&order[ship_address_attributes][company]=Company&order[ship_address_attributes][state_id]=47&order[ship_address_attributes][country_id]=47&order[ship_address_attributes][created_at]&order[ship_address_attributes][updated_at]&order[use_billing]=true&hold_state=true
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
ETag: W/&quot;6f5882e5744dd1222fde488554f5bc34&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: df8585e2-4bc0-4a61-b0e9-89ca772eedaf
X-Runtime: 0.150126
Vary: Origin
Content-Length: 4840
200 OK
```


```json
{
  "id": 26,
  "number": "M100196570",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "cart",
  "adjustment_total": "0.0",
  "user_id": 96,
  "created_at": "2020-01-02T11:00:36.094-05:00",
  "updated_at": "2020-01-02T11:00:36.197-05:00",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "email95@example.com",
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
  "token": "G3bqDRfC5796hThsAp99eQ",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order&order=M100196570&bzip=10049&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [

  ],
  "bill_address": {
    "id": 54,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "10 Lovely Street",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10049",
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
    "id": 54,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "10 Lovely Street",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10049",
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
        "name": "Product #80 - 5183",
        "sku": "SKU-148",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-80-5183",
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

  ],
  "shipments": [
    {
      "id": 30,
      "tracking": "U10000",
      "tracking_url": null,
      "number": "H00305857831",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M100196570",
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
      "delivery_estimation": "Jan 06"
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

Delete giftwrap related to shipment

## Create Giftwrap


### Request

#### Endpoint

```plaintext
POST /api/shipments/H80617025122/giftwrap
Accept: application/json
X-Spree-Order-Token: o2fZNLpXiCiHAX0nLPfxbw
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/shipments/:shipment_number/giftwrap`

#### Parameters


```json
order_number=M580907141
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
X-Request-Id: e69b4f91-b08b-49e2-bf42-1e50523f30c2
X-Runtime: 0.036965
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
DELETE /api/shipments/H28713323203/giftwrap
Accept: application/json
X-Spree-Order-Token: YSxznZN6iL5Paijl_Dw3YQ
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`DELETE /api/shipments/:shipment_number/giftwrap`

#### Parameters


```json
order_number=M650176045
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
X-Request-Id: 8d1abf0a-9fb9-42b3-8db3-65f07152eddd
X-Runtime: 0.044739
Vary: Origin
204 No Content
```




# LineItem

Representation of a single cart item for a specific variant with price of vendor

## Creating a line item


### Request

#### Endpoint

```plaintext
POST /api/orders/M692251476/line_items
Accept: application/json
X-Spree-Order-Token: 99X86_2t3GQYglORxErj8g
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/:order_number/line_items`

#### Parameters


```json
line_item[variant_id]=8&line_item[options][vendor_id]=13
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
ETag: W/&quot;cecad2c19587a88f6422aa9f2b7392ef&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 569ada3a-be44-4317-ba21-5acce8411704
X-Runtime: 0.103919
Vary: Origin
Content-Length: 926
201 Created
```


```json
{
  "id": 3,
  "quantity": 1,
  "price": "19.99",
  "variant_id": 8,
  "vendor_id": 13,
  "single_display_amount": "$19.99",
  "display_amount": "$19.99",
  "total": "19.99",
  "on_sale": false,
  "final_sale": false,
  "backordered": null,
  "promotionable": true,
  "variant": {
    "id": 8,
    "name": "Product #4 - 3558",
    "sku": "SKU-7",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": false,
    "slug": "product-4-3558",
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
    "product_id": 4,
    "lead_time": 2,
    "brand": null,
    "brand_slug": null,
    "brand_description": null
  },
  "monogram": null,
  "gift_cards": [

  ],
  "vendor_name": "Vendor #13",
  "country_iso": null,
  "adjustments": [

  ]
}
```



## Creating a line item gift card


### Request

#### Endpoint

```plaintext
POST /api/orders/M634381294/line_items
Accept: application/json
X-Spree-Order-Token: nXLBJLMWgKyYhHbhDDUFhQ
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/:order_number/line_items`

#### Parameters


```json
line_item[variant_id]=14&line_item[options][vendor_id]=26&line_item[options][gift_card_details][recipient_name]=Recipient+John&line_item[options][gift_card_details][recipient_email]=recipient%40email.com&line_item[options][gift_card_details][purchaser_name]=Purchaser+Bob&line_item[options][gift_card_details][gift_message]=Surprise&line_item[options][gift_card_details][send_email_at]=2020-01-02+11%3A00%3A14+-0500
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
ETag: W/&quot;2fe182c25876e34b87f59c3e59d2a5a0&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 98ed648f-a7dc-4314-8964-b0ee657c77dc
X-Runtime: 0.226160
Vary: Origin
Content-Length: 1065
201 Created
```


```json
{
  "id": 5,
  "quantity": 1,
  "price": "19.99",
  "variant_id": 14,
  "vendor_id": 26,
  "single_display_amount": "$19.99",
  "display_amount": "$19.99",
  "total": "19.99",
  "on_sale": false,
  "final_sale": false,
  "backordered": null,
  "promotionable": true,
  "variant": {
    "id": 14,
    "name": "Product #6 - 5121",
    "sku": "SKU-14",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": false,
    "slug": "product-6-5121",
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
    "product_id": 6,
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
      "send_email_at": "2020-01-02T00:00:00.000-05:00"
    }
  ],
  "vendor_name": "Vendor #26",
  "country_iso": null,
  "adjustments": [

  ]
}
```



## Deleting a line item


### Request

#### Endpoint

```plaintext
DELETE /api/orders/M297142481/line_items/6
Accept: application/json
X-Spree-Order-Token: PtDR0uSJWBB-RwR71O1iWQ
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
X-Request-Id: bcd2c79f-5d4c-4db5-904c-016121818287
X-Runtime: 0.086103
Vary: Origin
204 No Content
```




## Updating a line item


### Request

#### Endpoint

```plaintext
PUT /api/orders/M381561377/line_items/1
Accept: application/json
X-Spree-Order-Token: -p85KIh2s8fcmaenq3ahTw
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
ETag: W/&quot;b80931e861b47bd02b6880d2088e8965&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 7811e59a-ad84-4f7e-b9c3-951cb7300847
X-Runtime: 0.321563
Vary: Origin
Content-Length: 921
200 OK
```


```json
{
  "id": 1,
  "quantity": 2,
  "price": "10.0",
  "variant_id": 2,
  "vendor_id": 2,
  "single_display_amount": "$10.00",
  "display_amount": "$20.00",
  "total": "20.0",
  "on_sale": false,
  "final_sale": false,
  "backordered": null,
  "promotionable": true,
  "variant": {
    "id": 2,
    "name": "Product #1 - 5138",
    "sku": "SKU-1",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": false,
    "slug": "product-1-5138",
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
```



# Minis

Get a single mini, accessible by owner of the mini or admin

## Create a mini


### Request

#### Endpoint

```plaintext
POST /api/minis
Accept: application/json
Authorizat IO N: Bearer dc7180f540572818dc02543a8d88bd560b23cb993eec0940
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/minis`

#### Parameters


```json
mini[name]=Winny&mini[user_id]=84&mini[birth_year]=2019&mini[birth_month]=1&mini[birth_day]=1
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
ETag: W/&quot;7f7e5c1760ce454c63c318ef0bbec7c4&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: a2d5e82d-8f84-496c-9241-abfb4c6d26e2
X-Runtime: 0.012906
Vary: Origin
Content-Length: 163
201 Created
```


```json
{
  "id": 19,
  "user_id": 84,
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
Authorizat IO N: Bearer 2214e4bec99581bc205211f2e1ddb99a29b7d78d25d7a6d9
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
X-Request-Id: 277dd3e6-f98c-4eb1-8160-10dd4d05248f
X-Runtime: 0.007742
Vary: Origin
204 No Content
```




## Get a single mini


### Request

#### Endpoint

```plaintext
GET /api/minis/1
Accept: application/json
Authorizat IO N: Bearer 8fd50387cbcee6e9e35baab45fc5c18cc2367e1b34cfeae8
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
ETag: W/&quot;fb9b501e4e59648f46b0d9e435b149a5&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: d001d2d0-a99a-4a57-810a-480585473675
X-Runtime: 0.039532
Vary: Origin
Content-Length: 167
200 OK
```


```json
{
  "id": 1,
  "user_id": 68,
  "name": "Mini",
  "birth_year": 2019,
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
Authorizat IO N: Bearer added1225afa40ad76d9ed7d1f574e200aad49d80c3e9c0d
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
ETag: W/&quot;591e08a37cba215c650be2feaf3fabea&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 7cc1933b-19cf-4bd9-9a0c-903d039a8072
X-Runtime: 0.034473
Vary: Origin
Content-Length: 1769
200 OK
```


```json
{
  "minis": [
    {
      "id": 18,
      "user_id": 82,
      "name": "Mini",
      "birth_year": 2019,
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
      "id": 17,
      "user_id": 81,
      "name": "Mini",
      "birth_year": 2019,
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
      "id": 16,
      "user_id": 80,
      "name": "Mini",
      "birth_year": 2019,
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
      "user_id": 79,
      "name": "Mini",
      "birth_year": 2019,
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
      "id": 14,
      "user_id": 78,
      "name": "Mini",
      "birth_year": 2019,
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
      "id": 13,
      "user_id": 77,
      "name": "Mini",
      "birth_year": 2019,
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
      "id": 12,
      "user_id": 76,
      "name": "Mini",
      "birth_year": 2019,
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
      "id": 11,
      "user_id": 75,
      "name": "Mini",
      "birth_year": 2019,
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
      "id": 10,
      "user_id": 74,
      "name": "Mini",
      "birth_year": 2019,
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
      "user_id": 73,
      "name": "Mini",
      "birth_year": 2019,
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
Authorizat IO N: Bearer 435c339403bd2da0d5ca9dd94a8d19640ae4cdfe5475bcd8
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
ETag: W/&quot;2cc66567c996ef19da680dd3d6851c0b&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: eb4db777-111a-4dc1-afd4-3e5c88f35696
X-Runtime: 0.017005
Vary: Origin
Content-Length: 414
200 OK
```


```json
{
  "minis": [
    {
      "id": 7,
      "user_id": 71,
      "name": "Mini",
      "birth_year": 2019,
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
      "user_id": 71,
      "name": "Mini",
      "birth_year": 2019,
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
PATCH /api/minis/8
Accept: application/json
Authorizat IO N: Bearer 1a335b2d19b8d95eba55ae389f70fb0ec4e7e53d126a91e6
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
ETag: W/&quot;0003139ce25b5cfc7abee1d46833a646&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: c36b091e-d02e-4179-9a3b-2c4e40704e75
X-Runtime: 0.013852
Vary: Origin
Content-Length: 168
200 OK
```


```json
{
  "id": 8,
  "user_id": 72,
  "name": "Marge",
  "birth_year": 2019,
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
user_id&order_token&line_item[variant_id]=113&line_item[quantity]=1&line_item[vendor_id]=186&line_item[gift_card_details_attributes][recipient_name]=Recipient+John&line_item[gift_card_details_attributes][recipient_email]=recipient%40email.com&line_item[gift_card_details_attributes][purchaser_name]=Purchaser+Bob&line_item[gift_card_details_attributes][gift_message]=Surprise&line_item[gift_card_details_attributes][send_email_at]=2020-01-02
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
ETag: W/&quot;ce13890986190c27f95c2ca3045a7a67&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 9de4d88f-7863-41f8-819f-e7d7ba74dfe8
X-Runtime: 0.125428
Vary: Origin
Content-Length: 2820
200 OK
```


```json
{
  "id": 12,
  "number": "M677090450",
  "item_total": "19.99",
  "total": "19.99",
  "ship_total": "0.0",
  "state": "cart",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2020-01-02T11:00:26.786-05:00",
  "updated_at": "2020-01-02T11:00:26.824-05:00",
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
  "token": "v_JbbdO4E0p2I7SNV78ZIg",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order&order=M677090450&bzip=&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [

  ],
  "bill_address": null,
  "ship_address": null,
  "line_items": [
    {
      "id": 14,
      "quantity": 1,
      "price": "19.99",
      "variant_id": 113,
      "vendor_id": 186,
      "single_display_amount": "$19.99",
      "display_amount": "$19.99",
      "total": "19.99",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 113,
        "name": "Product #61 - 7709",
        "sku": "SKU-113",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-61-7709",
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
        "product_id": 61,
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
          "send_email_at": "2020-01-02T00:00:00.000-05:00"
        }
      ],
      "vendor_name": "Vendor #186",
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
user_id&order_token&line_item[variant_id]=109&line_item[quantity]=2&line_item[vendor_id]=175
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
ETag: W/&quot;a8716b550dfa2ce8dc98735b814cdc01&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: ca531c26-43e9-4364-bdb2-4844140b753a
X-Runtime: 0.141569
Vary: Origin
Content-Length: 2638
200 OK
```


```json
{
  "id": 11,
  "number": "M220308476",
  "item_total": "39.98",
  "total": "39.98",
  "ship_total": "0.0",
  "state": "cart",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2020-01-02T11:00:26.332-05:00",
  "updated_at": "2020-01-02T11:00:26.375-05:00",
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
  "token": "CeNaTYJ6YlwT-sxjffk93Q",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order&order=M220308476&bzip=&init=true",
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
      "variant_id": 109,
      "vendor_id": 175,
      "single_display_amount": "$19.99",
      "display_amount": "$39.98",
      "total": "39.98",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 109,
        "name": "Product #60 - 3515",
        "sku": "SKU-108",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-60-3515",
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
Authorizat IO N: Bearer 52a3cbde2986dd82c8eda15188d03225decdb5c8fa41eaea
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
ETag: W/&quot;26cad6dcb84758b455671dbc6d521094&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 908c10a7-05d8-4bbd-85c2-1b235b94eefb
X-Runtime: 0.023527
Vary: Origin
Content-Length: 310
200 OK
```


```json
{
  "orders": [
    {
      "number": "M262189454",
      "completed_at": "2020-01-02T11:00:25.880-05:00",
      "total": "120.0",
      "state": "Complete",
      "shipment_state": "shipped",
      "shipments": [
        {
          "number": "H54114675623",
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
GET /api/orders/M057061159
Accept: application/json
Authorizat IO N: Bearer 1f9be542b23e16a4505eacbd2ad315f8fe6551245e94dbe6
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
ETag: W/&quot;fc741df1c431c8dbb81578b3cd588dbb&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 74b458db-456a-4a6b-a3f8-7f53077bde14
X-Runtime: 0.206318
Vary: Origin
Content-Length: 10092
200 OK
```


```json
{
  "id": 14,
  "number": "M057061159",
  "item_total": "20.0",
  "total": "120.0",
  "ship_total": "100.0",
  "state": "complete",
  "adjustment_total": "0.0",
  "user_id": 58,
  "created_at": "2020-01-02T11:00:28.024-05:00",
  "updated_at": "2020-01-02T11:00:28.289-05:00",
  "completed_at": "2020-01-02T11:00:28.108-05:00",
  "payment_total": "120.0",
  "shipment_state": "shipped",
  "payment_state": "paid",
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
  "token": "ATRkEQbUhYcwLylwYUQBwg",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order&order=M057061159&bzip=10023&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [
    {
      "id": 16,
      "name": "Credit Card",
      "partial_name": "gateway",
      "method_type": "gateway"
    },
    {
      "id": 17,
      "name": "Credit Card",
      "partial_name": "gateway",
      "method_type": "gateway"
    }
  ],
  "bill_address": {
    "id": 24,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "PO Box 1337",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10023",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 32,
    "country_iso": "US",
    "state_id": 32,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 32,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 32,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 32
    }
  },
  "ship_address": {
    "id": 25,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "A Different Road",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10024",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 32,
    "country_iso": "US",
    "state_id": 32,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 32,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 32,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 32
    }
  },
  "line_items": [
    {
      "id": 17,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 119,
      "vendor_id": 200,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 119,
        "name": "Product #65 - 8343",
        "sku": "SKU-118",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-65-8343",
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

      ],
      "vendor_name": "Vendor #200",
      "country_iso": "US",
      "adjustments": [
        {
          "id": 17,
          "source_type": "Spree::TaxRate",
          "source_id": 3,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 17,
          "amount": "2.0",
          "label": "VAT 5%",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2020-01-02T11:00:28.258-05:00",
          "updated_at": "2020-01-02T11:00:28.270-05:00",
          "display_amount": "$2.00"
        },
        {
          "id": 11,
          "source_type": "Spree::PromotionAction",
          "source_id": 4,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 17,
          "amount": "5.0",
          "label": "foo",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2020-01-02T11:00:28.201-05:00",
          "updated_at": "2020-01-02T11:00:28.201-05:00",
          "display_amount": "$5.00"
        },
        {
          "id": 10,
          "source_type": "Spree::PromotionAction",
          "source_id": 4,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 17,
          "amount": "5.0",
          "label": "foo",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2020-01-02T11:00:28.190-05:00",
          "updated_at": "2020-01-02T11:00:28.190-05:00",
          "display_amount": "$5.00"
        }
      ]
    },
    {
      "id": 18,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 121,
      "vendor_id": 200,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 121,
        "name": "Product #66 - 6711",
        "sku": "SKU-120",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-66-6711",
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
        "product_id": 66,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [

      ],
      "vendor_name": "Vendor #200",
      "country_iso": "US",
      "adjustments": [
        {
          "id": 18,
          "source_type": "Spree::TaxRate",
          "source_id": 4,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 18,
          "amount": "1.5",
          "label": "VAT 5%",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2020-01-02T11:00:28.286-05:00",
          "updated_at": "2020-01-02T11:00:28.297-05:00",
          "display_amount": "$1.50"
        },
        {
          "id": 12,
          "source_type": "Spree::PromotionAction",
          "source_id": 4,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 18,
          "amount": "5.0",
          "label": "bar",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2020-01-02T11:00:28.209-05:00",
          "updated_at": "2020-01-02T11:00:28.209-05:00",
          "display_amount": "$5.00"
        }
      ]
    }
  ],
  "payments": [
    {
      "id": 7,
      "source_type": "Spree::CreditCard",
      "source_id": 7,
      "amount": "120.0",
      "display_amount": "$120.00",
      "payment_method_id": 16,
      "state": "completed",
      "avs_response": null,
      "created_at": "2020-01-02T11:00:28.124-05:00",
      "updated_at": "2020-01-02T11:00:28.124-05:00",
      "payment_method": {
        "id": 16,
        "name": "Credit Card"
      },
      "source": {
        "id": 7,
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
      "id": 11,
      "tracking": "U10000",
      "tracking_url": null,
      "number": "H03382423678",
      "cost": "100.0",
      "shipped_at": "2020-01-02T11:00:28.162-05:00",
      "state": "shipped",
      "order_id": "M057061159",
      "stock_location_name": "NY Warehouse",
      "giftwrappable": false,
      "stock_location_id": 37,
      "giftwrap": null,
      "shipping_rates": [
        {
          "id": 11,
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
        }
      ],
      "selected_shipping_rate": {
        "id": 11,
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
              "id": 13,
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
          "variant_id": 119,
          "quantity": 1,
          "states": {
            "shipped": 1
          }
        },
        {
          "variant_id": 121,
          "quantity": 1,
          "states": {
            "shipped": 1
          }
        }
      ],
      "adjustments": [
        {
          "id": 14,
          "source_type": "Spree::PromotionAction",
          "source_id": 4,
          "adjustable_type": "Spree::Shipment",
          "adjustable_id": 11,
          "amount": "-10.0",
          "label": "Shipping",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2020-01-02T11:00:28.227-05:00",
          "updated_at": "2020-01-02T11:00:28.227-05:00",
          "display_amount": "-$10.00"
        },
        {
          "id": 13,
          "source_type": "Spree::PromotionAction",
          "source_id": 4,
          "adjustable_type": "Spree::Shipment",
          "adjustable_id": 11,
          "amount": "-9.99",
          "label": "Shipping",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2020-01-02T11:00:28.218-05:00",
          "updated_at": "2020-01-02T11:00:28.218-05:00",
          "display_amount": "-$9.99"
        }
      ],
      "stock_location_address": "NY Warehouse, Washington, AL",
      "country_iso": "US",
      "international_shipping": false,
      "delivery_estimation": "Jan 06"
    }
  ],
  "adjustments": [
    {
      "id": 15,
      "source_type": "Spree::Promotion",
      "source_id": 4,
      "adjustable_type": "Spree::Order",
      "adjustable_id": 14,
      "amount": "20.0",
      "label": "adj1",
      "promotion_code_id": null,
      "finalized": false,
      "eligible": true,
      "created_at": "2020-01-02T11:00:28.235-05:00",
      "updated_at": "2020-01-02T11:00:28.235-05:00",
      "display_amount": "$20.00"
    },
    {
      "id": 16,
      "source_type": "Spree::Promotion",
      "source_id": 4,
      "adjustable_type": "Spree::Order",
      "adjustable_id": 14,
      "amount": "30.0",
      "label": "adj2",
      "promotion_code_id": null,
      "finalized": false,
      "eligible": true,
      "created_at": "2020-01-02T11:00:28.240-05:00",
      "updated_at": "2020-01-02T11:00:28.240-05:00",
      "display_amount": "$30.00"
    }
  ],
  "permissions": {
    "can_update": false
  },
  "credit_cards": [
    {
      "id": 7,
      "month": "12",
      "year": "2021",
      "cc_type": null,
      "last_digits": "1111",
      "name": "Spree Commerce",
      "address": {
        "id": 24,
        "firstname": "John",
        "lastname": null,
        "full_name": "John",
        "address1": "PO Box 1337",
        "address2": "Northwest",
        "city": "Herndon",
        "zipcode": "10023",
        "phone": "555-555-0199",
        "company": "Company",
        "alternative_phone": "555-555-0199",
        "country_id": 32,
        "country_iso": "US",
        "state_id": 32,
        "state_name": null,
        "state_text": "AL",
        "country": {
          "id": 32,
          "iso_name": "UNITED STATES",
          "iso": "US",
          "iso3": "USA",
          "name": "United States",
          "numcode": 840
        },
        "state": {
          "id": 32,
          "name": "Alabama",
          "abbr": "AL",
          "country_id": 32
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
GET /api/orders/M474924514
Accept: application/json
Authorizat IO N: ae8a2e98c7dd8bde6131c37c372fe436356a95561ca63ff4
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
X-Request-Id: 1f07dba9-8090-4988-8140-1279c94aa9ea
X-Runtime: 0.011376
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
user[email]=email64%40example.com
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
X-Request-Id: b4fd903d-6bf5-41fd-9602-65ed1171b0f3
X-Runtime: 0.025104
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
user[email]=email65%40example.com&user[password]=secret
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
Authorization: Bearer 3a94a874881a65354e2ae956b28d3977c2d131a9c290ed97
ETag: W/&quot;9754326c42bec6bb12c98718844a97f5&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 37f57e96-3f9c-4b0f-a552-053637da8544
X-Runtime: 0.010315
Vary: Origin
Content-Length: 562
200 OK
```


```json
{
  "id": 66,
  "email": "email65@example.com",
  "persistence_token": null,
  "perishable_token": null,
  "last_request_at": null,
  "login": "email65@example.com",
  "ship_address_id": null,
  "bill_address_id": null,
  "created_at": "2020-01-02T11:00:29.162-05:00",
  "updated_at": "2020-01-02T11:00:29.165-05:00",
  "spree_api_key": "3a94a874881a65354e2ae956b28d3977c2d131a9c290ed97",
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
X-Request-Id: 0bba7a15-aad6-4c99-b6a1-151414e7c7fa
X-Runtime: 0.004364
Vary: Origin
204 No Content
```




# Products

Get products info

## Fetch a single product by id


### Request

#### Endpoint

```plaintext
GET /api/products/product-55-3982
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
Date: Thu, 02 Jan 2020 16:00:23 GMT
Surrogate-Control: max-age=900
Surrogate-Key: product_id=1
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;309a00cac916e9ce57069a0ea1afd22c&quot;
X-Request-Id: 26e283ff-a8b5-433b-9056-a204f8dc2660
X-Runtime: 0.063772
Vary: Origin
Content-Length: 1512
200 OK
```


```json
{
  "id": 55,
  "name": "Product #55 - 3982",
  "description": "As seen on TV!",
  "available_on": "2019-01-02T11:00:23.569-05:00",
  "slug": "product-55-3982",
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
      "created_at": "2020-01-02T11:00:23.489-05:00",
      "url": "/clothing",
      "position": 1
    },
    {
      "id": 9,
      "name": "Girl",
      "taxonomy_id": 3,
      "created_at": "2020-01-02T11:00:23.517-05:00",
      "url": "/clothing/girl",
      "position": 2
    },
    {
      "id": 10,
      "name": "Dresses",
      "taxonomy_id": 3,
      "created_at": "2020-01-02T11:00:23.543-05:00",
      "url": "/clothing/girl/dresses",
      "position": 3
    }
  ],
  "has_variants": false,
  "master": {
    "id": 99,
    "name": "Product #55 - 3982",
    "sku": "SKU-99",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": true,
    "slug": "product-55-3982",
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
Date: Thu, 02 Jan 2020 16:00:22 GMT
Surrogate-Control: max-age=900
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;8e6ea1f45d3bc199a857471c416b298f&quot;
X-Request-Id: b7057efc-48e8-4353-a375-1786b82dcdbb
X-Runtime: 0.054009
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
      "id": 49,
      "name": "Product #49 - 7833",
      "description": "As seen on TV!",
      "available_on": "2019-01-02T11:00:22.816-05:00",
      "slug": "product-49-7833",
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
        "id": 93,
        "name": "Product #49 - 7833",
        "sku": "SKU-93",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-49-7833",
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
Date: Thu, 02 Jan 2020 16:00:23 GMT
Surrogate-Control: max-age=900
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;cebad918e8ba2590a4d2c6080fe6d374&quot;
X-Request-Id: fa875b2e-5b88-4c7f-b7e0-ca16eec655ff
X-Runtime: 0.027803
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
      "id": 50,
      "name": "Product #50 - 8149",
      "slug": "product-50-8149",
      "master_id": 94,
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
GET /api/products?ids=52%2C53%2C54
Host: example.org
Cookie: 
```

`GET /api/products`

#### Parameters


```json
ids: 52,53,54
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
Date: Thu, 02 Jan 2020 16:00:23 GMT
Surrogate-Control: max-age=900
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;894deaf7a6360b87c4121f31fa46e48e&quot;
X-Request-Id: 821b68d3-d219-4596-a9c5-f4ca7357ef51
X-Runtime: 0.097732
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
      "id": 52,
      "name": "Product #52 - 3195",
      "description": "As seen on TV!",
      "available_on": "2019-01-02T11:00:23.176-05:00",
      "slug": "product-52-3195",
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
        "id": 96,
        "name": "Product #52 - 3195",
        "sku": "SKU-96",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-52-3195",
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
      "id": 53,
      "name": "Product #53 - 6241",
      "description": "As seen on TV!",
      "available_on": "2019-01-02T11:00:23.238-05:00",
      "slug": "product-53-6241",
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
        "id": 97,
        "name": "Product #53 - 6241",
        "sku": "SKU-97",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-53-6241",
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
      "id": 54,
      "name": "Product #54 - 9658",
      "description": "As seen on TV!",
      "available_on": "2019-01-02T11:00:23.302-05:00",
      "slug": "product-54-9658",
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
        "id": 98,
        "name": "Product #54 - 9658",
        "sku": "SKU-98",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-54-9658",
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
ETag: W/&quot;56a9cfa4ebdaf7b997c1c472fb66db48&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 2e315c98-c83c-4c6b-863d-ac4e60e7a366
X-Runtime: 0.048089
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
      "id": 48,
      "name": "Product #48 - 4392",
      "description": "As seen on TV!",
      "available_on": "2019-01-02T11:00:22.660-05:00",
      "slug": "product-48-4392",
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
        "id": 92,
        "name": "Product #48 - 4392",
        "sku": "SKU-92",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-48-4392",
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
ETag: W/&quot;e4d776e6b551ea5473230e9db2b62ab2&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 8097ca30-f0bf-4386-a591-eb9151449df8
X-Runtime: 0.070042
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
      "id": 46,
      "name": "Product #46 - 2180",
      "description": "As seen on TV!",
      "available_on": "2019-01-02T11:00:22.329-05:00",
      "slug": "product-46-2180",
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
        "id": 90,
        "name": "Product #46 - 2180",
        "sku": "SKU-90",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-46-2180",
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
Authorizat IO N: Bearer 182c1b2ed7aefaad39343a6218164d9cf2c96f3d6f16dae9
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
X-Request-Id: b53fb54d-5f9e-4c44-8db4-4658984bec47
X-Runtime: 0.035416
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
X-Request-Id: b890d4d8-ac72-4b1f-9d32-5ca430721776
X-Runtime: 0.013345
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
GET /api/recently_viewed?recently_viewed[session_id]=sha38a5mll2dpzel0qrjhnt0a4q7zt294ehj903snnipf9co0mm8gfw66lpovrdyvev8rmw4o5nggceomc6jy7vkez9hmy26cdgimc4tf7ojcygou2oq7n54bnmye1qdm7bviftcp2zz5d94z4q1p9a9gfgj7y99qcg471k4kvgwulwh22yfp4bkxkyw0mjg0dep1zsstr2vapdilgvm8soq9bkd27c6x0qgga4tvz2j9ynstxi3ol1cfw4sjyi&amp;recently_viewed[user_id]=1302
Accept: application/json
Host: example.org
Cookie: 
```

`GET /api/recently_viewed`

#### Parameters


```json
recently_viewed: {&quot;session_id&quot;=&gt;&quot;sha38a5mll2dpzel0qrjhnt0a4q7zt294ehj903snnipf9co0mm8gfw66lpovrdyvev8rmw4o5nggceomc6jy7vkez9hmy26cdgimc4tf7ojcygou2oq7n54bnmye1qdm7bviftcp2zz5d94z4q1p9a9gfgj7y99qcg471k4kvgwulwh22yfp4bkxkyw0mjg0dep1zsstr2vapdilgvm8soq9bkd27c6x0qgga4tvz2j9ynstxi3ol1cfw4sjyi&quot;, &quot;user_id&quot;=&gt;&quot;1302&quot;}
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
ETag: W/&quot;10f89756d5c861c3651e8251a33bfd94&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 96971bc0-0240-4c5e-bb9d-ff6997a9ae15
X-Runtime: 0.004150
Vary: Origin
Content-Length: 119
200 OK
```


```json
[
  {
    "at": "2020-01-02T11:00:16.659-05:00",
    "variant_id": "var1"
  },
  {
    "at": "2020-01-02T11:05:16.659-05:00",
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
recently_viewed[session_id]=zfw0bogr77hgq99qfus9l4czoy4sbhm7smwtffg7exoe0o0nc8ve315ngm0f4rlbnrfozd73ots10jkzpusmh0b7uuk7693zsdz8e0ti8k7dx5xkk5a1ozvurljrmkfn83195cp6gooy36w1bdzol6qr5wm7lzej9xb9hl6ciwpt5p70xtw42l2qymu975t83z7cdc92cou3ozfqbp6ksccifztdtgzx4hxq9pvddon1k6k3xa1xndaebp84uk6&recently_viewed[user_id]=87368&recently_viewed[variant_id]=foo
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
X-Request-Id: 00895dbc-5948-44e5-a151-c2d5c1ef0659
X-Runtime: 0.028369
Vary: Origin
204 No Content
```




# Return Authorizations

Get a single user return authorziation

## Can get another user&#39;s return authorization


### Request

#### Endpoint

```plaintext
GET /api/returns/RA124346658
Authorizat IO N: Bearer 74fa73c27919b198172e95f51aec4143b5b145aa59157406
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
ETag: W/&quot;7ea9dd51192af3284224100c2f565fa6&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: dc78bdc5-dd97-4b4c-b83c-41593b2b2a9a
X-Runtime: 0.036356
Vary: Origin
Content-Length: 2912
200 OK
```


```json
{
  "id": 2,
  "number": "RA124346658",
  "state": "authorized",
  "order_id": 6,
  "memo": "Items were broken",
  "created_at": "2020-01-02T11:00:17.970-05:00",
  "updated_at": "2020-01-02T11:00:17.970-05:00",
  "amount": "10.0",
  "reason": {
    "id": 3,
    "name": "Defect #3",
    "active": true,
    "mutable": true,
    "created_at": "2020-01-02T11:00:17.966-05:00",
    "updated_at": "2020-01-02T11:00:17.966-05:00",
    "mirakl_code": null
  },
  "order": {
    "id": 6,
    "number": "M189274803",
    "item_total": "10.0",
    "total": "110.0",
    "state": "complete",
    "adjustment_total": "0.0",
    "user_id": 29,
    "completed_at": "2020-01-02T11:00:17.898-05:00",
    "bill_address_id": 11,
    "ship_address_id": 12,
    "payment_total": "110.0",
    "shipment_state": "shipped",
    "payment_state": "paid",
    "email": "email29@example.com",
    "special_instructions": null,
    "created_at": "2020-01-02T11:00:17.834-05:00",
    "updated_at": "2020-01-02T11:00:17.950-05:00",
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
    "guest_token": "toS9ijzV576lOZ7Z-qnUIw",
    "canceled_at": null,
    "canceler_id": null,
    "store_id": 6,
    "approver_name": null,
    "frontend_viewable": true,
    "is_gift": false,
    "gift_email": null,
    "gift_message": null,
    "gift_card_total": "0.0"
  },
  "ship_address": {
    "id": 12,
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
    "id": 11,
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
      "name": "Product #19 - 4730",
      "brand": null,
      "brand_slug": null,
      "image": null,
      "product_slug": "product-19-4730",
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
        "id": 6,
        "name": "Credit Card"
      },
      "source": {
        "id": 2,
        "month": "12",
        "year": "2021",
        "cc_type": null,
        "last_digits": "1111",
        "name": "Spree Commerce",
        "gateway_customer_profile_id": "BGS-101204",
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
Authorizat IO N: Bearer d09f5e9160310844c07ea048bc03e3b1ab789507791f257b
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
ETag: W/&quot;6ad3a6eebdb67e2c671e2655e33bf38f&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 21bcdc4b-53e2-4cde-aa7d-7b88fd6e5418
X-Runtime: 0.011454
Vary: Origin
Content-Length: 169
200 OK
```


```json
{
  "return_authorizations": [
    {
      "number": "RA232111480",
      "created_at": "2020-01-02T11:00:18.855-05:00",
      "return_amount": "10.0",
      "order_number": "M235784177",
      "state": "authorized"
    }
  ]
}
```



## returns a 200


### Request

#### Endpoint

```plaintext
GET /api/returns/RA120338715
Authorizat IO N: Bearer f85e9328762a989b961c49669792d9101bf7c67dfd83a036
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
ETag: W/&quot;0a09b218f2d9e44a3f305d937b0ddc8c&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: ef321970-ae9a-4b1c-8751-d5863425f39d
X-Runtime: 0.079892
Vary: Origin
Content-Length: 2833
200 OK
```


```json
{
  "id": 1,
  "number": "RA120338715",
  "state": "authorized",
  "order_id": 5,
  "memo": "Items were broken",
  "created_at": "2020-01-02T11:00:17.482-05:00",
  "updated_at": "2020-01-02T11:00:17.482-05:00",
  "amount": "10.0",
  "reason": {
    "id": 1,
    "name": "Defect #1",
    "active": true,
    "mutable": true,
    "created_at": "2020-01-02T11:00:17.473-05:00",
    "updated_at": "2020-01-02T11:00:17.473-05:00",
    "mirakl_code": null
  },
  "order": {
    "id": 5,
    "number": "M758703762",
    "item_total": "10.0",
    "total": "110.0",
    "state": "complete",
    "adjustment_total": "0.0",
    "user_id": 28,
    "completed_at": "2020-01-02T11:00:17.293-05:00",
    "bill_address_id": 9,
    "ship_address_id": 10,
    "payment_total": "110.0",
    "shipment_state": "shipped",
    "payment_state": "paid",
    "email": "email28@example.com",
    "special_instructions": null,
    "created_at": "2020-01-02T11:00:17.226-05:00",
    "updated_at": "2020-01-02T11:00:17.434-05:00",
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
    "guest_token": "PhYmPNMWEsxdxbSbL0MLtQ",
    "canceled_at": null,
    "canceler_id": null,
    "store_id": 5,
    "approver_name": null,
    "frontend_viewable": true,
    "is_gift": false,
    "gift_email": null,
    "gift_message": null,
    "gift_card_total": "0.0"
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
      "name": "Product #18 - 7867",
      "brand": null,
      "brand_slug": null,
      "image": null,
      "product_slug": "product-18-7867",
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
        "id": 4,
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
GET /api/returns/RA472774074
Authorizat IO N: Bearer 307a9310d491e8132266919e210e4b9eeaa91854cefe2946
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
X-Request-Id: ff1a8172-25e8-4a6d-bd87-d715e1a5606b
X-Runtime: 0.010793
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
stock_request[email]=marybelle%40glover.us&stock_request[variant_id]=129
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
X-Request-Id: a02173fc-8c94-49b4-a5a6-3ded87ef63cf
X-Runtime: 0.004357
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
stock_request[email]=foo&stock_request[variant_id]=125
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
X-Request-Id: ecb8442c-b029-491a-83b8-5eac30110bfa
X-Runtime: 0.031642
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
stock_request[email]=cara.mayer%40bashirian.biz&stock_request[variant_id]=127
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
X-Request-Id: 4a51fd43-1574-4604-8429-bdd59fd9fa7c
X-Runtime: 0.004577
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
Authorizat IO N: Bearer ddb8fe80f8c0626a2b058ccdea945b3851d98f91a0c74987
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
ETag: W/&quot;a6a73daf60ba1bd8049f2046412642c9&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 3a822fa5-9322-4289-b391-2b2ecd5815d7
X-Runtime: 0.037459
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
      "created_at": "2020-01-02T11:00:16.922-05:00"
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
Authorizat IO N: Bearer 8aae90730a98d32ba14a84fba85031bfe8c0fe689be2f3ce
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/subscribers`

#### Parameters


```json
subscriber[email]=nerissa%40hartmann.co.uk&subscriber[user_id]=51&subscriber[first_name]=Althea&subscriber[last_name]=Hintz&subscriber[status]=subscribed
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
ETag: W/&quot;0e69c57cc3c0f002b0565e49d8fa1964&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: e0fcb478-acd8-4270-ba70-bed42e1ef889
X-Runtime: 0.009853
Vary: Origin
Content-Length: 175
201 Created
```


```json
{
  "id": 2,
  "user_id": 51,
  "email": "nerissa@hartmann.co.uk",
  "first_name": "Althea",
  "last_name": "Hintz",
  "source": "",
  "status": "subscribed",
  "created_at": "2020-01-02T11:00:25.325-05:00"
}
```



## Delete a subscriber


### Request

#### Endpoint

```plaintext
DELETE /api/subscribers/3
Accept: application/json
Authorizat IO N: Bearer a6090517b6ac5877e49724c722e8c664dc69b32e89700ef0
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
X-Request-Id: baf14472-363b-46e1-bf36-eed6abbdb5da
X-Runtime: 0.007301
Vary: Origin
204 No Content
```




## Get a single subscriber by id


### Request

#### Endpoint

```plaintext
GET /api/subscribers/1
Accept: application/json
Authorizat IO N: Bearer e33283933db3152f1987bfefc34f12b45464a03223539358
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
ETag: W/&quot;a0afa776ba4fc515cafd8f477b9b5f60&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 2326f3a1-393a-4f51-8ce8-5bd61738432d
X-Runtime: 0.038016
Vary: Origin
Content-Length: 173
200 OK
```


```json
{
  "id": 1,
  "user_id": 50,
  "email": "terese@kunze.co.uk",
  "first_name": "Lashawn",
  "last_name": "Blanda",
  "source": "",
  "status": "subscribed",
  "created_at": "2020-01-02T11:00:25.267-05:00"
}
```



## Get all subscribers


### Request

#### Endpoint

```plaintext
GET /api/subscribers
Accept: application/json
Authorizat IO N: Bearer 5999c9553abb7755021181c43b7f3348d2c080b35f6c57fe
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
ETag: W/&quot;f3f57509118f1ad3b469bdd89c395770&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 5dd8f6cc-3569-45cd-8dd2-94baab52ea8f
X-Runtime: 0.011192
Vary: Origin
Content-Length: 615
200 OK
```


```json
{
  "subscribers": [
    {
      "id": 4,
      "user_id": null,
      "email": "deanne@fritschledner.com",
      "first_name": "Inge",
      "last_name": "Walter",
      "source": "",
      "status": "subscribed",
      "created_at": "2020-01-02T11:00:25.351-05:00"
    },
    {
      "id": 5,
      "user_id": null,
      "email": "blanch@rippin.biz",
      "first_name": "Delta",
      "last_name": "Ziemann",
      "source": "",
      "status": "subscribed",
      "created_at": "2020-01-02T11:00:25.353-05:00"
    },
    {
      "id": 6,
      "user_id": null,
      "email": "chrystal@glover.biz",
      "first_name": "Lucilla",
      "last_name": "Dibbert",
      "source": "",
      "status": "subscribed",
      "created_at": "2020-01-02T11:00:25.354-05:00"
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
PATCH /api/subscribers/7
Accept: application/json
Authorizat IO N: Bearer a953c5d51d504db559bf0c0f9abc276d2c7bdcbe712ce72a
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
ETag: W/&quot;c140b3545f6e18bdce85fa7a9c9de32d&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 52030e80-948b-4540-b46e-c22bc66fddb8
X-Runtime: 0.008950
Vary: Origin
Content-Length: 181
200 OK
```


```json
{
  "id": 7,
  "user_id": 54,
  "email": "kyle_dicki@koepp.biz",
  "first_name": "Doloris",
  "last_name": "McCullough",
  "source": "",
  "status": "unsubscribed",
  "created_at": "2020-01-02T11:00:25.392-05:00"
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
Authorizat IO N: Bearer 9ea2951858a37d66dccf55c03a9df10335971420416b0c3e
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
X-Request-Id: 2d9307cb-596b-42e1-af12-1534e4049d7d
X-Runtime: 0.039352
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
ETag: W/&quot;29adac5517584ad369e0de79413b0014&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: c82797ad-624e-4d44-a4d7-128809bde775
X-Runtime: 0.033955
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
      "id": 11,
      "name": "Category",
      "pretty_name": "Category",
      "permalink": "category",
      "parent_id": null,
      "taxonomy_id": 4,
      "url_override": null,
      "description": "Category",
      "icon": "/assets/default_taxon.png",
      "taxons": [
        {
          "id": 12,
          "name": "Kids",
          "pretty_name": "Category -> Kids",
          "permalink": "category/kids",
          "parent_id": 11,
          "taxonomy_id": 4,
          "url_override": null
        }
      ]
    },
    {
      "id": 12,
      "name": "Kids",
      "pretty_name": "Category -> Kids",
      "permalink": "category/kids",
      "parent_id": 11,
      "taxonomy_id": 4,
      "url_override": null,
      "description": "Kids",
      "icon": "/assets/default_taxon.png",
      "taxons": [
        {
          "id": 13,
          "name": "Boys",
          "pretty_name": "Category -> Kids -> Boys",
          "permalink": "category/kids/boys",
          "parent_id": 12,
          "taxonomy_id": 4,
          "url_override": null
        },
        {
          "id": 16,
          "name": "Girls",
          "pretty_name": "Category -> Kids -> Girls",
          "permalink": "category/kids/girls",
          "parent_id": 12,
          "taxonomy_id": 4,
          "url_override": null
        }
      ]
    },
    {
      "id": 13,
      "name": "Boys",
      "pretty_name": "Category -> Kids -> Boys",
      "permalink": "category/kids/boys",
      "parent_id": 12,
      "taxonomy_id": 4,
      "url_override": null,
      "description": "Boys",
      "icon": "/assets/default_taxon.png",
      "taxons": [
        {
          "id": 14,
          "name": "Boys Tops",
          "pretty_name": "Category -> Kids -> Boys -> Boys Tops",
          "permalink": "category/kids/boys/boys-tops",
          "parent_id": 13,
          "taxonomy_id": 4,
          "url_override": null
        }
      ]
    },
    {
      "id": 14,
      "name": "Boys Tops",
      "pretty_name": "Category -> Kids -> Boys -> Boys Tops",
      "permalink": "category/kids/boys/boys-tops",
      "parent_id": 13,
      "taxonomy_id": 4,
      "url_override": null,
      "description": "Boys Tops",
      "icon": "/assets/default_taxon.png",
      "taxons": [
        {
          "id": 15,
          "name": "Boys Shirts",
          "pretty_name": "Category -> Kids -> Boys -> Boys Tops -> Boys Shirts",
          "permalink": "category/kids/boys/boys-tops/boys-shirts",
          "parent_id": 14,
          "taxonomy_id": 4,
          "url_override": null
        }
      ]
    },
    {
      "id": 15,
      "name": "Boys Shirts",
      "pretty_name": "Category -> Kids -> Boys -> Boys Tops -> Boys Shirts",
      "permalink": "category/kids/boys/boys-tops/boys-shirts",
      "parent_id": 14,
      "taxonomy_id": 4,
      "url_override": null,
      "description": "Boys Shirts",
      "icon": "/assets/default_taxon.png",
      "taxons": [

      ]
    },
    {
      "id": 16,
      "name": "Girls",
      "pretty_name": "Category -> Kids -> Girls",
      "permalink": "category/kids/girls",
      "parent_id": 12,
      "taxonomy_id": 4,
      "url_override": null,
      "description": "Girls",
      "icon": "/assets/default_taxon.png",
      "taxons": [
        {
          "id": 17,
          "name": "Girls Tops",
          "pretty_name": "Category -> Kids -> Girls -> Girls Tops",
          "permalink": "category/kids/girls/girls-tops",
          "parent_id": 16,
          "taxonomy_id": 4,
          "url_override": null
        }
      ]
    },
    {
      "id": 17,
      "name": "Girls Tops",
      "pretty_name": "Category -> Kids -> Girls -> Girls Tops",
      "permalink": "category/kids/girls/girls-tops",
      "parent_id": 16,
      "taxonomy_id": 4,
      "url_override": null,
      "description": "Girls Tops",
      "icon": "/assets/default_taxon.png",
      "taxons": [
        {
          "id": 18,
          "name": "Girls Shirts",
          "pretty_name": "Category -> Kids -> Girls -> Girls Tops -> Girls Shirts",
          "permalink": "category/kids/girls/girls-tops/girls-shirts",
          "parent_id": 17,
          "taxonomy_id": 4,
          "url_override": null
        }
      ]
    },
    {
      "id": 18,
      "name": "Girls Shirts",
      "pretty_name": "Category -> Kids -> Girls -> Girls Tops -> Girls Shirts",
      "permalink": "category/kids/girls/girls-tops/girls-shirts",
      "parent_id": 17,
      "taxonomy_id": 4,
      "url_override": null,
      "description": "Girls Shirts",
      "icon": "/assets/default_taxon.png",
      "taxons": [

      ]
    },
    {
      "id": 19,
      "name": "Brand",
      "pretty_name": "Brand",
      "permalink": "brand",
      "parent_id": null,
      "taxonomy_id": 5,
      "url_override": null,
      "description": "Brand",
      "icon": "/assets/default_taxon.png",
      "taxons": [
        {
          "id": 20,
          "name": "Ruby on Rails - 3",
          "pretty_name": "Brand -> Ruby on Rails - 3",
          "permalink": "brand/ruby-on-rails-3",
          "parent_id": 19,
          "taxonomy_id": 5,
          "url_override": null
        },
        {
          "id": 21,
          "name": "Ruby on Rails - 4",
          "pretty_name": "Brand -> Ruby on Rails - 4",
          "permalink": "brand/ruby-on-rails-4",
          "parent_id": 19,
          "taxonomy_id": 5,
          "url_override": null
        }
      ]
    },
    {
      "id": 20,
      "name": "Ruby on Rails - 3",
      "pretty_name": "Brand -> Ruby on Rails - 3",
      "permalink": "brand/ruby-on-rails-3",
      "parent_id": 19,
      "taxonomy_id": 5,
      "url_override": null,
      "description": "Ruby on Rails - 3",
      "icon": "/assets/default_taxon.png",
      "taxons": [

      ]
    },
    {
      "id": 21,
      "name": "Ruby on Rails - 4",
      "pretty_name": "Brand -> Ruby on Rails - 4",
      "permalink": "brand/ruby-on-rails-4",
      "parent_id": 19,
      "taxonomy_id": 5,
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
ETag: W/&quot;e50c33c15210df73fb4b5d42ae92dae3&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 3272b6ef-c4e9-41fa-a6b6-db2445aad657
X-Runtime: 0.012744
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
      "id": 30,
      "name": "Brand",
      "pretty_name": "Brand",
      "permalink": "brand",
      "parent_id": null,
      "taxonomy_id": 7,
      "url_override": null,
      "description": "Brand",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 31,
      "name": "Ruby on Rails - 5",
      "pretty_name": "Brand -> Ruby on Rails - 5",
      "permalink": "brand/ruby-on-rails-5",
      "parent_id": 30,
      "taxonomy_id": 7,
      "url_override": null,
      "description": "Ruby on Rails - 5",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 32,
      "name": "Ruby on Rails - 6",
      "pretty_name": "Brand -> Ruby on Rails - 6",
      "permalink": "brand/ruby-on-rails-6",
      "parent_id": 30,
      "taxonomy_id": 7,
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
ETag: W/&quot;7813f82face3fa5f03bf418d09aa5eec&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 4be5af78-d88e-49a7-b3e0-2ce219b246da
X-Runtime: 0.025093
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
      "id": 33,
      "name": "Category",
      "pretty_name": "Category",
      "permalink": "category",
      "parent_id": null,
      "taxonomy_id": 8,
      "url_override": null,
      "description": "Category",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 34,
      "name": "Kids",
      "pretty_name": "Category -> Kids",
      "permalink": "category/kids",
      "parent_id": 33,
      "taxonomy_id": 8,
      "url_override": null,
      "description": "Kids",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 35,
      "name": "Boys",
      "pretty_name": "Category -> Kids -> Boys",
      "permalink": "category/kids/boys",
      "parent_id": 34,
      "taxonomy_id": 8,
      "url_override": null,
      "description": "Boys",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 36,
      "name": "Boys Tops",
      "pretty_name": "Category -> Kids -> Boys -> Boys Tops",
      "permalink": "category/kids/boys/boys-tops",
      "parent_id": 35,
      "taxonomy_id": 8,
      "url_override": null,
      "description": "Boys Tops",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 37,
      "name": "Boys Shirts",
      "pretty_name": "Category -> Kids -> Boys -> Boys Tops -> Boys Shirts",
      "permalink": "category/kids/boys/boys-tops/boys-shirts",
      "parent_id": 36,
      "taxonomy_id": 8,
      "url_override": null,
      "description": "Boys Shirts",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 38,
      "name": "Girls",
      "pretty_name": "Category -> Kids -> Girls",
      "permalink": "category/kids/girls",
      "parent_id": 34,
      "taxonomy_id": 8,
      "url_override": null,
      "description": "Girls",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 39,
      "name": "Girls Tops",
      "pretty_name": "Category -> Kids -> Girls -> Girls Tops",
      "permalink": "category/kids/girls/girls-tops",
      "parent_id": 38,
      "taxonomy_id": 8,
      "url_override": null,
      "description": "Girls Tops",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 40,
      "name": "Girls Shirts",
      "pretty_name": "Category -> Kids -> Girls -> Girls Tops -> Girls Shirts",
      "permalink": "category/kids/girls/girls-tops/girls-shirts",
      "parent_id": 39,
      "taxonomy_id": 8,
      "url_override": null,
      "description": "Girls Shirts",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 41,
      "name": "Brand",
      "pretty_name": "Brand",
      "permalink": "brand",
      "parent_id": null,
      "taxonomy_id": 9,
      "url_override": null,
      "description": "Brand",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 42,
      "name": "Ruby on Rails - 7",
      "pretty_name": "Brand -> Ruby on Rails - 7",
      "permalink": "brand/ruby-on-rails-7",
      "parent_id": 41,
      "taxonomy_id": 9,
      "url_override": null,
      "description": "Ruby on Rails - 7",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 43,
      "name": "Ruby on Rails - 8",
      "pretty_name": "Brand -> Ruby on Rails - 8",
      "permalink": "brand/ruby-on-rails-8",
      "parent_id": 41,
      "taxonomy_id": 9,
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
ETag: W/&quot;f5cc0d6b5a506a4f061158eb7bb85145&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 23b98c17-b5e9-4b19-902b-12f14c405c39
X-Runtime: 0.009141
Vary: Origin
Content-Length: 139
200 OK
```


```json
[
  {
    "id": 45,
    "name": "Kids",
    "navigation_url": "/kids",
    "parent_id": 44,
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
user[email]=email59%40example.com&user[password]=secret
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
Authorization: Bearer c05bd7432b92e29e8359903041e044ed97daf34b386cde70
ETag: W/&quot;6e8331de35a94486217dd62622bb1dba&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: fe15686f-2144-4e34-9b78-3d0c23fa2103
X-Runtime: 0.013493
Vary: Origin
Content-Length: 562
200 OK
```


```json
{
  "id": 59,
  "email": "email59@example.com",
  "persistence_token": null,
  "perishable_token": null,
  "last_request_at": null,
  "login": "email59@example.com",
  "ship_address_id": null,
  "bill_address_id": null,
  "created_at": "2020-01-02T11:00:28.513-05:00",
  "updated_at": "2020-01-02T11:00:28.515-05:00",
  "spree_api_key": "c05bd7432b92e29e8359903041e044ed97daf34b386cde70",
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
X-Spree-Order-Token: SJ53QUAXaGP_lYHIcwBwxg
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/users/login`

#### Parameters


```json
user[email]=email60%40example.com&user[password]=secret&order_number=M968509551
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
Authorization: Bearer e0ef50c0f6d38909ad534e0ca550711880a42848ee7ac6e3
ETag: W/&quot;b17c2db6e688e262fa5d47c99da3dedf&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: eb5941e9-393d-439f-b439-af3358e7a94d
X-Runtime: 0.013350
Vary: Origin
Content-Length: 562
200 OK
```


```json
{
  "id": 60,
  "email": "email60@example.com",
  "persistence_token": null,
  "perishable_token": null,
  "last_request_at": null,
  "login": "email60@example.com",
  "ship_address_id": null,
  "bill_address_id": null,
  "created_at": "2020-01-02T11:00:28.536-05:00",
  "updated_at": "2020-01-02T11:00:28.538-05:00",
  "spree_api_key": "e0ef50c0f6d38909ad534e0ca550711880a42848ee7ac6e3",
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
Authorizat IO N: Bearer 7358e3d38f83f3bbb5528d9dfdf88baa545296280d3cc70c
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
Authorization: Bearer 7358e3d38f83f3bbb5528d9dfdf88baa545296280d3cc70c
ETag: W/&quot;8364df1589303703ce5436ab5ecaf29c&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 609782c0-a324-48ff-afbc-58075bb91c50
X-Runtime: 0.025727
Vary: Origin
Content-Length: 1521
200 OK
```


```json
{
  "email": "email61@example.com",
  "first_name": null,
  "last_name": null,
  "id": 62,
  "subscribed": false,
  "addresses": [
    {
      "id": 29,
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
      "default": true
    },
    {
      "id": 28,
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
      "default": false
    }
  ],
  "payment_sources": [
    {
      "id": 4,
      "default": true,
      "source": {
        "id": 4,
        "payment_type": "CreditCard",
        "token": null,
        "created_at": "2020-01-02T11:00:28.963-05:00",
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
        "id": 5,
        "payment_type": "ApplePayCard",
        "token": null,
        "created_at": "2020-01-02T11:00:28.993-05:00",
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
        "id": 6,
        "payment_type": "PayPalAccount",
        "token": null,
        "created_at": "2020-01-02T11:00:29.035-05:00",
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
Authorization: Bearer 60b14219985d88f2b9ab521b34b12a74567a62f67b28e8f7
ETag: W/&quot;9ad36a9aa768813603b6372a716f6064&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: b5373943-042b-4e2e-90a7-e17f1a4f61d0
X-Runtime: 0.036370
Vary: Origin
Content-Length: 185
201 Created
```


```json
{
  "id": 61,
  "email": "test@example.com",
  "created_at": "2020-01-02T11:00:28.863-05:00",
  "updated_at": "2020-01-02T11:00:28.865-05:00",
  "subscribed": false,
  "bill_address": null,
  "ship_address": null
}
```



## Subscribe a user


### Request

#### Endpoint

```plaintext
PUT /api/users/64/subscribe
Authorizat IO N: Bearer 573853cce9d7fc6be2af367cfcf3a0b37021b7c8e66a9d77
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
Authorization: Bearer 573853cce9d7fc6be2af367cfcf3a0b37021b7c8e66a9d77
ETag: W/&quot;fa3af0d60273b33403b1c45c065d949e&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 08439e98-cb67-49fb-bd87-8843dc0f6cf1
X-Runtime: 0.013970
Vary: Origin
Content-Length: 187
200 OK
```


```json
{
  "id": 64,
  "email": "email63@example.com",
  "created_at": "2020-01-02T11:00:29.101-05:00",
  "updated_at": "2020-01-02T11:00:29.102-05:00",
  "subscribed": true,
  "bill_address": null,
  "ship_address": null
}
```



## Unsubscribe a user


### Request

#### Endpoint

```plaintext
PUT /api/users/63/unsubscribe
Authorizat IO N: Bearer b696d0b7e3c84e1cc6d411d22f967f69bad94a588a3dcee4
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
Authorization: Bearer b696d0b7e3c84e1cc6d411d22f967f69bad94a588a3dcee4
ETag: W/&quot;0698ae0c0f755340fefaaf288ef6301d&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 859db4e0-b2c7-4f4c-9360-c8757d40ad06
X-Runtime: 0.013411
Vary: Origin
Content-Length: 188
200 OK
```


```json
{
  "id": 63,
  "email": "email62@example.com",
  "created_at": "2020-01-02T11:00:29.074-05:00",
  "updated_at": "2020-01-02T11:00:29.076-05:00",
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
GET /api/variants/101
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
ETag: W/&quot;42544e7264272cdb99ec4730e7c26f84&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 4d22c7fd-0368-47be-88e0-77dc5434d58e
X-Runtime: 0.103046
Vary: Origin
Content-Length: 1939
200 OK
```


```json
{
  "id": 101,
  "name": "Product #56 - 5896",
  "sku": "SKU-100",
  "weight": "0.0",
  "height": null,
  "width": null,
  "depth": null,
  "is_master": false,
  "slug": "product-56-5896",
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
    {
      "id": 1,
      "position": 1,
      "attachment_content_type": "image/jpeg",
      "attachment_file_name": "thinking-cat.jpg",
      "type": "Spree::Image",
      "attachment_updated_at": "2020-01-02T11:00:24.929-05:00",
      "attachment_width": 489,
      "attachment_height": 490,
      "alt": null,
      "viewable_type": "Spree::Variant",
      "viewable_id": 101,
      "mini_url": "/spree/products/1/mini/thinking-cat.jpg?1577980824",
      "small_url": "/spree/products/1/small/thinking-cat.jpg?1577980824",
      "product_url": "/spree/products/1/product/thinking-cat.jpg?1577980824",
      "large_url": "/spree/products/1/large/thinking-cat.jpg?1577980824"
    }
  ],
  "variant_properties": [

  ],
  "stock_items": [

  ],
  "prices": [
    {
      "id": 67,
      "vendor_id": 163,
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
      "id": 68,
      "vendor_id": 164,
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
Authorizat IO N: Bearer f799e353035812ce21bad1cdf5819d3ac3039bb2ecdee164
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
ETag: W/&quot;05005e14dcb7f579996ffcb8e26d8b88&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: f9548678-301e-489d-9e77-fd841c76df27
X-Runtime: 0.036738
Vary: Origin
Content-Length: 206
200 OK
```


```json
[
  {
    "id": 1,
    "user_id": 23,
    "payment_source_type": "SolidusPaypalBraintree::Source",
    "payment_source_id": 1,
    "default": false,
    "created_at": "2020-01-02T11:00:16.738-05:00",
    "updated_at": "2020-01-02T11:00:16.738-05:00"
  }
]
```



## Remove the payment from the user wallet


### Request

#### Endpoint

```plaintext
DELETE /api/wallet_payment_sources/3
Accept: application/json
Authorizat IO N: Bearer 1d5308882f554a4aad195304408aed076bb8c1636318d5d0
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
X-Request-Id: 7a6243c8-e16d-42d6-9cc6-d570cd19c5e2
X-Runtime: 0.013400
Vary: Origin
204 No Content
```




## Set a wallet payment source as the default user payment method


### Request

#### Endpoint

```plaintext
POST /api/wallet_payment_sources/2/default
Accept: application/json
Authorizat IO N: Bearer 04b9a3f9e8e735661481898c98dd9fc95dba0ad0efbfb400
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
X-Request-Id: 60fe7497-2dc5-441a-ba9f-5014d97f495e
X-Runtime: 0.016371
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
Authorizat IO N: Bearer ee8e52ae78ac40467c61ab6820f8d3fc3963ba96449885e7
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/wished_products`

#### Parameters


```json
wished_product[wishlist_id]=34&wished_product[variant_id]=76&wished_product[quantity]=2&wished_product[remark]=Foo+bar
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
ETag: W/&quot;43c86aaa5aa6158876c739ce758a0101&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 5a49922b-4818-437b-87b4-93dc95c68974
X-Runtime: 0.012234
Vary: Origin
Content-Length: 74
201 Created
```


```json
{
  "id": 25,
  "wishlist_id": 34,
  "variant_id": 76,
  "quantity": 2,
  "remark": "Foo bar"
}
```



## Delete a wished product


### Request

#### Endpoint

```plaintext
DELETE /api/wished_products/22
Accept: application/json
Authorizat IO N: Bearer e82636e543d7a244fc4e57a758d613f71a4b6c4f8f09ed9b
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
X-Request-Id: 1a6e2d58-240c-4334-81c8-bb4daf3ecb57
X-Runtime: 0.012090
Vary: Origin
204 No Content
```




## Get a single wished product


### Request

#### Endpoint

```plaintext
GET /api/wished_products/10
Accept: application/json
Authorizat IO N: Bearer e2e57f21f99cd96c00e6467b72de31ce1fd3cd44826352eb
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
ETag: W/&quot;794e4e0ab56d724b9291c808705e5073&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 86b2676f-5a39-40dd-8ca5-226d391b79e8
X-Runtime: 0.041221
Vary: Origin
Content-Length: 69
200 OK
```


```json
{
  "id": 10,
  "wishlist_id": 29,
  "variant_id": 44,
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
Authorizat IO N: Bearer 6978bcc8ed392fb16fce8ab7a1b634c6736db44cb49fa51c
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
ETag: W/&quot;ccb3cb5c00dc4403623eed0116fa48cd&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 1f66ef6d-bcc1-4d02-a151-03219ce5d570
X-Runtime: 0.010136
Vary: Origin
Content-Length: 298
200 OK
```


```json
{
  "wished_products": [
    {
      "id": 26,
      "wishlist_id": 35,
      "variant_id": 78,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 27,
      "wishlist_id": 36,
      "variant_id": 80,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 28,
      "wishlist_id": 37,
      "variant_id": 82,
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
Authorizat IO N: Bearer d2290cd4d2fc647a18bf2093b56d659ed43455277e60486a
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
ETag: W/&quot;84966f12784854f56da822b8b58ad5e2&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 76a4f70d-353b-4264-b68e-8a28743fea7b
X-Runtime: 0.102885
Vary: Origin
Content-Length: 2086
200 OK
```


```json
{
  "wished_products": [
    {
      "id": 16,
      "wishlist_id": 31,
      "variant_id": 56,
      "quantity": 1,
      "remark": null,
      "variant": {
        "id": 56,
        "name": "Product #28 - 8450",
        "sku": "SKU-55",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-28-8450",
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
      "wishlist_id": 31,
      "variant_id": 58,
      "quantity": 1,
      "remark": null,
      "variant": {
        "id": 58,
        "name": "Product #29 - 9189",
        "sku": "SKU-57",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-29-9189",
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
        "variant_properties": [

        ],
        "stock_items": [

        ],
        "prices": [

        ]
      }
    },
    {
      "id": 18,
      "wishlist_id": 31,
      "variant_id": 60,
      "quantity": 1,
      "remark": null,
      "variant": {
        "id": 60,
        "name": "Product #30 - 7767",
        "sku": "SKU-59",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-30-7767",
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



## Get all wished products with variants


### Request

#### Endpoint

```plaintext
GET /api/wished_products?with_variant=true
Accept: application/json
Authorizat IO N: Bearer 341e6f99c0cc219bcd8ba812d1d8324fccd19967c85c6344
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
ETag: W/&quot;b7e2c7cce8dbb6b364b4fc618e81008e&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 0fb7877b-c617-4ac8-8f77-1223e1817fef
X-Runtime: 0.087852
Vary: Origin
Content-Length: 2146
200 OK
```


```json
{
  "wished_products": [
    {
      "id": 29,
      "wishlist_id": 38,
      "variant_id": 84,
      "quantity": 1,
      "remark": null,
      "variant": {
        "id": 84,
        "name": "Product #42 - 6866",
        "sku": "SKU-83",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-42-6866",
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
      "variant_id": 86,
      "quantity": 1,
      "remark": null,
      "variant": {
        "id": 86,
        "name": "Product #43 - 6120",
        "sku": "SKU-85",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-43-6120",
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
      "variant_id": 88,
      "quantity": 1,
      "remark": null,
      "variant": {
        "id": 88,
        "name": "Product #44 - 3359",
        "sku": "SKU-87",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-44-3359",
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
Authorizat IO N: Bearer b9ce00bb13804811872e7061026704969cb0d76865279446
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
ETag: W/&quot;422bd03b131f6f6cfea6a27feadaf5ba&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 071cea3e-f6ef-4bb5-96c9-09456d9f0913
X-Runtime: 0.010550
Vary: Origin
Content-Length: 298
200 OK
```


```json
{
  "wished_products": [
    {
      "id": 13,
      "wishlist_id": 30,
      "variant_id": 50,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 14,
      "wishlist_id": 30,
      "variant_id": 52,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 15,
      "wishlist_id": 30,
      "variant_id": 54,
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
PATCH /api/wished_products/19
Accept: application/json
Authorizat IO N: Bearer 2f4f1f6516bc19f0fb67c2320a1929b176d3508c67a6e00d
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/wished_products/:id`

#### Parameters


```json
wished_product[wishlist_id]=32&wished_product[variant_id]=68&wished_product[quantity]=2&wished_product[remark]=Foo+bar
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
ETag: W/&quot;9d96b03d7c03b921905f3cc5801ad0eb&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: f405144a-6cc2-4869-a3f0-eef6582b46b0
X-Runtime: 0.013238
Vary: Origin
Content-Length: 74
200 OK
```


```json
{
  "id": 19,
  "wishlist_id": 32,
  "variant_id": 68,
  "quantity": 2,
  "remark": "Foo bar"
}
```



# Wishlists

Create a wishlist. Any user can create their own wishlist, admins can create wishlists for others.

## Create a wishlist


### Request

#### Endpoint

```plaintext
POST /api/wishlists
Accept: application/json
Authorizat IO N: Bearer 3e51584b72544f47a8e6918178513fab0c994bb21b97dca6
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/wishlists`

#### Parameters


```json
wishlist[name]&wishlist[user_id]=5&wishlist[is_default]=true&wishlist[is_public]=false
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
ETag: W/&quot;ae33b9d5401cf40d7324d49158107f5e&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 128908db-e61f-4675-b91e-0ed513b5fb41
X-Runtime: 0.061988
Vary: Origin
Content-Length: 98
201 Created
```


```json
{
  "id": 1,
  "user_id": 5,
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
Authorizat IO N: Bearer 6ce58bfaebf80bd7b45637bd5ae1d9f976ed570158932479
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
X-Request-Id: 195ebecd-94db-48d6-b980-dc3a5ac4caf5
X-Runtime: 0.012985
Vary: Origin
204 No Content
```




## Get a single wishlist


### Request

#### Endpoint

```plaintext
GET /api/wishlists/13
Accept: application/json
Authorizat IO N: Bearer a0e6b1dc0ad4c52211122d79ed11073459292ef5ba496721
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
ETag: W/&quot;4bbeabc43f90ac0af979f7a544a7a6d8&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: ceee1643-c498-4b4d-90e2-e3b55f86a82b
X-Runtime: 0.011267
Vary: Origin
Content-Length: 307
200 OK
```


```json
{
  "id": 13,
  "user_id": 18,
  "name": "Wishlist #11",
  "is_public": false,
  "is_default": true,
  "wished_products": [
    {
      "id": 1,
      "wishlist_id": 13,
      "variant_id": 18,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 2,
      "wishlist_id": 13,
      "variant_id": 20,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 3,
      "wishlist_id": 13,
      "variant_id": 22,
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
Authorizat IO N: Bearer 3f0fa92397a76f9185efd6502abac064f8e9e2244de6d699
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
ETag: W/&quot;acb297522e480aba572a5bfc735f412f&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 244a9b54-1b43-4a44-80ea-447ccb1b3879
X-Runtime: 0.018673
Vary: Origin
Content-Length: 875
200 OK
```


```json
{
  "wishlists": [
    {
      "id": 3,
      "user_id": 7,
      "name": "Wishlist #1",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 4,
      "user_id": 8,
      "name": "Wishlist #2",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 5,
      "user_id": 9,
      "name": "Wishlist #3",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 6,
      "user_id": 10,
      "name": "Wishlist #4",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 7,
      "user_id": 11,
      "name": "Wishlist #5",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 8,
      "user_id": 12,
      "name": "Wishlist #6",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 9,
      "user_id": 13,
      "name": "Wishlist #7",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 10,
      "user_id": 14,
      "name": "Wishlist #8",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 11,
      "user_id": 15,
      "name": "Wishlist #9",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 12,
      "user_id": 16,
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
Authorizat IO N: Bearer da08065b0d60182970a520da6bb7fc0c77a75f8c7dead949
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
ETag: W/&quot;22d361d42ae5abb302b9faaee27f41b3&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: ac6ba35a-8d26-42d8-8365-9b5e1ad06d2d
X-Runtime: 0.010551
Vary: Origin
Content-Length: 307
200 OK
```


```json
{
  "id": 28,
  "user_id": 22,
  "name": "Wishlist #26",
  "is_public": false,
  "is_default": true,
  "wished_products": [
    {
      "id": 7,
      "wishlist_id": 28,
      "variant_id": 30,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 8,
      "wishlist_id": 28,
      "variant_id": 32,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 9,
      "wishlist_id": 28,
      "variant_id": 34,
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
Authorizat IO N: Bearer c131b55bd506466555a06e7356412f1898ec14b3f4e95146
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
ETag: W/&quot;49056b2b4357ec667ff74e064efd312f&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: eb8f680b-0aaa-4690-bc1a-542f502ae5ee
X-Runtime: 0.010868
Vary: Origin
Content-Length: 903
200 OK
```


```json
{
  "wishlists": [
    {
      "id": 18,
      "user_id": 21,
      "name": "Wishlist #16",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 19,
      "user_id": 21,
      "name": "Wishlist #17",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 20,
      "user_id": 21,
      "name": "Wishlist #18",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 21,
      "user_id": 21,
      "name": "Wishlist #19",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 22,
      "user_id": 21,
      "name": "Wishlist #20",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 23,
      "user_id": 21,
      "name": "Wishlist #21",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 24,
      "user_id": 21,
      "name": "Wishlist #22",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 25,
      "user_id": 21,
      "name": "Wishlist #23",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 26,
      "user_id": 21,
      "name": "Wishlist #24",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 27,
      "user_id": 21,
      "name": "Wishlist #25",
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
PATCH /api/wishlists/14
Accept: application/json
Authorizat IO N: Bearer 17bedee5b98ae799ccf1206687bd411cde22183720911f9a
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/wishlists/:id`

#### Parameters


```json
wishlist[name]=Another+Wishlist&wishlist[user_id]=19&wishlist[is_default]=true&wishlist[is_public]=false
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
ETag: W/&quot;1512a557650d4b01b60272e0f7b62861&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 9315a1ae-edaa-4fa6-92bd-4342b9933da9
X-Runtime: 0.021897
Vary: Origin
Content-Length: 311
200 OK
```


```json
{
  "id": 14,
  "user_id": 19,
  "name": "Another Wishlist",
  "is_public": false,
  "is_default": true,
  "wished_products": [
    {
      "id": 4,
      "wishlist_id": 14,
      "variant_id": 24,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 5,
      "wishlist_id": 14,
      "variant_id": 26,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 6,
      "wishlist_id": 14,
      "variant_id": 28,
      "quantity": 1,
      "remark": null
    }
  ]
}
```



