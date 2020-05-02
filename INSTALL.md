# Installation

This setup is pretty rough and only supports ElementaryOS and i3 (with
nitrogen) setups. With some help, it could definitely support other
environments.

## Dependencies

1. Install [pywal](https://github.com/dylanaraps/pywal)
2. Install the [haishoku](https://github.com/LanceGin/haishoku) backend

## Generate your theme

Run the following script:

```bash
./scripts/wal-colors
```

## Emacs configuration

Copy down the [wal-theme.el](./emacs/wal-theme.el) theme. To your Emacs configuration, then add the following config:

```
;; Optional, add directory for your themes
(add-to-list 'custom-theme-load-path "~/.emacs.d/themes/")

(require 'ewal)
(load-theme 'wal t)
```
