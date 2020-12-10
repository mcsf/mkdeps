mkdeps
======

Generate Makefile targets and dependencies based on C source files and their
`#include` guards. Written in AWK, because why not?

```sh
mkdeps *.c > Makefile
make
```

_or even_

```sh
make -f <(mkdeps *.c)
```


Example
-------

Given the following project:

```
main.c
types.h
utils.c
utils.h
```

`mkdeps *.c` will produce:

```
main: main.o utils.o 
utils.o: utils.h utils.c types.h 
main.o: types.h utils.h utils.c 
clean:
	rm *.o main
```
