# PHP SDK Documentation
## Introduction
The PHP SDK provides seamless integration with Paytring's payment gateway services. This SDK offers a range of features to facilitate payment processing for PHP developers. The following features are supported:
- Non-seamless integration API
- Create Order
- Fetch/Verify Order
- 

## Non Seamless Integration
This SDK exclusively supports non-seamless integration. Non-seamless integration requires users to be redirected to the payment gateway to select their preferred payment method and complete the payment.
## Create Order
To create an order using the Paytring PHP SDK, follow the code example below:
    
```Php
$api_key = "test_123";
$api_secret = "secret_123";

$paytring = new \Paytring\Php\Api($api_key, $api_secret);

$amount_in_paisa = "100";
$receipt_number = "10123450";
$merchant_callback_url = "https://httpbin/post";

$customer_info = [
    'name' => 'John Doe',
    'email' => 'a@mcsam.in',
    'phone' => '9234567890',    
];

$payment_info = [
    "currency" => "INR",
    "pg" => "payu",
    "pg_pool_id" => ""
];

$billing_address = [
    "firstname" => "BillingFirstname", 
    "lastname" => "BillingLastname", 
    "phone" => "09999999999", 
    "line1" => "Billing Address Line 1", 
    "line2" => "Billing Address Line 2", 
    "city" => "Gurugram", 
    "state" => "Haryana", 
    "country" => "India", 
    "zipcode" => "122001" 
];

$shipping_address = [
    "firstname" => "ShippingFirstname", 
    "lastname" => "ShippingLastname", 
    "phone" => "09999999999", 
    "line1" => "Shipping Address Line 1", 
    "line2" => "Shipping Address Line 2", 
    "city" => "Gurugram", 
    "state" => "Haryana", 
    "country" => "India", 
    "zipcode" => "122001" 
];

$notes = [
    "udf1" => "udf1", 
    "udf2" => "udf2",
    "udf3" => "udf3",
    "udf4" => "udf4",
    "udf5" => "udf5"
];

$response = $paytring->CreateOrder(
    $amount_in_paisa,
    $receipt_number,
    $merchant_callback_url,
    $customer_info,
    $payment_info,
    $billing_address,
    $shipping_address,
    $notes
);

var_dump($response);

```
    
The `CreateOrder` method requires the following information:
- Amount in paisa (e.g., for Rs.1, use 100)
- Receipt Number (merchant order reference number)
- Merchant Callback URL (the URL where the payment gateway will redirect the user after payment completion)
- Customer Information (name, email, and phone)
- Payment Information (currency, pg, and pg_pool_id)
- Billing Address Information (firstname, lastname, phone, line1, line2, city, state, country and zipcode)
- Shipping Address (firstname, lastname, phone, line1, line2, city, state, country and zipcode)
- Notes (udf1, udf2, udf3, udf4 and udf5)

## Fetch Order
To fetch an order using the Paytring PHP SDK, use the code example below:

```Php
$api_key = "test_123";
$api_secret = "secret_123";

$paytring = new \Paytring\Php\Api($api_key, $api_secret);

$pg_order_id = "d234ew32r4345fd";

$fetch_response = $paytring->FetchOrder($pg_order_id);

var_dump($fetch_response);

```

The `FetchOrder` method requires the following information:
- PG Order ID (provided by the payment gateway when creating an order). This ID allows you to retrieve payment status and other related information.

### `Note: Ensure you provide all the necessary information for each method to proceed successfully.`
