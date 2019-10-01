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
PUT /api/orders/M880429940/addresses/43
Accept: application/json
X-Spree-Order-Token: sJ8_zEQaAuR1oMpl73V-ow
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
ETag: W/&quot;6655bf9087369f2bfa3f8ed1a3254973&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: bc5c96e4-310f-4c2b-be33-b77de9d32eb9
X-Runtime: 0.048539
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
  "zipcode": "10041",
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
}
```



# Braintree transactions



## Creating a PayPal express checkout transaction


### Request

#### Endpoint

```plaintext
POST /api/braintree/transactions
Accept: application/json
X-Spree-Order-Token: EmcqWVFvsjwC8LoYtnX0fg
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/braintree/transactions`

#### Parameters


```json
order_id=M375585790&payment_method_id=11&options[restart_checkout]=true&transaction[email]=maryellen.oga%40mckenziemcglynn.com&transaction[nonce]=fake-paypal-billing-agreement-nonce&transaction[phone]=555-555-0199&transaction[address_attributes][first_name]=John&transaction[address_attributes][last_name]=Stamm&transaction[address_attributes][address_line_1]=A+Different+Road&transaction[address_attributes][city]=Herndon&transaction[address_attributes][state_code]=AL&transaction[address_attributes][zip]=10019&transaction[address_attributes][country_code]=US&transaction[payment_type]=PayPalAccount
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
ETag: W/&quot;3b398c705bb8fa9c6d2aab52e6377f62&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: c209eac3-e30f-4bf0-9e07-5d1f50b758ba
X-Runtime: 0.282712
Vary: Origin
Content-Length: 4839
200 OK
```


```json
{
  "id": 10,
  "number": "M375585790",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2019-10-01T14:49:44.596-04:00",
  "updated_at": "2019-10-01T14:49:44.865-04:00",
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
  "token": "EmcqWVFvsjwC8LoYtnX0fg",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 11,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 22,
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
    "id": 22,
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
      "id": 14,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 52,
      "vendor_id": 92,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 52,
        "name": "Product #26 - 7612",
        "sku": "SKU-51",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-26-7612",
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
        "product_id": 26,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #92",
      "country_iso": "US",
      "adjustments": [

      ]
    }
  ],
  "payments": [
    {
      "id": 5,
      "source_type": "SolidusPaypalBraintree::Source",
      "source_id": 5,
      "amount": "110.0",
      "display_amount": "$110.00",
      "payment_method_id": 11,
      "state": "checkout",
      "avs_response": null,
      "created_at": "2019-10-01T14:49:44.708-04:00",
      "updated_at": "2019-10-01T14:49:44.708-04:00",
      "payment_method": {
        "id": 11,
        "name": "Braintree"
      },
      "source": {
        "id": 5,
        "payment_type": "PayPalAccount",
        "token": "bgx899",
        "created_at": "2019-10-01T14:49:44.707-04:00",
        "email": "jane.doe@paypal.com"
      }
    }
  ],
  "shipments": [
    {
      "id": 11,
      "tracking": null,
      "tracking_url": null,
      "number": "H50861206405",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M375585790",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 11,
          "name": "UPS Ground",
          "admin_name": null,
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 9,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 11,
        "name": "UPS Ground",
        "admin_name": null,
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 9,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 9,
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
              "id": 14,
              "name": "ShippingCategory #14"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 52,
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
      "delivery_estimation": "Oct 03"
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
X-Spree-Order-Token: UAbvoANtIE-y9oeck3WVtA
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/braintree/transactions`

#### Parameters


```json
order_id=M443004685&payment_method_id=10&options[restart_checkout]=true&transaction[email]=maryellen.oga%40mckenziemcglynn.com&transaction[nonce]=fake-apple-pay-visa-nonce&transaction[phone]=555-555-0199&transaction[address_attributes][first_name]=John&transaction[address_attributes][last_name]=Stamm&transaction[address_attributes][address_line_1]=A+Different+Road&transaction[address_attributes][city]=Herndon&transaction[address_attributes][state_code]=AL&transaction[address_attributes][zip]=10017&transaction[address_attributes][country_code]=US&transaction[payment_type]=ApplePayCard
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
ETag: W/&quot;f6ac89989fad811763e50b580f462705&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: b8d3481b-9bcf-422b-9e7c-50d99c60d1bf
X-Runtime: 0.358649
Vary: Origin
Content-Length: 4881
200 OK
```


```json
{
  "id": 9,
  "number": "M443004685",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2019-10-01T14:49:43.916-04:00",
  "updated_at": "2019-10-01T14:49:44.291-04:00",
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
  "token": "UAbvoANtIE-y9oeck3WVtA",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 10,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 19,
    "firstname": "John",
    "lastname": "Stamm",
    "full_name": "John Stamm",
    "address1": "A Different Road",
    "address2": null,
    "city": "Herndon",
    "zipcode": "10017",
    "phone": "555-555-0199",
    "company": null,
    "alternative_phone": null,
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
    "id": 19,
    "firstname": "John",
    "lastname": "Stamm",
    "full_name": "John Stamm",
    "address1": "A Different Road",
    "address2": null,
    "city": "Herndon",
    "zipcode": "10017",
    "phone": "555-555-0199",
    "company": null,
    "alternative_phone": null,
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
      "id": 13,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 50,
      "vendor_id": 87,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 50,
        "name": "Product #25 - 1296",
        "sku": "SKU-49",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-25-1296",
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
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #87",
      "country_iso": "US",
      "adjustments": [

      ]
    }
  ],
  "payments": [
    {
      "id": 4,
      "source_type": "SolidusPaypalBraintree::Source",
      "source_id": 4,
      "amount": "110.0",
      "display_amount": "$110.00",
      "payment_method_id": 10,
      "state": "checkout",
      "avs_response": null,
      "created_at": "2019-10-01T14:49:44.074-04:00",
      "updated_at": "2019-10-01T14:49:44.074-04:00",
      "payment_method": {
        "id": 10,
        "name": "Braintree"
      },
      "source": {
        "id": 4,
        "payment_type": "ApplePayCard",
        "token": "cg7hsk",
        "created_at": "2019-10-01T14:49:44.073-04:00",
        "cc_type": "Apple Pay - Visa",
        "last_digits": "1881",
        "month": "12",
        "year": "2020"
      }
    }
  ],
  "shipments": [
    {
      "id": 9,
      "tracking": null,
      "tracking_url": null,
      "number": "H73218078214",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M443004685",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 9,
          "name": "UPS Ground",
          "admin_name": null,
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 8,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 9,
        "name": "UPS Ground",
        "admin_name": null,
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 8,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 8,
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
              "id": 13,
              "name": "ShippingCategory #13"
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
      "stock_location_address": "NY Warehouse, Washington, AL",
      "country_iso": "US",
      "international_shipping": false,
      "delivery_estimation": "Oct 03"
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
PUT /api/checkouts/M497142777/complete
Accept: application/json
X-Spree-Order-Token: R1ZSnra0GmL192IeqyqxFA
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
ETag: W/&quot;e3346a5f780c4c26b7a046fab2555729&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 2cd634f2-7663-4283-8e6e-2a06e95bd630
X-Runtime: 2.370068
Vary: Origin
Content-Length: 5018
200 OK
```


```json
{
  "id": 19,
  "number": "M497142777",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "complete",
  "adjustment_total": "0.0",
  "user_id": 85,
  "created_at": "2019-10-01T14:49:56.361-04:00",
  "updated_at": "2019-10-01T14:49:59.658-04:00",
  "completed_at": "2019-10-01T14:49:59.658-04:00",
  "payment_total": "110.0",
  "shipment_state": "ready",
  "payment_state": "paid",
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
  "total_applicable_store_credit": "0.0",
  "display_total_available_store_credit": "$0.00",
  "display_store_credit_remaining_after_capture": "$0.00",
  "canceler_id": null,
  "display_item_total": "$10.00",
  "total_quantity": 1,
  "display_total": "$110.00",
  "display_ship_total": "$100.00",
  "display_tax_total": "$0.00",
  "token": "R1ZSnra0GmL192IeqyqxFA",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 24,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    },
    {
      "id": 25,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
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
    "zipcode": "10037",
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
  "line_items": [
    {
      "id": 23,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 122,
      "vendor_id": 211,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 122,
        "name": "Product #64 - 8718",
        "sku": "SKU-121",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-64-8718",
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
        "product_id": 64,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #211",
      "country_iso": "US",
      "adjustments": [

      ]
    }
  ],
  "payments": [
    {
      "id": 10,
      "source_type": "SolidusPaypalBraintree::Source",
      "source_id": 7,
      "amount": "110.0",
      "display_amount": "$110.00",
      "payment_method_id": 24,
      "state": "completed",
      "avs_response": "M",
      "created_at": "2019-10-01T14:49:56.478-04:00",
      "updated_at": "2019-10-01T14:49:59.524-04:00",
      "payment_method": {
        "id": 24,
        "name": "Braintree"
      },
      "source": {
        "id": 7,
        "payment_type": "CreditCard",
        "token": "7mmp95",
        "created_at": "2019-10-01T14:49:56.477-04:00",
        "cc_type": "Visa",
        "last_digits": "1881",
        "month": "12",
        "year": "2020"
      }
    }
  ],
  "shipments": [
    {
      "id": 24,
      "tracking": "U10000",
      "tracking_url": null,
      "number": "H17723888812",
      "cost": "100.0",
      "shipped_at": null,
      "state": "ready",
      "order_id": "M497142777",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 24,
          "name": "UPS Ground",
          "admin_name": null,
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 18,
          "shipping_method_code": "UPS_GROUND",
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
              "id": 35,
              "name": "ShippingCategory #35"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 122,
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
      "delivery_estimation": "Oct 03"
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
PATCH /api/checkouts/M831380756
Accept: application/json
X-Spree-Order-Token: QNoWvJkz1VNwWOxwebbTkQ
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=21&order[payment_attributes][][source_attributes][nonce]=fake-apple-pay-visa-nonce&order[payment_attributes][][source_attributes][payment_type]=ApplePayCard
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
ETag: W/&quot;fae968b2410aa0bc4b83d8f811218acf&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 9ca4f9d7-339a-4e9d-9611-34f270868995
X-Runtime: 0.133406
Vary: Origin
Content-Length: 4401
200 OK
```


```json
{
  "id": 16,
  "number": "M831380756",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 82,
  "created_at": "2019-10-01T14:49:54.431-04:00",
  "updated_at": "2019-10-01T14:49:54.721-04:00",
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
  "total_applicable_store_credit": "0.0",
  "display_total_available_store_credit": "$0.00",
  "display_store_credit_remaining_after_capture": "$0.00",
  "canceler_id": null,
  "display_item_total": "$10.00",
  "total_quantity": 1,
  "display_total": "$110.00",
  "display_ship_total": "$100.00",
  "display_tax_total": "$0.00",
  "token": "QNoWvJkz1VNwWOxwebbTkQ",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 21,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 33,
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
    "address1": "A Different Road",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10032",
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
      "id": 20,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 116,
      "vendor_id": 196,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 116,
        "name": "Product #61 - 7524",
        "sku": "SKU-115",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-61-7524",
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
        "product_id": 61,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #196",
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
      "tracking": null,
      "tracking_url": null,
      "number": "H17315738555",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M831380756",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 19,
          "name": "UPS Ground",
          "admin_name": null,
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 15,
          "shipping_method_code": "UPS_GROUND",
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
              "id": 32,
              "name": "ShippingCategory #32"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 116,
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
      "delivery_estimation": "Oct 03"
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
PATCH /api/checkouts/M774196945
Accept: application/json
X-Spree-Order-Token: iJoDkllKqbsyAQo5cwKFhw
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=22&order[payment_attributes][][source_attributes][nonce]=fake-paypal-billing-agreement-nonce&order[payment_attributes][][source_attributes][payment_type]=PayPalAccount
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
ETag: W/&quot;ff86ee9e5142c2d985570b47bd3d4e5e&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: b58c1098-cd1e-442d-8db3-2bccf0121e25
X-Runtime: 0.137043
Vary: Origin
Content-Length: 4401
200 OK
```


```json
{
  "id": 17,
  "number": "M774196945",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 83,
  "created_at": "2019-10-01T14:49:55.070-04:00",
  "updated_at": "2019-10-01T14:49:55.388-04:00",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
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
  "total_applicable_store_credit": "0.0",
  "display_total_available_store_credit": "$0.00",
  "display_store_credit_remaining_after_capture": "$0.00",
  "canceler_id": null,
  "display_item_total": "$10.00",
  "total_quantity": 1,
  "display_total": "$110.00",
  "display_ship_total": "$100.00",
  "display_tax_total": "$0.00",
  "token": "iJoDkllKqbsyAQo5cwKFhw",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 22,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
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
    "zipcode": "10033",
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
  "line_items": [
    {
      "id": 21,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 118,
      "vendor_id": 201,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 118,
        "name": "Product #62 - 5734",
        "sku": "SKU-117",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-62-5734",
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
        "product_id": 62,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #201",
      "country_iso": "US",
      "adjustments": [

      ]
    }
  ],
  "payments": [

  ],
  "shipments": [
    {
      "id": 21,
      "tracking": null,
      "tracking_url": null,
      "number": "H05142004815",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M774196945",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 21,
          "name": "UPS Ground",
          "admin_name": null,
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 16,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 21,
        "name": "UPS Ground",
        "admin_name": null,
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 16,
        "shipping_method_code": "UPS_GROUND",
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
              "id": 33,
              "name": "ShippingCategory #33"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 118,
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
      "delivery_estimation": "Oct 03"
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
PATCH /api/checkouts/M129580688
Accept: application/json
X-Spree-Order-Token: 8qtezIcLqpiGyF3AgKxFmA
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=20&order[payment_attributes][][source_attributes][nonce]=fake-valid-visa-nonce&order[payment_attributes][][source_attributes][payment_type]=CreditCard
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
ETag: W/&quot;b4b4db034029bb19d1af8798cb5bcef5&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 968463af-b7b1-45cb-a1fc-a17b2770ef0a
X-Runtime: 0.145593
Vary: Origin
Content-Length: 4399
200 OK
```


```json
{
  "id": 15,
  "number": "M129580688",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 81,
  "created_at": "2019-10-01T14:49:53.717-04:00",
  "updated_at": "2019-10-01T14:49:54.078-04:00",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "email80@example.com",
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
  "token": "8qtezIcLqpiGyF3AgKxFmA",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 20,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 31,
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
    "id": 32,
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
      "id": 19,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 114,
      "vendor_id": 191,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 114,
        "name": "Product #60 - 426",
        "sku": "SKU-113",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-60-426",
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
        "product_id": 60,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #191",
      "country_iso": "US",
      "adjustments": [

      ]
    }
  ],
  "payments": [

  ],
  "shipments": [
    {
      "id": 17,
      "tracking": null,
      "tracking_url": null,
      "number": "H55205310851",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M129580688",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 17,
          "name": "UPS Ground",
          "admin_name": null,
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 14,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 17,
        "name": "UPS Ground",
        "admin_name": null,
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
              "id": 18,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 31,
              "name": "ShippingCategory #31"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 114,
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
      "delivery_estimation": "Oct 03"
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
PATCH /api/checkouts/M961180482
Accept: application/json
X-Spree-Order-Token: KVllh7Mf_qoae68pVKavWA
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=23&order[payment_attributes][][source_attributes][wallet_payment_source_id]=4
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
ETag: W/&quot;2c782c63711ed6400075414f0c70f2e9&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 33b66b96-cdd4-4c94-bb17-3510cabba9f9
X-Runtime: 0.146550
Vary: Origin
Content-Length: 4401
200 OK
```


```json
{
  "id": 18,
  "number": "M961180482",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 84,
  "created_at": "2019-10-01T14:49:55.730-04:00",
  "updated_at": "2019-10-01T14:49:56.024-04:00",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "email83@example.com",
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
  "token": "KVllh7Mf_qoae68pVKavWA",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 23,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
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
    "zipcode": "10035",
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
  "line_items": [
    {
      "id": 22,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 120,
      "vendor_id": 206,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 120,
        "name": "Product #63 - 7461",
        "sku": "SKU-119",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-63-7461",
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
        "product_id": 63,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #206",
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
      "number": "H33153234230",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M961180482",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 23,
          "name": "UPS Ground",
          "admin_name": null,
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
        "admin_name": null,
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
              "id": 21,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 34,
              "name": "ShippingCategory #34"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 120,
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
      "delivery_estimation": "Oct 03"
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
PUT /api/checkouts/M292797744
Accept: application/json
X-Spree-Order-Token: YZDuvkKSm1W8Oap0SGGgtw
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PUT /api/checkouts/:id`

#### Parameters


```json
order[ship_address_attributes][id]&order[ship_address_attributes][firstname]=John&order[ship_address_attributes][lastname]&order[ship_address_attributes][address1]=10+Lovely+Street&order[ship_address_attributes][address2]=Northwest&order[ship_address_attributes][city]=Herndon&order[ship_address_attributes][zipcode]=10039&order[ship_address_attributes][phone]=555-555-0199&order[ship_address_attributes][state_name]&order[ship_address_attributes][alternative_phone]=555-555-0199&order[ship_address_attributes][company]=Company&order[ship_address_attributes][state_id]=37&order[ship_address_attributes][country_id]=37&order[ship_address_attributes][created_at]&order[ship_address_attributes][updated_at]&order[use_billing]=true&hold_state=true
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
ETag: W/&quot;57df2c17a194094ee87c4d636b9527e9&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 3f5d4102-adc6-4922-931b-6d7a0d518851
X-Runtime: 0.128610
Vary: Origin
Content-Length: 4308
200 OK
```


```json
{
  "id": 20,
  "number": "M292797744",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "cart",
  "adjustment_total": "0.0",
  "user_id": 86,
  "created_at": "2019-10-01T14:50:00.574-04:00",
  "updated_at": "2019-10-01T14:50:00.687-04:00",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "email85@example.com",
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
  "token": "YZDuvkKSm1W8Oap0SGGgtw",
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
    "id": 41,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "10 Lovely Street",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10039",
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
    "id": 41,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "10 Lovely Street",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10039",
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
      "variant_id": 124,
      "vendor_id": 216,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 124,
        "name": "Product #65 - 7205",
        "sku": "SKU-123",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-65-7205",
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
        "product_id": 65,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #216",
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
      "tracking": "U10000",
      "tracking_url": null,
      "number": "H66542226123",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M292797744",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 25,
          "name": "UPS Ground",
          "admin_name": null,
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 19,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 25,
        "name": "UPS Ground",
        "admin_name": null,
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 19,
        "shipping_method_code": "UPS_GROUND",
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
              "id": 36,
              "name": "ShippingCategory #36"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 124,
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
      "delivery_estimation": "Oct 03"
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
POST /api/orders/M181474662/line_items
Accept: application/json
X-Spree-Order-Token: lievdthR-0oAWkjdwyIokg
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/:order_number/line_items`

#### Parameters


```json
line_item[variant_id]=28&line_item[options][vendor_id]=56
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
ETag: W/&quot;2d4655a57b9be6237d96c57cf46b1f54&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: c1572e57-c28d-4de0-af96-5ce875b6a199
X-Runtime: 0.144472
Vary: Origin
Content-Length: 891
201 Created
```


```json
{
  "id": 11,
  "quantity": 1,
  "price": "19.99",
  "variant_id": 28,
  "vendor_id": 56,
  "single_display_amount": "$19.99",
  "display_amount": "$19.99",
  "total": "19.99",
  "on_sale": false,
  "final_sale": false,
  "backordered": null,
  "promotionable": true,
  "variant": {
    "id": 28,
    "name": "Product #14 - 2163",
    "sku": "SKU-27",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": false,
    "slug": "product-14-2163",
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
    "product_id": 14,
    "brand": null,
    "brand_slug": null,
    "brand_description": null
  },
  "vendor_name": "Vendor #56",
  "country_iso": null,
  "adjustments": [

  ]
}
```



## Deleting a line item


### Request

#### Endpoint

```plaintext
DELETE /api/orders/M903176482/line_items/12
Accept: application/json
X-Spree-Order-Token: Dwg0FzjWAlYJdFVd3OHhqQ
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
X-Request-Id: b3fd1cf5-72d2-4f40-b95e-30f03ad86316
X-Runtime: 0.108520
Vary: Origin
204 No Content
```




## Updating a line item


### Request

#### Endpoint

```plaintext
PUT /api/orders/M707885293/line_items/9
Accept: application/json
X-Spree-Order-Token: r6j0uzyxPNVP8VynqMtrcw
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
ETag: W/&quot;dc61f22eee189c3f3cd1f2eaa4cd42d5&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 5fdcada0-d924-4066-bef9-0baac0f9bd5b
X-Runtime: 0.240551
Vary: Origin
Content-Length: 887
200 OK
```


```json
{
  "id": 9,
  "quantity": 2,
  "price": "10.0",
  "variant_id": 22,
  "vendor_id": 45,
  "single_display_amount": "$10.00",
  "display_amount": "$20.00",
  "total": "20.0",
  "on_sale": false,
  "final_sale": false,
  "backordered": null,
  "promotionable": true,
  "variant": {
    "id": 22,
    "name": "Product #11 - 7073",
    "sku": "SKU-21",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": false,
    "slug": "product-11-7073",
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
        "option_type_presentation": "Size",
        "position": 1
      }
    ],
    "images": [

    ],
    "product_id": 11,
    "brand": null,
    "brand_slug": null,
    "brand_description": null
  },
  "vendor_name": "Vendor #45",
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
Authorizat IO N: Bearer 6a15184de126a6e3d7796af8e9049824b774cb63dbedec45
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/minis`

#### Parameters


```json
mini[name]=Winny&mini[user_id]=63&mini[birth_year]=2019&mini[birth_month]=1&mini[birth_day]=1
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
ETag: W/&quot;7e68957879fde8626f368fbd3c389639&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 2af7faa9-256c-4bc1-832e-e8608376da96
X-Runtime: 0.012727
Vary: Origin
Content-Length: 122
201 Created
```


```json
{
  "id": 16,
  "user_id": 63,
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
DELETE /api/minis/19
Accept: application/json
Authorizat IO N: Bearer 9fed584db86ee734de9b0692e8fa24d2b3ebf30be4d85f6a
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
X-Request-Id: 46748551-593b-43c4-9d36-ead349944bbb
X-Runtime: 0.008448
Vary: Origin
204 No Content
```




## Get a single mini


### Request

#### Endpoint

```plaintext
GET /api/minis/17
Accept: application/json
Authorizat IO N: Bearer 15a302542589466dfc5f2be1a6b595ebe1a03178c4c23b01
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
ETag: W/&quot;028db46e5e4ab1e8030304825f85ebce&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 798b8853-87cf-4c4e-912b-48b70fb11733
X-Runtime: 0.009491
Vary: Origin
Content-Length: 127
200 OK
```


```json
{
  "id": 17,
  "user_id": 64,
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
Authorizat IO N: Bearer 8bf2e2571c5919a873b1e356a2fb90296f2abff2b9ce128e
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
ETag: W/&quot;5f1f615482c56c3bb3c3a811eae65344&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 64e55d59-fe87-4f9a-90a4-771d80698840
X-Runtime: 0.012407
Vary: Origin
Content-Length: 1356
200 OK
```


```json
{
  "minis": [
    {
      "id": 6,
      "user_id": 52,
      "name": "Mini",
      "birth_year": 2018,
      "birth_month": null,
      "birth_day": null,
      "gender_boy": true,
      "gender_girl": true
    },
    {
      "id": 7,
      "user_id": 53,
      "name": "Mini",
      "birth_year": 2018,
      "birth_month": null,
      "birth_day": null,
      "gender_boy": true,
      "gender_girl": true
    },
    {
      "id": 8,
      "user_id": 54,
      "name": "Mini",
      "birth_year": 2018,
      "birth_month": null,
      "birth_day": null,
      "gender_boy": true,
      "gender_girl": true
    },
    {
      "id": 9,
      "user_id": 55,
      "name": "Mini",
      "birth_year": 2018,
      "birth_month": null,
      "birth_day": null,
      "gender_boy": true,
      "gender_girl": true
    },
    {
      "id": 10,
      "user_id": 56,
      "name": "Mini",
      "birth_year": 2018,
      "birth_month": null,
      "birth_day": null,
      "gender_boy": true,
      "gender_girl": true
    },
    {
      "id": 11,
      "user_id": 57,
      "name": "Mini",
      "birth_year": 2018,
      "birth_month": null,
      "birth_day": null,
      "gender_boy": true,
      "gender_girl": true
    },
    {
      "id": 12,
      "user_id": 58,
      "name": "Mini",
      "birth_year": 2018,
      "birth_month": null,
      "birth_day": null,
      "gender_boy": true,
      "gender_girl": true
    },
    {
      "id": 13,
      "user_id": 59,
      "name": "Mini",
      "birth_year": 2018,
      "birth_month": null,
      "birth_day": null,
      "gender_boy": true,
      "gender_girl": true
    },
    {
      "id": 14,
      "user_id": 60,
      "name": "Mini",
      "birth_year": 2018,
      "birth_month": null,
      "birth_day": null,
      "gender_boy": true,
      "gender_girl": true
    },
    {
      "id": 15,
      "user_id": 61,
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
Authorizat IO N: Bearer ae956bb6167edd0be16bc16648ceb65db499abeb6684ec5f
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
ETag: W/&quot;efe357f45d9736dd768102cd4f13a84b&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: f022bda6-c81d-4792-970c-8ce4dcdebcb8
X-Runtime: 0.042774
Vary: Origin
Content-Length: 332
200 OK
```


```json
{
  "minis": [
    {
      "id": 4,
      "user_id": 51,
      "name": "Mini",
      "birth_year": 2018,
      "birth_month": null,
      "birth_day": null,
      "gender_boy": true,
      "gender_girl": true
    },
    {
      "id": 5,
      "user_id": 51,
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
PATCH /api/minis/18
Accept: application/json
Authorizat IO N: Bearer 5f175f727d5c0924ff07c805273b9caee6bac01175fed6ce
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
ETag: W/&quot;186457c290f4804b3e1d382a2f07ade4&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 5b80a58e-acd6-43f7-a60d-8040e651e7c1
X-Runtime: 0.009739
Vary: Origin
Content-Length: 128
200 OK
```


```json
{
  "id": 18,
  "user_id": 65,
  "name": "Marge",
  "birth_year": 2018,
  "birth_month": null,
  "birth_day": null,
  "gender_boy": true,
  "gender_girl": true
}
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
user_id&order_token&line_item[variant_id]=12&line_item[quantity]=2&line_item[vendor_id]=21
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
ETag: W/&quot;fba81192510ccdccfe663bb762b01efe&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: b1b5d85e-701d-45bf-8485-98a53117269c
X-Runtime: 0.151417
Vary: Origin
Content-Length: 2344
200 OK
```


```json
{
  "id": 3,
  "number": "M405103074",
  "item_total": "39.98",
  "total": "39.98",
  "ship_total": "0.0",
  "state": "cart",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2019-10-01T14:49:37.469-04:00",
  "updated_at": "2019-10-01T14:49:37.518-04:00",
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
  "token": "T22MntCFQrv76pr7umKSAQ",
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
      "id": 4,
      "quantity": 2,
      "price": "19.99",
      "variant_id": 12,
      "vendor_id": 21,
      "single_display_amount": "$19.99",
      "display_amount": "$39.98",
      "total": "39.98",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 12,
        "name": "Product #6 - 9588",
        "sku": "SKU-11",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-6-9588",
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
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #21",
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
Authorizat IO N: Bearer 72dd804b6c5d8d48fd768940f88a925b62af19afcb56c736
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
ETag: W/&quot;05a47cea47bffadf8949de0cef498ff3&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: e3afc3ff-bcf3-4518-9c66-e417c362fdb8
X-Runtime: 0.037046
Vary: Origin
Content-Length: 310
200 OK
```


```json
{
  "orders": [
    {
      "number": "M315019752",
      "completed_at": "2019-10-01T14:49:36.922-04:00",
      "total": "120.0",
      "state": "Complete",
      "shipment_state": "shipped",
      "shipments": [
        {
          "number": "H51081844217",
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
GET /api/orders/M949966802
Accept: application/json
Authorizat IO N: Bearer fed1ccc50f38d7d643a6a34759679ef97ddefb2c446c4125
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
ETag: W/&quot;6ebeba5cf5e9c5b3fa62f12da41dd0f4&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: d5fa674b-1b86-4481-8e1b-0e2de7e15a1a
X-Runtime: 0.246164
Vary: Origin
Content-Length: 9436
200 OK
```


```json
{
  "id": 4,
  "number": "M949966802",
  "item_total": "20.0",
  "total": "120.0",
  "ship_total": "100.0",
  "state": "complete",
  "adjustment_total": "0.0",
  "user_id": 13,
  "created_at": "2019-10-01T14:49:38.141-04:00",
  "updated_at": "2019-10-01T14:49:38.561-04:00",
  "completed_at": "2019-10-01T14:49:38.265-04:00",
  "payment_total": "120.0",
  "shipment_state": "shipped",
  "payment_state": "paid",
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
  "token": "MDmp3BbYA-_Ir-1ct-st7w",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 6,
      "name": "Credit Card",
      "partial_name": "gateway",
      "method_type": "gateway"
    },
    {
      "id": 7,
      "name": "Credit Card",
      "partial_name": "gateway",
      "method_type": "gateway"
    }
  ],
  "bill_address": {
    "id": 7,
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
    "id": 8,
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
      "variant_id": 14,
      "vendor_id": 29,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 14,
        "name": "Product #7 - 1216",
        "sku": "SKU-13",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-7-1216",
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
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #29",
      "country_iso": "US",
      "adjustments": [
        {
          "id": 8,
          "source_type": "Spree::TaxRate",
          "source_id": 1,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 5,
          "amount": "2.0",
          "label": "VAT 5%",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-10-01T14:49:38.519-04:00",
          "updated_at": "2019-10-01T14:49:38.543-04:00",
          "display_amount": "$2.00"
        },
        {
          "id": 2,
          "source_type": "Spree::PromotionAction",
          "source_id": 1,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 5,
          "amount": "5.0",
          "label": "foo",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-10-01T14:49:38.382-04:00",
          "updated_at": "2019-10-01T14:49:38.382-04:00",
          "display_amount": "$5.00"
        },
        {
          "id": 1,
          "source_type": "Spree::PromotionAction",
          "source_id": 1,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 5,
          "amount": "5.0",
          "label": "foo",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-10-01T14:49:38.371-04:00",
          "updated_at": "2019-10-01T14:49:38.371-04:00",
          "display_amount": "$5.00"
        }
      ]
    },
    {
      "id": 6,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 16,
      "vendor_id": 29,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 16,
        "name": "Product #8 - 4049",
        "sku": "SKU-15",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-8-4049",
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
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #29",
      "country_iso": "US",
      "adjustments": [
        {
          "id": 9,
          "source_type": "Spree::TaxRate",
          "source_id": 2,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 6,
          "amount": "1.5",
          "label": "VAT 5%",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-10-01T14:49:38.558-04:00",
          "updated_at": "2019-10-01T14:49:38.572-04:00",
          "display_amount": "$1.50"
        },
        {
          "id": 3,
          "source_type": "Spree::PromotionAction",
          "source_id": 1,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 6,
          "amount": "5.0",
          "label": "bar",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-10-01T14:49:38.397-04:00",
          "updated_at": "2019-10-01T14:49:38.397-04:00",
          "display_amount": "$5.00"
        }
      ]
    }
  ],
  "payments": [
    {
      "id": 2,
      "source_type": "Spree::CreditCard",
      "source_id": 2,
      "amount": "120.0",
      "display_amount": "$120.00",
      "payment_method_id": 6,
      "state": "completed",
      "avs_response": null,
      "created_at": "2019-10-01T14:49:38.278-04:00",
      "updated_at": "2019-10-01T14:49:38.278-04:00",
      "payment_method": {
        "id": 6,
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
  "shipments": [
    {
      "id": 3,
      "tracking": "U10000",
      "tracking_url": null,
      "number": "H75558130643",
      "cost": "100.0",
      "shipped_at": "2019-10-01T14:49:38.313-04:00",
      "state": "shipped",
      "order_id": "M949966802",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 3,
          "name": "UPS Ground",
          "admin_name": null,
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 3,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 3,
        "name": "UPS Ground",
        "admin_name": null,
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
              "id": 5,
              "name": "ShippingCategory #5"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 14,
          "quantity": 1,
          "states": {
            "shipped": 1
          }
        },
        {
          "variant_id": 16,
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
          "adjustable_id": 3,
          "amount": "-10.0",
          "label": "Shipping",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-10-01T14:49:38.442-04:00",
          "updated_at": "2019-10-01T14:49:38.442-04:00",
          "display_amount": "-$10.00"
        },
        {
          "id": 4,
          "source_type": "Spree::PromotionAction",
          "source_id": 1,
          "adjustable_type": "Spree::Shipment",
          "adjustable_id": 3,
          "amount": "-9.99",
          "label": "Shipping",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-10-01T14:49:38.417-04:00",
          "updated_at": "2019-10-01T14:49:38.417-04:00",
          "display_amount": "-$9.99"
        }
      ],
      "stock_location_address": "NY Warehouse, Washington, AL",
      "country_iso": "US",
      "international_shipping": false,
      "delivery_estimation": "Oct 03"
    }
  ],
  "adjustments": [
    {
      "id": 6,
      "source_type": "Spree::Promotion",
      "source_id": 1,
      "adjustable_type": "Spree::Order",
      "adjustable_id": 4,
      "amount": "20.0",
      "label": "adj1",
      "promotion_code_id": null,
      "finalized": false,
      "eligible": true,
      "created_at": "2019-10-01T14:49:38.456-04:00",
      "updated_at": "2019-10-01T14:49:38.456-04:00",
      "display_amount": "$20.00"
    },
    {
      "id": 7,
      "source_type": "Spree::Promotion",
      "source_id": 1,
      "adjustable_type": "Spree::Order",
      "adjustable_id": 4,
      "amount": "30.0",
      "label": "adj2",
      "promotion_code_id": null,
      "finalized": false,
      "eligible": true,
      "created_at": "2019-10-01T14:49:38.462-04:00",
      "updated_at": "2019-10-01T14:49:38.462-04:00",
      "display_amount": "$30.00"
    }
  ],
  "permissions": {
    "can_update": false
  },
  "credit_cards": [
    {
      "id": 2,
      "month": "12",
      "year": "2020",
      "cc_type": null,
      "last_digits": "1111",
      "name": "Spree Commerce",
      "address": {
        "id": 7,
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
GET /api/orders/M556010887
Accept: application/json
Authorizat IO N: f80e565afebb3eab5bf9770457f8fed54eb54ab4cb224a5e
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
X-Request-Id: a6e0e166-05ea-418e-9918-ecd6199f6b7a
X-Runtime: 0.015508
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
Content-Type: text/html
Cache-Control: no-cache
X-Request-Id: a931f197-5a1e-4388-b2f1-786ac699bf8e
X-Runtime: 0.178729
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
user[email]=email3%40example.com&user[password]=secret
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
Authorization: Bearer 5caa2eb7c4d8273ef90b934a89336d72541e8eb39b6c67f1
ETag: W/&quot;339f47d1577509cfb725187eb8587725&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 3fa734a8-5cbe-4649-88f3-9dae34af23eb
X-Runtime: 0.059039
Vary: Origin
Content-Length: 559
200 OK
```


```json
{
  "id": 3,
  "email": "email3@example.com",
  "persistence_token": null,
  "perishable_token": null,
  "last_request_at": null,
  "login": "email3@example.com",
  "ship_address_id": null,
  "bill_address_id": null,
  "created_at": "2019-10-01T14:49:33.266-04:00",
  "updated_at": "2019-10-01T14:49:33.268-04:00",
  "spree_api_key": "5caa2eb7c4d8273ef90b934a89336d72541e8eb39b6c67f1",
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
X-Request-Id: 57a8a7d9-158f-4d6e-913a-69c066e14c4b
X-Runtime: 0.003370
Vary: Origin
204 No Content
```




# Product Management

get products by taxon

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
Date: Tue, 01 Oct 2019 18:49:46 GMT
Surrogate-Control: max-age=900
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;7c536b6b69028042d09dbabfcc116423&quot;
X-Request-Id: 77385030-999a-412e-ae21-423f5be39fc7
X-Runtime: 0.049442
Vary: Origin
Content-Length: 916
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
      "id": 32,
      "name": "Product #32 - 9835",
      "description": "As seen on TV!",
      "available_on": "2018-10-01T14:49:45.988-04:00",
      "slug": "product-32-9835",
      "meta_description": null,
      "meta_keywords": null,
      "taxon_ids": [

      ],
      "total_on_hand": 0,
      "meta_title": null,
      "display_price": "$19.99",
      "trends": [

      ],
      "breadcrumb_taxons": [

      ],
      "brand": null,
      "brand_slug": null,
      "brand_description": null,
      "has_variants": false,
      "master": {
        "id": 58,
        "name": "Product #32 - 9835",
        "sku": "SKU-58",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-32-9835",
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
GET /api/products/product-31-1113
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
Date: Tue, 01 Oct 2019 18:49:45 GMT
Surrogate-Control: max-age=900
Surrogate-Key: product_id=1
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;c1af74cdf82ea6fc8be55c3b45884f49&quot;
X-Request-Id: db229a55-f1ad-4293-afda-e1f195053e8c
X-Runtime: 0.079853
Vary: Origin
Content-Length: 1524
200 OK
```


```json
{
  "id": 31,
  "name": "Product #31 - 1113",
  "description": "As seen on TV!",
  "available_on": "2018-10-01T14:49:45.784-04:00",
  "slug": "product-31-1113",
  "meta_description": null,
  "meta_keywords": null,
  "taxon_ids": [
    12
  ],
  "total_on_hand": 0,
  "meta_title": null,
  "display_price": "$19.99",
  "trends": [

  ],
  "breadcrumb_taxons": [
    {
      "id": 10,
      "name": "Clothing",
      "taxonomy_id": 5,
      "created_at": "2019-10-01T14:49:45.702-04:00",
      "url": "/category/clothing",
      "position": 1
    },
    {
      "id": 11,
      "name": "Girl",
      "taxonomy_id": 5,
      "created_at": "2019-10-01T14:49:45.738-04:00",
      "url": "/category/clothing/girl",
      "position": 2
    },
    {
      "id": 12,
      "name": "Dresses",
      "taxonomy_id": 5,
      "created_at": "2019-10-01T14:49:45.760-04:00",
      "url": "/category/clothing/girl/dresses",
      "position": 3
    }
  ],
  "brand": null,
  "brand_slug": null,
  "brand_description": null,
  "has_variants": false,
  "master": {
    "id": 57,
    "name": "Product #31 - 1113",
    "sku": "SKU-57",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": true,
    "slug": "product-31-1113",
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
        "name": "Dresses",
        "pretty_name": "Category -> Clothing -> Girl -> Dresses",
        "permalink": "category/clothing/girl/dresses",
        "parent_id": 11,
        "taxonomy_id": 5,
        "url_override": null,
        "description": "Dresses",
        "icon": "/assets/default_taxon.png"
      }
    }
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
X-Request-Id: bfe07933-dc19-418c-b57d-8f3e2d381598
X-Runtime: 0.015877
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
GET /api/taxons/products?id=4
Host: example.org
Cookie: 
```

`GET /api/taxons/products`

#### Parameters


```json
id: 4
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
ETag: W/&quot;7d0ed1f338e0e5a71a8ae121e196a6d4&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 8f16cb2d-632b-4968-840a-950f86c5ace3
X-Runtime: 0.071783
Vary: Origin
Content-Length: 1175
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
      "id": 28,
      "name": "Product #28 - 5194",
      "description": "As seen on TV!",
      "available_on": "2018-10-01T14:49:45.184-04:00",
      "slug": "product-28-5194",
      "meta_description": null,
      "meta_keywords": null,
      "taxon_ids": [
        4
      ],
      "total_on_hand": 0,
      "meta_title": null,
      "display_price": "$19.99",
      "trends": [

      ],
      "breadcrumb_taxons": [

      ],
      "brand": null,
      "brand_slug": null,
      "brand_description": null,
      "has_variants": false,
      "master": {
        "id": 54,
        "name": "Product #28 - 5194",
        "sku": "SKU-54",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-28-5194",
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
            "name": "Ruby on Rails - 1",
            "pretty_name": "Ruby on Rails - 1",
            "permalink": "ruby-on-rails-1",
            "parent_id": null,
            "taxonomy_id": 2,
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



## returns associated products


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
ETag: W/&quot;6f537176ded1c29982eeda72e375a756&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: b21f0513-4d8d-4fef-99fd-53d109205105
X-Runtime: 0.053069
Vary: Origin
Content-Length: 1175
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
      "id": 30,
      "name": "Product #30 - 3180",
      "description": "As seen on TV!",
      "available_on": "2018-10-01T14:49:45.528-04:00",
      "slug": "product-30-3180",
      "meta_description": null,
      "meta_keywords": null,
      "taxon_ids": [
        8
      ],
      "total_on_hand": 0,
      "meta_title": null,
      "display_price": "$19.99",
      "trends": [

      ],
      "breadcrumb_taxons": [

      ],
      "brand": null,
      "brand_slug": null,
      "brand_description": null,
      "has_variants": false,
      "master": {
        "id": 56,
        "name": "Product #30 - 3180",
        "sku": "SKU-56",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-30-3180",
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
            "name": "Ruby on Rails - 2",
            "pretty_name": "Ruby on Rails - 2",
            "permalink": "ruby-on-rails-2",
            "parent_id": null,
            "taxonomy_id": 4,
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



# Return Authorizations

Get a single user return authorziation

## Can get another user&#39;s return authorization


### Request

#### Endpoint

```plaintext
GET /api/returns/RA541255674
Authorizat IO N: Bearer e3d967d04ade093c08cc5a2b747b0c58de82b716b2dc58c9
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
ETag: W/&quot;65b408399e2fbc6a9a447ba56cbc3043&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: c138efa7-9ebc-4770-a910-a5e92a740eda
X-Runtime: 0.041438
Vary: Origin
Content-Length: 2781
200 OK
```


```json
{
  "id": 3,
  "number": "RA541255674",
  "state": "authorized",
  "order_id": 13,
  "memo": "Items were broken",
  "created_at": "2019-10-01T14:49:47.640-04:00",
  "updated_at": "2019-10-01T14:49:47.640-04:00",
  "reason": {
    "id": 5,
    "name": "Defect #5",
    "active": true,
    "mutable": true,
    "created_at": "2019-10-01T14:49:47.636-04:00",
    "updated_at": "2019-10-01T14:49:47.636-04:00",
    "mirakl_code": null
  },
  "order": {
    "id": 13,
    "number": "M661153027",
    "item_total": "10.0",
    "total": "110.0",
    "state": "complete",
    "adjustment_total": "0.0",
    "user_id": 42,
    "completed_at": "2019-10-01T14:49:47.527-04:00",
    "bill_address_id": 27,
    "ship_address_id": 28,
    "payment_total": "110.0",
    "shipment_state": "shipped",
    "payment_state": "paid",
    "email": "email41@example.com",
    "special_instructions": null,
    "created_at": "2019-10-01T14:49:47.428-04:00",
    "updated_at": "2019-10-01T14:49:47.596-04:00",
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
    "guest_token": "wF64pnwxEhKYZg7kXg-cIA",
    "canceled_at": null,
    "canceler_id": null,
    "store_id": 13,
    "approver_name": null,
    "frontend_viewable": true
  },
  "ship_address": {
    "id": 28,
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
  },
  "bill_address": {
    "id": 27,
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
  },
  "return_items": [
    {
      "name": "Product #35 - 2218",
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
        "id": 16,
        "name": "Credit Card"
      },
      "source": {
        "id": 6,
        "month": "12",
        "year": "2020",
        "cc_type": null,
        "last_digits": "1111",
        "name": "Spree Commerce",
        "gateway_customer_profile_id": "BGS-341211",
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
Authorizat IO N: Bearer b7b382a2339e5e746d8708817adc22f25f034e5aedb7e9d0
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
ETag: W/&quot;9e5e42b0fe6a6307e5c0a9089bd7c115&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 548935ff-6181-4411-9c68-624d4283c3fb
X-Runtime: 0.010640
Vary: Origin
Content-Length: 169
200 OK
```


```json
{
  "return_authorizations": [
    {
      "number": "RA034415438",
      "created_at": "2019-10-01T14:49:48.210-04:00",
      "return_amount": "10.0",
      "order_number": "M598507505",
      "state": "authorized"
    }
  ]
}
```



## returns a 200


### Request

#### Endpoint

```plaintext
GET /api/returns/RA286460055
Authorizat IO N: Bearer 3679efda82f653cca7b1faf68d19583b9b0d77630cfe10ba
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
ETag: W/&quot;989319465554aa7d89de72f00144d7cf&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 1bbeb59a-6137-4b3f-b321-622185bcbe21
X-Runtime: 0.062734
Vary: Origin
Content-Length: 2704
200 OK
```


```json
{
  "id": 1,
  "number": "RA286460055",
  "state": "authorized",
  "order_id": 11,
  "memo": "Items were broken",
  "created_at": "2019-10-01T14:49:46.543-04:00",
  "updated_at": "2019-10-01T14:49:46.543-04:00",
  "reason": {
    "id": 1,
    "name": "Defect #1",
    "active": true,
    "mutable": true,
    "created_at": "2019-10-01T14:49:46.532-04:00",
    "updated_at": "2019-10-01T14:49:46.532-04:00",
    "mirakl_code": null
  },
  "order": {
    "id": 11,
    "number": "M005021921",
    "item_total": "10.0",
    "total": "110.0",
    "state": "complete",
    "adjustment_total": "0.0",
    "user_id": 39,
    "completed_at": "2019-10-01T14:49:46.426-04:00",
    "bill_address_id": 23,
    "ship_address_id": 24,
    "payment_total": "110.0",
    "shipment_state": "shipped",
    "payment_state": "paid",
    "email": "email38@example.com",
    "special_instructions": null,
    "created_at": "2019-10-01T14:49:46.335-04:00",
    "updated_at": "2019-10-01T14:49:46.481-04:00",
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
    "guest_token": "xoOhUYWj2x0BPraPYiuP-w",
    "canceled_at": null,
    "canceler_id": null,
    "store_id": 11,
    "approver_name": null,
    "frontend_viewable": true
  },
  "ship_address": {
    "id": 24,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "A Different Road",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10022",
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
  "bill_address": {
    "id": 23,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "PO Box 1337",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10021",
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
  "return_items": [
    {
      "name": "Product #33 - 1230",
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
        "id": 12,
        "name": "Credit Card"
      },
      "source": {
        "id": 4,
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
GET /api/returns/RA235713151
Authorizat IO N: Bearer 91919be2e8f039ed30dd826f968aef307bb3eb43579ee3df
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
X-Request-Id: 5592797a-8faa-489b-a1bd-a6d1ff8e9cfe
X-Runtime: 0.007712
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
Authorizat IO N: Bearer a6dc5a757b024b6da023e344fe448f510eb6aea24d68b24a
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
ETag: W/&quot;26c5269ea7bb907d6cdef542b11dfd81&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 4136de1b-acfe-4741-8412-d9c7c0492660
X-Runtime: 0.054784
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
      "created_at": "2019-10-01T14:49:35.156-04:00"
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
Authorizat IO N: Bearer cf66d0d60006f5fa7dce149ab9df5759c1e6a3c32645f6c6
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/subscribers`

#### Parameters


```json
subscriber[email]=isobel_nikolaus%40stark.co.uk&subscriber[user_id]=45&subscriber[first_name]=Gennie&subscriber[last_name]=Murphy&subscriber[status]=subscribed
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
ETag: W/&quot;46e1247e85a1891dbb27cc51ad1f5488&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: df405ede-8b7e-4b1b-826c-55143f4995bf
X-Runtime: 0.033429
Vary: Origin
Content-Length: 181
201 Created
```


```json
{
  "id": 3,
  "user_id": 45,
  "email": "isobel_nikolaus@stark.co.uk",
  "first_name": "Gennie",
  "last_name": "Murphy",
  "source": "",
  "status": "subscribed",
  "created_at": "2019-10-01T14:49:48.282-04:00"
}
```



## Delete a subscriber


### Request

#### Endpoint

```plaintext
DELETE /api/subscribers/9
Accept: application/json
Authorizat IO N: Bearer 09785e80f65ecfd6a0cd38faf417a5ed31907a37e493915e
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
X-Request-Id: f9ea85aa-904c-4538-a3e2-57aa8ee17602
X-Runtime: 0.007197
Vary: Origin
204 No Content
```




## Get a single subscriber by id


### Request

#### Endpoint

```plaintext
GET /api/subscribers/4
Accept: application/json
Authorizat IO N: Bearer dc94a381db05c8be59b2e8ead4266edd4a90a294fe9247b1
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
ETag: W/&quot;75ebe517f6004e3ffc7f0f42abd6dea9&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 50f5c11c-0764-4113-8d39-85301ea7b6d0
X-Runtime: 0.008915
Vary: Origin
Content-Length: 180
200 OK
```


```json
{
  "id": 4,
  "user_id": 46,
  "email": "colette.johnson@kunde.com",
  "first_name": "Rhiannon",
  "last_name": "Walsh",
  "source": "",
  "status": "subscribed",
  "created_at": "2019-10-01T14:49:48.300-04:00"
}
```



## Get all subscribers


### Request

#### Endpoint

```plaintext
GET /api/subscribers
Accept: application/json
Authorizat IO N: Bearer 6d7a98d6a7fab484f99a47595ece857ec885215d9ef0d891
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
ETag: W/&quot;17145f9d88a8461d3cecc4f75c410dcb&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 67340ada-6f2b-4587-ad43-566ce48fae88
X-Runtime: 0.011143
Vary: Origin
Content-Length: 639
200 OK
```


```json
{
  "subscribers": [
    {
      "id": 5,
      "user_id": null,
      "email": "dayna_beahan@gulgowski.com",
      "first_name": "Noe",
      "last_name": "Kuphal",
      "source": "",
      "status": "subscribed",
      "created_at": "2019-10-01T14:49:48.314-04:00"
    },
    {
      "id": 6,
      "user_id": null,
      "email": "lindsey_johnson@kutchblanda.ca",
      "first_name": "Suk",
      "last_name": "Medhurst",
      "source": "",
      "status": "subscribed",
      "created_at": "2019-10-01T14:49:48.316-04:00"
    },
    {
      "id": 7,
      "user_id": null,
      "email": "bernardo.fisher@feilnitzsche.info",
      "first_name": "Lexie",
      "last_name": "Graham",
      "source": "",
      "status": "subscribed",
      "created_at": "2019-10-01T14:49:48.318-04:00"
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
PATCH /api/subscribers/8
Accept: application/json
Authorizat IO N: Bearer e75f7c1f63225f81508db9e4b74a5fed02d5d1f7a6268583
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
ETag: W/&quot;d44d9b8db9953752efbf94646f68e44c&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: e89e86e9-b8ac-4b5b-b9e9-9cc606244e9a
X-Runtime: 0.008852
Vary: Origin
Content-Length: 174
200 OK
```


```json
{
  "id": 8,
  "user_id": 48,
  "email": "deangelo_smith@dooley.us",
  "first_name": "Dee",
  "last_name": "Oga",
  "source": "",
  "status": "unsubscribed",
  "created_at": "2019-10-01T14:49:48.356-04:00"
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



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
ETag: W/&quot;5d265016f1f1bca131e40e335b9a3917&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 6cc6e7d4-6eaa-4090-be27-a0ade7cb1e52
X-Runtime: 0.066886
Vary: Origin
Content-Length: 8452
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
      "id": 15,
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
          "id": 16,
          "name": "Kids",
          "pretty_name": "Category -> Kids",
          "permalink": "category/kids",
          "parent_id": 15,
          "taxonomy_id": 7,
          "url_override": null,
          "description": "Kids",
          "icon": "/assets/default_taxon.png",
          "taxons": [
            {
              "id": 17,
              "name": "Boys",
              "pretty_name": "Category -> Kids -> Boys",
              "permalink": "category/kids/boys",
              "parent_id": 16,
              "taxonomy_id": 7,
              "url_override": null,
              "description": "Boys",
              "icon": "/assets/default_taxon.png",
              "taxons": [
                {
                  "id": 18,
                  "name": "Boys Tops",
                  "pretty_name": "Category -> Kids -> Boys -> Boys Tops",
                  "permalink": "category/kids/boys/boys-tops",
                  "parent_id": 17,
                  "taxonomy_id": 7,
                  "url_override": null,
                  "description": "Boys Tops",
                  "icon": "/assets/default_taxon.png",
                  "taxons": [
                    {
                      "id": 19,
                      "name": "Boys Shirts",
                      "pretty_name": "Category -> Kids -> Boys -> Boys Tops -> Boys Shirts",
                      "permalink": "category/kids/boys/boys-tops/boys-shirts",
                      "parent_id": 18,
                      "taxonomy_id": 7,
                      "url_override": null,
                      "description": "Boys Shirts",
                      "icon": "/assets/default_taxon.png",
                      "taxons": [

                      ]
                    }
                  ]
                }
              ]
            },
            {
              "id": 20,
              "name": "Girls",
              "pretty_name": "Category -> Kids -> Girls",
              "permalink": "category/kids/girls",
              "parent_id": 16,
              "taxonomy_id": 7,
              "url_override": null,
              "description": "Girls",
              "icon": "/assets/default_taxon.png",
              "taxons": [
                {
                  "id": 21,
                  "name": "Girls Tops",
                  "pretty_name": "Category -> Kids -> Girls -> Girls Tops",
                  "permalink": "category/kids/girls/girls-tops",
                  "parent_id": 20,
                  "taxonomy_id": 7,
                  "url_override": null,
                  "description": "Girls Tops",
                  "icon": "/assets/default_taxon.png",
                  "taxons": [
                    {
                      "id": 22,
                      "name": "Girls Shirts",
                      "pretty_name": "Category -> Kids -> Girls -> Girls Tops -> Girls Shirts",
                      "permalink": "category/kids/girls/girls-tops/girls-shirts",
                      "parent_id": 21,
                      "taxonomy_id": 7,
                      "url_override": null,
                      "description": "Girls Shirts",
                      "icon": "/assets/default_taxon.png",
                      "taxons": [

                      ]
                    }
                  ]
                }
              ]
            }
          ]
        }
      ]
    },
    {
      "id": 16,
      "name": "Kids",
      "pretty_name": "Category -> Kids",
      "permalink": "category/kids",
      "parent_id": 15,
      "taxonomy_id": 7,
      "url_override": null,
      "description": "Kids",
      "icon": "/assets/default_taxon.png",
      "taxons": [
        {
          "id": 17,
          "name": "Boys",
          "pretty_name": "Category -> Kids -> Boys",
          "permalink": "category/kids/boys",
          "parent_id": 16,
          "taxonomy_id": 7,
          "url_override": null,
          "description": "Boys",
          "icon": "/assets/default_taxon.png",
          "taxons": [
            {
              "id": 18,
              "name": "Boys Tops",
              "pretty_name": "Category -> Kids -> Boys -> Boys Tops",
              "permalink": "category/kids/boys/boys-tops",
              "parent_id": 17,
              "taxonomy_id": 7,
              "url_override": null,
              "description": "Boys Tops",
              "icon": "/assets/default_taxon.png",
              "taxons": [
                {
                  "id": 19,
                  "name": "Boys Shirts",
                  "pretty_name": "Category -> Kids -> Boys -> Boys Tops -> Boys Shirts",
                  "permalink": "category/kids/boys/boys-tops/boys-shirts",
                  "parent_id": 18,
                  "taxonomy_id": 7,
                  "url_override": null,
                  "description": "Boys Shirts",
                  "icon": "/assets/default_taxon.png",
                  "taxons": [

                  ]
                }
              ]
            }
          ]
        },
        {
          "id": 20,
          "name": "Girls",
          "pretty_name": "Category -> Kids -> Girls",
          "permalink": "category/kids/girls",
          "parent_id": 16,
          "taxonomy_id": 7,
          "url_override": null,
          "description": "Girls",
          "icon": "/assets/default_taxon.png",
          "taxons": [
            {
              "id": 21,
              "name": "Girls Tops",
              "pretty_name": "Category -> Kids -> Girls -> Girls Tops",
              "permalink": "category/kids/girls/girls-tops",
              "parent_id": 20,
              "taxonomy_id": 7,
              "url_override": null,
              "description": "Girls Tops",
              "icon": "/assets/default_taxon.png",
              "taxons": [
                {
                  "id": 22,
                  "name": "Girls Shirts",
                  "pretty_name": "Category -> Kids -> Girls -> Girls Tops -> Girls Shirts",
                  "permalink": "category/kids/girls/girls-tops/girls-shirts",
                  "parent_id": 21,
                  "taxonomy_id": 7,
                  "url_override": null,
                  "description": "Girls Shirts",
                  "icon": "/assets/default_taxon.png",
                  "taxons": [

                  ]
                }
              ]
            }
          ]
        }
      ]
    },
    {
      "id": 17,
      "name": "Boys",
      "pretty_name": "Category -> Kids -> Boys",
      "permalink": "category/kids/boys",
      "parent_id": 16,
      "taxonomy_id": 7,
      "url_override": null,
      "description": "Boys",
      "icon": "/assets/default_taxon.png",
      "taxons": [
        {
          "id": 18,
          "name": "Boys Tops",
          "pretty_name": "Category -> Kids -> Boys -> Boys Tops",
          "permalink": "category/kids/boys/boys-tops",
          "parent_id": 17,
          "taxonomy_id": 7,
          "url_override": null,
          "description": "Boys Tops",
          "icon": "/assets/default_taxon.png",
          "taxons": [
            {
              "id": 19,
              "name": "Boys Shirts",
              "pretty_name": "Category -> Kids -> Boys -> Boys Tops -> Boys Shirts",
              "permalink": "category/kids/boys/boys-tops/boys-shirts",
              "parent_id": 18,
              "taxonomy_id": 7,
              "url_override": null,
              "description": "Boys Shirts",
              "icon": "/assets/default_taxon.png",
              "taxons": [

              ]
            }
          ]
        }
      ]
    },
    {
      "id": 18,
      "name": "Boys Tops",
      "pretty_name": "Category -> Kids -> Boys -> Boys Tops",
      "permalink": "category/kids/boys/boys-tops",
      "parent_id": 17,
      "taxonomy_id": 7,
      "url_override": null,
      "description": "Boys Tops",
      "icon": "/assets/default_taxon.png",
      "taxons": [
        {
          "id": 19,
          "name": "Boys Shirts",
          "pretty_name": "Category -> Kids -> Boys -> Boys Tops -> Boys Shirts",
          "permalink": "category/kids/boys/boys-tops/boys-shirts",
          "parent_id": 18,
          "taxonomy_id": 7,
          "url_override": null,
          "description": "Boys Shirts",
          "icon": "/assets/default_taxon.png",
          "taxons": [

          ]
        }
      ]
    },
    {
      "id": 19,
      "name": "Boys Shirts",
      "pretty_name": "Category -> Kids -> Boys -> Boys Tops -> Boys Shirts",
      "permalink": "category/kids/boys/boys-tops/boys-shirts",
      "parent_id": 18,
      "taxonomy_id": 7,
      "url_override": null,
      "description": "Boys Shirts",
      "icon": "/assets/default_taxon.png",
      "taxons": [

      ]
    },
    {
      "id": 20,
      "name": "Girls",
      "pretty_name": "Category -> Kids -> Girls",
      "permalink": "category/kids/girls",
      "parent_id": 16,
      "taxonomy_id": 7,
      "url_override": null,
      "description": "Girls",
      "icon": "/assets/default_taxon.png",
      "taxons": [
        {
          "id": 21,
          "name": "Girls Tops",
          "pretty_name": "Category -> Kids -> Girls -> Girls Tops",
          "permalink": "category/kids/girls/girls-tops",
          "parent_id": 20,
          "taxonomy_id": 7,
          "url_override": null,
          "description": "Girls Tops",
          "icon": "/assets/default_taxon.png",
          "taxons": [
            {
              "id": 22,
              "name": "Girls Shirts",
              "pretty_name": "Category -> Kids -> Girls -> Girls Tops -> Girls Shirts",
              "permalink": "category/kids/girls/girls-tops/girls-shirts",
              "parent_id": 21,
              "taxonomy_id": 7,
              "url_override": null,
              "description": "Girls Shirts",
              "icon": "/assets/default_taxon.png",
              "taxons": [

              ]
            }
          ]
        }
      ]
    },
    {
      "id": 21,
      "name": "Girls Tops",
      "pretty_name": "Category -> Kids -> Girls -> Girls Tops",
      "permalink": "category/kids/girls/girls-tops",
      "parent_id": 20,
      "taxonomy_id": 7,
      "url_override": null,
      "description": "Girls Tops",
      "icon": "/assets/default_taxon.png",
      "taxons": [
        {
          "id": 22,
          "name": "Girls Shirts",
          "pretty_name": "Category -> Kids -> Girls -> Girls Tops -> Girls Shirts",
          "permalink": "category/kids/girls/girls-tops/girls-shirts",
          "parent_id": 21,
          "taxonomy_id": 7,
          "url_override": null,
          "description": "Girls Shirts",
          "icon": "/assets/default_taxon.png",
          "taxons": [

          ]
        }
      ]
    },
    {
      "id": 22,
      "name": "Girls Shirts",
      "pretty_name": "Category -> Kids -> Girls -> Girls Tops -> Girls Shirts",
      "permalink": "category/kids/girls/girls-tops/girls-shirts",
      "parent_id": 21,
      "taxonomy_id": 7,
      "url_override": null,
      "description": "Girls Shirts",
      "icon": "/assets/default_taxon.png",
      "taxons": [

      ]
    },
    {
      "id": 23,
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
          "id": 24,
          "name": "Ruby on Rails - 3",
          "pretty_name": "Brand -> Ruby on Rails - 3",
          "permalink": "brand/ruby-on-rails-3",
          "parent_id": 23,
          "taxonomy_id": 8,
          "url_override": null,
          "description": "Ruby on Rails - 3",
          "icon": "/assets/default_taxon.png",
          "taxons": [

          ]
        },
        {
          "id": 25,
          "name": "Ruby on Rails - 4",
          "pretty_name": "Brand -> Ruby on Rails - 4",
          "permalink": "brand/ruby-on-rails-4",
          "parent_id": 23,
          "taxonomy_id": 8,
          "url_override": null,
          "description": "Ruby on Rails - 4",
          "icon": "/assets/default_taxon.png",
          "taxons": [

          ]
        }
      ]
    },
    {
      "id": 24,
      "name": "Ruby on Rails - 3",
      "pretty_name": "Brand -> Ruby on Rails - 3",
      "permalink": "brand/ruby-on-rails-3",
      "parent_id": 23,
      "taxonomy_id": 8,
      "url_override": null,
      "description": "Ruby on Rails - 3",
      "icon": "/assets/default_taxon.png",
      "taxons": [

      ]
    },
    {
      "id": 25,
      "name": "Ruby on Rails - 4",
      "pretty_name": "Brand -> Ruby on Rails - 4",
      "permalink": "brand/ruby-on-rails-4",
      "parent_id": 23,
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



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
ETag: W/&quot;ef30f75c0109a862d334036d7349ff69&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: e87de420-84ae-4795-838e-bba4e1951ce1
X-Runtime: 0.013916
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
      "id": 34,
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
      "id": 35,
      "name": "Ruby on Rails - 5",
      "pretty_name": "Brand -> Ruby on Rails - 5",
      "permalink": "brand/ruby-on-rails-5",
      "parent_id": 34,
      "taxonomy_id": 10,
      "url_override": null,
      "description": "Ruby on Rails - 5",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 36,
      "name": "Ruby on Rails - 6",
      "pretty_name": "Brand -> Ruby on Rails - 6",
      "permalink": "brand/ruby-on-rails-6",
      "parent_id": 34,
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



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
ETag: W/&quot;07598b0a287a2e0488de131c15ca990d&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 25b9bb1d-3d8a-4a4f-9240-3c5d177ef5d0
X-Runtime: 0.019640
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
      "id": 37,
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
      "id": 38,
      "name": "Kids",
      "pretty_name": "Category -> Kids",
      "permalink": "category/kids",
      "parent_id": 37,
      "taxonomy_id": 11,
      "url_override": null,
      "description": "Kids",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 39,
      "name": "Boys",
      "pretty_name": "Category -> Kids -> Boys",
      "permalink": "category/kids/boys",
      "parent_id": 38,
      "taxonomy_id": 11,
      "url_override": null,
      "description": "Boys",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 40,
      "name": "Boys Tops",
      "pretty_name": "Category -> Kids -> Boys -> Boys Tops",
      "permalink": "category/kids/boys/boys-tops",
      "parent_id": 39,
      "taxonomy_id": 11,
      "url_override": null,
      "description": "Boys Tops",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 41,
      "name": "Boys Shirts",
      "pretty_name": "Category -> Kids -> Boys -> Boys Tops -> Boys Shirts",
      "permalink": "category/kids/boys/boys-tops/boys-shirts",
      "parent_id": 40,
      "taxonomy_id": 11,
      "url_override": null,
      "description": "Boys Shirts",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 42,
      "name": "Girls",
      "pretty_name": "Category -> Kids -> Girls",
      "permalink": "category/kids/girls",
      "parent_id": 38,
      "taxonomy_id": 11,
      "url_override": null,
      "description": "Girls",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 43,
      "name": "Girls Tops",
      "pretty_name": "Category -> Kids -> Girls -> Girls Tops",
      "permalink": "category/kids/girls/girls-tops",
      "parent_id": 42,
      "taxonomy_id": 11,
      "url_override": null,
      "description": "Girls Tops",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 44,
      "name": "Girls Shirts",
      "pretty_name": "Category -> Kids -> Girls -> Girls Tops -> Girls Shirts",
      "permalink": "category/kids/girls/girls-tops/girls-shirts",
      "parent_id": 43,
      "taxonomy_id": 11,
      "url_override": null,
      "description": "Girls Shirts",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 45,
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
      "id": 46,
      "name": "Ruby on Rails - 7",
      "pretty_name": "Brand -> Ruby on Rails - 7",
      "permalink": "brand/ruby-on-rails-7",
      "parent_id": 45,
      "taxonomy_id": 12,
      "url_override": null,
      "description": "Ruby on Rails - 7",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 47,
      "name": "Ruby on Rails - 8",
      "pretty_name": "Brand -> Ruby on Rails - 8",
      "permalink": "brand/ruby-on-rails-8",
      "parent_id": 45,
      "taxonomy_id": 12,
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
ETag: W/&quot;d5b1242d91b711f8215aef1fc10397ad&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 149cc99d-e075-445f-84bb-67bda6266131
X-Runtime: 0.007048
Vary: Origin
Content-Length: 150
200 OK
```


```json
[
  {
    "id": 14,
    "name": "Kids",
    "navigation_url": "/navigation/kids",
    "parent_id": 13,
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
user[email]=email6%40example.com&user[password]=secret
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
Authorization: Bearer be7190330ecce9b5dc72a6c6cf2f3ccb4ac0eacec34dbd2d
ETag: W/&quot;5c54a904f4938a44a97c4a693fccb39d&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: d2056b78-b7fb-4459-8ea0-be8a1045b656
X-Runtime: 0.008300
Vary: Origin
Content-Length: 559
200 OK
```


```json
{
  "id": 6,
  "email": "email6@example.com",
  "persistence_token": null,
  "perishable_token": null,
  "last_request_at": null,
  "login": "email6@example.com",
  "ship_address_id": null,
  "bill_address_id": null,
  "created_at": "2019-10-01T14:49:35.259-04:00",
  "updated_at": "2019-10-01T14:49:35.261-04:00",
  "spree_api_key": "be7190330ecce9b5dc72a6c6cf2f3ccb4ac0eacec34dbd2d",
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
X-Spree-Order-Token: -H_7ar4IZPGamuyL6fZQCg
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/users/login`

#### Parameters


```json
user[email]=email7%40example.com&user[password]=secret&order_number=M054624928
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
Authorization: Bearer 7bec343a8ce570b3f39b45a999fe79ab2bc8427428113ffb
ETag: W/&quot;41e7bff43bf68b6b64aff22b430538e2&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 62f37b5b-1b2e-4b86-8208-5f5add91631f
X-Runtime: 0.021192
Vary: Origin
Content-Length: 559
200 OK
```


```json
{
  "id": 7,
  "email": "email7@example.com",
  "persistence_token": null,
  "perishable_token": null,
  "last_request_at": null,
  "login": "email7@example.com",
  "ship_address_id": null,
  "bill_address_id": null,
  "created_at": "2019-10-01T14:49:35.276-04:00",
  "updated_at": "2019-10-01T14:49:35.277-04:00",
  "spree_api_key": "7bec343a8ce570b3f39b45a999fe79ab2bc8427428113ffb",
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
Authorizat IO N: Bearer 5c1e142fd7cde7edc8a7949e32732c2a42eecb9f950aa443
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
Authorization: Bearer 5c1e142fd7cde7edc8a7949e32732c2a42eecb9f950aa443
ETag: W/&quot;b236ef1706a4e8219fd53a5dae8f2629&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 10a51fb2-2469-4222-8ad0-0899e642472c
X-Runtime: 0.034190
Vary: Origin
Content-Length: 1511
200 OK
```


```json
{
  "email": "email8@example.com",
  "first_name": null,
  "last_name": null,
  "id": 8,
  "subscribed": false,
  "addresses": [
    {
      "id": 4,
      "firstname": "John",
      "lastname": null,
      "full_name": "John",
      "address1": "A Different Road",
      "address2": "Northwest",
      "city": "Herndon",
      "zipcode": "10004",
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
      "default": true
    },
    {
      "id": 3,
      "firstname": "John",
      "lastname": null,
      "full_name": "John",
      "address1": "PO Box 1337",
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
        "created_at": "2019-10-01T14:49:36.071-04:00",
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
        "created_at": "2019-10-01T14:49:36.099-04:00",
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
        "created_at": "2019-10-01T14:49:36.128-04:00",
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
Authorization: Bearer 0dcbf500372c84377c694069dc9f4a9c6f5bb684d1f9fabb
ETag: W/&quot;4e21249ebdfa000cc839b2cc09259d46&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: a37db30c-6fcb-40ca-bf47-124bdeab1d75
X-Runtime: 0.011840
Vary: Origin
Content-Length: 185
201 Created
```


```json
{
  "id": 11,
  "email": "test@example.com",
  "created_at": "2019-10-01T14:49:36.268-04:00",
  "updated_at": "2019-10-01T14:49:36.270-04:00",
  "subscribed": false,
  "bill_address": null,
  "ship_address": null
}
```



## Subscribe a user


### Request

#### Endpoint

```plaintext
PUT /api/users/10/subscribe
Authorizat IO N: Bearer 2ae8647eb89886d2b516a3118496c85899bda2c5ba0a5b34
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
Authorization: Bearer 2ae8647eb89886d2b516a3118496c85899bda2c5ba0a5b34
ETag: W/&quot;a43cbb8bd6161ffb5130a7f32a6e5496&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 86fd928a-0060-4c81-bcb6-0fe5ba1d9108
X-Runtime: 0.011966
Vary: Origin
Content-Length: 187
200 OK
```


```json
{
  "id": 10,
  "email": "email10@example.com",
  "created_at": "2019-10-01T14:49:36.241-04:00",
  "updated_at": "2019-10-01T14:49:36.243-04:00",
  "subscribed": true,
  "bill_address": null,
  "ship_address": null
}
```



## Unsubscribe a user


### Request

#### Endpoint

```plaintext
PUT /api/users/9/unsubscribe
Authorizat IO N: Bearer 527020be45b2702dc77a65710d1bc01353b44f90f48c8d20
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
Authorization: Bearer 527020be45b2702dc77a65710d1bc01353b44f90f48c8d20
ETag: W/&quot;4bb7064e7272184a18e6fd685f653705&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: c6104ee4-1df0-4435-89d7-69a59c930c46
X-Runtime: 0.032891
Vary: Origin
Content-Length: 186
200 OK
```


```json
{
  "id": 9,
  "email": "email9@example.com",
  "created_at": "2019-10-01T14:49:36.188-04:00",
  "updated_at": "2019-10-01T14:49:36.190-04:00",
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
ETag: W/&quot;cb71eacd6ef01ecbe838b5f09fb1f494&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 319df599-eee4-45aa-8c79-de5c31f473a5
X-Runtime: 0.153038
Vary: Origin
Content-Length: 1615
200 OK
```


```json
{
  "id": 2,
  "name": "Product #1 - 7253",
  "sku": "SKU-1",
  "weight": "0.0",
  "height": null,
  "width": null,
  "depth": null,
  "is_master": false,
  "slug": "product-1-7253",
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
      "attachment_updated_at": "2019-10-01T14:49:34.255-04:00",
      "attachment_width": 489,
      "attachment_height": 490,
      "alt": null,
      "viewable_type": "Spree::Variant",
      "viewable_id": 2,
      "mini_url": "http://localhost:3000/spree/images/attachments/000/000/001/mini/thinking-cat.jpg?1569955774",
      "small_url": "http://localhost:3000/spree/images/attachments/000/000/001/small/thinking-cat.jpg?1569955774",
      "product_url": "http://localhost:3000/spree/images/attachments/000/000/001/product/thinking-cat.jpg?1569955774",
      "large_url": "http://localhost:3000/spree/images/attachments/000/000/001/large/thinking-cat.jpg?1569955774"
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
      "on_sale": false
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
Authorizat IO N: Bearer af189915cecff1f23356048f91ae055c24c1c22a59e80527
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
ETag: W/&quot;541b4c2860bfdb66ddefd1d5da3035c0&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 8caa866a-2d11-44e2-9bc5-df4401b2767e
X-Runtime: 0.015502
Vary: Origin
Content-Length: 207
200 OK
```


```json
[
  {
    "id": 8,
    "user_id": 90,
    "payment_source_type": "SolidusPaypalBraintree::Source",
    "payment_source_id": 10,
    "default": false,
    "created_at": "2019-10-01T14:50:01.030-04:00",
    "updated_at": "2019-10-01T14:50:01.030-04:00"
  }
]
```



## Remove the payment from the user wallet


### Request

#### Endpoint

```plaintext
DELETE /api/wallet_payment_sources/7
Accept: application/json
Authorizat IO N: Bearer 9921c5e8d9a6ef9cef45f8a8eb89b45529193fc2be8feb95
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
X-Request-Id: 8c21c811-d4c2-400f-9d1d-d60b5a1200c6
X-Runtime: 0.012967
Vary: Origin
204 No Content
```




## Set a wallet payment source as the default user payment method


### Request

#### Endpoint

```plaintext
POST /api/wallet_payment_sources/6/default
Accept: application/json
Authorizat IO N: Bearer f8cd47b80e0da079713bdd4a3668832f89903d2342c15c8c
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
X-Request-Id: 464e02ab-bf83-4791-a730-0d3a2332fb43
X-Runtime: 0.032246
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
Authorizat IO N: Bearer 5d7e71457feb8f321fe373e150c18db80e391b78f81ad303
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/wished_products`

#### Parameters


```json
wished_product[wishlist_id]=35&wished_product[variant_id]=80&wished_product[quantity]=2&wished_product[remark]=Foo+bar
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
ETag: W/&quot;f52df0154a6ef0dd107d5aec7471a8fd&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: b38a8d5b-e52c-4a2c-b22b-c42bcb96be73
X-Runtime: 0.021315
Vary: Origin
Content-Length: 74
201 Created
```


```json
{
  "id": 16,
  "wishlist_id": 35,
  "variant_id": 80,
  "quantity": 2,
  "remark": "Foo bar"
}
```



## Delete a wished product


### Request

#### Endpoint

```plaintext
DELETE /api/wished_products/20
Accept: application/json
Authorizat IO N: Bearer 7ac1b46f6d70096f991c8b4d784b81c2493f5cfc83434588
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
X-Request-Id: ef9a85d2-5850-4154-b24a-0d4cb976d161
X-Runtime: 0.013066
Vary: Origin
204 No Content
```




## Get a single wished product


### Request

#### Endpoint

```plaintext
GET /api/wished_products/29
Accept: application/json
Authorizat IO N: Bearer 368078c7e3d7823285406900a8a81b4904cb3fa3f1de36ef
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
ETag: W/&quot;4877eefae6ca1e85263153605069cee9&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 2da78cdd-2ddc-4a60-b559-8ef9b3d0c039
X-Runtime: 0.011637
Vary: Origin
Content-Length: 70
200 OK
```


```json
{
  "id": 29,
  "wishlist_id": 40,
  "variant_id": 108,
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
Authorizat IO N: Bearer 1b10e2037c0a86e95ca606e077a9e43b2ffe4ac7e99a1549
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
ETag: W/&quot;b97d78928614b341077d9f8e05361ad1&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 6462edef-b398-4ec2-a270-130231ce5ab1
X-Runtime: 0.037137
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
      "variant_id": 68,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 11,
      "wishlist_id": 30,
      "variant_id": 70,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 12,
      "wishlist_id": 31,
      "variant_id": 72,
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
Authorizat IO N: Bearer c07029c95583b3c5bfc8a3829d81b2c1409224181cbe88ce
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
ETag: W/&quot;7bf5d48313cbd7468fbd4b42cdfb4499&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 7d32c193-e647-4340-9a04-6e8ee14f31b8
X-Runtime: 0.105415
Vary: Origin
Content-Length: 2146
200 OK
```


```json
{
  "wished_products": [
    {
      "id": 13,
      "wishlist_id": 32,
      "variant_id": 74,
      "quantity": 1,
      "remark": null,
      "variant": {
        "id": 74,
        "name": "Product #40 - 1621",
        "sku": "SKU-73",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-40-1621",
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
      "id": 14,
      "wishlist_id": 33,
      "variant_id": 76,
      "quantity": 1,
      "remark": null,
      "variant": {
        "id": 76,
        "name": "Product #41 - 9630",
        "sku": "SKU-75",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-41-9630",
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
      "id": 15,
      "wishlist_id": 34,
      "variant_id": 78,
      "quantity": 1,
      "remark": null,
      "variant": {
        "id": 78,
        "name": "Product #42 - 9797",
        "sku": "SKU-77",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-42-9797",
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
            "id": 36,
            "name": "Size-36",
            "presentation": "S",
            "option_type_name": "foo-size-36",
            "option_type_id": 36,
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
Authorizat IO N: Bearer eb0969008e0f31d0a0fde9ebe3d3f51af73a3d64daf832c1
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
ETag: W/&quot;497d7cda9acb4df806e4bf95c34b7944&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: c742a839-1660-4538-b67f-572e49c6b77f
X-Runtime: 0.105799
Vary: Origin
Content-Length: 2091
200 OK
```


```json
{
  "wished_products": [
    {
      "id": 26,
      "wishlist_id": 39,
      "variant_id": 102,
      "quantity": 1,
      "remark": null,
      "variant": {
        "id": 102,
        "name": "Product #54 - 6494",
        "sku": "SKU-101",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-54-6494",
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
    },
    {
      "id": 27,
      "wishlist_id": 39,
      "variant_id": 104,
      "quantity": 1,
      "remark": null,
      "variant": {
        "id": 104,
        "name": "Product #55 - 4640",
        "sku": "SKU-103",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-55-4640",
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
        "variant_properties": [

        ],
        "stock_items": [

        ],
        "prices": [

        ]
      }
    },
    {
      "id": 28,
      "wishlist_id": 39,
      "variant_id": 106,
      "quantity": 1,
      "remark": null,
      "variant": {
        "id": 106,
        "name": "Product #56 - 58",
        "sku": "SKU-105",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-56-58",
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
Authorizat IO N: Bearer f20c7896cbd7b98d83f72c0654c59b9089a5a553084d8fa3
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
ETag: W/&quot;f74cbbde9723fbfc39705cb71ca98dcc&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: ccfc046a-c2a9-403f-aa6c-1e3540edeeec
X-Runtime: 0.013990
Vary: Origin
Content-Length: 299
200 OK
```


```json
{
  "wished_products": [
    {
      "id": 23,
      "wishlist_id": 38,
      "variant_id": 96,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 24,
      "wishlist_id": 38,
      "variant_id": 98,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 25,
      "wishlist_id": 38,
      "variant_id": 100,
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
PATCH /api/wished_products/17
Accept: application/json
Authorizat IO N: Bearer 2cd34667fed686d4f1a26d6e57c48fc4dfe34b289fd0fe1e
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/wished_products/:id`

#### Parameters


```json
wished_product[wishlist_id]=36&wished_product[variant_id]=88&wished_product[quantity]=2&wished_product[remark]=Foo+bar
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
ETag: W/&quot;8ac81b78976da78f050d5a1f3b0eff40&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 56cd7a62-0173-4823-96bd-100b67df2130
X-Runtime: 0.016064
Vary: Origin
Content-Length: 74
200 OK
```


```json
{
  "id": 17,
  "wishlist_id": 36,
  "variant_id": 88,
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
Authorizat IO N: Bearer 624436617af00792ac9cf82c3090104872a5988a2ce4b4b8
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/wishlists`

#### Parameters


```json
wishlist[name]&wishlist[user_id]=19&wishlist[is_default]=true&wishlist[is_public]=false
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
ETag: W/&quot;cf25e57e128109fbb9f6eefce4ee914d&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 0a0eaca5-b41e-41f9-be42-206f025adc2b
X-Runtime: 0.082368
Vary: Origin
Content-Length: 99
201 Created
```


```json
{
  "id": 1,
  "user_id": 19,
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
Authorizat IO N: Bearer 610a5f60da51383b9fc1084559ea25ab14c83e6fb6f16860
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
X-Request-Id: 4ae51b64-b75c-46d0-9628-2e150280558b
X-Runtime: 0.022180
Vary: Origin
204 No Content
```




## Get a single wishlist


### Request

#### Endpoint

```plaintext
GET /api/wishlists/18
Accept: application/json
Authorizat IO N: Bearer 0ca0ccaaff7f183a9fdbc72f2ccbd344448ecd9ea943fe8d
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
ETag: W/&quot;f855126ff8bd35ab2f7d8b11b19235ce&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: abe871ed-9c6d-4364-ab67-78344c87f7f0
X-Runtime: 0.009999
Vary: Origin
Content-Length: 307
200 OK
```


```json
{
  "id": 18,
  "user_id": 25,
  "name": "Wishlist #16",
  "is_public": false,
  "is_default": true,
  "wished_products": [
    {
      "id": 7,
      "wishlist_id": 18,
      "variant_id": 44,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 8,
      "wishlist_id": 18,
      "variant_id": 46,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 9,
      "wishlist_id": 18,
      "variant_id": 48,
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
Authorizat IO N: Bearer bbd36c598ee0c2fdd16aff5058fa70257b923efb517b0c9a
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
ETag: W/&quot;417a43b1f7466db88bcacb22eebe2b10&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 0a71ad5f-e878-4636-b12c-7284efdadc92
X-Runtime: 0.016694
Vary: Origin
Content-Length: 894
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
      "user_id": 27,
      "name": "Wishlist #18",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 21,
      "user_id": 28,
      "name": "Wishlist #19",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 22,
      "user_id": 29,
      "name": "Wishlist #20",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 23,
      "user_id": 30,
      "name": "Wishlist #21",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 24,
      "user_id": 31,
      "name": "Wishlist #22",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 25,
      "user_id": 32,
      "name": "Wishlist #23",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 26,
      "user_id": 33,
      "name": "Wishlist #24",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 27,
      "user_id": 34,
      "name": "Wishlist #25",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 28,
      "user_id": 35,
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
Authorizat IO N: Bearer e91fcc0beb93c54a233304d5e6cae23bc90a30bd42c85f59
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
ETag: W/&quot;11ba7441c6114c4b8f525a3d6c9d501d&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: d37f7254-c743-435e-96a1-29ab369335ef
X-Runtime: 0.013534
Vary: Origin
Content-Length: 302
200 OK
```


```json
{
  "id": 3,
  "user_id": 21,
  "name": "Wishlist #1",
  "is_public": false,
  "is_default": true,
  "wished_products": [
    {
      "id": 1,
      "wishlist_id": 3,
      "variant_id": 32,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 2,
      "wishlist_id": 3,
      "variant_id": 34,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 3,
      "wishlist_id": 3,
      "variant_id": 36,
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
Authorizat IO N: Bearer db126dbfb07246eb6ec943d0f48c293505bb49b9a4386413
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
ETag: W/&quot;f11e6d765625d93d0dde24864730b385&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: bf08e3db-313d-4103-88c5-bdfcabceb79f
X-Runtime: 0.011738
Vary: Origin
Content-Length: 897
200 OK
```


```json
{
  "wishlists": [
    {
      "id": 8,
      "user_id": 24,
      "name": "Wishlist #6",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 9,
      "user_id": 24,
      "name": "Wishlist #7",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 10,
      "user_id": 24,
      "name": "Wishlist #8",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 11,
      "user_id": 24,
      "name": "Wishlist #9",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 12,
      "user_id": 24,
      "name": "Wishlist #10",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 13,
      "user_id": 24,
      "name": "Wishlist #11",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 14,
      "user_id": 24,
      "name": "Wishlist #12",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 15,
      "user_id": 24,
      "name": "Wishlist #13",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 16,
      "user_id": 24,
      "name": "Wishlist #14",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 17,
      "user_id": 24,
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
PATCH /api/wishlists/4
Accept: application/json
Authorizat IO N: Bearer e3ae8a302b43b63e3a130f466a5a6c18017c3d5f62da3e20
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/wishlists/:id`

#### Parameters


```json
wishlist[name]=Another+Wishlist&wishlist[user_id]=22&wishlist[is_default]=true&wishlist[is_public]=false
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
ETag: W/&quot;c539b53ab202267e339ed11bae5e4633&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 9791d37a-890b-49d2-9be3-62feec0f8302
X-Runtime: 0.027675
Vary: Origin
Content-Length: 307
200 OK
```


```json
{
  "id": 4,
  "user_id": 22,
  "name": "Another Wishlist",
  "is_public": false,
  "is_default": true,
  "wished_products": [
    {
      "id": 4,
      "wishlist_id": 4,
      "variant_id": 38,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 5,
      "wishlist_id": 4,
      "variant_id": 40,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 6,
      "wishlist_id": 4,
      "variant_id": 42,
      "quantity": 1,
      "remark": null
    }
  ]
}
```



