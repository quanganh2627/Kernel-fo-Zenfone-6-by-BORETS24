# Kernel-fo-Zenfone-6-by-BORETS24
How to build zenfone kernel

#1 Install tools and download aosp source code
	sudo apt-get install openjdk-7-jdk
	
	sudo apt-get install git-core gnupg flex bison gperf build-essential \
  	zip curl zlib1g-dev gcc-multilib g++-multilib libc6-dev-i386 \
  	lib32ncurses5-dev x11proto-core-dev libx11-dev lib32z-dev ccache \
  	libgl1-mesa-dev libxml2-utils xsltproc unzip
	
	cd [working dir]
	repo init -u https://android.googlesource.com/platform/manifest -b android-5.1.1_r29
	repo sync

# 2 Download original source from ASUS site end extract this to [working dir]
#3 Download my source code, then rename  Kernel-fo-Zenfone-6-by-BORETS24-master folder to 'linux' and put this folder in [working dir]

#4 build 'minigzip' and 'openssl' modules
	source build/envsetup.sh
	lunch aosp_x86-eng
	make -j4 minigzip openssl

#5 build kernel image and modules
## define TARGET_DEVICE to overwrite
## available options : 
## 	TARGET_DEVICE=hd  (A500CG/A501CG/A600CG - default)
##	TARGET_DEVICE=fhd (A502CG/A451CG)

	make -f KernelMakefile TARGET_DEVICE=hd build_kernel
  	or
	make -j4 -f KernelMakefile TARGET_DEVICE=hd modules_install
