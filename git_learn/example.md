# E.g : Clone to local repository

```#mkdir /git/linux-git-learn```  
```#cd /git/linux-git-learn```  
```#git init```  
```#git remote add origin URL```  
```#git pull orign```  
```#git checkout master```  


# E.g : Remove remote files except local file

```#git rm -r --cached bin```  
```#git commit -m "remove bin dir"```  
```#git push origin master```

```[root@localhost linux-git-learn]# git rm -r --help
usage: git rm [options] [--] <file>...

    -n, --dry-run         dry run
    -q, --quiet           do not list removed files
    --cached              only remove from the index
    -f, --force           override the up-to-date check
    -r                    allow recursive removal
    --ignore-unmatch      exit with a zero status even if nothing matched
```


# E.g : Merge projectA into projectB

> Summary

<pre>
# cd path/projectB
# git remote add projectA path/to/projectA or URI
# git fetch projectA
# git merge --allow-unrelated-histories projectA/master
# git remote remove projectA
</pre>

**Example**  

> Dir tree

```
projectA
  - projectA.md
projectB
  - projectB.md
```

> Commit history

```
```

> move projectB & add remote

```
$ cd projectB/
$ git remote add projectA https://github.com/zacscoding/projectA.git
$ git remote -v
origin  https://github.com/zacscoding/projectB.git (fetch)
origin  https://github.com/zacscoding/projectB.git (push)
projectA        https://github.com/zacscoding/projectA.git (fetch)
projectA        https://github.com/zacscoding/projectA.git (push)
```

> fetch

```
$ git fetch projectA
warning: no common commits
remote: Counting objects: 3, done.
remote: Total 3 (delta 0), reused 3 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), done.
From https://github.com/zacscoding/projectA
 * [new branch]      master     -> projectA/master

$ git remote -v
origin  https://github.com/zacscoding/projectB.git (fetch)
origin  https://github.com/zacscoding/projectB.git (push)
projectA        https://github.com/zacscoding/projectA.git (fetch)
projectA        https://github.com/zacscoding/projectA.git (push) 
```

> merge

```
$ git merge --allow-unrelated-histories projectA/master
Merge made by the 'recursive' strategy.
projectA.md | 1 +
1 file changed, 1 insertion(+)
create mode 100644 projectA.md

$ ll
total 2
-rw-r--r-- 1 Administrator 197121 26 12월 23 01:52 projectA.md
-rw-r--r-- 1 Administrator 197121 24 12월 23 01:48 projectB.md
```

> remove remote projectA

```
$ git remote remove projectA
Administrator@DESKTOP-CDEHV93 MINGW64 ~/git/projectB (master)

$ git remote -v
origin  https://github.com/zacscoding/projectB.git (fetch)
origin  https://github.com/zacscoding/projectB.git (push)
```

> push remote projectB

```
$ git push origin
Counting objects: 5, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (3/3), done.
Writing objects: 100% (5/5), 526 bytes | 0 bytes/s, done.
Total 5 (delta 0), reused 0 (delta 0)
To https://github.com/zacscoding/projectB.git
```

> Commit logs

```
$ pwd
...path/git/projectB

$ git log

commit 67649415c8db5bd9541666273d36323116ac03ad (HEAD -> master, origin/master)
Merge: 9af593d 1f01a86
Author: zaccoding <zaccoding725@gmail.com>
Date:   Sat Dec 23 01:52:56 2017 +0900

Merge remote-tracking branch 'projectA/master'

commit 9af593d891bfc928318cdfc08541014857e4dade
Author: zaccoding <zaccoding725@gmail.com>
Date:   Sat Dec 23 01:48:48 2017 +0900

create projectB

commit 1f01a86d03156b07c296d7149868d39b62c86147
Author: zaccoding <zaccoding725@gmail.com>
Date:   Sat Dec 23 01:47:06 2017 +0900

create porjectA

$ cd ../projectA
$ pwd
path../git/projectA
$ git log
commit 1f01a86d03156b07c296d7149868d39b62c86147 (HEAD -> master, origin/master)
Author: zaccoding <zaccoding725@gmail.com>
Date:   Sat Dec 23 01:47:06 2017 +0900

create porjectA
```

---
