# Report emails about your domain (DMARC reports)

For when you get emails with a subject like `Report domain: freedomoftechnology.com Submitter:
google.com`, with a `.zip` or `.gz` file attached, and wonder what they are.

Time: a minute to check one is real. About 10 minutes to read one.

## What they are

Big email companies such as Google, Microsoft and Yahoo send these once a day, to the address
in your `_dmarc` record (in your [records file](your-records-file.md), under **Email**). That's
`dmarc@` at your domain, an address kept just for these reports, which arrives in your own
mailbox ([Your email addresses](../workspace/addresses.md)). Each one is a tally for the day
before: "we received this many emails claiming to be from your domain, from these servers, and
this is how many proved they really were from you."

They hold the addresses of the servers that sent the emails and the counts. They never hold
anyone's emails, names or subject lines.

You get one from each company that received email from your domain that day, so a quiet day
brings none and a busy one can bring several.

Your `_dmarc` record also tells email companies what to do with email that fails the checks. To
see which setting yours has, look for `p=` in the `_dmarc` line of your records file:

| Setting | What happens to email that fails the checks |
|---|---|
| `p=none` | It's delivered anyway. The record only asks for these reports. Every domain starts here while FreeOT checks what sends email as you. |
| `p=quarantine` | It goes to the spam folder. Some domains wait here for a few weeks on the way to `p=reject`. |
| `p=reject` | It's refused, so it never arrives. Every domain ends here. |

Your real email passes the checks, so it isn't affected by any of them.

## 1. Make sure it's a real report

Fake "report" emails are a known trick for getting people to open a harmful file. A real one:

- **Comes from the email company's own address.** Google's is
  `noreply-dmarc-support@google.com`, and Microsoft's is `dmarcreport@microsoft.com`. Other
  companies use their own name after the `@`.
- **Has one attachment, ending in `.zip`, `.gz` or `.xml`.** Never anything else.
- **Asks nothing of you.** No links to click, nothing to sign in to, no payment.

If any of these is off, delete it without opening the attachment.

## 2. Decide whether to read it

Most of the time you don't need to. If email is working for you and the people you write to,
it's fine to leave these unread.

Read one when:

- Email you send has started bouncing back or landing in spam.
- You've just started using a new service that sends email as you, such as a newsletter,
  invoicing or booking tool, and want to see it's set up right. Set it up with FreeOT before its
  first email goes out: until its records are added, its email fails the checks, and it goes to
  spam or is refused, depending on your setting.
- FreeOT asks you to.

Tired of them in your inbox? See [Filing them out of the way](#filing-them-out-of-the-way)
below.

## 3. Read it in your browser

dmarcian, a company that sells email-checking services, has a free page that turns a report
into a summary you can read. It needs no account and takes the attachment as it comes. Your file
is sent to dmarcian to be read, and dmarcian keeps the summary at its own web address until you
delete it (step 9). That's all right: a report holds only server addresses and counts.

1. In the report email, save the attachment to your computer. Don't unzip it.
2. Open https://us.dmarcian.com/xml-to-human-converter/
3. Drag the file onto the box that says **Drag and drop files or browse**, or click **browse**
   and choose it.
4. The file appears below, under **Accepted files**. Click the blue **Upload file** button on its
   line.
5. Wait a few seconds for a green tick and **Valid XML** on that line.
6. Click the small page button under **View Report**. The summary opens in a new tab, headed
   **Domain Report for:** and your domain.
7. Look at **Sources**. A round chart splits the day's emails into three groups:

   | Group | What it means |
   |---|---|
   | **DMARC Capable** | Servers set up to send as you, such as Google sending your everyday email. |
   | **Forwarders** | Your emails that someone forwarded, or that a mailing list sent on. |
   | **Threat/Unknown** | Servers that aren't set up to send as you. |

8. For more detail, scroll down to **Identified Sources** and click each group's tab. Each line
   is one sender, with how many emails it sent (**Volume**). Under **DMARC Capable**, the column
   that matters is **DMARC Compliance Rate**: the share of emails that proved they were really
   from you. A green tick and **100%** is what you want.
9. When you're done, go back to the top of the summary. Click the trash can button next to
   **Uploaded to your account via Web Interface**, then **Delete Report**. It can take a moment
   to go.

## 4. What the results mean

**It's fine when:**

- **Everything under DMARC Capable is at 100%.** Your real email is proving it's from you.
- **There's something under Threat/Unknown.** That's usually someone faking your domain as the
  sender, most often for spam. It's common, it isn't caused by anything you did, and showing it
  to you is what these reports are for.
- **There are a few Forwarders.** Forwarded email often can't pass every check, and that's
  expected.

**Get help when:**

- **Something under DMARC Capable is below 100%.** If it's Google, your signature or your "who
  may send as you" record has probably stopped working: start with
  [Email stopped working](email-stopped-working.md).
- **A service you really use shows up under Threat/Unknown.** Its emails, such as your
  newsletter, invoices or booking confirmations, may be landing in spam or being refused. Its
  records need adding.
- **Threat/Unknown is suddenly many times bigger than usual.** Someone is sending a lot of email
  in your name. If your setting is `p=none`, that email is still reaching people.
- **The reports stop for more than two weeks,** while you're still sending email. Your `_dmarc`
  record may have been changed or deleted. Check it with
  [How to check a record](how-to-check-a-record.md).

When you ask, forward the report email itself to FreeOT and say what looked wrong.

## Filing them out of the way

If you use Gmail, a filter can move these reports into a folder of their own so they skip your
inbox. Gmail calls a filter's folder a **label**.

1. Open Gmail. In the search box at the top, click the **Show search options** button at its
   right end. It looks like three sliders.
2. In **Subject**, type `Report domain`
3. Click **Create filter**.
4. Tick **Skip the Inbox (Archive it)** and **Apply the label**. Choose **New label...**, name it
   `DMARC reports`, and click **Create**.
5. Tick **Also apply filter to matching conversations** to file the ones you already have.
6. Click **Create filter**.

They'll appear under **DMARC reports** in Gmail's left-hand menu. To undo it, open Gmail's
settings (the gear at the top right), then **See all settings › Filters and Blocked
Addresses**, and delete the filter.

A fake report with the same subject would be filed there too, so step 1 still applies to any you
open.
