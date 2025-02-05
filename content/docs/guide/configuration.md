---
title: Configuration
weight: 2
---

Southbridge reads its configuration from enviroment variables when starting.
Below is the explanation of each environment variable of the app:

## Enviroment variables

---

### **Application Configuration**

-   **`APP_BASE_URL`**: `http://localhost:8080`  
    Specifies the base URL of the application. Used for constructing URLs or API endpoints.

-   **`APP_ADDR`**: `127.0.0.1:3000`  
    Specifies the address and port where the application will run.

-   **`TLS_KEY`**: (deprecated use TLS_PATHS instead)  
    Path to the TLS private key file for listen with TLS. If empty, TLS will not be enabled.

-   **`TLS_CERT`**: (deprecated use TLS_PATHS instead)  
    Path to the TLS certificate file. Works with `TLS_KEY` to secure connections.

-   **`TLS_PATHS`**: `cert:key`(PEM)  
    Specifies the paths to the server's TLS certificate files in the format: `/path/to/cert:/path/to/key`.

-   **`TIMEZONE`**: `Asia/Bangkok`  
    Sets the application's timezone. This affects date and time operations.

-   **`APP_ENV`**: `PRODUCTION`  
    Indicates the environment where the app is running. Possible values: `PRODUCTION`.

---

### **Database Configuration**

