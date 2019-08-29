setwise
=======

`setwise` is a simple utility that performs set operations (INTERSECT, EXCEPT, UNION) on two sets of data.  It works upon simple text files.

Usage
-----

```
$ setwise
Usage: setwise [-i] <input-A> <intersect|union|except> <input-B>
       Each input must be either a file or '-' for STDIN.
       -i designates case-insensitive matching.
$ cat > foo
1
2
3
$ cat > bar
3
4
5
$ setwise foo intersect bar
3
$ setwise foo except bar
1
2
$ setwise bar except foo
4
5
$ setwise foo union bar
1
2
3
4
5
$
```

Be default it is case sensitive, but -i switch will undo that

```
$ cat > foo
Hello
World
$ cat > bar
hello
World
$ setwise foo intersect bar
World
$ setwise -i foo intersect bar
Hello
World
$
```

Caveats
-------

setwise works by loading everything into memory and working on it there.  So
large data sets will cause large memory usage.  There's no claim to efficiency
here, but on normal data sets, it works just fine.
