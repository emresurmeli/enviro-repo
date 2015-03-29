### enviro repo
------
this is a repo to store environment customizations and other setup features for a linux machine.  it is a git repo with commits of .bashrc, .profile, sublime-text preferences and the like.
  
  
#### basic idea
git repo of the home folder ~
gitignore all files, add only files you want to check-in to version control.
you will want to clone the repo to a folder on other machines and symlink or copy the files where they are needed.
  
  
#### DANGER
its easy to commit and push a sensitive file (AWS keys, ssh keys, credential caches, etc).  **Don't commit those! Ever!**
  
  
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

now you have an online repo of handy files for when you set up a new machine somewhere. just clone the repo to a folder in you new machine home folder and create symlinks to these files in your new system. 
  
  
  
##### reference
[a digitalocean article][1]  
[stackoverflow of course][2]  
[another stackoverflow][3]  
another not _really_ helpful [stackoverflow article][4]  

[1]:https://www.digitalocean.com/community/tutorials/how-to-use-git-to-manage-your-user-configuration-files-on-a-linux-vps
[2]:http://stackoverflow.com/questions/987142/make-gitignore-ignore-everything-except-a-few-files
[3]:http://stackoverflow.com/questions/2545602/git-ignore-sub-folders
[4]:http://stackoverflow.com/questions/5876075/gitignore-to-ignore-all-files-then-recursively-allows-files-of-a-certain-type
