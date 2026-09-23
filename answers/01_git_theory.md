# Part A — Git & project foundations

## Git Fundamentals

### 1. Git has three places a change can live: the working directory, the staging area, and the repository.Describe each, and explain what you would lose if the staging area did not exist.

The working directory is where files are created and edited. The staging area is where it contains the changes you have selected to include in your next commit. The repository has the committed history of the project. If staging area didn't exist then for example if you changed two files but want to commit only one then you wouldn't be able to separate those changes that is you would lose the ability to choose exactly which changes should go into a commit.

### 2. git init and git clone both leave you with a Git repository. Explain what each one actually does, and give a situation where each is the right choice.

git init is used when you have a project already on your computer that is locally and you want to start tracking it with Git. git clone makes a copy of already existing repository from GitHub to your computer. git init is right choice for a new local project and git clone is right choice when you want to work on an already existing project on a remote location.

### 3. What does a commit store, and why is "committing" not the same as "saving a file"? Why is Git muchless useful if user.name and user.email are unset or wrong?

Commit stores a snapshot of a project's tracked files at a particular point in time which includes information such as author and commit message. "Committing" is not the same as "Saving a file" because saving only changes the file on your computer but committing records a version in Git's history. Git is much less useful if user.name and user.email are unset or wrong because Git won't correctly show who made commits which can make project history confusing. 

### 4. git status, git log, and git diff answer three different questions. State the question each oneanswers, and describe a moment in your workflow where you would reach for each.

git status tells what files are changed, staged or untracked, so you would use it before making a commit. git log shows previous commits and project history so use it when you want to check what changes were made before. git diff shows the exact changes one made so use it before committing to review one's work.

### 5. Explain what makes a commit message good. Why is "update" a genuine problem for a team six months later, and when is it worth writing a message body rather than just a summary line?

If the messages are clear and specific about what changes were made so that one can understand the purpose of the commit easily then it makes a commit message good. "update" is a genuine problem for a team six months later because they won't know what was updated just from the message "update" and they won't know what the purpose of the change was. A message body is worth writing rather tha just a summary line in cases where the change needs explanation like why the changes were made and if there are some important details to know.

## Remotes and the everyday workflow

### 6. Explain the relationship between your local repository and origin. What do push and pull each move, in which direction, and why is pulling before pushing the habit to build?

Local repository means the Git repository on your computer. Origin is the remote repository connected to your local project, usually on GitHub. push sends local commits to remote repository and pull brings changes from remote repository to local one. Pulling before pushing is a habit to be built because it helps get the latest changes from others and avoid conflicts.

### 7. git fetch and git pull are not the same command. What is the difference, and when would you deliberately choose fetch ?

git fetch gets the latest changes from remote repository but does not apply them to your current work. git pull gets the changes and brings them to your current branch. I would deliberately choose fetch when i want to first check what changes others made before deciding to merge them.

## Branching, merging, pull requests

### 8. A branch in Git is often described as "just a pointer." Explain what that means, and explain concretely what goes wrong on a team when everyone commits directly to main .

A branch in Git is often described as "just a pointer" because it points to a commit and is movable, that is when a new commit is made it moves to the latest commit. If everyone commits directly to main then different team members work can get mixed together and unfinished changes can affect the main project.

### 9. A merge conflict happens when two branches change the same lines of the same file. Explain why Git cannot resolve this automatically, what the <<<<<<< , ======= , >>>>>>> markers mean, and what you must do to finish the merge.

Git cannot automatically resolve a merge conflict when two branches change the same lines of the same file because Git cannot know which version the change is intented to as there is not enough information. <<<<<<< marker means your current branch changes, ======= marker separates the two version, >>>>>>> marker means the change from incoming branch. To finish the merge I should decide what the correct code should be and remove conflict markers and combine the correct changes, stage the resolved file and complete the merge with commit.

### 10. You could merge a branch locally with git merge and push. What does opening a Pull Request add that a local merge does not? What belongs in a PR description?

A local merge combines the changes directly, but opening a Pull Request allows the team to review and discuss the changes before merging them into main which helps catch bugs and make sure the code is error free and ready. PR description includes what changes you made, why the change was made and any important details one should know about.

## Issues

### 11. Explain the purpose of labels and assignees on an Issue, and what Fixes #12 in a merged PR does. Why is linking work to Issues better than closing them by hand?

Labels categorize issues like bug or features and their type and priority. Assignees show who is responsible for working on an issue. Fixes #12 in a PR automatically closes Issue #12 when merged. Linking work to Issues is better than closing them by hand because it creates a clear history, what changes was made and the solutions.

## Project structure, environments, secrets

### 12. Why should .gitignore be one of your first commits? If a file is already tracked, does adding it to .gitignore stop Git from tracking it — and if not, what do you do instead?

.gitignore should be one of your first commits to prevent accidental commit of files such as .env files or temporary files. If a file is already tracked, adding it to .gitignore does not stop Git from tracking it. I would first remove it from tracking using git rm --cached <file> and commit the changes.

### 13. Explain the difference between .env and .env.example , and why they get opposite treatment. If a real API key was committed three weeks ago, why is deleting it in a new commit not a fix, and what should actually be done?

.env contains API keys and paawords so it should not be commited. .env.example contains values such as placeholder which shows what variables are needed so it can be committed. If a real API key was committed three weeks ago then deleting it in a new commit is not a fix because the key still exists in the Git's history and it should be revoked or rotated and Git history need to be cleared.

### 14. What problem do a virtual environment and requirements.txt solve together? Why is venv/ itself never committed, when requirements.txt always is?

Virtual environment keeps project's package separate from other projects. requirements.txt records which packages and versions the projec needs. These together makes it easier for another developer to recreate a similar environment on their computer. venv/ itself is never committed because it contains local installed environment, that is machine specific and the folder can be recreated. requirements.txt is always committed because it describes what needs to be installed and others can set up same dependencies.

### 15. Explain what git push --force does to a shared branch and whose work it can destroy. How does --force-with-lease behave differently, and why is that safer?

git push --force overwrites the remote branch with one's local version and can erase other people's commits if they have pushed the changes that you don't want locally. --force-with-lease behave differently in a sense that it is safer as Git checks whether the remote branch is still where it is as last expected before allowing a force push and it simply doesn't overwrite it if someone else has pushed new work.