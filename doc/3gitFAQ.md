# Git FAQ




git@gitlab.com:nex-fab/guide-book.git


1. git config 

```
$ git config user.name "Bob Wu"
fatal: not in a git directory
```
solution:

```
$ git init 
$ git config user.email “email@test.com” 
```
[reference information](https://blog.csdn.net/Esc_Tab_End/article/details/84144063)

2.git push

```
$ git push
fatal: No configured push destination.
Either specify the URL from the command-line or configure a remote repository using
 
    git remote add <name> <url>
 
and then push using the remote name
 
    git push <name>
```
solution:

```
$ git remote add origin 'remote url'
$ git push -u origin   'remote branch , for example master'
 
``` 
 next time ,you can direct operate
 
 
```  
$ git add --all
$ git commit -m "note"
$ git push

``` 
[reference](https://blog.csdn.net/COCOLI_BK/article/details/97921497)


3. 　git pull

``` 

git pull origin master
fatal: 'origin' does not appear to be a git repository
fatal: Could not read from remote repository.

Please make sure you have the correct access rights
and the repository exists.
``` 
solution : we need connect remote as origin 

`git remote add origin git@github:bx_reader/bx-reader-api.git`


``` 

douboydeMacBook-Pro-3:nexfab douboy$ git remote add origin git@gitlab.com:nex-fab/guide-book.git
douboydeMacBook-Pro-3:nexfab douboy$ git pull origin master
Enter passphrase for key '/Users/douboy/.ssh/id_rsa': 
remote: Enumerating objects: 130, done.
remote: Counting objects: 100% (130/130), done.
remote: Compressing objects: 100% (74/74), done.
remote: Total 130 (delta 58), reused 103 (delta 43), pack-reused 0
Receiving objects: 100% (130/130), 903.89 KiB | 60.00 KiB/s, done.
Resolving deltas: 100% (58/58), done.
From gitlab.com:nex-fab/guide-book
 * branch            master     -> FETCH_HEAD
 * [new branch]      master     -> origin/master

``` 


