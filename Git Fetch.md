# Git Fetch

`The git fetch command downloads commits, files, and refs from a remote repository into your local repo. Fetching is what you do when you want to see what everybody else has been working on. It’s similar to svn update in that it lets you see how the central history has progressed, but it doesn’t force you to actually merge the changes into your repository. Git isolates fetched content as a from existing local content, it has absolutely no effect on your local development work. Fetched content has to be explicitly checked out using the git checkout command. This makes fetching a safe way to review commits before integrating them with your local repository.`

`When downloading content from a remote repo, git pull and git fetch commands are available to accomplish the task. You can consider git fetch the 'safe' version of the two commands. It will download the remote content but not update your local repo's working state, leaving your current work intact. git pull is the more aggressive alternative, it will download the remote content for the active local branch and immediately execute git merge to create a merge commit for the new remote content. If you have pending changes in progress this will cause conflicts and kickoff the merge conflict resolution flow.`

### How git fetch works with remote branches

`To better understand how git fetch works let us discuss how Git organizes and stores commits. Behind the scenes, in the repository's ./.git/objects directory, Git stores all commits, local and remote. Git keeps remote and local branch commits distinctly separate through the use of branch refs. The refs for local branches are stored in the ./.git/refs/heads/. Executing the git branch command will output a list of the local branch refs. The following is an example of git branch output with some demo branch names.`

**git branch</br>
master</br>
feature1</br>
debug2**

`Examining the contents of the /.git/refs/heads/ directory would reveal similar output.`

**ls ./.git/refs/heads/</br>
master</br>
feature1</br>
debug2**

`Remote branches are just like local branches, except they map to commits from somebody else’s repository. Remote branches are prefixed by the remote they belong to so that you don’t mix them up with local branches. Like local branches, Git also has refs for remote branches. Remote branch refs live in the ./.git/refs/remotes/ directory. The next example code snippet shows the branches you might see after fetching a remote repo named conveniently named remote-repo:`\

**git branch -r</br>
`# origin/master`</br>
`# origin/feature1`</br>
`# origin/debug2`</br>
`# remote-repo/master`</br>
`# remote-repo/other-feature`**

`This output displays the local branches we had previously examined but now displays them prefixed with origin/. Additionally, we now see the remote branches prefixed with remote-repo. You can check out a remote branch just like a local one, but this puts you in a detached HEAD state (just like checking out an old commit). You can think of them as read-only branches. To view your remote branches, simply pass the -r flag to the git branch command.`

`You can inspect remote branches with the usual git checkout and git log commands. If you approve the changes a remote branch contains, you can merge it into a local branch with a normal git merge. So, unlike SVN, synchronizing your local repository with a remote repository is actually a two-step process: fetch, then merge. The git pull command is a convenient shortcut for this process.`

### Git fetch commands and options

**git fetch "remote"**

`Fetch all of the branches from the repository. This also downloads all of the required commits and files from the other repository.`

**git fetch "remote" "branch"**

`Same as the above command, but only fetch the specified branch.`

**git fetch --all**

`A power move which fetches all registered remotes and their branches:`

**git fetch --dry-run**

`The --dry-run option will perform a demo run of the command. I will output examples of actions it will take during the fetch but not apply them.`
### Git fetch examples
### git fetch a remote branch


### Git fetch summary

`In review, git fetch is a primary command used to download contents from a remote repository. git fetch is used in conjunction with git remote, git branch, git checkout, and git reset to update a local repository to the state of a remote. The git fetch command is a critical piece of collaborative git work flows. git fetch has similar behavior to git pull however git fetch can be considered a safer, nondestructive version.`
