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
PUT /api/orders/M837689382/addresses/57
Accept: application/json
X-Spree-Order-Token: YI6gTOt2BH_rREyGGht_EQ
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
X-Request-Id: 120b24a3-62da-4d7a-8eb2-3b202d8c07bd
X-Runtime: 0.067634
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
X-Spree-Order-Token: y8lOgmVGjjnMZqUTduis_w
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/braintree/transactions`

#### Parameters


```json
order_id=M671672096&payment_method_id=13&options[restart_checkout]=true&transaction[email]=maryellen.oga%40mckenziemcglynn.com&transaction[nonce]=fake-paypal-billing-agreement-nonce&transaction[phone]=555-555-0199&transaction[shipping_address_attributes][first_name]=John&transaction[shipping_address_attributes][last_name]=Stamm&transaction[shipping_address_attributes][address_line_1]=A+Different+Road&transaction[shipping_address_attributes][city]=Herndon&transaction[shipping_address_attributes][state_code]=AL&transaction[shipping_address_attributes][zip]=10033&transaction[shipping_address_attributes][country_code]=US&transaction[payment_type]=PayPalAccount&transaction[billing_address_attributes][first_name]=John&transaction[billing_address_attributes][last_name]=Stamm&transaction[billing_address_attributes][address_line_1]=A+Different+Road&transaction[billing_address_attributes][city]=Herndon&transaction[billing_address_attributes][state_code]=AL&transaction[billing_address_attributes][zip]=10033&transaction[billing_address_attributes][country_code]=US
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
ETag: W/&quot;2ef450e11263d5b1172d4032a8ead971&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 74d677f5-72aa-48a6-abeb-03a446b627ac
X-Runtime: 0.403639
Vary: Origin
Content-Length: 5410
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
X-Spree-Order-Token: OOnJyfD_wnCWgn-3Rk_RpQ
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/braintree/transactions`

#### Parameters


```json
order_id=M311954888&payment_method_id=12&options[restart_checkout]=true&transaction[email]=maryellen.oga%40mckenziemcglynn.com&transaction[nonce]=fake-apple-pay-visa-nonce&transaction[phone]=555-555-0199&transaction[shipping_address_attributes][first_name]=John&transaction[shipping_address_attributes][last_name]=Stamm&transaction[shipping_address_attributes][address_line_1]=A+Different+Road&transaction[shipping_address_attributes][city]=Herndon&transaction[shipping_address_attributes][state_code]=AL&transaction[shipping_address_attributes][zip]=10031&transaction[shipping_address_attributes][country_code]=US&transaction[payment_type]=ApplePayCard
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
ETag: W/&quot;f803bc598d2f9a8ef8f270efec53bb11&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: ae9ae30c-49f2-4de7-93e7-d703846fb4fd
X-Runtime: 0.482637
Vary: Origin
Content-Length: 5456
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
PUT /api/checkouts/M838872355/complete
Accept: application/json
X-Spree-Order-Token: 9WqiZwBxfIZhmOwHXeIYDA
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
ETag: W/&quot;86ca59a12c1f70dc0ab1bbb37afd0e75&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: dc83af13-0e2a-4442-9fff-1f49799d901e
X-Runtime: 0.542981
Vary: Origin
Content-Length: 5579
200 OK
```


```json
[binary data]
```



## Processing the checkout payment step with a not yet existing ApplePay payment


### Request

#### Endpoint

```plaintext
PATCH /api/checkouts/M198728938
Accept: application/json
X-Spree-Order-Token: LIINzpHIMy-M1c63iq0Grw
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
ETag: W/&quot;18ff3c2383f2a45542f6699ca984e1a8&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 28360a8e-c323-4b21-9b04-fa5e30f90280
X-Runtime: 0.202248
Vary: Origin
Content-Length: 4963
200 OK
```


```json
[binary data]
```



## Processing the checkout payment step with a not yet existing PayPal payment


### Request

#### Endpoint

```plaintext
PATCH /api/checkouts/M693792610
Accept: application/json
X-Spree-Order-Token: TcaGidMVk9cOu_TwNkwPnw
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=18&order[payment_attributes][][source_attributes][nonce]=fake-paypal-billing-agreement-nonce&order[payment_attributes][][source_attributes][payment_type]=PayPalAccount&order[payment_attributes][][source_attributes][reusable]=true
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
ETag: W/&quot;35cf6586b6ee050593e5a1f73464193f&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 7fafcacb-b6e2-43b9-ba2e-ce54067f1677
X-Runtime: 0.178673
Vary: Origin
Content-Length: 4963
200 OK
```


```json
[binary data]
```



## Processing the checkout payment step with a not yet existing credit card payment


### Request

#### Endpoint

```plaintext
PATCH /api/checkouts/M363795228
Accept: application/json
X-Spree-Order-Token: hHby1KZdbQrk-tkGfng7-w
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=16&order[payment_attributes][][source_attributes][nonce]=fake-valid-visa-nonce&order[payment_attributes][][source_attributes][payment_type]=CreditCard&order[payment_attributes][][source_attributes][reusable]=true
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
ETag: W/&quot;0d5faf8302d0e1cd9913af1f867b65fb&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 4aba62b1-0a26-4e44-b1c7-4599811c62a3
X-Runtime: 0.184731
Vary: Origin
Content-Length: 4963
200 OK
```


```json
[binary data]
```



## Processing the checkout payment step with an already existing payment


### Request

#### Endpoint

```plaintext
PATCH /api/checkouts/M246824482
Accept: application/json
X-Spree-Order-Token: Nk7qcYQLOwEfeqYIUhU3Jw
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/checkouts/:id`

#### Parameters


```json
order[payment_attributes][][payment_method_id]=19&order[payment_attributes][][source_attributes][wallet_payment_source_id]=5
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
ETag: W/&quot;decbc9989186f054bc2b5eb2d4c60fb3&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: ee282ed6-254d-4428-80c4-bed95a53d189
X-Runtime: 0.217622
Vary: Origin
Content-Length: 4963
200 OK
```


```json
[binary data]
```



## update address


### Request

#### Endpoint

```plaintext
PUT /api/checkouts/M218910159
Accept: application/json
X-Spree-Order-Token: w1B5tg9NtoF97rWcKp_wzw
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PUT /api/checkouts/:id`

#### Parameters


```json
order[ship_address_attributes][id]&order[ship_address_attributes][firstname]=John&order[ship_address_attributes][lastname]&order[ship_address_attributes][address1]=10+Lovely+Street&order[ship_address_attributes][address2]=Northwest&order[ship_address_attributes][city]=Herndon&order[ship_address_attributes][zipcode]=10045&order[ship_address_attributes][phone]=555-555-0199&order[ship_address_attributes][state_name]&order[ship_address_attributes][alternative_phone]=555-555-0199&order[ship_address_attributes][company]=Company&order[ship_address_attributes][state_id]=48&order[ship_address_attributes][country_id]=48&order[ship_address_attributes][created_at]&order[ship_address_attributes][updated_at]&order[use_billing]=true&hold_state=true
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
ETag: W/&quot;0b368801ebc6a8e18bb900f41a99c691&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 9dcfef7e-5296-47a0-a4fd-7b80d19a7122
X-Runtime: 0.192162
Vary: Origin
Content-Length: 4868
200 OK
```


```json
[binary data]
```



# Giftwrap

Delete giftwrap related to shipment

## Create Giftwrap


### Request

#### Endpoint

```plaintext
POST /api/shipments/H41814632818/giftwrap
Accept: application/json
X-Spree-Order-Token: IZWhfeu6vkFM1l7lY5Zjvw
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/shipments/:shipment_number/giftwrap`

#### Parameters


```json
order_number=M435308095
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
X-Request-Id: a00e78c5-8e7e-471a-a0d4-81e68aed48df
X-Runtime: 0.059856
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
DELETE /api/shipments/H01175605260/giftwrap
Accept: application/json
X-Spree-Order-Token: oNRy50hHhNVA2DP390R64A
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`DELETE /api/shipments/:shipment_number/giftwrap`

