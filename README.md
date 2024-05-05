# Lingmo OS System Build Tools

The tools and files used to build Lingmo OS can build a system that is not much different from the official version.

# How to use (only supports Debian systems and derivative systems, such as Ubuntu, Lingmo OS, etc.)

## Build base directory
 - clone warehouse
 ```shell
 git clone https://github.com/LingmoOS/lingmo-system-build.git
 ```
 - Install build tools
 ```shell
 apt install -y sudo dpkg-dev dctrl-tools devscripts wget isolinux syslinux
 
 wget http://ftp.cn.debian.org/debian/pool/main/d/debootstrap/debootstrap_1.0.134_all.deb
 # Install pkgs
 sudo apt -y install ./*.deb
 # Builds pkgs
 cd debootstrap/ 
 sudo apt-get build-dep ./
 debuild -us -uc -b
 sudo apt -y install ../*.deb
 cd ../
 ```
 - Build Main Tools
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
 - Build Lingmo OS
 ```shell
 cd build-sys/
 sudo lingmo-sys-build build
 ```

# License
GPL-3.0 license
