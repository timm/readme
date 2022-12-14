
#	readme.lua	

> Assumes a simple Hungarian notation,  infer doco from LUA files	
 	
For example, this file was generated via	
 	
      lua readme.lua readme.lua > README.md	
    	
## Why this code?	
I love documentation and I do not love most documentation 	
generators. 	
- Why are they so complex to use? 	
- Why can't they be really short and easy to change?	
- Why can't they just create tables for the functions,	
generated from in-line comments around the code? 	
- And if I use	
just a few simple naming conventions, why can't they add type	
hints to my favorite untyped languages (lua, lisp, etc).	
  	
## Conventions	
 	
1. Lines with Markdown start with `-- ` (and  we will print those).	
2. We only show help on public function.	
3. Public functions are denoted with a  trailing "-->", followed by 	
   return type then some comment text. e.g.     	
   `function fred(s) --> str; Returns `s`, written as a string`   	
   Note the semi-colon. Do not skip it (its important).	
4. In public function arguments, lower case versions of class type 	
   (e.g. `data`) are instances of that type (e.g.  `data` are `DATA` 	
   so `datas` is a list of `DATA` instances).	
5  Built in types are num, str, tab, bool, fun	
6. User-defined types are ny word starting with two upper case 	
   leading letters is a class; e.g. DATA	
7. Public function arguments have the following type hints:	
   	
| What        | Notes                                         |                                     	
|:------------|:----------------------------------------------|	
| 2 blanks    | 2 blanks denote start of optional arguments   |	
| 4 blanks    | 4 blanks denote start of local arguments      |	
| n           | prefix for numerics                           |	
| s           | prefix for strings                            |	
| is          | prefix for booleans                           |	
| suffix fun  | suffix for functions                          |                      	
| suffix s    | list of thing (so `names` is list of strings) |]]) end	
    	
## Guessing types	

| What | Notes |
|:---|:---|
| <b>are.of(s:`str`) &rArr;  ?str</b> |   top level, guesses a variable's type |


Types are either singular (one thing) or plural (a set of	
things). The naming conventions for plurals is the same as	
singulars, we just add an `s`. E.g. `bools` is a table of	
booleans. and `ns` is a table of `n`umbers.	
Singulars are either `bools`, `fun` (function),	
`n` (number), `s` (string), or `t` (table).	

| What | Notes |
|:---|:---|
| <b>are.bool(s:`str`) &rArr;  ?"bool"</b> |  names starting with "is" are booleans |
| <b>are.fun(s:`str`) &rArr;  ?"fun"</b> |  names ending in "fun" are functions |
| <b>are.num(s:`str`) &rArr;  ?"n"</b> |  names start with "n" are numbers  |
| <b>are.str(s:`str`) &rArr;  ?"s"</b> |  names starting with "s" are strings |
| <b>are.tbl(s:`str`) &rArr;  ?"tab"</b> |  names ending the "s" are tables |


## Low-level utilities	

| What | Notes |
|:---|:---|
| <b>hint(s1:`str`, type) &rArr;  str</b> |  if we know a type, add to arg (else return arg) |
| <b>pretty(s:`str`) &rArr;  str</b> |  clean up the signature (no spaces, no local vars) |
| <b>optional(s:`str`) &rArr;  str</b> |  removes local vars, returns the rest as a string |
| <b>lines(sFilename:`str`,  fun:`fun`) &rArr;  nil</b> |  call `fun` on csv rows. |
| <b>dump() &rArr;  nil</b> |  if we have any tbl contents, print them then zap tbl |


## Main	

| What | Notes |
|:---|:---|
| <b>main(sFiles:`[str]`) &rArr;  nil</b> |  for all lines on command line, print doco to standard output |


