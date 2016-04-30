Install FreeSurfer and FSL in Arch Linux
=========================================

FreeSurfer
----------
Install the built binary version of FreeSurfer-CentOS6.

For Freeview, there will be some dynamic library missing. 

Install them using pacman.

Then some version of the dynamic library would be wrong, just ``ln -s`` them into the ``/usr/share/lib``

But for ``libpng``, the ``ln -s`` woun't work, because the version of Freeview was built against (12.0) was not compatible with the newer version on Arch.

Download the source file of ``libpng-``.


FSL
---
We cannot use the ``installer.py`` file from FSL website.

One way is to built it from sources.

You can find the FSL package from AUR, however, there're some tweaks needed before working properly.

The built error comes from the ``libdb``. This library is using ``VPX``, but the newest VPX library has remove some of the constant used by the libdb codes in the FSL source.

The way to fix this is to download the source file of FSL, and then modify the source code of libdb, i.e. add the prefix "VPX" to those missing identifier.

Another way is to download the binary package directory from fsl's website (without the installer.py file). And then unpack and move it to destination.

Some dummy dynamic libraries will need to be linked to their newer version.
