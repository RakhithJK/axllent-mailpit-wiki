You can view available Docker images on [https://hub.docker.com/r/axllent/mailpit](https://hub.docker.com/r/axllent/mailpit)

An basic example of running Mailpit within Docker:

```
docker run --rm \
-p 8025:8025 \
-p 1025:1025 \
axllent/mailpit
```
You need to ensure you map the correct ports (default Web UI on 8025 and SMTP on 1025). 

## Setting Mailpit options

@TODO