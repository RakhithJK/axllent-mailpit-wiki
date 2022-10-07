## Content security policy

HTML content can embedded JavaScript or iframes, or link to remote scripts, stylesheets and fonts. Whilst email programs usually have either no or very limited support for such features, web browsers will typically load everything. Mailpit removes any base tags (`<base href="....">`) from HTML emails to ensure embedded images are displayed correctly, however the remainder is left intact. 

The Mailpit UI does have a strict `Content-Security-Policy` header which prevents your browser from loading any remote content, except for images. This means that your web browser will block all iframes, inline & remote JavaScript, remote CSS stylesheets & fonts (eg: Google Fonts) within the UI.

This security measure should not impact how an email displays, and is for your privacy and protection. Emails should not use these features anyway as they are predominantly blocked anyway by both email and webmail clients.

## Referrer policy

The Mailpit UI also uses a `Referrer-Policy: no-referrer`, meaning that any remote requests (when loading remote images) will not provide the remote server with the origin of the request (ie: your Mailpit UI web address).

## Tracking images

Tracking images (eg: in campaign emails) are not blocked. If you wish to block these then you will need to use a browser ad-blocker. All remote images are allowed.