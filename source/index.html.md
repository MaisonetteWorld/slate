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
PUT /api/orders/M851606214/addresses/32
Accept: application/json
X-Spree-Order-Token: kH0SSdGr8GQxH-PiKysHRA
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
ETag: W/&quot;c1e1d94de8ea4cebb75f469dfc795e7a&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 5e58934a-7460-47f0-88d7-0d6c079b5e0e
X-Runtime: 0.042317
Vary: Origin
Content-Length: 516
200 OK
```


```json
{
  "id": 33,
  "firstname": "John the Tester",
  "lastname": "Smith",
  "full_name": "John the Tester Smith",
  "address1": "A Different Road",
  "address2": "Northwest",
  "city": "Herndon",
  "zipcode": "10028",
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

Please do not send billing address attributes at all if there is no billing address, otherwise you will get an order error


## Creating a PayPal express checkout transaction


### Request

#### Endpoint

```plaintext
POST /api/braintree/transactions
Accept: application/json
X-Spree-Order-Token: yGNV4ksDefn8uhcEmIKqxw
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/braintree/transactions`

#### Parameters


```json
order_id=M037158619&payment_method_id=2&transaction[email]=maryellen.oga%40mckenziemcglynn.com&transaction[nonce]=fake-paypal-billing-agreement-nonce&transaction[phone]=555-555-0199&transaction[shipping_address_attributes][first_name]=John&transaction[shipping_address_attributes][last_name]=Stamm&transaction[shipping_address_attributes][address_line_1]=A+Different+Road&transaction[shipping_address_attributes][city]=Herndon&transaction[shipping_address_attributes][state_code]=AL&transaction[shipping_address_attributes][zip]=10003&transaction[shipping_address_attributes][country_code]=US&transaction[payment_type]=PayPalAccount&transaction[billing_address_attributes][first_name]=John&transaction[billing_address_attributes][last_name]=Stamm&transaction[billing_address_attributes][address_line_1]=A+Different+Road&transaction[billing_address_attributes][city]=Herndon&transaction[billing_address_attributes][state_code]=AL&transaction[billing_address_attributes][zip]=10003&transaction[billing_address_attributes][country_code]=US
```


| Name | Description |
|:-----|:------------|
| order_id *required* | The order number |
| payment_method_id *required* | The payment method id |
| transaction[device_data] *required* | The device_data |
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
ETag: W/&quot;66a48d63c84db8d7b012a57f44c5c366&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: df18a03a-c130-459c-9cb8-a6063a0dcd6e
X-Runtime: 0.342069
Vary: Origin
Content-Length: 5228
200 OK
```


```json
{
  "id": 2,
  "number": "M037158619",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2021-03-31T06:14:51.269-04:00",
  "updated_at": "2021-03-31T06:14:51.592-04:00",
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
  "token": "yGNV4ksDefn8uhcEmIKqxw",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order?order=M037158619&bzip=10003&init=true",
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
        "name": "Product #2 - 4736",
        "sku": "SKU-3",
        "is_master": false,
        "slug": "product-2-4736",
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
        "videos": [

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
      "domestic_override": false,
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
      "created_at": "2021-03-31T06:14:51.373-04:00",
      "updated_at": "2021-03-31T06:14:51.373-04:00",
      "payment_method": {
        "id": 2,
        "name": "Braintree"
      },
      "source": {
        "id": 2,
        "payment_type": "PayPalAccount",
        "token": "bgx899",
        "created_at": "2021-03-31T06:14:51.372-04:00",
        "email": "jane.doe@paypal.com"
      }
    }
  ],
  "shipments": [
    {
      "id": 4,
      "tracking": null,
      "tracking_url": null,
      "number": "H38076246445",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M037158619",
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
          "extra_cost": "+$100.00"
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
        "extra_cost": "+$100.00",
        "base_flat_rate_amount": 0.0
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
      "delivery_estimation": "Apr 02",
      "estimated_giftwrap_price": "5.0",
      "display_estimated_giftwrap_price": "$5.00"
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
X-Spree-Order-Token: jVgERAtATAhr98rW8vmeng
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/braintree/transactions`

#### Parameters


```json
order_id=M991816946&payment_method_id=1&transaction[email]=maryellen.oga%40mckenziemcglynn.com&transaction[nonce]=fake-apple-pay-visa-nonce&transaction[phone]=555-555-0199&transaction[shipping_address_attributes][first_name]=John&transaction[shipping_address_attributes][last_name]=Stamm&transaction[shipping_address_attributes][address_line_1]=A+Different+Road&transaction[shipping_address_attributes][city]=Herndon&transaction[shipping_address_attributes][state_code]=AL&transaction[shipping_address_attributes][zip]=10001&transaction[shipping_address_attributes][country_code]=US&transaction[payment_type]=ApplePayCard
```


| Name | Description |
|:-----|:------------|
| order_id *required* | The order number |
| payment_method_id *required* | The payment method id |
| transaction[device_data] *required* | The device_data |
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
ETag: W/&quot;96666903d652e0497bc0eeabb97b1823&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 91c35e4c-bfe4-4679-98cc-0104584fa448
X-Runtime: 0.745323
Vary: Origin
Content-Length: 5272
200 OK
```


```json
{
  "id": 1,
  "number": "M991816946",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2021-03-31T06:14:49.908-04:00",
  "updated_at": "2021-03-31T06:14:50.687-04:00",
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
  "token": "jVgERAtATAhr98rW8vmeng",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order?order=M991816946&bzip=10001&init=true",
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
        "name": "Product #1 - 832",
        "sku": "SKU-1",
        "is_master": false,
        "slug": "product-1-832",
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
        "videos": [

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
      "domestic_override": false,
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
      "created_at": "2021-03-31T06:14:50.359-04:00",
      "updated_at": "2021-03-31T06:14:50.359-04:00",
      "payment_method": {
        "id": 1,
        "name": "Braintree"
      },
      "source": {
        "id": 1,
        "payment_type": "ApplePayCard",
        "token": "cg7hsk",
        "created_at": "2021-03-31T06:14:50.357-04:00",
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
      "number": "H36542775378",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M991816946",
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
          "extra_cost": "+$100.00"
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
        "extra_cost": "+$100.00",
        "base_flat_rate_amount": 0.0
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
      "delivery_estimation": "Apr 02",
      "estimated_giftwrap_price": "5.0",
      "display_estimated_giftwrap_price": "$5.00"
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
PUT /api/checkouts/M309395797/complete
Accept: application/json
X-Spree-Order-Token: au8Wk1BopC6cC5nu6M_fiw
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
ETag: W/&quot;9219a3321fe49f16ae9be323ff8cb095&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 3ff822e8-6faf-4139-9af1-722deab760d2
X-Runtime: 0.428019
Vary: Origin
Content-Length: 5418
200 OK
```


```json
{
  "id": 23,
  "number": "M309395797",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "complete",
  "adjustment_total": "0.0",
  "user_id": 84,
  "created_at": "2021-03-31T06:15:10.884-04:00",
  "updated_at": "2021-03-31T06:15:11.289-04:00",
  "completed_at": "2021-03-31T06:15:11.270-04:00",
  "payment_total": "110.0",
  "shipment_state": "ready",
  "payment_state": "paid",
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
  "token": "au8Wk1BopC6cC5nu6M_fiw",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order?order=M309395797&bzip=10037&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [
    {
      "id": 17,
      "name": "Braintree"
    },
    {
      "id": 18,
      "name": "Braintree"
    }
  ],
  "bill_address": {
    "id": 42,
    "firstname": "John",
    "lastname": "Smith",
    "full_name": "John Smith",
    "address1": "PO Box 1337",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10037",
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
    "id": 43,
    "firstname": "John",
    "lastname": "Smith",
    "full_name": "John Smith",
    "address1": "A Different Road",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10038",
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
      "id": 28,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 115,
      "vendor_id": 241,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "breadcrumb_taxons": [

      ],
      "variant": {
        "id": 115,
        "name": "Product #63 - 4110",
        "sku": "SKU-114",
        "is_master": false,
        "slug": "product-63-4110",
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
        "videos": [

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
      "vendor_name": "Vendor #241",
      "country_iso": "US",
      "domestic_override": false,
      "adjustments": [

      ]
    }
  ],
  "payments": [
    {
      "id": 7,
      "source_type": "SolidusPaypalBraintree::Source",
      "source_id": 9,
      "amount": "110.0",
      "display_amount": "$110.00",
      "payment_method_id": 17,
      "state": "completed",
      "avs_response": "M",
      "created_at": "2021-03-31T06:15:10.977-04:00",
      "updated_at": "2021-03-31T06:15:11.117-04:00",
      "payment_method": {
        "id": 17,
        "name": "Braintree"
      },
      "source": {
        "id": 9,
        "payment_type": "CreditCard",
        "token": "4rptfz",
        "created_at": "2021-03-31T06:15:10.976-04:00",
        "cc_type": "Visa",
        "last_digits": "1881",
        "month": "12",
        "year": "2020"
      }
    }
  ],
  "shipments": [
    {
      "id": 23,
      "tracking": "U10000",
      "tracking_url": null,
      "number": "H17776454083",
      "cost": "100.0",
      "shipped_at": null,
      "state": "ready",
      "order_id": "M309395797",
      "stock_location_name": "NY Warehouse 46",
      "giftwrappable": false,
      "stock_location_id": 46,
      "giftwrap": null,
      "shipping_rates": [
        {
          "id": 23,
          "name": "UPS Ground",
          "admin_name": null,
          "cost": "100.0",
          "selected": true,
          "shipping_method_id": 17,
          "shipping_method_code": "UPS_GROUND",
          "extra_cost": "+$100.00"
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
        "extra_cost": "+$100.00",
        "base_flat_rate_amount": 0.0
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
              "id": 38,
              "name": "ShippingCategory #36"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 115,
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
      "delivery_estimation": "Apr 02",
      "estimated_giftwrap_price": "5.0",
      "display_estimated_giftwrap_price": "$5.00"
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
PATCH /api/checkouts/M928594170
Accept: application/json
X-Spree-Order-Token: WlU_-58kNJVuuYpC_Z4RHA
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][source_attributes][device_data]=fake+device+data
```


| Name | Description |
|:-----|:------------|
| id *required* | The order number |
| order[payment_attributes] *required* | The payment attibutes |
| order[payment_attributes][payment_method_id] *required* | The payment method id |
| order[payment_attributes][source_attributes][nonce] *required* | The payment nonce |
| order[payment_attributes][source_attributes][device_data]  | The Braintree device data |
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
ETag: W/&quot;3d6abe6067991faf27cae7adbf8d5f88&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 971b529d-7108-4b19-8679-1e6c996f1a36
X-Runtime: 0.135378
Vary: Origin
Content-Length: 4847
200 OK
```


```json
{
  "id": 28,
  "number": "M928594170",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 89,
  "created_at": "2021-03-31T06:15:14.180-04:00",
  "updated_at": "2021-03-31T06:15:14.502-04:00",
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
  "use_store_credits": false,
  "first_order": false,
  "display_item_total": "$10.00",
  "total_quantity": 1,
  "display_total": "$110.00",
  "display_ship_total": "$100.00",
  "display_tax_total": "$0.00",
  "token": "WlU_-58kNJVuuYpC_Z4RHA",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order?order=M928594170&bzip=10046&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [
    {
      "id": 22,
      "name": "Braintree"
    }
  ],
  "bill_address": {
    "id": 51,
    "firstname": "John",
    "lastname": "Smith",
    "full_name": "John Smith",
    "address1": "PO Box 1337",
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
  "ship_address": {
    "id": 52,
    "firstname": "John",
    "lastname": "Smith",
    "full_name": "John Smith",
    "address1": "A Different Road",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10047",
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
      "id": 33,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 125,
      "vendor_id": 266,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 125,
        "name": "Product #68 - 1765",
        "sku": "SKU-124",
        "is_master": false,
        "slug": "product-68-1765",
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
        "videos": [

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
      "vendor_name": "Vendor #266",
      "country_iso": "US",
      "domestic_override": false,
      "adjustments": [

      ]
    }
  ],
  "payments": [

  ],
  "shipments": [
    {
      "id": 32,
      "tracking": null,
      "tracking_url": null,
      "number": "H53325415667",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M928594170",
      "stock_location_name": "NY Warehouse 51",
      "giftwrappable": false,
      "stock_location_id": 51,
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
          "extra_cost": "+$100.00"
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
        "extra_cost": "+$100.00",
        "base_flat_rate_amount": 0.0
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
              "id": 43,
              "name": "ShippingCategory #41"
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
      "stock_location_address": "NY Warehouse 51, Washington, AL",
      "country_iso": "US",
      "international_shipping": false,
      "delivery_estimation": "Apr 02",
      "estimated_giftwrap_price": "5.0",
      "display_estimated_giftwrap_price": "$5.00"
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
PATCH /api/checkouts/M855798883
Accept: application/json
X-Spree-Order-Token: Vm1IJZsdEZA50Ns-6DCiSQ
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][source_attributes][device_data]=fake+device+data
```


| Name | Description |
|:-----|:------------|
| id *required* | The order number |
| order[payment_attributes] *required* | The payment attibutes |
| order[payment_attributes][payment_method_id] *required* | The payment method id |
| order[payment_attributes][source_attributes][nonce] *required* | The payment nonce |
| order[payment_attributes][source_attributes][device_data]  | The Braintree device data |
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
ETag: W/&quot;7b689f95a542b9eaa6c8d4d9568fdec5&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 5613ebfa-c973-45dd-ac1f-1877082233ef
X-Runtime: 0.134141
Vary: Origin
Content-Length: 4847
200 OK
```


```json
{
  "id": 27,
  "number": "M855798883",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 88,
  "created_at": "2021-03-31T06:15:13.481-04:00",
  "updated_at": "2021-03-31T06:15:13.828-04:00",
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
  "use_store_credits": false,
  "first_order": false,
  "display_item_total": "$10.00",
  "total_quantity": 1,
  "display_total": "$110.00",
  "display_ship_total": "$100.00",
  "display_tax_total": "$0.00",
  "token": "Vm1IJZsdEZA50Ns-6DCiSQ",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order?order=M855798883&bzip=10044&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [
    {
      "id": 21,
      "name": "Braintree"
    }
  ],
  "bill_address": {
    "id": 49,
    "firstname": "John",
    "lastname": "Smith",
    "full_name": "John Smith",
    "address1": "PO Box 1337",
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
  "ship_address": {
    "id": 50,
    "firstname": "John",
    "lastname": "Smith",
    "full_name": "John Smith",
    "address1": "A Different Road",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10045",
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
      "id": 32,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 123,
      "vendor_id": 261,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 123,
        "name": "Product #67 - 7055",
        "sku": "SKU-122",
        "is_master": false,
        "slug": "product-67-7055",
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
        "videos": [

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
      "vendor_name": "Vendor #261",
      "country_iso": "US",
      "domestic_override": false,
      "adjustments": [

      ]
    }
  ],
  "payments": [

  ],
  "shipments": [
    {
      "id": 30,
      "tracking": null,
      "tracking_url": null,
      "number": "H82555736101",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M855798883",
      "stock_location_name": "NY Warehouse 50",
      "giftwrappable": false,
      "stock_location_id": 50,
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
          "extra_cost": "+$100.00"
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
        "extra_cost": "+$100.00",
        "base_flat_rate_amount": 0.0
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
              "id": 42,
              "name": "ShippingCategory #40"
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
      "stock_location_address": "NY Warehouse 50, Washington, AL",
      "country_iso": "US",
      "international_shipping": false,
      "delivery_estimation": "Apr 02",
      "estimated_giftwrap_price": "5.0",
      "display_estimated_giftwrap_price": "$5.00"
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
PATCH /api/checkouts/M357131996
Accept: application/json
X-Spree-Order-Token: w68wGYB1x3Htn0r-T_9lHA
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][source_attributes][device_data]=fake+device+data
```


| Name | Description |
|:-----|:------------|
| id *required* | The order number |
| order[payment_attributes] *required* | The payment attibutes |
| order[payment_attributes][payment_method_id] *required* | The payment method id |
| order[payment_attributes][source_attributes][nonce] *required* | The payment nonce |
| order[payment_attributes][source_attributes][device_data]  | The Braintree device data |
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
ETag: W/&quot;56a344d3246b963ed029446414c91aa3&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 90b65300-53ad-4a2c-8c16-00c14c111c4e
X-Runtime: 0.136179
Vary: Origin
Content-Length: 4847
200 OK
```


```json
{
  "id": 26,
  "number": "M357131996",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 87,
  "created_at": "2021-03-31T06:15:12.802-04:00",
  "updated_at": "2021-03-31T06:15:13.150-04:00",
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
  "use_store_credits": false,
  "first_order": false,
  "display_item_total": "$10.00",
  "total_quantity": 1,
  "display_total": "$110.00",
  "display_ship_total": "$100.00",
  "display_tax_total": "$0.00",
  "token": "w68wGYB1x3Htn0r-T_9lHA",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order?order=M357131996&bzip=10042&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [
    {
      "id": 20,
      "name": "Braintree"
    }
  ],
  "bill_address": {
    "id": 47,
    "firstname": "John",
    "lastname": "Smith",
    "full_name": "John Smith",
    "address1": "PO Box 1337",
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
  "ship_address": {
    "id": 48,
    "firstname": "John",
    "lastname": "Smith",
    "full_name": "John Smith",
    "address1": "A Different Road",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10043",
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
      "id": 31,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 121,
      "vendor_id": 256,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 121,
        "name": "Product #66 - 3246",
        "sku": "SKU-120",
        "is_master": false,
        "slug": "product-66-3246",
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
        "videos": [

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
      "vendor_name": "Vendor #256",
      "country_iso": "US",
      "domestic_override": false,
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
      "number": "H23170044542",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M357131996",
      "stock_location_name": "NY Warehouse 49",
      "giftwrappable": false,
      "stock_location_id": 49,
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
          "extra_cost": "+$100.00"
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
        "extra_cost": "+$100.00",
        "base_flat_rate_amount": 0.0
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
              "id": 41,
              "name": "ShippingCategory #39"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 121,
          "quantity": 1,
          "states": {
            "on_hand": 1
          }
        }
      ],
      "adjustments": [

      ],
      "stock_location_address": "NY Warehouse 49, Washington, AL",
      "country_iso": "US",
      "international_shipping": false,
      "delivery_estimation": "Apr 02",
      "estimated_giftwrap_price": "5.0",
      "display_estimated_giftwrap_price": "$5.00"
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
PATCH /api/checkouts/M906066068
Accept: application/json
X-Spree-Order-Token: Z-pSFCmYcOwnO6-r9HkxJw
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][source_attributes][device_data]=fake+device+data
```


| Name | Description |
|:-----|:------------|
| id *required* | The order number |
| order[payment_attributes] *required* | The payment attibutes |
| order[payment_attributes][payment_method_id] *required* | The payment method id |
| order[payment_attributes][source_attributes][wallet_payment_source_id] *required* | The payment source id of a payment within the user’s payments wallet |
| order[payment_attributes][source_attributes][device_data]  | The Braintree device data |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
ETag: W/&quot;5eea041e46a316bc3f44a15aa3af06d9&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 1620d9ed-842f-4202-8283-fa8ad3c71fca
X-Runtime: 0.148916
Vary: Origin
Content-Length: 4847
200 OK
```


```json
{
  "id": 25,
  "number": "M906066068",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 86,
  "created_at": "2021-03-31T06:15:12.122-04:00",
  "updated_at": "2021-03-31T06:15:12.472-04:00",
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
  "use_store_credits": false,
  "first_order": false,
  "display_item_total": "$10.00",
  "total_quantity": 1,
  "display_total": "$110.00",
  "display_ship_total": "$100.00",
  "display_tax_total": "$0.00",
  "token": "Z-pSFCmYcOwnO6-r9HkxJw",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order?order=M906066068&bzip=10040&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [
    {
      "id": 19,
      "name": "Braintree"
    }
  ],
  "bill_address": {
    "id": 45,
    "firstname": "John",
    "lastname": "Smith",
    "full_name": "John Smith",
    "address1": "PO Box 1337",
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
  "ship_address": {
    "id": 46,
    "firstname": "John",
    "lastname": "Smith",
    "full_name": "John Smith",
    "address1": "A Different Road",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10041",
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
      "id": 30,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 119,
      "vendor_id": 251,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 119,
        "name": "Product #65 - 1500",
        "sku": "SKU-118",
        "is_master": false,
        "slug": "product-65-1500",
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
        "videos": [

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
      "vendor_name": "Vendor #251",
      "country_iso": "US",
      "domestic_override": false,
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
      "number": "H06085031558",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M906066068",
      "stock_location_name": "NY Warehouse 48",
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
          "shipping_method_id": 19,
          "shipping_method_code": "UPS_GROUND",
          "extra_cost": "+$100.00"
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
        "extra_cost": "+$100.00",
        "base_flat_rate_amount": 0.0
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
              "id": 40,
              "name": "ShippingCategory #38"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 119,
          "quantity": 1,
          "states": {
            "on_hand": 1
          }
        }
      ],
      "adjustments": [

      ],
      "stock_location_address": "NY Warehouse 48, Washington, AL",
      "country_iso": "US",
      "international_shipping": false,
      "delivery_estimation": "Apr 02",
      "estimated_giftwrap_price": "5.0",
      "display_estimated_giftwrap_price": "$5.00"
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
PUT /api/checkouts/M107899975
Accept: application/json
X-Spree-Order-Token: XyDhmCdfYKCMLNp6aK9ZfQ
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PUT /api/checkouts/:id`

#### Parameters


```json
order[ship_address_attributes][id]&order[ship_address_attributes][firstname]=John&order[ship_address_attributes][lastname]=Smith&order[ship_address_attributes][address1]=10+Lovely+Street&order[ship_address_attributes][address2]=Northwest&order[ship_address_attributes][city]=Herndon&order[ship_address_attributes][zipcode]=10039&order[ship_address_attributes][phone]=555-555-0199&order[ship_address_attributes][state_name]&order[ship_address_attributes][alternative_phone]=555-555-0199&order[ship_address_attributes][company]=Company&order[ship_address_attributes][state_id]=41&order[ship_address_attributes][country_id]=41&order[ship_address_attributes][created_at]&order[ship_address_attributes][updated_at]&order[use_billing]=true&hold_state=true
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
ETag: W/&quot;7ad03c9d3fde1addde2951799cc19738&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: b912e9b0-bf35-45b5-96e8-7bb2bc5c6242
X-Runtime: 0.127853
Vary: Origin
Content-Length: 4821
200 OK
```


```json
{
  "id": 24,
  "number": "M107899975",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "cart",
  "adjustment_total": "0.0",
  "user_id": 85,
  "created_at": "2021-03-31T06:15:11.654-04:00",
  "updated_at": "2021-03-31T06:15:11.759-04:00",
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
  "token": "XyDhmCdfYKCMLNp6aK9ZfQ",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order?order=M107899975&bzip=10039&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [

  ],
  "bill_address": {
    "id": 44,
    "firstname": "John",
    "lastname": "Smith",
    "full_name": "John Smith",
    "address1": "10 Lovely Street",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10039",
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
    "id": 44,
    "firstname": "John",
    "lastname": "Smith",
    "full_name": "John Smith",
    "address1": "10 Lovely Street",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10039",
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
      "id": 29,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 117,
      "vendor_id": 246,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 117,
        "name": "Product #64 - 1369",
        "sku": "SKU-116",
        "is_master": false,
        "slug": "product-64-1369",
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
        "videos": [

        ],
        "product_id": 64,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [

      ],
      "vendor_name": "Vendor #246",
      "country_iso": "US",
      "domestic_override": false,
      "adjustments": [

      ]
    }
  ],
  "payments": [

  ],
  "shipments": [
    {
      "id": 24,
      "tracking": "U10000",
      "tracking_url": null,
      "number": "H71378370682",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M107899975",
      "stock_location_name": "NY Warehouse 47",
      "giftwrappable": false,
      "stock_location_id": 47,
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
          "extra_cost": "+$100.00"
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
        "extra_cost": "+$100.00",
        "base_flat_rate_amount": 0.0
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
              "id": 39,
              "name": "ShippingCategory #37"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 117,
          "quantity": 1,
          "states": {
            "on_hand": 1
          }
        }
      ],
      "adjustments": [

      ],
      "stock_location_address": "NY Warehouse 47, Washington, AL",
      "country_iso": "US",
      "international_shipping": false,
      "delivery_estimation": "Apr 02",
      "estimated_giftwrap_price": "5.0",
      "display_estimated_giftwrap_price": "$5.00"
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
POST /api/shipments/H40720704135/giftwrap
Accept: application/json
X-Spree-Order-Token: Z6UqlCY3_lPF1X-yXivWhw
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/shipments/:shipment_number/giftwrap`

#### Parameters


```json
order_number=M831094608
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
X-Request-Id: db736885-2783-42fe-a798-68b1cde86ed4
X-Runtime: 0.035824
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
DELETE /api/shipments/H63342284806/giftwrap
Accept: application/json
X-Spree-Order-Token: BKtnsLh942Uii_q25xzbXA
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`DELETE /api/shipments/:shipment_number/giftwrap`

#### Parameters


```json
order_number=M729034973
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
X-Request-Id: 33ad897a-5263-43a4-888d-e7193be9ed56
X-Runtime: 0.035106
Vary: Origin
204 No Content
```




# LineItem

Representation of a single cart item for a specific variant with price of vendor

## Creating a line item


### Request

#### Endpoint

```plaintext
POST /api/orders/M418305776/line_items
Accept: application/json
Authorizat IO N: Bearer e54998f6eb06fe0c124f20bc1884a0ded7e7e3f9bd07d46b
X-Spree-Order-Token: S6za_BzMtudzp9kKWJ8CVA
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/:order_number/line_items`

#### Parameters


```json
line_item[variant_id]=24&line_item[options][vendor_id]=49&line_item[quantity]=1
```


| Name | Description |
|:-----|:------------|
| line_item[variant_id] *required* | Line item variant |
| line_item[options]  | Hash containing the vendor_id. It's used to set the price based on vendor |
| line_item[quantity]  | Line item quantity |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
ETag: W/&quot;d5d7daac3d720812451e33548b60d6b6&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: e4bcdcc7-e1cd-4ecb-9e9c-c5df8eb25b62
X-Runtime: 0.104117
Vary: Origin
Content-Length: 939
201 Created
```


```json
{
  "id": 10,
  "quantity": 1,
  "price": "19.99",
  "variant_id": 24,
  "vendor_id": 49,
  "single_display_amount": "$19.99",
  "display_amount": "$19.99",
  "total": "19.99",
  "on_sale": false,
  "final_sale": false,
  "backordered": null,
  "promotionable": true,
  "variant": {
    "id": 24,
    "name": "Product #12 - 9514",
    "sku": "SKU-23",
    "is_master": false,
    "slug": "product-12-9514",
    "description": "As seen on TV!",
    "track_inventory": true,
    "cost_price": "17.0",
    "price": "19.99",
    "display_price": "$19.99",
    "options_text": "Size: S",
    "in_stock": false,
    "is_backorderable": true,
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
    "videos": [

    ],
    "product_id": 12,
    "lead_time": 2,
    "brand": null,
    "brand_slug": null,
    "brand_description": null
  },
  "monogram": null,
  "gift_cards": [

  ],
  "vendor_name": "Vendor #49",
  "country_iso": null,
  "domestic_override": null,
  "adjustments": [

  ]
}
```



## Creating a line item gift card


### Request

#### Endpoint

```plaintext
POST /api/orders/M184009044/line_items
Accept: application/json
Authorizat IO N: Bearer 1cbed793bc3175e300d46de2e57cbd940d73b75ea8307da0
X-Spree-Order-Token: y3QTs8t5RVvqK6GVsfBxgQ
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/:order_number/line_items`

#### Parameters


```json
line_item[variant_id]=14&line_item[options][vendor_id]=30&line_item[options][gift_card_details][recipient_name]=Recipient+John&line_item[options][gift_card_details][recipient_email]=recipient%40email.com&line_item[options][gift_card_details][purchaser_name]=Purchaser+Bob&line_item[options][gift_card_details][gift_message]=Surprise&line_item[options][gift_card_details][send_email_at]=2021-03-31+06%3A14%3A53+-0400&line_item[quantity]=1
```


| Name | Description |
|:-----|:------------|
| line_item[variant_id] *required* | Line item variant |
| line_item[options]  | Hash containing the vendor_id and gift card details.
                          It's used to set the price based on vendor |
| line_item[quantity]  | Line item quantity |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: application/json; charset=utf-8
ETag: W/&quot;aba80b25b0bf8e352d72b2201c8d3436&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: a70d48ea-55d7-4af4-8219-879f516c0624
X-Runtime: 0.205684
Vary: Origin
Content-Length: 1067
201 Created
```


```json
{
  "id": 6,
  "quantity": 1,
  "price": "19.99",
  "variant_id": 14,
  "vendor_id": 30,
  "single_display_amount": "$19.99",
  "display_amount": "$19.99",
  "total": "19.99",
  "on_sale": false,
  "final_sale": false,
  "backordered": null,
  "promotionable": true,
  "variant": {
    "id": 14,
    "name": "Product #6 - 4138",
    "sku": "SKU-14",
    "is_master": false,
    "slug": "product-6-4138",
    "description": "As seen on TV!",
    "track_inventory": true,
    "cost_price": "17.0",
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
    "videos": [

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
      "send_email_at": "2021-03-31T00:00:00.000-04:00"
    }
  ],
  "vendor_name": "Vendor #30",
  "country_iso": null,
  "domestic_override": null,
  "adjustments": [

  ]
}
```



## Deleting a line item


### Request

#### Endpoint

```plaintext
DELETE /api/orders/M732927650/line_items/8
Accept: application/json
Authorizat IO N: Bearer 3c5d0701a1166a1c2cce87be85923174afe738da8b0510da
X-Spree-Order-Token: cIkyvSI7lomBEB7rDS54aA
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
X-Request-Id: d8b51505-81b6-4a48-867d-3555d531b2df
X-Runtime: 0.075162
Vary: Origin
204 No Content
```




## Updating a line item


### Request

#### Endpoint

```plaintext
PUT /api/orders/M495506895/line_items/7
Accept: application/json
Authorizat IO N: Bearer ddcaea415266a1c13ae1019f8fa45ec9fc2a6d8a7ccfbbec
X-Spree-Order-Token: 8YmtMRUSBDiGvUh-6nkzvQ
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
ETag: W/&quot;1bf4af912ce211989afe04db78055314&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 2aee0513-0779-4377-88ab-3b71eb833131
X-Runtime: 0.113013
Vary: Origin
Content-Length: 927
200 OK
```


```json
{
  "id": 7,
  "quantity": 2,
  "price": "10.0",
  "variant_id": 16,
  "vendor_id": 33,
  "single_display_amount": "$10.00",
  "display_amount": "$20.00",
  "total": "20.0",
  "on_sale": false,
  "final_sale": false,
  "backordered": null,
  "promotionable": true,
  "variant": {
    "id": 16,
    "name": "Product #8 - 163",
    "sku": "SKU-15",
    "is_master": false,
    "slug": "product-8-163",
    "description": "As seen on TV!",
    "track_inventory": true,
    "cost_price": "17.0",
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
    "videos": [

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
  "vendor_name": "Vendor #33",
  "country_iso": "US",
  "domestic_override": false,
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
Authorizat IO N: Bearer d0c80a4e9e0b74f8b8833655f24a2df63943c6d9211561ae
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/minis`

#### Parameters


```json
mini[name]=Winny&mini[user_id]=70&mini[birth_year]=2019&mini[birth_month]=1&mini[birth_day]=1
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
ETag: W/&quot;f7d081bf9debdc3a443e8b4533275aad&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: cb3730aa-db19-4409-b896-a23b8da46442
X-Runtime: 0.011711
Vary: Origin
Content-Length: 162
201 Created
```


```json
{
  "id": 4,
  "user_id": 70,
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
Authorizat IO N: Bearer 88a3ec37a99e686c90178cbca0ee3105feae13a6725ac08a
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
X-Request-Id: b2ed4fec-9fe7-4996-88fe-52c1cb68bedc
X-Runtime: 0.006985
Vary: Origin
204 No Content
```




## Get a single mini


### Request

#### Endpoint

```plaintext
GET /api/minis/3
Accept: application/json
Authorizat IO N: Bearer c0d145b42d79d35034e16ccab5100f45c27e1dd6c50f7026
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
ETag: W/&quot;836424c116da840e71b9d16d14486ef4&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 500bd3dd-3e05-432d-bd49-251c58c6a89c
X-Runtime: 0.010788
Vary: Origin
Content-Length: 162
200 OK
```


```json
{
  "id": 3,
  "user_id": 69,
  "name": "Mini",
  "birth_year": 2021,
  "birth_month": 3,
  "birth_day": 30,
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
Authorizat IO N: Bearer f5b0b2e8228de342fba420b71ccfb93fed3cc08b95ec98ad
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
ETag: W/&quot;89f610354ad331ac6733e9951058b335&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: a0e80700-1741-495e-940e-e58358c856a2
X-Runtime: 0.040048
Vary: Origin
Content-Length: 1720
200 OK
```


```json
{
  "minis": [
    {
      "id": 19,
      "user_id": 82,
      "name": "Mini",
      "birth_year": 2021,
      "birth_month": 3,
      "birth_day": 30,
      "gender_boy": true,
      "gender_girl": true,
      "gender_taxons": [

      ],
      "age_range_taxons": [

      ]
    },
    {
      "id": 18,
      "user_id": 81,
      "name": "Mini",
      "birth_year": 2021,
      "birth_month": 3,
      "birth_day": 30,
      "gender_boy": true,
      "gender_girl": true,
      "gender_taxons": [

      ],
      "age_range_taxons": [

      ]
    },
    {
      "id": 17,
      "user_id": 80,
      "name": "Mini",
      "birth_year": 2021,
      "birth_month": 3,
      "birth_day": 30,
      "gender_boy": true,
      "gender_girl": true,
      "gender_taxons": [

      ],
      "age_range_taxons": [

      ]
    },
    {
      "id": 16,
      "user_id": 79,
      "name": "Mini",
      "birth_year": 2021,
      "birth_month": 3,
      "birth_day": 30,
      "gender_boy": true,
      "gender_girl": true,
      "gender_taxons": [

      ],
      "age_range_taxons": [

      ]
    },
    {
      "id": 15,
      "user_id": 78,
      "name": "Mini",
      "birth_year": 2021,
      "birth_month": 3,
      "birth_day": 30,
      "gender_boy": true,
      "gender_girl": true,
      "gender_taxons": [

      ],
      "age_range_taxons": [

      ]
    },
    {
      "id": 14,
      "user_id": 77,
      "name": "Mini",
      "birth_year": 2021,
      "birth_month": 3,
      "birth_day": 30,
      "gender_boy": true,
      "gender_girl": true,
      "gender_taxons": [

      ],
      "age_range_taxons": [

      ]
    },
    {
      "id": 13,
      "user_id": 76,
      "name": "Mini",
      "birth_year": 2021,
      "birth_month": 3,
      "birth_day": 30,
      "gender_boy": true,
      "gender_girl": true,
      "gender_taxons": [

      ],
      "age_range_taxons": [

      ]
    },
    {
      "id": 12,
      "user_id": 75,
      "name": "Mini",
      "birth_year": 2021,
      "birth_month": 3,
      "birth_day": 30,
      "gender_boy": true,
      "gender_girl": true,
      "gender_taxons": [

      ],
      "age_range_taxons": [

      ]
    },
    {
      "id": 11,
      "user_id": 74,
      "name": "Mini",
      "birth_year": 2021,
      "birth_month": 3,
      "birth_day": 30,
      "gender_boy": true,
      "gender_girl": true,
      "gender_taxons": [

      ],
      "age_range_taxons": [

      ]
    },
    {
      "id": 10,
      "user_id": 73,
      "name": "Mini",
      "birth_year": 2021,
      "birth_month": 3,
      "birth_day": 30,
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
Authorizat IO N: Bearer 489a166790d0b77edd4585477a0e745964526b94a48f52e8
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
ETag: W/&quot;abafff44741df3928617e1863cb4e676&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 605f49e0-50e7-492b-99ec-afe9eecda3c9
X-Runtime: 0.016708
Vary: Origin
Content-Length: 404
200 OK
```


```json
{
  "minis": [
    {
      "id": 9,
      "user_id": 72,
      "name": "Mini",
      "birth_year": 2021,
      "birth_month": 3,
      "birth_day": 30,
      "gender_boy": true,
      "gender_girl": true,
      "gender_taxons": [

      ],
      "age_range_taxons": [

      ]
    },
    {
      "id": 8,
      "user_id": 72,
      "name": "Mini",
      "birth_year": 2021,
      "birth_month": 3,
      "birth_day": 30,
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
PATCH /api/minis/1
Accept: application/json
Authorizat IO N: Bearer 537d605cdfdd9ed23b29bc0478a3a5e96ac52aa48261d23c
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
ETag: W/&quot;245e03230adaa160e2596c67a2998bc8&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 8cdb9e98-568a-4134-a34f-ceb602dce82f
X-Runtime: 0.033990
Vary: Origin
Content-Length: 163
200 OK
```


```json
{
  "id": 1,
  "user_id": 67,
  "name": "Marge",
  "birth_year": 2021,
  "birth_month": 3,
  "birth_day": 30,
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
Authorizat IO N: Bearer a60585828e6e30c955f1124b996877275f79eccc3c6b5c4f
X-Spree-Order-Token: 
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/cart`

#### Parameters


```json
user_id&order_token&line_item[variant_id]=96&line_item[quantity]=1&line_item[vendor_id]=198&line_item[gift_card_details_attributes][recipient_name]=Recipient+John&line_item[gift_card_details_attributes][recipient_email]=recipient%40email.com&line_item[gift_card_details_attributes][purchaser_name]=Purchaser+Bob&line_item[gift_card_details_attributes][gift_message]=Surprise&line_item[gift_card_details_attributes][send_email_at]=2021-03-31
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
ETag: W/&quot;8a1aea7341e463701cbfd988aa50e166&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 18e3f65e-8ae7-483d-80eb-7b78e979639b
X-Runtime: 0.187119
Vary: Origin
Content-Length: 2889
200 OK
```


```json
{
  "id": 22,
  "number": "M251992211",
  "item_total": "19.99",
  "total": "19.99",
  "ship_total": "0.0",
  "state": "cart",
  "adjustment_total": "0.0",
  "user_id": 61,
  "created_at": "2021-03-31T06:15:07.719-04:00",
  "updated_at": "2021-03-31T06:15:07.771-04:00",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "email59@example.com",
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
  "total_applicable_store_credit": 0,
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
  "token": "x3i-N3DpDiaDXvioDCEaRw",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order?order=M251992211&bzip=&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [

  ],
  "bill_address": null,
  "ship_address": null,
  "line_items": [
    {
      "id": 27,
      "quantity": 1,
      "price": "19.99",
      "variant_id": 96,
      "vendor_id": 198,
      "single_display_amount": "$19.99",
      "display_amount": "$19.99",
      "total": "19.99",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 96,
        "name": "Product #47 - 6253",
        "sku": "SKU-96",
        "is_master": false,
        "slug": "product-47-6253",
        "description": "As seen on TV!",
        "track_inventory": true,
        "cost_price": "17.0",
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
        "videos": [

        ],
        "product_id": 47,
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
          "send_email_at": "2021-03-31T00:00:00.000-04:00"
        }
      ],
      "vendor_name": "Vendor #198",
      "country_iso": null,
      "domestic_override": null,
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
user_id&order_token&line_item[variant_id]=76&line_item[quantity]=2&line_item[vendor_id]=157
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
ETag: W/&quot;f38e4c8862f1f89ec9b9c94352943ff5&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 6ba3d636-b3f8-40f8-99dd-bf300786796b
X-Runtime: 0.103446
Vary: Origin
Content-Length: 2675
200 OK
```


```json
{
  "id": 17,
  "number": "M090654150",
  "item_total": "39.98",
  "total": "39.98",
  "ship_total": "0.0",
  "state": "cart",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2021-03-31T06:15:05.036-04:00",
  "updated_at": "2021-03-31T06:15:05.076-04:00",
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
  "token": "1RzK5r1ztxcxNXeZSgQNKg",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order?order=M090654150&bzip=&init=true",
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
      "variant_id": 76,
      "vendor_id": 157,
      "single_display_amount": "$19.99",
      "display_amount": "$39.98",
      "total": "39.98",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 76,
        "name": "Product #38 - 4719",
        "sku": "SKU-75",
        "is_master": false,
        "slug": "product-38-4719",
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
        "videos": [

        ],
        "product_id": 38,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [

      ],
      "vendor_name": "Vendor #157",
      "country_iso": null,
      "domestic_override": null,
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
user_id&order_token&line_item[variant_id]=80&line_item[quantity]=2&line_item[vendor_id]=165
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
ETag: W/&quot;ea7df19f0cf27c3c20744beb25e53003&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 6b29fc5c-7155-4cee-b829-f8368bbc7775
X-Runtime: 0.117204
Vary: Origin
Content-Length: 2675
200 OK
```


```json
{
  "id": 18,
  "number": "M743296078",
  "item_total": "39.98",
  "total": "39.98",
  "ship_total": "0.0",
  "state": "cart",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2021-03-31T06:15:05.452-04:00",
  "updated_at": "2021-03-31T06:15:05.493-04:00",
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
  "token": "sW1H0yTwIZ-DoqL9uVio4w",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order?order=M743296078&bzip=&init=true",
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
      "variant_id": 80,
      "vendor_id": 165,
      "single_display_amount": "$19.99",
      "display_amount": "$39.98",
      "total": "39.98",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 80,
        "name": "Product #40 - 6542",
        "sku": "SKU-79",
        "is_master": false,
        "slug": "product-40-6542",
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
        "videos": [

        ],
        "product_id": 40,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [

      ],
      "vendor_name": "Vendor #165",
      "country_iso": null,
      "domestic_override": null,
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
Authorizat IO N: Bearer c78d2206aba5838a7915b53243a25c318cf7a45574b2e2a5
X-Spree-Order-Token: 
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/cart`

#### Parameters


```json
user_id&order_token&line_item[variant_id]=84&line_item[quantity]=2&line_item[vendor_id]=173&user_token=Bearer+c78d2206aba5838a7915b53243a25c318cf7a45574b2e2a5
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
ETag: W/&quot;abff8a4788194a77b816e8e1fb6e120f&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 9abe9b85-af8b-4a56-beb2-e4619682713e
X-Runtime: 0.113377
Vary: Origin
Content-Length: 2687
200 OK
```


```json
{
  "id": 19,
  "number": "M938157182",
  "item_total": "39.98",
  "total": "39.98",
  "ship_total": "0.0",
  "state": "cart",
  "adjustment_total": "0.0",
  "user_id": 59,
  "created_at": "2021-03-31T06:15:05.916-04:00",
  "updated_at": "2021-03-31T06:15:05.957-04:00",
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
  "token": "xk2OSgukG5V0cG_wWwthpQ",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order?order=M938157182&bzip=&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [

  ],
  "bill_address": null,
  "ship_address": null,
  "line_items": [
    {
      "id": 23,
      "quantity": 2,
      "price": "19.99",
      "variant_id": 84,
      "vendor_id": 173,
      "single_display_amount": "$19.99",
      "display_amount": "$39.98",
      "total": "39.98",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 84,
        "name": "Product #42 - 6436",
        "sku": "SKU-83",
        "is_master": false,
        "slug": "product-42-6436",
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
        "videos": [

        ],
        "product_id": 42,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [

      ],
      "vendor_name": "Vendor #173",
      "country_iso": null,
      "domestic_override": null,
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
X-Spree-Order-Token: EzAgFnTCvSaoC2utVTks0g
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/cart`

#### Parameters


```json
user_id&order_token=EzAgFnTCvSaoC2utVTks0g&line_item[variant_id]=92&line_item[quantity]=2&line_item[vendor_id]=189
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
ETag: W/&quot;fc569864a820552ef218903e2d78913e&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 23c4aaa4-157f-4234-8237-65e9db2df303
X-Runtime: 0.138137
Vary: Origin
Content-Length: 2674
200 OK
```


```json
{
  "id": 21,
  "number": "M045483872",
  "item_total": "39.98",
  "total": "39.98",
  "ship_total": "0.0",
  "state": "cart",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2021-03-31T06:15:07.142-04:00",
  "updated_at": "2021-03-31T06:15:07.196-04:00",
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
  "token": "MsoCc9OkWLFLYSf3AiFweQ",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order?order=M045483872&bzip=&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [

  ],
  "bill_address": null,
  "ship_address": null,
  "line_items": [
    {
      "id": 26,
      "quantity": 2,
      "price": "19.99",
      "variant_id": 92,
      "vendor_id": 189,
      "single_display_amount": "$19.99",
      "display_amount": "$39.98",
      "total": "39.98",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 92,
        "name": "Product #46 - 2758",
        "sku": "SKU-91",
        "is_master": false,
        "slug": "product-46-2758",
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
        "videos": [

        ],
        "product_id": 46,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [

      ],
      "vendor_name": "Vendor #189",
      "country_iso": null,
      "domestic_override": null,
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
Authorizat IO N: Bearer 7818f3ddd4513882871da8b7f049ab5ca1c50dc9dfb33c51
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
X-Request-Id: 2da578d5-9591-441a-8f0d-a3e92947f5b7
X-Runtime: 0.015872
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
GET /api/orders/M794876912
Accept: application/json
Authorizat IO N: Bearer 83ea96e0e3ddb0dca674d69a17283d94c06d67184cb725a4
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
ETag: W/&quot;d955decc17109122cfa0e1d173462ab4&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 370274a4-24f3-4f04-a5c5-3c8c5fff28ac
X-Runtime: 0.132128
Vary: Origin
Content-Length: 7951
200 OK
```


```json
{
  "id": 15,
  "number": "M794876912",
  "item_total": "20.0",
  "total": "118.0",
  "ship_total": "100.0",
  "state": "payment",
  "adjustment_total": "-2.0",
  "user_id": 56,
  "created_at": "2021-03-31T06:15:03.008-04:00",
  "updated_at": "2021-03-31T06:15:03.592-04:00",
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
  "token": "QMBFNPcVMWNJ1W58VueauQ",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order?order=M794876912&bzip=10031&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [

  ],
  "bill_address": {
    "id": 36,
    "firstname": "John",
    "lastname": "Smith",
    "full_name": "John Smith",
    "address1": "PO Box 1337",
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
  "ship_address": {
    "id": 37,
    "firstname": "John",
    "lastname": "Smith",
    "full_name": "John Smith",
    "address1": "A Different Road",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10032",
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
      "variant_id": 66,
      "vendor_id": 142,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "9.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 66,
        "name": "Product #33 - 8150",
        "sku": "SKU-65",
        "is_master": false,
        "slug": "product-33-8150",
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
        "videos": [

        ],
        "product_id": 33,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [

      ],
      "vendor_name": "Vendor #142",
      "country_iso": "US",
      "domestic_override": false,
      "adjustments": [
        {
          "id": 1,
          "source_type": "Spree::PromotionAction",
          "source_id": 2,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 17,
          "amount": "-1.0",
          "label": "Promotion (10% off)",
          "promotion_code_id": 2,
          "finalized": false,
          "eligible": true,
          "created_at": "2021-03-31T06:15:03.442-04:00",
          "updated_at": "2021-03-31T06:15:03.442-04:00",
          "display_amount": "-$1.00"
        }
      ]
    },
    {
      "id": 18,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 68,
      "vendor_id": 142,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "9.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 68,
        "name": "Product #34 - 3614",
        "sku": "SKU-67",
        "is_master": false,
        "slug": "product-34-3614",
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
        "videos": [

        ],
        "product_id": 34,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [

      ],
      "vendor_name": "Vendor #142",
      "country_iso": "US",
      "domestic_override": false,
      "adjustments": [
        {
          "id": 2,
          "source_type": "Spree::PromotionAction",
          "source_id": 2,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 18,
          "amount": "-1.0",
          "label": "Promotion (10% off)",
          "promotion_code_id": 2,
          "finalized": false,
          "eligible": true,
          "created_at": "2021-03-31T06:15:03.452-04:00",
          "updated_at": "2021-03-31T06:15:03.452-04:00",
          "display_amount": "-$1.00"
        }
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
      "number": "H17222010420",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M794876912",
      "stock_location_name": "NY Warehouse 26",
      "giftwrappable": false,
      "stock_location_id": 26,
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
          "extra_cost": "+$100.00"
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
        "extra_cost": "+$100.00",
        "base_flat_rate_amount": 0.0
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
              "id": 22,
              "name": "ShippingCategory #21"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 66,
          "quantity": 1,
          "states": {
            "on_hand": 1
          }
        },
        {
          "variant_id": 68,
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
          "adjustable_id": 18,
          "amount": "-10.0",
          "label": "Shipping",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2021-03-31T06:15:03.520-04:00",
          "updated_at": "2021-03-31T06:15:03.520-04:00",
          "display_amount": "-$10.00"
        },
        {
          "id": 3,
          "source_type": "Spree::PromotionAction",
          "source_id": 3,
          "adjustable_type": "Spree::Shipment",
          "adjustable_id": 18,
          "amount": "-9.99",
          "label": "Shipping",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2021-03-31T06:15:03.512-04:00",
          "updated_at": "2021-03-31T06:15:03.512-04:00",
          "display_amount": "-$9.99"
        }
      ],
      "stock_location_address": "NY Warehouse 26, Washington, AL",
      "country_iso": "US",
      "international_shipping": false,
      "delivery_estimation": "Apr 02",
      "estimated_giftwrap_price": "5.0",
      "display_estimated_giftwrap_price": "$5.00"
    }
  ],
  "adjustments": [
    {
      "id": 5,
      "source_type": "Spree::Promotion",
      "source_id": 3,
      "adjustable_type": "Spree::Order",
      "adjustable_id": 15,
      "amount": "20.0",
      "label": "adj1",
      "promotion_code_id": null,
      "finalized": false,
      "eligible": true,
      "created_at": "2021-03-31T06:15:03.525-04:00",
      "updated_at": "2021-03-31T06:15:03.525-04:00",
      "display_amount": "$20.00"
    },
    {
      "id": 6,
      "source_type": "Spree::Promotion",
      "source_id": 3,
      "adjustable_type": "Spree::Order",
      "adjustable_id": 15,
      "amount": "30.0",
      "label": "adj2",
      "promotion_code_id": null,
      "finalized": false,
      "eligible": true,
      "created_at": "2021-03-31T06:15:03.529-04:00",
      "updated_at": "2021-03-31T06:15:03.529-04:00",
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
GET /api/orders/M469908188
Accept: application/json
Authorizat IO N: a66f2e9111b0cb99171efaaff642d130fb23977ee1330b26
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
X-Request-Id: 276ade75-b7e4-4727-8a4a-119827fee25d
X-Runtime: 0.010474
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
user[email]=email6%40example.com
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
X-Request-Id: 46779bde-734b-463a-80d3-0c9245bf0aa4
X-Runtime: 0.002526
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
user[email]=email4%40example.com&user[password]=secret
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
Authorization: Bearer 812cea709731f943b0eccdfb160e918745a4e2d4b63584c1
ETag: W/&quot;61f6cf0e22f1a8940968e5f8b75a4c5e&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: d5c8e9fd-9c52-4392-9008-41c12a8af0fa
X-Runtime: 0.015513
Vary: Origin
Content-Length: 559
200 OK
```


```json
{
  "id": 4,
  "email": "email4@example.com",
  "persistence_token": null,
  "perishable_token": null,
  "last_request_at": null,
  "login": "email4@example.com",
  "ship_address_id": null,
  "bill_address_id": null,
  "created_at": "2021-03-31T06:14:51.755-04:00",
  "updated_at": "2021-03-31T06:14:51.757-04:00",
  "spree_api_key": "812cea709731f943b0eccdfb160e918745a4e2d4b63584c1",
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
X-Request-Id: 308baa4f-eabc-4af3-a94f-ab3fbb98e289
X-Runtime: 0.017144
Vary: Origin
204 No Content
```




# Products

Get products info

## Fetch a single product by id


### Request

#### Endpoint

```plaintext
GET /api/products/product-59-5226
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
Date: Wed, 31 Mar 2021 10:15:09 GMT
Surrogate-Control: max-age=900
Surrogate-Key: product_id=1
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;215902d0537875b18775a376aedd2c4a&quot;
X-Request-Id: 46f86fd4-47ed-4d7d-b9ed-770a9bf86bfd
X-Runtime: 0.055860
Vary: Origin
Content-Length: 1598
200 OK
```


```json
{
  "id": 59,
  "name": "Product #59 - 5226",
  "description": "As seen on TV!",
  "available_on": "2020-03-31T06:15:09.691-04:00",
  "slug": "product-59-5226",
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
  "concierge_only": false,
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
      "created_at": "2021-03-31T06:15:09.639-04:00",
      "url": "/category/clothing",
      "position": 1
    },
    {
      "id": 15,
      "name": "Girl",
      "taxonomy_id": 6,
      "created_at": "2021-03-31T06:15:09.657-04:00",
      "url": "/category/clothing/girl",
      "position": 2
    },
    {
      "id": 16,
      "name": "Dresses",
      "taxonomy_id": 6,
      "created_at": "2021-03-31T06:15:09.674-04:00",
      "url": "/category/clothing/girl/dresses",
      "position": 3
    }
  ],
  "has_variants": false,
  "master": {
    "id": 107,
    "name": "Product #59 - 5226",
    "sku": "SKU-107",
    "is_master": true,
    "slug": "product-59-5226",
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

    ],
    "videos": [

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
Date: Wed, 31 Mar 2021 10:15:08 GMT
Surrogate-Control: max-age=900
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;a03eabad24931988a0578f358d557d63&quot;
X-Request-Id: 000e76e8-2131-491e-8f90-aebb974d9c9c
X-Runtime: 0.068062
Vary: Origin
Content-Length: 1276
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
      "name": "Product #49 - 9672",
      "description": "As seen on TV!",
      "available_on": "2020-03-31T06:15:08.129-04:00",
      "slug": "product-49-9672",
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
      "brand_description": "Maison You",
      "gift_card": false,
      "concierge_only": false,
      "is_registry": false,
      "discontinued": false,
      "available": true,
      "trends": [

      ],
      "breadcrumb_taxons": [

      ],
      "has_variants": false,
      "master": {
        "id": 97,
        "name": "Product #49 - 9672",
        "sku": "SKU-97",
        "is_master": true,
        "slug": "product-49-9672",
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

        ],
        "videos": [

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
Date: Wed, 31 Mar 2021 10:15:08 GMT
Surrogate-Control: max-age=900
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;55ecf3d7b366af4f854ca59dd600c531&quot;
X-Request-Id: 546aa91c-d6fe-4ab2-be64-19db7b8aabd2
X-Runtime: 0.055807
Vary: Origin
Content-Length: 405
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
      "id": 54,
      "name": "Product #54 - 654",
      "slug": "product-54-654",
      "master_id": 102,
      "display_price": "$0.00",
      "brand": "Maison You",
      "brand_slug": "maison-you",
      "brand_url": "/brand/maison-you",
      "brand_description": "Maison You",
      "gift_card": false,
      "concierge_only": false,
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
GET /api/products?ids=51%2C52%2C53
Host: example.org
Cookie: 
```

`GET /api/products`

#### Parameters


```json
ids: 51,52,53
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
Date: Wed, 31 Mar 2021 10:15:08 GMT
Surrogate-Control: max-age=900
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;f70c3bfcb2e9881d5cf6a332c5cb005f&quot;
X-Request-Id: 7c6c447e-335f-4d8a-96c2-a9e85e3f8002
X-Runtime: 0.105549
Vary: Origin
Content-Length: 2806
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
      "id": 51,
      "name": "Product #51 - 8851",
      "description": "As seen on TV!",
      "available_on": "2020-03-31T06:15:08.483-04:00",
      "slug": "product-51-8851",
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
      "concierge_only": false,
      "is_registry": false,
      "discontinued": false,
      "available": true,
      "trends": [

      ],
      "breadcrumb_taxons": [

      ],
      "has_variants": false,
      "master": {
        "id": 99,
        "name": "Product #51 - 8851",
        "sku": "SKU-99",
        "is_master": true,
        "slug": "product-51-8851",
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

        ],
        "videos": [

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
      "id": 52,
      "name": "Product #52 - 8081",
      "description": "As seen on TV!",
      "available_on": "2020-03-31T06:15:08.554-04:00",
      "slug": "product-52-8081",
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
      "concierge_only": false,
      "is_registry": false,
      "discontinued": false,
      "available": true,
      "trends": [

      ],
      "breadcrumb_taxons": [

      ],
      "has_variants": false,
      "master": {
        "id": 100,
        "name": "Product #52 - 8081",
        "sku": "SKU-100",
        "is_master": true,
        "slug": "product-52-8081",
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

        ],
        "videos": [

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
      "name": "Product #53 - 2430",
      "description": "As seen on TV!",
      "available_on": "2020-03-31T06:15:08.625-04:00",
      "slug": "product-53-2430",
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
      "concierge_only": false,
      "is_registry": false,
      "discontinued": false,
      "available": true,
      "trends": [

      ],
      "breadcrumb_taxons": [

      ],
      "has_variants": false,
      "master": {
        "id": 101,
        "name": "Product #53 - 2430",
        "sku": "SKU-101",
        "is_master": true,
        "slug": "product-53-2430",
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

        ],
        "videos": [

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
GET /api/taxons/products?id=9
Host: example.org
Cookie: 
```

`GET /api/taxons/products`

#### Parameters


```json
id: 9
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
ETag: W/&quot;5a3db340d8f9c7f173c89cb59c67237a&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 01334649-43dc-4950-98bf-e880e36e93c5
X-Runtime: 0.060780
Vary: Origin
Content-Length: 1302
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
      "id": 56,
      "name": "Product #56 - 150",
      "description": "As seen on TV!",
      "available_on": "2020-03-31T06:15:09.176-04:00",
      "slug": "product-56-150",
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
      "brand_description": "Ruby on Rails - 1",
      "gift_card": false,
      "concierge_only": false,
      "is_registry": false,
      "discontinued": false,
      "available": true,
      "trends": [

      ],
      "breadcrumb_taxons": [

      ],
      "has_variants": false,
      "master": {
        "id": 104,
        "name": "Product #56 - 150",
        "sku": "SKU-104",
        "is_master": true,
        "slug": "product-56-150",
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

        ],
        "videos": [

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
ETag: W/&quot;29584109daaea39bdaf6831a3c263561&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 29fd175e-e29d-41a4-983d-605cc7ff534b
X-Runtime: 0.049248
Vary: Origin
Content-Length: 1305
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
      "id": 58,
      "name": "Product #58 - 768",
      "description": "As seen on TV!",
      "available_on": "2020-03-31T06:15:09.478-04:00",
      "slug": "product-58-768",
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
      "brand_description": "Ruby on Rails - 2",
      "gift_card": false,
      "concierge_only": false,
      "is_registry": false,
      "discontinued": false,
      "available": true,
      "trends": [

      ],
      "breadcrumb_taxons": [

      ],
      "has_variants": false,
      "master": {
        "id": 106,
        "name": "Product #58 - 768",
        "sku": "SKU-106",
        "is_master": true,
        "slug": "product-58-768",
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

        ],
        "videos": [

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



## Get all products info


### Request

#### Endpoint

```plaintext
GET /api/sitemap/products
Accept: application/json
Authorizat IO N: Bearer e6235c4fc3be55c7f9439ba021b7296a1c4f0d97c4712f5e
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
X-Request-Id: f320a795-8200-4d45-bc2d-db6bd600e5cd
X-Runtime: 0.025226
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
X-Request-Id: bff8d332-469f-421d-a258-47a491061167
X-Runtime: 0.011950
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
GET /api/recently_viewed?recently_viewed[session_id]=x4q26skaiu9egv85qcp76sc810tbeofz5wj92sa25v8ywojhtai5dhazm5un9vq2jqenvk0gt7cs31dpyt69x4vbahmamoa6d3nhtw4wtjxtnyiokgzyi2jashvs6vcfpwsfbalr0511e8d0bmriz4fyn9fqdbblyhp0cj8xle11k731tmjffntc04o1jvkv18lkymbvmf5n07g8wiqahp1cei7xyobn4djwnrmtpgk0stsuaaif3rfkptm6ik8
Accept: application/json
Authorizat IO N: Bearer bf4000be727fcc8cd420d8c60fa72ecde19572038f630351
Host: example.org
Cookie: 
```

`GET /api/recently_viewed`

#### Parameters


```json
recently_viewed: {&quot;session_id&quot;=&gt;&quot;x4q26skaiu9egv85qcp76sc810tbeofz5wj92sa25v8ywojhtai5dhazm5un9vq2jqenvk0gt7cs31dpyt69x4vbahmamoa6d3nhtw4wtjxtnyiokgzyi2jashvs6vcfpwsfbalr0511e8d0bmriz4fyn9fqdbblyhp0cj8xle11k731tmjffntc04o1jvkv18lkymbvmf5n07g8wiqahp1cei7xyobn4djwnrmtpgk0stsuaaif3rfkptm6ik8&quot;}
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
ETag: W/&quot;80cf1583569f25bf88258d6579ed1cc0&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 526a083b-00ba-45a5-992f-133f95ed1260
X-Runtime: 0.021865
Vary: Origin
Content-Length: 119
200 OK
```


```json
[
  {
    "at": "2021-03-31T06:15:07.903-04:00",
    "variant_id": "var1"
  },
  {
    "at": "2021-03-31T06:20:07.903-04:00",
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
Authorizat IO N: Bearer ef844942ea86eeb33c4c7fc060776b849c9ba0ece7f5eec6
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/recently_viewed`

#### Parameters


```json
recently_viewed[session_id]=79e0jon4txoplizx6f7d4nsh0i6tyh52lqg1jw22eisbim2bpf6sz5pelscm6t2uxa2o87ssi6428mgl1ghjhzaf4alf407st2w6hzu2lp4l80odxs8uw8bv818fl6ybxmh5vvd6dhauzvoviyjot7rulcd7sh2gzs285tn0khoj7f0m1gztp5nbo9umr8odcimf6p1i15ti3jxizjmbuttq0yxt1hafxp2wkvkkfotje81tlkq6b26uzgndrok&recently_viewed[variant_id]=foo
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
X-Request-Id: 1a996139-d48e-41d8-a401-be6cf37c42c2
X-Runtime: 0.004970
Vary: Origin
204 No Content
```




# Return Authorizations

Get user return authorizations

## Can get another user&#39;s return authorization


### Request

#### Endpoint

```plaintext
GET /api/returns/RA112760538
Authorizat IO N: Bearer 380f3577cdef24bec59f1a067820b7c6e2c2b9bd1f4c33b0
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
ETag: W/&quot;ab74a2cc4bf46992d1493f11ddb3a234&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: f8af3fd1-818c-4a95-9cf7-58fae111c951
X-Runtime: 0.042829
Vary: Origin
Content-Length: 3115
200 OK
```


```json
{
  "id": 3,
  "number": "RA112760538",
  "state": "authorized",
  "order_id": 11,
  "memo": "Items were broken",
  "created_at": "2021-03-31T06:14:56.906-04:00",
  "updated_at": "2021-03-31T06:14:56.906-04:00",
  "amount": "10.0",
  "reason": {
    "id": 5,
    "name": "Defect #5",
    "active": true,
    "mutable": true,
    "created_at": "2021-03-31T06:14:56.902-04:00",
    "updated_at": "2021-03-31T06:14:56.902-04:00",
    "mirakl_code": null
  },
  "order": {
    "id": 11,
    "number": "M996484220",
    "item_total": "10.0",
    "total": "110.0",
    "state": "complete",
    "adjustment_total": "0.0",
    "user_id": 32,
    "completed_at": "2021-03-31T06:14:56.818-04:00",
    "bill_address_id": 27,
    "ship_address_id": 28,
    "payment_total": "110.0",
    "shipment_state": "shipped",
    "payment_state": "paid",
    "email": "email30@example.com",
    "special_instructions": null,
    "created_at": "2021-03-31T06:14:56.738-04:00",
    "updated_at": "2021-03-31T06:14:56.938-04:00",
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
    "guest_token": "baHdvJ00cz12Ea2wRM3Xgg",
    "canceled_at": null,
    "canceler_id": null,
    "store_id": 11,
    "approver_name": null,
    "frontend_viewable": true,
    "migrated": false,
    "is_gift": false,
    "gift_email": null,
    "gift_message": null,
    "gift_card_total": "0.0",
    "gift_confirmation_delivered_at": null,
    "use_store_credits": false,
    "first_order": false,
    "maisonette_customer_id": "71c67006-82b7-48c2-a346-9949267d89b7"
  },
  "ship_address": {
    "id": 28,
    "firstname": "John",
    "lastname": "Smith",
    "full_name": "John Smith",
    "address1": "A Different Road",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10024",
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
  "bill_address": {
    "id": 27,
    "firstname": "John",
    "lastname": "Smith",
    "full_name": "John Smith",
    "address1": "PO Box 1337",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10023",
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
  "return_items": [
    {
      "name": "Product #15 - 6790",
      "brand": null,
      "brand_slug": null,
      "image": null,
      "product_slug": "product-15-6790",
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
        "id": 10,
        "name": "Credit Card"
      },
      "source": {
        "id": 3,
        "month": "12",
        "year": "2022",
        "cc_type": null,
        "last_digits": "1111",
        "name": "Spree Commerce",
        "gateway_customer_profile_id": "BGS-241403",
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
Authorizat IO N: Bearer 1851bcf10ff3017bf0e1c7920f591b3842a32abfba936c84
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
ETag: W/&quot;10ae1635283330fb857de482f59a006c&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: ca0b2930-5b00-49fa-a22e-8e4518a1e423
X-Runtime: 0.013608
Vary: Origin
Content-Length: 169
200 OK
```


```json
{
  "return_authorizations": [
    {
      "number": "RA807044645",
      "created_at": "2021-03-31T06:14:55.918-04:00",
      "return_amount": "10.0",
      "order_number": "M815928517",
      "state": "authorized"
    }
  ]
}
```



## returns a 200


### Request

#### Endpoint

```plaintext
GET /api/returns/RA020872823
Authorizat IO N: Bearer edd5530a29668de09f4ad4d61c7983c8f112925f2eaaa01f
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
ETag: W/&quot;982cc02e87f61e6da9fe3d9b30868880&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 48505e44-c724-4b48-95e7-bbe73c65d09b
X-Runtime: 0.052135
Vary: Origin
Content-Length: 3037
200 OK
```


```json
{
  "id": 2,
  "number": "RA020872823",
  "state": "authorized",
  "order_id": 10,
  "memo": "Items were broken",
  "created_at": "2021-03-31T06:14:56.404-04:00",
  "updated_at": "2021-03-31T06:14:56.404-04:00",
  "amount": "10.0",
  "reason": {
    "id": 3,
    "name": "Defect #3",
    "active": true,
    "mutable": true,
    "created_at": "2021-03-31T06:14:56.401-04:00",
    "updated_at": "2021-03-31T06:14:56.401-04:00",
    "mirakl_code": null
  },
  "order": {
    "id": 10,
    "number": "M115541951",
    "item_total": "10.0",
    "total": "110.0",
    "state": "complete",
    "adjustment_total": "0.0",
    "user_id": 31,
    "completed_at": "2021-03-31T06:14:56.318-04:00",
    "bill_address_id": 25,
    "ship_address_id": 26,
    "payment_total": "110.0",
    "shipment_state": "shipped",
    "payment_state": "paid",
    "email": "email29@example.com",
    "special_instructions": null,
    "created_at": "2021-03-31T06:14:56.239-04:00",
    "updated_at": "2021-03-31T06:14:56.434-04:00",
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
    "guest_token": "jujJjQYmpjtnOWTw9tvTdA",
    "canceled_at": null,
    "canceler_id": null,
    "store_id": 10,
    "approver_name": null,
    "frontend_viewable": true,
    "migrated": false,
    "is_gift": false,
    "gift_email": null,
    "gift_message": null,
    "gift_card_total": "0.0",
    "gift_confirmation_delivered_at": null,
    "use_store_credits": false,
    "first_order": false,
    "maisonette_customer_id": "f9d570fa-ff9e-446e-b793-5c008e96cf1c"
  },
  "ship_address": {
    "id": 26,
    "firstname": "John",
    "lastname": "Smith",
    "full_name": "John Smith",
    "address1": "A Different Road",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10022",
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
    "id": 25,
    "firstname": "John",
    "lastname": "Smith",
    "full_name": "John Smith",
    "address1": "PO Box 1337",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10021",
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
      "name": "Product #14 - 5406",
      "brand": null,
      "brand_slug": null,
      "image": null,
      "product_slug": "product-14-5406",
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
        "id": 8,
        "name": "Credit Card"
      },
      "source": {
        "id": 2,
        "month": "12",
        "year": "2022",
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
GET /api/returns/RA877643765
Authorizat IO N: Bearer 0798610d14c67cf1f880b9c79281a63735747a2cc622ba59
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
X-Request-Id: 8b74a5be-0bd8-4933-a139-f3147a81a89c
X-Runtime: 0.010022
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
stock_request[email]=mao.emmerich%40dickenslegros.co.uk&stock_request[variant_id]=111
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
X-Request-Id: 1f1ae87a-a758-491b-b89a-364637ef2139
X-Runtime: 0.005296
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
stock_request[email]=foo&stock_request[variant_id]=113
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
X-Request-Id: 1c7efebc-aead-476e-a8d3-7f4d660ff4e8
X-Runtime: 0.005684
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
stock_request[email]=malik%40eberthayes.name&stock_request[variant_id]=109
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
X-Request-Id: 3e2f116b-2b5d-4d87-8075-f091dcd1c7c9
X-Runtime: 0.022388
Vary: Origin
Content-Length: 80
422 Unprocessable Entity
```


```json
{
  "success": false,
  "message": "Email is already on the waitlist for this product."
}
```



# Store Credits API

Get user store_credits and current account balance for the current user

## returns a 200


### Request

#### Endpoint

```plaintext
GET api/store_credits/mine
Authorizat IO N: Bearer 43a05ff66761cf88453e555255c8f1d79aeec62bb4bdb4c2
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
ETag: W/&quot;6a04d24054f30dc86d8dd8c33386ff79&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: dca1cc8d-01e8-4c27-b2d7-539c72a3ee0a
X-Runtime: 0.027659
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
      "created_at": "2021-03-31T06:14:55.358-04:00"
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

Get all subscribers, only accessible to admin users

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
subscriber[email]=riva%40carroll.ca&subscriber[first_name]=Eveline&subscriber[last_name]=Bauch&subscriber[source]=Numquam+consequatur+tempora+quod+eveniet+enim+pariatur+quibusdam+sunt.&subscriber[list_id]=pnmjhp
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
ETag: W/&quot;f7835f3babbd93fc93b06c63f5960ced&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 46404f9a-5874-44b9-800e-b519df54a163
X-Runtime: 0.009203
Vary: Origin
Content-Length: 273
201 Created
```


```json
{
  "id": 6,
  "user_id": null,
  "list_id": "pnmjhp",
  "email": "riva@carroll.ca",
  "first_name": "Eveline",
  "last_name": "Bauch",
  "source": "Numquam consequatur tempora quod eveniet enim pariatur quibusdam sunt.",
  "phone": null,
  "status": "subscribed",
  "created_at": "2021-03-31T06:14:55.229-04:00"
}
```



## Create a subscriber for the associated user


### Request

#### Endpoint

```plaintext
POST /api/subscribers
Accept: application/json
Authorizat IO N: Bearer 8f57e6b6afce0eff238bc8f20a4c1fd125f38ddc9f5d2385
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/subscribers`

#### Parameters


```json
subscriber[email]&subscriber[first_name]=Tomiko&subscriber[last_name]=Kunze&subscriber[source]=Quos+distinctio+cupiditate+eos+et+ab.&subscriber[list_id]=0zs0pt
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
ETag: W/&quot;8507fa3b107ce8eac0ef1a71462bde63&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: d2d74d5d-62cd-4098-a095-b7aa3bd88c7f
X-Runtime: 0.009143
Vary: Origin
Content-Length: 241
201 Created
```


```json
{
  "id": 7,
  "user_id": 24,
  "list_id": "0zs0pt",
  "email": "email22@example.com",
  "first_name": "Tomiko",
  "last_name": "Kunze",
  "source": "Quos distinctio cupiditate eos et ab.",
  "phone": null,
  "status": "subscribed",
  "created_at": "2021-03-31T06:14:55.249-04:00"
}
```



## Get all subscribers


### Request

#### Endpoint

```plaintext
GET /api/subscribers
Accept: application/json
Authorizat IO N: Bearer fc6adb3244a962614c549ee82de65e5c3bbe7d6f4a5d9a09
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
ETag: W/&quot;7eda66b8853183ac9e989023e3a36a48&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: d59e0e61-b6ba-44a6-aac9-fe74392d1317
X-Runtime: 0.030032
Vary: Origin
Content-Length: 737
200 OK
```


```json
{
  "subscribers": [
    {
      "id": 3,
      "user_id": null,
      "list_id": "th9xzd",
      "email": "luanna@gulgowski.com",
      "first_name": "Noe",
      "last_name": "Kuphal",
      "source": "Registration",
      "phone": null,
      "status": "subscribed",
      "created_at": "2021-03-31T06:14:55.163-04:00"
    },
    {
      "id": 4,
      "user_id": null,
      "list_id": "lwnn72",
      "email": "isela@wuckert.info",
      "first_name": "Lexie",
      "last_name": "Graham",
      "source": "Registration",
      "phone": null,
      "status": "subscribed",
      "created_at": "2021-03-31T06:14:55.167-04:00"
    },
    {
      "id": 5,
      "user_id": null,
      "list_id": "dtjv6s",
      "email": "dee@hyatt.co.uk",
      "first_name": "Mirna",
      "last_name": "Gorczany",
      "source": "Registration",
      "phone": null,
      "status": "subscribed",
      "created_at": "2021-03-31T06:14:55.170-04:00"
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
PATCH /api/subscribers/9
Accept: application/json
Authorizat IO N: Bearer 441f753ff1ceecbaa3339eca2bbe79a589a5318585165787
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/subscribers/:id`

#### Parameters


```json
subscriber[source]=Animi+sed+voluptas+facere+fugit+deleniti+incidunt.
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
ETag: W/&quot;8f794d3b4ef15c425c14b9196aa285ac&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: b4459ff3-5fe6-43e0-9193-ee7392aa6d24
X-Runtime: 0.009913
Vary: Origin
Content-Length: 267
200 OK
```


```json
{
  "id": 9,
  "user_id": 27,
  "list_id": "sfgvfe",
  "email": "email25@example.com",
  "first_name": "Latina",
  "last_name": "Goodwin",
  "source": "Animi sed voluptas facere fugit deleniti incidunt.",
  "phone": null,
  "status": "subscribed_and_synced",
  "created_at": "2021-03-31T06:14:55.299-04:00"
}
```



## unsubscribe a known subscriber


### Request

#### Endpoint

```plaintext
DELETE /api/subscribers
Accept: application/json
Authorizat IO N: Bearer a73fa881a55aa55ae04e929fa79ec17f2ecb22fd49070e8c
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`DELETE /api/subscribers`

#### Parameters


```json
subscriber[email]=email23%40example.com&subscriber[list_id]=apwhgz
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
X-Request-Id: bf8f77f2-fe54-49a7-97a1-01a6fd29a503
X-Runtime: 0.008079
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
Authorizat IO N: Bearer 00a9c7be7a6d8a06bb467db52c8da2f5a56ac6325b8f7ea6
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`DELETE /api/subscribers`

#### Parameters


```json
subscriber[email]=zelda.borer%40hayesjones.co.uk&subscriber[list_id]=9aqsk0
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
X-Request-Id: 63486757-1f96-4627-86e6-180ac6639dc3
X-Runtime: 0.004462
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
Authorizat IO N: Bearer 96e9338ef83c3f9b2be581156bb9fe165ae6dcdee1636a63
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
X-Request-Id: 5300ead3-5a6a-43a1-9495-51bfafc67200
X-Runtime: 0.026448
Vary: Origin
Content-Length: 2
200 OK
```


```json
[

]
```



# Taxons API

Return brand taxons that have products in stock with the provided category taxon

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
ETag: W/&quot;59dc875423b229c0ae6a4ff6053ed8b3&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 37e969ad-8c35-4d45-962f-b04bb736b981
X-Runtime: 0.036071
Vary: Origin
Content-Length: 4443
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
      "id": 21,
      "name": "Category",
      "pretty_name": "Category",
      "permalink": "category",
      "parent_id": null,
      "taxonomy_id": 9,
      "url_override": null,
      "description": "Category",
      "icon": "/assets/default_taxon.png",
      "taxons": [
        {
          "id": 22,
          "name": "Kids",
          "pretty_name": "Category -> Kids",
          "permalink": "category/kids",
          "parent_id": 21,
          "taxonomy_id": 9,
          "url_override": null
        }
      ]
    },
    {
      "id": 22,
      "name": "Kids",
      "pretty_name": "Category -> Kids",
      "permalink": "category/kids",
      "parent_id": 21,
      "taxonomy_id": 9,
      "url_override": null,
      "description": "Kids",
      "icon": "/assets/default_taxon.png",
      "taxons": [
        {
          "id": 23,
          "name": "Boys",
          "pretty_name": "Category -> Kids -> Boys",
          "permalink": "category/kids/boys",
          "parent_id": 22,
          "taxonomy_id": 9,
          "url_override": null
        },
        {
          "id": 26,
          "name": "Girls",
          "pretty_name": "Category -> Kids -> Girls",
          "permalink": "category/kids/girls",
          "parent_id": 22,
          "taxonomy_id": 9,
          "url_override": null
        }
      ]
    },
    {
      "id": 23,
      "name": "Boys",
      "pretty_name": "Category -> Kids -> Boys",
      "permalink": "category/kids/boys",
      "parent_id": 22,
      "taxonomy_id": 9,
      "url_override": null,
      "description": "Boys",
      "icon": "/assets/default_taxon.png",
      "taxons": [
        {
          "id": 24,
          "name": "Boys Tops",
          "pretty_name": "Category -> Kids -> Boys -> Boys Tops",
          "permalink": "category/kids/boys/boys-tops",
          "parent_id": 23,
          "taxonomy_id": 9,
          "url_override": null
        }
      ]
    },
    {
      "id": 24,
      "name": "Boys Tops",
      "pretty_name": "Category -> Kids -> Boys -> Boys Tops",
      "permalink": "category/kids/boys/boys-tops",
      "parent_id": 23,
      "taxonomy_id": 9,
      "url_override": null,
      "description": "Boys Tops",
      "icon": "/assets/default_taxon.png",
      "taxons": [
        {
          "id": 25,
          "name": "Boys Shirts",
          "pretty_name": "Category -> Kids -> Boys -> Boys Tops -> Boys Shirts",
          "permalink": "category/kids/boys/boys-tops/boys-shirts",
          "parent_id": 24,
          "taxonomy_id": 9,
          "url_override": null
        }
      ]
    },
    {
      "id": 25,
      "name": "Boys Shirts",
      "pretty_name": "Category -> Kids -> Boys -> Boys Tops -> Boys Shirts",
      "permalink": "category/kids/boys/boys-tops/boys-shirts",
      "parent_id": 24,
      "taxonomy_id": 9,
      "url_override": null,
      "description": "Boys Shirts",
      "icon": "/assets/default_taxon.png",
      "taxons": [

      ]
    },
    {
      "id": 26,
      "name": "Girls",
      "pretty_name": "Category -> Kids -> Girls",
      "permalink": "category/kids/girls",
      "parent_id": 22,
      "taxonomy_id": 9,
      "url_override": null,
      "description": "Girls",
      "icon": "/assets/default_taxon.png",
      "taxons": [
        {
          "id": 27,
          "name": "Girls Tops",
          "pretty_name": "Category -> Kids -> Girls -> Girls Tops",
          "permalink": "category/kids/girls/girls-tops",
          "parent_id": 26,
          "taxonomy_id": 9,
          "url_override": null
        }
      ]
    },
    {
      "id": 27,
      "name": "Girls Tops",
      "pretty_name": "Category -> Kids -> Girls -> Girls Tops",
      "permalink": "category/kids/girls/girls-tops",
      "parent_id": 26,
      "taxonomy_id": 9,
      "url_override": null,
      "description": "Girls Tops",
      "icon": "/assets/default_taxon.png",
      "taxons": [
        {
          "id": 28,
          "name": "Girls Shirts",
          "pretty_name": "Category -> Kids -> Girls -> Girls Tops -> Girls Shirts",
          "permalink": "category/kids/girls/girls-tops/girls-shirts",
          "parent_id": 27,
          "taxonomy_id": 9,
          "url_override": null
        }
      ]
    },
    {
      "id": 28,
      "name": "Girls Shirts",
      "pretty_name": "Category -> Kids -> Girls -> Girls Tops -> Girls Shirts",
      "permalink": "category/kids/girls/girls-tops/girls-shirts",
      "parent_id": 27,
      "taxonomy_id": 9,
      "url_override": null,
      "description": "Girls Shirts",
      "icon": "/assets/default_taxon.png",
      "taxons": [

      ]
    },
    {
      "id": 29,
      "name": "Brand",
      "pretty_name": "Brand",
      "permalink": "brand",
      "parent_id": null,
      "taxonomy_id": 10,
      "url_override": null,
      "description": "Brand",
      "icon": "/assets/default_taxon.png",
      "taxons": [
        {
          "id": 30,
          "name": "Ruby on Rails - 3",
          "pretty_name": "Brand -> Ruby on Rails - 3",
          "permalink": "brand/ruby-on-rails-3",
          "parent_id": 29,
          "taxonomy_id": 10,
          "url_override": null
        },
        {
          "id": 31,
          "name": "Ruby on Rails - 4",
          "pretty_name": "Brand -> Ruby on Rails - 4",
          "permalink": "brand/ruby-on-rails-4",
          "parent_id": 29,
          "taxonomy_id": 10,
          "url_override": null
        }
      ]
    },
    {
      "id": 30,
      "name": "Ruby on Rails - 3",
      "pretty_name": "Brand -> Ruby on Rails - 3",
      "permalink": "brand/ruby-on-rails-3",
      "parent_id": 29,
      "taxonomy_id": 10,
      "url_override": null,
      "description": "Ruby on Rails - 3",
      "icon": "/assets/default_taxon.png",
      "taxons": [

      ]
    },
    {
      "id": 31,
      "name": "Ruby on Rails - 4",
      "pretty_name": "Brand -> Ruby on Rails - 4",
      "permalink": "brand/ruby-on-rails-4",
      "parent_id": 29,
      "taxonomy_id": 10,
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
ETag: W/&quot;26cf2d79920aeebfc6a70eab9cdf2a5d&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 7e6b88c8-e454-4877-b2dc-03920ad28803
X-Runtime: 0.012908
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
      "id": 40,
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
      "id": 41,
      "name": "Ruby on Rails - 5",
      "pretty_name": "Brand -> Ruby on Rails - 5",
      "permalink": "brand/ruby-on-rails-5",
      "parent_id": 40,
      "taxonomy_id": 12,
      "url_override": null,
      "description": "Ruby on Rails - 5",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 42,
      "name": "Ruby on Rails - 6",
      "pretty_name": "Brand -> Ruby on Rails - 6",
      "permalink": "brand/ruby-on-rails-6",
      "parent_id": 40,
      "taxonomy_id": 12,
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
ETag: W/&quot;ec8eef17afdfb2e98a5a66b0840c413b&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 999c3f54-29e9-49ea-9d73-5ba5fb0f0e59
X-Runtime: 0.027741
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
      "id": 43,
      "name": "Category",
      "pretty_name": "Category",
      "permalink": "category",
      "parent_id": null,
      "taxonomy_id": 13,
      "url_override": null,
      "description": "Category",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 44,
      "name": "Kids",
      "pretty_name": "Category -> Kids",
      "permalink": "category/kids",
      "parent_id": 43,
      "taxonomy_id": 13,
      "url_override": null,
      "description": "Kids",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 45,
      "name": "Boys",
      "pretty_name": "Category -> Kids -> Boys",
      "permalink": "category/kids/boys",
      "parent_id": 44,
      "taxonomy_id": 13,
      "url_override": null,
      "description": "Boys",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 46,
      "name": "Boys Tops",
      "pretty_name": "Category -> Kids -> Boys -> Boys Tops",
      "permalink": "category/kids/boys/boys-tops",
      "parent_id": 45,
      "taxonomy_id": 13,
      "url_override": null,
      "description": "Boys Tops",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 47,
      "name": "Boys Shirts",
      "pretty_name": "Category -> Kids -> Boys -> Boys Tops -> Boys Shirts",
      "permalink": "category/kids/boys/boys-tops/boys-shirts",
      "parent_id": 46,
      "taxonomy_id": 13,
      "url_override": null,
      "description": "Boys Shirts",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 48,
      "name": "Girls",
      "pretty_name": "Category -> Kids -> Girls",
      "permalink": "category/kids/girls",
      "parent_id": 44,
      "taxonomy_id": 13,
      "url_override": null,
      "description": "Girls",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 49,
      "name": "Girls Tops",
      "pretty_name": "Category -> Kids -> Girls -> Girls Tops",
      "permalink": "category/kids/girls/girls-tops",
      "parent_id": 48,
      "taxonomy_id": 13,
      "url_override": null,
      "description": "Girls Tops",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 50,
      "name": "Girls Shirts",
      "pretty_name": "Category -> Kids -> Girls -> Girls Tops -> Girls Shirts",
      "permalink": "category/kids/girls/girls-tops/girls-shirts",
      "parent_id": 49,
      "taxonomy_id": 13,
      "url_override": null,
      "description": "Girls Shirts",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 51,
      "name": "Brand",
      "pretty_name": "Brand",
      "permalink": "brand",
      "parent_id": null,
      "taxonomy_id": 14,
      "url_override": null,
      "description": "Brand",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 52,
      "name": "Ruby on Rails - 7",
      "pretty_name": "Brand -> Ruby on Rails - 7",
      "permalink": "brand/ruby-on-rails-7",
      "parent_id": 51,
      "taxonomy_id": 14,
      "url_override": null,
      "description": "Ruby on Rails - 7",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 53,
      "name": "Ruby on Rails - 8",
      "pretty_name": "Brand -> Ruby on Rails - 8",
      "permalink": "brand/ruby-on-rails-8",
      "parent_id": 51,
      "taxonomy_id": 14,
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
ETag: W/&quot;e56a2a6da03a4152953afa693c6e584c&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 5ad052a4-4085-43ed-bc11-a64c81c4bb09
X-Runtime: 0.015668
Vary: Origin
Content-Length: 589
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
    "created_at": "2021-03-31T06:15:19.223-04:00",
    "updated_at": "2021-03-31T06:15:19.313-04:00",
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
    "google_product_category": null,
    "short_description": null,
    "view_all_url_override": null
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
ETag: W/&quot;91da67e7920f26401ba3c34f2a5f4759&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 6347dbb3-5ef0-494c-bb05-17d43c67d47a
X-Runtime: 0.018977
Vary: Origin
Content-Length: 199
200 OK
```


```json
[
  {
    "id": 59,
    "name": "Kids",
    "navigation_url": "/shop/kids",
    "parent_id": 58,
    "lft": 2,
    "depth": 1,
    "highlight": false,
    "header_link": false,
    "add_flair": false,
    "view_all_url_override": null,
    "icon_url_original": false
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
ETag: W/&quot;ce6371714200b975554be562b849960b&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 158fa6bf-1e98-4479-9b59-8cc4f25a1afa
X-Runtime: 0.011884
Vary: Origin
Content-Length: 590
200 OK
```


```json
[
  {
    "id": 57,
    "parent_id": 56,
    "position": 0,
    "name": "brand_x",
    "permalink": "brand/brand_x",
    "taxonomy_id": 16,
    "lft": 6,
    "rgt": 7,
    "icon_file_name": null,
    "icon_content_type": null,
    "icon_file_size": null,
    "icon_updated_at": null,
    "description": null,
    "created_at": "2021-03-31T06:15:20.247-04:00",
    "updated_at": "2021-03-31T06:15:20.299-04:00",
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
    "google_product_category": null,
    "short_description": null,
    "view_all_url_override": null
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
user[email]=email7%40example.com&user[password]=secret
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
Authorization: Bearer b02c5e5ea574d2cd6b470d22508eae3fdf8e5b4242d03c2c
ETag: W/&quot;048eeaf5e5cd5bca8a17f2b1824ef455&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 44ede480-5516-4c3a-902c-3e6e541354b8
X-Runtime: 0.009628
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
  "created_at": "2021-03-31T06:14:51.820-04:00",
  "updated_at": "2021-03-31T06:14:51.822-04:00",
  "spree_api_key": "b02c5e5ea574d2cd6b470d22508eae3fdf8e5b4242d03c2c",
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
X-Spree-Order-Token: wmwzetl4wU9zPlaOi77Xwg
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/users/login`

#### Parameters


```json
user[email]=email8%40example.com&user[password]=secret&order_number=M322747836
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
Authorization: Bearer 7541a388dead90b8d81d4302c7f6e8e93314092c962d8611
ETag: W/&quot;8e18714d1b1fb4daa7d1c19081628540&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 9a57f8b1-a57a-45e8-8a28-255d1cff27cd
X-Runtime: 0.013614
Vary: Origin
Content-Length: 559
200 OK
```


```json
{
  "id": 8,
  "email": "email8@example.com",
  "persistence_token": null,
  "perishable_token": null,
  "last_request_at": null,
  "login": "email8@example.com",
  "ship_address_id": null,
  "bill_address_id": null,
  "created_at": "2021-03-31T06:14:51.839-04:00",
  "updated_at": "2021-03-31T06:14:51.841-04:00",
  "spree_api_key": "7541a388dead90b8d81d4302c7f6e8e93314092c962d8611",
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
Authorizat IO N: Bearer 98845a89839181262b755140b8988d7f85db4e29214a5e47
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
Authorization: Bearer 98845a89839181262b755140b8988d7f85db4e29214a5e47
ETag: W/&quot;6faba858070f971e0e816f19a840c76a&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 328c8fcc-eedf-4ec8-9313-135242ecdd53
X-Runtime: 0.031056
Vary: Origin
Content-Length: 1531
200 OK
```


```json
{
  "email": "email9@example.com",
  "first_name": null,
  "last_name": null,
  "id": 9,
  "subscribed": false,
  "addresses": [
    {
      "id": 12,
      "firstname": "John",
      "lastname": "Smith",
      "full_name": "John Smith",
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
      "default": true
    },
    {
      "id": 11,
      "firstname": "John",
      "lastname": "Smith",
      "full_name": "John Smith",
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
        "created_at": "2021-03-31T06:14:52.202-04:00",
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
        "created_at": "2021-03-31T06:14:52.219-04:00",
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
        "created_at": "2021-03-31T06:14:52.228-04:00",
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
Authorization: Bearer 16ac6b708ed3abe37b4179f347158c92bbbbc9a4ea744520
ETag: W/&quot;23535f3ce7558502e9abcaebafca1dc1&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: ba45a1a1-abcf-4a40-b74d-5962f8c72dff
X-Runtime: 0.023029
Vary: Origin
Content-Length: 185
201 Created
```


```json
{
  "id": 10,
  "email": "test@example.com",
  "created_at": "2021-03-31T06:14:52.273-04:00",
  "updated_at": "2021-03-31T06:14:52.275-04:00",
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
X-Spree-Order-Token: wKHRjGrptU1dLUdR5_g_sg
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/users`

#### Parameters


```json
user[email]=test%40example.com&user[password]=test123&user[password_confirmation]=test123&order_number=M651663668
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
Authorization: Bearer 589420a20c90df6c74c5638836cac107104c1504207c372d
ETag: W/&quot;d9184c0f9dfd90af37129276035b9073&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 3bdd3334-8de0-49e7-ad9f-d9d986608356
X-Runtime: 0.022924
Vary: Origin
Content-Length: 185
201 Created
```


```json
{
  "id": 11,
  "email": "test@example.com",
  "created_at": "2021-03-31T06:14:52.650-04:00",
  "updated_at": "2021-03-31T06:14:52.652-04:00",
  "subscribed": false,
  "bill_address": null,
  "ship_address": null
}
```



## Subscribe a user


### Request

#### Endpoint

```plaintext
PUT /api/users/13/subscribe
Accept: application/json
Authorizat IO N: Bearer 3471cb7643cff277a50acc2cac6701f7e12db1c134fe2ec5
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
Authorization: Bearer 3471cb7643cff277a50acc2cac6701f7e12db1c134fe2ec5
ETag: W/&quot;6b34c735ba249a51e7f0e9e30ae705bd&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 7396b6ab-9726-4707-9cdb-12f19226d6d2
X-Runtime: 0.015495
Vary: Origin
Content-Length: 187
200 OK
```


```json
{
  "id": 13,
  "email": "email11@example.com",
  "created_at": "2021-03-31T06:14:52.716-04:00",
  "updated_at": "2021-03-31T06:14:52.718-04:00",
  "subscribed": true,
  "bill_address": null,
  "ship_address": null
}
```



## Unsubscribe a user


### Request

#### Endpoint

```plaintext
PUT /api/users/12/unsubscribe
Accept: application/json
Authorizat IO N: Bearer 9c0cc3696f710676ddc720c4b3e4525f60e6a0b2c383c9d2
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
Authorization: Bearer 9c0cc3696f710676ddc720c4b3e4525f60e6a0b2c383c9d2
ETag: W/&quot;e574d88e0fa65690fa404bf42e9db32c&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: b4512fe9-7721-43c4-8c82-97f90f142983
X-Runtime: 0.015886
Vary: Origin
Content-Length: 188
200 OK
```


```json
{
  "id": 12,
  "email": "email10@example.com",
  "created_at": "2021-03-31T06:14:52.685-04:00",
  "updated_at": "2021-03-31T06:14:52.687-04:00",
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
GET /api/variants/34
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
ETag: W/&quot;53660aedf85698267641c13c013b201f&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: a9d0b1db-51cd-45f4-8789-ced730111b47
X-Runtime: 0.105320
Vary: Origin
Content-Length: 2348
200 OK
```


```json
{
  "id": 34,
  "name": "Product #17 - 7447",
  "sku": "SKU-33",
  "is_master": false,
  "slug": "product-17-7447",
  "description": "As seen on TV!",
  "track_inventory": true,
  "height": null,
  "width": null,
  "depth": null,
  "weight": null,
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
    {
      "id": 1,
      "position": 1,
      "attachment_content_type": "image/jpeg",
      "attachment_file_name": "thinking-cat.jpg",
      "type": "Spree::Image",
      "attachment_updated_at": "2021-03-31T06:14:57.815-04:00",
      "attachment_width": 489,
      "attachment_height": 490,
      "alt": null,
      "viewable_type": "Spree::Variant",
      "viewable_id": 34,
      "mini_url": "/spree/products/1/mini/thinking-cat.jpg?1617185697",
      "small_url": "/spree/products/1/small/thinking-cat.jpg?1617185697",
      "product_url": "/spree/products/1/product/thinking-cat.jpg?1617185697",
      "large_url": "/spree/products/1/large/thinking-cat.jpg?1617185697",
      "product_large_url": "/spree/products/1/product_large/thinking-cat.jpg?1617185697",
      "product_retina_url": "/spree/products/1/product_retina/thinking-cat.jpg?1617185697",
      "product_zoom_url": "/spree/products/1/product_zoom/thinking-cat.jpg?1617185697"
    }
  ],
  "videos": [

  ],
  "variant_properties": [

  ],
  "stock_items": [

  ],
  "prices": [
    {
      "id": 32,
      "vendor_id": 80,
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
        "display_monogram_customizations": null,
        "monogrammable": null
      }
    },
    {
      "id": 33,
      "vendor_id": 81,
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
        "display_monogram_customizations": null,
        "monogrammable": null
      }
    }
  ]
}
```



## Fetching a variant with Monogram Customization


### Request

#### Endpoint

```plaintext
GET /api/variants/40
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
ETag: W/&quot;1d97580cdb35455df8fa2f3588203479&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: d27c6916-2a32-4d33-9ef2-6a8f75e87d8b
X-Runtime: 0.051251
Vary: Origin
Content-Length: 2987
200 OK
```


```json
{
  "id": 40,
  "name": "Product #20 - 1633",
  "sku": "SKU-39",
  "is_master": false,
  "slug": "product-20-1633",
  "description": "As seen on TV!",
  "track_inventory": true,
  "height": null,
  "width": null,
  "depth": null,
  "weight": null,
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
    {
      "id": 4,
      "position": 1,
      "attachment_content_type": "image/jpeg",
      "attachment_file_name": "thinking-cat.jpg",
      "type": "Spree::Image",
      "attachment_updated_at": "2021-03-31T06:14:59.504-04:00",
      "attachment_width": 489,
      "attachment_height": 490,
      "alt": null,
      "viewable_type": "Spree::Variant",
      "viewable_id": 40,
      "mini_url": "/spree/products/4/mini/thinking-cat.jpg?1617185699",
      "small_url": "/spree/products/4/small/thinking-cat.jpg?1617185699",
      "product_url": "/spree/products/4/product/thinking-cat.jpg?1617185699",
      "large_url": "/spree/products/4/large/thinking-cat.jpg?1617185699",
      "product_large_url": "/spree/products/4/product_large/thinking-cat.jpg?1617185699",
      "product_retina_url": "/spree/products/4/product_retina/thinking-cat.jpg?1617185699",
      "product_zoom_url": "/spree/products/4/product_zoom/thinking-cat.jpg?1617185699"
    }
  ],
  "videos": [

  ],
  "variant_properties": [

  ],
  "stock_items": [

  ],
  "prices": [
    {
      "id": 41,
      "vendor_id": 101,
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
        "display_monogram_customizations": null,
        "monogrammable": null
      }
    },
    {
      "id": 42,
      "vendor_id": 102,
      "price": "20.0",
      "original_price": "20.0",
      "discount_percent": 0.0,
      "total_on_hand": 0,
      "country_iso": null,
      "final_sale": false,
      "on_sale": false,
      "offer_settings": {
        "cost_price": null,
        "is_registry": false
      },
      "monogram": {
        "monogrammable_only": false,
        "monogram_price": "5.5",
        "monogram_cost_price": "2.25",
        "monogram_lead_time": null,
        "monogram_max_text_length": 20,
        "monogram_customizations": {
          "fonts": [
            {
              "name": "Monogram Font 1",
              "value": "serif"
            },
            {
              "name": "Monogram Font 1 Title",
              "value": "Toy Soilder"
            },
            {
              "name": "Monogram Font 2",
              "value": "Times"
            },
            {
              "name": "Monogram Font 2 Title",
              "value": "Emerson"
            }
          ],
          "colors": [
            {
              "name": "Monogram Color 1",
              "value": "#ffffff"
            },
            {
              "name": "Monogram Color 1 Title",
              "value": "White"
            },
            {
              "name": "Monogram Color 2",
              "value": "#FF0000"
            },
            {
              "name": "Monogram Color 2 Title",
              "value": "Red"
            }
          ]
        },
        "display_monogram_customizations": {
          "colors": {
            "Monogram Color 1": {
              "value": "#ffffff",
              "name": "White"
            },
            "Monogram Color 2": {
              "value": "#FF0000",
              "name": "Red"
            }
          },
          "fonts": {
            "Monogram Font 1": {
              "value": "serif",
              "name": "Toy Soilder"
            },
            "Monogram Font 2": {
              "value": "Times",
              "name": "Emerson"
            }
          }
        },
        "monogrammable": true
      }
    }
  ]
}
```



## Fetching a variant with Monogram Customization and color is not required


### Request

#### Endpoint

```plaintext
GET /api/variants/42
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
ETag: W/&quot;049685724b3b4b4c17d1461635d632ef&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 856c72a6-79da-464f-841f-d7c4e10a18ee
X-Runtime: 0.051052
Vary: Origin
Content-Length: 2693
200 OK
```


```json
{
  "id": 42,
  "name": "Product #21 - 7836",
  "sku": "SKU-41",
  "is_master": false,
  "slug": "product-21-7836",
  "description": "As seen on TV!",
  "track_inventory": true,
  "height": null,
  "width": null,
  "depth": null,
  "weight": null,
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
    {
      "id": 5,
      "position": 1,
      "attachment_content_type": "image/jpeg",
      "attachment_file_name": "thinking-cat.jpg",
      "type": "Spree::Image",
      "attachment_updated_at": "2021-03-31T06:15:00.041-04:00",
      "attachment_width": 489,
      "attachment_height": 490,
      "alt": null,
      "viewable_type": "Spree::Variant",
      "viewable_id": 42,
      "mini_url": "/spree/products/5/mini/thinking-cat.jpg?1617185700",
      "small_url": "/spree/products/5/small/thinking-cat.jpg?1617185700",
      "product_url": "/spree/products/5/product/thinking-cat.jpg?1617185700",
      "large_url": "/spree/products/5/large/thinking-cat.jpg?1617185700",
      "product_large_url": "/spree/products/5/product_large/thinking-cat.jpg?1617185700",
      "product_retina_url": "/spree/products/5/product_retina/thinking-cat.jpg?1617185700",
      "product_zoom_url": "/spree/products/5/product_zoom/thinking-cat.jpg?1617185700"
    }
  ],
  "videos": [

  ],
  "variant_properties": [

  ],
  "stock_items": [

  ],
  "prices": [
    {
      "id": 44,
      "vendor_id": 108,
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
        "display_monogram_customizations": null,
        "monogrammable": null
      }
    },
    {
      "id": 45,
      "vendor_id": 109,
      "price": "20.0",
      "original_price": "20.0",
      "discount_percent": 0.0,
      "total_on_hand": 0,
      "country_iso": null,
      "final_sale": false,
      "on_sale": false,
      "offer_settings": {
        "cost_price": null,
        "is_registry": false
      },
      "monogram": {
        "monogrammable_only": false,
        "monogram_price": "5.5",
        "monogram_cost_price": "2.25",
        "monogram_lead_time": null,
        "monogram_max_text_length": 20,
        "monogram_customizations": {
          "fonts": [
            {
              "name": "Monogram Font 1",
              "value": "serif"
            },
            {
              "name": "Monogram Font 1 Title",
              "value": "Toy Soilder"
            },
            {
              "name": "Monogram Font 2",
              "value": "Times"
            },
            {
              "name": "Monogram Font 2 Title",
              "value": "Emerson"
            }
          ],
          "colors": [

          ]
        },
        "display_monogram_customizations": {
          "colors": {
          },
          "fonts": {
            "Monogram Font 1": {
              "value": "serif",
              "name": "Toy Soilder"
            },
            "Monogram Font 2": {
              "value": "Times",
              "name": "Emerson"
            }
          }
        },
        "monogrammable": true
      }
    }
  ]
}
```



## Fetching a variant with dimensions


### Request

#### Endpoint

```plaintext
GET /api/variants/36
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
ETag: W/&quot;8db2ba82b7b74ea71cd2af68f1fd0882&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 361f4d60-a353-4fb8-9003-5d5ec0af43fc
X-Runtime: 0.060392
Vary: Origin
Content-Length: 2362
200 OK
```


```json
{
  "id": 36,
  "name": "Product #18 - 8320",
  "sku": "SKU-35",
  "is_master": false,
  "slug": "product-18-8320",
  "description": "As seen on TV!",
  "track_inventory": true,
  "height": "5.0\"",
  "width": "2.5\"",
  "depth": "1.2\"",
  "weight": "2.5 lbs",
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
    {
      "id": 2,
      "position": 1,
      "attachment_content_type": "image/jpeg",
      "attachment_file_name": "thinking-cat.jpg",
      "type": "Spree::Image",
      "attachment_updated_at": "2021-03-31T06:14:58.437-04:00",
      "attachment_width": 489,
      "attachment_height": 490,
      "alt": null,
      "viewable_type": "Spree::Variant",
      "viewable_id": 36,
      "mini_url": "/spree/products/2/mini/thinking-cat.jpg?1617185698",
      "small_url": "/spree/products/2/small/thinking-cat.jpg?1617185698",
      "product_url": "/spree/products/2/product/thinking-cat.jpg?1617185698",
      "large_url": "/spree/products/2/large/thinking-cat.jpg?1617185698",
      "product_large_url": "/spree/products/2/product_large/thinking-cat.jpg?1617185698",
      "product_retina_url": "/spree/products/2/product_retina/thinking-cat.jpg?1617185698",
      "product_zoom_url": "/spree/products/2/product_zoom/thinking-cat.jpg?1617185698"
    }
  ],
  "videos": [

  ],
  "variant_properties": [

  ],
  "stock_items": [

  ],
  "prices": [
    {
      "id": 35,
      "vendor_id": 87,
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
        "display_monogram_customizations": null,
        "monogrammable": null
      }
    },
    {
      "id": 36,
      "vendor_id": 88,
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
        "display_monogram_customizations": null,
        "monogrammable": null
      }
    }
  ]
}
```



## Fetching a variant without dimensions


### Request

#### Endpoint

```plaintext
GET /api/variants/38
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
ETag: W/&quot;55a1d157c586a8fdffdfc71e19b6aaa5&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 7dff9c6c-61a0-4efa-b432-fbbf906708c8
X-Runtime: 0.048640
Vary: Origin
Content-Length: 2348
200 OK
```


```json
{
  "id": 38,
  "name": "Product #19 - 7183",
  "sku": "SKU-37",
  "is_master": false,
  "slug": "product-19-7183",
  "description": "As seen on TV!",
  "track_inventory": true,
  "height": null,
  "width": null,
  "depth": null,
  "weight": null,
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
    {
      "id": 3,
      "position": 1,
      "attachment_content_type": "image/jpeg",
      "attachment_file_name": "thinking-cat.jpg",
      "type": "Spree::Image",
      "attachment_updated_at": "2021-03-31T06:14:59.027-04:00",
      "attachment_width": 489,
      "attachment_height": 490,
      "alt": null,
      "viewable_type": "Spree::Variant",
      "viewable_id": 38,
      "mini_url": "/spree/products/3/mini/thinking-cat.jpg?1617185699",
      "small_url": "/spree/products/3/small/thinking-cat.jpg?1617185699",
      "product_url": "/spree/products/3/product/thinking-cat.jpg?1617185699",
      "large_url": "/spree/products/3/large/thinking-cat.jpg?1617185699",
      "product_large_url": "/spree/products/3/product_large/thinking-cat.jpg?1617185699",
      "product_retina_url": "/spree/products/3/product_retina/thinking-cat.jpg?1617185699",
      "product_zoom_url": "/spree/products/3/product_zoom/thinking-cat.jpg?1617185699"
    }
  ],
  "videos": [

  ],
  "variant_properties": [

  ],
  "stock_items": [

  ],
  "prices": [
    {
      "id": 38,
      "vendor_id": 94,
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
        "display_monogram_customizations": null,
        "monogrammable": null
      }
    },
    {
      "id": 39,
      "vendor_id": 95,
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
        "display_monogram_customizations": null,
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
Authorizat IO N: Bearer 67342f44e0812b28a4deff27ec933c40ed45455b579b974a
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
ETag: W/&quot;ff348e357101d25fa8a24fe37196a7ce&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 09ff7c0c-0936-4f71-a9fd-4baef8b1c35d
X-Runtime: 0.010961
Vary: Origin
Content-Length: 206
200 OK
```


```json
[
  {
    "id": 5,
    "user_id": 65,
    "payment_source_type": "SolidusPaypalBraintree::Source",
    "payment_source_id": 7,
    "default": false,
    "created_at": "2021-03-31T06:15:08.036-04:00",
    "updated_at": "2021-03-31T06:15:08.036-04:00"
  }
]
```



## Remove the payment from the user wallet


### Request

#### Endpoint

```plaintext
DELETE /api/wallet_payment_sources/6
Accept: application/json
Authorizat IO N: Bearer 40538925ee376045194c3c6c7e8e1ff1ecccb11ac6f7b448
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
X-Request-Id: cb51da94-0bfe-430c-89b9-9109f0610e41
X-Runtime: 0.010755
Vary: Origin
204 No Content
```




## Set a wallet payment source as the default user payment method


### Request

#### Endpoint

```plaintext
POST /api/wallet_payment_sources/4/default
Accept: application/json
Authorizat IO N: Bearer 91fcc02f9966be88fa8db87afb3dc0b3f5f3a502c44977bd
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
X-Request-Id: 012ab2c6-f6e0-4f6f-8bc0-39dd95da2b0a
X-Runtime: 0.027711
Vary: Origin
204 No Content
```




# Wished Products

Create a wished product. Any user can create a wished product for one of their own wishlists.                 Admins can create wished products for others.

## Create a wished product


### Request

#### Endpoint

```plaintext
POST /api/wished_products
Accept: application/json
Authorizat IO N: Bearer 2d276d67a009fdc01e34edea5ffddbabf2d5b4f0f2e11430
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/wished_products`

#### Parameters


```json
wished_product[wishlist_id]=29&wished_product[variant_id]=131&wished_product[quantity]=2&wished_product[remark]=Foo+bar
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
ETag: W/&quot;5eec047626eeae76b7b7762f711fdef1&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 3162d00c-3837-4a45-8d3e-76392386f2b5
X-Runtime: 0.034470
Vary: Origin
Content-Length: 120
201 Created
```


```json
{
  "id": 10,
  "wishlist_id": 29,
  "variant_id": 131,
  "quantity": 2,
  "remark": "Foo bar",
  "created_at": "2021-03-31T06:15:15.657-04:00"
}
```



## Delete a wished product


### Request

#### Endpoint

```plaintext
DELETE /api/wished_products/17
Accept: application/json
Authorizat IO N: Bearer fc1c1738936ecf6e71a1c11ea54fff085241cc45c512ca45
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
X-Request-Id: 00d37f7c-26e0-4b50-a48e-1940e3317b18
X-Runtime: 0.011217
Vary: Origin
204 No Content
```




## Get a single wished product


### Request

#### Endpoint

```plaintext
GET /api/wished_products/14
Accept: application/json
Authorizat IO N: Bearer 0b751b5458a0b7ecba7ad52deebfb71ba4d3394c75eca90a
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
ETag: W/&quot;13730ec4adde2cd5372ba22b8bfddfed&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: bd1236fe-1e91-4126-89b7-4674f187c3ac
X-Runtime: 0.011975
Vary: Origin
Content-Length: 115
200 OK
```


```json
{
  "id": 14,
  "wishlist_id": 31,
  "variant_id": 141,
  "quantity": 1,
  "remark": null,
  "created_at": "2021-03-31T06:15:16.425-04:00"
}
```



## Get all wished products


### Request

#### Endpoint

```plaintext
GET /api/wished_products
Accept: application/json
Authorizat IO N: Bearer a357d96806d5bb160b00b929e0fc0bb82c1207f679ced667
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
ETag: W/&quot;f60d631b2b67ced31709da04f0805ae4&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 7f660494-55f4-4f61-baaa-29b98cad2773
X-Runtime: 0.011169
Vary: Origin
Content-Length: 436
200 OK
```


```json
{
  "wished_products": [
    {
      "id": 22,
      "wishlist_id": 35,
      "variant_id": 157,
      "quantity": 1,
      "remark": null,
      "created_at": "2021-03-31T06:15:17.536-04:00"
    },
    {
      "id": 21,
      "wishlist_id": 34,
      "variant_id": 155,
      "quantity": 1,
      "remark": null,
      "created_at": "2021-03-31T06:15:17.420-04:00"
    },
    {
      "id": 20,
      "wishlist_id": 33,
      "variant_id": 153,
      "quantity": 1,
      "remark": null,
      "created_at": "2021-03-31T06:15:17.303-04:00"
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
Authorizat IO N: Bearer e1938930847ff08d6ee8b4e3b199239e1cf62195844d33b8
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
ETag: W/&quot;5a56046a1168de71c0a266f1acdfd8b1&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 52b2fbe7-8fa7-4d22-9136-f6623199f485
X-Runtime: 0.108473
Vary: Origin
Content-Length: 2446
200 OK
```


```json
{
  "wished_products": [
    {
      "id": 25,
      "wishlist_id": 38,
      "variant_id": 163,
      "quantity": 1,
      "remark": null,
      "created_at": "2021-03-31T06:15:17.950-04:00",
      "variant": {
        "id": 163,
        "name": "Product #87 - 4815",
        "sku": "SKU-162",
        "is_master": false,
        "slug": "product-87-4815",
        "description": "As seen on TV!",
        "track_inventory": true,
        "cost_price": "17.0",
        "height": null,
        "width": null,
        "depth": null,
        "weight": null,
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
            "id": 76,
            "name": "Size-76",
            "presentation": "S",
            "option_type_name": "foo-size-76",
            "option_type_id": 76,
            "option_type_presentation": "Size",
            "position": 1
          }
        ],
        "images": [

        ],
        "videos": [

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
      "variant_id": 161,
      "quantity": 1,
      "remark": null,
      "created_at": "2021-03-31T06:15:17.831-04:00",
      "variant": {
        "id": 161,
        "name": "Product #86 - 5857",
        "sku": "SKU-160",
        "is_master": false,
        "slug": "product-86-5857",
        "description": "As seen on TV!",
        "track_inventory": true,
        "cost_price": "17.0",
        "height": null,
        "width": null,
        "depth": null,
        "weight": null,
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
            "id": 75,
            "name": "Size-75",
            "presentation": "S",
            "option_type_name": "foo-size-75",
            "option_type_id": 75,
            "option_type_presentation": "Size",
            "position": 1
          }
        ],
        "images": [

        ],
        "videos": [

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
      "variant_id": 159,
      "quantity": 1,
      "remark": null,
      "created_at": "2021-03-31T06:15:17.711-04:00",
      "variant": {
        "id": 159,
        "name": "Product #85 - 6054",
        "sku": "SKU-158",
        "is_master": false,
        "slug": "product-85-6054",
        "description": "As seen on TV!",
        "track_inventory": true,
        "cost_price": "17.0",
        "height": null,
        "width": null,
        "depth": null,
        "weight": null,
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
            "id": 74,
            "name": "Size-74",
            "presentation": "S",
            "option_type_name": "foo-size-74",
            "option_type_id": 74,
            "option_type_presentation": "Size",
            "position": 1
          }
        ],
        "images": [

        ],
        "videos": [

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
Authorizat IO N: Bearer 7b153f4d61eea3b6cd28152b4a95430d9156d184ebad905a
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
ETag: W/&quot;d4b7458449c126b1de4952e9c122a25b&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 9a82d9be-a594-42a3-81b2-85df2d82073f
X-Runtime: 0.096181
Vary: Origin
Content-Length: 2386
200 OK
```


```json
{
  "wished_products": [
    {
      "id": 29,
      "wishlist_id": 40,
      "variant_id": 171,
      "quantity": 1,
      "remark": null,
      "created_at": "2021-03-31T06:15:18.620-04:00",
      "variant": {
        "id": 171,
        "name": "Product #91 - 9267",
        "sku": "SKU-170",
        "is_master": false,
        "slug": "product-91-9267",
        "description": "As seen on TV!",
        "track_inventory": true,
        "height": null,
        "width": null,
        "depth": null,
        "weight": null,
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
            "id": 80,
            "name": "Size-80",
            "presentation": "S",
            "option_type_name": "foo-size-80",
            "option_type_id": 80,
            "option_type_presentation": "Size",
            "position": 1
          }
        ],
        "images": [

        ],
        "videos": [

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
      "variant_id": 173,
      "quantity": 1,
      "remark": null,
      "created_at": "2021-03-31T06:15:18.728-04:00",
      "variant": {
        "id": 173,
        "name": "Product #92 - 9208",
        "sku": "SKU-172",
        "is_master": false,
        "slug": "product-92-9208",
        "description": "As seen on TV!",
        "track_inventory": true,
        "height": null,
        "width": null,
        "depth": null,
        "weight": null,
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
            "id": 81,
            "name": "Size-81",
            "presentation": "S",
            "option_type_name": "foo-size-81",
            "option_type_id": 81,
            "option_type_presentation": "Size",
            "position": 1
          }
        ],
        "images": [

        ],
        "videos": [

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
      "variant_id": 175,
      "quantity": 1,
      "remark": null,
      "created_at": "2021-03-31T06:15:18.836-04:00",
      "variant": {
        "id": 175,
        "name": "Product #93 - 5417",
        "sku": "SKU-174",
        "is_master": false,
        "slug": "product-93-5417",
        "description": "As seen on TV!",
        "track_inventory": true,
        "height": null,
        "width": null,
        "depth": null,
        "weight": null,
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
            "id": 82,
            "name": "Size-82",
            "presentation": "S",
            "option_type_name": "foo-size-82",
            "option_type_id": 82,
            "option_type_presentation": "Size",
            "position": 1
          }
        ],
        "images": [

        ],
        "videos": [

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
Authorizat IO N: Bearer dcdf678153b717eb3d446af45f0f28fd01cb7f1148d4037b
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
ETag: W/&quot;bbda9ce7472e5308f73755ab5dbe6f68&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 439f6738-9da6-4608-a882-671f740a08b6
X-Runtime: 0.010962
Vary: Origin
Content-Length: 436
200 OK
```


```json
{
  "wished_products": [
    {
      "id": 26,
      "wishlist_id": 39,
      "variant_id": 165,
      "quantity": 1,
      "remark": null,
      "created_at": "2021-03-31T06:15:18.225-04:00"
    },
    {
      "id": 27,
      "wishlist_id": 39,
      "variant_id": 167,
      "quantity": 1,
      "remark": null,
      "created_at": "2021-03-31T06:15:18.357-04:00"
    },
    {
      "id": 28,
      "wishlist_id": 39,
      "variant_id": 169,
      "quantity": 1,
      "remark": null,
      "created_at": "2021-03-31T06:15:18.463-04:00"
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
PATCH /api/wished_products/11
Accept: application/json
Authorizat IO N: Bearer 271f6dd3de33f218f740de0b208de353b2fd8e2da323618c
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/wished_products/:id`

#### Parameters


```json
wished_product[wishlist_id]=30&wished_product[variant_id]=139&wished_product[quantity]=2&wished_product[remark]=Foo+bar
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
ETag: W/&quot;9b1503d7633a7a1a7b853146102c8074&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: bfa38172-3875-4027-b91a-4e3ddaae6630
X-Runtime: 0.043382
Vary: Origin
Content-Length: 120
200 OK
```


```json
{
  "id": 11,
  "wishlist_id": 30,
  "variant_id": 139,
  "quantity": 2,
  "remark": "Foo bar",
  "created_at": "2021-03-31T06:15:15.834-04:00"
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
Authorizat IO N: Bearer 9e7c73293fd9b8f70ae5520e04d9f98f80f3405d60a40e1c
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/wishlists`

#### Parameters


```json
wishlist[name]&wishlist[user_id]=54&wishlist[is_default]=true&wishlist[is_public]=false
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
ETag: W/&quot;a8e371cc9f6cf51bf9dfbe7a59b9231a&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 8c822958-fa69-4bce-adfb-9d6c4392916c
X-Runtime: 0.013573
Vary: Origin
Content-Length: 100
201 Created
```


```json
{
  "id": 28,
  "user_id": 54,
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
Authorizat IO N: Bearer 376bde6cce4b80a7489e1227b5b37f75ee5ece9c183059d0
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
X-Request-Id: 2a59f6f9-54fa-4c03-8bd3-d21d277b3272
X-Runtime: 0.012237
Vary: Origin
204 No Content
```




## Get a single wishlist


### Request

#### Endpoint

```plaintext
GET /api/wishlists/17
Accept: application/json
Authorizat IO N: Bearer 31dd9c62ff3afdba2047a824ce51d00d9abc4ddbbb4713f7
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
ETag: W/&quot;0054c331a324337fb38d44a7d8fae168&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 276444c7-5eb6-4c73-bf7e-b073bb8f0e6e
X-Runtime: 0.012716
Vary: Origin
Content-Length: 442
200 OK
```


```json
{
  "id": 17,
  "user_id": 42,
  "name": "Wishlist #16",
  "is_public": false,
  "is_default": true,
  "wished_products": [
    {
      "id": 7,
      "wishlist_id": 17,
      "variant_id": 56,
      "quantity": 1,
      "remark": null,
      "created_at": "2021-03-31T06:15:01.409-04:00"
    },
    {
      "id": 8,
      "wishlist_id": 17,
      "variant_id": 58,
      "quantity": 1,
      "remark": null,
      "created_at": "2021-03-31T06:15:01.514-04:00"
    },
    {
      "id": 9,
      "wishlist_id": 17,
      "variant_id": 60,
      "quantity": 1,
      "remark": null,
      "created_at": "2021-03-31T06:15:01.620-04:00"
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
Authorizat IO N: Bearer 7ff387f0f5768ea7c4bfe80b1363a41cb7526712adccd272
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
ETag: W/&quot;2526eda1eddeb5c68f65c60676025748&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 1b788e3e-769e-4190-870d-2f3a5dc78f24
X-Runtime: 0.012735
Vary: Origin
Content-Length: 894
200 OK
```


```json
{
  "wishlists": [
    {
      "id": 18,
      "user_id": 43,
      "name": "Wishlist #17",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 19,
      "user_id": 44,
      "name": "Wishlist #18",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 20,
      "user_id": 45,
      "name": "Wishlist #19",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 21,
      "user_id": 46,
      "name": "Wishlist #20",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 22,
      "user_id": 47,
      "name": "Wishlist #21",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 23,
      "user_id": 48,
      "name": "Wishlist #22",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 24,
      "user_id": 49,
      "name": "Wishlist #23",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 25,
      "user_id": 50,
      "name": "Wishlist #24",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 26,
      "user_id": 51,
      "name": "Wishlist #25",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 27,
      "user_id": 52,
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
Authorizat IO N: Bearer 5622f991a6b3482d9b0e5d439d2ed69ed551223cd18c2460
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
ETag: W/&quot;8dd5f6d44214e44e86f0de1ce1f34629&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: c6df60d7-8750-4e6d-9952-f1d2e8e7ecd6
X-Runtime: 0.009676
Vary: Origin
Content-Length: 442
200 OK
```


```json
{
  "id": 16,
  "user_id": 41,
  "name": "Wishlist #15",
  "is_public": false,
  "is_default": true,
  "wished_products": [
    {
      "id": 4,
      "wishlist_id": 16,
      "variant_id": 50,
      "quantity": 1,
      "remark": null,
      "created_at": "2021-03-31T06:15:01.049-04:00"
    },
    {
      "id": 5,
      "wishlist_id": 16,
      "variant_id": 52,
      "quantity": 1,
      "remark": null,
      "created_at": "2021-03-31T06:15:01.151-04:00"
    },
    {
      "id": 6,
      "wishlist_id": 16,
      "variant_id": 54,
      "quantity": 1,
      "remark": null,
      "created_at": "2021-03-31T06:15:01.255-04:00"
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
Authorizat IO N: Bearer 9d93094a45be287fee1eb249056f3f204c7c198d6107647d
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
ETag: W/&quot;9336a5b8e771af614d294ed10d8043b1&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: afffbe56-65ef-49aa-9d2f-4c0f76bac3bf
X-Runtime: 0.010961
Vary: Origin
Content-Length: 894
200 OK
```


```json
{
  "wishlists": [
    {
      "id": 6,
      "user_id": 40,
      "name": "Wishlist #5",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 7,
      "user_id": 40,
      "name": "Wishlist #6",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 8,
      "user_id": 40,
      "name": "Wishlist #7",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 9,
      "user_id": 40,
      "name": "Wishlist #8",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 10,
      "user_id": 40,
      "name": "Wishlist #9",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 11,
      "user_id": 40,
      "name": "Wishlist #10",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 12,
      "user_id": 40,
      "name": "Wishlist #11",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 13,
      "user_id": 40,
      "name": "Wishlist #12",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 14,
      "user_id": 40,
      "name": "Wishlist #13",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 15,
      "user_id": 40,
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
PATCH /api/wishlists/1
Accept: application/json
Authorizat IO N: Bearer c258d6ec59d70fa6618954916cccde0fe2b60f56d4676277
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/wishlists/:id`

#### Parameters


```json
wishlist[name]=Another+Wishlist&wishlist[user_id]=37&wishlist[is_default]=true&wishlist[is_public]=false
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
ETag: W/&quot;a19fa700d513bab0319829f0fef86bca&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: eeaa4ccd-7d59-4abe-860c-9ea1556c4fd1
X-Runtime: 0.051573
Vary: Origin
Content-Length: 442
200 OK
```


```json
{
  "id": 1,
  "user_id": 37,
  "name": "Another Wishlist",
  "is_public": false,
  "is_default": true,
  "wished_products": [
    {
      "id": 1,
      "wishlist_id": 1,
      "variant_id": 44,
      "quantity": 1,
      "remark": null,
      "created_at": "2021-03-31T06:15:00.520-04:00"
    },
    {
      "id": 2,
      "wishlist_id": 1,
      "variant_id": 46,
      "quantity": 1,
      "remark": null,
      "created_at": "2021-03-31T06:15:00.626-04:00"
    },
    {
      "id": 3,
      "wishlist_id": 1,
      "variant_id": 48,
      "quantity": 1,
      "remark": null,
      "created_at": "2021-03-31T06:15:00.757-04:00"
    }
  ]
}
```



