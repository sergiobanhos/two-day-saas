# Git, PRs and GitHub Issues

## Branches and commits
- One branch per epic: `epic/E02-booking`, created from the updated main branch (`git switch main && git pull` when there's a remote).
- One commit per task, imperative, in the project's language:
  `E02-T03: new booking screen with conflict warning`
  When tasks come from GitHub, add `Refs #<issue>` in the body.
- Before each commit: tests passing, `git status` with no stray files (builds, `.env`, dumps). Add files by name, not with a blind `git add -A`.
- A project without a remote, or a person without GitHub: everything works locally. The "PR" becomes a summary in the chat, and the merge is `git switch main && git merge --no-ff epic/E02-…` after the OK.

## Opening the PR (end of epic, after the epic end gate)
1. `git push -u origin epic/E02-booking`
2. `gh pr create --title "E02 · Booking" --body-file <file>` with this body (in the project's language):

```
## What changes
Two to four plain lines, from the user's point of view.

## Tasks
- [x] T01 · … (#12)
- [x] T02 · … (#13)

## How to test
1. Run `<command>` (or open <test deploy link>)
2. Sign in as <test user>
3. Click … → you should see …

## Review
- Independent reviewer: <model/tool>. Important problems found and fixed: N.
- Tests: <command> → <result>

Closes #12, closes #13
```

3. If the repository has CI, watch the checks; if they fail, fix them on the same branch before calling the person.
4. Give the person the PR link together with "How to test".

## Merge
- Only with the person's explicit OK (merge gate), and according to the authorization recorded in STATUS.md.
- Recommended default: `gh pr merge --squash --delete-branch`, which leaves one clean commit per epic on main.
- Afterwards: `git switch main && git pull`, set the epic to `done` in `docs/epics/README.md` and run the next-epic gate.

## GitHub Issues (when the project uses option B)
- Read tasks: `gh issue list --label E02 --state open --json number,title,labels,body`
- When starting a task: `gh issue edit <n> --add-label "doing"` (create the label if missing).
- Closing happens through the PR's `Closes #n` at merge. Don't close earlier.
- Blocked: comment the reason on the issue (`gh issue comment <n> --body "…"`) and add the `blocked` label.
- Keep `docs/epics/README.md` consistent with the issues.

## Never
`git push --force` · rewriting main · committing secrets · merging without an OK · closing an issue before its PR is merged.
