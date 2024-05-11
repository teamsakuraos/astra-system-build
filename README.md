# astraOS System Build Tools

The tools and files used to build astraOS can build a system that is not much different from the official version.

## **Prerequisite**: Please ensure that your build host has at least **45GB** of space and **administrator** privileges

## Build base directory
 - clone warehouse
 ```shell
 git clone https://github.com/teamsakuraos/astra-system-build.git
 ```
 - Install related dependency packages
 ```shell
 sudo apt install -y sudo dpkg-dev dctrl-tools devscripts wget isolinux syslinux

 wget http://ftp.cn.debian.org/debian/pool/main/d/debootstrap/debootstrap_1.0.134_all.deb
 sudo apt -y install ./*.deb
 ```

 - Building and installing debootstrap
 ```shell
 # Builds pkgs
 cd debootstrap/ 
 sudo apt-get build-dep ./
 debuild -us -uc -b
 sudo apt -y install ../*.deb
 cd ../
 ```
 - Build LSBT
 ```shell
 sudo apt-get build-dep ./
 sudo make install
 ```

 - Initialize basic configuration
 ```shell
 mkdir build-sys/
 mv auto/ build-sys/
 mv config/ build-sys/
 cd build-sys/
 sudo chmod +x auto/*
 sudo lingmo-sys-build clean
 sudo lingmo-sys-build config
 ```
 - Build astraOS (Delta)
 ```shell
 cd build-sys/
 sudo lingmo-sys-build build
 ```
### **Tips**: This process will consume a lot of time and disk space. After completion, you can view the completed product in the _out/_ directory

# License
GPL-3.0 license
