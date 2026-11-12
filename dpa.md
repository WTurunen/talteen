---
title: Data Processing Addendum
---

# Data Processing Addendum — Talteen

**Version 1.0** &middot; **Effective date:** {{ site.dpa_effective_date }} &middot; **Last updated:** {{ site.dpa_updated }}

{{ site.legal_name }} (business ID {{ site.business_id }}, {{ site.business_address }},
Finland) — "Provider" — publishes the Atlassian Marketplace app **Talteen - Restore
Deleted Issues & Attachments for Jira** ("the App").

This Addendum forms part of the agreement between Provider and Customer for Customer's
use of the App. It governs Provider's processing of personal data on Customer's behalf
and is required by Article 28(3) of Regulation (EU) 2016/679 ("GDPR"). Terms defined in
the GDPR have the same meaning here.

Contact for all data protection matters:
**[{{ site.privacy_email }}](mailto:{{ site.privacy_email }})**

---

## 1. Roles

**1.1** Customer is the controller of the personal data contained in its Jira instance.
Provider is a processor of that personal data, and processes it only on Customer's
documented instructions.

**1.2** Customer's instructions are: this Addendum, the agreement it forms part of, and
the configuration Customer's administrators choose in the App's Settings. Installing and
configuring the App is an instruction to process as described in Annex I.

**1.3** Provider is not a controller of End-User Data. Provider is a separate and
independent controller of the information a person chooses to submit through the App's
optional feedback form. That form is an external link that a person clicks; the App
transmits nothing to it. It is outside the scope of this Addendum and is described in the
[Privacy Policy](privacy).

**1.4** If Provider considers an instruction to infringe the GDPR, Provider will inform
Customer without undue delay.

## 2. Scope and duration

**2.1** The subject matter, duration, nature and purpose of the processing, the types of
personal data and the categories of data subjects are set out in Annex I.

**2.2** This Addendum applies for as long as the App is installed in Customer's Atlassian
environment.

## 3. Confidentiality

Provider will keep End-User Data confidential. Provider is a sole proprietorship with no
employees. If that changes, Provider will ensure that any person authorised to process
End-User Data is bound by an appropriate obligation of confidentiality.

## 4. Security

**4.1** Provider implements the technical and organisational measures set out in Annex
II, having regard to Article 32 of the GDPR.

**4.2** Customer acknowledges that the principal security measure is architectural: the
App stores all End-User Data inside Customer's own Atlassian Cloud environment on the
Atlassian Forge platform. Provider operates no servers, has no remote backend, performs
no network egress, and has no technical means of reading End-User Data.

## 5. Sub-processors

**5.1** Customer gives Provider general authorisation to engage the sub-processors listed
in Annex III. Annex III currently lists one entity: Atlassian, as the operator of the
platform on which the App runs and on which Customer's own Atlassian products already run
under Customer's separate agreement with Atlassian.

**5.2** Provider will inform Customer of any intended addition or replacement of a
sub-processor by updating Annex III on this page at least 30 days before the change takes
effect. Customer may object on reasonable data protection grounds, in which case the
parties will discuss in good faith; if no resolution is reached, Customer may terminate
and uninstall the App.

**5.3** Provider remains liable to Customer for a sub-processor's performance of its data
protection obligations.

## 6. International transfers

Provider carries out no transfer of End-User Data. End-User Data remains in Customer's
own Atlassian environment, in the data residency location Customer holds with Atlassian.
Any transfer arising from Atlassian's operation of that environment is governed by
Customer's own agreement with Atlassian and not by this Addendum.

## 7. Assistance to Customer

**7.1 Data subject rights.** The App gives Customer's administrators direct access to
everything the App holds, and the ability to delete any of it immediately. Customer can
therefore satisfy requests for access, rectification, erasure and restriction without
Provider's involvement. Provider will assist with any request Customer cannot satisfy
through the App, taking into account the nature of the processing.

**7.2** Provider will assist Customer with data protection impact assessments and with
prior consultation under Articles 35 and 36, taking into account the information
available to Provider.

**7.3** If Provider receives a request from a data subject relating to End-User Data,
Provider will not respond to it other than to direct the data subject to Customer, and
will inform Customer without undue delay.

## 8. Personal data breach

**8.1** Provider will notify Customer without undue delay after becoming aware of a
personal data breach affecting End-User Data, and will provide the information Customer
needs for its own notification obligations.

**8.2** Customer acknowledges that Provider has no access to Customer's Atlassian
environment and therefore no means of detecting an incident inside it. Detection and
notification for that environment are governed by Customer's agreement with Atlassian.
Provider's obligation under 8.1 relates to a breach of which Provider actually becomes
aware, including one arising from a defect in the App.

## 9. Deletion and return

