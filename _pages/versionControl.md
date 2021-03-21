---
layout: single
author_profile: false
permalink: /versionControl/
title: "Version Control"
excerpt: "Instructions on how to use Github to branch, pull, and push content"
toc: true
header:
  caption: "Version Control"
  image: "/assets/images/versionControl.jpg"
tipue_search_active: true
exclude_from_search: false

---
Our [application software](https://en.wikipedia.org/wiki/Application_software) and associated documentation use [Git](https://en.wikipedia.org/wiki/Git) and the [Github](https://en.wikipedia.org/wiki/GitHub) hosting service to handle the [software version control](https://en.wikipedia.org/wiki/Version_control) (SVC) aspects of the [change control](https://en.wikipedia.org/wiki/Change_control) process that we follow. This page details how to set up and use the the VA3WAM git environment. 

## Local Directory Setup
Set up your local hard-drive with a directory structure like the one below. The "Markdown" directory tree hold local repositories for Pages and Wiki. The "PlatformIO" directory tree holds local repositories for embedded code. 
```
.
+--VisualStudioCode
   +--Markdown
      +--Projects
         +--Github URL (i.e. va3wam.github.io)
         +--Github URL (i.e. https://github.com/va3wam/TWIPe/wiki)
   +--PlatformIO
      +--Projects
         +--TWIPI
         +--etc
 ```

## Local Repository Setup
Once the directory tree above is set up on your hard drive use the command 

``` git clone ``` to set up any of the repositories that interest you. <i>Note that you get the URL in your browser by navigating to the repository you want, click the green <b>Clone or Download</b> button and copying the <b> repository URL</b> to the clipboard</i>. The next steps are done in a terminal session within Visual Studio Code.
    
### Website
Here is a link to the source code for [Aging Apprentice website](https://github.com/va3wam/va3wam.github.io) which is hosted on [Github Pages](https://pages.github.com).

### Embedded Code Repository
If you want to work on a VA3WAM Github <b>embedded code repository</b> follow these steps.
```
cd .../VisualStudioCode/PlatformIO/Projects
git clone https://github.com/va3wam/{project name}
```

### Set up Remote Association
Once you clone the directory to the Projects folder you should see a sub-directory named after the cloned repository. Go into that directory and issue the command ```git remote```. If you get the response origin back then you are all set up with a local repository and an associated remote. If you get a blank response back then issue the command <code>git remote add origin {repository URL}</code> to set up the remote. At this point you can start developing your additions to the repository.    

## Git Workflow
VA3WAM repositories are updated using a <a href="https://www.atlassian.com/git/tutorials/comparing-workflows/feature-branch-workflow">feature branching</a> workflow. This approach was selected after reading a <a href="https://nvie.com/posts/a-successful-git-branching-model/">post</a> by Vincent Driessen about how his widely adapted method created 2010 is worth revisiting. The approach selected for VA3WAM repositories was chosen based on this survey conducted by <a href="https://en.wikipedia.org/wiki/Atlassian">Atlassian</a> regarding <a href="https://www.atlassian.com/git/tutorials/comparing-workflows">common Git workflows</a>. Here is a run down on how to contribute following this workflow. If you want to practice this process and have been granted access then you can use the <a href="https://github.com/va3wam/LearnToBranch">VA3WAM LearnToBranch</a> repository.  

### Branch
If you want to make changes to an existing VA3WAM repository you must first create a branch as we do not submit changes to the remote repositories master branch. Here is the process.

1. ```git checkout master``` to get into the local master branch
2. ```git pull``` to make sure your local mater is in sync with the remote master
3. ```git checkout -b {branch name}``` to create a local branch and move to it. Use a meaningful branch name like an issue number or reference to the purpose of the code
   <li><code>git merge master</code> - put local mater code into local branch</li>
   <li><code>git push --set-upstream origin {branch name}</code> - create a branch on the remote server and push the local branch content up to it.</li>
   <li><code>git branch -a</code> - check your work. You should see you local and remote branches listed</li>
</ol>
Now start coding. A best practice for naming a branch is either an issue number as all work should be assigned an issue before working on it. If you want  to know what branch you are in locally or what remote branch you are pushing to type <code>git status -sb</code>. To delete a local branch type <code>git branch -d {branch name}</code>. To delete a remote branch type <code>git push --delete origin {branch name}</code>.

### Commit
<a href="https://git-scm.com/docs/git-commit">Committing</a> does not affect the local Master (assuming that you branched as described above) nor the remote repository at all. It is a best practice to make commits often. This will create a nice set of comments for all the work being done. These comments will carry forward to your pull request. <code>git commit -a -m "{put message here}"</code>. Alternatively, we recomendusing the <a href="https://code.visualstudio.com/Docs/editor/versioncontrol#_git-support">Source Control Tool</a> in Visual Studio Code to do your commits. When you have files that have changed they are listed under the Chnages heading. Each line has a + icon used to stage the file. 
  <li>Click the + (stage) icon beside the file you wish to stage.</li>
  <li>The file moves up to the Staged Changes heading. Repeat this for all files that get the same commit message.</li>
  <li>Type in an explanation of what you did to the file. in the Messag text box.</li>
  <li>Click the checkmark icon to check in the staged file(s)</li>
  <li>Click the elipse tool then from the drop down menu select push. This commits thhe changes.</li>
  <li>Repeat this process until all of the filles have been staged and committed with comments.</li>

### Pull Request
We use pull requests to merge branches with master. To make the pull/merge go smoothly you must first ensure that your branch is synchronized with master. Here is how to do that:
<ul>
<li><code>git checkout master</code> - make sure that you are in your local master branch</li>
<li><code>git pull</code> - get the latest code from GitHub master</li>
<li><code>git checkout {branch name}</code> - switch to the local branch you want to make a pull request for</li>
<li><code>git merge master</code> - sync the local master code with your local branch code</li>
<li><code>git push -u origin {branch name}</code> - push local branch to remote branch</li>
</ul>
At this point get into your browser and use the GitHub Pull Request button to create a pull request. Your pull request may be simple and be done fast or it may be complex and involve resolving conflicts or a lot of back and forward with reviewers. Whatever the case, eventually your pull request will be merged to the remote master. Once your pull request gets merged you need to do some clean up.

### Post Merge
Once your pull request is merged into mater on the remote server you need to clean up your local and remote branches. Here is how to do that. 
<ul>
<li><code>git checkout master</code> - get into the local master directory</li>
<li><code>git pull</code> - get the latest remote master code into the local master repository</li>
<li><code>git branch -a</code> - list all local and remote branches</li>
<li><code>git branch -d -r origin/{branch name}</code> - delete local pointer to GitHub remote branch</li>
<li><code>git push origin --delete {branch name}</code> - delete branch on Github. NOTE: If the command above gives this error: <code>error: unable to delete '{branch name}': remote ref does not exist</code> then you may have deleted the branch using your browser when you completed your merge. You can safely ignore this error and proceed.</li>
<li><code>git branch -d {branch-name}</code> - delete local branch</li>
</ul>
If you want to track a remote branch from a local branch then use the command
<code>git branch -u upstream/{branch name}</code>

### Pruning
If you issue the command ```git branch -a``` and find that you have a bunch of dead local and remote branches listed then you can clean up by issuog the command ```git fetch --prune origin```.   
