# Email stopped working

For when email to you isn't arriving, or email you send bounces back or lands in people's spam.

Time: about 15 minutes.

## 1. Make sure it's not just one person

Send an email to yourself from a personal account (Gmail, Yahoo, Outlook). Then reply to it.

- Both work: your records are probably fine. The problem is with the one sender or receiver.
  Ask them to check their spam folder.
- Either one fails: carry on.

## 2. Let Google check your email records

Google has a free page that checks any domain's email records, whichever company runs your
email.

1. Open https://toolbox.googleapps.com/apps/checkmx/
2. Type your domain, for example `freedomoftechnology.com`.
3. If your records file has a signature record (step 3 says how to spot one), type the part of
   its name before `._domainkey` in **DKIM selector**, for example `google`. If it has more than
   one, check each in turn.
4. Click **Run checks!** It lists anything wrong. Note which items it flags.

The page is made for Google's own email service. If another company runs your email, ignore
anything it says about Google's servers or settings.

## 3. Compare your email records with your file

In your [records file](your-records-file.md), the email records are under headings starting
**Email**. There are four kinds:

| Name in the file | Type | What it's for | If it's wrong |
| --- | --- | --- | --- |
| `@`, one or more lines | MX | Where incoming email goes | Email to you doesn't arrive |
| `@`, starting `v=spf1` | TXT | Who may send as you | What you send lands in spam or bounces back |
| A name ending in `._domainkey` | TXT or CNAME | A service's signature on what it sends as you | What you send lands in spam or bounces back |
| `_dmarc` | TXT | What to do with fake email using your name | Usually nothing you'd notice |

Each service that sends email as you, such as the company that runs your email or your
website's contact form, can have its own signature record. The note above each one says which
service it's for.

If your file doesn't have one of these, skip it. Your file may have other email records too,
such as `autodiscover`. The note above each says what it's for: check those the same way.

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

A signature value is often too long to fit in one piece, so the record itself is split into
pieces. Don't copy those. Just above it there's a note line starting `; paste:`. Copy
everything after `paste:` and its space on that line: it's the whole value in one go.

## 5. Check the signature at the service that made it

Skip this step if your file has no signature records.

The note above each signature record says which service made it, and where in that service's
settings it's shown. Sign in there and check the service says it's signing your email. If it
says signing is off, turn it back on there.

If the service says the record doesn't match, it may have a newer value than your file. Get
help rather than making a new one yourself: the file and your DNS company both need the new
value at the same time.

If a note doesn't say where the service shows it, get help (below).

## 6. Test again

Wait 15 minutes, then repeat step 1.

## Getting help

Contact FreeOT at almanac-check@freedomoftechnology.com. Say which guide you were on and what you saw.
