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
PUT /api/orders/M072310139/addresses/57
Accept: application/json
X-Spree-Order-Token: gyUl_nKHpf8Qj1B3iWn0LA
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
ETag: W/&quot;ee71aebd384bc4010d724f6f61925e68&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: aaaffc17-a46f-48b2-9f5d-651caf887145
X-Runtime: 0.053976
Vary: Origin
Content-Length: 507
200 OK
```


```json
[binary data]
```



# Braintree transactions

Please do not send billing address attributes at all if there is no billing address, otherwise you will get an order error


## Creating a PayPal express checkout transaction


### Request

#### Endpoint

```plaintext
POST /api/braintree/transactions
Accept: application/json
X-Spree-Order-Token: -Rh83cpl4fyk79VMbPYbzg
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/braintree/transactions`

#### Parameters


```json
order_id=M638619399&payment_method_id=8&options[restart_checkout]=true&transaction[email]=maryellen.oga%40mckenziemcglynn.com&transaction[nonce]=fake-paypal-billing-agreement-nonce&transaction[phone]=555-555-0199&transaction[shipping_address_attributes][first_name]=John&transaction[shipping_address_attributes][last_name]=Stamm&transaction[shipping_address_attributes][address_line_1]=A+Different+Road&transaction[shipping_address_attributes][city]=Herndon&transaction[shipping_address_attributes][state_code]=AL&transaction[shipping_address_attributes][zip]=10022&transaction[shipping_address_attributes][country_code]=US&transaction[payment_type]=PayPalAccount&transaction[billing_address_attributes][first_name]=John&transaction[billing_address_attributes][last_name]=Stamm&transaction[billing_address_attributes][address_line_1]=A+Different+Road&transaction[billing_address_attributes][city]=Herndon&transaction[billing_address_attributes][state_code]=AL&transaction[billing_address_attributes][zip]=10022&transaction[billing_address_attributes][country_code]=US
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
ETag: W/&quot;7799bc960318f385d1d646f2dbaf8384&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 12ebdb71-afc1-4757-8798-3e69dd91fc76
X-Runtime: 0.410136
Vary: Origin
Content-Length: 5403
200 OK
```


```json
[binary data]
```



## Creating an ApplePay one-click checkout transaction


### Request

#### Endpoint

```plaintext
POST /api/braintree/transactions
Accept: application/json
X-Spree-Order-Token: exJUQsRsG1uGog1QmQCJHA
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/braintree/transactions`

#### Parameters


```json
order_id=M074075242&payment_method_id=7&options[restart_checkout]=true&transaction[email]=maryellen.oga%40mckenziemcglynn.com&transaction[nonce]=fake-apple-pay-visa-nonce&transaction[phone]=555-555-0199&transaction[shipping_address_attributes][first_name]=John&transaction[shipping_address_attributes][last_name]=Stamm&transaction[shipping_address_attributes][address_line_1]=A+Different+Road&transaction[shipping_address_attributes][city]=Herndon&transaction[shipping_address_attributes][state_code]=AL&transaction[shipping_address_attributes][zip]=10020&transaction[shipping_address_attributes][country_code]=US&transaction[payment_type]=ApplePayCard
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
ETag: W/&quot;c1c11471841c642aaa96645779dd8b37&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 47f5321b-ddaa-41e8-9d7d-d5ac34d671b4
X-Runtime: 0.393673
Vary: Origin
Content-Length: 5449
200 OK
```


```json
[binary data]
```



# Checkout



## Completing the checkout when the order includes a Braintree payment


### Request

#### Endpoint

```plaintext
PUT /api/checkouts/M784179771/complete
Accept: application/json
X-Spree-Order-Token: V19JLZ_Nt9BvIzhEAPVlgQ
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
ETag: W/&quot;50c3f8d949389c86ace5a9c36276b04d&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 13d4368c-e872-40dd-9213-de42c1264fd5
X-Runtime: 0.593020
Vary: Origin
Content-Length: 5530
200 OK
```


```json
[binary data]
```



## Processing the checkout payment step with a not yet existing ApplePay payment


### Request

#### Endpoint

```plaintext
PATCH /api/checkouts/M011702581
Accept: application/json
X-Spree-Order-Token: -rDv5V3VVasdIL-PNgabhA
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=3&order[payment_attributes][][source_attributes][nonce]=fake-apple-pay-visa-nonce&order[payment_attributes][][source_attributes][payment_type]=ApplePayCard&order[payment_attributes][][source_attributes][reusable]=true
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
ETag: W/&quot;1058bead8d9d0a80c5c068fff1e0e5c1&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: a26348cf-69fc-44b9-8aca-52a8d5f13f9f
X-Runtime: 0.167927
Vary: Origin
Content-Length: 4919
200 OK
```


```json
[binary data]
```



## Processing the checkout payment step with a not yet existing PayPal payment


### Request

#### Endpoint

```plaintext
PATCH /api/checkouts/M646609057
Accept: application/json
X-Spree-Order-Token: nQJT027kdJxXbzUQm0C4VQ
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=4&order[payment_attributes][][source_attributes][nonce]=fake-paypal-billing-agreement-nonce&order[payment_attributes][][source_attributes][payment_type]=PayPalAccount&order[payment_attributes][][source_attributes][reusable]=true
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
ETag: W/&quot;ce2d9391960038c90096d028f29623d6&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: e9612c60-b52d-4524-926a-09e45f171b95
X-Runtime: 0.285286
Vary: Origin
Content-Length: 4919
200 OK
```


```json
[binary data]
```



## Processing the checkout payment step with a not yet existing credit card payment


### Request

#### Endpoint

```plaintext
PATCH /api/checkouts/M463918341
Accept: application/json
X-Spree-Order-Token: VGR1t22SJEfnftfSakE_-A
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=5&order[payment_attributes][][source_attributes][nonce]=fake-valid-visa-nonce&order[payment_attributes][][source_attributes][payment_type]=CreditCard&order[payment_attributes][][source_attributes][reusable]=true
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
ETag: W/&quot;e84d2340922815b0ca3b64a1e2c7a2ff&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 350bd11a-c8c9-41ed-8b41-b15f46d2dea4
X-Runtime: 0.178769
Vary: Origin
Content-Length: 4922
200 OK
```


```json
[binary data]
```



## Processing the checkout payment step with an already existing payment


### Request

#### Endpoint

```plaintext
PATCH /api/checkouts/M372321999
Accept: application/json
X-Spree-Order-Token: bI8A4Lm1p-_S9D-Sf92Uww
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=6&order[payment_attributes][][source_attributes][wallet_payment_source_id]=2
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
ETag: W/&quot;ea27197db101a5828238d24768825c6c&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 4c2a01ba-7bb3-4a6c-b465-9f8c6ac54fa1
X-Runtime: 0.189655
Vary: Origin
Content-Length: 4928
200 OK
```


```json
[binary data]
```



## update address


### Request

#### Endpoint

```plaintext
PUT /api/checkouts/M087302787
Accept: application/json
X-Spree-Order-Token: 5qlBmpfGj9FDVpboPy0a5Q
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PUT /api/checkouts/:id`

#### Parameters


```json
order[ship_address_attributes][id]&order[ship_address_attributes][firstname]=John&order[ship_address_attributes][lastname]&order[ship_address_attributes][address1]=10+Lovely+Street&order[ship_address_attributes][address2]=Northwest&order[ship_address_attributes][city]=Herndon&order[ship_address_attributes][zipcode]=10001&order[ship_address_attributes][phone]=555-555-0199&order[ship_address_attributes][state_name]&order[ship_address_attributes][alternative_phone]=555-555-0199&order[ship_address_attributes][company]=Company&order[ship_address_attributes][state_id]=1&order[ship_address_attributes][country_id]=1&order[ship_address_attributes][created_at]&order[ship_address_attributes][updated_at]&order[use_billing]=true&hold_state=true
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
ETag: W/&quot;be21495fa87f2bd026922522b0d154dc&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 9b90d69f-f973-4f5d-8ac1-38b16402ca35
X-Runtime: 0.471940
Vary: Origin
Content-Length: 4825
200 OK
```


```json
[binary data]
```



# Giftwrap

Create giftwrap related to shipment

## Create Giftwrap


### Request

#### Endpoint

```plaintext
POST /api/shipments/H77754570440/giftwrap
Accept: application/json
X-Spree-Order-Token: ApMJH98P7QSHm9pRvLALnA
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/shipments/:shipment_number/giftwrap`

#### Parameters


```json
order_number=M416322380
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
X-Request-Id: fe5547bc-c7c0-41d3-a37c-62ca93b1bacc
X-Runtime: 0.114661
Vary: Origin
Content-Length: 74
201 Created
```


```json
[binary data]
```



## Delete Giftwrap


### Request

#### Endpoint

```plaintext
DELETE /api/shipments/H60550572203/giftwrap
Accept: application/json
X-Spree-Order-Token: iemgbP-gJ_tk4moqtWrN6w
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`DELETE /api/shipments/:shipment_number/giftwrap`

