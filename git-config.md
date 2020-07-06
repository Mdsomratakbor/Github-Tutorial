# Git Config 

`In this document, we'll take an in-depth look at the git config command. We briefly discussed git config usage on our Setting up a Repository page. The git config command is a convenience function that is used to set Git configuration values on a global or local project level. These configuration levels correspond to .gitconfig text files. Executing git config will modify a configuration text file. We'll be covering common configuration settings like email, username, and editor. We'll discuss Git aliases, which allow you to create shortcuts for frequently used Git operations. Becoming familiar with git config and the various Git configuration settings will help you create a powerful, customized Git workflow.`

### Usage
`The most basic use case for git config is to invoke it with a configuration name, which will display the set value at that name. Configuration names are dot delimited strings composed of a 'section' and a 'key' based on their hierarchy. For example: user.email`

**git config user.email**

`In this example, email is a child property of the user configuration block. This will return the configured email address, if any, that Git will associate with locally created commits.`
