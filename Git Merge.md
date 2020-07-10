# Git Merge
 
 `Merging is Git's way of putting a forked history back together again. The git merge command lets you take the independent lines of development created by git branch and integrate them into a single branch.`

`Note that all of the commands presented below merge into the current branch. The current branch will be updated to reflect the merge, but the target branch will be completely unaffected. Again, this means that git merge is often used in conjunction with git checkout for selecting the current branch and git branch -d for deleting the obsolete target branch.`

### How it works

`Git merge will combine multiple sequences of commits into one unified history. In the most frequent use cases, git merge is used to combine two branches. The following examples in this document will focus on this branch merging pattern. In these scenarios, git merge takes two commit pointers, usually the branch tips, and will find a common base commit between them. Once Git finds a common base commit it will create a new "merge commit" that combines the changes of each queued merge commit sequence.`

`Say we have a new branch feature that is based off the master branch. We now want to merge this feature branch into master.`

<img src="https://wac-cdn.atlassian.com/dam/jcr:86eba9ec-9391-45ea-800a-948cec1f2ed7/Branch-2.png?cdnVersion=1118"/>

`Invoking this command will merge the specified branch feature into the current branch, we'll assume master. Git will determine the merge algorithm automatically (discussed below).`

<img src="https://wac-cdn.atlassian.com/dam/jcr:83323200-3c57-4c29-9b7e-e67e98745427/Branch-1.png?cdnVersion=1118"/>

`Merge commits are unique against other commits in the fact that they have two parent commits. When creating a merge commit Git will attempt to auto magically merge the separate histories for you. If Git encounters a piece of data that is changed in both histories it will be unable to automatically combine them. This scenario is a version control conflict and Git will need user intervention to continue. `

### Preparing to merge

`Before performing a merge there are a couple of preparation steps to take to ensure the merge goes smoothly.`

### Confirm the receiving branch

`Execute git status to ensure that HEAD is pointing to the correct merge-receiving branch. If needed, execute git checkout <receiving> to switch to the receiving branch. In our case we will execute git checkout master.`

### Fetch latest remote commits

`Make sure the receiving branch and the merging branch are up-to-date with the latest remote changes. Execute git fetch to pull the latest remote commits. Once the fetch is completed ensure the master branch has the latest updates by executing git pull.`

### Merging

`Once the previously discussed "preparing to merge" steps have been taken a merge can be initiated by executing git merge <branch name> where <branch name> is the name of the branch that will be merged into the receiving branch.`

### Fast Forward Merge

`A fast-forward merge can occur when there is a linear path from the current branch tip to the target branch. Instead of “actually” merging the branches, all Git has to do to integrate the histories is move (i.e., “fast forward”) the current branch tip up to the target branch tip. This effectively combines the histories, since all of the commits reachable from the target branch are now available through the current one. For example, a fast forward merge of some-feature into master would look something like the following:`

<img src="https://wac-cdn.atlassian.com/dam/jcr:b87df050-2a3a-4f17-bb80-43c5217b4947/07%20(1).svg?cdnVersion=1118" loading="lazy" alt="">

`While you can use either of these merge strategies, many developers like to use fast-forward merges (facilitated through rebasing) for small features or bug fixes, while reserving 3-way merges for the integration of longer-running features. In the latter case, the resulting merge commit serves as a symbolic joining of the two branches.`

`Our first example demonstrates a fast-forward merge. The code below creates a new branch, adds two commits to it, then integrates it into the main line with a fast-forward merge.`

**`# Start a new feature`

**`git checkout -b new-feature master`**

**`# Edit some files`**

**`git add <file>`**

**`git commit -m "Start a feature"`**

**`# Edit some files`**

**`git add <file>`**

**`git commit -m "Finish a feature"`**

**`# Merge in the new-feature branch`**

**`git checkout master`**

**`git merge new-feature`**

**`git branch -d new-feature`**

`This is a common workflow for short-lived topic branches that are used more as an isolated development than an organizational tool for longer-running features.`

`Also note that Git should not complain about the git branch -d, since new-feature is now accessible from the master branch.`

`In the event that you require a merge commit during a fast forward merge for record keeping purposes you can execute git merge with the --no-ffoption.`

**git merge --no-ff "branch"**

