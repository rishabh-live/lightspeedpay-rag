# Lightspeed Pay - Technical Domain and Hosting Documentation

## 1. Domain Information Overview
All domain names related to **Lightspeed Pay** have been purchased from **Hostinger**. Both domain registration and DNS configuration are managed within the Hostinger account. Below is a detailed overview of the domains, their purposes, and the hosting platforms used.

## 2. Domain List with Purpose and Hosting Information

### 2.1. [https://lightspeedpay.in](https://lightspeedpay.in)
- **Purpose**: This is the **main landing website** for Lightspeed Pay. It serves as the public-facing homepage where users can learn more about the product offerings, features, and other business-related information.
- **Hosting**: Hosted on **Hostinger Shared Hosting**, providing an easy-to-manage solution with sufficient performance for handling the web traffic on the public-facing website.
- **DNS Configuration**: Configured in Hostinger.

### 2.2. [https://dashboard.lightspeedpay.in](https://dashboard.lightspeedpay.in)
- **Purpose**: This subdomain hosts the **dashboard** for both **Admins and Merchants** of Lightspeed Pay. It serves as the main control panel for managing transactions, viewing analytics, and administering the platform.
- **Hosting**: Hosted on **VPS (srv467779.hstgr.cloud)** to ensure better performance, customization, and resource allocation for managing the heavier load and processing demands of the dashboard application.
- **DNS Configuration**: Managed via Hostinger, pointing to the VPS.

### 2.3. [https://affiliate.lightspeedpay.in](https://affiliate.lightspeedpay.in)
- **Purpose**: This subdomain is dedicated to the **Affiliate Dashboard**, where affiliate marketers can track their referral traffic, commissions, and other affiliate-related metrics.
- **Hosting**: Hosted on **VPS (srv467779.hstgr.cloud)** to provide a stable and fast environment for managing affiliate users and their data.
- **DNS Configuration**: Configured in Hostinger, directing to the VPS instance.

### 2.4. [https://api.lightspeedpay.in](https://api.lightspeedpay.in)
- **Purpose**: This domain is used for hosting the **APIs** that power the various systems of Lightspeed Pay. These APIs are integral to the functionality of the payment systems, allowing integration with third-party services and internal operations.
- **Hosting**: Hosted on **VPS (srv467779.hstgr.cloud)** for high availability, security, and scalability. The VPS ensures optimal performance for API calls and interactions with other systems.
- **DNS Configuration**: Managed via Hostinger, pointing to the VPS.

### 2.5. [https://recharge.lightspeedpay.in/<lsp_mid>](https://recharge.lightspeedpay.in/<lsp_mid>)
- **Purpose**: This subdomain serves as the **Recharge Portal** for merchants. Merchants can use this portal to recharge their accounts and manage payments or transactions.
- **Hosting**: Hosted on **Hostinger Shared Hosting**. Since this portal primarily serves individual merchants, shared hosting is sufficient for its resource requirements.
- **DNS Configuration**: Configured in Hostinger.

### 2.6. [https://system.lightspeedpay.in](https://system.lightspeedpay.in)
- **Purpose**: The **System Monitoring Page** is accessible via this subdomain. It provides insights into the health, status, and performance of various components of the Lightspeed Pay system.
- **Hosting**: Hosted on **Hostinger Shared Hosting**, as the system monitoring page doesn’t require extensive resources.
- **DNS Configuration**: Managed in Hostinger.

### 2.7. [https://docs.lightspeedpay.in](https://docs.lightspeedpay.in)
- **Purpose**: This subdomain hosts the **Documentation Page** for Lightspeed Pay, containing technical documentation, API references, and user manuals for developers and users.
- **Hosting**: Hosted on **Hostinger Shared Hosting**, ensuring easy access for users while providing sufficient bandwidth for the content.
- **DNS Configuration**: Managed through Hostinger.

---

## 3. Hosting Platforms Overview

### 3.1. **Hostinger Shared Hosting**
- **Used For**: Main landing website, merchant recharge portal, system monitoring page, documentation page.
- **Advantages**:
  - Cost-effective for websites with moderate traffic.
  - Easy management and maintenance.
  - Sufficient for serving static content and lightweight applications.

### 3.2. **VPS (srv467779.hstgr.cloud)**
- **Used For**: Admin & Merchant Dashboard, Affiliate Dashboard, API systems.
- **Advantages**:
  - High performance and scalability.
  - Dedicated resources (CPU, RAM, Disk).
  - Greater control and customization for server settings.
  - Ideal for handling high-traffic applications and backend systems.
  
---

## 4. DNS Management

All domain names are registered and managed via the **Hostinger** platform. DNS records are configured to point to the appropriate hosting services, whether it’s Hostinger Shared Hosting or the VPS instance (srv467779.hstgr.cloud). Hostinger's DNS management interface allows easy configuration of A records, CNAMEs, and other required settings for proper domain resolution.

---

## 5. Security Measures

To ensure the security and reliability of all domains and subdomains, the following measures are in place:
- **SSL Certificates**: All domains are secured using SSL to provide encrypted connections, ensuring that sensitive data is protected.
- **Firewalls and DDoS Protection**: The VPS hosting platform is equipped with firewall protections and DDoS mitigation techniques to safeguard against malicious attacks.
- **Access Control**: Administrative access to the VPS and Hostinger accounts is restricted to authorized personnel, and multi-factor authentication (MFA) is enabled for added security.

---

## 6. Backup and Recovery

- **Hostinger Shared Hosting**: Automated daily backups are provided as part of the hosting package, ensuring that data can be recovered in case of failure.
- **VPS**: The VPS is configured with scheduled backups, including full server snapshots and incremental backups, ensuring minimal downtime in case of failure or data corruption.

---

## 7. Future Expansion Plans

As the system grows, additional resources can be added to the VPS to accommodate increased traffic and functionality. Hostinger also offers scalable options for upgrading shared hosting plans if required.

