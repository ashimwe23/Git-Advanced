# Git-Advanced
# QUESTIONS(1-3)

Part 1: Refining Git History (10 Challenges)

1. Missing File Fix:

Run git status and git log to assess the current state of your repository.
From the status you will see that you forgot to add test4.md in the last commit.
Challenge: Recover from this error by staging/adding test4.md and amending the commit message with an appropriate description.

2. Editing Commit History:

It's crucial to maintain accurate commit messages. Modify the message from "Create another file" to "Create second file".
Challenge: Utilize interactive rebasing (git rebase -i HEAD~2) to edit the commit message and ensure clarity. learn more about git rebase here

3. Keeping History Tidy - Squashing Commits:

Squashing combines multiple commits into a single one. Let's merge "Create second file" into "Create initial file" for a cleaner history.
Challenge: Use interactive rebasing with the squash command to achieve this. learn more about squash here



# ANSWERS(1-3)
```

Admin@DESKTOP-31KQOVP MINGW64 ~
$ pwd
/c/Users/Admin

Admin@DESKTOP-31KQOVP MINGW64 ~
$ cd 'C:\Users\Admin\Desktop\THE GYM\Git Advanced Exercises'

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises
$ git init
Initialized empty Git repository in C:/Users/Admin/Desktop/THE GYM/Git Advanced Exercises/.git/

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ echo "#Git-Advanced" >> README.md

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ git add README.md
warning: in the working copy of 'README.md', LF will be replaced by CRLF the next time Git touches it

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ git commit -m "First Commit"
[main (root-commit) 26d39fe] First Commit
 1 file changed, 1 insertion(+)
 create mode 100644 README.md

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ git branch -M main

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ git remote add origin https://github.com/ashimwe23/Git-Advanced.git

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ git push -u origin main
Enumerating objects: 3, done.
Counting objects: 100% (3/3), done.
Writing objects: 100% (3/3), 233 bytes | 233.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
To https://github.com/ashimwe23/Git-Advanced.git
 * [new branch]      main -> main
branch 'main' set up to track 'origin/main'.

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ git status
On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ git log --oneline
26d39fe (HEAD -> main, origin/main) First Commit

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ git status
On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ touch test{1..4}.md
git add test1.md && git commit -m "chore: Create initial file"
git add test2.md && git commit -m "chore: Create another file"
git add test3.md && git commit -m "chore: Create third and fourth files"
[main 55be22f] chore: Create initial file
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test1.md
[main cf9c88f] chore: Create another file
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test2.md
[main 029a88f] chore: Create third and fourth files
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test3.md

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ git status
On branch main
Your branch is ahead of 'origin/main' by 3 commits.
  (use "git push" to publish your local commits)

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        test4.md

nothing added to commit but untracked files present (use "git add" to track)

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ git log --oneline
029a88f (HEAD -> main) chore: Create third and fourth files
cf9c88f chore: Create another file
55be22f chore: Create initial file
26d39fe (origin/main) First Commit

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ git add test4.md

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ git commit --amend -m "Add test4.md file"
[main 656ae4d] Add test4.md file
 Date: Mon Jun 15 11:49:04 2026 +0200
 2 files changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test3.md
 create mode 100644 test4.md

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ git status
On branch main
Your branch is ahead of 'origin/main' by 3 commits.
  (use "git push" to publish your local commits)

nothing to commit, working tree clean

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ git log --oneline
656ae4d (HEAD -> main) Add test4.md file
cf9c88f chore: Create another file
55be22f chore: Create initial file
26d39fe (origin/main) First Commit

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ git rebase -i HEAD~2
[detached HEAD 52778c1] chore: Create Second file
 Date: Mon Jun 15 11:49:03 2026 +0200
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test2.md
Successfully rebased and updated refs/heads/main.

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ git rebase -i HEAD~2
error: cannot 'squash' without a previous commit
You can fix this with 'git rebase --edit-todo' and then run 'git rebase --continue'.
Or you can abort the rebase with 'git rebase --abort'.

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main|REBASE)
$ git rebase --abort

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ git log --oneline
df71ff5 (HEAD -> main) Add test4.md file
52778c1 chore: Create Second file
55be22f chore: Create initial file
26d39fe (origin/main) First Commit

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ ^C

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ git rebase --edit-todo
fatal: no rebase in progress

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ git rebase -i HEAD~2
[detached HEAD bda0e7b] chore: Create Second file
 Date: Mon Jun 15 11:49:03 2026 +0200
 3 files changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test2.md
 create mode 100644 test3.md
 create mode 100644 test4.md
Successfully rebased and updated refs/heads/main.

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ git log --oneline
bda0e7b (HEAD -> main) chore: Create Second file
55be22f chore: Create initial file
26d39fe (origin/main) First Commit

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ git rebase -i HEAD~2
[detached HEAD cfeb1a7] chore: Create Second file and test4.md file
 Date: Mon Jun 15 11:49:03 2026 +0200
 3 files changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test2.md
 create mode 100644 test3.md
 create mode 100644 test4.md
Successfully rebased and updated refs/heads/main.

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ git rebase -i HEAD~2
Successfully rebased and updated refs/heads/main.

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$

```


