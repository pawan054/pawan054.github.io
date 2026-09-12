# Installation of recent ver. of QE in lastest ver. of ubuntu linux OS

 **Hi, this is Pawan. I help you with your computational solid state research.** 
 <hr>
 When you follow these steps you will automatically download the lastest version of quantum espresso (QE) in your linux OS. However, if you want specific version then you have to clone
 that link. <br/>
 
I guess this is most convenient and easiest way to install any open sources software or codes. <br/>
Please copy paste each line in your terminal sequentially. Though order of installation some source packages does not matter, follow steps in order. 

If you encounter any error please comment at youtube video link 

**This method is not only applied in case of personal laptop but you can also apply in clusters. 
The only difference is you don't need to install open source libraries just load mkl intel libraries using module load if they are not
automaticaly provided by default.**


 **Step I** <br/>
 You need to download and install some required packages such as math libraries $-$ blas, lapack, fft and open-mpi libraries for parallel calculation and 
 some dependencies. 

 Let's start. Open your terminal and follow the following commands: <br/>
 *Note that you can install qe in your home directory. Thats okay; however, I personally prefer to download such codes inside software directory
 inside home dir. So you can create this. Just type cd and then mkdir software and cd software. Then check you are inside software dir by typing pwd* <br/>
1. Update your system
 ```
sudo apt update
```
2. Install git 
```
sudo apt install -y git
```
3. Install build-essential
```
sudo apt install -y build-essential
```
4. Install gfortran which is one main key element here
```
sudo apt install -y gfortran
```
5. Install wget to download source link directly from terminal
```
sudo apt install -y wget
```
6. Install math libraries
```
sudo apt install -y libblas-dev
```
7. This is a another math library
```
sudo apt install -y liblapack-dev
```
8. Install FFT package
```
sudo apt install -y libfftw3-dev
```
9. Install libraries for parallel calculation
```
sudo apt install -y openmpi-bin
```
```
sudo apt install -y libopenmpi-dev
```

```
sudo apt install -y libscalapack-openmpi-dev
```
**Step II** <br/>
Now download the source code using git clone. It will actually download the entire project history, including all past versions and branches, 
along with the latest files. You can install old sources files as well if you need but I will install latest version at this time qe-7.6.

13. Download qe
```
git clone https://gitlab.com/QEF/q-e.git
```
**Step III** <br/>
14. Configure source files
```
ls
```
```
cd q-e/
```
```
git checkout qe-7.6
```
```
./configure
```
**Step IV** <br/>
15. Install  QE and make binary files
```
make -j 4 all
```
```
make -j 4 epw
```
*Everything is done so far successfully. Now just check whether binary files are produced.* **Here -j 4 means I am using 4 cores for installing this code. 
I have used only half since  I have 8. This is because some other functions in laptop are also running. You can take 2 cores less than you have. To check how many core 
you have type *lscpu* and hit enter in terminal and look for CPU**

 ```
ls bin/
```
*You will see pw.x, ph.x, epw.x, projectwfc.x, q2r.x and so on ....*

**Step V** <br/>
16. Now add path to binary files (executables) to your laptop's .bashrc file such that you can access these files from everywhere no matter in
which directory you are working otherwise you to provide path to qe/bin everytime before running calculations. 

For instance in my case:  ***/home/pjoshi4/software/q-e/bin/pw.x -in scf.in > scf.out***

For this follow as 
```
cd bin/
```
*Make sure your inside q-e/*
```
pwd
```
*Now copy the path*
```
gedit ~/.bashrc
```
*At the bottom of this file copy following line*
```
export PATH="pwd:$PATH"
```
*Here pwd means replace it by copy pasting its result after you typed it.* 

*For instance in my case: **export PATH="/home/pjoshi4/software/q-e/bin:$PATH"***

Then finally do 
```
source ~/.bashrc
```
That's it. You have installed latest version of QE in your laptop. Congratulations and best of luck with your calculations.

Now type cd hit enter and then type *which pw.x* let me know in comment what you get. Then I can say whether you are correctly configured.

For more help, please the  refer the following you tube video.
<a href="https://youtu.be/tNNlHjNNbj8" target="_blank" rel="noopener noreferrer">
  <img src="https://github.com/pawan054/pawan054.github.io/blob/main/install%20xcrysden%20thumbnail.png" alt="Watch Video on YouTube" style="width:100%; max-width:560px;">
</a>
