---
category: dev
tags:
  - VB.Net
date: 2021-01-22
title: Should probably be a warning?
vssue: false
---

Should probably be a Warning not a Note?

<!-- more -->

## There's a slight problem with this code

I had a bug in some code which just didn't make any sense. The snippet below recreates it, but its not immediately obvious.

```vbnet
Sub Main()
    Dim items = New Integer() {1, 2, 3, 4}
    For Each item In items
        Dim count As Integer
        count += 1
        Console.WriteLine(count)
    Next
    Console.ReadLine()
End Sub
```

What would you expect the output to be?

1

1

1

1

Nope. It's

1

2

3

4

But are we not declaring the count variable in the For Each block? Well, now that you mention that, there's this note in the VB.Net documentation:

> Even if the scope of a variable is limited to a block, its lifetime is still that of the entire procedure. If you enter the block more than once during the procedure, each block variable retains its previous value. To avoid unexpected results in such a case, it is wise to initialize block variables at the beginning of the block.

There must be a really good reason for this, though I think should probably be a warning, not a note. To resolve, set the variable to an initial value.

```vbnet
Dim count As Integer = 0
```
