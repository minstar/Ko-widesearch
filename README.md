# Ko-WideSearch

A Korean breadth-search benchmark for exhaustive set enumeration by web agents.

🔗 **Project page:** https://minstar.github.io/Ko-widesearch/
📄 **Paper:** https://arxiv.org/abs/2606.27595

## TL;DR

Web-agent benchmarks overwhelmingly measure *depth* — pinning one obscure answer behind a
chain of constraints. **Ko-WideSearch** measures *breadth*: list **every** member of a closed
set (a TV season, a dynasty, a league, an administrative region, an election) and fill each
item's attribute table. Graded by Item-, Column- and Row-F1.

**228 gold tables · 14,560 attribute cells · 16 categories · 190 entities · 12 web agents.**

## Key findings

- **Sets, not rows.** Every agent recovers membership far better than complete rows — best
  Item-F1 **92.8** vs best Row-F1 **53.7**. The loss is at the cell level.
- **Harder knobs, lower scores.** Row-F1 falls monotonically Easy → Medium → Hard as table
  width and a 2-D composite key are dialed up.
- **More search ≠ better.** The heaviest searchers score lowest; effort does not buy completeness.
- **Spend ≠ completeness.** Frontier costs ~10× the best open model for +9 Row-F1.
- **Korean specialists don't close the gap** — A.X-4.0, Solar-Open-2 and K-EXAONE-236B all land
  at or below the open-weight floor.
- **Finding > formatting.** Free-text and enum cells fail most; dates and names come out right.

## Analysis highlights

- **Where the gap comes from.** Column-F1 by cell type: date **58**, name **56**, number **55**,
  enum **51**, free-text **49** — the bottleneck is finding/normalizing values, not formatting.
- **Membership is balanced.** Item precision ≈ recall (e.g. GPT-5.5 P85/R86) — agents neither
  systematically hallucinate nor drop members; the loss is entirely at the cell level (Row P≈R≈25–37).
- **Big sets aren't the problem.** Pooled Row-F1 is roughly flat across set size (33.8 / 30.7 / 36.9).
- **The gap is broad.** Pooled Row-F1 clusters at 0.28–0.49 across well-sampled categories; Sports
  (the largest, n=80) sits mid-pack at 0.31.
- **Errors are substantive.** After a normalization-aware judge credits transliteration/granularity
  variants, the residual wrong cells are wrong entities, wrong regions, wrong values — not formatting noise.
- **Cost.** Per task, frontier ≈ $0.82–0.87 vs DeepSeek-V4-Pro $0.23 (the Pareto value winner, Row 45.0).

## Release

The pipeline and scorer are open (MIT). The **gold evaluation data is gated** — shared on
request rather than posted on the open web, so a live-web agent cannot search up and copy the
answers (following GAIA and BrowseComp). See the paper for the request process.

## Citation

```bibtex
@inproceedings{jeong2026kowidesearch,
  title     = {Ko-WideSearch: A Korean Breadth-Search Benchmark
               for Exhaustive Set Enumeration by Web Agents},
  author    = {Jeong, Minbyul},
  year      = {2026},
  note      = {Upstage AI},
  url       = {https://github.com/minstar/Ko-widesearch}
}
```
