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
PUT /api/orders/M514607447/addresses/16
Accept: application/json
X-Spree-Order-Token: ry9Ut3hC1-jgRRqQ_TfYTQ
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
ETag: W/&quot;1352fd528c09af3278daaff2a4f14fc9&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 896e193f-e172-41f4-a124-6496ef43b2d0
X-Runtime: 0.068297
Vary: Origin
Content-Length: 502
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
X-Spree-Order-Token: J-JqoXJYXIc7_7LECAyjZw
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/braintree/transactions`

#### Parameters


```json
order_id=M935255518&payment_method_id=5&options[restart_checkout]=true&transaction[email]=maryellen.oga%40mckenziemcglynn.com&transaction[nonce]=fake-paypal-billing-agreement-nonce&transaction[phone]=555-555-0199&transaction[shipping_address_attributes][first_name]=John&transaction[shipping_address_attributes][last_name]=Stamm&transaction[shipping_address_attributes][address_line_1]=A+Different+Road&transaction[shipping_address_attributes][city]=Herndon&transaction[shipping_address_attributes][state_code]=AL&transaction[shipping_address_attributes][zip]=10009&transaction[shipping_address_attributes][country_code]=US&transaction[payment_type]=PayPalAccount&transaction[billing_address_attributes][first_name]=John&transaction[billing_address_attributes][last_name]=Stamm&transaction[billing_address_attributes][address_line_1]=A+Different+Road&transaction[billing_address_attributes][city]=Herndon&transaction[billing_address_attributes][state_code]=AL&transaction[billing_address_attributes][zip]=10009&transaction[billing_address_attributes][country_code]=US
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
ETag: W/&quot;f26b6821e52cbf3c8c19503bcb6cb8b5&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 951d2b4c-a7ee-4b1b-abfa-696dbe044019
X-Runtime: 0.369049
Vary: Origin
Content-Length: 5368
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
X-Spree-Order-Token: mOHPQA6nmCzb2S40EQ5mCw
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/braintree/transactions`

#### Parameters


```json
order_id=M755514335&payment_method_id=4&options[restart_checkout]=true&transaction[email]=maryellen.oga%40mckenziemcglynn.com&transaction[nonce]=fake-apple-pay-visa-nonce&transaction[phone]=555-555-0199&transaction[shipping_address_attributes][first_name]=John&transaction[shipping_address_attributes][last_name]=Stamm&transaction[shipping_address_attributes][address_line_1]=A+Different+Road&transaction[shipping_address_attributes][city]=Herndon&transaction[shipping_address_attributes][state_code]=AL&transaction[shipping_address_attributes][zip]=10007&transaction[shipping_address_attributes][country_code]=US&transaction[payment_type]=ApplePayCard
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
ETag: W/&quot;be9dc3b40634fb7736b31c4572dc4c3e&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: cb124d44-a683-4661-a611-e55ce1d8273d
X-Runtime: 0.618889
Vary: Origin
Content-Length: 5411
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
PUT /api/checkouts/M620685516/complete
Accept: application/json
X-Spree-Order-Token: rTlYicAq54lYapjnfBAOhw
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
ETag: W/&quot;c043d72c663bcaac72cab54b8afbab8a&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: d6739fde-34d8-4a89-bb3e-fb7a2de6d35b
X-Runtime: 0.581438
Vary: Origin
Content-Length: 5573
200 OK
```


```json
[binary data]
```



## Processing the checkout payment step with a not yet existing ApplePay payment


### Request

#### Endpoint

```plaintext
PATCH /api/checkouts/M083321900
Accept: application/json
X-Spree-Order-Token: edtm51VxDdTDR2f7O5M5iA
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=17&order[payment_attributes][][source_attributes][nonce]=fake-apple-pay-visa-nonce&order[payment_attributes][][source_attributes][payment_type]=ApplePayCard&order[payment_attributes][][source_attributes][reusable]=true
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
ETag: W/&quot;bdf10db54962eae942014d7731abeec2&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: f6389fb5-ad91-40e7-9f00-91aa2d390f3d
X-Runtime: 0.179126
Vary: Origin
Content-Length: 4957
200 OK
```


```json
[binary data]
```



## Processing the checkout payment step with a not yet existing PayPal payment


### Request

#### Endpoint

```plaintext
PATCH /api/checkouts/M906796846
Accept: application/json
X-Spree-Order-Token: 5lmmUoOxMht5FBKm2LGNJg
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=19&order[payment_attributes][][source_attributes][nonce]=fake-paypal-billing-agreement-nonce&order[payment_attributes][][source_attributes][payment_type]=PayPalAccount&order[payment_attributes][][source_attributes][reusable]=true
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
ETag: W/&quot;a91e6473c35719009a79599c35f35f36&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: eceacc2d-504e-44bf-8467-5ace23fbd10e
X-Runtime: 0.174838
Vary: Origin
Content-Length: 4957
200 OK
```


```json
[binary data]
```



## Processing the checkout payment step with a not yet existing credit card payment


### Request

#### Endpoint

```plaintext
PATCH /api/checkouts/M651624608
Accept: application/json
X-Spree-Order-Token: V2WROEEhjK6Tfn1UXjLIEQ
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=18&order[payment_attributes][][source_attributes][nonce]=fake-valid-visa-nonce&order[payment_attributes][][source_attributes][payment_type]=CreditCard&order[payment_attributes][][source_attributes][reusable]=true
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
ETag: W/&quot;84326ab46bee2294543ee5354554b1c9&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 17356a97-7c9f-4ff9-856c-ddad2b32fc29
X-Runtime: 0.187089
Vary: Origin
Content-Length: 4955
200 OK
```


```json
[binary data]
```



## Processing the checkout payment step with an already existing payment


### Request

#### Endpoint

```plaintext
PATCH /api/checkouts/M351875989
Accept: application/json
X-Spree-Order-Token: CWFxIYNPgax3D_p5ONJKKA
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=16&order[payment_attributes][][source_attributes][wallet_payment_source_id]=5
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
ETag: W/&quot;db544ca60e2a2cbaa197a65a0635853d&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 942ad24f-4060-4dbc-810d-5a8039515244
X-Runtime: 0.165043
Vary: Origin
Content-Length: 4955
200 OK
```


```json
[binary data]
```



## update address


### Request

#### Endpoint

```plaintext
PUT /api/checkouts/M204444803
Accept: application/json
X-Spree-Order-Token: Q0zcooa7ZePX_NlP83pCOQ
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PUT /api/checkouts/:id`

#### Parameters


```json
order[ship_address_attributes][id]&order[ship_address_attributes][firstname]=John&order[ship_address_attributes][lastname]&order[ship_address_attributes][address1]=10+Lovely+Street&order[ship_address_attributes][address2]=Northwest&order[ship_address_attributes][city]=Herndon&order[ship_address_attributes][zipcode]=10037&order[ship_address_attributes][phone]=555-555-0199&order[ship_address_attributes][state_name]&order[ship_address_attributes][alternative_phone]=555-555-0199&order[ship_address_attributes][company]=Company&order[ship_address_attributes][state_id]=18&order[ship_address_attributes][country_id]=18&order[ship_address_attributes][created_at]&order[ship_address_attributes][updated_at]&order[use_billing]=true&hold_state=true
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
ETag: W/&quot;a3ae9a2084795338301086714f7e981b&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 85eb65b1-cb60-4e40-a550-ddfc7def3267
X-Runtime: 0.190840
Vary: Origin
Content-Length: 4864
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
POST /api/shipments/H47158625857/giftwrap
Accept: application/json
X-Spree-Order-Token: VglCg3DFaFG5r8kNd2ATBA
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/shipments/:shipment_number/giftwrap`

#### Parameters


```json
order_number=M648848467
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
X-Request-Id: bc7a8589-54bb-427d-97f8-81fe9a87ff5a
X-Runtime: 0.150026
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
DELETE /api/shipments/H55151331668/giftwrap
Accept: application/json
X-Spree-Order-Token: YJ9gOCL3pvczZDIhGrXGxw
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`DELETE /api/shipments/:shipment_number/giftwrap`

