<!---  PLEASE DO NOT EDIT DIRECTLY. EDIT THE .md.in FILE PLEASE. --->
# Glossary

_Under construction_

## $*

All key-value pairs in the current record, as a [map](reference-main-maps.md).

## @*

All [out-of-stream variables](reference-dsl-variables.md#out-of-stream-variables), as a [map](reference-main-maps.md).
Synonymous with `all`.

## absent

The data-type obtained from accessing a missing key, e.g. `$x` when the current record has no field named `x`.
See the [null-data page](reference-main-null-data.md).

## all

All [out-of-stream variables](reference-dsl-variables.md#out-of-stream-variables), as a [map](reference-main-maps.md).
Synonymous with `@*`.

## array

A list of [values](reference-main-data-types.md), indexable by integer index starting with 1 for the first value.

## auxents

## begin

## block

## bool

A boolean [true/false value](reference-main-data-types.md).

## break

Used to exit a [for-loop or while-loop](reference-dsl-control-structures.md)
earlier than its top-of-loop continuation expression would have specific.

## bunzip2 / .bz2

## call

## colorization

## compression

## continue

Used to jump to the next iteration of a [for-loop or while-loop](reference-dsl-control-structures.md)
without executing the remaining loop-body statements on the current iteration.

## CSV

A popular [file format](file-formats.md#csvtsvasvusvetc) for tabular data
(comma-separated values) supported by Miller.

## Cygwin

A collection of GNU and open-source tools which provide functionality similar
to a Linux distribution on Windows.  Miller can run inside Cygwin, but does not
need to. See [Miller on Windows](miller-on-windows.md).

## delimiter

## division

## DKVP

A Miller-specific [file format](file-formats.md#dkvp-key-value-pairs) for
key-value pairs, with each line of a file being of the form `x=1,y=2,z=3`.  For
historical reasons, this is Miller's default format unless
[flags](reference-main-io-options.md) such as `--csv` are supplied.  You can
also make CSV your default format using a [.mlrrc file(customization.md).

## do

Keyword used to indicate the start of a [do-while loop](reference-dsl-control-structures.md)
in the [Miller programming language](programming-language.md).

## DSL

The [Miller programming language](programming-language.md) is embedded within
the [put and filter verbs](reference-dsl). It's a language with its own syntax
and semantics; the Miller executable does not embed, say, Python or Lua as a
language for put and filter statements. This makes the Miller programming
language an _embedded domain-specific language_, or _domain-specific language_,
or (more briefly) a _DSL_.

## dump

## edump

## elif

## else

## emit

## emitf

## emitp

## empty

## end

## ENV

## eprint

## eprintn

## false

## field

## FILENAME

## FILENUM

## filter

## float

## FNR

## for

Keyword used to indicate the start of a [for-loop](reference-dsl-control-structures.md)
in the [Miller programming language](programming-language.md).

## format

## func

## function

## gzip / .gz

## hashmap

## header

## heterogeneity

## if

Keyword used to indicate the start of an [if-statement](reference-dsl-control-structures.md)
in the [Miller programming language](programming-language.md).

## IFS

## in

## in-place

## int

## IPS

## IRS

## JSON

## line

## manpage

## map

A data structure in the [Miller programming language](programming-language.md) containing
an ordered sequence of key-value pairs.
See the [maps page](reference-main-maps.md) for more information.

## .mlrrc

A file you can create, nominally in your home directory, to customize the
default flag-settings used by Miller. For example, while Miller's default file
format is [DKVP](#dkvp), you can make the default format be CSV so that instead
of `mlr --csv sort myfile.csv` you can simply do `mlr sort myfile.csv`.

## msys2

## M_E

## M_PI

## NF

## nidx

## NR

## null

## num

## OFS

## one-up

## oosvar

A whimsical shorthand for [out-of-stream variable](#out-of-stream-variable).

## OPS

## ORS

## Out-of-stream variable

Variables, prefixed with the `@` sigil, which persist their values across
multiple records in the [Miller programming language](programming-language.md).
See [out-of-stream
variables](reference-dsl-variables.md#out-of-stream-variables) for more
information.

## PPRINT

A Miller-specific [file format](file-formats.md#pprint-pretty-printed-tabular)
for key-value pairs, with columns vertically aligned for easy visual scanning.

## print

## printn

## put

## ragged

## record

## rectangular

## REPL

## return

## semicolon

Semicolons are used to [delimit statements](reference-dsl-syntax.md) in the
[Miller programming language](programming-language.md).

## separator

## sparse

## stderr

## stdout

## str

## streaming

## subr

## subroutine

## tee

## terminator

## toolkit

## true

## TSV

A popular [file format](file-formats.md#csvtsvasvusvetc) for tabular data
(tab-separated values) supported by Miller.

## unset

## unsparse

## var

## variable

## verb

## while

Keyword used to indicate the start of a [while-loop](reference-dsl-control-structures.md),
and also used in do-while loops, in the [Miller programming language](programming-language.md).

## XTAB

A Miller-specific [file format](file-formats.md#xtab-vertical-tabular) for
key-value pairs: it's a vertical-tabular format useful for looking a files with
a large number of columns. Example: `mlr --icsv --oxtab head -n 1
widefile.csv`.

## zero-up

## zlib / .z
