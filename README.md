# FreeImage-CMake
This repository is a fork of the FreeImage that supports cmake building.
[FreeImage](https://freeimage.sourceforge.io/) is an Open Source library project for developers who would like to support popular graphics image formats like PNG, BMP, JPEG, TIFF and others as needed by today's multimedia applications. FreeImage is easy to use, fast, multithreading safe, compatible with all 32-bit or 64-bit versions of Windows, and cross-platform (works both with Linux and Mac OS X).

[CMake](https://cmake.org/) is a cross-platform, open source tool for defining build processes that run on multiple platforms. 

## Building

Here I use Visual Studio 19 to develop this CMake project. The local machine is Windows and the remote Linux server is added in Visual Studio.[1]

### Windows
* Windows 10
* CMake 3.16.6
* CMake generator:  Visual Studio 16 2019 Win64, **NOT Ninja**
* configuration Type:  Debug or Release
### Linux

* Ubuntu 18.04.5 LTS
* CMake 3.19.6
* gcc, g++ 8.4.0
* CMake generator: Unix Makefile
* configuration Type:  Debug or Release

## Process

| Target            | OS + Configuration Type | Build  |
| ----------------- | ----------------------- | ------ |
| FreeImage         | Windows + Debug/Release | Pass   |
| FreeImage         | Linux + Debug/Release   | Pass   |
| FreeImage TestAPI | Windows + Release       | Pass   |
| FreeImage TestAPI | Windows + Debug         | Failed |

## Reference
[1] [CMake projects in Visual Studio](https://docs.microsoft.com/en-us/cpp/build/cmake-projects-in-visual-studio?view=msvc-160) and [Build Linux projects with CMake in Visual studio](https://docs.microsoft.com/en-us/cpp/linux/cmake-linux-project?view=msvc-160).