#### Parameters


```json
order_number=M552180519
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
X-Request-Id: 0b34ba52-2903-4076-ae39-e1b66c467a8f
X-Runtime: 0.029153
Vary: Origin
204 No Content
```




# LineItem

Representation of a single cart item for a specific variant with price of vendor

## Creating a line item


### Request

#### Endpoint

```plaintext
POST /api/orders/M697237110/line_items
Accept: application/json
X-Spree-Order-Token: hwNM8lOtydS72qM-kTzWOA
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/:order_number/line_items`

#### Parameters


```json
line_item[variant_id]=95&line_item[options][vendor_id]=181
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
ETag: W/&quot;0bb28dc8697900ddd3af0a7322311828&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 6ffde5e0-69f5-4058-bf51-465b5ec26a72
X-Runtime: 0.120037
Vary: Origin
Content-Length: 937
201 Created
```


```json
[binary data]
```



## Creating a line item gift card


### Request

#### Endpoint

```plaintext
POST /api/orders/M641998206/line_items
Accept: application/json
X-Spree-Order-Token: kgtf9PMoYx2PXbTSNtazpA
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/:order_number/line_items`

#### Parameters


```json
line_item[variant_id]=101&line_item[options][vendor_id]=194&line_item[options][gift_card_details][recipient_name]=Recipient+John&line_item[options][gift_card_details][recipient_email]=recipient%40email.com&line_item[options][gift_card_details][purchaser_name]=Purchaser+Bob&line_item[options][gift_card_details][gift_message]=Surprise&line_item[options][gift_card_details][send_email_at]=2020-03-11+14%3A07%3A30+-0400
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
ETag: W/&quot;44d6067193536dda70c8ae4294802f6a&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 4a9bc120-2417-41cf-b0dc-103de62cf398
X-Runtime: 0.127141
Vary: Origin
Content-Length: 1078
201 Created
```


```json
[binary data]
```



## Deleting a line item


### Request

#### Endpoint

```plaintext
DELETE /api/orders/M471861034/line_items/27
Accept: application/json
X-Spree-Order-Token: yoxskUEIfYInYVgZAHlwVg
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
X-Request-Id: 9bbbea5c-b300-48f6-9fe4-931773b3cae4
X-Runtime: 0.074509
Vary: Origin
204 No Content
```




## Updating a line item


### Request

#### Endpoint

```plaintext
PUT /api/orders/M005320016/line_items/22
Accept: application/json
X-Spree-Order-Token: 45IAvgrKp2j0dNxii6hHKQ
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
ETag: W/&quot;2807f56ed59ae4d8a11c7051b6d05063&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: ed0219ae-980f-49ee-b534-0aa9c6902d5f
X-Runtime: 0.122607
Vary: Origin
Content-Length: 936
200 OK
```


```json
[binary data]
```



# Minis

Get a single mini, accessible by owner of the mini or admin

## Create a mini


### Request

#### Endpoint

```plaintext
POST /api/minis
Accept: application/json
Authorizat IO N: Bearer a32ad462e07a9d2e67db66c5b82f9007dea5cc420fe2859c
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/minis`

#### Parameters


