# MQ GIT CHEAT SHEET

**This is a collection of Git commands, which are very useful for beginners**

refer to the official [Git book](https://git-scm.com/book/en/v2) for more commands

* Check Git [version](https://git-scm.com/docs/git-version)

  ```bash
  git --version or git -v
  ```

## Table of content

1. [Bash commands](#bash-commands)
2. [Basic settings before to start](#basic-settings-before-to-start)
3. [Basic Git operations](#basic-git-operations)
4. [Track changes](#track-changes)
5. [Alias](#alias)
6. [Tagging](#tagging)
7. [Undoing things](#undoing-things)
8. [Branching](#branching)
9. [Stashing](#stashing)
10. [Searching](#searching)
11. [Remote repository](#remote-repository)
12. [Git advanced features](#advanced-features)
13. [Common Git workflow](#common-git-workflow)
14. [Preparing release](#preparing-release)
15. [Miscellaneous](#miscellaneous)

---

* Get help on git commands directly in your internet browser

  ```bash
  git <cmd> --help
  ```

## BASH COMMANDS

* Check current working folder

  ```bash
  pwd
  ```

* List all files except hidden files and files starting with a "." like .gitignore

  ```bash
  ls 
  ```

* list all files

  ```bash
  ls -a
  ```

* list files with detail properties

  ```bash
  ls -l
  ```

* list in a better format

  ```bash
  ls -la
  ```

* clear the window

  ```bash
  clear
  ```

* create a directory

  ```bash
  mkdir
  ```

* change directory

  ```bash
  cd 
  ```

* create file

  ```bash
  touch <file> 
  ```

* delete file

  ```bash
  rm <file> 
  ```

  > use the option "-i" for confirmation before file deletion

* delete the command history

  ```bash
  history -c
  ```

* show environment variables

  ```bash
  printenv
  ```

* edit file

  ```bash
  vim <file> 
  ```
  
  > use the key INSERT & ESC to switch between edit mode and cmd mode
  > use the cmd <:wq> to store the file and to exit the editor

## BASIC SETTINGS BEFORE TO START

* set my username

  ```bash
  git config [option] user.name "Camille Ferrière"
  ```

* set my mail address

  ```bash
  git config [option] user.email "camille.ferriere@marquardt.com"
  ```

* change default editor to Notepad++

  ```bash
  git config --global core.editor "'C:/Program Files (x86)/Notepad++/notepad++.exe' -multiInst -notabbar -nosession -noPlugin"
  ```

* change default editor to VS-Code

  ```bash
  git config --global core.editor "code --wait"
  ```

* setup auto-correction

  ```bash
  git config --global help.autocorrect 10
  ```

* look where the configurations are coming from

  ```bash
  git config --list --show-origin
  ```

* list all config of a Git repository

  ```bash
  git config --list
  ```

* open the config file in editor for edition

  ```bash
  git config --global --edit
  ```

  > [Where are stored "system", "global" and "local" Git config files on your computer?](<https://www.theserverside.com/blog/Coffee-Talk-Java-News-Stories-and-Opinions/Where-system-global-and-local-Windows-Git-config-files-are-saved>)
  >
  >* with the option "--local", you can set these values for the specific repository, you are working on  
  **>> projectFolder\.git\config**
  >
  >* with the option "--global", you can set these values for all your repositories  
  **>> C:\Users\yourName\.gitconfig**
  >
  >* with the option "--system", you can set these values for all PC repositories  
  **>> C:\Program Files\Git\etc\gitconfig**

* [create a repository](<https://git-scm.com/docs/git-init>)

  ```bash
  git init
  ```

  > a ***.git*** hidden folder will be created !

* if you want to create a new repo. with a specific default branch

 ```bash
  git init -b <branchName>
  ```


* create a bare repository

  ```bash
  git init --bare
  ```

  > A bare repository can't be used as a working repository!!
  > It's used for sharing code and acting as a central repository.

* see the repo configuration

  ```bash
  cat .git/config
  ```

## BASIC GIT OPERATIONS

* get the [status](https://git-scm.com/docs/git-status) of the repository

  ```bash
  git status
  ```

> With the option **-s** you can get the short status

* create an empty file "test.c"

  ```bash
  touch test.c
  ```

* create an empty [".gitignore"](https://git-scm.com/docs/gitignore) file

  ```bash
  touch .gitignore
  ```

  > Add all folders/file extensions which shall be ignored in the .ignore file.  
  >
  >**.ignore file examples** are available [**here**](https://github.com/github/gitignore)
  >**.ignore file generator** is available [**here**](https://www.toptal.com/developers/gitignore)

* show available commands

  ```bash
  git help
  ```

  > With the option **-a** it will show all available commands
  > Get online help [>> here <<](https://git-scm.com/doc)

* quit a transaction in Git bash

  ```bash
  q
  ```

* [add](https://git-scm.com/docs/git-add) all files to the staging area

  ```bash
  git add .
  or
  git add -A
  ```

* add the specific file "test.c" to the staging area

  ```bash
  git add test.c
  ```

* [commit](https://git-scm.com/docs/git-commit) a file on the repository

  ```bash
  git commit -m "commit message"
  ```

* all modified files are staged and commited on the repository

  ```bash
  git commit -a -m "commit message"
  ```

* rename file

  ```bash
  git mv oldName.c newName.c
  ```

* create an empty commit

  ```bash
  git commit --allow-empty -m "empty"
  ```

## TRACK CHANGES

* see [differences](https://git-scm.com/docs/git-diff) between unstaged working file and repository file

  ```bash
  git diff
  ```

* see [differences](https://git-scm.com/docs/git-diff) between staged file and repository file

  ```bash
  git diff --staged
  ```

* see [differences](https://git-scm.com/docs/git-diff) between local file (staged and unstaged) and repository file

  ```bash
  git diff HEAD
  ```

* create a patch

  ```bash
  git diff > patchName.patch
  ```

* apply a patch

  ```bash
  git apply <patchFile>
  ```

* see the repository [history](https://git-scm.com/docs/git-log)

  ```bash
  git log
  ```

* see only the last 2 commits

  ```bash
  git log -2
  ```

  > Get a compact view of the history with the option **--oneline**  
  > Get only the history of the last two days with the option **--since="2 days ago"**  
  > Get only the history of specific author with the option **--author="camille"**

* show file modifications contained within each commit

  ```bash
  git log --stat
  ```

* show file modifications contained within each commit

  ```bash
  git log --stat
  ```

* view a condensed version of the log output

  ```bash
  git log --oneline
  ```

* show the graph history

  ```bash
  git log --oneline --decorate --graph --all
  ```

* show changes within files modified by a specific commit

  ```bash
  git show <hash>
  ```

* show the log help

  ```bash
  git help log
  ```

* who changed what and when in a file

  ```bash
  git blame <file>
  ```

* show commits in [Git GUI](https://git-scm.com/docs/git-gui)

  ```bash
  gitk --all
  ```

  > As a good practice use [**SourceTree**](https://docs.marquardt.de/x/idsAB) or **Git Graph in VS-Code**

## ALIAS

* useful alias to see the last commit (enter "*git last*")

  ```bash
  git config --global alias.last 'log -1 HEAD' 
  ```

* useful alias to unstage all files in stage area

  ```bash
  git config --global alias.unstage 'reset HEAD --'
  ```

## TAGGING

* show the [tag](https://git-scm.com/docs/git-tag) list

  ```bash
  git tag --list
  ```

* create a lightweight tag

  ```bash
  git tag <tagName> 
  ```

* create an annotated tag

  ```bash
  git tag -a <tagName> <optional: HASH code of previous commit> -m "my version 1.4" 
  ```

* show info. about a specific tag

  ```bash
  git show <tagName>
  ```

* delete a tag

  ```bash
  git tag -d <tagName>
  ```

* push tag on remote

  ```bash
  git push origin <tagName>
  ```

* generate version strings for software builds

  ```bash
  git describe
  ```

## UNDOING THINGS

  > The “git restore” command is a versatile tool in Git for discarding changes and restoring files to a previous state

* revert all changes, which are not staged

  ```bash
  git restore .
  ```

* undo the specified modifications introduced since the latest commit

  ```bash
  git restore <filename(s)>
  ```

### UNSTAGE FILES

* remove the file "test.h" from the staging area

  ```bash
  git reset test.h
  ```

  > As alternative, you can use the command "*git restore --staged test.h*"

* remove all files from the stage area = unstage all files

  ```bash
  git reset HEAD
  ```

  > As alternative, you can use the command "*git reset*" as per default it reset to the HEAD
  > As second alternative, you can use the command "*git restore --staged*".

### CHANGE COMMIT

* allow to change the last commit message or to add missing files to the last commit

  ```bash
  git commit --amend
  ```

* update the latest commit message

  ```bash
  git commit --amend -m "new commit message"
  ```

* retroactively insert staged files into the latest commit

  ```bash
  git commit --amend --no-edit
  ```

  > Refer to [How to change commit messages?](https://docs.github.com/en/pull-requests/committing-changes-to-your-project/creating-and-editing-commits/changing-a-commit-message#commit-has-not-been-pushed-online)

* [revert](https://git-scm.com/docs/git-revert) the last commit

  ```bash
  git revert HEAD
  ```

  > The revert command doesn't delete any commits. Instead, it reverts the effects of a certain commit, effectively undoing it. It does this by producing a new commit with changes that revert each of the changes in that unwanted commit. 
  >
  > Use the option "**^**" to refer to the previous commit (parent commit)
  > For example, the command "*git revert HEAD^*" will revert your work to the last commit-1

* modify an empty commit

  ```bash
  git commit --amend --allow-empty -m "bla bla…"
  ```


### REVERT COMMITTED WORK (USE CAREFULLY !!!)

* unstage all files and revert all changes

  ```bash
  git reset HEAD --hard
  ```

* undo the latest commit

  ```bash
  git reset HEAD^ or git reset HEAD~1
  ```

  > Use the option "**^**" to refer to the previous parent commit
  > Use the option "~" followed by a the number of commit you want to reset
  > For example, the command "*git reset HEAD^*" will revert your work to the last commit-1 and the deleted commits will disappear from the log
  > If you have some troubles, the "git reflog" command can help you to find the hash code of deleted commits

## BRANCHING

* show all available [branches](https://git-scm.com/docs/git-branch) on local repository

  ```bash
  git branch
  ```

  > The branch marked with a star is the active branch

* show all available branches on local repository and last commit msg

  ```bash
  git branch -v
  ```

* show all available branches on remote repository

  ```bash
  git branch -r
  ```

* show all available branches on local and remote repository

  ```bash
  git branch -a
  ```

* shows all available branches on local and remote repository + last commit msg

  ```bash
  git branch -va
  ```

* shows all available branches (local and remote repository) and last commit msg + ahead/behind information of local branch

  ```bash
  git branch -vva
  ```

* show the merged branch

  ```bash
  git branch --merged
  ```

* show the non merged branch

  ```bash
  git branch --no-merged
  ```

* create the branch xyz

  ```bash
  git branch xyz
  ```

* This command assumes you’ve already checked out the branch you’d like to rename (your local HEAD branch)

  ```bash
  git branch -m <newName>
  ```

* [switch to](<https://git-scm.com/docs/git-checkout>) a specific commit node

  ```bash
  git checkout <nodeID>
  ```

> Use the switch command, which is better than the checkout command for switching purposes in Git
>
> INFO: the switch and the restore commands were introduce in Git to **split the checkout command** !!

* switch the HEAD on the master branch

  ```bash
  git checkout master
  or
  git switch master 
  ```

* switch to the previous active branch

  ```bash
  git checkout -
  or
  git switch - 
  ```

* create the branch xyz and switch the HEAD to the branch "xyz" directly

  > **it's a very useful command !**

  ```bash
  git checkout -b xyz or git switch -c xyz
  ```

* find the common ancestor of two branches

  ```bash
  git merge-base branch1 branch2
  ```

* [merge](https://git-scm.com/docs/git-merge) the "newFeature" branch to HEAD (checkout the branch you want to merge on first!!)

  ```bash
  git merge newFeature
  ```

* [rebase](https://git-scm.com/docs/git-rebase) a branch on the master (checkout the branch to rebase first!!)

  ```bash
  git rebase master
  ```

* interactive rebase

  ```bash
  git rebase -i HEAD~<numberOfCommitToWorkOn-u>
  ```

  > P >> pick
  R >> reword
  E >> edit
  S >> squash
  F >> fixup
  X >> exec
  D >> drop
  

* delete the branch "newFeature"

  ```bash
  git branch -d newFeature
  or
  git branch -D newFeature
  ```

> Prefer to use a **powerful compare tool like "BeyondCompare"** to deal with merge conflicts  
> Follow this [link](https://www.scootersoftware.com/kb/vcs) to properly setup BeyondCompare  

* starts Beyond Compare for all conflicted files, one at a time

  ```bash
  git mergetool
  ```

* starts Beyond Compare just for the specified file

  ```bash
  git mergetool -- <file>
  ```

## STASHING

* [stash](https://git-scm.com/docs/git-stash) files in order to temporary save changes without commiting them

  ```bash
  git stash -m "message"
  ```

  > with the option "-u", untracked files are included
  > with the option "-a", all files are included

* display the list of all saved stashes

  ```bash
  git stash list
  ```

* show detailed content of a specific stash

  ```bash
  git git stash show stash@{n}
  ```

* show line-by-line changes

  ```bash
  git stash show -p stash@{n}
  ```

* apply the latest stash without removing it

  ```bash
  git stash apply
  ```

* apply a specific stash

  ```bash
  git stash apply stash@{n}
  ```

* apply the latest stash and removes it from the stack

  ```bash
  git stash pop
  ```

* apply a specific stash and removes it

  ```bash
  git stash pop stash@{n}
  ```

* remove a specific stash

  ```bash
  git stash drop stash@{n}
  ```

* remove all stashes

  ```bash
  git stash clear
  ```

## SEARCHING

* search the word "test" in the git repository files

  ```bash
  git grep -n test
  ```

## REMOTE REPOSITORY

* [clone](https://git-scm.com/docs/git-clone) a repository

  ```bash
  git clone <repository URL>
  ```

* clone in a specific directory

  ```bash
  git clone <repository_url> <new_directory_name>
  ```

* clone without creating a new folder

  ```bash
  git clone <repository_url> .
  ```

* specify the remote repository

  ```bash
  git remote add origin <repository URL>
  ```

* you can use more than one remote if required

  ```bash
  git remote set-url --add <remote name> <url>
  ```

  > If you have a local remote on your C drive, then use following URL ***<file://C:/myLocalRepo.git>***
  > If you have a remote on a network disk, then use ***<file:////netdrive_path...>***

* remove the remote repository

  ```bash
  git remote remove origin
  ```

* rename remote

  ```bash
  git remote rename <currentName> <newName>
  ```

* [push](https://git-scm.com/docs/git-push) everything to the remote repository

  ```bash
  git push <remote> <branch>
  ```

* first push in order to establish a tracking connection

  ```bash
  git push --set-upstream origin master
  ```

  > use the option "--set-upstream" or "-u" to setup a tracking connection between the local repository and the remote repository

  > default remote name = origin
  > default branch = master

* replace master through other branch on the remote

  ```bash
  git push origin otherbranch:master -f
  ```

* get everything ([fetch](https://git-scm.com/docs/git-fetch)) from the remote repository

  ```bash
  git fetch <remote> <branch>
  ```

* get a remote branch and create a corresponding local one

  ```bash
  git checkout -b <branchFromRemote> <remote>/<branchFromRemote>
  ```

* delete branch on remote

  ```bat
  git push origin --delete <branchToDelete>
  ```

* rewrite remote history

  ```bash
  git push --force-with-lease or git push --force
  ```
  
  > --force: Unconditionally overwrites the remote branch. If someone else pushed changes to the remote after your last git fetch and before your force push, their work will be lost without warning.
  
  > --force-with-lease: This is a safer alternative. It will only push if the remote branch is exactly as you last fetched it. If someone else has pushed new commits to the remote since your last fetch, git push --force-with-lease will reject the push, preventing you from unknowingly overwriting their work.

* get everything from the remote repository and try to merge ([pull](https://git-scm.com/docs/git-pull) = fetch + merge)

  ```bash
  git pull <remote> <branch>
  ```

* setup pull options

  > setup fast-forward only

  ```bash
  git config pull.ff only
  ```

  > setup merge

  ```bash
  git config pull.rebase false
  ```

  > setup rebase

  ```bash
  git config pull.rebase true
  ```

* show all remote information

  ```bash
  git remote show origin
  ```

* shows you the URLs that Git has stored for the shortname to be used when reading and writing to that remote

  ```bash
  git remote -v
  ```

## ADVANCED FEATURES

### GIT CHERRY-PICK

> Cherry-picking is a Git operation that allows you to select a specific commit from one branch and apply it to a different branch. This is in contrast to merging or rebasing, where typically a series of commits are applied together.

* integrate a commit to the current branch

  ```bash
  git cherry-pick <commit ID>
  ```

* perform a cherry-pick without automatically committing the changes

  ```bash
  git cherry-pick -n <commit ID>
  ```

### GIT WORKTREE

> Git worktree is a powerful Git feature that allows you to have multiple working directories attached to the same Git repository, each checked out to a different branch. Think of it as having several independent "sandboxes" for the same project, all sharing the underlying .git directory and object database.

* create a new worktree

  ```bash
  git worktree add <path> <branch>
  ```

* Shows a list of all worktrees associated with the current repository

  ```bash
  git worktree list
  ```

* remove a new worktree

  ```bash
  git worktree remove <worktree>
  ```

* remove any stale metadata associated with worktrees that no longer exist on the filesystem

  ```bash
  git worktree prune
  ```

### GIT SUBMODULES

> Submodule is a powerful feature in Git that allows you to embed and manage another Git repository within your main Git repository as a subdirectory. Think of it as including a separate, fully functional Git repository inside your project, allowing you to keep the history and management of that external project separate.

* add a new submodule to your repository

  ```bash
  git submodule add <repository_url> <submodule_path>
  ```
  > * <repository_url>: The URL of the Git repository you want to add as a submodule
  > * <submodule_path>: The path within your main repository where the submodule should be located.

* clone a project inclusive submodules

  ```bash
  git clone --recursive <repository URL>
  ```

* if the repository containing some submodules was clone without the recursive flag then following command shall be used to get the submodule content (otherwise the submodule folder keeps empty)

  ```bash
  git submodule update --init --recursive
  ```

  > this command shall be run from the parent repository !!

* show the checkout version of the submodule

  ```bash
  git ls-tree HEAD <submodule_name>
  ```

  > OR easier

   ```bash
  git submodule status
  ```

### GIT LFS (Large File Storage)

> Git Large File Storage (LFS) was primarily developed by GitHub.
While Git itself was created by Linus Torvalds, Git LFS is a separate extension designed to address a specific limitation of Git (handling large files), and GitHub took the lead in its creation.
It's important to note that Git LFS is an open-source project, and many individuals and organizations have contributed to its development and improvement. However, GitHub was the driving force behind its initial creation and continues to be a major contributor.

* install LFS

  ```bash
  git lfs install
  ```

* add a specific file type to LFS

  ```bash
  git lfs track *.extension
  ```

  > Don't forget to commit the .gitattributes file

### GIT Archive & Bundle

> git archive exports a specific version of project files without history, while git bundle packages commits and references for transferring repository history.

* create a .zip file of the project master branch

  ```bat
  git archive master --prefix='project/' --format=zip > 'fileName'.zip
  ```

  > with the 'prefix' option, you can add a folder in the root of the created file

  > OR

  ```bat
  git archive master --format=zip --output=../myproject.zip
  ```

* create a repository bundle

  ```bash
  git bundle create ../repo.bundle master
  ```

* verify a repository bundle

  ```bash
  git bundle verify <file> 
  ```

* clone a repository bundle

  ```bash
  git clone <file> <directory>
  ```

* pull a repository bundle in an existing repository

  ```bash
  git pull <file> <refspec>
  ```

> refspec: Specifies which branches or tags from the bundle you want to fetch or merge.
If omitted, Git will try to fetch all of them.

### GIT HOOKS

> Git hooks are scripts that Git executes automatically whenever a particular event occurs in a repository.
> They let you customize Git's internal behavior and trigger actions at key points in the development life cycle.
>
> Hook file samples are available in the **.git/hooks folder**
>
> Remove the extension "**.sample**" to make it usable
>
> Modify the concerned hook file according to your requirements

* Activate the pre-commit hook

  ```bash
  chmod +x .git/hooks/pre-commit
  ```

* You can bypass hooks for a single commit by using the --no-verify option

  ```bash
  git commit --no-verify -m "Your commit message"
  ```

> If you want to remove an hook, then just rename the corresponding hook file or remove it from the hook folder !
>
> You can use the extension "**.disable**" if you want to keep the hook file

* Deactivate the pre-commit hook

  ```bash
  chmod -x .git/hooks/pre-commit
  ```

### GIT MISC

#### Special commits

* create an empty commit

  ```bash
  git commit --allow-empty -m "empty
  ```

* modify an empty commit

  ```bash
  git commit --amend --allow-empty -m "bla bla…“
  ```

#### Special functions

* create an orphan commit

  ```bash
  git checkout --orphan im_lonely
  ```

* inspect the contents of Git objects directly

  ```bash
  git cat-file –p <object/HASH>
  ```

* download a specific file from a remote repository

  ```bash
  curl –o <file> <URL_rawData>
  ```

  > * Browse to the file on the Git hosting platform
  > * Click on the "Raw" button. This will open the raw content of the file in your browser
  > * Copy the URL (URL_rawData) from your browser's address bar

* remove all untracked files and directories

  ```bash
  git clean -fdx
  ```

* perform garbage collection

  ```bash
  git gc
  ```

* check repository objects integrity

  ```bash
  git fsck
  ```

## COMMON GIT [WORKFLOW](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow)

### create a [branch](<https://confluence.atlassian.com/bitbucketserver0721/branches-1115665710.html?utm_campaign=in-app-help&utm_medium=in-app-help&locale=de_DE%2Cde&utm_source=stash>) for desired feature

  ```bat
  git branch CRxxx
  git checkout CRxxx
  ```

* Visualize on which branch you are working on

  ```bat
  git branch  
  ```

  > the star show you on which branch you are working on (HEAD)

### after modifications

* commit and push branch to remote

  ```bat
  git push -u origin CRxxx
  ```

  > the "-u" is used to establish a tracked connection

* verify that the push has worked

  ```bat
  git branch -a >> 
  ```

### merge a branch

  ```bat
  git checkout master
  git pull origin master
  git branch --merged
  git merge CRxxx
  git push origin master
  ```

### deleting a branch

* check if everything is merged

  ```bat
  git branch --merged
  ```

* delete branch locally

  ```bat
  git branch -d CRxxx
  ```

* show all branches

  ```bat
  git branch -a
  ```

* delete branch on remote

  ```bat
  git push origin --delete CRxxx
  ```

## PREPARING RELEASE

* refer to [git archive](#git-archive--bundle)

* create a short log for release note

  ```bat
  git shortlog --no-merges master --not v1.1
  ```

* generate a build number

  ```bat
  git describe master
  ```

## MISCELLANEOUS

### Secure connection (SSH)

* create an SSH key pair

  ```bat
  ssh-keygen -t ed25519 -C "Key_label"
  ```

  > the -t is used to specified the encryption algorithm used for the key generation
  >> rsa: A widely used and traditional algorithm
  >> ed25519: A newer, more secure, and faster alternative based on elliptic-curve cryptography.

  > The -C option is used to provide a comment for the key

* test the SSH connection

  ```bat
  ssh -T <host address>
  ```
