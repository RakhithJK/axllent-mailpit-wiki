Mailpit stores incoming emails using [CloverDB](https://github.com/ostafen/clover), which uses [BadgerDB](https://github.com/dgraph-io/badger) under the hood. It supports two storage mechanisms, namely in-memory and persistent.

## In-memory storage (default)

Mailpit will by default store messages in memory. The advantage is a zero-configuration database that is ready to go. 

There are however some downsides to this. For starters, when Mailpit is shut down or restarted, all stored emails are lost. Secondly, depending on how many emails you wish to store (and more importantly, how big they are), this uses the system memory (RAM). Lastly, due to a (security?) [feature](https://github.com/dgraph-io/badger/issues/60) in BadgerDB, **in-memory storage is limited to a maximum of 1MB per email**.

## Persistent storage (on-disk file storage)

Mailpit allows you to provide a path to a directory for persistent database storage (`--data <path>`). This means that the physical email database is stored within this directory, and will survive restarts. There is effectively no restriction to email size, and it does not get reserved in RAM.

Persistent storage does however can take up quite a considerable storage on your harddrive, specifically when Mailpit is running. BadgerDB creates a temporary additional 2GB file which it uses internally for logging, which is then removed when Mailpit is shut down. In addition to this, when emails are deleted from the database, previously-used space is not immediately reclaimed, but over time CloverDB will attempt to reclaim what it can. This is simply a design feature of BadgerDB, not a bug.
