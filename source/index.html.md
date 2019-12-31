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
PUT /api/orders/M854241851/addresses/53
Accept: application/json
X-Spree-Order-Token: XLg9Frffr7zYZUd9sGxTxg
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
ETag: W/&quot;896c05e56f4d415d0cca8565f3fa47c7&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 643c347c-b54f-4ea6-89c4-43250e3aa764
X-Runtime: 0.045747
Vary: Origin
Content-Length: 507
200 OK
```


```json
{
  "id": 54,
  "firstname": "John the Tester",
  "lastname": null,
  "full_name": "John the Tester",
  "address1": "A Different Road",
  "address2": "Northwest",
  "city": "Herndon",
  "zipcode": "10049",
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
X-Spree-Order-Token: Ul_n6uxnSBZnK8O-OP_p_Q
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/braintree/transactions`

#### Parameters


```json
order_id=M623595767&payment_method_id=5&options[restart_checkout]=true&transaction[email]=maryellen.oga%40mckenziemcglynn.com&transaction[nonce]=fake-paypal-billing-agreement-nonce&transaction[phone]=555-555-0199&transaction[shipping_address_attributes][first_name]=John&transaction[shipping_address_attributes][last_name]=Stamm&transaction[shipping_address_attributes][address_line_1]=A+Different+Road&transaction[shipping_address_attributes][city]=Herndon&transaction[shipping_address_attributes][state_code]=AL&transaction[shipping_address_attributes][zip]=10007&transaction[shipping_address_attributes][country_code]=US&transaction[payment_type]=PayPalAccount&transaction[billing_address_attributes][first_name]=John&transaction[billing_address_attributes][last_name]=Stamm&transaction[billing_address_attributes][address_line_1]=A+Different+Road&transaction[billing_address_attributes][city]=Herndon&transaction[billing_address_attributes][state_code]=AL&transaction[billing_address_attributes][zip]=10007&transaction[billing_address_attributes][country_code]=US
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
ETag: W/&quot;4a0dcf2e43031f7db4665950847aa903&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 17907db5-6785-47c3-9907-437b5ff2f9d4
X-Runtime: 0.255057
Vary: Origin
Content-Length: 5338
200 OK
```


```json
{
  "id": 3,
  "number": "M623595767",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2019-12-31T09:44:53.087-05:00",
  "updated_at": "2019-12-31T09:44:53.299-05:00",
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
  "token": "Ul_n6uxnSBZnK8O-OP_p_Q",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order&order=M623595767&bzip=10007&init=true",
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
    "id": 11,
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
    "id": 12,
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
      "variant_id": 6,
      "vendor_id": 12,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 6,
        "name": "Product #3 - 4685",
        "sku": "SKU-5",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-3-4685",
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
      "vendor_name": "Vendor #12",
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
      "created_at": "2019-12-31T09:44:53.177-05:00",
      "updated_at": "2019-12-31T09:44:53.177-05:00",
      "payment_method": {
        "id": 5,
        "name": "Braintree"
      },
      "source": {
        "id": 5,
        "payment_type": "PayPalAccount",
        "token": "bgx899",
        "created_at": "2019-12-31T09:44:53.176-05:00",
        "email": "jane.doe@paypal.com"
      }
    }
  ],
  "shipments": [
    {
      "id": 5,
      "tracking": null,
      "tracking_url": null,
      "number": "H34345650223",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M623595767",
      "stock_location_name": "NY Warehouse",
      "giftwrappable": false,
      "stock_location_id": 3,
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
      "delivery_estimation": "Jan 02"
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
X-Spree-Order-Token: M0xBnChVOVuKN7TH2YALzg
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/braintree/transactions`

#### Parameters


```json
order_id=M823041737&payment_method_id=4&options[restart_checkout]=true&transaction[email]=maryellen.oga%40mckenziemcglynn.com&transaction[nonce]=fake-apple-pay-visa-nonce&transaction[phone]=555-555-0199&transaction[shipping_address_attributes][first_name]=John&transaction[shipping_address_attributes][last_name]=Stamm&transaction[shipping_address_attributes][address_line_1]=A+Different+Road&transaction[shipping_address_attributes][city]=Herndon&transaction[shipping_address_attributes][state_code]=AL&transaction[shipping_address_attributes][zip]=10005&transaction[shipping_address_attributes][country_code]=US&transaction[payment_type]=ApplePayCard
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
ETag: W/&quot;57c7fae4ebc869009c68e9583da0e6dd&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 0e2b2227-7b0b-4ce9-b99b-af0f226d3eec
X-Runtime: 0.448289
Vary: Origin
Content-Length: 5380
200 OK
```


```json
{
  "id": 2,
  "number": "M823041737",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2019-12-31T09:44:52.377-05:00",
  "updated_at": "2019-12-31T09:44:52.740-05:00",
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
  "token": "M0xBnChVOVuKN7TH2YALzg",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order&order=M823041737&bzip=10005&init=true",
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
    "id": 7,
    "firstname": "John",
    "lastname": "Stamm",
    "full_name": "John Stamm",
    "address1": "A Different Road",
    "address2": null,
    "city": "Herndon",
    "zipcode": "10005",
    "phone": "555-555-0199",
    "company": null,
    "alternative_phone": null,
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
    "id": 8,
    "firstname": "John",
    "lastname": "Stamm",
    "full_name": "John Stamm",
    "address1": "A Different Road",
    "address2": null,
    "city": "Herndon",
    "zipcode": "10005",
    "phone": "555-555-0199",
    "company": null,
    "alternative_phone": null,
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
        "name": "Product #2 - 6551",
        "sku": "SKU-3",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-2-6551",
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
      "created_at": "2019-12-31T09:44:52.529-05:00",
      "updated_at": "2019-12-31T09:44:52.529-05:00",
      "payment_method": {
        "id": 4,
        "name": "Braintree"
      },
      "source": {
        "id": 4,
        "payment_type": "ApplePayCard",
        "token": "cg7hsk",
        "created_at": "2019-12-31T09:44:52.528-05:00",
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
      "number": "H75631354847",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M823041737",
      "stock_location_name": "NY Warehouse",
      "giftwrappable": false,
      "stock_location_id": 2,
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
      "delivery_estimation": "Jan 02"
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
PUT /api/checkouts/M593982310/complete
Accept: application/json
X-Spree-Order-Token: KuDbTpifk_9yJLu6Jjgkkg
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
ETag: W/&quot;0c6527c8c67a86490685de0bc766c5f7&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: b30b07b9-8531-40a9-bccd-7c2f00a80da3
X-Runtime: 0.381607
Vary: Origin
Content-Length: 5542
200 OK
```


```json
{
  "id": 12,
  "number": "M593982310",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "complete",
  "adjustment_total": "0.0",
  "user_id": 58,
  "created_at": "2019-12-31T09:45:01.570-05:00",
  "updated_at": "2019-12-31T09:45:01.896-05:00",
  "completed_at": "2019-12-31T09:45:01.896-05:00",
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
  "gift_email": null,
  "gift_message": null,
  "is_gift": false,
  "display_item_total": "$10.00",
  "total_quantity": 1,
  "display_total": "$110.00",
  "display_ship_total": "$100.00",
  "display_tax_total": "$0.00",
  "token": "KuDbTpifk_9yJLu6Jjgkkg",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order&order=M593982310&bzip=10024&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [
    {
      "id": 9,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    },
    {
      "id": 10,
      "name": "Braintree",
      "partial_name": "paypal_braintree",
      "method_type": "paypal_braintree"
    }
  ],
  "bill_address": {
    "id": 28,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "PO Box 1337",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10024",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 25,
    "country_iso": "US",
    "state_id": 25,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 25,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 25,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 25
    }
  },
  "ship_address": {
    "id": 29,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "A Different Road",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10025",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 25,
    "country_iso": "US",
    "state_id": 25,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 25,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 25,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 25
    }
  },
  "line_items": [
    {
      "id": 13,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 67,
      "vendor_id": 132,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 67,
        "name": "Product #39 - 7181",
        "sku": "SKU-66",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-39-7181",
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
      "vendor_name": "Vendor #132",
      "country_iso": "US",
      "adjustments": [

      ]
    }
  ],
  "payments": [
    {
      "id": 3,
      "source_type": "SolidusPaypalBraintree::Source",
      "source_id": 9,
      "amount": "110.0",
      "display_amount": "$110.00",
      "payment_method_id": 9,
      "state": "completed",
      "avs_response": "M",
      "created_at": "2019-12-31T09:45:01.655-05:00",
      "updated_at": "2019-12-31T09:45:01.767-05:00",
      "payment_method": {
        "id": 9,
        "name": "Braintree"
      },
      "source": {
        "id": 9,
        "payment_type": "CreditCard",
        "token": "4rptfz",
        "created_at": "2019-12-31T09:45:01.654-05:00",
        "cc_type": "Visa",
        "last_digits": "1881",
        "month": "12",
        "year": "2020"
      }
    }
  ],
  "shipments": [
    {
      "id": 15,
      "tracking": "U10000",
      "tracking_url": null,
      "number": "H85321167316",
      "cost": "100.0",
      "shipped_at": null,
      "state": "ready",
      "order_id": "M593982310",
      "stock_location_name": "NY Warehouse",
      "giftwrappable": false,
      "stock_location_id": 27,
      "giftwrap": null,
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
              "id": 11,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 24,
              "name": "ShippingCategory #23"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 67,
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
      "delivery_estimation": "Jan 02"
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
PATCH /api/checkouts/M038079937
Accept: application/json
X-Spree-Order-Token: XNMbRYlDnXMdqU-wqfobKg
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=13&order[payment_attributes][][source_attributes][nonce]=fake-apple-pay-visa-nonce&order[payment_attributes][][source_attributes][payment_type]=ApplePayCard&order[payment_attributes][][source_attributes][reusable]=true
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
ETag: W/&quot;25d1f2ff9c4aa9c5996c1e276cf4efc3&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: a511422e-e19b-4f0c-8ee6-082d2e7ed2dd
X-Runtime: 0.117126
Vary: Origin
Content-Length: 4929
200 OK
```


```json
{
  "id": 15,
  "number": "M038079937",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 61,
  "created_at": "2019-12-31T09:45:03.254-05:00",
  "updated_at": "2019-12-31T09:45:03.474-05:00",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "email60@example.com",
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
  "token": "XNMbRYlDnXMdqU-wqfobKg",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order&order=M038079937&bzip=10030&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [
    {
      "id": 13,
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
    "zipcode": "10030",
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
  "ship_address": {
    "id": 35,
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
      "id": 16,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 73,
      "vendor_id": 147,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 73,
        "name": "Product #42 - 6657",
        "sku": "SKU-72",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-42-6657",
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
        "product_id": 42,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [

      ],
      "vendor_name": "Vendor #147",
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
      "number": "H13318041826",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M038079937",
      "stock_location_name": "NY Warehouse",
      "giftwrappable": false,
      "stock_location_id": 30,
      "giftwrap": null,
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
              "id": 14,
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
          "variant_id": 73,
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
      "delivery_estimation": "Jan 02"
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
PATCH /api/checkouts/M246836534
Accept: application/json
X-Spree-Order-Token: Jp1-u4ac-SoJG_oVcBCgSQ
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=12&order[payment_attributes][][source_attributes][nonce]=fake-paypal-billing-agreement-nonce&order[payment_attributes][][source_attributes][payment_type]=PayPalAccount&order[payment_attributes][][source_attributes][reusable]=true
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
ETag: W/&quot;8840dbf6f1d24750fd0ba5b087cad667&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 1a60ab44-5f76-45a3-804f-903976bf9dfc
X-Runtime: 0.114668
Vary: Origin
Content-Length: 4929
200 OK
```


```json
{
  "id": 14,
  "number": "M246836534",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 60,
  "created_at": "2019-12-31T09:45:02.778-05:00",
  "updated_at": "2019-12-31T09:45:02.982-05:00",
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
  "token": "Jp1-u4ac-SoJG_oVcBCgSQ",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order&order=M246836534&bzip=10028&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [
    {
      "id": 12,
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
    "zipcode": "10028",
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
    "state": {
      "id": 27,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 27
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
    "zipcode": "10029",
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
    "state": {
      "id": 27,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 27
    }
  },
  "line_items": [
    {
      "id": 15,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 71,
      "vendor_id": 142,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 71,
        "name": "Product #41 - 9331",
        "sku": "SKU-70",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-41-9331",
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
      "vendor_name": "Vendor #142",
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
      "number": "H86305776822",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M246836534",
      "stock_location_name": "NY Warehouse",
      "giftwrappable": false,
      "stock_location_id": 29,
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
              "id": 13,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 26,
              "name": "ShippingCategory #25"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 71,
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
      "delivery_estimation": "Jan 02"
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
PATCH /api/checkouts/M767759632
Accept: application/json
X-Spree-Order-Token: RrRbiWKdtUuyDQB_sL1Fsg
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
ETag: W/&quot;6bbad0101c85147b64f23588667767c2&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: fded26ca-a353-41f5-988e-dae40d480a8e
X-Runtime: 0.124931
Vary: Origin
Content-Length: 4929
200 OK
```


```json
{
  "id": 16,
  "number": "M767759632",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 62,
  "created_at": "2019-12-31T09:45:03.764-05:00",
  "updated_at": "2019-12-31T09:45:03.988-05:00",
  "completed_at": null,
  "payment_total": "0.0",
  "shipment_state": null,
  "payment_state": null,
  "email": "email61@example.com",
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
  "token": "RrRbiWKdtUuyDQB_sL1Fsg",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order&order=M767759632&bzip=10032&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [
    {
      "id": 14,
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
    "zipcode": "10032",
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
    "id": 37,
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
      "id": 17,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 75,
      "vendor_id": 152,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 75,
        "name": "Product #43 - 6036",
        "sku": "SKU-74",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-43-6036",
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
      "gift_cards": [

      ],
      "vendor_name": "Vendor #152",
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
      "number": "H62341728165",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M767759632",
      "stock_location_name": "NY Warehouse",
      "giftwrappable": false,
      "stock_location_id": 31,
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
              "id": 15,
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
      "delivery_estimation": "Jan 02"
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
PATCH /api/checkouts/M449102605
Accept: application/json
X-Spree-Order-Token: _qXv23I18Fl8X16Wb25PVA
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=11&order[payment_attributes][][source_attributes][wallet_payment_source_id]=8
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
ETag: W/&quot;e0b5f26a8c7d361e8fa5bd3becdc5a85&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 0463434b-776b-4de8-a3b0-6270bbcc429d
X-Runtime: 0.118986
Vary: Origin
Content-Length: 4927
200 OK
```


```json
{
  "id": 13,
  "number": "M449102605",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "confirm",
  "adjustment_total": "0.0",
  "user_id": 59,
  "created_at": "2019-12-31T09:45:02.270-05:00",
  "updated_at": "2019-12-31T09:45:02.485-05:00",
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
  "display_item_total": "$10.00",
  "total_quantity": 1,
  "display_total": "$110.00",
  "display_ship_total": "$100.00",
  "display_tax_total": "$0.00",
  "token": "_qXv23I18Fl8X16Wb25PVA",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order&order=M449102605&bzip=10026&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [
    {
      "id": 11,
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
    "zipcode": "10026",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 26,
    "country_iso": "US",
    "state_id": 26,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 26,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 26,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 26
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
    "zipcode": "10027",
    "phone": "555-555-0199",
    "company": "Company",
    "alternative_phone": "555-555-0199",
    "country_id": 26,
    "country_iso": "US",
    "state_id": 26,
    "state_name": null,
    "state_text": "AL",
    "country": {
      "id": 26,
      "iso_name": "UNITED STATES",
      "iso": "US",
      "iso3": "USA",
      "name": "United States",
      "numcode": 840
    },
    "state": {
      "id": 26,
      "name": "Alabama",
      "abbr": "AL",
      "country_id": 26
    }
  },
  "line_items": [
    {
      "id": 14,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 69,
      "vendor_id": 137,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 69,
        "name": "Product #40 - 793",
        "sku": "SKU-68",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-40-793",
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
        "product_id": 40,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [

      ],
      "vendor_name": "Vendor #137",
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
      "number": "H12636213387",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M449102605",
      "stock_location_name": "NY Warehouse",
      "giftwrappable": false,
      "stock_location_id": 28,
      "giftwrap": null,
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
              "id": 12,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 25,
              "name": "ShippingCategory #24"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 69,
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
      "delivery_estimation": "Jan 02"
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
PUT /api/checkouts/M425419747
Accept: application/json
X-Spree-Order-Token: 1pnqeKjZqlGAZkdB4Whs5Q
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PUT /api/checkouts/:id`

#### Parameters


```json
order[ship_address_attributes][id]&order[ship_address_attributes][firstname]=John&order[ship_address_attributes][lastname]&order[ship_address_attributes][address1]=10+Lovely+Street&order[ship_address_attributes][address2]=Northwest&order[ship_address_attributes][city]=Herndon&order[ship_address_attributes][zipcode]=10023&order[ship_address_attributes][phone]=555-555-0199&order[ship_address_attributes][state_name]&order[ship_address_attributes][alternative_phone]=555-555-0199&order[ship_address_attributes][company]=Company&order[ship_address_attributes][state_id]=24&order[ship_address_attributes][country_id]=24&order[ship_address_attributes][created_at]&order[ship_address_attributes][updated_at]&order[use_billing]=true&hold_state=true
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
ETag: W/&quot;2aac04f121c664ba80b16e385e7b8185&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: e98e96d4-431a-44a6-83c9-b9b1d31a8e6e
X-Runtime: 0.124661
Vary: Origin
Content-Length: 4836
200 OK
```


```json
{
  "id": 11,
  "number": "M425419747",
  "item_total": "10.0",
  "total": "110.0",
  "ship_total": "100.0",
  "state": "cart",
  "adjustment_total": "0.0",
  "user_id": 57,
  "created_at": "2019-12-31T09:45:01.201-05:00",
  "updated_at": "2019-12-31T09:45:01.276-05:00",
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
  "token": "1pnqeKjZqlGAZkdB4Whs5Q",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order&order=M425419747&bzip=10023&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [

  ],
  "bill_address": {
    "id": 27,
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
    "id": 27,
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
      "id": 12,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 65,
      "vendor_id": 127,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 65,
        "name": "Product #38 - 1935",
        "sku": "SKU-64",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-38-1935",
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
        "product_id": 38,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [

      ],
      "vendor_name": "Vendor #127",
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
      "tracking": "U10000",
      "tracking_url": null,
      "number": "H22848116083",
      "cost": "100.0",
      "shipped_at": null,
      "state": "pending",
      "order_id": "M425419747",
      "stock_location_name": "NY Warehouse",
      "giftwrappable": false,
      "stock_location_id": 26,
      "giftwrap": null,
      "shipping_rates": [
        {
          "id": 14,
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
        "id": 14,
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
              "id": 10,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 23,
              "name": "ShippingCategory #22"
            }
          ]
        }
      ],
      "manifest": [
        {
          "variant_id": 65,
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
      "delivery_estimation": "Jan 02"
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
POST /api/shipments/H82260646524/giftwrap
Accept: application/json
X-Spree-Order-Token: dpoCy5KKBJkPwfUOswuWpw
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/shipments/:shipment_number/giftwrap`

#### Parameters


```json
order_number=M540470707
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
X-Request-Id: 9de5c87a-860e-4b80-9de9-c2961e3a1f8e
X-Runtime: 0.032458
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
DELETE /api/shipments/H07582038815/giftwrap
Accept: application/json
X-Spree-Order-Token: BfA7ec_5Ty7DHANr2zxm-Q
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`DELETE /api/shipments/:shipment_number/giftwrap`

#### Parameters


```json
order_number=M741871572
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
X-Request-Id: e207571e-f823-403d-8455-297f0d3e7aa8
X-Runtime: 0.038207
Vary: Origin
204 No Content
```




# LineItem

Representation of a single cart item for a specific variant with price of vendor

## Creating a line item


### Request

#### Endpoint

```plaintext
POST /api/orders/M248000963/line_items
Accept: application/json
X-Spree-Order-Token: qgO2AsVHfMiT7SbbLBd7Jg
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/:order_number/line_items`

#### Parameters


```json
line_item[variant_id]=35&line_item[options][vendor_id]=80
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
ETag: W/&quot;db4d8ba52a4b505bf5968f35be1d714f&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 4512a6db-2733-4265-aab3-add5016e4f02
X-Runtime: 0.082622
Vary: Origin
Content-Length: 935
201 Created
```


```json
{
  "id": 10,
  "quantity": 1,
  "price": "19.99",
  "variant_id": 35,
  "vendor_id": 80,
  "single_display_amount": "$19.99",
  "display_amount": "$19.99",
  "total": "19.99",
  "on_sale": false,
  "final_sale": false,
  "backordered": null,
  "promotionable": true,
  "variant": {
    "id": 35,
    "name": "Product #23 - 720",
    "sku": "SKU-34",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": false,
    "slug": "product-23-720",
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
    "product_id": 23,
    "lead_time": 2,
    "brand": null,
    "brand_slug": null,
    "brand_description": null
  },
  "monogram": null,
  "gift_cards": [

  ],
  "vendor_name": "Vendor #80",
  "country_iso": null,
  "adjustments": [

  ]
}
```



## Creating a line item gift card


### Request

#### Endpoint

```plaintext
POST /api/orders/M651410755/line_items
Accept: application/json
X-Spree-Order-Token: OAAqdXhi65VSXEVaDQZL-w
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/:order_number/line_items`

#### Parameters


```json
line_item[variant_id]=27&line_item[options][vendor_id]=66&line_item[options][gift_card_details][recipient_name]=Recipient+John&line_item[options][gift_card_details][recipient_email]=recipient%40email.com&line_item[options][gift_card_details][purchaser_name]=Purchaser+Bob&line_item[options][gift_card_details][gift_message]=Surprise&line_item[options][gift_card_details][send_email_at]=2019-12-31+09%3A44%3A56+-0500
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
ETag: W/&quot;1b5948248b221906f7db6100af844d46&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: acdd1dfa-400a-431f-935a-431dbbac4067
X-Runtime: 0.174128
Vary: Origin
Content-Length: 1068
201 Created
```


```json
{
  "id": 7,
  "quantity": 1,
  "price": "19.99",
  "variant_id": 27,
  "vendor_id": 66,
  "single_display_amount": "$19.99",
  "display_amount": "$19.99",
  "total": "19.99",
  "on_sale": false,
  "final_sale": false,
  "backordered": null,
  "promotionable": true,
  "variant": {
    "id": 27,
    "name": "Product #18 - 4116",
    "sku": "SKU-27",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": false,
    "slug": "product-18-4116",
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
    "product_id": 18,
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
      "send_email_at": "2019-12-31T00:00:00.000-05:00"
    }
  ],
  "vendor_name": "Vendor #66",
  "country_iso": null,
  "adjustments": [

  ]
}
```



## Deleting a line item


### Request

#### Endpoint

```plaintext
DELETE /api/orders/M608506475/line_items/8
Accept: application/json
X-Spree-Order-Token: wplF4Lu_gfB8Y-8j99-z6A
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
X-Request-Id: 0d44361d-bb17-4cda-8da3-1890c44f9345
X-Runtime: 0.064682
Vary: Origin
204 No Content
```




## Updating a line item


### Request

#### Endpoint

```plaintext
PUT /api/orders/M595356945/line_items/11
Accept: application/json
X-Spree-Order-Token: She181nqel2Jp9gYLdeBmQ
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
ETag: W/&quot;87a29c970b3200c2168429fbc9536348&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 53954866-3c07-4aa8-8c98-17e2b8c20cff
X-Runtime: 0.099745
Vary: Origin
Content-Length: 934
200 OK
```


```json
{
  "id": 11,
  "quantity": 2,
  "price": "10.0",
  "variant_id": 37,
  "vendor_id": 85,
  "single_display_amount": "$10.00",
  "display_amount": "$20.00",
  "total": "20.0",
  "on_sale": false,
  "final_sale": false,
  "backordered": null,
  "promotionable": true,
  "variant": {
    "id": 37,
    "name": "Product #24 - 8418",
    "sku": "SKU-36",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": false,
    "slug": "product-24-8418",
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
  "vendor_name": "Vendor #85",
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
Authorizat IO N: Bearer fddff0f8e66f49f9732aae3064bdc97ec9dd7ecbc6902294
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/minis`

#### Parameters


```json
mini[name]=Winny&mini[user_id]=10&mini[birth_year]=2019&mini[birth_month]=1&mini[birth_day]=1
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
ETag: W/&quot;576ddff5f80a8fd195953c583bf2f995&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 380818aa-c972-4789-9c4c-4701fa2c4988
X-Runtime: 0.011178
Vary: Origin
Content-Length: 162
201 Created
```


```json
{
  "id": 2,
  "user_id": 10,
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
DELETE /api/minis/8
Accept: application/json
Authorizat IO N: Bearer df20bb8c9544c4ee71602879dcb85e7e0dea67be49b4f7a7
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
X-Request-Id: 55902725-a9b3-4efa-b550-ff64ddb2b595
X-Runtime: 0.006405
Vary: Origin
204 No Content
```




## Get a single mini


### Request

#### Endpoint

```plaintext
GET /api/minis/1
Accept: application/json
Authorizat IO N: Bearer fbc62493f5b6219ceaf13e2b0bea300a44a9d68506dda7c9
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
ETag: W/&quot;9fcce7b4713b2ed36ca6731e82a7a533&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 9b4df80a-a101-46f1-947e-99bb76792ae9
X-Runtime: 0.036456
Vary: Origin
Content-Length: 166
200 OK
```


```json
{
  "id": 1,
  "user_id": 9,
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
Authorizat IO N: Bearer 26efc6aa57a37ce44e271ed6b6ce4dc5ab02dd3a8f068532
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
ETag: W/&quot;5e142e82ebc5607c63eac44bcfdf3992&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 90346aee-33b3-4b87-9553-9f23b8d107df
X-Runtime: 0.028119
Vary: Origin
Content-Length: 1769
200 OK
```


```json
{
  "minis": [
    {
      "id": 18,
      "user_id": 23,
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
      "user_id": 22,
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
      "id": 15,
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
      "id": 14,
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
      "id": 13,
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
      "id": 12,
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
      "id": 11,
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
      "id": 10,
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
      "id": 9,
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
Authorizat IO N: Bearer eb8dc7599bddf008024fc2132880cc668b53900cabfb75ee
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
ETag: W/&quot;b9a90748870a7219de50dcdf4e15235d&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: db30d5a2-96a9-40a4-961f-92d1ca875836
X-Runtime: 0.015072
Vary: Origin
Content-Length: 414
200 OK
```


```json
{
  "minis": [
    {
      "id": 7,
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
    },
    {
      "id": 6,
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
Authorizat IO N: Bearer 4dee9db840361df18239ab58f2105e7125429f3809b157ad
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
ETag: W/&quot;555d470a96e0606e245ed974c5cab88a&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 34ce0de1-61f7-4e93-9a55-6e747ad29c23
X-Runtime: 0.010319
Vary: Origin
Content-Length: 169
200 OK
```


```json
{
  "id": 19,
  "user_id": 25,
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
user_id&order_token&line_item[variant_id]=99&line_item[quantity]=1&line_item[vendor_id]=207&line_item[gift_card_details_attributes][recipient_name]=Recipient+John&line_item[gift_card_details_attributes][recipient_email]=recipient%40email.com&line_item[gift_card_details_attributes][purchaser_name]=Purchaser+Bob&line_item[gift_card_details_attributes][gift_message]=Surprise&line_item[gift_card_details_attributes][send_email_at]=2019-12-31
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
ETag: W/&quot;2ba20bb6c1086ffe2d3d5c16020ee97d&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 5b47baa8-f66c-4e99-be4b-fc418403b202
X-Runtime: 0.117259
Vary: Origin
Content-Length: 2815
200 OK
```


```json
{
  "id": 24,
  "number": "M199571389",
  "item_total": "19.99",
  "total": "19.99",
  "ship_total": "0.0",
  "state": "cart",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2019-12-31T09:45:08.036-05:00",
  "updated_at": "2019-12-31T09:45:08.075-05:00",
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
  "token": "CkvtwG_4GdfhPLgquPhoHA",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order&order=M199571389&bzip=&init=true",
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
      "variant_id": 99,
      "vendor_id": 207,
      "single_display_amount": "$19.99",
      "display_amount": "$19.99",
      "total": "19.99",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 99,
        "name": "Product #54 - 133",
        "sku": "SKU-99",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-54-133",
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
          "send_email_at": "2019-12-31T00:00:00.000-05:00"
        }
      ],
      "vendor_name": "Vendor #207",
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
user_id&order_token&line_item[variant_id]=95&line_item[quantity]=2&line_item[vendor_id]=196
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
ETag: W/&quot;60cff447c707d328d02e5ad0caf2dd86&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: b519d73d-b93c-471e-b867-49d0e5a1b371
X-Runtime: 0.101527
Vary: Origin
Content-Length: 2633
200 OK
```


```json
{
  "id": 23,
  "number": "M910285151",
  "item_total": "39.98",
  "total": "39.98",
  "ship_total": "0.0",
  "state": "cart",
  "adjustment_total": "0.0",
  "user_id": null,
  "created_at": "2019-12-31T09:45:07.652-05:00",
  "updated_at": "2019-12-31T09:45:07.691-05:00",
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
  "token": "ls4QJoLONADR5_403LC-5Q",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order&order=M910285151&bzip=&init=true",
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
      "variant_id": 95,
      "vendor_id": 196,
      "single_display_amount": "$19.99",
      "display_amount": "$39.98",
      "total": "39.98",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 95,
        "name": "Product #53 - 521",
        "sku": "SKU-94",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-53-521",
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
        "product_id": 53,
        "lead_time": 2,
        "brand": null,
        "brand_slug": null,
        "brand_description": null
      },
      "monogram": null,
      "gift_cards": [

      ],
      "vendor_name": "Vendor #196",
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
Authorizat IO N: Bearer 335a0fec0552afeae4be4f2d356f6d9b4c146f83f40e57bd
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
ETag: W/&quot;6e65410639f51bf48fb0cb74fa32a6b0&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 07ba7c69-1ef0-4164-8135-e1de4774798e
X-Runtime: 0.014006
Vary: Origin
Content-Length: 310
200 OK
```


```json
{
  "orders": [
    {
      "number": "M116062570",
      "completed_at": "2019-12-31T09:45:08.562-05:00",
      "total": "120.0",
      "state": "Complete",
      "shipment_state": "shipped",
      "shipments": [
        {
          "number": "H08301745177",
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
GET /api/orders/M924416077
Accept: application/json
Authorizat IO N: Bearer d05462acc90f7f3ecb85c88f70f86718d0cddbba8be50cae
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
ETag: W/&quot;79c64e208d68f67f27f6a1636a9da7b3&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 45d78a40-7ffd-4524-a4c2-2cbd566b6a84
X-Runtime: 0.145257
Vary: Origin
Content-Length: 10084
200 OK
```


```json
{
  "id": 22,
  "number": "M924416077",
  "item_total": "20.0",
  "total": "120.0",
  "ship_total": "100.0",
  "state": "complete",
  "adjustment_total": "0.0",
  "user_id": 75,
  "created_at": "2019-12-31T09:45:07.007-05:00",
  "updated_at": "2019-12-31T09:45:07.228-05:00",
  "completed_at": "2019-12-31T09:45:07.078-05:00",
  "payment_total": "120.0",
  "shipment_state": "shipped",
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
  "token": "G9frNTBqZ1_QMtI7Ou_tWw",
  "checkout_steps": [
    "address",
    "delivery",
    "payment",
    "confirm",
    "complete"
  ],
  "eligible_for_return": null,
  "narvar_return_url": "http://localhost:4000/order&order=M924416077&bzip=10044&init=true",
  "free_shipping_threshold": null,
  "payment_methods": [
    {
      "id": 25,
      "name": "Credit Card",
      "partial_name": "gateway",
      "method_type": "gateway"
    },
    {
      "id": 26,
      "name": "Credit Card",
      "partial_name": "gateway",
      "method_type": "gateway"
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
    "zipcode": "10044",
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
    "id": 49,
    "firstname": "John",
    "lastname": null,
    "full_name": "John",
    "address1": "A Different Road",
    "address2": "Northwest",
    "city": "Herndon",
    "zipcode": "10045",
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
      "vendor_id": 189,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 89,
        "name": "Product #50 - 3808",
        "sku": "SKU-88",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-50-3808",
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
      "vendor_name": "Vendor #189",
      "country_iso": "US",
      "adjustments": [
        {
          "id": 19,
          "source_type": "Spree::TaxRate",
          "source_id": 3,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 24,
          "amount": "2.0",
          "label": "VAT 5%",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-12-31T09:45:07.204-05:00",
          "updated_at": "2019-12-31T09:45:07.213-05:00",
          "display_amount": "$2.00"
        },
        {
          "id": 13,
          "source_type": "Spree::PromotionAction",
          "source_id": 3,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 24,
          "amount": "5.0",
          "label": "foo",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-12-31T09:45:07.154-05:00",
          "updated_at": "2019-12-31T09:45:07.154-05:00",
          "display_amount": "$5.00"
        },
        {
          "id": 12,
          "source_type": "Spree::PromotionAction",
          "source_id": 3,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 24,
          "amount": "5.0",
          "label": "foo",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-12-31T09:45:07.144-05:00",
          "updated_at": "2019-12-31T09:45:07.144-05:00",
          "display_amount": "$5.00"
        }
      ]
    },
    {
      "id": 25,
      "quantity": 1,
      "price": "10.0",
      "variant_id": 91,
      "vendor_id": 189,
      "single_display_amount": "$10.00",
      "display_amount": "$10.00",
      "total": "10.0",
      "on_sale": false,
      "final_sale": false,
      "backordered": null,
      "promotionable": true,
      "variant": {
        "id": 91,
        "name": "Product #51 - 2795",
        "sku": "SKU-90",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-51-2795",
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
      "vendor_name": "Vendor #189",
      "country_iso": "US",
      "adjustments": [
        {
          "id": 20,
          "source_type": "Spree::TaxRate",
          "source_id": 4,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 25,
          "amount": "1.5",
          "label": "VAT 5%",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-12-31T09:45:07.226-05:00",
          "updated_at": "2019-12-31T09:45:07.235-05:00",
          "display_amount": "$1.50"
        },
        {
          "id": 14,
          "source_type": "Spree::PromotionAction",
          "source_id": 3,
          "adjustable_type": "Spree::LineItem",
          "adjustable_id": 25,
          "amount": "5.0",
          "label": "bar",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-12-31T09:45:07.164-05:00",
          "updated_at": "2019-12-31T09:45:07.164-05:00",
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
      "payment_method_id": 25,
      "state": "completed",
      "avs_response": null,
      "created_at": "2019-12-31T09:45:07.091-05:00",
      "updated_at": "2019-12-31T09:45:07.091-05:00",
      "payment_method": {
        "id": 25,
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
      "id": 29,
      "tracking": "U10000",
      "tracking_url": null,
      "number": "H33030156006",
      "cost": "100.0",
      "shipped_at": "2019-12-31T09:45:07.113-05:00",
      "state": "shipped",
      "order_id": "M924416077",
      "stock_location_name": "NY Warehouse",
      "giftwrappable": false,
      "stock_location_id": 41,
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
              "id": 23,
              "name": "GlobalZone",
              "description": null
            }
          ],
          "shipping_categories": [
            {
              "id": 34,
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
            "shipped": 1
          }
        },
        {
          "variant_id": 91,
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
          "adjustable_id": 29,
          "amount": "-10.0",
          "label": "Shipping",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-12-31T09:45:07.181-05:00",
          "updated_at": "2019-12-31T09:45:07.181-05:00",
          "display_amount": "-$10.00"
        },
        {
          "id": 15,
          "source_type": "Spree::PromotionAction",
          "source_id": 3,
          "adjustable_type": "Spree::Shipment",
          "adjustable_id": 29,
          "amount": "-9.99",
          "label": "Shipping",
          "promotion_code_id": null,
          "finalized": false,
          "eligible": true,
          "created_at": "2019-12-31T09:45:07.174-05:00",
          "updated_at": "2019-12-31T09:45:07.174-05:00",
          "display_amount": "-$9.99"
        }
      ],
      "stock_location_address": "NY Warehouse, Washington, AL",
      "country_iso": "US",
      "international_shipping": false,
      "delivery_estimation": "Jan 02"
    }
  ],
  "adjustments": [
    {
      "id": 17,
      "source_type": "Spree::Promotion",
      "source_id": 3,
      "adjustable_type": "Spree::Order",
      "adjustable_id": 22,
      "amount": "20.0",
      "label": "adj1",
      "promotion_code_id": null,
      "finalized": false,
      "eligible": true,
      "created_at": "2019-12-31T09:45:07.186-05:00",
      "updated_at": "2019-12-31T09:45:07.186-05:00",
      "display_amount": "$20.00"
    },
    {
      "id": 18,
      "source_type": "Spree::Promotion",
      "source_id": 3,
      "adjustable_type": "Spree::Order",
      "adjustable_id": 22,
      "amount": "30.0",
      "label": "adj2",
      "promotion_code_id": null,
      "finalized": false,
      "eligible": true,
      "created_at": "2019-12-31T09:45:07.189-05:00",
      "updated_at": "2019-12-31T09:45:07.189-05:00",
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
        "id": 48,
        "firstname": "John",
        "lastname": null,
        "full_name": "John",
        "address1": "PO Box 1337",
        "address2": "Northwest",
        "city": "Herndon",
        "zipcode": "10044",
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
GET /api/orders/M509987149
Accept: application/json
Authorizat IO N: f74b0ab49ac05e832ea9893a67205ca56eec1cbcf337d7f7
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
X-Request-Id: 2f552bd6-5adf-4c31-82ad-7ea64789fe7a
X-Runtime: 0.017140
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
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/users/password`

#### Parameters


```json
user[email]=email70%40example.com
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
X-Request-Id: e0e3e416-e724-47e1-90d8-491c4db44c0b
X-Runtime: 0.002853
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
user[email]=email68%40example.com&user[password]=secret
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
Authorization: Bearer d2b243b42d51196f2dd7f1cf2c87c3b781e95db277223169
ETag: W/&quot;a5dd9039d02216fbc8939a09ebf795aa&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: b71d26c9-0294-4ff1-a0f9-4b2e673b144a
X-Runtime: 0.008382
Vary: Origin
Content-Length: 562
200 OK
```


```json
{
  "id": 69,
  "email": "email68@example.com",
  "persistence_token": null,
  "perishable_token": null,
  "last_request_at": null,
  "login": "email68@example.com",
  "ship_address_id": null,
  "bill_address_id": null,
  "created_at": "2019-12-31T09:45:05.939-05:00",
  "updated_at": "2019-12-31T09:45:05.941-05:00",
  "spree_api_key": "d2b243b42d51196f2dd7f1cf2c87c3b781e95db277223169",
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
X-Request-Id: c1f3ca59-41b7-45c5-ae2e-2fcaf1a017c3
X-Runtime: 0.023317
Vary: Origin
204 No Content
```




# Products

get products by taxon

## Fetch a single product by id


### Request

#### Endpoint

```plaintext
GET /api/products/product-10-6232
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
Date: Tue, 31 Dec 2019 14:44:55 GMT
Surrogate-Control: max-age=900
Surrogate-Key: product_id=1
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;1a3dad9c903f9acb2b605a8741322f5f&quot;
X-Request-Id: 4618fc90-e9ae-4161-a1ff-01a18af9cf84
X-Runtime: 0.063963
Vary: Origin
Content-Length: 1512
200 OK
```


```json
{
  "id": 10,
  "name": "Product #10 - 6232",
  "description": "As seen on TV!",
  "available_on": "2018-12-31T09:44:55.040-05:00",
  "slug": "product-10-6232",
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
      "created_at": "2019-12-31T09:44:54.978-05:00",
      "url": "/clothing",
      "position": 1
    },
    {
      "id": 9,
      "name": "Girl",
      "taxonomy_id": 3,
      "created_at": "2019-12-31T09:44:54.999-05:00",
      "url": "/clothing/girl",
      "position": 2
    },
    {
      "id": 10,
      "name": "Dresses",
      "taxonomy_id": 3,
      "created_at": "2019-12-31T09:44:55.019-05:00",
      "url": "/clothing/girl/dresses",
      "position": 3
    }
  ],
  "has_variants": false,
  "master": {
    "id": 15,
    "name": "Product #10 - 6232",
    "sku": "SKU-15",
    "weight": "0.0",
    "height": null,
    "width": null,
    "depth": null,
    "is_master": true,
    "slug": "product-10-6232",
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
Date: Tue, 31 Dec 2019 14:44:55 GMT
Surrogate-Control: max-age=900
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;2364682ba9b5dedecb758397cb635b45&quot;
X-Request-Id: 0f2a3a81-349e-43fc-8946-c6b6ad64fce6
X-Runtime: 0.037400
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
      "id": 11,
      "name": "Product #11 - 9865",
      "description": "As seen on TV!",
      "available_on": "2018-12-31T09:44:55.231-05:00",
      "slug": "product-11-9865",
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
        "id": 16,
        "name": "Product #11 - 9865",
        "sku": "SKU-16",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-11-9865",
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
Date: Tue, 31 Dec 2019 14:44:55 GMT
Surrogate-Control: max-age=900
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;fd7f50c9b3f0bfa6f277ee0e17242886&quot;
X-Request-Id: b88f7d05-97f2-403f-8e63-866bddf22200
X-Runtime: 0.023376
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
      "id": 16,
      "name": "Product #16 - 8568",
      "slug": "product-16-8568",
      "master_id": 21,
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
GET /api/products?ids=13%2C14%2C15
Host: example.org
Cookie: 
```

`GET /api/products`

#### Parameters


```json
ids: 13,14,15
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
Date: Tue, 31 Dec 2019 14:44:55 GMT
Surrogate-Control: max-age=900
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;42c470c623ea4a07de3a155238522e53&quot;
X-Request-Id: 5e1b1bbb-aa5f-4a20-914c-c168d0a95157
X-Runtime: 0.079760
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
      "id": 13,
      "name": "Product #13 - 2029",
      "description": "As seen on TV!",
      "available_on": "2018-12-31T09:44:55.433-05:00",
      "slug": "product-13-2029",
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
        "id": 18,
        "name": "Product #13 - 2029",
        "sku": "SKU-18",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-13-2029",
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
      "id": 14,
      "name": "Product #14 - 3392",
      "description": "As seen on TV!",
      "available_on": "2018-12-31T09:44:55.492-05:00",
      "slug": "product-14-3392",
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
        "id": 19,
        "name": "Product #14 - 3392",
        "sku": "SKU-19",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-14-3392",
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
      "id": 15,
      "name": "Product #15 - 3814",
      "description": "As seen on TV!",
      "available_on": "2018-12-31T09:44:55.561-05:00",
      "slug": "product-15-3814",
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
        "id": 20,
        "name": "Product #15 - 3814",
        "sku": "SKU-20",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-15-3814",
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
ETag: W/&quot;c7a00c0feeb3d05eb2efb67940810abd&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 05483a3e-50f9-470f-9a52-7d9722d340fb
X-Runtime: 0.036626
Vary: Origin
Content-Length: 1216
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
      "id": 9,
      "name": "Product #9 - 3335",
      "description": "As seen on TV!",
      "available_on": "2018-12-31T09:44:54.830-05:00",
      "slug": "product-9-3335",
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
        "id": 14,
        "name": "Product #9 - 3335",
        "sku": "SKU-14",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-9-3335",
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
ETag: W/&quot;d6c5547ec72c11158c1dbf31f408147f&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: eba2ba35-4a01-467f-931f-23615af71f63
X-Runtime: 0.063795
Vary: Origin
Content-Length: 1216
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
      "id": 7,
      "name": "Product #7 - 3555",
      "description": "As seen on TV!",
      "available_on": "2018-12-31T09:44:54.528-05:00",
      "slug": "product-7-3555",
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
        "id": 12,
        "name": "Product #7 - 3555",
        "sku": "SKU-12",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": true,
        "slug": "product-7-3555",
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
Authorizat IO N: Bearer d145c8f948ddad139d248fb5b792d44dc9db82d120188be5
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
X-Request-Id: c14472a8-ed15-43f1-9e68-1035f73874b5
X-Runtime: 0.031175
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
X-Request-Id: 33d9594d-046b-44d0-8a21-dd3452408a41
X-Runtime: 0.020384
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
GET /api/recently_viewed?recently_viewed[session_id]=v18lkymbvmf5n07g8wiqahp1cei7xyobn4djwnrmtpgk0stsuaaif3rfkptm6ik879e0jon4txoplizx6f7d4nsh0i6tyh52lqg1jw22eisbim2bpf6sz5pelscm6t2uxa2o87ssi6428mgl1ghjhzaf4alf407st2w6hzu2lp4l80odxs8uw8bv818fl6ybxmh5vvd6dhauzvoviyjot7rulcd7sh2gzs285tn0khoj7f0m1gztp5nbo9umr8o&amp;recently_viewed[user_id]=11704
Accept: application/json
Host: example.org
Cookie: 
```

`GET /api/recently_viewed`

#### Parameters


```json
recently_viewed: {&quot;session_id&quot;=&gt;&quot;v18lkymbvmf5n07g8wiqahp1cei7xyobn4djwnrmtpgk0stsuaaif3rfkptm6ik879e0jon4txoplizx6f7d4nsh0i6tyh52lqg1jw22eisbim2bpf6sz5pelscm6t2uxa2o87ssi6428mgl1ghjhzaf4alf407st2w6hzu2lp4l80odxs8uw8bv818fl6ybxmh5vvd6dhauzvoviyjot7rulcd7sh2gzs285tn0khoj7f0m1gztp5nbo9umr8o&quot;, &quot;user_id&quot;=&gt;&quot;11704&quot;}
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
ETag: W/&quot;42ae3794040f0635748c730a4599cd69&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 538660db-53cd-4c9a-948e-6dfeb86ff5f1
X-Runtime: 0.005923
Vary: Origin
Content-Length: 119
200 OK
```


```json
[
  {
    "at": "2019-12-31T09:45:11.719-05:00",
    "variant_id": "var1"
  },
  {
    "at": "2019-12-31T09:50:11.719-05:00",
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
recently_viewed[session_id]=nmjhpulg9b8m0zs0ptapwhgzqv40f7j69aqsk0sfgvfezc0vfp2qh3p2aipy1h8cx4q26skaiu9egv85qcp76sc810tbeofz5wj92sa25v8ywojhtai5dhazm5un9vq2jqenvk0gt7cs31dpyt69x4vbahmamoa6d3nhtw4wtjxtnyiokgzyi2jashvs6vcfpwsfbalr0511e8d0bmriz4fyn9fqdbblyhp0cj8xle11k731tmjffntc04o1jvk&recently_viewed[user_id]=46757&recently_viewed[variant_id]=foo
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
X-Request-Id: d3061869-0861-472a-9abd-5f7d22bcc135
X-Runtime: 0.025001
Vary: Origin
204 No Content
```




# Return Authorizations

Get a single user return authorziation

## Can get another user&#39;s return authorization


### Request

#### Endpoint

```plaintext
GET /api/returns/RA226340103
Authorizat IO N: Bearer f0df1b7b2183b49def4f02d782771b00c0253c2ee097f225
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
ETag: W/&quot;31223079951362989f8557a7a0997e21&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 1de298d2-efb7-4e35-8abf-3ccf79c241bc
X-Runtime: 0.056979
Vary: Origin
Content-Length: 2926
200 OK
```


```json
{
  "id": 3,
  "number": "RA226340103",
  "state": "authorized",
  "order_id": 19,
  "memo": "Items were broken",
  "created_at": "2019-12-31T09:45:05.409-05:00",
  "updated_at": "2019-12-31T09:45:05.409-05:00",
  "amount": "10.0",
  "reason": {
    "id": 5,
    "name": "Defect #5",
    "active": true,
    "mutable": true,
    "created_at": "2019-12-31T09:45:05.404-05:00",
    "updated_at": "2019-12-31T09:45:05.404-05:00",
    "mirakl_code": null
  },
  "order": {
    "id": 19,
    "number": "M673947079",
    "item_total": "10.0",
    "total": "110.0",
    "state": "complete",
    "adjustment_total": "0.0",
    "user_id": 66,
    "completed_at": "2019-12-31T09:45:05.305-05:00",
    "bill_address_id": 42,
    "ship_address_id": 43,
    "payment_total": "110.0",
    "shipment_state": "shipped",
    "payment_state": "paid",
    "email": "email65@example.com",
    "special_instructions": null,
    "created_at": "2019-12-31T09:45:05.201-05:00",
    "updated_at": "2019-12-31T09:45:05.383-05:00",
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
    "guest_token": "U4AAMg_iV1vHwjtrTKXSCQ",
    "canceled_at": null,
    "canceler_id": null,
    "store_id": 19,
    "approver_name": null,
    "frontend_viewable": true,
    "is_gift": false,
    "gift_email": null,
    "gift_message": null,
    "gift_card_total": "0.0"
  },
  "ship_address": {
    "id": 43,
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
  "bill_address": {
    "id": 42,
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
  "return_items": [
    {
      "name": "Product #46 - 8482",
      "brand": null,
      "brand_slug": null,
      "image": null,
      "product_slug": "product-46-8482",
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
        "id": 3,
        "month": "12",
        "year": "2020",
        "cc_type": null,
        "last_digits": "1111",
        "name": "Spree Commerce",
        "gateway_customer_profile_id": "BGS-400250",
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
Authorizat IO N: Bearer 6ff27c216d12b76ad93efcf4a22f6fc997e185532f85db7c
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
ETag: W/&quot;036488a8c8d2c925b836ea04ca83904b&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 3f122ba1-884b-4678-94bd-977995a71dea
X-Runtime: 0.008383
Vary: Origin
Content-Length: 169
200 OK
```


```json
{
  "return_authorizations": [
    {
      "number": "RA636036212",
      "created_at": "2019-12-31T09:45:05.907-05:00",
      "return_amount": "10.0",
      "order_number": "M929435692",
      "state": "authorized"
    }
  ]
}
```



## returns a 200


### Request

#### Endpoint

```plaintext
GET /api/returns/RA166345312
Authorizat IO N: Bearer b82b23ae77365c3a870ede1b31576825605b4d41bb377a9c
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
ETag: W/&quot;78e6fd268723ca6b6d487688922c2e4e&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: e86d0d64-359f-44cd-93db-541c1de01615
X-Runtime: 0.054079
Vary: Origin
Content-Length: 2849
200 OK
```


```json
{
  "id": 1,
  "number": "RA166345312",
  "state": "authorized",
  "order_id": 17,
  "memo": "Items were broken",
  "created_at": "2019-12-31T09:45:04.494-05:00",
  "updated_at": "2019-12-31T09:45:04.494-05:00",
  "amount": "10.0",
  "reason": {
    "id": 1,
    "name": "Defect #1",
    "active": true,
    "mutable": true,
    "created_at": "2019-12-31T09:45:04.485-05:00",
    "updated_at": "2019-12-31T09:45:04.485-05:00",
    "mirakl_code": null
  },
  "order": {
    "id": 17,
    "number": "M626017397",
    "item_total": "10.0",
    "total": "110.0",
    "state": "complete",
    "adjustment_total": "0.0",
    "user_id": 63,
    "completed_at": "2019-12-31T09:45:04.339-05:00",
    "bill_address_id": 38,
    "ship_address_id": 39,
    "payment_total": "110.0",
    "shipment_state": "shipped",
    "payment_state": "paid",
    "email": "email62@example.com",
    "special_instructions": null,
    "created_at": "2019-12-31T09:45:04.276-05:00",
    "updated_at": "2019-12-31T09:45:04.447-05:00",
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
    "guest_token": "62e3Xk9snJNiZFSjljK9Ug",
    "canceled_at": null,
    "canceler_id": null,
    "store_id": 17,
    "approver_name": null,
    "frontend_viewable": true,
    "is_gift": false,
    "gift_email": null,
    "gift_message": null,
    "gift_card_total": "0.0"
  },
  "ship_address": {
    "id": 39,
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
  "bill_address": {
    "id": 38,
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
  "return_items": [
    {
      "name": "Product #44 - 5022",
      "brand": null,
      "brand_slug": null,
      "image": null,
      "product_slug": "product-44-5022",
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
GET /api/returns/RA363246182
Authorizat IO N: Bearer fef2d813ae9c7d1ec7a4f5b91cc2f51627e7eed26759f041
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
X-Request-Id: e649965c-d3ec-4cdb-bafc-d757a1fbbc4e
X-Runtime: 0.007028
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
stock_request[email]=isobel_nikolaus%40stark.co.uk&stock_request[variant_id]=61
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
X-Request-Id: 6120529a-c8f4-40a3-bff4-2a148f6e6cc6
X-Runtime: 0.004387
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
stock_request[email]=foo&stock_request[variant_id]=59
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
X-Request-Id: 1613698c-3075-4dc9-a0ca-ee6a7dc82cb2
X-Runtime: 0.031422
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
stock_request[email]=telma.collier%40ankunding.info&stock_request[variant_id]=63
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
X-Request-Id: 40a7f600-edb8-4ab9-8c34-8e6cc1c64b3f
X-Runtime: 0.003995
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
Authorizat IO N: Bearer 70d1515a5e56791e15ec35a2b7b9546db4c6de564088a965
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
ETag: W/&quot;e9276ae297e58ee136fa857f6c6592ba&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: d8e21516-ca39-4c78-946c-ceaa76e83d81
X-Runtime: 0.035046
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
      "created_at": "2019-12-31T09:44:57.754-05:00"
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

Update a subscriber. Users can update their own subscriber, admins can update minis for others.

## Create a subscriber


### Request

#### Endpoint

```plaintext
POST /api/subscribers
Accept: application/json
Authorizat IO N: Bearer 801bf943d9edf1684bc8232cdc60eefa0ae2e19dd6981bce
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/subscribers`

#### Parameters


```json
subscriber[email]=suzette%40mills.biz&subscriber[user_id]=81&subscriber[first_name]=Laurena&subscriber[last_name]=Schultz&subscriber[status]=subscribed
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
ETag: W/&quot;7778397417ad4fa2da41926f53d86fd6&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 3e727b75-7c8d-4111-bbc7-2257bf045a33
X-Runtime: 0.007985
Vary: Origin
Content-Length: 173
201 Created
```


```json
{
  "id": 8,
  "user_id": 81,
  "email": "suzette@mills.biz",
  "first_name": "Laurena",
  "last_name": "Schultz",
  "source": "",
  "status": "subscribed",
  "created_at": "2019-12-31T09:45:08.819-05:00"
}
```



## Delete a subscriber


### Request

#### Endpoint

```plaintext
DELETE /api/subscribers/9
Accept: application/json
Authorizat IO N: Bearer 8e683bd1e7ecda2a1393caf42a95ad160986d7a6bad7c317
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
X-Request-Id: ffa1d35c-bb1f-4637-9efc-33e22bf49867
X-Runtime: 0.006868
Vary: Origin
204 No Content
```




## Get a single subscriber by id


### Request

#### Endpoint

```plaintext
GET /api/subscribers/7
Accept: application/json
Authorizat IO N: Bearer d5027301dfa5801ee8c7027d145511a2746bd0d0630d770e
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
ETag: W/&quot;ef9464acb0d718b15af6ac408a05f263&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 7d24873e-90ee-4589-8e92-5f4d1f3eac8a
X-Runtime: 0.007562
Vary: Origin
Content-Length: 172
200 OK
```


```json
{
  "id": 7,
  "user_id": 80,
  "email": "mirna@conroyhilll.ca",
  "first_name": "Hunter",
  "last_name": "Rowe",
  "source": "",
  "status": "subscribed",
  "created_at": "2019-12-31T09:45:08.796-05:00"
}
```



## Get all subscribers


### Request

#### Endpoint

```plaintext
GET /api/subscribers
Accept: application/json
Authorizat IO N: Bearer b280cbef3e57c081c538fe3d2dfea7bed16ce0df43ea1f9b
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
ETag: W/&quot;1bfd9e084b22167989115ca0cc841f86&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: bf1921da-5760-4565-836d-87e419923d93
X-Runtime: 0.010369
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
      "created_at": "2019-12-31T09:45:08.759-05:00"
    },
    {
      "id": 5,
      "user_id": null,
      "email": "suk_medhurst@fisher.co.uk",
      "first_name": "Lexie",
      "last_name": "Graham",
      "source": "",
      "status": "subscribed",
      "created_at": "2019-12-31T09:45:08.760-05:00"
    },
    {
      "id": 6,
      "user_id": null,
      "email": "deangelo_smith@dooley.us",
      "first_name": "Dee",
      "last_name": "Oga",
      "source": "",
      "status": "subscribed",
      "created_at": "2019-12-31T09:45:08.761-05:00"
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
Authorizat IO N: Bearer 0a4f452efe08b160ce8dc9bd8a76229d234891a9f261550a
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
ETag: W/&quot;d28c8a0ef45b6603a2c8a7b9099e08a4&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 96dd5955-28e8-4edc-bc73-57490a0c3fd2
X-Runtime: 0.038634
Vary: Origin
Content-Length: 182
200 OK
```


```json
{
  "id": 3,
  "user_id": 78,
  "email": "rhiannon_walsh@smitham.info",
  "first_name": "Donnie",
  "last_name": "Runte",
  "source": "",
  "status": "unsubscribed",
  "created_at": "2019-12-31T09:45:08.715-05:00"
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
Authorizat IO N: Bearer 54ee52088da28bc01df1d70f20a7c147a67416ec78c4ba73
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
X-Request-Id: a336045b-250f-4340-8db5-3210ef1ab280
X-Runtime: 0.044138
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
X-Request-Id: 12b4b57a-7f76-4afe-8a09-652ec5769929
X-Runtime: 0.030090
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
ETag: W/&quot;3535812c9fa04652750a3a27999b7bd4&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 3f906105-4910-4c37-ab83-95c3f65bc28e
X-Runtime: 0.011526
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
ETag: W/&quot;3f0c114060f8f04c4432770f1385596d&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 6cddd7fb-9cf0-487e-a002-f872c405a2eb
X-Runtime: 0.022577
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
      "id": 24,
      "name": "Category",
      "pretty_name": "Category",
      "permalink": "category",
      "parent_id": null,
      "taxonomy_id": 7,
      "url_override": null,
      "description": "Category",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 25,
      "name": "Kids",
      "pretty_name": "Category -> Kids",
      "permalink": "category/kids",
      "parent_id": 24,
      "taxonomy_id": 7,
      "url_override": null,
      "description": "Kids",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 26,
      "name": "Boys",
      "pretty_name": "Category -> Kids -> Boys",
      "permalink": "category/kids/boys",
      "parent_id": 25,
      "taxonomy_id": 7,
      "url_override": null,
      "description": "Boys",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 27,
      "name": "Boys Tops",
      "pretty_name": "Category -> Kids -> Boys -> Boys Tops",
      "permalink": "category/kids/boys/boys-tops",
      "parent_id": 26,
      "taxonomy_id": 7,
      "url_override": null,
      "description": "Boys Tops",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 28,
      "name": "Boys Shirts",
      "pretty_name": "Category -> Kids -> Boys -> Boys Tops -> Boys Shirts",
      "permalink": "category/kids/boys/boys-tops/boys-shirts",
      "parent_id": 27,
      "taxonomy_id": 7,
      "url_override": null,
      "description": "Boys Shirts",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 29,
      "name": "Girls",
      "pretty_name": "Category -> Kids -> Girls",
      "permalink": "category/kids/girls",
      "parent_id": 25,
      "taxonomy_id": 7,
      "url_override": null,
      "description": "Girls",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 30,
      "name": "Girls Tops",
      "pretty_name": "Category -> Kids -> Girls -> Girls Tops",
      "permalink": "category/kids/girls/girls-tops",
      "parent_id": 29,
      "taxonomy_id": 7,
      "url_override": null,
      "description": "Girls Tops",
      "icon": "/assets/default_taxon.png"
    },
    {
      "id": 31,
      "name": "Girls Shirts",
      "pretty_name": "Category -> Kids -> Girls -> Girls Tops -> Girls Shirts",
      "permalink": "category/kids/girls/girls-tops/girls-shirts",
      "parent_id": 30,
      "taxonomy_id": 7,
      "url_override": null,
      "description": "Girls Shirts",
      "icon": "/assets/default_taxon.png"
    },
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
ETag: W/&quot;fdcbf50ddb2d6b6bc4cfe11dd4da8377&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 3c4b0cd2-c8d6-4208-9458-40287b23be16
X-Runtime: 0.007057
Vary: Origin
Content-Length: 139
200 OK
```


```json
[
  {
    "id": 12,
    "name": "Kids",
    "navigation_url": "/kids",
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
user[email]=email2%40example.com&user[password]=secret
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
Authorization: Bearer 19004ffa6b044fe5862034f3c5ac9d57eff8e5a7ca1280a2
ETag: W/&quot;1ce740d86d715770e828098067992db9&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: e61980a5-ab78-4bb1-bc67-4bad8bf4123e
X-Runtime: 0.035710
Vary: Origin
Content-Length: 559
200 OK
```


```json
{
  "id": 2,
  "email": "email2@example.com",
  "persistence_token": null,
  "perishable_token": null,
  "last_request_at": null,
  "login": "email2@example.com",
  "ship_address_id": null,
  "bill_address_id": null,
  "created_at": "2019-12-31T09:44:51.142-05:00",
  "updated_at": "2019-12-31T09:44:51.144-05:00",
  "spree_api_key": "19004ffa6b044fe5862034f3c5ac9d57eff8e5a7ca1280a2",
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
X-Spree-Order-Token: jlU8Vxff88b2aBriORZMSQ
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/users/login`

#### Parameters


```json
user[email]=email3%40example.com&user[password]=secret&order_number=M142022401
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
Authorization: Bearer 51781964ba229fa110489aa04f9ff21ec34a214154933269
ETag: W/&quot;a1fd77699137b8661583101d4f56a796&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: c0d59a41-4cb5-4ead-96dd-2fd0569907ba
X-Runtime: 0.010499
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
  "created_at": "2019-12-31T09:44:51.190-05:00",
  "updated_at": "2019-12-31T09:44:51.193-05:00",
  "spree_api_key": "51781964ba229fa110489aa04f9ff21ec34a214154933269",
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
Authorizat IO N: Bearer 938543f5ba7c289531dfebec0f6a00564e321b130ca12215
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
Authorization: Bearer 938543f5ba7c289531dfebec0f6a00564e321b130ca12215
ETag: W/&quot;996329c28f99cacded9843c0aa5c46cf&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: dbfedbba-cc32-43d4-bfb8-c9d341cc208e
X-Runtime: 0.022554
Vary: Origin
Content-Length: 1511
200 OK
```


```json
{
  "email": "email5@example.com",
  "first_name": null,
  "last_name": null,
  "id": 6,
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
        "created_at": "2019-12-31T09:44:52.136-05:00",
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
        "created_at": "2019-12-31T09:44:52.158-05:00",
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
        "created_at": "2019-12-31T09:44:52.172-05:00",
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
Authorization: Bearer 2614d6cd2df1fd57e185814e89175fdcba6f88f09badbade
ETag: W/&quot;46ff3693cad8f48ac7dc6dde95476c55&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 059189dd-f2a5-46bd-887e-8c735c216364
X-Runtime: 0.011801
Vary: Origin
Content-Length: 184
201 Created
```


```json
{
  "id": 4,
  "email": "test@example.com",
  "created_at": "2019-12-31T09:44:52.031-05:00",
  "updated_at": "2019-12-31T09:44:52.033-05:00",
  "subscribed": false,
  "bill_address": null,
  "ship_address": null
}
```



## Subscribe a user


### Request

#### Endpoint

```plaintext
PUT /api/users/1/subscribe
Authorizat IO N: Bearer c3f724a601b35be694c11625de00abd174cff17983ac13d5
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
Authorization: Bearer c3f724a601b35be694c11625de00abd174cff17983ac13d5
ETag: W/&quot;fbda016606c58dc8b8f88364f1517ac8&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: ae01a5a7-79a5-4d48-ae43-59f11452eaf3
X-Runtime: 0.206456
Vary: Origin
Content-Length: 185
200 OK
```


```json
{
  "id": 1,
  "email": "email1@example.com",
  "created_at": "2019-12-31T09:44:50.899-05:00",
  "updated_at": "2019-12-31T09:44:50.902-05:00",
  "subscribed": true,
  "bill_address": null,
  "ship_address": null
}
```



## Unsubscribe a user


### Request

#### Endpoint

```plaintext
PUT /api/users/5/unsubscribe
Authorizat IO N: Bearer 6a55db6d31c514fed1de229264a519ffb1271f7832ae7908
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
Authorization: Bearer 6a55db6d31c514fed1de229264a519ffb1271f7832ae7908
ETag: W/&quot;ef7494756d9a52ec5e24500181ebd7cf&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: ad357d9e-1ab1-4aca-b144-a62ec4e3b685
X-Runtime: 0.010031
Vary: Origin
Content-Length: 186
200 OK
```


```json
{
  "id": 5,
  "email": "email4@example.com",
  "created_at": "2019-12-31T09:44:52.047-05:00",
  "updated_at": "2019-12-31T09:44:52.048-05:00",
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
GET /api/variants/57
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
ETag: W/&quot;aa7bb8794793f50b084bfc74dd5974ad&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 674f8ab1-5e39-4404-b7dd-cec7b10f2852
X-Runtime: 0.106831
Vary: Origin
Content-Length: 1936
200 OK
```


```json
{
  "id": 57,
  "name": "Product #34 - 2232",
  "sku": "SKU-56",
  "weight": "0.0",
  "height": null,
  "width": null,
  "depth": null,
  "is_master": false,
  "slug": "product-34-2232",
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
    {
      "id": 1,
      "position": 1,
      "attachment_content_type": "image/jpeg",
      "attachment_file_name": "thinking-cat.jpg",
      "type": "Spree::Image",
      "attachment_updated_at": "2019-12-31T09:44:59.274-05:00",
      "attachment_width": 489,
      "attachment_height": 490,
      "alt": null,
      "viewable_type": "Spree::Variant",
      "viewable_id": 57,
      "mini_url": "/spree/products/1/mini/thinking-cat.jpg?1577803499",
      "small_url": "/spree/products/1/small/thinking-cat.jpg?1577803499",
      "product_url": "/spree/products/1/product/thinking-cat.jpg?1577803499",
      "large_url": "/spree/products/1/large/thinking-cat.jpg?1577803499"
    }
  ],
  "variant_properties": [

  ],
  "stock_items": [

  ],
  "prices": [
    {
      "id": 46,
      "vendor_id": 113,
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
      "id": 47,
      "vendor_id": 114,
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
Authorizat IO N: Bearer 611a1ee634c2ea93c74069a977efa896a95f8e5b2a96fb99
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
ETag: W/&quot;4420de400b62721e05b21d2fd6b7ab26&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 1c961714-201c-4e05-a365-90744fefc7dc
X-Runtime: 0.013344
Vary: Origin
Content-Length: 206
200 OK
```


```json
[
  {
    "id": 5,
    "user_id": 55,
    "payment_source_type": "SolidusPaypalBraintree::Source",
    "payment_source_id": 7,
    "default": false,
    "created_at": "2019-12-31T09:45:00.954-05:00",
    "updated_at": "2019-12-31T09:45:00.954-05:00"
  }
]
```



## Remove the payment from the user wallet


### Request

#### Endpoint

```plaintext
DELETE /api/wallet_payment_sources/6
Accept: application/json
Authorizat IO N: Bearer c73aeb24b9a1d3bc8c336e7bb6df57a0a6333a0276200da6
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
X-Request-Id: 80bb4711-b9af-43d8-a6eb-53842f8c624c
X-Runtime: 0.011994
Vary: Origin
204 No Content
```




## Set a wallet payment source as the default user payment method


### Request

#### Endpoint

```plaintext
POST /api/wallet_payment_sources/4/default
Accept: application/json
Authorizat IO N: Bearer 216d961596b1bd88ed11be69047a4764a65bd22206539607
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
X-Request-Id: 694407fe-0b13-418b-96c8-cee74505bc97
X-Runtime: 0.030617
Vary: Origin
204 No Content
```




# Wished Products

Destroy a wished product. Users can destroy their own wished_products, admins can destroy any.

## Create a wished product


### Request

#### Endpoint

```plaintext
POST /api/wished_products
Accept: application/json
Authorizat IO N: Bearer 42a47cb1c708b81eebc71b4edd5d925bd67c8e7dbd846782
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/wished_products`

#### Parameters


```json
wished_product[wishlist_id]=36&wished_product[variant_id]=123&wished_product[quantity]=2&wished_product[remark]=Foo+bar
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
ETag: W/&quot;988af6fe20ec252df3e8588f2ad86978&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 01adf556-5e82-436d-9481-493715915d24
X-Runtime: 0.013181
Vary: Origin
Content-Length: 75
201 Created
```


```json
{
  "id": 19,
  "wishlist_id": 36,
  "variant_id": 123,
  "quantity": 2,
  "remark": "Foo bar"
}
```



## Delete a wished product


### Request

#### Endpoint

```plaintext
DELETE /api/wished_products/10
Accept: application/json
Authorizat IO N: Bearer 7669d04f5bbd1ae49741af80cf0ed44fdf711c8d5e971c3c
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
X-Request-Id: 6f8d18cb-a538-4855-9a72-ceca2e56d70c
X-Runtime: 0.035439
Vary: Origin
204 No Content
```




## Get a single wished product


### Request

#### Endpoint

```plaintext
GET /api/wished_products/23
Accept: application/json
Authorizat IO N: Bearer 8c0d4068cddfbf0db01dc1e8aa1ace95922ec663a6f4696c
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
ETag: W/&quot;9140dd982d5b353064e7f8534d985ecb&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 1734097b-dfce-49fd-89ae-88f6ea2cc10c
X-Runtime: 0.009170
Vary: Origin
Content-Length: 70
200 OK
```


```json
{
  "id": 23,
  "wishlist_id": 38,
  "variant_id": 133,
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
Authorizat IO N: Bearer f9b9161e4386ae48e7ddb5d0bfaf00a55a913a2410809541
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
ETag: W/&quot;fe495a01847a8a51f8a7f281c196318b&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 0c0d797c-9198-4da1-9b21-0d30140f5d36
X-Runtime: 0.013763
Vary: Origin
Content-Length: 301
200 OK
```


```json
{
  "wished_products": [
    {
      "id": 13,
      "wishlist_id": 30,
      "variant_id": 111,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 14,
      "wishlist_id": 31,
      "variant_id": 113,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 15,
      "wishlist_id": 32,
      "variant_id": 115,
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
Authorizat IO N: Bearer bbea021626b4a22840cb4c7640d5c992ca612fe44275161b
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
ETag: W/&quot;9e12f822764d64e50ebfe834a2219771&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 59314293-a4aa-4ce2-b401-01ddfa2c1e5a
X-Runtime: 0.101434
Vary: Origin
Content-Length: 2155
200 OK
```


```json
{
  "wished_products": [
    {
      "id": 16,
      "wishlist_id": 33,
      "variant_id": 117,
      "quantity": 1,
      "remark": null,
      "variant": {
        "id": 117,
        "name": "Product #64 - 2579",
        "sku": "SKU-116",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-64-2579",
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
    },
    {
      "id": 17,
      "wishlist_id": 34,
      "variant_id": 119,
      "quantity": 1,
      "remark": null,
      "variant": {
        "id": 119,
        "name": "Product #65 - 9337",
        "sku": "SKU-118",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-65-9337",
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
      "wishlist_id": 35,
      "variant_id": 121,
      "quantity": 1,
      "remark": null,
      "variant": {
        "id": 121,
        "name": "Product #66 - 7788",
        "sku": "SKU-120",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-66-7788",
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
Authorizat IO N: Bearer 997d474622ac7eaa827bf46789e5a45d4def0ded96def5a7
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
ETag: W/&quot;9c7d1fde7b97934cc88e2f969528fbd8&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 11d68dff-e3c5-4c3c-9934-7ff12ce80da9
X-Runtime: 0.083950
Vary: Origin
Content-Length: 2093
200 OK
```


```json
{
  "wished_products": [
    {
      "id": 29,
      "wishlist_id": 40,
      "variant_id": 145,
      "quantity": 1,
      "remark": null,
      "variant": {
        "id": 145,
        "name": "Product #78 - 2373",
        "sku": "SKU-144",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-78-2373",
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
      "wishlist_id": 40,
      "variant_id": 147,
      "quantity": 1,
      "remark": null,
      "variant": {
        "id": 147,
        "name": "Product #79 - 466",
        "sku": "SKU-146",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-79-466",
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
    },
    {
      "id": 31,
      "wishlist_id": 40,
      "variant_id": 149,
      "quantity": 1,
      "remark": null,
      "variant": {
        "id": 149,
        "name": "Product #80 - 1770",
        "sku": "SKU-148",
        "weight": "0.0",
        "height": null,
        "width": null,
        "depth": null,
        "is_master": false,
        "slug": "product-80-1770",
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
Authorizat IO N: Bearer 651e45c8fe140bdf0989b21802d4ad36aaefebe6306ca588
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
ETag: W/&quot;26767975300cae2bab8fc176f17a33da&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: c60ec966-8e6b-481d-ac0c-e7394c125136
X-Runtime: 0.009311
Vary: Origin
Content-Length: 301
200 OK
```


```json
{
  "wished_products": [
    {
      "id": 26,
      "wishlist_id": 39,
      "variant_id": 139,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 27,
      "wishlist_id": 39,
      "variant_id": 141,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 28,
      "wishlist_id": 39,
      "variant_id": 143,
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
PATCH /api/wished_products/20
Accept: application/json
Authorizat IO N: Bearer 9b82a8854c4fa96fde43bfd134f71396d1395e8c0ea12d34
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/wished_products/:id`

#### Parameters


```json
wished_product[wishlist_id]=37&wished_product[variant_id]=131&wished_product[quantity]=2&wished_product[remark]=Foo+bar
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
ETag: W/&quot;b7f378b63dd99a55f23e082da7c38b3a&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: fe2db650-316d-4624-a08c-a72693b2017a
X-Runtime: 0.012428
Vary: Origin
Content-Length: 75
200 OK
```


```json
{
  "id": 20,
  "wishlist_id": 37,
  "variant_id": 131,
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
Authorizat IO N: Bearer d216d9bfca5e755afa9e1a2204e65ee8ba4ad7830e20b085
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/wishlists`

#### Parameters


```json
wishlist[name]&wishlist[user_id]=37&wishlist[is_default]=true&wishlist[is_public]=false
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
ETag: W/&quot;d255652caed84a5f7495a0641910f726&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 87cf1565-a3d6-402f-bba6-3597b3433551
X-Runtime: 0.011804
Vary: Origin
Content-Length: 99
201 Created
```


```json
{
  "id": 3,
  "user_id": 37,
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
DELETE /api/wishlists/5
Accept: application/json
Authorizat IO N: Bearer 1f04ff04e5325d29e5c5ec9d9185bc0a05c1339760d571cf
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
X-Request-Id: ee34ebe1-45eb-47b3-9e1a-f7d91303b1fc
X-Runtime: 0.012572
Vary: Origin
204 No Content
```




## Get a single wishlist


### Request

#### Endpoint

```plaintext
GET /api/wishlists/4
Accept: application/json
Authorizat IO N: Bearer 668f60415604f091a4a26d43c3dd896256fe6bc5b19eeab6
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
ETag: W/&quot;fa3d0e7def97e2d62c8917d7f56c865f&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 6f43557d-c631-4d63-9f6f-feb765d8c762
X-Runtime: 0.012833
Vary: Origin
Content-Length: 302
200 OK
```


```json
{
  "id": 4,
  "user_id": 38,
  "name": "Wishlist #3",
  "is_public": false,
  "is_default": true,
  "wished_products": [
    {
      "id": 7,
      "wishlist_id": 4,
      "variant_id": 51,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 8,
      "wishlist_id": 4,
      "variant_id": 53,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 9,
      "wishlist_id": 4,
      "variant_id": 55,
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
Authorizat IO N: Bearer 5d8e739933d8f74b675921279f58deb227a2b0e37590b9c8
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
ETag: W/&quot;c98daaaa1899c14d943331f2409689fd&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 5b6ed267-7126-4657-888c-d2700f90a954
X-Runtime: 0.010706
Vary: Origin
Content-Length: 894
200 OK
```


```json
{
  "wishlists": [
    {
      "id": 19,
      "user_id": 42,
      "name": "Wishlist #17",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 20,
      "user_id": 43,
      "name": "Wishlist #18",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 21,
      "user_id": 44,
      "name": "Wishlist #19",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 22,
      "user_id": 45,
      "name": "Wishlist #20",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 23,
      "user_id": 46,
      "name": "Wishlist #21",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 24,
      "user_id": 47,
      "name": "Wishlist #22",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 25,
      "user_id": 48,
      "name": "Wishlist #23",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 26,
      "user_id": 49,
      "name": "Wishlist #24",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 27,
      "user_id": 50,
      "name": "Wishlist #25",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 28,
      "user_id": 51,
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
Authorizat IO N: Bearer a39f4b7573f1d3c22e744419d028ea4d4421d66632e7c63d
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
ETag: W/&quot;b22b50c7ab614f79539aeec4cfbe7cc5&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 1220aa9e-7771-45fd-89a6-05a4e5527fb6
X-Runtime: 0.034871
Vary: Origin
Content-Length: 302
200 OK
```


```json
{
  "id": 1,
  "user_id": 35,
  "name": "Wishlist #1",
  "is_public": false,
  "is_default": true,
  "wished_products": [
    {
      "id": 1,
      "wishlist_id": 1,
      "variant_id": 39,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 2,
      "wishlist_id": 1,
      "variant_id": 41,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 3,
      "wishlist_id": 1,
      "variant_id": 43,
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
Authorizat IO N: Bearer 113b619a84454f76f410badb43d444d126d1046022100213
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
ETag: W/&quot;4643e383557f6cc2159146d06212d393&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 73957e06-1367-47d1-9a3a-91ffd7024d59
X-Runtime: 0.010416
Vary: Origin
Content-Length: 899
200 OK
```


```json
{
  "wishlists": [
    {
      "id": 9,
      "user_id": 41,
      "name": "Wishlist #7",
      "is_public": false,
      "is_default": true
    },
    {
      "id": 10,
      "user_id": 41,
      "name": "Wishlist #8",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 11,
      "user_id": 41,
      "name": "Wishlist #9",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 12,
      "user_id": 41,
      "name": "Wishlist #10",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 13,
      "user_id": 41,
      "name": "Wishlist #11",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 14,
      "user_id": 41,
      "name": "Wishlist #12",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 15,
      "user_id": 41,
      "name": "Wishlist #13",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 16,
      "user_id": 41,
      "name": "Wishlist #14",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 17,
      "user_id": 41,
      "name": "Wishlist #15",
      "is_public": false,
      "is_default": false
    },
    {
      "id": 18,
      "user_id": 41,
      "name": "Wishlist #16",
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
PATCH /api/wishlists/2
Accept: application/json
Authorizat IO N: Bearer b51897b4ef5abfb2a145ee9e9ae806c8765ed8008d04950b
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
ETag: W/&quot;89ad776ff9e38e16b0e8a680da93ec35&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: ea9c49b5-f6c9-4d28-89bb-7e8a7f877b0c
X-Runtime: 0.012656
Vary: Origin
Content-Length: 307
200 OK
```


```json
{
  "id": 2,
  "user_id": 36,
  "name": "Another Wishlist",
  "is_public": false,
  "is_default": true,
  "wished_products": [
    {
      "id": 4,
      "wishlist_id": 2,
      "variant_id": 45,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 5,
      "wishlist_id": 2,
      "variant_id": 47,
      "quantity": 1,
      "remark": null
    },
    {
      "id": 6,
      "wishlist_id": 2,
      "variant_id": 49,
      "quantity": 1,
      "remark": null
    }
  ]
}
```



