# A record was changed or deleted

For when one or a few records don't match your [records file](your-records-file.md): someone edited one, deleted one,
or a service changed something on its own.

Time: about 10 minutes.

Which company holds your records? It's near the top of your records file, on the line
**DNS company**. Follow the part of each step for that company.

## 1. Find what's different

Check your whole records file with Almanac Check, as [How to check a record](how-to-check-a-record.md)
shows. It lists every record that's different or missing.

## 2. Find out who changed it

This tells you whether a change was a mistake or done on purpose for a reason.

**At Cloudflare:**

1. Sign in at https://dash.cloudflare.com
2. Go to **Manage Account › Audit Log**.
3. Look for recent entries about DNS records. Each shows who made the change and when.

**At GoDaddy:** GoDaddy only keeps a history of record changes for domains with its paid
**Domain Protection**. If yours has it, click **Activity Log** in the menu on the left: it shows
what changed, when, and who did it. If it doesn't, the Activity Log only offers to sell you
Domain Protection, and GoDaddy has no record of who changed what: ask the people who can sign in
to your GoDaddy account.

If a person or a company you work with made the change on purpose, ask them why before
undoing it. If the change was right, update your records file instead (see
[Adding a record](adding-a-record.md)).

## 3. Put the record back

For a TXT record, paste the text without the quote marks around it. If the line just above the
record in your file starts with `; paste:`, copy from that line instead (everything after
`paste: `). Long values are written out there in one piece.

**At Cloudflare:**

1. Sign in at https://dash.cloudflare.com, open your domain, then **DNS › Records**.
2. Find the record by its name and type.
   - **It's there but different:** click **Edit**, and replace the value with the one from your
     file.
   - **It's missing:** click **Add record**. Choose the type, type the name (use `@` for the
     domain itself), and paste the value from your file.
3. If the line in your file ends in `cf-proxied:true`, set **Proxy status** to on (orange
   cloud). Otherwise set it to off (gray cloud, "DNS only").
4. Leave **TTL** on **Auto**.
5. Click **Save**.

**At GoDaddy:**

1. Sign in at https://dcc.godaddy.com/control/portfolio. This is GoDaddy's list of your domains.
2. Click your domain, then **DNS**.
3. Find the record by its type and name. GoDaddy shows 10 records at a time: the page numbers
   are below the list.
   - **It's there but different:** click the pencil in the **Edit** column on its line. Replace
     the **Value** with the one from your file, then click **Save**.
   - **It's missing:** click **Add New Record**. Choose the **Type**, type the **Name** (use `@`
     for the domain itself), paste the **Value** from your file, and click **Save**.
4. Leave **TTL** as GoDaddy sets it.

If GoDaddy asks for a code before it saves, that's its Domain Protection: it sends the code to
your phone or email.

If GoDaddy won't let you change the `@` record of type **A**, the domain is set to forward to
another web address. Forwarding controls that record. Get help before turning it off: it
changes where your domain's web address goes.

## 4. Check it

Wait 5 minutes, then check the record again with
[How to check a record](how-to-check-a-record.md). It should match your file.

## Many records wrong at once?

If more than a handful are wrong or missing, it's faster to put everything back in one go.
See [Putting everything back](putting-everything-back.md).
