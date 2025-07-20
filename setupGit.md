# install git

### download and install git

`https://git-scm.com/downloads`

### check git version

`git --version`

#

# configuration

### config user.name, user.email

`git config --global user.name "username"`  
`git config --global user.email "user.email"`

### check user

`git config user.name`  
`git config user.email`

### config alias for git command

`git config --global alias.lg "log --oneline"` -> git lg = git log --oneline

### view all configuration

`git config --list`  
or open configuration file to view:  
`cat ~/.gitconfig`  
or open configuration file to edit:  
`git config --global --edit`

### config default editor

`git config --global core.editor <editor>`  
where `<editor>` canbe:

- vim (for Vim)
- nano (for Nano)
- notepad (for Nodepad)
- "code --wait" (for Visual Studio Code)
- or "path/to/editor"

### config color.ui : better display in terminal

`git config --global color.ui auto`

### config default branch

`git config --global init.defaultBranch main`  
replace `main` by any word you want

### config SSH (if push/pull via SSH)

#

# setup project

### go to project's directory

`cd "path\to\project"`

### init a new repository

`git init`  
create .gitignore file to ignore files:  
`echo "" > .gitignore`

### or clone from an existing repository

`git clone <repo_URL>`
