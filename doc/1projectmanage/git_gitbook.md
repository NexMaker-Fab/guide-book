# Gitbook for webpage
We would use the following tool to build our own webpage
* [Git](https://git-scm.com/) is used to control our version in gitlab;
* [Gitlab](https://gitlab.com/) is used as a servicer for our webpage;
* [Gitbook](https://www.gitbook.com/) is a style for our webpage;
* [Markdown  language](https://www.nexmaker.com/doc/1projectmanage/markdown.html) to write our document;
* [Image upload service](https://www.nexmaker.com/doc/1projectmanage/imageuploadservice.html) to storage our image on cloud and used in markdwon document;

#### Tool 

* [Git](https://git-scm.com/downloads),mac don't need to install,it use to setting git and gitlab;
* [Nodejs](https://nodejs.org/en/) ,it use to setting environment for gitbook;
* [VScode](https://code.visualstudio.com/) for write document;
* [Picgo image upload service](https://github.com/Molunerfinn/PicGo/releases/tag/v2.2.2);it is used to storage picture in gitlab;





**Git Practice introduce**

Git is a free and open source distributed version control system designed to handle everything from small to very large projects with speed and efficiency.

Git is easy to learn and has a tiny footprint with lightning fast performance. It outclasses SCM tools like Subversion, CVS, Perforce, and ClearCase with features like cheap local branching, convenient staging areas, and multiple workflows.

We can learn the general knowledge on[Git](https://git-scm.com/)
We can get the detail information about git on the [Git pro](https://git-scm.com/book/en/v2)



## 1.Installation
   
* Linux

`$ sudo apt-get install git-all`

* Mac
`$ git`
If you don't have it, OSX will ask you to install XCode Developer tools.
If you want a new version download it from the main Git site and install like any other mac app.


* Windows

The best way to get started on Windows is to download Git from [git web](https://git-scm.com/downloads) for Windows and install it.Now we can open [GUI BASH](https://gitforwindows.org/).


##2.Configure,setting up local identity

Configure user's name, user's email ,in our case, it connect with gitlab

```
$ git config user.name "XXX"  
$ git config user.email "XXX@xx.com": 

```  
"mkdir" used to build a new folder; "touch"used to build a new file; "cd" used to open local file

`$ cd /Users/douboy/Documents/nexfab  `   
Initialized empty Git repository
`$ git init   `  
`Initialized empty Git repository in /Users/douboy/Documents/nexfab`


##3.Clone

` $ git clone git@gitlab.com:nex-fab/guide-book.git `
"git@gitlab.com:nex-fab/guide-book.git"get from gitlab
![](https://github.com/bobwu0214/dm360.github.io/raw/master/Img/gitc.png)

* If Ok , we will find the following information

``` 
douboydeMacBook-Pro-3:nexfab douboy$ git clone git@gitlab.com:nex-fab/guide-book.git
Cloning into 'guide-book'...
The authenticity of host 'gitlab.com (35.231.145.151)' can't be established.
ECDSA key fingerprint is SHA256:HbW3g8zUjNSksFbqTiUWPWg2Bq1x8xdGUrliXFzSnUw.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added 'gitlab.com,35.231.145.151' (ECDSA) to the list of known hosts.
Enter passphrase for key '/Users/douboy/.ssh/id_rsa': 
remote: Enumerating objects: 74, done.
remote: Counting objects: 100% (74/74), done.
remote: Compressing objects: 100% (37/37), done.
remote: Total 74 (delta 34), reused 64 (delta 28), pack-reused 0
Receiving objects: 100% (74/74), 7.37 KiB | 943.00 KiB/s, done.
Resolving deltas: 100% (34/34), done.
```
* But if we get the following

```
Cloning into 'guide-book'...
git@gitlab.com: Permission denied (publickey).
fatal: Could not read from remote repository.

Please make sure you have the correct access rights
and the repository exists.
```
The problem is [SSH key](https://docs.gitlab.com/ce/ssh/README.html)，check  if we have generate SSH
   
`$ ls ~/.ssh/`
There will be two result:
Result1: we have the following information 
`id_rsa		id_rsa.pub	known_hosts`
we can skip "generate SSH"
Result2:  no above information, we should  "generate SSH"

```
ssh-keygen -t rsa -C  "your email"
Generating public/private rsa key pair.
Enter file in which to save the key (/Users/douboy/.ssh/id_rsa): (/Users/douboy/.ssh/id_rsa)
Created directory '/Users/douboy/.ssh'.
Enter passphrase (empty for no passphrase):   "your passphase"
Enter same passphrase again:    "your passphase"
Your identification has been saved in /Users/douboy/.ssh/id_rsa.
Your public key has been saved in /Users/douboy/.ssh/id_rsa.pub.
The key fingerprint is:
SHA256:5jNxNnUyxu6JL+UmowRyaPgTFswLhovHd3rbRqDjXqc bob@nexpcb.com
The key's randomart image is:
+---[RSA 2048]----+
|                 |
| . o       .     |
|. o +       * .  |
|.+ o +.    + +   |
|o + O.+.S + .    |
| . =o* +.+ +..   |
|   .+.o.* .oo    |
|    .+ *.o+.o    |
|   .. E.o. =.    |
+----[SHA256]-----+
```

* Check the SSH key and copy to gitlab

```
$ cat ~/.ssh/id_rsa.pub
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDCyoT5ifhVJLXYGzFIcZuLRWtjehKA/lQyLPDVwENvPAmo9j2MnhTJA99mEefabs/MYz5wJwHMRtpAUgVGoHi+tY69K7PUYspZhFlbJ6YS7DDHpcoQpQCdDra3jrYLrhsS2fcPmEZjhqv37uE3NOVU4ceng/qIqt178Bp3F2J2p3qL0i0yZ0hQz6rsJfuvUyNvD/OsKPsCzYNtiHRX8maDY91e/jb8VSfNMznVHJXzWnVLJAiF8VDlVCQoutOtEnoApKKXvTd2vOue7kepNAB+1Sji+A9NnerKkLHy5JCJ7qalmqUhS6cPn9P1+NhH9W9n9PjmT4AACxTwKCLIPuZP bob@nexpcb.com
```

![](https://github.com/bobwu0214/dm360.github.io/raw/master/Img/WechatIMG54.png)

* git clone again

```
douboydeMacBook-Pro-3:nexfab douboy$ git clone git@gitlab.com:nex-fab/guide-book.git
Cloning into 'guide-book'...
The authenticity of host 'gitlab.com (35.231.145.151)' can't be established.
ECDSA key fingerprint is SHA256:HbW3g8zUjNSksFbqTiUWPWg2Bq1x8xdGUrliXFzSnUw.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added 'gitlab.com,35.231.145.151' (ECDSA) to the list of known hosts.
Enter passphrase for key '/Users/douboy/.ssh/id_rsa': 
remote: Enumerating objects: 74, done.
remote: Counting objects: 100% (74/74), done.
remote: Compressing objects: 100% (37/37), done.
remote: Total 74 (delta 34), reused 64 (delta 28), pack-reused 0
Receiving objects: 100% (74/74), 7.37 KiB | 943.00 KiB/s, done.
Resolving deltas: 100% (34/34), done.
```
Now you can get data to your local machine
![](https://github.com/bobwu0214/dm360.github.io/raw/master/Img/floder.png)



## 4. Command


* Git pull :  download gitlab to local

`$ git pull `

* Build new folder

` $ mkdir /Users/douboy/Documents/nexfab/pic`

![](https://github.com/bobwu0214/dm360.github.io/raw/master/Img/addpng.png)

* Remove  floder or file
` $ git rm -r /Users/douboy/Documents/nexfab/guide-book/pic`

* git add new file: Tracking new files

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


* Staging files: git add, git commit

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

* git diff:Edit one or more files, then check what you changed since the last commit

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



* git log:Looking at the commit history



* git push:   Push the local data to gitlab


## 5.Gitbook

This document will show us how to setting gitbook document for ever member.

we can reference the following two document:
* [gitbook from gitlab](https://gitlab.com/pages/gitbook)
* [gitbook practice from bob](http://archive.fabacademy.org/2018/labs/fablaboshanghai/students/bob-wu/Fabclass/week2_project_management/gitbook.html)

**gitlab-ci.yml**
```

# requiring the environment of NodeJS 8.9.x LTS (carbon)
image: node:10.18

# add 'node_modules' to cache for speeding up builds
cache:
  paths:
    - node_modules/ # Node modules and dependencies

before_script:
  - npm install npm@latest -g # install latest npm
  - npm install gitbook-cli -g # install gitbook
  #- gitbook fetch latest # fetch latest stable version
  - gitbook install # add any requested plugins in book.json
  - gitbook fetch pre # fetch latest pre-release version
  #- gitbook fetch 2.6.7 # fetch specific version

# the 'pages' job will deploy and build your site to the 'public' path
pages:
  stage: deploy
  script:
    - gitbook build . public # build to public path
  artifacts:
    paths:
      - public
  only:
    - master # this job will affect only the 'master' branch

```

## 6. Git QA

**6.1 git config**

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

**6.2 git push**

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


**6.3　git pull**

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

**6.4 go back to old edition**
Some time we would have the problem that our new edition would broken ,so we want to go former edition,there are many method.The below will introduce one method

``` 
$git log    //we can now many old edition make sure which edition we need to go back 
$ git checkout add34          //go back  to old edition "commit add3492c"
$ git branch check                 //add new branch "check"
$ git branch                     // check the branch status, we can ignore if we now the logic
* (HEAD detached at add3492)
  check
  master

  //next step is use check(the old eidtion"add3492c" we want to go back) content to cover master (the new broken edition )
$ git branch -D master            //delete old edition
Deleted branch master (was 952de05).
$ git branch master               // re- add branch "master"
$ git checkout master             //covery  
M	guide-book
Switched to branch 'master'
$ git branch 
  check
* master
$ git branch -D check                 //delete history
Deleted branch check (was add3492).
$ git branch
* master
$ git add --all
$ git commit -m "branch"
$ git push origin master -f

``` 



## 7. Reference

* [guide from fab academy ](http://fabacademy.org/2018/recitations/version-control.html#60) 
* [SSH key](https://docs.gitlab.com/ce/ssh/README.html)
* [Git Cheat Sheet 中文版](https://github.com/sindresorhus/awesome) 






