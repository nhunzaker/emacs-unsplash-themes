# Installation

Note - this project only works on OSX. For Linux, see the `linux` branch.

### System setup

Color theme generation is produced by [pywal](https://github.com/dylanaraps/pywal) using the [haishoku](https://github.com/LanceGin/haishoku) backend

```bash
pip3 install pywal haishoku
```

You'll also need [wallpaper](https://formulae.brew.sh/formula/wallpaper) to access current wallpaper properties

```bash
brew install wallpaper
```

Now link the wal-colors script to your local bin directory:

```bash
mkdir -p ~/.local/bin
ln -s ./wal-colors ~/.local/bin/wal-colors
```

### Emacs setup

Copy down the [wal-theme.el](./emacs/wal-theme.el) theme. To your Emacs configuration, then add the following config:

```emacs-lisp
(use-package ewal) ; or get ewal some other way

(add-to-list 'custom-theme-load-path "~/.emacs.d/themes/")

(defun user/apply-theme ()
  "Set the Emacs theme based on the current wallpaper."
  (shell-command "~/.local/bin/wal-colors")
  (load-theme 'wal t))

(add-function :after after-focus-change-function 'user/apply-theme)

(user/apply-theme)
```

### Sourcing Wallpapers

You can really use any source for wallpapers, but consider installing the [Unsplash Wallpapers app from the app store](https://apps.apple.com/us/app/unsplash-wallpapers/id1284863847?mt=12).
