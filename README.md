# tiny-chess-engine

A chess engine in at most 4,096 bytes of Python, written for the
[make.fun tiny-chess-01 bounty](https://make.fun/bounty/tiny-chess-01):
the strongest engine you can write in 4 KB, playing the house gauntlet
through the env at `MAKEFUN_ENV_URL`.

`main.py` is the whole engine (an LZMA-packed payload written by
`makefun compress` from the readable source; the source itself is not
committed). It is a 0x88-board negamax engine: alpha-beta with a
transposition table, quiescence search, killer and history move ordering,
null-move pruning and late-move reductions, searching to a fixed node
budget — never a clock, so a replayed trial plays the same moves.
Evaluation is material plus generated piece-square tables with a tapered
king term and the bishop pair, maintained incrementally on make/unmake.

Practice trials (local env server, 80,000 nodes/move): trial-0 Elo 1809
(5 wins, 1 draw), trial-1 and trial-2 to be added. The floor to enter the
final is 1154; the house baseline (sunfish 4K) rates about 1365 on the
same practice trials.

## Run it

    MAKEFUN_ENV_URL=http://127.0.0.1:PORT ENGINE_NODES=80000 python3 main.py

It plays every game the env serves and exits when the trial is done.

## License

MIT, see LICENSE.