#### Parameters


```json
order_number=M242386309
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
X-Request-Id: c296f7ba-280b-4fd2-af37-c4a0e8883b71
X-Runtime: 0.030327
Vary: Origin
204 No Content
```




# LineItem

Representation of a single cart item for a specific variant with price of vendor

## Creating a line item


### Request

#### Endpoint

```plaintext
POST /api/orders/M250171732/line_items
Accept: application/json
X-Spree-Order-Token: aU--EiEGiXly0NYKs_B8Sg
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/:order_number/line_items`

#### Parameters


```json
line_item[variant_id]=167&line_item[options][vendor_id]=305
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
ETag: W/&quot;feedf51631fcdb9dbc824050497aff1e&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 4844e124-22a2-4084-9cd6-e1459dd4a67e
X-Runtime: 0.116282
Vary: Origin
Content-Length: 942
201 Created
```


```json
[binary data]
```



## Creating a line item gift card


### Request

#### Endpoint

```plaintext
POST /api/orders/M022835968/line_items
Accept: application/json
X-Spree-Order-Token: xfpCDko3vGSPSW5xI61u-w
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/:order_number/line_items`

#### Parameters


```json
line_item[variant_id]=159&line_item[options][vendor_id]=291&line_item[options][gift_card_details][recipient_name]=Recipient+John&line_item[options][gift_card_details][recipient_email]=recipient%40email.com&line_item[options][gift_card_details][purchaser_name]=Purchaser+Bob&line_item[options][gift_card_details][gift_message]=Surprise&line_item[options][gift_card_details][send_email_at]=2020-03-17+16%3A41%3A38+-0400
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
ETag: W/&quot;1b5429dd763f354b9e394ab267cfddea&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 5fb3725b-4a4c-448c-9686-bc585134191c
X-Runtime: 0.165474
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
DELETE /api/orders/M436578087/line_items/33
Accept: application/json
X-Spree-Order-Token: kWq5qOUMLLHwVvwZFNMv8A
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
X-Request-Id: b0b679d6-3a5e-4923-8fe7-b6568fd95d00
X-Runtime: 0.079498
Vary: Origin
204 No Content
```




## Updating a line item


### Request

#### Endpoint

