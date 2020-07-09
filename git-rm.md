# Git RM

### Why use git rm command in git?
`A common question when getting started with Git is "How do I tell Git not to track a file (or files) any more?" The git rm command is used to remove files from a Git repository. It can be thought of as the inverse of the git add command.`

### Git rm Overview
`The git rm command can be used to remove individual files or a collection of files. The primary function of git rm is to remove tracked files from the Git index. Additionally, git rm can be used to remove files from both the staging index and the working directory. There is no option to remove a file from only the working directory. The files being operated on must be identical to the files in the current HEAD. If there is a discrepancy between the HEAD version of a file and the staging index or working tree version, Git will block the removal. This block is a safety mechanism to prevent removal of in-progress changes.`

### Usage

**"file"…​**

`Specifies the target files to remove. The option value can be an individual file, a space delimited list of files file1 file2 file3, or a wildcard file glob (~./directory/*).`

**-f**
**--force**

`The -foption is used to override the safety check that Git makes to ensure that the files in HEAD match the current content in the staging index and working directory.`

**-n**
**--dry-run**

`The "dry run" option is a safeguard that will execute the git rm command but not actually delete the files. Instead it will output which files it would have removed.`

**-r**

`The -r option is shorthand for 'recursive'. When operating in recursive mode git rm will remove a target directory and all the contents of that directory.`

**--**

`The separator option is used to explicitly distinguish between a list of file names and the arguments being passed to git rm. This is useful if some of the file names have syntax that might be mistaken for other options.`

**--cached**

`The cached option specifies that the removal should happen only on the staging index. Working directory files will be left alone.`

**--ignore-unmatch**

`This causes the command to exit with a 0 sigterm status even if no files matched. This is a Unix level status code. The code 0 indicates a successful invocation of the command. The --ignore-unmatch option can be helpful when using git rm as part of a greater shell script that needs to fail gracefully.`

**-q**
**-quiet**

`The quiet option hides the output of the git rm command. The command normally outputs one line for each file removed.`

### The scope of git rm

`The git rm command operates on the current branch only. The removal event is only applied to the working directory and staging index trees. The file removal is not persisted to the repository history until a new commit is created.`

### Why use git rm instead of rm

`A Git repository will recognize when a regular shell rm command has been executed on a file it is tracking. It will update the working directory to reflect the removal. It will not update the staging index with the removal. An additional git add command will have to be executed on the removed file paths to add the changes to the staging index. The git rm command acts a shortcut in that it will update the working directory and the staging index with the removal.`

### How to remove files no longer in the filesystem

`As stated above in "Why use git rm instead of rm" , git rm is actually a convenience command that combines the standard shell rm and git add to remove a file from the working directory and promote that removal to the staging index. A repository can get into a cumbersome state in the event that several files have been removed using only the standard shell rm command.`

`If intentions are to record all the explicitly removed files as part of the next commit, git commit -a will add all the removal events to the staging index in preparation of the next commit.`

`If however, intentions are to persistently remove the files that were removed with the shell rm, use the following command:`

**git diff --name-only --diff-filter=D -z | xargs -0 git rm --cached**

`This command will generate a list of the removed files from the working directory and pipe that list to git rm --cached which will update the staging index.`
