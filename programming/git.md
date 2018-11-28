# Git

## Rename a local and remote branch in git

1. Rename your local branch

        git branch -m old_branch new_branch

2. Push the new branch, set local branch to track the new remote
        
        git push --set-upstream origin new_branch 

3. Delete the old branch

        git push origin -d :old_branch
