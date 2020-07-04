### What does virsion control means?
`Version control is a system that records changes to a file or set of files over time so that you can recall specific versions later. For the examples in this book, you will use software source code as the files being version controlled, though in reality you can do this with nearly any type of file on a computer.`
### How does version control work?
Version control enables multiple people to simultaneously work on a single project. Each person edits his or her own copy of the files and chooses when to share those changes with the rest of the team. Thus, temporary or partial edits by one person do not interfere with another person's work.

<img src="https://media.geeksforgeeks.org/wp-content/uploads/20191203164948/Distributed-Version-Control-System.jpg">

### Distributed System:
Distributed systems are those which allow the users to perform work on a project from all over the world. A distributed system holds a Central repository that can be accessed by many remote collaborators by using a Version Control System. Git is one of the most popular Versions Control System that is being used nowadays. Having a Central Server results in a problem of Data Loss or Data disconnectivity in case of a system failure of the central server. To tackle such kind of a situation, Git mirrors the whole repository on each snapshot of the version that is being pulled by the user. In this case, if the central server crashes, then the copy of repositories can be gained back from the users who have downloaded the latest snapshot of the project.

Having a distributed system, Git allows the users to work simultaneously on the same project, without interfering with others’ work. When a particular user gets done with their part of the code, they push the changes to the repository and these changes get updated in the local copy of every other remote user which pulls the latest copy of the project.

### Compatibility:
Git is compatible with all the Operating Systems that are being used these days. Git repositories can also access the repositories of other Version Control Systems like SVN, CVK, etc. Git can directly access the remote repositories created by these SVNs. So, the users who were not using Git in the first place can also switch to Git without going through the process of copying their files from the repositories of other VCS’s into Git-VCS. Git can also access the central repositories of other VCSs. Hence, one can perform work on Git-SVN and use the central repository as the same. Git has a CVS server emulation, which enables the use of existing CVS clients and IDE plugins to access Git repositories.

### Which is a source code management tool?
A Source Code Management (SCM) is a software tool used by programmers to manage the source codes. SCMs are used to give versions/revisions to the program. Each version is given a timestamp and includes the person responsible for the change. Even various versions can be compared and merged with other versions.
