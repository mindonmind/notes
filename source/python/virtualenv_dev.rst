使用 Virtualenv 与 pip 进行科学计算库开发
=========================================

1. 安装 Virtualenv ::

    pip install virtualenv

2. 新建虚拟环境 ::

    virtualenv myenv
    cd myenv

3. *使用* 新环境 ::

    source myenv/bin/active

4. 安装 numpy, scipy, Cython ::

    pip install numpy
    pacman -S lapack blas gcc-fortran
    pip install scipy
    pip install Cython

5. 安装 nose ::

    pip install nose

6. 使用 ``pip`` 时，如果是在版本库中，可以使用 ::

    pip install -e src/to/your/library  # eg. git+https://github.com/scipy/scipy or .

如果是源文件在本地，pip 会在该文件夹中编译，并在 ``site-package`` 中添入一个链接文件。

**注意** : 在每个 shell 中使用虚拟环境时，均需要 ``source yourenv/bin/active``

