## Unable to receive live web UI message updates

If you are using a proxy server (for example Nginx or Apache) to access your Mailpit instance, then your proxy configuration must be adjusted to include the protocol `Upgrade` headers. Please refer to the [Nginx](https://www.nginx.com/blog/websocket-nginx/) & [Apache](https://httpd.apache.org/docs/2.4/mod/mod_proxy_wstunnel.html) documentation for details how to do this.


## No browser notifications for new messages

This feature is only possible when accessing your Mailpit web UI via HTTPS. This is not a restriction of Mailpit, this is a browser security feature. Please refer to the [HTTPS documentation](HTTPS)


## XMLHttpRequest blocked by CORS policy

> Access to XMLHttpRequest at 'http://example.com/api/v1/messages' from origin 'http://anotherexample.com/' has been blocked by CORS policy: No 'Access-Control-Allow-Origin' header is present on the requested resource.

If you are trying to access your Mailpit API via browser JavaScript from another domain, you will need to specifically allow CORS (cross-origin resource sharing) from that domain.

By default Mailpit does not contain a CORS policy. The `Access-Control-Allow-Origin` header can be manually set (for API calls only), for example either via the `--api-cors "*"` flag, or `MP_API_CORS="*"` environment variable.


## Errors returned when using busybox's sendmail implementation (eg: Alpine Linux)

This is an issue with that implementation of sendmail (see [issue #87](https://github.com/axllent/mailpit/issues/87#issuecomment-1502720004)). 
