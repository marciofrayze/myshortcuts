# Shortcuts vim

This shortcuts assumes you are using the same [~/.vimrc](https://github.com/marciofrayze/dot-files/tree/master/vim) as mine.

## File
* **Open file**: ```:e filename```
* **Reload .vimrc**: ```:source %```

## Run shell
* **Run a shell command:** ```:!command```
* **Run a shell command and paste stdout into document:** ```:r!command```

## Tabs and Windows
* **Switch tabs**: ```gt```
* **Move from one window to another**: ```<C-w>h|l```

## Normal mode
*  **Center current line**: ```zz```

## Registers
* **List registers**: ```:reg```
* **Paste content from register "4**: ```"4p```
* **Add selected texto to register r**"```"ry``` then paste it with: ```"rp```

## Visual-Block mode
* **Enter Visual-Block mode**: ```<C-v>```

## Insert Normal Mode
* **Fire off a single comnmand (from insert mode) and go back to insert**: ```<C-o>``` (eg: ```<C-o>dd```)
* **Paste**: ```<C-r>0``` (or 1, 2, 3...)
* **Expression register (to evaluate a expression)**: ```<C-r>=``` (eg: ```<C-r>=1+1``` will paste 2)

## Visual mode
* **Enter Visual mode**: ```v```
* **Select paragraph**: ```vip```
* **Select line**: ```V```
* **Select block**: ```<C-v>```
* **Reselect**: ```gv```
* **Go to the another end of selected text**: ```o```
* **Visually select inside a tag**: ```vit```
* **Change a word in 3 lines**: ```C<v>jje c <ESC>```
* **Append a ; in the end of 3 lines**: ```C<v>jj$ A; <ESC>```

## Ex commands
* **Copy line 6 and paste to just bellow current line**: ```:6t.``` or ```:6copy.```or ```:6co.```
* **Copy line 6,7 and 8 and paste to just bellow line 8 line**: ```:6,8t8```
* **Repeat last Ex command**: ```@:```
* **Repeat a normal command on every line (in this example, appending a ; in the end of the line)**: ```:normal A;```

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

## Nerdtree
*  **Open|Close**: ```<C-n>```

## Autocomplete
* **Select next or previous option**: ```<C-n>|<C-p>``` 

## Spell checking
* **Add word to dictionary**: ```zg```
* **Remove word to dictionary**: ```zug```
* **Enable spell checking (portuguese br)**: ```:setlocal spell spelllang=pt_br```
* **Select next or previous to autocomplete**: ```<C-n>|<C-p>```

## Symbols for ranges
* **First line of file**: ```1```
* **Last line of file**: ```$```
* **Virtual line above the first one**: ```0```
* **Line where the cursor is placed**: ```.```
* **Line containing mark m**: ```'m```
* **Start of visual selection**: ```'<```
* **End of visual selection**: ```'>```
* **Entire file (shortcut for 1,$)**: ```%```

## Links
http://www.atmos.albany.edu/daes/atmclasses/atm350/vi_cheat_sheet.pdf
