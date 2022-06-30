# krkrz_textrenderguide

This is a rough guide to special command usage in KiriKiriZ TextRender(.dll) based visual novel dialogue.

## Notes
- The font face is assumed to stay the same per a single draw call. Results are not guaranteed if it changes midway through. I think.
- Bold and italics can only work if the selected font face has them. If not, text will be rendered normally.
- Lines cannot start with a wait command (`%wXXX;`), it will cause a script exception.

## Functional
- `\n` Linebreak
- `\t` Tabstop character
- `\i` Indentation, from next line
- `\r` Unindentation, from next line
- `\w` Advance display position by one blank character
- `\k` Wait for key input
- `\x` Null ???

## Rubies/Furigana
Rubies are small annotations that are rendered above, below or next to base text, in this case above.  
Usually this means furigana, but works fine with western characters too.
- `[XX]` Ruby specification over the immediately following character. `XX` is what to display above, usually hiragana.
- `[XX, NUM]` Ruby specification over `NUM` following characters. `XX` is what to display above, usually hiragana.

## Text styling
- `%b1` Bold on.
- `%b0` Bold off.
- `%i1` Italics on.
- `%i0` Italics off.
- `%s1` Shadow on.
- `%s0` Shadow off.
- `%B` Large text.
- `%S` Small text.
- `%L` Align to left.
- `%R` Align to right.
- `%C` Align to center.
- `%r` Reset all styling.
- `%NUM` Font size change, where `NUM` is a percentage compared to default. Use 3 numbers, pad with zeroes.
- `%fNAME;` Font face change, where `NAME` is a preregistered or system font. Use `%fuser;` to reset back to user-selected/default font.
- `#XXXXXX;` Font color change where `XXXXXX` is a hexadecimal RGB color value.
- `%pNUM;` Text pitch change, a.k.a. letter spacing. `NUM` is integer in relative font points.  For example, `%p-1;` = one unit less than default, `%p10;` = ten units more than default. Use `%p;` to reset.

## Timing
- `%dNUM;` Change text display speed (wait time), where `NUM` is a percentage of the default. Lower = faster.
- `%wNUM;` Wait for `NUM` count character display times. Use 3 numbers, pad with zeroes.
- `%DNUM;` Time synchronization (???) for `NUM` milliseconds
- `%D$XXX;` Time synchronization (???) where `XXX` is a label name

## Special
- `$XXX;` Print a variable, where `XXX` is processed by `onEval()`.
- `&XXX;` Print a graphic, where `XXX` is the name of a predefined image ???

### Disclaimer
Reversed and cobbled together from multiple sources.  
Accuracy for any given game not guaranteed.  
Pull requests/comments welcome and appreciated.  

xoxo,  
yumi/pantsudev