```json
mini[name]=Winny&mini[user_id]=99&mini[birth_year]=2019&mini[birth_month]=1&mini[birth_day]=1
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
ETag: W/&quot;f15fc072ea413b9613f69a5c532b46db&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 011eb3b1-c7bd-4d34-8e09-b058b57d7921
X-Runtime: 0.013076
Vary: Origin
Content-Length: 163
201 Created
```


```json
[binary data]
```



## Delete a mini


### Request

#### Endpoint

```plaintext
DELETE /api/minis/17
Accept: application/json
Authorizat IO N: Bearer 17b12ac751c7609e46926a2fae29b3c1e1b26ac19c764801
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
X-Request-Id: 4295734a-49b5-498f-a940-cf640f5aad1c
X-Runtime: 0.008597
Vary: Origin
204 No Content
```




## Get a single mini


### Request

#### Endpoint

```plaintext
GET /api/minis/1
Accept: application/json
Authorizat IO N: Bearer 713d14559616208289adcf24bb77a4fab1a29c98a509910c
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
ETag: W/&quot;ad788022513e35fa33ac20c8927ba3f2&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 778da7cb-2969-431f-9009-7d081a9483ba
X-Runtime: 0.040446
Vary: Origin
Content-Length: 162
200 OK
```


```json
[binary data]
```



## Get all minis


### Request

#### Endpoint

```plaintext
GET /api/minis
Accept: application/json
Authorizat IO N: Bearer 77a2e88c4778bb794cf6322a58684d6cc9ed9bc4efb87ebf
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
ETag: W/&quot;a402d9304887d6987553924568f41cb8&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 88bcc2e3-aa84-44b3-bb26-55fbb46d60f6
X-Runtime: 0.059441
Vary: Origin
Content-Length: 1712
200 OK
```


```json
[binary data]
```



## Get my minis


### Request

#### Endpoint

```plaintext
GET /api/minis/mine
Accept: application/json
Authorizat IO N: Bearer c22eeb8a7e3269c0106964a4e9d17ea78ce33c955b783f5f
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
ETag: W/&quot;8048d3f7a9ed1d7971c4cabbfd6ebe8f&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 766a385e-0830-4062-89e6-8a37f8bb7556
X-Runtime: 0.016701
Vary: Origin
Content-Length: 406
200 OK
```


```json
[binary data]
```



## Update a mini


### Request

#### Endpoint

```plaintext
PATCH /api/minis/18
Accept: application/json
Authorizat IO N: Bearer a1ad3929a3df284077f9b6db6baa5de561d04658a52d8712
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
ETag: W/&quot;1cd8bc0726b4ae16e2db1f279763865d&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 5e82365e-7347-4ada-a8d3-6280fb5dfe73
X-Runtime: 0.014185
Vary: Origin
Content-Length: 164
200 OK
```


```json
[binary data]
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
user_id&order_token&line_item[variant_id]=66&line_item[quantity]=1&line_item[vendor_id]=117&line_item[gift_card_details_attributes][recipient_name]=Recipient+John&line_item[gift_card_details_attributes][recipient_email]=recipient%40email.com&line_item[gift_card_details_attributes][purchaser_name]=Purchaser+Bob&line_item[gift_card_details_attributes][gift_message]=Surprise&line_item[gift_card_details_attributes][send_email_at]=2020-03-11
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
ETag: W/&quot;962cec629b110763aa9953a21ebc23bf&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: fbd3bf7a-4a4e-4235-ae84-776511df1478
X-Runtime: 0.304820
Vary: Origin
Content-Length: 2847
200 OK
```


```json
[binary data]
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
user_id&order_token&line_item[variant_id]=38&line_item[quantity]=2&line_item[vendor_id]=60
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
ETag: W/&quot;e7cb0af34edd21b275a5301ef96af507&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 79726c23-d9f8-457a-a854-c8b58034fd2b
X-Runtime: 0.161038
Vary: Origin
Content-Length: 2661
200 OK
```


```json
[binary data]
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
user_id&order_token&line_item[variant_id]=42&line_item[quantity]=2&line_item[vendor_id]=68
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
ETag: W/&quot;03620560b1b0287922ce13f9c6e2bc94&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 411c7d1f-83c3-44e2-94c5-f1b45837c740
X-Runtime: 0.139810
Vary: Origin
Content-Length: 2662
200 OK
```


```json
[binary data]
```



## Add an item to a cart related to the user


### Request

#### Endpoint

```plaintext
POST /api/orders/cart
Accept: application/json
Authorizat IO N: Bearer 737250f4fdb4ea156d5a887db2ed6633e95930db4c86a5d4
X-Spree-Order-Token: 
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/cart`

#### Parameters


```json
user_id&order_token&line_item[variant_id]=54&line_item[quantity]=2&line_item[vendor_id]=90&user_token=Bearer+737250f4fdb4ea156d5a887db2ed6633e95930db4c86a5d4
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
ETag: W/&quot;d4d571c90084e829b7897482719f77cd&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: b604c0f1-cf6d-4670-82f2-cc0e6db02b35
X-Runtime: 0.170706
Vary: Origin
Content-Length: 2675
200 OK
```


```json
[binary data]
```



## Add an item to a order


### Request

#### Endpoint

```plaintext
POST /api/orders/cart
Accept: application/json
Authorizat IO N: 
X-Spree-Order-Token: 6pBH2rh8Vlg0uklkn1W2LA
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/cart`

#### Parameters


```json
user_id&order_token=6pBH2rh8Vlg0uklkn1W2LA&line_item[variant_id]=50&line_item[quantity]=2&line_item[vendor_id]=84
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
ETag: W/&quot;b8ff2180c384ca638dbb1f81b527ef5e&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: ddad1fcc-0081-4973-8fae-f17f30c47c30
X-Runtime: 0.277089
Vary: Origin
Content-Length: 5510
200 OK
```


```json
[binary data]
```



## Get my orders


### Request

#### Endpoint

```plaintext
GET /api/orders/mine
Accept: application/json
Authorizat IO N: Bearer 64ccee6b89df37785f6840388a7e13ddd2926ccf2017de09
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
X-Request-Id: dde32391-a7b7-4ac8-9724-0b7a2d4df74b
X-Runtime: 0.027853
Vary: Origin
Content-Length: 80
200 OK
```


