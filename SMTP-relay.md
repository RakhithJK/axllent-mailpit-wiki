Configuring an SMTP relay enables the message "release" feature, which allows you to "forward" the message onto a pre-configured SMTP server.

To enable this feature, the configuration file (yaml syntax) must be provided to Mailpit either via `--smtp-relay-config <config-file>` or the environment variable `MP_SMTP_RELAY_CONFIG=<config-file>`.

## SMTP relay configuration

```yaml
host:                <hostname-or-ip>      # required
port:                <port>                # optional - default 25
starttls:            <true|false>          # optional - default false
allow-insecure:      <true|false>          # optional - default false
auth:                <none|plain|cram-md5> # optional - default none
username:            <username>            # required for both plain or cram-md5 auth
password:            <password>            # required for plain auth
secret:              <cram-secret>         # required for cram-md5 auth
return-path:         <bounce-address>      # optional - overrides Return-Path for all released emails
recipient-allowlist: '@example\.com$'      # optional - regex to limit allowed relay addresses or domains (see below)
```

### Notes
Messages relayed via the web UI / API, they get assigned a new unique `Message-Id`. This is to enable testing via services such as Gmail which will silently drop / hide incoming emails containing the same message ID. 

The `return-path` configuration option will add / overwrite the `Return-Path` for all messages relayed via the web UI and API. This is useful to provide a valid email address to catch any accidental bounces and prevent SPF errors for email domain names. Servers such as Gmail have become very pedantic about the mail they accept, and unresolvable Return-Path addresses, or unauthorised Return-Path addresses (SPF / DMARC) get rejected very easily.

#### Recipient allowlist

The optional `recipient-allowlist` allows you to set a regular expression (Go format) to limit which addresses or domains you wish to limit to (applies to both released & relayed messages). Please note that the regular expression should be quoted with single apostrophes (`'`) to avoid parsing errors. You can use https://regex101.com/r/mfbicW/1 as a playground to test your expression.


## Relaying all messages

The `--smtp-relay-all` flag (or `MP_SMTP_RELAY_ALL` environment variable) can be set to automatically relay all incoming messages via the configured SMTP relay server. This means that Mailpit will act like a caching proxy server, and automatically pass on any incoming email to the configured SMTP server and store a local copy. The incoming email is not modified (unlike releasing via the web UI / API), and the message is simply passed through as-is. This option should be used with caution.