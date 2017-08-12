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

<pre>
# cd path/projectB
# git remote add projectA path/to/projectA or URI
# git fetch projectA
# git merge --allow-unrelated-histories projectA/master
# git remote remove projectA
</pre>
