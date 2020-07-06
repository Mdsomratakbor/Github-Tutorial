# Initialize Git Repository Using Command line

### How to Adding an existing project to GitHub using the command line?
- `1. Create a new repository on GitHub. You can also add a gitignore file, a readme and a licence if you want.`
- `2. Open Git Bash.`
- `3. Change the current working directory to your local project.`
- `4. Initialize the local directory as a Git repository.`

   **Using this command : git init**
- `5. Add the files in your new local repository. This stages them for the first commit.`

   **Using this command : git add .**
   
- `6. Commit the files that you’ve staged in your local repository.`

   **Using this command : git commit -m "initial commit"**
   
- `7. Copy the https url of your newly created repository.`
- `8. In the Command prompt, add the URL for the remote repository where your local repository will be pushed.`
  
  **Using this command : git remote add origin "remote repository URL"**
  **Using this command : git remote -v**
  
- `9. Push the changes in your local repository to GitHub.`

 **Using this command : git push -f origin master**

