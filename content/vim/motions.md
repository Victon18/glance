normal
visual
insert
leader key
save -> :w
# horizontal nav
hjkl -> motions
5j-> 5 line motion
w -> word by word motion
b -> backward word by word
e -> jump to the end of a word
$ -> end of line
0 -> start of line
^ -> jump first non empty char
f+'char' -> jump to first next specific character
F+'char'-> jump to last next specific character
# vertical nav
() -> one sentence up and down
{} -> one paragraph up and down
<C-d> -> half page up
<C-u> -> half page down
<C-f> -> full page up
<C-b> -> full page down
gg -> start of the page
G -> end of the page
# entering into insert
i -> insert before the cursor
a -> insert after the cursor
I -> insert at the start of the line
A -> insert at the end of the line
o -> insert after the current line
O -> insert before the current line
c -> insert by changing the word
s -> insert by replacing the current chaaracter
# visual mode
y -> yank
p -> paste
yy -> yank a line
yi+"respective curly" -> yank whats between the curly braces
ya+"respective curly" -> yank whats between the curly braces and braces itself
u -> undo
<C-r> -> redo
diw -> delete a word
dis -> delete a sentence
dip -> delete a paragraph
dd -> delete a whole line
dt+'char' -> delete upto that char
. -> repeat last operation
ciw -> change a word
/+"word" -> search the file
n -> iterate on search results
N -> iterate on search results backward
`*` -> search forward for the word under the cursor
`#` -> search backward for the word under the cursor
m+"char" -> to bookmark position under letter a
`backtick`+"char" -> return to the bookmarked position
`2*backtick` -> toggle between last two visited position
`backtick`+. -> last position where editing happend

