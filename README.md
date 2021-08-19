# Beamer TikZ Utilities

Collected here are some useful things that make beamer and TikZ play a
bit nicer together.
They are currently all based on ideas from
[TeX-SX](https://tex.stackexchange.com).

## Overlay-Aware Styles

Originally designed by [Matthew Leingang](https://tex.stackexchange.com/users/1402/matthew-leingang) from [How to make beamer overlays with Tikz node](https://tex.stackexchange.com/a/6155/86).

* `onslide=<overlay specification>{style set}`

  Uses `style set` when the `overlay specification` matches.
  
* `alt=<overlay specification>{style set 1}{style set 2}`

  Uses `style set 1` when the `overlay specification` matches,
  otherwise uses `style set 2`.
  
* `temporal=<overlay specification>{style set 1}{style set 2}{style
  set 3}`

  Uses `style set 2` when the `overlay specification` matches,
  otherwise uses `style set 1` if before and `style set 3` if after.
  
## Jumping Pictures

Originally designed by [me](https://tex.stackexchange.com/users/86/andrew-stacey) from [How can I fix jumping TikZ pictures in beamer?](https://tex.stackexchange.com/a/51638/86).

If a picture is built up from components that are added bit by bit
then the whole picture might jump around since TeX just uses its
bounding box to place it on the page.
The code in this section prevents that by saving the bounding boxes of
the intermediate pictures and imposing the largest one throughout.
This means that the picture will stay in the same place through
different frames.

* `stop jumping`

  Use this key on a TikZ picture that you want to use this with.
  
* `max size={width}{height}`

  Used in conjunction with the `stop jumping` key, this will shrink
  the picture (if necessary) so that it fits inside a box of width
  `width` and height `height`.
  The aspect ratio is preserved.
  
* `constrain`

  This key will clip the picture to the eventual bounding box.
  The purpose of this is to ensure that any paths drawn using the
  `overlay` specification don't stray outside the eventual bounding
  box.

* `enclosing box`

  This is the name of a rectangular pseudo-node that fits the eventual
  bounding box.
  It is available at the start of the picture (unlike the pseudo-nodes
  that TikZ defines automatically).

* `enclosing box/offset=<dimen>`

  This adds a little extra to the enclosing box so that it isn't tight
  against the picture's contents.
  It does this in a way to ensure that the picture doesn't keep
  getting bigger on each run.

  
