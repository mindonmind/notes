设置 MathJax 与 Jekyll/Pandoc
==============================

MathJax 提供了许多设置（比如开启公式编号）供用户设置，而且贴心到对那些使用 CDN 的用户都可以加载自己的本地设置，具体方法见 http://docs.mathjax.org/en/latest/configuration.html#local-config-files.

注意事项写得听清楚的，剩下需要做的就是手动编辑配置文件了，关于某些配置该如何设置的问题，一是可以参考 `MathJax TeX and LaTeX Support <http://docs.mathjax.org/en/latest/tex.html>`_ 而是可以参考源码中的 ``config/default.js`` 文件，里面包含了对几乎所有配置详细的说明。

今天遇到的最恶心的问题倒不是 MathJax 这块，而是，关于在 Jekyll 中如何将 ``MathJax`` 及其参数传给 Pandoc 的问题。

在 ``_config.yml`` 文件里搞了半天没弄出来后，终于忍无可忍，直接修改了 Jekyll 源码对应的 PandocRuby 函数部分，直接把参数写死了，下次有机会，还是改用 dansan 写的 Pandoc 插件吧，再也不想自己折腾这些东西了，太浪费时间和精力。

