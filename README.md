# learn2
learn how to push files to github from local git repository.

Git and GitHub 1- Introduction
Link: https://www.youtube.com/watch?v=-U-eUHI6euM

Today We will learn:
1. What is GIT
2. What is GIT HUB
3. Is GIT related to GIT HUB
4. A simple workflow

1. GIT - VCS - Version Control System
	- to track changes in files /folders
	- to collaborate in teams
	- free and open source

There are two types of GIT: Centralized VCS | Distributed VCS (DVCS)
Git = DVCS

2. GIT HUB (GIT Server) - website to upload your repositories online
	- provides backup

	- provides visual interface to your repository
	- makes collaboration easier
	- 
3. GIT != GIT HUB

4. A simple workflow show in note's documents


Tutorial 2: Installing Git
https://www.youtube.com/watch?v=0Icla6TVNNo
Step 1: Check for installing version if any: git --version (if you see command not found meaning not yet installed)

Step 2: Download and install git:

a) Windows version: https://git-for-windows.github.io/
b) https://www.atlassian.com/git/tutorials/install-git

Step 3: Signup and create a free account on GitHub - type github from google search
a) https://github.com/

Step 4: Add your github email and username to git, go to terminal and issue commands below:
	The below information is required when you commit your changes so GIT can keep track of who changes what on your local repository.
a) $ git config --global user.email "t_hooya@yahoo.com"
b) $ git config --global user.name "Tam Tran T."

Step 5: Create the repository: Add files/folders to git - tracking 
	- To add the folders to GIT, you first create folder that you want to add to GIT
	- cd to the new created folder that you want to add to GIT, issue command: git init (this could me new or existing one)
	- "git init" will create folder .git under the directory that you issue command, and git will store every under .git folder.
	- You can remove this repository by just remove this folder .git.
	- You can zip and send this .git command to anybody so they can have the local repository right away!

Step 6: Commands set that you need to work with GIT
	- git status
	- create a file that you want to check in (touch readme.txt)
	- to add file: gid add readme.txt
	- check in: git commit (without -m "comment" git will popup to ask for your comment so it can record in the log)
		+ commint -m "Initial check in for readme.txt"
	- Now, modify file1.txt
	- git status (it will show "Changes not staged for commit" message)
	- Issue command add (with flag -a) and commit with -m comment flag: git comit -a -m "checkin my first update on file1.txt"
	- Now issue "git status" again to see all clear!

Step 7: How to push files to github from local git VCS
	Create new directory from github server: https://github.com/login
	- Top right conner click on '+' -> New repository
	- under "Repository name", enter your repository name that you want.
	- from the website address bar, copy https://github.com/trantamt/learn2
	- from command line on local system, issue comamnd: git remote add origin https://github.com/trantamt/learn1.git
		+ To do this you just add the the remote repository on github server to your config files
		+ nothing has been pushed after this command yet
	- Now, issue command to push file to server github: push -u origin master (because "master" is the main branch)
		+ git will prompt you for login github server like:
			Username for 'https://github.com': trantamt
			Password for 'https://trantamt@github.com':
		+ After the push command, git on your local machine will transmit files to github server.

Note: 
for some reason you want to change the remote origin, the "giet remote add origin" does not work
C:\myrepository\learn2>git remote add origin https://github.com/trantamt/learn2.git
fatal: remote origin already exists.

List what remote origin that you currently have
C:\myrepository\learn2>git remote -v
origin  https://github.com/trantamt/tttranRepo.git (fetch)
origin  https://github.com/trantamt/tttranRepo.git (push)

This is the command to change remote origin
C:\myrepository\learn2>git remote set-url origin https://github.com/trantamt/learn2.git

C:\myrepository\learn2>git remote -v
origin  https://github.com/trantamt/learn2.git (fetch)
origin  https://github.com/trantamt/learn2.git (push)
		
---------------
FAILED to push 
---------------
C:\myrepository\learn2>git push origin master
Username for 'https://github.com': trantamt
Password for 'https://trantamt@github.com':
To https://github.com/trantamt/learn2.git
 ! [rejected]        master -> master (fetch first)
error: failed to push some refs to 'https://github.com/trantamt/learn2.git'
hint: Updates were rejected because the remote contains work that you do
hint: not have locally. This is usually caused by another repository pushing
hint: to the same ref. You may want to first integrate the remote changes
hint: (e.g., 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.

-----------------
git fetech origin
------------------
C:\myrepository\learn2>git fetch origin
remote: Counting objects: 3, done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
warning: no common commits
Unpacking objects: 100% (3/3), done.
From https://github.com/trantamt/learn2
 * [new branch]      master     -> origin/master

C:\myrepository\learn2>ls
file1.txt

-----------------
git pull origin
-----------------
C:\myrepository\learn2>git pull origin
You asked to pull from the remote 'origin', but did not specify
a branch. Because this is not the default configured remote
for your current branch, you must specify a branch on the command line.

-----------------------
git pull origin master
-----------------------
C:\myrepository\learn2>git pull origin master
From https://github.com/trantamt/learn2
 * branch            master     -> FETCH_HEAD
fatal: refusing to merge unrelated histories

----------------------------
Add this flag below in so it can merge
http://stackoverflow.com/questions/37937984/git-refusing-to-merge-unrelated-histories
--allow-unrelated-histories
----------------------------
C:\myrepository\learn2>git pull origin master --allow-unrelated-histories
From https://github.com/trantamt/learn2
 * branch            master     -> FETCH_HEAD
Merge made by the 'recursive' strategy.
 README.md | 2 ++
 1 file changed, 2 insertions(+)
 create mode 100644 README.md

Step 8: Successfully push 
C:\myrepository\learn2>git push origin master
Username for 'https://github.com': trantamt
Password for 'https://trantamt@github.com':
Counting objects: 11, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (7/7), done.
Writing objects: 100% (11/11), 3.40 KiB | 0 bytes/s, done.
Total 11 (delta 0), reused 0 (delta 0)
To https://github.com/trantamt/learn2.git
   f303299..e965ba6  master -> master
	
	- Now go to github check, you should see test1.txt files and the README file got updated
