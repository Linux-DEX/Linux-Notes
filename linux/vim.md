# VIM / NEOVIM
## Global
| Command         | description            |
| --------------- | ---------------------- |
| :h[elp] keyword | open help for keyword  |
| :sav[eas] file  | save file as           |
| :clo[se]        | close current pane     |
| :ter[minal]     | open a terminal window |
| :w              | save file              |
| :wq             | save & exit            |
| :q              | exit                   |
| :!q             | exit without saving    |
| :x              | save & exit            |
| ZZ              | save & exit            |
| ZQ              | exit without saving    |
| :qa             | close all files        |

## Cursor Movement
| Command   | Description                                                           |
| --------- | --------------------------------------------------------------------- |
| h         | move cursor left                                                      |
| j         | move cursor down                                                      |
| k         | move cursor up                                                        |
| l         | move cursor right                                                     |
| gj        | move cursor down multi-line text                                      |
| gk        | move cursor up multi-line text                                        |
| H         | move to top of screen                                                 |
| M         | move to middle of screen                                              |
| L         | move to bottom of screen                                              |
| w         | jump forward to the start of word                                     |
| W         | jump forward to the start of a word ( word can contain punctuation )  |
| e         | jump forward to the end of a word                                     |
| E         | jump forward to the end of a word ( word can contain punctuation )    |
| b         | jump backward to the start of a word                                  |
| B         | jump backward to the start of a word ( word can contain punctuation ) |
| ge        | jump backwards to the end of a word                                   |
| gE        | jump backwards to the end of a word ( word can contain punctuatin )   |
| %         | move cursor to matching character eg: '()' '{}' '[]'                  |
| 0         | jump to the start of the line                                         |
| ^         | jump to the first non-blank character of the line                     |
| $         | jump to the end of the line                                           |
| g_        | jump to the last non-blank character of the line                      |
| gg        | go to the first line of the document                                  |
| G         | go to the last line of the document                                   |
| 5gg or 5G | go to line 5                                                          |
| gd        | move to local declaration                                             |
| gD        | move to global declaration                                            |
| fx        | jump to next occurrence of character x                                |
| tx        | jump to before next occurrence of character x                         |
| Fx        | jump to the previous occurrence of character x                        |
| Tx        | jump to after previous occurrence of character x                      |
| ;         | repeat previous f,t,F or T movement                                   |
| ,         | repeat previous f,t,F or T movement backwards                         |
| }         | jump to next paragraph                                                |
| {         | jump to previous paragraph                                            |
| zz        | center cursor on screen                                               |
| zt        | position cursor on top of the screen                                  |
| zb        | position cursor on bottom of the screen                               |
| ctrl + e  | move screen down one line                                             |
| ctrl + y  | move screen up on line                                                |
| ctrl + b  | move screen up one page                                               |
| ctrl + f  | move screen down one page                                             |
| ctrl + d  | move cursor & screen down 1/2 page                                    |
| ctrl + u  | move cursor & screen up 1/2 page                                      |
 
## INSERT MODE - inserting/appending text
| Command         | Description                                                                |
| --------------- | -------------------------------------------------------------------------- |
| i               | insert before the cursor                                                   |
| I               | insert at the beginning of the line                                        |
| a               | insert (append) after the cursor                                           |
| A               | insert (append) at the end of line                                         |
| o               | append (open) a new line below the current line                            |
| O               | append (open) a new line above the current line                            |
| ea              | insert (append) at the end of the word                                     |
| ctrl + h        | delete the character before the cursor during insert mode                  |
| ctrl + w        | delete word before the cursor during insert mode                           |
| ctrl + j        | add a line break at the cursor position during insert mode                 |
| ctrl + t        | indent (move right) line one shiftwidth during insert mode                 |
| ctrl + d        | de-indent (move left) line one shiftwidth during insert mode               |
| ctrl + n        | insert (auto-complete) next match before the cursor during insert mode     |
| ctrl + p        | insert (auto-complete) previous match before the cursor during insert mode |
| ctrl + rx       | insert the contents of register x                                          |
| ctrl + ox       | Temporarily enter normal mode to issue one normal-mode command x           |
| Esc or ctrl + c | exit insert mode                                                           |

## EDITING
| Command  | Description                                                  |
| -------- | ------------------------------------------------------------ |
| r        | replace a single character                                   |
| R        | replace more than one character, until ~ESC~ is pressed      |
| J        | join line below to the current one with one space in between |
| gJ       | join line below to the current one without space in between  |
| gwip     | reflow paragraph                                             |
| g~       | switch case up to motion                                     |
| gu       | change to lowercase up to motion                             |
| gU       | change to uppercase up to motion                             |
| cc       | change (replace) entire line                                 |
| c$ or C  | change (replace) to the end of the line                      |
| ciw      | change (replace) entire word                                 |
| cw or ce | change (replace) to the end of the word                      |
| s        | delete character and substitute text                         |
| S        | delete line and substitute text                              |
| xp       | transpose two letters (delete and paste)                     |
| u        | undo                                                         |
| U        | restore (undo) last changed line                             |
| ctrl + r | redo                                                         |
| .        | repeat last command                                          |

## MARKING TEXT (Visual mode)
| Command        | Description                                     |
| -------------- | ----------------------------------------------- |
| v              | start visual mode, mark lines, then do  command |
| V              | start linewise visual mode                      |
| o              | move to other end of marked area                |
| ctrl + v       | start visual block mode                         |
| O              | move to other corner of block                   |
| aw             | mark a word                                     |
| ab             | a block with ()                                 |
| aB             | a block with {}                                 |
| at             | a block with <> tags                            |
| ib             | inner block with ()                             |
| iB             | inner block with {}                             |
| it             | inner block with <> tags                        |
| Esc or ctrl +c | exit visual mode                                |

## VISUAL COMMANDS
| Command | Description                     |
| ------- | ------------------------------- |
| >       | shift text right                |
| <       | shift text left                 |
| y       | yank (copy) marked text         |
| d       | delete marked text              |
| ~       | switch case                     |
| u       | change marked text to lowercase |
| U       | change marked text to uppercase |

## REGISTERS
| Command      | Description                              |
| ------------ | ---------------------------------------- |
| :reg[isters] | show registers content                   |
| "xy          | yank into register x                     |
| "xp          | paste contents of register x             |
| "+y          | yank into the system clipboard register  |
| "+p          | paste from the system clipboard register |

## MARKS & POSITIONS
| Command  | Description                                        |
| -------- | -------------------------------------------------- |
| :marks   | list of marks                                      |
| ma       | set current position for mark A                    |
| `a       | jump to position of mark A                         |
| y`a      | yank text to position of mark A                    |
| `0       | go to the position where Vim was previously exited |
| `"       | go to the position when last editing this file     |
| `.       | go to the position of the last change in this file |
| ``       | go to the position before the last jump            |
| :ju[mps] | list of jumps                                      |
| ctrl + i | go to newer position in jump list                  |
| ctrl + o | go to older position in jump list                  |
| :changes | list of changes                                    |
| g,       | go to newer position in change list                |
| g;       | go to older position in change list                |
| ctrl + ] | jump to the tag under cursor                       |

## MACROS
| Command | Description          |
| ------- | -------------------- |
| qa      | record macro a       |
| q       | stop recording macro |
| @a      | run macro a          |
| @@      | rerun last run macro |

## CUT & PASTE
| Command         | Description                                                                                    |
| --------------- | ---------------------------------------------------------------------------------------------- |
| yy              | yank (copy) a line                                                                             |
| 2yy             | yank (copy) 2 lines                                                                            |
| yw              | yank (copy) the characters of the word from the cursor position to the start of the next word  |
| yiw             | yank (copy) word under the cursor                                                              |
| yaw             | yank (copy) word under the cursor and the space after or before it                             |
| y$ or Y         | yank (copy) to end of line                                                                     |
| p               | put (paste) the clipboard after cursor                                                         |
| P               | put (paste) before cursor                                                                      |
| gp              | put (paste) the clipboard after cursor and leave cursor after the new text                     |
| gP              | put (paste) before cursor and leave cursor after the new text                                  |
| dd              | delete (cut) a line                                                                            |
| 2dd             | delete (cut) 2 line                                                                            |
| dw              | delete (cut) the characters of the word from the cursor position to the start of the next word |
| diw             | delete (cut) word under the cursor                                                             |
| daw             | delete (cut) word under the cursor and the space after or before it                            |
| :3,5d           | delete lines starting from 3 to 5                                                              |
| :g/{pattern}/d  | delete all lines containing pattern                                                            |
| :g!/{pattern}/d | delete all lines not containing pattern                                                        |
| d$ or D         | delete (cut) to the end of the line                                                            |
| x               | delete (cut) character                                                                         |

## INDENT TEXT
| Command | Description                                       |
| ------- | ------------------------------------------------- |
| >>      | indent (move right) line one shiftwidth           |
| <<      | de-indent (move left) line one shiftwidth         |
| >%      | indent a block with () or {} (cursor on brace)    |
| <%      | de-indent a block with () or {} (cursor on brace) |
| >ib     | indent inner block with ()                        |
| >at     | indent a block with <> tags                       |
| 3==     | re-indent 3 lines                                 |
| =%      | re-indent a block with () or {} (cursor on brace) |
| =iB     | re-indent inner block with {}                     |
| gg=G    | re-indent entire buffer                           |
| ]p      | paste and adjust indent to current line           |

## SEARCH & REPLACE
| Command        | Description                                                          |
| -------------- | -------------------------------------------------------------------- |
| /pattern       | search for pattern                                                   |
| ?pattern       | search backward for pattern                                          |
| \vpattern      | non-alphanumeric characters are interpreted as special regex symbols |
| n              | repeat search in same direction                                      |
| N              | repeat search in opposite direction                                  |
| :%s/old/new/g  | replace all old with new throughout file                             |
| :%s/old/new/gc | replace all old with new throughout file with confirmation           |
| :noh[lsearch]  | remove highlighting of search matches                                |
| :s/old/new/g   | replace all old with new throughout the line                         |
| :s/old/new/g 5 | replace all old with new in next 5 lines                             |
| :s/old/new     | replace only first match of old with new                             |

## SEARCH IN MULTIPLE FILES
| Command                       | Description                                  |
| ----------------------------- | -------------------------------------------- |
| :vim[grep]/pattern/{`{file}`} | search for pattern in multiple files         |
| :cn[text]                     | jump to the next match                       |
| :cp[revious]                  | jump to the previous match                   |
| :cope[n]                      | open a window containing the list of matches |
| :ccl[ose]                     | close the quickfix window                    |

## TABS
| Command                              | Description                                           |
| ------------------------------------ | ----------------------------------------------------- |
| :tabnew or :tabnew {page.words.file} | open a file in a new tab                              |
| ctrl + wT                            | move the currrent split window into its own tab       |
| gt or :tabn[ext]                     | move to the next tab                                  |
| gT or :tabp[revious]                 | move to the previous tab                              |
| #gt                                  | move to tab number #                                  |
| :tabm[ove] #                         | move current tab to the #th position (indexed from 0) |
| :tabo[nly]                           | close all tabs except for the current one             |
| :tabdo                               | command - run the command on all tabs                 |

## WORKING WITH MULTIPLE FILES
| Command            | Description                                                                      |
| ------------------ | -------------------------------------------------------------------------------- |
| :e[dit] file       | edit a file in a new buffer                                                      |
| :bn[ext]           | go to the next buffer                                                            |
| :bp[revious]       | go to the previous buffer                                                        |
| :bd[delete]        | delete a buffer (close a file)                                                   |
| :b[uffer]#         | go to a buffer by index #                                                        |
| :b[uffer] file     | go to a buffer by file                                                           |
| :ls or :buffers    | list all open buffers                                                            |
| :sp[lit] file      | open a file in new buffer and split window                                       |
| :vs[plit] file     | open a file in a new buffer and vertically split window                          |
| :vert[ical] ba[ll] | edit all buffers and vertical windows                                            |
| :tab ba[ll]        | edit all buffers as tabs                                                         |
| ctrl + ws          | split window                                                                     |
| ctrl + wv          | split window vertically                                                          |
| ctrl + ww          | switch windows                                                                   |
| ctrl + wq          | quit a window                                                                    |
| ctrl + wx          | exchange current window with next one                                            |
| ctrl + w=          | make all windows equal height & width                                            |
| ctrl + wh          | move cursor to the left window (vertical split)                                  |
| ctrl + wl          | move cursor to the right window (vertical split)                                 |
| ctrl + wj          | move cursor to the window below (horizontal split)                               |
| ctrl + wk          | move cursor to the window above (horizontal split)                               |
| ctrl + wH          | make current window full height at far left (leftmost vertical window)           |
| ctrl + wL          | make current window full height at far right (rightmost vertical window)         |
| ctrl + wJ          | make current window full width at the very bottom (bottommost horizontal window) |
| ctrl + wK          | make current window full width at the very top (topmost horizontal window)       |

## Diff
| Command          | Description                                 |
| ---------------- | ------------------------------------------- |
| zf               | manually define a fold up to motion         |
| zd               | delete fold under the cursor                |
| za               | toggle fold under the cursor                |
| zo               | open fold under the cursor                  |
| zc               | close fold under the cursor                 |
| zr               | reduce (open) all folds by one level        |
| zm               | fold more (close) all folds by one level    |
| zi               | toggle folding functionality                |
| ]c               | jump to start of next change                |
| [c               | jump to start on previous change            |
| do or :diffg[et] | obtain (get) difference (from other buffer) |
| dp or :diffpu[t] | put difference (to other buffer)            |
| :diffthis        | make current window part of diff            |
| :dif[fupdate]    | update differences                          |
| :diffo[ff]       | switch off diff mode for current window     |