`This command merges the specified branch into the current branch, but always generates a merge commit (even if it was a fast-forward merge). This is useful for documenting all merges that occur in your repository.`

### 3-way merge

`The next example is very similar, but requires a 3-way merge because master progresses while the feature is in-progress. This is a common scenario for large features or when several developers are working on a project simultaneously.`

- `Start a new feature`
- `git checkout -b new-feature master`
- `# Edit some files`
- `git add <file>`
- `git commit -m "Start a feature"`
- `# Edit some files`
- `git add <file>`
- `git commit -m "Finish a feature"`
- `# Develop the master branch`
- `git checkout master`
- `# Edit some files`
- `git add <file>`
- `git commit -m "Make some super-stable changes to master"`
- `# Merge in the new-feature branch
- `git merge new-feature`
- `git branch -d new-feature`

`Note that it’s impossible for Git to perform a fast-forward merge, as there is no way to move master up to new-feature without backtracking.`

`For most workflows, new-feature would be a much larger feature that took a long time to develop, which would be why new commits would appear on master in the meantime. If your feature branch was actually as small as the one in the above example, you would probably be better off rebasing it onto master and doing a fast-forward merge. This prevents superfluous merge commits from cluttering up the project history.`

### Resolving conflict
`If the two branches you're trying to merge both changed the same part of the same file, Git won't be able to figure out which version to use. When such a situation occurs, it stops right before the merge commit so that you can resolve the conflicts manually.`

`The great part of Git's merging process is that it uses the familiar edit/stage/commit workflow to resolve merge conflicts. When you encounter a merge conflict, running the git status command shows you which files need to be resolved. For example, if both branches modified the same section of hello.py, you would see something like the following:`

<pre><code class="hljs vim">On branch master
Unmerged path<span class="hljs-variable">s:</span>
(use <span class="hljs-string">"git add/rm ..."</span> <span class="hljs-keyword">as</span> appropriate <span class="hljs-keyword">to</span> <span class="hljs-keyword">mark</span> resolution)
both modified: hello.<span class="hljs-keyword">py</span>
</code></pre>

### How conflicts are presented

`When Git encounters a conflict during a merge, It will edit the content of the affected files with visual indicators that mark both sides of the conflicted content. These visual markers are: <<<<<<<, =======, and >>>>>>>. Its helpful to search a project for these indicators during a merge to find where conflicts need to be resolved.`
<pre><code class="hljs applescript">here <span class="hljs-keyword">is</span> <span class="hljs-keyword">some</span> content <span class="hljs-keyword">not</span> affected <span class="hljs-keyword">by</span> <span class="hljs-keyword">the</span> conflict
&lt;&lt;&lt;&lt;&lt;&lt;&lt; master
this <span class="hljs-keyword">is</span> conflicted <span class="hljs-built_in">text</span> <span class="hljs-keyword">from</span> master
=======
this <span class="hljs-keyword">is</span> conflicted <span class="hljs-built_in">text</span> <span class="hljs-keyword">from</span> feature branch
</code><span style="font-family: sans-serif, Arial, Verdana, &quot;Trebuchet MS&quot;;">&gt;&gt;&gt;&gt;&gt;&gt;&gt; feature branch</span>;</pre>

`Generally the content before the ======= marker is the receiving branch and the part after is the merging branch.`

`Once you've identified conflicting sections, you can go in and fix up the merge to your liking. When you're ready to finish the merge, all you have to do is run git add on the conflicted file(s) to tell Git they're resolved. Then, you run a normal git commit to generate the merge commit. It’s the exact same process as committing an ordinary snapshot, which means it’s easy for normal developers to manage their own merges.`

`Note that merge conflicts will only occur in the event of a 3-way merge. It’s not possible to have conflicting changes in a fast-forward merge. `

### Summary
`This document is an overview of the git merge command. Merging is an essential process when working with Git. We discussed the internal mechanics behind a merge and the differences between a fast forward merge and a three way, true merge. Some key take-aways are:`
 

- `Git merging combines sequences of commits into one unified history of commits.`
- `There are two main ways Git will merge: Fast Forward and Three way.`
- `Git can automatically merge commits unless there are changes that conflict in both commit sequences.`
- `This document integrated and referenced other Git commands like: git branch, git pull, and git fetch. Visit their corresponding stand-alone pages for more information. `
