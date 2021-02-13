# LinuxDockerWindows
 
## LinuxDockerWindows
```
pwd
```
commavds 


 

### how to use linux grep functions to search for files on your windows machine
searching for "blah blah"
1. (under windows) change directory (cd) to where you want to search  
For example to cd to D:\crtUsers\Iulia\My_writing (after changing the disk as neccessary - e.g. via d: ) simply type:  
```
C:\Users\iulia>d:
D:\>cd \crtUsers\Iulia\My_writing
```
A typical session looks like this:   
D:\crtUsers\Iulia\prj\LinuxDockerWindows>cd D:\crtUsers\Iulia\My_writing
D:\crtUsers\Iulia\My_writing>

1. (under windows) start your preferred linux docker image (e.g. continuumio/miniconda3) in a container on windows.

```
docker run ^
-it ^
--rm ^
--name miniconda3container01 ^
-v %cd%:/cntmnt:rw ^
continuumio/miniconda3 ^
/bin/bash 

```

2.  (under linux) Let's look for __searchedword__ in all txt files (denoted by *) in above windows directory mounted as __cntmnt__ inside the linux container.
```
grep -rHn searchedword /cntmnt/*.*

```

For more complex search patterns, like searching for a string (e.g. "blah b;ah") with multiple words in quotes, 
change your command by escaping special characters:  
 
```
docker run ^
-it ^
--rm ^
--name miniconda3container01 ^
-v %cd%:/cntmnt:rw ^
continuumio/miniconda3 ^
/bin/bash -c "grep -rn --with-filename \"blah blah\" /cntmnt/ "

```

[continuumio/miniconda3](https://hub.docker.com/r/continuumio/miniconda3) instructions for running a notebook on Windows:
 
```
docker run ^
-it ^
--rm ^
--name miniconda3container01 ^
-v %cd%:/cntmnt:rw ^
continuumio/miniconda3 ^
/bin/bash  -c "/opt/conda/bin/conda install jupyter -y --quiet && mkdir /opt/notebooks && /opt/conda/bin/jupyter notebook --notebook-dir=/cntmnt --ip='*' --port=8888 --no-browser"
```