#### Parameters


```json
order_number=M102008234
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
X-Request-Id: b96b2a0f-5d4b-4755-a73f-3daa4b51eafa
X-Runtime: 0.056673
Vary: Origin
204 No Content
```




# LineItem

Representation of a single cart item for a specific variant with price of vendor

## Creating a line item


### Request

#### Endpoint

```plaintext
POST /api/orders/M773847913/line_items
Accept: application/json
X-Spree-Order-Token: HaqoM_vWBpYmWog03MNHHw
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/:order_number/line_items`

#### Parameters


```json
line_item[variant_id]=18&line_item[options][vendor_id]=42
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
ETag: W/&quot;797edcf1c2ce21287b17a387e1e447a1&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: d77709cd-24bc-448f-bec3-5dcdc6398c77
X-Runtime: 0.223413
Vary: Origin
Content-Length: 929
201 Created
```


```json
[binary data]
```



## Creating a line item gift card


### Request

#### Endpoint

```plaintext
POST /api/orders/M047639958/line_items
Accept: application/json
X-Spree-Order-Token: 2uGi-L7tZMZ1Ace6OJ03BQ
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/:order_number/line_items`

#### Parameters


```json
line_item[variant_id]=28&line_item[options][vendor_id]=65&line_item[options][gift_card_details][recipient_name]=Recipient+John&line_item[options][gift_card_details][recipient_email]=recipient%40email.com&line_item[options][gift_card_details][purchaser_name]=Purchaser+Bob&line_item[options][gift_card_details][gift_message]=Surprise&line_item[options][gift_card_details][send_email_at]=2020-03-16+17%3A07%3A57+-0400
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
ETag: W/&quot;4bd34b5414ddc01e06e807a1d56e0c01&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: fc6b36fe-3598-44c6-830b-ef7656da3794
X-Runtime: 0.324341
Vary: Origin
Content-Length: 1073
201 Created
```


```json
[binary data]
```



## Deleting a line item


### Request

#### Endpoint

```plaintext
DELETE /api/orders/M742307904/line_items/10
Accept: application/json
X-Spree-Order-Token: DIWVuL3UlwRWFfrvuB99Rw
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
X-Request-Id: c98377cd-298e-419b-8879-dffb6f9a2d4a
X-Runtime: 0.093177
Vary: Origin
204 No Content
```




