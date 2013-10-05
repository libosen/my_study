Tutsplus: Venture into Vim
==========================
## 1 Introduction
### 1.1 Introduciton

Vim < vi  
Vim < Bram Moolenaar

* Agenda
	* Introduciton
		* Installation
		* Movement & edition
		* Cut, copy and paste
		* .vimrc for beginners
	* Digging deeper
		* search & Replace
		* Macros and registers
		* Advanced movement
		* Command line from Vim
		* Buffers
	* Vim as the extention of Vi
		* Windows/panes and tabs
		* Graphical Vim: Gvim
		* indents and folds
	* Cusomization
		* The .vimrc file
		* Plugins
		* Themes
		* Mappings
		* Final Tips

### 1.2 Modes and Basic Movement
* Normal mode, Insert Mode, Command Mode 
* Insert Mode: i
* Back command Mode: esc
* :w(rite) xxxx.xxx
* :q(uit)
* movement: h j k l

### 1.3 Faster Movement
* w: word forword
* b: word back
* W: word forword (skip hyphen)
* B: word back (skip hyphen)
* $: go to end of line
* ^: go to start of line(none blank)
* 0: go to begin of line
* gg: go to begin of file
* G: go to end o file
* }: paragraph to paragraph forward
* {: patagraph to paragraph back
* f(x): the first letter in the line(forward)
* F(x): the first letter int the line(back)
* t(x): the front of the first letter in the line(forword)
* T(x): the front of the first letter in the line(back)
* 2fw: the second w in the line
	* you can use the number to repeat the command
* 3j: go to the next 3 lines
	* 4k 9h 8l
	* 3gg/3G: go to the 3rd line
	* :14: go to the 14th line
