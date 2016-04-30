.. _vim_solarized:

Solarized VIM
=============

VIM 终极配色方案 `Solarized <http://ethanschoonover.com/solarized>`_ ，谁用谁知道::

    cd ~/.vim/bundle          # assume you use pathogen
    git clone git://github.com/altercation/vim-colors-solarized.git
    
在 .vimrc 中加入::
    
    set t_Co=16               # or set t_Co=256
    syntax on 
    set background=light      # or set background=dark
    colorscheme solarized
