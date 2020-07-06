# git checkout 

`In this section, we will discuss the available 'undo' Git strategies and commands. It is first important to note that Git does not have a traditional 'undo' system like those found in a word processing application. It will be beneficial to refrain from mapping Git operations to any traditional 'undo' mental model. Additionally, Git has its own nomenclature for 'undo' operations that it is best to leverage in a discussion. This nomenclature includes terms like reset, revert, checkout, clean, and more.`

`A fun metaphor is to think of Git as a timeline management utility. Commits are snapshots of a point in time or points of interest along the timeline of a project's history. Additionally, multiple timelines can be managed through the use of branches. When 'undoing' in Git, you are usually moving back in time, or to another timeline where mistakes didn't happen.`

`This tutorial provides all of the necessary skills to work with previous revisions of a software project. First, it shows you how to explore old commits, then it explains the difference between reverting public commits in the project history vs. resetting unpublished changes on your local machine.`

### Finding what is lost: Reviewing old commits

`The whole idea behind any version control system is to store “safe” copies of a project so that you never have to worry about irreparably breaking your code base. Once you’ve built up a project history of commits, you can review and revisit any commit in the history. One of the best utilities for reviewing the history of a Git repository is the git log command. In the example below, we use git log to get a list of the latest commits to a popular open-source graphics library.`

<pre><code class="hljs sql">git log <span class="hljs-comment">--oneline</span>
e2f9a78fe Replaced FlyControls with OrbitControls
d35ce0178 Editor: Shortcuts panel Safari support.
9dbe8d0cf Editor: Sidebar.Controls to Sidebar.Settings.Shortcuts. Clean up.
05c5288fc <span class="hljs-keyword">Merge</span> pull request #<span class="hljs-number">12612</span> <span class="hljs-keyword">from</span> TyLindberg/editor-controls-panel
<span class="hljs-number">0</span>d8b6e74b <span class="hljs-keyword">Merge</span> pull request #<span class="hljs-number">12805</span> <span class="hljs-keyword">from</span> harto/<span class="hljs-keyword">patch</span><span class="hljs-number">-1</span>
<span class="hljs-number">23</span>b20c22e <span class="hljs-keyword">Merge</span> pull request #<span class="hljs-number">12801</span> <span class="hljs-keyword">from</span> gam0022/improve-raymarching-example-v2
fe78029f1 Fix typo <span class="hljs-keyword">in</span> documentation
<span class="hljs-number">7</span>ce43c448 <span class="hljs-keyword">Merge</span> pull request #<span class="hljs-number">12794</span> <span class="hljs-keyword">from</span> WestLangley/dev-x
<span class="hljs-number">17452</span>bb93 <span class="hljs-keyword">Merge</span> pull request #<span class="hljs-number">12778</span> <span class="hljs-keyword">from</span> OndrejSpanel/unitTestFixes
b5c1b5c70 <span class="hljs-keyword">Merge</span> pull request #<span class="hljs-number">12799</span> <span class="hljs-keyword">from</span> dhritzkiv/<span class="hljs-keyword">patch</span><span class="hljs-number">-21</span>
<span class="hljs-number">1</span>b48ff4d2 <span class="hljs-keyword">Updated</span> builds.
<span class="hljs-number">88</span>adbcdf6 WebVRManager: Clean up.
<span class="hljs-number">2720</span>fbb08 <span class="hljs-keyword">Merge</span> pull request #<span class="hljs-number">12803</span> <span class="hljs-keyword">from</span> dmarcos/parentPoseObject
<span class="hljs-number">9</span>ed629301 <span class="hljs-keyword">Check</span> <span class="hljs-keyword">parent</span> <span class="hljs-keyword">of</span> poseObject instead <span class="hljs-keyword">of</span> camera
<span class="hljs-number">219</span>f3eb13 <span class="hljs-keyword">Update</span> GLTFLoader.js
<span class="hljs-number">15</span>f13bb3c <span class="hljs-keyword">Update</span> GLTFLoader.js
<span class="hljs-number">6</span>d9c22a3b <span class="hljs-keyword">Update</span> uniforms <span class="hljs-keyword">only</span> <span class="hljs-keyword">when</span> onWindowResize
<span class="hljs-number">881</span>b25b58 <span class="hljs-keyword">Update</span> ProjectionMatrix <span class="hljs-keyword">on</span> <span class="hljs-keyword">change</span> aspect
</code></pre>


`Each commit has a unique SHA-1 identifying hash. These IDs are used to travel through the committed timeline and revisit commits. By default, git log will only show commits for the currently selected branch. It is entirely possible that the commit you're looking for is on another branch. You can view all commits across all branches by executing git log --branches=*. The command git branch is used to view and visit other branches. Invoking the command, git branch -a will return a list of all known branch names. One of these branch names can then be logged using git log <branch_name>.`

`When you have found a commit reference to the point in history you want to visit, you can utilize the git checkout command to visit that commit. Git checkout is an easy way to “load” any of these saved snapshots onto your development machine. During the normal course of development, the HEAD usually points to master or some other local branch, but when you check out a previous commit, HEAD no longer points to a branch—it points directly to a commit. This is called a “detached HEAD” state, and it can be visualized as the following:`

<img src="https://wac-cdn.atlassian.com/dam/jcr:362f3b15-9e74-4fe5-b97d-784e296880ad/01.svg?cdnVersion=1109" alt="Git Tutorial: Checking out a previous commit" class="lozad">

`Checking out an old file does not move the HEAD pointer. It remains on the same branch and same commit, avoiding a 'detached head' state. You can then commit the old version of the file in a new snapshot as you would any other changes. So, in effect, this usage of git checkout on a file, serves as a way to revert back to an old version of an individual file. For more information on these two modes visit the git checkout page`

### Viewing an old revision

`This example assumes that you’ve started developing a crazy experiment, but you’re not sure if you want to keep it or not. To help you decide, you want to take a look at the state of the project before you started your experiment. First, you’ll need to find the ID of the revision you want to see.`

**git log --oneline**

`Let’s say your project history looks something like the following:`

<pre><code class="hljs monkey">b7119f2 <span class="hljs-keyword">Continue</span> doing crazy things
<span class="hljs-number">872</span>fa7e <span class="hljs-keyword">Try</span> something crazy
a1e8fb5 Make some important changes <span class="hljs-keyword">to</span> hello.txt
<span class="hljs-number">435</span>b61d Create hello.txt
<span class="hljs-number">9773</span>e52 Initial <span class="hljs-keyword">import</span></code></pre>

`You can use git checkout to view the “Make some import changes to hello.txt” commit as follows`

**git checkout a1e8fb5**

`This makes your working directory match the exact state of the a1e8fb5 commit. You can look at files, compile the project, run tests, and even edit files without worrying about losing the current state of the project. Nothing you do in here will be saved in your repository. To continue developing, you need to get back to the “current” state of your project:`

**git checkout master**

`This assumes that you're developing on the default master branch. Once you’re back in the master branch, you can use either git revert or git reset to undo any undesired changes.`