**9.1** The App deletes End-User Data on the schedule Customer's administrator
configures, and immediately when an administrator purges an item.

**9.2** On uninstallation of the App, the Atlassian platform deletes all data the App
holds for that installation, in line with Atlassian's Forge data lifecycle policies.
Provider retains no copy, because Provider holds no copy at any time.

**9.3** Customer acknowledges that uninstalling the App therefore also destroys
everything the App was holding for recovery.

## 10. Audit

**10.1** Provider will make available to Customer the information necessary to
demonstrate compliance with Article 28, including the App's published
[privacy](privacy), [security](security) and [documentation](docs) pages, and will
respond to reasonable written questions.

**10.2** Provider is a sole proprietorship and does not host on-site audits. An audit
under Article 28(3)(h) will be conducted by written information request. Provider does
not control the platform on which the App runs and cannot grant audit rights over it;
Atlassian's certifications and reports are available to Customer from Atlassian.

## 11. Data protection officer

Provider has not appointed a data protection officer. Provider's processing does not meet
the conditions in Article 37(1): Provider is not a public authority, does not carry out
regular and systematic monitoring of data subjects on a large scale, and does not process
special categories of data on a large scale. All data protection matters go to
[{{ site.privacy_email }}](mailto:{{ site.privacy_email }}).

## 12. General

**12.1** This Addendum is governed by the laws of Finland, with venue as set out in
Provider's Provider-Specific Terms.

**12.2** If any provision of this Addendum conflicts with the agreement it forms part of,
this Addendum prevails as to the processing of personal data.

---

## Annex I — Description of the processing

**Subject matter.** Retention of copies of Jira issue and attachment data so that
Customer's administrators can restore items deleted from Customer's Jira site.

**Nature and purpose.** Capture, storage, retrieval, restoration and deletion of Jira
content within Customer's own Atlassian environment, for the purpose of recovering
content deleted in error.

**Duration.** For as long as the App is installed, and within that, for the retention
period Customer's administrator configures for each type of item.

**Categories of data subjects.**

- Customer's Jira users, including anyone who creates, edits, comments on, is assigned,
  uploads a file to, or deletes an issue.
- Any person whose personal data Customer's users place in issue content, comment
  content, or an attached file.

**Types of personal data.**

- Atlassian account identifiers of assignees, reporters, comment authors, file uploaders,
  deleting users and acting administrators.
- Display names of comment authors.
- Free-text content: issue summary, description, labels, custom field values and comment
  bodies. Customer determines what personal data this contains.
- Attachment file names and, where attachment capture is enabled, the file contents.
  Customer determines what personal data these contain.
- Timestamps of the above actions.

**Special categories of personal data.** Provider does not request or require any.
Whether any is present is determined solely by what Customer's users put into Jira
issues, comments and attached files.

**Processing operations the App does not perform.** It does not store worklogs, issue
history, watchers or votes; it does not write issue or comment content to logs; it skips
capture entirely for projects Customer excludes; and it stores no attachment file
contents while Customer has attachment capture switched off.

## Annex II — Technical and organisational measures

**Architectural.**

- All End-User Data is stored in Customer's own Atlassian Cloud environment using
  Atlassian Forge storage. Provider operates no servers and holds no copy.
- The App declares no external domains and performs no network egress. Provider has no
  technical path to read End-User Data.
- The App uses no third-party analytics and no remote backend.

**Encryption.** At rest and in transit, provided by the Atlassian Forge platform.

**Access control.**

- Trash contents, restore, purge, the audit log and Settings are restricted to Jira site
  administrators, verified on the server on every call.
- Customer may optionally extend view and restore rights to project administrators for
  the projects they administer. Purge, audit log and Settings remain restricted to site
  administrators.

**Accountability.** The App writes an audit entry for each restore and each purge,
recording the acting administrator's account identifier, the action and the timestamp.

**Data minimisation.**

- Only restore-relevant fields are captured.
- Log output is filtered so that issue and comment content cannot reach platform logs.
- Customer sets a monthly storage budget, a per-file size cap and a retention period, and
  can exclude projects from capture entirely.

**Resilience and availability.** Provided by the Atlassian Forge platform. Provider does
not control it and commits to no availability target.

## Annex III — Sub-processors

| Sub-processor | Role | Processing location |
|---|---|---|
| Atlassian Pty Ltd and its affiliates | Operator of the Atlassian Cloud and Forge platform on which the App runs and on which the data remains | The Atlassian data residency location Customer holds with Atlassian |

Atlassian is listed for completeness. It is the provider of Customer's own Atlassian
products, engaged by Customer under Customer's own agreement with Atlassian, and
Customer's data does not leave that environment by reason of the App.

**There are no other sub-processors.**
