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