```json
[binary data]
```



## it returns a 200


### Request

#### Endpoint

```plaintext
GET /api/orders/M283948845
Accept: application/json
Authorizat IO N: Bearer 48be8d2f17f06c7d162f8f4205fcdc0160cd619f788cbe40
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
ETag: W/&quot;f2ba71be86cdab00e6d5c38dbec61ccb&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: d789afdd-2ed0-4e1e-b07a-f6d13b81eca2
X-Runtime: 0.198388
Vary: Origin
Content-Length: 8022
200 OK
```


```json
[binary data]
```



## it returns a 401


### Request

#### Endpoint

```plaintext
GET /api/orders/M362299957
Accept: application/json
Authorizat IO N: c13f4f37a4e1151a5636cff74119a779feb6fec678167b26
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
X-Request-Id: d513a73b-9746-4594-886f-72559d894cbe
X-Runtime: 0.016759
Vary: Origin
Content-Length: 58
401 Unauthorized
```


```json
[binary data]
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
user[email]=email80%40example.com
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
X-Request-Id: 2daab439-a9de-456e-9bae-891d1f217963
X-Runtime: 0.003347
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
user[email]=email78%40example.com&user[password]=secret
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
Authorization: Bearer c6a83545c61c4541a59d228ab47d3c949279df2e096a3581
ETag: W/&quot;2352ba4654a064a8533bea24dcdff113&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: f4843443-709f-48b9-835b-ee04147f1485
X-Runtime: 0.009077
Vary: Origin
Content-Length: 562
200 OK
```


```json
[binary data]
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
X-Request-Id: 43dc8cdc-51a5-4787-bec2-6a5f60ba9aad
X-Runtime: 0.023636
Vary: Origin
204 No Content
```




# Products

Get products info

## Fetch a single product by id


### Request

#### Endpoint

```plaintext
GET /api/products/product-45-7363
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
Date: Wed, 11 Mar 2020 18:07:27 GMT
Surrogate-Control: max-age=900
Surrogate-Key: product_id=1
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;2fef798e92a97ef8f0e42e0bd72a334d&quot;
X-Request-Id: 3bbdbb6a-77db-474a-b0f8-718293eac411
X-Runtime: 0.059314
Vary: Origin
Content-Length: 1575
200 OK
```


```json
[binary data]
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
Date: Wed, 11 Mar 2020 18:07:26 GMT
Surrogate-Control: max-age=900
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;7a68899855be07bcd79cc47a5bb4fc41&quot;
X-Request-Id: 13790bf5-d4da-4ab4-9fc7-288682c52676
X-Runtime: 0.074448
Vary: Origin
Content-Length: 1250
200 OK
```


```json
[binary data]
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
Date: Wed, 11 Mar 2020 18:07:27 GMT
Surrogate-Control: max-age=900
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;34ad38b817e5f8454f30809c1ab4aa3d&quot;
X-Request-Id: 126ff0c6-df2b-4b9c-87c2-bae5ad2540b4
X-Runtime: 0.033608
Vary: Origin
Content-Length: 337
200 OK
```


```json
[binary data]
```



## Fetch multiple products by id


### Request

#### Endpoint

```plaintext
GET /api/products?ids=41%2C42%2C43
Host: example.org
Cookie: 
```

`GET /api/products`

#### Parameters


```json
ids: 41,42,43
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
Date: Wed, 11 Mar 2020 18:07:27 GMT
Surrogate-Control: max-age=900
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;3676d8a7371ecc7908c5db8bf9926623&quot;
X-Request-Id: e2c338ca-827c-4c99-84f2-e7f699a6df4b
X-Runtime: 0.110070
Vary: Origin
Content-Length: 2748
200 OK
```


```json
[binary data]
```



## Fetch products by taxon id


### Request

#### Endpoint

```plaintext
GET /api/taxons/products?id=16
Host: example.org
Cookie: 
```

`GET /api/taxons/products`

#### Parameters


```json
id: 16
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
ETag: W/&quot;8732da1fb9422ec3e55171efcda9c780&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 121562e5-a011-45a8-9f0f-3918582a8e8e
X-Runtime: 0.059524
Vary: Origin
Content-Length: 1270
200 OK
```


```json
[binary data]
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
ETag: W/&quot;de4b96841fd62d75e44ff1b88aa8f09c&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 26189bd1-d2ee-42ab-9580-c827ef3113b1
X-Runtime: 0.062744
Vary: Origin
Content-Length: 1274
200 OK
```


```json
[binary data]
```



## Get all products info


### Request

#### Endpoint

```plaintext
GET /api/sitemap/products
Accept: application/json
Authorizat IO N: Bearer ace464210409ca9685464c261e80fb477d0204ad7fa65e2b
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
X-Request-Id: 33e38eb0-0423-4b2a-ab2f-b8d397fd1d97
X-Runtime: 0.056657
Vary: Origin
Content-Length: 2
200 OK
```


```json
[binary data]
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
X-Request-Id: 3e8d42c3-7cff-49d6-b762-3385ed18e53f
X-Runtime: 0.016773
Vary: Origin
Content-Length: 65
404 Not Found
```


```json
[binary data]
```



# Recently Viewed Products

Get all recently viewed products using a session_id

## Get all recently viewed products


### Request

#### Endpoint

```plaintext
GET /api/recently_viewed?recently_viewed[session_id]=khigo8ow3cnzjdth9xzd0rv0hlwnn724foi6gddtjv6s3gdjtub1aobvpnmjhpulg9b8m0zs0ptapwhgzqv40f7j69aqsk0sfgvfezc0vfp2qh3p2aipy1h8cx4q26skaiu9egv85qcp76sc810tbeofz5wj92sa25v8ywojhtai5dhazm5un9vq2jqenvk0gt7cs31dpyt69x4vbahmamoa6d3nhtw4wtjxtnyiokgzyi2jashvs6vcfpwsfba
Accept: application/json
Authorizat IO N: Bearer c4a168b61d0c63ed9ff9a4d74fbbf2e060917a201b85407b
Host: example.org
Cookie: 
```

`GET /api/recently_viewed`

#### Parameters


