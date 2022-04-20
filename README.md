# Git

Example of Git version control system commands.

Please click the "Star" button on GitHub if you find this asset to be useful!

## Configuration

View the manpage for a command.

```
// View comprehensive manpages.
git help <command>

// View condensed manpages.
git help <command> -h
```

Set or view Git credentials for this user. These properties are baked into every commit.

```
// Set credentials.
git config --global user.name "<name>"
git config --global user.email <email>

// View credentials.
git config user.name
git config user.email

// View all credentials and where they are stored.
git config --list --show-origin
```

## Basics

Declare an existing directory as a Git repository. A `.git` directory will be created containing repository metadata.

```
git init
```

Clone an existing repository onto this machine.

```
// Clone normally.
git clone https://github.com/<user>/<repository>

// Clone with a custom name.
git clone https://github.com/<user>/<repository> <custom_name>
```

View the current state of files in this repository. States include untracked, unmodified, modified, and staged.

```
// View comprehensive status.
git status

// View condensed status.
git status --short
```

Add files to the staging area. If an added file is not yet tracked by the current repository, then it will start being tracked.

```
// Add and track a file.
git add <file>

// Add and track all files in a directory.
git add <directory>
```

View changes between staged and unstaged files, or view changes between staged files and the most recent commit.

```
// View changes between staged and unstaged files.
git diff

// View changes between staged files and the most recent commit.
git diff --cached
```

Commit staged files.

```
// Opens a text editor with a default commit message.
git commit

// Inlines a commit message and skips the text editor.
git commit -m "<message>"
```

Modify the most recent commit. Only use this method for local commits that have not yet been pushed.

```
// Amend files and message.
git commit --amend

// Only amend files.
git commit --amend --no-edit
```

Delete a tracked file, or untrack a file in the staging area.

```
// Delete a tracked file.
git rm <file>

// Delete a file in the staging area.
git rm <file> -f

// Untrack a file without deleting it.
git rm --cached <file>
```

Move or rename a tracked file.

```
git mv <from_file> <to_file>
```

View commit history, including the hash, author, date, message, etc.

```
// Comprehensive list including hash, author, date, and message.
git log

// Truncated list also including staged/unstaged diff.
git log --patch -<length>

// ...including the exact files that were changed.
git log --stat

// ...including one line per commit.
git log --oneline

// Target a specific branch.
git log <branch>

// Target all branches.
git log --all

...
```

Unstage a file.

```
// Old method.
git reset HEAD <file>

// New method.
git restore --staged <file>
```

Revert a file to its previous commit. Note that all changes not commited will be lost.

```
// Old method.
git checkout -- <file>

// New method.
git restore --staged <file>
```

View remote servers for this repository.

```
// Name only.
git remote

// Names and URLs of all remotes.
git remote -v

// Names, URLs, branches, etc.
git remote show <remote>
```

Add a remote and assign a name to it.

```
git remote add <remote> <url>
```

Fetch all data from a remote.

```
git fetch <remote>
```

Push commits from a local branch to a remote branch.

```
git push <remote> <branch>
```

Rename a remote.

```
git remote rename <remote> <new_remote>
```

Remove a remote.

```
git remote remove <remote>
git remote rm <remote>
```

View tags for this repository.

```
// All tags.
git tag

// Filtered tags.
git tag -l "<tag>"
```

Create an annotated or lightweight tag. Annotated tags record a name, metadata, and description. Lightweight tags do not record any data except a searchable name.

```
// Annotated tag.
git tag -a <tag> -m "<message>"

// Lightweight tag.
git tag <tag>

// Tag an old commit.
git tag -a <tag> -m "<message>" <commit>
```

Push local tags to a remote.

```
// Push a particular tag.
git push <remote> <tag>

// Push all tags.
git push <remote> --tags

// Push only annotated tags.
git push <remote> --follow-tags
```

Delete a tag.

```
// Delete locally.
git tag -d <tag>

// Delete remotely.
git push <remote> --delete <tag>
```

Checkout a tag. Note that the working directory will become detached and a new branch must be created to save changes.

```
git checkout <tag>
```

Create an alias for custom Git command.

```
git config --global alias.<custom_command> "<command>"
```

## Branching

Create a new branch.

```
git branch <branch>
```

Checkout a branch.

```
// Move HEAD to a branch.
git checkout <branch>
git switch <branch>

// ...also create a branch.
git checkout -b <branch>
git switch -c <branch>

// Revert to the previous branch.
git switch -
```

Merge branches. The current branch pulls in changes from the targetted branch.

```
git merge <branch>
```

Delete a branch.

```
// On the local machine.
git branch -d <branch>

// On the server.
git push <remote> --delete <branch>
```

View branches.

```
// All branches.
git branch

// Branches that have been merged with the current branch.
git branch --merged

// Branches that have not been merged with the current branch.
git branch --no-merged
```

Rename a branch.

```
// On the local machine.
git branch --move <old_branch> <new_branch>

// On the server.
git push --set-upstream <remote> <new_branch>
```

View the stash stack.

```
git stash list
```

Stash the current working directory.

```
// Tracked files.
git stash
git stash push

// Tracked and untracked files.
git stash --all
```

Load a stashed working directory. Note that applying a stash does not restore the staging area unless a special option is used, nor does it drop the stash from the stack.

```
// Top of the stack.
git stash apply

// Specific entry in the stack.
git stash apply stash@{<entry>}

// ...including the staging area.
git stash apply --index
```

Drop a stash from the stack.

```
// Apply then drop.
git stash pop

// Only drop.
git stash drop stash@{<entry>}
```

## Miscellaneous

Delete all files in this repository that are untracked. Note that files referred to by `.gitignore` are not deleted by default.

```
// Force delete all files.
git clean

// Force delete all files and subdirectories that become empty.
git clean -f -d

// View potential deleted files or directories.
git clean -d --dry-run
git clean -d -n

// ...include files referred to by .gitignore.
git clean -x
```