# QUESTIONS(4-8)

4. Splitting a Commit:

Imagine "Create third and fourth files" describes too much at once. Separate them for better tracking with two different commit messages: "Create Third File" and "Create fourth file".
Challenge: Leverage git reset to separate the files into individual commits with distinct messages. learn more about splitting commits here

5. Advanced Squashing:

Let's explore more complex squashing. Can you combine the last two commits ("Create third file" and "Create fourth file") into a single commit named "Create third and fourth files"?
Challenge: Utilize interactive rebasing with the squash command to achieve this advanced squash. Check step 4

6. Dropping a Commit:

We all make mistakes. Imagine needing to completely remove an unwanted commit from your history.

Create a new file named unwanted.txt add some changes and commit it with a message like "Unwanted commit".

Challenge: Use git rebase -i to identify and remove the "Unwanted commit" commit, cleaning up your history. learn more about dropping commits here

7. Reordering Commits:

Delve deeper into git rebase -i. Can you rearrange commits within your history using this command? learn more about ordering commits here

8. Cherry-Picking Commits:

Create a branch, call it ft/branch, and add a new file named test5.md with some content. Commit these changes with a message like "Implemented test 5".
Imagine you only desire a specific commit from ft/branch. Research and use git cherry-pick to selectively bring that commit into your current branch which is main.



