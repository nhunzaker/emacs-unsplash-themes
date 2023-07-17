# Installation

Note - this project only works on OSX. For Linux, see the `linux` branch.

You can perform all setup actions by running:

```bash
./scripts/install
```

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

Copy down the [wal-theme.el](./emacs/wal-theme.el) to your theme directory, then add the following config:

```emacs-lisp
(use-package ewal) ; or get ewal some other way

;; Or whatever your theme directory is
(add-to-list 'custom-theme-load-path "~/.emacs.d/themes/")

(defun user/apply-theme ()
  "Set the Emacs theme based on the current wallpaper."
  (shell-command "~/.local/bin/wal-colors")
  (load-theme 'wal t))

(user/apply-theme)

;; Optional, run this hook when refocusing emacs
(add-function :after after-focus-change-function 'user/apply-theme)
```

### Sourcing Wallpapers

You can really use any source for wallpapers, but consider installing [Unsplash Wallpapers app from the app store](https://apps.apple.com/us/app/unsplash-wallpapers/id1284863847?mt=12).
