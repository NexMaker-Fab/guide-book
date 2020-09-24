## Basic introduce

Git is a free and open source distributed version control system designed to handle everything from small to very large projects with speed and efficiency.

Git is easy to learn and has a tiny footprint with lightning fast performance. It outclasses SCM tools like Subversion, CVS, Perforce, and ClearCase with features like cheap local branching, convenient staging areas, and multiple workflows.

We can learn the general knowledge on[GIT](https://git-scm.com/)
We can get the detail information about git on the [GIT pro](https://git-scm.com/book/en/v2)




## Basic practice



1.Installation
   
* Linux

`$ sudo apt-get install git-all`

* Mac
![](https://ws4.sinaimg.cn/large/006tKfTcgy1fo87udug63j31kw0uye81.jpg)

`$ git`
If you don't have it, OSX will ask you to install [XCode Developer tools:command line tools](developer.apple.com/download/).

If you want a new version download it from the main Git site and install like any other mac app.


* Windows

The best way to get started on Windows is to download Github for Windows


2.Configure,setting up local identity

Configure user's name, user's email ,in our case, it connect with gitlab

```
$ git config user.name "XXX"  
$ git config user.email "XXX@xx.com": 

```  
"mkdir" used to build a new folder; "touch"used to build a new file; "cd" used to open local file

`$ cd /Users/douboy/Documents/gitlab  `   
Initialized empty Git repository
`$ git init   `  
`Initialized empty Git repository in /Users/douboy/Documents/gitlab`


3.Clone ,pull


``` 
$ douboydeMacBook-Pro:gitlab douboy$ git clone git@gitlab.fabcloud.org:academany/fabacademy/2018/labs/fablaboshanghai/students/bob-wu.git
Cloning into 'bob-wu'...
remote: Counting objects: 670, done.
remote: Compressing objects: 100% (48/48), done.
remote: Total 670 (delta 64), reused 91 (delta 55)
Receiving objects: 100% (670/670), 6.55 MiB | 1.11 MiB/s, done.
Resolving deltas: 100% (378/378), done.
$ douboydeMacBook-Pro:bob-wu douboy$ git pull origin master
From gitlab.fabcloud.org:academany/fabacademy/2018/labs/fablaboshanghai/students/bob-wu
 * branch            master     -> FETCH_HEAD
Already up-to-date. 

```
![](https://ws1.sinaimg.cn/large/006tKfTcgy1fo8x9f8zm9j31kw0pfna4.jpg)

git pull :  
`$ git pull origin master:`

4.git add new file: Tracking new files

`$ vi test.txt
$ git add test.txt` 

check status

```
$ vi test2.txt // or notepad, textmate, sublime, any editor
$ git status
On branch master
No commits yet
Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
    new file:   test.txt
Untracked files:
  (use "git add <file>..." to include in what will be committed)
    test2.txt
    
    ```

5.Edit file:in this part I use sublime Text to write local information

![](https://ws4.sinaimg.cn/large/006tKfTcgy1fo8x8rzjsbj31kw0z74qp.jpg)

6.Stageing files: git add,git commit

git add --all (git add -A)
git commit -m "write commit" ,you can write what you want in the part of "write commit"

```
$ git add --all
$ git commit -m "code"
[master 0611cd9] code
 1 file changed, 16 insertions(+), 16 deletions(-)
douboydeMacBook-Pro:bob-wu douboy$ git push
Counting objects: 5, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (5/5), done.
Writing objects: 100% (5/5), 642 bytes | 642.00 KiB/s, done.
Total 5 (delta 4), reused 0 (delta 0)
To gitlab.fabcloud.org:academany/fabacademy/2018/labs/fablaboshanghai/students/bob-wu.git
   d1567a2..0611cd9  master -> master
   
   ```

7.git diff:Edit one or more files, then check what you changed since the last commit

```
$ git diff test2.txt 
diff --git a/test2.txt b/test2.txt
index b0b9fc8..835f9c0 100644
--- a/test2.txt
+++ b/test2.txt
@@ -1 +1,4 @@
 Another file
+
+
+This is the new content of the file

```

8.git rm:removing files

```
$ git rm test.txt
rm 'test.txt'
$ git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)
    deleted:    test.txt
    
    ```

9.git log

```
git log: Looking at the commit history

```


10.git push:   Push the local data to gitlab

The following is the structure of local operation

![](https://ws4.sinaimg.cn/large/006tKfTcgy1fo87qzfvpzj30jg081mx3.jpg)
![](https://ws3.sinaimg.cn/large/006tKfTcgy1fo87rio118j30m80c90sy.jpg)

## advantace git
coming soon , click [the page](http://fabacademy.org/2018/recitations/version-control.html#60) for reference


## GET
After this class's learn , I basic konw the git system ,and the operation ,in the future i would practice more to get it




