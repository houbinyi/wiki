
git --exec-path
git --version

=== git config ===
git config [--global|--system] key value

git config -e
git config -e --global
git config -e --system
git config --global user.name "user name"
git config --global user.email "user@mail.to"
git config --unset --global user.name
git config --unset --global user.email
git config --system alias.st status
git config --system color.ui true
git config user.name
git config user.email
GIT_CONFIG=test.init git config a.b.c.d "hello world"
git config core.logallrefupdates

git init
git status
git commit --allow-empty -m 'some message'
git commit --amend --allow-empty --reset-author
git clean -fd
git checkout 
git mv # change name


=== git add ===
git add -u
git add -A
git add -i
git add -f 

=== git ignore ===
edit .gitignore
edit .git/info/exclude
git config core.excluedsfile
edit ~/.gitignore

=== git archive ===
git archive -o some.zip HEAD
git archive -o some.tar HEAD src doc
git archive --fromat=tar --prefix=1.0/ v1.0
git tar-commit-id

=== git show ===
git show

=== git log ===
git log --pretty=oneline
git log --pretty=fuller
git log --pretty=raw
git log --pretty=raw --graph
git log --stat
git log -l HEAD
git log -l master
git log -l refs/heads/master
git log --oneline --decorate -4

=== git status ===
git status -s
git status -s -b
git status --ignored -s

=== git diff ===
git diff <commit1> <commit2> — <paths>
git diff <path1> <path2>
git diff --word-diff
git diff # workspace - stage
git diff HEAD # workspace - reporsitory
git diff master
git diff --cached # stage - reporsitory
git diff --cached HEAD
git diff --cached master

=== git blame ===
git blame file
git blame -L 6,+5 file

=== git ls ===
git write-tree # write tree from stage to reporistory
git ls-tree -l HEAD # reporsitory
git ls-files -s # stage
git ls-files --with-tree=HEAD^

=== git object ( commit, tree, blob ) ===
hash path:
commit: 123abc^2 the second parent of 123abc's all parents
tree : 123abc^{tree}
blob: 123abc:path/to/file
blob in stage: :path/to/file

=== git tree ===
git mktree # create tree from stdio
git read-tree # read tree to stage
git write-tree # create tree from stage
git commit-tree # commit tree
git ls-tree # list objects in a tree


=== git cat-file ===
git cat-file -t 123abc
git cat-file -p 123abc
git cat-file blob HEAD:some.file


=== git branch ===
git branch
git branch -v

=== git reset ===
# reset HEAD
git reset [-q] [<commit>] [--] <path>...
git reset [--soft|--mixed|--hard|--merge|--keep] [-q] [<commit>]
git reset --hard <commit> # change ref, replace stage, workspace 
git reset --soft <commit> # change ref
git reset --mixed <commit> # change ref, replace stage
git reset --hard HEAD^

=== git reflog ===
git reflog show master
git reflog show refs/stash

=== git checkout ===
# check out from stage
git checkout 123abc
git checkout [-q] [<commit>] [--] <paths>...
git checkout [<branch>]
git checkout [-m] [[-b] --orphan <new_branch>] [<start_point>]

=== git stash ===
git stash
git stash save "message"
git stash list
git stash pop
git stash apply
git stash drop
git stash clear
git stash bracn <branch-name>

=== git tag ===
git tag -m 'message' tagname
git describe

=== git rm ===

=== git archive ===
git archive -o some

gitk
gitk --all
gitk --since="2 weeks ago"
gitk v2.6.12.. include/scsi drivers/scsi

=== git rev-parse ===
# parse reference variable to hash value
git rev-parse --git-dir
git rev-parse --show-toplevel
git rev-parse --show-prefix
git rev-parse --show-cdup
git rev-parse --parseopt
git rev-parse --symbolic --branches
git rev-parse --symbolic --tags
git rev-parse --symbolic --glob-refs/*

git rev-parse master
git rev-parse HEAD
git rev-parse refs/heads/master

== git rev-list ==
git rev-list HEAD


















