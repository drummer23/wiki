# Git

## States

- **working tree** a single checkout of one version of the project

- **index** a file that stores information about what goes into next commit **staging area**

- **repository** .git directory

- **head** pointer to local branch you’re currently on

## Log

```git log —name-status```

## Tagging

show tags
```
git tag //lists all
git show v1.4
```

create tag
```
git tag [-a] v1.4  //-a for annotaded (with checksum and ..)
```

tags must be pushed to share
```
git push origin v1.5
```

checkout tag (as a branch)
```
git checkout -b version2 v2.0.0
```

## Retome

If you want to delete all branches that were deleted on server ("Sync" your branches with server), use:
```
git remote prune origin
```
