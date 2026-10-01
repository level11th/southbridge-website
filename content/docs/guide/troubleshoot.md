---
title: Troubleshooting
weight: 7
---

#### Mounted File Permissions
When the application shows an error indicating "open file permission denied," ensure that you change the file owner to `65532` and set the appropriate permissions before mounting the file in the container.

```shell
chmod 400 ca.crt
chown 65532:65532 ca.crt

docker run --rm -v /home/foo/ca.crt:/home/nonroot/ca.crt:ro southbridge
```

#### LDAP TLS Host Verification Failed
```
open connect to LDAP server error: failed to connect to LDAP server: LDAP Result Code 200 "Network Error": tls: failed to verify certificate: x509: cannot validate certificate for {ip or host} because it doesn't contain any IP SANs
```

Check whether your certificate SANs include the host specified in `LDAP_DIAL_URL`. If not, you should contact your certificate issuer.


#### PFX to PEM Conversion
Use OpenSSL to convert a `.pfx` file to `.pem` format:

1. **Extract the private key:**
   ```bash
   openssl pkcs12 -in yourfile.pfx -nocerts -out key.pem -nodes
   ```
   - **`-nocerts`**: Tells OpenSSL to only output the private key.

2. **Extract the certificate:**
   ```bash
   openssl pkcs12 -in yourfile.pfx -clcerts -nokeys -out cert.pem
   ```
   - **`-clcerts`**: Excludes CA certificates.
   - **`-nokeys`**: Excludes the private key.

You may need the `-legacy` flag when converting files that use older ciphers.