## Updating a line item


### Request

#### Endpoint

```plaintext
PUT /api/orders/M828845365/line_items/9
Accept: application/json
X-Spree-Order-Token: rV40_6kR7MLSj8axac18CQ
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
ETag: W/&quot;1035ed5f9a92754c25c98a0efe5c6a44&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 622c63e9-d220-4124-b16c-d53d05e93e64
X-Runtime: 0.132500
Vary: Origin
Content-Length: 933
200 OK
```


```json
[binary data]
```



# Minis

Destroy a mini. Users can destroy their own minis, admins can destroy any.

## Create a mini


### Request

#### Endpoint

```plaintext
POST /api/minis
Accept: application/json
Authorizat IO N: Bearer e2a0d4b4b97b0eb877300b607c7c2f9c8a42b0e2ae3cda16
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/minis`

#### Parameters


```json
mini[name]=Winny&mini[user_id]=65&mini[birth_year]=2019&mini[birth_month]=1&mini[birth_day]=1
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
ETag: W/&quot;c9f9470eeb16f6e29cac4c55cceaeccb&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: fd573846-ca75-485e-a5cb-eaa6a402f21a
X-Runtime: 0.020561
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
DELETE /api/minis/1
Accept: application/json
Authorizat IO N: Bearer 0aaec437f40023638cc255eb73485a8cf4d7d71a9ffb6b0d
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
X-Request-Id: ab391f15-f041-4d3e-aa6c-97fd9b7567b4
X-Runtime: 0.030115
Vary: Origin
204 No Content
```




## Get a single mini


### Request

#### Endpoint

```plaintext
GET /api/minis/4
Accept: application/json
Authorizat IO N: Bearer 16c1bf0dae264783339002ef330556da804b47b2a02a2928
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
ETag: W/&quot;119212173062c94f59844c12f5786d0f&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 4b3853f2-e0ae-4d5f-a4b4-f34833cd2da0
X-Runtime: 0.012569
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
Authorizat IO N: Bearer 1661afc28f90eed83e1cce8542e6978896fa445a074c71e0
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
ETag: W/&quot;e27bd09d913ea1cd732171a539be6a60&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 3cf30306-fdee-45cd-a6ab-e21d1046eac8
X-Runtime: 0.041368
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
Authorizat IO N: Bearer ca9eee2dabaf973d809a6eaf2bf51cbc1f004dfb6bc94475
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
ETag: W/&quot;9abfae51f40e591d424bd3a74bb31180&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: b14ee607-6574-4007-9f84-57581d15aae2
X-Runtime: 0.017975
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
PATCH /api/minis/3
Accept: application/json
Authorizat IO N: Bearer 3c06928d3b8341474ff0eda05516ba12d56cec501b744d28
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
ETag: W/&quot;57e5eb093ece8b0403cfe92bd4078990&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 4b5cd1de-0b71-40bf-9239-e55f4b72cb46
X-Runtime: 0.015186
Vary: Origin
Content-Length: 163
200 OK
```


```json
[binary data]
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
user_id&order_token&line_item[variant_id]=64&line_item[quantity]=1&line_item[vendor_id]=132&line_item[gift_card_details_attributes][recipient_name]=Recipient+John&line_item[gift_card_details_attributes][recipient_email]=recipient%40email.com&line_item[gift_card_details_attributes][purchaser_name]=Purchaser+Bob&line_item[gift_card_details_attributes][gift_message]=Surprise&line_item[gift_card_details_attributes][send_email_at]=2020-03-16
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
ETag: W/&quot;b77ffa7c3923b006e804b64ef36090e6&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: f47c70f7-2499-45bd-87c7-69b66a831cd0
X-Runtime: 0.172095
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
user_id&order_token&line_item[variant_id]=44&line_item[quantity]=2&line_item[vendor_id]=91
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
ETag: W/&quot;be4df182259d01c5381aa2a07f8bbf02&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 65f708dc-b07d-4abc-90ee-442398cf7c70
X-Runtime: 0.110686
Vary: Origin
Content-Length: 2663
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
user_id&order_token&line_item[variant_id]=48&line_item[quantity]=2&line_item[vendor_id]=99
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
ETag: W/&quot;f2270de58195f8bbe27692837c3e1d8a&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: f37f4815-0001-4d50-bd5e-d9668838bcc1
X-Runtime: 0.126181
Vary: Origin
Content-Length: 2663
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
Authorizat IO N: Bearer 94ef12da6b535a7b5de64599aad718091cf6d9bc1c374301
X-Spree-Order-Token: 
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/cart`

#### Parameters


```json
user_id&order_token&line_item[variant_id]=52&line_item[quantity]=2&line_item[vendor_id]=107&user_token=Bearer+94ef12da6b535a7b5de64599aad718091cf6d9bc1c374301
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
ETag: W/&quot;1ffea8dc571fe76a5a00d1d0e5bc6e99&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 2736b0fd-4f19-4149-b3b5-98fb867abf8f
X-Runtime: 0.130216
Vary: Origin
Content-Length: 2677
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
X-Spree-Order-Token: C61s2RJshFVUEEytTP1QPA
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders/cart`

