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
PUT /api/orders/M126496271/addresses/2
Accept: application/json
X-Spree-Order-Token: 8kW_1ye-a8knS8bZZAU-PA
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
ETag: W/&quot;ed4572a53b8570dbe6303ebda79fcdfa&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: eb5a7eeb-7d21-4dce-a0e2-a3d5d163c274
X-Runtime: 0.074280
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
}
```



# Braintree transactions



## Creating a PayPal express checkout transaction


### Request

#### Endpoint

```plaintext
POST /api/braintree/transactions
Accept: application/json
X-Spree-Order-Token: mjQCw8ozAYo9v9RZrNiTCQ
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/braintree/transactions`

#### Parameters


```json
order_id=M237874734&payment_method_id=5&options[restart_checkout]=true&transaction[email]=maryellen.oga%40mckenziemcglynn.com&transaction[nonce]=fake-paypal-billing-agreement-nonce&transaction[phone]=555-555-0199&transaction[address_attributes][first_name]=John&transaction[address_attributes][last_name]=Stamm&transaction[address_attributes][address_line_1]=A+Different+Road&transaction[address_attributes][city]=Herndon&transaction[address_attributes][state_code]=AL&transaction[address_attributes][zip]=10009&transaction[address_attributes][country_code]=US&transaction[payment_type]=PayPalAccount
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
ETag: W/&quot;c422f3390ec044d476662a69ce5cfc62&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 4e382eb7-5b2f-4392-9e6c-6fddc1f79706
X-Runtime: 0.284799
Vary: Origin
Content-Length: 5307
200 OK
```


```json
{
  "id": 4,
  "number": "M237874734",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2019-12-13T08:19:21.999-05:00",
  "updated_at": "2019-12-13T08:19:22.241-05:00",
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
  "token": "mjQCw8ozAYo9v9RZrNiTCQ",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order&order=M237874734&bzip=10009&init=true",
  "payment_methods": [
    {
      "id": 5,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 13,
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
    "id": 13,
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
        "name": "Product #4 - 5299",
        "sku": "SKU-7",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-4-5299",
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
    {
      "id": 2,
      "source_type": "SolidusPaypalBraintree::Source",
      "source_id": 5,
      "amount": "110.0",
      "display_amount": "$110.00",
      "payment_method_id": 5,
      "state": "checkout",
      "avs_response": null,
      "created_at": "2019-12-13T08:19:22.092-05:00",
      "updated_at": "2019-12-13T08:19:22.092-05:00",
      "payment_method": {
        "id": 5,
        "name": "Braintree"
      },
      "source": {
        "id": 5,
        "payment_type": "PayPalAccount",
        "token": "bgx899",
        "created_at": "2019-12-13T08:19:22.091-05:00",
        "email": "jane.doe@paypal.com"
      }
    }
  ],
  "shipments": [
    {
      "id": 5,
      "tracking": null,
      "tracking_url": null,
      "number": "H13800320843",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M237874734",
      "stock_location_name": "NY Warehouse",
      "giftwrappable": false,
      "stock_location_id": 4,
      "giftwrap": null,
      "shipping_rates": [
        {
          "id": 5,
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
        "id": 5,
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
      "delivery_estimation": "Dec 17"
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
X-Spree-Order-Token: bd94LKzk8uLqCSSwF9FT0g
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/braintree/transactions`

#### Parameters


```json
order_id=M025684181&payment_method_id=4&options[restart_checkout]=true&transaction[email]=maryellen.oga%40mckenziemcglynn.com&transaction[nonce]=fake-apple-pay-visa-nonce&transaction[phone]=555-555-0199&transaction[address_attributes][first_name]=John&transaction[address_attributes][last_name]=Stamm&transaction[address_attributes][address_line_1]=A+Different+Road&transaction[address_attributes][city]=Herndon&transaction[address_attributes][state_code]=AL&transaction[address_attributes][zip]=10007&transaction[address_attributes][country_code]=US&transaction[payment_type]=ApplePayCard
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
ETag: W/&quot;c740c4c70672227b13244248937a1eaa&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 150bf0cf-f3f7-4610-9bf0-61f7a329662e
X-Runtime: 0.421285
Vary: Origin
Content-Length: 5353
200 OK
```


```json
{
  "id": 3,
  "number": "M025684181",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2019-12-13T08:19:21.312-05:00",
  "updated_at": "2019-12-13T08:19:21.642-05:00",
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
  "token": "bd94LKzk8uLqCSSwF9FT0g",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order&order=M025684181&bzip=10007&init=true",
  "payment_methods": [
    {
      "id": 4,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 10,
    "firstname": "John",
    "lastname": "Stamm",
    "full_name": "John Stamm",
    "address1": "A Different Road",
    "address2": null,
    "city": "Herndon",
    "zipcode": "10007",
    "phone": "555-555-0199",
    "company": null,
    "alternative_phone": null,
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
    "id": 10,
    "firstname": "John",
    "lastname": "Stamm",
    "full_name": "John Stamm",
    "address1": "A Different Road",
    "address2": null,
    "city": "Herndon",
    "zipcode": "10007",
    "phone": "555-555-0199",
    "company": null,
    "alternative_phone": null,
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
        "name": "Product #3 - 7679",
        "sku": "SKU-5",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-3-7679",
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
    {
      "id": 1,
      "source_type": "SolidusPaypalBraintree::Source",
      "source_id": 4,
      "amount": "110.0",
      "display_amount": "$110.00",
      "payment_method_id": 4,
      "state": "checkout",
      "avs_response": null,
      "created_at": "2019-12-13T08:19:21.442-05:00",
      "updated_at": "2019-12-13T08:19:21.442-05:00",
      "payment_method": {
        "id": 4,
        "name": "Braintree"
      },
      "source": {
        "id": 4,
        "payment_type": "ApplePayCard",
        "token": "cg7hsk",
        "created_at": "2019-12-13T08:19:21.441-05:00",
        "cc_type": "Apple Pay - Visa",
        "last_digits": "1881",
        "month": "12",
        "year": "2020"
      }
    }
  ],
  "shipments": [
    {
      "id": 3,
      "tracking": null,
      "tracking_url": null,
      "number": "H34161784468",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M025684181",
      "stock_location_name": "NY Warehouse",
      "giftwrappable": false,
      "stock_location_id": 3,
      "giftwrap": null,
      "shipping_rates": [
        {
          "id": 3,
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
        "id": 3,
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
      "delivery_estimation": "Dec 17"
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
PUT /api/checkouts/M189064281/complete
Accept: application/json
X-Spree-Order-Token: ACXXgelCFtbRA1Cva9e2Hg
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
ETag: W/&quot;a5d466623635812e330dc730f696b482&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 2a362765-02d7-4d45-b25f-02459f537b2e
X-Runtime: 0.403325
Vary: Origin
Content-Length: 5521
200 OK
```


```json
{
  "id": 22,
  "number": "M189064281",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "complete",
  "adjustment_total": "0.0",
  "user_id": 90,
  "created_at": "2019-12-13T08:19:36.843-05:00",
  "updated_at": "2019-12-13T08:19:37.161-05:00",
  "completed_at": "2019-12-13T08:19:37.161-05:00",
  "payment_total": "110.0",
  "shipment_state": "ready",
  "payment_state": "paid",
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
  "token": "ACXXgelCFtbRA1Cva9e2Hg",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order&order=M189064281&bzip=10040&init=true",
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
    "id": 43,
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
  "ship_address": {
    "id": 44,
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
  "line_items": [
    {
      "id": 23,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 133,
      "vendor_id": 236,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 133,
        "name": "Product #72 - 7361",
        "sku": "SKU-132",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-72-7361",
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
      "vendor_name": "Vendor #236",
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
      "created_at": "2019-12-13T08:19:36.927-05:00",
      "updated_at": "2019-12-13T08:19:37.032-05:00",
      "payment_method": {
        "id": 27,
        "name": "Braintree"
      },
      "source": {
        "id": 10,
        "payment_type": "CreditCard",
        "token": "4rptfz",
        "created_at": "2019-12-13T08:19:36.926-05:00",
        "cc_type": "Visa",
        "last_digits": "1881",
        "month": "12",
        "year": "2020"
      }
    }
  ],
  "shipments": [
    {
      "id": 26,
      "tracking": "U10000",
      "tracking_url": null,
      "number": "H23775032433",
      "cost": "100.0",
      "shipped_at": null,
      "state": "ready",
      "order_id": "M189064281",
      "stock_location_name": "NY Warehouse",
      "giftwrappable": false,
      "stock_location_id": 48,
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
              "id": 22,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 41,
              "name": "ShippingCategory #40"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 133,
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
      "delivery_estimation": "Dec 17"
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
PATCH /api/checkouts/M557136367
Accept: application/json
X-Spree-Order-Token: IcyKT6a4rNvoQbhTc1rD9A
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
ETag: W/&quot;4e426495bc725f35029dbcc4b806ff30&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 60218538-bad6-4350-8d05-e8ac8102ea0d
X-Runtime: 0.122158
Vary: Origin
Content-Length: 4902
200 OK
```


```json
{
  "id": 20,
  "number": "M557136367",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 88,
  "created_at": "2019-12-13T08:19:35.888-05:00",
  "updated_at": "2019-12-13T08:19:36.116-05:00",
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
  "token": "IcyKT6a4rNvoQbhTc1rD9A",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order&order=M557136367&bzip=10037&init=true",
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
      "id": 21,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 129,
      "vendor_id": 226,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 129,
        "name": "Product #70 - 1358",
        "sku": "SKU-128",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-70-1358",
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
        "product_id": 70,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [

      ],
      "vendor_name": "Vendor #226",
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
      "number": "H27522740403",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M557136367",
      "stock_location_name": "NY Warehouse",
      "giftwrappable": false,
      "stock_location_id": 46,
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
              "id": 20,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 39,
              "name": "ShippingCategory #38"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 129,
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
      "delivery_estimation": "Dec 17"
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
PATCH /api/checkouts/M668689736
Accept: application/json
X-Spree-Order-Token: LH3kWNZhtbiljFFQ8Vj0wQ
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
ETag: W/&quot;523da814d6737cd5399182103295b4df&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 30e7fe95-1828-4930-bbae-55239f6f9cf0
X-Runtime: 0.126071
Vary: Origin
Content-Length: 4902
200 OK
```


```json
{
  "id": 18,
  "number": "M668689736",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 86,
  "created_at": "2019-12-13T08:19:34.776-05:00",
  "updated_at": "2019-12-13T08:19:34.985-05:00",
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
  "token": "LH3kWNZhtbiljFFQ8Vj0wQ",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order&order=M668689736&bzip=10033&init=true",
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
    "country_id": 39,
    "country_iso": "US",
    "state_id": 39,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 39,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 39,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 39
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
    "country_id": 39,
    "country_iso": "US",
    "state_id": 39,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 39,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 39,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 39
    }
  },
  "line_items": [
    {
      "id": 19,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 125,
      "vendor_id": 216,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 125,
        "name": "Product #68 - 6696",
        "sku": "SKU-124",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-68-6696",
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
        "product_id": 68,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [

      ],
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
      "id": 20,
      "tracking": null,
      "tracking_url": null,
      "number": "H08668728451",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M668689736",
      "stock_location_name": "NY Warehouse",
      "giftwrappable": false,
      "stock_location_id": 44,
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
              "id": 18,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 37,
              "name": "ShippingCategory #36"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 125,
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
      "delivery_estimation": "Dec 17"
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
PATCH /api/checkouts/M014105495
Accept: application/json
X-Spree-Order-Token: 3FufIX3qHVTbP3NPWhTggA
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=25&order[payment_attributes][][source_attributes][nonce]=fake-valid-visa-nonce&order[payment_attributes][][source_attributes][payment_type]=CreditCard&order[payment_attributes][][source_attributes][reusable]=true
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
ETag: W/&quot;fed9e076a2afda2536a5a1b48bca58f9&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 0eeded4a-52b5-4230-8cf6-edb6f083f033
X-Runtime: 0.138188
Vary: Origin
Content-Length: 4902
200 OK
```


```json
{
  "id": 19,
  "number": "M014105495",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 87,
  "created_at": "2019-12-13T08:19:35.303-05:00",
  "updated_at": "2019-12-13T08:19:35.552-05:00",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "email86@example.com",
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
  "token": "3FufIX3qHVTbP3NPWhTggA",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order&order=M014105495&bzip=10035&init=true",
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
    "lastname": null,
    "full_name": "John",
    "address1": "A Different Road",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10036",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
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
      "id": 20,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 127,
      "vendor_id": 221,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 127,
        "name": "Product #69 - 5438",
        "sku": "SKU-126",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-69-5438",
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
      "vendor_name": "Vendor #221",
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
      "number": "H55502460136",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M014105495",
      "stock_location_name": "NY Warehouse",
      "giftwrappable": false,
      "stock_location_id": 45,
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
          "is_flat_rate": false,
          "is_flat_rate_expedited": false,
          "is_free_shipping": false,
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
              "id": 19,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 38,
              "name": "ShippingCategory #37"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 127,
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
      "delivery_estimation": "Dec 17"
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
PATCH /api/checkouts/M792563648
Accept: application/json
X-Spree-Order-Token: CAshzihDv1kpAQjdYRWMvg
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=23&order[payment_attributes][][source_attributes][wallet_payment_source_id]=7
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
ETag: W/&quot;bbb787721a9d5f25f3ee8d7c3e8b9163&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 2e89c2fb-c12f-4931-bb31-8081f29b79b2
X-Runtime: 0.132935
Vary: Origin
Content-Length: 4902
200 OK
```


```json
{
  "id": 17,
  "number": "M792563648",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 85,
  "created_at": "2019-12-13T08:19:34.244-05:00",
  "updated_at": "2019-12-13T08:19:34.484-05:00",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
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
  "gift_email": null,
  "gift_message": null,
  "is_gift": false,
  "display_item_total": "$10.00",
  "total_quantity": 1,
  "display_total": "$110.00",
  "display_ship_total": "$100.00",
  "display_tax_total": "$0.00",
  "token": "CAshzihDv1kpAQjdYRWMvg",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order&order=M792563648&bzip=10031&init=true",
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
      "id": 18,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 123,
      "vendor_id": 211,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 123,
        "name": "Product #67 - 9772",
        "sku": "SKU-122",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-67-9772",
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
        "product_id": 67,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [

      ],
      "vendor_name": "Vendor #211",
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
      "number": "H11665736211",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M792563648",
      "stock_location_name": "NY Warehouse",
      "giftwrappable": false,
      "stock_location_id": 43,
      "giftwrap": null,
      "shipping_rates": [
        {
          "id": 18,
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
        "id": 18,
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
              "id": 17,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 36,
              "name": "ShippingCategory #35"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 123,
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
      "delivery_estimation": "Dec 17"
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
PUT /api/checkouts/M926483097
Accept: application/json
X-Spree-Order-Token: _ux0Y4m3wTzl8mCppORYEQ
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PUT /api/checkouts/:id`

#### Parameters


```json
order[ship_address_attributes][id]&order[ship_address_attributes][firstname]=John&order[ship_address_attributes][lastname]&order[ship_address_attributes][address1]=10+Lovely+Street&order[ship_address_attributes][address2]=Northwest&order[ship_address_attributes][city]=Herndon&order[ship_address_attributes][zipcode]=10039&order[ship_address_attributes][phone]=555-555-0199&order[ship_address_attributes][state_name]&order[ship_address_attributes][alternative_phone]=555-555-0199&order[ship_address_attributes][company]=Company&order[ship_address_attributes][state_id]=42&order[ship_address_attributes][country_id]=42&order[ship_address_attributes][created_at]&order[ship_address_attributes][updated_at]&order[use_billing]=true&hold_state=true
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
ETag: W/&quot;0c699477e4a23f4beab35053442fb9fe&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: ca11be03-2a03-4d51-86e0-7fd28c627c35
X-Runtime: 0.134897
Vary: Origin
Content-Length: 4807
200 OK
```


```json
{
  "id": 21,
  "number": "M926483097",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "cart",
  "adjustment_total": "0.0",
  "user_id": 89,
  "created_at": "2019-12-13T08:19:36.421-05:00",
  "updated_at": "2019-12-13T08:19:36.515-05:00",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "email88@example.com",
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
  "token": "_ux0Y4m3wTzl8mCppORYEQ",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order&order=M926483097&bzip=10039&init=true",
  "payment_methods": [

  ],
  "bill_address": {
    "id": 42,
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
    "id": 42,
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
      "id": 22,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 131,
      "vendor_id": 231,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 131,
        "name": "Product #71 - 110",
        "sku": "SKU-130",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-71-110",
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
      "vendor_name": "Vendor #231",
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
      "number": "H78244420138",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M926483097",
      "stock_location_name": "NY Warehouse",
      "giftwrappable": false,
      "stock_location_id": 47,
      "giftwrap": null,
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
              "id": 21,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 40,
              "name": "ShippingCategory #39"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 131,
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
      "delivery_estimation": "Dec 17"
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
POST /api/shipments/H15865115767/giftwrap
Accept: application/json
X-Spree-Order-Token: 8Kh9e7AikzSe56QGqwYLHQ
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/shipments/:shipment_number/giftwrap`

#### Parameters


```json
order_number=M014542103
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
X-Request-Id: 52325ebd-db3e-4c3f-b288-46dfa31e93d4
X-Runtime: 0.052161
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
DELETE /api/shipments/H41206346168/giftwrap
Accept: application/json
X-Spree-Order-Token: GLAfYRrZIrIg1s4agxGrCA
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`DELETE /api/shipments/:shipment_number/giftwrap`

#### Parameters


```json
order_number=M766641525
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
X-Request-Id: 74ef1252-4d85-42da-bcbb-b7092d63a9d4
X-Runtime: 0.009347
Vary: Origin
204 No Content
```




# LineItem

Representation of a single cart item for a specific variant with price of vendor

## Creating a line item


### Request

#### Endpoint

```plaintext
POST /api/orders/M087814066/line_items
Accept: application/json
X-Spree-Order-Token: m65wqI3LIvmziDWWkkH25Q
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/:order_number/line_items`

#### Parameters


```json
line_item[variant_id]=149&line_item[options][vendor_id]=268
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
ETag: W/&quot;5f27d2548dd381d438710f207ac896dc&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 35712298-133a-4c28-baf1-659ef3615b8b
X-Runtime: 0.089782
Vary: Origin
Content-Length: 942
201 Created
```


```json
{
  "id": 29,
  "quantity": 1,
  "price": "19.99",
  "variant_id": 149,
  "vendor_id": 268,
  "single_display_amount": "$19.99",
  "display_amount": "$19.99",
  "total": "19.99",
  "on_sale": false,
  "final_sale": false,
  "backordered": null,
  "promotionable": true,
  "variant": {
    "id": 149,
    "name": "Product #80 - 7121",
    "sku": "SKU-148",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": false,
    "slug": "product-80-7121",
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
  "vendor_name": "Vendor #268",
  "country_iso": null,
  "adjustments": [

  ]
}
```



## Creating a line item gift card


### Request

#### Endpoint

```plaintext
POST /api/orders/M754822714/line_items
Accept: application/json
X-Spree-Order-Token: rx1TTi_I2Z5uJjxhjKK4XA
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/:order_number/line_items`

#### Parameters


```json
line_item[variant_id]=141&line_item[options][vendor_id]=254&line_item[options][gift_card_details][recipient_name]=Recipient+John&line_item[options][gift_card_details][recipient_email]=recipient%40email.com&line_item[options][gift_card_details][purchaser_name]=Purchaser+Bob&line_item[options][gift_card_details][gift_message]=Surprise&line_item[options][gift_card_details][send_email_at]=2019-12-13+08%3A19%3A38+-0500
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
ETag: W/&quot;6c832be52f382e5de91be082ddd2452f&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 19956053-9371-4ace-99b5-c673d4a86859
X-Runtime: 0.139689
Vary: Origin
Content-Length: 1078
201 Created
```


```json
{
  "id": 26,
  "quantity": 1,
  "price": "19.99",
  "variant_id": 141,
  "vendor_id": 254,
  "single_display_amount": "$19.99",
  "display_amount": "$19.99",
  "total": "19.99",
  "on_sale": false,
  "final_sale": false,
  "backordered": null,
  "promotionable": true,
  "variant": {
    "id": 141,
    "name": "Product #75 - 7429",
    "sku": "SKU-141",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": false,
    "slug": "product-75-7429",
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
    "product_id": 75,
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
      "send_email_at": "2019-12-13T00:00:00.000-05:00"
    }
  ],
  "vendor_name": "Vendor #254",
  "country_iso": null,
  "adjustments": [

  ]
}
```



## Deleting a line item


### Request

#### Endpoint

```plaintext
DELETE /api/orders/M507420876/line_items/24
Accept: application/json
X-Spree-Order-Token: rpTuUEQPTvOXmN9uw0k0Aw
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
X-Request-Id: 746d1dc1-ea2d-4369-82fa-5b431ef7f3ef
X-Runtime: 0.085049
Vary: Origin
204 No Content
```




## Updating a line item


### Request

#### Endpoint

```plaintext
PUT /api/orders/M452532524/line_items/27
Accept: application/json
X-Spree-Order-Token: VytPAVZNsKDIR394TCUBzA
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
ETag: W/&quot;69a1ff1071c16820f080570c4d8dcbf6&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: f99ba078-e317-4a3b-832a-097c5d9efa95
X-Runtime: 0.133671
Vary: Origin
Content-Length: 939
200 OK
```


```json
{
  "id": 27,
  "quantity": 2,
  "price": "10.0",
  "variant_id": 143,
  "vendor_id": 257,
  "single_display_amount": "$10.00",
  "display_amount": "$20.00",
  "total": "20.0",
  "on_sale": false,
  "final_sale": false,
  "backordered": null,
  "promotionable": true,
  "variant": {
    "id": 143,
    "name": "Product #77 - 3270",
    "sku": "SKU-142",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": false,
    "slug": "product-77-3270",
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
  "vendor_name": "Vendor #257",
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
Authorizat IO N: Bearer c64b092c4ef8523a2c8af9e8466893c55486c1736d441466
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/minis`

#### Parameters


```json
mini[name]=Winny&mini[user_id]=66&mini[birth_year]=2019&mini[birth_month]=1&mini[birth_day]=1
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
ETag: W/&quot;46cafcb18c0b17dba6ae13bdae0f0be1&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: fb1766ae-4cba-4708-bcf5-7f3bf0d5331c
X-Runtime: 0.010185
Vary: Origin
Content-Length: 163
201 Created
```


```json
{
  "id": 18,
  "user_id": 66,
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
DELETE /api/minis/11
Accept: application/json
Authorizat IO N: Bearer 1d98e279efe0e39c6c80c1d059b668983609a1e63341108d
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
X-Request-Id: 52fbc573-3da8-41e4-807a-e211834c7840
X-Runtime: 0.007660
Vary: Origin
204 No Content
```




## Get a single mini


### Request

#### Endpoint

```plaintext
GET /api/minis/19
Accept: application/json
Authorizat IO N: Bearer 4701c0e96b3ecbcb5023a0df9703249d4128a2e182ab99a9
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
ETag: W/&quot;15cb9d42330bedf1c10842a8338cf932&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 223f1830-7d73-4ea5-9434-bccbffac1405
X-Runtime: 0.010109
Vary: Origin
Content-Length: 168
200 OK
```


```json
{
  "id": 19,
  "user_id": 67,
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
Authorizat IO N: Bearer ea39030f8a7fa7f54f76723504e23e94ca3e63006e7559bb
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
ETag: W/&quot;63d86c713cb15c7c6ad6dfcd0c2f6ba2&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 8650c7b5-cb26-4ca6-9ea4-fc306b284d1e
X-Runtime: 0.054074
Vary: Origin
Content-Length: 1761
200 OK
```


```json
{
  "minis": [
    {
      "id": 10,
      "user_id": 60,
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
      "user_id": 59,
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
      "user_id": 58,
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
      "user_id": 57,
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
      "user_id": 56,
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
      "user_id": 55,
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
      "user_id": 54,
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
      "user_id": 53,
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
      "user_id": 52,
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
      "user_id": 51,
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
Authorizat IO N: Bearer 63b5f4acae46d1cd2b82b86b540ed0eaba16ff5a67fb189f
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
ETag: W/&quot;d1759784193ed4369aa66ceeee9b5148&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 72337439-19c2-4a8d-8856-021dfbc5c881
X-Runtime: 0.012693
Vary: Origin
Content-Length: 416
200 OK
```


```json
{
  "minis": [
    {
      "id": 16,
      "user_id": 64,
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
      "user_id": 64,
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
PATCH /api/minis/17
Accept: application/json
Authorizat IO N: Bearer fe3ce6ad89144e2c0a52475c6d5b1cd298438bffb970a6e8
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
ETag: W/&quot;7cac913edd3ceb1fbeb2b599299ef596&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: e3422c35-2319-467e-8f61-788dc2b77f30
X-Runtime: 0.011637
Vary: Origin
Content-Length: 169
200 OK
```


```json
{
  "id": 17,
  "user_id": 65,
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
user_id&order_token&line_item[variant_id]=24&line_item[quantity]=1&line_item[vendor_id]=55&line_item[gift_card_details_attributes][recipient_name]=Recipient+John&line_item[gift_card_details_attributes][recipient_email]=recipient%40email.com&line_item[gift_card_details_attributes][purchaser_name]=Purchaser+Bob&line_item[gift_card_details_attributes][gift_message]=Surprise&line_item[gift_card_details_attributes][send_email_at]=2019-12-13
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
ETag: W/&quot;be8e87eb3f1235d957d0c3f6a36ab5fb&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 5cf9f3d8-22a7-4f84-9871-ed1dd74f6bd5
X-Runtime: 0.173301
Vary: Origin
Content-Length: 2784
200 OK
```


```json
{
  "id": 10,
  "number": "M765719174",
  "item_total": "19.99",
  "total": "19.99",
  "ship_total": "0.0",
  "state": "cart",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2019-12-13T08:19:24.981-05:00",
  "updated_at": "2019-12-13T08:19:25.016-05:00",
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
  "token": "otabkIR0qZiraqqUckI7yg",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order&order=M765719174&bzip=&init=true",
  "payment_methods": [

  ],
  "bill_address": null,
  "ship_address": null,
  "line_items": [
    {
      "id": 10,
      "quantity": 1,
      "price": "19.99",
      "variant_id": 24,
      "vendor_id": 55,
      "single_display_amount": "$19.99",
      "display_amount": "$19.99",
      "total": "19.99",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 24,
        "name": "Product #11 - 5599",
        "sku": "SKU-24",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-11-5599",
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
        "product_id": 11,
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
          "send_email_at": "2019-12-13T00:00:00.000-05:00"
        }
      ],
      "vendor_name": "Vendor #55",
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
user_id&order_token&line_item[variant_id]=28&line_item[quantity]=2&line_item[vendor_id]=59
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
ETag: W/&quot;66b6f53343e8cda898ec6bb007caf426&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 81e47296-8e53-4a5a-8b9f-54d411f18f76
X-Runtime: 0.106663
Vary: Origin
Content-Length: 2600
200 OK
```


```json
{
  "id": 11,
  "number": "M742520893",
  "item_total": "39.98",
  "total": "39.98",
  "ship_total": "0.0",
  "state": "cart",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2019-12-13T08:19:25.443-05:00",
  "updated_at": "2019-12-13T08:19:25.479-05:00",
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
  "token": "7nbuirrfNIsDshKaUmxn_Q",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order&order=M742520893&bzip=&init=true",
  "payment_methods": [

  ],
  "bill_address": null,
  "ship_address": null,
  "line_items": [
    {
      "id": 11,
      "quantity": 2,
      "price": "19.99",
      "variant_id": 28,
      "vendor_id": 59,
      "single_display_amount": "$19.99",
      "display_amount": "$39.98",
      "total": "39.98",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 28,
        "name": "Product #14 - 351",
        "sku": "SKU-27",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-14-351",
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
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [

      ],
      "vendor_name": "Vendor #59",
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
Authorizat IO N: Bearer 740b20c1a217bb27f4e026df651a218910a8948f73a3b530
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
ETag: W/&quot;8b47c56bc8edb174f9bae281fd6a24f4&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: f4c31230-eab9-40d8-8948-7cba62ba247f
X-Runtime: 0.013546
Vary: Origin
Content-Length: 310
200 OK
```


```json
{
  "orders": [
    {
      "number": "M113359287",
      "completed_at": "2019-12-13T08:19:26.151-05:00",
      "total": "120.0",
      "state": "Complete",
      "shipment_state": "shipped",
      "shipments": [
        {
          "number": "H13105371373",
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
GET /api/orders/M387408582
Accept: application/json
Authorizat IO N: Bearer 562fdeb7811e80020138a08b615ee96444bdabb0371c158e
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
ETag: W/&quot;cff0a202f830e4c19181bfcf88643d5c&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: ef9ba704-671b-4948-aa31-8b3d2bbb7b5a
X-Runtime: 0.161257
Vary: Origin
Content-Length: 9991
200 OK
```


```json
{
  "id": 8,
  "number": "M387408582",
  "item_total": "20.0",
  "total": "120.0",
  "ship_total": "100.0",
  "state": "complete",
  "adjustment_total": "0.0",
  "user_id": 15,
  "created_at": "2019-12-13T08:19:23.432-05:00",
  "updated_at": "2019-12-13T08:19:23.879-05:00",
  "completed_at": "2019-12-13T08:19:23.521-05:00",
  "payment_total": "120.0",
  "shipment_state": "shipped",
  "payment_state": "paid",
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
  "token": "o_geXvDCMxUOmZR96CnYaQ",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order&order=M387408582&bzip=10017&init=true",
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
    "id": 20,
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
    "id": 21,
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
      "id": 6,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 14,
      "vendor_id": 37,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 14,
        "name": "Product #7 - 6865",
        "sku": "SKU-13",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-7-6865",
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
      "vendor_name": "Vendor #37",
      "country_iso": "US",
      "adjustments": [
        {
          "id": 8,
          "source_type": "Spree::TaxRate",
          "source_id": 1,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 6,
          "amount": "2.0",
          "label": "VAT 5%",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-12-13T08:19:23.853-05:00",
          "updated_at": "2019-12-13T08:19:23.863-05:00",
          "display_amount": "$2.00"
        },
        {
          "id": 2,
          "source_type": "Spree::PromotionAction",
          "source_id": 1,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 6,
          "amount": "5.0",
          "label": "foo",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-12-13T08:19:23.737-05:00",
          "updated_at": "2019-12-13T08:19:23.737-05:00",
          "display_amount": "$5.00"
        },
        {
          "id": 1,
          "source_type": "Spree::PromotionAction",
          "source_id": 1,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 6,
          "amount": "5.0",
          "label": "foo",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-12-13T08:19:23.725-05:00",
          "updated_at": "2019-12-13T08:19:23.725-05:00",
          "display_amount": "$5.00"
        }
      ]
    },
    {
      "id": 7,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 16,
      "vendor_id": 37,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 16,
        "name": "Product #8 - 5924",
        "sku": "SKU-15",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-8-5924",
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
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [

      ],
      "vendor_name": "Vendor #37",
      "country_iso": "US",
      "adjustments": [
        {
          "id": 9,
          "source_type": "Spree::TaxRate",
          "source_id": 2,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 7,
          "amount": "1.5",
          "label": "VAT 5%",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-12-13T08:19:23.876-05:00",
          "updated_at": "2019-12-13T08:19:23.886-05:00",
          "display_amount": "$1.50"
        },
        {
          "id": 3,
          "source_type": "Spree::PromotionAction",
          "source_id": 1,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 7,
          "amount": "5.0",
          "label": "bar",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-12-13T08:19:23.749-05:00",
          "updated_at": "2019-12-13T08:19:23.749-05:00",
          "display_amount": "$5.00"
        }
      ]
    }
  ],
  "payments": [
    {
      "id": 3,
      "source_type": "Spree::CreditCard",
      "source_id": 1,
      "amount": "120.0",
      "display_amount": "$120.00",
      "payment_method_id": 6,
      "state": "completed",
      "avs_response": null,
      "created_at": "2019-12-13T08:19:23.611-05:00",
      "updated_at": "2019-12-13T08:19:23.611-05:00",
      "payment_method": {
        "id": 6,
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
  "shipments": [
    {
      "id": 10,
      "tracking": "U10000",
      "tracking_url": null,
      "number": "H66564702467",
      "cost": "100.0",
      "shipped_at": "2019-12-13T08:19:23.652-05:00",
      "state": "shipped",
      "order_id": "M387408582",
      "stock_location_name": "NY Warehouse",
      "giftwrappable": false,
      "stock_location_id": 10,
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
          "adjustable_id": 10,
          "amount": "-10.0",
          "label": "Shipping",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-12-13T08:19:23.773-05:00",
          "updated_at": "2019-12-13T08:19:23.773-05:00",
          "display_amount": "-$10.00"
        },
        {
          "id": 4,
          "source_type": "Spree::PromotionAction",
          "source_id": 1,
          "adjustable_type": "Spree::Shipment",
          "adjustable_id": 10,
          "amount": "-9.99",
          "label": "Shipping",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-12-13T08:19:23.762-05:00",
          "updated_at": "2019-12-13T08:19:23.762-05:00",
          "display_amount": "-$9.99"
        }
      ],
      "stock_location_address": "NY Warehouse, Washington, AL",
      "country_iso": "US",
      "international_shipping": false,
      "delivery_estimation": "Dec 17"
    }
  ],
  "adjustments": [
    {
      "id": 6,
      "source_type": "Spree::Promotion",
      "source_id": 1,
      "adjustable_type": "Spree::Order",
      "adjustable_id": 8,
      "amount": "20.0",
      "label": "adj1",
      "promotion_code_id": null,
      "finalized": false,
      "eligible": true,
      "created_at": "2019-12-13T08:19:23.779-05:00",
      "updated_at": "2019-12-13T08:19:23.779-05:00",
      "display_amount": "$20.00"
    },
    {
      "id": 7,
      "source_type": "Spree::Promotion",
      "source_id": 1,
      "adjustable_type": "Spree::Order",
      "adjustable_id": 8,
      "amount": "30.0",
      "label": "adj2",
      "promotion_code_id": null,
      "finalized": false,
      "eligible": true,
      "created_at": "2019-12-13T08:19:23.784-05:00",
      "updated_at": "2019-12-13T08:19:23.784-05:00",
      "display_amount": "$30.00"
    }
  ],
  "permissions": {
    "can_update": false
  },
  "credit_cards": [
    {
      "id": 1,
      "month": "12",
      "year": "2020",
      "cc_type": null,
      "last_digits": "1111",
      "name": "Spree Commerce",
      "address": {
        "id": 20,
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
GET /api/orders/M098107732
Accept: application/json
Authorizat IO N: c78b477c9bddce3efe64213689ce850991d116c926a37130
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
X-Request-Id: 12d46cdc-0a74-4ebe-b3e6-05334dcee438
X-Runtime: 0.013027
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
user[email]=email72%40example.com
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
X-Request-Id: 71a6ecd7-b8a8-4fd9-b4e0-f4d2273a7c3e
X-Runtime: 0.002734
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
user[email]=email71%40example.com&user[password]=secret
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
Authorization: Bearer 99194d11cf9d80c3e2f7b6943b0f80733e4b9cfc4842b421
ETag: W/&quot;5270fc3b9c4ffe9835dbf5baf9c0905c&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: d3d830d8-0e8c-4fa3-90e1-9acb56a29080
X-Runtime: 0.007845
Vary: Origin
Content-Length: 562
200 OK
```


```json
{
  "id": 72,
  "email": "email71@example.com",
  "persistence_token": null,
  "perishable_token": null,
  "last_request_at": null,
  "login": "email71@example.com",
  "ship_address_id": null,
  "bill_address_id": null,
  "created_at": "2019-12-13T08:19:30.925-05:00",
  "updated_at": "2019-12-13T08:19:30.927-05:00",
  "spree_api_key": "99194d11cf9d80c3e2f7b6943b0f80733e4b9cfc4842b421",
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
X-Request-Id: c6fdbedc-3b32-4d9b-a2a8-cc608aa46c2d
X-Runtime: 0.022849
Vary: Origin
204 No Content
```




# Products

Get all products, queryable by ransack

## Fetch a single product by id


### Request

#### Endpoint

```plaintext
GET /api/products/product-62-9141
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
Date: Fri, 13 Dec 2019 13:19:33 GMT
Surrogate-Control: max-age=900
Surrogate-Key: product_id=1
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;3db93de5864fd08c64fc05402c5fc77f&quot;
X-Request-Id: a9d52ce3-433f-4540-86c8-0fe7b68a4850
X-Runtime: 0.050005
Vary: Origin
Content-Length: 1544
200 OK
```


```json
{
  "id": 62,
  "name": "Product #62 - 9141",
  "description": "As seen on TV!",
  "available_on": "2018-12-13T08:19:33.181-05:00",
  "slug": "product-62-9141",
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
  "brand_description": null,
  "gift_card": false,
  "trends": [

  ],
  "breadcrumb_taxons": [
    {
      "id": 37,
      "name": "Clothing",
      "taxonomy_id": 8,
      "created_at": "2019-12-13T08:19:33.108-05:00",
      "url": "/category/clothing",
      "position": 1
    },
    {
      "id": 38,
      "name": "Girl",
      "taxonomy_id": 8,
      "created_at": "2019-12-13T08:19:33.132-05:00",
      "url": "/category/clothing/girl",
      "position": 2
    },
    {
      "id": 39,
      "name": "Dresses",
      "taxonomy_id": 8,
      "created_at": "2019-12-13T08:19:33.157-05:00",
      "url": "/category/clothing/girl/dresses",
      "position": 3
    }
  ],
  "has_variants": false,
  "master": {
    "id": 117,
    "name": "Product #62 - 9141",
    "sku": "SKU-117",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": true,
    "slug": "product-62-9141",
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
Date: Fri, 13 Dec 2019 13:19:32 GMT
Surrogate-Control: max-age=900
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;76e0d8c86802dfabc02b0c8cc19ce8ab&quot;
X-Request-Id: 0ae25393-3faf-4697-b011-637714988a94
X-Runtime: 0.061016
Vary: Origin
Content-Length: 936
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
      "id": 56,
      "name": "Product #56 - 1750",
      "description": "As seen on TV!",
      "available_on": "2018-12-13T08:19:32.511-05:00",
      "slug": "product-56-1750",
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
        "id": 111,
        "name": "Product #56 - 1750",
        "sku": "SKU-111",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-56-1750",
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
Date: Fri, 13 Dec 2019 13:19:32 GMT
Surrogate-Control: max-age=900
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;6792ece1456bab486e9ed7a24680d3c7&quot;
X-Request-Id: 2e091b57-5c54-4427-8d8c-58376b645f91
X-Runtime: 0.024618
Vary: Origin
Content-Length: 271
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
      "id": 57,
      "name": "Product #57 - 3887",
      "slug": "product-57-3887",
      "master_id": 112,
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
GET /api/products?ids=59%2C60%2C61
Host: example.org
Cookie: 
```

`GET /api/products`

#### Parameters


```json
ids: 59,60,61
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
Date: Fri, 13 Dec 2019 13:19:33 GMT
Surrogate-Control: max-age=900
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;6b5927ec8e029207086e7357d9ea500f&quot;
X-Request-Id: f29eafc4-80af-4593-b7d2-131264d94474
X-Runtime: 0.083361
Vary: Origin
Content-Length: 2642
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
      "id": 59,
      "name": "Product #59 - 1706",
      "description": "As seen on TV!",
      "available_on": "2018-12-13T08:19:32.833-05:00",
      "slug": "product-59-1706",
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
        "id": 114,
        "name": "Product #59 - 1706",
        "sku": "SKU-114",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-59-1706",
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
      "id": 60,
      "name": "Product #60 - 4041",
      "description": "As seen on TV!",
      "available_on": "2018-12-13T08:19:32.889-05:00",
      "slug": "product-60-4041",
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
        "id": 115,
        "name": "Product #60 - 4041",
        "sku": "SKU-115",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-60-4041",
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
      "id": 61,
      "name": "Product #61 - 501",
      "description": "As seen on TV!",
      "available_on": "2018-12-13T08:19:32.947-05:00",
      "slug": "product-61-501",
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
        "id": 116,
        "name": "Product #61 - 501",
        "sku": "SKU-116",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-61-501",
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
GET /api/taxons/products?id=42
Host: example.org
Cookie: 
```

`GET /api/taxons/products`

#### Parameters


```json
id: 42
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
ETag: W/&quot;bff72d224a82a0c51bdc784451805040&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 41e2a2b9-30ab-40eb-87d3-48ecb3305e30
X-Runtime: 0.041115
Vary: Origin
Content-Length: 1226
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
      "id": 64,
      "name": "Product #64 - 9891",
      "description": "As seen on TV!",
      "available_on": "2018-12-13T08:19:33.516-05:00",
      "slug": "product-64-9891",
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
      "brand_description": null,
      "gift_card": false,
      "trends": [

      ],
      "breadcrumb_taxons": [

      ],
      "has_variants": false,
      "master": {
        "id": 119,
        "name": "Product #64 - 9891",
        "sku": "SKU-119",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-64-9891",
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



## Fetch products by taxon permalink


### Request

#### Endpoint

```plaintext
GET /api/taxons/products?permalink=ruby-on-rails-8
Host: example.org
Cookie: 
```

`GET /api/taxons/products`

#### Parameters


```json
permalink: ruby-on-rails-8
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
ETag: W/&quot;f1b60510358d1cecfed357ac107eadf1&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 9175c819-cb55-4577-ad91-b735ecdbab03
X-Runtime: 0.040296
Vary: Origin
Content-Length: 1227
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
      "id": 66,
      "name": "Product #66 - 9185",
      "description": "As seen on TV!",
      "available_on": "2018-12-13T08:19:33.780-05:00",
      "slug": "product-66-9185",
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
      "brand_description": null,
      "gift_card": false,
      "trends": [

      ],
      "breadcrumb_taxons": [

      ],
      "has_variants": false,
      "master": {
        "id": 121,
        "name": "Product #66 - 9185",
        "sku": "SKU-121",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-66-9185",
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
X-Request-Id: ce840810-f0a2-4d0d-a0fb-bebee7d3c349
X-Runtime: 0.010847
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
GET /api/recently_viewed?recently_viewed[session_id]=7yrdk31xxz8gl28el7jpdsuhp9zh6dvuisxq4e46n9cl4pdqf8b028ufqf69zr9nb1aay6bcidw1ulnh1b2vwvfzd785yoitz2bik46ajnpmw3amrsqn4wrqhg6vr6sq8lr1dknhne5u07m7ncma1qjpenhz7w9nh5aey6n41x4rvksn48d2uq6gomk6oi31vi4vexiwt3tort3rzy45f3wt4xcn96eu9w9k5t9d2igs3098e31au6muz0vgmw6&amp;recently_viewed[user_id]=47002
Accept: application/json
Host: example.org
Cookie: 
```

`GET /api/recently_viewed`

#### Parameters


```json
recently_viewed: {&quot;session_id&quot;=&gt;&quot;7yrdk31xxz8gl28el7jpdsuhp9zh6dvuisxq4e46n9cl4pdqf8b028ufqf69zr9nb1aay6bcidw1ulnh1b2vwvfzd785yoitz2bik46ajnpmw3amrsqn4wrqhg6vr6sq8lr1dknhne5u07m7ncma1qjpenhz7w9nh5aey6n41x4rvksn48d2uq6gomk6oi31vi4vexiwt3tort3rzy45f3wt4xcn96eu9w9k5t9d2igs3098e31au6muz0vgmw6&quot;, &quot;user_id&quot;=&gt;&quot;47002&quot;}
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
ETag: W/&quot;662e5ab0e95c0ba0343bb5a50600acfb&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: b35f1b12-e665-4289-9ae2-340dc22e22f8
X-Runtime: 0.003535
Vary: Origin
Content-Length: 119
200 OK
```


```json
[
  {
    "at": "2019-12-13T08:19:19.201-05:00",
    "variant_id": "var1"
  },
  {
    "at": "2019-12-13T08:24:19.201-05:00",
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
recently_viewed[session_id]=qd5e930cvv4354tv4h4edo0cap4h0dzi2zyisshnh5mvjiq2s2r2u56xc62zktrw5gcrkg2u77b97fl6pmr49ahwdo1lm2q4xbdggn42e1u8fpiqpxrtj6ooc6c3wmkv9poqlb292khypbnsuzurn4r9jd9p2b45kcuqsmoh0gekx3ehkrbl41tgnd1736s4hi50py49zxglstiq3q54a5vsjc1e8rw56m59zfbz7a3abaeero9ehkrm5qpe4iq&recently_viewed[user_id]=43881&recently_viewed[variant_id]=foo
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
X-Request-Id: 152ee09c-da90-4332-90dd-79ef5a341eb0
X-Runtime: 0.026796
Vary: Origin
204 No Content
```




# Return Authorizations

Get a single user return authorziation

## Can get another user&#39;s return authorization


### Request

#### Endpoint

```plaintext
GET /api/returns/RA571464283
Authorizat IO N: Bearer 69e4f72798bfc88f81e9951882dcd10caa306b0c8e064254
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
ETag: W/&quot;e734134cadac38bc63a5953f290d46de&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: dd0c5a7c-b0bc-4f68-a527-fc1d35649da0
X-Runtime: 0.041093
Vary: Origin
Content-Length: 2859
200 OK
```


```json
{
  "id": 2,
  "number": "RA571464283",
  "state": "authorized",
  "order_id": 14,
  "memo": "Items were broken",
  "created_at": "2019-12-13T08:19:31.697-05:00",
  "updated_at": "2019-12-13T08:19:31.697-05:00",
  "reason": {
    "id": 3,
    "name": "Defect #3",
    "active": true,
    "mutable": true,
    "created_at": "2019-12-13T08:19:31.694-05:00",
    "updated_at": "2019-12-13T08:19:31.694-05:00",
    "mirakl_code": null
  },
  "order": {
    "id": 14,
    "number": "M130221605",
    "item_total": "10.0",
    "total": "110.0",
    "state": "complete",
    "adjustment_total": "0.0",
    "user_id": 75,
    "completed_at": "2019-12-13T08:19:31.633-05:00",
    "bill_address_id": 28,
    "ship_address_id": 29,
    "payment_total": "110.0",
    "shipment_state": "shipped",
    "payment_state": "paid",
    "email": "email74@example.com",
    "special_instructions": null,
    "created_at": "2019-12-13T08:19:31.578-05:00",
    "updated_at": "2019-12-13T08:19:31.680-05:00",
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
    "guest_token": "EI4YHsF7TqkpPwVVYN5PJQ",
    "canceled_at": null,
    "canceler_id": null,
    "store_id": 14,
    "approver_name": null,
    "frontend_viewable": true,
    "is_gift": false,
    "gift_email": null,
    "gift_message": null,
    "gift_card_total": "0.0"
  },
  "ship_address": {
    "id": 29,
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
  "bill_address": {
    "id": 28,
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
  "return_items": [
    {
      "name": "Product #53 - 4320",
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
        "id": 17,
        "name": "Credit Card"
      },
      "source": {
        "id": 5,
        "month": "12",
        "year": "2020",
        "cc_type": null,
        "last_digits": "1111",
        "name": "Spree Commerce",
        "gateway_customer_profile_id": "BGS-321140",
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
Authorizat IO N: Bearer 7092b52008ba8c11b5855d9c96faa8e49f9f0b16704c4ddf
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
ETag: W/&quot;16661957123f8096cd1f8857475c17fa&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 4b2c9fd5-c0d4-4944-a977-8425c99eca5b
X-Runtime: 0.007228
Vary: Origin
Content-Length: 169
200 OK
```


```json
{
  "return_authorizations": [
    {
      "number": "RA815318363",
      "created_at": "2019-12-13T08:19:32.480-05:00",
      "return_amount": "10.0",
      "order_number": "M228083211",
      "state": "authorized"
    }
  ]
}
```



## returns a 200


### Request

#### Endpoint

```plaintext
GET /api/returns/RA804385153
Authorizat IO N: Bearer da5d8086d9dbd03f08d71bc6c41e852713227d052a331133
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
ETag: W/&quot;f300d1d85f0a40c4001a7489a931aee5&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 00d6b0d6-83ae-4964-a03b-598d55fe8e61
X-Runtime: 0.051028
Vary: Origin
Content-Length: 2782
200 OK
```


```json
{
  "id": 1,
  "number": "RA804385153",
  "state": "authorized",
  "order_id": 13,
  "memo": "Items were broken",
  "created_at": "2019-12-13T08:19:31.289-05:00",
  "updated_at": "2019-12-13T08:19:31.289-05:00",
  "reason": {
    "id": 1,
    "name": "Defect #1",
    "active": true,
    "mutable": true,
    "created_at": "2019-12-13T08:19:31.280-05:00",
    "updated_at": "2019-12-13T08:19:31.280-05:00",
    "mirakl_code": null
  },
  "order": {
    "id": 13,
    "number": "M343854518",
    "item_total": "10.0",
    "total": "110.0",
    "state": "complete",
    "adjustment_total": "0.0",
    "user_id": 74,
    "completed_at": "2019-12-13T08:19:31.192-05:00",
    "bill_address_id": 26,
    "ship_address_id": 27,
    "payment_total": "110.0",
    "shipment_state": "shipped",
    "payment_state": "paid",
    "email": "email73@example.com",
    "special_instructions": null,
    "created_at": "2019-12-13T08:19:31.135-05:00",
    "updated_at": "2019-12-13T08:19:31.240-05:00",
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
    "guest_token": "oQ-KU-V1QAezowF0fROfjQ",
    "canceled_at": null,
    "canceler_id": null,
    "store_id": 13,
    "approver_name": null,
    "frontend_viewable": true,
    "is_gift": false,
    "gift_email": null,
    "gift_message": null,
    "gift_card_total": "0.0"
  },
  "ship_address": {
    "id": 27,
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
  "bill_address": {
    "id": 26,
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
  "return_items": [
    {
      "name": "Product #52 - 5533",
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
        "id": 15,
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
GET /api/returns/RA731726335
Authorizat IO N: Bearer 3fcc44eb8519f61a673333a56ce6cb3659d6413892271f04
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
X-Request-Id: 23d1a187-c6d8-42e6-b63f-5239a39d15e1
X-Runtime: 0.010753
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
stock_request[email]=telma.collier%40ankunding.info&stock_request[variant_id]=100
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
X-Request-Id: c51961d3-d7d6-46fe-ada4-5d8de398407b
X-Runtime: 0.003867
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
stock_request[email]=foo&stock_request[variant_id]=102
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
X-Request-Id: a9798595-6bd9-4dd7-8c8d-14e118c967a3
X-Runtime: 0.004056
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
stock_request[email]=isobel_nikolaus%40stark.co.uk&stock_request[variant_id]=98
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
X-Request-Id: eb565dc0-8f74-4036-a506-6eaeff9d46b8
X-Runtime: 0.023438
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
Authorizat IO N: Bearer 2d79e31ef0db1712bce7a3f380fb4baa2bc643d5c1ccb27f
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
ETag: W/&quot;4c60be61a4a6628aac9dbd3741741b9a&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 11cc3a76-0b87-4a41-989c-aaecb49d1295
X-Runtime: 0.053981
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
      "created_at": "2019-12-13T08:19:19.255-05:00"
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
Authorizat IO N: Bearer 51028f7d925de761b5871203c372c307d0c8c3de63748df8
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/subscribers`

#### Parameters


```json
subscriber[email]=mirna%40conroyhilll.ca&subscriber[user_id]=82&subscriber[first_name]=Hunter&subscriber[last_name]=Rowe&subscriber[status]=subscribed
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
ETag: W/&quot;ba958be7f84f5f2d7a48f6c8ce7a3d55&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 526d72ad-318c-40fe-adb9-9e6cb93805c2
X-Runtime: 0.009170
Vary: Origin
Content-Length: 172
201 Created
```


```json
{
  "id": 7,
  "user_id": 82,
  "email": "mirna@conroyhilll.ca",
  "first_name": "Hunter",
  "last_name": "Rowe",
  "source": "",
  "status": "subscribed",
  "created_at": "2019-12-13T08:19:34.001-05:00"
}
```



## Delete a subscriber


### Request

#### Endpoint

```plaintext
DELETE /api/subscribers/3
Accept: application/json
Authorizat IO N: Bearer a6136e41f9c5b8644b36e39c0283e2cad4f2cb3d1a8a5bdf
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
X-Request-Id: 1649ba49-a8dc-4152-bfd6-ff337064fc9a
X-Runtime: 0.027168
Vary: Origin
204 No Content
```




## Get a single subscriber by id


### Request

#### Endpoint

```plaintext
GET /api/subscribers/9
Accept: application/json
Authorizat IO N: Bearer 6137d56ebaaa22e659670b88dbe25af59f15db05ecf99245
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
ETag: W/&quot;ddca44c2ebed055da68ca628b6b2f627&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 06afbc6c-69eb-40c5-aa82-5e63525874da
X-Runtime: 0.007285
Vary: Origin
Content-Length: 178
200 OK
```


```json
{
  "id": 9,
  "user_id": 84,
  "email": "levi_ohara@homenick.com",
  "first_name": "Megan",
  "last_name": "Cummings",
  "source": "",
  "status": "subscribed",
  "created_at": "2019-12-13T08:19:34.032-05:00"
}
```



## Get all subscribers


### Request

#### Endpoint

```plaintext
GET /api/subscribers
Accept: application/json
Authorizat IO N: Bearer f8ba344c480f291857e2b2615e80070d5d0b7c1449b825ad
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
ETag: W/&quot;8dfb82be426d0c8e6a737de5d910a3d3&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 4372c2da-ff82-4bb2-818f-472179835b29
X-Runtime: 0.014676
Vary: Origin
Content-Length: 621
200 OK
```


```json
{
  "subscribers": [
    {
      "id": 4,
      "user_id": null,
      "email": "noe_kuphal@johnson.com",
      "first_name": "Marylynn",
      "last_name": "Blanda",
      "source": "",
      "status": "subscribed",
      "created_at": "2019-12-13T08:19:33.953-05:00"
    },
    {
      "id": 5,
      "user_id": null,
      "email": "suk_medhurst@fisher.co.uk",
      "first_name": "Lexie",
      "last_name": "Graham",
      "source": "",
      "status": "subscribed",
      "created_at": "2019-12-13T08:19:33.955-05:00"
    },
    {
      "id": 6,
      "user_id": null,
      "email": "deangelo_smith@dooley.us",
      "first_name": "Dee",
      "last_name": "Oga",
      "source": "",
      "status": "subscribed",
      "created_at": "2019-12-13T08:19:33.956-05:00"
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
Authorizat IO N: Bearer 14924a4e0397498b45640c0ba6b268be9d20cb52847b90aa
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
ETag: W/&quot;8ecaf11c6c94e91df1ea211b60eb5115&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 34b2dc3f-b0ce-4ea7-92d0-cb09c22f9592
X-Runtime: 0.007901
Vary: Origin
Content-Length: 175
200 OK
```


```json
{
  "id": 8,
  "user_id": 83,
  "email": "suzette@mills.biz",
  "first_name": "Laurena",
  "last_name": "Schultz",
  "source": "",
  "status": "unsubscribed",
  "created_at": "2019-12-13T08:19:34.014-05:00"
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
ETag: W/&quot;b896815ef6ab259486d635d19dd3466d&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: fa4c14d0-dd15-4764-8171-38d09fc02f45
X-Runtime: 0.109475
Vary: Origin
Content-Length: 4411
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
      "id": 3,
      "name": "Category",
      "pretty_name": "Category",
      "permalink": "category",
      "parent_id": null,
      "taxonomy_id": 2,
      "url_override": null,
      "description": "Category",
      "icon": "/assets/default_taxon.png",
      "taxons": [
        {
          "id": 4,
          "name": "Kids",
          "pretty_name": "Category -> Kids",
          "permalink": "category/kids",
          "parent_id": 3,
          "taxonomy_id": 2,
          "url_override": null
        }
      ]
    },
    {
      "id": 4,
      "name": "Kids",
      "pretty_name": "Category -> Kids",
      "permalink": "category/kids",
      "parent_id": 3,
      "taxonomy_id": 2,
      "url_override": null,
      "description": "Kids",
      "icon": "/assets/default_taxon.png",
      "taxons": [
        {
          "id": 5,
          "name": "Boys",
          "pretty_name": "Category -> Kids -> Boys",
          "permalink": "category/kids/boys",
          "parent_id": 4,
          "taxonomy_id": 2,
          "url_override": null
        },
        {
          "id": 8,
          "name": "Girls",
          "pretty_name": "Category -> Kids -> Girls",
          "permalink": "category/kids/girls",
          "parent_id": 4,
          "taxonomy_id": 2,
          "url_override": null
        }
      ]
    },
    {
      "id": 5,
      "name": "Boys",
      "pretty_name": "Category -> Kids -> Boys",
      "permalink": "category/kids/boys",
      "parent_id": 4,
      "taxonomy_id": 2,
      "url_override": null,
      "description": "Boys",
      "icon": "/assets/default_taxon.png",
      "taxons": [
        {
          "id": 6,
          "name": "Boys Tops",
          "pretty_name": "Category -> Kids -> Boys -> Boys Tops",
          "permalink": "category/kids/boys/boys-tops",
          "parent_id": 5,
          "taxonomy_id": 2,
          "url_override": null
        }
      ]
    },
    {
      "id": 6,
      "name": "Boys Tops",
      "pretty_name": "Category -> Kids -> Boys -> Boys Tops",
      "permalink": "category/kids/boys/boys-tops",
      "parent_id": 5,
      "taxonomy_id": 2,
      "url_override": null,
      "description": "Boys Tops",
      "icon": "/assets/default_taxon.png",
      "taxons": [
        {
          "id": 7,
          "name": "Boys Shirts",
          "pretty_name": "Category -> Kids -> Boys -> Boys Tops -> Boys Shirts",
          "permalink": "category/kids/boys/boys-tops/boys-shirts",
          "parent_id": 6,
          "taxonomy_id": 2,
          "url_override": null
        }
      ]
    },
    {
      "id": 7,
      "name": "Boys Shirts",
      "pretty_name": "Category -> Kids -> Boys -> Boys Tops -> Boys Shirts",
      "permalink": "category/kids/boys/boys-tops/boys-shirts",
      "parent_id": 6,
      "taxonomy_id": 2,
      "url_override": null,
      "description": "Boys Shirts",
      "icon": "/assets/default_taxon.png",
      "taxons": [

      ]
    },
    {
      "id": 8,
      "name": "Girls",
      "pretty_name": "Category -> Kids -> Girls",
      "permalink": "category/kids/girls",
      "parent_id": 4,
      "taxonomy_id": 2,
      "url_override": null,
      "description": "Girls",
      "icon": "/assets/default_taxon.png",
      "taxons": [
        {
          "id": 9,
          "name": "Girls Tops",
          "pretty_name": "Category -> Kids -> Girls -> Girls Tops",
          "permalink": "category/kids/girls/girls-tops",
          "parent_id": 8,
          "taxonomy_id": 2,
          "url_override": null
        }
      ]
    },
    {
      "id": 9,
      "name": "Girls Tops",
      "pretty_name": "Category -> Kids -> Girls -> Girls Tops",
      "permalink": "category/kids/girls/girls-tops",
      "parent_id": 8,
      "taxonomy_id": 2,
      "url_override": null,
      "description": "Girls Tops",
      "icon": "/assets/default_taxon.png",
      "taxons": [
        {
          "id": 10,
          "name": "Girls Shirts",
          "pretty_name": "Category -> Kids -> Girls -> Girls Tops -> Girls Shirts",
          "permalink": "category/kids/girls/girls-tops/girls-shirts",
          "parent_id": 9,
          "taxonomy_id": 2,
          "url_override": null
        }
      ]
    },
    {
      "id": 10,
      "name": "Girls Shirts",
      "pretty_name": "Category -> Kids -> Girls -> Girls Tops -> Girls Shirts",
      "permalink": "category/kids/girls/girls-tops/girls-shirts",
      "parent_id": 9,
      "taxonomy_id": 2,
      "url_override": null,
      "description": "Girls Shirts",
      "icon": "/assets/default_taxon.png",
      "taxons": [

      ]
    },
    {
      "id": 11,
      "name": "Brand",
      "pretty_name": "Brand",
      "permalink": "brand",
      "parent_id": null,
      "taxonomy_id": 3,
      "url_override": null,
      "description": "Brand",
      "icon": "/assets/default_taxon.png",
      "taxons": [
        {
          "id": 12,
          "name": "Ruby on Rails - 1",
          "pretty_name": "Brand -> Ruby on Rails - 1",
          "permalink": "brand/ruby-on-rails-1",
          "parent_id": 11,
          "taxonomy_id": 3,
          "url_override": null
        },
        {
          "id": 13,
          "name": "Ruby on Rails - 2",
          "pretty_name": "Brand -> Ruby on Rails - 2",
          "permalink": "brand/ruby-on-rails-2",
          "parent_id": 11,
          "taxonomy_id": 3,
          "url_override": null
        }
      ]
    },
    {
      "id": 12,
      "name": "Ruby on Rails - 1",
      "pretty_name": "Brand -> Ruby on Rails - 1",
      "permalink": "brand/ruby-on-rails-1",
      "parent_id": 11,
      "taxonomy_id": 3,
      "url_override": null,
      "description": "Ruby on Rails - 1",
      "icon": "/assets/default_taxon.png",
      "taxons": [

      ]
    },
    {
      "id": 13,
      "name": "Ruby on Rails - 2",
      "pretty_name": "Brand -> Ruby on Rails - 2",
      "permalink": "brand/ruby-on-rails-2",
      "parent_id": 11,
      "taxonomy_id": 3,
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
ETag: W/&quot;fe8e9e93b61816c3bde86bb4b8efaa3a&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 8052428c-d08d-4d36-b978-5d42ad5f6ef6
X-Runtime: 0.012341
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
      "id": 33,
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
      "id": 34,
      "name": "Ruby on Rails - 5",
      "pretty_name": "Brand -> Ruby on Rails - 5",
      "permalink": "brand/ruby-on-rails-5",
      "parent_id": 33,
      "taxonomy_id": 7,
      "url_override": null,
      "description": "Ruby on Rails - 5",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 35,
      "name": "Ruby on Rails - 6",
      "pretty_name": "Brand -> Ruby on Rails - 6",
      "permalink": "brand/ruby-on-rails-6",
      "parent_id": 33,
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
ETag: W/&quot;357d31e6385dfd85316ef5529cd44e39&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 31c81b08-9f78-494a-90e2-b0cb0efbe506
X-Runtime: 0.020596
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
      "id": 14,
      "name": "Category",
      "pretty_name": "Category",
      "permalink": "category",
      "parent_id": null,
      "taxonomy_id": 4,
      "url_override": null,
      "description": "Category",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 15,
      "name": "Kids",
      "pretty_name": "Category -> Kids",
      "permalink": "category/kids",
      "parent_id": 14,
      "taxonomy_id": 4,
      "url_override": null,
      "description": "Kids",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 16,
      "name": "Boys",
      "pretty_name": "Category -> Kids -> Boys",
      "permalink": "category/kids/boys",
      "parent_id": 15,
      "taxonomy_id": 4,
      "url_override": null,
      "description": "Boys",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 17,
      "name": "Boys Tops",
      "pretty_name": "Category -> Kids -> Boys -> Boys Tops",
      "permalink": "category/kids/boys/boys-tops",
      "parent_id": 16,
      "taxonomy_id": 4,
      "url_override": null,
      "description": "Boys Tops",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 18,
      "name": "Boys Shirts",
      "pretty_name": "Category -> Kids -> Boys -> Boys Tops -> Boys Shirts",
      "permalink": "category/kids/boys/boys-tops/boys-shirts",
      "parent_id": 17,
      "taxonomy_id": 4,
      "url_override": null,
      "description": "Boys Shirts",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 19,
      "name": "Girls",
      "pretty_name": "Category -> Kids -> Girls",
      "permalink": "category/kids/girls",
      "parent_id": 15,
      "taxonomy_id": 4,
      "url_override": null,
      "description": "Girls",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 20,
      "name": "Girls Tops",
      "pretty_name": "Category -> Kids -> Girls -> Girls Tops",
      "permalink": "category/kids/girls/girls-tops",
      "parent_id": 19,
      "taxonomy_id": 4,
      "url_override": null,
      "description": "Girls Tops",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 21,
      "name": "Girls Shirts",
      "pretty_name": "Category -> Kids -> Girls -> Girls Tops -> Girls Shirts",
      "permalink": "category/kids/girls/girls-tops/girls-shirts",
      "parent_id": 20,
      "taxonomy_id": 4,
      "url_override": null,
      "description": "Girls Shirts",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 22,
      "name": "Brand",
      "pretty_name": "Brand",
      "permalink": "brand",
      "parent_id": null,
      "taxonomy_id": 5,
      "url_override": null,
      "description": "Brand",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 23,
      "name": "Ruby on Rails - 3",
      "pretty_name": "Brand -> Ruby on Rails - 3",
      "permalink": "brand/ruby-on-rails-3",
      "parent_id": 22,
      "taxonomy_id": 5,
      "url_override": null,
      "description": "Ruby on Rails - 3",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 24,
      "name": "Ruby on Rails - 4",
      "pretty_name": "Brand -> Ruby on Rails - 4",
      "permalink": "brand/ruby-on-rails-4",
      "parent_id": 22,
      "taxonomy_id": 5,
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
ETag: W/&quot;86f93e076e4a257860cc624d8b95356a&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: e94f1410-c2ee-4b48-8a0e-cbc87a899523
X-Runtime: 0.107708
Vary: Origin
Content-Length: 148
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
user[email]=email5%40example.com&user[password]=secret
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
Authorization: Bearer 8bbff1fad9781abc6048115d05a9644bb9a961cfab4fb0af
ETag: W/&quot;e4b2e42861663042c159287fab0f005f&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 93605ea4-ed76-412f-8bc8-46999004655d
X-Runtime: 0.012017
Vary: Origin
Content-Length: 559
200 OK
```


```json
{
  "id": 5,
  "email": "email5@example.com",
  "persistence_token": null,
  "perishable_token": null,
  "last_request_at": null,
  "login": "email5@example.com",
  "ship_address_id": null,
  "bill_address_id": null,
  "created_at": "2019-12-13T08:19:20.354-05:00",
  "updated_at": "2019-12-13T08:19:20.356-05:00",
  "spree_api_key": "8bbff1fad9781abc6048115d05a9644bb9a961cfab4fb0af",
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
X-Spree-Order-Token: 9ILEjKXi5-qsqtFGMgt6xA
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/users/login`

#### Parameters


```json
user[email]=email6%40example.com&user[password]=secret&order_number=M497926168
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
Authorization: Bearer f2afd9ac02e1be5e7a424f2c9813c51c8261a5694b6fa774
ETag: W/&quot;44c4f7aa68cb6945979f19fe8bf2125d&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: b96f0d93-4f99-436f-946f-e1f69f48b849
X-Runtime: 0.016371
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
  "created_at": "2019-12-13T08:19:20.375-05:00",
  "updated_at": "2019-12-13T08:19:20.376-05:00",
  "spree_api_key": "f2afd9ac02e1be5e7a424f2c9813c51c8261a5694b6fa774",
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
Authorizat IO N: Bearer 1a47622278fab88679754a1fc8a17d9a8b025a1982a78f90
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
Authorization: Bearer 1a47622278fab88679754a1fc8a17d9a8b025a1982a78f90
ETag: W/&quot;c02fc196911fe23515456df9c0a8d039&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: fd963b99-ac2b-4c0a-ab94-6a3b7faa1aea
X-Runtime: 0.025415
Vary: Origin
Content-Length: 1511
200 OK
```


```json
{
  "email": "email8@example.com",
  "first_name": null,
  "last_name": null,
  "id": 9,
  "subscribed": false,
  "addresses": [
    {
      "id": 7,
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
      "default": true
    },
    {
      "id": 6,
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
        "created_at": "2019-12-13T08:19:20.976-05:00",
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
        "created_at": "2019-12-13T08:19:21.002-05:00",
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
        "created_at": "2019-12-13T08:19:21.019-05:00",
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
Authorization: Bearer b90ea62ff86bd384f137b9875be14d476380e231470fc768
ETag: W/&quot;caa03b280c85e62523d5fbad082b8359&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: e751ec19-7d73-4893-94c2-8ab7e81acb1c
X-Runtime: 0.020020
Vary: Origin
Content-Length: 184
201 Created
```


```json
{
  "id": 8,
  "email": "test@example.com",
  "created_at": "2019-12-13T08:19:20.877-05:00",
  "updated_at": "2019-12-13T08:19:20.879-05:00",
  "subscribed": false,
  "bill_address": null,
  "ship_address": null
}
```



## Subscribe a user


### Request

#### Endpoint

```plaintext
PUT /api/users/4/subscribe
Authorizat IO N: Bearer e728ecc46aa57ff508e8c9672255399d8d8e9978ade37b5d
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
Authorization: Bearer e728ecc46aa57ff508e8c9672255399d8d8e9978ade37b5d
ETag: W/&quot;3ab1d0b89ada99f99808abb911105140&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 7a8b7f3d-dadf-4336-8042-fcb5ffbb1a16
X-Runtime: 0.040637
Vary: Origin
Content-Length: 185
200 OK
```


```json
{
  "id": 4,
  "email": "email4@example.com",
  "created_at": "2019-12-13T08:19:20.299-05:00",
  "updated_at": "2019-12-13T08:19:20.301-05:00",
  "subscribed": true,
  "bill_address": null,
  "ship_address": null
}
```



## Unsubscribe a user


### Request

#### Endpoint

```plaintext
PUT /api/users/7/unsubscribe
Authorizat IO N: Bearer e36ce8d9d06301b71b83251d290f02ffd56afa04e6253a6a
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
Authorization: Bearer e36ce8d9d06301b71b83251d290f02ffd56afa04e6253a6a
ETag: W/&quot;17390b3779c3d7f4f6fc91d9d06ba0e4&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 1ce7133f-bfac-421a-93ae-e67bf5ee5f7b
X-Runtime: 0.017118
Vary: Origin
Content-Length: 186
200 OK
```


```json
{
  "id": 7,
  "email": "email7@example.com",
  "created_at": "2019-12-13T08:19:20.836-05:00",
  "updated_at": "2019-12-13T08:19:20.838-05:00",
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
ETag: W/&quot;0ef3994950d01e1063676f102f9af701&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 956c88b6-bc4e-4903-ae4a-583c2a29d07c
X-Runtime: 0.145726
Vary: Origin
Content-Length: 1921
200 OK
```


```json
{
  "id": 2,
  "name": "Product #1 - 7408",
  "sku": "SKU-1",
  "weight": "0.0",
  "height": null,
  "width": null,
  "depth": null,
  "is_master": false,
  "slug": "product-1-7408",
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
      "attachment_updated_at": "2019-12-13T08:19:19.812-05:00",
      "attachment_width": 489,
      "attachment_height": 490,
      "alt": null,
      "viewable_type": "Spree::Variant",
      "viewable_id": 2,
      "mini_url": "/spree/products/1/mini/thinking-cat.jpg?1576243159",
      "small_url": "/spree/products/1/small/thinking-cat.jpg?1576243159",
      "product_url": "/spree/products/1/product/thinking-cat.jpg?1576243159",
      "large_url": "/spree/products/1/large/thinking-cat.jpg?1576243159"
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
Authorizat IO N: Bearer 1093d2978f1f46612b07ef3d7d6dee14932ceef54fd6aee2
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
ETag: W/&quot;3ea37f1c3550c8e1e9483e390724b145&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: fc4c04e6-ed1e-48d6-87f4-40b98a9a285c
X-Runtime: 0.033097
Vary: Origin
Content-Length: 206
200 OK
```


```json
[
  {
    "id": 4,
    "user_id": 68,
    "payment_source_type": "SolidusPaypalBraintree::Source",
    "payment_source_id": 6,
    "default": false,
    "created_at": "2019-12-13T08:19:30.782-05:00",
    "updated_at": "2019-12-13T08:19:30.782-05:00"
  }
]
```



## Remove the payment from the user wallet


### Request

#### Endpoint

```plaintext
DELETE /api/wallet_payment_sources/6
Accept: application/json
Authorizat IO N: Bearer 3c40eb563c9b75ec3b0912a7988d669aff68ea02ad005eab
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
X-Request-Id: b2751b87-3730-4fea-a820-4454566ba037
X-Runtime: 0.011040
Vary: Origin
204 No Content
```




## Set a wallet payment source as the default user payment method


### Request

#### Endpoint

```plaintext
POST /api/wallet_payment_sources/5/default
Accept: application/json
Authorizat IO N: Bearer 3979784213c9209a7075ecb44457bb764ac7f013262d7701
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
X-Request-Id: 0c45bfb5-5bb3-4e0a-946e-b35fe5e79df4
X-Runtime: 0.008914
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
Authorizat IO N: Bearer 0532fb7b574739ddc3e924ab844a5d4bcecdcadf9e2b38cb
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/wished_products`

#### Parameters


```json
wished_product[wishlist_id]=30&wished_product[variant_id]=58&wished_product[quantity]=2&wished_product[remark]=Foo+bar
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
ETag: W/&quot;a2bf7bb535ddf3c2a907eca61d68ee77&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 5f65d415-8d32-42bb-85c7-18fc6f02cf80
X-Runtime: 0.011962
Vary: Origin
Content-Length: 74
201 Created
```


```json
{
  "id": 13,
  "wishlist_id": 30,
  "variant_id": 58,
  "quantity": 2,
  "remark": "Foo bar"
}
```



## Delete a wished product


### Request

#### Endpoint

```plaintext
DELETE /api/wished_products/14
Accept: application/json
Authorizat IO N: Bearer 911881cbcc03df84a627d233309467f2307952d21fefa8ec
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
X-Request-Id: 96519dac-14bf-47d7-98ca-78d1c2d61414
X-Runtime: 0.011776
Vary: Origin
204 No Content
```




## Get a single wished product


### Request

#### Endpoint

```plaintext
GET /api/wished_products/10
Accept: application/json
Authorizat IO N: Bearer 8ad02ac100b32a4dba0292442e5435baa285ca2bd3c4d41c
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
ETag: W/&quot;f70c677f038f21c8ea900eb1d4ee71aa&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 7e2c0a78-baf5-4997-9001-91caa91f018a
X-Runtime: 0.033575
Vary: Origin
Content-Length: 69
200 OK
```


```json
{
  "id": 10,
  "wishlist_id": 29,
  "variant_id": 52,
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
Authorizat IO N: Bearer 858e88abd8f09869cac898e18379a007a1dc6695b79c656e
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
ETag: W/&quot;a5e01e715b51c77f2029426a2182c019&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 8ff9e3fe-72ec-4cd8-a159-5fcbcc71aa95
X-Runtime: 0.008766
Vary: Origin
Content-Length: 298
200 OK
```


```json
{
  "wished_products": [
    {
      "id": 17,
      "wishlist_id": 32,
      "variant_id": 66,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 18,
      "wishlist_id": 33,
      "variant_id": 68,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 19,
      "wishlist_id": 34,
      "variant_id": 70,
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
Authorizat IO N: Bearer e1176a5b5f73439adc01f41313518d9596285bcacae55025
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
ETag: W/&quot;4c9e490690a6f6e127e9cbb0720c0904&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 8b6b04c2-22a0-4c17-b3df-33d99d002e97
X-Runtime: 0.100393
Vary: Origin
Content-Length: 2146
200 OK
```


```json
{
  "wished_products": [
    {
      "id": 20,
      "wishlist_id": 35,
      "variant_id": 72,
      "quantity": 1,
      "remark": null,
      "variant": {
        "id": 72,
        "name": "Product #36 - 4108",
        "sku": "SKU-71",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-36-4108",
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
    },
    {
      "id": 21,
      "wishlist_id": 36,
      "variant_id": 74,
      "quantity": 1,
      "remark": null,
      "variant": {
        "id": 74,
        "name": "Product #37 - 4357",
        "sku": "SKU-73",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-37-4357",
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
      "wishlist_id": 37,
      "variant_id": 76,
      "quantity": 1,
      "remark": null,
      "variant": {
        "id": 76,
        "name": "Product #38 - 2835",
        "sku": "SKU-75",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-38-2835",
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
Authorizat IO N: Bearer 08dcccb7c445f9361bc1fc9bcff7043272dc241d579869c4
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
ETag: W/&quot;71f480c496daa4e12fe847ce123de5cc&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 7cf11211-6828-4505-baf8-58a9d93e0f4c
X-Runtime: 0.078592
Vary: Origin
Content-Length: 2086
200 OK
```


```json
{
  "wished_products": [
    {
      "id": 29,
      "wishlist_id": 40,
      "variant_id": 92,
      "quantity": 1,
      "remark": null,
      "variant": {
        "id": 92,
        "name": "Product #46 - 2946",
        "sku": "SKU-91",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-46-2946",
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
      "variant_id": 94,
      "quantity": 1,
      "remark": null,
      "variant": {
        "id": 94,
        "name": "Product #47 - 5746",
        "sku": "SKU-93",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-47-5746",
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
      "variant_id": 96,
      "quantity": 1,
      "remark": null,
      "variant": {
        "id": 96,
        "name": "Product #48 - 3643",
        "sku": "SKU-95",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-48-3643",
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
Authorizat IO N: Bearer ed4690e42add690147558100939d9f78d248343baac4a0f1
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
ETag: W/&quot;d8903d98b9f1495b1f0f58cd5f61c669&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: e1f25de2-e6e3-4792-8578-bef674a04305
X-Runtime: 0.008640
Vary: Origin
Content-Length: 298
200 OK
```


```json
{
  "wished_products": [
    {
      "id": 26,
      "wishlist_id": 39,
      "variant_id": 86,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 27,
      "wishlist_id": 39,
      "variant_id": 88,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 28,
      "wishlist_id": 39,
      "variant_id": 90,
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
PATCH /api/wished_products/23
Accept: application/json
Authorizat IO N: Bearer f676cdc8fa18da1cdce5381b997149018e26dfc0010b352d
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/wished_products/:id`

#### Parameters


```json
wished_product[wishlist_id]=38&wished_product[variant_id]=84&wished_product[quantity]=2&wished_product[remark]=Foo+bar
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
ETag: W/&quot;ac49bd73df46b91ffbe88fa2bfbd1eb7&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: ee6fe39f-5c50-4970-aaee-f735b773ee36
X-Runtime: 0.011318
Vary: Origin
Content-Length: 74
200 OK
```


```json
{
  "id": 23,
  "wishlist_id": 38,
  "variant_id": 84,
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
Authorizat IO N: Bearer be9829b810c50881c1994475fa8f2e2c938bff4507a7d558
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/wishlists`

#### Parameters


```json
wishlist[name]&wishlist[user_id]=33&wishlist[is_default]=true&wishlist[is_public]=false
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
ETag: W/&quot;8937aedc701e11df4d1896d67d2caaca&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 119a2942-564c-4531-af67-83f101a99fbb
X-Runtime: 0.013143
Vary: Origin
Content-Length: 100
201 Created
```


```json
{
  "id": 14,
  "user_id": 33,
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
Authorizat IO N: Bearer bf889f441d1dc1096fc44b26e53da16c0bdea03a08cffdd3
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
X-Request-Id: 585f63c9-4e6e-4262-a9ba-766c732e6a57
X-Runtime: 0.017981
Vary: Origin
204 No Content
```




## Get a single wishlist


### Request

#### Endpoint

```plaintext
GET /api/wishlists/1
Accept: application/json
Authorizat IO N: Bearer fc82dbd060b8f0d74dfb7ce7592cd529582bf9e0910e44b2
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
ETag: W/&quot;ca154e91f79cd06c73629fbd77b66768&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: e966e967-b198-44c5-adc3-f10f83c4a26f
X-Runtime: 0.044289
Vary: Origin
Content-Length: 302
200 OK
```


```json
{
  "id": 1,
  "user_id": 19,
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
Authorizat IO N: Bearer 24eec9481bcedbdc609b378b4ae16446d89d50f84f1cebfb
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
ETag: W/&quot;e8e5bc2c5fdd0206eb3a3870c0a98923&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: f46a6faf-6f5f-49d1-90ae-0c341e786809
X-Runtime: 0.012755
Vary: Origin
Content-Length: 880
200 OK
```


```json
{
  "wishlists": [
    {
      "id": 3,
      "user_id": 21,
      "name": "Wishlist #3",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 4,
      "user_id": 22,
      "name": "Wishlist #4",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 5,
      "user_id": 23,
      "name": "Wishlist #5",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 6,
      "user_id": 24,
      "name": "Wishlist #6",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 7,
      "user_id": 25,
      "name": "Wishlist #7",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 8,
      "user_id": 26,
      "name": "Wishlist #8",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 9,
      "user_id": 27,
      "name": "Wishlist #9",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 10,
      "user_id": 28,
      "name": "Wishlist #10",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 11,
      "user_id": 29,
      "name": "Wishlist #11",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 12,
      "user_id": 30,
      "name": "Wishlist #12",
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
Authorizat IO N: Bearer e28118404eb1dbbc14a59fb3f011e6bbdc26b556228fe98e
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
ETag: W/&quot;a560739fc152484592257097ca826d6d&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 8b539d12-3736-46b6-9083-17c843574572
X-Runtime: 0.008851
Vary: Origin
Content-Length: 302
200 OK
```


```json
{
  "id": 2,
  "user_id": 20,
  "name": "Wishlist #2",
  "is_public": false,
  "is_default": true,
  "wished_products": [
    {
      "id": 4,
      "wishlist_id": 2,
      "variant_id": 40,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 5,
      "wishlist_id": 2,
      "variant_id": 42,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 6,
      "wishlist_id": 2,
      "variant_id": 44,
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
Authorizat IO N: Bearer 27fc37008749026a2ecf4ffb0ef69ac689c04798b643b2af
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
ETag: W/&quot;2be1d9173e657e60abbc64ddef7102e2&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: bdc81381-cb5f-44ec-bc9e-d5a499554aa8
X-Runtime: 0.011100
Vary: Origin
Content-Length: 903
200 OK
```


```json
{
  "wishlists": [
    {
      "id": 18,
      "user_id": 35,
      "name": "Wishlist #16",
      "is_public": false,
      "is_default": true
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
    },
    {
      "id": 27,
      "user_id": 35,
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
PATCH /api/wishlists/28
Accept: application/json
Authorizat IO N: Bearer 8cc14a9c6a8c8a78f1b02143802287b2c2ba5702a62ce06b
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
ETag: W/&quot;ac73fc6dc9a6f3e7a376d2f6fb801097&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 7b34870c-baa4-44d6-979f-dce564efa9f3
X-Runtime: 0.012616
Vary: Origin
Content-Length: 311
200 OK
```


```json
{
  "id": 28,
  "user_id": 36,
  "name": "Another Wishlist",
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



