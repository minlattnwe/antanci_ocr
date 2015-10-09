INSTALLATION INSTRUCTIONS
------------ ------------

How to build banti from scratch.

1) Install git, g++, png, jpeg, tiff, zlib etc.
	sudo apt-get install git g++ libpng-dev libjpeg-dev libtiff-dev libz-dev

2) Add SSH keys based on 
	https://help.github.com/articles/generating-ssh-keys

3) Clone
	git clone git@github.com:rakeshvar/banti.git

4) Get latest version of Eclipse C++
	Copy extracted directory to /opt
	Creat shortcut
		sudo ln -s -T /opt/eclipse/eclipse /usr/bin/eclipse
	Add application by creating /usr/share/applications/eclipse.desktop
	If titles are not showing specify in the above file:
		Exec=env UBUNTU_MENUPROXY= eclipse

5) Run eclipse

6) Set workspace to the directory you cloned to (say /d/ocr/)

7) File -> Import -> General -> Existing Projects into Workspace
	Specify the directory you cloned to 
	Check the option "Search for Nested Projects"

8) Install Freetype
	Download latest source from 
		http://sourceforge.net/projects/freetype/files/freetype2/
	Unzip 
	Run the usual
		./configure
		make -j4 
		sudo make install
	
	(ONLY) If you are getting Freetype errors, go to the properties of leptonica project
		C/C++ Build ->  Settings   -> Tool Settings -> GCC Compiler -> Includes 
	and add /usr/local/include and /usr/local/include/freetype2

9) Compile leptonica, gfft, banti

10) Run <path_to_git_directory>/banti/Debug/banti to see full options
	Increase stack size if you are getting a Seg Fault. 
		ulimit -s 1000000

11) If you want to run classifier you will need to have the data 
    (charcodes.txt, cp.bin, sm.bin, wr.bin) in the data directory 
    (symbolically) located in the same folder as the executable. 
    e.g.:- <path_to_git_directory>//banti/Debug$ ln -s -T ../../data/ data