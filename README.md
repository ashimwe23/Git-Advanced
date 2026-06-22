# Git-Advanced
This line was added directly on GitHub.
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
# Part 3: Advanced Workflows (10+ Challenges)

1. Stashing Changes:

Imagine you're working on some changes in the main branch but need to attend to something urgent. You don't want to lose your uncommitted work.
Challenge: Stash your current changes in the main branch using git stash.

2. Retrieving Stashed Changes:

Later, when you're ready to resume working on those stashed changes, you can retrieve them.
Challenge: Apply the most recent stash back onto the main branch using git stash pop.

3. Branch Merging Conflicts (Continued):

Merge conflicts can arise when the same lines of code are modified in both branches being merged.
Challenge: Simulate a merge conflict scenario (you can create conflicting changes in a file on both main and a new feature branch). Then, try merging again and resolve the conflicts manually using your text editor.

4. Resolving Merge Conflicts with a Merge Tool:

Explore using a merge tool like git mergetool to help you visualize and resolve merge conflicts more efficiently.
Understanding Detached HEAD State:

5. Detached HEAD refers to a state where your working directory is not associated with any specific branch. Research the implications and how to recover from this state using commands like git checkout <branch-name>.

```

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ git checkout -b ft/new-feature
Switched to a new branch 'ft/new-feature'

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (ft/new-feature)
$ git branch
  ft/branch
* ft/new-feature
  main

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (ft/new-feature)
$ touch feature.txt

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (ft/new-feature)
$ echo "core functionality for the new feauture" > feature.txt

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (ft/new-feature)
$ git status
On branch ft/new-feature
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        feature.txt

nothing added to commit but untracked files present (use "git add" to track)

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (ft/new-feature)
$ git add feature.txt
warning: in the working copy of 'feature.txt', LF will be replaced by CRLF the next time Git touches it

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (ft/new-feature)
$ git commit -m "Implemented core functionality for a new feature"
[ft/new-feature d377aaa] Implemented core functionality for a new feature
 1 file changed, 1 insertion(+)
 create mode 100644 feature.txt

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (ft/new-feature)
$ git log --oneline
d377aaa (HEAD -> ft/new-feature) Implemented core functionality for a new feature
e8f7c63 (origin/main, main) Merge branch 'main' of https://github.com/ashimwe23/Git-Advanced
a71290b Update README.md with Git advanced codes
d431a0c implemented test 5
dc8a40c chore: Create Second file and test4.md file
f3ec80f create third and fourth files
cfeb1a7 chore: Create Second file and test4.md file
55be22f chore: Create initial file
26d39fe First Commit

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (ft/new-feature)
$ git checkout main
Switched to branch 'main'
Your branch is up to date with 'origin/main'.

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ touch readme.txt

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ echo "Welcome to this project." > readme.txt

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ git status
On branch main
Your branch is up to date with 'origin/main'.

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        readme.txt

nothing added to commit but untracked files present (use "git add" to track)

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ git add readme.txt
warning: in the working copy of 'readme.txt', LF will be replaced by CRLF the next time Git touches it

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ git commit "updated project readme"
error: pathspec 'updated project readme' did not match any file(s) known to git

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ git commit -m "updated project readme"
[main 92110df] updated project readme
 1 file changed, 1 insertion(+)
 create mode 100644 readme.txt

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ git log --oneline
92110df (HEAD -> main) updated project readme
e8f7c63 (origin/main) Merge branch 'main' of https://github.com/ashimwe23/Git-Advanced
a71290b Update README.md with Git advanced codes
d431a0c implemented test 5
dc8a40c chore: Create Second file and test4.md file
f3ec80f create third and fourth files
cfeb1a7 chore: Create Second file and test4.md file
55be22f chore: Create initial file
26d39fe First Commit

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ git branch -r
  origin/ft/branch
  origin/main

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ git remote -v
origin  https://github.com/ashimwe23/Git-Advanced.git (fetch)
origin  https://github.com/ashimwe23/Git-Advanced.git (push)

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ git push -u origin ft/new-feature
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 4 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 340 bytes | 340.00 KiB/s, done.
Total 3 (delta 1), reused 0 (delta 0), pack-reused 0 (from 0)
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
remote:
remote: Create a pull request for 'ft/new-feature' on GitHub by visiting:
remote:      https://github.com/ashimwe23/Git-Advanced/pull/new/ft/new-feature
remote:
To https://github.com/ashimwe23/Git-Advanced.git
 * [new branch]      ft/new-feature -> ft/new-feature
branch 'ft/new-feature' set up to track 'origin/ft/new-feature'.

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ git branch -d ft/new-feature
warning: deleting branch 'ft/new-feature' that has been merged to
         'refs/remotes/origin/ft/new-feature', but not yet merged to HEAD
Deleted branch ft/new-feature (was d377aaa).

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ git branch
bash: $'\302\203git': command not found

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ git merge origin/ft/new-feature
Merge made by the 'ort' strategy.
 feature.txt | 1 +
 1 file changed, 1 insertion(+)
 create mode 100644 feature.txt

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ git push origin --delete ft/new-feature
bash: $'\302\203git': command not found

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ git push origin --delete ft/new-feature
bash: $'\302\203git': command not found

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ git push origin --delete ft/new-feature
fatal: unable to access 'https://github.com/ashimwe23/Git-Advanced.git/': Could not resolve host: github.com

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ git branch -r
  origin/ft/branch
  origin/ft/new-feature
  origin/main

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ git push origin --delete ft/new-feature
To https://github.com/ashimwe23/Git-Advanced.git
 - [deleted]         ft/new-feature

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$

```
Branch Deletion:

