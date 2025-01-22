---
title: Troubleshoot
weight: 7
---

#### Mount File Permissions
When the application shows an error indicating "open file permission denied," ensure that you change the file owner to `65532` and set the appropriate permissions before mounting the file to the container.

```shell
chmod 400 ca.crt
chown 65532:65532 ca.crt

docker run --rm -v /home/foo/ca.crt:/home/nonroot/ca.crt:ro southbridge
```