#### Parameters


```json
user_id&order_token=C61s2RJshFVUEEytTP1QPA&line_item[variant_id]=60&line_item[quantity]=2&line_item[vendor_id]=123
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
ETag: W/&quot;48a966010688cdbe0928f0e237e228c7&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 7d602f97-c865-497d-87d0-643778906212
X-Runtime: 0.277662
Vary: Origin
Content-Length: 5516
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
Authorizat IO N: Bearer 81887abcfbbe03d20d24aeeff751235e993f9e0b17b59b24
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
X-Request-Id: b6ad7ef6-848a-49fc-8efc-628ccd74a0ce
X-Runtime: 0.013524
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
GET /api/orders/M573675664
Accept: application/json
Authorizat IO N: Bearer d181b9fa0211e16dc208474442f8bf212a1e17caaecc59c3
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
ETag: W/&quot;96193a2984ca715b60d6d255d6ffe8b1&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 0bc250f5-5be0-483d-ae70-9b7234295241
X-Runtime: 0.221221
Vary: Origin
Content-Length: 8018
200 OK
```


```json
[binary data]
```



## it returns a 401


### Request

#### Endpoint

```plaintext
GET /api/orders/M088066909
Accept: application/json
Authorizat IO N: 8858f06e1d16deba1c611bb8576f254c794b534d0e54f748
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
X-Request-Id: df206ec0-9d7d-4a39-8d65-e8e6981ba848
X-Runtime: 0.025414
Vary: Origin
Content-Length: 58
401 Unauthorized
```


```json
[binary data]
```



# Passwords

