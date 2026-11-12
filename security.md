---
title: Security
---

# Security

Talteen is a Forge app. Atlassian supplies all of its compute and all of its
storage, and the app has no servers, no external services and no network egress
of its own. Everything the app captures stays inside your own Atlassian Cloud
environment, encrypted at rest by the platform. The app is verified eligible for
Atlassian's Runs on Atlassian programme.

## Reporting a vulnerability

Email **{{ site.security_email }}** with "security" in the subject line. Please include
what you found, how to reproduce it, and what an attacker could do with it.

Talteen is run by a single developer, so there is no 24/7 rota and no bug
bounty. Reports are acknowledged on Finnish business days, and you will get a
real answer rather than an auto-reply. Please give a reasonable window to fix
before publishing.

## What the app protects

- **Access control.** The Trash, restore, purge, audit log and Settings are
  limited to Jira site administrators, checked in the backend on every call and
  not only in the interface. Administrators may optionally extend view and
  restore to project administrators, for their own projects only; purge, the
  audit log and Settings stay site-administrator-only.
- **Audit trail.** Every restore and purge records the administrator who did it,
  what changed, and when.
- **Least privilege.** Four Jira permissions, each with a stated reason, and no
  access to passwords, tokens or shared secrets.
- **Deletion.** Captured data is deleted automatically on the retention schedule
  the administrator sets, immediately on manual purge, and entirely when the app
  is uninstalled.

## What the app does not do

- It does not send your data anywhere. There is no analytics, no telemetry and no
  remote backend.
- It does not log your content. Log lines carry issue identifiers and counts, never
  field contents or comment text.
- It does not hold attachment files after an administrator switches attachment capture
  off, or for a project on the capture exclusion list. Capture is on when the app is
  installed, so a fresh install does hold them, bounded by a per-file size cap and a
  monthly write allowance.

## Related

- [Privacy policy](privacy)
- [Known limitations](limitations)
- [Documentation](docs)