```plaintext
PUT /api/orders/M102478582/line_items/30
Accept: application/json
X-Spree-Order-Token: FS7BRQu8Mh6MZvRJczuv9g
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
ETag: W/&quot;c71c37954565b157718a16b6d083f0f6&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 6fe0b2c1-64a0-451e-9c46-a7ddcf472e1f
X-Runtime: 0.145655
Vary: Origin
Content-Length: 939
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
Authorizat IO N: Bearer feadc3e2406de5a3f0b753d7a76ec8c9deffd7d3e61e31a9
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/minis`

#### Parameters


```json
mini[name]=Winny&mini[user_id]=30&mini[birth_year]=2019&mini[birth_month]=1&mini[birth_day]=1
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
ETag: W/&quot;25063fb9acb2e8acc735f5c8c4c8be2a&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: b304c62d-a207-48ef-bfb5-3d4c4da4fae1
X-Runtime: 0.014884
Vary: Origin
Content-Length: 162
201 Created
```


```json
[binary data]
```



## Delete a mini


### Request

#### Endpoint

```plaintext
DELETE /api/minis/8
Accept: application/json
Authorizat IO N: Bearer dcdb733d7333bb487aeebd49481721eac86d7a1eee3a62b9
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
X-Request-Id: acfac0d3-0816-4e10-966a-f70abfd61d07
X-Runtime: 0.021868
Vary: Origin
204 No Content
```




## Get a single mini


### Request

#### Endpoint

```plaintext
GET /api/minis/1
Accept: application/json
Authorizat IO N: Bearer c351210e4b9bde549bb25d66ea559a073b73cf336a999beb
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
ETag: W/&quot;913dd7c98117aee5f77fb6431f9273e5&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 29583147-281c-494d-94ae-6c2107ff029f
X-Runtime: 0.044582
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
Authorizat IO N: Bearer 729ca4a434ad9f92b194d6a0e433be514ecaf134fc727089
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
ETag: W/&quot;581103c57522cd3c3e4a91fa2eef8490&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 2d366806-ee58-4e57-b24e-9d6d05a3f906
X-Runtime: 0.042680
Vary: Origin
Content-Length: 1720
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
Authorizat IO N: Bearer 21f06ca35f53ab937d8d11588cb84e51cfb9bb79f2bcdeda
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
ETag: W/&quot;ec74d3f06774cbcd86cf1230f43a8045&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 4568aa49-5a4a-42ad-b304-e6538cd67865
X-Runtime: 0.022407
Vary: Origin
Content-Length: 404
200 OK
```


```json
[binary data]
```



## Update a mini


### Request

#### Endpoint

```plaintext
PATCH /api/minis/2
Accept: application/json
Authorizat IO N: Bearer 77b67b57b7e3952ba26b0a95fbebc3f13b5156ee16c4519f
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
ETag: W/&quot;2b50d7a15b8fad5c353d8047f5300e1a&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 0f6ae910-fb55-4bd8-b1c0-104ba1da5a6f
X-Runtime: 0.016371
Vary: Origin
Content-Length: 163
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
user_id&order_token&line_item[variant_id]=101&line_item[quantity]=1&line_item[vendor_id]=189&line_item[gift_card_details_attributes][recipient_name]=Recipient+John&line_item[gift_card_details_attributes][recipient_email]=recipient%40email.com&line_item[gift_card_details_attributes][purchaser_name]=Purchaser+Bob&line_item[gift_card_details_attributes][gift_message]=Surprise&line_item[gift_card_details_attributes][send_email_at]=2020-03-17
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
ETag: W/&quot;0c852837d59c3e9d4c52db24528b3f5e&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 30819b81-0f9a-4532-af4e-5a96f51ca134
X-Runtime: 0.221141
Vary: Origin
Content-Length: 2850
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
user_id&order_token&line_item[variant_id]=105&line_item[quantity]=2&line_item[vendor_id]=194
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
ETag: W/&quot;4d30fe23b720b6fad7672cb848949852&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 9b2fc1a5-4467-4a47-b414-d021383ca6e9
X-Runtime: 0.133783
Vary: Origin
Content-Length: 2668
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
Authorizat IO N: Bearer b3fa3cf811ff00623bb2ccb08e0cb539fde73dad307e2acb
X-Spree-Order-Token: 
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/cart`

#### Parameters


```json
user_id&order_token&line_item[variant_id]=117&line_item[quantity]=2&line_item[vendor_id]=216&user_token=Bearer+b3fa3cf811ff00623bb2ccb08e0cb539fde73dad307e2acb
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
ETag: W/&quot;3829b7b4be4a7926e18ccbfe70e37ef1&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 273deaff-cb08-4294-8656-9bbdaecbb4fc
X-Runtime: 0.182140
Vary: Origin
Content-Length: 2680
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
user_id&order_token&line_item[variant_id]=121&line_item[quantity]=2&line_item[vendor_id]=224
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
ETag: W/&quot;2cb57c4b23b14253abbf071376df42f9&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 5c98ced1-c72f-4aef-bd19-c075ccc5c62a
X-Runtime: 0.178732
Vary: Origin
Content-Length: 2668
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
X-Spree-Order-Token: XUFAg-k6KbZ2FaZoO2JsyA
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/cart`

#### Parameters


