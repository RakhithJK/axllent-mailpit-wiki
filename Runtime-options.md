| Environment                   | Command line                 | Default        | Explanation                                                                                                     |
|-------------------------------|------------------------------|----------------|-----------------------------------------------------------------------------------------------------------------|
| `MP_DATA_FILE`                | `--db-file`                  |                | A database filename to store persistent data. Default is a temporary file.                                      |
| `MP_SMTP_BIND_ADDR`           | `--smtp`                     | `0.0.0.0:1025` | SMTP bind interface and port.                                                                                   |
| `MP_UI_BIND_ADDR`             | `--listen`                   | `0.0.0.0:8025` | HTTP bind interface and port for UI.                                                                            |
| `MP_MAX_MESSAGES`             | `--max`                      | `500`          | Maximum number of messages to store. Mailpit will periodically delete the oldest messages if greater than this. |
| `MP_TAG`                      | `--tag`                      |                | Tag new messages matching filters ([see wiki](Tagging))                                                         |
| `MP_WEBROOT`                  | `--webroot`                  | `/`            | Set the webroot for web UI & API                                                                                |
| `MP_API_CORS`                 | `--api-cors`                 |                | Set API CORS Access-Control-Allow-Origin header ([see wiki](CORS))                                              |
| `MP_USE_MESSAGE_DATES`        | `--use-message-dates`        |                | Use message dates as the received dates                                                                         |
| `MP_IGNORE_DUPLICATE_IDS`     | `--ignore-duplicate-ids`     |                | Ignore duplicate messages (by Message-Id)                                                                       |
| `MP_UI_AUTH_FILE`             | `--ui-auth-file`             |                | A password file for basic authentication ([see wiki](Basic-authentication)).                                    |
| `MP_UI_TLS_CERT`              | `--ui-tls-cert`              |                | TLS certificate for web UI - requires --ui-tls-key ([see wiki](HTTPS))                                          |
| `MP_UI_TLS_KEY`               | `--ui-tls-key`               |                | TLS key for web UI - requires --ui-tls-cert ([see wiki](HTTPS))                                                 |
| `MP_SMTP_AUTH_FILE`           | `--smtp-auth-file`           |                | A password file for SMTP authentication ([see wiki](SMTP-with-STARTTLS-and-authentication)).                    |
| `MP_SMTP_AUTH_ACCEPT_ANY`     | `--smtp-auth-accept-any`     |                | Accept any SMTP username and password, including none                                                           |
| `MP_SMTP_TLS_CERT`            | `--smtp-tls-cert`            |                | TLS certificate for SMTP STARTTLS - requires --smtp-tls-key ([see wiki](SMTP-with-STARTTLS-and-authentication)) |
| `MP_SMTP_TLS_KEY`             | `--smtp-tls-key`             |                | TLS key for SMTP STARTTLS - requires --smtp-tls-cert ([see wiki](SMTP-with-STARTTLS-and-authentication))        |
| `MP_SMTP_AUTH_ALLOW_INSECURE` | `--smtp-auth-allow-insecure` |                | Enable insecure PLAIN & LOGIN authentication                                                                    |
| `MP_SMTP_RELAY_CONFIG`        | `--smtp-relay-config`        |                | SMTP configuration file to allow releasing messages ([see wiki](SMTP-relay))                                    |
| `MP_SMTP_RELAY_ALL`           | `--smtp-relay-all`           |                | Relay all incoming messages via external SMTP server (caution! [see wiki](SMTP-relay))                          |
| `MP_QUIET`                    | `--quiet`                    |                | Quiet logging (errors only)                                                                                     |
| `MP_VERBOSE`                  | `--verbose`                  |                | Verbose logging                                                                                                 |
