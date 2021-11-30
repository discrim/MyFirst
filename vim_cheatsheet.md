# Vim Cheatsheet
1. [Initial `~/.vimrc` Setting](#initial-vimrc-setting)
1. [Insert Actual Tab](#insert-actual-tab)
1. [Command Mode Commands (Case-Sensitive)](#command-mode-commands-case-sensitive)
1. [Tab Multiple Lines](#tab-multiple-lines)
### Initial ~/.vimrc Setting
```vim
set nu
set autoindent
set cindent
set shiftwidth=4
set tabstop=4
set expandtab
set history=1000
set ruler
syntax on
filetype indent on
colorscheme elflord
```
### Insert Actual Tab
Source: [Stackoverflow](https://stackoverflow.com/questions/6951672/how-can-i-insert-a-real-tab-character-in-vim/6951704)  
- Type CTRL + V then TAB.
- Using CTRL + V signals Vim that it should take the next character literally. Even in insert mode.
### Command Mode Commands (Case-Sensitive)
- `:NUMBER`: Jump to NUMBERth line. E.g.`:5` jumps you to 5th line.
- `u`: Undo
### Tab Multiple Lines
Sourse: [fir3net.com](https://www.fir3net.com/UNIX/General/how-do-i-tab-multiple-lines-within-vi.html)
1. Press "SHIFT + v" to enter VISUAL LINE mode.
1. Select the text you wish to indent but using either the cursor keys or the "j" and "k" keys.
1. To indent press "SHIFT + dot" (> character).
