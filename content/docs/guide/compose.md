
---
title: Compose
weight: 3
---

You can use Docker Compose to define deployment specifications instead of using docker run. This method is recommended. Below are some examples:

### Application
`app.yaml`

```yaml
services:
  chromium:
    image: chromedp/headless-shell:latest
    container_name: chromium
    restart: always
    shm_size: 2G # increase if not enough
    init: true # prevent zombie processes

  app:
    image: path-to-image:${IMAGE_TAG}
    container_name: app
    restart: unless-stopped
    env_file:
      - secret.env
    environment:
      APP_ADDR: ":8080"
      CHROME_REMOTE_URL: "http://chromium:9222"
    healthcheck:
      test: ["CMD", "/home/nonroot/server", "isready"]
      interval: 10s
      timeout: 5s
      retries: 5
```

### Database
`db.yaml`

```yaml
services:
  postgres:
    image: postgres:17.2
    container_name: pg
    restart: unless-stopped
    command: postgres -c max_connections=100
    shm_size: 512mb # increase if not enough
    env_file:
      - secret.env
    ports:
      - "5432:5432"
    volumes:
      - pg-data:/var/lib/postgresql/data
    healthcheck:
      test: "pg_isready -U postgres -d postgres"
      interval: 10s
      timeout: 5s
      retries: 5

  pgadmin:
    image: dpage/pgadmin4:latest
    container_name: pgadmin
    restart: unless-stopped
    env_file:
      - secret.env
    environment:
      - PGADMIN_CONFIG_WTF_CSRF_ENABLED=False # fix csrf token invalid when behind load balancer
      - PGADMIN_CONFIG_WTF_CSRF_SSL_STRICT=False # fix csrf token invalid when behind load balancer
    ports:
      - "5050:80"
    volumes:
      - pgadmin-data:/var/lib/pgadmin

volumes:
  pg-data:
  pgadmin-data:
```
