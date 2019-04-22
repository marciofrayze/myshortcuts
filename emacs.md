# Shortcuts emacs

## Text editor

### Ruller (fill-column-indicator plugin)

* **Show**: fci-mode
* **Show line number**: global-display-line-numbers-mode 

## Switch

* **Previous|Next buffer**: C-x LEFT|RIGHT
* **Another window**: C-x o

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

 * **Open file**: find-file <filename>

## Dired

**Enter edit mode**: C-x C-q
