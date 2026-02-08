+++
title = "Your First Hour in Emacs — Skip the Tutorial, Do This Instead"
author = ["Jonathan Chu"]
date = 2026-02-07
lastmod = 2026-02-07
tags = ["emacs", "beginners", "getting-started"]
categories = ["tutorials"]
series = ["Getting Started with Emacs"]
draft = false
+++

Most Emacs tutorials start the same way: "Run the built-in tutorial with `C-h t`." We're going to skip that entirely. Instead, let's get you productive in Emacs in under an hour with a modern setup.

{{< youtube dQw4w9WxXcQ >}}


## Install Emacs 29+ {#install-emacs-29-plus}

Make sure you're running Emacs 29 or later — it includes tree-sitter support, `eglot` for LSP, and a much better default experience.

On macOS:

```shell
brew install emacs-plus@30 --with-native-comp
```

On Fedora:

```shell
sudo dnf install emacs
```

On Ubuntu:

```shell
sudo snap install emacs --classic
```


## The First 5 Things to Configure {#the-first-5-things-to-configure}

Create `~/.emacs.d/init.el` (or `~/.config/emacs/init.el`) and add:

```emacs-lisp
;; Clean up the UI
(menu-bar-mode -1)
(tool-bar-mode -1)
(scroll-bar-mode -1)
(setq inhibit-startup-message t)

;; Line numbers in programming modes
(add-hook 'prog-mode-hook #'display-line-numbers-mode)

;; Remember recent files
(recentf-mode 1)

;; Save your place in files
(save-place-mode 1)

;; Don't litter the filesystem with backup files
(setq backup-directory-alist '(("." . "~/.emacs.d/backups")))
```


## Install Your First Packages {#install-your-first-packages}

Set up `use-package` (built-in since Emacs 29) and install the essentials:

```emacs-lisp
;; Set up package archives
(require 'package)
(add-to-list 'package-archives '("melpa" . "https://melpa.org/packages/") t)

;; Vertico — better minibuffer completion
(use-package vertico
  :ensure t
  :init (vertico-mode))

;; Marginalia — helpful annotations in the minibuffer
(use-package marginalia
  :ensure t
  :init (marginalia-mode))

;; Magit — the best Git interface
(use-package magit
  :ensure t
  :bind ("C-x g" . magit-status))
```


## What's Next? {#what-s-next}

You now have a clean, modern Emacs with completion, Git integration, and a solid foundation. In the next article, we'll cover the 10 packages every new Emacs user should install.
