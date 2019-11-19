---
layout:     post
title:      Hi3559AV100 Cross Compilation
subtitle:   Misc series
date:       2019-11-19
author:     Micah
header-img: img/post-bg-universe.jpg
catalog: true
tags:
    - cross compilation
---

## Background

Sorry for not updating for such a long time. From today, I will try to write blog every week to summarize something I learn in the week.
Today will introduce something related to Huawei Hi3559AV100 cross compilation. In this article, I will mainly focus on OpenCV, Boost and 
Protobuf these libraries.


## System Environment
* `Host` CentOS 7 
* x86_x64
* gcc 6.3.0

* `Target` Hi3559AV100
* ARM 64 (aarch64)
* gcc 6.3.0

* Toolchain 
* aarch64-himix100-linux-gcc 
* aarch64-himix100-linux-g++


## Steps


### Boost 1.66.0
* wget https://dl.bintray.com/boostorg/release/1.66.0/source/boost_1_66_0.tar.gz
* tar -zxvf boost_1_66_0.tar.gz
* cd boost_1_66_0
* ./bootstrap.sh --prefix=$PWD/../boost-1-66-0
* Moidfy project-config.jam to
```
using gcc : arm : aarch64-himix100-linux-gcc ;
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
            --host=aarch64-himix100-linux \
            --with-protoc=protoc \
            CC=aarch64-himix100-linux-gcc \
            CXX=aarch64-himix100-linux-g++ \
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
cmake -D CMAKE_C_COMPILER=aarch64-himix100-linux-gcc \
      -D CMAKE_CXX_COMPILER=aarch64-himix100-linux-g++ \
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