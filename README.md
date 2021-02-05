### syntax for efficiently typing notes with relationships

notes are stored in a 3 column graph database

```
note | relationship | note
```

a colon separating 2 notes will add an implicit relationship between them

> color : red

```
color |  | red
red   |  |color
```

square brackets will add a 2 way relationship between 2 notes

> Ben [friends] Jacob

```
Ben   | friend | Jacob
Jacob | friend | Ben
```

the relationship itself is also a note, so it is still given relationships of it's own

```
Ben    | | friend
friend | | Ben
friend | | Jacob
Jacob  | | friend
```

parentheses will add a directional relationship between 2 notes

> Jacob (son of) Micheal

```
Jacob   | son of | Micheal
Micheal |        | Jacob
```

you can add a relationship, or another relationship to a note you've already written

> Micheal (father of) Jacob

```
Jacob   | son of    | Micheal
Micheal |           | Jacob
Micheal | father of | Jacob
```

multiple colons in a line can be used to link multiple notes at a time

> Jacob : programmer : coder

```
Jacob      | | programmer
Jacob      | | coder

programmer | | Jacob
programmer | | coder

coder      | | Jacob
coder      | | programer
```

a relationship can be written as a separate note to apply it to all notes in a line

> Assignment pt 1 : Assignment pt 2 : (due) 4/6/7

```
Assignment pt 1 |     | Assignment pt 2
Assignment pt 1 |     | due
Assignment pt 1 | due | 4/6/7 <---

Assignment pt 2 |     | Assignment pt 1
Assignment pt 2 |     | due
Assignment pt 2 | due | 4/6/7 <---
```

you can use multiple colons to represent depth of a relationship to limit it's reach

> color : red :: hot

```
color |  | red
red   |  | color

red   |  | hot <---
```

a more complex example

> heat the beaker to 70 degrees : (step) 5 : (part) a :: letter of alphabet

```
heat the beaker to 70 degrees |      | step
the beaker to 70 degrees      | step | 5
the beaker to 70 degrees      |      | part
heat the beaker to 70 degrees | part | a

step                          |      | heat the beaker to 70 degrees
step                          |      | 5
step                          |      | part
step                          |      | a

5                             |      | heat the beaker to 70 degrees
5                             |      | step
5                             | part | a

part                          |      | heat the beaker to 70 degrees
part                          |      | step
part                          | step | 5
part                          |      | a

a                             |      | heat the beaker to 70 degrees
a                             |      | step
a                             | step | 1
a                             |      | part
a                             |      | letter of alphabet
```
