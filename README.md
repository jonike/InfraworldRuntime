Vizor Infraworld
================

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)

Welcome to the Infraworld source code!

![](icon.png)


Infraworld is a solution that enables [Unreal Engine 4](https://www.unrealengine.com/en-US) to work with [Google gRPC](https://gRPC.io) services from either C++ or Blueprints.

Infraworld is a fast, robust and cross platform.
It fits any stage of development: either prototyping or production. Saving a tons of your team's time, you need to write your gRPC wrappers by hand no more.
A special converter utility will do it for you, producing high quality, debuggable and multi-threaded code, gaining lowest possible overhead to your game logic thread.
You may also work with either generated or shipped with gRPC C++ classes in your own way, since the Infraworld Runtime adds all required headers and wires all required libraries automatically.

This repo contains source code of an Unreal Engine 4 plugin, that enables code, generated by the [Cornerstone converter](https://github.com/vizor-games/infraworld-cornerstone) to work.
Also, you may want to use a [Protobuild utility](https://github.com/vizor-games/infraworld-protobuild) to automate cross-language gRPC wrapper generation.


Getting started
===============

##### Building gRPC support

At the first step, you need to build gRPC runtime libraries.
Just run `Setup.sh` for Linux, `Setup.bat` for Windows or `Setup.command` for macOS. It uses gRPC branch `v1.3.x`.

* For Windows, we recommend you to use [chocolatey](https://chocolatey.org) to install packages into your system.
**Note** that you do need all these programs in your system's `PATH` ([See how to edit PATH on Windows](https://www.computerhope.com/issues/ch000549.htm)):
  * [Git VCS](https://git-scm.com/download/win)
  * Visual Studio 2015 with VC++ tools v140 installed
  * [CMake](https://cmake.org) is used to generate a Visual Studio solution from the `CMakeLists.txt` provided with gRPC
  * [Strawberry perl 64bit version](http://strawberryperl.com)
  * [NASM](https://www.nasm.us)
  * [Golang](https://golang.org/doc/install)
* For any distribution of Linux and for macOS systems you need:
  * git
  * automake
  * autoconf
  * libtool
  * make
  * strip
  * clang and clang++
  * go

**Note** that you may need to edit `VSVARSALL`, `DEVENV_PATH` and `CMAKE_FOLDER` variables in the bat file, because these paths may not be portable.

**Note** that required programs for Linux and MacOS systems are being checked in run-time.

Then you may (or may not) import `GrpcIncludes` and `GrpcIncludes` folders into your VCS, but you need to build them manually at least one time for each platform.
The build process requires an access to the Internet.


##### Installing the plugin
Just copy the resulting folder into the your project’s Plugins folder (create it if you don’t have one).
Then after that project is being opened, a dialog box, telling that the plugin is need to be compiled should appear.

Confirm the dialog by clicking `Yes`.


##### Building and the converter
Please look into the [Connerstone documentation](https://github.com/vizor-games/infraworld-cornerstone) for details.

##### Using generated code.
Please look into the [example project](InfraworldExample) for tutorial.

Running the example project
===========================

You should copy [built plugin's folder](InfraworldRuntime) into [InfraworldExample's Plugins folder](InfraworldExample/Plugins).
Then just open InfraworldExample.uproject. Server's code is in [InfraworldExample/Server](InfraworldExample/Server) folder.
You are required to install dependencies using pip and requirements.txt file.

Debugging
=========

Since the plugin itself is an open source software, you may want to debug it or add some extra functionality.
Since it is distributed as an Unreal Engine plugin, you can add it into your own game or into an [example project](InfraworldExample),
and then generate either Visual Studio, or XCode or CMake solution.

Contribution
============

Please feel free to report known bugs, propose new features and improve tests using Github's pull request system.
Please do not add either build libraries for an any platform or header files into your commits. Thank you very much for contributing into free software.

References
==========
* [Introduction to UE4 Plugins](https://wiki.unrealengine.com/An_Introduction_to_UE4_Plugins)
* [gRPC API docs](https://gRPC.io/docs/)
