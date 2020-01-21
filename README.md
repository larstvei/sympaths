# SymPaths: Symbolic Execution Meets Partial Order Reduction

This is a Maude implementation of symbolic execution for a basic programming
language with concurrency and partial order reduction. To run the program, be
sure to have the [Maude system
installed](http://maude.cs.illinois.edu/w/index.php?title=Maude_download_and_installation)
first.

To get started, run:

```sh
$ maude testmod.maude
```

which loads the `testmod.maude` source, and provides a Maude prompt, and
should display something similar to:

```
		     \||||||||||||||||||/
		   --- Welcome to Maude ---
		     /||||||||||||||||||\
	   Maude 2.7.1 built: Jun 27 2016 16:43:23
	    Copyright 1997-2016 SRI International
		   Tue Jan 21 18:25:12 2020
Maude>
```

The Maude prompt accepts [Maude
commands](http://maude.cs.uiuc.edu/maude2-manual/html/maude-manualch18.html),
of which the perhaps most useful is `rew`. The following is an example of using
the `rew` command:

```
Maude> rew init((< 0 | 'y := 'x >, < 1 | 'z := 'x >, < 2 | 'x := 2 >)) .
```

The call corresponds to three threads, all of which are performing a single
assignment. The result is a set of symbolic search states, enumerating all the
non-equivalent symbolic executions of the program. Though there are six ways of
interleaving these processes in an execution, the program only outputs four, as
some are pruned away due to partial order reduction.

For more examples, look to the `tests.maude` file located in this directory.