# ANSWERS(4-8)
```
Admin@DESKTOP-31KQOVP MINGW64 ~
$ pwd
/c/Users/Admin

Admin@DESKTOP-31KQOVP MINGW64 ~
$ cd 'C:\Users\Admin\THE GYM\Git Advanced Exercises'
bash: cd: C:\Users\Admin\THE GYM\Git Advanced Exercises: No such file or directory

Admin@DESKTOP-31KQOVP MINGW64 ~
$ cd 'C:\Users\Admin\Desktop\THE GYM\Git Advanced Exercises'

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ git push
Everything up-to-date

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ touch third.txt fourth.txt

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ echo "third file" > third.txt

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ echo "fourth file" > fourth.txt

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ git add third.text fourth.txt
fatal: pathspec 'third.text' did not match any files

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ git add third.txt fourth.txt
warning: in the working copy of 'fourth.txt', LF will be replaced by CRLF the next time Git touches it
warning: in the working copy of 'third.txt', LF will be replaced by CRLF the next time Git touches it

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ git commit -m "Create third and fourth files"
[main f047d4f] Create third and fourth files
 2 files changed, 2 insertions(+)
 create mode 100644 fourth.txt
 create mode 100644 third.txt

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ git reset HEAD~1
Unstaged changes after reset:
M       README.md

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ git add third.txt
warning: in the working copy of 'third.txt', LF will be replaced by CRLF the next time Git touches it

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ git commit -m "create third file"
[main 9a18ca0] create third file
 1 file changed, 1 insertion(+)
 create mode 100644 third.txt

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ git add fourth.txt
warning: in the working copy of 'fourth.txt', LF will be replaced by CRLF the next time Git touches it

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ git commit -m "create fourth file"
[main c22c4c0] create fourth file
 1 file changed, 1 insertion(+)
 create mode 100644 fourth.txt

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ git log --oneline
c22c4c0 (HEAD -> main) create fourth file
9a18ca0 create third file
cfeb1a7 (origin/main) chore: Create Second file and test4.md file
55be22f chore: Create initial file
26d39fe First Commit

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ git rebase -i HEAD~2
error: cannot rebase: You have unstaged changes.
error: Please commit or stash them.

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ git stash
warning: in the working copy of 'README.md', LF will be replaced by CRLF the next time Git touches it
Saved working directory and index state WIP on main: c22c4c0 create fourth file

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ git rebase -i HEAD~2
Aborting commit due to empty commit message.
Could not apply c22c4c0... # create fourth file

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main|REBASE 2/2)
$ git log --oneline
9a18ca0 (HEAD) create third file
cfeb1a7 (origin/main) chore: Create Second file and test4.md file
55be22f chore: Create initial file
26d39fe First Commit

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main|REBASE 2/2)
$ git commit --amend -m "Create third and fourth files"
bash: $'\302\203git': command not found

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main|REBASE 2/2)
$ git commit --amend -m "create third and fourth files"
[detached HEAD 12cb1a9] create third and fourth files
 Date: Mon Jun 15 21:02:47 2026 +0200
 2 files changed, 2 insertions(+)
 create mode 100644 fourth.txt
 create mode 100644 third.txt

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main|REBASE 2/2)
$ git rebase --continue
Successfully rebased and updated refs/heads/main.

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ git log --oneline
12cb1a9 (HEAD -> main) create third and fourth files
cfeb1a7 (origin/main) chore: Create Second file and test4.md file
55be22f chore: Create initial file
26d39fe First Commit

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ touch unwanted.txt

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ echo "This is unwanted" > unwanted.txt

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ git add unwanted.txt
warning: in the working copy of 'unwanted.txt', LF will be replaced by CRLF the next time Git touches it

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ git commit -m "unwanted commit"
[main 0b221da] unwanted commit
 1 file changed, 1 insertion(+)
 create mode 100644 unwanted.txt

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ git log --oneline
0b221da (HEAD -> main) unwanted commit
12cb1a9 create third and fourth files
cfeb1a7 (origin/main) chore: Create Second file and test4.md file
55be22f chore: Create initial file
26d39fe First Commit

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ git rebase -i HEAD~2
Successfully rebased and updated refs/heads/main.

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ git log --oneline
12cb1a9 (HEAD -> main) create third and fourth files
cfeb1a7 (origin/main) chore: Create Second file and test4.md file
55be22f chore: Create initial file
26d39fe First Commit

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ git rebase -i HEAD~3
Successfully rebased and updated refs/heads/main.

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ git log --oneline
dc8a40c (HEAD -> main) chore: Create Second file and test4.md file
f3ec80f create third and fourth files
55be22f chore: Create initial file
26d39fe First Commit

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ git checkout -b ft/branch
Switched to a new branch 'ft/branch'

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (ft/branch)
$ touch test5.md

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (ft/branch)
$ echo "test 5 content" > test5.md

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (ft/branch)
$ git add test5.md
warning: in the working copy of 'test5.md', LF will be replaced by CRLF the next time Git touches it

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (ft/branch)
$ git commit -m "implemented test 5"
[ft/branch ae0625c] implemented test 5
 1 file changed, 1 insertion(+)
 create mode 100644 test5.md

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (ft/branch)
$ git log --oneline
ae0625c (HEAD -> ft/branch) implemented test 5
dc8a40c (main) chore: Create Second file and test4.md file
f3ec80f create third and fourth files
55be22f chore: Create initial file
26d39fe First Commit

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (ft/branch)
$ git checkout main
Switched to branch 'main'
Your branch and 'origin/main' have diverged,
and have 2 and 1 different commits each, respectively.
  (use "git pull" if you want to integrate the remote branch with yours)

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ git cherry-pick ae0625c
[main d431a0c] implemented test 5
 Date: Mon Jun 15 21:45:13 2026 +0200
 1 file changed, 1 insertion(+)
 create mode 100644 test5.md

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ git log --oneline
d431a0c (HEAD -> main) implemented test 5
dc8a40c chore: Create Second file and test4.md file
f3ec80f create third and fourth files
55be22f chore: Create initial file
26d39fe First Commit

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$

```

# QUESTIONS(9-10)

9.Visualizing Commit History (Bonus):

Tools like git log --graph or a graphical Git client can help visualize your commit history. Explore these tools for a clearer understanding of your workflow.
10.Understanding Reflogs (Bonus):

Reflogs track Git operation history. Research about git reflog to learn how you can navigate back to previous states in your repository if needed.


