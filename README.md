# Your almanac

Templates and guides created and maintained by
[Freedom of Technology, LLC](https://freedomoftechnology.com) ·
[almanac template](https://github.com/Freedom-of-Technology/almanac-template) v1.0, 12 Oct 2026

This is your **almanac**: the written record of how your business's technology is set up. Like
the almanac people kept on the shelf, it's the book you reach for when something needs fixing.
If something breaks, or a company loses your settings, this is how to put things back the way
they were.

Right now it holds your **DNS records** and your **email addresses**. DNS is your domain's
address book: it tells the internet where your website is and where your email should go. Each
line in it is called a record. The email addresses are the ones your business uses for a job,
like info@ or billing@, and where each one's mail goes.

## Something's wrong. Which guide do I need?

| What's happening | Guide |
|---|---|
| Email isn't arriving, or what you send lands in spam | [Email stopped working](guides/email-stopped-working.md) |
| Mail to one address bounces or never arrives, but the rest of your email works | [An email address stopped working](guides/an-address-stopped-working.md) |
| You get daily emails titled "Report domain: …" with a `.zip` or `.gz` file attached | [Report emails about your domain](guides/dmarc-reports.md) |
| Your website won't load | [The website is down](guides/website-is-down.md) |
| Someone changed or deleted a record, or you're not sure | [A record was changed or deleted](guides/record-changed-or-deleted.md) |
| Your DNS company lost everything, or you're locked out, or you're switching companies | [Putting everything back](guides/putting-everything-back.md) |
| A company asks you to "add a DNS record" | [Adding a record](guides/adding-a-record.md) |

Most guides also use these two:

- [How to check a record](guides/how-to-check-a-record.md): see whether what the internet sees
  still matches your records file, for the whole file at once
  ([Almanac Check](https://freedomoftechnology.com/tools/domain-check/)) or one record at a time. It takes a minute and
  needs only a web browser.
- [Your records file](guides/your-records-file.md): open it, save a copy on your computer, or
  change it.

## Your records

Each domain has one records file. It's a plain text file listing every record, with a note on
each saying what it's for.

<!-- FreeOT: one row per domain, linking to its file in dns/. The row below is an example. -->
| Domain | Records file | DNS company | Where you bought the domain |
|---|---|---|---|
| freedomoftechnology.com | [Open it](dns/freedomoftechnology.com.zone) | Cloudflare | GoDaddy |

## Your email addresses

The addresses your business uses for a job, rather than for one person, are listed in
[Your email addresses](workspace/addresses.md), with what each one is for and where its mail
goes.

## Three habits that keep this useful

1. **The file comes first.** Whenever a record or an address changes, its file changes too, the same day.
   A file that doesn't match is a file you can't trust when you need it.
2. **Don't delete what you don't recognize.** Check the records file first. If it's not in the
   file and you don't know what it does, ask before removing it.
3. **Changes take a little while to show.** Most records update within 5 minutes. Some
   computers remember the old answer for up to an hour.

## Keeping it safe

Most of what's in your records file is public: anyone can look it up. But it also holds a few
things that aren't, and anyone who can change it could quietly change where your email goes the
next time it's used. So:

- **Keep it private.** It's set up so only you can see it, plus FreeOT while it works with you.
  Don't add anyone else unless you'd trust them with your email.
- **Turn on two-step sign-in for GitHub,** so a stolen password alone can't get in.
- **Never put a password, key or code in it.** Not in the file, not in a note. Passwords, the
  keys services give you, recovery codes and the code for moving your domain all belong in your
  password manager, such as 1Password. FreeOT set one up for you as part of setup, unless you
  chose not to have one.
- **Only list what's safe to be seen.** Admin accounts, accounts that only software signs in to,
  and recovery addresses and phone numbers would help someone trying to get in, so they're never
  written here. They go in your business's Business Technology Account Map, a note in your
  password manager.

## Getting help

If a guide doesn't fix it, or you'd rather not do it yourself, contact FreeOT at
almanac-check@freedomoftechnology.com. Say which guide you were on and what you saw.

## Who wrote this

The guides and the text of this page are by Freedom of Technology, LLC, shared under the
[Creative Commons Attribution 4.0](LICENSE) license: anyone may copy and change them, as long as
they credit Freedom of Technology, LLC. Your records files and your list of addresses are your
business's own.
