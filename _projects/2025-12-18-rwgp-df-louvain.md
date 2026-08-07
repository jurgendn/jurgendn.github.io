---
title: "Random-Walk Refinement for Dynamic Community Detection"
collection: projects
type: "Graph algorithms"
permalink: /research-project/rwgp-df-louvain/
excerpt: "A RIVF 2025 project extending Dynamic Frontier Louvain with a local random-walk refinement for recovering community splits after graph updates."
date: 2025-12-18
---

## The question

Community-detection algorithms for dynamic graphs should update a partition without recomputing it from scratch after every edge change. Dynamic Frontier Louvain (DF-Louvain) does this by restricting local moves to an affected frontier. This is efficient, but deletions inside a community can create a different kind of change: one community may need to split.

This project asks: **can a local random walk identify plausible splits while preserving the efficiency and modularity objective of DF-Louvain?**

## At a glance

- **Problem:** community detection on evolving graphs
- **Baseline:** Dynamic Frontier Louvain
- **Extension:** random-walk graph-partition refinement
- **Decision rule:** accept a proposed split only when it improves modularity
- **Venue:** 2025 RIVF International Conference on Computing and Communication Technologies
- **Code:** [RWGP-DF on GitHub](https://github.com/jurgendn/RWGP-DF)

## The method

For each batch of edge insertions and deletions, RWGP-DF first runs the ordinary frontier update. It then identifies communities affected by internal edge deletions and applies a refinement only within those candidates.

For a candidate-community subgraph with adjacency matrix \(A\) and degree matrix \(D\), the random walk uses

$$
P=D^{-1}A.
$$

Starting from a source vertex, a short walk produces a distribution \(p^{(t)}\). Comparing this distribution with the subgraph's stationary distribution provides a proposed bisection. The algorithm accepts that proposal only when the corresponding modularity change is positive and both parts satisfy the minimum-size constraints.

This design keeps the expensive work localized: only communities implicated by the update are examined, and an exploratory random walk does not change the partition unless it improves the objective.

## My contribution

I implemented and optimized the research code for the DF-Louvain baseline and the random-walk refinement. I also contributed to part of the separation-theorem proof and developed a generalization that localizes the modularity-change argument within a candidate cluster.

The implementation includes temporal graph loaders, dynamic-community baselines, multiple refinement variants, benchmark scripts, and experiment tracking. Optimizing the DF-Louvain implementation with Numba produced a 15–30× runtime improvement in our experimental workflow.

## Why this project matters to me

This work connects the three parts of my research direction directly: graph structure, evolving systems, and stochastic processes. The random walk is not used as a decorative model component; it proposes a structural change that is checked against an explicit graph objective.

It also illustrates the kind of applied-mathematics research I want to pursue: identify a concrete limitation in an algorithm, characterize when it matters, derive a local decision rule, and evaluate the resulting method under realistic graph updates.

## Scope and limitations

RWGP-DF is research code rather than a general-purpose production library. Its behavior depends on how temporal updates are constructed, which communities are selected for refinement, the random-walk length, and the modularity resolution. A positive modularity change also does not by itself establish that a partition matches external ground truth.

The next questions are how to characterize the conditions under which the refinement recovers a meaningful split, how sensitive it is to update ordering and parameter choices, and how its runtime-quality trade-off changes across larger and more heterogeneous dynamic graphs.

## Links

- [Paper DOI](https://doi.org/10.1109/RIVF68649.2025.11365046)
- [Code repository](https://github.com/jurgendn/RWGP-DF)
- [Publication record](/publication/conferences/2025-12-26-rwgp-df-louvain)

## Citation

D. H. Do, D. Nguyen, and T. H. D. Phan, “Improving the DF-Louvain algorithm through random walk-based refinement,” in *Proc. 2025 RIVF International Conference on Computing and Communication Technologies (RIVF)*, Ho Chi Minh City, Vietnam, 2025, pp. 932–937, doi: 10.1109/RIVF68649.2025.11365046.
