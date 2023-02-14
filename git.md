# git

https://git-scm.com/book/en/v2

## terminology

tree: folder/ directory

blob: file

history is a linear sequence of snapshots
copy of folders dated in timestamp?

git history: directed acyclic graph

## git in pesudo code

type blob = array<byte>

type tree = map<string, tree | blob>

type commit = struct {
parent: array<commit>
author: string
message: string
snapshot: tree
}

type object = blob | tree | commit

objects = map<string, object>

def store(o):
id = sha1(o)
objects[id] = o

def load(id):
return objects[id]

`all are pointers`
(eg snapshot is refrencing the tree through tree's id, but not storing the tree itself)

43tio3jtui5 <- hashed name of specific commit generated from sha1
"fixing xxx bug" <- commit message
reference = map<string, string>

## COMMAND

### Basics

git help <command>: get help for a git command

git init: creates a new git repo, with data stored in
the .git directory

git status: tells you what’s going on

git add <filename>: adds files to staging area

git commit: creates a new commit

Write good commit messages!

Even more reasons to write good commit messages!

git log: shows a flattened log of history

git log --all --graph --decorate: visualizes history as
a DAG

git diff <filename>: show changes you made relative to
the staging area

git diff <revision> <filename>: shows differences in a
file between snapshots

git checkout <revision>: updates HEAD and current branch

### Branching and merging

git branch: shows branches

git branch <name>: creates a branch

git checkout -b <name>: creates a branch and switches to
it

same as git branch <name>; git checkout <name>

git merge <revision>: merges into current branch

git mergetool: use a fancy tool to help resolve merge
conflicts

git rebase: rebase set of patches onto a new base

### Remotes

git remote: list remotes

git remote add <name> <url>: add a remote

git push <remote> <local branch>:<remote branch>: send
objects to remote, and update remote reference

git branch --set-upstream-to=<remote>/<remote branch>:
set up correspondence between local and remote branch

git fetch: retrieve objects/references from a remote

git pull: same as git fetch; git merge

git clone: download repository from remote

### Undo

git commit --amend: edit a commit’s contents/message

git reset HEAD <file>: unstage a file

git checkout -- <file>: discard changes

### Advanced Git

git config: Git is highly customizable

git clone --depth=1: shallow clone, without entire
version history

git add -p: interactive staging

git rebase -i: interactive rebasing

git blame: show who last edited which line

git stash: temporarily remove modifications to working
directory

git bisect: binary search history (e.g. for regressions)

.gitignore: specify intentionally untracked files to
ignore

## about git commit message

https://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html

https://cbea.ms/git-commit/

## Best Practices

https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow

https://www.endoflineblog.com/gitflow-considered-harmful

https://nvie.com/posts/a-successful-git-branching-model/
