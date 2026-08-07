---
title: "Graph-Based Epidemic Model Simulation"
collection: projects
type: "Epidemiological modelling"
permalink: /research-project/epidemic-model-simulation/
excerpt: "A graph-based prototype for representing epidemic relationships, ranking influential cases, and exploring outbreak structure interactively."
date: 2020-10-23
---

## The question

Compartmental models such as SI, SIR, and SEIR describe how populations move between broad epidemiological states. They are useful abstractions, but they can hide the relational structure of an outbreak: who was connected to whom, which cases shared a location, and which individuals sit at the centre of a transmission network.

This project explores a complementary question:

**Can an epidemic be represented as a changing influence network, and can graph metrics help identify the cases or regions that deserve attention?**

The repository accompanies the report *Mô phỏng mô hình lan truyền dịch bệnh* from the Applied Mathematics and Informatics programme at HUST.

## The graph representation

The model represents the outbreak as a graph \\(G=(V,E)\\). Patient cases become nodes with attributes such as age group, onset date, announcement date, and name. Edges represent known or hypothesised relationships between cases.

Location nodes can also connect otherwise fragmented patient-only components. This is important when two cases have no explicit direct relationship but share a ward, commune, or other environment. In the graph, that shared location becomes a way to represent indirect exposure rather than discarding it.

The processed relationship table contains fields for source case, target case, age group, onset date, announcement date, and relationship type. The pipeline then stores the graph in Neo4j or constructs an `igraph` representation directly from the CSV.

## The modelling idea from the report

The report proposes a daily weighted influence network. Edge weights are intended to vary with factors such as relationship strength, age-group mixing, interventions or media effects, and the time around symptom onset. When location nodes are used, the report also considers a short surface-survival window and an indirect-transmission decay factor.

For each day, PageRank is used to rank cases by their relative influence in the current network. The resulting score is not an infection probability. It is a graph-centrality signal that depends on the network definition and the weights assigned to its edges.

## What the repository implements

The current code provides an end-to-end prototype:

1. load a raw case CSV with Vietnamese epidemiological fields;
2. normalize announcement and onset dates, imputing missing onset dates with a configurable default offset;
3. convert case relationships into an edge list;
4. import nodes and typed relationships into Neo4j when database mode is enabled;
5. construct an `igraph` graph and compute PageRank, degree, betweenness, and closeness metrics;
6. detect graph clusters and generate a force-directed layout;
7. export nodes and edges to Sigma.js-style JSON;
8. explore the result in the browser-based visualization.

The main entry point is `src/main.py`, which supports processing, migration, analysis, or the full pipeline. The visualization stores node size as a scaled PageRank value and colors nodes by detected cluster, making high-centrality cases and network structure visible at a glance.

## Interactive exploration

The project includes a lightweight graph viewer under `visualization/`. It reads the exported `data.json`, lays out the network with a force simulation, and renders nodes and edges in the browser. That visual layer is useful for asking questions that a table can make difficult to see:

- Are cases concentrated in a few connected components?
- Which cases have unusually high centrality?
- Do clusters correspond to plausible social or location-based groupings?
- How sensitive is the interpretation to the chosen relationship graph?

The visualization is deliberately exploratory. It helps inspect a modelled network; it does not turn a centrality score into a clinical conclusion.

## Data handling and reproducibility

The repository keeps the raw case table, relationship table, graph database, and visualization as separate stages. It also supports Docker Compose for running Neo4j locally and environment variables for database credentials and input/output paths.

That separation is useful for research, but the public artifact still requires external input data and a running graph database for the full historical workflow. A reproducible run therefore needs the raw-data snapshot, the relationship-construction rules, the graph mode, and the exact analysis configuration—not only the visualization JSON.

## Why this project matters to me

This was an early project in which I treated epidemiological information as a relational system rather than only as a collection of time series. It connected applied mathematics, graph databases, network centrality, and interactive visualization in one workflow.

The project also shaped a caution that still matters in my work: a graph can make a hypothesis look concrete before the hypothesis has been validated. The most important question is not “which node is largest?” but “what does an edge mean, and what evidence supports its weight?”

## Limitations and next questions

The current repository should be read as research code and a visualization prototype. Several implementation choices limit direct epidemiological interpretation:

- the graph and edge weights depend on input assumptions;
- the current data-processing path assigns relationship labels stochastically rather than estimating them from validated evidence;
- the fallback graph calculator uses random edge weights;
- the report’s time-varying influence formulation is richer than the static prototype path;
- centrality is not the same as transmission probability, causal influence, or individual risk.

The next version I would want would make edge provenance explicit, remove placeholder randomness from the production path, preserve deterministic seeds and configuration receipts, and evaluate rankings against held-out epidemiological evidence. That would make it possible to distinguish a compelling network visualization from a validated risk-assessment method.

## Links

- [Code repository](https://github.com/jurgendn/epidemic_model_simulation)
- [Project report](https://drive.google.com/file/d/1xAvo7zwlBNHZxxsiwgL30FlB6OCQ5aU1/view?usp=sharing)
- [Projects index](/research-projects/)