```json
recently_viewed: {&quot;session_id&quot;=&gt;&quot;khigo8ow3cnzjdth9xzd0rv0hlwnn724foi6gddtjv6s3gdjtub1aobvpnmjhpulg9b8m0zs0ptapwhgzqv40f7j69aqsk0sfgvfezc0vfp2qh3p2aipy1h8cx4q26skaiu9egv85qcp76sc810tbeofz5wj92sa25v8ywojhtai5dhazm5un9vq2jqenvk0gt7cs31dpyt69x4vbahmamoa6d3nhtw4wtjxtnyiokgzyi2jashvs6vcfpwsfba&quot;}
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
ETag: W/&quot;8bfdeda67355823ea5ba48c0b3d5a55f&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 5befc662-2b18-4cec-abfe-d19cc1777a50
X-Runtime: 0.031802
Vary: Origin
Content-Length: 119
200 OK
```


```json
[binary data]
```



## Store a recently viewed variant


### Request

#### Endpoint

```plaintext
POST /api/recently_viewed
Accept: application/json
Authorizat IO N: Bearer 49080ca21027ce02607b3e868c9ddecc453564ae62dac87b
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/recently_viewed`

#### Parameters


```json
recently_viewed[session_id]=lr0511e8d0bmriz4fyn9fqdbblyhp0cj8xle11k731tmjffntc04o1jvkv18lkymbvmf5n07g8wiqahp1cei7xyobn4djwnrmtpgk0stsuaaif3rfkptm6ik879e0jon4txoplizx6f7d4nsh0i6tyh52lqg1jw22eisbim2bpf6sz5pelscm6t2uxa2o87ssi6428mgl1ghjhzaf4alf407st2w6hzu2lp4l80odxs8uw8bv818fl6ybxmh5vv&recently_viewed[variant_id]=foo
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
X-Request-Id: bc10a7b9-36a9-432e-8a9c-436e69f4f1aa
X-Runtime: 0.010587
Vary: Origin
204 No Content
```




# Return Authorizations

Get user return authorizations

## Can get another user&#39;s return authorization


### Request

#### Endpoint

```plaintext
GET /api/returns/RA830862414
Authorizat IO N: Bearer b7e2653d56377ba83b8920ba128483c42cff9b3d99266ff2
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
ETag: W/&quot;802cf0473c74b7192efda69dcca69c56&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 20227132-0f09-452b-926f-cb354a7553b0
X-Runtime: 0.044575
Vary: Origin
Content-Length: 2970
200 OK
```


```json
[binary data]
```



## Gets the user&#39;s return authorizations


### Request

#### Endpoint

```plaintext
GET /api/returns/mine
Authorizat IO N: Bearer a5e8d8f85f3ac292a830165f886cbfeca984deb9c6aeca53
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
ETag: W/&quot;77a362e2e805935e5d910f56f959161a&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 3f40e4d0-d2ef-4129-a4e8-2a4dbe0f6226
X-Runtime: 0.015637
Vary: Origin
Content-Length: 169
200 OK
```


```json
[binary data]
```



## returns a 200


### Request

#### Endpoint

```plaintext
GET /api/returns/RA875036042
Authorizat IO N: Bearer 3a5125221052f00f2a1d8749aee6f319333d6df71d04a204
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
ETag: W/&quot;1fa0891549c39cfcbdbb843d7ccb5d3c&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: eaaa6f1f-3788-4479-b6a6-2d1ca60684f7
X-Runtime: 0.053355
Vary: Origin
Content-Length: 2893
200 OK
```


```json
[binary data]
```



## returns a 404


### Request

#### Endpoint

```plaintext
GET /api/returns/RA831572452
Authorizat IO N: Bearer ca20811dbf0f5f1546bcb580ff6b2cfa3b99d23c5d8137b6
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
X-Request-Id: 587b2d50-f7b6-4a7d-9b08-e322669af248
X-Runtime: 0.008755
Vary: Origin
Content-Length: 65
404 Not Found
```


```json
[binary data]
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
stock_request[email]=michale.huels%40mertz.biz&stock_request[variant_id]=68
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
X-Request-Id: 02c631ca-3708-40e3-a5f9-df720f7ba4b5
X-Runtime: 0.032875
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
stock_request[email]=foo&stock_request[variant_id]=70
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
X-Request-Id: 7047d25c-9f5e-4dff-bdc5-2cc1a9d9e545
X-Runtime: 0.007533
Vary: Origin
Content-Length: 48
422 Unprocessable Entity
```


```json
[binary data]
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
stock_request[email]=shantae_rice%40jewess.co.uk&stock_request[variant_id]=72
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
X-Request-Id: e323e74c-c78a-449c-8cbe-5506883b77da
X-Runtime: 0.006333
Vary: Origin
Content-Length: 93
422 Unprocessable Entity
```


```json
[binary data]
```



# Store Credits API

Get user store_credits and current account balance for the current user

## returns a 200


### Request

#### Endpoint

```plaintext
GET api/store_credits/mine
Authorizat IO N: Bearer c85709284bd996bfef53dc3de12af89d2a8810b3a4891939
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
ETag: W/&quot;b013d3f3c9facb1a8a69c388a8b22c47&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 1317cd56-5d23-4ef8-9325-6c48bc0eab55
X-Runtime: 0.050328
Vary: Origin
Content-Length: 218
200 OK
```


```json
[binary data]
```



# Subscribers

