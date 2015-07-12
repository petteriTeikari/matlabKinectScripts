# Matlab Kinect
by Dirk-Jan Kroon
31 Jan 2011 (Updated 06 Jun 2013)
http://www.mathworks.com/matlabcentral/fileexchange/30242-kinect-matlab

Including the pre-built binaries for 64-bit Ubuntu (for 64-bit Windows see FruitNinjaKinect, https://github.com/hayyaan/FruitNinjaKinect/tree/master/Kinect/Mex)

If you had hit the following error, you can just use pre-built binaries:

    mxNiChangeDepthViewPoint.cpp:62:51: error: ‘class xn::AlternativeViewPointCapability’ has no member named ‘SetViewPoint’
         g_DepthGenerator.GetAlternativeViewPointCap().SetViewPoint(g_Image);

    mex: compile of ' "mxNiChangeDepthViewPoint.cpp"' failed.

For some insights see also "Kinect for Ubuntu with Matlab Wrapper" by Ujwal D. Bonde
https://github.com/wgardner6/MatlabKinect/blob/master/KinectInstallationUbuntuBonde.pdf

In practice you might need to edit the "XnPlatform.h" with:

    sudo gedit /usr/include/ni/XnPlatform.h

And replace the following lines:

    #include "Linux-x86/XnPlatformLinux-x86.h"
    #if defined(_WIN32) // Microsoft Visual Studio
    	#ifndef RC_INVOKED
    		#if _MSC_VER < 1300 // Before MSVC7 (2003)
    			#error Xiron Platform Abstraction Layer - Win32 - Microsoft Visual Studio versions below 2003 (7.0) are not supported!
    		#endif
    
    		#if _MSC_VER > 1600 // After MSVC8 (2010)
    			#error Xiron Platform Abstraction Layer - Win32 - Microsoft Visual Studio versions above 2010     (10.0) are not supported!
    		#endif
	    #endif

    	#include "Win32/XnPlatformWin32.h"
    #elif defined(ANDROID) && defined(__arm__)
    	#include "Android-Arm/XnPlatformAndroid-Arm.h"
    #elif (linux && (i386 || __x86_64__))
    	#include "Linux-x86/XnPlatformLinux-x86.h"
    #elif (linux && __arm__)
    	#include "Linux-Arm/XnPlatformLinux-Arm.h"
    #elif _ARC
    	#include "ARC/XnPlatformARC.h"
    #elif (__APPLE__)
    	#include "MacOSX/XnPlatformMacOSX.h"
    #else
    	#error OpenNI Platform Abstraction Layer - Unsupported Platform!
    #endif

with just :

    #include "Linux-x86/XnPlatformLinux-x86.h"

to make sure that Matlab/GCC does not think that you have some non-Linux platform

Note: The examples are not included here, but you can download them from the original submission: http://www.mathworks.com/matlabcentral/fileexchange/30242-kinect-matlab
