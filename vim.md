# (neo)vim

### Sources

- `vimtutor`
- [Learn vim for the last time](https://danielmiessler.com/p/vim)
- TODO: Drew Neil, Practical Vim

## Modes

- I mapped `jk` to switch from insert to normal mode
- `v` goes to *normal* visual mode (selecting text)
  - `V` selects by line
  - `C-v` selects by *rectangle* (like emacs did!)

## Config

Translating VimScript options to lua:

vimscript | lua
--------- | ---
`language en_US.utf8` | `vim.cmd('language en_US.utf8')`
`set myoption` | `vim.opt.myoption = true`
`set myoption=2` | `vim.opt.myoption = 2`
`set myoption=sth` | `vim.opt.myoption = 'sth'`

## Vim as a language

From [Learn vim for the last time](https://danielmiessler.com/p/vim)

### Verbs

char | verb
---- | ----
d | delete
c | change
y | yank (copy)
v | visually select (V for entire lines) 

### Modifiers

char | modification
---- | ------------
i | inside
a | around
NUM | number (e.g.: 1, 2, 10)
t | "to": to char (excluding) (`;` for next, `,` for previous)
f | "find": to char (including) (these only work on the current line)
/ | find a string (literal or regex) 

### Nouns

char | noun
---- | ----
w | word
s or )| sentence
p or } | paragraph
t | tag (think HTML/XML)
b | block (think programming) 

### Sentences

Some examples:

sentence | description
-------- | -----------
d2w | delete 2 words
cis | change inside sentence
yip | yank inside paragraph
gqap | format around paragraph
ct< | change until the next open bracket

## Normal mode

### Help

cmd | description
--- | -----------
`F1` or `:help` | Opens a new help window
`C-w C-w` | Switch between windows
`:e C-d` | Shows completions of commands that start with `e`

### Movement

cmd | description
--- | -----------
`gg` | Goto line 0
`10G` | Goto line 10
`GG` | Goto last line
`%`  | Goto matching parenthesis
---- | ----
`w` or `W` | Move forward a word (`W` moves by big-word, i.e. ignores non-whitespace delimiters)
`b` or `B` | Move backward a (big-)word
`e` or `E` | Move to end of (big-)word
`)` | Move forward a sentence
`}` | Move forward a paragraph
---- | ----
`H` | move to the top of the screen
`M` | move to the middle of the screen
`L` | move to the bottom of the screen
`^U` | move up half a screen
`^D` | move down half a screen
`^F` | page down
`^B` | page up

### Editing

cmd | description
--- | -----------
`:10,20s/old/new/g` | Replace "old" to "new" between lines 10 and 20
`:%s/old/new/g` | Replace in whole file
`:%s/old/new/gc` | Also prompt before each replace

### Files

- [ ] Switch between open (but currently not shown) buffers

cmd | description
--- | -----------
`:view file.txt` | Open file readonly
`:e file.txt` | Open file read/write
`:tabnew file.txt` | Opens file in new tab
`gt` | Goto next tab
`gT` | Goto previous tab

### Windows

cmd | description
--- | -----------
`:split file.txt` | Open file in horizontal split screen
`:vsplit file.txt` | Open file in vertical split screen
`C-w C-w` | Move between windows

### Undo

cmd | description
--- | -----------
`u` | Undo last
`U` | Undo everything you did on this line
`Ctrl-R` | Redo

### Formatting

- [ ] Markdown table formatting

cmd | description
--- | -----------
`gq ap` | Format around paragraph

## Command mode

cmd | description
--- | -----------
`:!ls` | Shell commands
`:r file.txt` | Insert `file.txt` contents here
`:r !ls` | Insert shell output here

