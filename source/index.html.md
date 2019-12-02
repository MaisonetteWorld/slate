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
PUT /api/orders/M793297452/addresses/12
Accept: application/json
X-Spree-Order-Token: TZVZELY1I-gTVOgzcWxjBg
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
ETag: W/&quot;07fc999e939c161e723995e9aad8477a&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 7aaa6c5c-edd6-4b85-a861-39b4817fbff6
X-Runtime: 0.072616
Vary: Origin
Content-Length: 507
200 OK
```


```json
{
  "id": 13,
  "firstname": "John the Tester",
  "lastname": null,
  "full_name": "John the Tester",
  "address1": "A Different Road",
  "address2": "Northwest",
  "city": "Herndon",
  "zipcode": "10012",
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
}
```



# Braintree transactions



## Creating a PayPal express checkout transaction


### Request

#### Endpoint

```plaintext
POST /api/braintree/transactions
Accept: application/json
X-Spree-Order-Token: pZLD1GyGKvDBg_6ZOAAhZQ
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/braintree/transactions`

#### Parameters


```json
order_id=M434508199&payment_method_id=21&options[restart_checkout]=true&transaction[email]=maryellen.oga%40mckenziemcglynn.com&transaction[nonce]=fake-paypal-billing-agreement-nonce&transaction[phone]=555-555-0199&transaction[address_attributes][first_name]=John&transaction[address_attributes][last_name]=Stamm&transaction[address_attributes][address_line_1]=A+Different+Road&transaction[address_attributes][city]=Herndon&transaction[address_attributes][state_code]=AL&transaction[address_attributes][zip]=10027&transaction[address_attributes][country_code]=US&transaction[payment_type]=PayPalAccount
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
ETag: W/&quot;d11eb6c120555caf197d4089bfb54930&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 4735fc46-da5a-44df-ad80-dd4c63309e74
X-Runtime: 0.355245
Vary: Origin
Content-Length: 5266
200 OK
```


```json
{
  "id": 14,
  "number": "M434508199",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2019-12-02T11:35:30.088-05:00",
  "updated_at": "2019-12-02T11:35:30.425-05:00",
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
  "token": "pZLD1GyGKvDBg_6ZOAAhZQ",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order&order=M434508199&bzip=10027&init=true",
  "payment_methods": [
    {
      "id": 21,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 30,
    "firstname": "John",
    "lastname": "Stamm",
    "full_name": "John Stamm",
    "address1": "A Different Road",
    "address2": null,
    "city": "Herndon",
    "zipcode": "10027",
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
    "id": 30,
    "firstname": "John",
    "lastname": "Stamm",
    "full_name": "John Stamm",
    "address1": "A Different Road",
    "address2": null,
    "city": "Herndon",
    "zipcode": "10027",
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
      "id": 17,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 75,
      "vendor_id": 148,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 75,
        "name": "Product #43 - 684",
        "sku": "SKU-74",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-43-684",
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
        "product_id": 43,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "vendor_name": "Vendor #148",
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
      "created_at": "2019-12-02T11:35:30.216-05:00",
      "updated_at": "2019-12-02T11:35:30.216-05:00",
      "payment_method": {
        "id": 21,
        "name": "Braintree"
      },
      "source": {
        "id": 7,
        "payment_type": "PayPalAccount",
        "token": "bgx899",
        "created_at": "2019-12-02T11:35:30.215-05:00",
        "email": "jane.doe@paypal.com"
      }
    }
  ],
  "shipments": [
    {
      "id": 13,
      "tracking": null,
      "tracking_url": null,
      "number": "H74855614324",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M434508199",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 13,
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
        }
      ],
      "selected_shipping_rate": {
        "id": 13,
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
              "id": 16,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 26,
              "name": "ShippingCategory #26"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 75,
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
      "delivery_estimation": "Dec 04"
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
X-Spree-Order-Token: JJ3yhPjPAHC6TJfiYneT6w
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/braintree/transactions`

#### Parameters


```json
order_id=M285512408&payment_method_id=22&options[restart_checkout]=true&transaction[email]=maryellen.oga%40mckenziemcglynn.com&transaction[nonce]=fake-apple-pay-visa-nonce&transaction[phone]=555-555-0199&transaction[address_attributes][first_name]=John&transaction[address_attributes][last_name]=Stamm&transaction[address_attributes][address_line_1]=A+Different+Road&transaction[address_attributes][city]=Herndon&transaction[address_attributes][state_code]=AL&transaction[address_attributes][zip]=10029&transaction[address_attributes][country_code]=US&transaction[payment_type]=ApplePayCard
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
ETag: W/&quot;118eca6f575d4c9b2aca57d1770d8517&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 8481422a-73a6-474c-804e-69ae720de2e0
X-Runtime: 0.296039
Vary: Origin
Content-Length: 5314
200 OK
```


```json
{
  "id": 15,
  "number": "M285512408",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2019-12-02T11:35:30.710-05:00",
  "updated_at": "2019-12-02T11:35:30.980-05:00",
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
  "token": "JJ3yhPjPAHC6TJfiYneT6w",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order&order=M285512408&bzip=10029&init=true",
  "payment_methods": [
    {
      "id": 22,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 33,
    "firstname": "John",
    "lastname": "Stamm",
    "full_name": "John Stamm",
    "address1": "A Different Road",
    "address2": null,
    "city": "Herndon",
    "zipcode": "10029",
    "phone": "555-555-0199",
    "company": null,
    "alternative_phone": null,
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
    "id": 33,
    "firstname": "John",
    "lastname": "Stamm",
    "full_name": "John Stamm",
    "address1": "A Different Road",
    "address2": null,
    "city": "Herndon",
    "zipcode": "10029",
    "phone": "555-555-0199",
    "company": null,
    "alternative_phone": null,
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
      "variant_id": 77,
      "vendor_id": 153,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 77,
        "name": "Product #44 - 6902",
        "sku": "SKU-76",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-44-6902",
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
      "vendor_name": "Vendor #153",
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
      "created_at": "2019-12-02T11:35:30.816-05:00",
      "updated_at": "2019-12-02T11:35:30.816-05:00",
      "payment_method": {
        "id": 22,
        "name": "Braintree"
      },
      "source": {
        "id": 8,
        "payment_type": "ApplePayCard",
        "token": "cg7hsk",
        "created_at": "2019-12-02T11:35:30.815-05:00",
        "cc_type": "Apple Pay - Visa",
        "last_digits": "1881",
        "month": "12",
        "year": "2020"
      }
    }
  ],
  "shipments": [
    {
      "id": 15,
      "tracking": null,
      "tracking_url": null,
      "number": "H68381323718",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M285512408",
      "stock_location_name": "NY Warehouse",
      "shipping_rates": [
        {
          "id": 15,
          "name": "UPS Ground",
          "admin_name": null,
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 13,
          "shipping_method_code": "UPS_GROUND",
          "extra_cost": "",
          "is_flat_rate": false,
          "is_flat_rate_expedited": false,
          "is_free_shipping": false,
          "display_cost": "$100.00"
        }
      ],
      "selected_shipping_rate": {
        "id": 15,
        "name": "UPS Ground",
        "admin_name": null,
        "cost": "100.0",
        "selected": true,
        "shipping_method_id": 13,
        "shipping_method_code": "UPS_GROUND",
        "extra_cost": "",
        "is_flat_rate": false,
        "is_flat_rate_expedited": false,
        "is_free_shipping": false,
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
              "id": 27,
              "name": "ShippingCategory #27"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 77,
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
      "delivery_estimation": "Dec 04"
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
PUT /api/checkouts/M618693919/complete
Accept: application/json
X-Spree-Order-Token: YJ-57f4eJIKKx_XHAP5iSQ
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
ETag: W/&quot;b7b8f33835f3686694abaf7822acf131&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 34f3eea2-e6e1-4f43-a549-04aa834c51c4
X-Runtime: 0.372777
Vary: Origin
Content-Length: 5440
200 OK
```


```json
{
  "id": 20,
  "number": "M618693919",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "complete",
  "adjustment_total": "0.0",
  "user_id": 75,
  "created_at": "2019-12-02T11:35:34.714-05:00",
  "updated_at": "2019-12-02T11:35:35.057-05:00",
  "completed_at": "2019-12-02T11:35:35.057-05:00",
  "payment_total": "110.0",
  "shipment_state": "ready",
  "payment_state": "paid",
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
  "token": "YJ-57f4eJIKKx_XHAP5iSQ",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order&order=M618693919&bzip=10039&init=true",
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
    "id": 42,
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
    "id": 43,
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
      "variant_id": 87,
      "vendor_id": 178,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 87,
        "name": "Product #49 - 1628",
        "sku": "SKU-86",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-49-1628",
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
            "id": 38,
            "name": "Size-38",
            "presentation": "S",
            "option_type_name": "foo-size-38",
            "option_type_id": 38,
            "option_type_presentation": "Size",
            "position": 1
          }
        ],
        "images": [

        ],
        "product_id": 49,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "vendor_name": "Vendor #178",
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
      "created_at": "2019-12-02T11:35:34.818-05:00",
      "updated_at": "2019-12-02T11:35:34.923-05:00",
      "payment_method": {
        "id": 27,
        "name": "Braintree"
      },
      "source": {
        "id": 10,
        "payment_type": "CreditCard",
        "token": "4rptfz",
        "created_at": "2019-12-02T11:35:34.817-05:00",
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
      "number": "H32410518510",
      "cost": "100.0",
      "shipped_at": null,
      "state": "ready",
      "order_id": "M618693919",
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
              "id": 32,
              "name": "ShippingCategory #32"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 87,
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
      "delivery_estimation": "Dec 04"
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
PATCH /api/checkouts/M226935205
Accept: application/json
X-Spree-Order-Token: K7MQ4KJzcp4umYEjAzsVWg
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=25&order[payment_attributes][][source_attributes][nonce]=fake-apple-pay-visa-nonce&order[payment_attributes][][source_attributes][payment_type]=ApplePayCard&order[payment_attributes][][source_attributes][reusable]=true
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
ETag: W/&quot;f0b54708b9063a3cf977a8f313e98d06&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: e01cb341-e22e-44e0-b2b5-23747b16fed9
X-Runtime: 0.232727
Vary: Origin
Content-Length: 4821
200 OK
```


```json
{
  "id": 18,
  "number": "M226935205",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 73,
  "created_at": "2019-12-02T11:35:33.177-05:00",
  "updated_at": "2019-12-02T11:35:33.543-05:00",
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
  "token": "K7MQ4KJzcp4umYEjAzsVWg",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order&order=M226935205&bzip=10035&init=true",
  "payment_methods": [
    {
      "id": 25,
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
    "zipcode": "10035",
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
    "id": 39,
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
      "variant_id": 83,
      "vendor_id": 168,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 83,
        "name": "Product #47 - 1945",
        "sku": "SKU-82",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-47-1945",
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
        "product_id": 47,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "vendor_name": "Vendor #168",
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
      "number": "H44118527070",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M226935205",
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
              "id": 30,
              "name": "ShippingCategory #30"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 83,
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
      "delivery_estimation": "Dec 04"
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
PATCH /api/checkouts/M119594829
Accept: application/json
X-Spree-Order-Token: Mp-RsTbOTYKwZAvzM4DuGg
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=24&order[payment_attributes][][source_attributes][nonce]=fake-paypal-billing-agreement-nonce&order[payment_attributes][][source_attributes][payment_type]=PayPalAccount&order[payment_attributes][][source_attributes][reusable]=true
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
ETag: W/&quot;36e4f6da0d4b0ab316a2366866667584&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 9b8643f8-a38e-414b-8bc8-7c00a65b5e01
X-Runtime: 0.126580
Vary: Origin
Content-Length: 4821
200 OK
```


```json
{
  "id": 17,
  "number": "M119594829",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 72,
  "created_at": "2019-12-02T11:35:32.615-05:00",
  "updated_at": "2019-12-02T11:35:32.885-05:00",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "email71@example.com",
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
  "token": "Mp-RsTbOTYKwZAvzM4DuGg",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order&order=M119594829&bzip=10033&init=true",
  "payment_methods": [
    {
      "id": 24,
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
    "zipcode": "10033",
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
    "id": 37,
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
      "variant_id": 81,
      "vendor_id": 163,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 81,
        "name": "Product #46 - 5569",
        "sku": "SKU-80",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-46-5569",
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
        "product_id": 46,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "vendor_name": "Vendor #163",
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
      "number": "H01013470317",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M119594829",
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
          "extra_cost": "",
          "is_flat_rate": false,
          "is_flat_rate_expedited": false,
          "is_free_shipping": false,
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
              "id": 29,
              "name": "ShippingCategory #29"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 81,
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
      "delivery_estimation": "Dec 04"
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
PATCH /api/checkouts/M281251824
Accept: application/json
X-Spree-Order-Token: wteBjAk9UOISY5lfuGixoQ
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=23&order[payment_attributes][][source_attributes][nonce]=fake-valid-visa-nonce&order[payment_attributes][][source_attributes][payment_type]=CreditCard&order[payment_attributes][][source_attributes][reusable]=true
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
ETag: W/&quot;5401f83be8e55439746388b9f7811330&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 3061f34b-a2de-4f50-a4d1-28cece0d6e9e
X-Runtime: 0.154778
Vary: Origin
Content-Length: 4821
200 OK
```


```json
{
  "id": 16,
  "number": "M281251824",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 71,
  "created_at": "2019-12-02T11:35:32.040-05:00",
  "updated_at": "2019-12-02T11:35:32.315-05:00",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "email70@example.com",
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
  "token": "wteBjAk9UOISY5lfuGixoQ",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order&order=M281251824&bzip=10031&init=true",
  "payment_methods": [
    {
      "id": 23,
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
    "zipcode": "10031",
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
    "id": 35,
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
      "variant_id": 79,
      "vendor_id": 158,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 79,
        "name": "Product #45 - 2572",
        "sku": "SKU-78",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-45-2572",
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
      "vendor_name": "Vendor #158",
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
      "number": "H83531206417",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M281251824",
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
          "extra_cost": "",
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
              "id": 18,
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
          "variant_id": 79,
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
      "delivery_estimation": "Dec 04"
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
PATCH /api/checkouts/M541803452
Accept: application/json
X-Spree-Order-Token: jRgAFPQa0XMcpicwMD5UEw
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
ETag: W/&quot;1043fa6d9da3e569df4e165cf96b1cf7&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 1bf2ab6d-3265-452b-9c85-cb171ab0cfe1
X-Runtime: 0.138550
Vary: Origin
Content-Length: 4819
200 OK
```


```json
{
  "id": 19,
  "number": "M541803452",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 74,
  "created_at": "2019-12-02T11:35:34.048-05:00",
  "updated_at": "2019-12-02T11:35:34.425-05:00",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "email73@example.com",
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
  "token": "jRgAFPQa0XMcpicwMD5UEw",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order&order=M541803452&bzip=10037&init=true",
  "payment_methods": [
    {
      "id": 26,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 40,
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
    "id": 41,
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
      "variant_id": 85,
      "vendor_id": 173,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 85,
        "name": "Product #48 - 324",
        "sku": "SKU-84",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-48-324",
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
            "id": 37,
            "name": "Size-37",
            "presentation": "S",
            "option_type_name": "foo-size-37",
            "option_type_id": 37,
            "option_type_presentation": "Size",
            "position": 1
          }
        ],
        "images": [

        ],
        "product_id": 48,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "vendor_name": "Vendor #173",
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
      "number": "H06167402026",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M541803452",
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
              "id": 31,
              "name": "ShippingCategory #31"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 85,
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
      "delivery_estimation": "Dec 04"
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
PUT /api/checkouts/M555288582
Accept: application/json
X-Spree-Order-Token: gJkqyf2HPU5picATKtYBJg
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PUT /api/checkouts/:id`

#### Parameters


```json
order[ship_address_attributes][id]&order[ship_address_attributes][firstname]=John&order[ship_address_attributes][lastname]&order[ship_address_attributes][address1]=10+Lovely+Street&order[ship_address_attributes][address2]=Northwest&order[ship_address_attributes][city]=Herndon&order[ship_address_attributes][zipcode]=10041&order[ship_address_attributes][phone]=555-555-0199&order[ship_address_attributes][state_name]&order[ship_address_attributes][alternative_phone]=555-555-0199&order[ship_address_attributes][company]=Company&order[ship_address_attributes][state_id]=35&order[ship_address_attributes][country_id]=35&order[ship_address_attributes][created_at]&order[ship_address_attributes][updated_at]&order[use_billing]=true&hold_state=true
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
ETag: W/&quot;a7aa8da4d8cf8b884731d0093460ac61&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 993d03af-6500-4643-83f5-2063753a9d21
X-Runtime: 0.139635
Vary: Origin
Content-Length: 4728
200 OK
```


```json
{
  "id": 21,
  "number": "M555288582",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "cart",
  "adjustment_total": "0.0",
  "user_id": 76,
  "created_at": "2019-12-02T11:35:35.383-05:00",
  "updated_at": "2019-12-02T11:35:35.477-05:00",
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
  "token": "gJkqyf2HPU5picATKtYBJg",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order&order=M555288582&bzip=10041&init=true",
  "payment_methods": [

  ],
  "bill_address": {
    "id": 44,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "10 Lovely Street",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10041",
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
    "id": 44,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "10 Lovely Street",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10041",
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
      "id": 24,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 89,
      "vendor_id": 183,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 89,
        "name": "Product #50 - 7803",
        "sku": "SKU-88",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-50-7803",
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
      "vendor_name": "Vendor #183",
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
      "number": "H18321773642",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M555288582",
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
              "id": 33,
              "name": "ShippingCategory #33"
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
      "international_shipping": false,
      "delivery_estimation": "Dec 04"
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



# LineItem

Representation of a single cart item for a specific variant with price of vendor

## Creating a line item


### Request

#### Endpoint

```plaintext
POST /api/orders/M500056840/line_items
Accept: application/json
X-Spree-Order-Token: 3izv4VBj0EH7gTijpCxzqQ
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/:order_number/line_items`

#### Parameters


```json
line_item[variant_id]=55&line_item[options][vendor_id]=122
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
ETag: W/&quot;b3eb0e6f5bf35b20356662ba78b308ab&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: faf08041-570e-42f5-9a15-ecf92234a7ee
X-Runtime: 0.092003
Vary: Origin
Content-Length: 923
201 Created
```


```json
{
  "id": 16,
  "quantity": 1,
  "price": "19.99",
  "variant_id": 55,
  "vendor_id": 122,
  "single_display_amount": "$19.99",
  "display_amount": "$19.99",
  "total": "19.99",
  "on_sale": false,
  "final_sale": false,
  "backordered": null,
  "promotionable": true,
  "variant": {
    "id": 55,
    "name": "Product #33 - 3146",
    "sku": "SKU-54",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": false,
    "slug": "product-33-3146",
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
    "product_id": 33,
    "lead_time": 2,
    "brand": null,
    "brand_slug": null,
    "brand_description": null
  },
  "monogram": null,
  "vendor_name": "Vendor #122",
  "country_iso": null,
  "adjustments": [

  ]
}
```



## Deleting a line item


### Request

#### Endpoint

```plaintext
DELETE /api/orders/M838731182/line_items/13
Accept: application/json
X-Spree-Order-Token: XLMUzNnwPmKMFIU6lO8waw
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
X-Request-Id: fb8b9381-f8ba-476e-a6c4-edfbfd7b1ff2
X-Runtime: 0.089801
Vary: Origin
204 No Content
```




## Updating a line item


### Request

#### Endpoint

```plaintext
PUT /api/orders/M099923941/line_items/14
Accept: application/json
X-Spree-Order-Token: 7cyRqig45L7CBzsrAk3Yhg
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
ETag: W/&quot;62c127889980760372831edb2419ddc8&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 58c0c399-2791-4a6a-993e-fe5270fd194c
X-Runtime: 0.104620
Vary: Origin
Content-Length: 920
200 OK
```


```json
{
  "id": 14,
  "quantity": 2,
  "price": "10.0",
  "variant_id": 49,
  "vendor_id": 111,
  "single_display_amount": "$10.00",
  "display_amount": "$20.00",
  "total": "20.0",
  "on_sale": false,
  "final_sale": false,
  "backordered": null,
  "promotionable": true,
  "variant": {
    "id": 49,
    "name": "Product #30 - 5795",
    "sku": "SKU-48",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": false,
    "slug": "product-30-5795",
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
  "vendor_name": "Vendor #111",
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
Authorizat IO N: Bearer 3a9109afacaedfadfeb3ff7bc60b491464dd4a6269716be6
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/minis`

#### Parameters


```json
mini[name]=Winny&mini[user_id]=25&mini[birth_year]=2019&mini[birth_month]=1&mini[birth_day]=1
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
ETag: W/&quot;47677e9de6b007aa75df2865966c90ca&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 19b44cf5-6e82-459e-a15b-4e4e5d13c86e
X-Runtime: 0.009068
Vary: Origin
Content-Length: 162
201 Created
```


```json
{
  "id": 9,
  "user_id": 25,
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
DELETE /api/minis/7
Accept: application/json
Authorizat IO N: Bearer d3e7427289ff216308747afcaf3b43efaca8594d67cc044d
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
X-Request-Id: 3ffe29a1-43c4-4151-abc4-ffe1f887aafd
X-Runtime: 0.005991
Vary: Origin
204 No Content
```




## Get a single mini


### Request

#### Endpoint

```plaintext
GET /api/minis/8
Accept: application/json
Authorizat IO N: Bearer 07f95799a05a5b92b69d52c4ad7b24c4e9a07faaf8648c95
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
ETag: W/&quot;3332c1fa0677c52277d437cc9ae92662&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 0d205664-c6c0-4daa-8b19-ffd4666926d7
X-Runtime: 0.008823
Vary: Origin
Content-Length: 167
200 OK
```


```json
{
  "id": 8,
  "user_id": 24,
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
Authorizat IO N: Bearer 903f4f09947b4d3ed8dcff167f9003118e5131a28de66796
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
ETag: W/&quot;5f9a7158dc93400de32a6cdd49e42b66&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: d040b50f-0e30-4418-9a68-8e1ac31f1481
X-Runtime: 0.028262
Vary: Origin
Content-Length: 1770
200 OK
```


```json
{
  "minis": [
    {
      "id": 19,
      "user_id": 35,
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
      "id": 18,
      "user_id": 34,
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
      "id": 17,
      "user_id": 33,
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
      "id": 16,
      "user_id": 32,
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
      "user_id": 31,
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
      "id": 14,
      "user_id": 30,
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
      "id": 13,
      "user_id": 29,
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
      "id": 12,
      "user_id": 28,
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
      "id": 11,
      "user_id": 27,
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
      "id": 10,
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
Authorizat IO N: Bearer 9f124c25e43fa4fdaa0d98d8e107e70865398e9f0f7d10db
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
ETag: W/&quot;06174831015c028c097367fe49ee3d89&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 93ed57af-baf5-4751-a0be-2249da62b949
X-Runtime: 0.036025
Vary: Origin
Content-Length: 414
200 OK
```


```json
{
  "minis": [
    {
      "id": 5,
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
      "id": 4,
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
PATCH /api/minis/6
Accept: application/json
Authorizat IO N: Bearer 41c51221baf9c5fb1b1871803645bd25d30c5574f4b4b55f
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
ETag: W/&quot;e4ea5ca57d65da3a0b7a6eb96057e2d9&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 3033e4af-84a7-49c7-8fb3-bc241a704ef2
X-Runtime: 0.010957
Vary: Origin
Content-Length: 168
200 OK
```


```json
{
  "id": 6,
  "user_id": 22,
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

Return an order, scoped to the current user

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
user_id&order_token&line_item[variant_id]=14&line_item[quantity]=2&line_item[vendor_id]=22
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
ETag: W/&quot;5b3bd654656de48fc04e040e5d463901&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: d2f4743b-f636-4a3b-b1de-8d57a27bed66
X-Runtime: 0.100217
Vary: Origin
Content-Length: 2577
200 OK
```


```json
{
  "id": 4,
  "number": "M571765109",
  "item_total": "39.98",
  "total": "39.98",
  "ship_total": "0.0",
  "state": "cart",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2019-12-02T11:35:22.583-05:00",
  "updated_at": "2019-12-02T11:35:22.616-05:00",
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
  "token": "_HE1cWlJYQ9BkimpUTEi5A",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order&order=M571765109&bzip=&init=true",
  "payment_methods": [

  ],
  "bill_address": null,
  "ship_address": null,
  "line_items": [
    {
      "id": 6,
      "quantity": 2,
      "price": "19.99",
      "variant_id": 14,
      "vendor_id": 22,
      "single_display_amount": "$19.99",
      "display_amount": "$39.98",
      "total": "39.98",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 14,
        "name": "Product #7 - 3651",
        "sku": "SKU-13",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-7-3651",
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
      "vendor_name": "Vendor #22",
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
Authorizat IO N: Bearer 983f09bafded7a8b03bafbf68d418e7ce2b5a4cffa9be799
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
ETag: W/&quot;0a0dcfbbac06e8f910de4b64965f0ddd&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 09a8d907-8e7a-4d0a-b60e-d116e70c4de1
X-Runtime: 0.014149
Vary: Origin
Content-Length: 310
200 OK
```


```json
{
  "orders": [
    {
      "number": "M514933858",
      "completed_at": "2019-12-02T11:35:23.065-05:00",
      "total": "120.0",
      "state": "Complete",
      "shipment_state": "shipped",
      "shipments": [
        {
          "number": "H83127018242",
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
GET /api/orders/M982244579
Accept: application/json
Authorizat IO N: Bearer 92d7dfa4d97217c6621964413bd182d72b12f240d656a06d
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
ETag: W/&quot;267901818ad98759394e15c301915de6&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: da5da587-a04d-40e2-8e1d-c8154c2d7d41
X-Runtime: 0.189508
Vary: Origin
Content-Length: 9892
200 OK
```


```json
{
  "id": 3,
  "number": "M982244579",
  "item_total": "20.0",
  "total": "120.0",
  "ship_total": "100.0",
  "state": "complete",
  "adjustment_total": "0.0",
  "user_id": 9,
  "created_at": "2019-12-02T11:35:21.902-05:00",
  "updated_at": "2019-12-02T11:35:22.164-05:00",
  "completed_at": "2019-12-02T11:35:21.991-05:00",
  "payment_total": "120.0",
  "shipment_state": "shipped",
  "payment_state": "paid",
  "email": "email8@example.com",
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
  "token": "1TK7hHFnUdnxCWfvu0mcGA",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order&order=M982244579&bzip=10007&init=true",
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
  "line_items": [
    {
      "id": 4,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 8,
      "vendor_id": 15,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 8,
        "name": "Product #4 - 4311",
        "sku": "SKU-7",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-4-4311",
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
      "vendor_name": "Vendor #15",
      "country_iso": "US",
      "adjustments": [
        {
          "id": 17,
          "source_type": "Spree::TaxRate",
          "source_id": 3,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 4,
          "amount": "2.0",
          "label": "VAT 5%",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-12-02T11:35:22.126-05:00",
          "updated_at": "2019-12-02T11:35:22.137-05:00",
          "display_amount": "$2.00"
        },
        {
          "id": 11,
          "source_type": "Spree::PromotionAction",
          "source_id": 2,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 4,
          "amount": "5.0",
          "label": "foo",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-12-02T11:35:22.058-05:00",
          "updated_at": "2019-12-02T11:35:22.058-05:00",
          "display_amount": "$5.00"
        },
        {
          "id": 10,
          "source_type": "Spree::PromotionAction",
          "source_id": 2,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 4,
          "amount": "5.0",
          "label": "foo",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-12-02T11:35:22.049-05:00",
          "updated_at": "2019-12-02T11:35:22.049-05:00",
          "display_amount": "$5.00"
        }
      ]
    },
    {
      "id": 5,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 10,
      "vendor_id": 15,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 10,
        "name": "Product #5 - 2210",
        "sku": "SKU-9",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-5-2210",
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
      "vendor_name": "Vendor #15",
      "country_iso": "US",
      "adjustments": [
        {
          "id": 18,
          "source_type": "Spree::TaxRate",
          "source_id": 4,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 5,
          "amount": "1.5",
          "label": "VAT 5%",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-12-02T11:35:22.149-05:00",
          "updated_at": "2019-12-02T11:35:22.173-05:00",
          "display_amount": "$1.50"
        },
        {
          "id": 12,
          "source_type": "Spree::PromotionAction",
          "source_id": 2,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 5,
          "amount": "5.0",
          "label": "bar",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-12-02T11:35:22.067-05:00",
          "updated_at": "2019-12-02T11:35:22.067-05:00",
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
      "created_at": "2019-12-02T11:35:22.002-05:00",
      "updated_at": "2019-12-02T11:35:22.002-05:00",
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
      "number": "H55242118261",
      "cost": "100.0",
      "shipped_at": "2019-12-02T11:35:22.024-05:00",
      "state": "shipped",
      "order_id": "M982244579",
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
          "extra_cost": "",
          "is_flat_rate": false,
          "is_flat_rate_expedited": false,
          "is_free_shipping": false,
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
              "id": 5,
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
          "variant_id": 8,
          "quantity": 1,
          "states": {
            "shipped": 1
          }
        },
        {
          "variant_id": 10,
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
          "adjustable_id": 3,
          "amount": "-10.0",
          "label": "Shipping",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-12-02T11:35:22.090-05:00",
          "updated_at": "2019-12-02T11:35:22.090-05:00",
          "display_amount": "-$10.00"
        },
        {
          "id": 13,
          "source_type": "Spree::PromotionAction",
          "source_id": 2,
          "adjustable_type": "Spree::Shipment",
          "adjustable_id": 3,
          "amount": "-9.99",
          "label": "Shipping",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-12-02T11:35:22.076-05:00",
          "updated_at": "2019-12-02T11:35:22.076-05:00",
          "display_amount": "-$9.99"
        }
      ],
      "stock_location_address": "NY Warehouse, Washington, AL",
      "country_iso": "US",
      "international_shipping": false,
      "delivery_estimation": "Dec 04"
    }
  ],
  "adjustments": [
    {
      "id": 15,
      "source_type": "Spree::Promotion",
      "source_id": 2,
      "adjustable_type": "Spree::Order",
      "adjustable_id": 3,
      "amount": "20.0",
      "label": "adj1",
      "promotion_code_id": null,
      "finalized": false,
      "eligible": true,
      "created_at": "2019-12-02T11:35:22.102-05:00",
      "updated_at": "2019-12-02T11:35:22.102-05:00",
      "display_amount": "$20.00"
    },
    {
      "id": 16,
      "source_type": "Spree::Promotion",
      "source_id": 2,
      "adjustable_type": "Spree::Order",
      "adjustable_id": 3,
      "amount": "30.0",
      "label": "adj2",
      "promotion_code_id": null,
      "finalized": false,
      "eligible": true,
      "created_at": "2019-12-02T11:35:22.108-05:00",
      "updated_at": "2019-12-02T11:35:22.108-05:00",
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
GET /api/orders/M783310317
Accept: application/json
Authorizat IO N: ae48544f28a81839fcc034655b0c204a1b4ba87a2f00be42
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
X-Request-Id: db0b5707-68c3-4c59-8fb3-b4f325646074
X-Runtime: 0.015937
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
user[email]=email10%40example.com
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
X-Request-Id: 420c6aae-9ea2-467b-9fb1-1b8a6938cb9c
X-Runtime: 0.021508
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
user[email]=email11%40example.com&user[password]=secret
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
Authorization: Bearer b9e467ae37b47ad0a77b74ebc3780a9983b2dd85c16a12d8
ETag: W/&quot;88fdce6e2dc90f7a39f7fdee1d240e21&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 0990c564-da20-4426-884c-7b0cd1d95a60
X-Runtime: 0.007651
Vary: Origin
Content-Length: 562
200 OK
```


```json
{
  "id": 12,
  "email": "email11@example.com",
  "persistence_token": null,
  "perishable_token": null,
  "last_request_at": null,
  "login": "email11@example.com",
  "ship_address_id": null,
  "bill_address_id": null,
  "created_at": "2019-12-02T11:35:24.481-05:00",
  "updated_at": "2019-12-02T11:35:24.483-05:00",
  "spree_api_key": "b9e467ae37b47ad0a77b74ebc3780a9983b2dd85c16a12d8",
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
X-Request-Id: 7720bac6-8199-4409-aae5-a59a77b8e88b
X-Runtime: 0.002344
Vary: Origin
204 No Content
```




# Products

get products by taxon

## Fetch a single product by id


### Request

#### Endpoint

```plaintext
GET /api/products/product-14-2013
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
Date: Mon, 02 Dec 2019 16:35:23 GMT
Surrogate-Control: max-age=900
Surrogate-Key: product_id=1
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;d45c18b9e5c5d815e2fe704211e1e657&quot;
X-Request-Id: 1d99d940-2301-420d-98ae-92a711fbc964
X-Runtime: 0.057057
Vary: Origin
Content-Length: 1521
200 OK
```


```json
{
  "id": 14,
  "name": "Product #14 - 2013",
  "description": "As seen on TV!",
  "available_on": "2018-12-02T11:35:23.757-05:00",
  "slug": "product-14-2013",
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
  "trends": [

  ],
  "breadcrumb_taxons": [
    {
      "id": 8,
      "name": "Clothing",
      "taxonomy_id": 3,
      "created_at": "2019-12-02T11:35:23.696-05:00",
      "url": "/category/clothing",
      "position": 1
    },
    {
      "id": 9,
      "name": "Girl",
      "taxonomy_id": 3,
      "created_at": "2019-12-02T11:35:23.718-05:00",
      "url": "/category/clothing/girl",
      "position": 2
    },
    {
      "id": 10,
      "name": "Dresses",
      "taxonomy_id": 3,
      "created_at": "2019-12-02T11:35:23.737-05:00",
      "url": "/category/clothing/girl/dresses",
      "position": 3
    }
  ],
  "has_variants": false,
  "master": {
    "id": 23,
    "name": "Product #14 - 2013",
    "sku": "SKU-23",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": true,
    "slug": "product-14-2013",
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
Date: Mon, 02 Dec 2019 16:35:23 GMT
Surrogate-Control: max-age=900
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;4df04108ce3fbfd459932ad49e02dc0e&quot;
X-Request-Id: e70fe05f-6dea-4d0b-9912-01ca41dde95a
X-Runtime: 0.039436
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
      "id": 15,
      "name": "Product #15 - 3135",
      "description": "As seen on TV!",
      "available_on": "2018-12-02T11:35:23.925-05:00",
      "slug": "product-15-3135",
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
      "trends": [

      ],
      "breadcrumb_taxons": [

      ],
      "has_variants": false,
      "master": {
        "id": 24,
        "name": "Product #15 - 3135",
        "sku": "SKU-24",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-15-3135",
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
Date: Mon, 02 Dec 2019 16:35:24 GMT
Surrogate-Control: max-age=900
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;63c4c6bcd439029579552ae21a5a21e9&quot;
X-Request-Id: d43df603-5382-489d-9b13-8958321cf969
X-Runtime: 0.025004
Vary: Origin
Content-Length: 237
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
      "id": 16,
      "name": "Product #16 - 4786",
      "slug": "product-16-4786",
      "display_price": "$19.99",
      "brand": null,
      "brand_slug": null,
      "brand_description": null,
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
GET /api/products?ids=18%2C19%2C20
Host: example.org
Cookie: 
```

`GET /api/products`

#### Parameters


```json
ids: 18,19,20
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
Date: Mon, 02 Dec 2019 16:35:24 GMT
Surrogate-Control: max-age=900
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;438351b910a00aca786070162d0f0bd2&quot;
X-Request-Id: 23fac90c-f40f-4fdc-b83f-aca698a5666f
X-Runtime: 0.097344
Vary: Origin
Content-Length: 2586
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
      "id": 18,
      "name": "Product #18 - 6141",
      "description": "As seen on TV!",
      "available_on": "2018-12-02T11:35:24.198-05:00",
      "slug": "product-18-6141",
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
      "trends": [

      ],
      "breadcrumb_taxons": [

      ],
      "has_variants": false,
      "master": {
        "id": 27,
        "name": "Product #18 - 6141",
        "sku": "SKU-27",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-18-6141",
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
      "id": 19,
      "name": "Product #19 - 3761",
      "description": "As seen on TV!",
      "available_on": "2018-12-02T11:35:24.249-05:00",
      "slug": "product-19-3761",
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
      "trends": [

      ],
      "breadcrumb_taxons": [

      ],
      "has_variants": false,
      "master": {
        "id": 28,
        "name": "Product #19 - 3761",
        "sku": "SKU-28",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-19-3761",
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
      "id": 20,
      "name": "Product #20 - 3650",
      "description": "As seen on TV!",
      "available_on": "2018-12-02T11:35:24.299-05:00",
      "slug": "product-20-3650",
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
      "trends": [

      ],
      "breadcrumb_taxons": [

      ],
      "has_variants": false,
      "master": {
        "id": 29,
        "name": "Product #20 - 3650",
        "sku": "SKU-29",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-20-3650",
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
ETag: W/&quot;337e62d1b62ef4043b3b37ddcc72a764&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 7a336d09-e0b8-4314-a96d-ba8ae7105c5d
X-Runtime: 0.038053
Vary: Origin
Content-Length: 1203
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
      "id": 13,
      "name": "Product #13 - 4292",
      "description": "As seen on TV!",
      "available_on": "2018-12-02T11:35:23.555-05:00",
      "slug": "product-13-4292",
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
      "trends": [

      ],
      "breadcrumb_taxons": [

      ],
      "has_variants": false,
      "master": {
        "id": 22,
        "name": "Product #13 - 4292",
        "sku": "SKU-22",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-13-4292",
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
ETag: W/&quot;7a63dceecb114d1a59b4c859792673cf&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 9307c93b-9c9d-4e72-bcaa-6a5eabae26b2
X-Runtime: 0.058121
Vary: Origin
Content-Length: 1203
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
      "id": 11,
      "name": "Product #11 - 6648",
      "description": "As seen on TV!",
      "available_on": "2018-12-02T11:35:23.296-05:00",
      "slug": "product-11-6648",
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
      "trends": [

      ],
      "breadcrumb_taxons": [

      ],
      "has_variants": false,
      "master": {
        "id": 20,
        "name": "Product #11 - 6648",
        "sku": "SKU-20",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-11-6648",
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
X-Request-Id: 5cf4eb9e-d847-45e1-9865-ccd1f53e2cea
X-Runtime: 0.013470
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
GET /api/recently_viewed?recently_viewed[session_id]=mdr4evn135p22pymxkrwq5mpby9cado0rmrj1z2ok0np6zf4c8qwjhnizwftnefo5ywkd9hnj97eu9abap2x9smpdeqjl3d6q5cburd25l6brrqmgtnpbkqjn9edqd1jprwe8oevah8yijdzmt7pj7sohurykhgy0i4y83m48seyg500zuh0nmdss6g3pvbmfvb4jsltww2fnkdg4gynngljm8cce46y21s3np3ip68j6boeyj1i0d9tc0ls5dh&amp;recently_viewed[user_id]=95002
Accept: application/json
Host: example.org
Cookie: 
```

`GET /api/recently_viewed`

#### Parameters


```json
recently_viewed: {&quot;session_id&quot;=&gt;&quot;mdr4evn135p22pymxkrwq5mpby9cado0rmrj1z2ok0np6zf4c8qwjhnizwftnefo5ywkd9hnj97eu9abap2x9smpdeqjl3d6q5cburd25l6brrqmgtnpbkqjn9edqd1jprwe8oevah8yijdzmt7pj7sohurykhgy0i4y83m48seyg500zuh0nmdss6g3pvbmfvb4jsltww2fnkdg4gynngljm8cce46y21s3np3ip68j6boeyj1i0d9tc0ls5dh&quot;, &quot;user_id&quot;=&gt;&quot;95002&quot;}
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
ETag: W/&quot;f863e51bab4dc3d6c87fbe62f6beb56b&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 2e988a63-2ffe-4361-9021-3d0dcf7eeb68
X-Runtime: 0.003048
Vary: Origin
Content-Length: 119
200 OK
```


```json
[
  {
    "at": "2019-12-02T11:35:28.758-05:00",
    "variant_id": "var1"
  },
  {
    "at": "2019-12-02T11:40:28.758-05:00",
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
recently_viewed[session_id]=r1zonmng0prnoyy0wo6pwbyjj3osfli27uayr4wo112zxtmk4qx1207ts0szkp281fad59idajl6a0iwau97xr3xdv5j36neshz1j9yjhdivia1fb9ofqspj5vx8wh62ffyxqn2i8qkfjgyhfviw2h819x2vqrfsv73rxe8ov79dpy3yu5hqct25okyhp73jlufsya1msa627cwskryesvo8cy4yb1ioz0kvb24xx46kyx2pjt8zqluc3yo1l0g&recently_viewed[user_id]=94875&recently_viewed[variant_id]=foo
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
X-Request-Id: 801d592c-a2f0-49e0-b5ee-0f6d44397db7
X-Runtime: 0.021691
Vary: Origin
204 No Content
```




# Return Authorizations

Get user return authorizations

## Can get another user&#39;s return authorization


### Request

#### Endpoint

```plaintext
GET /api/returns/RA364047884
Authorizat IO N: Bearer e7083ba8fb54d3e7650844a6f07dd311f11b619206818307
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
ETag: W/&quot;d8f56e84dfb32b3c7b9b4740d4872f35&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 241d4d61-e172-48e9-ab73-d66f0c94dac1
X-Runtime: 0.032734
Vary: Origin
Content-Length: 2859
200 OK
```


```json
{
  "id": 4,
  "number": "RA364047884",
  "state": "authorized",
  "order_id": 10,
  "memo": "Items were broken",
  "created_at": "2019-12-02T11:35:27.162-05:00",
  "updated_at": "2019-12-02T11:35:27.162-05:00",
  "reason": {
    "id": 7,
    "name": "Defect #7",
    "active": true,
    "mutable": true,
    "created_at": "2019-12-02T11:35:27.159-05:00",
    "updated_at": "2019-12-02T11:35:27.159-05:00",
    "mirakl_code": null
  },
  "order": {
    "id": 10,
    "number": "M935576057",
    "item_total": "10.0",
    "total": "110.0",
    "state": "complete",
    "adjustment_total": "0.0",
    "user_id": 41,
    "completed_at": "2019-12-02T11:35:27.094-05:00",
    "bill_address_id": 20,
    "ship_address_id": 21,
    "payment_total": "110.0",
    "shipment_state": "shipped",
    "payment_state": "paid",
    "email": "email40@example.com",
    "special_instructions": null,
    "created_at": "2019-12-02T11:35:27.021-05:00",
    "updated_at": "2019-12-02T11:35:27.139-05:00",
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
    "guest_token": "T4XpSdz0Gp8EFBZbqm5XBw",
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
    "id": 21,
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
  },
  "bill_address": {
    "id": 20,
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
  },
  "return_items": [
    {
      "name": "Product #28 - 3730",
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
        "id": 7,
        "month": "12",
        "year": "2020",
        "cc_type": null,
        "last_digits": "1111",
        "name": "Spree Commerce",
        "gateway_customer_profile_id": "BGS-221322",
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
Authorizat IO N: Bearer 0db9ffedf775a46107640c8e7a858f512698e6330cbcdb73
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
ETag: W/&quot;235e1c7a16a278aa82938f83137919cc&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 22197cdb-a897-46fd-8456-1e494e70ae41
X-Runtime: 0.013506
Vary: Origin
Content-Length: 169
200 OK
```


```json
{
  "return_authorizations": [
    {
      "number": "RA246026272",
      "created_at": "2019-12-02T11:35:26.076-05:00",
      "return_amount": "10.0",
      "order_number": "M025263425",
      "state": "authorized"
    }
  ]
}
```



## returns a 200


### Request

#### Endpoint

```plaintext
GET /api/returns/RA422847518
Authorizat IO N: Bearer f9952eb3237c8227020a5b400c549becd8bb1939f885f9f4
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
ETag: W/&quot;21070113013c36224664a253bafeb748&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 58cb437c-74c4-4d80-bfa6-76c1b3cae1e1
X-Runtime: 0.039533
Vary: Origin
Content-Length: 2779
200 OK
```


```json
{
  "id": 2,
  "number": "RA422847518",
  "state": "authorized",
  "order_id": 8,
  "memo": "Items were broken",
  "created_at": "2019-12-02T11:35:26.445-05:00",
  "updated_at": "2019-12-02T11:35:26.445-05:00",
  "reason": {
    "id": 3,
    "name": "Defect #3",
    "active": true,
    "mutable": true,
    "created_at": "2019-12-02T11:35:26.442-05:00",
    "updated_at": "2019-12-02T11:35:26.442-05:00",
    "mirakl_code": null
  },
  "order": {
    "id": 8,
    "number": "M841513905",
    "item_total": "10.0",
    "total": "110.0",
    "state": "complete",
    "adjustment_total": "0.0",
    "user_id": 38,
    "completed_at": "2019-12-02T11:35:26.378-05:00",
    "bill_address_id": 16,
    "ship_address_id": 17,
    "payment_total": "110.0",
    "shipment_state": "shipped",
    "payment_state": "paid",
    "email": "email37@example.com",
    "special_instructions": null,
    "created_at": "2019-12-02T11:35:26.304-05:00",
    "updated_at": "2019-12-02T11:35:26.422-05:00",
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
    "guest_token": "XjvwmRNAIqWIlrQlRLsjeQ",
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
    "id": 17,
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
  "bill_address": {
    "id": 16,
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
  "return_items": [
    {
      "name": "Product #26 - 1427",
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
        "id": 5,
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
GET /api/returns/RA502085823
Authorizat IO N: Bearer 0586d0014120da0ff0b7cfcafddeb8c271704280bd0b025e
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
X-Request-Id: 01352f8a-3cbb-48d5-9999-3f373e48be22
X-Runtime: 0.005537
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
stock_request[email]=audrey_bogisich%40feil.us&stock_request[variant_id]=35
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
X-Request-Id: 87b0e810-cc72-46a9-aac1-b77188b883f3
X-Runtime: 0.003753
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
stock_request[email]=foo&stock_request[variant_id]=33
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
X-Request-Id: 128c8a48-37bd-4c8b-8654-f9c61dd23a72
X-Runtime: 0.024635
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
stock_request[email]=romona.hermiston%40torpstroman.info&stock_request[variant_id]=37
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
X-Request-Id: 5a0285ac-c373-4304-bced-bb7c72bea7e1
X-Runtime: 0.003687
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
Authorizat IO N: Bearer efc3d5847cbc609163b5e83b376e834b722b6ee930d7aa43
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
ETag: W/&quot;49daa629d761e6121fed142f897f3a33&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 9f3a3de8-6527-4262-a26d-634b3ca4d749
X-Runtime: 0.035182
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
      "created_at": "2019-12-02T11:35:27.270-05:00"
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

Destroy a subscriber. Users can destroy their own subscriber, admins can destroy any.

## Create a subscriber


### Request

#### Endpoint

```plaintext
POST /api/subscribers
Accept: application/json
Authorizat IO N: Bearer 69f77a3593881a6b2c1ca4b7068b12dfff97c9c5a8acf8d5
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/subscribers`

#### Parameters


```json
subscriber[email]=shizuko_murazik%40terry.biz&subscriber[user_id]=15&subscriber[first_name]=Albert&subscriber[last_name]=Bergnaum&subscriber[status]=subscribed
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
ETag: W/&quot;d89b32d71a9802a00d64c638b9f637d6&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: f75220c2-71e4-497f-aef0-0f1d7a5a731f
X-Runtime: 0.011767
Vary: Origin
Content-Length: 181
201 Created
```


```json
{
  "id": 4,
  "user_id": 15,
  "email": "shizuko_murazik@terry.biz",
  "first_name": "Albert",
  "last_name": "Bergnaum",
  "source": "",
  "status": "subscribed",
  "created_at": "2019-12-02T11:35:24.547-05:00"
}
```



## Delete a subscriber


### Request

#### Endpoint

```plaintext
DELETE /api/subscribers/3
Accept: application/json
Authorizat IO N: Bearer 948bdecb7456118fa75f95f1b8c9057058af4d18240426f3
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
X-Request-Id: 599c1c13-4aae-4842-8103-71c369ac55fa
X-Runtime: 0.023570
Vary: Origin
204 No Content
```




## Get a single subscriber by id


### Request

#### Endpoint

```plaintext
GET /api/subscribers/5
Accept: application/json
Authorizat IO N: Bearer 71e9a7e4791b63c9c22eb117c093d1de4528c7eeea408f71
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
ETag: W/&quot;9cc3db1a7e1aa7cd9c65e7b7f666b594&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: d28db064-00ce-4f3e-b8b6-cf4a76bffcc3
X-Runtime: 0.005953
Vary: Origin
Content-Length: 176
200 OK
```


```json
{
  "id": 5,
  "user_id": 16,
  "email": "joelle@krajcik.info",
  "first_name": "Veronique",
  "last_name": "Corwin",
  "source": "",
  "status": "subscribed",
  "created_at": "2019-12-02T11:35:24.562-05:00"
}
```



## Get all subscribers


### Request

#### Endpoint

```plaintext
GET /api/subscribers
Accept: application/json
Authorizat IO N: Bearer 36efbe25f5d22138fca74296e4fe4275d1d98cd57f51383d
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
ETag: W/&quot;37b01643901c124a088acb136b6169e9&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: b19640b1-ea18-4d9b-9e1d-899a89b82fc8
X-Runtime: 0.008555
Vary: Origin
Content-Length: 613
200 OK
```


```json
{
  "subscribers": [
    {
      "id": 7,
      "user_id": null,
      "email": "clotilde@heathcote.info",
      "first_name": "Jody",
      "last_name": "Doyle",
      "source": "",
      "status": "subscribed",
      "created_at": "2019-12-02T11:35:24.587-05:00"
    },
    {
      "id": 8,
      "user_id": null,
      "email": "eric_langosh@kuvalis.ca",
      "first_name": "Kathy",
      "last_name": "Braun",
      "source": "",
      "status": "subscribed",
      "created_at": "2019-12-02T11:35:24.588-05:00"
    },
    {
      "id": 9,
      "user_id": null,
      "email": "burton@christiansen.us",
      "first_name": "Tisa",
      "last_name": "Fay",
      "source": "",
      "status": "subscribed",
      "created_at": "2019-12-02T11:35:24.589-05:00"
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
Authorizat IO N: Bearer 7378a92399686810f6072c62c2da6391b35ab33410fdfed4
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
ETag: W/&quot;cf1c18b06655444ebf9cd4d31cabb626&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 84a17d46-4255-437b-abb6-feba3b859581
X-Runtime: 0.006584
Vary: Origin
Content-Length: 182
200 OK
```


```json
{
  "id": 6,
  "user_id": 17,
  "email": "sam@bradtkegleichner.biz",
  "first_name": "Tara",
  "last_name": "Hodkiewicz",
  "source": "",
  "status": "unsubscribed",
  "created_at": "2019-12-02T11:35:24.576-05:00"
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
X-Request-Id: 1d582255-6113-4812-ad52-de691bc597ab
X-Runtime: 0.029670
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
X-Request-Id: cb017055-093c-463f-b878-8bd6a83c75ce
X-Runtime: 0.011043
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
X-Request-Id: 6b8fe519-ac21-4bdb-a6d7-e82266b9cdaa
X-Runtime: 0.021764
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
X-Request-Id: c664d665-9725-46f8-aaff-1817ed3ed5d8
X-Runtime: 0.005921
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
user[email]=email4%40example.com&user[password]=secret
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
Authorization: Bearer d1407f7223cf09eeb6c977a50411f574b890f95fc7207aad
ETag: W/&quot;e2ae62851977d94ddf47bd3cd0da4ab8&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 9e447b5a-da6d-4f24-a3b3-e1062611b277
X-Runtime: 0.027505
Vary: Origin
Content-Length: 559
200 OK
```


```json
{
  "id": 5,
  "email": "email4@example.com",
  "persistence_token": null,
  "perishable_token": null,
  "last_request_at": null,
  "login": "email4@example.com",
  "ship_address_id": null,
  "bill_address_id": null,
  "created_at": "2019-12-02T11:35:20.214-05:00",
  "updated_at": "2019-12-02T11:35:20.215-05:00",
  "spree_api_key": "d1407f7223cf09eeb6c977a50411f574b890f95fc7207aad",
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
X-Spree-Order-Token: kUEYjxtDxF1PnLmu2e8vCw
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/users/login`

#### Parameters


```json
user[email]=email5%40example.com&user[password]=secret&order_number=M359063560
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
Authorization: Bearer 116ee939f418d49f904a282d568140191bcf689c98972a7b
ETag: W/&quot;c89bf64e7b36bf3c9d6ffc5195acea76&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 24c2c1da-234a-4275-b9ed-d2e638658229
X-Runtime: 0.010497
Vary: Origin
Content-Length: 559
200 OK
```


```json
{
  "id": 6,
  "email": "email5@example.com",
  "persistence_token": null,
  "perishable_token": null,
  "last_request_at": null,
  "login": "email5@example.com",
  "ship_address_id": null,
  "bill_address_id": null,
  "created_at": "2019-12-02T11:35:20.248-05:00",
  "updated_at": "2019-12-02T11:35:20.250-05:00",
  "spree_api_key": "116ee939f418d49f904a282d568140191bcf689c98972a7b",
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
Authorizat IO N: Bearer f4aa2eb27daab2a20ab50fc18179280d143a172d66941b34
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
Authorization: Bearer f4aa2eb27daab2a20ab50fc18179280d143a172d66941b34
ETag: W/&quot;59c3ad2b7be03839d70d0feb5139d1d1&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 1ebbabc5-1d17-4199-b688-7b70b7542115
X-Runtime: 0.025133
Vary: Origin
Content-Length: 1511
200 OK
```


```json
{
  "email": "email2@example.com",
  "first_name": null,
  "last_name": null,
  "id": 2,
  "subscribed": false,
  "addresses": [
    {
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
      "default": true
    },
    {
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
        "created_at": "2019-12-02T11:35:20.062-05:00",
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
        "created_at": "2019-12-02T11:35:20.105-05:00",
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
        "created_at": "2019-12-02T11:35:20.148-05:00",
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
Authorization: Bearer 2f4354ad68cac39d82b99992d858d8552b321e20427eff94
ETag: W/&quot;c7952213730f6eef1f832ee391e73d34&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 03b3d59f-e0fa-468e-ab66-128453475a04
X-Runtime: 0.010956
Vary: Origin
Content-Length: 184
201 Created
```


```json
{
  "id": 4,
  "email": "test@example.com",
  "created_at": "2019-12-02T11:35:20.204-05:00",
  "updated_at": "2019-12-02T11:35:20.206-05:00",
  "subscribed": false,
  "bill_address": null,
  "ship_address": null
}
```



## Subscribe a user


### Request

#### Endpoint

```plaintext
PUT /api/users/3/subscribe
Authorizat IO N: Bearer 9f10b882370d536852caf1b23febbf0b47983b2d6b7e95ed
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
Authorization: Bearer 9f10b882370d536852caf1b23febbf0b47983b2d6b7e95ed
ETag: W/&quot;18485839bd2441c140c97f584583b1a4&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 708393f4-8faf-4323-a4ac-907df1b8c7df
X-Runtime: 0.010226
Vary: Origin
Content-Length: 185
200 OK
```


```json
{
  "id": 3,
  "email": "email3@example.com",
  "created_at": "2019-12-02T11:35:20.181-05:00",
  "updated_at": "2019-12-02T11:35:20.183-05:00",
  "subscribed": true,
  "bill_address": null,
  "ship_address": null
}
```



## Unsubscribe a user


### Request

#### Endpoint

```plaintext
PUT /api/users/1/unsubscribe
Authorizat IO N: Bearer a2c5dfd9aab8c25a5b4a078b6b436fc3a59db5c25b2f7654
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
Authorization: Bearer a2c5dfd9aab8c25a5b4a078b6b436fc3a59db5c25b2f7654
ETag: W/&quot;7cfb2f4a7e288d80deb9cd08ad7eb4bc&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 2c316995-1a31-4378-b71d-0458d011e84b
X-Runtime: 0.172930
Vary: Origin
Content-Length: 186
200 OK
```


```json
{
  "id": 1,
  "email": "email1@example.com",
  "created_at": "2019-12-02T11:35:19.613-05:00",
  "updated_at": "2019-12-02T11:35:19.615-05:00",
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
GET /api/variants/31
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
ETag: W/&quot;781c9962e94161b3fcf2c7cfbd75123e&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: f8b506bd-3009-4349-a35f-8e1344c11ddb
X-Runtime: 0.096700
Vary: Origin
Content-Length: 1934
200 OK
```


```json
{
  "id": 31,
  "name": "Product #21 - 1866",
  "sku": "SKU-30",
  "weight": "0.0",
  "height": null,
  "width": null,
  "depth": null,
  "is_master": false,
  "slug": "product-21-1866",
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
      "attachment_updated_at": "2019-12-02T11:35:24.780-05:00",
      "attachment_width": 489,
      "attachment_height": 490,
      "alt": null,
      "viewable_type": "Spree::Variant",
      "viewable_id": 31,
      "mini_url": "/spree/products/1/mini/thinking-cat.jpg?1575304524",
      "small_url": "/spree/products/1/small/thinking-cat.jpg?1575304524",
      "product_url": "/spree/products/1/product/thinking-cat.jpg?1575304524",
      "large_url": "/spree/products/1/large/thinking-cat.jpg?1575304524"
    }
  ],
  "variant_properties": [

  ],
  "stock_items": [

  ],
  "prices": [
    {
      "id": 30,
      "vendor_id": 68,
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
      "id": 31,
      "vendor_id": 69,
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
Authorizat IO N: Bearer 6feebc81792af81d72c7d70648e4d96261099dd1f34ba4f7
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
ETag: W/&quot;de32b2730b050075cf10de11f9e306b9&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: c3f40010-880e-4d44-a94c-eea423fe37f4
X-Runtime: 0.031455
Vary: Origin
Content-Length: 206
200 OK
```


```json
[
  {
    "id": 4,
    "user_id": 48,
    "payment_source_type": "SolidusPaypalBraintree::Source",
    "payment_source_id": 4,
    "default": false,
    "created_at": "2019-12-02T11:35:28.631-05:00",
    "updated_at": "2019-12-02T11:35:28.631-05:00"
  }
]
```



## Remove the payment from the user wallet


### Request

#### Endpoint

```plaintext
DELETE /api/wallet_payment_sources/5
Accept: application/json
Authorizat IO N: Bearer f2dc32a6961173bb1ed069104782dd7cbb9ed0d9449823f8
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
X-Request-Id: 3070273b-8e0f-4dea-9de6-2945b7a06aed
X-Runtime: 0.010622
Vary: Origin
204 No Content
```




## Set a wallet payment source as the default user payment method


### Request

#### Endpoint

```plaintext
POST /api/wallet_payment_sources/6/default
Accept: application/json
Authorizat IO N: Bearer 3d5ff29de9a559cf175fea2113ba74a72afc38a4172ef33f
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
X-Request-Id: 59c15b85-4ee6-41f0-968c-8deeb8110d54
X-Runtime: 0.008643
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
Authorizat IO N: Bearer 9325a28b67a67f8cb4e3f704433aab042f0d1139d087263a
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/wished_products`

#### Parameters


```json
wished_product[wishlist_id]=40&wished_product[variant_id]=135&wished_product[quantity]=2&wished_product[remark]=Foo+bar
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
ETag: W/&quot;8fafe8196601dc1db683f6891854a01c&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 06511bc1-4da4-4c47-ba53-976ae8d679bf
X-Runtime: 0.010660
Vary: Origin
Content-Length: 75
201 Created
```


```json
{
  "id": 31,
  "wishlist_id": 40,
  "variant_id": 135,
  "quantity": 2,
  "remark": "Foo bar"
}
```



## Delete a wished product


### Request

#### Endpoint

```plaintext
DELETE /api/wished_products/28
Accept: application/json
Authorizat IO N: Bearer 32dab5b83981b3a235cb216a8bd3533c71ce2bbe13efc606
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
X-Request-Id: 9291949c-b9f0-4b96-8b68-f8b01b56be71
X-Runtime: 0.010873
Vary: Origin
204 No Content
```




## Get a single wished product


### Request

#### Endpoint

```plaintext
GET /api/wished_products/22
Accept: application/json
Authorizat IO N: Bearer 2bd4b46ac035520c3cae29e40099a8fd0b8f21f5cf8fb99c
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
ETag: W/&quot;118780e1007b54c933022127212752b9&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: f1223b40-dbd6-4a67-9642-97ea553ad466
X-Runtime: 0.010203
Vary: Origin
Content-Length: 70
200 OK
```


```json
{
  "id": 22,
  "wishlist_id": 37,
  "variant_id": 115,
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
Authorizat IO N: Bearer b494521934c32cca4f6c3eeb64f1dbd0c4e2f2a81d97e0eb
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
ETag: W/&quot;7e85706513ed41feea9982668ce5bd21&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 1c13b478-cd2b-434c-8b9e-20cf7001d7af
X-Runtime: 0.037906
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
      "variant_id": 91,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 11,
      "wishlist_id": 30,
      "variant_id": 93,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 12,
      "wishlist_id": 31,
      "variant_id": 95,
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
Authorizat IO N: Bearer be3d720b915bb33030c27363f2b1a81c6abbbed7129bdfcc
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
ETag: W/&quot;a0fd5f8ba2bc1644a738d0c0de554cfa&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: bf1a4525-4a66-4448-aa71-768229d4a591
X-Runtime: 0.088106
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
      "variant_id": 97,
      "quantity": 1,
      "remark": null,
      "variant": {
        "id": 97,
        "name": "Product #54 - 2004",
        "sku": "SKU-96",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-54-2004",
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
      "id": 14,
      "wishlist_id": 33,
      "variant_id": 99,
      "quantity": 1,
      "remark": null,
      "variant": {
        "id": 99,
        "name": "Product #55 - 6564",
        "sku": "SKU-98",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-55-6564",
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
    },
    {
      "id": 15,
      "wishlist_id": 34,
      "variant_id": 101,
      "quantity": 1,
      "remark": null,
      "variant": {
        "id": 101,
        "name": "Product #56 - 2912",
        "sku": "SKU-100",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-56-2912",
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
Authorizat IO N: Bearer 9eddd6e38627791eca7d4af9f264e351cc26e7123293adca
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
ETag: W/&quot;f047991daabf8dcaf050106039ba6954&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: fbb33020-b62a-4d13-9d5e-b0f210e2658d
X-Runtime: 0.079925
Vary: Origin
Content-Length: 2095
200 OK
```


```json
{
  "wished_products": [
    {
      "id": 19,
      "wishlist_id": 36,
      "variant_id": 109,
      "quantity": 1,
      "remark": null,
      "variant": {
        "id": 109,
        "name": "Product #60 - 3736",
        "sku": "SKU-108",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-60-3736",
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
      "id": 20,
      "wishlist_id": 36,
      "variant_id": 111,
      "quantity": 1,
      "remark": null,
      "variant": {
        "id": 111,
        "name": "Product #61 - 5081",
        "sku": "SKU-110",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-61-5081",
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
    },
    {
      "id": 21,
      "wishlist_id": 36,
      "variant_id": 113,
      "quantity": 1,
      "remark": null,
      "variant": {
        "id": 113,
        "name": "Product #62 - 2551",
        "sku": "SKU-112",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-62-2551",
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
Authorizat IO N: Bearer 6cddcc131dbc1d4503fb57828a22f39684c1d60a61dbb135
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
ETag: W/&quot;fdad364b0d8e398bb6873b2925447d47&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 6987b561-fc41-41e1-82c0-f615ded45d30
X-Runtime: 0.009493
Vary: Origin
Content-Length: 301
200 OK
```


```json
{
  "wished_products": [
    {
      "id": 16,
      "wishlist_id": 35,
      "variant_id": 103,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 17,
      "wishlist_id": 35,
      "variant_id": 105,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 18,
      "wishlist_id": 35,
      "variant_id": 107,
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
PATCH /api/wished_products/25
Accept: application/json
Authorizat IO N: Bearer 4d08c3f97e7c224c371f1b75ded4354bdea90806ab799c9c
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/wished_products/:id`

#### Parameters


```json
wished_product[wishlist_id]=38&wished_product[variant_id]=127&wished_product[quantity]=2&wished_product[remark]=Foo+bar
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
ETag: W/&quot;9c075742bfcd493460a6901856e3479f&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: cbece571-5e52-41a0-9ede-9903ed7e8cbc
X-Runtime: 0.011943
Vary: Origin
Content-Length: 75
200 OK
```


```json
{
  "id": 25,
  "wishlist_id": 38,
  "variant_id": 127,
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
Authorizat IO N: Bearer 27bb835c9b45c97b554b2280c7e6365f3f5d7badb1c78f74
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/wishlists`

#### Parameters


```json
wishlist[name]&wishlist[user_id]=52&wishlist[is_default]=true&wishlist[is_public]=false
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
ETag: W/&quot;f47536141c545bfac998ff86b14ba94e&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: eb87d1e2-1a42-4bee-bfdb-3debccbe57ea
X-Runtime: 0.011435
Vary: Origin
Content-Length: 99
201 Created
```


```json
{
  "id": 2,
  "user_id": 52,
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
DELETE /api/wishlists/3
Accept: application/json
Authorizat IO N: Bearer 4dfc0e6d73d4210e9c480ad9261abc5736d3d31ff0b466cf
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
X-Request-Id: 3b08ffd5-9980-48dc-bf61-d5f8657ec1f5
X-Runtime: 0.010810
Vary: Origin
204 No Content
```




## Get a single wishlist


### Request

#### Endpoint

```plaintext
GET /api/wishlists/1
Accept: application/json
Authorizat IO N: Bearer bcf8ea5caba8ad801e15986e35ea2716766e9e4ab90e4baf
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
ETag: W/&quot;1669302449845b443ffdaf1555a8a78c&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 455a72ee-6827-41b4-a8b5-7ebd4ac2f1ad
X-Runtime: 0.034564
Vary: Origin
Content-Length: 302
200 OK
```


```json
{
  "id": 1,
  "user_id": 51,
  "name": "Wishlist #1",
  "is_public": false,
  "is_default": true,
  "wished_products": [
    {
      "id": 1,
      "wishlist_id": 1,
      "variant_id": 57,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 2,
      "wishlist_id": 1,
      "variant_id": 59,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 3,
      "wishlist_id": 1,
      "variant_id": 61,
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
Authorizat IO N: Bearer fe0585f664a8d7275cac6ac4e4bf84e19f9490dc0a6bb4b7
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
ETag: W/&quot;0b345a920e46681bf916dc36b778044e&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 7fc60931-0236-497b-869d-1892943ba8ba
X-Runtime: 0.011052
Vary: Origin
Content-Length: 884
200 OK
```


```json
{
  "wishlists": [
    {
      "id": 6,
      "user_id": 56,
      "name": "Wishlist #4",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 7,
      "user_id": 57,
      "name": "Wishlist #5",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 8,
      "user_id": 58,
      "name": "Wishlist #6",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 9,
      "user_id": 59,
      "name": "Wishlist #7",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 10,
      "user_id": 60,
      "name": "Wishlist #8",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 11,
      "user_id": 61,
      "name": "Wishlist #9",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 12,
      "user_id": 62,
      "name": "Wishlist #10",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 13,
      "user_id": 63,
      "name": "Wishlist #11",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 14,
      "user_id": 64,
      "name": "Wishlist #12",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 15,
      "user_id": 65,
      "name": "Wishlist #13",
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
Authorizat IO N: Bearer 8a3569dfb43ae7ceb73a2af215104d67c5b63f72f2b43352
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
ETag: W/&quot;9fcf044c46ffbaedd20cd3c15d5ad6f8&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 1d2720ae-f6ea-4c06-a654-c85b86120c8f
X-Runtime: 0.007483
Vary: Origin
Content-Length: 302
200 OK
```


```json
{
  "id": 5,
  "user_id": 55,
  "name": "Wishlist #3",
  "is_public": false,
  "is_default": true,
  "wished_products": [
    {
      "id": 7,
      "wishlist_id": 5,
      "variant_id": 69,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 8,
      "wishlist_id": 5,
      "variant_id": 71,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 9,
      "wishlist_id": 5,
      "variant_id": 73,
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
Authorizat IO N: Bearer 756aa7cdff4d465c68fd5fb4e0684c3a955f068f59d34cba
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
ETag: W/&quot;4cdd2f949386677a8ba3f28d44ffb457&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 7c208fea-c6ee-400a-a07d-d62a95d76c6a
X-Runtime: 0.009739
Vary: Origin
Content-Length: 903
200 OK
```


```json
{
  "wishlists": [
    {
      "id": 19,
      "user_id": 68,
      "name": "Wishlist #17",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 20,
      "user_id": 68,
      "name": "Wishlist #18",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 21,
      "user_id": 68,
      "name": "Wishlist #19",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 22,
      "user_id": 68,
      "name": "Wishlist #20",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 23,
      "user_id": 68,
      "name": "Wishlist #21",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 24,
      "user_id": 68,
      "name": "Wishlist #22",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 25,
      "user_id": 68,
      "name": "Wishlist #23",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 26,
      "user_id": 68,
      "name": "Wishlist #24",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 27,
      "user_id": 68,
      "name": "Wishlist #25",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 28,
      "user_id": 68,
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
PATCH /api/wishlists/4
Accept: application/json
Authorizat IO N: Bearer 80ab887a70e339572321b5180e7dbc5c74ac6232e7b0d764
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/wishlists/:id`

#### Parameters


```json
wishlist[name]=Another+Wishlist&wishlist[user_id]=54&wishlist[is_default]=true&wishlist[is_public]=false
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
ETag: W/&quot;c5b10c1946648cb9623cb843c9aa0e48&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 26a011bf-9b1d-4563-b829-69d2b32475c8
X-Runtime: 0.013083
Vary: Origin
Content-Length: 307
200 OK
```


```json
{
  "id": 4,
  "user_id": 54,
  "name": "Another Wishlist",
  "is_public": false,
  "is_default": true,
  "wished_products": [
    {
      "id": 4,
      "wishlist_id": 4,
      "variant_id": 63,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 5,
      "wishlist_id": 4,
      "variant_id": 65,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 6,
      "wishlist_id": 4,
      "variant_id": 67,
      "quantity": 1,
      "remark": null
    }
  ]
}
```



