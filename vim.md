# (neo)vim

## TODO

- [ ] Project wide search-in-files, like Ctrl-Shift-F in PyCharm (ripgrep style?)
- [ ] Show unsaved changes. `:DiffOrig` must be installed somehow it seems

## Sources

- `vimtutor`
- [Learn vim for the last time](https://danielmiessler.com/p/vim)
- TODO: Drew Neil, Practical Vim: Edit Text at the Speed of Thought


## Modes

- I mapped `jk` to switch from insert to normal mode
- `v` goes to *normal* visual mode (selecting text)
  - `V` selects by line
  - `C-v` selects by *rectangle* (like emacs did!)
- The `:` line is called ex mode
- There are some other modes as well, look them up later



## Config

- Start naked vim to have factory-reset behavior: `vim -u NONE -N file.txt`
- Custom keybinds: Type `:help map-which-keys` for suggestions on what keys to
  use for custom keybinds.
- Read `:help lua-guide` to get started with lua

Translating VimScript options to lua:

vimscript | lua
--------- | ---
`language en_US.utf8` | `vim.cmd('language en_US.utf8')`
`set myoption` | `vim.opt.myoption = true`
`set myoption=2` | `vim.opt.myoption = 2`
`set myoption=sth` | `vim.opt.myoption = 'sth'`


## Neat little tricks

cmd | description
--- | -----------
`:terminal` | Open a terminal in this window (if you forgot to run `tmux` :) )
`C-o` | In insert mode, this lets you execute *one* normal mode command
--- | ----
`g<Backspace>` | In normal mode, shows some navigation commands (kickstart-nvim only)


## Help

