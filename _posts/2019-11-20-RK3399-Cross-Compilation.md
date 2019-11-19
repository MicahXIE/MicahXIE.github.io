---
layout:     post
title:      RK3399 Cross Compilation
subtitle:   Misc series
date:       2019-11-20
author:     Micah
header-img: img/post-bg-universe.jpg
catalog: true
tags:
    - cross compilation
---

## Background

This article will introduce something related to rockchip `rk3399` cross compilation. Later I will add some testing examples.


## System Environment
* `Host` Ubuntu 16.04 
* x86_x64
* gcc 5.4.0

* `Target` rk3399
* ARM 64 (aarch64)
* gcc 6.3.1

* Toolchain 
* aarch64-linux-gnu-gcc 
* aarch64-linux-gnu-g++


## Steps

### Download the cross compilation tools
* goto https://releases.linaro.org/components/toolchain/binaries/6.3-2017.05/aarch64-linux-gnu/
* download `gcc-linaro-6.3.1-2017.05-x86_64_aarch64-linux-gnu.tar.xz`
* cp `gcc-linaro-6.3.1-2017.05-x86_64_aarch64-linux-gnu.tar.xz` /opt (root)
* cd /opt
* tar -zxvf gcc-linaro-6.3.1-2017.05-x86_64_aarch64-linux-gnu.tar.xz
* mv gcc-linaro-6.3.1-2017.05-x86_64_aarch64-linux-gnu gcc-aarch64-linux-gnu
* edit `~/.bashrc` (user)

```
export PATH=$PATH:/opt/gcc-aarch64-linux-gnu/bin
```

* source `~/.bashrc`
* check setup, `aarch64-linux-gnu-gcc -v`



### Boost 1.66.0
* wget https://dl.bintray.com/boostorg/release/1.66.0/source/boost_1_66_0.tar.gz
* tar -zxvf boost_1_66_0.tar.gz
* cd boost_1_66_0
* ./bootstrap.sh --prefix=$PWD/../boost-1-66-0
* Moidfy project-config.jam to

```
using gcc : arm : aarch64-linux-gnu-gcc ;
```

* ./bjam
* ./bjam install

### Protobuf 3.5.1
* wget https://github.com/protocolbuffers/protobuf/releases/download/v3.5.1/protobuf-cpp-3.5.1.tar.gz
* tar -zxvf protobuf-cpp-3.5.1.tar.gz
* cd protobuf-3.5.1
* sudo yum install autoconf automake libtool
* ./autogen.sh

***generate protoc***
* ./configure
* make
* sudo make install
* make disclean

***cross compilation***
* set configure as below

```
./configure --build=i686-pc-linux \
            --host=aarch64-linux-gnu \
            --with-protoc=protoc \
            CC=aarch64-linux-gnu-gcc \
            CXX=aarch64-linux-gnu-g++ \
            --prefix=$PWD/install
```

* make -j8
* make install

### OpenCV 3.4.4
* wget https://github.com/opencv/opencv/archive/3.4.4.tar.gz
* tar -zxvf 3.4.4.tar.gz
* cd opencv-3.4.4
* run configure as below:

```
cmake -D CMAKE_C_COMPILER=aarch64-linux-gnu-gcc \
      -D CMAKE_CXX_COMPILER=aarch64-linux-gnu-g++ \
      -D BUILD_SHARED_LIBS=ON \
      -D BUILD_ZLIB=ON \
      -D CMAKE_CXX_FLAGS=-fPIC \
      -D CMAKE_C_FLAGS=-fPIC \
      -D CMAKE_EXE_LINKER_FLAGS=-lrt -lpthread -ldl \
      -D CMAKE_INSTALL_PREFIX=./install \
      -D CUDA_GENERATION=Auto \
      -D WITH_CUDA=ON \
      -D WITH_OPENGL=ON \
      -D WITH_OPENNI=ON \
      -D WITH_OPENNI2=ON \
      -D WITH_ZLIB=ON \
      -D WITH_ITT=OFF \
      -D WITH_FFMPEG=ON \
      -D WITH_PNG=ON \
      -D WITH_JPEG=ON \
      -D ENABLE_CXX11=ON \
      -D WITH_ZLIB_INCLUDE_DIRS=/home/iim/Documents/libs/opencv-3.4.4/3rdparty/zlib \
      ..
```

* make -j8
* make install