---
title: Maintenance
weight: 4
---

### Check the Southbridge Version

```shell
docker run --rm app-image:tag version
```

### Update Database Notification Triggers
The Southbridge application uses PostgreSQL triggers to send notifications when table data changes. Use the following command to recreate all notification triggers in the database. Superuser privileges are required.

```shell
docker run --rm app-image:tag update notify [db connection with superuser]
```

Alternatively:

```shell
docker run --rm -e SUPER_USER_DB_URL="db_conn_str" app-image:tag update notify
```

### Update Database Roles for the Southbridge Application
Use this command to update the database roles to match the current version of the application.

```shell
docker run --rm app-image:tag update role [db connection]
```

### Hash a Given Password
This command is useful when you need to change a user's password by directly replacing the hashed password in the database. It will output the hashed version of the provided password.

```shell
docker run --rm app-image:tag hash [password]
``` 


### Debug the runtime

The Southbridge application uses [gcr.io/distroless/static-debian12:nonroot](https://github.com/GoogleContainerTools/distroless) as its runtime.

You can debug the runtime using the image tag `gcr.io/distroless/static-debian12:debug-nonroot`.  
For example:

```shell
docker run --rm -it gcr.io/distroless/static-debian12:debug-nonroot

$ id
uid=65532(nonroot) gid=65532(nonroot) groups=65532(nonroot)
```
