# Git Practice introduce

Git is a free and open source distributed version control system designed to handle everything from small to very large projects with speed and efficiency.

Git is easy to learn and has a tiny footprint with lightning fast performance. It outclasses SCM tools like Subversion, CVS, Perforce, and ClearCase with features like cheap local branching, convenient staging areas, and multiple workflows.

We can learn the general knowledge on[GIT](https://git-scm.com/)
We can get the detail information about git on the [GIT pro](https://git-scm.com/book/en/v2)



##1.Installation
   
* Linux

`$ sudo apt-get install git-all`

* Mac
`$ git`
If you don't have it, OSX will ask you to install XCode Developer tools.
If you want a new version download it from the main Git site and install like any other mac app.


* Windows

The best way to get started on Windows is to download Github for Windows


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


## 5. Reference

* [guide from fab academy ](http://fabacademy.org/2018/recitations/version-control.html#60) 
* [SSH key](https://docs.gitlab.com/ce/ssh/README.html)
* [Git Cheat Sheet 中文版](https://github.com/sindresorhus/awesome) 






