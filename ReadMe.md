# Hello WOrld ReadMe

##Test1: Steps:
1) Add some content
2) Don't stage the content
3) Create new branch and switch to new branch while this content is there

Result:
$ git checkout -b NewBranchWhenUnstagedContentPresent
Switched to a new branch 'NewBranchWhenUnstagedContentPresent'
M       ReadMe.md

- Readme.md file has all the contents which was unstaged earlier in master branch.

4) Make some changes in branch: NewBranchWhenUnstagedContentPresent
5) Checkout back to master branch

Result:
$ git checkout master
Switched to branch 'master'
M       ReadMe.md
Your branch is up to date with 'origin/master'.

CONCLUSION from TEST1: 
1) There is no effect on branch change if there is any unstage content
2) No problem in switching brnach with content that is not staged. Content can be added  added or deleted in any branch and it will be available in the same way in both branches.


##Test2: How to make sure that my unstaged work in master branch is not commited to a new branch
Steps:
1) Assume you are on master branch with Head at Commit say C1 and some unstaged content in readMe file
2) git stash to hide the unstaged work
3) Create a new branch git checkout -b NewBranchWithoutMasterContent
4) Revert back to master branch >> git checkout master
5) Undo stashed content >> git stash apply. At this moment all unstaged work is available in master. 
###CRUX1: Switching with unstaged content present in master to a new branch say NewBranch will take forward the unstaged content to NEW Branch. We did not want this at first place
6) To handle CRUX1, we will create a dummy commit in master branch. We move all unstage content into this commit
7) Now switch to branch  >>git checkout NewBranchWithoutMasterContent

NOTE: Why we earlier stashed master branch unstage content and then create a new branch. Why did we not create a dummy commit already of unstage commit in master and then create new commit.
That is because in this case, the dummy commit will move to NewBranch as well. 
#### IMPORTANT: Current state of master (current state of master branch which includes **commits** and **unstaged content** and **StagedContent**) is carried forward when creating a new branch out of it.

NOTE 2: If there is any staged content in master branch then you cannot create or shift to a new branh









1) Switch to featurebranch say FC1
- All the content that is unstaged in master branch is carried fwd to branch FC1.
- So take care that you stash all unstaged content of master before creating a new branch FC1
- But stashing is not a good solution. Because if you go to FC1 branch and have some unstaged work there, then while moving to master branch you will be stashing again to not bring that unstaged work(of FC1 branch) to master. in this process stash stack will have two elements and it gets difficult to track stashed items
- Better solution is to commit the unstaged work as a temp commit in master branch and move to FC1 branch.     