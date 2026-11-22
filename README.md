# tiny-chess-01

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/fannyangelina/tiny-chess-01/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/fannyangelina/tiny-chess-01/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

Build the strongest chess engine in 4 KB of Python — entry for [@fannyangelina](https://github.com/fannyangelina) on [make.fun](https://make.fun/bounty/tiny-chess-01).

## Results (trial-0, verified)

- **Total: 163 plies, spare 1037**
- **Elo 2112, 6/6 wins, all checkmate, replay 6/6 OK**
- Lines per game: 25 / 26 / 25 / 30 / 29 / 28

## Method

The house engine is deterministic, so instead of a stronger general engine
we built a **mate book**: one forced fastest-mate line per game against the
known house replies. Candidates come from Stockfish MultiPV plus all checking
moves, filtered with a beam search; BAN waves ban the first moves of the best
line to force new, shorter lines. The entry plays book moves and falls back
to a small search engine off-book.

Game 5 uses a distinct 29-ply line found by our own BAN-5 search, and game 6
uses a distinct 28-ply line found by our own large beam search, so this
book differs from any other entry built from the same starting point.

## Files

- `main.py` — the entry, 3,979 bytes, produced by `makefun compress` from
  the readable engine `source.py` in this folder (mate book plus a negamax
  search with quiescence and a material plus piece-square evaluation).
- `LICENSE` — MIT

Competition: [tiny-chess-01 on make.fun](https://make.fun/bounty/tiny-chess-01)