```json
user_id&order_token=XUFAg-k6KbZ2FaZoO2JsyA&line_item[variant_id]=113&line_item[quantity]=2&line_item[vendor_id]=210
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
ETag: W/&quot;fe8df15e95fba251e1171e1630e4a1d4&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 01a68f4b-2193-4844-a31f-a07c4f064ee7
X-Runtime: 0.292138
Vary: Origin
Content-Length: 5525
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
Authorizat IO N: Bearer 06c3f3b5873b9f9c075a8b07a6cf9505857a61850d5edcef
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
X-Request-Id: 92d3e124-2830-4e3b-95e6-6db809d02dee
X-Runtime: 0.019075
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
GET /api/orders/M713649834
Accept: application/json
Authorizat IO N: Bearer 0b5388ff065e187a3196cc02c1c6d75bec2b9d27f6e1312b
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
ETag: W/&quot;6090b1a47962341acf2f3da1b30111dd&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 98dfb8d0-652e-448a-b91c-18174c96ce1d
X-Runtime: 0.239745
Vary: Origin
Content-Length: 8029
200 OK
```


```json
[binary data]
```



## it returns a 401


### Request

#### Endpoint

```plaintext
GET /api/orders/M567192443
Accept: application/json
Authorizat IO N: 5d3c70b58a2e8f8dda9c60e274242effb1dcc14e21b25bd9
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
X-Request-Id: 0522c175-a18e-45aa-8a11-455866eb3a83
X-Runtime: 0.017976
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
user[email]=email3%40example.com
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
X-Request-Id: 7cf25bcc-b9cb-4770-bd81-3fdbe7e8fd18
X-Runtime: 0.003394
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
user[email]=email1%40example.com&user[password]=secret
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
Authorization: Bearer f96c4d975e60f61e8c41623fe9cb35a2b0eeac452bd738c8
ETag: W/&quot;db16f75bc7bf95dcafbf72afc377b399&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: c9492b95-6506-45a4-94ee-c3718305cec7
X-Runtime: 0.132914
Vary: Origin
Content-Length: 559
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
X-Request-Id: 5cd40221-65ff-40b4-a03d-16e1470d2499
X-Runtime: 0.023704
Vary: Origin
204 No Content
```




# Products

Get products info

## Fetch a single product by id


### Request

#### Endpoint

```plaintext
GET /api/products/product-28-9334
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
Date: Tue, 17 Mar 2020 20:41:22 GMT
Surrogate-Control: max-age=900
Surrogate-Key: product_id=1
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;76fc3e5fdc34eae5a56189b8509b87bc&quot;
X-Request-Id: bfb4c24b-28d3-45e9-8d77-b979b8ce43de
X-Runtime: 0.063985
Vary: Origin
Content-Length: 1620
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
Date: Tue, 17 Mar 2020 20:41:20 GMT
Surrogate-Control: max-age=900
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;806f54aec739aca3b03674dff7f06bc7&quot;
X-Request-Id: 07e1a2e6-e923-47e4-8749-f51c4a3511a9
X-Runtime: 0.075675
Vary: Origin
Content-Length: 1292
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
Date: Tue, 17 Mar 2020 20:41:21 GMT
Surrogate-Control: max-age=900
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;d349ff3e02a46a458a04e62da2d77d4b&quot;
X-Request-Id: f26b926c-f54b-4586-9159-dc2503465e4e
X-Runtime: 0.032703
Vary: Origin
Content-Length: 375
200 OK
```


```json
[binary data]
```



## Fetch multiple products by id


### Request

#### Endpoint

```plaintext
GET /api/products?ids=21%2C22%2C23
Host: example.org
Cookie: 
```

`GET /api/products`

#### Parameters


```json
ids: 21,22,23
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
Date: Tue, 17 Mar 2020 20:41:21 GMT
Surrogate-Control: max-age=900
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;4ef46b091612cacc6fb84cba9032502b&quot;
X-Request-Id: eb4d9fa9-33c2-4da2-97f0-b5ef16813c0e
X-Runtime: 0.114251
Vary: Origin
Content-Length: 2862
200 OK
```


```json
[binary data]
```



## Fetch products by taxon id


### Request

#### Endpoint

```plaintext
GET /api/taxons/products?id=47
Host: example.org
Cookie: 
```

`GET /api/taxons/products`

#### Parameters


```json
id: 47
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
ETag: W/&quot;a54fda4bd5610edb331d47aed724779b&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 2d78dcbf-8a52-4987-a553-02724209ad17
X-Runtime: 0.059868
Vary: Origin
Content-Length: 1313
200 OK
```


```json
[binary data]
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
ETag: W/&quot;0abce0db512ae6004e3881646cfafbaa&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 6721c9f9-6c69-4aa6-9722-ae1c77870529
X-Runtime: 0.055947
Vary: Origin
Content-Length: 1313
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
Authorizat IO N: Bearer c264d126727614d4aabf1aba6e0f5c6f8e5c0072148ba935
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
X-Request-Id: c832d395-ff83-4490-a930-cce36ae3ab62
X-Runtime: 0.050752
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
X-Request-Id: 5c5ca546-4bcb-450f-a0aa-4077cd115f5f
X-Runtime: 0.013320
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
GET /api/recently_viewed?recently_viewed[session_id]=o8ow3cnzjdth9xzd0rv0hlwnn724foi6gddtjv6s3gdjtub1aobvpnmjhpulg9b8m0zs0ptapwhgzqv40f7j69aqsk0sfgvfezc0vfp2qh3p2aipy1h8cx4q26skaiu9egv85qcp76sc810tbeofz5wj92sa25v8ywojhtai5dhazm5un9vq2jqenvk0gt7cs31dpyt69x4vbahmamoa6d3nhtw4wtjxtnyiokgzyi2jashvs6vcfpwsfbalr05
Accept: application/json
Authorizat IO N: Bearer eb4b900e5dbed73a3d007452f48f9d5997be41802cbafde6
Host: example.org
Cookie: 
```

