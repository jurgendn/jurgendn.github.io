---
title: "Improving the DF-Louvain Algorithm through Random Walk-Based Refinement"
collection: publications
category: conferences
permalink: /publication/conferences/2025-12-26-rwgp-df-louvain
excerpt: 'RWGP-DF augments Dynamic Frontier Louvain with a local random-walk refinement that proposes community splits after structural changes and accepts them when modularity improves.'
date: 2025-12-18
venue: '2025 RIVF International Conference on Computing and Communication Technologies'
paperurl: 'https://doi.org/10.1109/RIVF68649.2025.11365046'
codeurl: 'https://github.com/jurgendn/RWGP-DF'
citation: 'D. H. Do, D. Nguyen, and T. H. D. Phan, “Improving the DF-Louvain algorithm through random walk-based refinement,” in Proc. 2025 RIVF International Conference on Computing and Communication Technologies (RIVF), Ho Chi Minh City, Vietnam, 2025, pp. 932–937, doi: 10.1109/RIVF68649.2025.11365046.'
---

Dynamic Frontier Louvain updates communities efficiently by restricting local moves to nodes affected by graph changes. This work adds a random-walk refinement for cases in which deleted internal edges weaken a community enough that it should be split.

The refinement proposes a binary partition within an affected community and accepts it only when the modularity change is positive. This preserves the local-update motivation of DF-Louvain while adding a mechanism for recovering community splits.

[Project overview](/research-project/rwgp-df-louvain/) · [Code](https://github.com/jurgendn/RWGP-DF) · [DOI](https://doi.org/10.1109/RIVF68649.2025.11365046)
