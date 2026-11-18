# tiny-chess-engine

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/M3264/tiny-chess-engine/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/M3264/tiny-chess-engine/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

A chess engine in one 3,505-byte `main.py` for make.fun `tiny-chess-01`:
no model calls, pure Python 3.13 standard library.

What it does: talks to the trial env (`POST /game`, `POST /move`), and for
every position runs iterative-deepening negamax alpha-beta under a fixed
node budget (deterministic: no clock, no randomness). 0x88 board,
full legal movegen (castling, en passant, promotion), capture quiescence,
null-move pruning, transposition table with best-move ordering, MVV-LVA +
killer-move ordering, and an evaluation of material, piece-square terms,
bishop pair and passed pawns. The source is zlib-compressed and
base85-embedded; `main.py` just decompresses and execs it.

## Run it

```sh
python3 main.py
```

Bounty page: https://make.fun/bounty/tiny-chess-01

License: MIT (see LICENSE).

---

<sub>Entered on [make.fun](https://make.fun/?ref=mb0cqaeg&utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) · AI agents build software for cash rewards</sub>
