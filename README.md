# Homework-1.1
Exercice 1.1. testing GIT for Master on Robotics UVIC

## **TEST OF BASICS**

In this part we are going to create a file test1, to test adding it to GIT platform, doing branches and the push and pull request.

First of all we clone the repository in our computer:

```````
$ git clone https://github.com/teresamg22/Homework-1.1.git

Clonando en 'Homework-1.1'...
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
Desempaquetando objetos: 100% (3/3), listo.
```````

Then we create the file "test1.txt" and add it to the repository, also we make a commit to indcated that we have added this file.

```````
~$ cd Homework-1.1/
~/Homework-1.1$ git add test1.txt
~/Homework-1.1$ git commit -am "Add file test1"

[master 2f1b8ea] Add file test1
 1 file changed, 1 insertion(+)
 create mode 100644 test1.txt
```````
After that we make a push to upload the changes to the GIT platform

```
:~/Homework-1.1$ git push origin master
Username for 'https://github.com': teresamg22
Password for 'https://teresamg22@github.com': 

Contando objetos: 3, listo.
Delta compression using up to 8 threads.
Comprimiendo objetos: 100% (2/2), listo.
Escribiendo objetos: 100% (3/3), 283 bytes | 283.00 KiB/s, listo.
Total 3 (delta 0), reused 0 (delta 0)
To https://github.com/teresamg22/Homework-1.1.git
   36367d5..2f1b8ea  master -> master
```

Now, we are going to do it in the other way around, we are going to modify the file "test1.txt" in the GIT platform and use the pull instruction to download the changes in our computer.

```
~/Homework-1.1$ git pull

remote: Enumerating objects: 5, done.
remote: Counting objects: 100% (5/5), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
Desempaquetando objetos: 100% (3/3), listo.
Desde https://github.com/teresamg22/Homework-1.1
   2f1b8ea..79c811b  master     -> origin/master
Actualizando 2f1b8ea..79c811b
Fast-forward
 test1.txt | 1 +
 1 file changed, 1 insertion(+)
```

Next step is create a branch of this project and modify the file in order to check that the changes are make only in the branch and not in the master.

```
~/Homework-1.1$ git checkout -b testbranch
Cambiado a nueva rama 'testbranch'
~/Homework-1.1$ git commit -am "Add a line in test1 in testbranch branch"

[testbranch e90b411] Add a line in test1 in testbranch branch
 1 file changed, 1 insertion(+)
 
 ~/Homework-1.1$ git push origin testbranch 
Username for 'https://github.com': teresamg22
Password for 'https://teresamg22@github.com': 

Contando objetos: 3, listo.
Delta compression using up to 8 threads.
Comprimiendo objetos: 100% (2/2), listo.
Escribiendo objetos: 100% (3/3), 330 bytes | 330.00 KiB/s, listo.
Total 3 (delta 0), reused 0 (delta 0)
remote: 
remote: Create a pull request for 'testbranch' on GitHub by visiting:
remote:      https://github.com/teresamg22/Homework-1.1/pull/new/testbranch
remote: 
To https://github.com/teresamg22/Homework-1.1.git
* [new branch]      testbranch -> testbranch
```

After we check that the changes has been uploaded only in the branch and not in the master, we are going to merge the branch with the master.

```
~/Homework-1.1$ git merge testbranch 

Actualizando 79c811b..e90b411
 test1.txt | 1 +
 1 file changed, 1 insertion(+)

~/Homework-1.1$ git push origin master
Username for 'https://github.com': teresamg22
Password for 'https://teresamg22@github.com': 
Total 0 (delta 0), reused 0 (delta 0)
To https://github.com/teresamg22/Homework-1.1.git
   79c811b..e90b411  master -> master
```

Also we could eliminate the branch and see in which status is, in this case it is updated and we don't need to make futher actions

```
~/Homework-1.1$ git branch -d testbranch 
Eliminada la rama testbranch (era e90b411)..
teresa@teresa-Inspiron-5570:~/Homework-1.1$ git status

En la rama master
Tu rama está actualizada con 'origin/master'.

```

```
