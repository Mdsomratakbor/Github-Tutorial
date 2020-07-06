# Git Init
`This page will explore the git init command in depth. By the end of this page you will be informed on the core functionality and extended feature set of git init. This exploration includes:`

- git init options and usage
- .git directory overview
- custom git init directory environment values
- git init vs. git clone
- git init bare repositories
- git init templates

**git init :**

`The git init command creates a new Git repository. It can be used to convert an existing, unversioned project to a Git repository or initialize a new, empty repository. Most other Git commands are not available outside of an initialized repository, so this is usually the first command you'll run in a new project.`

**.git directory overview :**

`Executing git init creates a .git subdirectory in the current working directory, which contains all of the necessary Git metadata for the new repository. This metadata includes subdirectories for objects, refs, and template files. A HEAD file is also created which points to the currently checked out commit.`

**custom git init directory environment values :**
`Aside from the .git directory, in the root directory of the project, an existing project remains unaltered (unlike SVN, Git doesn't require a .git subdirectory in every subdirectory).`

`By default, git init will initialize the Git configuration to the .git subdirectory path. The subdirectory path can be modified and customized if you would like it to live elsewhere. You can set the $GIT_DIR environment variable to a custom path and git init will initialize the Git configuration files there. Additionally you can pass the --separate-git-dir argument for the same result. A common use case for a separate .git subdirectory is to keep your system configuration "dotfiles" (.bashrc, .vimrc, etc.) in the home directory while keeping the .git folder elsewhere.`

### Usage

`Compared to SVN, the git init command is an incredibly easy way to create new version-controlled projects. Git doesn’t require you to create a repository, import files, and check out a working copy. Additionally, Git does not require any pre-existing server or admin privileges. All you have to do is cd into your project subdirectory and run git init, and you'll have a fully functional Git repository.`

**git init**

`Transform the current directory into a Git repository. This adds a .git subdirectory to the current directory and makes it possible to start recording revisions of the project.`

**git init "directory"**
