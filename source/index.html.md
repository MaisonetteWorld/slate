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
PUT /api/orders/R420878599/addresses/41
Accept: application/json
X-Spree-Order-Token: MWkTQFikMwzpG0JRgR0vZg
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
ETag: W/&quot;cac4a51a687223b92d6e03def4189db1&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 5ed3bdd9-6c89-4b17-8fc1-239b0d8a69f6
X-Runtime: 0.046207
Content-Length: 507
200 OK
```


```json
{
  "id": 42,
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
}
```



# Braintree transactions



## Creating a PayPal express checkout transaction


### Request

#### Endpoint

```plaintext
POST /api/braintree/transactions
Accept: application/json
X-Spree-Order-Token: jG8Ab2YOCrtbEbfmq_kupg
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/braintree/transactions`

#### Parameters


```json
order_id=R582022033&payment_method_id=10&options[restart_checkout]=true&transaction[email]=maryellen.oga%40mckenziemcglynn.com&transaction[nonce]=fake-paypal-billing-agreement-nonce&transaction[phone]=555-555-0199&transaction[address_attributes][first_name]=John&transaction[address_attributes][last_name]=Stamm&transaction[address_attributes][address_line_1]=A+Different+Road&transaction[address_attributes][city]=Herndon&transaction[address_attributes][state_code]=AL&transaction[address_attributes][zip]=10017&transaction[address_attributes][country_code]=US&transaction[payment_type]=PayPalAccount
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
ETag: W/&quot;0da8b501e43105c10e40926da362990d&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 91a3b5fd-3a15-4bc2-9f4c-feaef7caca54
X-Runtime: 0.312146
Content-Length: 4704
200 OK
```


```json
{
  "id": 9,
  "number": "R582022033",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2019-09-04T10:43:39.569Z",
  "updated_at": "2019-09-04T10:43:39.846Z",
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
  "token": "jG8Ab2YOCrtbEbfmq_kupg",
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
    "id": 20,
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
  "ship_address": {
    "id": 20,
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
  "line_items": [
    {
      "id": 10,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 22,
      "vendor_id": 52,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 22,
        "name": "Product #11 - 1568",
        "sku": "SKU-21",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-11-1568",
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
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 11,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #52",
      "country_iso": "US",
      "adjustments": [

      ]
    }
  ],
  "payments": [
    {
      "id": 6,
      "source_type": "SolidusPaypalBraintree::Source",
      "source_id": 2,
      "amount": "110.0",
      "display_amount": "$110.00",
      "payment_method_id": 10,
      "state": "checkout",
      "avs_response": null,
      "created_at": "2019-09-04T10:43:39.677Z",
      "updated_at": "2019-09-04T10:43:39.677Z",
      "payment_method": {
        "id": 10,
        "name": "Braintree"
      },
      "source": {
        "id": 2,
        "payment_type": "PayPalAccount",
        "token": "bgx899",
        "created_at": "2019-09-04T10:43:39.676Z",
        "email": "jane.doe@paypal.com"
      }
    }
  ],
  "shipments": [
    {
      "id": 11,
      "tracking": null,
      "tracking_url": null,
      "number": "H18687323445",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R582022033",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 11,
          "name": "UPS Ground",
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
              "id": 9,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 9,
              "name": "ShippingCategory #9"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 22,
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
X-Spree-Order-Token: hR_QxAOqjCWT4PdBZYS0ig
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/braintree/transactions`

#### Parameters


```json
order_id=R151647487&payment_method_id=9&options[restart_checkout]=true&transaction[email]=maryellen.oga%40mckenziemcglynn.com&transaction[nonce]=fake-apple-pay-visa-nonce&transaction[phone]=555-555-0199&transaction[address_attributes][first_name]=John&transaction[address_attributes][last_name]=Stamm&transaction[address_attributes][address_line_1]=A+Different+Road&transaction[address_attributes][city]=Herndon&transaction[address_attributes][state_code]=AL&transaction[address_attributes][zip]=10015&transaction[address_attributes][country_code]=US&transaction[payment_type]=ApplePayCard
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
ETag: W/&quot;b52d83848cae95d915ddd24fd500a1e9&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 137d266a-90b2-4acc-981d-10ab1c07ff87
X-Runtime: 0.403606
Content-Length: 4743
200 OK
```


```json
{
  "id": 8,
  "number": "R151647487",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2019-09-04T10:43:38.831Z",
  "updated_at": "2019-09-04T10:43:39.225Z",
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
  "token": "hR_QxAOqjCWT4PdBZYS0ig",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 9,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 17,
    "firstname": "John",
    "lastname": "Stamm",
    "full_name": "John Stamm",
    "address1": "A Different Road",
    "address2": null,
    "city": "Herndon",
    "zipcode": "10015",
    "phone": "555-555-0199",
    "company": null,
    "alternative_phone": null,
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
  "ship_address": {
    "id": 17,
    "firstname": "John",
    "lastname": "Stamm",
    "full_name": "John Stamm",
    "address1": "A Different Road",
    "address2": null,
    "city": "Herndon",
    "zipcode": "10015",
    "phone": "555-555-0199",
    "company": null,
    "alternative_phone": null,
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
  "line_items": [
    {
      "id": 9,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 20,
      "vendor_id": 47,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 20,
        "name": "Product #10 - 2668",
        "sku": "SKU-19",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-10-2668",
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
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 10,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #47",
      "country_iso": "US",
      "adjustments": [

      ]
    }
  ],
  "payments": [
    {
      "id": 5,
      "source_type": "SolidusPaypalBraintree::Source",
      "source_id": 1,
      "amount": "110.0",
      "display_amount": "$110.00",
      "payment_method_id": 9,
      "state": "checkout",
      "avs_response": null,
      "created_at": "2019-09-04T10:43:38.997Z",
      "updated_at": "2019-09-04T10:43:38.997Z",
      "payment_method": {
        "id": 9,
        "name": "Braintree"
      },
      "source": {
        "id": 1,
        "payment_type": "ApplePayCard",
        "token": "cg7hsk",
        "created_at": "2019-09-04T10:43:38.994Z",
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
      "number": "H02256140364",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R151647487",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 9,
          "name": "UPS Ground",
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
              "id": 8,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 8,
              "name": "ShippingCategory #8"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 20,
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
PUT /api/checkouts/R891008586/complete
Accept: application/json
X-Spree-Order-Token: t6oksejRpyIoUMLPrEMKVg
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
ETag: W/&quot;92ec4cbae350bd27e000007c5d9527a5&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 56d75fb0-ce15-4b94-89ad-00f18383163e
X-Runtime: 4.415061
Content-Length: 4888
200 OK
```


```json
{
  "id": 19,
  "number": "R891008586",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "complete",
  "adjustment_total": "0.0",
  "user_id": 58,
  "created_at": "2019-09-04T10:43:52.803Z",
  "updated_at": "2019-09-04T10:44:00.269Z",
  "completed_at": "2019-09-04T10:44:00.269Z",
  "payment_total": "110.0",
  "shipment_state": "ready",
  "payment_state": "paid",
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
  "display_item_total": "$10.00",
  "total_quantity": 1,
  "display_total": "$110.00",
  "display_ship_total": "$100.00",
  "display_tax_total": "$0.00",
  "token": "t6oksejRpyIoUMLPrEMKVg",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 27,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    },
    {
      "id": 28,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 38,
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
    "id": 39,
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
      "id": 23,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 99,
      "vendor_id": 184,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 99,
        "name": "Product #53 - 759",
        "sku": "SKU-98",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-53-759",
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
            "id": 46,
            "name": "Size-46",
            "presentation": "S",
            "option_type_name": "foo-size-46",
            "option_type_id": 46,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 53,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #184",
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
      "payment_method_id": 27,
      "state": "completed",
      "avs_response": "M",
      "created_at": "2019-09-04T10:43:52.904Z",
      "updated_at": "2019-09-04T10:44:00.105Z",
      "payment_method": {
        "id": 27,
        "name": "Braintree"
      },
      "source": {
        "id": 10,
        "payment_type": "CreditCard",
        "token": "3qhtnf",
        "created_at": "2019-09-04T10:43:52.903Z",
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
      "number": "H30172351547",
      "cost": "100.0",
      "shipped_at": null,
      "state": "ready",
      "order_id": "R891008586",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 24,
          "name": "UPS Ground",
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
              "id": 33,
              "name": "ShippingCategory #33"
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
PATCH /api/checkouts/R771307031
Accept: application/json
X-Spree-Order-Token: DsRZJLAhaP3tq6Gcjxpfdw
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=23&order[payment_attributes][][source_attributes][nonce]=fake-apple-pay-visa-nonce&order[payment_attributes][][source_attributes][payment_type]=ApplePayCard
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
ETag: W/&quot;f4fef3e4f828cf95ac476aee21e4a79c&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 0915083e-b999-4bac-a84f-9f7a5038d82f
X-Runtime: 0.163374
Content-Length: 4291
200 OK
```


```json
{
  "id": 15,
  "number": "R771307031",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 54,
  "created_at": "2019-09-04T10:43:49.751Z",
  "updated_at": "2019-09-04T10:43:50.065Z",
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
  "display_item_total": "$10.00",
  "total_quantity": 1,
  "display_total": "$110.00",
  "display_ship_total": "$100.00",
  "display_tax_total": "$0.00",
  "token": "DsRZJLAhaP3tq6Gcjxpfdw",
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
    "id": 30,
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
    "country_id": 30,
    "country_iso": "US",
    "state_id": 30,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 30,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 30,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 30
    }
  },
  "ship_address": {
    "id": 31,
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
    "country_id": 30,
    "country_iso": "US",
    "state_id": 30,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 30,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 30,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 30
    }
  },
  "line_items": [
    {
      "id": 19,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 91,
      "vendor_id": 164,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 91,
        "name": "Product #49 - 4837",
        "sku": "SKU-90",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-49-4837",
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
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 49,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #164",
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
      "number": "H48561481716",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R771307031",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 17,
          "name": "UPS Ground",
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
              "id": 29,
              "name": "ShippingCategory #29"
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
PATCH /api/checkouts/R157413392
Accept: application/json
X-Spree-Order-Token: gzyenklFrQ-NpPkWKALRzQ
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=24&order[payment_attributes][][source_attributes][nonce]=fake-paypal-billing-agreement-nonce&order[payment_attributes][][source_attributes][payment_type]=PayPalAccount
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
ETag: W/&quot;7ffca77af5e5bb6d367a62993f6d9f24&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 1bfeb659-7c1f-46c1-adf4-a7913d4526b4
X-Runtime: 0.169102
Content-Length: 4291
200 OK
```


```json
{
  "id": 16,
  "number": "R157413392",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 55,
  "created_at": "2019-09-04T10:43:50.523Z",
  "updated_at": "2019-09-04T10:43:50.838Z",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
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
  "display_item_total": "$10.00",
  "total_quantity": 1,
  "display_total": "$110.00",
  "display_ship_total": "$100.00",
  "display_tax_total": "$0.00",
  "token": "gzyenklFrQ-NpPkWKALRzQ",
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
    }
  ],
  "bill_address": {
    "id": 32,
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
    "state": {
      "id": 31,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 31
    }
  },
  "ship_address": {
    "id": 33,
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
    "state": {
      "id": 31,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 31
    }
  },
  "line_items": [
    {
      "id": 20,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 93,
      "vendor_id": 169,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 93,
        "name": "Product #50 - 6221",
        "sku": "SKU-92",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-50-6221",
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
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 50,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #169",
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
      "number": "H33381862057",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R157413392",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 19,
          "name": "UPS Ground",
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
              "id": 30,
              "name": "ShippingCategory #30"
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
PATCH /api/checkouts/R158374642
Accept: application/json
X-Spree-Order-Token: Z5aB0kXFyUfa_Ey37YjD_A
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=25&order[payment_attributes][][source_attributes][nonce]=fake-valid-visa-nonce&order[payment_attributes][][source_attributes][payment_type]=CreditCard
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
ETag: W/&quot;6ac1fbbe90c1a4ac2a7996f393f1ebcb&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: b7bd9f6c-03a0-4b05-9253-e02d98b6277e
X-Runtime: 0.178171
Content-Length: 4291
200 OK
```


```json
{
  "id": 17,
  "number": "R158374642",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 56,
  "created_at": "2019-09-04T10:43:51.293Z",
  "updated_at": "2019-09-04T10:43:51.612Z",
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
  "display_item_total": "$10.00",
  "total_quantity": 1,
  "display_total": "$110.00",
  "display_ship_total": "$100.00",
  "display_tax_total": "$0.00",
  "token": "Z5aB0kXFyUfa_Ey37YjD_A",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 25,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 34,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "PO Box 1337",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10032",
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
    "id": 35,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "A Different Road",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10033",
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
      "id": 21,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 95,
      "vendor_id": 174,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 95,
        "name": "Product #51 - 8515",
        "sku": "SKU-94",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-51-8515",
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
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 51,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #174",
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
      "number": "H12106534380",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R158374642",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 21,
          "name": "UPS Ground",
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
              "id": 31,
              "name": "ShippingCategory #31"
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
PATCH /api/checkouts/R707544329
Accept: application/json
X-Spree-Order-Token: vO4V72vZm-aWCERYPbDP5A
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=26&order[payment_attributes][][source_attributes][wallet_payment_source_id]=7
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
ETag: W/&quot;acf8d853bedb6e99667451a0de8ce5a7&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 1b026604-bb0b-4037-a886-f65dc2daf371
X-Runtime: 0.153741
Content-Length: 4291
200 OK
```


```json
{
  "id": 18,
  "number": "R707544329",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 57,
  "created_at": "2019-09-04T10:43:52.065Z",
  "updated_at": "2019-09-04T10:43:52.369Z",
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
  "display_item_total": "$10.00",
  "total_quantity": 1,
  "display_total": "$110.00",
  "display_ship_total": "$100.00",
  "display_tax_total": "$0.00",
  "token": "vO4V72vZm-aWCERYPbDP5A",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 26,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 36,
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
    "id": 37,
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
      "id": 22,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 97,
      "vendor_id": 179,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 97,
        "name": "Product #52 - 3503",
        "sku": "SKU-96",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-52-3503",
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
            "id": 45,
            "name": "Size-45",
            "presentation": "S",
            "option_type_name": "foo-size-45",
            "option_type_id": 45,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 52,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #179",
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
      "number": "H47341061107",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R707544329",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 23,
          "name": "UPS Ground",
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
              "id": 32,
              "name": "ShippingCategory #32"
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



## update address


### Request

#### Endpoint

```plaintext
PUT /api/checkouts/R504407414
Accept: application/json
X-Spree-Order-Token: Qe-F74ZjZYkuwfA8UPeWvw
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PUT /api/checkouts/:id`

#### Parameters


```json
order[ship_address_attributes][id]&order[ship_address_attributes][firstname]=John&order[ship_address_attributes][lastname]&order[ship_address_attributes][address1]=10+Lovely+Street&order[ship_address_attributes][address2]=Northwest&order[ship_address_attributes][city]=Herndon&order[ship_address_attributes][zipcode]=10027&order[ship_address_attributes][phone]=555-555-0199&order[ship_address_attributes][state_name]&order[ship_address_attributes][alternative_phone]=555-555-0199&order[ship_address_attributes][company]=Company&order[ship_address_attributes][state_id]=29&order[ship_address_attributes][country_id]=29&order[ship_address_attributes][created_at]&order[ship_address_attributes][updated_at]&order[use_billing]=true&hold_state=true
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
ETag: W/&quot;5e0e2454c5fce90944db2a7bc5b1c9f9&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: e846db35-28f4-400d-8d60-d298ce3248d1
X-Runtime: 0.175587
Content-Length: 4198
200 OK
```


```json
{
  "id": 14,
  "number": "R504407414",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "cart",
  "adjustment_total": "0.0",
  "user_id": 53,
  "created_at": "2019-09-04T10:43:49.132Z",
  "updated_at": "2019-09-04T10:43:49.287Z",
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
  "total_applicable_store_credit": 0,
  "display_total_available_store_credit": "$0.00",
  "display_store_credit_remaining_after_capture": "$0.00",
  "canceler_id": null,
  "display_item_total": "$10.00",
  "total_quantity": 1,
  "display_total": "$110.00",
  "display_ship_total": "$100.00",
  "display_tax_total": "$0.00",
  "token": "Qe-F74ZjZYkuwfA8UPeWvw",
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
    "id": 29,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "10 Lovely Street",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10027",
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
  },
  "ship_address": {
    "id": 29,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "10 Lovely Street",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10027",
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
  },
  "line_items": [
    {
      "id": 18,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 89,
      "vendor_id": 159,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 89,
        "name": "Product #48 - 4977",
        "sku": "SKU-88",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-48-4977",
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
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 48,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #159",
      "country_iso": "US",
      "adjustments": [

      ]
    }
  ],
  "payments": [

  ],
  "shipments": [
    {
      "id": 15,
      "tracking": "U10000",
      "tracking_url": null,
      "number": "H26685857335",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "R504407414",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 15,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 13,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 15,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 13,
        "shipping_method_code": "UPS_GROUND",
        "display_cost": "$100.00"
      },
      "shipping_methods": [
        {
          "id": 13,
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
              "id": 28,
              "name": "ShippingCategory #28"
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
POST /api/orders/R486434171/line_items
Accept: application/json
X-Spree-Order-Token: qwRZv3XjPxVCAyhCQc043g
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/:order_number/line_items`

#### Parameters


```json
line_item[variant_id]=10&line_item[options][vendor_id]=18
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
ETag: W/&quot;8be5a018425f5732fef2123f924eeb7c&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: bb87f70c-1e28-426e-b8f3-9b3ed640b2ee
X-Runtime: 0.080254
Content-Length: 853
201 Created
```


```json
{
  "id": 4,
  "quantity": 1,
  "price": "19.99",
  "variant_id": 10,
  "vendor_id": 18,
  "single_display_amount": "$19.99",
  "display_amount": "$19.99",
  "total": "19.99",
  "final_sale": false,
  "backordered": null,
  "promotionable": true,
  "variant": {
    "id": 10,
    "name": "Product #5 - 8354",
    "sku": "SKU-9",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": false,
    "slug": "product-5-8354",
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
        "option_type_presentation": "Size"
      }
    ],
    "images": [

    ],
    "product_id": 5,
    "brand": null,
    "brand_slug": null,
    "brand_description": null
  },
  "vendor_name": "Vendor #18",
  "country_iso": null,
  "adjustments": [

  ]
}
```



## Deleting a line item


### Request

#### Endpoint

```plaintext
DELETE /api/orders/R080029164/line_items/2
Accept: application/json
X-Spree-Order-Token: LkOyk-wIIqC4N49KSxWJqg
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
X-Request-Id: 75851884-2290-494f-b9b4-28eab16955c8
X-Runtime: 0.072509
204 No Content
```




## Updating a line item


### Request

#### Endpoint

```plaintext
PUT /api/orders/R168018905/line_items/1
Accept: application/json
X-Spree-Order-Token: xQ5UUo8XvLz31hJDVLd8zA
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
ETag: W/&quot;ac9b146e4729fe1d08997b8379326346&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: a2fbce79-b4d0-45fc-aa9a-d1281658e1d0
X-Runtime: 0.249014
Content-Length: 846
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
  "final_sale": false,
  "backordered": null,
  "promotionable": true,
  "variant": {
    "id": 2,
    "name": "Product #1 - 5505",
    "sku": "SKU-1",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": false,
    "slug": "product-1-5505",
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
        "option_type_presentation": "Size"
      }
    ],
    "images": [

    ],
    "product_id": 1,
    "brand": null,
    "brand_slug": null,
    "brand_description": null
  },
  "vendor_name": "Vendor #2",
  "country_iso": "US",
  "adjustments": [

  ]
}
```



# Minis

Destroy a mini. Users can destroy their own minis, admins can destroy any.

## Create a mini


### Request

#### Endpoint

```plaintext
POST /api/minis
Accept: application/json
Authorization: Bearer 83f96a7257e4bfbcaf0f1ea11186690a8aba18d3b3cfe6ab
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/minis`

#### Parameters


```json
mini[name]=Winny&mini[user_id]=64&mini[birth_year]=2019&mini[birth_month]=1&mini[birth_day]=1
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
ETag: W/&quot;a8aef6bd9b9f20bd6e87e94a06d73a62&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: b61985a7-3bbb-4d49-963d-2e19a5026761
X-Runtime: 0.009392
Content-Length: 121
201 Created
```


```json
{
  "id": 8,
  "user_id": 64,
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
DELETE /api/minis/1
Accept: application/json
Authorization: Bearer 65d359e3c2226574d1a8a831da9fafd3c20278f6587e8618
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
X-Request-Id: 38423f04-98ed-4e8c-ad11-70e0d68de08c
X-Runtime: 0.026874
204 No Content
```




## Get a single mini


### Request

#### Endpoint

```plaintext
GET /api/minis/2
Accept: application/json
Authorization: Bearer 50c45a304c949bb4e681af79440f0a4e7ccca9ca6f891269
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
ETag: W/&quot;44a34f67e4e936a3e668ddd6b81ee880&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: eef6ee5c-587f-4332-856a-ca1c27f6c364
X-Runtime: 0.015244
Content-Length: 126
200 OK
```


```json
{
  "id": 2,
  "user_id": 61,
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
Authorization: Bearer 00507e9813aeafbc396abb265daf4c7e07ca7e59d879d497
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
ETag: W/&quot;6a7d404226d678742dd313b716fbe1f8&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 339a9d12-ad63-4c8e-9409-d1312cc16e13
X-Runtime: 0.013680
Content-Length: 1359
200 OK
```


```json
{
  "minis": [
    {
      "id": 9,
      "user_id": 65,
      "name": "Mini",
      "birth_year": 2018,
      "birth_month": null,
      "birth_day": null,
      "gender_boy": true,
      "gender_girl": true
    },
    {
      "id": 10,
      "user_id": 66,
      "name": "Mini",
      "birth_year": 2018,
      "birth_month": null,
      "birth_day": null,
      "gender_boy": true,
      "gender_girl": true
    },
    {
      "id": 11,
      "user_id": 67,
      "name": "Mini",
      "birth_year": 2018,
      "birth_month": null,
      "birth_day": null,
      "gender_boy": true,
      "gender_girl": true
    },
    {
      "id": 12,
      "user_id": 68,
      "name": "Mini",
      "birth_year": 2018,
      "birth_month": null,
      "birth_day": null,
      "gender_boy": true,
      "gender_girl": true
    },
    {
      "id": 13,
      "user_id": 69,
      "name": "Mini",
      "birth_year": 2018,
      "birth_month": null,
      "birth_day": null,
      "gender_boy": true,
      "gender_girl": true
    },
    {
      "id": 14,
      "user_id": 70,
      "name": "Mini",
      "birth_year": 2018,
      "birth_month": null,
      "birth_day": null,
      "gender_boy": true,
      "gender_girl": true
    },
    {
      "id": 15,
      "user_id": 71,
      "name": "Mini",
      "birth_year": 2018,
      "birth_month": null,
      "birth_day": null,
      "gender_boy": true,
      "gender_girl": true
    },
    {
      "id": 16,
      "user_id": 72,
      "name": "Mini",
      "birth_year": 2018,
      "birth_month": null,
      "birth_day": null,
      "gender_boy": true,
      "gender_girl": true
    },
    {
      "id": 17,
      "user_id": 73,
      "name": "Mini",
      "birth_year": 2018,
      "birth_month": null,
      "birth_day": null,
      "gender_boy": true,
      "gender_girl": true
    },
    {
      "id": 18,
      "user_id": 74,
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
Authorization: Bearer 8d4aa0542cb656785432e15df4fba8e187f35681014e37aa
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
ETag: W/&quot;0f3f7a59ac8698c031fd5ab4edd2feea&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 5bb6c712-60c5-47ce-b18c-1ebd625a86b8
X-Runtime: 0.013180
Content-Length: 332
200 OK
```


```json
{
  "minis": [
    {
      "id": 6,
      "user_id": 63,
      "name": "Mini",
      "birth_year": 2018,
      "birth_month": null,
      "birth_day": null,
      "gender_boy": true,
      "gender_girl": true
    },
    {
      "id": 7,
      "user_id": 63,
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
PATCH /api/minis/19
Accept: application/json
Authorization: Bearer 6fa8ba9ecbbe2bf42e2463246de062c1248a132d37ddcd6a
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
ETag: W/&quot;ccfdcc1d4341b78082979c32a19c33eb&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: aa52bdfd-2f76-4b0b-8fa1-cb3c4dff66f3
X-Runtime: 0.010710
Content-Length: 128
200 OK
```


```json
{
  "id": 19,
  "user_id": 76,
  "name": "Marge",
  "birth_year": 2018,
  "birth_month": null,
  "birth_day": null,
  "gender_boy": true,
  "gender_girl": true
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
ETag: W/&quot;64cbc6c193ee705aee4d1b87854336d5&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 0b1d3fbe-b77c-46a7-aca6-5a9e8b58b784
X-Runtime: 0.101351
Content-Length: 130
200 OK
```


```json
[
  {
    "id": 2,
    "name": "Kids",
    "navigation_url": "/navigation/kids",
    "parent_id": 1,
    "lft": 2,
    "depth": 1,
    "highlight": false,
    "header_link": false
  }
]
```



# Orders

Return an order, scoped to the current user

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
user_id&order_token&line_item[variant_id]=60&line_item[quantity]=2&line_item[vendor_id]=104
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
ETag: W/&quot;cd373dfe2f523092c1f345224d2743fc&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: fcfc8605-325f-4ff7-9e3c-2773beaff0dc
X-Runtime: 0.128254
Content-Length: 2316
200 OK
```


```json
{
  "id": 13,
  "number": "R179049771",
  "item_total": "39.98",
  "total": "39.98",
  "ship_total": "0.0",
  "state": "cart",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2019-09-04T10:43:44.548Z",
  "updated_at": "2019-09-04T10:43:44.591Z",
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
  "token": "P2dyQdnED_BiakzL-fHo7w",
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
      "id": 17,
      "quantity": 2,
      "price": "19.99",
      "variant_id": 60,
      "vendor_id": 104,
      "single_display_amount": "$19.99",
      "display_amount": "$39.98",
      "total": "39.98",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 60,
        "name": "Product #30 - 8600",
        "sku": "SKU-59",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-30-8600",
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
            "id": 30,
            "name": "Size-30",
            "presentation": "S",
            "option_type_name": "foo-size-30",
            "option_type_id": 30,
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 30,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #104",
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
Authorization: Bearer be0ca72044991051dc5984903a2a2f9429500c8d3631d0a6
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
ETag: W/&quot;a628d9670845919e8f5b42888e66096d&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 0109b077-a69f-4d9a-99c4-f2e8affe9252
X-Runtime: 0.024247
Content-Length: 305
200 OK
```


```json
{
  "orders": [
    {
      "number": "R601674747",
      "completed_at": "2019-09-04T10:43:44.029Z",
      "total": "120.0",
      "state": "Complete",
      "shipment_state": "shipped",
      "shipments": [
        {
          "number": "H75433750065",
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
GET /api/orders/R811432909
Accept: application/json
Authorization: Bearer f7a449bb4c5b13a9ae8cc3d7db7d5f39a4dafff96c6de7fa
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
ETag: W/&quot;aa6478f411a5ccb8f14289b2475d74c5&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 7f310489-be29-4943-aefc-7c3c5b1bb06d
X-Runtime: 0.154734
Content-Length: 9248
200 OK
```


```json
{
  "id": 10,
  "number": "R811432909",
  "item_total": "20.0",
  "total": "120.0",
  "ship_total": "100.0",
  "state": "complete",
  "adjustment_total": "0.0",
  "user_id": 23,
  "created_at": "2019-09-04T10:43:42.388Z",
  "updated_at": "2019-09-04T10:43:42.697Z",
  "completed_at": "2019-09-04T10:43:42.471Z",
  "payment_total": "120.0",
  "shipment_state": "shipped",
  "payment_state": "paid",
  "email": "email22@example.com",
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
  "token": "X3eHmHquRCQWeIevwMC6tg",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 14,
      "name": "Credit Card",
      "partial_name": "gateway",
      "method_type": "gateway"
    },
    {
      "id": 15,
      "name": "Credit Card",
      "partial_name": "gateway",
      "method_type": "gateway"
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
    "zipcode": "10021",
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
      "id": 11,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 52,
      "vendor_id": 90,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 52,
        "name": "Product #26 - 4248",
        "sku": "SKU-51",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-26-4248",
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
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 26,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #90",
      "country_iso": "US",
      "adjustments": [
        {
          "id": 8,
          "source_type": "Spree::TaxRate",
          "source_id": 1,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 11,
          "amount": "2.0",
          "label": "VAT 5%",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-09-04T10:43:42.657Z",
          "updated_at": "2019-09-04T10:43:42.670Z",
          "display_amount": "$2.00"
        },
        {
          "id": 2,
          "source_type": "Spree::PromotionAction",
          "source_id": 1,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 11,
          "amount": "5.0",
          "label": "foo",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-09-04T10:43:42.583Z",
          "updated_at": "2019-09-04T10:43:42.583Z",
          "display_amount": "$5.00"
        },
        {
          "id": 1,
          "source_type": "Spree::PromotionAction",
          "source_id": 1,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 11,
          "amount": "5.0",
          "label": "foo",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-09-04T10:43:42.571Z",
          "updated_at": "2019-09-04T10:43:42.571Z",
          "display_amount": "$5.00"
        }
      ]
    },
    {
      "id": 12,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 52,
      "vendor_id": 90,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 52,
        "name": "Product #26 - 4248",
        "sku": "SKU-51",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-26-4248",
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
            "option_type_presentation": "Size"
          }
        ],
        "images": [

        ],
        "product_id": 26,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "vendor_name": "Vendor #90",
      "country_iso": "US",
      "adjustments": [
        {
          "id": 9,
          "source_type": "Spree::TaxRate",
          "source_id": 2,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 12,
          "amount": "1.5",
          "label": "VAT 5%",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-09-04T10:43:42.693Z",
          "updated_at": "2019-09-04T10:43:42.708Z",
          "display_amount": "$1.50"
        },
        {
          "id": 3,
          "source_type": "Spree::PromotionAction",
          "source_id": 1,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 12,
          "amount": "5.0",
          "label": "bar",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-09-04T10:43:42.590Z",
          "updated_at": "2019-09-04T10:43:42.590Z",
          "display_amount": "$5.00"
        }
      ]
    }
  ],
  "payments": [
    {
      "id": 7,
      "source_type": "Spree::CreditCard",
      "source_id": 5,
      "amount": "120.0",
      "display_amount": "$120.00",
      "payment_method_id": 14,
      "state": "completed",
      "avs_response": null,
      "created_at": "2019-09-04T10:43:42.486Z",
      "updated_at": "2019-09-04T10:43:42.486Z",
      "payment_method": {
        "id": 14,
        "name": "Credit Card"
      },
      "source": {
        "id": 5,
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
      "id": 12,
      "tracking": "U10000",
      "tracking_url": null,
      "number": "H01263067573",
      "cost": "100.0",
      "shipped_at": "2019-09-04T10:43:42.516Z",
      "state": "shipped",
      "order_id": "R811432909",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 12,
          "name": "UPS Ground",
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 10,
          "shipping_method_code": "UPS_GROUND",
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 12,
        "name": "UPS Ground",
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 10,
        "shipping_method_code": "UPS_GROUND",
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
              "id": 15,
              "name": "ShippingCategory #15"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 52,
          "quantity": 1,
          "states": {
            "shipped": 1
          }
        },
        {
          "variant_id": 52,
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
          "adjustable_id": 12,
          "amount": "-10.0",
          "label": "Shipping",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-09-04T10:43:42.606Z",
          "updated_at": "2019-09-04T10:43:42.606Z",
          "display_amount": "-$10.00"
        },
        {
          "id": 4,
          "source_type": "Spree::PromotionAction",
          "source_id": 1,
          "adjustable_type": "Spree::Shipment",
          "adjustable_id": 12,
          "amount": "-9.99",
          "label": "Shipping",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-09-04T10:43:42.598Z",
          "updated_at": "2019-09-04T10:43:42.598Z",
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
      "id": 6,
      "source_type": "Spree::Promotion",
      "source_id": 1,
      "adjustable_type": "Spree::Order",
      "adjustable_id": 10,
      "amount": "20.0",
      "label": "adj1",
      "promotion_code_id": null,
      "finalized": false,
      "eligible": true,
      "created_at": "2019-09-04T10:43:42.611Z",
      "updated_at": "2019-09-04T10:43:42.611Z",
      "display_amount": "$20.00"
    },
    {
      "id": 7,
      "source_type": "Spree::Promotion",
      "source_id": 1,
      "adjustable_type": "Spree::Order",
      "adjustable_id": 10,
      "amount": "30.0",
      "label": "adj2",
      "promotion_code_id": null,
      "finalized": false,
      "eligible": true,
      "created_at": "2019-09-04T10:43:42.614Z",
      "updated_at": "2019-09-04T10:43:42.614Z",
      "display_amount": "$30.00"
    }
  ],
  "permissions": {
    "can_update": false
  },
  "credit_cards": [
    {
      "id": 5,
      "month": "12",
      "year": "2020",
      "cc_type": null,
      "last_digits": "1111",
      "name": "Spree Commerce",
      "address": {
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
GET /api/orders/R678371903
Accept: application/json
Authorization: 31a3585dc79888d352da7694911c235245602314bcd55aee
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
X-Request-Id: d8245b09-61d3-49cc-8bdd-210372542720
X-Runtime: 0.017869
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
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/users/password`

#### Parameters


```json
user[email]=email29%40example.com
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
X-Request-Id: 8e230094-dcbb-4e92-91c3-30044003ae4f
X-Runtime: 0.032739
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
user[email]=email28%40example.com&user[password]=secret
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
Authorization: Bearer 9da8f3b39c12fc7d37a9ce40c225ebe23f446d2d00e530c5
ETag: W/&quot;eba53753184ba87dae72cb2f1a29ffad&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: fc37b34d-e2b1-4840-aef5-4029a4044fae
X-Runtime: 0.007725
Content-Length: 552
200 OK
```


```json
{
  "id": 29,
  "email": "email28@example.com",
  "persistence_token": null,
  "perishable_token": null,
  "last_request_at": null,
  "login": "email28@example.com",
  "ship_address_id": null,
  "bill_address_id": null,
  "created_at": "2019-09-04T10:43:45.467Z",
  "updated_at": "2019-09-04T10:43:45.470Z",
  "spree_api_key": "9da8f3b39c12fc7d37a9ce40c225ebe23f446d2d00e530c5",
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
X-Request-Id: 591e1860-0fd7-4b8f-8005-2625572711f7
X-Runtime: 0.004430
204 No Content
```




# Product Management

get product by slug

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
Date: Wed, 04 Sep 2019 10:43:46 GMT
Surrogate-Control: max-age=900
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;b8be097817a676124e7049db1e5d0b8e&quot;
X-Request-Id: 179b78c3-ec39-447e-b9c4-6fe62cde8fe5
X-Runtime: 0.046908
Content-Length: 937
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
      "id": 38,
      "name": "Product #38 - 5176",
      "description": "As seen on TV!",
      "available_on": "2018-09-04T10:43:46.875Z",
      "slug": "product-38-5176",
      "meta_description": null,
      "meta_keywords": null,
      "shipping_category_id": 24,
      "taxon_ids": [

      ],
      "total_on_hand": 0,
      "meta_title": null,
      "display_price": "$19.99",
      "trends": [

      ],
      "breadcrumb_taxons": {
      },
      "brand": null,
      "brand_slug": null,
      "brand_description": null,
      "has_variants": false,
      "master": {
        "id": 69,
        "name": "Product #38 - 5176",
        "sku": "SKU-69",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-38-5176",
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
GET /api/products/product-32-3498
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
Date: Wed, 04 Sep 2019 10:43:45 GMT
Surrogate-Control: max-age=900
Surrogate-Key: product_id=1
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;5aa36826b233eb47501b28ecb73ee2c1&quot;
X-Request-Id: dd5f997b-12ed-4b20-b4b3-43b34eff8454
X-Runtime: 0.123711
Content-Length: 855
200 OK
```


```json
{
  "id": 32,
  "name": "Product #32 - 3498",
  "description": "As seen on TV!",
  "available_on": "2018-09-04T10:43:45.745Z",
  "slug": "product-32-3498",
  "meta_description": null,
  "meta_keywords": null,
  "shipping_category_id": 20,
  "taxon_ids": [

  ],
  "total_on_hand": 0,
  "meta_title": null,
  "display_price": "$19.99",
  "trends": [

  ],
  "breadcrumb_taxons": {
  },
  "brand": null,
  "brand_slug": null,
  "brand_description": null,
  "has_variants": false,
  "master": {
    "id": 63,
    "name": "Product #32 - 3498",
    "sku": "SKU-63",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": true,
    "slug": "product-32-3498",
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
X-Request-Id: 271115bf-827c-4ed8-8173-5c16efe0e6dd
X-Runtime: 0.017247
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
ETag: W/&quot;beaa9a77a321bcd57a874dd2729a9022&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 095c0949-a121-4ef4-a685-195203ad03ab
X-Runtime: 0.067489
Content-Length: 1119
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
      "id": 34,
      "name": "Product #34 - 3359",
      "description": "As seen on TV!",
      "available_on": "2018-09-04T10:43:46.167Z",
      "slug": "product-34-3359",
      "meta_description": null,
      "meta_keywords": null,
      "shipping_category_id": 22,
      "taxon_ids": [
        4
      ],
      "total_on_hand": 0,
      "meta_title": null,
      "display_price": "$19.99",
      "trends": [

      ],
      "breadcrumb_taxons": {
      },
      "brand": "Ruby on Rails",
      "brand_slug": "ruby-on-rails",
      "brand_description": null,
      "has_variants": false,
      "master": {
        "id": 65,
        "name": "Product #34 - 3359",
        "sku": "SKU-65",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-34-3359",
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
            "name": "Ruby on Rails",
            "pretty_name": "Ruby on Rails",
            "permalink": "ruby-on-rails",
            "parent_id": null,
            "taxonomy_id": 2
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
GET /api/taxons/products?id=8
Host: example.org
Cookie: 
```

`GET /api/taxons/products`

#### Parameters


```json
id: 8
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
ETag: W/&quot;1340e81644160a7f25b2978e4eade525&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: ed1e43c0-9eb7-4a07-bf36-3ca60cb77e13
X-Runtime: 0.049978
Content-Length: 1119
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
      "id": 36,
      "name": "Product #36 - 2952",
      "description": "As seen on TV!",
      "available_on": "2018-09-04T10:43:46.555Z",
      "slug": "product-36-2952",
      "meta_description": null,
      "meta_keywords": null,
      "shipping_category_id": 23,
      "taxon_ids": [
        8
      ],
      "total_on_hand": 0,
      "meta_title": null,
      "display_price": "$19.99",
      "trends": [

      ],
      "breadcrumb_taxons": {
      },
      "brand": "Ruby on Rails",
      "brand_slug": "ruby-on-rails",
      "brand_description": null,
      "has_variants": false,
      "master": {
        "id": 67,
        "name": "Product #36 - 2952",
        "sku": "SKU-67",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-36-2952",
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
            "name": "Ruby on Rails",
            "pretty_name": "Ruby on Rails",
            "permalink": "ruby-on-rails",
            "parent_id": null,
            "taxonomy_id": 4
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
GET /api/returns/RA038446860
Authorization: Bearer c4fdf8ef880824701643bcd6d81222fcbe484b46e7be2773
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
ETag: W/&quot;de858737680d642e2061ca89291e1f25&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 8ba74441-4bd8-4f56-87eb-ff88210e935a
X-Runtime: 0.046145
Content-Length: 2727
200 OK
```


```json
{
  "id": 2,
  "number": "RA038446860",
  "state": "authorized",
  "order_id": 5,
  "memo": "Items were broken",
  "created_at": "2019-09-04T10:43:37.712Z",
  "updated_at": "2019-09-04T10:43:37.712Z",
  "reason": {
    "id": 3,
    "name": "Defect #3",
    "active": true,
    "mutable": true,
    "created_at": "2019-09-04T10:43:37.709Z",
    "updated_at": "2019-09-04T10:43:37.709Z",
    "mirakl_code": null
  },
  "order": {
    "id": 5,
    "number": "R585627684",
    "item_total": "10.0",
    "total": "110.0",
    "state": "complete",
    "adjustment_total": "0.0",
    "user_id": 5,
    "completed_at": "2019-09-04T10:43:37.645Z",
    "bill_address_id": 9,
    "ship_address_id": 10,
    "payment_total": "110.0",
    "shipment_state": "shipped",
    "payment_state": "paid",
    "email": "email5@example.com",
    "special_instructions": null,
    "created_at": "2019-09-04T10:43:37.586Z",
    "updated_at": "2019-09-04T10:43:37.694Z",
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
    "guest_token": "4dogvIPZ8rrK6HavmOcNRA",
    "canceled_at": null,
    "canceler_id": null,
    "store_id": 5,
    "approver_name": null,
    "frontend_viewable": true
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
  "return_items": [
    {
      "name": "Product #7 - 9158",
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
        "id": 3,
        "name": "Credit Card"
      },
      "source": {
        "id": 2,
        "month": "12",
        "year": "2020",
        "cc_type": null,
        "last_digits": "1111",
        "name": "Spree Commerce",
        "gateway_customer_profile_id": "BGS-430151",
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
Authorization: Bearer 77d14f841b9fd402f0a38307a181eec3f06350b9e6a3172e
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
ETag: W/&quot;e95f7946762ad10af83b4ccc261c5fff&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: a191564b-117a-4abb-a25e-6b4c4b09f59d
X-Runtime: 0.010342
Content-Length: 164
200 OK
```


```json
{
  "return_authorizations": [
    {
      "number": "RA720204325",
      "created_at": "2019-09-04T10:43:38.539Z",
      "return_amount": "10.0",
      "order_number": "R183633408",
      "state": "authorized"
    }
  ]
}
```



## returns a 200


### Request

#### Endpoint

```plaintext
GET /api/returns/RA086281054
Authorization: Bearer 969d13853892feea6399c5c4ac6c4f948b0a697803910558
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
ETag: W/&quot;4047a4634934999abe4cbbf6c05f986c&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 8cf4c0a6-dac5-4abb-8ef7-dbcd2c924993
X-Runtime: 0.079707
Content-Length: 2648
200 OK
```


```json
{
  "id": 1,
  "number": "RA086281054",
  "state": "authorized",
  "order_id": 4,
  "memo": "Items were broken",
  "created_at": "2019-09-04T10:43:37.241Z",
  "updated_at": "2019-09-04T10:43:37.241Z",
  "reason": {
    "id": 1,
    "name": "Defect #1",
    "active": true,
    "mutable": true,
    "created_at": "2019-09-04T10:43:37.230Z",
    "updated_at": "2019-09-04T10:43:37.230Z",
    "mirakl_code": null
  },
  "order": {
    "id": 4,
    "number": "R618174920",
    "item_total": "10.0",
    "total": "110.0",
    "state": "complete",
    "adjustment_total": "0.0",
    "user_id": 4,
    "completed_at": "2019-09-04T10:43:37.032Z",
    "bill_address_id": 7,
    "ship_address_id": 8,
    "payment_total": "110.0",
    "shipment_state": "shipped",
    "payment_state": "paid",
    "email": "email4@example.com",
    "special_instructions": null,
    "created_at": "2019-09-04T10:43:36.978Z",
    "updated_at": "2019-09-04T10:43:37.187Z",
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
    "guest_token": "nWRmDkMoOjhEQjZOgQGtNw",
    "canceled_at": null,
    "canceler_id": null,
    "store_id": 4,
    "approver_name": null,
    "frontend_viewable": true
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
  "return_items": [
    {
      "name": "Product #6 - 6421",
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
        "id": 1,
        "name": "Credit Card"
      },
      "source": {
        "id": 1,
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
GET /api/returns/RA827351163
Authorization: Bearer b5d83ebef5a02dd3b175d4e6654c529222eea1bd136c50d4
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
X-Request-Id: cb9363e2-5c88-45d1-ba16-c0957edf5a92
X-Runtime: 0.010865
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
Authorization: Bearer a1ea3e68108bec3bfc8d87888cd1d6994dded1474f2691bc
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
ETag: W/&quot;11ce9abf124e58734fb6aa6cb651d4c7&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: d68c4472-9f05-4cea-8929-58509c8f446d
X-Runtime: 0.038692
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
      "created_at": "2019-09-04T10:43:44.708Z"
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
user[email]=email20%40example.com&user[password]=secret
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
Authorization: Bearer f24ba1c251ddecb326e78db1b52b10d6d79f682e8ebd7de0
ETag: W/&quot;34612c4390f26af3630d5f49d25bd48a&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: d02551b7-fc00-4b84-8b5f-dff6a02a96df
X-Runtime: 0.009880
Content-Length: 552
200 OK
```


```json
{
  "id": 20,
  "email": "email20@example.com",
  "persistence_token": null,
  "perishable_token": null,
  "last_request_at": null,
  "login": "email20@example.com",
  "ship_address_id": null,
  "bill_address_id": null,
  "created_at": "2019-09-04T10:43:41.831Z",
  "updated_at": "2019-09-04T10:43:41.833Z",
  "spree_api_key": "f24ba1c251ddecb326e78db1b52b10d6d79f682e8ebd7de0",
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
Authorization: Bearer 2a06f26f4983fcf26402cde94341bb68e4563427dccebd61
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
Authorization: Bearer 2a06f26f4983fcf26402cde94341bb68e4563427dccebd61
ETag: W/&quot;7daf341c859380b7c7dd0f28f2dd8671&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 4ead1875-d6d6-4f15-82c2-476c588beaae
X-Runtime: 0.035544
Content-Length: 1505
200 OK
```


```json
{
  "email": "email21@example.com",
  "first_name": null,
  "last_name": null,
  "id": 21,
  "subscribed": null,
  "addresses": [
    {
      "id": 22,
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
      "default": true
    },
    {
      "id": 21,
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
      "default": false
    }
  ],
  "payment_sources": [
    {
      "id": 1,
      "default": true,
      "source": {
        "id": 3,
        "payment_type": "CreditCard",
        "token": null,
        "created_at": "2019-09-04T10:43:41.920Z",
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
        "id": 4,
        "payment_type": "ApplePayCard",
        "token": null,
        "created_at": "2019-09-04T10:43:41.955Z",
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
        "id": 5,
        "payment_type": "PayPalAccount",
        "token": null,
        "created_at": "2019-09-04T10:43:41.979Z",
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



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
Authorization: Bearer 8ed5615dc90523b0f60a8aa7ef931ace71c46052b92cbc09
ETag: W/&quot;79a764d87dbb604631972fa0f9261957&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: f64db353-7cab-4b53-acd3-47a240a9b931
X-Runtime: 0.024431
Content-Length: 156
201 Created
```


```json
{
  "id": 22,
  "email": "test@example.com",
  "created_at": "2019-09-04T10:43:42.033Z",
  "updated_at": "2019-09-04T10:43:42.035Z",
  "bill_address": null,
  "ship_address": null
}
```



# Variant



## Fetching a variant


### Request

#### Endpoint

```plaintext
GET /api/variants/62
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
ETag: W/&quot;a74f3b6ca5c61be778b4675382a9747e&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 6d0f2413-4eed-4479-b3d7-d2c7de44306b
X-Runtime: 0.127429
Content-Length: 1448
200 OK
```


```json
{
  "id": 62,
  "name": "Product #31 - 1723",
  "sku": "SKU-61",
  "weight": "0.0",
  "height": null,
  "width": null,
  "depth": null,
  "is_master": false,
  "slug": "product-31-1723",
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
      "id": 31,
      "name": "Size-31",
      "presentation": "S",
      "option_type_name": "foo-size-31",
      "option_type_id": 31,
      "option_type_presentation": "Size"
    }
  ],
  "images": [
    {
      "id": 1,
      "position": 1,
      "attachment_content_type": "image/jpeg",
      "attachment_file_name": "thinking-cat.jpg",
      "type": "Spree::Image",
      "attachment_updated_at": "2019-09-04T10:43:45.009Z",
      "attachment_width": 489,
      "attachment_height": 490,
      "alt": null,
      "viewable_type": "Spree::Variant",
      "viewable_id": 62,
      "mini_url": "/spree/products/1/mini/thinking-cat.jpg?1567593825",
      "small_url": "/spree/products/1/small/thinking-cat.jpg?1567593825",
      "product_url": "/spree/products/1/product/thinking-cat.jpg?1567593825",
      "large_url": "/spree/products/1/large/thinking-cat.jpg?1567593825"
    }
  ],
  "variant_properties": [

  ],
  "stock_items": [

  ],
  "prices": [
    {
      "id": 46,
      "vendor_id": 114,
      "price": "10.0",
      "original_price": "10.0",
      "discount_percent": 0.0,
      "total_on_hand": 0,
      "country_iso": null,
      "final_sale": false,
      "on_sale": false
    },
    {
      "id": 47,
      "vendor_id": 115,
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
Authorization: Bearer 44d588b766779ee8151f30e039e6ac6ad9599165f10d9543
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
ETag: W/&quot;0de4fa2aa64d63129d18ff61b5e7eb55&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 21407fb3-7578-4a40-a923-faa309120888
X-Runtime: 0.040435
Content-Length: 196
200 OK
```


```json
[
  {
    "id": 4,
    "user_id": 32,
    "payment_source_type": "SolidusPaypalBraintree::Source",
    "payment_source_id": 6,
    "default": false,
    "created_at": "2019-09-04T10:43:45.583Z",
    "updated_at": "2019-09-04T10:43:45.583Z"
  }
]
```



## Remove the payment from the user wallet


### Request

#### Endpoint

```plaintext
DELETE /api/wallet_payment_sources/5
Accept: application/json
Authorization: Bearer 6523411d6a373c00660a028ffb3be210b7d7b90e2f541c91
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
X-Request-Id: 98e25575-7a3a-44ef-8174-fd56ee67a958
X-Runtime: 0.017253
204 No Content
```




## Set a wallet payment source as the default user payment method


### Request

#### Endpoint

```plaintext
POST /api/wallet_payment_sources/6/default
Accept: application/json
Authorization: Bearer 9ce6678e4207eab8edd5b40a3bf06419b4532bfad3a5742a
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
X-Request-Id: 8f4b1a6a-cdd7-4435-ab9b-e0e3f5fe78b5
X-Runtime: 0.017828
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
Authorization: Bearer 09b538c4490856b14c5b039e87e4a5384f97432b68d28dd0
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/wished_products`

#### Parameters


```json
wished_product[wishlist_id]=2&wished_product[variant_id]=32&wished_product[quantity]=2&wished_product[remark]=Foo+bar
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
ETag: W/&quot;378ff5bc3ee166ebad6bf22c19990c8e&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: fc37f14b-a3f0-458a-ab63-f328b0724926
X-Runtime: 0.019100
Content-Length: 72
201 Created
```


```json
{
  "id": 4,
  "wishlist_id": 2,
  "variant_id": 32,
  "quantity": 2,
  "remark": "Foo bar"
}
```



## Delete a wished product


### Request

#### Endpoint

```plaintext
DELETE /api/wished_products/11
Accept: application/json
Authorization: Bearer 25f9defafa1c73805911793f03efca1e76c42615fed8c224
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
X-Request-Id: 43bbbb65-3191-4e92-a638-91330e3c7dc7
X-Runtime: 0.013485
204 No Content
```




## Get a single wished product


### Request

#### Endpoint

```plaintext
GET /api/wished_products/8
Accept: application/json
Authorization: Bearer ee2f8af3b8e08a9a7b8c4594c8571da9d5361e14ba7d74a9
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
ETag: W/&quot;873546a6d450e419f7de3814b37b908a&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 35759888-74e3-4532-8cfd-b401a12a4121
X-Runtime: 0.010066
Content-Length: 67
200 OK
```


```json
{
  "id": 8,
  "wishlist_id": 6,
  "variant_id": 40,
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
Authorization: Bearer e5d7d344547e5eb722f4091435c2b9b50df46a2add939a42
Host: example.org
Cookie: 
```

`GET /api/wished_products`

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
ETag: W/&quot;d4d892f60ade79cd699e63be7ba3ead0&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 03e461db-9c5e-4924-89fc-10458db7533c
X-Runtime: 0.014168
Content-Length: 292
200 OK
```


```json
{
  "wished_products": [
    {
      "id": 5,
      "wishlist_id": 3,
      "variant_id": 34,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 6,
      "wishlist_id": 4,
      "variant_id": 36,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 7,
      "wishlist_id": 5,
      "variant_id": 38,
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
PATCH /api/wished_products/1
Accept: application/json
Authorization: Bearer 169accaac348d85205bb98e5b864e8a782f7899b6a718397
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/wished_products/:id`

#### Parameters


```json
wished_product[wishlist_id]=1&wished_product[variant_id]=30&wished_product[quantity]=2&wished_product[remark]=Foo+bar
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
ETag: W/&quot;bf5bd281459fe943c6a30f540b1607eb&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: a1436a64-d236-4f0c-85d3-0aea466aff7a
X-Runtime: 0.038608
Content-Length: 72
200 OK
```


```json
{
  "id": 1,
  "wishlist_id": 1,
  "variant_id": 30,
  "quantity": 2,
  "remark": "Foo bar"
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
Authorization: Bearer 79fe7bf125b605da711d7499e974d9e9f4f45db86a1efc39
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/wishlists`

#### Parameters


```json
wishlist[name]&wishlist[user_id]=51&wishlist[is_default]=true&wishlist[is_public]=false
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
ETag: W/&quot;8efa3491b77375c2b67621c1522a2371&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: cf10fc8d-ed1c-46dd-b471-5c9793529f8a
X-Runtime: 0.019608
Content-Length: 100
201 Created
```


```json
{
  "id": 34,
  "user_id": 51,
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
DELETE /api/wishlists/20
Accept: application/json
Authorization: Bearer 7ec6628f037dc9bc9270446ff7695898e2e3e072e5ace78f
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
X-Request-Id: fd9886cd-2971-4855-94c2-dbf1ddb1c7a5
X-Runtime: 0.020441
204 No Content
```




## Get a single wishlist


### Request

#### Endpoint

```plaintext
GET /api/wishlists/19
Accept: application/json
Authorization: Bearer e9b18847e35d7b9b50ff96386b8a6445e300debf9fe64277
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
ETag: W/&quot;38cfc53bf05c284cb61e1d9d39c7441e&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 857c424e-d992-4743-98e2-62327af846a7
X-Runtime: 0.017304
Content-Length: 310
200 OK
```


```json
{
  "id": 19,
  "user_id": 47,
  "name": "Wishlist #18",
  "is_public": false,
  "is_default": true,
  "wished_products": [
    {
      "id": 17,
      "wishlist_id": 19,
      "variant_id": 77,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 18,
      "wishlist_id": 19,
      "variant_id": 79,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 19,
      "wishlist_id": 19,
      "variant_id": 81,
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
Authorization: Bearer 97d0deeb96bbc865b2ee8c4528c9193945ea65b8fa7bbdee
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
ETag: W/&quot;593ab16d78e23492c9d2c2cd911ebc04&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 409cadd0-2a9b-4f6c-960e-f5b9a73ce0f9
X-Runtime: 0.013785
Content-Length: 891
200 OK
```


```json
{
  "wishlists": [
    {
      "id": 9,
      "user_id": 36,
      "name": "Wishlist #8",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 10,
      "user_id": 37,
      "name": "Wishlist #9",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 11,
      "user_id": 38,
      "name": "Wishlist #10",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 12,
      "user_id": 39,
      "name": "Wishlist #11",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 13,
      "user_id": 40,
      "name": "Wishlist #12",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 14,
      "user_id": 41,
      "name": "Wishlist #13",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 15,
      "user_id": 42,
      "name": "Wishlist #14",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 16,
      "user_id": 43,
      "name": "Wishlist #15",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 17,
      "user_id": 44,
      "name": "Wishlist #16",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 18,
      "user_id": 45,
      "name": "Wishlist #17",
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
Authorization: Bearer 148b05f27f72abe67e780854b943a20031b6ffc20357d093
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
ETag: W/&quot;57ea9a9af1f04b7373d2dd52d5915b0b&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 22601a15-550f-48ce-bf3b-2dd2bca39699
X-Runtime: 0.013930
Content-Length: 310
200 OK
```


```json
{
  "id": 35,
  "user_id": 52,
  "name": "Wishlist #32",
  "is_public": false,
  "is_default": true,
  "wished_products": [
    {
      "id": 20,
      "wishlist_id": 35,
      "variant_id": 83,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 21,
      "wishlist_id": 35,
      "variant_id": 85,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 22,
      "wishlist_id": 35,
      "variant_id": 87,
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
Authorization: Bearer c5e99dc0b564837988ecd833afd51bfb1c4945f9b9c8787b
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
ETag: W/&quot;dc1ad3c827027641ea2b23fedaa32295&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: eb1a443d-93bd-4910-8a2d-cd2815247bf2
X-Runtime: 0.014606
Content-Length: 903
200 OK
```


```json
{
  "wishlists": [
    {
      "id": 24,
      "user_id": 50,
      "name": "Wishlist #22",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 25,
      "user_id": 50,
      "name": "Wishlist #23",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 26,
      "user_id": 50,
      "name": "Wishlist #24",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 27,
      "user_id": 50,
      "name": "Wishlist #25",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 28,
      "user_id": 50,
      "name": "Wishlist #26",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 29,
      "user_id": 50,
      "name": "Wishlist #27",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 30,
      "user_id": 50,
      "name": "Wishlist #28",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 31,
      "user_id": 50,
      "name": "Wishlist #29",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 32,
      "user_id": 50,
      "name": "Wishlist #30",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 33,
      "user_id": 50,
      "name": "Wishlist #31",
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
PATCH /api/wishlists/8
Accept: application/json
Authorization: Bearer be086af31246da54582d4089c4291d657b460a0995316395
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/wishlists/:id`

#### Parameters


```json
wishlist[name]=Another+Wishlist&wishlist[user_id]=35&wishlist[is_default]=true&wishlist[is_public]=false
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
ETag: W/&quot;a19160f3ff522e79c3550af779ede2b2&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 2b0c403c-f0e8-444b-a994-350aaff7f964
X-Runtime: 0.049962
Content-Length: 310
200 OK
```


```json
{
  "id": 8,
  "user_id": 35,
  "name": "Another Wishlist",
  "is_public": false,
  "is_default": true,
  "wished_products": [
    {
      "id": 14,
      "wishlist_id": 8,
      "variant_id": 71,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 15,
      "wishlist_id": 8,
      "variant_id": 73,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 16,
      "wishlist_id": 8,
      "variant_id": 75,
      "quantity": 1,
      "remark": null
    }
  ]
}
```



