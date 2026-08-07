---
title: "Network Model for COVID-19 Risk Evaluation in Vietnam"
collection: projects
type: "Epidemiological modelling"
permalink: /research-project/covid19-risk-evaluation-vietnam/
excerpt: "A network and random-walk model for turning recent COVID-19 case locations into daily, region-level risk estimates for Vietnam."
date: 2022-11-03
---

## The question

During an outbreak, a case count is only part of the picture. A newly reported patient is connected to a place, and places are connected to one another through movement, geography, and administrative structure. The question behind this project was:

**Can a network model turn recent case locations into a spatial risk signal that helps us see where exposure may diffuse next?**

This work became my thesis project, *Network Model and Its Application in Assessing Risk During the COVID-19 Pandemic in Vietnam*. The repository contains the research implementation of the core simulation pipeline.

## The modelling idea

The model represents administrative regions as nodes in a graph. The graph stores a transition-probability matrix that describes how a random walker can move from one region to another. Recent patient locations provide the starting points for the walkers.

For a target date, the pipeline:

1. selects patients reported within a recent time window;
2. maps their locations to graph nodes at commune, province, or Hanoi level;
3. starts random walks from those nodes;
4. aggregates the nodes visited by the walkers;
5. converts the visit distribution into a regional risk table for that date.

The result is not a deterministic forecast of infections. It is a graph-based exposure signal: regions receiving more simulated flow from recent case locations receive a larger relative risk score.

## From patient data to a risk table

The input patient workbook uses Vietnamese administrative fields such as:

- `Ngày công bố` — announcement or detection date;
- `MCB` — patient identifier;
- `Xã/Phường` — commune or ward;
- `Quận/Huyện` — district;
- `Tỉnh/TP` — province or municipality.

The loader filters patients by a configurable recency threshold. The main runner uses a seven-day window, so each target date is influenced by a moving set of recent cases rather than the entire historical record.

The graph can operate at multiple geographic resolutions. At commune level, a location is mapped from commune, district, and province; at province level, the province itself becomes the node. This makes the same modelling idea usable for a fine-grained local map or a coarser national view.

## The simulation

Let \\(G=(V,E,w)\\) be the region graph and let \\(W\\) be its transition-probability matrix. For each initial patient location, the simulator performs a walk of length \\(L\\) and records the visited nodes. Because a single walk is noisy, the model repeats the process \\(M\\) times and aggregates the outcomes:

$$
R = \frac{1}{M}\sum_{m=1}^{M} R_m.
$$

In the implementation, `walk_length` controls \\(L\\) and `max_iteration` controls \\(M\\). Walkers are processed in batches, and the simulation uses PyTorch tensors, with CUDA selected automatically when available. The post-processing step counts visits and writes one Excel file per date and epoch, with risk values scaled as a proportion per 10,000 visits.

## Engineering structure

The repository keeps the workflow small and inspectable:

- `main.py` selects the geographic mode, date range, graph, and output directory;
- `src/initial_parameters.py` loads patient records and maps locations to node IDs;
- `src/walk_model.py` performs batched random walks;
- `src/learner.py` runs the date-by-date and epoch-by-epoch loop;
- `src/post_process.py` turns simulated visits into Excel risk tables;
- `utils/aggregate/` and `utils/helpers/` prepare or validate input workbooks.

The graph itself is stored as a compressed pickle containing node mappings and a PyTorch transition matrix. The patient data and graph resources are intentionally supplied separately, which keeps sensitive inputs outside the public code repository.

## Why this project matters to me

This project is where my interest in graphs became an applied modelling workflow. Instead of treating a region as an isolated row in a table, the model makes relationships between regions part of the calculation. It also taught me to separate three things that are easy to conflate:

- the observed reports we have;
- the movement assumptions encoded by the graph;
- the uncertainty introduced by a stochastic simulation.

That distinction still shapes how I approach graph-based research. The algorithm is only one component. The important work is making the representation, assumptions, and output interpretation explicit enough that another person can challenge them.

## What the output means—and does not mean

The output is a relative, model-based risk score for each region and date. It should be interpreted alongside the input data, graph construction, reporting delays, and public-health context. It should not be read as an infection probability, a diagnosis, or a causal estimate of transmission.

The public repository does not include the patient workbook or graph resources required for a full historical run. That is an intentional boundary for the public artifact, but it also means that reproducing a particular historical output requires the corresponding input snapshot and graph definition.

## Limitations and next questions

The random walk is only as meaningful as its transition matrix. If the graph does not represent actual mobility or contact pathways, simulated movement can look precise while encoding the wrong mechanism. The current implementation also leaves the random walk stochastic without exposing a run seed in the main configuration, so exact reruns need additional reproducibility controls.

The next version I would want would make the graph provenance explicit, preserve the raw input snapshot and configuration with every output, quantify sensitivity to the recency window and walk length, and compare the risk signal against held-out reports. Those checks would turn a useful modelling prototype into a more defensible evaluation harness.

## Links

- [Code repository](https://github.com/jurgendn/covid19-risk-evaluation)
- [English thesis](https://drive.google.com/file/d/1VQl_iTkP2uwHm1d_90zPOdgP1nDTBx7K/view?usp=sharing)
- [Vietnamese thesis](https://drive.google.com/file/d/1yhuCP41ezmRUjhP2NvTANgm9kOBTl2LM/view?usp=sharing)
- [Projects index](/research-projects/)