`GET /api/recently_viewed`

#### Parameters


```json
recently_viewed: {&quot;session_id&quot;=&gt;&quot;o8ow3cnzjdth9xzd0rv0hlwnn724foi6gddtjv6s3gdjtub1aobvpnmjhpulg9b8m0zs0ptapwhgzqv40f7j69aqsk0sfgvfezc0vfp2qh3p2aipy1h8cx4q26skaiu9egv85qcp76sc810tbeofz5wj92sa25v8ywojhtai5dhazm5un9vq2jqenvk0gt7cs31dpyt69x4vbahmamoa6d3nhtw4wtjxtnyiokgzyi2jashvs6vcfpwsfbalr05&quot;}
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
ETag: W/&quot;32eb1769f181e79f1d3c40a12184417b&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 5cf9a2f9-eed2-4bc8-98a5-16a6064c8ad5
X-Runtime: 0.035394
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
Authorizat IO N: Bearer f17d343ebfacb477422e2262b325eb3fab37d9e08088abff
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/recently_viewed`

#### Parameters


```json
recently_viewed[session_id]=11e8d0bmriz4fyn9fqdbblyhp0cj8xle11k731tmjffntc04o1jvkv18lkymbvmf5n07g8wiqahp1cei7xyobn4djwnrmtpgk0stsuaaif3rfkptm6ik879e0jon4txoplizx6f7d4nsh0i6tyh52lqg1jw22eisbim2bpf6sz5pelscm6t2uxa2o87ssi6428mgl1ghjhzaf4alf407st2w6hzu2lp4l80odxs8uw8bv818fl6ybxmh5vvd6dh&recently_viewed[variant_id]=foo
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
X-Request-Id: d1a04bb7-1231-4fe8-aab7-fc3ba5f01817
X-Runtime: 0.011158
Vary: Origin
204 No Content
```




# Return Authorizations

Get a single user return authorziation

## Can get another user&#39;s return authorization


### Request

#### Endpoint

```plaintext
GET /api/returns/RA673347506
Authorizat IO N: Bearer 4da54f7fbff76da8a01f1aa085612408d1561f9d93007c3d
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
ETag: W/&quot;168aa4b7b87a89aca6e82b3f1306c506&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 695e0c93-10b4-46e2-bd59-6ff6fb83c399
X-Runtime: 0.044334
Vary: Origin
Content-Length: 2954
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
Authorizat IO N: Bearer eac8e56c1b1d99f9315f0c5ed6d606b3f1c154f99315be67
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
ETag: W/&quot;c12a33a9ab43db0974b69c09bf9d0b54&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 0c189225-b7e6-4a01-9e3b-05fefadb9aa4
X-Runtime: 0.010298
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
GET /api/returns/RA823885611
Authorizat IO N: Bearer 9a91e1471fcf8d2dbf2709f80165088a0e4b4197fd05cee2
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
ETag: W/&quot;cc8e90fdc6421f8aa07b8cdadb42f505&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 97a9eb84-e757-4a3c-840a-6275b291983c
X-Runtime: 0.069374
Vary: Origin
Content-Length: 2877
200 OK
```


```json
[binary data]
```



## returns a 404


### Request

#### Endpoint

```plaintext
GET /api/returns/RA252810324
Authorizat IO N: Bearer 8da7ef49d9b57a4b6d889abd7233e1f2cf528f7ff9cce02c
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
X-Request-Id: e8c7e80c-7cb3-4adf-99fd-d710a84ae43a
X-Runtime: 0.012188
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
stock_request[email]=telma.collier%40ankunding.info&stock_request[variant_id]=97
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
X-Request-Id: 594d3ede-2be4-4aa5-985a-c2285849b7a3
X-Runtime: 0.006444
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
stock_request[email]=foo&stock_request[variant_id]=93
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
X-Request-Id: d12b127c-93b7-4126-baa9-332385fbd361
X-Runtime: 0.043852
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
stock_request[email]=isobel_nikolaus%40stark.co.uk&stock_request[variant_id]=95
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
X-Request-Id: 5866c2db-aa85-48c7-9028-1233866ace60
X-Runtime: 0.006284
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
Authorizat IO N: Bearer ae50ab1a855a632866d0c50d5e23c238adb51b0d69d5b0f0
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
ETag: W/&quot;f1f4b0b0c4acdc1134d7606b92cf9297&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 41f43611-5bce-4772-a08f-abad0357daf0
X-Runtime: 0.039565
Vary: Origin
Content-Length: 218
200 OK
```


```json
[binary data]
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
subscriber[email]=selena_little%40pfeffer.ca&subscriber[first_name]=Cora&subscriber[last_name]=Stamm&subscriber[source]=Quas+repudiandae+eum+placeat+eos+porro+illo+dolor+et.
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
ETag: W/&quot;c8defca1a2b32ef5cc2874117b419c03&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: d64f3e39-5c9e-4403-9359-0fea7530c625
X-Runtime: 0.012040
Vary: Origin
Content-Length: 243
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
Authorizat IO N: Bearer ff9349eaf2096d48f5cf56e7490bacc2539fe7f3a4769953
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/subscribers`

