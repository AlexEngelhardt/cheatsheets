# git

- In git version 2.23, `git checkout` was split into:
  - `git switch` for checking out branches
  - `git restore` for restoring edited files
- The commands don't add new functionality, just make it easier than using `git checkout` for both tasks


## Config

`git config --list --show-origin` shows the currently active config settings
along with where they are set


## .gitignore

- `/foo` ignores the `foo` folder in the root
- `foo/` ignores *every* `foo` folder
- `foo` ignores *every* `foo` *file and folder*


## Relative refs

see also `git help revisions`

ref | description
--- | -----------
`@` | Shortcut for `HEAD`. E.g. `git diff @~1 @ -- file.txt`
`HEAD~` | The commit before HEAD
`master~` | The commit before where `master` points to
`master~~` | The commit 2 generations before
`master~3` | `master~~~`
`master^2` | Useful when a commit has multiple parents
`master@{3}` | a *reflog*
`master@{1.week.ago}` | This works too!


## git mv, git rm

cmd | description
--- | ----------- 
`git rm file.txt` | delete file from working directory and stage deletion
`git rm --cached file.txt` | delete file from version control, but keep it locally
`git mv fa.txt fb.txt` | Move file and stage change


## git diff

Generally, `git diff A B` shows the changes required to go **from A to B**.

`git diff A` shows the changes required to go **from older to newer**, newer in
this case is your working directory.

TODO: Difference between `git diff A..B` and `git diff A...B`

cmd | description
--- | -----------
`git diff` | Difference from index (or last commit if index is empty) to working tree
`git diff --staged` (or `--cached`) | Difference from last commit to index ("what is about to be committed")
`git diff HEAD` | Difference from last commit to working tree
`git diff -- file.txt` | Shows the changes for just `file.txt`
`git diff A B` | Difference from A to B 
`git diff A..B` | Synonymous to `git diff A B`
`git diff --name-only A B` | Show only the file names
`git diff A...B` | Difference *from their common ancestor* (TODO huh?)
`git show [SHA]` | Shows the changes a specific commit introduced


## git log

cmd | description
--- | -----------
`git log --follow file.txt` | Shows log only for commits that modified file.txt
`git log A B` | Show commit difference from A to B


## git add

### Hunks

To add only a part of a file: ([read me](https://git-scm.com/book/en/v2/Git-Tools-Interactive-Staging) for details)

- `git add -i` to enter interactive staging
  - Select a file or files
  - Press Enter
- or `git add -p file.txt` to directly enter patch mode for one file
- Git will ask you for each hunk what to do. Type `?` for help.

Afterwards, use `git diff --staged` to verify you staged the correct changes.
Use `git reset -p` to unstage mistakenly added hunks.

## git merge

`git merge featureA master`

The direction is merging A **into** B.

`git merge featureA` merges `featureA` into the currently active branch

### Merge conflicts

- Add `vimdiff` as the diff tool in your config file and use it, [read me](https://www.rosipov.com/blog/use-vimdiff-as-git-mergetool/)
- Using `diff3` should be the default, [read me](https://stackoverflow.com/questions/27417654/should-diff3-be-default-conflictstyle-on-git/70387424#70387424)
- Try `git mergetool` when a conflict occurs. This opens a GUI (or `vimdiff`) where you can choose how to resolve conflicts.


## Remotes

cmd | description
--- | -----------
`git fetch` | Only download all history, change nothing locally
`git pull` | == `git fetch; git merge` (can be configured to use rebase instead)
`git pull origin master` | Pull the branch `master` from the remote `origin`
`git merge origin/master` | Merge the (locally available!) branch `origin/master` into the current branch