Reset password by token

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
user[email]=email84%40example.com
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
X-Request-Id: 60af171b-a996-474c-83b4-d14306b5f8dd
X-Runtime: 0.003358
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
user[email]=email85%40example.com&user[password]=secret
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
Authorization: Bearer 2a00f1cb0a7d535621047bcf9f87091189b8597929b9f59d
ETag: W/&quot;eef27e821f206ac21f1bb5862396d836&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 109ac490-4b5e-472d-813e-9857072cf4bc
X-Runtime: 0.008939
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
X-Request-Id: 539231ba-24cb-4988-b9a4-f22113ea3b8a
X-Runtime: 0.025677
Vary: Origin
204 No Content
```




# Products

get products by taxon

## Fetch a single product by id


### Request

#### Endpoint

```plaintext
GET /api/products/product-75-7653
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
Date: Mon, 16 Mar 2020 21:08:12 GMT
Surrogate-Control: max-age=900
Surrogate-Key: product_id=1
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;301e5ac8ad38470abb10a40593ee682a&quot;
X-Request-Id: 5973d862-b268-4a59-88df-e1ad4f031dfb
X-Runtime: 0.064908
Vary: Origin
Content-Length: 1601
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
Date: Mon, 16 Mar 2020 21:08:11 GMT
Surrogate-Control: max-age=900
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;431c9b7f4a5c8e7341a9a047a59d5f1d&quot;
X-Request-Id: bc527099-6869-4bcd-b7c9-adcba56986b7
X-Runtime: 0.075462
Vary: Origin
Content-Length: 1273
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
Date: Mon, 16 Mar 2020 21:08:11 GMT
Surrogate-Control: max-age=900
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;846fbe2a3b2ba64e7ee7a3e71c9322a7&quot;
X-Request-Id: 12f0a746-1823-48ec-b82b-da9fb2c03b03
X-Runtime: 0.034113
Vary: Origin
Content-Length: 359
200 OK
```


```json
[binary data]
```



## Fetch multiple products by id


### Request

#### Endpoint

```plaintext
GET /api/products?ids=71%2C72%2C73
Host: example.org
Cookie: 
```

`GET /api/products`

#### Parameters


```json
ids: 71,72,73
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
Date: Mon, 16 Mar 2020 21:08:11 GMT
Surrogate-Control: max-age=900
Content-Type: application/json; charset=utf-8
Cache-Control: max-age=900, public
ETag: W/&quot;08cd98ee984d2da5958a76c1de478400&quot;
X-Request-Id: d74a8a41-7369-46c9-a00d-66e3b2412275
X-Runtime: 0.112663
Vary: Origin
Content-Length: 2817
200 OK
```


```json
[binary data]
```



## Fetch products by taxon id


### Request

#### Endpoint

```plaintext
GET /api/taxons/products?id=3
Host: example.org
Cookie: 
```

`GET /api/taxons/products`

#### Parameters


```json
id: 3
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
ETag: W/&quot;8e66b1b8e0eee890af20a5a0fa3600eb&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: dd500c88-a8df-49bb-ac29-d7b03c6f6cfc
X-Runtime: 0.088910
Vary: Origin
Content-Length: 1294
200 OK
```


```json
[binary data]
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
ETag: W/&quot;0896e80617a40bc705a689ee4fbde9bb&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 6e5caeb1-81d7-426e-94a6-02ed8cd8755a
X-Runtime: 0.052080
Vary: Origin
Content-Length: 1290
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
Authorizat IO N: Bearer b120f92e7785d6a0afcb12e7f0af37d985b8342790476039
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
X-Request-Id: dec780e5-e1df-4b70-89cf-b1ef250a8b50
X-Runtime: 0.035954
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
X-Request-Id: 19670a0f-941a-451a-86a2-c5b6da44a4da
X-Runtime: 0.016392
Vary: Origin
Content-Length: 65
404 Not Found
```


```json
[binary data]
```



# Recently Viewed Products

Store a recently viewed variant with a logged in user or session token

## Get all recently viewed products


### Request

#### Endpoint

```plaintext
GET /api/recently_viewed?recently_viewed[session_id]=e1jv53dgf2np5h0titk96u2sqdyeu74n984xhgm2s54tustrava8nxou6iks68s7vlwemq0udmj2xblgj45bmi8l7rh1bi4h8vbminkxmf1yjxfdmqeux26hjvmvhmjxrmm2uv7jueimzu0zub797af5yn54hmcqqd4b222qpdgt8yfqhv21fnm2dvpkkf3v7wkeb32himg8k5a3gxbnj2remv7o7yig842s1cvltz2joaifkgfrhu4ejpdva8w
Accept: application/json
Authorizat IO N: Bearer f6cb82bf3843c04b0610e1c815e1bd77ff79238344ce1c59
Host: example.org
Cookie: 
```

`GET /api/recently_viewed`

#### Parameters


```json
recently_viewed: {&quot;session_id&quot;=&gt;&quot;e1jv53dgf2np5h0titk96u2sqdyeu74n984xhgm2s54tustrava8nxou6iks68s7vlwemq0udmj2xblgj45bmi8l7rh1bi4h8vbminkxmf1yjxfdmqeux26hjvmvhmjxrmm2uv7jueimzu0zub797af5yn54hmcqqd4b222qpdgt8yfqhv21fnm2dvpkkf3v7wkeb32himg8k5a3gxbnj2remv7o7yig842s1cvltz2joaifkgfrhu4ejpdva8w&quot;}
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
ETag: W/&quot;8c3238b6aa74f6f005cf71c9dd1b6860&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 56c546ca-5376-4f7f-9252-660b834a9e68
X-Runtime: 0.014971
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
Authorizat IO N: Bearer e43854c3182a805034e88bbd06ec870283367f6a63acaa2d
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/recently_viewed`

#### Parameters


```json
recently_viewed[session_id]=vzhn4cdt7a6cq39z2bp1fht3uztox78gmzffq0nbhib0k1zkekpvx0haxwybfun6zcfe2tfe6f33ibyzfn8b3qgjorr5a9gcdhkc8xfxlqs7wzinml0e73sgmtf23zdk2bnh1upessn7jzssdeyphvsj2ftiu95m9nto9pvm1dhoflvf69du41rzhvdvs2gjughfy7yfwx5704j5oh9m2xznrvasuos5967p28k9bwpyoyalpttfqjhw4021bgb&recently_viewed[variant_id]=foo
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
X-Request-Id: 95052397-405c-45db-a248-855eb2e14c43
X-Runtime: 0.034060
Vary: Origin
204 No Content
```




# Return Authorizations

Get a single user return authorziation

## Can get another user&#39;s return authorization


### Request

#### Endpoint

```plaintext
GET /api/returns/RA601075234
Authorizat IO N: Bearer c7a746a7ec6830cb0ed6ae23819d2d2c307ce43a8b5f2259
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
ETag: W/&quot;adfb26a4db56faa761faef280387e4ff&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 388dff1a-5744-4ec3-9ac1-e9c9ece95fde
X-Runtime: 0.046745
Vary: Origin
Content-Length: 2948
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
Authorizat IO N: Bearer 3617350bdf839a372a91947e06d1ebdea296b5caa8ba52c2
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
ETag: W/&quot;fda622aa07bf0abb0a8e1c02875b99eb&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: e5efb449-c661-407f-985f-1fe823e675e1
X-Runtime: 0.008287
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
GET /api/returns/RA860085443
Authorizat IO N: Bearer 938bf99df37cef20a15665b442165e5392ea4f60a4ce25b5
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
ETag: W/&quot;0d0ee8de8d87bf58f00e7e445fe84ced&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: ddaa8fd3-4047-455a-9678-495865f8a7de
X-Runtime: 0.101593
Vary: Origin
Content-Length: 2869
200 OK
```


```json
[binary data]
```



## returns a 404


### Request

#### Endpoint

```plaintext
GET /api/returns/RA303340580
Authorizat IO N: Bearer 6c1bae61c4e592753e66652541cdcc9930fa5761edced064
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
X-Request-Id: fce49bd5-e808-4a98-8ec4-c1d2748fa6a7
X-Runtime: 0.016015
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
stock_request[email]=velda%40haagcremin.name&stock_request[variant_id]=143
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
X-Request-Id: ff34feb2-91d9-401c-893a-3ecce4d6ab59
X-Runtime: 0.046138
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
stock_request[email]=foo&stock_request[variant_id]=145
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
X-Request-Id: c2be14b3-b49a-487c-801a-3e0711ad18f6
X-Runtime: 0.007217
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
stock_request[email]=otis%40blanda.us&stock_request[variant_id]=147
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
X-Request-Id: 1f9ee15a-b8cf-4c63-b2bd-0a3e76966f5b
X-Runtime: 0.006526
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
Authorizat IO N: Bearer 4d4f41328acac31144921300e519c715abcbaf9e2aa27713
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
ETag: W/&quot;4b12a50a7781d279c3d9fc39a2d5248b&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: c18d9a73-c38d-4f94-b081-b96c2e20d60d
X-Runtime: 0.038161
Vary: Origin
Content-Length: 218
200 OK
```


```json
[binary data]
```



# Subscribers

Create a subscriber using the provided email. If a logged in user creates a subscriber the record                 will automatically be associated with the user's account. If a user is already subscribed, nothing                 will happen unless any additional parameters are included and are different than what is current.
                Status can not be set on create.

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
subscriber[email]=harvey%40terry.biz&subscriber[first_name]=Lena&subscriber[last_name]=Runte&subscriber[source]=Quia+quisquam+qui+qui+reiciendis+saepe+asperiores+distinctio.
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
ETag: W/&quot;777433bda71b663114bdd5b7f2078d9a&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 3a4e93f4-bf4d-4c10-96be-a06b747616f4
X-Runtime: 0.203341
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
Authorizat IO N: Bearer 55c411f29921ca5fc795e4ac8867b6ed65f7e6183a0541ba
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/subscribers`