#### Parameters


```json
subscriber[email]=onie_oga%40lynch.com&subscriber[first_name]=Israel&subscriber[last_name]=Rutherford&subscriber[source]=Consequatur+maxime+tempore+accusantium+repellat+rerum+consectetur+quis+maiores.
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
ETag: W/&quot;d581eff589d0fd769e10bc227d773541&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 1366c0ee-8468-49b5-8956-d6de44ddead3
X-Runtime: 0.010271
Vary: Origin
Content-Length: 268
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
Authorizat IO N: Bearer 1816c877ee3b4341b78a8aba2828f073b04f42432ac4892c
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
ETag: W/&quot;c365efafd1ec431ad3fa6b2ed1d2487d&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: e5f1512b-8db5-41ae-83a5-dfcd22093675
X-Runtime: 0.038459
Vary: Origin
Content-Length: 661
200 OK
```


```json
[binary data]
```



## Update a subscriber


### Request

#### Endpoint

```plaintext
PATCH /api/subscribers/9
Accept: application/json
Authorizat IO N: Bearer 15f20e636bcca8ac90fb9639af28b50061afd6ab8869c762
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/subscribers/:id`

#### Parameters


```json
subscriber[source]=Aut+consequatur+consequuntur+beatae+aperiam+blanditiis+quia.
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
ETag: W/&quot;e7b4c7f8facb86dd5e3ede2be0409f0d&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: a5234f68-01fb-46f9-aa15-f17eff830a78
X-Runtime: 0.011514
Vary: Origin
Content-Length: 257
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
Authorizat IO N: Bearer 0c406211eaf7aa8dbf6fb53289e3be616decefdeadcfa17d
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`DELETE /api/subscribers`

#### Parameters


```json
subscriber[email]=email90%40example.com
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
X-Request-Id: 216a41e8-7fe0-449b-a383-6af958aadb08
X-Runtime: 0.008600
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
Authorizat IO N: Bearer 7c31683b303dc28cca824ecd050a02678bb28f7ee18f46ab
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`DELETE /api/subscribers`

#### Parameters


```json
subscriber[email]=burl%40rodriguezprosacco.biz
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
X-Request-Id: 156b2428-c75d-4488-9383-83c2fff5c5e2
X-Runtime: 0.005703
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
Authorizat IO N: Bearer 307ea1aa314c362cbd3e53e47e1d1bf19dfa2bbf0e34e2bc
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
X-Request-Id: 217be000-7060-46c5-8d14-53d360d0e25d
X-Runtime: 0.035020
Vary: Origin
Content-Length: 2
200 OK
```


```json
[binary data]
```



# Taxons API

