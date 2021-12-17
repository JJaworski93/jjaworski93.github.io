+++
title = 'How to add a project to GitHub using command line'
slug = 'post1'
image = '../images/github.jpg'
date = "2021-01-07"
description = 'Adding your project to GitHub can let you build your portfolio, share your work and collaborate with others.'
disableComments = true
+++

##### Creating and adding your project to GitHub can let you build your portfolio, share your work and collaborate with others. Let's start!

In case you don't have Git installed yet, check [this article](https://docs.github.com/en/free-pro-team@latest/github/getting-started-with-github/set-up-git) on how to set it up. 

If you already have Git installed, create a [new repository](https://docs.github.com/en/free-pro-team@latest/github/creating-cloning-and-archiving-repositories/creating-a-new-repository) on GitHub, open Terminal and navigate into the directory where your source code (project) is located and **initialize the local directory as a Git repository** using:

_git init_

**Add all project files in your new local repository and stage them** before the first commit using:

_git add ._

**Commit the files** that you have staged in your local repository:

_git commit -m "*your commit comment*"_

 Now you should add the URL for the remote repository where your local repository will be pushed. At the top of your new GitHub repository, you will find the remote repository HTTPS URL. It should look similar to: *ht<span>tps://</span>github.com/yourusername/reponame.git*. Copy this URL, as you will need it in the next step. Next step is to **add a remote (github) location** with this command (remember to replace below URL with the URL that you copied in previous step):

_git remote add origin ht<span>tps://</span>github.com/yourusername/reponame.git_

Now you can **verify the new remote URL**:

_git remote -v_

At this stage you are ready to **push your project to your repository** hosted with GitHub:

_git push -u origin master_

Short note. GitHub is already working on replacing the term "master" on its service with a more neutral term "main". The reason is to avoid any unnecessary references to slavery (master and slave relation). For now you can choose if you want to have "master" or "main" as your default branch. In case your default (main) branch is "main", you should use:

_git push -u origin main_

instead of: _git push -u origin master_.

Thanks for reading!


