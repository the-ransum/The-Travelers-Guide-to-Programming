# Example Scenarios

**Table of Contents**

- [Change the branch from one name to another name](#change-the-branch-from-one-name-to-another-name)
- [Replace the committer info for a specific commit](#replace-the-committer-info-for-a-specific-commit)
- [Replace the committer info for all commits](#replace-the-committer-info-for-all-commits)

## Change the branch from one name to another name

For the following examples, we will assume the current branch name is **naughtybranch**, and we actually meant to name the branch **correctbranch**.

First, we will need to create a new branch with the 
Rename the Git branch locally with the git branch -m new-branch-name command
Rename the Git branch locally with the git branch -m new-branch-name command


## Replace the committer info for a specific commit

For the following, lets assume for exposition sake that the commit we want to change the author is `03f482d6` and the commit with the new author is `42627abe`.

1. Checkout the commit we are trying to modify.
```
git checkout 03f482d6
```

2. Make the author change.
```
git commit --amend --author "NEW_AUTHORS_NAME <NEW_AUTHORS_EMAIL>"
```

3. Checkout the original branch.

4. Replace the old commit with the new one locally.
```
git replace 03f482d6 42627abe
```

5. Rewrite all future commits based on the replacement.
```
git filter-branch -- --all
```

Alternatively, for steps 4-5 you can just rebase onto new commit:
```
git rebase -i 42627abe
```

6. Remove the replacement for cleanliness.
```
git replace -d 03f482d6
```

7. Push the new history (only use --force if the below fails, and only after sanity checking with `git log` and/or `git diff`).
```
git push --force-with-lease
```

Now we have a new commit with hash assumed to be `42627abe`.


## Replace the committer info for all commits

You can run the following, after adjusting the variables accordingly -
```
git filter-branch --env-filter '
WRONG_EMAIL="incorrect@example.com"
NEW_NAME="John Doe"
NEW_EMAIL="correct@example.com"

if [ "$GIT_COMMITTER_EMAIL" = "$WRONG_EMAIL" ]; then
	export GIT_COMMITTER_NAME="$NEW_NAME"
	export GIT_COMMITTER_EMAIL="$NEW_EMAIL"
fi
if [ "$GIT_AUTHOR_EMAIL" = "$WRONG_EMAIL" ]; then
    export GIT_AUTHOR_NAME="$NEW_NAME"
    export GIT_AUTHOR_EMAIL="$NEW_EMAIL"
fi
' --tag-name-filter cat -- --branches --tags --allow-unrelated-histories
```

Then push the corrected history to remote.
```
git push --force --tags origin 'refs/heads/*'
```

Or you can push the selected refs to a specific branches.
```
git push --force --tags origin 'refs/heads/develop'
```