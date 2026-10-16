# tmux-config

My tmux configuration.

It is built on top of [Oh my tmux!](https://github.com/gpakosz/.tmux), so the two
files here are exactly the ones tmux loads on this machine:

- `.tmux.conf` — the Oh my tmux! base configuration (`~/.tmux.conf`)
- `.tmux.conf.local` — my local overrides (`~/.tmux.conf.local`)

## Install

```sh
git clone --single-branch https://github.com/gpakosz/.tmux.git ~/.tmux
ln -s -f ~/.tmux/.tmux.conf ~/.tmux.conf
```

Then copy the two files from this repository into place:

```sh
cp .tmux.conf ~/.tmux/.tmux.conf
cp .tmux.conf.local ~/.tmux.conf.local
```

## Differences from Oh my tmux!

Only a handful of things differ from a fresh Oh my tmux! install. Everything
else — themes, key bindings, status line, TPM settings — is the untouched
upstream default. Nothing in the stock template was uncommented.

### `.tmux.conf` (base)

Two blank lines added at the very top. No functional change.

### `.tmux.conf.local`

Nine lines added at the very top of the upstream template:

```tmux
set -g mouse on
setw -g mode-keys vi

# Sistem clipboard'a kopyalama
bind-key -T copy-mode-vi MouseDragEnd1Pane send-keys -X copy-pipe-and-cancel "xclip -i -selection clipboard"
bind-key -T copy-mode-vi y send-keys -X copy-pipe-and-cancel "xclip -i -selection clipboard"
bind-key -T copy-mode-vi Enter send-keys -X copy-pipe-and-cancel "xclip -i -selection clipboard"
```

| Addition | Effect |
| --- | --- |
| `set -g mouse on` | mouse support on (default is off) |
| `setw -g mode-keys vi` | vi keys in copy mode (default is emacs) |
| `bind-key -T copy-mode-vi MouseDragEnd1Pane … xclip` | drag selection is sent to the system clipboard |
| `bind-key -T copy-mode-vi y … xclip` | `y` copies the selection to the system clipboard |
| `bind-key -T copy-mode-vi Enter … xclip` | `Enter` copies the selection to the system clipboard |

The three clipboard bindings require `xclip` on Linux.

## Licensing

The base `.tmux.conf` is upstream Oh my tmux!, dual licensed under the WTFPL v2
and the MIT license, copyright Gregory Pakosz.
