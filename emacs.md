# Shortcuts emacs

## Text editor

### Ruller (fill-column-indicator plugin)

* **Show**: fci-mode
* **Show line number**: global-display-line-numbers-mode 

## Switch

* **Previous|Next buffer**: C-x LEFT|RIGHT (in term mode, use C-c instead)
* **Another window**: C-x o
* **Kill current window**: C-x 0

## ansi-term
* **Activate term-line-mode**: C-x C-j
* **Switch back to character mode**: C-c C-k
 
## Font

* **Increase|Decrease size**: C-x C-+|- 

## Resize window
* **Increase|Decrease size**: s- UP|DOWN|LEFT|RIGHT
```
(global-set-key (kbd "<s-up>") 'shrink-window)
(global-set-key (kbd "<s-down>") 'enlarge-window)
(global-set-key (kbd "<s-left>") 'shrink-window-horizontally)
(global-set-key (kbd "<s-right>") 'enlarge-window-horizontally)
```

### Ruller (fill-column-indicator plugin)

* **Show**: fci-mode
* **Show line number**: global-display-line-numbers-mode 

## Bookmark

* **Add to bookmark**: ctrl + x r m  
* **List bookmarks**: ctrl + x r l2

## Dired

**Enter edit mode**: C-x C-q

## Clojure / Cider

**Start/connect to server**: M-x cider-jack-in
**Compile**: C-c C-k ou :cider-load-buffer  
