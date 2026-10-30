# Your email addresses

Every email address your business uses for a job, rather than for one person, and where its
mail goes. If one stops working, [An email address stopped working](../guides/an-address-stopped-working.md) shows
how to put it back from this list.

<!-- FreeOT: the company that runs the business's email, and where its addresses are managed.
The text below is an example. -->
Your business email is run by **Google Workspace**. Its addresses are managed in the Google
Admin console, https://admin.google.com, signed in with your own business account.

<!-- FreeOT: the date this list was last compared with the email company's settings. -->
Last checked against Google Workspace: 12 Oct 2026.

## Addresses

<!-- FreeOT: one row per address. The row below is an example. -->
| Address | What it's for | Where its mail goes | Set up as |
| --- | --- | --- | --- |
| dmarc@freedomoftechnology.com | Email companies send their daily reports about the domain here (see [Report emails about your domain](../guides/dmarc-reports.md)). It's in the domain's `_dmarc` record, which anyone can look up, so expect some spam. | The owner's mailbox | An extra address (Google calls it an "alternate email") on the owner's account |

## Putting an address back

<!-- FreeOT: the steps for this business's email company. The steps below are for Google
Workspace. Where FreeOT puts addresses back for the business, replace them with a line saying to
contact FreeOT. -->
1. Go to the Google Admin console: https://admin.google.com. Sign in with your own business
   account.
2. On the left, click **Directory**, then **Users**.
3. Click the name of the person whose mailbox the address goes to ("Where its mail goes" in the
   table above).
4. Click **User information**. Under **Alternate email addresses (email alias)**, look for the
   address. If it's there, it's still set up: go back to the guide and test it.
5. If it's missing, click **ADD ALTERNATE EMAILS** in the list of actions on the left.
6. In the **Alternate email** box, type the part of the address before the `@`, for example
   `dmarc`. Leave the domain next to it as it is: your main domain.
7. Click **SAVE**.

Google says a new address can take a little while to start working.

<!-- FreeOT: keep this part only if the business has a second domain set up as another name for
the first. Otherwise delete it. -->
## Your second domain works for every address

Your second domain is set up in Google Workspace as another name for your main one (Google calls
it a "user alias domain"). Every address at your main domain also works at the second one, and
mail to either arrives in the same place. That's why an address only needs adding once.

## What's not in this list, on purpose

This list is kept in GitHub so it can be read and checked easily. So it holds only addresses
that are already public, or harmless if they become public. These are never written here:

- Admin accounts, and which accounts can change settings.
- Accounts that only software signs in to (service accounts), or any address used to sign in to
  something rather than to receive mail.
- Recovery email addresses and phone numbers.
- Passwords, codes or keys of any kind.

Those are kept in your business's Business Technology Account Map, a note in your password
manager, such as 1Password. Someone who can read them could use them to get into your accounts.

## When an address changes

Change this list the same day, the same way you'd change a records file
([Your records file](../guides/your-records-file.md), "To change it"). A list that doesn't match
what's set up can't be trusted when you need it.
