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

### Change Multiple Commits

If you want to change multiple commits, you can use the `-i` (interactive) flag
with the rebase command:

```bash
$ git rebase -i HEAD~3        # Rebase the last 3 commits
$ git rebase -i <commit-hash> # Rebase from a specific commit
```

??? note "Examples"

    For example, if you have the following commit history:

    ```bash
    22186ea --- 2cae922 --- 4de22bd --- b76d5f7 --- f167f21
    ```

    If you want to change the last three commits, you can run:
    ```bash
    $ git rebase -i 2cae922
    # or
    $ git rebase -i HEAD~3
    ```

    It will open an editor with the last three commits listed. You can choose whether to pick or drop the commits:

    ```
    pick 4de22bd <message>
    drop b76d5f7 <message>
    pick f167f21 <message>
    ```

    | Action | Description                         |
    |--------|-------------------------------------|
    | `pick` | Keep the commit as is.              |
    | `drop` | Remove the commit from the history. |

    The commit `b76d5f7` will be dropped. The commit `f167f21` will be kept and be rehashed onto the previous commit. The final history will look like this:

    ```bash
    22186ea --- 2cae922 --- 4de22bd --- 1f7bf84(f167f21)
    ```

---

## Show Log

You can view the commit history of your repository using the `git log` command.
```bash
$ git log --all --graph --decorate --oneline
```

??? note "Flags"
    - `--all`: Show all branches.
    - `--graph`: Show a text-based graph of the commit history.
    - `--decorate`: Show branch names and tags.
    - `--oneline`: Show each commit on a single line.
