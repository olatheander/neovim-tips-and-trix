# Vim/Neovim Tips & Tricks

## Line numbers

`{number}` - an absolute line number

`.` - the current line

`$` - the last line in the file

`%` - equal to `1,$` (the entire file)

## Command mode

`:` - enter command mode.

`:w` - write the file.

`:wq` - write and quit.

`:q` - quit.

`:q!` - quit without saving.

`:e {file}` - edit a file.

`:set number` - show line numbers.

`:set nonumber` - hide line numbers.

`:set list` - show white space characters (e.g. tabs, spaces).

`:set nolist` - hide white space characters.

`:help {command}` - show help for a command.

`!{command}` - execute a shell command.

`.!{command}` - execute a shell command and replace the current line with its output, e.g. `.!ls`.

`:r {file}` - read a file and insert its content at the current cursor position.

`:r !{command}` - read the output of a shell command and insert it at the current cursor position, e.g. `:r !ls`.

`:r !{command} | {filter}` - read the output of a shell command and filter it, e.g. `:r !ls | grep txt`.

`:s/{pattern}/{replacement}/` - substitute the first occurrence of `pattern` with `replacement` on the current line.

`:s/{pattern}/{replacement}/g` - substitute all occurrences of `pattern` with `replacement` on the current line.

`:s/{pattern}/{replacement}/c` - confirm each substitution.

`:g/{pattern}/{command}` - act on the range of lines matching `pattern` and execute `command` on them.

E.g. `:g!/{pattern}/d` - delete all lines not containing pattern

`:v` - inverse of `g` (not matching pattern).

## Normal mode

### Cursor movement

`e` - jump forwards to the end of a word

`E` - jump forwards to the end of a word (words can contain punctuation)

`b` - jump backwards to the start of a word

`B` - jump backwards to the start of a word (words can contain punctuation)

`ge` - jump backwards to the end of a word

`gE` - jump backwards to the end of a word (words can contain punctuation)

`0` - jump to the start of the line

`^` - jump to the first non-blank character of the line

`$` - jump to the end of the line

`g_` - jump to the last non-blank character of the line

`;` - repeat previous f, t, F or T movement

`,` - repeat previous f, t, F or T movement, backwards

### Editing

`c$` or `C` - change (replace) to the end of the line

`d$` or `D` - delete (cut) to the end of the line

`r` - replace a single character.

`R` - replace more than one character, until ESC is pressed.

`cc`/`S` - change (replace) entire line

`xp` - transpose two letters (delete and paste)

`u` - undo

`U` - restore (undo) last changed line

. - repeat last command

### Misc

`q:` - command line history.

## Visual mode

`o` - move to other end of marked area

`O` - move to other corner of block (block mode)

`~` - switch case

`u` - change marked text to lowercase

`U` - change marked text to uppercase

## Insert mode

### Commands in insert (and command) mode

`CTRL-E` - Insert character which is below the cursor.

`CTRL-Y` - Insert character which is above the cursor.

`CTRL-W` - Delete word before the cursor.

`CTRL-H` - Delete character before the cursor.

`CTRL-T` - Indent to the right.

`CTRL-D` - Indent to the left.

`CTRL-O` - Execute one command and return to normal node.

`CTRL-M` - New line, just like `<CR>`.

`CTRL-G j/k` - Move down/up a line in insert mode.

`CTRL-A` - Insert previously inserted text.

`CTRL-V` - Insert literally (e.g. `CTRL-V` followed by `Esc` will insert an actual `Esc` character).

`CTRL-U` - Delete everything before the cursor on the current line.

`CTRL-N` - Next completion.

`CTRL-P` - Previous completion.

`CTRL-X` - CTRL-X mode

#### Scrolling

`CTRL-Y` - Scroll window [count] lines upwards in the buffer.

`CTRL-U` - Scroll window Upwards by half a screen.

`CTRL-B` - Scroll window [count] pages Backwards (upwards).

`z^` - Redraw with the line just above the window at the bottom of the window.

`CTRL-E` - Scroll window [count] lines downwards in the buffer.

`CTRL-D` - Scroll window downwards by half a screen.

`CTRL-F` - Scroll window [count] pages Forwards (downwards).

`z+` - Redraw with the line just below the window at the top of the window.

`zt` - Draw current line at the top of the window.

`zz` - Center the current line in the window.

`zb` - Draw current line at the bottom of the window.

#### Insert mode completion

`CTRL-X CTRL-F` - File name completion.

## Macros

