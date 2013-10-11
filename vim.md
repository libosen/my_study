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

### 1.4 Basic Editing
* :e(dit) ~/.vimrc
* syntax on: syntax highlight
* set number
* source ~/.vimrc: reload vimconfig
* x: delete the letter on cursor
* u: undo
* dw: delete word
* db: delete before word
* 2dw: delete 2 word
* cw: delete word and into insert mode
* dd: delete whole line
* cc: delete whole line and insert mode
* 2dd: delete 2 lines
* 2cc: delete 2 liens and edit
* ct": delete the "" content 
* ci": delete the "" content and edit i(nside)
* ci): if in the (), delete and edit i(nside)
* ca): if in the (), delete,include() and edit a(round)

### 1.5 Cut, Copy and Paste
* cut: every delete command is cut command
* p: paste in the cursor after 
* P: paste in the cursor before
* dj: delete current and next line
* y: copy
* yw: copy word
* yy: copy line
* y0: copy cursor to the begin of the line
* 10p: paste 10 times
* X: delete the letter before cursor 

## 2 Digging Deeper
### 2.1 Search
* / search
* n search next
* N search back
* ? back search
* set incsearch ---- open increment search
* set ignorcase ---- ingnore case
* set hlsearch ---- highlight search
* noh --- cancle the highlight
* d /xxx ---- delete between cursor to xxx
* c /xxx ---- delete between cursor to xxx and insert
* y /xxx ---- copy ...

### 2.2 Replace
* :s/Ember/Amber ---- replace Ember with Amber in current line
* :%s/Ember/Amber ---- replace Ember with Amber in whole file 但是仅仅替换每行第一个出现的单词
* :%s/Ember/Amber/g ---- replace Ember with Amber in whole file every word
* v ---- into virtual mode
* shift+v ---- into virtual line mode
* % ---- in virtual mode , you can put cursor under (|[|{, then the % can select the match content
* gv ---- select last selection
* :s/Ember/Amber/gc ---- ask you substitue 

### 2.3 Macros and Registers
* ^G ---- Display file info
* q ---- start macro record
* a ---- record macro to a register
* :reg ---- open register

### 2.4 Advanced Movement
* ^d ---- down hakf screen
* ^u ---- up half scrren
* ^f ---- forword screen
* ^b ---- back screen
* M ---- middle the screen 
* H ---- top of the window
* L ---- bottom of th window (last line)
* 3L ---- 3 line to botom
* 3H ---- 3 line to top
