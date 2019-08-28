---
title: Vim cheat sheet
date: 2018-08-29 17:03:34
tags: [vim]
---

https://vim.rtorr.com/

## Use relative line mode with vim

In vim, you will frequently need to manipulate multi line with `3dd` `4yy` or something else, relative line mode in IDE could help you easy to count the line number.
if you are using VScode like me, you could enable it by add the line to user setting:

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

# replace word with yanked word
viwp

# Comment multi line, for example using # for comment
1. Ctrl + v to enter "Visual block mode"
2. Move cursor to select lines that need to be edited
2. Shift + i
3. #
4. Esc
```

## Common command

```bash
# get recent command list
q:

# Replace word A with word B
:%s/A/B/g

# Next word
w

# Previous word
b

# copy (yank)
y

# copy line
yy

# paste
p

# delete
d

# Undo
u

# Redo
ctrl + r

# Show Line numbers
set number
```
