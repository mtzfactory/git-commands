# Git Commands

## General-use

### `git cm` & `git cml`
Gets the current commit ID. `cm` gives the short ID, and `cml` gives the long ID.

```bash
git diff $(git cml)...HEAD
```

### `git conflicted`
Opens merge-conflicted files for editing in the editor you provide

```bash
git conflicted $EDITOR
```

### `git contains`
Finds which branches/tags a particular commit is part of

```bash
git contains 7ebcf01
```

### `git delete`
Deletes the local copy of the branch, as well as the one on the `origin` remote.

```bash
git delete outdated-feature-branch
```

### `git delta`
Shows the commits from the current branch which are not in the specified branch.

```bash
git delta release-branch
```

### `git lol`, `git lola` & `git hist`
`lol` is a "better" version of `git log` (e.g., long commit ID, commit message, commit author, relative timestamp). `hist` is identical, but also includes a list of all files that were changed in that commit.

`lola` is the same as `lol`, but uses `--graph` to show branch relationships.

```bash
git lol
git hist
```

### `git long` & `git short`
Gets the long/short version of a commit ID.

```bash
git long e60a01d
# e60a01d107d0de7f97689bb311d8d8d80862e583

git short e60a01d107d0de7f97689bb311d8d8d80862e583
# e60a01d
```

### `git nuke`
Permanently blows-away any uncommitted changes. Resets to the position of the last commit.

```bash
git nuke
```

### `git tags`
Returns a list of all tags in the repository.

```bash
git tags
```

### `git this`
Returns the name of the current branch.

```bash
git push --set-upstream origin $(git this)
```

### `git track`
Sets the current branch to track against the specified remote branch.

```bash
git track origin master
```

### `git uncommit`
Uncommits the last commit in your local branch.

```bash
git uncommit
```

### `git unstage`
Unstages (i.e., un-adds) the files you're preparing to commit.

```bash
git unstage
```

----

## [Hub](http://hub.github.com)

### `git clone`
Clone yours — or another — project on GitHub Enterprise.

```bash
git clone dotfiles
→ git clone git://github.company.com/YOUR_USER/dotfiles.git

git clone ryan_parman/hub
→ git clone git://github.company.com/ryan_parman/hub.git
```

### `git browse`
See the current project's issues.

```bash
git browse -- issues
→ open https://github.company.com/ryan_parman/hub/issues
```

Open another project's wiki

```bash
$ git browse ryan_parman/jekyll wiki
→ open https://github.company.com/ryan_parman/jekyll/wiki
```

Example workflow for contributing to a project:

```bash
git clone github/hub
cd hub

# create a topic branch
git checkout -b feature
  ( making changes ... )
git commit -m "done with feature"
```

### `git fork`
It's time to fork the repo!

```bash
git fork
→ (forking repo on GitHub...)
→ git remote add YOUR_USER git://github.com/YOUR_USER/hub.git
```

Push the changes to your new remote.

```bash
git push YOUR_USER feature
```

### `git pull-request`
Open a pull request for the topic branch you've just pushed.

```bash
git pull-request
→ (opens a text editor for your pull request message)
```

### `git fetch`
Fetch from multiple trusted forks, even if they don't yet exist as remotes.

```bash
git fetch johnny_bravo,ryan_parman
→ git remote add johnny_bravo git://github.company.com/johnny_bravo/hub.git
→ git remote add ryan_parman git://github.company.com/ryan_parman/hub.git
→ git fetch --multiple johnny_bravo ryan_parman
```

### `git checkout`
Check out a pull request for review.

```bash
git checkout https://github.company.com/ryan_parman/hub/pull/134
→ (creates a new branch with the contents of the pull request)
```

### `git am`
Directly apply all commits from a pull request to the current branch.

```bash
git am -3 https://github.company.com/ryan_parman/hub/pull/134
```

`am` can be better than cherry-pick since it doesn't create a remote

```bash
git am https://github.company.com/ryan_parman/hub/commit/177eeb8
```

### `git cherry-pick`
Cherry-pick a GitHub URL.

```bash
git cherry-pick https://github.company.com/ryan_parman/hub/commit/177eeb8
→ git remote add ryan_parman git://github.company.com/ryan_parman/hub.git
→ git fetch ryan_parman
→ git cherry-pick 177eeb8
```

### `git compare`
Open the GitHub compare view between two releases.

```bash
git compare v0.9..v1.0
```

Put compare URL for a topic branch to clipboard.

```bash
$ git compare -u feature | pbcopy
```

### `git create`
Create a repo for a new project.

```bash
git init
git add .
git commit -m "It begins."
git create -d "My new thing"
→ (creates a new project on GitHub with the name of current directory)
git push origin master
```
