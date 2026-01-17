🛠 Git History Identity Fixer

Don't forget to give a star

This script uses git filter-branch to programmatically scan your repository's history and replace an incorrect author/committer email and name with the correct ones.
Note for safety it does not change for other collaborators should use with precaution ensuring you have written your correct details 

⚠️ Important Warning

This operation rewrites Git history. * It will change the commit hashes for all affected commits.

If you are working in a team, colleagues will need to re-clone or rebase their work once this is pushed.

Always back up your repository or work on a fresh clone before running this.
## Installation

Run script either on terminal or create a file fix-history.sh

```bash
git filter-branch -f --env-filter '
OLD_EMAIL="xxxxxxxxxxxxxxxxxxxxxxxxxx"
YOUR_CORRECT_NAME="zzzzzzzzzzzzzzzzz"
NEW_EMAIL="yyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyy"
if [ "$GIT_COMMITTER_EMAIL" = "$OLD_EMAIL" ]
then
    export GIT_COMMITTER_NAME="$YOUR_CORRECT_NAME"
    export GIT_COMMITTER_EMAIL="$NEW_EMAIL"
fi
if [ "$GIT_AUTHOR_EMAIL" = "$OLD_EMAIL" ]
then
    export GIT_AUTHOR_NAME="$YOUR_CORRECT_NAME"
    export GIT_AUTHOR_EMAIL="$NEW_EMAIL"
fi
'  HEAD
```


    
## 🚀 How to Use
1. Edit the variables: Replace OLD_EMAIL, YOUR_CORRECT_NAME, and NEW_EMAIL with your actual details.

2. Make it executable (Terminal):
```bash
  chmod +x fix-history.sh
```
3. Run the script:
```bash
  ./fix-history.sh
```
4. Review the logs: Check git log to ensure the names and emails are now correct.
5. Force Push: Once you are 100% sure the history is correct, push the changes to the remote branch:
```bash
  git push branch --force
```


## 🔍 What this does
Allows you to modify environment variables (like author/committer details) for every commit on one branch can be modified to support all branches at once.

