Mailpit requires messages to be delivered via SMTP. Emails can come directly from and email client (eg: Thunderbird), or via a mail transfer agent (MTA) such as `sendmail` (which is commonly used with applications such as PHP). Mailpit has its own implementation of sendmail for convenience (by default delivering to `localhost:1025` instead of `localhost:25`), however you can theoretically use any existing sendmail provided it allows you to set the delivery host/port.

Please note that Mailpit's implementation of sendmail is not intended to deliver email to other SMTP servers, only Mailpit. It may work, but is not recommended.

There are several different options available:


### Use the mailpit binary directly 

You can use `mailpit sendmail` as your sendmail configuration in `php.ini`:
```
sendmail_path = /usr/local/bin/mailpit sendmail
```

If your Mailpit server is not running on the default 1025 port or on another machine, then this can be set by adding `--smtp-addr <host>:<port>` to the sendmail command.


### Symlink to the mailpit binary

If Mailpit is found on the same host as sendmail, you can symlink the Mailpit binary to sendmail, eg: `ln -s /usr/local/bin/mailpit /usr/sbin/sendmail`  (only if Mailpit is running on default 1025 port).


### Use a system-installed sendmail binary

You can use your default system `sendmail` binary to route directly to port `1025` (configurable) by calling `/usr/sbin/sendmail -S localhost:1025`. This may vary depending on which implementation of sendmail you are using, and whether it allows you to configure the port.


### Compile Mailpit's sendmail implementation

You can build a Mailpit-specific sendmail binary from source (see [building from source](https://github.com/axllent/mailpit/wiki/Building-from-source)).


## Mailpit's sendmail options

Mailpit's sendmail works very similar to other implementations, and shares several of the common flags (even if most are ignored and simply exist for compatibility).

To view all options, see `mailpit sendmail -h`

```
Usage:
  mailpit sendmail [flags] [recipients]

Flags:
  -f, --from string        SMTP sender
  -b, --long-b             Ignored. This flag exists for sendmail compatibility.
  -i, --long-i             Ignored. This flag exists for sendmail compatibility.
  -o, --long-o             Ignored. This flag exists for sendmail compatibility.
  -s, --long-s             Ignored. This flag exists for sendmail compatibility.
  -t, --long-t             Ignored. This flag exists for sendmail compatibility.
  -S, --smtp-addr string   SMTP server address (default "localhost:1025")
  -v, --verbose            Verbose mode (sends debug output to stderr)
```