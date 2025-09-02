### Answer the following questions in you own words.

> It's not necessary that you havee to know and answer all the questions. Just answer the ones
> you know and write in your own words.

1. Give the difference between the remotes - upstream and origin - with an example.

You answer:

origin is the name for our own remote local repository and upstream is generally used to point to the original repo thet we forked from.

Example: 

-> git push origin feature-x -> pushes to our forked repo

-> git fetch upstream -> updates things from the main/original repo

--- 
2. You have two branches A and B and you have currently made some changes in branch A.
You want to move into branch B but do not want to commit the current changes in branch A.
What will you do?

You answer:

We can use git stash for this, as we need to save uncommitted changes temporarily. After that we can do git checkout branchB to switch into branch B. Again when we need those changes of branch A we can use git stash pop to get them.

---
3. You were assigned a work to implement a feature and create a PR to your organization's remote repository.
For this you made a branch (say A) and made some changes and commited them. Now you moved to some other branch 
(say B) to do some other assigned work. But later you realisd that have to complete the task assigned earlier 
first and commited some changes in branch B which are meant for branch A. How will you use git to bring the 
changes from branch B to branch A?

You answer:

To do this, we can use git cherry pick commithash command. This is used when we need to get specific commits only from another branch to current branch. 
First we can do git log to get stats, commit hashes. Then switch branch from B to A usinf gitcheckout branchA. Then we can just use git cherry pick specificcommithash. Then we can remove those changes done by that commit using git revert or git reset(soft is better).

---
4. What is the difference between fetching changes and pulling changes?

Your answer:

git fetch only gets the chnages from remote repo but doesnt modify existing other files in local branch according to fetched things.

git pull is like git fetch+merge, here the changes are applied directly to local branch from remote repo.

---
5. What does -i flag stand for? What is it's significance in git?

You answer:

-i stands for interactive. Its generally used with git rebase. It allows us to edit the comments and history. We can use it for cleaning commit history in before pushing into big repos.

---
6. You are working in an organization that follows very strict guidelines for PRs and commits.
You made three commits in your PR and the maintainer says you were supposed to make a single commit.
What will you do in this case?

You answer:

using above interactive thing only, we can squash 3 commits into one that is by using git rebase -i head3. We can then use git force push branchname so gthat PR now will have only one commit.

---
7. Explain `git merge` and `git rebase` with example(s).

You answer:

git merge is used to combine both branches. Using this makes our history look like a tree structure.
git rebase moves one branch on to the top of another branch. Using this makes our merge history linear and clean.

Suppose we have a main branch and a feature branch, git merge combines the contyent of feature branch and main while git rebase adds the linear structure of feature branch in front of linear structure of main branch, keeping our merge history clean and linear.

---
8. Write the flow how you create a repository and push changes to it. Also mention the commands used at each step.

You answer:

git init - to intialise git

git remote add origin url - adds remote  (but I generally create a repo manually in github)

git add . - to add all files  (or)  git add filename - to add specific file

git commit -m "message" - commiting staged changes(Added ones)

git push origin main - to push changes into upstream.

---
9. How would you prevent a file or folder from getting tracked by git?

Your answer:

We can simply use '.gitignore' and list all the files, folders names that we need to prevent from tracking by git. We use it generally to avoind pushing .env files or node_modules etc.

---
10. You did not implement the step you mentioned in question 8 and now you have committed and pushed your database's
secret key to the github. How will you remove the key from your git's commit history to avoid any misuse?

You answer:

First I would revoke and generate new key to prevent working of previous key. Now we can use git filter branch to removethe .env file from all the commits containing it. Then we do git force push to push these changes  of deleting the .env containing secrets.


NOTE : I revised all the easy and intermediate git commands and concepts that I learned long back, before Axios Foss wing selection quiz. So I was able to recall most of them.

---