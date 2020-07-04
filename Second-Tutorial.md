# Configuring git on windows

### git clone
`Here we'll examine the git clone command in depth. git clone is a Git command line utility which is used to target an existing repository and create a clone, or copy of the target repository. In this page we'll discuss extended configuration options and common use cases of git clone. Some points we'll cover here are:`

- `Cloning a local or remote repository`
- `Cloning a bare repository`
- `Using shallow options to partially clone repositories`
- `Git URL syntax and supported protocols`
- `On the setting up a repository guide, we covered a basic use case of git clone. This page will explore more complex cloning and configuration scenarios.`

### Purpose: repo-to-repo collaboration development copy

`If a project has already been set up in a central repository, the git clone command is the most common way for users to obtain a development copy. Like git init, cloning is generally a one-time operation. Once a developer has obtained a working copy, all version control operations and collaborations are managed through their local repository.`

### Repo-to-repo collaboration
It’s important to understand that Git’s idea of a “working copy” is very different from the working copy you get by checking out code from an SVN repository. Unlike SVN, Git makes no distinction between the working copy and the central repository—they're all full-fledged Git repositories.

This makes collaborating with Git fundamentally different than with SVN. Whereas SVN depends on the relationship between the central repository and the working copy, Git’s collaboration model is based on repository-to-repository interaction. Instead of checking a working copy into SVN’s central repository, you push or pull commits from one repository to another.

<img src="https://wac-cdn.atlassian.com/dam/jcr:e5228129-76b1-4b2c-8f10-af789f2ea6c0/03.svg?cdnVersion=1109" alt="Git Tutorial: Repo to Working Copy Collaboration" class="lozad">

<img src="https://wac-cdn.atlassian.com/dam/jcr:5d68ce55-59a7-4840-a896-eb2014a9f17b/02.svg?cdnVersion=1109" alt="Git Tutorial: Repo to Repo Collaboration" class="lozad">


`Of course, there’s nothing stopping you from giving certain Git repos special meaning. For example, by simply designating one Git repo as the “central” repository, it’s possible to replicate a centralized workflow using Git. The point is, this is accomplished through conventions rather than being hardwired into the VCS itself.`

### Usage
git clone is primarily used to point to an existing repo and make a clone or copy of that repo at in a new directory, at another location. The original repository can be located on the local filesystem or on remote machine accessible supported protocols. The git clone command copies an existing Git repository. This is sort of like SVN checkout, except the “working copy” is a full-fledged Git repository—it has its own history, manages its own files, and is a completely isolated environment from the original repository.

As a convenience, cloning automatically creates a remote connection called "origin" pointing back to the original repository. This makes it very easy to interact with a central repository. This automatic connection is established by creating Git refs to the remote branch heads under refs/remotes/origin and by initializing remote.origin.url and remote.origin.fetch configuration variables.

An example demonstrating using git clone can be found on the setting up a repository guide. The example below demonstrates how to obtain a local copy of a central repository stored on a server accessible at example.com using the SSH username john:
<code class="hljs crmsh">git <span class="hljs-keyword">clone</span> <span class="hljs-title">ssh</span>://john@example.com/path/to/my-project.git
cd my-project
<span class="hljs-comment"># Start working on the project</span></code>
