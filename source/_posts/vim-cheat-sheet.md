---
title: Awesome Vim cheat sheet
date: 2018-08-29 17:03:34
tags: [vim, introduction, trick, must know]
---

- [My slides share](https://www.paddingleft.com/slides/html/vim.html)[
- [Coding faster with Vim + IDE](/2021/09/24/Coding-faster-with-Vim-IDE/)

## Mode

- insert
- normal
- visual
- command

---

### Insert mode

- i
  - insert before the cursor
- I
  - insert before the start of line
- a
  - append after the cursor
- A
  - append at the end of line

---

### Normal mode

- `<ESC>`

---

### Visual mode

- v
  - select a char
- V
  - select a line
- Ctrl + v
  - visual block mode

---

### Command mode

`:` + `<command>`

```vim
:wq
:cq
:set rnu
```

---

## Cursor movement

---

### Char

- h (left)
- j (down)
- k (up)
- l (right)
- Combile with number to move, `2k` to jump 2 lines up
- Relative line numbers `:set rnu`

---

### Word

- w or W
  - jump forwards to the start of a word
- e or E
  - jump forwards to the end of a word
- b or B
  - jump backwards to the start of a word
- Capital case can contain `punctuation`

---

### Single line

- $ - end of line
- ^ - start of the line after the indentation
- 0 - move to the column 0

---

### Text Object motion

- {}
  - paragraphs forward/backward
- ()
  - sentences forward/backward
- []
  - backward/forward sections

---

### Pair

- %
  - go to the match bracket

---

### Screen

- H
  - move to top of screen
- M
  - move to middle of screen
- L
  - move to bottom of screen

---

### File

- gg
  - Start
- G
  - end of file
- :`<absolute-line-numbers>`
  - move to the absolute line

---

### Scroll

- zt
  - scroll current line to top
- zb
  - scroll current line to bottom
- zz
  - scroll current line to middle

---

## Search

---

### Search char in single line

- f/F
  - find char, forward/backward
  - `abcABCabc`, `fC` to find middle C
- t/T
  - Go to previous char before the char, forward/backward
  - `foo.bar<>` , move to r by `t<`
- ;
  - Repeat `t/T/f/F`
- ,
  - Reverse `t/T/f/F`

---

### Search in file

- /
  - Search forward
- ?
  - Search backward
- n and N
  - next and previous
- *, #
  - search next/previous current word
  - The behavior is identical to /`word`

---

## Edit

- Undo/Redo
  - u / Ctrl+r

---

### Insert

- insert line before/after the current line
  - o, O
- join two line (keep mode)
  - J

---

### Copy

- y + motion
  - combine with any motion, e.g. `yt;` or `yw`
- yy = Y
  - yank (copy) the current line

---

### Paste from clipboard registry

- p
  - paste after

- P
  - paste before

---

### Cut and switch to insert mode

- c + motion
  - Cut
- C
  - Cut to end of line
- s
  - Substitute the char under the cursor
- S
  - Substitube the line
- r
  - replace a char
- R
  - Enter the insert-replace mode

---

### Cut and keep in normal mode

- d
  - `d3j` or `3dd`
- D
  - Delete to end of the line
- dd
  - Delete the entire line
- x and X
  - delete and backspace

---

### inside / around

```bash
# edit neariest word inside symbol, e.g. }
ci}

# edit neariest word outside symbol, e.g. ]
ca]

# delete inside tag
dit

# replace word with yanked word
vi]p

```

---

### Repeat action

- repeat action
  - .

---

### Macro

- `q` + `a~z`
  - record macro to `a~z`
- `normal mode` + `q` to quit recording
- `@` + `a~z` to excute macro

---

### Bookmark

- `m` + `a~z`
  - bookmark current location to `a~z`
- `'` + `a~z`
  - go to a~z bookmark
- `''`
  - go to the last position

---

### [Registers](https://www.brianstorti.com/vim-registers/)

- `"` + `a~z` `0~9` `"+*/:%-`
  - `:reg` see all registers
  - `"` the default(unnamed) register
  - `0` the default register for `y`(yank)
  - `+`, `*` the system clipboard
  - `/` the latest search keyword
  - `:` the latest used command
  - `%` the current file path
  - `#` the last edited file

> "adw : delete the word and save to register `a`

===

### Registers - Advance

- `"0p` - paste from last yank
- Use the register in the `Search` and `Command mode`
  - `ctrl` + `r` + `<register>`

> `*:%s/<ctrl+r>//abc/gc` to replace the lastest search keyword(*) to `abc` with confirmation dialog

---

### Change multi line

1. `Ctrl + v` to enter `Visual block mode`
2. Move cursor to select lines that need to be edited
3. `Shift + i`
4. `#`
5. Esc

---

### More

```bash
# increase the first right number in the line
Ctrl + A

# decrease the first right number in the line
Ctrl + X

# Make a word uppercase
gUe

# Show Line numbers
:set number

# Set relative line number
:set rnu

# get recent command list
q:

# Replace word A with word B
:%s/A/B/g

```

---

### More...and more

- ctrl+o
  - previous jump position
- ctrl+i
  - next jump position
- g;
  - previous Change position
- g,
  - next Change position

---

## vim X IDE

---

### Setup

- Ideavim
  1. click the `V` icon on the right bottom corner
  2. open `~/.ideavimrc`
  3. edit and save

- [VScode](https://github.com/Asing1001/tennis-kata#setup-vscode-configs)

---

## Reference

- [vim doc](http://vimdoc.sourceforge.net/htmldoc/motion.html)
- [vim register](https://www.brianstorti.com/vim-registers/)
- [vim cheatsheet](https://vim.rtorr.com/)

---

### Get the difference before saving in vim

```bash
:w !diff % -
```

- `w` without filename will output to stdin
- `!` will excute bash in vim
- `%` is current file in vim
- `diff` with `-` will read content from stdin
