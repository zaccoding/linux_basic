## Rebase  

> maste 브랜치와 hotfix 브랜치 구조  

<table>
  <tr>
    <td>브랜치</td>
    <td>파일</td>
    <td>파일 안 코드</td>
    <td>커밋 메시지</td>
  </tr>

  <tr>
    <td>master</td>
    <td>hello.py</td>
    <td>
      print("Hello World")<br>
      print("Hello World 2")
    </td>
    <td>
      Hello World <br />
      Hello World2
    </td>
  </tr>

  <tr>
    <td>hotfix1</td>
    <td>hello.py</td>
    <td>
      print("Hello World")<br>
      print("Tell Your World")
    </td>
    <td>
      Tell Your World
    </td>
  </tr>

  <tr>
    <td>hotfix2</td>
    <td>hello.py</td>
    <td>
      print("Hello World")<br>
      print("Hello World 2")<br>
      print("Tell His World")
    </td>
    <td>
      Tell His World
    </td>
  </tr>

  <tr>
    <td>hotfix3</td>
    <td>hello.py</td>
    <td>
      print("Hello World")<br>
      print("Hello World 2")<br>
      print("Tell Her World")
    </td>
    <td>
      Tell Her World
    </td>
  </tr>
</table>

> 초기 브런치 상태  

![rebase init-branches](https://user-images.githubusercontent.com/25560203/49565361-47211480-f96a-11e8-8ffa-0c6271d374d1.png)  

> Rebase 없이 merge  

![rebase merge-without-rebase](https://user-images.githubusercontent.com/25560203/49565535-d3cbd280-f96a-11e8-8fca-9604f671b48e.png)

> Rebase 후 merge  

![rebase merge-with-rebase](https://user-images.githubusercontent.com/25560203/49565857-0629ff80-f96c-11e8-9909-df39a8c879d3.png)

> e.g) hotfix1 merge  


1. hotfix1 브런치로 변경

```
$ git checkout hotfix1
Switched to branch 'hotfix1'
```

2. master 브런치를 rebase  

```
$ git rebase master
First, rewinding head to replay your work on top of it...
Applying: Tell Your World
error: Failed to merge in the changes.
Using index info to reconstruct a base tree...
M       hello.py
Falling back to patching base and 3-way merge...
Auto-merging hello.py
CONFLICT (content): Merge conflict in hello.py
Patch failed at 0001 Tell Your World
The copy of the patch that failed is found in: .git/rebase-apply/patch

Resolve all conflicts manually, mark them as resolved with
"git add/rm <conflicted_files>", then run "git rebase --continue".
You can instead skip this commit: run "git rebase --skip".
To abort and get back to the state before "git rebase", run "git rebase --abort".
```  

3. 충돌 해결  

```
Administrator@DESKTOP-497E2KO MINGW64 /f/rebase-test2 (hotfix1|REBASE 1/1)
$ git status
rebase in progress; onto 4b9daae
You are currently rebasing branch 'hotfix1' on '4b9daae'.
  (fix conflicts and then run "git rebase --continue")
  (use "git rebase --skip" to skip this patch)
  (use "git rebase --abort" to check out the original branch)

Unmerged paths:
  (use "git reset HEAD <file>..." to unstage)
  (use "git add <file>..." to mark resolution)

        both modified:   hello.py

no changes added to commit (use "git add" and/or "git commit -a")

Administrator@DESKTOP-497E2KO MINGW64 /f/rebase-test2 (hotfix1|REBASE 1/1)
$ vi hello.py

Administrator@DESKTOP-497E2KO MINGW64 /f/rebase-test2 (hotfix1|REBASE 1/1)
$ git add .
```  

4. RABSE Continue  

```
$ git rebase --continue
Applying: Tell Your World

Administrator@DESKTOP-497E2KO MINGW64 /f/rebase-test2 (hotfix1)
$
```