#### Parameters


```json
subscriber[email]=ian.koss%40hilll.biz&subscriber[first_name]=Keila&subscriber[last_name]=Yundt&subscriber[source]=Vel+excepturi+vitae+officia+at+incidunt+corrupti.
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
ETag: W/&quot;cbcb96eab17bbf9d4d5447c42235d508&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: ea7362c7-ae6b-4442-bb75-fe802d018dd2
X-Runtime: 0.025189
Vary: Origin
Content-Length: 231
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
Authorizat IO N: Bearer efd61ededae4643505dadd8faeae045bf8e0d39fdf99b70c
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
ETag: W/&quot;5a3363174e341b0f48aaa44e76a83e5f&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: e3e47657-8586-4f64-86e2-b9d720e29034
X-Runtime: 0.022747
Vary: Origin
Content-Length: 676
200 OK
```


```json
[binary data]
```



## Update a subscriber


### Request

#### Endpoint

```plaintext
PATCH /api/subscribers/3
Accept: application/json
Authorizat IO N: Bearer adfe64f0bd1805e9c3852a8a542aefe09f74622d72fd3ff1
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/subscribers/:id`

#### Parameters


```json
subscriber[source]=Occaecati+id+assumenda+veritatis+reiciendis+molestias.
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
ETag: W/&quot;9bed8e88dc88f5fae47ed16fa6e1965c&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: e2d3dcca-f617-4434-9da3-11b4ee79499c
X-Runtime: 0.042816
Vary: Origin
Content-Length: 252
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
Authorizat IO N: Bearer 34e6263ee0593ec5f10367bbecea7eb98b56d69ea83d68a1
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`DELETE /api/subscribers`

#### Parameters


```json
subscriber[email]=email4%40example.com
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
X-Request-Id: 68acf7a7-e7a0-49f6-8458-3c72e11335e4
X-Runtime: 0.009090
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
Authorizat IO N: Bearer 2d51325784c8873cc8778cbf7c3cf2e8a0c76836f79bfb03
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`DELETE /api/subscribers`

#### Parameters


```json
subscriber[email]=kayla_gutkowski%40kohler.biz
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
X-Request-Id: 44cf48bc-8487-4e95-b421-05aa98800022
X-Runtime: 0.006137
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
Authorizat IO N: Bearer 1692f5bb2921088e42061ae0658f7b5215ea0c6d83005818
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
X-Request-Id: 43cf7516-b1dd-4223-a2d9-67200b1da726
X-Runtime: 0.051453
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
ETag: W/&quot;016c0d38dbfd3539595b1490c4af9c11&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 72a307eb-a42a-46ac-9b8e-6ab4fe44e5f3
X-Runtime: 0.065012
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
ETag: W/&quot;7212ade8773b5f1e3910ad018a6a6579&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 3412f51e-610f-48dd-8c87-36f7d35ed4dc
X-Runtime: 0.014475
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
ETag: W/&quot;7c9316dca706bfa2b873d622e959d9ce&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: feb2306b-196a-47fc-8968-ccc8f00d9c6a
X-Runtime: 0.029323
Vary: Origin
Content-Length: 2670
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
ETag: W/&quot;51944f6d48ed832b8eb5d1ddda6c86d7&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: be9469a2-5f3a-4b26-b19d-7dde3ef9c7ad
X-Runtime: 0.004234
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
user[email]=email16%40example.com&user[password]=secret
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
Authorization: Bearer 3efe91c3144e81253c9f992289164aed02b9d9a984ede795
ETag: W/&quot;75bd4943cca6cb0253b494fdfb37cc6b&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 777cd578-aaa1-450d-98dc-682b99ec2d6e
X-Runtime: 0.010400
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
X-Spree-Order-Token: bjVsu4uWfFfAKGkYcOtNbw
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/users/login`

#### Parameters


