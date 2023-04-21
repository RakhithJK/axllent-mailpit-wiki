Configuring an SMTP relay enables the message "release" feature, which allows you to "forward" the message onto a pre-configured SMTP server.

To enable this feature, either the configuration file (yaml syntax) must be provided to Mailpit either via `--smtp-relay-config <config-file>` or via the environment variable `MP_SMTP_RELAY_CONFIG=<config-file>`.

## Configuration syntax

```yaml
host:           <hostname-or-ip>      # required
port:           <port>                # optional - default 25
starttls:       <true|false>          # optional - default false
allow-insecure: <true|false>          # optional - default false
auth:           <none|plain|cram-md5> # optional - default none
username:       <username>            # required for both plain or cram-md5 auth
password:       <password>            # required for plain auth
secret:         <cram-secret>         # required for cram-md5 auth
return-path:    <bounce-email>        # optional - overrides Return-Path for all released emails
```