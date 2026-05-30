# tmux

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



