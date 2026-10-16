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

## Notes

The local overrides on top of the defaults are:

- `set -g mouse on`
- `setw -g mode-keys vi`
- copy-mode bindings that pipe the selection to the system clipboard via `xclip`

The base `.tmux.conf` is upstream Oh my tmux!, dual licensed under the WTFPL v2
and the MIT license, copyright Gregory Pakosz.
