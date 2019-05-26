## Hello WOrld ReadMe

Test1: Steps:
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


Test2: Staging content in a feature branch and then switching to master
Steps:
1) Switch to featurebranch say FC1
- All the content that is unstaged in master branch is carried fwd to branch FC1.
- So take care that you stash all unstaged content of master before creating a new branch FC1