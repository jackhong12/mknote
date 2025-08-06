# git

## Rebase

`git rebase` is a powerful command that allows you to integrate changes from
one branch into another by moving or combining a sequence of commits.

```
A---B---C---E (master) <- other's change
         \
          D (new-feature) <- your change
```

For example, if you have a branch `new-feature` that you want to rebase onto the
`master` branch, you can do so with the following command:

```bash
$ git branch
  main
* new-feature

$ git rebase master
```

After running the rebase command, Git will take the commits from `new-feature`

```
A---B---C---E---D'
```

### Resolve Conflicts

There may be conflicts during the rebase process. If this happens, Git will
pause. You can resolve the conflicts by editing the files, then rebase again:

1. Find the files with conflicts.

    ```bash
    $ git status
    Unmerged paths:
      (use "git add <file>..." to mark resolution)

            both modified:   <conflicted file>
    ```

2. Edit the files to resolve the conflicts. The conflicts will be marked in the files.

    ```diff title="conflicted file"
    <<<<<<< HEAD
    Your changes
    =======
    Changes from the branch you are rebasing onto
    >>>>>>> master
    ```

3. Add the resolved files and rebase again.

    ```bash
    $ git add <conflicted file>
    $ git rebase --continue
    ```
