# proxdd

**proxdd** is an open-source Prolog program for SICStus (4.2+) or Yap (6.2+) Prolog, implementing the SXDD algorithm for assumption-based argumentation (ABA) from the paper:

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[A generalised framework for dispute derivations in assumption-based argumentation](https://www.sciencedirect.com/science/article/pii/S0004370212001233).  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Francesca Toni. *Artificial Intelligence*, volume 195, 2013.

## Requirements

**abagraph** has been tested on Ubuntu Linux, with SICStus Prolog 4.2+ and yap Prolog (6.2+).

## Usage

Basic usage can be described as follows.

- After cloning the repository, `cd` to the `src/` directory.
- Load abagraph by `sicstus -l proxdd.pl`.
- ABA framework files are placed in `frameworks/`.  (This contains some examples.)
- To load a file from the `frameworks/` directory—such as `a12.pl`—do `loadf(a12).`.
- To find a derivation for, say, the sentence `y1`, do `sxdd(y1, X).`.

## Options

Current values of options are displayed by:

    ?- options.

To print the derivation steps during a call to `sxdd/2`, use:

    ?- set_verbose.

To hide the derivation steps (default), use:

    ?- set_quiet.

To output the solutions, as found, to a `.dot` file for visualization with `graphviz`, use:

    ?- set_print.

To set not to print, use:

    ?- set_noprint.

To use AB-dispute derivations, do:

    ?- set_ab.

To use GB-dispute derivations, do:

    ?- set_gb.

To change strategies, use:

    ?- set_strategies(StratList).

StratList has the form: `[T,PA,OA,PS,OS,PR]`.

- turn choice (`T`):

        p - proponent priority [DEFAULT]
        o - opponent priority

- argument choice (proponent `PA`, and opponent `OA`):

        n - newest
        o - oldest
        s - smallest unmarked support [DEFAULT (prop and opp)]
        l - largest unmarked support

- sentence choice (proponent `PS`, and opponent `OS`):

        n - newest
        o - oldest
        e - eager (choose an assumption if possible)
        p - patient (choose non-assumption if poss.) [DEFAULT (prop and opp)]

- proponent rule choice (`PR`):

        s - smallest rule body first