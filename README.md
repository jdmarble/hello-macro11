# Hello MACRO-11

"Hello, World!" in MACRO-11 assembly for the PDP-11.

Adapted from [Testprogram #1: "Hello, world" by Administrator](https://www.retrocmp.com/how-tos/interfacing-to-a-pdp-1105/146-interfacing-with-a-pdp-1105-test-programs-and-qhello-worldq).

## Regular Build

You'll need [`macro11`, `obj2bin.pl`](https://gitlab.com/Rhialto/macro11)
and [`simh`](https://opensimh.org) on your path.

```sh
macro11 -o hello.obj hello.mac
obj2bin.pl --binary --out hello.bin hello.obj
pdp11 hello.ini
```

## Docker Build

```sh
> docker run --rm --volume `pwd`:`pwd` --workdir `pwd` \
  ghcr.io/jdmarble/macro11-container:main macro11 -o hello.obj hello.mac
> docker run --rm --volume `pwd`:`pwd` --workdir `pwd` \
  ghcr.io/jdmarble/macro11-container:main obj2bin.pl --binary --out hello.bin hello.obj
> docker run --rm --volume `pwd`:`pwd` --workdir `pwd` \
  ghcr.io/jdmarble/pdp11-container:main hello.ini

PDP-11 simulator Open SIMH V4.1-0 Current        git commit id: c077c22d
Hello, world

HALT instruction, PC: 002030 (BR 2000)
Goodbye
```