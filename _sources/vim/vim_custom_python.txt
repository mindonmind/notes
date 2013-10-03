Build Vim With Custom Python (e.g. EPD) Support
================================================

Preinstallation
---------------

1.Make sure ``which python`` gives the specific python you want to build vim with.

2.If possible, remove the origin python built in your system (/usr/bin/python) or go to 3 ::

   pacman -R python2    # you can use your own package manager

3.If you don't remove the python packaged with your system, you may have ``libpython2.7.so`` in your ``/usr/lib`` or ``/usr/local/lib``, which may bring troubles in the following installation. So mask them first ::

   cd /usr/lib          # or /usr/local/lib
   sudo mv libpython2.7.so libpython2.7.so.back
   sudo mv libpython2.7.so.1.0 libpython2.7.so.1.0.back

Installation
-------------

Download the Vim source, in arch ::

    abs extra/vim
    cp -r /var/extra/vim ~/abs/vim

Configure your vim installation with python support, e.g ::

    ./configure --prefix=/path/to/your/installdir/ \
                --with-features=huge \
                --enable-gpm \
                --enable-acl \
                --enable-multibyte \                                                # for UltiSnip and NERDTree
                --enable-cscope \
                --enable-perlinterp \
                --enable-pythoninterp \
                --with-python-config-dir=/usr/local/epd-7.3-2/lib/python2.7/config   # this line could be omitted
                --disable-selinux

*Notice:* During the configuration procedure of latest vim version, configure tries to find ``python2`` instead of ``python``, so make sure ``python2`` link to your desired python program. Otherwise, vim will always use ``/usr/bin/python2`` which links to the system's default python.

Postinstallation
----------------

Unmask your original pythonlib ::

    sudo mv libpython2.7.so.back libpython2.7.so
    sudo mv libpython2.7.so.1.0.back libpython2.7.so.1.0

Reference
---------

1. `Building MacVim with full python EPD support <http://dpinte.wordpress.com/2011/01/02/building-macvim-with-full-python-epd-support/>`_
2. `A very boring note: setting up python-mode in Vim <http://homepages.see.leeds.ac.uk/~eeaol/notes/2012/10/vim-python-mode/>`_
3. `UltiSnips requires multibyte support enabled in Vim <http://www.psteiner.com/2013/03/ultisnips-requires-multibyte-support.html>`_
