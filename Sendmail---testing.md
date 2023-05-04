## Configuring sendmail

There are several different options available:


### Use the mailpit binary directly 

You can use `mailpit sendmail` as your sendmail configuration in `php.ini`:
```
sendmail_path = /usr/local/bin/mailpit sendmail
```
### Symlink to the mailpit binary

If Mailpit is found on the same host as sendmail, you can symlink the Mailpit binary to sendmail, eg: `ln -s /usr/local/bin/mailpit /usr/sbin/sendmail`  (only if Mailpit is running on default 1025 port).


### Use a system-installed sendmail binary

You can use your default system `sendmail` binary to route directly to port `1025` (configurable) by calling `/usr/sbin/sendmail -S localhost:1025`. This may vary depending on which implementation of sendmail you are using, and whether it allows you to configure the port.


### Compile Mailpit's sendmail implementation

You can build a Mailpit-specific sendmail binary from source (see [building from source](https://github.com/axllent/mailpit/wiki/Building-from-source)).

## Testing sendmail / Mailpit

These instructions are the easiest way to "send" a test email to Mailpit to ensure it is working. This assumes Mailpit is running, and is listening on port 1025 (default).

Create a text file `email.txt` with the following contents.

```text
From: sender@example.com
To: recipient@example.com
Subject: Email Subject

This is the body of the email.
It can contain multiple lines of text.
```

Then run the following command to "send" your test email:
```shell
mailpit sendmail < email.txt
```

If you are using a system-installed version of sendmail, your command may look like this:
```shell
sendmail -t -S localhost:1025 < email.txt
```

Please note that various packages provide different implementations of sendmail, and they all work slightly different to each other, so please refer to the help of your version of sendmail. Also note that Alpine linux's sendmail implementation (actually part of busybox) has a serious bug which, together with a changes in PHP8, result in a double `\r` in the email headers ([see issue](https://github.com/axllent/mailpit/issues/87)). This causes the email to get rejected as it is invalid. In these cases, the suggestion is to switch to the Mailpit implementation of sendmail instead.