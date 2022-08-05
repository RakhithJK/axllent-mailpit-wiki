Mailpit has several configuration options that can be set either via "flags" or environment variables, depending on your preference.

| Environment         | Command line  | Default        | Explanation                                                                                                     |
|---------------------|---------------|----------------|-----------------------------------------------------------------------------------------------------------------|
| `MP_DATA_DIR`       | `--data`      |                | A directory to store persistent data. Default is non-persistent in-memory storage.                              |
| `MP_SMTP_BIND_ADDR` | `--smtp`      | `0.0.0.0:1025` | SMTP bind interface and port.                                                                                   |
| `MP_UI_BIND_ADDR`   | `--listen`    | `0.0.0.0:8025` | HTTP bind interface and port for UI.                                                                            |
| `MP_MAX_MESSAGES`   | `--max`       | `500`          | Maximum number of messages to store. Mailpit will periodically delete the oldest messages if greater than this. |
| `MP_AUTH_FILE`      | `--auth-file` |                | A password file for basic authentication (see [wiki](Basic-authentication) for details).