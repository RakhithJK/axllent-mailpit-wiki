Mailpit has several configuration options that can be set either via "flags" or environment variables, depending on your preference.

| Environment            | Command line       | Default        | Explanation                                                                                                     |
|------------------------|--------------------|----------------|-----------------------------------------------------------------------------------------------------------------|
| `MP_DATA_DIR`          | `--data`           |                | A directory to store persistent data. Default is non-persistent in-memory storage.                              |
| `MP_SMTP_BIND_ADDR`    | `--smtp`           | `0.0.0.0:1025` | SMTP bind interface and port.                                                                                   |
| `MP_UI_BIND_ADDR`      | `--listen`         | `0.0.0.0:8025` | HTTP bind interface and port for UI.                                                                            |
| `MP_MAX_MESSAGES`      | `--max`            | `500`          | Maximum number of messages to store. Mailpit will periodically delete the oldest messages if greater than this. |
| `MP_UI_AUTH_FILE`      | `--ui-auth-file`   |                | A password file for basic authentication ([see wiki](Basic-authentication)).                                    |
| `MP_UI_SSL_CERT`       | `--ui-ssl-cert`    |                | SSL certificate for web UI - requires ssl-key ([see wiki](HTTPS))                                               |
| `MP_UI_SSL_KEY`        | `--ui-ssl-key`     |                | SSL key for web UI - requires ssl-cert ([see wiki](HTTPS))                                                      |
| `MP_SMTP_AUTH_FILE`    | `--smtp-auth-file` |                | A password file for SMTP authentication ([see wiki](SMTP-with-STARTTLS-and-authentication)).                    |
| `MP_SMTP_SSL_CERT`     | `--smtp-ssl-cert`  |                | SSL certificate for SMTP - requires smtp-ssl-key ([see wiki](SMTP-with-STARTTLS-and-authentication))            |
| `MP_SMTP_SSL_KEY`      | `--smtp-ssl-key`   |                | SSL key for SMTP - requires smtp-ssl-cert ([see wiki](SMTP-with-STARTTLS-and-authentication))                   |