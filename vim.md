# Shortcuts vim

This shortcuts assumes you are using the same [~/.vimrc](https://github.com/marciofrayze/dot-files/tree/master/vim) as mine.

## File
* **Open file**: ```:e filename```

## Run shell
* **Run a shell command:** ```:!command```
* **Run a shell command and paste stdout into document:** ```:r!command```

## Tabs and Windows
* **Switch tabs**: ```gt```
* **Move from one window to another**: ```<C-w>h|l```

## Nerdtree
*  **Open|Close**: ```<C-n>```

## Visual-Block mode
* **Enter Visual-Block mode**: ```<C-v>```

## Insert Normal Mode
* **Fire off a single comnmand (from insert mode) and go back to insert**: ```<C-o>``` (ex: ```<C-o>dd```)

## Bookmark
* **Show all bookmarks (toggle)**: ```ma```
* **Add/remove bookmark at current line**: ```mm```
* **Add/edit/remove annotation at current line**: ```mi```
* **Jump to next bookmark in buffer**: ```mn```
* **Jump to previous bookmark in buffer**: ```mp```

## Delete
* **Delete**: ```d{motion}```
* **Delete single char:** ```dl```
* **Delete complete word:** ```daw```
* **Delete paragraph:** ```dap```
* **Delete line**: ```dd```

## Delete (insert mode)
* **Delete back one char**: ```<C-h>```
* **Delete back one word**: ```<C-w>```
* **Delete back to start of line**: ```<C-u>```

## Trigger / Effect
* **c** ```Change```
* **d** ```Delete```
* **y** ```Yank into register```
* **g~** ```Swap case```
* **gu** ```Make lowercase```
* **gU** ```Make uppercase```
* **>** ```Shift right```
* **<** ```Shift left```
* **=** ```Autoindent```
* **!** ```Filter {motion}^lines through an external program```
