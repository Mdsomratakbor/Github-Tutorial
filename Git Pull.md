# git pull

`The git pull command is used to fetch and download content from a remote repository and immediately update the local repository to match that content. Merging remote upstream changes into your local repository is a common task in Git-based collaboration work flows. The git pull command is actually a combination of two other commands, git fetch followed by git merge. In the first stage of operation git pull will execute a git fetch scoped to the local branch that HEAD is pointed at. Once the content is downloaded, git pull will enter a merge workflow. A new merge commit will be-created and HEAD updated to point at the new commit.`

### Git pull usage

**How it works**

`The git pull command first runs git fetch which downloads content from the specified remote repository. Then a git merge is executed to merge the remote content refs and heads into a new local merge commit. To better demonstrate the pull and merging process let us consider the following example. Assume we have a repository with a master branch and a remote origin.`

<img src="https://wac-cdn.atlassian.com/dam/jcr:00d011ed-03dc-440f-afc5-9b13d5e14fbf/bubble%20diagram-01.svg?cdnVersion=1109" alt="" class="lozad">

`In this scenario, git pull will download all the changes from the point where the local and master diverged. In this example, that point is E. git pull will fetch the diverged remote commits which are A-B-C. The pull process will then create a new local merge commit containing the content of the new diverged remote commits.`

<img src="https://wac-cdn.atlassian.com/dam/jcr:b3a663dc-1985-40df-b0a5-c6bcbacd71af/bubble%20diagram-02.svg?cdnVersion=1109" alt="" class="lozad">

In the above diagram, we can see the new commit H. This commit is a new merge commit that contains the contents of remote A-B-C commits and has a combined log message. This example is one of a few git pull merging strategies. A --rebase option can be passed to git pull to use a rebase merging strategy instead of a merge commit. The next example will demonstrate how a rebase pull works. Assume that we are at a starting point of our first diagram, and we have executed git pull --rebase.

### Common Options

**git pull "remote"**

`Fetch the specified remote’s copy of the current branch and immediately merge it into the local copy. This is the same as git fetch <remote> followed by git merge origin/<current-branch>.`

**git pull --no-commit "remote"**

`Similar to the default invocation, fetches the remote content but does not create a new merge commit.`

**git pull --rebase "remote"**

`Same as the previous pull Instead of using git merge to integrate the remote branch with the local one, use git rebase.`

**git pull --verbose**

`Gives verbose output during a pull which displays the content being downloaded and the merge details.`

### Git pull discussion

You can think of git pull as Git's version of svn update. It’s an easy way to synchronize your local repository with upstream changes. The following diagram explains each step of the pulling process.

<img src="https://wac-cdn.atlassian.com/dam/jcr:60943ee2-bec2-4433-8216-885c4bd3c2b9/03.svg?cdnVersion=1123"/>