`qa` - record macro to register `a`.

`q` - stop recording macro

`@a` - run macro `a`

`@@` - rerun last run macro

Since macros are stored in the same registers that are used for yanking text, we can paste a macro as text, change it as we want (fix a mistake), and then yank back into the register.

## Registers

`:reg[isters]` - show registers content

`"xy` - yank into register `x`

`"xp` - paste contents of register `x`

`"+y` - yank into the system clipboard register

`"+p` - paste from the system clipboard register

Registers are being stored in `~/.viminfo` and will be loaded again on next restart.

### Special registers

`0` - last yank

`"` - unnamed register, last delete or yank

`%` - current file name

`#` - alternate file name

`*` - clipboard contents (X11 primary)

`+` - clipboard contents (X11 clipboard)

`/` - last search pattern

`:` - last command-line

`.` - last inserted text

`-` - last small (less than a line) delete

`=` - expression register

`_` - black hole register

## Marks and positions

`:marks` - list of marks

`ma` - set current position for mark A

\`a - jump to position of mark A

y`a - yank text to position of mark A

\`0 - go to the position where Vim was previously exited

\`" - go to the position when last editing this file

\`. - go to the position of the last change in this file

\`\` - go to the position before the last jump

`:ju[mps]` - list of jumps

`CTRL + i` - go to newer position in jump list

`CTRL + o` - go to older position in jump list

`:changes` - list of changes

`g,` - go to newer position in change list

`g;` - go to older position in change list

`CTRL + ]` - jump to the tag under cursor

To jump to a mark you can either use a backtick (`) or an apostrophe ('). Using an apostrophe jumps to the beginning (first non-blank) of the line holding the mark.

## Cut and paste

`p` - put (paste) the clipboard after cursor

`P` - put (paste) before cursor

`gp` - put (paste) the clipboard after cursor and leave cursor after the new text

`gP` - put (paste) before cursor and leave cursor after the new text

## Indent text

`>>` - indent (move right) line one shiftwidth
`<<` - de-indent (move left) line one shiftwidth

`>%` - indent a block with () or {} (cursor on brace)

`<%` - de-indent a block with () or {} (cursor on brace)

`>ib` - indent inner block with ()

`>at` - indent a block with <> tags

`3==` - re-indent 3 lines

`=%` - re-indent a block with () or {} (cursor on brace)

`=iB` - re-indent inner block with {}

`gg=G` - re-indent entire buffer

`]p` - paste and adjust indent to current line

## Search and replace

`/pattern` - search for pattern

`?pattern` - search backward for pattern

`\vpattern` - 'very magic' pattern: non-alphanumeric characters are interpreted as special regex symbols (no escaping needed)

### Search in multiple files

`:vim[grep] /pattern/ {`{file}`}` - search for pattern in multiple files

e.g. `:vim[grep] /foo/ **/*`

`:cn[ext]` - jump to the next match

`:cp[revious]` - jump to the previous match

`:cope[n]` - open a window containing the list of matches

`:ccl[ose]` - close the quickfix window

## Diff

`$nvim -d {file1} {file2} {file3}` - open Neovim in diff-mode

`]c` - jump to start of next change

`[c` - jump to start of previous change

`do` or `:diffg[et]` - obtain (get) difference (from other buffer)

`dp` or `:diffpu[t]` - put difference (to other buffer)

`:difft[his]` - make current window part of diff

`:diffs[plit] {filename}` - open a new window on the file `{filename`.

`:dif[fupdate]` - update differences

`:diffo[ff]` - switch off diff mode for current window

`windo difft/diffo` - apply `difft`/`diffo` to all windows.

## Fun stuff

### Execute normal commands from command mode

`norm` - Execute normal commands from command mode.

E.g. do `:norm _isrc={f,i}` on the line 1-3 below (the `` is `CTRL-V` followed by `Esc` to put in an actual `Esc` character):

```
lorem,
ipsum,
dolor,
sit,
amet,
consectetur,
adipiscing,
elit,
```

expected result:

```
src={lorem},
src={ipsum},
src={dolor},
sit,
amet,
consectetur,
adipiscing,
elit,
```

## Use ripgrep to grep

Use `rg` as built in `:grep` command:

```
:set grepprg=rg\ --vimgrep

```

Search for `my-search-string` using ripgrep's arguments in the current folder but exclude all folders containing `test` and send the result to the quickfix list:

```
:grep -F -n -g '**/*' -g '!**/test/**' "my-search-string" . | cw

```
