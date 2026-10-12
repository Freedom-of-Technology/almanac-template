# How to check a record

This shows what the internet sees for your records, so you can compare it with your
[records file](your-records-file.md). You only need a web browser.

There are two ways:

- **Check the whole file at once** with FreeOT's free Almanac Check. Start here, especially if
  you're not sure which record is the problem.
- **Look up one record** with Google's free lookup page, when a guide or a company names the
  record to check.

## Check the whole file

1. Open your domain's records file (the links are in [Your records file](your-records-file.md)).
2. Just above the file, at the right, there's a row of small buttons. Click the one with two
   squares, one on top of the other. If you rest the mouse on it, it says **Copy raw file**.
3. Open Almanac Check: https://freedomoftechnology.com/tools/domain-check/
4. Click **Paste it instead**, click in the box that opens, and paste (Ctrl+V on Windows,
   Command+V on a Mac).
5. Click **Check it**.

If you've saved a copy of the file on your computer, you can click **Choose a file** instead,
or drag the file onto the page.

Your file stays on your computer: the page doesn't upload it anywhere. It checks each record by
asking the same public questions any web browser or email server asks.

The page says whether everything matches. If something doesn't, it lists it under **Needs a
look**, shows what your file says next to what's live, and names the guide to follow. Records
marked **Cloudflare answers** or **GoDaddy website** are fine: the page explains why at the bottom.

It can't see records that are live but missing from your file. If you suspect one, ask FreeOT.

## Look up one record

### Read the line in your records file

Each record is one line. For example:

```
_dmarc   300   IN  TXT   "v=DMARC1; p=reject; rua=mailto:dmarc@freedomoftechnology.com"
```

| Part | Here | What it means |
|---|---|---|
| Name | `_dmarc` | Which address the record is for. `@` means the domain itself, like freedomoftechnology.com. Anything else goes in front: `_dmarc` means `_dmarc.freedomoftechnology.com`. |
| Number | `300` | How many seconds other computers remember the answer. You can ignore it. |
| `IN` | | Always there. Ignore it. |
| Type | `TXT` | The kind of record. The common ones: **MX** says where email goes. **TXT** is text other services read. **CNAME** points one name at another. **A** points a name at an internet address. |
| Value | `"v=DMARC1; ..."` | What the record says. This is the part that has to match exactly. |

### Look it up

1. Open Google's free lookup page: https://toolbox.googleapps.com/apps/dig/
2. In **Name**, type the full name: the record's name, a dot, then your domain. For `@`, type
   just the domain.
3. Click the record's type (MX, TXT, CNAME or A).
4. Compare what it shows with the value in your file.

Shortcut: a link like this one opens the page with everything filled in. Change the end to the
type and name you want:
https://toolbox.googleapps.com/apps/dig/#MX/freedomoftechnology.com

### What you might see

- **It matches.** That record is fine.
- **It's different.** Someone changed it. Follow
  [A record was changed or deleted](record-changed-or-deleted.md).
- **Nothing comes back.** The record is missing. Same guide.
- **A website record shows numbers instead of the name in your file.** That's normal for lines
  ending in `cf-proxied:true`. Cloudflare stands in front of your website and answers with its
  own numbers. Numbers showing up means the record is there.
- **Records with a note saying GODADDY EXTRA.** GoDaddy added these by itself. They're live,
  so check them like any other record, and leave them in place. On GoDaddy's own records page,
  the `@` records of type **A** show as one line saying **WebsiteBuilder Site** instead of the
  numbers in your file. That's the same thing.
- **Extra values you don't recognize, next to the right ones.** Check the file again. If they're
  not in it, ask before deleting them: a company may have added one for a reason.

Just fixed something and it still looks wrong? Wait 5 minutes and look again.
