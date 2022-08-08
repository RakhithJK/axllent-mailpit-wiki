You can view available Docker images on [https://hub.docker.com/r/axllent/mailpit](https://hub.docker.com/r/axllent/mailpit)

An basic example of running Mailpit within Docker:

```
docker run -d \
--restart unless-stopped \
--name=mailpit \
-p 8025:8025 \
-p 1025:1025 \
axllent/mailpit
```
You need to ensure you map the correct ports (default Web UI on 8025 and SMTP on 1025). 

## Setting Mailpit options

Refer to [the wiki](https://github.com/axllent/mailpit/wiki/Runtime-options) for a list of runtime options. Environment variables can be set using the `-e` flag when starting your docker container, for instance:


```
docker run -d \
--name=mailpit \
--restart unless-stopped \
-e MP_DATA_DIR=/mailpit/data/ \
-e MP_UI_AUTH_FILE=/mailpit/authfile \
-e TZ=Europe/London \
-p 8025:8025 \
-p 1025:1025 \
axllent/mailpit
```