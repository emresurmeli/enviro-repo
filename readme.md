### enviro repo
------
this is a repo to store environment customizations and other setup features for a linux machine.  it is a git repo with commits of .bashrc, .profile, terminal color choices, text editor preferences, and the like.
<br>
<br>
  
#### basic idea
git repo of the home folder ~  
gitignore all files, add only files you want to check-in to version control.  
to use these files, you will clone the repo to a folder on other machines and symlink or copy the files where they are needed.

this is just for preference files and customizations, handy scripts, or other stuff that would make you sad to re-do on a new machine. this is not useful for binary files, executables, packages, or system-dependent applications.  for example, the node.js package still needs to get reinstalled on a new machine with your local package manager. if you create a setup script that installs npm, updates your package manager, installs node, sets up a directory and bootstrap whatevers, this would be a good file to save on a github repo to help you get quickly set up on a new machine.

anything more, such as GB backups of assets or machine images, and you are looking for a drive storage/backup solution.
<br>
<br>

#### DANGER
its easy to commit and push a sensitive file (AWS keys, ssh keys, credential caches, etc).  **Don't commit those! Ever!**
<br>  
<br>

#### steps

```shell
cd ~
git init
git status
```

now see lots of untracked files, not useful. add the following lines to a .gitignore file in home directory:

```shell
# ignores everything
*
# excludes from ignore rule (in repo root folder only)
!.bashrc
```

now run `git status` and see that `.bashrc` is tracked. this makes a handy reminder of your tracked files that have changed, so you can commit and push those periodically.  over time your customizations will evolve just the way you like them, and be saved for all time.  sweet!

```shell
git add .bashrc
```

to add files deeper in the directory structure, you'll have to force tracking.  I was not able to un-gitignore files in subdirectories, comment if you figure it out (and test it).

```shell
git add -f directory/path/to/file.txt
git status
git commit -m 'first commit of some useful files'
```

now create new remote repo on github.com (comment if you find a way to create from command line)

```shell
git remote add origin https://github.com/USERNAME/REPONAME.git
git push -u origin master
git remote -v
```

now you have an online repo of handy files for when you set up a new machine somewhere. just clone the repo to a folder in your new machine home folder and create symlinks to these files in your new system. 
<br>
<br>
<br>

##### reference
[a digitalocean article][1]  
[stackoverflow of course][2]  
[another stackoverflow][3]  
another not really helpful [stackoverflow article][4] on gitignore subdirectories  

[1]:https://www.digitalocean.com/community/tutorials/how-to-use-git-to-manage-your-user-configuration-files-on-a-linux-vps
[2]:http://stackoverflow.com/questions/987142/make-gitignore-ignore-everything-except-a-few-files
[3]:http://stackoverflow.com/questions/2545602/git-ignore-sub-folders
[4]:http://stackoverflow.com/questions/5876075/gitignore-to-ignore-all-files-then-recursively-allows-files-of-a-certain-type
