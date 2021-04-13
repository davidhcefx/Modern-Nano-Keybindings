# Modern Nano Keybindings
[![test](https://github.com/davidhcefx/Modern-Nano-Keybindings/actions/workflows/test.yml/badge.svg)](https://github.com/davidhcefx/Modern-Nano-Keybindings/actions/workflows/test.yml)

## Features

- Common _mainstream_ keybindings.
    - eg. `Ctrl+C` to copy, `Ctrl+V` to paste, `Ctrl+Q` to quit, etc.
- Vim-like support.
    - eg. `Ctrl+F` for page-down, `Ctrl+G` to go to *head-of-file*, etc.
- and at the same time preserve _all_ default functionalities!

## Install

1. Make sure you are running the [latest nano](https://www.nano-editor.org/) (>= 5.4).
2. Copy the following contents into `~/.nanorc`.

```nanorc
# Version: nano 5.4
# Syntax highlights (path might be different)
include "/usr/share/nano/*.nanorc"
include "/usr/share/nano/extra/*.nanorc"

# Options
set tabsize 4
set tabstospaces
set indicator   # side-bar for indicating cur position
set linenumbers
set numbercolor yellow,normal
set mouse
set suspendable # allow nano be suspended
set smarthome   # home jumps to line start first
set zap         # delete selected text as a whole
set afterends   # Ctrl+Right move to word ends instead of word starts
set wordchars "_"   # recognize _ as part of a word
#set rawsequences    # get keystroke without asking ncurses


#####  Modern Nano Keybindings  #####
## M-U   undo
## M-R   redo
## ^-C   copy
## ^-X   cut
## ^-V   paste
## ^-K   delete line
## ^-bsp delete until word start (or M-bsp)
## ^-del delete until next word
## ^-L   refresh
## ^-S   save file
## M-/   comment/uncomment
## M-V   insert keystroke verbatim
## M-:   record macro
## M-;   play macro

## M-C   cursor position
## ^-W   search forward (= M-W + prompt)
## ^-E   seach backwards (= M-E + prompt)
## ^-up  goto previous block
## ^-dn  goto next block
## M-(   goto block begin
## M-)   goto block end
## ^_    goto line/coloumn number
## ^-G   head of file (vim-like)
## M-G   end of file
## M-up  screen up one line
## M-dn  screen down one line
## M-]   goto matching bracket
## M-ins   insert anchor
## M-pgup  goto previous anchor
## ^-T   terminal (eg. |xxd)

unbind ^Y  main  # remove unused bindings
unbind ^A  main
unbind M-Q all

bind M-R  redo          main
bind ^C   copy          main
bind ^X   cut           main
bind ^V   paste         main
bind ^K   zap           main
bind ^H   chopwordleft  all
bind ^Q   exit          all
bind M-/  comment       main

bind M-C  curpos        main
bind ^E   wherewas      all
bind M-E  findprevious  all
bind ^B   pageup        all  # vim-like support
bind ^F   pagedown      all
bind ^G   firstline     all
bind M-G  lastline      all
bind M-F  constantshow  main  # fix M-C been used
```

> - If the path to **syntax highlighting files** are different on your system, please modify those `includes` around `line 3`.  
> - For more colorful syntax highlightings, see: [scopatz/nanorc](https://github.com/scopatz/nanorc).