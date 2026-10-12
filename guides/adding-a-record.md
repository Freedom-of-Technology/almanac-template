# Adding a record

For when a company asks you to "add a DNS record" or "verify your domain": a new email tool, a
booking system, Google, a payment service.

Time: about 10 minutes.

The record goes in two places: your DNS company, and your records file. If it only goes into
the DNS company, it's lost the next time anything has to be put back.

## 1. Write it in your records file

1. Open your records file for changing: follow steps 1 to 3 of "To change it" in
   [Your records file](your-records-file.md).
2. Find the section the record belongs to (Email, Website, or Proof we own the domain). If none
   fits, add a new section at the bottom: a line starting with `; ----` and a name.
3. Add a note line starting with `;` saying who asked for it and why. For example:
   `; Calendly checks this to confirm the domain is ours (added 2026-11-04).`
4. Under it, add the record in the same layout as the lines around it: name, the same number
   as the lines around it, `IN`, type, value. Put TXT values in quote marks.
5. Save it: steps 4 and 5 of "To change it" in [Your records file](your-records-file.md).

If the company asked you to *change* a record rather than add one, edit its line instead, and
update the note.

## 2. Add it at your DNS company

Follow step 3 of [A record was changed or deleted](record-changed-or-deleted.md), using the
line you just wrote.

## 3. Check it

Wait 5 minutes, then look it up with [How to check a record](how-to-check-a-record.md). Then go
back to the company that asked and tell it to check (it's often a **Verify** button).

## Watch out for

- **"Connect automatically" buttons.** Some services offer to add records for you. That's
  fine, but they won't update your file. Afterwards, see what they added (step 2 of
  [A record was changed or deleted](record-changed-or-deleted.md)) and write it down.
  At GoDaddy these buttons sometimes split the record starting `v=spf1` into two, with a new one
  whose name ends in `._spfm`. That's normal: write both down exactly as GoDaddy shows them.
- **Keys and passwords.** If the company also gives you a key, password or code, it goes in your
  password manager, never in the records file. The record itself is fine to write down: anyone
  can look it up once it's live.
- **A second sender record.** Your domain can have only one TXT record starting with `v=spf1`.
  If an email service asks for a new one, it has to be merged into the existing one. Get help
  with this one.
