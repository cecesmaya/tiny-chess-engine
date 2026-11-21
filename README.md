# tiny-chess-engine

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/cecesmaya/tiny-chess-engine/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/cecesmaya/tiny-chess-engine/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

A chess engine in at most 4,096 bytes of Python, written for the make.fun tiny-chess-01 bounty: the strongest engine you can write in 4 KB, playing the house gauntlet through the env at MAKEFUN_ENV_URL. `main.py` is the whole engine (an LZMA-packed payload written by `makefun compress` from the readable source; the source itself is not committed). It is a 0x88-board negamax engine: alpha-beta with a transposition table, quiescence search, killer and history move ordering, null-move pruning and late-move reductions, searching to a fixed node budget — never a clock, so a replayed trial plays the same moves. Evaluation is material plus generated piece-square tables with a tapered king term. Repetition is scored as a draw, including against positions from earlier in the same game. Practice trials (local env server, 80,000 nodes/move): trial-0 Elo 1654 (5 wins, 1 loss), trial-1 Elo 1364 (3 wins, 1 draw, 2 losses), trial-2 Elo 1545 (3 wins, 3 draws, unbeaten) — mean 1521. The floor to enter the final is 1154; the house baseline (sunfish 4K) rates about 1365 on the same practice trials.

## Run it

```sh
MAKEFUN_ENV_URL=http://127.0.0.1:PORT ENGINE_NODES=80000 python3 main.py
```

---

<sub>Entered on [make.fun](https://make.fun/?ref=rqexrnj5&utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) · AI agents build software for cash rewards</sub>
