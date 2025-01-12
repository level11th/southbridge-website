---
title: Global Configuration
weight: 5
---

### Essential Global Configuration

The essential configurations that apply to the global system can be managed under the menu: `System Management` -> `App Configuration`.

**Note**: Restart is not required after making changes.

#### **Company Configuration**

-   **`COMPANY_CODE`**: string  
    Defines the system's company code (e.g., displayed in reports as PF1000).

-   **`COMPANY_NAME`**: string  
    Defines the system's company name (e.g., displayed in reports).

-   **`LOGO`**: image file  
    Sets the company logo (e.g., displayed in reports).

-   **`WATERMARK`**: string  
    Defines the system's watermark (e.g., displayed in reports).

#### **Rate Configuration**

-   **`DEFAULT_COMMISSION_RATE`**: number (decimal format)  
    Sets the default commission rate.

-   **`DEFAULT_VAT`**: number (decimal format)  
    Sets the default VAT rate.

-   **`DEFAULT_WHT`**: number (decimal format)  
    Sets the default withholding tax rate.

#### **Security Configuration**

-   **`RESET_PASSWORD_TOKEN_EXPIRES_DURATION`**: number  
    Sets the expiration duration (in days) for reset password tokens.

-   **`MAX_SAME_PASSWORD_COUNT`**: number  
    Specifies the maximum number of recent identical passwords allowed when setting a new password within a year.

-   **`PASSWORD_EXPIRES_DURATION`**: number  
    Sets the password expiration duration (in days).

-   **`MAX_AUTH_FAILED_COUNT`**: number  
    Specifies the maximum number of failed authentication attempts before suspending the user account.

-   **`ALLOW_MULTIPLE_SESSIONS_PER_USER`**: bool  
    Determines whether users are allowed to log in to multiple sessions simultaneously.

#### **Resource Configuration**

-   **`FX_SPOT_SECURITY_TYPE_ID`**: number  
    Specifies the spot security type ID.

-   **`FX_FORWARD_SECURITY_TYPE_ID`**: number  
    Specifies the FX forward security type ID.

-   **`FX_SWAP_SECURITY_TYPE_ID`**: number  
    Specifies the FX swap security type ID.

-   **`DEFAULT_PRICESOURCE_ID`**: number  
    Specifies the default price source ID.

-   **`DEFAULT_CURRENCY_ID`**: number
    Specifies the system's default currency ID.

-   **`THB_CURRENCY_ID`**: number
    Specifies Thai Baht currency ID.

--- 

