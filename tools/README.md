# Tools (for FreeOT)

Business owners don't need anything in this folder. The guides check records with Almanac Check
(https://freedomoftechnology.com/tools/domain-check/), which runs in the browser, and with Google's free lookup page for
single records.

The same check runs from the command line, for FreeOT and for GitHub. It lives with the page, in
`Freedom-of-Technology/tools` (public), as `cli/check.mjs`, and runs the page's own checking code.
It needs Node 22 or later and nothing else. With the tools repo cloned beside this one:

    node ../tools/cli/check.mjs dns --secrets .
    node ../tools/cli/check.mjs dns/freedomoftechnology.com.zone --ns carlane.ns.cloudflare.com

It compares every records file in `dns/` with what's live: records from Google Public DNS, and name
servers and DNSSEC from the domain's registry. It exits with 1 if anything needs a look.

Before anything else, it refuses a records file that looks like it holds a secret (a private
key, a known token format, or a password or key written out after its name). `--secrets .`
looks the same way through every other file in this repo, such as the guides and
`workspace/addresses.md`. Secrets go in the password manager. If one was committed,
removing it from the file isn't enough: it has to come out of the history too, and the secret
itself has to be replaced with a new one.

The `--ns` form asks a named server instead, for checking a new DNS company's copy before the
domain is pointed at it.

It can't see names that are live but missing from the files, or where a proxied record really
points. An export from the DNS company covers both (Cloudflare: DNS › Records › Import and
Export › Export; GoDaddy: the domain's DNS page › Actions › Export Zone File). GoDaddy's export
is for comparing only: it writes its website records as `A WebsiteBuilder Site` rather than
addresses, so no DNS company can import it as is.

GitHub runs it on every change and every Monday morning (`.github/workflows/check.yml`), and
emails a failed run. The workflow checks out the tools repo's `main` each time, so a fix there
reaches this check without a change here. Secret blocking before a change is saved needs a paid
GitHub plan, so on the free plan this is the guard: it catches a secret right after the change,
not before.

## The template this almanac comes from

Every almanac starts as a copy of `Freedom-of-Technology/almanac-template` (public), made with
GitHub's **Use this template** button into the business's own GitHub account, as a private repo.
The front page names the template version it was copied from.

- **What's the same everywhere:** the `guides/` folder, word for word. Each guide reads correctly
  for any business and any setting; anything that differs between businesses lives in their own
  files: the records files in `dns/`, `workspace/addresses.md`, and the front page's tables.
- **What FreeOT fills in for each business:** the rows and dates marked with a `FreeOT:` note
  (notes in `<!-- -->` don't show on GitHub's page), and the records files.
- **Keeping a copy current:** when the template has a newer version, FreeOT copies the changed
  guides into the business's almanac by pull request and updates the version on its front page.
  That's part of looking after the business. A business that stops working with FreeOT keeps the
  version it has; it still works.
- **Changing the template:** a guide changes in the template first, never only in one almanac.
  Each release gets a version number and date on the template's front page and a matching git tag
  (`v1.0`, `v1.1`, ...).
