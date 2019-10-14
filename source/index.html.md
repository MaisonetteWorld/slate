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
PUT /api/orders/M299671060/addresses/27
Accept: application/json
X-Spree-Order-Token: JKnJFC6aqFtJnFr5I2-2nA
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
ETag: W/&quot;6f1c7cb152d8e66d4e5daa05d41b5fc4&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 7821610b-0ff2-4536-8066-b74abe2585c7
X-Runtime: 0.047326
Vary: Origin
Content-Length: 507
200 OK
```


```json
{
  "id": 28,
  "firstname": "John the Tester",
  "lastname": null,
  "full_name": "John the Tester",
  "address1": "A Different Road",
  "address2": "Northwest",
  "city": "Herndon",
  "zipcode": "10025",
  "phone": "555-555-0199",
  "company": "Company",
  "alternative_phone": "555-555-0199",
  "country_id": 21,
  "country_iso": "US",
  "state_id": 21,
  "state_name": null,
  "state_text": "AL",
  "country": {
    "id": 21,
    "iso_name": "UNITED STATES",
    "iso": "US",
    "iso3": "USA",
    "name": "United States",
    "numcode": 840
  },
  "state": {
    "id": 21,
    "name": "Alabama",
    "abbr": "AL",
    "country_id": 21
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
X-Spree-Order-Token: Hybwb3gi-VkMp1_STucrDQ
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/braintree/transactions`

#### Parameters


```json
order_id=M656985563&payment_method_id=10&options[restart_checkout]=true&transaction[email]=maryellen.oga%40mckenziemcglynn.com&transaction[nonce]=fake-paypal-billing-agreement-nonce&transaction[phone]=555-555-0199&transaction[address_attributes][first_name]=John&transaction[address_attributes][last_name]=Stamm&transaction[address_attributes][address_line_1]=A+Different+Road&transaction[address_attributes][city]=Herndon&transaction[address_attributes][state_code]=AL&transaction[address_attributes][zip]=10011&transaction[address_attributes][country_code]=US&transaction[payment_type]=PayPalAccount
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
ETag: W/&quot;dddc9537cc5598d745550ab6bff6f297&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 2e7c9359-3cf1-49a6-be8f-20018e2e3b15
X-Runtime: 0.243614
Vary: Origin
Content-Length: 5052
200 OK
```


```json
{
  "id": 6,
  "number": "M656985563",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2019-10-14T08:43:32.954-04:00",
  "updated_at": "2019-10-14T08:43:33.206-04:00",
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
  "token": "Hybwb3gi-VkMp1_STucrDQ",
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
    "id": 14,
    "firstname": "John",
    "lastname": "Stamm",
    "full_name": "John Stamm",
    "address1": "A Different Road",
    "address2": null,
    "city": "Herndon",
    "zipcode": "10011",
    "phone": "555-555-0199",
    "company": null,
    "alternative_phone": null,
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
    "id": 14,
    "firstname": "John",
    "lastname": "Stamm",
    "full_name": "John Stamm",
    "address1": "A Different Road",
    "address2": null,
    "city": "Herndon",
    "zipcode": "10011",
    "phone": "555-555-0199",
    "company": null,
    "alternative_phone": null,
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
      "id": 6,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 18,
      "vendor_id": 47,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 18,
        "name": "Product #12 - 3748",
        "sku": "SKU-17",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-12-3748",
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
        "product_id": 12,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monograms": [

      ],
      "vendor_name": "Vendor #47",
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
      "created_at": "2019-10-14T08:43:33.069-04:00",
      "updated_at": "2019-10-14T08:43:33.069-04:00",
      "payment_method": {
        "id": 10,
        "name": "Braintree"
      },
      "source": {
        "id": 2,
        "payment_type": "PayPalAccount",
        "token": "bgx899",
        "created_at": "2019-10-14T08:43:33.068-04:00",
        "email": "jane.doe@paypal.com"
      }
    }
  ],
  "shipments": [
    {
      "id": 8,
      "tracking": null,
      "tracking_url": null,
      "number": "H03140671721",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M656985563",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 8,
          "name": "UPS Ground",
          "admin_name": null,
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 6,
          "shipping_method_code": "UPS_GROUND",
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
        "shipping_method_id": 6,
        "shipping_method_code": "UPS_GROUND",
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
              "id": 10,
              "name": "ShippingCategory #10"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 18,
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
      "delivery_estimation": "Oct 16"
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
X-Spree-Order-Token: v6rK_HDZgd-KRd4tbTmnBw
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/braintree/transactions`

#### Parameters


```json
order_id=M029856592&payment_method_id=9&options[restart_checkout]=true&transaction[email]=maryellen.oga%40mckenziemcglynn.com&transaction[nonce]=fake-apple-pay-visa-nonce&transaction[phone]=555-555-0199&transaction[address_attributes][first_name]=John&transaction[address_attributes][last_name]=Stamm&transaction[address_attributes][address_line_1]=A+Different+Road&transaction[address_attributes][city]=Herndon&transaction[address_attributes][state_code]=AL&transaction[address_attributes][zip]=10009&transaction[address_attributes][country_code]=US&transaction[payment_type]=ApplePayCard
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
ETag: W/&quot;9b202ac7c49370949af47ccf297d40aa&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: b71e04cb-80cc-4d18-85c2-4279b453d35a
X-Runtime: 0.428649
Vary: Origin
Content-Length: 5083
200 OK
```


```json
{
  "id": 5,
  "number": "M029856592",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2019-10-14T08:43:32.251-04:00",
  "updated_at": "2019-10-14T08:43:32.650-04:00",
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
  "token": "v6rK_HDZgd-KRd4tbTmnBw",
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
    "id": 11,
    "firstname": "John",
    "lastname": "Stamm",
    "full_name": "John Stamm",
    "address1": "A Different Road",
    "address2": null,
    "city": "Herndon",
    "zipcode": "10009",
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
    "id": 11,
    "firstname": "John",
    "lastname": "Stamm",
    "full_name": "John Stamm",
    "address1": "A Different Road",
    "address2": null,
    "city": "Herndon",
    "zipcode": "10009",
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
      "id": 5,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 16,
      "vendor_id": 42,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 16,
        "name": "Product #11 - 6931",
        "sku": "SKU-15",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-11-6931",
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
        "product_id": 11,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monograms": [

      ],
      "vendor_name": "Vendor #42",
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
      "created_at": "2019-10-14T08:43:32.437-04:00",
      "updated_at": "2019-10-14T08:43:32.437-04:00",
      "payment_method": {
        "id": 9,
        "name": "Braintree"
      },
      "source": {
        "id": 1,
        "payment_type": "ApplePayCard",
        "token": "cg7hsk",
        "created_at": "2019-10-14T08:43:32.435-04:00",
        "cc_type": "Apple Pay - Visa",
        "last_digits": "1881",
        "month": "12",
        "year": "2020"
      }
    }
  ],
  "shipments": [
    {
      "id": 6,
      "tracking": null,
      "tracking_url": null,
      "number": "H03757323846",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M029856592",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 6,
          "name": "UPS Ground",
          "admin_name": null,
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 5,
          "shipping_method_code": "UPS_GROUND",
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
        "shipping_method_id": 5,
        "shipping_method_code": "UPS_GROUND",
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
              "id": 9,
              "name": "ShippingCategory #9"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 16,
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
      "delivery_estimation": "Oct 16"
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
PUT /api/checkouts/M324342210/complete
Accept: application/json
X-Spree-Order-Token: E3VZ_ykau3gCuPPnNgTjbg
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
ETag: W/&quot;5a47eec42aa73aa2861f3518fb5f2be3&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 8e3c846f-b67b-44c0-8e99-631b56bc4955
X-Runtime: 2.390787
Vary: Origin
Content-Length: 5234
200 OK
```


```json
{
  "id": 11,
  "number": "M324342210",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "complete",
  "adjustment_total": "0.0",
  "user_id": 18,
  "created_at": "2019-10-14T08:43:35.931-04:00",
  "updated_at": "2019-10-14T08:43:38.431-04:00",
  "completed_at": "2019-10-14T08:43:38.431-04:00",
  "payment_total": "110.0",
  "shipment_state": "ready",
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
  "token": "E3VZ_ykau3gCuPPnNgTjbg",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 15,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    },
    {
      "id": 16,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
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
      "id": 11,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 28,
      "vendor_id": 72,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 28,
        "name": "Product #17 - 8477",
        "sku": "SKU-27",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-17-8477",
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
        "product_id": 17,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monograms": [

      ],
      "vendor_name": "Vendor #72",
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
      "payment_method_id": 15,
      "state": "completed",
      "avs_response": "M",
      "created_at": "2019-10-14T08:43:36.029-04:00",
      "updated_at": "2019-10-14T08:43:38.276-04:00",
      "payment_method": {
        "id": 15,
        "name": "Braintree"
      },
      "source": {
        "id": 4,
        "payment_type": "CreditCard",
        "token": "hbk69q",
        "created_at": "2019-10-14T08:43:36.028-04:00",
        "cc_type": "Visa",
        "last_digits": "1881",
        "month": "12",
        "year": "2020"
      }
    }
  ],
  "shipments": [
    {
      "id": 17,
      "tracking": "U10000",
      "tracking_url": null,
      "number": "H77452810108",
      "cost": "100.0",
      "shipped_at": null,
      "state": "ready",
      "order_id": "M324342210",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 17,
          "name": "UPS Ground",
          "admin_name": null,
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 11,
          "shipping_method_code": "UPS_GROUND",
          "is_flat_rate": false,
          "is_flat_rate_expedited": false,
          "is_free_shipping": false,
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 17,
        "name": "UPS Ground",
        "admin_name": null,
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 11,
        "shipping_method_code": "UPS_GROUND",
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
              "id": 15,
              "name": "ShippingCategory #15"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 28,
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
      "delivery_estimation": "Oct 16"
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
PATCH /api/checkouts/M686847178
Accept: application/json
X-Spree-Order-Token: p2HjKc7iGTqCSJ028M2gJQ
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=11&order[payment_attributes][][source_attributes][nonce]=fake-apple-pay-visa-nonce&order[payment_attributes][][source_attributes][payment_type]=ApplePayCard
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
ETag: W/&quot;821e0f366a4d0d81c77bde12dec083b5&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 281547c2-8667-4f83-82fb-82074af7b521
X-Runtime: 0.129214
Vary: Origin
Content-Length: 4608
200 OK
```


```json
{
  "id": 7,
  "number": "M686847178",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 14,
  "created_at": "2019-10-14T08:43:33.634-04:00",
  "updated_at": "2019-10-14T08:43:34.053-04:00",
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
  "gift_email": null,
  "gift_message": null,
  "is_gift": false,
  "display_item_total": "$10.00",
  "total_quantity": 1,
  "display_total": "$110.00",
  "display_ship_total": "$100.00",
  "display_tax_total": "$0.00",
  "token": "p2HjKc7iGTqCSJ028M2gJQ",
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
    "id": 15,
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
    "id": 16,
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
      "id": 7,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 20,
      "vendor_id": 52,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 20,
        "name": "Product #13 - 6679",
        "sku": "SKU-19",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-13-6679",
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
        "product_id": 13,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monograms": [

      ],
      "vendor_name": "Vendor #52",
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
      "number": "H21325851803",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M686847178",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 10,
          "name": "UPS Ground",
          "admin_name": null,
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 7,
          "shipping_method_code": "UPS_GROUND",
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
        "shipping_method_id": 7,
        "shipping_method_code": "UPS_GROUND",
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
              "id": 11,
              "name": "ShippingCategory #11"
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
      "international_shipping": false,
      "delivery_estimation": "Oct 16"
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
PATCH /api/checkouts/M500668288
Accept: application/json
X-Spree-Order-Token: eMYUpKADdavnWthHIp57oQ
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=12&order[payment_attributes][][source_attributes][nonce]=fake-paypal-billing-agreement-nonce&order[payment_attributes][][source_attributes][payment_type]=PayPalAccount
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
ETag: W/&quot;5cfc371c5182a51cfe4c7a61712263c7&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: e13dd201-22d8-4262-8d93-6dea7d9a25da
X-Runtime: 0.115442
Vary: Origin
Content-Length: 4604
200 OK
```


```json
{
  "id": 8,
  "number": "M500668288",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 15,
  "created_at": "2019-10-14T08:43:34.336-04:00",
  "updated_at": "2019-10-14T08:43:34.587-04:00",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "email15@example.com",
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
  "token": "eMYUpKADdavnWthHIp57oQ",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 12,
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
    "zipcode": "10015",
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
    "id": 18,
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
      "id": 8,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 22,
      "vendor_id": 57,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 22,
        "name": "Product #14 - 32",
        "sku": "SKU-21",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-14-32",
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
        "product_id": 14,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monograms": [

      ],
      "vendor_name": "Vendor #57",
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
      "number": "H45758211535",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M500668288",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 12,
          "name": "UPS Ground",
          "admin_name": null,
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 8,
          "shipping_method_code": "UPS_GROUND",
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
        "shipping_method_id": 8,
        "shipping_method_code": "UPS_GROUND",
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
              "id": 12,
              "name": "ShippingCategory #12"
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
      "international_shipping": false,
      "delivery_estimation": "Oct 16"
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
PATCH /api/checkouts/M534637689
Accept: application/json
X-Spree-Order-Token: YvLQNe-MF_JRq3msiY39pA
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=13&order[payment_attributes][][source_attributes][nonce]=fake-valid-visa-nonce&order[payment_attributes][][source_attributes][payment_type]=CreditCard
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
ETag: W/&quot;1212b7927dba2fe42f82a04b3c7238ef&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 20592abd-d063-4e0b-86cc-f9e98aaf8fa1
X-Runtime: 0.116065
Vary: Origin
Content-Length: 4608
200 OK
```


```json
{
  "id": 9,
  "number": "M534637689",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 16,
  "created_at": "2019-10-14T08:43:34.863-04:00",
  "updated_at": "2019-10-14T08:43:35.110-04:00",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "email16@example.com",
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
  "token": "YvLQNe-MF_JRq3msiY39pA",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "payment_methods": [
    {
      "id": 13,
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
    "zipcode": "10017",
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
    "id": 20,
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
      "id": 9,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 24,
      "vendor_id": 62,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 24,
        "name": "Product #15 - 5592",
        "sku": "SKU-23",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-15-5592",
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

        ],
        "product_id": 15,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monograms": [

      ],
      "vendor_name": "Vendor #62",
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
      "number": "H26848602867",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M534637689",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 14,
          "name": "UPS Ground",
          "admin_name": null,
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 9,
          "shipping_method_code": "UPS_GROUND",
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
        "shipping_method_id": 9,
        "shipping_method_code": "UPS_GROUND",
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
              "id": 13,
              "name": "ShippingCategory #13"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 24,
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
      "delivery_estimation": "Oct 16"
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
PATCH /api/checkouts/M037347023
Accept: application/json
X-Spree-Order-Token: iNjPtofA6qqJ9sfois4kFw
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=14&order[payment_attributes][][source_attributes][wallet_payment_source_id]=1
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
ETag: W/&quot;6b6b3af331cd5da2e10a094c90fa3e5e&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 253ece1a-97c1-47cf-8648-908293b64816
X-Runtime: 0.115866
Vary: Origin
Content-Length: 4618
200 OK
```


```json
{
  "id": 10,
  "number": "M037347023",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 17,
  "created_at": "2019-10-14T08:43:35.396-04:00",
  "updated_at": "2019-10-14T08:43:35.645-04:00",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "email17@example.com",
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
  "token": "iNjPtofA6qqJ9sfois4kFw",
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
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
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
    "zipcode": "10019",
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
      "id": 10,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 26,
      "vendor_id": 67,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 26,
        "name": "Product #16 - 8320",
        "sku": "SKU-25",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-16-8320",
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
        "product_id": 16,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monograms": [

      ],
      "vendor_name": "Vendor #67",
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
      "number": "H20661170700",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M037347023",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 16,
          "name": "UPS Ground",
          "admin_name": null,
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 10,
          "shipping_method_code": "UPS_GROUND",
          "is_flat_rate": false,
          "is_flat_rate_expedited": false,
          "is_free_shipping": false,
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 16,
        "name": "UPS Ground",
        "admin_name": null,
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 10,
        "shipping_method_code": "UPS_GROUND",
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
              "id": 14,
              "name": "ShippingCategory #14"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 26,
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
      "delivery_estimation": "Oct 16"
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
PUT /api/checkouts/M918075448
Accept: application/json
X-Spree-Order-Token: QVKVUo1Z0GPUoEzVLKkyBw
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PUT /api/checkouts/:id`

#### Parameters


```json
order[ship_address_attributes][id]&order[ship_address_attributes][firstname]=John&order[ship_address_attributes][lastname]&order[ship_address_attributes][address1]=10+Lovely+Street&order[ship_address_attributes][address2]=Northwest&order[ship_address_attributes][city]=Herndon&order[ship_address_attributes][zipcode]=10023&order[ship_address_attributes][phone]=555-555-0199&order[ship_address_attributes][state_name]&order[ship_address_attributes][alternative_phone]=555-555-0199&order[ship_address_attributes][company]=Company&order[ship_address_attributes][state_id]=16&order[ship_address_attributes][country_id]=16&order[ship_address_attributes][created_at]&order[ship_address_attributes][updated_at]&order[use_billing]=true&hold_state=true
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
ETag: W/&quot;39c1b4d9b75856d2fb8bab7b33234f77&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 93f9a5a1-9ba3-4d68-8cbb-d54fd2bbf4f0
X-Runtime: 0.112483
Vary: Origin
Content-Length: 4525
200 OK
```


```json
{
  "id": 12,
  "number": "M918075448",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "cart",
  "adjustment_total": "0.0",
  "user_id": 19,
  "created_at": "2019-10-14T08:43:39.435-04:00",
  "updated_at": "2019-10-14T08:43:39.561-04:00",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "email19@example.com",
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
  "token": "QVKVUo1Z0GPUoEzVLKkyBw",
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
    "id": 25,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "10 Lovely Street",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10023",
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
    "id": 25,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "10 Lovely Street",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10023",
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
      "id": 12,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 30,
      "vendor_id": 77,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 30,
        "name": "Product #18 - 4555",
        "sku": "SKU-29",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-18-4555",
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
        "product_id": 18,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monograms": [

      ],
      "vendor_name": "Vendor #77",
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
      "tracking": "U10000",
      "tracking_url": null,
      "number": "H25630477065",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M918075448",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 18,
          "name": "UPS Ground",
          "admin_name": null,
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 12,
          "shipping_method_code": "UPS_GROUND",
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
        "shipping_method_id": 12,
        "shipping_method_code": "UPS_GROUND",
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
              "id": 16,
              "name": "ShippingCategory #16"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 30,
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
      "delivery_estimation": "Oct 16"
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
POST /api/orders/M543104055/line_items
Accept: application/json
X-Spree-Order-Token: U-GLNz4vklle6njEadmY9g
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/:order_number/line_items`

#### Parameters


```json
line_item[variant_id]=76&line_item[options][vendor_id]=157
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
ETag: W/&quot;b899d8f7492a97bfc5794879d455a14c&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: e5f7816a-cfff-4793-8495-d4ecd8fea2fc
X-Runtime: 0.084180
Vary: Origin
Content-Length: 908
201 Created
```


```json
{
  "id": 23,
  "quantity": 1,
  "price": "19.99",
  "variant_id": 76,
  "vendor_id": 157,
  "single_display_amount": "$19.99",
  "display_amount": "$19.99",
  "total": "19.99",
  "on_sale": false,
  "final_sale": false,
  "backordered": null,
  "promotionable": true,
  "variant": {
    "id": 76,
    "name": "Product #41 - 1462",
    "sku": "SKU-75",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": false,
    "slug": "product-41-1462",
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
    "product_id": 41,
    "brand": null,
    "brand_slug": null,
    "brand_description": null
  },
  "monograms": [

  ],
  "vendor_name": "Vendor #157",
  "country_iso": null,
  "adjustments": [

  ]
}
```



## Deleting a line item


### Request

#### Endpoint

```plaintext
DELETE /api/orders/M672592209/line_items/24
Accept: application/json
X-Spree-Order-Token: f5R706CqjRXNRi6tT82uVA
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
X-Request-Id: 1dae1aff-2ea0-4f36-89d8-b51e547b0c97
X-Runtime: 0.082370
Vary: Origin
204 No Content
```




## Updating a line item


### Request

#### Endpoint

```plaintext
PUT /api/orders/M185435891/line_items/21
Accept: application/json
X-Spree-Order-Token: LeF_N4uDWgG3Uae40vtSDw
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
ETag: W/&quot;aab404096cb6aefaa2848f0c1abc7348&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: a9e6fe9d-8e94-4442-b1ca-9cc63376557c
X-Runtime: 0.096267
Vary: Origin
Content-Length: 905
200 OK
```


```json
{
  "id": 21,
  "quantity": 2,
  "price": "10.0",
  "variant_id": 70,
  "vendor_id": 146,
  "single_display_amount": "$10.00",
  "display_amount": "$20.00",
  "total": "20.0",
  "on_sale": false,
  "final_sale": false,
  "backordered": null,
  "promotionable": true,
  "variant": {
    "id": 70,
    "name": "Product #38 - 8193",
    "sku": "SKU-69",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": false,
    "slug": "product-38-8193",
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
    "product_id": 38,
    "brand": null,
    "brand_slug": null,
    "brand_description": null
  },
  "monograms": [

  ],
  "vendor_name": "Vendor #146",
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
Authorizat IO N: Bearer ae2079c3c17b055078eb92ecaee600937c3135fb1a8a3115
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/minis`

#### Parameters


```json
mini[name]=Winny&mini[user_id]=60&mini[birth_year]=2019&mini[birth_month]=1&mini[birth_day]=1
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
ETag: W/&quot;c3e117161f33d7a16ae40745ade6d261&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 34855cfe-e7e4-4725-95bc-10e3f6b0b001
X-Runtime: 0.007900
Vary: Origin
Content-Length: 122
201 Created
```


```json
{
  "id": 17,
  "user_id": 60,
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
DELETE /api/minis/18
Accept: application/json
Authorizat IO N: Bearer 27db1b1c4460a9b0ff997ed26edf04b458b6bf6761af623d
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
X-Request-Id: 7c2e42a4-becd-4eb6-8d2b-d411e3a6820d
X-Runtime: 0.006289
Vary: Origin
204 No Content
```




## Get a single mini


### Request

#### Endpoint

```plaintext
GET /api/minis/19
Accept: application/json
Authorizat IO N: Bearer 5ebc34af42d23f268e004af9bfee92ec39d7cc7c960889aa
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
ETag: W/&quot;73382adff1ed65bed3bf5d856e2458eb&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 3272a9de-19e4-4230-ad9a-ee51b6a3ca71
X-Runtime: 0.006736
Vary: Origin
Content-Length: 127
200 OK
```


```json
{
  "id": 19,
  "user_id": 62,
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
Authorizat IO N: Bearer 29031d40d4011f0832c7029465ae12bde78ba5dd853a8f0e
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
ETag: W/&quot;2ecca64627df104c5608f1ce295d8789&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: c4e7926c-652b-4649-99b2-144db3e5e25d
X-Runtime: 0.011339
Vary: Origin
Content-Length: 1352
200 OK
```


```json
{
  "minis": [
    {
      "id": 2,
      "user_id": 47,
      "name": "Mini",
      "birth_year": 2018,
      "birth_month": null,
      "birth_day": null,
      "gender_boy": true,
      "gender_girl": true
    },
    {
      "id": 3,
      "user_id": 48,
      "name": "Mini",
      "birth_year": 2018,
      "birth_month": null,
      "birth_day": null,
      "gender_boy": true,
      "gender_girl": true
    },
    {
      "id": 4,
      "user_id": 49,
      "name": "Mini",
      "birth_year": 2018,
      "birth_month": null,
      "birth_day": null,
      "gender_boy": true,
      "gender_girl": true
    },
    {
      "id": 5,
      "user_id": 50,
      "name": "Mini",
      "birth_year": 2018,
      "birth_month": null,
      "birth_day": null,
      "gender_boy": true,
      "gender_girl": true
    },
    {
      "id": 6,
      "user_id": 51,
      "name": "Mini",
      "birth_year": 2018,
      "birth_month": null,
      "birth_day": null,
      "gender_boy": true,
      "gender_girl": true
    },
    {
      "id": 7,
      "user_id": 52,
      "name": "Mini",
      "birth_year": 2018,
      "birth_month": null,
      "birth_day": null,
      "gender_boy": true,
      "gender_girl": true
    },
    {
      "id": 8,
      "user_id": 53,
      "name": "Mini",
      "birth_year": 2018,
      "birth_month": null,
      "birth_day": null,
      "gender_boy": true,
      "gender_girl": true
    },
    {
      "id": 9,
      "user_id": 54,
      "name": "Mini",
      "birth_year": 2018,
      "birth_month": null,
      "birth_day": null,
      "gender_boy": true,
      "gender_girl": true
    },
    {
      "id": 10,
      "user_id": 55,
      "name": "Mini",
      "birth_year": 2018,
      "birth_month": null,
      "birth_day": null,
      "gender_boy": true,
      "gender_girl": true
    },
    {
      "id": 11,
      "user_id": 56,
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
Authorizat IO N: Bearer fa7b909e1cd08c5887db86337f07c4923fc40d6ee670e1a0
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
ETag: W/&quot;eff55149176d6d08d00474f0ecb1a531&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: e0eda7ed-11bc-4037-9f53-beae249bd19a
X-Runtime: 0.008303
Vary: Origin
Content-Length: 334
200 OK
```


```json
{
  "minis": [
    {
      "id": 15,
      "user_id": 59,
      "name": "Mini",
      "birth_year": 2018,
      "birth_month": null,
      "birth_day": null,
      "gender_boy": true,
      "gender_girl": true
    },
    {
      "id": 16,
      "user_id": 59,
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
PATCH /api/minis/1
Accept: application/json
Authorizat IO N: Bearer 8a74d29463a9d78131e4a1dc2d68b67928473b3f7f2992f4
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
ETag: W/&quot;db4668c33788cd86cb8f80b7629c5e8a&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 8c8a4227-296d-4441-b2bb-b5f8fd255025
X-Runtime: 0.032567
Vary: Origin
Content-Length: 127
200 OK
```


```json
{
  "id": 1,
  "user_id": 46,
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
user_id&order_token&line_item[variant_id]=66&line_item[quantity]=2&line_item[vendor_id]=133
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
ETag: W/&quot;fa535bc950e2dd4ead6967a5f4bd279d&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: cf83d573-ae49-4217-b559-732497426de9
X-Runtime: 0.107487
Vary: Origin
Content-Length: 2422
200 OK
```


```json
{
  "id": 17,
  "number": "M312557001",
  "item_total": "39.98",
  "total": "39.98",
  "ship_total": "0.0",
  "state": "cart",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2019-10-14T08:43:45.162-04:00",
  "updated_at": "2019-10-14T08:43:45.195-04:00",
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
  "token": "WjbZb37pndj06faVoAPlBg",
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
      "id": 19,
      "quantity": 2,
      "price": "19.99",
      "variant_id": 66,
      "vendor_id": 133,
      "single_display_amount": "$19.99",
      "display_amount": "$39.98",
      "total": "39.98",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 66,
        "name": "Product #36 - 503",
        "sku": "SKU-65",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-36-503",
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
            "option_type_presentation": "Size",
            "position": 1
          }
        ],
        "images": [

        ],
        "product_id": 36,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monograms": [

      ],
      "vendor_name": "Vendor #133",
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
Authorizat IO N: Bearer 0d54d18aef751b115c6b8213144b4186b743e799fa1f1941
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
ETag: W/&quot;75b0c8787a635594c6cca25293e0d8bc&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 329f8ecd-9e8c-4927-bb94-dd04dd8de236
X-Runtime: 0.021261
Vary: Origin
Content-Length: 310
200 OK
```


```json
{
  "orders": [
    {
      "number": "M438451320",
      "completed_at": "2019-10-14T08:43:43.392-04:00",
      "total": "120.0",
      "state": "Complete",
      "shipment_state": "shipped",
      "shipments": [
        {
          "number": "H25321616052",
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
GET /api/orders/M255655315
Accept: application/json
Authorizat IO N: Bearer 241d429b37706040917702292f2925021f1910ec159d9ee7
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
ETag: W/&quot;5c0147743c48ba886a058ae695954afa&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 4460b330-2b3e-4097-a2b9-38044a94200f
X-Runtime: 0.143751
Vary: Origin
Content-Length: 9745
200 OK
```


```json
{
  "id": 16,
  "number": "M255655315",
  "item_total": "20.0",
  "total": "120.0",
  "ship_total": "100.0",
  "state": "complete",
  "adjustment_total": "0.0",
  "user_id": 67,
  "created_at": "2019-10-14T08:43:44.505-04:00",
  "updated_at": "2019-10-14T08:43:44.765-04:00",
  "completed_at": "2019-10-14T08:43:44.597-04:00",
  "payment_total": "120.0",
  "shipment_state": "shipped",
  "payment_state": "paid",
  "email": "email67@example.com",
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
  "token": "S7_j29O4wpLLCAMae-USCw",
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
      "name": "Credit Card",
      "partial_name": "gateway",
      "method_type": "gateway"
    },
    {
      "id": 25,
      "name": "Credit Card",
      "partial_name": "gateway",
      "method_type": "gateway"
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
    "zipcode": "10030",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 24,
    "country_iso": "US",
    "state_id": 24,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 24,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 24,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 24
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
    "zipcode": "10031",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 24,
    "country_iso": "US",
    "state_id": 24,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 24,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 24,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 24
    }
  },
  "line_items": [
    {
      "id": 17,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 60,
      "vendor_id": 126,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 60,
        "name": "Product #33 - 8929",
        "sku": "SKU-59",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-33-8929",
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
        "product_id": 33,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monograms": [

      ],
      "vendor_name": "Vendor #126",
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
          "created_at": "2019-10-14T08:43:44.737-04:00",
          "updated_at": "2019-10-14T08:43:44.749-04:00",
          "display_amount": "$2.00"
        },
        {
          "id": 11,
          "source_type": "Spree::PromotionAction",
          "source_id": 2,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 17,
          "amount": "5.0",
          "label": "foo",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-10-14T08:43:44.670-04:00",
          "updated_at": "2019-10-14T08:43:44.670-04:00",
          "display_amount": "$5.00"
        },
        {
          "id": 10,
          "source_type": "Spree::PromotionAction",
          "source_id": 2,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 17,
          "amount": "5.0",
          "label": "foo",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-10-14T08:43:44.661-04:00",
          "updated_at": "2019-10-14T08:43:44.661-04:00",
          "display_amount": "$5.00"
        }
      ]
    },
    {
      "id": 18,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 62,
      "vendor_id": 126,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 62,
        "name": "Product #34 - 2168",
        "sku": "SKU-61",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-34-2168",
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
        "product_id": 34,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monograms": [

      ],
      "vendor_name": "Vendor #126",
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
          "created_at": "2019-10-14T08:43:44.762-04:00",
          "updated_at": "2019-10-14T08:43:44.774-04:00",
          "display_amount": "$1.50"
        },
        {
          "id": 12,
          "source_type": "Spree::PromotionAction",
          "source_id": 2,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 18,
          "amount": "5.0",
          "label": "bar",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-10-14T08:43:44.680-04:00",
          "updated_at": "2019-10-14T08:43:44.680-04:00",
          "display_amount": "$5.00"
        }
      ]
    }
  ],
  "payments": [
    {
      "id": 10,
      "source_type": "Spree::CreditCard",
      "source_id": 7,
      "amount": "120.0",
      "display_amount": "$120.00",
      "payment_method_id": 24,
      "state": "completed",
      "avs_response": null,
      "created_at": "2019-10-14T08:43:44.609-04:00",
      "updated_at": "2019-10-14T08:43:44.609-04:00",
      "payment_method": {
        "id": 24,
        "name": "Credit Card"
      },
      "source": {
        "id": 7,
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
      "id": 21,
      "tracking": "U10000",
      "tracking_url": null,
      "number": "H66680831368",
      "cost": "100.0",
      "shipped_at": "2019-10-14T08:43:44.632-04:00",
      "state": "shipped",
      "order_id": "M255655315",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 21,
          "name": "UPS Ground",
          "admin_name": null,
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 15,
          "shipping_method_code": "UPS_GROUND",
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
        "shipping_method_id": 15,
        "shipping_method_code": "UPS_GROUND",
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
              "id": 17,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 23,
              "name": "ShippingCategory #23"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 60,
          "quantity": 1,
          "states": {
            "shipped": 1
          }
        },
        {
          "variant_id": 62,
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
          "source_id": 2,
          "adjustable_type": "Spree::Shipment",
          "adjustable_id": 21,
          "amount": "-10.0",
          "label": "Shipping",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-10-14T08:43:44.703-04:00",
          "updated_at": "2019-10-14T08:43:44.703-04:00",
          "display_amount": "-$10.00"
        },
        {
          "id": 13,
          "source_type": "Spree::PromotionAction",
          "source_id": 2,
          "adjustable_type": "Spree::Shipment",
          "adjustable_id": 21,
          "amount": "-9.99",
          "label": "Shipping",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-10-14T08:43:44.689-04:00",
          "updated_at": "2019-10-14T08:43:44.689-04:00",
          "display_amount": "-$9.99"
        }
      ],
      "stock_location_address": "NY Warehouse, Washington, AL",
      "country_iso": "US",
      "international_shipping": false,
      "delivery_estimation": "Oct 16"
    }
  ],
  "adjustments": [
    {
      "id": 15,
      "source_type": "Spree::Promotion",
      "source_id": 2,
      "adjustable_type": "Spree::Order",
      "adjustable_id": 16,
      "amount": "20.0",
      "label": "adj1",
      "promotion_code_id": null,
      "finalized": false,
      "eligible": true,
      "created_at": "2019-10-14T08:43:44.714-04:00",
      "updated_at": "2019-10-14T08:43:44.714-04:00",
      "display_amount": "$20.00"
    },
    {
      "id": 16,
      "source_type": "Spree::Promotion",
      "source_id": 2,
      "adjustable_type": "Spree::Order",
      "adjustable_id": 16,
      "amount": "30.0",
      "label": "adj2",
      "promotion_code_id": null,
      "finalized": false,
      "eligible": true,
      "created_at": "2019-10-14T08:43:44.719-04:00",
      "updated_at": "2019-10-14T08:43:44.719-04:00",
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
      "year": "2020",
      "cc_type": null,
      "last_digits": "1111",
      "name": "Spree Commerce",
      "address": {
        "id": 33,
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
        "country_id": 24,
        "country_iso": "US",
        "state_id": 24,
        "state_name": null,
        "state_text": "AL",
        "country": {
          "id": 24,
          "iso_name": "UNITED STATES",
          "iso": "US",
          "iso3": "USA",
          "name": "United States",
          "numcode": 840
        },
        "state": {
          "id": 24,
          "name": "Alabama",
          "abbr": "AL",
          "country_id": 24
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
GET /api/orders/M396263740
Accept: application/json
Authorizat IO N: 1a601d6f2e6c64913d1e35337a2fdadf18229b088f5e0c0a
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
X-Request-Id: 2a49f655-3778-4474-8e1a-9d7b0ce79f67
X-Runtime: 0.010650
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
Content-Type: text/html
Cache-Control: no-cache
X-Request-Id: 1af46d30-b464-47a4-8a2f-f28bd5326f75
X-Runtime: 0.002703
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
Authorization: Bearer b150e05015fc0a4877b42afd2e61a6dbcc2efd298ac40127
ETag: W/&quot;eab1799facd23cc338175e26d958430a&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 3cde1c64-ed69-4843-928e-f3d1b407e194
X-Runtime: 0.013081
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
  "created_at": "2019-10-14T08:43:41.820-04:00",
  "updated_at": "2019-10-14T08:43:41.822-04:00",
  "spree_api_key": "b150e05015fc0a4877b42afd2e61a6dbcc2efd298ac40127",
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
X-Request-Id: 3fff8273-e57a-4172-ac6c-bc9eabd8773e
X-Runtime: 0.022393
Vary: Origin
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
Date: Mon, 14 Oct 2019 12:43:31 GMT
Surrogate-Control: max-age=900
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;0adbeca34f0059fb247b2df1cb1e502a&quot;
X-Request-Id: e3888788-cafd-4155-883e-54026e0aa857
X-Runtime: 0.049032
Vary: Origin
Content-Length: 911
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
      "id": 6,
      "name": "Product #6 - 9050",
      "description": "As seen on TV!",
      "available_on": "2018-10-14T08:43:31.391-04:00",
      "slug": "product-6-9050",
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
        "id": 10,
        "name": "Product #6 - 9050",
        "sku": "SKU-10",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-6-9050",
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
GET /api/products/product-5-4297
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
Date: Mon, 14 Oct 2019 12:43:31 GMT
Surrogate-Control: max-age=900
Surrogate-Key: product_id=1
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;ba95318fb3b32f2a9b47c6f66d4c24db&quot;
X-Request-Id: 1b66575a-face-408d-b87b-a001b1fb4322
X-Runtime: 0.094210
Vary: Origin
Content-Length: 1510
200 OK
```


```json
{
  "id": 5,
  "name": "Product #5 - 4297",
  "description": "As seen on TV!",
  "available_on": "2018-10-14T08:43:31.172-04:00",
  "slug": "product-5-4297",
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
    {
      "id": 2,
      "name": "Clothing",
      "taxonomy_id": 1,
      "created_at": "2019-10-14T08:43:31.098-04:00",
      "url": "/category/clothing",
      "position": 1
    },
    {
      "id": 3,
      "name": "Girl",
      "taxonomy_id": 1,
      "created_at": "2019-10-14T08:43:31.130-04:00",
      "url": "/category/clothing/girl",
      "position": 2
    },
    {
      "id": 4,
      "name": "Dresses",
      "taxonomy_id": 1,
      "created_at": "2019-10-14T08:43:31.151-04:00",
      "url": "/category/clothing/girl/dresses",
      "position": 3
    }
  ],
  "brand": null,
  "brand_slug": null,
  "brand_description": null,
  "has_variants": false,
  "master": {
    "id": 9,
    "name": "Product #5 - 4297",
    "sku": "SKU-9",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": true,
    "slug": "product-5-4297",
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
        "name": "Dresses",
        "pretty_name": "Category -> Clothing -> Girl -> Dresses",
        "permalink": "category/clothing/girl/dresses",
        "parent_id": 3,
        "taxonomy_id": 1,
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
X-Request-Id: e776de95-6601-44ce-ba45-5357d3f90eab
X-Runtime: 0.011336
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
GET /api/taxons/products?id=7
Host: example.org
Cookie: 
```

`GET /api/taxons/products`

#### Parameters


```json
id: 7
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
ETag: W/&quot;751cc6345164420be4ed047c565b87d7&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: e4c95717-3a77-4225-8ada-e02d9e263c24
X-Runtime: 0.051589
Vary: Origin
Content-Length: 1198
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
      "id": 8,
      "name": "Product #8 - 9249",
      "description": "As seen on TV!",
      "available_on": "2018-10-14T08:43:31.660-04:00",
      "slug": "product-8-9249",
      "meta_description": null,
      "meta_keywords": null,
      "taxon_ids": [
        7
      ],
      "total_on_hand": 0,
      "meta_title": null,
      "display_price": "$19.99",
      "trends": [

      ],
      "breadcrumb_taxons": [

      ],
      "brand": "Ruby on Rails - 1",
      "brand_slug": "ruby-on-rails-1",
      "brand_description": null,
      "has_variants": false,
      "master": {
        "id": 12,
        "name": "Product #8 - 9249",
        "sku": "SKU-12",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-8-9249",
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
          "taxon_id": 7,
          "position": 1,
          "taxon": {
            "id": 7,
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
ETag: W/&quot;7b6b5bc946f14514712a59ba0956e326&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: ba16b1db-e305-415c-89c5-da385365c56e
X-Runtime: 0.041262
Vary: Origin
Content-Length: 1206
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
      "id": 10,
      "name": "Product #10 - 8940",
      "description": "As seen on TV!",
      "available_on": "2018-10-14T08:43:31.931-04:00",
      "slug": "product-10-8940",
      "meta_description": null,
      "meta_keywords": null,
      "taxon_ids": [
        10
      ],
      "total_on_hand": 0,
      "meta_title": null,
      "display_price": "$19.99",
      "trends": [

      ],
      "breadcrumb_taxons": [

      ],
      "brand": "Ruby on Rails - 2",
      "brand_slug": "ruby-on-rails-2",
      "brand_description": null,
      "has_variants": false,
      "master": {
        "id": 14,
        "name": "Product #10 - 8940",
        "sku": "SKU-14",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-10-8940",
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
            "name": "Ruby on Rails - 2",
            "pretty_name": "Ruby on Rails - 2",
            "permalink": "ruby-on-rails-2",
            "parent_id": null,
            "taxonomy_id": 3,
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

Get user return authorizations

## Can get another user&#39;s return authorization


### Request

#### Endpoint

```plaintext
GET /api/returns/RA372066772
Authorizat IO N: Bearer 4acb69ef6d02280083158653183b4a3e4071eae2c03fd433
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
ETag: W/&quot;a9bdc0ec2c27b6ec6413c7fd5821d019&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 478f039b-1824-4c02-ba90-11c558ec58da
X-Runtime: 0.035367
Vary: Origin
Content-Length: 2814
200 OK
```


```json
{
  "id": 3,
  "number": "RA372066772",
  "state": "authorized",
  "order_id": 3,
  "memo": "Items were broken",
  "created_at": "2019-10-14T08:43:30.611-04:00",
  "updated_at": "2019-10-14T08:43:30.611-04:00",
  "reason": {
    "id": 5,
    "name": "Defect #5",
    "active": true,
    "mutable": true,
    "created_at": "2019-10-14T08:43:30.608-04:00",
    "updated_at": "2019-10-14T08:43:30.608-04:00",
    "mirakl_code": null
  },
  "order": {
    "id": 3,
    "number": "M611255706",
    "item_total": "10.0",
    "total": "110.0",
    "state": "complete",
    "adjustment_total": "0.0",
    "user_id": 3,
    "completed_at": "2019-10-14T08:43:30.524-04:00",
    "bill_address_id": 5,
    "ship_address_id": 6,
    "payment_total": "110.0",
    "shipment_state": "shipped",
    "payment_state": "paid",
    "email": "email3@example.com",
    "special_instructions": null,
    "created_at": "2019-10-14T08:43:30.443-04:00",
    "updated_at": "2019-10-14T08:43:30.586-04:00",
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
    "guest_token": "2LKHCLSlQl-Kp5LEemyXnQ",
    "canceled_at": null,
    "canceler_id": null,
    "store_id": 3,
    "approver_name": null,
    "frontend_viewable": true,
    "is_gift": false,
    "gift_email": null,
    "gift_message": null
  },
  "ship_address": {
    "id": 6,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
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
  },
  "bill_address": {
    "id": 5,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "PO Box 1337",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10005",
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
  "return_items": [
    {
      "name": "Product #3 - 1833",
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
        "id": 5,
        "name": "Credit Card"
      },
      "source": {
        "id": 3,
        "month": "12",
        "year": "2020",
        "cc_type": null,
        "last_digits": "1111",
        "name": "Spree Commerce",
        "gateway_customer_profile_id": "BGS-345200",
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
Authorizat IO N: Bearer 68697faefb84b51b797424987d607a65fa83a85ed35ac607
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
ETag: W/&quot;d123817de25bc544e88f0585eab430ef&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 100f907e-4a2f-41fc-a15b-2497f24eceb1
X-Runtime: 0.121724
Vary: Origin
Content-Length: 169
200 OK
```


```json
{
  "return_authorizations": [
    {
      "number": "RA864582102",
      "created_at": "2019-10-14T08:43:29.614-04:00",
      "return_amount": "10.0",
      "order_number": "M193233570",
      "state": "authorized"
    }
  ]
}
```



## returns a 200


### Request

#### Endpoint

```plaintext
GET /api/returns/RA725703134
Authorizat IO N: Bearer f89841b240ab93a6ccb24e35ae733f7e06add11c3feb449d
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
ETag: W/&quot;9a3bca3e9af194e9f45771e98f476c51&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: f7b3ce76-2190-4258-98af-1d9c6ea73d6e
X-Runtime: 0.062114
Vary: Origin
Content-Length: 2737
200 OK
```


```json
{
  "id": 2,
  "number": "RA725703134",
  "state": "authorized",
  "order_id": 2,
  "memo": "Items were broken",
  "created_at": "2019-10-14T08:43:30.168-04:00",
  "updated_at": "2019-10-14T08:43:30.168-04:00",
  "reason": {
    "id": 3,
    "name": "Defect #3",
    "active": true,
    "mutable": true,
    "created_at": "2019-10-14T08:43:30.164-04:00",
    "updated_at": "2019-10-14T08:43:30.164-04:00",
    "mirakl_code": null
  },
  "order": {
    "id": 2,
    "number": "M325013406",
    "item_total": "10.0",
    "total": "110.0",
    "state": "complete",
    "adjustment_total": "0.0",
    "user_id": 2,
    "completed_at": "2019-10-14T08:43:30.092-04:00",
    "bill_address_id": 3,
    "ship_address_id": 4,
    "payment_total": "110.0",
    "shipment_state": "shipped",
    "payment_state": "paid",
    "email": "email2@example.com",
    "special_instructions": null,
    "created_at": "2019-10-14T08:43:30.014-04:00",
    "updated_at": "2019-10-14T08:43:30.141-04:00",
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
    "guest_token": "NFwfNmw2goxJshgW4SgL2g",
    "canceled_at": null,
    "canceler_id": null,
    "store_id": 2,
    "approver_name": null,
    "frontend_viewable": true,
    "is_gift": false,
    "gift_email": null,
    "gift_message": null
  },
  "ship_address": {
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
  "bill_address": {
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
  "return_items": [
    {
      "name": "Product #2 - 2353",
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
GET /api/returns/RA243614220
Authorizat IO N: Bearer f68816b144667eb718e6b54c8ba7bc1c912ac2c992f99634
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
X-Request-Id: c67c27b2-32c7-4904-9d6c-c877b388539c
X-Runtime: 0.010483
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
Authorizat IO N: Bearer 571f1de20e2a6c36c0770514a93ab41dcce56367a230bb0a
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
ETag: W/&quot;bd5d5de5195c1fdcd1b324e8c16eba56&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 568828ab-45ba-49e8-8eef-b2056b8bc492
X-Runtime: 0.032800
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
      "created_at": "2019-10-14T08:43:41.727-04:00"
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
Authorizat IO N: Bearer bc457bd8760b3b8cebbc98102df7446d9071574be506e2e4
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/subscribers`

#### Parameters


```json
subscriber[email]=colette.johnson%40kunde.com&subscriber[user_id]=10&subscriber[first_name]=Rhiannon&subscriber[last_name]=Walsh&subscriber[status]=subscribed
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
ETag: W/&quot;a80656cdecd5f597069a2741578d2125&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: a43b1c2f-12b7-455c-8f90-140369b73b3b
X-Runtime: 0.008376
Vary: Origin
Content-Length: 180
201 Created
```


```json
{
  "id": 2,
  "user_id": 10,
  "email": "colette.johnson@kunde.com",
  "first_name": "Rhiannon",
  "last_name": "Walsh",
  "source": "",
  "status": "subscribed",
  "created_at": "2019-10-14T08:43:33.361-04:00"
}
```



## Delete a subscriber


### Request

#### Endpoint

```plaintext
DELETE /api/subscribers/7
Accept: application/json
Authorizat IO N: Bearer 88cd30125625b4ed63a03fbc9d8a6b79e79da0f0aedad52f
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
X-Request-Id: c57b589c-6b9a-4ca0-8a4c-6e82f78987bd
X-Runtime: 0.006768
Vary: Origin
204 No Content
```




## Get a single subscriber by id


### Request

#### Endpoint

```plaintext
GET /api/subscribers/1
Accept: application/json
Authorizat IO N: Bearer ed659d4d8ab81af6a68fea210a4eb936ca83457b73493471
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
ETag: W/&quot;18a42e6a795a4f2556d6e6982fa1697b&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 4717514c-2513-4cb1-9faf-b919c489e16d
X-Runtime: 0.031978
Vary: Origin
Content-Length: 180
200 OK
```


```json
{
  "id": 1,
  "user_id": 9,
  "email": "isobel_nikolaus@stark.co.uk",
  "first_name": "Gennie",
  "last_name": "Murphy",
  "source": "",
  "status": "subscribed",
  "created_at": "2019-10-14T08:43:33.312-04:00"
}
```



## Get all subscribers


### Request

#### Endpoint

```plaintext
GET /api/subscribers
Accept: application/json
Authorizat IO N: Bearer 87ec7824ccfc741f3a909dcd8c615f911e134aed55792c30
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
ETag: W/&quot;771069d67a4b3f8c290cc3ab59cb4689&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: b14de63d-e313-40ba-b7b4-d5be95bc537a
X-Runtime: 0.010750
Vary: Origin
Content-Length: 639
200 OK
```


```json
{
  "subscribers": [
    {
      "id": 3,
      "user_id": null,
      "email": "dayna_beahan@gulgowski.com",
      "first_name": "Noe",
      "last_name": "Kuphal",
      "source": "",
      "status": "subscribed",
      "created_at": "2019-10-14T08:43:33.367-04:00"
    },
    {
      "id": 4,
      "user_id": null,
      "email": "lindsey_johnson@kutchblanda.ca",
      "first_name": "Suk",
      "last_name": "Medhurst",
      "source": "",
      "status": "subscribed",
      "created_at": "2019-10-14T08:43:33.368-04:00"
    },
    {
      "id": 5,
      "user_id": null,
      "email": "bernardo.fisher@feilnitzsche.info",
      "first_name": "Lexie",
      "last_name": "Graham",
      "source": "",
      "status": "subscribed",
      "created_at": "2019-10-14T08:43:33.369-04:00"
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
PATCH /api/subscribers/6
Accept: application/json
Authorizat IO N: Bearer 85aacb3230ef66dbe581bf7e3ca15b4a96ec69896aa4c9dd
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
ETag: W/&quot;bf4ad6b0286d18c88e7d98f9a8cdedf5&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 0ad4d869-4a18-47cb-b18d-568eefd13422
X-Runtime: 0.008730
Vary: Origin
Content-Length: 174
200 OK
```


```json
{
  "id": 6,
  "user_id": 12,
  "email": "deangelo_smith@dooley.us",
  "first_name": "Dee",
  "last_name": "Oga",
  "source": "",
  "status": "unsubscribed",
  "created_at": "2019-10-14T08:43:33.414-04:00"
}
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
X-Request-Id: c48008d9-3d08-4463-a3ea-f0dda4f27662
X-Runtime: 0.029237
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
X-Request-Id: 178cc0a5-892d-4660-9027-b650ca47975f
X-Runtime: 0.011312
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
X-Request-Id: 9153a957-31da-4f20-9037-ee150b4922b7
X-Runtime: 0.024216
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
ETag: W/&quot;df281eb0cd064950276e4476d4c86093&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: ee808bac-b29e-4f62-a289-7123b8a750da
X-Runtime: 0.006410
Vary: Origin
Content-Length: 150
200 OK
```


```json
[
  {
    "id": 45,
    "name": "Kids",
    "navigation_url": "/navigation/kids",
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

Subscribe a user. If the user does not already have an associated subscriber, this will create one.                 If the user is already in a subscribed state, this will not change any records

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
Authorization: Bearer 5c2bf281b89563bac79b284bc2da1a285fed7ab9cbbec2e6
ETag: W/&quot;f5b16eba6155a9fb0ee4c1200eabe5e1&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 24134f01-e036-4b05-bf52-082d7c0e108c
X-Runtime: 0.007379
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
  "created_at": "2019-10-14T08:43:45.323-04:00",
  "updated_at": "2019-10-14T08:43:45.325-04:00",
  "spree_api_key": "5c2bf281b89563bac79b284bc2da1a285fed7ab9cbbec2e6",
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
X-Spree-Order-Token: jMp0eMjpiTgsk-KK8nKqQw
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/users/login`

#### Parameters


```json
user[email]=email71%40example.com&user[password]=secret&order_number=M359393373
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
Authorization: Bearer f65a4d8e70cb1d589ec2749c03e34df562a393d77e027430
ETag: W/&quot;8048cda4537c6e2ba30e58668bdfaad5&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 820cdf42-dc38-4443-a1f9-6555d5364ad3
X-Runtime: 0.011051
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
  "created_at": "2019-10-14T08:43:45.338-04:00",
  "updated_at": "2019-10-14T08:43:45.340-04:00",
  "spree_api_key": "f65a4d8e70cb1d589ec2749c03e34df562a393d77e027430",
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
Authorizat IO N: Bearer c2362103097102b94e958f53080537d976b5e8531c865d24
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
Authorization: Bearer c2362103097102b94e958f53080537d976b5e8531c865d24
ETag: W/&quot;e2de4bd2021cca334a742899ec4d21ae&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: f1bbbe4d-4950-4d15-bd79-e52b72dc6df9
X-Runtime: 0.019949
Vary: Origin
Content-Length: 1522
200 OK
```


```json
{
  "email": "email72@example.com",
  "first_name": null,
  "last_name": null,
  "id": 72,
  "subscribed": false,
  "addresses": [
    {
      "id": 38,
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
      "id": 37,
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
        "id": 8,
        "payment_type": "CreditCard",
        "token": null,
        "created_at": "2019-10-14T08:43:45.624-04:00",
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
        "created_at": "2019-10-14T08:43:45.638-04:00",
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
        "created_at": "2019-10-14T08:43:45.651-04:00",
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
Authorization: Bearer 959c1fab1e3f69544ac220c912739d29125311781f583610
ETag: W/&quot;b903b889c6bd3d496c54bbe76875850e&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: c78810e1-a348-4207-9085-d6067df4ba29
X-Runtime: 0.012790
Vary: Origin
Content-Length: 185
201 Created
```


```json
{
  "id": 73,
  "email": "test@example.com",
  "created_at": "2019-10-14T08:43:45.684-04:00",
  "updated_at": "2019-10-14T08:43:45.686-04:00",
  "subscribed": false,
  "bill_address": null,
  "ship_address": null
}
```



## Subscribe a user


### Request

#### Endpoint

```plaintext
PUT /api/users/68/subscribe
Authorizat IO N: Bearer 956e0036262691f17c6aa9ed84f135e7941b0dc5d987a6ce
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
Authorization: Bearer 956e0036262691f17c6aa9ed84f135e7941b0dc5d987a6ce
ETag: W/&quot;0d5a4b1662adf3c4fb67f90592f98af7&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: ccd49708-6b9c-4030-981d-6d1c99263aa3
X-Runtime: 0.025436
Vary: Origin
Content-Length: 187
200 OK
```


```json
{
  "id": 68,
  "email": "email68@example.com",
  "created_at": "2019-10-14T08:43:45.264-04:00",
  "updated_at": "2019-10-14T08:43:45.266-04:00",
  "subscribed": true,
  "bill_address": null,
  "ship_address": null
}
```



## Unsubscribe a user


### Request

#### Endpoint

```plaintext
PUT /api/users/69/unsubscribe
Authorizat IO N: Bearer 9fc8f2a4792923861a332eb8308645e8e1623c1e1b01ef8d
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
Authorization: Bearer 9fc8f2a4792923861a332eb8308645e8e1623c1e1b01ef8d
ETag: W/&quot;05143347250a57ef4cd0092a307ea986&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: a8e18366-69d7-45b5-93ad-989bd4e3c7e2
X-Runtime: 0.010825
Vary: Origin
Content-Length: 188
200 OK
```


```json
{
  "id": 69,
  "email": "email69@example.com",
  "created_at": "2019-10-14T08:43:45.302-04:00",
  "updated_at": "2019-10-14T08:43:45.304-04:00",
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
GET /api/variants/32
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
ETag: W/&quot;e94608a16df86a13dd1caba22e3a6d2c&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 05127c95-bf0e-45e1-8d1a-8ce1360ee746
X-Runtime: 0.102143
Vary: Origin
Content-Length: 2098
200 OK
```


```json
{
  "id": 32,
  "name": "Product #19 - 3657",
  "sku": "SKU-31",
  "weight": "0.0",
  "height": null,
  "width": null,
  "depth": null,
  "is_master": false,
  "slug": "product-19-3657",
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
    {
      "id": 1,
      "position": 1,
      "attachment_content_type": "image/jpeg",
      "attachment_file_name": "thinking-cat.jpg",
      "type": "Spree::Image",
      "attachment_updated_at": "2019-10-14T08:43:39.833-04:00",
      "attachment_width": 489,
      "attachment_height": 490,
      "alt": null,
      "viewable_type": "Spree::Variant",
      "viewable_id": 32,
      "mini_url": "http://localhost:3000/spree/images/attachments/000/000/001/mini/thinking-cat.jpg?1571057019",
      "small_url": "http://localhost:3000/spree/images/attachments/000/000/001/small/thinking-cat.jpg?1571057019",
      "product_url": "http://localhost:3000/spree/images/attachments/000/000/001/product/thinking-cat.jpg?1571057019",
      "large_url": "http://localhost:3000/spree/images/attachments/000/000/001/large/thinking-cat.jpg?1571057019"
    }
  ],
  "variant_properties": [

  ],
  "stock_items": [

  ],
  "prices": [
    {
      "id": 32,
      "vendor_id": 84,
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
      "id": 33,
      "vendor_id": 85,
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
Authorizat IO N: Bearer 202629a99f08a2a622397605f121d4f50b70c4cb1ef0f9f0
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
ETag: W/&quot;ab78ddc4227887445e12f2ccd71ac228&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 1b1c7d74-a417-4e5d-8c06-43dd59240dcc
X-Runtime: 0.033035
Vary: Origin
Content-Length: 206
200 OK
```


```json
[
  {
    "id": 3,
    "user_id": 43,
    "payment_source_type": "SolidusPaypalBraintree::Source",
    "payment_source_id": 5,
    "default": false,
    "created_at": "2019-10-14T08:43:41.869-04:00",
    "updated_at": "2019-10-14T08:43:41.869-04:00"
  }
]
```



## Remove the payment from the user wallet


### Request

#### Endpoint

```plaintext
DELETE /api/wallet_payment_sources/5
Accept: application/json
Authorizat IO N: Bearer 6815aefd9cd4a79542b17e82779ce0896fab7faa35213b44
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
X-Request-Id: fd8ca736-9668-4d18-9a8b-877421d54b8a
X-Runtime: 0.011587
Vary: Origin
204 No Content
```




## Set a wallet payment source as the default user payment method


### Request

#### Endpoint

```plaintext
POST /api/wallet_payment_sources/4/default
Accept: application/json
Authorizat IO N: Bearer 0840d6dab4376e230edeb6f0759ce2e643d027d7b37da4cb
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
X-Request-Id: 4b32375a-1652-40ec-b508-03dd7b768229
X-Runtime: 0.008713
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
Authorizat IO N: Bearer 53769babde0a1f8b04eabc4c06625bc93195eb9296ceb3c9
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/wished_products`

#### Parameters


```json
wished_product[wishlist_id]=31&wished_product[variant_id]=92&wished_product[quantity]=2&wished_product[remark]=Foo+bar
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
ETag: W/&quot;10960701dd319c207557dd083f9c50a2&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: e0173f23-ef03-4a10-ab86-36c0b5a38f93
X-Runtime: 0.013274
Vary: Origin
Content-Length: 74
201 Created
```


```json
{
  "id": 16,
  "wishlist_id": 31,
  "variant_id": 92,
  "quantity": 2,
  "remark": "Foo bar"
}
```



## Delete a wished product


### Request

#### Endpoint

```plaintext
DELETE /api/wished_products/26
Accept: application/json
Authorizat IO N: Bearer 56c52dd2e4c13d19319963dd62cc7318169187be710413d5
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
X-Request-Id: 4bba12a1-9f29-4242-952a-38279e89d087
X-Runtime: 0.011194
Vary: Origin
204 No Content
```




## Get a single wished product


### Request

#### Endpoint

```plaintext
GET /api/wished_products/29
Accept: application/json
Authorizat IO N: Bearer d879aed29aff21cf55ba1c02dfca90cbec4e505b87d1cc45
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
ETag: W/&quot;002ce5a71ac575a20cd44f04ccd8b60b&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 5ef18395-e986-4f5e-b9b6-110a1bef7c55
X-Runtime: 0.008959
Vary: Origin
Content-Length: 70
200 OK
```


```json
{
  "id": 29,
  "wishlist_id": 40,
  "variant_id": 120,
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
Authorizat IO N: Bearer d503911456d8216b6322d777c44e65a4c837deb61373ccae
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
ETag: W/&quot;b734ec1902598c352aef538155c6002e&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 9a03409b-adc2-4e6f-8e1c-69bf1aed04a4
X-Runtime: 0.010327
Vary: Origin
Content-Length: 301
200 OK
```


```json
{
  "wished_products": [
    {
      "id": 20,
      "wishlist_id": 33,
      "variant_id": 102,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 21,
      "wishlist_id": 34,
      "variant_id": 104,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 22,
      "wishlist_id": 35,
      "variant_id": 106,
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
Authorizat IO N: Bearer dd94e7c44849ea730c495452e8431107f4891540f54b8ee3
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
ETag: W/&quot;99f238aa20f9acf2370e301e6518bce6&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: b66ed380-7e70-4ca9-8a1f-835d5f682477
X-Runtime: 0.077539
Vary: Origin
Content-Length: 2084
200 OK
```


```json
{
  "wished_products": [
    {
      "id": 13,
      "wishlist_id": 30,
      "variant_id": 86,
      "quantity": 1,
      "remark": null,
      "variant": {
        "id": 86,
        "name": "Product #46 - 5413",
        "sku": "SKU-85",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-46-5413",
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
      "variant_id": 88,
      "quantity": 1,
      "remark": null,
      "variant": {
        "id": 88,
        "name": "Product #47 - 7626",
        "sku": "SKU-87",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-47-7626",
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
      "variant_id": 90,
      "quantity": 1,
      "remark": null,
      "variant": {
        "id": 90,
        "name": "Product #48 - 888",
        "sku": "SKU-89",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-48-888",
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
Authorizat IO N: Bearer 5f9beb66a91b0ef95b90851e6b9aad4e0484444a7cd2c72a
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
ETag: W/&quot;533533175891c66e5bfe9faaacae79dc&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 6a0aaec4-4e30-4f26-8b1e-8664a0ddf487
X-Runtime: 0.089564
Vary: Origin
Content-Length: 2155
200 OK
```


```json
{
  "wished_products": [
    {
      "id": 23,
      "wishlist_id": 36,
      "variant_id": 108,
      "quantity": 1,
      "remark": null,
      "variant": {
        "id": 108,
        "name": "Product #57 - 1475",
        "sku": "SKU-107",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-57-1475",
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
      "id": 24,
      "wishlist_id": 37,
      "variant_id": 110,
      "quantity": 1,
      "remark": null,
      "variant": {
        "id": 110,
        "name": "Product #58 - 4480",
        "sku": "SKU-109",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-58-4480",
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
    },
    {
      "id": 25,
      "wishlist_id": 38,
      "variant_id": 112,
      "quantity": 1,
      "remark": null,
      "variant": {
        "id": 112,
        "name": "Product #59 - 5852",
        "sku": "SKU-111",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-59-5852",
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
Authorizat IO N: Bearer a10029ad512a0f453392cde8e034bb30cdb24cb5c781aad0
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
ETag: W/&quot;136db50555e28e07310cd0b8cc02c122&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: dd7a596a-0756-4a71-b732-c7654824db06
X-Runtime: 0.035412
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
      "variant_id": 80,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 11,
      "wishlist_id": 29,
      "variant_id": 82,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 12,
      "wishlist_id": 29,
      "variant_id": 84,
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
Authorizat IO N: Bearer 7f3099ca69b155959b840c431c431929e26bd457a556feea
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/wished_products/:id`

#### Parameters


```json
wished_product[wishlist_id]=32&wished_product[variant_id]=100&wished_product[quantity]=2&wished_product[remark]=Foo+bar
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
ETag: W/&quot;88d422cfad70ca6cc75041c83242b504&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 3f9b1c62-6dff-4f95-a712-255cde4509ed
X-Runtime: 0.011887
Vary: Origin
Content-Length: 75
200 OK
```


```json
{
  "id": 17,
  "wishlist_id": 32,
  "variant_id": 100,
  "quantity": 2,
  "remark": "Foo bar"
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
Authorizat IO N: Bearer f80a878685f1b49e985080bf61ffca4e76ff9ad09de3d1cd
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
ETag: W/&quot;fd183b13383e841c03cef55969826a7e&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: f9da06a5-6eb8-4dd0-b61d-b8c46bb7d9f9
X-Runtime: 0.014602
Vary: Origin
Content-Length: 99
201 Created
```


```json
{
  "id": 3,
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
DELETE /api/wishlists/2
Accept: application/json
Authorizat IO N: Bearer e060049ce9dd13c8ed1c07ded26143f0611a2e5d752c29e5
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
X-Request-Id: 82d36028-1d4b-4063-82fe-2e34b196a79a
X-Runtime: 0.016711
Vary: Origin
204 No Content
```




## Get a single wishlist


### Request

#### Endpoint

```plaintext
GET /api/wishlists/1
Accept: application/json
Authorizat IO N: Bearer d0d9d8ad8268cbbd37c3519512e321d84ff473c62c606b86
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
ETag: W/&quot;becf764ba8691fc29a4e84208ce83bc1&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: ad58a720-a71f-4cd9-a3c3-5ecc3044d355
X-Runtime: 0.048739
Vary: Origin
Content-Length: 302
200 OK
```


```json
{
  "id": 1,
  "user_id": 20,
  "name": "Wishlist #1",
  "is_public": false,
  "is_default": true,
  "wished_products": [
    {
      "id": 1,
      "wishlist_id": 1,
      "variant_id": 34,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 2,
      "wishlist_id": 1,
      "variant_id": 36,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 3,
      "wishlist_id": 1,
      "variant_id": 38,
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
Authorizat IO N: Bearer cd126aa2faaca1ce7ed5dbd2f6fa0cdced796bb52c700945
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
ETag: W/&quot;5574c219c3c7411c17679961ca0cd1f4&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 68607da3-8973-4532-98b0-a790ec256544
X-Runtime: 0.010805
Vary: Origin
Content-Length: 880
200 OK
```


```json
{
  "wishlists": [
    {
      "id": 4,
      "user_id": 23,
      "name": "Wishlist #2",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 5,
      "user_id": 24,
      "name": "Wishlist #3",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 6,
      "user_id": 25,
      "name": "Wishlist #4",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 7,
      "user_id": 26,
      "name": "Wishlist #5",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 8,
      "user_id": 27,
      "name": "Wishlist #6",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 9,
      "user_id": 28,
      "name": "Wishlist #7",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 10,
      "user_id": 29,
      "name": "Wishlist #8",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 11,
      "user_id": 30,
      "name": "Wishlist #9",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 12,
      "user_id": 31,
      "name": "Wishlist #10",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 13,
      "user_id": 32,
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
Authorizat IO N: Bearer 8e79a915bdc904a3e9c0dfd8fd0ad1400d8b235432499c0d
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
ETag: W/&quot;d8c0509374cb5e500cf841a2cfa89d26&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 5b0f6cc4-9911-402f-a22c-72a414909692
X-Runtime: 0.007136
Vary: Origin
Content-Length: 307
200 OK
```


```json
{
  "id": 28,
  "user_id": 37,
  "name": "Wishlist #26",
  "is_public": false,
  "is_default": true,
  "wished_products": [
    {
      "id": 7,
      "wishlist_id": 28,
      "variant_id": 46,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 8,
      "wishlist_id": 28,
      "variant_id": 48,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 9,
      "wishlist_id": 28,
      "variant_id": 50,
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
Authorizat IO N: Bearer 724bfd0a28868d02a07e6ffda166b9970fd32b319c32c652
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
ETag: W/&quot;d2b10b9261ccb02b98fe05568d74bd59&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 5fb0bfe9-9349-4d18-8ef8-0d4447459a72
X-Runtime: 0.009427
Vary: Origin
Content-Length: 903
200 OK
```


```json
{
  "wishlists": [
    {
      "id": 17,
      "user_id": 35,
      "name": "Wishlist #15",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 18,
      "user_id": 35,
      "name": "Wishlist #16",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 19,
      "user_id": 35,
      "name": "Wishlist #17",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 20,
      "user_id": 35,
      "name": "Wishlist #18",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 21,
      "user_id": 35,
      "name": "Wishlist #19",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 22,
      "user_id": 35,
      "name": "Wishlist #20",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 23,
      "user_id": 35,
      "name": "Wishlist #21",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 24,
      "user_id": 35,
      "name": "Wishlist #22",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 25,
      "user_id": 35,
      "name": "Wishlist #23",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 26,
      "user_id": 35,
      "name": "Wishlist #24",
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
Authorizat IO N: Bearer 31f56284a18ec27bb4b97a4117912ec6911f48286fdcf5b8
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/wishlists/:id`

#### Parameters


```json
wishlist[name]=Another+Wishlist&wishlist[user_id]=36&wishlist[is_default]=true&wishlist[is_public]=false
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
ETag: W/&quot;ffccd523a7abea7acfa3650de578b3b8&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 686965eb-24b6-4401-b8b7-c4e519da4dfc
X-Runtime: 0.012529
Vary: Origin
Content-Length: 311
200 OK
```


```json
{
  "id": 27,
  "user_id": 36,
  "name": "Another Wishlist",
  "is_public": false,
  "is_default": true,
  "wished_products": [
    {
      "id": 4,
      "wishlist_id": 27,
      "variant_id": 40,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 5,
      "wishlist_id": 27,
      "variant_id": 42,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 6,
      "wishlist_id": 27,
      "variant_id": 44,
      "quantity": 1,
      "remark": null
    }
  ]
}
```



