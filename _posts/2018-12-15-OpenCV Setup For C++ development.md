---
layout:     post
title:      OpenCV Setup For C++ development
subtitle:   OpenCV Setup
date:       2018-12-15
author:     Micah
header-img: img/post-bg-universe.jpg
catalog: true
tags:
    - opencv
---

## Background

OpenCV (Open Source Computer Vision Library) is a very strong Computer Vision Library using in industry. OpenCV is originally written in C++ but it also can be used by Python, JAVA and MATLAB. 
Written in optimized C/C++, the library can take advantage of multi-core processing. Enabled with OpenCL, it can take advantage of the hardware acceleration of the underlying heterogeneous compute platform.

Below two articles are very good reference for setting up opencv in Mac for c++ development. The first one compiles the source code to install the library. The second one uses homebrew to install 
the opencv. Really thanks for sharing your knowledge! In this article, I will focus on the issues
I hit when I install the libraries.

- [Mac平台上OpenCV开发环境搭建](https://segmentfault.com/a/1190000000711132)

- [Setting up OpenCV and C++ development environment in Xcode for Computer Vision projects](https://medium.com/@jaskaranvirdi/setting-up-opencv-and-c-development-environment-in-xcode-b6027728003)

 
## Issues & Solutions

- 'array' file not found in cvdef.h

  The issue is because `array` is provided in C++11, you need to provide the -std=c++11 flag to enable it, and provide the `-stdlib=libc++` flag for the corresponding library. But in the article one, we need to choose `libstdc++`. So there is a conflict here, that's why finally I choose to use the command Line Method in article 2.
<br/>

- macports for gcc upgrade

  my previous gcc version is 4.2 and I use macports to upgrade it to 4.7 to make sure it to support 
  C++11. You can refer to below article to upgrade your gcc in mac.

  [Installing GCC on Mac](https://www.ficksworkshop.com/blog/installing-gcc-on-mac)
<br/>

- pkg-config --cflags --libs opencv not found

  As mentioned in article 2, if `pkg-config --cflags --libs opencv` doesn't work, you should specify the location of your opencv.pc path. Also you need to add it to your ~/.bash_profile and apply it.

```shell
#pk_package path as below
export PKG_CONFIG_PATH=/usr/local/lib/pkgconfig:/usr/local/lib:/usr/local/Cellar/opencv/3.4.3_1/lib/pkgconfig/
```

- glog Library not loaded

  After you build your program, when you run your program, it maybe report below error:

```C++
	dyld: Library not loaded: /usr/local/opt/glog/lib/libglog.0.3.5.dylib
	Referenced from: /usr/local/opt/opencv/lib/libopencv_sfm.3.4.dylib
	Reason: image not found
	Abort trap: 6
```

  This issue is because you need to install glog separately.

> brew install glog
<br/>

## Testing Program


	#include <iostream>
	#include <opencv2/opencv.hpp>
	#include <opencv2/highgui.hpp>
	using namespace std;
	using namespace cv;

	int main(int argc, const char * argv[]) {
    	Mat image;
    	//change to your own path
    	image = imread("/Users/micah/Downloads/1.jpg", 1);
    	namedWindow("Display Image", WINDOW_AUTOSIZE);
    	imshow("Display Image", image);
    	waitKey(0);
    	return 0;
	}












 

