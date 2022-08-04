# Basic authentication

Basic authentication can be added to Mailpit by supplying it with a password file (eg: [Apache htpassword](https://httpd.apache.org/docs/current/programs/htpasswd.html).

Mailpit currently supports multiple users & passwords in a single password file, and the passwords in the following formats:

- SSHA
- MD5Crypt
- APR1Crypt
- SHA
- Bcrypt
- Plain text
- Crypt with SHA-256 and SHA-512

## Examples

A plain text password file would look like:
```
user1:password1
user2:password2
```
or encrypted like:
```
user1:$apr1$rja5hy8u$0DN2pENpLk1d4BqgPEho61
user2:$apr1$asfohhn3$WXNtWWEnCMRFkI75J3exy1
```

Save your file and start Mailpit using the `--auth-file <path-to-file>`. Note that if your password file is blank then all access is blocked. If you modify your password file while Mailpit is running, then you will need to restart Mailpit.
