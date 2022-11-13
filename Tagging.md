Mailpit allows you to tag messages with one or more tags. Message tags can be added, edited and deleted via the web UI when viewing a message, as well as automatically applied when receiving emails.

Tags can then be seen in the web UI and filtered by in the search. Please note that viewing is limited to 200 results per tag.


## Allowed tag names

Tags are limited to the following characters: `a-z`, `A-Z`, `0-9`, `-`, ` ` & `_`, and must be a minimum of 3 characters.


## Filtering

Filtering is simply a string match, meaning the filter you set must match something anywhere in the raw message (message source). Filtering is all converted to lowercase, so casing does not matter.


## Automatically tagging messages

Basic tag filtering can be set using the `--tag` flag when starting Mailpit. For each tag filter the string is matched to the entire email (including headers and body), and the tag is applied. Messages can have multiple tags, and duplicate tags are ignored.


## Example syntax

All tags are specified within a single `--tag <options>` flag. the tag options should be quoted, and within the options each separate tag and match are space-separated.

```
--tag 'user=user@example.com user2=user2@example.com "Scanned with antivirus"="X-Antivirus: "'
```
In the above example all messages containing `user@example.com` are tagged with `user`, all messages containing `user2@example.com` are tagged with `user2`, and all messages containing `X-Antivirus: ` are tagged with `Scanned with antivirus`.