-   **`DB_URL`**: `postgres://postgres:mysecretpassword@localhost:5432/lv11?sslmode=disable`  
    Connection string for the PostgreSQL database. Includes username, password, host, port and database name.  
    [Learn more about connection string](https://pkg.go.dev/github.com/lib/pq#hdr-Connection_String_Parameters)

-   **`DB_MAX_IDLE_CONNS`**: `16`  
    Maximum number of idle connections in the database connection pool.

-   **`DB_MAX_OPEN_CONNS`**: `16`  
    Maximum number of open connections to the database.

-   **`DB_CONN_MAX_LIFETIME`**: `0`  
    Maximum lifetime of a database connection. `0` means no limit.

---

### **Session Management**

-   **`SESS_SECRET`**: `my-secret`  
    Secret key for encrypting and signing session data.

---

### **Feature Toggles**

-   **`FEATURES`**:
    Enables or disables application features. Possible values include `worker` or `migrate_role`.

    -   `worker` start a background worker for process async task
    -   `migrate_role` automatically update roles of the users in connected database to match the current version of the the app

-   **`BODY_LIMIT`**: `500M`  
    Maximum size for the request body. Useful for controlling upload limits.

-   **`CHROME_MAX_TAB`**: `100`  
    Maximum number of tabs allowed in the Chrome browser automation tool.

-   **`CHROME_REMOTE_URL`**: `http://localhost:9222`  
    URL of the remote Chrome instance used for automation. empty if you have local chrome

---

### **Email Configuration**

-   **`MAIL_CLIENT_TYPE`**: `smtp`  
    Specifies the mail client type. Useful for testing with `mock`or production services like`smtp`.

#### SMTP Configuration:

-   **`SMTP_SENDER`**: `noreply@foo.com`  
    Default sender email address for SMTP.
-   **`SMTP_HOSTNAME`**: `smtp.com`  
    SMTP server hostname.
-   **`SMTP_PORT`**: `25`  
    Port used for SMTP communication.
-   **`SMTP_USERNAME`**: `foo`  
    Username for SMTP authentication. (optional)
-   **`SMTP_PASSWORD`**: `bar`  
    Password for SMTP authentication. (optional)
-   **`SMTP_INSECURE_SKIP_VERIFY`**: `false`  
    Skips TLS verification for SMTP connections.
-   **`SMTP_TLS_PATHS`**: `cert:key:ca`(PEM)  
    Specifies the paths to the SMTP's TLS certificate files in the format: `/path/to/cert:/path/to/key:/path/to/ca`.  
    You can also provide only the CA file, for example: `::/path/to/ca`.

**Note:** SMTP will upgrade to a TLS connection if TLS is available via the STARTTLS SMTP extension automatically.  
if the `SMTP_TLS_PATHS` or `SMTP_INSECURE_SKIP_VERIFY` environment variables are provided, it will establish a connection using TLS without upgrading the connection.

---

### **LDAP Configuration**

-   **`LDAP_DIAL_URL`**: `ldap://localhost:389` or `ldaps://localhost:636`  
    URL for connecting to the LDAP server. use ldaps:// for tls connection
-   **`LDAP_ROOT_DN`**: `cn=user-ro,dc=alibnr,dc=com`  
    Root distinguished name for LDAP access.
-   **`LDAP_ROOT_PASSWORD`**: `ro_pass`  
    Password for the root DN.
-   **`LDAP_AUTH_DN`**: `dc=alibnr,dc=com`  
    Base distinguished name for user authentication.
-   **`LDAP_AUTH_FILTER`**: `(&(objectClass=inetOrgPerson)(uid={{ .Username }}))`  
    LDAP query filter for authenticating users.
-   **`LDAP_INSECURE_SKIP_VERIFY`**: `false`  
    Skips TLS verification for LDAP connections.
-   **`LDAP_TLS_PATHS`**: `cert:key:ca`(PEM)  
    Specifies the paths to the LDAP's TLS certificate files in the format: `/path/to/cert:/path/to/key:/path/to/ca`.  
    You can also provide only the CA file, for example: `::/path/to/ca`.

**Note:** The difference between `ldap://` and `ldaps://` is that 
- `ldap://` will upgrade to a TLS connection only if the `LDAP_TLS_PATHS` or `LDAP_INSECURE_SKIP_VERIFY` environment variables are provided. 
- `ldaps://` will establish a connection using TLS without upgrading the connection.

---

### **Logging Configuration**

-   **`LOGGER_TYPE`**: `text`  
    Specifies the logging format. Possible values: `text`, `json`.

-   **`LOG_HEALTH_CHECK`**: `false`  
    Enables or disables logging of health check requests.

---

### **Go releated configuration**
more details [Go Runtime](https://pkg.go.dev/runtime)

-   **`GOGC`**:
    Configures the garbage collection (GC) target percentage in Go. Higher values decrease GC frequency and memory use, while lower values increase frequency and decrease latency. Defaults to `100` if not set.

-   **`GOMEMLIMIT`**:
    sets a soft memory limit for the runtime. (eg. 5GiB)


---


### Example
```env
APP_BASE_URL=http://localhost:8080
APP_ADDR=127.0.0.1:8080
TLS_PATHS=/path/to/cert.pem:/path/to/key.pem

TIMEZONE=Asia/Bangkok
APP_ENV=PRODUCTION

DB_URL=postgres://postgres:mysecretpassword@localhost:5432/lv11?sslmode=disable
DB_MAX_IDLE_CONNS=16
DB_MAX_OPEN_CONNS=16
DB_CONN_MAX_LIFETIME=0

SESS_SECRET=my-secret

# possible values worker,migrate_role
FEATURES=
BODY_LIMIT=500M
CHROME_MAX_TAB=100
CHROME_REMOTE_URL=http://localhost:9222

MAIL_CLIENT_TYPE=smtp
SMTP_SENDER=noreply@foo.com
SMTP_HOSTNAME=smtp.com
SMTP_PORT=25
SMTP_USERNAME=foo
SMTP_PASSWORD=bar
SMTP_INSECURE_SKIP_VERIFY=false
SMTP_TLS_PATHS=/path/to/cert.pem:/path/to/key.pem:/path/to/ca.pem

# LDAP
LDAP_DIAL_URL=ldap://localhost:389 or ldaps://localhost:636
LDAP_ROOT_DN=cn=user-ro,dc=alibnr,dc=com
LDAP_ROOT_PASSWORD=ro_pass
LDAP_AUTH_DN=dc=alibnr,dc=com
LDAP_AUTH_FILTER="(&(objectClass=inetOrgPerson)(uid={{ .Username }}))"
LDAP_INSECURE_SKIP_VERIFY=false
LDAP_TLS_PATHS=/path/to/cert.pem:/path/to/key.pem:/path/to/ca.pem

# possible values text, json
LOGGER_TYPE=text
LOG_HEALTH_CHECK=false

GOGC=80
GOMEMLIMIT=5GiB
```
