---
title: Getting Started
weight: 1
next: /docs/guide
prev: /docs
---

#### Prerequisites

Before starting, you need to have the following software installed:

- [Docker](https://www.docker.com) or [Podman](https://podman.io)
- [PostgreSQL](https://www.postgresql.org) or its [Docker image](https://hub.docker.com/_/postgres). Versions 14–17 have been tested, but newer versions should work too.
- [Headless Chromium](https://hub.docker.com/r/chromedp/headless-shell)

You also need the following:

- Application image
- `table.sql` (database schema)
- `genesis.sql` (initial data)

#### Steps

{{% steps %}}

### Prepare database schema SQL files
The Southbridge application image contains the matching database schema in `/home/nonroot/table.sql`.

```shell
# Create a Docker container and copy table.sql from it.

cid=$(docker create -q image:tag)
docker cp $cid:/home/nonroot/table.sql table.sql && docker rm $cid
```

Contact our team to obtain `genesis.sql`.

### Start the PostgreSQL server

```shell
# Start the PostgreSQL server container.
docker run --name pg -e POSTGRES_PASSWORD=mysecretpassword -d postgres:17.2

# Create the database.
docker exec pg createdb -U postgres {database name}

# Initialize the database schema from table.sql.
docker exec -i pg psql -U postgres {database name} < table.sql

# Import initial data from genesis.sql.
docker exec -i pg psql -U postgres {database name} < genesis.sql

# Replace {database name} with your database name.
```
**Note:** The PostgreSQL image creates a superuser named `postgres` by default. See the [PostgreSQL Docker Hub page](https://hub.docker.com/_/postgres) for configuration details.

### Start the Chromium headless browser

Southbridge uses the Chromium headless browser to render PDFs.

Start the Chromium headless browser:

```shell
docker run --rm -d -p 9222:9222 --init --name chromium --shm-size 2G chromedp/headless-shell:latest
```
For more details about the image, see [docker-headless-shell](https://github.com/chromedp/docker-headless-shell).

### Configure the application environment

Southbridge needs environment variables to run properly.
How you configure them depends on your deployment method.
This example uses an `.env` file:

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

See [configuration](/docs/guide/configuration) for a full list of environment variables.

### Start the Southbridge application
```shell
docker run --name app --env-file ./env image
```
Your site is available at `http://localhost:8080/`.

{{% /steps %}}
