# Matlab Kinect
by Dirk-Jan Kroon
31 Jan 2011 (Updated 06 Jun 2013)
http://www.mathworks.com/matlabcentral/fileexchange/30242-kinect-matlab

Including the pre-built binaries for 64-bit Ubuntu (for 64-bit Windows see FruitNinjaKinect, https://github.com/hayyaan/FruitNinjaKinect/tree/master/Kinect/Mex)

If you had hit the following error, you can just use pre-built binaries:

    mxNiChangeDepthViewPoint.cpp:62:51: error: ‘class xn::AlternativeViewPointCapability’ has no member named ‘SetViewPoint’
         g_DepthGenerator.GetAlternativeViewPointCap().SetViewPoint(g_Image);

    mex: compile of ' "mxNiChangeDepthViewPoint.cpp"' failed.

Note: The examples are not included here, but you can download them from the original submission: http://www.mathworks.com/matlabcentral/fileexchange/30242-kinect-matlab
