# Git log commdand in git

### git log
`The git log command displays committed snapshots. It lets you list the project history, filter it, and search for specific changes. While git status lets you inspect the working directory and the staging area, git log only operates on the committed history.`

<img src="https://wac-cdn.atlassian.com/dam/jcr:52d530ce-7f51-48e3-920b-a18f776048d3/01.svg?cdnVersion=1109" alt="Git Tutorial: git status vs. git log" class="lozad">

`Log output can be customized in several ways, from simply filtering commits to displaying them in a completely user-defined format. Some of the most common configurations of git log are presented below.`

### Usage
<pre><code class="hljs 1c">git <span class="hljs-built_in">log</span></code></pre>

`Display the entire commit history using the default formatting. If the output takes up more than one screen, you can use Space to scroll and q to exit.`
**git log -n "limit"**

`Limit the number of commits by <limit>. For example, git log -n 3 will display only 3 commits.`

**git log --oneline**

`Condense each commit to a single line. This is useful for getting a high-level overview of the project history.`

**git log --stat**
Along with the ordinary git log information, include which files were altered and the relative number of lines that were added or deleted from each of them.
