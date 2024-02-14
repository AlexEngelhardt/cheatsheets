# ipdb

## Some tips

- `n`: Step over
- `s`: Step into
- `j` line_no : Jump to line line_no

## Full cheatsheet

From here: https://wangchuan.github.io/coding/2017/07/12/ipdb-cheat-sheet.html

<dl>

<dt>h(elp)</dt>
<dd>Without argument, print the list of available commands. With a command name as argument, print help about that command.</dd>

<dt>w(here)</dt>
<dd>Print a stack trace, with the most recent frame at the bottom. An arrow indicates the “current frame”, which determines the context of most commands.</dd>

<dt>d(own)</dt>
<dd>Move the current frame one level down in the stack trace (to a newer frame).</dd>

<dt>u(p)</dt>
<dd>Move the current frame one level up in the stack trace (to an older frame).</dd>

<dt>b(reak): [ ([filename:]lineno | function) [, condition] ]</dt>
<dd>With a filename:line number argument, set a break there. If filename is omitted, use the current file. With a function name, set a break at the first executable line of that function. Without argument, list all breaks. Each breakpoint is assigned a number to which all the other breakpoint commands refer.

The condition argument, if present, is a string which must evaluate to true in order for the breakpoint to be honored.</dd>

<dt>tbreak: [ ([filename:]lineno | function) [, condition] ]</dt>
<dd>Temporary breakpoint, which is removed automatically when it is first hit. The arguments are the same as break.</dd>

<dt>cl(ear): [bpnumber [bpnumber ...] ]</dt>
<dd>With a space separated list of breakpoint numbers, clear those breakpoints. Without argument, clear all breaks (but first ask confirmation).</dd>

<dt>disable bpnumber: [bpnumber ...]</dt>
<dd>Disables the breakpoints given as a space separated list of breakpoint numbers. Disabling a breakpoint means it cannot cause the program to stop execution, but unlike clearing a breakpoint, it remains in the list of breakpoints and can be (re-)enabled.</dd>

<dt>enable bpnumber: [bpnumber ...]</dt>
<dd>Enables the breakpoints specified.</dd>

<dt>ignore bpnumber count</dt>
<dd>Sets the ignore count for the given breakpoint number. If count is omitted, the ignore count is set to 0. A breakpoint becomes active when the ignore count is zero. When non-zero, the count is decremented each time the breakpoint is reached and the breakpoint is not disabled and any associated condition evaluates to true.</dd>

<dt>condition bpnumber condition</dt>
<dd>condition is an expression which must evaluate to true before the breakpoint is honored. If condition is absent, any existing condition is removed; i.e., the breakpoint is made unconditional.</dd>

<dt>s(tep)</dt>
<dd>Execute the current line, stop at the first possible occasion (either in a function that is called or in the current function).</dd>

<dt>n(ext)</dt>
<dd>Continue execution until the next line in the current function is reached or it returns.</dd>

<dt>unt(il)</dt>
<dd>Continue execution until the line with a number greater than the current one is reached or until the current frame returns.</dd>

<dt>r(eturn)</dt>
<dd>Continue execution until the current function returns.</dd>

<dt>run [args ...]</dt>
<dd>Restart the debugged python program. If a string is supplied it is splitted with “shlex”, and the result is used as the new sys.argv. History, breakpoints, actions and debugger options are preserved. “restart” is an alias for “run”.</dd>

<dt>c(ont(inue))</dt>
<dd>Continue execution, only stop when a breakpoint is encountered.</dd>

<dt>l(ist): [first [,last]]</dt>
<dd>List source code for the current file. Without arguments, list 11 lines around the current line or continue the previous listing. With one argument, list 11 lines starting at that line. With two arguments, list the given range; if the second argument is less than the first, it is a count.</dd>

<dt>a(rgs)</dt>
<dd>Print the argument list of the current function.</dd>

<dt>p expression</dt>
<dd>Print the value of the expression.</dd>

</dl>
