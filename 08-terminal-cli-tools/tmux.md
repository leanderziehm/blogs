# Tmux

```
tmux new -s mysession
```

```
tmux a -t mysession
```

<table data-search="false"><thead><tr><th>Description</th><th>Keyboard</th></tr></thead><tbody><tr><td>side bar pane/panel</td><td>Ctrl+b + %</td></tr><tr><td>bottom pane/terminal</td><td>Ctrl + b + "</td></tr><tr><td>Next Pane</td><td>Ctrl + b + o</td></tr><tr><td>Switch Layout</td><td>Ctrl + b + Space</td></tr><tr><td>Next window</td><td>Ctrl + b + n</td></tr><tr><td>Previous window</td><td>Ctrl + b + p</td></tr><tr><td>Previous Pane</td><td>Ctrl + b + ;</td></tr><tr><td>select pane</td><td>Ctrl + b + 1,2,3 ...</td></tr><tr><td>close pane/panel</td><td>Ctrl + b + x</td></tr><tr><td>new window</td><td>Ctrl + b + c </td></tr><tr><td>view sessions</td><td>Ctrl + b + s</td></tr><tr><td>last window</td><td>Ctrl + b + l</td></tr><tr><td>copy mode</td><td>Ctrl + b + [</td></tr><tr><td>keys</td><td>Ctrl + b + ?</td></tr><tr><td>close windows and panes </td><td>exit</td></tr><tr><td>show time</td><td>Ctrl + b + t</td></tr><tr><td>choose window from list</td><td>Ctrl + b + w</td></tr><tr><td>zoom pane full screen</td><td>Ctrl + b + z</td></tr><tr><td>Last Session</td><td>Ctrl + b + L</td></tr><tr><td>show messages</td><td>Ctrl + b + ~ </td></tr><tr><td>pane into new window</td><td>Ctrl + b + !</td></tr><tr><td>command</td><td>Ctrl + b + :</td></tr><tr><td>Evenly size panes</td><td>Ctrl + b + E</td></tr></tbody></table>

```
:set mouse on
```











***







attach instead of always creating a new session:

tmux a



tmux new -s mysession



| Command                        | Effect              |
| ------------------------------ | ------------------- |
| Ctrl + b + c                   | New Window          |
| Ctrl + b + n                   | Next Window         |
| Ctrl + b + s                   | Selectable Sessions |
| Ctrl + b + x                   | close pane          |
| Ctrl + b + $                   | Rename Session      |
| Ctrl + b + \[     Space, Enter | copy mode           |
|                                |                     |
| Ctrl + b + w                   | Selectable Windows  |
| Ctrl + b + 0-9                 | Select Window       |
|                                |                     |
| Ctrl + b + %                   | vertial pane        |
| Ctrl + b + "                   | horizontal pane     |
| Ctrl + b + arrow               | select pane         |
| Ctrl + b + z                   | focus pane          |
| Ctrl + b + Space               | Toggle layout pane  |
|                                |                     |
| :new -s sessionName            | New Session         |
| :kill-session                  | Kill Session        |
| Ctrl + b + )                   | Next Session        |
| Ctrl + b + d                   | Detatch Session     |
|                                |                     |





## Special Sync Mode

:setw synchronize-panes



## Config

:setw -g mode-keys vi

:set mouse on



set -g set-clipboard on



set -g default-terminal "tmux-256color"\
set -as terminal-overrides ",\*:Tc"





## 1. Increase scrollback history

Default history is small.

```
set -g history-limit 100000
```

This allows deep scrolling when inspecting logs.

***

## 2. Enable mouse support

Improves pane selection, resizing, and scrolling.

```
set -g mouse on
```

***

## 3. Use vi-style copy mode

Your bindings already show this, but ensure it is explicitly set.

```
set -g mode-keys vi
```

This makes navigation consistent with Vim.

***

## 4. Improve pane borders

Helps visually identify active panes.

```
set -g pane-border-style fg=colour238
set -g pane-active-border-style fg=colour39
```

Result:

* inactive panes = dim
* active pane = bright

***

## 5. Cleaner status bar

The default bar wastes space.

```
set -g status-position bottom
set -g status-interval 5
set -g status-justify left
set -g status-left-length 40
set -g status-right-length 100
```

***

## 6. Informative status bar content

```
set -g status-left "#[fg=colour39]#S #[fg=colour244]| #[fg=colour250]#W"
set -g status-right "#[fg=colour244]%Y-%m-%d #[fg=colour250]%H:%M"
```

Displays:

```
session | window                     date time
```

***

## 7. Highlight active window

```
set -g window-status-current-style fg=colour231,bg=colour39,bold
set -g window-status-style fg=colour244,bg=default
```

This makes the active window stand out clearly.

***

## 8. Better message visibility

```
set -g message-style bg=colour39,fg=colour231
set -g message-command-style bg=colour39,fg=colour231
```

***

## 9. Improve pane numbering visibility

```
set -g display-panes-time 1500
set -g display-panes-active-colour colour39
set -g display-panes-colour colour244
```

***

## 10. True color support (important for modern terminals)

```
set -g default-terminal "tmux-256color"
set -as terminal-overrides ",*:Tc"
```

***

## 11. Clipboard integration (Wayland/Linux)

Since your config already uses `wl-copy`, ensure this:

```
set -g set-clipboard on
```





***

## Example minimal UI-focused `.tmux.conf`

```
set -g history-limit 100000
set -g mouse on
set -g mode-keys vi

set -g pane-border-style fg=colour238
set -g pane-active-border-style fg=colour39

set -g status-position bottom
set -g status-interval 5
set -g status-left "#[fg=colour39]#S #[fg=colour244]| #[fg=colour250]#W"
set -g status-right "#[fg=colour244]%Y-%m-%d #[fg=colour250]%H:%M"

set -g window-status-current-style fg=colour231,bg=colour39,bold
set -g window-status-style fg=colour244

set -g message-style bg=colour39,fg=colour231

set -g default-terminal "tmux-256color"
set -as terminal-overrides ",*:Tc"

set -g set-clipboard on
```

#### Better pane titles

```
set -g pane-border-format "#{pane_index} #{pane_current_command}"
```

#### Automatic window renaming

```
set -g automatic-rename on
```

#### More visible activity

```
setw -g monitor-activity on
set -g visual-activity on
```