# ANSWERS(9-10)
```
Admin@DESKTOP-31KQOVP MINGW64 ~
$ pwd
/c/Users/Admin

Admin@DESKTOP-31KQOVP MINGW64 ~
$ cd 'C:\Users\Admin\Desktop\THE GYM\Git Advances Exercises'
bash: cd: C:\Users\Admin\Desktop\THE GYM\Git Advances Exercises: No such file or directory

Admin@DESKTOP-31KQOVP MINGW64 ~
$ cd 'C:\Users\Admin\Desktop\THE GYM\Git Advanced Exercises'

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ git log --oneline --graph --all
* d431a0c (HEAD -> main) implemented test 5
| * ae0625c (ft/branch) implemented test 5
|/
* dc8a40c chore: Create Second file and test4.md file
* f3ec80f create third and fourth files
| *   5d149d4 (refs/stash) WIP on main: c22c4c0 create fourth file
| |\
| | * 0c1d434 index on main: c22c4c0 create fourth file
| |/
| * c22c4c0 create fourth file
| * 9a18ca0 create third file
| * cfeb1a7 (origin/main) chore: Create Second file and test4.md file
|/
* 55be22f chore: Create initial file
* 26d39fe First Commit

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ git reflog
d431a0c (HEAD -> main) HEAD@{0}: cherry-pick: implemented test 5
dc8a40c HEAD@{1}: checkout: moving from ft/branch to main
ae0625c (ft/branch) HEAD@{2}: commit: implemented test 5
dc8a40c HEAD@{3}: checkout: moving from main to ft/branch
dc8a40c HEAD@{4}: rebase (finish): returning to refs/heads/main
dc8a40c HEAD@{5}: rebase (pick): chore: Create Second file and test4.md file
f3ec80f HEAD@{6}: rebase (pick): create third and fourth files
55be22f HEAD@{7}: rebase (start): checkout HEAD~3
12cb1a9 HEAD@{8}: rebase (finish): returning to refs/heads/main
12cb1a9 HEAD@{9}: rebase (start): checkout HEAD~2
0b221da HEAD@{10}: commit: unwanted commit
12cb1a9 HEAD@{11}: rebase (finish): returning to refs/heads/main
12cb1a9 HEAD@{12}: commit (amend): create third and fourth files
9a18ca0 HEAD@{13}: rebase (start): checkout HEAD~2
c22c4c0 HEAD@{14}: reset: moving to HEAD
c22c4c0 HEAD@{15}: commit: create fourth file
9a18ca0 HEAD@{16}: commit: create third file
cfeb1a7 (origin/main) HEAD@{17}: reset: moving to HEAD~1
f047d4f HEAD@{18}: commit: Create third and fourth files
cfeb1a7 (origin/main) HEAD@{19}: rebase (finish): returning to refs/heads/main
cfeb1a7 (origin/main) HEAD@{20}: rebase (start): checkout HEAD~2
cfeb1a7 (origin/main) HEAD@{21}: rebase (finish): returning to refs/heads/main
cfeb1a7 (origin/main) HEAD@{22}: rebase (reword): chore: Create Second file and test4.md file
bda0e7b HEAD@{23}: rebase: fast-forward
55be22f HEAD@{24}: rebase (start): checkout HEAD~2
bda0e7b HEAD@{25}: rebase (finish): returning to refs/heads/main
bda0e7b HEAD@{26}: rebase (squash): chore: Create Second file
52778c1 HEAD@{27}: rebase (start): checkout HEAD~2
df71ff5 HEAD@{28}: rebase (abort): returning to refs/heads/main
55be22f HEAD@{29}: rebase (start): checkout HEAD~2
df71ff5 HEAD@{30}: rebase (finish): returning to refs/heads/main
df71ff5 HEAD@{31}: rebase (pick): Add test4.md file
52778c1 HEAD@{32}: rebase (reword): chore: Create Second file
cf9c88f HEAD@{33}: rebase: fast-forward
55be22f HEAD@{34}: rebase (start): checkout HEAD~2
656ae4d HEAD@{35}: commit (amend): Add test4.md file
029a88f HEAD@{36}: commit: chore: Create third and fourth files
cf9c88f HEAD@{37}: commit: chore: Create another file
55be22f HEAD@{38}: commit: chore: Create initial file
26d39fe HEAD@{39}: Branch: renamed refs/heads/main to refs/heads/main
26d39fe HEAD@{41}: commit (initial): First Commit

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$
```
