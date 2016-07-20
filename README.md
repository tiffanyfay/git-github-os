# Git, GitHub, and Contributing to Open Source
This is a rough template for what [Scott Hanselman](https://github.com/shanselman) and I are teaching at the Women Who Code workshop on July 19th, 2016. All pull requests or issues to improve it are welcome :).

*Disclaimer: This is still a WIP.*

# Contents
**Table of Contents**  *generated with [DocToc](http://doctoc.herokuapp.com/)*

- [Git, GitHub, and Contributing to Open Source](#git-github-and-contributing-to-open-source)
	- [Git/GitHub](#gitgithub)
		- [Creating a GitHub account](#creating-a-github-account)
		- [Getting git](#getting-git)
		- [Initial git setup](#initial-git-setup)
			- [Config](#config)
		- [Getting an existing repository](#getting-an-existing-repository)
		- [Creating your own repository](#creating-your-own-repository)
		- [Adding content to your new repo](#adding-content-to-your-new-repo)
		- [Making a new branch](#making-a-new-branch)
		- [Pulling down new content](#pulling-down-new-content)
	- [Contributing to Open Source](#contributing-to-open-source)
		- [Creating an Issue](#creating-an-issue)
		- [Creating a Pull Request](#creating-a-pull-request)
		- [Resources](#resources)
	- [Some Git/GitHub resources](#some-gitgithub-resources)

## Git/GitHub
### Creating a GitHub account
Head over to https://github.com/join?source=header-home and create an account.

### Getting git
Download git:
* https://git-scm.com/downloads

Or:
* Linux: `apt-get install git`
* Mac: `brew install git` (requires you to have brew installed)

### Initial git setup
#### Config
First you should tell git your name and email (You can set specific ones for different repositories if you wish.). So if you're Scott Hanselman, you'd do it like this:
```
git config --global user.name "Scott Hanselman"
git config --global user.email scott@hanselman.com
```

If you want to set up a default editor you can set it using:
```
git config --global core.editor vim
```

To see what configuration settings you have:
```
git config --list
```

### Getting an existing repository
Say you want to pull down Intel Snap, you would go to the github page, https://github.com/intelsdi-x/snap, click clone or download, pick HTTPS or SSH and copy the link. For HTTPS you can just add .git to the URL `https://github.com/intelsdi-x/snap.git`.
![git-clone](https://cloud.githubusercontent.com/assets/12282848/16968258/8f066e18-4dc2-11e6-9171-92b4b76f8590.png)

After copying the link, go to the path you want to clone this to. For organization it is more clear when there are separate directories for different repo owners.

### Creating your own repository
Go to GitHub and click the button `new repository`. This is what mine looks like:
![new-repo](https://cloud.githubusercontent.com/assets/12282848/16969555/79445e48-4dca-11e6-83ce-33a358caa4a5.png)

After clicking it you get to pick a title for your repo, decide if you want to make it public or private (this costs money), adding a license, and whether you want to have a [.gitignore](https://git-scm.com/docs/gitignore) file.
![create-new-repo](https://cloud.githubusercontent.com/assets/12282848/16969577/8f26101c-4dca-11e6-9916-8a8560c55f24.png)

After you create it, you can then go to your terminal to add either an existing git repo, or you can turn a directory into one.
![quick-setup](https://cloud.githubusercontent.com/assets/12282848/16969553/73f22560-4dca-11e6-9f4e-d1a8657ac5ab.png)

### Adding content to your new repo
Let's assume you haven't created your content yet.

You can either:
Clone your new repository with the first link shown, so
```
git clone https://github.com/tiffanyfj/git-github-os.git
```

Or
create a directory locally on your machine, create a directory with the same name that you used to create the GitHub repository. If you do it this way, you need to run
```sh
git init # this initializes your directory as a git repo
git remote add origin https://github.com/tiffanyfj/git-github-os.git
```

To see your remotes, you can run
```
git remote -v
```
Mine shows:
```
origin	https://github.com/tiffanyfj/git-github-os.git (fetch)
origin	https://github.com/tiffanyfj/git-github-os.git (push)
```

Make some files, say README.md. Add something to the README. Then add the file and make a commit. When creating this repository I created a directory on my machine in the path `github.com/tiffanyfj/git-github-os`. Then I created this README and added some content.
```sh
git add README.md # if you do . instead of README.md, it adds all files in the directory
git commit -m "Initial readme commit"
git push -u origin master # if you cloned, you just need to do git push
```

Now if you go refresh your repository on github.com, your commit with your README.md should be there.

If you decide to make changes you can make a new commit with the changes by doing the previous `git add` and `git commit lines` or use `git commit -am "Message goes here"` which does the two commands in one line. Then do a `git push`.

Or if you want to add your new changes to the same commit you can do
```sh
git add README.md
git commit --amend --no-edit
git push --force # This is risky though because it overwrites what you had so make sure you know what you're committing.
```

### Making a new branch
Say you want to make changes on a branch other than master. This is common when wanting to separate different changes. If you want to have the exact

### Pulling down new content
* `git fetch`: fetches the changes, but doesn't merge them
* `git pull`: does `git fetch` and `git merge`. This results in an [extra commit](https://coderwall.com/p/7aymfa/please-oh-please-use-git-pull-rebase).
* `git pull --rebase`: leaves your commits in a straight line without branches

## Contributing to Open Source
### Creating an Issue
Click the button at the top that says "Issues" and then the green button to the right.
![create-issue](https://cloud.githubusercontent.com/assets/12282848/16970455/112131a4-4dd1-11e6-890b-697903e9b94b.png)

### Creating a Pull Request
Click the button at the top that says "Pull Requests" and then the green button to the right.
![create-pr](https://cloud.githubusercontent.com/assets/12282848/16970458/128818aa-4dd1-11e6-9388-f27a7106cb4e.png)
If the pull request (PR) is to fix an existing issue, you can reference it by `#somenumber`, e.g. `#2`. It's common to say "Fixes #somenumber" so when the PR is merged, it closes the corresponding issue.

*Tip: Include the issue the PR fixes in the commit message and have descriptive messages.*

### Resources
Great websites for people who are new to coding/contributing to open source:
* [Code Newbie](http://www.codenewbie.org/)
* [Get involved in tech](http://www.getinvolvedintech.com)
* [First timers only](http://www.firsttimersonly.com/)
* [Your first PR](https://twitter.com/yourfirstpr)

## Some Git/GitHub Resources
* [Official git documentation](https://git-scm.com/doc)
* [GitHub's Hello-World](https://guides.github.com/activities/hello-world/)
* [Brent Beer's OSCON talk: Everything I wish I knew when I started using GitHub](https://www.youtube.com/watch?v=KDUtjZHIx44)
* [SWDB-2015 Git and GitHub tutorial](https://github.com/AllenBrainAtlas/SWDB-2015/blob/master/presentations/git/tutorial.ipynb)
* [Start Learning Git and GitHub Today with Self-Paced Training](https://github.com/blog/2083-start-learning-git-and-github-today-with-self-paced-training)

## Contributing to an Open Source Project  
* [Course from egghead.io: How to Contribute to an Open Source Project on GitHub](https://egghead.io/courses/how-to-contribute-to-an-open-source-project-on-github)
