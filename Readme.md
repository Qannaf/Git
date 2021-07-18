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
````
git push [remote-name] --delete [branch-name]
or
git push [remote-name] :[branch-name]
````
## 3.2. Changing Git Remote URL
* Check existing remote
````
git remote -v
# origin https://github.com/username/repo.git (fetch)
# origin https://github.com/usernam/repo.git (push)
````
* Changing repository URL
````
git remote set-url origin https://github.com/username/repo2.git
# Change the 'origin' remote's URL
````
* Verify new remote URL
````
git remote -v
# origin https://github.com/username/repo2.git (fetch)
# origin https://github.com/username/repo2.git (push)
````
## 3.3. List Existing Remotes
* List all the existing remotes associated with this repository:
````
git remote
````
* List all the existing remotes associated with this repository in detail including the fetch and push URLs:
````
git remote --verbose
	or simply
git remote -v
````








## 3.4: Removing Local Copies of Deleted Remote Branches
If a remote branch has been deleted, your local repository has to be told to prune the reference to it.
To prune deleted branches from a specific remote:
```
git fetch [remote-name] --prune
```
To prune deleted branches from all remotes:
```
git fetch --all --prune
```

## 3.5: Updating from Upstream Repository
Assuming you set the upstream (as in the "setting an upstream repository")
```
git fetch remote-name
git merge remote-name/branch-name
```
The pull command combines a fetch and a merge.
```
git pull
The pull with --rebase flag command combines a fetch and a rebase instead of merge.
git pull --rebase remote-name branch-name
```

## 3.6: ls-remote
git ls-remote is one unique command allowing you to query a remote repo without having to clone/fetch it first.
It will list refs/heads and refs/tags of said remote repo.
You will see sometimes refs/tags/v0.1.6 and refs/tags/v0.1.6^{}: the ^{} to list the dereferenced annotated
tag (ie the commit that tag is pointing to)
Since git 2.8 (March 2016), you can avoid that double entry for a tag, and list directly those dereferenced tags with:
```
git ls-remote --ref
```
It can also help resolve the actual url used by a remote repo when you have "url.<base>.insteadOf" config setting.
If git remote --get-url <aremotename> returns https://server.com/user/repo, and you have set git config
url.ssh://git@server.com:.insteadOf https://server.com/:
```
git ls-remote --get-url <aremotename>
ssh://git@server.com:user/repo
```
## 3.7: Adding a New Remote Repository
```
git remote add upstream git-repository-url
```
Adds remote git repository represented by git-repository-url as new remote named upstream to the git repository

## 3.8: Set Upstream on a New Branch
You can create a new branch and switch to it using
``` 
git checkout -b AP-57
```
After you use git checkout to create a new branch, you will need to set that upstream origin to push to using
```
git push --set-upstream origin AP-57
```
After that, you can use git push while you are on that branch.

## 3.9: Getting Started
Syntax for pushing to a remote branch
```
git push <remote_name> <branch_name>
```
Example
```
git push origin master
```

## 3.10: Renaming a Remote
To rename remote, use command git remote rename
The git remote rename command takes two arguments:
 * An existing remote name, for example : origin
 * A new name for the remote, for example : destination
Get existing remote name
```
git remote
# origin
```
Check existing remote with URL
```
git remote -v
# origin https://github.com/username/repo.git (fetch)
# origin https://github.com/usernam/repo.git (push)
```
Rename remote
```
git remote rename origin destination
# Change remote name from 'origin' to 'destination'
```
Verify new name
```
git remote -v
# destination https://github.com/username/repo.git (fetch)
# destination https://github.com/usernam/repo.git (push)
```
=== Posible Errors ===
1. Could not rename config section 'remote.[old name]' to 'remote.[new name]'
This error means that the remote you tried the old remote name (origin) doesn't exist.
2. Remote [new name] already exists.
Error message is self explanatory.

## 3.11: Show information about a Specific Remote
Output some information about a known remote: origin
```
git remote show origin
```
Print just the remote's URL:
```
git config --get remote.origin.url
```
With 2.7+, it is also possible to do, which is arguably better than the above one that uses the config command.
```
git remote get-url origin
```

## 3.12: Set the URL for a Specific Remote
You can change the url of an existing remote by the command
```
git remote set-url remote-name url
```

## 3.13: Get the URL for a Specific Remote
You can obtain the url for an existing remote by using the command
```
git remote get-url <name>
```
By default, this will be
```
git remote get-url origin
```

## 3.14: Changing a Remote Repository
To change the URL of the repository you want your remote to point to, you can use the set-url option, like so:
```
git remote set-url <remote_name> <remote_repository_url>
```
Example:
```
git remote set-url heroku https://git.herok
```