# Git Status command in git

### Git Status: Inspecting a repository

`The git status command displays the state of the working directory and the staging area. It lets you see which changes have been staged, which haven’t, and which files aren’t being tracked by Git. Status output does not show you any information regarding the committed project history. For this, you need to use git log.`

### Usage

<pre><code class="hljs ebnf"><span class="hljs-attribute">git status</span></code></pre>

`List which files are staged, unstaged, and untracked.`

### Discussion
`The git status command is a relatively straightforward command. It simply shows you what's been going on with git add and git commit. Status messages also include relevant instructions for staging/unstaging files. Sample output showing the three main categories of a git status call is included below:`

<pre><code class="hljs shell"><span class="hljs-meta">#</span><span class="bash"> On branch master</span>
<span class="hljs-meta">#</span><span class="bash"> Changes to be committed:</span>
<span class="hljs-meta">#</span><span class="bash"> (use <span class="hljs-string">"git reset HEAD &lt;file&gt;..."</span> to unstage)</span>
<span class="hljs-meta">#</span><span class="bash"></span>
<span class="hljs-meta">#</span><span class="bash">modified: hello.py</span>
<span class="hljs-meta">#</span><span class="bash"></span>
<span class="hljs-meta">#</span><span class="bash"> Changes not staged <span class="hljs-keyword">for</span> commit:</span>
<span class="hljs-meta">#</span><span class="bash"> (use <span class="hljs-string">"git add &lt;file&gt;..."</span> to update what will be committed)</span>
<span class="hljs-meta">#</span><span class="bash"> (use <span class="hljs-string">"git checkout -- &lt;file&gt;..."</span> to discard changes <span class="hljs-keyword">in</span> working directory)</span>
<span class="hljs-meta">#</span><span class="bash"></span>
<span class="hljs-meta">#</span><span class="bash">modified: main.py</span>
<span class="hljs-meta">#</span><span class="bash"></span>
<span class="hljs-meta">#</span><span class="bash"> Untracked files:</span>
<span class="hljs-meta">#</span><span class="bash"> (use <span class="hljs-string">"git add &lt;file&gt;..."</span> to include <span class="hljs-keyword">in</span> what will be committed)</span>
<span class="hljs-meta">#</span><span class="bash"></span>
<span class="hljs-meta">#</span><span class="bash">hello.pyc</span></code></pre>

**Ignoring Files**

`Untracked files typically fall into two categories. They're either files that have just been added to the project and haven't been committed yet, or they're compiled binaries like .pyc, .obj, .exe, etc. While it's definitely beneficial to include the former in the git status output, the latter can make it hard to see what’s actually going on in your repository.`

`For this reason, Git lets you completely ignore files by placing paths in a special file called .gitignore. Any files that you'd like to ignore should be included on a separate line, and the * symbol can be used as a wildcard. For example, adding the following to a .gitignore file in your project root will prevent compiled Python modules from appearing in git status:`
<pre><code class="hljs css">*<span class="hljs-selector-class">.pyc</span></code></pre>

### Example
`It's good practice to check the state of your repository before committing changes so that you don't accidentally commit something you don't mean to. This example displays the repository status before and after staging and committing a snapshot:`

<pre><code class="hljs shell"><span class="hljs-meta">#</span><span class="bash"> Edit hello.py</span>
git status
<span class="hljs-meta">#</span><span class="bash"> hello.py is listed under <span class="hljs-string">"Changes not staged for commit"</span></span>
git add hello.py
git status
<span class="hljs-meta">#</span><span class="bash"> hello.py is listed under <span class="hljs-string">"Changes to be committed"</span></span>
git commit
git status
<span class="hljs-meta">#</span><span class="bash"> nothing to commit (working directory clean)</span></code></pre>

`The first status output will show the file as unstaged. The git add action will be reflected in the second git status, and the final status output will tell you that there is nothing to commit—the working directory matches the most recent commit. Some Git commands (e.g., git merge) require the working directory to be clean so that you don't accidentally overwrite changes.`
