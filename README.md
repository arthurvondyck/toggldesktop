
[![Build Status](https://travis-ci.org/toggl/toggldesktop.png)](https://travis-ci.org/toggl/toggldesktop)

Build instructions
==================

OSX and Linux
-------------
First, build dependencies:
```
make deps
```
then the app itself:
```
make
```

To build, then run the app:
```
make run
```

Run unit tests with
```
make test
```

Linux
-----
You'll need QT to be at least version 5.2

If qmake is not on your PATH, set this first, before running make:

```
export QMAKE=/usr/bin/qmake-qt5
```

You also need libreadline-dev to build.

Below are some distribution specific package requirements:

Debian
------
* qt5-default

Ubuntu
------
* xorg-dev
* qtcreator
* libxss-dev
* libqt5webkit5-dev

Fedora
------
* qt5-qtwebkit-devel
* libXScrnSaver-devel
* qt5-qtsvg

Windows
-------
We're building the Windows app using [Visual Studio Express 2013 for Windows Desktop](http://www.microsoft.com/en-us/download/details.aspx?id=40787) 

You'll need to [install ActivePerl](http://www.activestate.com/activeperl/downloads) to build OpenSSL from source.

To build OpenSSL, from Visual Studio Tools, open up a Developer Command Prompt.

cd to the project folder, then

```
cd third_party\openssl
perl Configure VC-WIN32
ms\do_nasm
nmake -f ms\ntdll.mak clean
nmake -f ms\ntdll.mak 
```

Instead of do_nasm (use NASM) you can also use do_ms (no asm at all), or do_masm (use MASM). 
NASM can be downloaded here: http://www.nasm.us/pub/nasm/releasebuilds/?C=M;O=D


Then open the solution in Visual Studio. Next, you'll need to install the net-bugsnag package: from the Tools menu select NuGet Package Manager, then Package Manager Console. Into the console, type:

```
Install-Package Bugsnag.Library
```

From the same console, install Oauth2 related packages:

```
Install-Package Google.Apis.Auth;
Install-Package Google.Apis.Oauth2.v2;
```

Now, select *Release* from the Solution Configurations combobox in the Visual Studio toolbar, and build the solution.

Downloads
=========

OSX
---
Toggl built and signed app for OSX is [available for download](https://www.toggl.com/api/v8/installer?platform=darwin&app=td&channel=stable). You need at least OSX 10.8.

Windows
-------
Toggl built and signed app for Windows is [available for download](https://www.toggl.com/api/v8/installer?platform=windows&app=td&channel=stable). App has been tested on Windows 7, 8 and 8.1

Linux (64 bit only)
-------------------
* [tarball](https://www.toggl.com/api/v8/installer?app=td&platform=linux&channel=stable)
* [deb](https://www.toggl.com/api/v8/installer?app=td&platform=deb64&channel=stable)


Contribute
==========
Fork the repo and hack away!

Before sending us a pull request, please format the source code:

```
make fmt
```

Also, please check for any cpplint issues:

```
make lint
```

Check if unit tests continue to pass:

```
make test
```

