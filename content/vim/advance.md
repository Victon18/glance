# folding
- `z+R` -> unfold all folds
- `z+M` -> fold all unfolds
- `z+c` -> individual folds
- `z+o` -> individual unfolds

- `==` -> indent a line
- `"visually selected lines"+=` -> indent selected lines
- `"visually selected lines"+>` -> shift selected lines to the right side
- `"visually selected lines"+<` -> shift selected lines to the left side

-  `%` -> jump between brackets under cursor
- `"relative line no"+J` -> join upto given line no
- `"visually selected lines"+J` -> join all selected lines

- `~` -> toggle case of character under cursor
- `gUw` -> uppercase word under cursor
- `guw` -> lowercase word under cursor
- `gUU` -> uppercase whole line
- `guu` -> lowercase whole line
- `<C-a>` -> increment number under cursor
- `<C-x>` -> decrement number under cursor

# multiple modification
- `"visual vertical select"+I+"modifications"+esc` ->  make same modifications to the selected lines

### macro recording
1. `qa` -> start recording
2. macro will be stored as a character
3. do modifications
4. `q` -> quit recording
5. `"relative line no"+@a` -> to apply recording to a specific line

# command mode
- `:sort` -> sort in  ascending order
- `:sort!` -> sort in descending order
- `:read \path\to\file` -> read and append its content under cursor
- `:read !command` -> append the output respective command under cursor
- `:'<,'>!jq .city` -> parse visually selected json data and get specific column
- `:'<,'>s/to_replace/replaced_with/g` -> substitute all matching pattern
- `:g/pattern/d` -> delete all lines with matching pattern
- `:v/http/d` -> delete all lines the do not match this pattern

# registers

