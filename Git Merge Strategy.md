# Git Merge Strategy Options and Examples

`When a piece of work is complete, tested and ready to be merged back into the main line of development, your team has some policy choices to make. What are your merge strategy options? In this article we'll examine the possibilities and then provide some notes on how Atlassian operates. Hopefully at the end you'll have the tools to decide what works best for your team.`

### Git Merge Strategies

`A merge happens when combining two branches. Git will take two (or more) commit pointers and attempt to find a common base commit between them. Git has several different methods to find a base commit, these methods are called "merge strategies". Once Git finds a common base commit it will create a new "merge commit" that combines the changes of the specified merge commits. Technically, a merge commit is a regular commit which just happens to have two parent commits.`

<img src="https://wac-cdn.atlassian.com/dam/jcr:2d3aef7f-6e1d-4e39-a5a5-97dd7714fdd2/what-is-a-merge.gif?cdnVersion=1123"/>

`git merge will automatically select a merge strategy unless explicitly specified. The git merge and git pull commands can be passed an -s (strategy) option. The -s option can be appended with the name of the desired merge strategy. If not explicitly specified, Git will select the most appropriate merge strategy based on the provided branches. The following is a list of the available merge strategies.`

### Recursive

**git merge -s recursive branch1 branch2**

`This operates on two heads. Recursive is the default merge strategy when pulling or merging one branch. Additionally this can detect and handle merges involving renames, but currently cannot make use of detected copies. This is the default merge strategy when pulling or merging one branch.`

### Resolve

**git merge -s resolve branch1 branch2**

`This can only resolve two heads using a 3-way merge algorithm. It tries to carefully detect cris-cross merge ambiguities and is considered generally safe and fast.`

### Octopus

**git merge -s octopus branch1 branch2 branch3 branchN**

`The default merge strategy for more than two heads. When more than one branch is passed octopus is automatically engaged. If a merge has conflicts that need manual resolution octopus will refuse the merge attempt. It is primarily used for bundling similar feature branch heads together.`

### Ours

**git merge -s ours branch1 branch2 branchN**

`The Ours strategy operates on multiple N number of branches. The output merge result is always that of the current branch HEAD. The "ours" term implies the preference effectively ignoring all changes from all other branches. It is intended to be used to combine history of similar feature branches.`

### Subtree

**git merge -s subtree branchA branchB**

`This is an extension of the recursive strategy. When merging A and B, if B is a child subtree of A, B is first updated to reflect the tree structure of A, This update is also done to the common ancestor tree that is shared between A and B.`
