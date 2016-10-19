Vim survivor kit
========================
2016-10-19


Enhance your vim rapidly so that you can do your tasks.



This document explains a technique to use to enhance vim rapidly.

It should work on Mac and Linux.


Overview
------------

What we want is:

- a good bookmarking system, which allows us to jump quickly from file to file (for instance /etc/apache2/sites-available/my.conf, /home/me/.bashrc) -- this is provided by the NERDTree plugin
- IDE like vim navigation keyboard shortcuts -- provided by the "decent vim navigation" config
- be able to comment/uncomment a bunch of lines in one keystroke -- provided by the Commentary plugin



1. First, we are going to install some plugins:

- [vundle](https://github.com/VundleVim/Vundle.vim) (plugin manager)
- [ctrp](https://github.com/ctrlpvim/ctrlp.vim) (fuzzy search)
- [nerdtree](https://github.com/scrooloose/nerdtree) (file tree)
- [Commentary](https://github.com/tpope/vim-commentary) (toggle comment system)


2. Then we will enhance the default navigation keyboard


If you are experimented, this should take between 1 to 3 minutes.



Plugins
----------------

First install Vundle

```bash
git clone https://github.com/VundleVim/Vundle.vim.git ~/.vim/bundle/Vundle.vim
```


Now install all other plugins, via Vundle.

Open your .vimrc, and paste the following code at the top of it.


```vim
set nocompatible              " be iMproved, required
filetype off                  " required

set rtp+=~/.vim/bundle/Vundle.vim
call vundle#begin()


Plugin 'VundleVim/Vundle.vim'
Plugin 'https://github.com/scrooloose/nerdtree'
Plugin 'https://github.com/ctrlpvim/ctrlp.vim'
Plugin 'https://github.com/tpope/vim-commentary'


" Add your own plugin ABOVE this line

call vundle#end()            " required
filetype plugin indent on    " required


map <F5> :normal! :NERDTree<cr>
nmap <C-c> gcc 
vmap <C-c> gc



```


Now, install all plugins at once. Type the following command in a terminal.

```bash
vim +PluginInstall +qall
```



Enhance keyboard navigation
----------------

Now, install the [vim decent navigation](https://github.com/lingtalfi/vim-decent-navigation) (this is the long part).




That's it, your good to go.



Memo
----------

&lt;CR> means: press the Return key.


### Vim


- basic editing
	- go to the top of the file -- gg
	- go to the bottom of the file -- G
	- go to the middle of the screen -- M
	- go to line 23 -- :g23 &lt;CR>
	- delete the current word -- diw
	- delete inside the current parenthesis -- di(
	- delete inside the current double quotes -- di"
	- delete the current line -- dd
	- replace the current word -- ciw
	- replace inside the current parenthesis -- ci(
	- replace inside the current double quotes -- ci"
	- replace the current line -- cc
	- copy the current word -- yiw
	- copy the current line -- yy
	- paste below/above the current line -- p/P
	- insert at the beginning/end of the line -- I/A
	- select the whole line -- V
	- expand/reduce the selected line(s) -- &lt;UP>/&lt;DOWN>
	- undo/redo -- u/ctrl+r
	- delete/change until end of line -- D/C
	- insert new line below/above current line and insert -- o/O
	- mark/goto the caret position with name {posName}	-- m{posName}/`{posName}
	- search forward up to the next match -- /
	- search backward up to the next match -- ?
	- replace all sharps (#) by double quotes (") in the document -- %s/#/"/g
	- edit file {fileName} -- :e {fileName}
	- clean the command line (at the bottom) - ctrl+u


- advanced editing
	- repeat the last motion -- .	
	- execute a bash command without exiting out of vim -- :! {command}
	- execute a bash command and insert the result into the document -- :read! {command}

- macros	
	- record macro x -- qx	
	- end recording macro -- q
	- execute macro x -- @x
	- execute macro x 4 times -- @4x

- windows
	- split window by drawing an horizontal line -- :sp or ctrl+w s
	- split window by drawing a vertical line -- :vsp or ctrl+w v
	- resize current window so that it spans {n} lines -- :res {n}
	- move between the panes -- ctrl+w (x2)
	- resize all windows to an equal size -- ctrl+w =
	- open the current window so that it takes the whole screen -- ctrl+w o
	- close the current window -- ctrl+w c
	- jump to the window on the {left|down|up|right} side -- ctrl+w {up|right|down|left}
	- increase/decrease the size of the current window by {number} lines -- ctrl+w {number}? +/-

- registers	
	- list the registers -- :registers
	- copy the current word to register {register} -- "{register}yiw
	- paste the content from register {register} -- "{register}p

- buffers
	- list the buffers -- :ls
	- list the buffers, including hidden buffers -- :ls!
	- go to buffer {buffer} -- :b{buffer}
	- go to the last buffer -- :b#
	- delete the current buffer, or the specified {buffer} -- :bd{buffer,...}?
	- delete buffers 22 to 24 -- :22,24bd
	- delete all buffers -- :%bd
	- go to the next buffer -- :bn
	- go to the previous buffer -- :bp
	- execute {command} on all files in the buffer -- :bufdo {command}
	- delete the Hithere expression in all files in the buffer -- :bufdo g/"\s*Hithere/d

- tabs:
	- open the {file} in a new tab -- :tabedit {file}
	- list all tabs -- :tabs
	- go to the next tab -- gt
	- go to the previous tab -- gT
	- go to tab number {i}, starting at 1 left to right -- {i}gt


- configuration	
	- add/remove line numbers -- :set number/:set nonumber


### NERDTree

Use vim windows (and tabs) shortcuts when appropriate.


- general
	- open NERDTree -- &lt;F5> (custom map from your .vimrc)
	- quit -- q
	- quit both the tree and the opened buffers -- qall
	- help -- ?
	- show the menu -- m
		- create a new file (node) in the current dir -- a
		- reveal in finder the current node -- r
		- move a file -- m

- navigating
	- open split (drawing horizontal line) -- i
	- open vsplit (drawing vertical line) -- s
	- open in new tab -- t
	- change to the directory under cursor -- cd
	- change root to the directory under cursor -- C
	- refresh cursor dir -- r
	- refresh current root -- R

- tree filtering
	- show/hide hidden files -- I	
	- show/hide files -- F


- bookmarks
	- show/hide the bookmarks -- B
	- create the {name} bookmark -- :Bookmark {name}
	- clear bookmarks -- :ClearBookmarks {name}



### CtrlP

- open ctrlP -- ctrl+p
- open ctrlP on {dir} -- :CtrlP {dir}
- close ctrlP -- &lt;ESC>
- cycle between file/buf/mru modes -- ctrl+f
- cycle between filename/path mode -- ctrl+d
- toggle regexp mode -- ctrl+r


### Commentary

- comment the current line -- gcc or ctrl+c (custom map from your .vimrc)
- comment the selected (visual) line(s) -- gc or ctrl+c (custom map from your .vimrc)



Related
-------------
- [vim decent navigation](https://github.com/lingtalfi/vim-decent-navigation)
- [vim survivor kit](https://github.com/lingtalfi/vim-survivor-kit)
- [vim refresher notes](https://github.com/lingtalfi/vim-refresher-notes)


Sources
------------
- https://github.com/VundleVim/Vundle.vim


