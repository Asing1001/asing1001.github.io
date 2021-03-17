---
title: Awesome Vim cheat sheet
date: 2018-08-29 17:03:34
tags: [vim, line number]
---

## Switch mode

### Insert mode

- i
  - insert before the char
- I
  - insert before the start of line
- a
  - append after the char
- A
  - append at the end of line

### Normal mode

- ESC

### Visual mode

- v
  - select a char
- V
  - select a line
- Ctrl + v
  - visual block mode

## Move cursor(Normal mode)

### char

- h
- j
- k
- l

### Word

- w
  - go to next start of word
- e
  - go to end of word
- b
  - back to start of word

### Block & Paragraph

- {}
  - paragraphs forward/backward
- ()
  - sentences forward/backward
- []
  - goto []
- [{ or }] or [( or )] or [[ or ]]
  - goto start/end of { or ( or [
- %
  - go to the match bracket

### Window

- H
  - Top of window
- L
  - Last of window
- M
  - Middle of window

### File

- gg
  - Start
- G
  - end of file

### Others

- ctrl+o
  - previous jump position
- ctrl+i
  - next jump position
- g;
  - previous Change position
- g,
  - next Change position

## Scroll

- zt
  - scroll current line to top
- zb
  - scroll current line to bottom
- zz
  - scroll current line to middle

## Search

### Search char in single line (keep normal mode)

- f/F
  - find char, forward/backward
  - `abcABCabc`, `fC` to find middle C
- t/T
  - Go to previous char before the char, forward/backward
  - `foo.bar<>` , go to r by `t<`
- ;
  - Repeat t/T/f/F
- ,
  - Reverse t/T/f/F

### Search in file

- /
  - Search forward
- ?
  - Search backward
- n and N
  - next and previous
- *, #
  - search next/previous current word

## Edit

- insert line before/after the current line
  - o, O
- join two line (keep mode)
  - j
- yank (copy) the current line
  - yy, Y
- Cut and change to insert mode
  - c
    - Change
  - s
    - substitute
  - C
    - Cut to end of line
  - S
    - Delete line and go to insert mode
- delete
  - d(keep mode)
    - `d3j` or `3dd`
  - x and X
    - delete and backspace
- replace
  - r
- repeat action
  - .
- Macro
  - q + a~z
    - record macro to key in a~z
  - normal mode + q to quit recording
  - @ + a~z to excute macro
- Bookmark
  - m + a~z
    - bookmark current location to a~z
  - ` + a~z
    - go to a~z bookmark
  - \``
    - go to last position
- [registers](https://www.brianstorti.com/vim-registers/)
  - " + registerKey (a~z, 0~9, "+*/:%-)
    - `:reg` to see all registers
    - `"` is the default(unnamed) register
    - `0` is the default register for `y`(yank)
    - `+`, `*` is the system clipboard
    - `/` stores the latest search keyword
    - `:` stores the latest used command
    - `%` has the current file path
    - `#` has the last edited file
    - In command mode, `ctrl+r+<register>` to paste the register content into the command.
    - e.g. `*:/s/<ctrl+r>//abc/gc` to replace the lastest search keyword(*) to `abc` with confirmation dialog
    - e.g. `"adw` : delete the and save it to register `a`
    - e.g. `"0p` : paste from last yank
    - e.g. to copy `foo` and replace it with `bar`, `yw` then `/bardw"0p`
  - In search mode, you could press `ctrl + r + register key` to use the value in register
- Join lines
  - J

## Concept

- There are three dimention in vim
  - window, file, project
- Use vim like your mouse
  - e.g. delete `Bar` in `fooBarBeBaz`, `fBdfe`

## Useful vim command combination list

```bash
# Make a word uppercase
gUe

# edit neariest word inside symbol, e.g. }
ci}

# edit neariest word outside symbol, e.g. ]
ca]

# edit and delete from cursor to next symbol, e.g. )
ct)

# edit and delete from cursor to previos symbol, e.g. )
cT)

# delete inside tag
dit

# replace word with yanked word
viwp

# Comment multi line, for example using # for comment
1. Ctrl + v to enter "Visual block mode"
2. Move cursor to select lines that need to be edited
3. Shift + i
4. #
5. Esc

# Show Line numbers
:set number

# Set relative line number
:set rnu

# get recent command list
q:

# Replace word A with word B
:%s/A/B/g

# Undo/Redo
u / Ctrl+r

# increase the first right number in the line
Ctrl + A

# decrease the first right number in the line
Ctrl + X
```

## Use relative line mode with vim

In vim, you will frequently need to manipulate multi line with `y3j` `4yy` or something else, relative line mode in IDE could help you easy to count the line number.

- In vim

```vi
:set rnu
```

- In VSCode:

```json
"editor.lineNumbers": "relative",
```

## Get difference before save

```bash
:w !diff % -
```

### Explanation

- `w` without filename will save to stdin
- `!` will excute bash in vim
- `%` is current file in vim
- `diff` with `-` will read content from stdin

## vimrc

`"` is the comment symbol in .vimrc, could only be placed at the start of line

```vi
"Enable copy paste from system clibboard
set clipboard^=unnamed,unnamedplus

"Show differt cursor in different mode
let &t_SI = "\<Esc>]50;CursorShape=1\x7"
let &t_SR = "\<Esc>]50;CursorShape=2\x7"
let &t_EI = "\<Esc>]50;CursorShape=0\x7"

"Show relative line number
set rnu
```

### Reference

- https://vim.rtorr.com/
- http://vimdoc.sourceforge.net/htmldoc/motion.html
- https://www.brianstorti.com/vim-registers/
