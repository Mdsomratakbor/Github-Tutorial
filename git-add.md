# git add Command in git

### What is git add Command in git?

`The git add is a command, which adds changes in the working directory to the staging area. With the help of this command, you tell Git that you want to add updates to a certain file in the next commit. But in order to record changes, you need to run git commit too. In combination with the commands mentioned above, git status command is also needed to see which state the working directory and the staging area are in.`

<img src="https://www.w3docs.com/uploads/media/default/0001/03/ad19114d2f18ae7f7e8b99a5110d1a2f339282c6.png"/>

### Working principles

`The git add, along with git commit are used to record project versions into the history of the repository. They are must-know for every Git user, as they compose the basis of Git workflow.`
`While developing a project, you first edit the files in the working directory, then when a copy of the current state is ready to save, you need to stage changes, which is done with the git add command. The git add command should be called every time altering a file.`
### Working principles
`The git add, along with git commit are used to record project versions into the history of the repository. They are must-know for every Git user, as they compose the basis of Git workflow.`

`While developing a project, you first edit the files in the working directory, then when a copy of the current state is ready to save, you need to stage changes, which is done with the git add command. The git add command should be called every time altering a file.`
### Common options

**Staging changes in "file" for the next commit:**
<pre content="code snippet"><code class="hljs makefile">git <span class="hljs-keyword">add</span><span class="bash"> &lt;file&gt;</span></code></pre>

**Staging all changes in "directory" for the next commit**
<pre content="code snippet"><code class="hljs makefile">git <span class="hljs-keyword">add</span><span class="bash"> -p</span></code></pre>

<pre>y - stage this hunk
n - do not stage this hunk
q - quit; do not stage this hunk or any of the remaining ones
a - stage this hunk and all later hunks in the file
d - do not stage this hunk or any of the later hunks in the file
g - select a hunk to go to
/ - search for a hunk matching the given regex
j - leave this hunk undecided, see next undecided hunk
J - leave this hunk undecided, see next hunk
k - leave this hunk undecided, see previous undecided hunk
K - leave this hunk undecided, see previous hunk
s - split the current hunk into smaller hunks
e - manually edit the current hunk
? - print help</pre>
