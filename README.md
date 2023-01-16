# Modern Nano Keybindings (v4.8)

[![test](https://github.com/davidhcefx/Modern-Nano-Keybindings/actions/workflows/test.yml/badge.svg?branch=v4.8)](https://github.com/davidhcefx/Modern-Nano-Keybindings/actions/workflows/test.yml)

## Features

- Common _mainstream_ keybindings.
    + `Ctrl+C`: copy
    + `Ctrl+Z`: suspend
    + `Ctrl+Q`: quit
- Vim-like support.
    + `Ctrl+F`: page-down
    + `Ctrl+G`: head-of-file
    + `Alt+G`: end-of-file
- and at the same time preserve ***all*** functionalities!
    + (many rcfiles override keys and don't assign new ones for them)

## Install

1. **This rcfile is for nano v4.8. For latest version, please see [master branch](https://github.com/davidhcefx/Modern-Nano-Keybindings).**
2. Copy the following contents into `~/.nanorc`:

```nanorc
# Version: nano 4.8
# Syntax highlights (path might be different)
include "/usr/share/nano/*.nanorc"

# Options
set tabsize 4
set tabstospaces
set linenumbers
set numbercolor yellow,normal
set suspend     # allow nano be suspended
set smarthome   # `Home` jumps to line start first
set afterends   # `Ctrl+Right` move to word ends instead of word starts
set wordchars "_"   # recognize '_' as part of a word
set zap             # delete selected text as a whole
set historylog      # remember search history
set multibuffer     # read files into multibuffer instead of insert
set mouse       # enable mouse support
#set locking     # vim-like file locks


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
## ^-T     terminal (eg. |xxd)

bind M-R  redo          main
bind ^C   copy          main
bind ^X   cut           main
bind ^V   paste         main
bind ^K   zap           main
bind ^H   chopwordleft  all
bind ^Q   exit          all
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
#bind M-F  nextword      all  # to bind to `M-left` on macOS
#bind M-B  prevword      all

bind M-1    help        all    # fix ^G been used
bind Sh-M-C constantshow main  # fix M-C, M-F and M-b been used
bind Sh-M-F formatter   main
bind Sh-M-B linter      main
```

> - If the path to **syntax highlighting files** are different on your system, please modify those `includes` around `line 3`.
> - For more colorful syntax highlightings, see: [scopatz/nanorc](https://github.com/scopatz/nanorc).

## Screenshot

<img src="screenshot.png" alt="screenshot" width="83%">
