---
title: State Machines
pdf: markdeck-scaffold.pdf
slideNumber: true
controls: true
---

# State Machines
Gerardo Gonzalez

@fmizzell

<img src="assets/CA-full-RGB_red.svg" alt="CivicActions" width="25%"/>

#

<img src="assets/dkan-avatar-white.svg" alt="DKAN" width="30%"/>

And [non-standar CSVs](https://chriswarrick.com/blog/2017/04/07/csv-is-not-a-standard/)

# Theory of Computation

<small>
... is the branch that deals with how efficiently problems can be solved on a model of computation, using an algorithm.
</small> 

* automata theory and languages
* computability theory
* computational complexity theory

#

 <img src="assets/gottfried_leibniz.svg" alt="Gottfried Leibniz" width="50%" />

#  Entscheidungsproblem

#

<img src="assets/TuringInsp.svg" alt="Alan Turing" width="40%" />

#

<img src="assets/turing-machine.png" alt="Turing Machine" width="80%" />

# Halting Problem

#

<img src="assets/SM.svg" alt="State Machine #1" width="80%" />
<img src="assets/SM2.svg" alt="State Machine #2" width="80%" />

#

<img src="assets/turnstile.svg" alt="Turnstile State Machine" width="80%" />

# Back to CSV

#

<pre>
(?:(?:\r\n)?[ \t])*(?:(?:(?:[^()<>@,;:\\".\[\] \000-\031]+(?:(?:
(?:\r\n)?[ \t])+|\Z|(?=[\["()<>@,;:\\".\[\]]))|"(?:[^\"\r\\]|\\.
|(?:(?:\r\n)?[ \t]))*"(?:(?:\r\n)?[ \t])*)(?:\.(?:(?:\r\n)?[ \t]
)*(?:[^()<>@,;:\\".\[\]\000-\031]+(?:(?:(?:\r\n)?[ \t])+|\Z|(?=
[\["()<>@,;:\\".\[\]]))|"(?:[^\"\r\\]|\\.|(?:(?:\r\n)?[ \t]))*"
(?:(?:\r\n)?[ \t])*))*@(?:(?:\r\n)?[ \t])*(?:[^()<>@,;:\\".\[\] 
\000-\031]+(?:(?:(?:\r\n)?[ \t])+|\Z|(?=[\["()<>@,;:\\".\[\]]))|
\[([^\[\]\r\\]|\\.)*\](?:(?:\r\n)?[ \t])*)(?:\.(?:(?:\r\n)?[ \t]
)*(?:[^()<>@,;:\\".\[\]\000-\031]+(?:(?:(?:\r\n)?[ \t])+|\Z|(?=[
\["()<>@,;:\\".\[\]]))|\[([^\[\]\r\\]|\\.)*\](?:(?:\r\n)?[ \t])*)
)*|(?:[^()<>@,;:\\".\[\] \000-\031]+(?:(?:(?:\r\n)?[ \t])+|\Z|(?=
[\["()<>@,;:\\".\[\]]))|"(?:[^\"\r\\]|\\.|(?:(?:\r\n)?[ \t]))*"(
?:(?:\r\n)?[ \t])*)*\<(?:(?:\r\n)?[ \t])*(?:@(?:[^()<>@,;:\\".\[\]
\000-\031]+(?:(?:(?:\r\n)?[ \t])+|\Z|(?=[\["()<>@,;:\\".\[\]]))|
\[([^\[\]\r\\]|\\.)*\](?:(?:\r\n)?[ \t])*)(?:\.(?:(?:\r\n)?[ \t])*
(?:[^()<>@,;:\\".\[\] \000-\031]+(?:(?:(?:\r\n)?[ \t])+|\Z|(?=[\["
()<>@,;:\\".\[\]]))|\[([^\[\]\r\\]|\\.)*\](?:(?:\r\n)?[ \t])*))*(
?:,@(?:(?:\r\n)?[ \t])*(?:[^()<>@,;:\\".\[\] \000-\031]+(?:(?:(?:
\r\n)?[ \t])+|\Z|(?=[\["()<>@,;:\\".\[\]]))|\[([^\[\]\r\\]|\\.)*\]
(?:(?:\r\n)?[ \t])*)(?:\.(?:(?:\r\n)?[\t])*(?:[^()<>@,;:\\".\[\] 
\000-\031]+(?:(?:(?:\r\n)?[ \t])+|\Z|(?=[\["()<>@,;:\\".\[\]]))|\
[([^\[\]\r\\]|\\.)*\](?:(?:\r\n)?[ \t])*))*)*:(?:(?:\r\n)?[ \t])*)?
(?:[^()<>@,;:\\".\[\] \000-\031]+(?:(?:(?:\r\n)?[ \t])+|\Z|(?=[\["
()<>@,;:\\".\[\]]))|"(?:[^\"\r\\]| ...
</pre>

#

> Regular expressions describe regular languages

> A regular language can be defined as a language recognized by a finite automaton

#

<img src="assets/regularexpression.svg" alt="" width="40%" />

* a
* accccc
* ab
* abcc

#
<img src="assets/modernregex.svg" alt="" width="20%" />

* 1c
* 5bcc

<img src="assets/modernregexexpanded.svg" alt="" width="50%" />

#

<img src="assets/regexsm.svg" alt="" width="40%" />
<img src="assets/regularexpression.svg" alt="" width="20%" />

* accccc ,ab, abcc

# Back to CSV ... Again!

#

<pre>
first_name, last_name, stuff\n\r
    Gerardo     , "Gonzalez Calle ", \\ After spaces\\, yes!\n\r
Camila, """Awesomeness"" Gonzalez", Great\\\nEscape\n\r
</pre>

#

<img src="assets/fullcsvsm.svg" alt="" width="95%" />

#

<img src="assets/csvsm.svg" alt="" width="90%" />

#

```php
if ($endState == sm::STATE_RECORD_END) 
{
    $this->createNewRecord();
} 
elseif ($endState == sm::STATE_NEW_FIELD) 
{
    $this->createNewField();
} 
elseif (
  $endState == sm::STATE_CAPTURE || 
  $endState == sm::STATE_QUOTE_CAPTURE
) 
{
    $this->addCharToField($input);
}
```

#

```sql 
SELECT field1,field2 FROM blah;
```
```sql
SELECT * FROM blah;
```

#

<img src="assets/from.svg" alt="" width="70%" />

<img src="assets/var.svg" alt="" width="60%" />

#

<img src="assets/nested.svg" alt="" width="80%" />

# Takeaways

* State machines are simple but powerful
* Constraints can help simplify, and crystalize systems
* Validating, parsing, categorizing, control-systems 

# Recommendation

* !Implementation -> Mental exercise

# Resources

* [PHP State Machine Library](https://github.com/fmizzell/maquina)
* [State-Machine-Driven CSV Parser](https://github.com/getdkan/csv-parser)
* [JS State Machine Implementation](https://github.com/davidkpiano/xstate)
* [Debug Regular Expressions](https://regex101.com)
* [Diagrams as Text](http://plantuml.com/)
* [Diagrams as Test Editor](https://www.planttext.com)
* [Presentation as Text](https://github.com/arnehilmann/markdeck)

# Q&A
@fmizzell