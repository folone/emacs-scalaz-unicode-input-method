# Emacs Scalaz Unicode input method
## adapted version of [Emacs Haskell unicode input method](https://github.com/roelvandijk/emacs-haskell-unicode-input-method)

This package provides **scalaz-unicode-input-method**, an input
method which allows you to easily type a number of Unicode symbols
that are useful when writing Scala code using [Scalaz](https://github.com/scalaz/scalaz) library.

To automically load in scala-mode put the following code in your
.emacs file:

    (require 'scalaz-unicode-input-method)
    (add-hook 'scala-mode-hook 
      (lambda () (set-input-method "scalaz-unicode")))

Make sure the directory containing the .el file is in your load-path,
for example:

    (add-to-list 'load-path "~/.elisp/emacs-scalaz-unicode-input-method")

To manually enable use **M-x set-input-method** or **C-x RET C-\\**
with **scalaz-unicode**. Note that the elisp file must be evaluated
for this to work.

Now you can simply type `->` and it is immediately replaced with
`→`. Use **C-\\** to toggle the input method. To see a table of all
key sequences use **M-x describe-input-method scalaz-unicode**. A
sequence like `contains` is ambiguous and can mean either `∋` or `∈`. Typing
it presents you with a choice. Type 1 or 2 to select an option or keep
typing to use the default option.

If you don't like the highlighting of partially matching tokens you
can turn it off:

    (setq input-method-highlight-flag nil)

If using with evil-mode, consider adding the following to your config:

    ;; Only enable unicode mode for insert and emacs states in evil-mode
    (add-hook 'evil-insert-state-entry-hook
                (lambda () (set-input-method "scalaz-unicode")))
    (add-hook 'evil-insert-state-exit-hook
                (lambda () (set-input-method nil)))
    (add-hook 'evil-emacs-state-entry-hook
                (lambda () (set-input-method "scalaz-unicode")))
    (add-hook 'evil-emacs-state-exit-hook
                (lambda () (set-input-method nil)))