Update a subscriber. Users can update their own subscriber, admins can update minis for others.

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
subscriber[email]=janis%40ritchieshields.info&subscriber[first_name]=Cori&subscriber[last_name]=Berge&subscriber[source]=Hic+sunt+quia+a+numquam+sapiente+sed+molestias+dolor.
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
ETag: W/&quot;3cdadec80ae9746037d7672c38fa77cf&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 64eee4a1-94d4-49db-ad05-237ad93692df
X-Runtime: 0.009185
Vary: Origin
Content-Length: 231
201 Created
```


```json
[binary data]
```



## Create a subscriber for the associated user


### Request

#### Endpoint

```plaintext
POST /api/subscribers
Accept: application/json
Authorizat IO N: Bearer 4e912958127c514517397d0924411ef4e407ff6dc258e35c
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/subscribers`

#### Parameters


```json
subscriber[email]=kasandra%40schmidtcormier.biz&subscriber[first_name]=Jannet&subscriber[last_name]=Ledner&subscriber[source]=Quaerat+ex+repellendus+esse+aliquam+rerum.
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
ETag: W/&quot;cbc2e1fc44262660a030d3e3fc8313be&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: dc450b56-8448-41e2-8124-15d4a80e989d
X-Runtime: 0.009871
Vary: Origin
Content-Length: 223
201 Created
```


```json
[binary data]
```



## Get all subscribers


### Request

#### Endpoint

```plaintext
GET /api/subscribers
Accept: application/json
Authorizat IO N: Bearer de84ab4aa5d6c12779cc61a36c598896987e84e1b2b6711e
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
ETag: W/&quot;4e4357e1c1567907a7b963b76c4ad9dd&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 4f6d6900-ceac-4973-85fd-91cd9fbfadbc
X-Runtime: 0.021193
Vary: Origin
Content-Length: 627
200 OK
```


```json
[binary data]
```



## Update a subscriber


### Request

#### Endpoint

```plaintext
PATCH /api/subscribers/1
Accept: application/json
Authorizat IO N: Bearer 6f1b23292f1e940be48be3b785ddb9e34a4c06bf6c83bef5
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/subscribers/:id`

#### Parameters


```json
subscriber[source]=Vero+facilis+sint+in+hic+nisi.
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
ETag: W/&quot;80ad2dc605ac8529646f6c3d532ddf99&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: ea1d8117-e426-4309-852f-79ffa92d4ecd
X-Runtime: 0.049753
Vary: Origin
Content-Length: 211
200 OK
```


```json
[binary data]
```



## unsubscribe a known subscriber


### Request

#### Endpoint

```plaintext
DELETE /api/subscribers
Accept: application/json
Authorizat IO N: Bearer 7762c2d9674db3b78fda6a9fc2e361d28c87126ea373d7e9
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`DELETE /api/subscribers`

#### Parameters


```json
subscriber[email]=email33%40example.com
```


| Name | Description |
|:-----|:------------|
| subscriber[email]  | Subscriber email |



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
X-Request-Id: 6ff01167-29fa-460d-936b-bf76ff4e6d0b
X-Runtime: 0.007469
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
Authorizat IO N: Bearer 9e9e091511ada67f637a0e7ab7e26141a6fd86bdfe7c5dd1
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`DELETE /api/subscribers`

#### Parameters


```json
subscriber[email]=chrissy_gusikowski%40powlowski.name
```


| Name | Description |
|:-----|:------------|
| subscriber[email]  | Subscriber email |



### Response

```plaintext
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Cache-Control: no-cache
X-Request-Id: cfbea64c-d1b8-433c-a029-c29ae7cf025b
X-Runtime: 0.007509
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
Authorizat IO N: Bearer 074e2369c7ce722e365fc95785fa7aaf39a7477b4f6a39aa
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
X-Request-Id: 155794f3-f4f2-475c-89bb-16624c5e1edb
X-Runtime: 0.033347
Vary: Origin
Content-Length: 2
200 OK
```


```json
[binary data]
```



# Taxons API

