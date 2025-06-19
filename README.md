# LearningGit

- First initialize the repository with following command in directory of project.
	- `git init . or git init`

- To clone an existing repository.
	- `git clone <repo url>`
		- e.g. git clone https://github.com/mudassirhussain0121/LearningGit.git

- Check the repository status. It will show the latest changes in the repository.
	- `git status`

## Commit

- For commit first add all untracked files (files that contain changes or new file in the repository).
	- `git add <files name>`
		- e.g. git add README.md
	- To add all files at once.
		- `git add .`

- All untracked changes will be shown in red color. When `git add .` command is exeuted then all changes will be shown in gree, which means that all green files are now being tracked and ready for commit.

- Commit all changes using commit command.
	- `git commit -m <"comments about changes">`
		- e.g. git commit -m "Added information about git in README."

- To view last few commit on the repository.
	- `git log`
	
- Delete commit.
	- Soft reset: It will delete the most recent commit and retain the changes.
	- `git reset --soft HEAD~1`
		- "1" indicates the number of commits that will be reset.
	- Hard reset: It will delete the most recent commit and destroy the changes as well.
	- `git reset --hard HEAD~1`
	- Delete specific commit.
	- `git reset --soft/hard <commit>
		- e.g. git reset --soft c14809fa
		- e.g. git reset --hard c14809fa