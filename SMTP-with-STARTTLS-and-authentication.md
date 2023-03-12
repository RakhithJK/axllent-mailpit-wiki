Mailpit supports SMTP encryption via STARTTLS, with optional authentication (`PLAIN` & `LOGIN`). RFC 4954 specifies that plaintext authentication mechanisms such as LOGIN and PLAIN require a TLS connection. If you wish to enable insecure authentication (ie: not use STARTTLS), you should use the `--smtp-auth-allow-insecure` flag.

## SMTP with STARTTLS

To configure Mailpit to serve SMTP with STARTTLS, a SSL certificate and private key must be provided via either the command flags or environment when starting Mailpit, for example:

```
mailpit --smtp-tls-cert /path/to/cert.pem --smtp-tls-key /path/to/privkey.pem 
```

Certificates can be both self-signed/generated or official certificates (if you have a valid domain name) obtained via sources like [Let's Encrypt](https://letsencrypt.org/).

### Creating a self-signed certificate

Please note that self-signed certificates will issue email client warnings (so you will have to allow the insecure connection/certificate), and that the Common Name (when asked) should match the hostname hostname you are using to send via STARTTLS:

```
openssl req -x509 -newkey rsa:4096 -nodes -keyout privkey.pem -out cert.pem -sha256 -days 3650
```

In addition, some SMTP clients may require the SAN (Subject Alt Name) to match the hostname you are using for your client, in which case you should append `-addext "subjectAltName = DNS:<hostname>"` to the argument above, eg:

```
openssl req -x509 -newkey rsa:4096 -nodes -keyout privkey.pem -out cert.pem -sha256 -days 3650 -addext "subjectAltName = DNS:localhost"
```

## SMTP authentication

To use SMTP authentication Mailpit must also be using STARTTLS (see above), or use the `--smtp-auth-allow-insecure` flag. A file containing one or more usernames & password can be provided in exactly the same manner. This file syntax is exactly the same as a [basic authentication](Basic-authentication), so you could reuse one you already are using for the web UI, or create a unique one.

SMTP clients will then need to provide plain text / normal authentication details using a STARTTLS connection to send.

To run Mailpit with STARTTLS SMTP authentication:

```
mailpit --smtp-auth-file /path/to/password-file --smtp-tls-cert /path/to/cert.pem --smtp-tls-key /path/to/key.pem 
```

For testing purposes, Mailpit also allows you to accept any username & password (or none) by using the `--smtp-auth-accept-any` flag. 