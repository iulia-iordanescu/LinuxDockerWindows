# LinuxDockerWindows
 
### LinuxDockerWindows
```
pwd
```
commavds 


# searching for "blah blah"
```
D:\crtUsers\Iulia\prj\Coding
docker run ^
-it ^
-v %cd%:/cntmnt:rw ^
continuumio/miniconda3 ^
/bin/bash -c "grep -r /"blah blah/" /cntmnt/*.md "
```