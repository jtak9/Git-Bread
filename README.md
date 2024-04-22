This is a demo to showcase some advanced git functions using a loaf of bread.

             ________________             
           /               / )
          /               /  |
         /_____________  /   |
       (                )    /
        |              |    /         👍
        |              |   /
        |              |  /
        | ____________ | /

**THIS DEMO SHOULD BE PERFORMED WITHOUT ANY PUSHING OR MERGING TO THE REMOTE REPO**
**THIS DEMO IS ONLY DONE LOCALLY**

Initial Setup:
1. You can clone the repo and open it locally on your IDE of choice or press '.' (period) key on this repo to open VS Code Web Editor and then begin a GitHub Codespace in the terminal.
2. The 'ingredients' file contains some food emojis that will be used during this demo. Just copy and paste to any bread file when directed to. Adjust the borders of any loaf as you see fit.
3. The commit messages are just suggestions, they can be anything related to the current work.

------------------------------------
DEMO WALKTHROUGH (DO THESE IN ORDER)
------------------------------------
1. GIT ALIASES (creates a shortcut that can be used to perform actions without having to write the original commands i.e. 'ac' for adding and committing files)
   1. Use command 'git config --global alias.ac "commit -m"' in the terminal (make sure you're on the main branch and 'freshloaf' file)
   2. This command creates an alias called 'ac' that handles the act of adding and committing to save time
   3. Stay on the main branch and copy and add bananas from the 'ingredients' file to the 'freshloaf'
   4. Use command 'git ac "added bananas to fresh loaf"' and it should auto add and commit the file with added bananas

2. GIT STASH (takes a snapshot of your current work and returns you to clean work directory, the stash can be reintroduced when you come back to work on it)
   1. Stay on main branch and add avocados from 'ingredients' file to the fresh loaf
   2. Use command 'git stash' to save your work on the main branch
   3. Use command 'git checkout -b garlic' to create and checkout to new branch called 'garlic'
   4. Add garlic from 'ingredients' file to the fresh loaf and use 'git ac "made some garlic bread"'
   5. Use command 'git checkout main' to switch back to the main branch
   6. Use command 'git stash pop' to reintroduce your WIP to the current file in main branch
   7. Use command 'git ac "made avocado toast"' to commit the fresh loaf that you added avocados to in step 1.

3. GIT REVERT (removes the changes made in the last commit or any commit (as long as the hash is provided) and adds a new 'revert' commit that contains the removal of said commit)
   1. Copy 'sliceofbread' and replace the contents in the 'freshloaf' file
   2. Use command 'git ac "reduced loaf to a single slice of bread"' in terminal
   3. Use command 'git log' to see list of commits (type 'q' to quit)
   4. Copy the hash of the most recent commit in the log
   5. Use command 'git revert "that copied hash"' to perform a git revert that removes the changes of the last commit
   6. A file containing the commit message will show up, save it and close it
   7. Use command 'git log' again to see the new revert commit (the commit that you wanted to revert should still be in the log)

4. GIT CHERRY-PICK (takes a recent commit from one branch that can be placed into another branch, the original branch should still have the chosen commit)
   1. Make sure you're on the main branch
   2. Add cherries from 'ingredients' to fresh loaf and use 'git ac "baked some cherry bread"'
   3. Turns out you made a commit on the wrong branch (should be on a feature branch, instead of main)
   4. Use 'git log' and copy the hash of the most recent commit for cherry-picking
   5. Use 'git checkout -b cherries' to create and checkout to branch called 'cherries'
   6. Use 'git cherry-pick "that copied hash"' to place the commit in the cherries branch
   7. Use 'git log' to see that the commit has moved to the cherries branch
   8. The commit is still on the main branch, so use 'git checkout main' to return to main branch
   9. Use 'git reset --hard HEAD ~1' to delete the commit from the main branch

5. GIT BISECT (performs a binary search on all of your commits to narrow down the first instance of a bug in a commit)
   1. Copy contents of 'moldyloaf' file and replace the 'freshloaf' in the main branch and use 'git ac "new bread from different distributor"'
   2. Add butter from 'ingredients' and use 'git ac "added butter to odd looking bread"'
   3. Add egg from 'ingredients' and use 'git ac "added egg to kinda smelly bread"'
   4. Add carrot from 'ingredients' and use 'git ac "baked carrot bread with weird color"'
   5. Add onion from 'ingredients' and use 'git ac "baked onion bread on disgusting load"'
   6. Realize that we have been working on top of a moldy loaf (buggy code) and use 'git reflog' to copy the very first commit's hash
   7. Use 'git bisect start' to begin the binary search. 'git bisect reset' can be used to restart the binary search at any time
   8. Use 'git bisect bad' to mark the most recent commit as the 'bad' commit
   9. Use 'git bisect good "the first commit hash"' to mark the first commit made as the 'good' commit
   10. If done correctly, it should show the commit of step 1 and that is the target with the start of "buggy code"
   11. Here you would get rid of any buggy code in your own projects (don't need to do anything for this demo)
  
6. GIT REBASE (combines all or chosen commits on a feature branch to a single commit that can be merged into the main branch)
   1. Use 'git checkout garlic' to return to the 'garlic' branch
   2. Use 'git fetch origin' to update the branch with most recent version of main branch
   3. Add butter from 'ingredients' and use 'git ac "baked garlic bread with butter"'
   4. Use 'git rebase main --interactive' to start the rebase
   5. A file containing your commits should open. Change every commit besides the top commit, the word 'pick' to 'squash'. 'squash' is used to combine all messages.
   6. Save and close the file
   7. Another file should open showing all the commit messages and what was chosen for rebasing
   8. Save and close the file
   9. Use 'git checkout cherries' to return to the 'cherries' branch
   10. Use 'git fetch origin' to update the feature branch
   11. Add more cherries to the loaf and use 'git ac "baked bread with extra cherries"'
   12. Use 'git rebase main --interactive' to start rebasing
   13. This time, write 'fixup' in place of every 'pick' besides the top commit. 'fixup' is used if you don't want to combine all messages.
   14. Save and close the file
   15. The rebase should happen automatically this time (no other file opens). Sometimes you can run into a merge conflict, so make sure to resolve any conflicts 

7. GIT 'PRETTY LOGS' AND REFLOG ('pretty logs' just show your log with colored branches, shortened hashes. 'reflog' is similarly a condensed version of traditional log)
   1. Use 'git chechout main' to return to the main branch
   2. Use 'git log --graph --oneline --decorate' to see 'pretty logs'
   3. The log doesn't look very impressive, so look up other examples online or use on personal project
   4. Use 'git reflog' to see a condensed version of a git log. 'reflog' stands for 'reference log' and is used for quick checking of what work has been made so far

8. GIT RESET (powerful command that usually shouldn't be used, but can be used to restart all work on a project)
   1. Use 'git reset --hard origin/main' to get rid of all work done so far
   2. This only cleaned the work on your local copy of the project, the repo should be untouched

**THIS IS THE END OF THE DEMO**
  
-------------------------------------------------------------------------------------------------------
