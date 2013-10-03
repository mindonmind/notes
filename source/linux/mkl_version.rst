Get Version Info for MKL in Matlab and Numpy/Scipy
===================================================

Matlab uses LAPACK and BLAS to do underlying matrix computations. To maximize efficiency in a specific computer architecture, it often uses MKL(for Intel) or ACML(for AMD) as the BLAS implementation.

If you want to check the version infos for these underlying linear algebra libraries, you could simply do::

    version -lapack
    version -blas

Same as matlab, Numpy/Scipy could also link to MKL/ACML version of BLAS/LAPACK, to check these libraries version, you could enter::

    import mkl
    mkl.get_version_string()

There are also a bunch of other useful functions in the ``mkl`` module, such as ``set_num_threads`` and ``get_max_num_threads``.
