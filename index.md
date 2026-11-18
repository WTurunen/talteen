---
title: Talteen
---

# Talteen - Restore Deleted Issues & Attachments for Jira

Jira Cloud has no recycle bin. When a user deletes an issue, Jira deletes that issue
permanently, and no support request can bring it back.

**Talteen** keeps a copy of each issue on your own Jira site. When a user deletes an
issue, the app moves that copy to the Trash page, where a site administrator can restore
it with its fields, its labels, its comments, its links and its files.

Your data stays inside Atlassian. The app has no server of its own and sends nothing to
an external service.

> **Install the app before a user deletes data.** The app can restore an issue only if
> someone created or changed it after you installed the app. A new comment alone is not
> enough. The app can restore a file only if someone added it after you installed the
> app. No app can recover data that Jira deleted before you installed it.

## Pages

- **[Documentation](docs)** — how to restore an issue, what the app restores, settings,
  attachment capture, and the audit log.
- **[Known limitations](limitations)** — what the app cannot do.
- **[Privacy policy](privacy)** — what the app stores, where it lives, how long it is
  kept, and who can reach it.
- **[Security](security)** — how the app is built, how to report a vulnerability, and
  what it deliberately does not do.
- **[Data Processing Addendum](dpa)** — the GDPR Article 28 contract for the personal
  data the app processes on your behalf.

## Support

Email <a href="mailto:{{ site.support_email }}">{{ site.support_email }}</a>. Support is
offered on a commercially reasonable basis during Finnish business days. Hours and what
to include in a request are on the [support page](support).

## Get the app

Available on the [Atlassian Marketplace](https://marketplace.atlassian.com/).
