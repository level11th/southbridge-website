---
title: Reverse Proxy
weight: 6
---

### Introduction

Although Southbridge can serve TLS, you may want to use a reverse proxy in front of the application. A reverse proxy offers benefits such as load balancing and caching.  

Southbridge works with any reverse proxy that provides the following features:  

- Forwarding of the `Host` header  
- Forwarding of the `X-Real-IP` header  
- Forwarding of the `X-Forwarded-For` header  
- Support for Server-Sent Events (SSE)  

#### Nginx
Below is an example Nginx configuration:

```nginx
server {
    listen       443 ssl;
    listen  [::]:443 ssl;
    server_name    ${DOMAIN};

    ssl_certificate /etc/nginx/ssl/cert.pem;
    ssl_certificate_key /etc/nginx/ssl/key.pem;

    resolver 127.0.0.11 valid=10s;

    location /api/v1/notification.subscribe {
        set $target ${UPSTREAM};
        proxy_pass $target;
        proxy_redirect     off;
        proxy_set_header   Host             $host;
        proxy_set_header   X-Real-IP        $remote_addr;
        proxy_set_header   X-Forwarded-For  $proxy_add_x_forwarded_for;
        proxy_buffering off;
        proxy_read_timeout 86400s; # 1 day (adjust as needed)
    }

    location / {
        set $target ${UPSTREAM};
        proxy_pass $target;
        proxy_redirect     off;
        proxy_set_header   Host             $host;
        proxy_set_header   X-Real-IP        $remote_addr;
        proxy_set_header   X-Forwarded-For  $proxy_add_x_forwarded_for;
    }
}
```
