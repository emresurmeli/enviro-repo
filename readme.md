### enviro repo
------
this is a repo to store environment customizations and other setup features for a linux machine.  it is a git repo with commits of .bashrc, .profile, sublime-text preferences and the like.

#### basic idea
_git repo of the home folder ~_
_gitignore all files, add only files you want to checkin to version control_
_you will want to clone the repo to a folder on other machines and symlink or copy the files where they are needed_

#### DANGER
_its easy to commit and push a sensitive file (AWS keys, ssh keys, credential caches, etc).  *Don't commit those!*_ *Ever!*

#### steps
```#shell code block here
    another way to block code
    
_here goes_
  cd ~
  git init
  git status
now see lots untracked, not useful. Add the following lines to a .gitignore file in home directory:
  # ignores everything
  *
  # excludes from ignore rule (in repo root folder only)
  !.bashrc
now run `git status` and see that `.bashrc` is tracked.
  git add .bashrc
to add files deeper in the directory structure, you'll have to force tracking.  I was not able to un-gitignore files in subdirectories.
  git add -f directory/path/to/file.txt
  git status            _see?  good to go_
  git commit -m 'first commit of some useful files'
now create new remote repo on github.com (comment if you find a way to create from command line)
  git remote add origin https://github.com/USERNAME/REPONAME.git
  git push -u origin master
  git remote -v
now you have an online repo of handy files for when you set up a new machine somewhere.



##### reference
[a digitalocean article][1]
[stackoverflow of course][2]
[another stackoverflow][3]
another not _really_ helpful [stackoverflow article][4]


[1]:https://www.digitalocean.com/community/tutorials/how-to-use-git-to-manage-your-user-configuration-files-on-a-linux-vps
[2]:http://stackoverflow.com/questions/987142/make-gitignore-ignore-everything-except-a-few-files
[3]:http://stackoverflow.com/questions/2545602/git-ignore-sub-folders
[4]:http://stackoverflow.com/questions/5876075/gitignore-to-ignore-all-files-then-recursively-allows-files-of-a-certain-type