Return all taxons

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
ETag: W/&quot;148a85ed32d768fe93d985f00b8fa45e&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 69183e73-2372-4fbd-b682-3a70fbda848d
X-Runtime: 0.038412
Vary: Origin
Content-Length: 4438
200 OK
```


```json
[binary data]
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
ETag: W/&quot;836ed0a541e7298b47eec90713ccf3c3&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 3621880f-cb92-4077-86ea-ea9a66201de2
X-Runtime: 0.023579
Vary: Origin
Content-Length: 742
200 OK
```


```json
[binary data]
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
ETag: W/&quot;c63fea009dae5edf5af8e8d8d3cb5a71&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 76678de1-dfbe-489a-af2e-c58116c5007d
X-Runtime: 0.043256
Vary: Origin
Content-Length: 2662
200 OK
```


```json
[binary data]
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
ETag: W/&quot;8e5b7f56e4a8a00fc3e95d24d49ef678&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 743dfae9-c7a8-4522-8e37-7f830c6216fd
X-Runtime: 0.003612
Vary: Origin
Content-Length: 142
200 OK
```


```json
[binary data]
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
user[email]=email49%40example.com&user[password]=secret
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
Authorization: Bearer dc9d0e3d92a7ea2f2c763f3534eee215274e9f78285a47e9
ETag: W/&quot;19e65f0ef2d2f5e188f488a5da903caf&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 41f5553b-b86f-453c-8189-53b963bc67e1
X-Runtime: 0.011167
Vary: Origin
Content-Length: 562
200 OK
```


```json
[binary data]
```



## Login and merge guest cart

Log in and merge an existing guest cart with any existing carts associated with the user

### Request

#### Endpoint

```plaintext
POST /api/users/login
Accept: application/json
X-Spree-Order-Token: hQAbuK8Yk0NnVbCrHo2spA
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/users/login`

#### Parameters


```json
user[email]=email50%40example.com&user[password]=secret&order_number=M714442024
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
Authorization: Bearer d3e7faa3a1d0a9d7232f5bafcf55038e816b9f40696e54c8
ETag: W/&quot;5a9964649a432a76a6f8b4fbc2a52c78&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 4eb7e91b-b1e6-465a-8a9c-f29474ad5344
X-Runtime: 0.013537
Vary: Origin
Content-Length: 562
200 OK
```


```json
[binary data]
```



## Mine

Get user account details, stored addresses, and stored credit cards

### Request

#### Endpoint

```plaintext
GET /api/users/mine
Accept: application/json
Authorizat IO N: Bearer 975c330daca80aa3458103f00a9415b3803f28d6208bfc18
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
Authorization: Bearer 975c330daca80aa3458103f00a9415b3803f28d6208bfc18
ETag: W/&quot;9528320269a022942c6a419a32dacc1f&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 7b431f2a-b68b-4b7c-a5d0-3ca4d86d6761
X-Runtime: 0.039327
Vary: Origin
Content-Length: 1522
200 OK
```


```json
[binary data]
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
Authorization: Bearer 657c90cbb5469e08ff27e20e5929b0b852f1fb8e7e500d18
ETag: W/&quot;d0e25578035ab4e79a5e4e0354a06c4f&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: b3292156-53a7-494f-ac51-a2968526afee
X-Runtime: 0.026001
Vary: Origin
Content-Length: 185
201 Created
```


```json
[binary data]
```



## Signup and merge guest cart

Create a user and merge an existing guest cart with any existing carts associated with the user

### Request

#### Endpoint

```plaintext
POST /api/users
Accept: application/json
X-Spree-Order-Token: jKot8v7n6nlaupzr0r6Zwg
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/users`

#### Parameters


```json
user[email]=test%40example.com&user[password]=test123&user[password_confirmation]=test123&order_number=M770009885
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
Authorization: Bearer 432386de82c481446170d4dabf6a1486835e33642a418107
ETag: W/&quot;88457d3474bc38cb0738114e7da9e883&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: a82ecdf0-5d50-4c24-b5e1-742613603f9c
X-Runtime: 0.023342
Vary: Origin
Content-Length: 185
201 Created
```


```json
[binary data]
```



## Subscribe a user


### Request

#### Endpoint

```plaintext
PUT /api/users/54/subscribe
Accept: application/json
Authorizat IO N: Bearer 61aedf759e31c1722f6c979a545ec427c6d1108569bc066b
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
Authorization: Bearer 61aedf759e31c1722f6c979a545ec427c6d1108569bc066b
ETag: W/&quot;747a27d08392ec74facb661a69ba5bb1&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: b2092394-5dd2-4206-b61f-71813d6ac9a4
X-Runtime: 0.016634
Vary: Origin
Content-Length: 187
200 OK
```


```json
[binary data]
```



## Unsubscribe a user


### Request

#### Endpoint

```plaintext
PUT /api/users/53/unsubscribe
Accept: application/json
Authorizat IO N: Bearer ccf536be0e0563d72e69717d4db7f1711a78e9c4a544bc57
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
Authorization: Bearer ccf536be0e0563d72e69717d4db7f1711a78e9c4a544bc57
ETag: W/&quot;48185d3aa6d5f3fe28b7f299426bdd57&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 19fdecae-e068-4d32-850b-92394c412d82
X-Runtime: 0.015451
Vary: Origin
Content-Length: 188
200 OK
```


```json
[binary data]
```



# Variant



## Fetching a variant


### Request

#### Endpoint

```plaintext
GET /api/variants/167
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
ETag: W/&quot;82420d45af2119cbd78add51e4c50195&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: b76a648d-c95a-44f3-8816-7b91f4a197ba
X-Runtime: 0.093092
Vary: Origin
Content-Length: 1999
200 OK
```


```json
[binary data]
```



# Wallet payment sources



## Get user wallet payment sources


### Request

#### Endpoint

```plaintext
GET /api/wallet_payment_sources
Accept: application/json
Authorizat IO N: Bearer 5fb578fdd8bb28f12aa2267dd9d7a1894db6f71fadffc845
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
ETag: W/&quot;b25efbbd66096b61fc2651be3e4bb662&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 0f02e3b4-9694-4ba7-b3be-93d29e14bf0e
X-Runtime: 0.036831
Vary: Origin
Content-Length: 206
200 OK
```


```json
[binary data]
```



## Remove the payment from the user wallet


### Request

#### Endpoint

```plaintext
DELETE /api/wallet_payment_sources/5
Accept: application/json
Authorizat IO N: Bearer 9e50de1ffc5857a2de834ffccb560e5711b730a51bb1ddf8
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
X-Request-Id: a5de81d1-cd2b-41f7-a720-55a8ee48fc95
X-Runtime: 0.013559
Vary: Origin
204 No Content
```




## Set a wallet payment source as the default user payment method


### Request

#### Endpoint

```plaintext
POST /api/wallet_payment_sources/4/default
Accept: application/json
Authorizat IO N: Bearer 296c9fb3cf3e0965719b7d8c649fb06c25b881235f2f5209
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
X-Request-Id: 1d37c025-5e4b-46b7-9ceb-5a4333e0a736
X-Runtime: 0.012948
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
Authorizat IO N: Bearer 02d827c1eb71378f7a5b4e1dd3a12ed695dc086bde6365f5
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/wished_products`

#### Parameters


```json
wished_product[wishlist_id]=32&wished_product[variant_id]=139&wished_product[quantity]=2&wished_product[remark]=Foo+bar
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
ETag: W/&quot;cb7e3eb4fddd4d0dbb767bf566063ea0&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 176287cd-f31f-4d49-aa5b-89e269b5d450
X-Runtime: 0.015200
Vary: Origin
Content-Length: 75
201 Created
```


```json
[binary data]
```



## Delete a wished product


### Request

#### Endpoint

```plaintext
DELETE /api/wished_products/29
Accept: application/json
Authorizat IO N: Bearer 8746e9fdbf81424933d1c8cfb75205d10888f1945570217e
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
X-Request-Id: 4e1cff6e-8d0c-4253-ae95-642c7fbde53c
X-Runtime: 0.012769
Vary: Origin
204 No Content
```




## Get a single wished product


### Request

#### Endpoint

```plaintext
GET /api/wished_products/10
Accept: application/json
Authorizat IO N: Bearer ce93f0a5ea48da4384b520658d6efbb7c87ada8a2c08f0cc
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
ETag: W/&quot;03666b5ce516fe98e37808ca2ae7330b&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 76530aa6-60be-4a11-b1bd-ac2af38bc415
X-Runtime: 0.039248
Vary: Origin
Content-Length: 70
200 OK
```


```json
[binary data]
```



## Get all wished products


### Request

#### Endpoint

```plaintext
GET /api/wished_products
Accept: application/json
Authorizat IO N: Bearer b028a63fbab948e616089fecfe728491189acfd3c34e7879
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
ETag: W/&quot;3febf56de6c57c27699dc3b890a5e43f&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 20c432c6-1927-4f7c-b911-170ee9128496
X-Runtime: 0.011220
Vary: Origin
Content-Length: 301
200 OK
```


```json
[binary data]
```



## Get all wished products with variants


### Request

#### Endpoint

```plaintext
GET /api/wished_products/mine?with_variant=true
Accept: application/json
Authorizat IO N: Bearer 24ea0e7f1c400ea431b13a4b173d72e1984849f7ab3712bb
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
ETag: W/&quot;77fd2472a0e8c77b9ade42c5f283be28&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 1e0b3bf5-aa48-454d-813a-b40747686839
X-Runtime: 0.127873
Vary: Origin
Content-Length: 2155
200 OK
```


```json
[binary data]
```



## Get all wished products with variants


### Request

#### Endpoint

```plaintext
GET /api/wished_products?with_variant=true
Accept: application/json
Authorizat IO N: Bearer 1244b440f2fe6d6f972d953156eaba83c72d3e88580bbab4
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
ETag: W/&quot;aac538eb263d0de5032e5290d91c398e&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 0858848f-1dfa-48d8-83ba-b0e7cd25f5de
X-Runtime: 0.098486
Vary: Origin
Content-Length: 2215
200 OK
```


```json
[binary data]
```



## Get my wished products


### Request

#### Endpoint

```plaintext
GET /api/wished_products/mine
Accept: application/json
Authorizat IO N: Bearer a67070f9e079954eccbddd702e7fbf4cbac2df1e4855a174
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
ETag: W/&quot;2c0ab55d2c9e998012f521bd9b86a3c3&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 38321211-bed6-45be-b68e-9ef3b3e5582c
X-Runtime: 0.011813
Vary: Origin
Content-Length: 301
200 OK
```


```json
[binary data]
```



## Update a wishlist


### Request

#### Endpoint

```plaintext
PATCH /api/wished_products/26
Accept: application/json
Authorizat IO N: Bearer 5c07316468276f737028f1a46390a1cab5e3e33e31d35dc8
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/wished_products/:id`

#### Parameters


```json
wished_product[wishlist_id]=39&wished_product[variant_id]=159&wished_product[quantity]=2&wished_product[remark]=Foo+bar
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
ETag: W/&quot;a3781a5c8b9288e279db86242b018c82&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 24b1b001-410b-426a-a48e-1f1f21b0bc26
X-Runtime: 0.013505
Vary: Origin
Content-Length: 75
200 OK
```


```json
[binary data]
```



# Wishlists

Create a wishlist. Any user can create their own wishlist, admins can create wishlists for others.

## Create a wishlist


### Request

#### Endpoint

```plaintext
POST /api/wishlists
Accept: application/json
Authorizat IO N: Bearer 0b02191898f5f2d647e5c0f1746bbdb6721dc7c5cd238d53
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/wishlists`

#### Parameters


```json
wishlist[name]&wishlist[user_id]=7&wishlist[is_default]=true&wishlist[is_public]=false
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
ETag: W/&quot;3ab0b45ba8a8da3bb856b9b380c9204e&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: e34a4fcc-c89c-40a3-a1b5-0854c5a7b78e
X-Runtime: 0.068236
Vary: Origin
Content-Length: 98
201 Created
```


```json
[binary data]
```



## Delete a wishlist


### Request

#### Endpoint

```plaintext
DELETE /api/wishlists/13
Accept: application/json
Authorizat IO N: Bearer b420f4c492f56955f1e225583a3dd99e6bae4bb698588c37
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
X-Request-Id: 2f511213-3338-4016-88d2-efd9695dc37f
X-Runtime: 0.019545
Vary: Origin
204 No Content
```




## Get a single wishlist


### Request

#### Endpoint

```plaintext
GET /api/wishlists/12
Accept: application/json
Authorizat IO N: Bearer d5fb850220551cb30dbb5d2fe0e86cd5b17d7c7b70ed775c
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
ETag: W/&quot;04d371af9031678147a970a4b316d86e&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 3e25db7a-15c5-4378-89cd-7bd74077a3a3
X-Runtime: 0.013902
Vary: Origin
Content-Length: 307
200 OK
```


```json
[binary data]
```



## Get all wishlists


### Request

#### Endpoint

```plaintext
GET /api/wishlists
Accept: application/json
Authorizat IO N: Bearer 75da2d411feb19d586beab5a860f599813a86d32610a9cb4
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
ETag: W/&quot;530834b0094af9ffff7bc4a074606bab&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 499dce89-4681-4b1a-a091-bf2d11c2bd72
X-Runtime: 0.015733
Vary: Origin
Content-Length: 875
200 OK
```


```json
[binary data]
```



## Get my default wishlist


### Request

#### Endpoint

```plaintext
GET /api/wishlist
Accept: application/json
Authorizat IO N: Bearer 074a41a7d089e551e53e60f2aecc236ad30f3fbda7497239
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
ETag: W/&quot;0d694bd0ff275abc033738da81e64591&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: c218dcdc-0cc9-4b4b-851c-52aa181e0803
X-Runtime: 0.010479
Vary: Origin
Content-Length: 307
200 OK
```


```json
[binary data]
```



## Get my wishlists


### Request

#### Endpoint

```plaintext
GET /api/wishlists/mine
Accept: application/json
Authorizat IO N: Bearer 32e6ab64d4dea5f44a91d072ca91dea1fccf629181a5cc5d
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
ETag: W/&quot;48f9992908bc9798d316ec498eb84a86&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 7e573f1e-4451-418a-ae5b-18d725b758e1
X-Runtime: 0.012661
Vary: Origin
Content-Length: 903
200 OK
```


```json
[binary data]
```



## Update a wishlist


### Request

#### Endpoint

```plaintext
PATCH /api/wishlists/28
Accept: application/json
Authorizat IO N: Bearer 48a29a9e7bc1a10da4795089bf4c0557faa3b0d6ecd43e10
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/wishlists/:id`

#### Parameters


```json
wishlist[name]=Another+Wishlist&wishlist[user_id]=24&wishlist[is_default]=true&wishlist[is_public]=false
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
ETag: W/&quot;42865028b88855c148f5244871862630&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 83797bc8-355b-4c44-8530-98a2349df69c
X-Runtime: 0.021912
Vary: Origin
Content-Length: 311
200 OK
```


```json
[binary data]
```



