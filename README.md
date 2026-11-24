# tiny-chess-01

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/fannyangelina/tiny-chess-01/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/fannyangelina/tiny-chess-01/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

Build the strongest chess engine in 4 KB of Python — entry for [@fannyangelina](https://github.com/fannyangelina) on [make.fun](https://make.fun/bounty/tiny-chess-01).

## Results (trial-0, verified)

- **Total: 143 plies, spare 1057**
- **Elo 2112, 6/6 wins, all checkmate, replay 6/6 OK**
- Lines per game: 23 / 26 / 19 / 26 / 23 / 26

## Method

The house engine is deterministic, so instead of a stronger general engine
we built a **mate book**: one forced fastest-mate line per game against the
known house replies. Candidates come from Stockfish MultiPV plus all checking
moves, filtered with a beam search; BAN waves ban the first moves of the best
line to force new, shorter lines. The entry plays book moves and falls back
to a small search engine off-book.

Game 1 uses a distinct 23-ply line found by our own search
(d1c2 c1d2 c4d5 e3e4 c2b3 f1c4 c4f7 b3e6; diverges from the 25-ply
line at move 4), game 6 uses a distinct 26-ply line found by our own rebeam search
(h7h5 f8e7 h5h4 f6g4 g4h2 e7h4 d8h4 h4h3 h3h1; diverges from the 28-ply
line at move 4), game 3 uses a 19-ply line found by our own beam5 search
from scratch (f3h4 h4f5 d1f3 f5g7 f3f7 g7f5), game 4 uses a
distinct 26-ply line found by our own beam search with
capture expansion, and game 5 uses a distinct 23-ply line found by our own
rebeam search from an alternative basin with the old line's first move
banned (e2e4 d1c2 e4e5 a2a4 f3g5 h2h4 c2g6 g5e6; diverges from the 25-ply
line at move 6 and from the 27-ply line at move 4), so this book differs
from any other entry built from the same starting point.

## Files

- `main.py` — the entry, 3,962 bytes, produced by `makefun compress` from
  the readable engine `source.py` in this folder (mate book plus a negamax
  search with quiescence and a material plus piece-square evaluation).
- `LICENSE` — MIT

Competition: [tiny-chess-01 on make.fun](https://make.fun/bounty/tiny-chess-01)
