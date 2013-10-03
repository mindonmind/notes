Change Library Search Path For Binary Files in Linux
====================================================

In Linux, every binary file(most ELF) relies on some other library.
For dynamic linking ELFs, the search path where system finds these libraries are decided by compiling option, ``LD_LIBRARY_PATH``, and system's default library paths.
As most ELFs share the system's default libraries which are commonly deposited at ``/usr/lib/`` or ``/usr/lib64``, their library dependencies could be easily resolved by ``ld``, the system's dynamic linker/loader.

However, at times some applications need to use some libraries which are not located in the system's library directories.
For example, you are working on a server and you want to install a application which relies on some libraries that are newer than your server's version.
So you need to compile the libraries by yourself and let the application know where these compiled libraries are.

To accomplish that, the easiest way is to set the ``LD_LIBRARY_PATH``. 
As that path is always searched before the system's default path, the system will use your newer libraries for all your applications.

Nevertheless, there are a few times when some application want to use a specific libraries which are not sharable for other applications. In other words, these libraries are used the same way as static libraries.

To do that, we need the ``RPATH`` property in the ELF's dynamic section.
It's a property which assigns the specific library search paths for the current ELF.
The ``RPATH`` is commonly set during compile time with the ``-rpath`` compiling option.
Thanks to `PatchELF <http://nixos.org/patchelf.html>`_ , we could change the ``RPATH`` of an ELF anytime.

It's very easy to use, just like::

    patchelf --set-rpath /path/to/your/libdir:/path2/to/your/libdir/:$ORIGIN yourelf

The ``$ORIGIN`` variable could be used to represent for the current directory where you put your elf and is very useful if you want to distribute your elf as an user application. 

The ``patchelf`` could also be used to specifiy your dynamic linker.
In addition to ``pathelf``, the followings are some other useful programs to debug elf executables.

1. ldd: to see the library dependencies.
2. readelf: to see infos about a elf, you could use ``readelf -d xxx`` to see its dynamic section, where ``RPATH`` is located.
3. strings: to print strings infos about an file. Use ``strings glibc.so.1 | grep GLIBC`` to see which vesions are supported by the lib.

References:

1. `PatchELF <http://nixos.org/patchelf.html>`_
2. `Redirecting functions in shared ELF libraries <http://www.codeproject.com/Articles/70302/Redirecting-functions-in-shared-ELF-libraries>`_
3. `ld-linux manpage <http://linux.die.net/man/8/ld-linux>`_
