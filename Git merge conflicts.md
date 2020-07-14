# Git merge conflicts

`Version control systems are all about managing contributions between multiple distributed authors ( usually developers ). Sometimes multiple developers may try to edit the same content. If Developer A tries to edit code that Developer B is editing a conflict may occur. To alleviate the occurrence of conflicts developers will work in separate isolated branches. The git merge command's primary responsibility is to combine separate branches and resolve any conflicting edits.`

### Understanding merge conflicts

`Merging and conflicts are a common part of the Git experience. Conflicts in other version control tools like SVN can be costly and time-consuming. Git makes merging super easy. Most of the time, Git will figure out how to automatically integrate new changes.`

`Conflicts generally arise when two people have changed the same lines in a file, or if one developer deleted a file while another developer was modifying it. In these cases, Git cannot automatically determine what is correct. Conflicts only affect the developer conducting the merge, the rest of the team is unaware of the conflict. Git will mark the file as being conflicted and halt the merging process. It is then the developers' responsibility to resolve the conflict.`


### Types of merge conflicts

`A merge can enter a conflicted state at two separate points. When starting and during a merge process. The following is a discussion of how to address each of these conflict scenarios.`

**Git fails to start the merge**

`A merge will fail to start when Git sees there are changes in either the working directory or staging area of the current project. Git fails to start the merge because these pending changes could be written over by the commits that are being merged in. When this happens, it is not because of conflicts with other developer's, but conflicts with pending local changes. The local state will need to be stabilized using git stash, git checkout, git commit or git reset. A merge failure on start will output the following error message:`

**error: Entry 'fileName' not uptodate. Cannot merge. (Changes in working directory)**

**Git fails during the merge**

`A failure DURING a merge indicates a conflict between the current local branch and the branch being merged. This indicates a conflict with another developers code. Git will do its best to merge the files but will leave things for you to resolve manually in the conflicted files. A mid-merge failure will output the following error message:`

**error: Entry 'fileName' would be overwritten by merge. Cannot merge. (Changes in staging area)**

### Creating a merge conflict

`In order to get real familiar with merge conflicts, the next section will simulate a conflict to later examine and resolve. The example will be using a Unix-like command-line Git interface to execute the example simulation.`

**`$ mkdir git-merge-test`**</br>
**`$ cd git-merge-test`**</br>
**`$ git init .`**</br>
**`$ echo "this is some content to mess with" > merge.txt`**</br>
**`$ git add merge.txt`**</br>
**`$ git commit -am"we are commiting the inital content"`**</br>
**`[master (root-commit) d48e74c] we are commiting the inital content`**</br>
**`1 file changed, 1 insertion(+)`**</br>
**`create mode 100644 merge.txt**`**</br>
