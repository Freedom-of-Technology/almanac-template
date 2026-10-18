# Email stopped working

For when email to you isn't arriving, or email you send bounces back or lands in people's spam.

Time: about 15 minutes.

## 1. Make sure it's not just one person

Send an email to yourself from a personal account (Gmail, Yahoo, Outlook). Then reply to it.

- Both work: your records are probably fine. The problem is with the one sender or receiver.
  Ask them to check their spam folder.
- Either one fails: carry on.

## 2. Let Google check your email records

1. Open https://toolbox.googleapps.com/apps/checkmx/
2. Type your domain, for example `freedomoftechnology.com`, and click **Run checks!**
3. It lists anything wrong. Note which items it flags.

## 3. Compare your email records with your file

In your [records file](your-records-file.md), the email records are under **Email**. There are four kinds:

| Name in the file | Type | What it's for | If it's wrong |
| --- | --- | --- | --- |
| `@` (five lines) | MX | Where incoming email goes | Email to you doesn't arrive |
| `@`, starting `v=spf1` | TXT | Who may send as you | What you send lands in spam or bounces back |
| `google._domainkey` | TXT | Google's signature on what you send | What you send lands in spam or bounces back |
| `_dmarc` | TXT | What to do with fake email using your name | Usually nothing you'd notice |

If your file doesn't have one of these, skip it.

The `_dmarc` record is also why you get daily report emails. Reading the latest one can show
which of these checks is failing: see [Report emails about your domain](dmarc-reports.md).

If your DNS company is GoDaddy, the "who may send as you" record may be split over two lines:
the `@` one says `include:dc-` and a name ending in `._spfm`, and a second line has that name.
GoDaddy does this by itself when a service connects to your domain. Both lines are needed: check
both.

Check each one with [How to check a record](how-to-check-a-record.md).

## 4. Fix what doesn't match

Follow [A record was changed or deleted](record-changed-or-deleted.md) for each record that's
different or missing. Copy the value from the file exactly, letter for letter.

The `google._domainkey` value is too long to fit in one piece, so the record itself is split
into pieces. Don't copy those. Just above it there's a note line starting `; paste:`. Copy
everything after `paste:` and its space on that line: it's the whole value in one go.

## 5. Check Google's side

Sign in at https://admin.google.com and go to **Apps › Google Workspace › Gmail ›
Authenticate email**. It should say **Authenticating email with DKIM**. If it doesn't, click
**Start authentication**.

If Google says the record doesn't match, Google may have a newer value than your file. Get
help rather than generating a new one yourself: the file and your DNS company both need the
new value at the same time.

## 6. Test again

Wait 15 minutes, then repeat step 1.
