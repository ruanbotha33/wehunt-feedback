# WeHunt Product — Project Configuration

Project: https://github.com/users/ruanbotha33/projects/2

This is the recommended final configuration for the public WeHunt.gg product tracker.

## Ownership and visibility

- Owner: `ruanbotha33`
- Project name: `WeHunt Product`
- Visibility: **Public** when the roadmap is ready for users
- Default repository: `ruanbotha33/wehunt-feedback`
- Linked repository: `ruanbotha33/wehunt-feedback`

The public feedback repository should contain user-facing bugs and accepted feature work. Private implementation details can remain in a private source repository and should only be added to a public Project when the item itself is safe to expose.

## Keep one source of truth

Use repository labels for these attributes instead of duplicating them as Project fields:

- Type: `type: bug`, `type: feature`, `type: improvement`, `type: maintenance`
- Priority: `priority: critical`, `priority: high`, `priority: normal`, `priority: low`
- Platform: `platform: steam`, `platform: xbox`, `platform: playstation`, `platform: website`, `platform: all`
- Product area: the `area:` labels

Show GitHub's built-in **Labels** field in table and board views. This keeps issue metadata and Project metadata synchronized automatically.

If duplicate Type, Priority, Platform, or Area custom fields were already created, remove them after confirming no unique data is stored in them.

## Project fields

### Status

Use the Project's built-in Status single-select field with these options, in this order:

1. Inbox
2. Needs Review
3. Accepted
4. Planned
5. In Progress
6. Testing
7. Shipped
8. Declined

### Additional custom fields

| Field | Type | Values or purpose |
|---|---|---|
| Effort | Single select | XS, S, M, L, XL |
| Release | Single select | Backlog, MVP, Beta, v1.0, Later |
| Start date | Date | When implementation is intended to begin |
| Target date | Date | Intended completion or release date |
| Public request | Text | URL of the original feature Discussion |

Use GitHub's built-in Assignees, Labels, Milestone, Repository, and Linked pull requests fields instead of recreating them.

## Recommended views

GitHub's filter box provides autocomplete. Save each configured view after changing its filter, layout, grouping, sorting, or visible fields.

| View | Layout | Filter | Configuration |
|---|---|---|---|
| All Work | Table | none | Show Status, Labels, Assignees, Effort, Release, Start date, Target date, and Repository |
| Triage Inbox | Table | `status:"Inbox","Needs Review"` | Sort by Priority labels manually during triage; show Labels and Assignees |
| Bug Board | Board | `label:"type: bug"` | Columns by Status; hide Shipped and Declined when focusing on active work |
| Feature Pipeline | Board | `label:"type: feature"` | Columns by Status; show Release and Effort |
| Current Work | Board | `status:"In Progress",Testing` | Columns by Status; show Assignees and Target date |
| Roadmap | Roadmap | `status:Accepted,Planned,"In Progress",Testing` | Use Start date and Target date; group by Release |
| Platform Health | Table | `label:"type: bug"` | Show Labels and group or filter using the `platform:` labels |
| Shipped | Table | `status:Shipped` | Sort by Target date descending for release-note preparation |

## Built-in workflows

Open the Project menu and select **Workflows**.

### Auto-add new feedback Issues

Configure **Auto-add to project**:

- Repository: `ruanbotha33/wehunt-feedback`
- Filter: `is:issue`
- State: enabled

This adds new Issues created after the workflow is enabled. Add existing Issues manually, because auto-add does not backfill existing matching items.

### Set the initial status

Configure the built-in workflow for items added to the Project:

- Trigger: Item added to project
- Action: Set Status to `Inbox`

### Optional cleanup

After the tracker has been in use for a while, configure an auto-archive workflow for items that have remained Shipped or Declined long enough that they no longer need to appear in active views.

## Link the Project and repository

In `wehunt-feedback`:

1. Open the repository's **Projects** tab.
2. Select **Link a project**.
3. Select **WeHunt Product**.

In the Project settings:

1. Set `ruanbotha33/wehunt-feedback` as the default repository.
2. Save the change.

## Suggested Project description

> Public roadmap and product tracker for WeHunt.gg bugs, feature requests, improvements, and releases.

## Suggested Project README

```markdown
# WeHunt Product

This Project tracks public bugs, accepted feature requests, improvements, and roadmap work for [WeHunt.gg](https://wehunt.gg).

- Report bugs in the [feedback repository](https://github.com/ruanbotha33/wehunt-feedback/issues/new?template=bug_report.yml).
- Suggest and vote on features in [Ideas](https://github.com/ruanbotha33/wehunt-feedback/discussions/categories/ideas).
- Votes help show community interest but do not guarantee implementation or delivery order.

Items may change as technical constraints, platform limitations, and product priorities evolve.
```

## Verification checklist

- [ ] Project visibility is Public
- [ ] Project description and README are populated
- [ ] `wehunt-feedback` is the default repository
- [ ] Project is linked from the repository's Projects tab
- [ ] Status options match the agreed workflow
- [ ] Effort, Release, Start date, Target date, and Public request fields exist
- [ ] Duplicate Type, Priority, Platform, and Area custom fields are removed
- [ ] All eight recommended views exist and are saved
- [ ] Auto-add is enabled for new `wehunt-feedback` Issues
- [ ] Newly added items receive Status = Inbox
- [ ] Issue #1 is manually added to the Project
- [ ] A test bug enters the Project and receives the expected labels
