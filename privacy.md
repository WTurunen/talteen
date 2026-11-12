---
title: Privacy policy
---

# Privacy Policy — Talteen

**Effective date:** {{ site.effective_date }} &middot; **Last updated:** {{ site.privacy_updated }}

{{ site.legal_name }} (business ID {{ site.business_id }}, {{ site.business_address }},
Finland) — "we", "us" — publishes the Atlassian Marketplace app **Talteen - Restore
Deleted Issues & Attachments for Jira** ("the app").

This policy explains what the app does with data, and what we do with a support request
you send us (section 12). It does not
cover Atlassian's own handling of your Jira site, which is governed by the
[Atlassian Privacy Policy](https://www.atlassian.com/legal/privacy-policy).

---

## 1. Our role

The app is installed by a Jira site administrator onto that organisation's own Jira
site. The organisation is the **data controller** for the Jira content the app handles.
We act as a **data processor** on the organisation's behalf, and only to provide the
app's function: keeping restorable copies of deleted Jira issues.

That processing is governed by our **[Data Processing Addendum](dpa)**, which is the
contract required by Article 28 GDPR. It sets out what we process, the technical and
organisational measures, our sub-processors, and how long the data is kept.

## 2. Where your data lives

**The app has no server.** It runs entirely on Atlassian's Forge platform, using
Forge-hosted compute and storage inside your own Atlassian environment.

- No external egress. The app declares no remote backends and no external domains.
- No third-party analytics.
- No copy of your data on infrastructure we own or control — we own none.

The app meets the technical eligibility criteria for Atlassian's **Runs on Atlassian**
programme. Data is encrypted at rest by the Atlassian platform.

**We cannot read your data.** We have no access path to a customer's Forge storage.

## 3. What the app stores

All of the following is stored per-installation in Forge storage:

| Data | When | Contents |
|---|---|---|
| Issue snapshots | On issue create/update (debounced) | Restore-relevant fields only: summary, description, project/type/status ids, priority, labels, assignee and reporter account ids, parent, due date, created date, non-empty custom fields. Compressed. |
| Comment mirror | On comment create/edit | Comment id, author account id and display name, created timestamp, body. Compressed. |
| Trash records | On issue deletion | The snapshot, plus deleted-by account id and deleted-at timestamp. |
| Attachment mirrors | On upload, while attachment capture is enabled. **Capture is ON from installation.** | Filename, size, uploader account id, created date, media id, and the file bytes in chunks. Files over the per-file cap or past the monthly budget: metadata only, no bytes. |
| Attachment usage counter | As files are mirrored | Per-month aggregate only: bytes stored, files mirrored, files skipped. No file content. |
| Audit log | On restore/purge | Timestamp, acting administrator's account id, action, old and new issue keys. |
| Settings | On save | Retention days, restorer role, excluded projects, notification toggle, attachment capture settings. |
| Feedback bookkeeping | On first app open | A random install ID generated locally, when the app was first opened, and whether the feedback card was dismissed. No account ids, no issue data. |

**Attachment capture is on from the moment you install the app.** The app copies each
attachment as a user uploads it, so that a file deleted later can be put back. The volume
is bounded by a per-file size cap (default 10 MB) and by a monthly write budget (default
250 MB). A site administrator can switch capture off in Settings, or exclude individual
projects from it.

## 4. What the app does not store

- Attachment binaries while an administrator has switched attachment capture off.
  Capture is on by default, so this is a choice the administrator makes.
- Worklogs, issue history, watchers, votes.
- Anything from projects on the Settings exclusion list. Capture is skipped entirely
  for those projects.
- Issue content in logs. Log lines carry issue ids and counts, never field content or
  comment bodies.

## 5. Personal data

The app stores Atlassian **account ids** — the platform's pseudonymous identifier — for
the user who deleted an issue, for comment authors, and for administrators who restore
or purge. It also stores comment-author **display names** as they appeared at capture
time.

Personal data inside captured issue content (descriptions, comments, attachments) is
retained only for the retention window, and only so the issue can be restored.

**Legal basis:** we process this as a processor on the controller's documented
instructions, which are given by the administrator's act of installing and configuring
the app.

## 6. The optional feedback form

The app shows two links to a feedback form — one in Settings, one on a dismissible card
in the Trash view. Both are optional.

**The app never transmits anything.** It builds a link and hands it to your browser.
Your browser prompts you before opening it. If you do not click, nothing leaves.

If you do click, the link carries up to four values, all visible to you on the form:

| Value | What it is |
|---|---|
| Install ID | A random identifier generated by this installation. Not derived from your site name, cloud ID, or any account. Carries no site-identifying information on its own. |
| Days since first opened | How long ago the app was first opened here. |
| Attachment capture on | Whether attachment capture is enabled — `1` or `0`. |
| Which link | Whether you clicked from Settings or from the card. |

If the app cannot read its own local storage when you click, the install ID and the
days-since-first-opened are omitted rather than guessed at.

**Nothing else travels.** No site name or URL, no account ids, no display names, no
project or issue keys, no issue content, no file names.

The form is hosted by **Tally BV** (Sint-Pietersnieuwstraat 11, 9000 Gent, Belgium),
which stores form data on servers within the European Union. Tally's own handling is
governed by the [Tally privacy notice](https://tally.so/help/privacy-policy).

Treat the form as you would any external form: **do not paste customer data into it.**
Anything you type there is your own choice, and we use it only to act on your feedback.

## 7. Sub-processors

| Party | Purpose | Location |
|---|---|---|
| Atlassian | Hosts all app compute and storage (Forge) | Per your Atlassian site's data residency |
| Tally BV | Hosts the optional feedback form only — reached only if you click the link | Belgium; data stored within the EU |

No other party receives data from the app. Support requests are covered separately in
section 12.

Neither is a sub-processor for the app's core function. Atlassian hosts the app inside
your own Atlassian environment. Tally receives nothing unless a person at your
organisation chooses to open and submit the feedback form. Both are listed for
completeness.

## 8. Retention and deletion

- **Trashed issues** are purged automatically after the configured retention period
  (default 60 days, maximum 365). Administrators can purge any item immediately.
- **Snapshots of live issues** are kept while the issue exists — they are the safety
  net. On deletion they are promoted to trash and then follow retention.
- **Superseded comment mirror data** is evicted by the daily maintenance job.
- **Attachment files follow their issue.** Purging a trash record, manually or by
  retention expiry, deletes every mirrored attachment file for that issue.
- **A file deleted from an issue that still exists** is kept for a configurable window
  (default 14 days, adjustable 1–90) and is restorable from the Deleted files tab for
  that window. After it, the nightly job removes the copy permanently.
- **A restored file's copy outlives the restore by up to the grace window.** Restoring
  puts the file back immediately, but the app's now-redundant copy is deleted only by
  the next nightly sweep past a full grace window measured **from the restore**. The
  stored copy can therefore persist for close to twice the configured window after the
  file was first deleted.
- **On uninstall**, all Forge storage for the installation is deleted by the Atlassian
  platform under Forge data lifecycle policy. Nothing survives on our side, because
  there is no our side.

  Note the flip side: **uninstalling destroys the safety net and everything in the
  trash.**

## 9. Access control

- Trash contents, restore, purge, the audit log and settings are limited to **Jira site
  administrators** (`ADMINISTER`), verified server-side on every call.
- Optionally, and off by default, site administrators can allow **project
  administrators** to view and restore trash for projects they administer. Purge, audit
  log and settings stay site-administrator-only.
- Regular, guest and anonymous users can never reach trash data. The check runs in the
  backend resolver, not only in the interface.
- **One exception, which grants no access to data:** dismissing the feedback card. While
  project-administrator access is switched on, any licensed user can dismiss it. The card
  is a single site-wide notice with a single dismissal, so dismissing it hides it for
  everyone. It reads nothing and reveals nothing about trash, settings or issues.

## 10. Your rights

For data the app holds in your Jira site, data subject requests should go to the
**controller** — the organisation whose Jira site holds the data — not to us. For a
support request you sent us, we are the controller; see section 12. Their administrator can satisfy a right-to-erasure request by
purging the relevant trash items in the app, by shortening retention, or by uninstalling.

If you are a customer administrator and need our help with a request, contact us at the
address in section 13. Where we act as processor we will assist the controller as
required by Article 28 GDPR.

## 11. Changes

We will update this page if the app's data handling changes, and change the "last
updated" date. Material changes will be notified to customer administrators and to
Atlassian, as required by the Atlassian Marketplace Partner Agreement.

## 12. Support requests

This section covers a support request you send us. It does not concern data the app
holds in your Jira site.

**What we receive:** your email address and the headers your email carries, your name
if you give it, and what you write or attach — typically your Jira site URL, an issue
key, a description of the problem and a screenshot of an error. For this data we are the
**data controller**.

**Why:** to answer your request and fix the problem. The legal basis is our
legitimate interest in supporting the users of the app (GDPR Article 6(1)(f)).

**Where it is kept:** support email arrives in an inbox hosted by **Proton AG**
(Geneva, Switzerland). Switzerland has an adequacy decision from the European
Commission.

**How long:** while the request is open, and afterwards for as long as we need it to
handle follow-up questions about the same problem. Then we delete it.

**Your rights:** you can ask us for a copy of this data, to correct it or to delete it,
and you can object to its use, by writing to the address in section 13. You can also
complain to the Finnish Data Protection Ombudsman (tietosuoja.fi).

**Do not send customer data.** Issue keys and error messages are enough to start.

## 13. Contact

Email **[{{ site.privacy_email }}](mailto:{{ site.privacy_email }})** for any question
about this policy or about data the app holds.

{{ site.legal_name }}
{{ site.business_address }}, Finland
Business ID {{ site.business_id }}
