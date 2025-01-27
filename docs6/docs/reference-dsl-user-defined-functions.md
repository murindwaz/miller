<!---  PLEASE DO NOT EDIT DIRECTLY. EDIT THE .md.in FILE PLEASE. --->
# DSL user-defined functions

As of Miller 5.0.0 you can define your own functions, as well as subroutines.

## User-defined functions

Here's the obligatory example of a recursive function to compute the factorial function:

<pre class="pre-highlight-in-pair">
<b>mlr --opprint --from data/small put '</b>
<b>    func f(n) {</b>
<b>        if (is_numeric(n)) {</b>
<b>            if (n > 0) {</b>
<b>                return n * f(n-1);</b>
<b>            } else {</b>
<b>                return 1;</b>
<b>            }</b>
<b>        }</b>
<b>        # implicitly return absent-null if non-numeric</b>
<b>    }</b>
<b>    $ox = f($x + NR);</b>
<b>    $oi = f($i);</b>
<b>'</b>
</pre>
<pre class="pre-non-highlight-in-pair">
a   b   i x        y        ox                 oi
pan pan 1 0.346791 0.726802 0.4670549976810001 1
eks pan 2 0.758679 0.522151 3.6808304227112796 2
wye wye 3 0.204603 0.338318 1.7412477437471126 6
eks wye 4 0.381399 0.134188 18.588317372151177 24
wye pan 5 0.573288 0.863624 211.38663947090302 120
</pre>

Properties of user-defined functions:

* Function bodies start with `func` and a parameter list, defined outside of `begin`, `end`, or other `func` or `subr` blocks. (I.e. the Miller DSL has no nested functions.)

* A function (uniqified by its name) may not be redefined: either by redefining a user-defined function, or by redefining a built-in function. However, functions and subroutines have separate namespaces: you can define a subroutine `log` (for logging messages to stderr, say) which does not clash with the mathematical `log` (logarithm) function.

* Functions may be defined either before or after use -- there is an object-binding/linkage step at startup.  More specifically, functions may be either recursive or mutually recursive.

* Functions may be defined and called either within `mlr filter` or `mlr put`.

* Argument values may be reassigned: they are not read-only.

* When a return value is not implicitly returned, this results in a return value of [absent-null](reference-main-null-data.md). (In the example above, if there were records for which the argument to `f` is non-numeric, the assignments would be skipped.) See also the [null-data reference page](reference-main-null-data.md).

* See the section on [Local variables](reference-dsl-variables.md#local-variables) for information on scope and extent of arguments, as well as for information on the use of local variables within functions.

* See the section on [Expressions from files](reference-dsl-syntax.md#expressions-from-files) for information on the use of `-f` and `-e` flags.

## User-defined subroutines

Example:

<pre class="pre-highlight-in-pair">
<b>mlr --opprint --from data/small put -q '</b>
<b>  begin {</b>
<b>    @call_count = 0;</b>
<b>  }</b>
<b>  subr s(n) {</b>
<b>    @call_count += 1;</b>
<b>    if (is_numeric(n)) {</b>
<b>      if (n > 1) {</b>
<b>        call s(n-1);</b>
<b>      } else {</b>
<b>        print "numcalls=" . @call_count;</b>
<b>      }</b>
<b>    }</b>
<b>  }</b>
<b>  print "NR=" . NR;</b>
<b>  call s(NR);</b>
<b>'</b>
</pre>
<pre class="pre-non-highlight-in-pair">
NR=1
numcalls=1
NR=2
numcalls=3
NR=3
numcalls=6
NR=4
numcalls=10
NR=5
numcalls=15
</pre>

Properties of user-defined subroutines:

* Subroutine bodies start with `subr` and a parameter list, defined outside of `begin`, `end`, or other `func` or `subr` blocks. (I.e. the Miller DSL has no nested subroutines.)

* A subroutine (uniqified by its name) may not be redefined. However, functions and subroutines have separate namespaces: you can define a subroutine `log` which does not clash with the mathematical `log` function.

* Subroutines may be defined either before or after use -- there is an object-binding/linkage step at startup.  More specifically, subroutines may be either recursive or mutually recursive. Subroutines may call functions.

* Subroutines may be defined and called either within `mlr put` or `mlr put`.

* Subroutines have read/write access to `$`-variables and `@`-variables.

* Argument values may be reassigned: they are not read-only.

* See the section on [local variables](reference-dsl-variables.md#local-variables) for information on scope and extent of arguments, as well as for information on the use of local variables within functions.

* See the section on [Expressions from files](reference-dsl-syntax.md#expressions-from-files) for information on the use of `-f` and `-e` flags.
