<!---  PLEASE DO NOT EDIT DIRECTLY. EDIT THE .md.in FILE PLEASE. --->
# Data types

## List of types

Miller's types for function processing are:

* Scalars:
    * **string**
    * **float** (double-precision)
    * **int** (64-bit signed)
    * **boolean**
* Collections:
    * **map**
    * **array**
* Nulls and error:
    * **empty-null** (empty string)
    * **absent-null** (reads of unset right-hand sides, or fall-through non-explicit return values from user-defined functions)
    * **JSON-null** (TODO)
    * **error** (TODO: give an example)

TODO: point to null-data page; arrays page; arithmetic page; what else?

## To be ported

Miller's input and output are all string-oriented: there is (as of August 2015 anyway) no support for binary record packing. In this sense, everything is a string in and out of Miller.  During processing, field names are always strings, even if they have names like "3"; field values can have various data types.  Field values' ability to be interpreted as a non-string type only has meaning when comparison or function operations are done on them.  And it is an error condition if Miller encounters non-numeric (or otherwise mistyped) data in a field in which it has been asked to do numeric (or otherwise type-specific) operations.

Field values are treated as numeric for the following:

* Numeric sort: `mlr sort -n`, `mlr sort -nr`.
* Statistics: `mlr histogram`, `mlr stats1`, `mlr stats2`.
* Cross-record arithmetic: `mlr step`.

For `mlr put` and `mlr filter`:

* Miller's types for function processing are **empty-null** (empty string), **absent-null** (reads of unset right-hand sides, or fall-through non-explicit return values from user-defined functions), **error**, **string**, **float** (double-precision), **int** (64-bit signed), and **boolean**.

* On input, string values representable as numbers, e.g. "3" or "3.1", are treated as int or float, respectively. If a record has `x=1,y=2` then `mlr put '$z=$x+$y'` will produce `x=1,y=2,z=3`, and `mlr put '$z=$x.$y'` does not give an error, but only because the dot operator has been generalized to stringify non-strings.  To coerce back to string for processing, use the `string` function: `mlr put '$z=string($x).string($y)'` will produce `x=1,y=2,z=12`.

* On input, string values representable as boolean  (e.g. `"true"`, `"false"`) are *not* automatically treated as boolean.  (This is because `"true"` and `"false"` are ordinary words, and auto string-to-boolean on a column consisting of words would result in some strings mixed with some booleans.) Use the `boolean` function to coerce: e.g. giving the record `x=1,y=2,w=false` to `mlr put '$z=($x<$y) || boolean($w)'`.

* Functions take types as described in `mlr --help-all-functions`: for example, `log10` takes float input and produces float output, `gmt2sec` maps string to int, and `sec2gmt` maps int to string.

* All math functions described in `mlr --help-all-functions` take integer as well as float input.

## Escape sequences for string literals

You can use the following backslash escapes for strings such as between the double quotes in contexts such as `mlr filter '$name =~ "..."'`, `mlr put '$name = $othername . "..."'`, `mlr put '$name = sub($name, "...", "...")`, etc.:

* `\a`: ASCII code 0x07 (alarm/bell)
* `\b`: ASCII code 0x08 (backspace)
* `\f`: ASCII code 0x0c (formfeed)
* `\n`: ASCII code 0x0a (LF/linefeed/newline)
* `\r`: ASCII code 0x0d (CR/carriage return)
* `\t`: ASCII code 0x09 (tab)
* `\v`: ASCII code 0x0b (vertical tab)
* `\\`: backslash
* `\"`: double quote
* `\123`: Octal 123, etc. for `\000` up to `\377`
* `\x7f`: Hexadecimal 7f, etc. for `\x00` up to `\xff`

See also [https://en.wikipedia.org/wiki/Escape_sequences_in_C](https://en.wikipedia.org/wiki/Escape_sequences_in_C).

These replacements apply only to strings you key in for the DSL expressions for `filter` and `put`: that is, if you type `\t` in a string literal for a `filter`/`put` expression, it will be turned into a tab character. If you want a backslash followed by a `t`, then please type `\\t`.

However, these replacements are done automatically only for string literals within DSL expressions -- they are not done automatically to fields within your data stream.  If you wish to make these replacements, you can do (for example) `mlr put '$field = gsub($field, "\\t", "\t")'`. If you need to make such a replacement for all fields in your data, you should probably use the system `sed` command instead. 

