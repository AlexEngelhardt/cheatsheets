# tmux

- I remapped the Prefix from default `C-b` to `C-s`


Hierarchy:
- Session
- Window
- Pane


cmd | description
--- | -----------
`C-s ?` | See all commands
`C-s I` | Install plugins after editing `.tmux.conf`
`C-s :` | enter a manual command, e.g. `kill-session`

## From the shell

cmd | description
--- | -----------
`tmux source ~/.tmux.conf` | Reload your configuration
`tmux ls` | List open sessions
`tmux a` | Attach to newest session (e.g. if you accidentally closed it)
`tmux a -t sessionNameorNumber` | Attach to target session

(Many commands look the same in the shell and as a `C-s :` command from within
tmux, e.g. `C-s :ls` lists open sessions)

## Sessions

cmd | description
--- | -----------
`C-s :new` | Create new session
`C-s s` | View open sessions prettily. Pressing `x` kills a session
`C-s )` | Switch to next session
`C-s (` | Switch to previous session
`C-s $` | Rename current session
`C-s d` | Detach current session

## Windows

cmd | description
--- | -----------
`C-s c` | Create new window
`C-s w` | View open windows prettily (`x` kills a window)
`C-s p` | Switch to previous window
`C-s n` | Switch to next window
`C-s 3` | Switch to window 3
`C-s ,` | Rename current window
`C-s &` | Kill current window

## Panes

cmd | description
--- | -----------
`C-s -` | Split pane vertically
`C-s <pipe>` | Split pane horizontally (the .md table fails when I print the pipe character)
`C-s [arrow]` | Change panes
`C-s [hjlk]` | Change panes
`C-s z` | Temporarily make pane fullscreen (or go back)
`C-s C-[arrow]` | Resize pane into direction (repeatable)
`C-s x` | Kill pane (`C-d` from shell does that too)
`C-s {` | Swap pane "up" re. its index (`C-s q`)
`C-s }` | Swap pane "down"
`C-s !` | Convert pane into new window
