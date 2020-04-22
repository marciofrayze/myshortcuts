# Shortcuts vim

Some shortcuts assumes you are using the same [~/.vimrc](https://github.com/marciofrayze/dot-files/tree/master/vim) as mine.

## Normal mode
* **Center current line**: ```zz```
* **Forward to start of next word**: ```w```
* **Backward to end of current/previous word**: ```b```
* **Forward to end of current/next word**: ```e```
* **Backward to end of previous word**: ```ge```
* **Forward to start of next WORD**: ```W```
* **Backward to end of current/previous WORD**: ```B```
* **Forward to end of current/next WORD**: ```E```
* **Backward to end of previous WORD**: ```gE```

## Jumps
* **Jump back to previous place**: ```ctr-o```
* **Jump forward to next place**: ```ctr-i```
* **List jumps**: ```:jumps```
* **Jump to line**: ```[count]G```
* **Jump to top, middle, bottom of screen**: ```H / M / L```
* **Jump to mark**: ``` `{mark} or '{mark}```
* **Jump to definition of keyword under the cursor**: ```ctr-]```
* **Jump to filename under the cursor**: ```gf```
* **Set global (and persisted) mark**: ```m{some-capital-letter}```

## Finding
* **Find the first occurrence of {char} in current line and move to it**: ```f{char}```
* **Repeat find the next ocurrence and move to it**: ```;```
* **Repeat find the next ocurrence in backwards and move to it**: ```,```
* **Find the next ocurrence in backwards and move to it**: ```F{char}```
* **Grep files (and go to first occurrence)**: ```:vimgrep {pattern} {files-pattern}

## Files and Directories
* **Open file**: ```:e filename```
* **Open file using filepath from active buffer**: ```:e %:h<TAB>```
* **Open netrw (native file explorer)**: ```:E```
* **Reload current file**: ```:source %```
* **Open multiple files splitting windows**: ```vim file1 file2 -O```
* **Diffing the files from multiple windows**: ```:windo difft```

## Netrw (:E)
* **Create directory**: ```d```
* **Delete file/directory**: ```D```
* **Rename**: ```R```  
More shortcuts [here](https://gist.github.com/danidiaz/37a69305e2ed3319bfff9631175c5d0f).

## Run shell
* **Run a shell command:** ```:!command```
* **Run a shell command and paste stdout into document:** ```:r!command```

## Tabs and Windows
* **Switch tabs**: ```gt```
* **Move from one window to another**: ```<C-w>h|l```

## Registers
* **List registers**: ```:reg```
* **Paste content from register "4**: ```"4p```
* **Add selected texto to register r**": ```"ry``` then paste it with: ```"rp```
* **Paste content from yank register**": ```"0p```

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

## Delete
* **Delete**: ```d{motion}```
* **Delete single char:** ```dl```
* **Delete complete word:** ```daw```
* **Delete paragraph:** ```dap```
* **Delete line**: ```dd```
* **Delete from current cursor until a search pattern**: ```d/{pattern}```

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

## Autocomplete
* **Select next or previous option**: ```<C-n>|<C-p>``` 

## Spell checking
* **Add word to dictionary**: ```zg```
* **Remove word to dictionary**: ```zug```
* **Enable spell checking (portuguese br)**: ```:setlocal spell spelllang=pt_br```

## Symbols for ranges
* **First line of file**: ```1```
* **Last line of file**: ```$```
* **Virtual line above the first one**: ```0```
* **Line where the cursor is placed**: ```.```
* **Line containing mark m**: ```'m```
* **Start of visual selection**: ```'<```
* **End of visual selection**: ```'>```
* **Entire file (shortcut for 1,$)**: ```%```

## Links and info
* **Cheat sheet**: http://www.atmos.albany.edu/daes/atmclasses/atm350/vi_cheat_sheet.pdf
* **Tutorial**: ```In your shell: vimtutor```
* **Help about motion**: ```:h motion.txt```

