if v:lang =~ "utf8$" || v:lang =~ "UTF-8$"
   set fileencodings=ucs-bom,utf-8,latin1
endif

set nocompatible	" Use Vim defaults (much better!)
set bs=indent,eol,start		" allow backspacing over everything in insert mode
"set ai			" always set autoindenting on
"set backup		" keep a backup file
set viminfo='20,\"50	" read/write a .viminfo file, don't store more
			" than 50 lines of registers
set history=50		" keep 50 lines of command line history
set ruler		" show the cursor position all the time

" Only do this part when compiled with support for autocommands
if has("autocmd")
  augroup redhat
  autocmd!
  " In text files, always limit the width of text to 78 characters
  autocmd BufRead *.txt set tw=78
  " When editing a file, always jump to the last cursor position
  autocmd BufReadPost *
  \ if line("'\"") > 0 && line ("'\"") <= line("$") |
  \   exe "normal! g'\"" |
  \ endif
  " don't write swapfile on most commonly used directories for NFS mounts or USB sticks
  autocmd BufNewFile,BufReadPre /media/*,/mnt/* set directory=~/tmp,/var/tmp,/tmp
  " start with spec file template
  autocmd BufNewFile *.spec 0r /usr/share/vim/vimfiles/template.spec
  augroup END
endif

if has("cscope") && filereadable("/usr/bin/cscope")
   set csprg=/usr/bin/cscope
   set csto=0
   set cst
   set nocsverb
   " add any database in current directory
   if filereadable("cscope.out")
      cs add cscope.out
   " else add database pointed to by environment
   elseif $CSCOPE_DB != ""
      cs add $CSCOPE_DB
   endif
   set csverb
endif

" Switch syntax highlighting on, when the terminal has colors
" Also switch on highlighting the last used search pattern.
if &t_Co > 2 || has("gui_running")
  syntax on
  set hlsearch
endif

filetype plugin on

if &term=="xterm"
     set t_Co=8
     set t_Sb=[4%dm
     set t_Sf=[3%dm
endif

" Don't wake up system with blinking cursor:
" http://www.linuxpowertop.org/known.php
let &guicursor = &guicursor . ",a:blinkon0"

"Add by Yc"
syntax on
set autoindent
set cindent
"set cursorline
set ru
set number
set cursorcolumn"

autocmd bufNewFile *.py,*.sh, exec ":call SetTitle()"
let $author_name = "Yc"
let $author_email = "1522105005@qq.com"
 
func SetTitle()
if &filetype == 'sh'
call setline(1,"\###############################################")
call append(line("."),"\# File Name:".expand("%"))
call append(line(".")+1,"\# Author: ".$author_name)
call append(line(".")+2,"\# Mail : ".$author_email)
call append(line(".")+3,"\# Created Time: ".strftime("%c"))
call append(line(".")+4,"\#===============================================")
call append(line(".")+5,"\#!/bin/bash")
call append(line(".")+6,"")
else
call setline(1,"\###############################################")
call append(line("."),"\# File Name:".expand("%"))
call append(line(".")+1,"\# Author: ".$author_name)
call append(line(".")+2,"\# Mail : ".$author_email)
call append(line(".")+3,"\# Created Time: ".strftime("%c"))
call append(line(".")+4,"\#==============================================")
call append(line(".")+5,"\#!/usr/bin/python")
call append(line(".")+6,"")
endif
autocmd BufNewFile * normal G
endfunction
