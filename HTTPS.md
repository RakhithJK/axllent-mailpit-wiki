HTTPS can be enabled for the web UI simply by providing Mailpit with an SSL key & certificate, depending on your requirements.

For this you require **both** the SSL certificate and private key set in the Mailpit flags or environment variables, for example:

```
mailpit --ssl-cert path/to/cert.pem --ssl-key /path/to/privkey.pem 
```

Certificates can be both self-signed/generated or official certificates (if you have a valid domain name) obtained via sources like [Let's Encrypt](https://letsencrypt.org/).

## Creating a self-signed certificate

Please note that self-signed certificates will issue browser warnings, and that the Common Name (when asked) should match the IP address or hostname you are accessing Mailpit with:

```
openssl req -x509 -newkey rsa:4096 -nodes -keyout privkey.pem -out cert.pem -sha256 -days 365
```