# AGENTS.md

Guidance for coding agents working in this repository.

## What this repo is

The `.github` repo for the [@datarobot-labs](https://github.com/datarobot-labs) GitHub organization. It holds org-level defaults, not application code:

- `profile/README.md` — the org profile page rendered at <https://github.com/datarobot-labs>. Public, indexed, and the first thing most people see.
- `.github/workflows/` — org-level reusable workflows. See [README.md](./README.md) for how repos opt in.

Most work here is editing `profile/README.md`.

## Repository listing rules

`profile/README.md` links to repositories across the DataRobot GitHub orgs. Every link is a public endorsement, so the listing is governed by hard rules. These apply to **every** repository reference on the page, in any org (`datarobot`, `datarobot-oss`, `datarobot-community`, `datarobot-labs`, `datarobot-forks`) and in any form.

### Must

- **Public only.** A repository may be listed only if its visibility is `PUBLIC`.
- **Non-archived only.** A repository may be listed only if `isArchived` is `false`.
- **Actively maintained only.** A repository may be listed only if it has been pushed to within the last **9 months**. Anything older is stale — remove it.

### Must not

- **Never list an internal or private repository.** Not in a table, not in prose, not in a footnote, not "for reference". Private repo names can themselves be sensitive; if you are unsure whether a repo is public, verify before writing it down, and omit it if you cannot verify.
- **Never link a private GitHub Pages site.** The Labs site is internal, and its Pages deployment reports `public: false`, so the URL 404s for anyone outside the org. Check with `gh api repos/<org>/<repo>/pages --jq .public` before linking any Pages URL.
- **Never list an archived repository**, even to mark it deprecated.
- **Never link a repo you have not verified exists and is reachable.** A 404 on the org profile is worse than an omission.

### Verify before you edit

Run these before adding, and before any pass that touches the listing:

```bash
# Every public, non-archived repo in the org, newest push first
gh repo list datarobot-labs --limit 200 --no-archived --visibility public \
  --json name,pushedAt,description,isArchived,visibility \
  --jq 'sort_by(.pushedAt) | reverse | .[] | "\(.pushedAt[:10])  \(.name)"'

# Check every repo already linked from the page
grep -oE 'github\.com/(datarobot|datarobot-oss|datarobot-community|datarobot-labs|datarobot-forks)/[A-Za-z0-9._-]+' \
  profile/README.md | sed 's|github.com/||' | sort -u | while read -r r; do
    gh repo view "$r" --json nameWithOwner,visibility,isArchived,pushedAt \
      --jq '[.nameWithOwner, .visibility, (.isArchived|tostring), .pushedAt[:10]] | @tsv' \
      2>/dev/null || echo -e "$r\tNOT-FOUND"
done
```

Anything that comes back non-`PUBLIC`, `true` for archived, `NOT-FOUND`, or with a `pushedAt` older than 9 months from today must be removed from `profile/README.md` in the same change.

### When pruning

- Remove the row or bullet entirely rather than leaving a commented-out stub.
- If a pruned repo was the only entry in a section, remove the section heading and its intro too — don't leave an empty table.
- If a pruned repo has a live successor, add a one-line pointer to the successor instead of the dead entry.
- If a listing genuinely needs an exception to the 9-month rule, raise it with the user rather than silently keeping it.

## Editing profile/README.md

- Keep the existing structure: what Labs is → org comparison table → where to start → get involved. Don't reorganize without being asked.
- Keep the tone. Labs writes with more personality than the other org pages (see the [Labs site](https://github.com/datarobot-labs/site) copy), but the rules still hold: second person, concrete, no marketing superlatives. Describe what a repo *builds* or *adds*, not how great it is.
- Descriptions are one sentence. Two at most, and only when the second one earns it.
- The org is new and mostly internal. Resist padding the page with a repository catalogue it hasn't earned; the org comparison table is what makes the page useful while the org is thin.
- GitHub renders this file with the standard GFM subset — `> [!NOTE]`, `> [!TIP]`, tables, and `<details>` all work. Raw HTML beyond the centered header block does not always render, so avoid adding more.
- The org profile only renders from `profile/README.md` on the default branch.

## Workflow

- Branch naming: `<github-user>/<ticket>-<short-name>`.
- Run `git diff` before committing; commit subjects are `[<JIRA-ID>] <Verb> <what>`.
- Do not `git push` — leave that to the human.
