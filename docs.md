---
title: Documentation
---

# Talteen — documentation

## 1. How to restore an issue

1. Open Talteen from the Apps menu in Jira.
2. Find the issue on the Trash page. To make the list shorter, filter it by project, by
   date, or by user.
3. Click Restore.
4. To restore more than one issue, select the issues, then click Restore. The app
   restores a maximum of 25 issues in one operation. The app divides a larger set
   automatically.
5. Read the report. The report gives the result for each issue.

The audit log records each restore. The audit log also records each deletion of a copy
that an administrator starts with the Purge button. Each record gives the user and the
time.

## 2. What the app restores

- the summary and the description, with the format
- the issue type and the priority
- the labels and the due date
- the custom fields that have a value
- the comments
- the issue links

If the Jira permissions permit it, the app also restores the reporter and the assignee.
If you set Attachment capture to on, the app also restores the attachment files.

## 3. What changes when the app restores an issue

**Caution: A restored issue is a new issue. It is not the initial issue.**

- **The issue key changes.** When Jira deletes an issue, Jira Cloud cannot use that key
  again. The app puts
  the label `restored-from-trash` on each restored issue, and it records the initial key
  with the new key. The app also adds a comment that gives the initial key.
- **The status changes.** Jira does not permit an app to set the status when it makes an
  issue. The restored issue gets the first status of its workflow. An issue with the
  status "Done" comes back with the status "To Do".
- **The dates change.** Jira does not permit an app to set the initial dates. The app
  records these data in the audit comment: the date of creation, the date of the
  deletion, and the user who deleted the issue.
- **The author of a comment changes.** Jira does not permit an app to write a comment as
  a different user. Each restored comment starts with the name of its initial author and
  the initial date.
- **The change history does not come back.** The restored issue has a copy of the
  content of the initial issue. It does not have the change history.

## 4. The report gives the data that did not come back

The app removes no data without a record.

- If the target screen rejects a field, the report gives the name of that field.
- If a link points to an issue that is no longer there, the report gives that link as
  lost.
- If the app cannot restore a file, the report gives the name of the file and the cause.

The report is the same on each restore path. You can also download the part of the report
about the files as a CSV file. The dropped fields and the lost links are on the screen
only.

## 5. Deleted files

Jira Cloud has no recovery for a file that a user deletes from an issue that stays.
Atlassian has a public request for this, with the number JRACLOUD-81027.

Attachment capture is on after you install the app. The app keeps a copy of each file
that a user deletes. If you set Attachment capture to off, the app keeps no copy of a
file that a user deletes from an issue that stays. The Deleted files page does not show
that file.

Attachment capture has two limits:

- The maximum size of one file is 10 MB. You can set a value from 1 MB to 50 MB.
- The maximum quantity of data for one month is 250 MB. You can change this value in the
  Settings page. The Settings page gives the maximum value that you can set.

If a file is above one of these two limits, the app keeps only the data about that file.
The report gives the cause for each such file.

The app keeps a copy of a deleted file for 14 days. You can set a value from 1 day to 90
days.

**Caution: When you restore a file, the size of that file counts against the limit for
the month a second time.** The app has no procedure to give those megabytes back. The
dialog gives the size and this cost before you click.

**Caution: The app does not correct the link to a file in a comment.** The app corrects
the link in the description of the issue only. The app does not change the text that a
user wrote.

To restore a file, open the Deleted files page and click Restore. The app puts the file
on the same issue again, and it corrects the link to that file in the description of the
issue.

## 6. Where your data stays

Talteen is a Forge app. Atlassian supplies all the compute and all the storage. The app
keeps each copy in the storage of your own Jira site. The app has no server of its own,
and it sends no data to an external service.

The app needs four permissions:

| Permission | Why the app needs it |
|---|---|
| `read:jira-work` | To read the data of an issue at the moment a user deletes it |
| `write:jira-work` | To make the issue, its comments and its links again |
| `read:jira-user` | To give the name of a user, and not only an identifier |
| `storage:app` | To keep the copies in the storage of Atlassian |

## 7. Who can do what

Only a Jira site administrator can open the Trash page, restore an issue, delete a copy,
read the audit log, or change the settings. The app makes this check on the server for
each request, and not only in the interface.

You can also permit project administrators to open and restore the trash of the projects
that they administer. This setting is off after you install the app. The Purge button,
the audit log and the settings stay for site administrators only.

## 8. How long the app keeps the data

The app keeps a deleted issue for 60 days. You can set a value from 1 day to 365 days.
After that time, the app deletes the copy automatically. An administrator can also delete
a copy immediately with the Purge button.

**Caution: If you uninstall the app, Atlassian deletes all the data of the app.** After
that, you cannot restore the issues that were on the Trash page.

## 9. The limits

- The app restores only the issues that users delete after you install it.
- A restored issue has a new key, the first status of its workflow, and no change
  history.
- The app cannot write the initial author on a comment. Each restored comment starts with
  the name of that author.
- If that user is not active, or if the Modify Reporter permission is not there, the app
  cannot set the reporter. The report gives the reporter field as dropped. The report
  does not give the name of the initial reporter.
- If the app reaches the monthly limit for attachment data, the app keeps no more files
  until the next month.
- **Keep the browser page open during a restore that contains files.** The files go to
  Jira from your browser. If you close the page, the new issue stays in Jira, but without
  its description, its comments and its links. To complete the operation, click Restore
  on the same item again, then click Resume.
- The audit log records the restores, and the deletions that an administrator starts. It
  does not record the automatic deletion at the end of the retention time.
- If two administrators click Restore on the same file at the same moment, the app can
  put two copies of that file on the issue. Delete the copy that you do not need.
- The Deleted files page gives the project and the issue of the moment of the deletion.
  If a user moved that issue to a different project, the page gives the initial project.
  The app always makes the permission check against the project of the issue now.
- The meter for the month is exact in normal operation. If the storage gives an error,
  the meter is approximate.
