Configure VIM
=============

Step 1:
-------
Create a vimrc configuration file:

	vi ~/.vimrc
	
This is a per user configuration file.

Step 2:
-------
Add the following content:

	" This is a comment
	
	syntax on 													" turn syntax highlighting on
	set mouse-=a 												" allow copy pasting by right click
	highlight Visual cterm=bold ctermbg=Grey ctermfg=NONE		" set color vor visual mode