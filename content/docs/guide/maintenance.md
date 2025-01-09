---
title: Maintenance
weight: 4
---

### Check Southbridge version

```shell
docker run --rm app-image:tag version
```

### Update database notify trigger
Soutbridge application rely on PostgreSQL trigger feature to notify an mutation event of tables. use this command to recreate every notification triggers in database. (`super user` is required)

```shell
docker run --rm app-image:tag update notify [db connection with super user]
```

or

```shell
docker run --rm -e SUPER_USER_DB_URL="db_conn_str" app-image:tag update notify
```

### Update database Southbridge application's role
update database roles to match current version of the application

```shell
docker run --rm app-image:tag update role [db connection]
```
