# The website is down

For when your website won't load, or shows an error instead of your page.

Time: about 10 minutes.

## 1. Make sure it's not just your computer

Open the website on your phone with Wi-Fi turned off, so it uses mobile data. Try both
addresses: with and without `www`.

- It loads on your phone: the website is fine. Your computer or office network remembers an
  old answer. Restart the computer, or wait an hour.
- It doesn't load anywhere: carry on.

## 2. Check the website records

In your [records file](your-records-file.md), the website records are under **Website**: one named `@` and one named
`www`. Check both with [How to check a record](how-to-check-a-record.md), choosing type **A**.

- **Numbers come back for both:** the records are there. Go to step 4.
- **Nothing comes back for one or both:** a website record is missing. Go to step 3.

## 3. Reconnect the website to the domain

The note above the website records in your file says where your website is kept. Some website
companies make the website records themselves, so put the records back through them rather
than by hand.

**Your website is on Cloudflare Pages:**

1. Sign in at https://dash.cloudflare.com
2. Go to **Workers & Pages** and open the website's project. Its name is in the note above the
   website records in your file.
3. Open **Custom domains**. Your domain and the `www` address should both be listed as
   **Active**.
4. If one is missing, click **Set up a custom domain**, type it in, and confirm. If one is
   listed but not Active, remove it and add it again.

**Your website is made with GoDaddy's website builder** (GoDaddy calls it Websites +
Marketing):

1. Sign in at https://account.godaddy.com/products and find **Websites + Marketing**. Click
   **Manage**, then **Edit Website**.
2. Open **Settings**, then click **Manage** next to your domain.
3. Choose **On a domain I already own**, pick your domain, and click **Save & Publish**.

**Anywhere else:** put the website records back by hand from your file, as in step 3 of
[A record was changed or deleted](record-changed-or-deleted.md).

Wait 5 minutes, then check again from step 1.

## 4. The records are fine but the site is still down

Then the problem is the website itself, not your DNS.

- **On Cloudflare Pages:** in **Workers & Pages**, open the project and look at
  **Deployments**. The most recent one should say **Success**. If it says Failed, or you can't
  tell, get help and say what the page shows.
- **Anywhere else:** contact the company that keeps your website, or get help.