```json
user[email]=email17%40example.com&user[password]=secret&order_number=M596585983
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
Authorization: Bearer 82f26f600c3eadc13f4224a754e67b594c7a9c68aa1ab0ae
ETag: W/&quot;b87ac2c1bd09831d385ca492223d4a24&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 58191a1e-2dc2-473d-905e-b5ee03fe4dc1
X-Runtime: 0.013185
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
Authorizat IO N: Bearer 42fc52505a2c286aa4be5e86b6b3e1233eaacd652c0e85b9
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
Authorization: Bearer 42fc52505a2c286aa4be5e86b6b3e1233eaacd652c0e85b9
ETag: W/&quot;4884927ae65e3f8985d7b33fb84bd2e7&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 27053328-467d-4ed8-957f-06b61aafb6ed
X-Runtime: 0.028922
Vary: Origin
Content-Length: 1515
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
Authorization: Bearer 4ae3248344b00928a9bcf4ba75946726495043030c32061c
ETag: W/&quot;3d57176beb03931a4b31a11608fb56ed&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 6be1c9e3-8c93-4c27-b635-5395f3e976a3
X-Runtime: 0.047627
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
X-Spree-Order-Token: lFA__tCIe7JaGG19IE1Ykw
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/users`

#### Parameters


```json
user[email]=test%40example.com&user[password]=test123&user[password_confirmation]=test123&order_number=M595940605
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
Authorization: Bearer 24ffba133232468cfbcdc76f0bafcdede6ece1fe11973ebd
ETag: W/&quot;d50a2905df31a6e0571cf56c1eaa3256&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: feeae407-8f1b-4a36-b235-8b27409f4214
X-Runtime: 0.043594
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
PUT /api/users/16/subscribe
Accept: application/json
Authorizat IO N: Bearer 74931b7f854b1c869a10ec172e62a5b70e479e344950796a
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
Authorization: Bearer 74931b7f854b1c869a10ec172e62a5b70e479e344950796a
ETag: W/&quot;cabc38b61818fa7ff0e22ad6b2e57fc5&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: a1fa7664-e1a8-4c1a-a3ff-e9d582569fc2
X-Runtime: 0.023568
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
PUT /api/users/15/unsubscribe
Accept: application/json
Authorizat IO N: Bearer e140ed311dcaa0eb3fa6e25852ae5cffee90e1b6323724c8
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
Authorization: Bearer e140ed311dcaa0eb3fa6e25852ae5cffee90e1b6323724c8
ETag: W/&quot;8d6d3bea8c690da7936cdb0b015d0a7f&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 1db7212b-8053-4b91-ad70-16cc9da7b48e
X-Runtime: 0.023778
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
GET /api/variants/141
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
ETag: W/&quot;e628c082ffbb2162ace813518d601a01&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 43d63abc-ceb5-42c3-b649-5f8f0700412b
X-Runtime: 0.096396
Vary: Origin
Content-Length: 2018
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
Authorizat IO N: Bearer 98b8e373ea42aab63df68aa7442967a87882ee696ea8d3b6
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
ETag: W/&quot;8d304de3e2998040e69b0f4701758d6e&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 21139fc2-a5ac-4b3a-851a-c3aa1656a42d
X-Runtime: 0.037057
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
DELETE /api/wallet_payment_sources/8
Accept: application/json
Authorizat IO N: Bearer 7b6320a9f08b9abb7a91e6790addebbdb77acf966db6914a
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
X-Request-Id: dba96396-7244-408f-9d1a-1640c480c07f
X-Runtime: 0.016405
Vary: Origin
204 No Content
```




## Set a wallet payment source as the default user payment method


### Request

#### Endpoint

```plaintext
POST /api/wallet_payment_sources/7/default
Accept: application/json
Authorizat IO N: Bearer ee24f409d3280fd71afdc35e808c970fcba35416ce7f7a7a
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
X-Request-Id: 0a19381e-a306-4a8f-84d7-4699e033143b
X-Runtime: 0.017649
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
Authorizat IO N: Bearer 8171ca0bb49c6e29e6abb9c550cf5c1da89515d4d2bff97b
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/wished_products`

#### Parameters


```json
wished_product[wishlist_id]=12&wished_product[variant_id]=110&wished_product[quantity]=2&wished_product[remark]=Foo+bar
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
ETag: W/&quot;f2636188a43b5d3b3583fc81953cf7b7&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: cb2b0b78-9646-4108-9296-8a5ccf784a9a
X-Runtime: 0.016163
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
DELETE /api/wished_products/16
Accept: application/json
Authorizat IO N: Bearer e0551ff9f1a8ccf794199ce6a89dc2d9f3ac8545251831d3
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
X-Request-Id: b859e679-8320-4d47-b78d-854608d44450
X-Runtime: 0.014856
Vary: Origin
204 No Content
```




## Get a single wished product


### Request

#### Endpoint

