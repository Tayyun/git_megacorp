# megacorp



### Fork vs Clone

* To **Contribute** to the main line

  or

* To **Peruse** the original repo only

Make changes the cloned forked repo, Push to forked repo, Open Pull Request




### HEAD

It is stored as a _path_ to a **branch** or **tag**

> cat .git/HEAD



### RefLogs

Tracks changes (steps) of branches and other references (HEAD)

If you accidentally delete the `fix_branch`, this command can help to recover the changes you deleted together with:

> git cat-file -p <HASH>

Using the below command also provide the same result:

> git merge HEAD@{<position>}



### Multiple Merge Conflicts

**"Ours"** refers to the branch your are on (merging into)

**"Theirs"** refers to the branch being merged

​	**!! REMEMBER !!**

​	Use `git reset --hard` to undo any resolved merge commit

​	Check `git config` for `rerere.enabled` to set to false, so that the <u>previous merge conflict resolution will not be used automatically</u>



### Checkout

> megacorp main $ git checkout --theirs customers/all.csv
> Updated 1 path from the index
>
> megacorp main $ git checkout --ours orgs/partners.txt
> Updated 1 path from the index



### Rebase Conflicts

Since `rebase` perform a _checkout_ to the **target branch**, then _"replay"_ to the **source branch**, this makes:

* **"Ours"** refers to the target branch, **"Theirs"** refers to the source branch

From the example, `main` branch contains `J: ...` commit, and `fix` branch contains `I: ...` commit

1. If we are trying to rebase `fix` onto `main`, it basically means that we are rewriting history of `fix` to include all changes from `main`

2. Since we `git checkout --ours <path_to_conflict_file>`, `git add` afterward effectively removed all the changes from `I: ...`commit 

   (By choosing to keep the changes from `main`)

3.  Then we `git rebase --continue`, Git will realize that `I: ...` commit was pointless, hence removed it entirely. `git log` will not show `I: ...` commit


### Stash

It work like a "clipboard" temporary storage for your index (staging area)

> git stash <list> <pop> <apply> ...

It uses the stack data structure to handle multiple stashes
