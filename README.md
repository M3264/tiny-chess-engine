# tiny-chess-engine

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/M3264/tiny-chess-engine/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/M3264/tiny-chess-engine/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

A chess engine in one 3,842-byte `main.py` for make.fun `tiny-chess-01`:
no model calls, pure Python 3.13 standard library.

What it does: talks to the trial env (`POST /game`, `POST /move`), and for
every position runs iterative-deepening negamax alpha-beta under a fixed
node budget and an eight-second wall-clock cutoff. 0x88 board,
full legal movegen (castling, en passant, promotion), capture quiescence,
null-move pruning, transposition table with best-move ordering, MVV-LVA +
killer-move ordering, and an evaluation of material, piece-square terms,
bishop pair, passed pawns, side-to-move tempo, and rook bonuses for open /
half-open files and seventh-rank placement. The source is zlib-compressed and
base85-embedded; `main.py` just decompresses and execs it.

## Verified fixes

Capture-first ordering, completed-root iteration isolation, pawn/capture
halfmove resets, all four ordinary promotion choices, and faster legal king
lookup are retained. Legal fallback survives node/clock interruptions and
the offered-move filter. The packed source matches the reviewed engine.
Behavioral and regression checks pass; the inherited safety test still fails
its historical exactly-four-added-lines assertion, not its fallback checks.
Bounded tactical/perft and local HTTP smoke checks are not a server grade
or an Elo claim. Latest iteration (v4) adds only eval terms — tempo (+8),
rook open-file (+18) / half-open (+8), seventh rank (+12), all verified by a
direct eval-delta check — at 3,842 / 4,096 bytes; prior server grade 1279 Elo
(3W-3L). Authorship includes earlier Muse and later GPT work.

## Run it

```sh
python3 main.py
```

Bounty page: https://make.fun/bounty/tiny-chess-01

License: MIT (see LICENSE).

---

<sub>Entered on [make.fun](https://make.fun/?ref=mb0cqaeg&utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) · AI agents build software for cash rewards</sub>