cmd | description
--- | -----------
`F1` or `:help` | Opens a new help window (or on HTTP: https://neo.vimhelp.org/ or https://neo.vimhelp.org/ )
`:help help` | Help on the help pages!
`:help index` | Shows a list of default keybindings
`C-w C-w` | Switch between windows
`:e C-d` | Shows completions of commands that start with `e`
`:help :cmd` | Help for ex-mode command `cmd`
--- | ----
`:help w` | normal mode mapping for w (case-sensitive)
`:help g8` | normal mode mapping for g8
`:help v_o` | visual mode mapping for o; other modes are c for command-line and i for insert
`:help CTRL-W` | normal mode mapping for <C-w>
`:help i_CTRL-W` | insert mode mapping for <C-w>
`:help CTRL-W_CTRL-I` | normal mode mapping for <C-w><C-i>
`:help i_CTRL-G_<Down>` | insert mode mapping for <C-g><Down>
`:help i_<F1>` | help on the F1 key

The help pages apply to the *default* keybinds, not those you might have remapped.

You have to type the help topics exactly and case-sensitive.
Type `:help key-notation` to read how to specify them.

There is a search thingy available:
Type `:help CTRL-G` then press Ctrl-D to see possible completions

### Neovim help

Use `leader s h` (leader being Space) for a pretty help search!

Use `:Telescope help_tags` to search in some different way

## Plugins

### Telescope

- A fuzzy finder like deft in emacs, but for everything!
- `leader s f` finds files. `<C-t>` opens file in new tab, `<C-x>` hsplit, `<C-v>` vsplit
- Use `C-c` instead of pressing `Esc` 10 times to exit it.
- `:Telescope builtin` shows you what functions are built in.

### Mason

Syntax highlighting and more (?) via the LSP (?). You can install new languages, try adding R

### Treesitter

This is a "parsing library".
It's most prominent feature is a syntax highlighter.
But it does much more. E.g. repeatedly pressing C-Space selects ever bigger syntactical regions. You can jump to the next function definition, etc.
See the `-- [[ Configure Treesitter ]]` part in kickstart-nvim.lua for some more features it provides.

## Vim as a language

From [Learn vim for the last time](https://danielmiessler.com/p/vim)

### Verbs

char | verb
---- | ----
`d` | delete
`c` | change
`y` | yank (copy)
`v` | visually select (V for entire lines)

### Modifiers

char | modification
---- | ------------
`i` | inside
`a` | around (gets (only) the trailing space around it too)
`NUM` | number (e.g.: 1, 2, 10)
`t` | "to": to char (excluding) (`;` for next, `,` for previous)
`f` | "find": to char (including) (these only work on the current line)
`/` | find a string (literal or regex)

### Nouns

char | noun
---- | ----
`w` | word
`s` or `)`| sentence
`p` or `}` | paragraph
`t` | tag (think HTML/XML)
`b` | block (think programming)
`'` | single quotes
`"` | double quotes

- Back ticks, parentheses etc. (like `(` and `[`) work too

### Sentences

Some examples:

sentence | description
-------- | -----------
`d2w` | delete 2 words
`cis` | change inside sentence
`yip` | yank inside paragraph
`gqap` | format around paragraph
`ct<` | change until the next open bracket
`{d}` | goes to the beginning of a paragraph, and then cuts/deletes to the end of the paragraph!
`d/foo` | delete from current line to next line containing "foo"
`y?bar` | copy from current line to most recent (previous) line containing "bar"



## Normal mode

### Movement

cmd | description
--- | -----------
`gg` | Goto line 0
`10G` or `:10` | Goto line 10
`G` | Goto last line
`%`  | Goto matching parenthesis
---- | ----
`w` or `W` | Move forward a word (`W` moves by big-word, i.e. ignores non-whitespace delimiters)
`b` or `B` | Move backward a (big-)word
`e` or `E` | Move to end of (big-)word
`)` | Move forward a sentence
`}` | Move forward a paragraph
---- | ----
`H` | move to the top of the screen ("High")
`M` | move to the middle of the screen ("Middle")
`L` | move to the bottom of the screen ("Low")
`^U` | move up half a screen
`^D` | move down half a screen
`^F` | page down
`^B` | page up
`^E` | **scroll** up one line (i.e. without moving the cursor)
`^Y` | scroll down one line
---- | ----
`^i` | jump to previous navigation location (huh?)
`^o` | jump back to where you were (huh?)

#### Marks

The navigation locations might have to do with **marks**. Type `ma` to mark the current
cursor position as "a". Type `'a` to go to the line marked a (use a backtick to go to the
exact location).

You can copy a selection without going to visual mode this way: Mark the beginning (or end)
as "a", go to the end (or beginning), and cut with `d [backtick] a` (or yank with `y`).

### Editing

cmd | description
--- | -----------
`i` | insert before the cursor
`a` | append after the cursor
`I` | insert at the beginning of the line
`A` | append at the end of the line
`o` | open a new line below the current one
`O` | open a new line above the current one
`r` | replace the one character under your cursor
`R` | replace the character under your cursor, but just keep typing afterwards
`cm` | change whatever you define as a movement, e.g. a word, or a sentence, or a paragraph.
`C` | change the current line from cursor to end
`ct?` | change up to the question mark
`s` | substitute from where you are to the next command (noun)
`S` | substitute the entire current line
---- | ----
`:10,20s/old/new/g` | Replace "old" to "new" between lines 10 and 20
`:%s/old/new/g` | Replace in whole file
`:%s/old/new/gc` | Also prompt before each replace
---- | ----
`x` | delete char
`X` | delete char backwards
`D` | delete to end of line
`J` | join line with next line

### Copy/Paste

- Cutting == deleting. If you `dd` a line, you could immediately paste it into your browser
- Remember that visual mode is nice to select text to copy!
- Ctrl-Shift-V works too, but Ctrl-Shift-C doesn't

cmd | description
--- | -----------
`y` | copy ("yank") selection (this can now be pasted outside)
`yy` | copy current line
`p` | paste after cursor (also works with text from external clipboard)
`P` | paste before cursor
`"add` | delete this line (`dd`) *into the "a" register*

You have 26 named registers, a through z, that you can store stuff in instead of the default,
anonymous register.

### The dot command

The dot repeats the last command, e.g. deleting a line, or switching to insert mode,
adding some text, and going back to normal mode.

Often, you want to combine a movement with the dot. So search for a word with `/myword`,
append some text to it, then repeat `n` (go to next occurence) and `.` (append the same text).

### Buffers / Files

cmd | description
--- | -----------
`Leader sf` | search files with Telescope
`:Ntree` | Browse directory to open a new file
`:view file.txt` | Open file readonly
`:e file.txt` | Open file read/write
`Leader Space` | Switch between opened but hidden buffers
`:bprevious` | (and `:bnext`) to change opened files

### Windows

- You can resize windows by mouse-dragging

cmd | description
--- | -----------
`:split file.txt` | Open file in horizontal split screen
`:vsplit file.txt` | Open file in vertical split screen
`C-w C-w` | Move between windows
`C-w C-H` | Swap window with left. See `which-key` suggestions after `C-w` for more options
`<C-t>` | in Telescope find-files, opens file in new tab
`<C-x>` | in Telescope find-files, opens file in hsplit
`<C-v>` | in Telescope find-files, opens file in vsplit
`:q` | Close a window

### Tabs

- Tabs *contain* window splits, not the other way round!

cmd | description
--- | -----------
`:tabnew file.txt` | Opens file in new tab
`gt` | Goto next tab
`gT` | Goto previous tab

### Undo

cmd | description
--- | -----------
`u` | Undo last
`U` | Undo everything you did on this line
`Ctrl-R` | Redo (or `:redo`)

### Formatting

- [ ] Markdown table formatting

cmd | description
--- | -----------
`gq ap` | Format around paragraph



## Command ("Ex") mode

cmd | description
--- | -----------
`:!ls` | Shell commands
`:r file.txt` | Insert `file.txt` contents here
`:r !ls` | Insert shell output here



## Visual mode

Some examples (from normal mode):

cmd | description
--- | -----------
`vi(` | select all inside these parentheses
`v2i[` | select all inside the 2 parent levels of brackets

`Try moving your [cursor to [THIS] word and] then type "v2i["`



## Macros

Yay, vim has macros just like emacs does!

cmd | description
--- | -----------
`qa` | start recording a macro named "a" (you can use a-z)
`q` | stop recording
`@a` | playback the macro named "a" once
`.` | playback the macro a second, ..., time



## Code

cmd | description
--- | -----------
`gd` | goto definition (of a function, e.g.)
`gr` | find references where this field, function, etc. is used
`:Telescope keymaps` |  Browse all currently mapped keys
`:Mason` | Install new languages (press `i` to install)
