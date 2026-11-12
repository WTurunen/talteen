---
title: Known limitations
---

# Known limitations

- **Restored issues get a new issue key.** Jira Cloud's API doesn't allow re-using keys.
  We label every restored issue and record the old→new mapping, and the restored issue
  carries an audit comment naming the original key.
- **Original created date and comment timestamps can't be re-applied.** Jira doesn't
  allow setting them. The original creation date, deletion date, and who deleted the
  issue are recorded in the audit comment; each restored comment is prefixed with its
  original author and timestamp.
- **Only deletions that happen *after* you install are recoverable.** We can't see into
  the past — Jira deletes are permanent and leave nothing behind. **Install before you
  need it.**
- **Reporter is restored when permissions allow.** Setting the reporter requires the
  Modify Reporter permission; without it, the restored issue's reporter falls back and
  the original reporter is noted in the audit comment.
- **Restored issues start at the workflow's initial status.** Jira doesn't allow setting
  the status when an issue is created, so a "Done" issue comes back at its workflow's
  first status (e.g. "To Do"). Everything else about the issue restores normally.
- **A link changed just before an issue is deleted can be missed.** The app records an
  issue's links about 10 seconds after a link changes, so that one recording covers many
  link changes. During a bulk link change the wait can be a few minutes, because the app
  records the links of only a few issues at a time. If the issue is deleted during the
  wait, the restored issue does not get that link, and the restore report does not list it.
- **A link removed just before one of its issues is deleted can come back on restore.**
  The app keeps a link to an issue that is in the trash, so that a restore of both issues
  can link them again. If someone removes a link and then deletes one of the two issues
  during the same wait, the app cannot tell this from a link that Jira removed together
  with the deleted issue. A restore then creates the link again. Remove it by hand if you
  do not want it.
- **Restore two linked issues together to get their link back.** If both issues of a link
  are in the trash, select both and click Restore selected. The app restores a selection in
  groups of 25, and a link between two groups is not created again. If you restore the
  issues one at a time, each restore report lists the link as lost.
- **Attachment files come back while attachment capture is on.** Capture is already on
  when you install the app, so a fresh install is keeping copies from day one. You can
  switch it off in Settings, or exclude individual projects from it. The app keeps a copy
  of each attachment's file. Two separate limits apply. Each file has a size cap
  (adjustable 1–25 MB, default 10 MB). 25 MB is a hard maximum: the app cannot keep a
  larger file, such as a long video, at any setting, because the platform limits how much
  data an app can store in a few seconds. Separately, capture has a monthly *write
  allowance* (adjustable, default 250 MB) that resets on the 1st of each month, UTC. It
  limits how much is captured each month, not how much is held at once: a captured copy
  is kept for as long as its issue exists, and is deleted along with the issue's trash
  record when retention expires (60 days by default). A file deleted from an issue that
  still exists is kept for the grace window instead (14 days by default). The allowance
  is charged on stored size, about a third larger than the file itself, so 250 MB of
  allowance takes in roughly 187 MB of actual files. Captured files are re-uploaded on
  restore, with inline image embeds in the description re-pointed at the restored files.
  Files over the cap, over the allowance, or uploaded while capture was switched off
  restore as metadata only — the restore report lists every affected file, and the CSV
  export gives a per-file reason, so nothing is silently lost.
- **A restore that carries attachment files runs from your browser tab — keep it open.**
  The files upload from the admin's browser in batches. If the tab closes mid-restore,
  the recreated issue exists but has no description, comments, or links yet — those land
  when the restore finishes. To finish it: open the app, click Restore on the same trash
  item, and use the Resume button on the "restore already in progress" notice. The app
  has no permission to delete Jira issues, so it cannot clean up a half-finished restore
  by itself.
- **Change history starts fresh.** The restored issue is a faithful copy of content, not
  of Jira's internal history stream.
- **Restoring a deleted file charges your monthly attachment budget again.** The file is
  uploaded back to the issue as a new attachment, and the app re-captures it like any other
  upload — so those megabytes count twice in total for the month. There is no refund path.
  The confirmation dialog names the file's size and states the cost before you click.
- **Two people clicking Restore on the same file at the same instant can produce two copies.**
  The app blocks the ordinary double-click, but Jira's storage offers no way to lock a row that
  carries an index, so two genuinely simultaneous clicks from different browsers can both get
  through. Delete the spare from the issue.
- **A crash mid-upload can leave a file attached with no record of it.** If the app dies in the
  instant between Jira accepting the upload and the app writing that down, a retry uploads a
  second copy. It is one write wide and cannot be closed on this platform. It is visible on the
  issue, not silent.
- **With capture off, the project excluded, or the file now over your per-file cap, a restored
  file is not protected again.** The restore still succeeds and the file comes back — it just
  will not be re-banked, so deleting it again is permanent. The confirmation dialog tells you
  which of the three applies before you commit to the restore.
- **The project and issue shown for a deleted file are from the moment it was deleted.** If the
  issue has since been moved to another project, the list still shows the old one — and so can
  the warning about whether a restored file will be protected again. Permission to restore is
  always checked against where the issue lives *now*, so the stale label can never grant access
  it should not; only the display and that advisory notice can be out of date.
- **A file's stored copy outlives the restore by up to the grace window.** Restoring puts the
  file back immediately; releasing the app's own copy is background work that runs on the
  nightly job. Nothing is billed for holding it.
- **Inline images in an issue's description are re-pointed at the restored file; images inside
  comments are not.** The app does not edit comments people wrote — an embed in a comment keeps
  pointing at the removed file, and the file itself is back on the issue either way.
- **If re-pointing a description embed fails, the file still comes back but the image stays
  broken, and restoring again will not retry it.** The app re-points the embed only on the
  restore that puts the file back; a second restore of the same file recognises it is already
  restored and stops there. It also skips the re-point deliberately if anyone edited the
  description in the meantime — overwriting someone's edit to fix an image is the worse trade.
  Re-inserting the image by hand is the fix.