After merging or completing work on a feature branch, it's good practice to remove it.
Challenge: Delete the ft/new-feature branch once you're confident the changes are integrated into main.

Creating a Branch from a Commit:

You can also create a branch from a specific commit in your history.
Challenge: Use git checkout -b ft/new-branch-from-commit commit-hash (adjust the commit hash as needed) to create a new branch named ft/new-branch-from-commit starting from the commit two positions back in your history. learn more here

Branch Merging:

Now that you've completed work on your feature branch, it's time to integrate it into main.
Challenge: Merge the ft/new-branch-from-commit branch into the main branch. Address any merge conflicts that might arise.

Branch Rebasing:

Rebasing is another method to integrate changes from a feature branch. It rewrites your branch history by incorporating its commits on top of the latest commit in the target branch (main in our case).
Challenge: Try rebasing the ft/new-branch-from-commit branch onto the main branch. Remember, rebasing rewrites history, so use it with caution, especially in shared repositories. learn more about rebasing here

Renaming Branches:

Branch names can sometimes evolve. Let's rename ft/new-branch-from-commit to a more descriptive name.
Challenge: Use git branch -m ft/new-branch-from-commit ft/improved-branch-name to rename your branch.

Checking Out Detached HEAD:

In specific situations, you might need to detach HEAD from your current branch. Research git checkout <commit-hash> (replace with the desired commit hash) to understand this concept.
```

Admin@DESKTOP-31KQOVP MINGW64 ~
$ pwd
/c/Users/Admin

Admin@DESKTOP-31KQOVP MINGW64 ~
$ cd 'C:\Users\Admin\Desktop\THE GYM\Git Advanced Exercises'

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ git log --oneline
161a12a (HEAD -> main) Merge remote-tracking branch 'origin/ft/new-feature'
92110df updated project readme
d377aaa Implemented core functionality for a new feature
e8f7c63 (origin/main) Merge branch 'main' of https://github.com/ashimwe23/Git-Advanced
a71290b Update README.md with Git advanced codes
d431a0c implemented test 5
dc8a40c chore: Create Second file and test4.md file
f3ec80f create third and fourth files
cfeb1a7 chore: Create Second file and test4.md file
55be22f chore: Create initial file
26d39fe First Commit

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ git checkout -b ft/new-branch-from-commit d377aaa
Switched to a new branch 'ft/new-branch-from-commit'

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (ft/new-branch-from-commit)
$ git branch
  ft/branch
* ft/new-branch-from-commit
  main

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (ft/new-branch-from-commit)
$ git log --oneline -3
d377aaa (HEAD -> ft/new-branch-from-commit) Implemented core functionality for a new feature
e8f7c63 (origin/main) Merge branch 'main' of https://github.com/ashimwe23/Git-Advanced
a71290b Update README.md with Git advanced codes

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (ft/new-branch-from-commit)
$ git checkout main
Switched to branch 'main'
Your branch is ahead of 'origin/main' by 3 commits.
  (use "git push" to publish your local commits)

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ git merge ft/new-branch-from-commit
Already up to date.

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ git merge ft/new-branch-from-commit
Already up to date.

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ ^C

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ git status
bash: $'\302\203git': command not found

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ git status
On branch main
Your branch is ahead of 'origin/main' by 3 commits.
  (use "git push" to publish your local commits)

nothing to commit, working tree clean

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ git log --oneline --graph --all
*   161a12a (HEAD -> main) Merge remote-tracking branch 'origin/ft/new-feature'
|\
| * d377aaa (ft/new-branch-from-commit) Implemented core functionality for a new feature
* | 92110df updated project readme
|/
*   e8f7c63 (origin/main) Merge branch 'main' of https://github.com/ashimwe23/Git-Advanced
|\
| * a71290b Update README.md with Git advanced codes
* | d431a0c implemented test 5
| | * ae0625c (origin/ft/branch, ft/branch) implemented test 5
| |/
|/|
* | dc8a40c chore: Create Second file and test4.md file
* | f3ec80f create third and fourth files
| | *   5d149d4 (refs/stash) WIP on main: c22c4c0 create fourth file
| | |\
| | | * 0c1d434 index on main: c22c4c0 create fourth file
| | |/
| | * c22c4c0 create fourth file
| | * 9a18ca0 create third file
| |/
| * cfeb1a7 chore: Create Second file and test4.md file
|/
* 55be22f chore: Create initial file
* 26d39fe First Commit

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ git branch --merged
bash: $'\302\226\302\203git': command not found

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ git branch --merged
  ft/new-branch-from-commit
* main

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$ git checkout ft/new-branch-from-commit
Switched to branch 'ft/new-branch-from-commit'

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (ft/new-branch-from-commit)
$ git rebase main
Successfully rebased and updated refs/heads/ft/new-branch-from-commit.

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (ft/new-branch-from-commit)
$ git branch -m ft/new-branch-from-commit ft/improved-branch-name

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (ft/improved-branch-name)
$ git branch
  ft/branch
* ft/improved-branch-name
  main

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (ft/improved-branch-name)
$ git push -u origin ft/improved-branch-name
Enumerating objects: 9, done.
Counting objects: 100% (9/9), done.
Delta compression using up to 4 threads
Compressing objects: 100% (6/6), done.
Writing objects: 100% (8/8), 775 bytes | 387.00 KiB/s, done.
Total 8 (delta 4), reused 0 (delta 0), pack-reused 0 (from 0)
remote: Resolving deltas: 100% (4/4), completed with 1 local object.
remote:
remote: Create a pull request for 'ft/improved-branch-name' on GitHub by visiting:
remote:      https://github.com/ashimwe23/Git-Advanced/pull/new/ft/improved-branch-name
remote:
To https://github.com/ashimwe23/Git-Advanced.git
 * [new branch]      ft/improved-branch-name -> ft/improved-branch-name
branch 'ft/improved-branch-name' set up to track 'origin/ft/improved-branch-name'.

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (ft/improved-branch-name)
$ git push origin --delete ft/new-branch-from-commit
error: unable to delete 'ft/new-branch-from-commit': remote ref does not exist
error: failed to push some refs to 'https://github.com/ashimwe23/Git-Advanced.git'

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (ft/improved-branch-name)
$ git branch -r
  origin/ft/branch
  origin/ft/improved-branch-name
  origin/main

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (ft/improved-branch-name)
$ git checkout d377aaa
Note: switching to 'd377aaa'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by switching back to a branch.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -c with the switch command. Example:

  git switch -c <new-branch-name>

Or undo this operation with:

  git switch -

Turn off this advice by setting config variable advice.detachedHead to false

HEAD is now at d377aaa Implemented core functionality for a new feature

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises ((d377aaa...))
$ git status
HEAD detached at d377aaa
nothing to commit, working tree clean

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises ((d377aaa...))
$ git checkout main
Previous HEAD position was d377aaa Implemented core functionality for a new feature
Switched to branch 'main'
Your branch is ahead of 'origin/main' by 3 commits.
  (use "git push" to publish your local commits)

Admin@DESKTOP-31KQOVP MINGW64 ~/Desktop/THE GYM/Git Advanced Exercises (main)
$

```
