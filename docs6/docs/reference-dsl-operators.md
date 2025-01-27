<!---  PLEASE DO NOT EDIT DIRECTLY. EDIT THE .md.in FILE PLEASE. --->
# DSL operators

## Operator precedence

Operators are listed in order of decreasing precedence, highest first.

<pre class="pre-non-highlight-non-pair">
Operators              Associativity
---------              -------------
()                     left to right
**                     right to left
! ~ unary+ unary- &    right to left
binary* / // %         left to right
binary+ binary- .      left to right
<< >> >>>              left to right
&                      left to right
^                      left to right
|                      left to right
< <= > >=              left to right
== != =~ !=~           left to right
???
??
&&                     left to right
^^                     left to right
||                     left to right
? :                    right to left
=                      N/A for Miller (there is no $a=$b=$c)
</pre>

## Operator and function semantics

* Functions are often pass-throughs straight to the system-standard Go libraries.

* The [`min`](reference-dsl-builtin-functions.md#min) and [`max`](reference-dsl-builtin-functions.md#max) functions are different from other multi-argument functions which return null if any of their inputs are null: for [`min`](reference-dsl-builtin-functions.md#min) and [`max`](reference-dsl-builtin-functions.md#max), by contrast, if one argument is absent-null, the other is returned. Empty-null loses min or max against numeric or boolean; empty-null is less than any other string.

* Symmetrically with respect to the bitwise OR, XOR, and AND operators
[`|`](reference-dsl-builtin-functions.md#bitwise-or),
[`&`](reference-dsl-builtin-functions.md#bitwise-and), and
[`^`](reference-dsl-builtin-functions.md#bitwise-xor), Miller has logical operators
[`||`](reference-dsl-builtin-functions.md#logical-or),
[`&&`](reference-dsl-builtin-functions.md#logical-and), and
[`^^`](reference-dsl-builtin-functions.md#logical-xor).

* The exponentiation operator [`**`](reference-dsl-builtin-functions.md#exponentiation) is familiar from many languages, except that an integer raised to an int power is int, not float.

* The regex-match and regex-not-match operators [`=~`](reference-dsl-builtin-functions.md#regmatch) and [`!=~`](reference-dsl-builtin-functions.md#regnotmatch) are similar to those in Ruby and Perl.

