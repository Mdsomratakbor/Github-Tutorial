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
