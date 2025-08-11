# Create a new repository on the command line:

>	git init 

>	git add < files >

>	git commit -m "first commit"

>	git branch -M main

https:
>	git remote add origin https://github.com/AlexanderFur/obsidian_notes.git

SSH:
>	git remote add origin git@github.com:AlexanderFur/test_osterone.git

>	git push -u origin main

---
# …or push an existing repository from the command line

Replace URL with the correct one
>	git remote add origin https://github.com/AlexanderFur/obsidian_notes.git 

>	git branch -M main

>	git push -u origin main

---
# Everyday use:
>	git status 

>	git pull

>	git add <filename (or type a quotationless '.' for all of the current dir)>

>	git commit -m < Message >

>	git push

To see and compare all changes:

>	 git diff HEAD

------------------------------------------------------

# Git branch
List branches:

>	git branch 

Create branch:
> 	git branch < new branch name > 

 Change branch:
> 	git checkout < branch name >

Delete branch:
> 	git branch -d < branch name > 

Rename a local branch. If no old branch name is provided, it renames the current branch.
> 	git branch -m < old-branch-name > < new-branch-name > 

List all local and remote-tracking branches:
> 	git branch -a 

Create and change to -branch:
> 	git checkout -b <new_branch_name > 