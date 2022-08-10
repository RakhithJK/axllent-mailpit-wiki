Mailpit stores incoming emails using [CloverDB](https://github.com/ostafen/clover), which uses [BadgerDB](https://github.com/dgraph-io/badger) under the hood. It supports two storage mechanisms, either namely in-memory or persistent on-disk storage.


## In-memory storage (default)

Mailpit will by default store messages in memory. The advantage is a zero-configuration database that is ready to go. 

There are however some downsides to this, depending on your requirements. For starters, when Mailpit is shut down or restarted, all stored emails are lost. Secondly, depending on how many emails you wish to store (and more importantly, how big they are), this uses the system memory (RAM). Lastly, due to a (security?) [feature](https://github.com/dgraph-io/badger/issues/60) in BadgerDB, **in-memory storage is limited to a maximum of 1MB per email**. This means that any email larger than 1MB returns a SMTP error to the client.


## Persistent storage (on-disk file storage)

Mailpit allows you to provide a path to a directory for persistent database storage (`--data <path>`). This means that the physical email database is stored within this directory and will survive restarts. There is effectively no restriction to email size, and it does not get stored in RAM.

Persistent storage does however can take up quite a considerable storage on your harddrive depending on how many emails are stored. When deleting emails, BadgerDB will eventually reclaim the space, but this can take time. This is simply a design feature of BadgerDB, not a bug.
