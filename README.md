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
## TEST OF MERGE BY PULL REQUEST WITHOUT CONFLICTS 

One classmate has done a Fork of this repository and has added a line in file test1.txt. After he has asked for a pull request to merge both branches.
First from our project repository we checkout a new branch and test the changes.
```
:~/Homework-1.1$ git pull
Actualizando 2a667bc..c4fad6d
Fast-forward
 README.md | 120 ++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
 1 file changed, 120 insertions(+)

~/Homework-1.1$ git checkout -b danielvicedo-master master
Cambiado a nueva rama 'danielvicedo-master'

~/Homework-1.1$ git pull https://github.com/danielvicedo/Homework-1.1.git
remote: Enumerating objects: 5, done.
remote: Counting objects: 100% (5/5), done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 3 (delta 0), reused 3 (delta 0), pack-reused 0
Desempaquetando objetos: 100% (3/3), listo.
Desde https://github.com/danielvicedo/Homework-1.1
 * branch            HEAD       -> FETCH_HEAD
Actualizando c4fad6d..369f019
Fast-forward
 test1.txt | 3 +++
 1 file changed, 3 insertions(+)
 
 ```
 We can see that there isn't any conflict with the two branches. So we come back to master branch, merge them and we do a push to updated the repository.
 
 ``` 
~/Homework-1.1$ git checkout master
Cambiado a rama 'master'
Tu rama está actualizada con 'origin/master'.


~/Homework-1.1$ git merge --no-ff danielvicedo-master
Merge made by the 'recursive' strategy.
 test1.txt | 3 +++
 1 file changed, 3 insertions(+)

~/Homework-1.1$ git push origin master
Username for 'https://github.com': teresamg22
Password for 'https://teresamg22@github.com': 
Contando objetos: 4, listo.
Delta compression using up to 8 threads.
Comprimiendo objetos: 100% (4/4), listo.
Escribiendo objetos: 100% (4/4), 571 bytes | 571.00 KiB/s, listo.
Total 4 (delta 0), reused 0 (delta 0)
To https://github.com/teresamg22/Homework-1.1.git
   c4fad6d..116984a  master -> master
   
```
## TEST OF MERGE BY PULL REQUEST WITH CONFLICTS 

In this case another classmate has done also changes in test1.txt and also has added another file pullrequest.txt.
As in the previous case. we start doing checkout a new branch and test the changes.

```
~/Homework-1.1$ git checkout -b adiaz92-master master
Cambiado a nueva rama 'adiaz92-master'

~/Homework-1.1$ git pull https://github.com/adiaz92/Homework-1.1.gitremote: 
Enumerating objects: 6, done.
remote: Counting objects: 100% (6/6), done.
remote: Compressing objects: 100% (4/4), done.
remote: Total 4 (delta 0), reused 4 (delta 0), pack-reused 0
Desempaquetando objetos: 100% (4/4), listo.
Desde https://github.com/adiaz92/Homework-1.1
 * branch            HEAD       -> FETCH_HEAD
Auto-fusionando test1.txt
CONFLICTO (contenido): Conflicto de fusión en test1.txt
Fusión automática falló; arregle los conflictos y luego realice un commit con el resultado.
```
In this case we can see that there is a conflict with the file test1.txt. If we open this file we can see where are the conflicts
```
~/Homework-1.1$ cat test1.txt
Test 1.1
Hello World!
Text in branch testbranch
Adding a tag

<<<<<<< HEAD

Trying to perform a pull-action
=======
Pull Request Prove by adiaz92

Adding file pullrequest.txt
>>>>>>> 901f9df8864e6d8384eef6991553ac982f01c456
```
What has been added by the user adiaz92 is what is below the ====== We modify the file erasing the line ==== and the lines with the <<<<<<<< and >>>>>>>. and we do a commit with the changes:
```
~/Homework-1.1$ git commit -m "modify test1.txt conflict"
U	test1.txt
error: No es posible realizar un commit porque tienes archivos sin fusionar.
ayuda: Corrígelos en el árbol de trabajo y entonces usa 'git add/rm <archivo>',
ayuda: como sea apropiado, para marcar la resolución y realizar un commit.
fatal: Saliendo porque existe un conflicto sin resolver.

~/Homework-1.1$ git add test1.txt
~/Homework-1.1$ git commit -am "modify test1.txt conflict"
[master 2a55daf] modify test1.txt conflict
```
And we make the merge of the branches as in the previous case:
```
~/Homework-1.1$ git merge -m "Merge branch adiaz92-master" adiaz92-master
Ya está actualizado.
teresa@teresa-Inspiron-5570:~/Homework-1.1$ git push origin master
Username for 'https://github.com': teresamg22
Password for 'https://teresamg22@github.com': 
Contando objetos: 10, listo.
Delta compression using up to 8 threads.
Comprimiendo objetos: 100% (10/10), listo.
Escribiendo objetos: 100% (10/10), 1.00 KiB | 1.00 MiB/s, listo.
Total 10 (delta 5), reused 0 (delta 0)
remote: Resolving deltas: 100% (5/5), completed with 1 local object.
To https://github.com/teresamg22/Homework-1.1.git
   a8fb5be..2a55daf  master -> master
```

