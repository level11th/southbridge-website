---
title: Getting Started
weight: 1
next: /docs/guide
prev: /docs
---

#### Prerequisites

Before starting, you need to have the following software installed:

- [Docker](https://www.docker.com) or [Podman](https://podman.io)
- [PostgreSQL](https://www.postgresql.org) or [Image](https://hub.docker.com/_/postgres) version 14-17 are tested but newer version should work too.
- [Headless Chromium](https://hub.docker.com/r/chromedp/headless-shell)

you need to have these files:
- App image
- genesis.sql (initialize data)

#### Steps

{{% steps %}}

### Start PostgreSQL server

```shell
# start postgresl server container
docker run --name pg -e POSTGRES_PASSWORD=mysecretpassword -d postgres:17.2

# create database name
docker exec pg createdb -U postgres {database name}

# import initialize data
docker exec -i pg psql -U postgres {database name} < genesis.sql

# don't forget to subsitute {database name}
# postgres image will create superuser name postgres as a default. Please refer to the image documentation on how to config.
```

### Start Chromium headless browser

Southbridge using chromium headless browser for rendering PDF.

Start chromium headless browser:

```shell
docker run --rm -d -p 9222:9222 --rm --name chromium --shm-size 2G chromedp/headless-shell:latest
```

### Configure application enviroment

Southbridge need enviroment variables to run properly.
you can config enviroment depends on how you deploy.
this example using `.env` file

```env
APP_BASE_URL=http://localhost:8080
APP_ADDR=:8080
APP_ENV=PRODUCTION
DB_URL=postgres://postgres:mysecretpassword@pg/{database name}?sslmode=disable
SESS_SECRET=secret
TIMEZONE=Asia/Bangkok
FEATURES=migrate_role,worker
CHROME_REMOTE_URL=http://chromium:9222
```

See [configuration](/docs/guide/configuration) for full list of environment variables.

### Start Southbridge application
```shell
docker run --name app --env-file ./env image
```
Your site is available at `http://localhost:8080/`.

{{% /steps %}}
