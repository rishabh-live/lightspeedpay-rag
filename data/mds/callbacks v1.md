# LightSpeedPay Payment Gateway API Callback Documentation

This documentation provides an overview of the callback structure and status flow for transactions. The callbacks are triggered at various stages during the lifecycle of a transaction, from initiation to completion or failure. Developers can use this guide to handle transaction events and integrate them into their systems.

## Table of Contents
1. [Overview](#overview)
2. [Transaction Statuses](#transaction-statuses)
    - [INITIATE](#initiate)
    - [IN PROGRESS](#in-progress)
    - [FAILED / COMPLETED](#failed--completed)
3. [Callback Structure](#callback-structure)
    - [Fields](#fields)
    - [Example Payloads](#example-payloads)
4. [Callback Flow](#callback-flow)
5. [Handling Callbacks](#handling-callbacks)

---

## Overview

The Payment Gateway API provides a callback mechanism that notifies merchants when the status of a transaction changes. These callbacks contain essential details of the transaction, such as the transaction ID, amount, status, and method. 

Callbacks occur at key points:
1. When the transaction is **initiated**.
2. When the user **opens the payment page**.
3. When the transaction is either **successful (COMPLETED)** or **unsuccessful (FAILED)**.

---

## Transaction Statuses

Each transaction passes through different stages, and the status reflects the current phase of the transaction.

### 1. **INITIATE**:  
This status indicates that the transaction has been initiated but not yet processed. No payment method has been selected, and the transaction has not yet been directed to the payment page.

### 2. **IN PROGRESS**:  
Once the payment page is opened, the transaction moves to an "in progress" state. This status indicates that the user is on the payment page and has the option to complete or cancel the transaction.

### 3. **FAILED / COMPLETED**:  
After the payment is processed, the transaction moves to either a **FAILED** or **COMPLETED** state.
- **FAILED**: The transaction could not be completed due to insufficient funds, a canceled operation, or an error.
- **COMPLETED**: The transaction was successfully processed, and payment has been received.

---

## Callback Structure

The API sends transaction details via a POST request in JSON format to the merchant's callback URL. Below is the structure and a detailed explanation of the fields present in the callback payload.

### Fields

| Field             | Type     | Description                                                  |
|-------------------|----------|--------------------------------------------------------------|
| `transactionId`    | String   | Unique identifier for the transaction.                       |
| `billId`           | String   | Unique identifier for the bill or invoice.                   |
| `status`           | String   | Current status of the transaction (`INITIATE`, `REQUESTED(Qr)`, `FAILED`, `COMPLETED`). |
| `customerName`     | String   | (Optional) Name of the customer, if provided.                |
| `merchant_id`      | String   | ID of the merchant involved in the transaction.              |
| `method`           | String   | Payment method used (e.g., QR Shared, unknown).              |
| `description`      | String   | (Optional) Description of the transaction.                   |
| `amount`           | Number   | Total amount for the transaction.                            |
| `vpaId`            | String   | Virtual Payment Address (VPA), if applicable.                |
| `psp`              | String   | Payment service provider responsible for the transaction.    |
| `isVerified`       | Boolean  | Whether the transaction is verified (for initiate status).   |
| `reason`           | String   | (Optional) Reason for failure, if the transaction failed.    |
| `apiKeyUsed`       | String   | API key used to initiate the transaction.                    |
| `fees`             | Number   | Fees applicable to the transaction.                          |
| `createdAt`        | String   | Timestamp of when the transaction was initiated.             |
| `updatedAt`        | String   | Timestamp of the last update to the transaction.             |
| `paymentTime`      | String   | (Optional) Time of successful payment (for completed status).|

---

### Example Payloads

#### **1. Initiate Transaction**  
When a transaction is initiated, the system sends the following payload:

```json
{
  "customerName": "recharge for 8986194738",
  "merchant_id": "6687b019834e7c9b318e8683",
  "status": "initiate",
  "method": "unknown",
  "description": "Recharge",
  "amount": 11,
  "billId": "ABC123456789",
  "vpaId": "-",
  "psp": "Others",
  "isVerified": false,
  "apiKeyUsed": "2247bbb4-3995-424b-ba45-08162191181d",
  "fees": 0,
  "createdAt": "2024-10-19T05:56:33.828Z",
  "updatedAt": "2024-10-19T05:56:33.828Z"
}
```

#### **2. In Progress (Payment Page Opened)**  
When the user opens the payment page, the following payload is sent:

```json
{
  "transactionId": "67134a113deac68758a5998b",
  "billId": "ABC123456789",
  "status": "REQUESTED(Qr)",
  "psp": "Others",
  "amount": 11,
  "method": "QR Shared"
}
```

#### **3. Failed Transaction**  
In the event of a failed transaction, this payload is sent:

```json
{
  "transactionId": "67134a113deac68758a5998b",
  "status": "FAILED",
  "vpaId": "-",
  "psp": "Others",
  "amount": 11,
  "billId": "ABC123456789"
}
```

#### **4. Completed Transaction**  
When a transaction is successfully completed, the following payload is sent:

```json
{
  "transactionId": "67134a113deac68758a5998b",
  "status": "COMPLETED",
  "vpaId": "-",
  "psp": "Others",
  "amount": 11,
  "billId": "ABC123456789",
  "paymentTime": "2024-10-19T12:45:30Z"
}
```

---

## Callback Flow

1. **Transaction Initiation**: 
   - The transaction is initiated when the customer starts the process, but no payment details are provided at this stage.  
   - Status: `INITIATE`.

2. **Payment Page Opened**:
   - Once the user opens the payment page to proceed with the transaction, the status changes to "in progress."
   - Status: `REQUESTED(Qr)`.

3. **Transaction Completion**:
   - After the user completes the payment, the status will either change to `COMPLETED` for a successful payment or `FAILED` if the payment was not successful.

---

## Handling Callbacks

To handle the callbacks properly, follow these steps:

1. **Set up a Callback Endpoint**:
   - Create an endpoint on your server that can receive HTTP POST requests.
   - Ensure that your endpoint processes incoming JSON payloads.

2. **Verify Transaction Status**:
   - Each callback payload contains a `status` field. Use this to determine the current state of the transaction (`INITIATE`, `REQUESTED(Qr)`, `FAILED`, `COMPLETED`).

3. **Update Merchant's System**:
   - Based on the transaction status, update your system records:
     - For **INITIATE**, start a new transaction entry.
     - For **REQUESTED(Qr)**, mark the transaction as in progress.
     - For **FAILED**, mark the transaction as failed and handle any user notifications or retries.
     - For **COMPLETED**, mark the transaction as successful and finalize any order or service.

4. **Error Handling**:
   - In case of failure to process the callback, log the error and attempt to retry processing.
   - Use the `reason` field (if present) for debugging in the case of failed transactions.

5. **Security Considerations**:
   - Always verify the source of the callback by checking the `apiKeyUsed` or using a signature validation method.
   - Ensure the callback payload is securely transmitted (via HTTPS) to prevent tampering.

---

## Conclusion

The Payment Gateway API uses a reliable callback system to notify merchants of transaction status changes. Merchants and developers should handle these callbacks carefully to ensure proper tracking of transactions and a seamless customer experience.