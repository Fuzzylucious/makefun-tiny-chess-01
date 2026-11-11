# Tiny chess engine — 4 KB of Python

Entry for the [make.fun](https://make.fun) bounty
**"Build the strongest chess engine in 4 KB of Python"**
(`tiny-chess-01`, $500 prize pool, top 20 paid).

## What it does

`main.py` (4,081 bytes) is a complete chess engine that plays the
trial's 16 games through the env at `MAKEFUN_ENV_URL`: alpha-beta
search with a transposition table, killer moves, move ordering,
quiescence over captures/promotions and replies to check, and
iterative deepening capped at 30,000 nodes per depth. Evaluation is
material plus piece-square terms and a bishop-pair bonus. No model
calls, no clock in the search, no unseeded randomness — every move
derives from the position, the game history and the trial seed, so a
replay reproduces the trial move for move.

Board: 0x88, Zobrist hashing, repetition-aware. The packed source is
an LZMA payload decoded at startup; the engine itself is standard
library only and runs as `python3 -P -s main.py` on Python 3.13.

Practice trial-0 (kit's `grade-local`): Elo 1173, 5 wins / 0 draws /
11 losses, 411 plies to spare — above the live rank-20 paid
threshold of Elo 1090.

## License

MIT — see [LICENSE](LICENSE).
