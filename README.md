# Learning Git

- Open a terminal and navigate to your project’s root directory and execute the following command to initialize Git.
	- `git init . or git init`

- To create a local copy of an existing remote repository (the process called cloning), execute the following command.
	- `git clone <repo url>`
		- e.g. Clone a project into local project directory/
			- git clone https://github.com/ARMmbed/mbed-os.git
		
- To check the current state of your working directory and staging area, execute the following command.
	- `git status`
	- Untracked or modified files appear in red when viewing `git status` output. 
	- Successfully staged files appear in green, indicating they are:
		- Now being tracked by Git.
		- Ready to be committed.

## Commit

- Prior to committing changes, all modified or untracked files must be staged using the `git add` command.
	- `git add <file name>`
		- e.g. git add README.md
	- To stage all changes in the current directory (including subdirectories):
		- `git add .`
	- Following the execution of the `git add` command, successfully staged files will be displayed in green when viewing the repository status via `git status`. This color indication signifies that:
		- The files have been properly staged.
		- All modifications are now tracked by Git.
		- The changes are ready to be committed to the repository.

- To commit the changes into the repository.
	- `git commit -m <"comments about changes">`
		- e.g. git commit -m "Added information about git in README."

- To review the most recent commits in the repository.
	- `git log`
	
- Delete commit.
	- Soft reset: It removes the most recent commit while preserving all changes in the working directory and staging area.
		- `git reset --soft HEAD~<n>`
			- `n`: Number of commits to undo (positive integer).
			- e.g. To remove most recent commit.
				- git reset --soft HEAD~1
	- Hard reset: It permanently removes the most recent commit and discards all associated changes in both the working directory and staging area
		- `git reset --hard HEAD~<n>`
			- `n`: Number of commits to undo (positive integer).
			- e.g. To remove last 2 recent commit from respository along with changes.
				- git reset --hard HEAD~2
	- Delete specific commit.
		- `git reset --soft/hard <commit>`
			- e.g. git reset --soft c14809fa
			- e.g. git reset --hard c14809fa

## Branches

- The git branch command displays a complete listing of all branches existing within the local repository.
	- `git branch`
	
- To create a new branch.
	- `git branch <branch name>`
		- e.g. Create a new branch called "develop".
			- git branch develop
	
- Switch to new branch.
	- `git checkout <branch name>`
		- e.g. Checkout to "develop" branch.
			- git checkout develop

- Create a new branch and switch to it immediately.
	- `git checkout -b <branch name>`

- Merge two branches.
	- To integrate changes from one branch into another.
	- Switch to the target branch (the receiving branch).
	- Execute merge command.
	- `git merge <branch name>`
		- e.g "develop" branch is mearge into "main" branch.
			- git checkout main
			- git merge develop

- Delete the branch.
	- To delete the branch, navigate to a safe branch (typically main/master) and execute delete branch command.
	- `git branch -d <branch name>` # Safe deletion (verifies merge status)
	- `git branch -D <branch name>` # Force deletion (unmerged changes will be lost)
		- e.g. Delete a branch "develop".
			- git checkout main
			- git branch -D develop

## Update remote repository

- Prior to executing merge operations: (Not recommended to update master branch using merge command, always use pull request for merging new changes into master)
	- Confirm all changes are:
		- Properly tested.
		- Code reviewed (if applicable).
		- Conflict-free with the target branch
	- `git merge origin main` # Standard merge command.
	- `git merge -f origin main` # Force merge command.

## Create pull request to remote repository

- To create a pull request to remote master/repo.
	- Switch to that branch and run push command.
		- `git checkout <branch name>`
		- `git push origin <branch name>`
			- e.g. Create a pull request from branch "develop".
				- git checkout develop
				- git push origin develop

# Rebase branch to master and resolve conflict

- Rebase local branch to local master/main.
	- Switch to the target branch and run rebase command.
		- `git checkout <branch name>`
		- `git rebase main`
	- After rebase their is high chance that conflicts occurs. Fix conflicts in marked files.
		- Manually resolve conflicts by removing all code between <<<<<<<<<<, the commit hash (e.g., 123123454645768768), and ==============, as well as the line containing >>>>>>>>>> your previous commit.
		- Remove conflicts from all files and run following commands.
			- `git add <file name> or git add .` # To add all file at once.
			- `git rebase --continue`
		- After this command it will show next conflict. Continue from step 1 until all conflicts are resolved.
