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
