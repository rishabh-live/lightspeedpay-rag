### API Documentation for Merchant Integration

---

Welcome to the **LightSpeedPay API** integration guide, designed to enable seamless payment processing on your e-commerce platform. This documentation provides detailed information on the prerequisites, API endpoints, request/response formats, and workflows to help you integrate LightSpeedPay’s payment gateway efficiently.

---

## 1. Prerequisites for Integration

Before initiating transactions via LightSpeedPay, you must complete the following setup:

### 1.1 IP Whitelisting
- **Sandbox Mode**: IP whitelisting is **optional** for testing purposes in the sandbox environment. You can freely test APIs without needing to whitelist IPs.
- **Live Mode**: For the production environment, IP whitelisting is **mandatory**. Only whitelisted IPs are authorized to initiate transactions via the API. Contact support to add your server's IP to the whitelist before going live.

### 1.2 Webhook Configuration
- **Webhook URL**: You must provide a Webhook URL for asynchronous notifications. This URL will be used by LightSpeedPay to send transaction status updates, ensuring that your system receives the latest payment information in real time.
- **Security**: For enhanced security, we recommend the use of a **Bearer Token** in your webhook setup. This token is used to verify the authenticity of the server-to-server (S2S) communication, ensuring that only trusted requests are accepted by your system.

### 1.3 Redirect URLs
- **Success URL**: This is the URL where the customer will be redirected after a successful payment. It should display a confirmation message to the customer.
- **Fail URL**: This is the URL where the customer will be redirected in case the payment fails. It should notify the customer of the failure and provide steps for retrying the payment.

---

## 2. API Key Generation

Once the prerequisites are configured (IP whitelisting, Webhook URL, Redirect URLs, etc.), you can generate your **API Key** and **API Secret**. These credentials are crucial for authenticating API requests and are only valid when initiated from whitelisted IPs.

- **API Key**: Unique identifier for your account, used for API authentication.
- **API Secret**: Secret token used to secure the communication between your server and the LightSpeedPay server.

---

## 3. API Integration Workflow

### 3.1 Steps to Integrate LightSpeedPay

1. **Configure IP Whitelisting**: Ensure that your server IPs are whitelisted for the Live environment.
2. **Generate API Credentials**: Get your API Key and API Secret from the LightSpeedPay dashboard.
3. **Set Webhook and Redirect URLs**: Define and secure your Webhook URL for transaction status updates. Also, configure the Success and Fail URLs for user redirection.
4. **Initiate a Payment**: Make an API call from the whitelisted server to initiate the transaction.
5. **Redirect Customer to Payment Page**: Use the payment link received in the API response to redirect the customer to LightSpeedPay’s hosted payment page.
6. **Receive Webhook Notifications**: After the payment is processed, a Webhook notification will be sent to your server to confirm the payment status.
7. **Redirect Customer Based on Outcome**: After the transaction is completed, LightSpeedPay will redirect the customer to the provided Success or Fail URL.

---

## 4. API Details

### 4.1 Endpoints

The LightSpeedPay API supports both Sandbox and Live environments. Ensure you're using the correct endpoint based on your environment.

- **Sandbox Environment (For Testing)**:  
  `POST https://api.lightspeedpay.in/api/v1/transaction/sandbox/initiate-transaction`
  
- **Live Environment (For Production)**:  
  `POST https://api.lightspeedpay.in/api/v1/transaction/initiate-transaction`

### 4.2 HTTP Method
- **POST**: Transactions are initiated using a POST request.

### 4.3 Request Headers
The request must contain the following header to specify the format of the data being sent:

```http
Content-Type: application/json
```

### 4.4 Request Payload

Below is an example of the JSON payload required to initiate a transaction:

```json
{
  "customerName": "John Doe",
  "status": "success",
  "method": "Qr",
  "description": "Payment for Order #12345",
  "amount": 500,
  "billId": "ABC123456789",
  "vpaId": "johndoe@upi",
  "apiKey": "your_api_key",
  "apiSecret": "your_api_secret",
  "type": "sandbox"
}
```

#### **4.4.1 Parameters Explained**

