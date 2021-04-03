# 1. Getting started with Git
## 1.1. Create your first repository, then add and commit files
* See if we have git installed
````
git --version
git status
````
* Intialize git 
````
git init
````
* Add commit
````````
git add <file1> <file2> < ... >
git add commit -m"message or v0.0.0.1 beta"
````````
for add all file
```
git add .             
```
* Upload to github
```
git remote add origin <https://your-git-service-address>/owner/repository.git>
git push -u origin main
```

## 1.2. Clone a repository
````
git clone https://github.com/username/projectname.git  
			or 
git clone https://github.com/username/projectname.git MyFolder
````

## 1.3. Setting your user name and email
* Add a global identity
````
git config --global user.name "Your Name"
git config --global user.email mail@example.com
````

* Remove a global identity
````
git config --global --remove-section user.name
git config --global --remove-section user.email
````
## 1.4.Learning about a command
* Help
````
git diff --help
git help diff            
git diff -h       If you only want a quick help showing you
````

# 2. Browsing the history
## 2.1. "Regular" Git Log
````
git log
git log -2         If you wish to limit your command to last n commits log
````
## 2.2. Prettier log
````
git log --decorate --oneline --graph
````
## 2.3. Oneline log
````
git log --oneline
git log -2 --oneline
````
## 2.4. Log search
````
git log -S"Hello Qannaf"      	Searches for addition or removal
git log -S"Hello Qannaf"	Searches for changes in lines containing
````
## 2.5. List all contributions grouped by author name
````
git shortlog
````
## 2.6. Searching commit string in git log
````
git log --all --grep "removed file"		Will search for removed file string in all logs in all branches.
git log --grep="add file" --invert-grep
````
## 2.7. Log for a range of lines within a file
````
git log -L 1,20:main.cpp
````
## 2.8. Filter logs
````
git log --after '3 days ago'
git log --after 2021-04-03
git log --author=Qannaf 
````
## 2.9. Log with changes inline
````
git log --patch		or		git log --p
````
## 2.10. Log showing commited files
````
git log --stat
````
## 2.11. Show the contents of a single commit
````
git show 6531d54
````
## 2.12. Git Log Between Two Branches
````
git log master..foo 
``````
will show the commits that are on foo and not on master. Helpful for seeing what commits
					you've added since branching!


# 3. Working with Remotes
## 3.1. Deleting a Remote Branch
To delete a remote branch in Git:
	git push [remote-name] --delete [branch-name]
or
	git push [remote-name] :[branch-name]