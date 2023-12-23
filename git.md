# git

- In git version 2.23, `git checkout` was split into:
  - `git switch` for checking out branches
  - `git restore` for restoring edited files
- The commands don't add new functionality, just make it easier than using `git checkout` for both tasks

### Config

`git config --list --show-origin` shows the currently active config settings
along with where they are set

### .gitignore

- `/foo` ignores the `foo` folder in the root
- `foo/` ignores *every* `foo` folder
- `foo` ignores *every* `foo` *file and folder*

### Relative refs

see also `git help revisions`

ref | description
--- | -----------
`@` | Shortcut for `HEAD`. E.g. `git diff @~1 @ -- file.txt`
`HEAD~` | The commit before HEAD
`master~` | The commit before where `master` points to
`master~~` | The commit 2 generations before
`master~3` | `master~~~`
`master^` | Useful when a commit has multiple parents.
`master@{3}` | a *reflog*
`master@{1.week.ago}` | This works too!

### diff

Generally, `git diff A B` shows the changes required to go **from A to B**.

`git diff A` shows the changes required to go **from older to newer**.

cmd | description
--- | -----------
`git diff` | Difference from index (or last commit if index is empty) to working tree
`git diff --staged` (or `--cached`) | Difference from last commit to index ("what is about to be committed")
`git diff HEAD` | Difference from last commit to working tree
`git diff -- file.txt` | Shows the changes for just `file.txt`
`git show [SHA]` | Shows the changes a specific commit introduced

### Merging

`git merge featureA master`

The direction is merging A **into** B.

`git merge featureA` merges `featureA` into the currently active branch

### Merge conflicts

- Add `vimdiff` as the diff tool in your config file and use it, [read me](https://www.rosipov.com/blog/use-vimdiff-as-git-mergetool/)
- Using `diff3` should be the default, [read me](https://stackoverflow.com/questions/27417654/should-diff3-be-default-conflictstyle-on-git/70387424#70387424)

