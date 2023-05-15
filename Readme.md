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

$response = $paytring->CreateOrder(
    $amount_in_paisa,
    $receipt_number,
    $merchant_callback_url,
    $customer_info
);

var_dump($response);

```
    
The `CreateOrder` method requires the following information:
- Amount in paisa (e.g., for Rs.1, use 100)
- Receipt Number (merchant order reference number)
- Merchant Callback URL (the URL where the payment gateway will redirect the user after payment completion)
- Customer Information (name, email, and phone)

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