Returns taxons associated with the Navigation Taxonomy for display in the menu bar

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
ETag: W/&quot;b896815ef6ab259486d635d19dd3466d&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 75afb0ed-7660-448b-b654-3526da23b43c
X-Runtime: 0.039175
Vary: Origin
Content-Length: 4411
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
ETag: W/&quot;39f3d8863126e37262588883390471b0&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 60b67d7e-ef23-419e-844d-c3aa515eb804
X-Runtime: 0.015005
Vary: Origin
Content-Length: 739
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
ETag: W/&quot;0980047f3967b20f383da2c5020da5cf&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 022291f1-a2af-4c2f-98ea-82bee37f2351
X-Runtime: 0.027780
Vary: Origin
Content-Length: 2659
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
ETag: W/&quot;e792603001e30bc231de7835aa338967&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 9d5cd53d-f65c-4348-b0f8-d34c3c7e4ade
X-Runtime: 0.006395
Vary: Origin
Content-Length: 144
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
Authorization: Bearer 0de1de7bfe9065ced749858666d6b0743f53c67506d1d642
ETag: W/&quot;81e0ae3ba93cfdb3d2a00dceb3573241&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: bf9a2dcc-72ae-42bf-bc59-a3f649691fbe
X-Runtime: 0.011710
Vary: Origin
Content-Length: 559
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
X-Spree-Order-Token: UNcCVrb2O6WhGljbjeUz4w
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/users/login`

#### Parameters


```json
user[email]=email8%40example.com&user[password]=secret&order_number=M848652153
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
Authorization: Bearer f3a485a30d4f388be1e60ca238a382a05bfcb8c4eb9fbb9a
ETag: W/&quot;7722d0b55b18b6a70409d43ae007f1ba&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 9e340e32-84b9-4063-a0c3-3ac2cfd5deac
X-Runtime: 0.017333
Vary: Origin
Content-Length: 560
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
Authorizat IO N: Bearer 6fad0a9dcb67940b1149b755569b2f4e862123711160d355
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
Authorization: Bearer 6fad0a9dcb67940b1149b755569b2f4e862123711160d355
ETag: W/&quot;f5ac1971783a12b5c0197bc175877597&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: c1ccd54c-3267-4d43-89e4-9f76ef973101
X-Runtime: 0.061594
Vary: Origin
Content-Length: 1511
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
Authorization: Bearer aa5ed31d1fc512a9b51423e871e66126028b8238b1de465b
ETag: W/&quot;d3e0793c0d2cb285058f51531defec2e&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: c22e6607-851e-454f-bc0a-46a73bf1f29a
X-Runtime: 0.041325
Vary: Origin
Content-Length: 184
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
X-Spree-Order-Token: ewpz2_6EL4v1lsYHUb_moA
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/users`

#### Parameters


```json
user[email]=test%40example.com&user[password]=test123&user[password_confirmation]=test123&order_number=M457544359
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
Authorization: Bearer a26713966d884bdcaec6171ea4da677ea66ff701b65b82e4
ETag: W/&quot;e2cf20eeedb9d3657e900d626e9c936b&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: b5cf5a7a-b93f-4033-b66c-b0abe74c49b0
X-Runtime: 0.027257
Vary: Origin
Content-Length: 184
201 Created
```


```json
[binary data]
```



## Subscribe a user


### Request

#### Endpoint

```plaintext
PUT /api/users/7/subscribe
Accept: application/json
Authorizat IO N: Bearer 8d518d7fce870e4192149fb9219332601f61bc9dbfefd721
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
Authorization: Bearer 8d518d7fce870e4192149fb9219332601f61bc9dbfefd721
ETag: W/&quot;4a192acbe880ac328cff0c4887b5648f&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 6608cd0d-a0de-4d87-9ad2-e63e49a67dcc
X-Runtime: 0.029671
Vary: Origin
Content-Length: 185
200 OK
```


```json
[binary data]
```



## Unsubscribe a user


### Request

#### Endpoint

```plaintext
PUT /api/users/8/unsubscribe
Accept: application/json
Authorizat IO N: Bearer 5ed1b0f852e6d1948747537f78bc3c05d0e64a1232d79c52
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
Authorization: Bearer 5ed1b0f852e6d1948747537f78bc3c05d0e64a1232d79c52
ETag: W/&quot;c6879604934a8784ed0ca244dc6ba57d&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 2479edbe-60fc-4dad-9bd8-ec65ca4ba971
X-Runtime: 0.019061
Vary: Origin
Content-Length: 186
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
ETag: W/&quot;aa08f4f534445ac4e73ed84ee1e2239e&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 0ff23a3d-0a32-413b-84de-3cae438c577d
X-Runtime: 0.107294
Vary: Origin
Content-Length: 2013
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
Authorizat IO N: Bearer 0d08b19bbb48ffeb5c931a13fbed5c745e471aecb0af3141
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
ETag: W/&quot;8e19ddbf443b0b7204f14cc0dff16e7f&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 556498a0-cd6b-4882-8011-e610d1bc6a7a
X-Runtime: 0.015862
Vary: Origin
Content-Length: 208
200 OK
```


```json
[binary data]
```



## Remove the payment from the user wallet


### Request

#### Endpoint

```plaintext
DELETE /api/wallet_payment_sources/7
Accept: application/json
Authorizat IO N: Bearer d2c2f408d52c82217b7bf74d50e879a956bbe179bd1fad7c
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
X-Request-Id: c98352b3-3260-4486-ae47-6ff22f94ca4d
X-Runtime: 0.016681
Vary: Origin
204 No Content
```




## Set a wallet payment source as the default user payment method


### Request

#### Endpoint

```plaintext
POST /api/wallet_payment_sources/6/default
Accept: application/json
Authorizat IO N: Bearer f4ae01443a40442b1953d3228f44ec973937f50f5c04a7c3
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
X-Request-Id: 37c1d2b5-7615-4d43-b2c9-45c58b7ed75f
X-Runtime: 0.051483
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
Authorizat IO N: Bearer d25525678c4769c64862fbd1f96363631d1099a078f8a023
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/wished_products`

#### Parameters


```json
wished_product[wishlist_id]=12&wished_product[variant_id]=91&wished_product[quantity]=2&wished_product[remark]=Foo+bar
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
ETag: W/&quot;bd51086cf93ec47c873042a11ea0a060&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: d61dff77-c0a6-4ea0-bfe9-398505d96799
X-Runtime: 0.013558
Vary: Origin
Content-Length: 74
201 Created
```


```json
[binary data]
```



## Delete a wished product


### Request

#### Endpoint

```plaintext
DELETE /api/wished_products/19
Accept: application/json
Authorizat IO N: Bearer f78f8472c0d1cb42d6c8303b48b8de8b4581ca3cda9dafea
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
X-Request-Id: eb22a80e-6228-4aed-b586-602beeedb918
X-Runtime: 0.018473
Vary: Origin
204 No Content
```




## Get a single wished product


### Request

#### Endpoint

```plaintext
GET /api/wished_products/1
Accept: application/json
Authorizat IO N: Bearer f90a59e61f2bb8eb67a087da5abc8b507d838cff3975c4a7
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
ETag: W/&quot;7f3746a7e179b39f087aad435480f30f&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: d3b9af79-b165-49fa-9f73-0e8cfc0eeed8
X-Runtime: 0.037545
Vary: Origin
Content-Length: 67
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
Authorizat IO N: Bearer 6fc31cdac52a164309b1810ee3d6dfd50a210fbde3699838
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
ETag: W/&quot;7251a70ccd7c2c20e2ca69b42ba35cba&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 702f8b4a-67cb-41be-8eb2-8dfc31657b45
X-Runtime: 0.011637
Vary: Origin
Content-Length: 292
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
Authorizat IO N: Bearer d9de799b3b57ff8103ec9455919c0764646082713fad5993
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
ETag: W/&quot;162489b25beea2f0c5a8e084d3d31ed3&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 6b1ab0ba-f826-413b-9230-69fae8686f85
X-Runtime: 0.113403
Vary: Origin
Content-Length: 2263
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
Authorizat IO N: Bearer 9872b33d1dbe5a758b128840840882979c8c3ff5e8dfec67
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
ETag: W/&quot;9fb9d452117bb53b97ec10b9eced1c89&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: a28566b8-bcce-4889-b570-5b22afb6c803
X-Runtime: 0.107443
Vary: Origin
Content-Length: 2206
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
Authorizat IO N: Bearer 7d0bd4d1a931e5fcfae54b15fed9a41e2b65238a4f085703
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
ETag: W/&quot;11f703d4ec4853ed6c396ec399074861&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: cbfbcc46-97ee-4e9f-acc5-8615419a3fcd
X-Runtime: 0.012867
Vary: Origin
Content-Length: 295
200 OK
```


```json
[binary data]
```



## Update a wishlist


### Request

#### Endpoint

```plaintext
PATCH /api/wished_products/16
Accept: application/json
Authorizat IO N: Bearer 8dfcab9f580a0440491eadfd59fbab70b387d6eae6d3d80f
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/wished_products/:id`

#### Parameters


```json
wished_product[wishlist_id]=10&wished_product[variant_id]=83&wished_product[quantity]=2&wished_product[remark]=Foo+bar
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
ETag: W/&quot;2d609dfce77c07afcf8f721553be57cb&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 6e1a81e8-6269-4b09-b1fc-f3ce0dc9e00d
X-Runtime: 0.015086
Vary: Origin
Content-Length: 74
200 OK
```


```json
[binary data]
```



# Wishlists

Get a single wishlist, accessible by owner of the list, or if it is public

## Create a wishlist


### Request

#### Endpoint

```plaintext
POST /api/wishlists
Accept: application/json
Authorizat IO N: Bearer b39ece7fbeac6d6f39c19c013bf02643f6a522909d36130a
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/wishlists`

#### Parameters


```json
wishlist[name]&wishlist[user_id]=85&wishlist[is_default]=true&wishlist[is_public]=false
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
ETag: W/&quot;256a5ddd00518c6a168ee43cd4221c19&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 2fc4cb34-7113-4551-b194-9c969c517c10
X-Runtime: 0.017447
Vary: Origin
Content-Length: 100
201 Created
```


```json
[binary data]
```



## Delete a wishlist


### Request

#### Endpoint

```plaintext
DELETE /api/wishlists/14
Accept: application/json
Authorizat IO N: Bearer ba9266c73faf5bbde9558d79016d4036a72bd92acf847f4c
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
X-Request-Id: cfc9d2b1-5b17-4d6a-ba29-1df469997c32
X-Runtime: 0.015946
Vary: Origin
204 No Content
```




## Get a single wishlist


### Request

#### Endpoint

```plaintext
GET /api/wishlists/13
Accept: application/json
Authorizat IO N: Bearer 5b34868430bd72262d70d47f2325d5732bfba6fbc3f54b50
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
ETag: W/&quot;bb1f57f29a6cd58dbdeeb7f4f9b80951&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 5d17aafd-6007-4bcc-b823-b0c101ac4515
X-Runtime: 0.042815
Vary: Origin
Content-Length: 313
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
Authorizat IO N: Bearer edd92fe0233e9fcc67dd38b2648bcdad2bdbfc810c0b94b3
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
ETag: W/&quot;6b3af24977062cd192063a8b7b0b21d1&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 6ee392cf-a3dd-4a74-8161-b8746332b4b2
X-Runtime: 0.017415
Vary: Origin
Content-Length: 894
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
Authorizat IO N: Bearer 60b85d0d570a509ff8b1cfa4328910a452643a1a3d5a754f
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
ETag: W/&quot;51dec97c41f2643ff7c62327796a9a72&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: a5955f50-7cfa-4b7d-852c-f0fda9e80b7f
X-Runtime: 0.010589
Vary: Origin
Content-Length: 313
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
Authorizat IO N: Bearer 4abc27b0bcb375b497a32d5c6b2024d3315827f0f684e2aa
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
ETag: W/&quot;302cb49c6a927c78d1807f28af1e3b8d&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 35c152f3-db38-4d08-b420-d0e07bfca206
X-Runtime: 0.014947
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
PATCH /api/wishlists/39
Accept: application/json
Authorizat IO N: Bearer c7b5cc221a09de5d75e308a754c8245b1fc6c675fe7235ab
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/wishlists/:id`

#### Parameters


```json
wishlist[name]=Another+Wishlist&wishlist[user_id]=86&wishlist[is_default]=true&wishlist[is_public]=false
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
ETag: W/&quot;45f07686133eeac1c8a6951bcebf719e&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 70f87e48-dbd8-4b1d-b6d1-e8aee75664f3
X-Runtime: 0.018684
Vary: Origin
Content-Length: 317
200 OK
```


```json
[binary data]
```



