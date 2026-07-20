# WeHunt.gg Feedback Hub — Maintainer Setup

The repository files are ready. Complete the settings below in GitHub's web interface to activate Discussions, voting, labels, and the roadmap.

## 1. Enable repository features

Open **Settings → General → Features** and make sure these are enabled:

- Issues
- Discussions
- Projects

Keep blank Issues disabled through `.github/ISSUE_TEMPLATE/config.yml` so public submissions use the structured forms.

## 2. Configure Discussions

Create or confirm these categories under **Discussions → Categories**:

| Category | Format | Purpose |
|---|---|---|
| Ideas | Open-ended discussion | Feature requests and community voting |
| Q&A | Question and answer | Product questions and help |
| Announcements | Announcement | Releases and important updates |
| Polls | Poll | Compare product choices with the community |

The feature request form is stored at `.github/DISCUSSION_TEMPLATE/ideas.yml`. The category must be named **Ideas** so its slug is `ideas` and GitHub applies the form.

Suggested Ideas category description:

> Suggest improvements to WeHunt.gg, explain the problem they solve, and upvote requests you want to see built.

## 3. Create labels

Create the following repository labels. The values below are suggested colors without the leading `#`.

### Type

| Label | Color |
|---|---|
| type: bug | d73a4a |
| type: feature | a2eeef |
| type: improvement | 84b6eb |
| type: maintenance | c5def5 |

### Status

| Label | Color |
|---|---|
| status: needs-triage | fbca04 |
| status: needs-review | fbca04 |
| status: considering | d4c5f9 |
| status: accepted | 0e8a16 |
| status: planned | 1d76db |
| status: in-progress | 5319e7 |
| status: testing | bfdadc |
| status: shipped | 0052cc |
| status: declined | cfd3d7 |

### Priority

| Label | Color |
|---|---|
| priority: critical | b60205 |
| priority: high | d93f0b |
| priority: normal | fbca04 |
| priority: low | 0e8a16 |

### Platform

| Label | Color |
|---|---|
| platform: steam | 1b2838 |
| platform: xbox | 107c10 |
| platform: playstation | 006fcd |
| platform: website | 0969da |
| platform: all | 6f42c1 |

### Product area

| Label | Color |
|---|---|
| area: achievements | c5def5 |
| area: sync | f9d0c4 |
| area: accounts | e99695 |
| area: profiles | fef2c0 |
| area: search | bfdadc |
| area: ui | d4c5f9 |
| area: notifications | b60205 |
| area: admin | 7057ff |

### Triage helpers

| Label | Color |
|---|---|
| duplicate | cfd3d7 |
| needs-information | d876e3 |
| cannot-reproduce | e4e669 |
| security | b60205 |

The bug and feature forms already reference the initial type and triage labels. Once the labels exist, new submissions will receive them automatically.

## 4. Create the project tracker

Create a user-level GitHub Project named **WeHunt Product** and link this repository to it.

### Suggested custom fields

| Field | Type | Values or use |
|---|---|---|
| Status | Single select | Inbox, Needs Review, Accepted, Planned, In Progress, Testing, Shipped, Declined |
| Type | Single select | Bug, Feature, Improvement, Maintenance |
| Priority | Single select | P0 Critical, P1 High, P2 Normal, P3 Low |
| Platform | Single select | All, Website, Steam, Xbox, PlayStation |
| Area | Single select | Achievements, Sync, Accounts, Profiles, Search, UI, Notifications, Admin |
| Effort | Single select | XS, S, M, L, XL |
| Release | Single select | Backlog, MVP, Beta, v1.0, Later |
| Start date | Date | Work start |
| Target date | Date | Intended completion |
| Public request | Text | Link to the original Discussion |

Use GitHub's built-in assignee field for the owner.

### Suggested views

1. **Triage Inbox** — Status is Inbox or Needs Review
2. **Bug Board** — board grouped by Status, filtered to Type = Bug
3. **Feature Pipeline** — board grouped by Status, filtered to Type = Feature
4. **Current Work** — In Progress or Testing
5. **Roadmap** — roadmap layout grouped by Release or Platform
6. **Platform Health** — grouped by Platform
7. **Shipped** — completed items for release notes

### Suggested automation

Create an auto-add workflow that adds new Issues from `ruanbotha33/wehunt-feedback` to the project with Status set to Inbox.

When accepting a feature request:

1. Add `status: accepted` to the Discussion.
2. Create an Issue from the Discussion.
3. Add the Issue to the project.
4. Set Type, Priority, Platform, Area, Effort, and Release.
5. Preserve the Discussion link in the Public request field.

## 5. Add links to WeHunt.gg

Add a visible **Feedback & Roadmap** link in the site navigation or footer.

Recommended destinations:

- Bugs: `https://github.com/ruanbotha33/wehunt-feedback/issues/new?template=bug_report.yml`
- Features and voting: `https://github.com/ruanbotha33/wehunt-feedback/discussions/categories/ideas`
- All feedback: `https://github.com/ruanbotha33/wehunt-feedback`

Recommended link text:

> Feedback & Roadmap — report bugs, suggest features, and vote on upcoming improvements.

## 6. Weekly triage routine

Once a week:

1. Review new Issues and Ideas.
2. Close or merge duplicates.
3. Request missing reproduction details.
4. Apply platform, area, type, and priority labels.
5. Move accepted work into the project.
6. Update statuses on work already underway.
7. Mark shipped requests and include them in release notes.

## 7. Before announcing the hub

Test the experience with a non-maintainer GitHub account:

- Submit a bug report.
- Open an Idea.
- Upvote an Idea.
- Confirm labels apply correctly.
- Confirm new Issues enter the project.
- Confirm no private or source-code information is exposed.
