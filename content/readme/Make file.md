
---
title: "Makefile"
date: 2020-11-19T12:20:06+02:00
draft: false
intro: "How to create and use Makefiles"
---

# Create Makefile

## Rule
The shape of a rule:
```
<target> : <dependency 1> <dependency 2>
	<command>
```

- `Target` can be a name of a file or action.
- `Dependency` is a file used as input to create the target. It can also be an action that will run before the command.
- `Command` is an action that make carries out. A rule may have more than one command, each on its own line. Please note: you need to put a tab character at the beginning of every command line! This is an obscurity that catches the unwary.

## .PHONY
"A phony target is one that is not really the name of a file; rather it is just a name for a recipe to be executed when you make an explicit request. There are two reasons to use a phony target: to avoid a conflict with a file of the same name, and to improve performance."

```
.PHONY: build
build:
	build stuff.js
```

## Variables
You can define variables as *recursively expanded variable* or *simply expanded variable*

Is recommended to use := because it will make the code more predictable and easier to understand.

### Recursively expanded variable =
The recursively expanded variable will expand everything every time it's called.

```
first = $(second)
second = $(last)
last = done

echo $(first) # done
```

### Simply expanded variable :=
Behaves more like a variable in any programming language. The simply expanded variable is only expanded when defined.

```
x := foo
y := $(x) bar
x := baz
```

Is the same as:
```
y := foo bar
x := baz
```

### Conditional variables ?=
A conditional variable will only be set if it's not yet defined.

```
VERSION?=1.0.0
```


## Links
- https://www.gnu.org/software/make/manual/html_node/
- http://web.mit.edu/gnu/doc/html/make_2.html