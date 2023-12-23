# (neo)vim

### Sources

- `vimtutor`
- [Learn vim for the last time](https://danielmiessler.com/p/vim)
- TODO: Drew Neil, Practical Vim

## Modes

- I mapped `jk` to switch from insert to normal mode

## Config

Translating VimScript options to lua:

vimscript | lua
--------- | ---
`language en_US.utf8` | `vim.cmd('language en_US.utf8')`
`set myoption` | `vim.opt.myoption = true`
`set myoption=2` | `vim.opt.myoption = 2`
`set myoption=sth` | `vim.opt.myoption = 'sth'`

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

### Editing

cmd | description
--- | -----------
`:10,20s/old/new/g` | Replace "old" to "new" between lines 10 and 20
`:%s/old/new/g` | Replace in whole file
`:%s/old/new/gc` | Also prompt before each replace


### Files

- [ ] Switch between open buffers

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

