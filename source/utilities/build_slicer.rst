How  to Build 3D Slicer
========================

General Instruction: `Documentation/Nightly/Developers/Build Instructions <https://www.slicer.org/slicerWiki/index.php/Documentation/Nightly/Developers/Build_Instructions>`_

On Windows
----------

1.Install Visual Studio Express (Remember to install Git and OpenSSL)

2.Install Qt 4.8.6 (Qt 5.x won't work) binaries from `Slicer website <https://www.slicer.org/slicerWiki/index.php/Documentation/Nightly/Developers/Build_Instructions/Prerequisites/Qt#Windows>`_

3.Install CMake binaries.

4.Download slicer source code from github.

5.Open Cmake gui. Select source directory and build directory.

6.Add following Environment Variables ::

   CMAKE_INSTALL_PREFIX = /path/to/install/dir
   QT_QMAKE_EXECTUABLE = /path/to/qt/bin/qmake.exe
   CMAKE_CONFIGURATION_TYPES = Release

7.Click ``Configure`` and then ``Generate``

8.Cd to build dir. Open the ``Slicer.sln`` file. It will be opened in the Visual Studio.

9.In Visual Studio, Set the active build configuration into ``Active``. See `Setting the Active Build Configuration <https://msdn.microsoft.com/en-us/library/aa244296(v=vs.60).aspx>`_

10.Build the ``All_BUILD`` project.

