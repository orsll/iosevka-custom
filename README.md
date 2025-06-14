This package  provides an Arch  Linux PKGBUILD file for  my custom build  of the
[Iosevka](https://github.com/be5invis/Iosevka) font.  It builds:

* The default, ss05 (Ubuntu) and ss12 (Fira) variants;
* All weights;
* Only normal width and spacing; and
* Discretionary ligatures, with the following cutom settings:
  * The "not equals"  ligation is activated with both the  exclamation sign (!=,
    =!=, !==) and slash (/=, =/=).   To differentiate between them, the slash is
    vertical with a dot at the bottom when using "!" and slanted when using "/".
    This can be useful, e.g., if you  use a language like Haskell, which has the
    slightly unusual notation "/=" for "not  equals", and want to have ligations
    for  both that  and "!=",  while still  being able  to tell  which character
    combination created it.
  * Equality/inequality  sign ligatures  use  three lines  when  they are  three
    characters long (e.g., in JavaScript).
