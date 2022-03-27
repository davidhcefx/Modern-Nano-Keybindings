# Modern Nano Keybindings

[![test](https://github.com/davidhcefx/Modern-Nano-Keybindings/actions/workflows/test.yml/badge.svg?branch=master)](https://github.com/davidhcefx/Modern-Nano-Keybindings/actions/workflows/test.yml)

## Features

- Common _mainstream_ keybindings.
    + `Ctrl+C`: copy
    + `Ctrl+Z`: suspend
    + `Ctrl+Q`: quit
- Vim-like support.
    + `Ctrl+F`: page-down
    + `Ctrl+G`: head-of-file
    + `Alt+G`: end-of-file
- ...and at the same time preserve ***all*** functionalities!
    + (many rcfiles overrode keys and didn't assign new ones for them)

## Install

1. Make sure you are running the [latest nano](https://www.nano-editor.org/).
    - If you are using a legacy version, please take a look at [other branches](https://github.com/davidhcefx/Modern-Nano-Keybindings/branches)!
2. Copy the following contents into `~/.nanorc`:

```nanorc
# Version: nano 6.2
# Syntax highlights (path might be different)
include "/usr/share/nano/*.nanorc"
include "/usr/share/nano/extra/*.nanorc"

# Options
set tabsize 4
set tabstospaces
set linenumbers
set numbercolor yellow,normal
set indicator   # side-bar for indicating cur position
set mouse       # enable mouse support
set smarthome   # `Home` jumps to line start first
set zap         # delete selected text as a whole
set afterends   # `Ctrl+Right` move to word ends instead of word starts
set wordchars "_"   # recognize '_' as part of a word
set historylog      # remember search history


#####  Modern Nano Keybindings  #####
## M-U   undo
## M-R   redo
## ^-C   copy
## ^-X   cut
## ^-V   paste
## ^-K   delete line
## ^-bsp delete until word start (or M-bsp)
## ^-del delete until next word
## ^-L   refresh and center cursor
## ^-S   save file
## M-/   comment/uncomment
## M-V   insert keystroke verbatim
## M-:   record macro
## M-;   play macro
## ^-Space  autocomplete word

## M-C   cursor position
## ^-W   search forward (= M-W + prompt)
## ^-E   seach backwards (= M-E + prompt)
## ^-R   replace
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
bind ^Z   suspend       main
bind M-/  comment       main
bind ^Space complete    main

bind M-C  curpos        main
bind ^E   wherewas      all
bind M-E  findprevious  all
bind ^R   replace       main
bind ^B   pageup        all  # vim-like support
bind ^F   pagedown      all
bind ^G   firstline     all
bind M-G  lastline      all
bind M-1  help          all  # fix ^G been used
bind Sh-M-C  constantshow  main  # fix M-C been used
```

> - If the path to **syntax highlighting files** are different on your system, please modify those `includes` around `line 3`.
> - For more colorful syntax highlightings, see: [scopatz/nanorc](https://github.com/scopatz/nanorc) :-)

## Screenshot

<img src="screenshot.png" alt="screenshot" width="83%">
