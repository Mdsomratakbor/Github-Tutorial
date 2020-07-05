# git commit

### What does it mean to commit in git?
`git github git-commit. commit is. A commit, or "revision", is an individual change to a file (or set of files). It's like when you save a file, except with Git, every time you save it creates a unique ID (a.k.a. the "SHA" or "hash") that allows you to keep record of what changes were made when and by who`

### What is git Commit in git?
`The "commit" command is used to save your changes to the local repository.`

`Note that you have to explicitly tell Git which changes you want to include in a commit before running the "git commit" command. This means that a file won't be automatically included in the next commit just because it was changed. Instead, you need to use the "git add" command to mark the desired changes for inclusion.`

`Also note that in Git (not like in Subversion), a commit is not automatically transferred to the remote server. Using the "git commit" command only saves a new commit object in the local Git repository. Exchanging commits has to be performed manually and explicitly (with the "git fetch", "git pull", and "git push" commands).`

### Important Options

### -m "message"
`Sets the commit's message. Make sure to provide a concise description that helps your teammates (and yourself) understand what happened.`

### -a
`Includes all currently changed files in this commit. Keep in mind, however, that untracked (new) files are not included.`

### --amend
`Rewrites the very last commit with any currently staged changes and/or a new commit message. Git will rewrite the last commit and effectively replace it with the amended one. Note that such a rewriting of commits should only be performed on commits that have not been pushed to a remote repository, yet.`

### Usage Examples
<hr>

**For a basic workflow, you can use the "git add" command to stage changes for the next commit. The actual commit command will then wrap up the mentioned changes in a new commit object:**

<pre><code>git add index.html css/styles.css
git commit -m "Change titles and styling on homepage"</code></pre>
`If you have lots of changed files in your working copy - and want all of them included in the next commit - you can make use of the "-a" parameter and thereby omit the "git add" step:`
<pre><code>git commit -a -m "Change titles and styling on homepage"</code></pre>

`The "--amend" option comes in handy, for example, when you mistyped the last commit's message or forgot to add a change. The following example will correct the very last commit by overwriting its message and adding another change:`

<pre><code>git add forgotten-change.js
git commit --amend -m "New commit message"</code></pre>
