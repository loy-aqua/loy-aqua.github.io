---
title: "Literate Emacs Config"
categories: emacs
---

Literate programming is a **programming paradigm** introduced by  Donald Knuth, definition from Wikipedia :
> Literate programming is writing out the program logic in a human language with included code snippets and macros.

Emacs’  [org-mode](https://orgmode.org/)  makes literate programming extremely easy. A classic way to do this is using org-mode to manage your emacs initialization!

### How to do it 
- - - -
Use org-babel to bootstrap.

**init.el**
```lisp
;; Load up Org Mode and Babel and load the configuration file
(setq dotfiles-dir (file-name-directory (or load-file-name (buffer-file-name))))
(add-to-list 'load-path
	     (expand-file-name "lisp" (expand-file-name "org" (expand-file-name "src" dotfiles-dir))))
(require 'org-install)
(org-babel-load-file (expand-file-name "config.org" dotfiles-dir))
```
**config.org**
```lisp
* Melpa default configuration
  #+BEGIN_SRC emacs-lisp
    (require 'package)
    (setq package-archives '(("gnu" . "http://elpa.gnu.org/packages/")
			     ("melpa" . "http://melpa.org/packages/")))
    (package-initialize)
  #+END_SRC
* Use-package
  #+BEGIN_SRC emacs-lisp
    (eval-when-compile
      (require 'use-package))
  #+END_SRC
```
Write your awesome code like this, beautifully
>  #+BEGIN_SRC emacs-lisp
>
>  "Code snippets here."
>
>  #+END_SRC

Enjoy it!

