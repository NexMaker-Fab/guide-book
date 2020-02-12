# git FAQ




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


