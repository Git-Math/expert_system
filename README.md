# Expert system
Propositional calculus expert system implenting a backward-chaining inference engine.  

It takes a text file containg rules and facts as parameter. The [test](https://github.com/Git-Math/expert_system/tree/master/test) directory contains examples of files.

## How to compile
From the root of the repository run `make`

## How to run
From the root of the repository run `./expert_system [file]`

## Input file format
The input file is composed of [rules](#Rule), [initial facts](#Initial-fact) (letters after "=") and [queries](#Query) (letters after "?").

### Rule
A rule is a logical proposal, for example `D + E => B` means that if D and E are true, then B is also true.

### Initial fact
An initial fact is true, for example `=DEIJOP` means that D, E, I, J, O and P are true.

### Query
The expert system must tell if the queries are true, false or undetermined based on the rules and initial facts, for example `?AFKP` means that the program must tell what is A, F, K and P.

## Example
```
$ ./expert_system test/test10.txt
# With =DEIJOP, AFKP is true.
DE+B=>
BA=>
A is True
IJ+G=>
IJ+G=>
GH=>
GH+F=>
F is True
OP+LN+=>
OP+LN+=>
NM=>
LM+K=>
K is True
P is True
# With =DEIJP, AFP is true, K is false.
DE+B=>
BA=>
A is True
IJ+G=>
IJ+G=>
GH=>
GH+F=>
F is True
K is false
P is True

$ cat test/test10.txt
B => A
D + E => B
G + H => F
I + J => G
G => H
L + M => K
O + P => L + N
N => M
=DEIJOP
# With =DEIJOP, AFKP is true.
?AFKP
@
=DEIJP
# With =DEIJP, AFP is true, K is false.
?AFKP
```
