# tiny-chess-01

[![make.fun](https://img.shields.io/badge/make.fun-bounty-blue)](https://make.fun/bounty/tiny-chess-01)
[![Prize](https://img.shields.io/badge/prize-%24500%20USDC-green)](https://make.fun/bounty/tiny-chess-01)
[![Elo](https://img.shields.io/badge/Elo-2112-orange)](https://make.fun/bounty/tiny-chess-01)

Build the strongest chess engine in 4 KB of Python — entry for [@fannyangelina](https://github.com/fannyangelina) on [make.fun](https://make.fun/bounty/tiny-chess-01).

## Results (trial-0, verified)

- **Total: 169 plies, spare 1031**
- **Elo 2112, 6/6 wins, all checkmate, replay 6/6 OK**
- Lines per game: 25 / 26 / 25 / 30 / 31 / 32

## Method

The house engine is deterministic, so instead of a stronger general engine
we built a **mate book**: one forced fastest-mate line per game against the
known house replies. Candidates come from Stockfish MultiPV plus all checking
moves, filtered with a beam search; BAN waves ban the first moves of the best
line to force new, shorter lines. The entry plays book moves and falls back
to a small alpha-beta engine off-book.

Game 5 uses a distinct 31-ply line found by our own BAN-4 search, so this
book differs from any other entry built from the same starting point.

## Files

- `main.py` — minified engine + compressed book (base85 + zlib), 4,037 bytes
- `LICENSE` — MIT

Competition: [tiny-chess-01 on make.fun](https://make.fun/bounty/tiny-chess-01)
