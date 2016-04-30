Linux 动态库查找与链接相关知识
===============================

ld.so, ld-linux.so
-------------------

动态库查找程序 ``ld.so``, ``ld-linux.so`` (from man ld.so): ::

     The programs ld.so and ld-linux.so* find and load the shared libraries needed by a program, prepare the program to run, and then run it.

       Linux binaries require dynamic linking (linking at run time) unless the -static option was given to ld(1) during compilation.

       The program ld.so handles a.out binaries, a format used long ago; ld-linux.so* handles ELF (/lib/ld-linux.so.1 for libc5, /lib/ld-linux.so.2 for  glibc2),  which
       everybody  has  been  using  for  years  now.   Otherwise  both  have  the  same  behavior,  and  use the same support files and programs ldd(1), ldconfig(8) and
       /etc/ld.so.conf.

       When resolving library dependencies, the dynamic linker first inspects each dependency string to see if it contains a slash (this can occur if a library pathname
       containing  slashes  was  specified  at link time).  If a slash is found, then the dependency string is interpreted as a (relative or absolute) pathname, and the
       library is loaded using that pathname.

       If a library dependency does not contain a slash, then it is searched for in the following order:

       o  (ELF only) Using the directories specified in the DT_RPATH dynamic section attribute of the binary if present and DT_RUNPATH attribute does not exist.  Use of
          DT_RPATH is deprecated.

       o  Using the environment variable LD_LIBRARY_PATH.  Except if the executable is a set-user-ID/set-group-ID binary, in which case it is ignored.

       o  (ELF only) Using the directories specified in the DT_RUNPATH dynamic section attribute of the binary if present.

       o  From  the cache file /etc/ld.so.cache, which contains a compiled list of candidate libraries previously found in the augmented library path.  If, however, the
          binary was linked with the -z nodeflib linker option, libraries in the default library paths are skipped.  Libraries installed in hardware capability directo‐
          ries (see below) are preferred to other libraries.

       o  In the default path /lib, and then /usr/lib.  If the binary was linked with the -z nodeflib linker option, this step is skipped.

如果使用 gcc 编译程序， ``-L`` 后面的地址将会最后寻找。

ldd
----

动态库依赖关系查看程序 ``ldd`` ::

    ldd prints the shared libraries required by each program or shared library specified on the command line.
    #使用范例
    ldd /bin/cat
    linux-vdso.so.1 (0x00007fff9a1ff000)
    libc.so.6 => /usr/lib/libc.so.6 (0x00007f4e177ae000)
    /lib/ld-linux-x86-64.so.2 (0x00007f4e17b5b000)

ldconfig
---------

动态库地址管理程序 ``ldconfig`` ::
    
    # 查看当前 ld cache 中的所有库文件
    ldconfig -p
    # 重建 cache
    sudo ldconfig -v
    # 查看当前 ld 的搜索路径
    ldconfig -v 2>/dev/null | grep -v ^$'\t'
        /usr/lib32:
        /opt/qt/lib:
        /usr/lib:

参考:
-----

1. man ld.so
2. man ldd
3. man ldconfig
4. http://stackoverflow.com/questions/9922949/how-to-print-the-ldlinker-search-path
 

