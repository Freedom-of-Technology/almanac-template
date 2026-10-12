# Putting everything back

For the big problems:

- Your DNS company lost your records, or many are wrong at once.
- You're locked out of your DNS company account.
- You're moving your DNS to a different company.

Time: about an hour. This is the guide where it's most worth asking for help if you're unsure.

Which company holds your records? It's near the top of your records file, on the line
**DNS company**.

Steps 3 and 4 are only for when your records are going somewhere new: to a different company, or
to a new Cloudflare account because you're locked out of the old one. Then your website and
email can stop working for a while during step 4, so pick a quiet time. In steps 1 and 2, follow
the part for where your records are going.

## Before you start

You'll need:

- A copy of your records file, saved on your computer. Follow "To save a copy on your
  computer" in [Your records file](your-records-file.md). It has a link straight to each
  domain's file.
- A sign-in for your DNS company.
- If your records are going somewhere new: a sign-in for the company you bought the domain from
  (for most businesses, GoDaddy), for steps 3 and 4.

Your sign-ins are saved in your password manager.

**Locked out?**

- **Cloudflare:** make a new Cloudflare account in your business's name, and follow this guide
  with it.
- **GoDaddy:** GoDaddy usually holds the domain itself as well as its records, so you have to get
  back in; there's no going around it. If you know the account's email address and can still
  read that email, reset the password at https://www.godaddy.com/help/reset-my-godaddy-password-8.
  If not, use GoDaddy's account recovery: https://supportcenter.godaddy.com/accountrecovery. It
  asks for a photo of your ID, and business papers if the account is in the business's name.
  Then get help with the rest.

## First, make sure the file hasn't been tampered with

Everything in the file goes live, so check it before you use it. Look at its recent changes:
follow "To see what changed" in [Your records file](your-records-file.md).

Every change should be one you recognize: one you made, or one FreeOT told you about. **Stop and
get help before going on** if you see a change you don't recognize, especially to:

- an email record (type **MX**), which could send your email to someone else, or
- a line with **verification** in it, which could let someone else claim your domain.

## 1. Load your records from the file

**At Cloudflare:**

1. Sign in at https://dash.cloudflare.com. If the domain isn't in your account:
   1. Click **Add a domain** and type your domain.
   2. Choose to enter records yourself, not to scan for them.
   3. Choose the **Free** plan.
2. Open the domain, then **DNS › Records**.
3. If records are already there and wrong, delete them first. If Cloudflare won't let you
   delete one, it's one Cloudflare made for itself: leave it.
4. Click **Import and Export**, choose your records file, and click **Import**. Leave the
   option to proxy imported records **off**: your file already says which ones to proxy.
5. Cloudflare says how many records it added. If it reports any it couldn't add, note them:
   you'll add those by hand in step 2.

**At GoDaddy:**

1. Sign in at https://dcc.godaddy.com/control/portfolio, click your domain, then **DNS**.
2. Open the **Actions** menu and choose **Import Zone File**. ("Zone file" is GoDaddy's name for
   a records file.)
3. Drag your records file into the window, or click **Browse files** and choose it.
4. Click **Apply Zone File**.

GoDaddy adds the records in the file to the ones already there. If any record in the file
clashes with one that's already there, GoDaddy refuses the whole file. If that happens, don't
delete things to make room: put the records back one at a time instead, as in step 3 of
[A record was changed or deleted](record-changed-or-deleted.md). It takes longer but always
works.

## 2. Compare the list with your file

Go down the records page and tick off each record against your file. GoDaddy shows 10 records
at a time: the page numbers are below the list. Look closely at the email
records: they matter most and are the easiest to get subtly wrong. Add anything missing by hand,
as in step 3 of [A record was changed or deleted](record-changed-or-deleted.md).

Records your DNS company makes for itself, such as the two of type **NS**, don't need to be in
your file. Leave them.

If your records went back into the same account they were in, skip to step 5.

## 3. Turn off the security lock (DNSSEC) if it's on

Your records file says whether DNSSEC is on, near the top. If it's **off**, skip this step.

DNSSEC is a lock with two halves. Your DNS company signs your records, and the company you
bought the domain from tells the internet how to recognize that signature. When your records go
somewhere new, the old signature stops matching and your domain stops working everywhere. So the
lock comes off first, in the right order. Follow the part for the DNS company your records file
names:

**Your records file says GoDaddy:** GoDaddy holds both halves, so one switch turns them both off.

1. At GoDaddy, open the domain, then **DNS › DNSSEC**.
2. Click **Turn Off DNSSEC**, then **Remove**.
3. Wait a day before step 4.

**Your records file says Cloudflare** (with the domain bought at GoDaddy):

1. At GoDaddy, open the domain, then **DNS › DS Records**, and delete each record listed there.
   They're what tell the internet how to recognize Cloudflare's signature.
2. Wait a day. Leave DNSSEC on at Cloudflare while you wait: turning it off there first makes
   your domain stop working until the day is up.
3. In the old Cloudflare account, open the domain, then **DNS › Settings**, and turn DNSSEC
   off. If you're locked out of that account, skip this: once the record at GoDaddy is gone,
   the old signature no longer matters.
4. Go on to step 4.

## 4. Point the domain at your DNS company

This tells the world which company holds your records. You change it where you bought the
domain. At GoDaddy:

1. Sign in at https://dcc.godaddy.com/control/portfolio, click your domain, then
   **DNS › Nameservers**, and click **Change Nameservers**.
2. In the box that opens, choose one:
   - **Records going to Cloudflare** (a different company, or a new Cloudflare account): choose
     **I'll use my own nameservers**. Type the two name servers Cloudflare shows on the domain's
     overview page, in the account your records are now in, into **Nameserver 1** and
     **Nameserver 2**. They look like `carlane.ns.cloudflare.com`.
   - **Records going back to GoDaddy:** choose **GoDaddy Nameservers (recommended)**.
3. Click **Save**. GoDaddy asks you to confirm: click **Continue**.
4. Records going to Cloudflare: wait until the domain shows **Active** in Cloudflare. It can take
   a few hours. To hurry it, click **Check nameservers now** on the domain's overview page in
   Cloudflare. Until it's Active, your email keeps working, but your website may not.
5. In your records file, update the **DNS company** line and the `nameservers:` line near the
   top. GoDaddy shows its name servers on the same **Nameservers** page.

## 5. Reconnect the website

Follow step 3 of [The website is down](website-is-down.md).

Then, if your records file says **Always Use HTTPS: on** near the top and your records are at
Cloudflare: open the domain in Cloudflare, then **SSL/TLS › Edge Certificates**, and turn on
**Always Use HTTPS**. It sends anyone who types `http://` on to the secure `https://` address.

## 6. Check email and the website

1. Follow steps 1 and 2 of [Email stopped working](email-stopped-working.md).
2. Open your website, with and without `www`, on your phone using mobile data.

If both work, you're done. Update the **Last checked** date at the top of your records file.
