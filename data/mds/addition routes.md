# API Documentation - Additional Routes

This documentation outlines the routes related to whitelisting, transaction reports, merchant passbook management, and more. These routes offer functionality to generate reports, manage whitelisted IPs, handle merchant passbooks, and retrieve transaction data in different formats.

---

## Report and Transaction Routes

### **GET /ca-report**
Fetch the CA report.
- **Method**: `GET`
- **URL**: `/ca-report`
- **Protected**: No
- **Description**: Retrieves the CA report for the current period.

### **GET /ca-report-csv**
Fetch the CA report in CSV format.
- **Method**: `GET`
- **URL**: `/ca-report-csv`
- **Protected**: No
- **Description**: Retrieves the CA report in CSV format.

### **GET /ca-report-csv-today**
Fetch today's CA report in CSV format.
- **Method**: `GET`
- **URL**: `/ca-report-csv-today`
- **Protected**: No
- **Description**: Retrieves today's CA report in CSV format.

### **GET /ca-report-csv-yesterday**
Fetch yesterday’s CA report in CSV format.
- **Method**: `GET`
- **URL**: `/ca-report-csv-yesterday`
- **Protected**: No
- **Description**: Retrieves yesterday’s CA report in CSV format.

---

## Whitelister Routes

### **POST /add-whitelisted-ip**
Add a new IP address to the whitelist.
- **Method**: `POST`
- **URL**: `/add-whitelisted-ip`
- **Protected**: No
- **Description**: Adds a new IP address to the whitelist, allowing access to protected routes or services.

### **POST /add-package-to-whitelist**
Add a package to the whitelist.
- **Method**: `POST`
- **URL**: `/add-package-to-whitelist`
- **Protected**: No
- **Description**: Adds a new package to the whitelist, allowing access to specific packages or services.

### **POST /remove-package-from-whitelist**
Remove a package from the whitelist.
- **Method**: `POST`
- **URL**: `/remove-package-from-whitelist`
- **Protected**: No
- **Description**: Removes a package from the whitelist, restricting access to it.

### **POST /remove-whitelisted-ip**
Remove a whitelisted IP address.
- **Method**: `POST`
- **URL**: `/remove-whitelisted-ip`
- **Protected**: No
- **Description**: Removes an IP address from the whitelist.

---

## Merchant Volume and Transaction Reports

### **GET /get-volume-today-merchant-wise**
Fetch today's transaction volume, grouped by merchant.
- **Method**: `GET`
- **URL**: `/get-volume-today-merchant-wise`
- **Protected**: No
- **Description**: Retrieves the total transaction volume for today, grouped by each merchant.

### **GET /get-daily-volume-report-merchant-wise**
Fetch the daily volume report, grouped by merchant.
- **Method**: `GET`
- **URL**: `/get-daily-volume-report-merchant-wise`
- **Protected**: No
- **Description**: Retrieves the daily transaction volume report, grouped by merchant.

### **GET /get-all-transactions-csv**
Fetch all transactions in CSV format.
- **Method**: `GET`
- **URL**: `/get-all-transactions-csv`
- **Protected**: No
- **Description**: Retrieves a report of all transactions in CSV format.

---

## Merchant Passbook Management

### **GET /get-merchant-passbook-entry**
Fetch merchant passbook entries.
- **Method**: `GET`
- **URL**: `/get-merchant-passbook-entry`
- **Protected**: No
- **Description**: Retrieves passbook entries for a specific merchant.

### **GET /delete-merchant-passbook-entry**
Delete merchant passbook entries.
- **Method**: `GET`
- **URL**: `/delete-merchant-passbook-entry`
- **Protected**: No
- **Description**: Deletes a passbook entry for a specified merchant.

---

## Miscellaneous Routes

### **GET /get-sheet-wallet-vs-trnxn-table**
Fetch the comparison table of wallet vs transactions.
- **Method**: `GET`
- **URL**: `/get-sheet-wallet-vs-trnxn-table`
- **Protected**: No
- **Description**: Retrieves a table comparing wallet balances versus transaction amounts.

### **GET /merchant-info**
Fetch merchant information.
- **Method**: `GET`
- **URL**: `/merchant-info`
- **Protected**: No
- **Description**: Retrieves detailed information about a specific merchant.

### **GET /get-all-transactions-sfeee**
Fetch all transactions, filtered by a specific field (SFEee).
- **Method**: `GET`
- **URL**: `/get-all-transactions-sfeee`
- **Protected**: No
- **Description**: Retrieves all transactions filtered by the SFEee field.

### **GET /get-daily-transactions-report-generate**
Generate the daily transactions report.
- **Method**: `GET`
- **URL**: `/get-daily-transactions-report-generate`
- **Protected**: No
- **Description**: Generates and retrieves a report of daily transactions.

---

This documentation provides a detailed explanation of the new API routes for your system, allowing users to interact with transactions, merchant data, and whitelist features effectively.