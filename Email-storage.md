As of version 1.0.0, Mailpit stores all email data in a SQLite database. Older releases used to use a different format (BadgerDB), however there were several reasons to switch the backend databases which have been [documented here](https://github.com/axllent/mailpit/issues/10).

Mailpit stores both an email summary and the raw email (compressed with zstd) in the database, has two storage options:

## Temporary storage (default)

Mailpit will by default create a temporary database to store its data. When the applications terminates, the temporary database is deleted from disk.


## Persistent storage

Mailpit allows you to provide a path to a file for persistent database storage (`--db-file <file-path>`). This file will not get deleted when the application terminates, and restarting Mailpit with the same `--db-file` will reload previous stored messages.