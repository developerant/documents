# Git

### Standard setup

```bash
git init

git add .
```

```bash
git commit -m "commit message"
```

or git commit followed by typing message and :wq in vi

### Other Commands

Show origin
```bash
git remote show origin
```

Assume Unchanged a file
```bash
git update-index --assume-unchanged path/to/file.m
```

Undo
```bash
git update-index --assume-unchanged path/to/file.m
```

Pull with rebase
```bash
git pull --rebase
```

Push with tags:
```git tag <release_tag>```
then
```git push --tags```


Sources: https://confluence.atlassian.com/bitbucket/reduce-repository-size-321848262.html


Remove a file, and from git index/history
```bash
git rm --cached <file>
```
This answer ignores changes to the file that is in the repository whilst not removing it from the repository.

Very important adding. If file that is ignored would be modified (but in spite of this should be not committed), after modifying and executing git add . it would be added to index. And next commit would commit it to repository.

To avoid this execute right after all that said one more command:

Don't show file in unstaged changes - independent of gitignore:

```--assume-unchanged``` for performance to prevent git to check status of big tracked files
```bash
git update-index --assume-unchanged <file>
```

```--skip-worktree``` for modified tracked files that the user don't want to commit anymore and keep
```bash
git update-index --skip-worktree <file>
```

Undo the above
```bash
git update-index --no-assume-unchanged <file>
```


Remove from history
```bash
git filter-branch -f --index-filter "git rm -rf --cached --ignore-unmatch public/wp-content/uploads.zip" -- --all
```


Remove all ignored files
```bash
git rm -r --cached . 
git add .
git commit -am "Remove ignored files"
```

List out all files from a commit
```bash
git diff-tree --no-commit-id --name-only -r bd61ad98
```

The --no-commit-id suppresses the commit ID output.
The --pretty argument specifies an empty format string to avoid the cruft at the beginning.
The --name-only argument shows only the file names that were affected (Thanks Hank).
The -r argument is to recurse into sub-trees


See repo size
```bash
git count-objects -v 
```

To fix: this is larger than GitHub's recommended maximum file size of 50 MB
```
git filter-branch -f --index-filter "git rm -rf --cached --ignore-unmatch FILEORFOLDERNAME" -- --all
```

### Delete Branch
```git branch -D branch-name```

Prune all of the reflog references from the branch on back.
git reflog expire --expire=now branch-name

## Git repo maintenance

Clean git repo - clean Garbage repository
```bash
git gc --auto
```

Find out sie of the git folder
```bash
du -hs .git/objects
```

For removing directory
```git filter-branch --index-filter 'git rm --cached --ignore-unmatch pathname' ```commitHASH

For removing file
```git filter-branch --index-filter 'git rm --cached --ignore-unmatch filename' HEAD```


```--index-filter``` option modifies a repo's staging (or index).
```--cached``` option removes a file from the index not the disk.  This is faster as you don't have to checkout each revision before running the filter. 
```--ignore-unmatch``` option in git rm prevents the command from failing if the pathname it is trying to remove isn't there. 
By specifying a commit HASH, you remove the pathname from every commit starting with the HASH on up.  To remove from the start, leave this off or you can specify HEAD.  
If all your large files are in different branches, you'll need to delete each file by name. If all the files are within a single branch,  you can delete the branch itself.


Update the references in your repository. filter-branch creates backups of your original refs namespaced under refs/original/. Once you're confident that you deleted the correct files, you can run the following command to delete the backed up refs, allowing the large objects to be garbage collected:
```git for-each-ref --format="%(refname)" refs/original/ | xargs -n 1 git update-ref -d```


### Garbage collecting dead data

Prune all of the reflog references from now on back (unless you're explicitly only operating on one branch):
```git reflog expire --expire=now --all```

Repack the repository by running the garbage collector and pruning old objects.
```git gc --prune=now```

Push changes:
```git push --all --force```


