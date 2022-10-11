# krkrz_textrenderguide

This is a rough guide to special command usage in KiriKiriZ TextRender(.dll) based visual novel dialogue.

This syntax is very common in different VN systems built on top of krkrz, apart from direct KAG script,
and is typically impleted via one of the following:
- By `textrender.dll`, a binary plugin
- By `textrender.tjs`, a pure TJS version of the parser
- By `texttagconverter.tjs`, a TJS parser that turns this syntax into KAG tags for the KAG[EX] engine.  
This is in particular typical for novels that use the `SCN` binary scene format.

## Notes
- Bold and italics can only work if the selected font face has them. If not, text will be rendered normally.
- Lines cannot start with a character wait command (`%wXXX;`), it will cause a script exception in some cases.

## Functional
- `\n` Linebreak
- `\t` Tabstop character
- `\i` Indent the following lines to current horizontal position
- `\r` Reset indenting for following lines
- `\w` Advance display position by one blank character (not supported in all cases)
- `\k` Wait for click/key input
- `\x` Null ? (not supported in all cases)
- `\` When followed by some other control character, escapes that character.

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
- `%n` Bold and italics off.
- `%s1` Shadow on.
- `%s0` Shadow off.
- `%e1` Edge on.
- `%e0` Edge off.
- `%B` Large text.
- `%S` Small text.
- `%L` Align to left.
- `%R` Align to right.
- `%C` Align to center.
- `%r` Reset all styling.
- `%NUM;` Font size change, where `NUM` is a percentage compared to default. `%100;` is default.
- `%fNAME;` Font face change, where `NAME` is a preregistered custom or allowed system font name.  
Use `%fuser;` to reset back to user-selected/default font.
- `#XXXXXX;` Font color change where `XXXXXX` is a hexadecimal RGB color value. Use `#;` to reset.
- `%pNUM;` Text pitch change, a.k.a. letter spacing. `NUM` is integer in relative font points.  
For example, `%p-1;` = one unit less than default, `%p10;` = ten units more than default. Use `%p;` to reset.

## Timing
- `%dNUM;` Change text display speed (wait time), where `NUM` is a percentage of the default. Lower = faster.
- `%aNUM;` Change text display speed (wait time), where `NUM` is an absolute value (in ms?)
- `%wNUM;` Wait for `NUM` count character display times.
- `%tNUM;` Wait for `NUM` milliseconds.
- `%DNUM;` Time synchronization (???) for `NUM` milliseconds
- `%D$XXX;` Time synchronization (???) where `XXX` is a label name

## Special
- `$XXX;` Print a variable, where `XXX` is processed by `onEval()`.
- `&XXX;` Print a graphic, where `XXX` is the name of a an image.

### Disclaimer
Reversed and cobbled together from multiple sources.  
Accuracy for any given game not guaranteed.  
Pull requests/comments welcome and appreciated.  

xoxo,  
yumi/pantsudev
