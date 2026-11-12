# talteen

Public legal and support pages for **Talteen - Restore Deleted Issues & Attachments for Jira**, an
Atlassian Marketplace app. Served by GitHub Pages.

This repo is public **only** so the Marketplace listing can point at stable URLs. The app
source lives elsewhere and stays private.

## URLs the Marketplace listing needs

| Listing field | URL |
|---|---|
| Privacy policy (mandatory) | `/privacy` |
| Documentation | `/docs` |
| Support (App details → Support ticketing system) | `/support` |
| Support email | the `support_email` in `_config.yml` |

## Editing

Identity — legal name, business ID, address, contact addresses, effective date — lives in
`_config.yml` and nowhere else. The pages read it as `{{ site.* }}`. Change it once,
there.

**There are three contact addresses, and which one a page uses is deliberate:**

| Variable | Used by |
|---|---|
| `support_email` | the footer on every page, and the landing page |
| `privacy_email` | `privacy.md` section 13, and both contacts in `dpa.md` |
| `security_email` | the vulnerability-report line in `security.md` |

They are aliases to one inbox, so the split is about what each document says rather than
where mail lands. `privacy_email` is the one that matters: it keeps the DPA and the privacy
policy naming the same data protection contact. Do not collapse them back into one.

Page content is plain Markdown rendered by `_layouts/default.html`. No theme gem, no
plugins, no Gemfile — GitHub Pages builds it as-is.

## Keeping it honest

`privacy.md` mirrors `docs/listing/data-handling.md` in the private app repo, which is the
source of record for every technical claim in it. **If capture behaviour or retention
changes in the app, both files change.** A privacy policy that has drifted from the code
is worse than none.

`limitations.md` and `docs.md` mirror `docs/listing/known-limitations.md` and
`docs/listing/DOCS-STE.md` the same way.
