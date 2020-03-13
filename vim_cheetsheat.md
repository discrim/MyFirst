# Vim Cheetsheat
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
```
### Insert Actual Tab
Source: [Stackoverflow](https://stackoverflow.com/questions/6951672/how-can-i-insert-a-real-tab-character-in-vim/6951704)  
- Type CTRL + V then TAB.
- Using CTRL + V signals Vim that it should take the next character literally. Even in insert mode.
### Command Mode Commands (Case-Sensitive)
- `:NUMBER`: Jump to NUMBERth line. E.g.`:5` jumps you to 5th line.
- `u`: Undo
