The Mailpit search has a number of features that include filtering by `To`, `From`, `Subject`, read/unread status, attachment status, as well as excluding terms by prefixing the term with either a `-` or ` !`. Searches are not case sensitive, and returns up to 200 results.

Some examples include:

- `john doe` - containing the words "john" and "doe" (any order)
- `"john doe"` - containing the phrase "john doe" (exact match)
- `john -doe` - containing "john" but not containing "doe"
- `to:"john doe"` - to "john doe"
- `from:"john doe"` - from "john doe"
- `cc:"john doe"` - cc "john doe"
- `bcc:"john doe"` - bcc "john doe"
- `subject:"john doe"` - "john doe" in the subject line
- `is:read` - with read status
- `is:unread` - with unread status
- `has:attachment` - containing an attachment
- `message-id:12345.678910.JavaMail.j2ee@localhost` - search by Message-ID

Searches can also be combined, for instance `to:john subject:payment` or `from:john is:unread -has:attachment`.