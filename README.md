# Min FreeCells

This is an attempt to get the minimum number of free cells to beat each of the million Microsoft deals. Currently it's just a list of proofs for each of the computations I've made so far, with a list coming later once I've finished running the solver on all million of them.

This is not an exact value, but an upper bound on the number of free cells. It's likely that the solver, especially for the iteration limit I set, has not found the actual minimums in all cases.

## How they were generated

The initial set of deals were generated using the excellent [FreeCell Solver](https://github.com/shlomif/fc-solve) program. It was used with the looking-glass algorithm and 200000 max iterations.

Specifically, the arguments used for the deal program were `-m -sn -l looking-glass -mi 200000` along with `--freecells-num {num}` for whichever one I was testing.

## Why

I want to have my in-development version of FreeCell have a mode where you can play with the lowest number of free cells possible.

## Misc

### Is this a good source of FreeCell solutions?

It is *a* source of FreeCell solutions, but since I was optimizing for number of free cells, they likely aren't optimal in terms of move count or intuitiveness. However, to my knowledge, this is the only source of solutions that has easy access online, so I guess it works OK at that. See [FreeCell game solutions](https://freecellgamesolutions.com/) if you just want an individual deal.

### Proof format

Each proof file (which doubles as a solution) has the number of free cells used, followed by a newline, followed by the solution in [standard notation](https://freecellgamesolutions.com/notation.html). Moves to foundations are always done explicitly. This is ideal for my purposes, as different programs have different ideas of what triggers an automatic move to the foundation. For instance, FreeCell game solution's solution to [game 1](https://freecellgamesolutions.com/ds/?g=1&v=All) automatically moves the 4 of hearts to the foundation, even though it's more than three above the diamond number in the foundation.

If you run into an issue verifying any of the games, keep in mind that running them with a different number of free cells other than the minimum specified can cause a verifier to become out of sync. This is because standard notation always assumes you move the maximum number of cards, which can differ based on the number of free cells.

## Thanks

This project literally would not have been possible without the scores of people who have a passion for FreeCell, especially those who spent the time making the open source solvers. This effort is just me burning some CPU cycles and putting the results online.