- **customerName**: Name of the customer making the payment (string).
- **status**: Indicates the intended status of the payment initiation (set to "success" for initiating a successful transaction) (string).
- **method**: The payment method (e.g., "Qr" for UPI QR-based transactions) (string).
- **description**: A brief description of the transaction (string).
- **amount**: The total amount for the transaction in INR (integer).
- **billId**: A unique identifier for the bill or order (string).
- **vpaId**: UPI Virtual Payment Address (VPA) of the customer (string).
- **apiKey**: Your LightSpeedPay API Key (string).
- **apiSecret**: Your LightSpeedPay API Secret (string).
- **type**: Defines the environment type for the transaction ("sandbox" for testing or "live" for production) (string).

---

## 5. API Response

Upon successful initiation of a transaction, the API will return a JSON response with the transaction details and the payment link.

### 5.1 Sample Response

```json
{
  "status": "success",
  "code": 200,
  "message": "Transaction initiated successfully",
  "data": {
    "_id": "649a2b5f8f9836df8d48dba1"
  },
  "paymentLink": "https://pay.lightspeedpay.in/?txn=649a2b5f8f9836df8d48dba1&key=your_api_key&secret=your_api_secret"
}
```

#### **5.1.1 Response Fields**

- **status**: Indicates the result of the transaction initiation (e.g., "success") (string).
- **code**: HTTP status code of the response (integer).
- **message**: Description of the result (e.g., "Transaction initiated successfully") (string).
- **data**: Contains additional data related to the transaction:
  - **_id**: Unique identifier for the initiated transaction (string).
- **paymentLink**: The link that the customer must use to complete the payment. This link can be used to redirect customers to the hosted payment page.

---

## 6. Payment Flow

### 6.1 Steps in the Payment Process

1. **Initiate Transaction**: You initiate a transaction by making an API call with the required parameters.
2. **Get Payment Link**: The API response will include a `paymentLink` that should be presented to the customer.
3. **Customer Completes Payment**: The customer is redirected to the LightSpeedPay payment page via the payment link. Ensure the browser or WebView supports JavaScript and DOM storage.
   - **Note**: In case you are using a WebView, ensure that JavaScript and DOM storage are enabled. Without these, the payment page will not function properly.
4. **Redirect to Success or Fail URL**: Based on the outcome of the payment, the customer is redirected to either the success or fail URL.
5. **Receive Webhook Notification**: Simultaneously, LightSpeedPay will send a webhook notification to your server with the final transaction status.

---

## 7. Webhook Handling

### 7.1 Webhook Request

When the transaction is completed (successful or failed), LightSpeedPay will make a POST request to your configured Webhook URL. Ensure your server is ready to receive and validate this data.

### 7.2 Webhook Security

To secure your webhook, we recommend using a **Bearer Token** for authentication. The token will be included in the headers of the webhook request and should be verified by your server before processing the request.

```http
Authorization: Bearer <your_bearer_token>
```

---

## 8. Testing in Sandbox Mode

Before going live, you should thoroughly test your integration in the **Sandbox environment**. In sandbox mode, transactions are simulated, and IP whitelisting is not required. You can experiment with different payment scenarios to ensure your system handles all outcomes properly.

---

## 9. Going Live

Once you are satisfied with your testing, contact LightSpeedPay to move your integration to **Live Mode**. Make sure you have completed the following steps before going live:
- **IP Whitelisting**: Ensure your production server's IPs are whitelisted.
- **Webhook URL**: Your production Webhook URL is configured and secured with a Bearer Token.
- **Success & Fail URLs**: Correct URLs for user redirection after payment completion are in place.

---

## 10. Additional Considerations

### 10.1 Security Best Practices

- Always use HTTPS to communicate with LightSpeedPay’s APIs.
- Ensure that your Webhook URL is secured and validates incoming requests properly.
- Use strong and unique API keys for each environment (sandbox/live).

### 10.2 Error Handling

- Handle errors gracefully by capturing API response codes and messages. Display user-friendly messages in case of failures.
- In case of network issues, ensure your system can retry API requests or display

 appropriate information to the customer.

---

For further assistance or queries, please contact our **Technical Support Team**. We are here to help ensure a smooth and successful integration. Write your queries on Whatsapp @ +91 84510 76632. 

--- 

End of Documentation.