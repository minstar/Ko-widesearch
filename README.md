# Ko-WideSearch

A Korean breadth-search benchmark for exhaustive set enumeration by web agents.

🔗 **Project page:** https://minstar.github.io/Ko-widesearch/
📄 **Paper:** [ko_widesearch.pdf](ko_widesearch.pdf)

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