```plaintext
GET /api/wished_products/7
Accept: application/json
Authorizat IO N: Bearer f03bf9b29283af56e144390fea0d013c07d13f654a248522
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
ETag: W/&quot;55821928b9dfe032c57561c5d40b55f7&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 290bed41-5869-4036-891b-cd42cd7217b9
X-Runtime: 0.017633
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
Authorizat IO N: Bearer 557b89ad1ad1ee1847600f8acf0f89b35d070901aec4201d
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
ETag: W/&quot;6f140f7fdd5bd4ba0c7bb30804201fb6&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 63158591-28de-4918-9313-b589b6fba720
X-Runtime: 0.012606
Vary: Origin
Content-Length: 295
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
Authorizat IO N: Bearer 305d3db57ca726cbb520f4f57ae5af02f787500ef200d0ca
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
ETag: W/&quot;fceb5c1b042ec209a20e588a9e47d070&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 32ca1270-2970-461b-95d9-d6fa73301811
X-Runtime: 0.125898
Vary: Origin
Content-Length: 2203
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
Authorizat IO N: Bearer 99ec558a6f1c1a4e0f3a511b345bb26986f98901cfa99f60
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
ETag: W/&quot;826709a79f4b344e0eedd0ad0ffb792d&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 3e6a37c3-0de8-40af-959d-05bbeb569e9e
X-Runtime: 0.105370
Vary: Origin
Content-Length: 2264
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
Authorizat IO N: Bearer 41efd01ae792300f57cb12f98a4e3263926404c06d17ad34
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
ETag: W/&quot;1b3a0ac5f1a5a292fa4b769b0cb5a4cf&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: f9bca71b-d948-45ce-bfd8-343ca6e8ca9f
X-Runtime: 0.037428
Vary: Origin
Content-Length: 292
200 OK
```


```json
[binary data]
```



## Update a wishlist


### Request

#### Endpoint

```plaintext
PATCH /api/wished_products/19
Accept: application/json
Authorizat IO N: Bearer 491220127dd9e3cc54b15818c379505bd764d9d2bdce58e9
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/wished_products/:id`

#### Parameters


```json
wished_product[wishlist_id]=11&wished_product[variant_id]=108&wished_product[quantity]=2&wished_product[remark]=Foo+bar
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
ETag: W/&quot;26205a07afc71b0d6c242df86f096b17&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: ad43aabf-bb45-43ec-b948-901946c99cc8
X-Runtime: 0.015442
Vary: Origin
Content-Length: 75
200 OK
```


```json
[binary data]
```



# Wishlists

Get a users wishlists

## Create a wishlist


### Request

#### Endpoint

```plaintext
POST /api/wishlists
Accept: application/json
Authorizat IO N: Bearer f3298cf2a2a83d107cd4af41f39c166498533caa92b73211
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/wishlists`

#### Parameters


```json
wishlist[name]&wishlist[user_id]=48&wishlist[is_default]=true&wishlist[is_public]=false
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
ETag: W/&quot;dff47ebfb88a1270148ecff415fa849d&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 6f4f0468-6763-4ea6-bc9a-77dea0185675
X-Runtime: 0.017560
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
DELETE /api/wishlists/30
Accept: application/json
Authorizat IO N: Bearer 5894c08d99bfdc5017ee5e7350d7f5b0ee746aa6c56920f6
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
X-Request-Id: e25d52ee-4bc5-4da8-ba64-245b242d88ec
X-Runtime: 0.015016
Vary: Origin
204 No Content
```




## Get a single wishlist


### Request

#### Endpoint

```plaintext
GET /api/wishlists/27
Accept: application/json
Authorizat IO N: Bearer f0e1aedcf01524f6e550206b5865311d80de4a25da245827
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
ETag: W/&quot;dc1c29a662221ce285317bb4543a3dd5&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 15ea5d38-460d-4c6a-b07f-f733c3203561
X-Runtime: 0.012743
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
Authorizat IO N: Bearer f699a7768e8b55760f9b2fc5654d69cd497144a8a6c79807
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
ETag: W/&quot;21cc545e456b2ab35eab93b9d4c3e14c&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 48632316-27ab-42be-a63f-14fd867f6e0d
X-Runtime: 0.015922
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
Authorizat IO N: Bearer c5132e381983058d65b91a2549110f5730b01d76d788e2e1
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
ETag: W/&quot;83a2a463797d5e397701cdd91d5befd3&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 7498d37a-a556-429a-8f3d-5bf6793d2b82
X-Runtime: 0.015155
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
Authorizat IO N: Bearer 2a31dcea7e9ab00b042e6e7476d39b8033f50a788eca03cf
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
ETag: W/&quot;8ed36cf24f6a8e4349809d817bdea602&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 1e873836-0dc0-47d5-804d-7f2618dd4106
X-Runtime: 0.044049
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
PATCH /api/wishlists/29
Accept: application/json
Authorizat IO N: Bearer b294042f2436ffbcafed32de2678246149c30cabdbaedff5
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`PATCH /api/wishlists/:id`

#### Parameters


```json
wishlist[name]=Another+Wishlist&wishlist[user_id]=49&wishlist[is_default]=true&wishlist[is_public]=false
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
ETag: W/&quot;a6814a5589e2d6cd27d209712115a4b8&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 2d58378e-d0fd-4394-a626-51c904c2fc2e
X-Runtime: 0.017517
Vary: Origin
Content-Length: 317
200 OK
```


```json
[binary data]
```



