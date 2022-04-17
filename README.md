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

...
```
