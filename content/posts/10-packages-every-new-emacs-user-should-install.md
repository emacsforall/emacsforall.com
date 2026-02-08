+++
title = "The 10 Packages Every New Emacs User Should Install"
author = ["Jonathan Chu"]
date = 2026-02-08
lastmod = 2026-02-08
tags = ["emacs", "packages", "beginners"]
categories = ["tutorials"]
series = ["Getting Started with Emacs"]
draft = false
+++

The Emacs package ecosystem is vast — MELPA alone has over 5,000 packages. That's exciting but also overwhelming. Here are the 10 packages that give you the most value for the least configuration.

{{< youtube dQw4w9WxXcQ >}}


## 1. Vertico {#vertico}

Modern, minimal vertical completion UI. Replaces the default minibuffer completion with something you'd actually want to use.

```emacs-lisp
(use-package vertico
  :ensure t
  :init (vertico-mode))
```


## 2. Consult {#consult}

Search and navigation commands that integrate with Vertico. `consult-ripgrep`, `consult-line`, and `consult-buffer` will change how you navigate code.

```emacs-lisp
(use-package consult
  :ensure t
  :bind (("C-s" . consult-line)
         ("C-x b" . consult-buffer)
         ("M-g g" . consult-goto-line)))
```


## 3. Marginalia {#marginalia}

Adds helpful annotations next to completion candidates — file sizes, docstrings, keybindings.

```emacs-lisp
(use-package marginalia
  :ensure t
  :init (marginalia-mode))
```


## 4. Orderless {#orderless}

Flexible completion matching. Type any part of what you're looking for in any order.

```emacs-lisp
(use-package orderless
  :ensure t
  :custom (completion-styles '(orderless basic)))
```


## 5. Magit {#magit}

The best Git interface ever made. Not an exaggeration. Once you use Magit, you'll never want to go back to the command line for Git.

```emacs-lisp
(use-package magit
  :ensure t
  :bind ("C-x g" . magit-status))
```


## 6. Org-mode {#org-mode}

Technically built-in, but worth mentioning because it's often why people come to Emacs in the first place. Notes, tasks, literate programming, and more.


## 7. Which-key {#which-key}

Shows available keybindings in a popup. Essential for discoverability when you're learning.

```emacs-lisp
(use-package which-key
  :ensure t
  :init (which-key-mode))
```


## 8. Corfu {#corfu}

In-buffer completion popup. Fast, minimal, works with Eglot's LSP completions out of the box.

```emacs-lisp
(use-package corfu
  :ensure t
  :init (global-corfu-mode))
```


## 9. Eglot {#eglot}

Built-in LSP client (since Emacs 29). Minimal configuration, just install a language server and go.

```emacs-lisp
;; Eglot is built-in, just hook it up
(add-hook 'python-mode-hook #'eglot-ensure)
(add-hook 'js-mode-hook #'eglot-ensure)
(add-hook 'rust-mode-hook #'eglot-ensure)
```


## 10. Doom Themes {#doom-themes}

Even if you don't use Doom Emacs, the theme collection is excellent. `doom-one` and `doom-gruvbox` are crowd favorites.

```emacs-lisp
(use-package doom-themes
  :ensure t
  :config
  (load-theme 'doom-one t))
```


## Putting It All Together {#putting-it-all-together}

All of these packages work together harmoniously. Vertico + Consult + Marginalia + Orderless form a completion framework that rivals anything in VS Code, and Magit + Org-mode are the power tools that keep experienced users on Emacs for decades.
