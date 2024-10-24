# Project Documentation

## 1. **settlementController.js**

This controller manages settlement logs and the merchant's settlement process.

### Functions

- **markAsSettled**
  - Marks the settlement as complete for a given merchant.
  - Validates whether the merchant has outstanding settlements and updates the settlement status.
  - Example Usage:
    ```javascript
    POST /settlement/settle/:merchantId
    ```

- **fetchSettlementStats**
  - Fetches the current settlement status of the merchant, including due amounts and settled amounts.
  - Example Usage:
    ```javascript
    GET /settlement/stats/:merchantId
    ```

---

## 2. **easeBuzzController.js**

This controller handles the integration with the EaseBuzz payment gateway, including initiating payments, generating QR codes, and handling callbacks.

### Functions

- **initiatePayment**
  - Initiates a payment on EaseBuzz with a random Indian name, email, and mobile number.
  - Example Usage:
    ```javascript
    POST /easebuzz/initiate
    ```

- **generateQr**
  - Generates a QR code for UPI payments using the EaseBuzz platform.
  - Example Usage:
    ```javascript
    POST /easebuzz/qr
    ```

- **easebuzzQr**
  - Combines payment initiation and QR code generation for UPI payments.
  - Example Usage:
    ```javascript
    POST /easebuzz/upi
    ```

- **easeBuzzTransactionCallback**
  - Handles transaction status updates from EaseBuzz.
  - Example Usage:
    ```javascript
    POST /easebuzz/callback
    ```

---

## 3. **walletController.js**

This controller manages wallet operations for merchants, including creating wallets, adding funds, and debiting funds.

### Functions

- **createWallet**
  - Creates a wallet for a new merchant with a default balance of 0.
  - Example Usage:
    ```javascript
    POST /wallet/create/:merchantId
    ```

- **addFund**
  - Adds funds to a merchant's wallet and updates the passbook.
  - Example Usage:
    ```javascript
    POST /wallet/add
    ```

- **debitFund**
  - Debits an amount from a merchant's wallet and logs the transaction in the passbook.
  - Example Usage:
    ```javascript
    POST /wallet/debit/:walletId
    ```

- **walletBalance**
  - Retrieves the balance of a merchant's wallet.
  - Example Usage:
    ```javascript
    GET /wallet/balance/:merchantId
    ```

- **rechargeWallet**
  - Initiates a wallet recharge process.
  - Example Usage:
    ```javascript
    POST /wallet/recharge
    ```

---

## 4. **merchantController.js**

This controller manages merchant-related functionalities, including onboarding, updating details, and managing KYC documents.

### Functions

- **getAllMerchants**
  - Retrieves all merchants with pagination and optional search filters.
  - Example Usage:
    ```javascript
    GET /merchant/all
    ```

- **getMerchantById**
  - Retrieves detailed information about a specific merchant.
  - Example Usage:
    ```javascript
    GET /merchant/:id
    ```

- **onboardMerchant**
  - Onboards a merchant and marks them as active.
  - Example Usage:
    ```javascript
    POST /merchant/onboard/:merchantId
    ```

- **uploadMerchantDocument**
  - Uploads KYC or other merchant-related documents.
  - Example Usage:
    ```javascript
    POST /merchant/document/:merchantId
    ```

- **addAmountForMerchantSettlement**
  - Adds settlement amounts for a merchant.
  - Example Usage:
    ```javascript
    POST /merchant/settlement
    ```

---

## Models Used

1. **Merchant**: Represents merchant-related data.
2. **Wallet**: Stores merchant wallet details.
3. **MerchantPassbook**: Logs transactions for the merchant wallet.
4. **SettlementLogs**: Tracks settlement logs and due amounts for merchants.
5. **merchantAmountSettlement**: Tracks the settlement amounts for each merchant.
6. **bankModel**: Represents the merchant's bank account details.
7. **Transaction**: Handles transaction details for payments made via EaseBuzz.

---

This documentation gives an overview of the key controllers and their functionality. Please refer to the respective files for detailed implementation.