---
title: "Poisson Hidden Markov Models for Over-Dispersed Counts"
collection: projects
type: "Statistical modelling"
permalink: /research-project/poisson-hidden-markov-models-overdispersed-counts/
excerpt: "A thesis-backed implementation of Poisson Hidden Markov Models for discovering latent regimes in over-dispersed count time series."
date: 2020-07-06
---

## The question

A standard Poisson model assumes that the variance of a count series is equal to its mean. Real count data often violate that assumption: traffic counts, arrivals, incidents, and demand measurements can fluctuate much more than a single Poisson rate allows.

This project asks whether the extra variation can be explained by **latent regimes** rather than treated only as unexplained noise. The repository accompanies my report on using Poisson Hidden Markov Models (PHMMs) to model over-dispersed count time series.

## The central idea

A PHMM combines:

- a hidden Markov chain \\(S_t\\) describing the unobserved regime at time \\(t\\);
- a state-specific Poisson rate \\(\lambda_i\\) for each regime;
- transition probabilities that describe how regimes evolve over time.

Conditional on the hidden state, the observation is still Poisson:

$$Y_t \mid (S_t=i) \sim \operatorname{Poisson}(\lambda_i).$$

The marginal process can nevertheless be over-dispersed because it mixes multiple regimes with different rates:

$$
\operatorname{Var}(Y_t)
= \operatorname{E}[\lambda_{S_t}]
+ \operatorname{Var}(\lambda_{S_t}).
$$

The second term is the key. It represents variation caused by switching between latent low-, medium-, and high-intensity states.

## What the implementation does

The main script trains a family of models with different numbers of hidden states, then compares them rather than fixing the state count in advance. The pipeline is:

1. load a one-dimensional count series;
2. split it into training and test segments;
3. initialize and train PHMMs with \\(1,\ldots,m\\) states;
4. compute log-likelihood diagnostics and AIC/BIC;
5. decode the most likely hidden-state path with Viterbi;
6. visualize observed counts, fitted regime means, predictions, and state transitions;
7. report expected dwell times from the transition matrix.

The demo uses traffic-count data from NYC roadway sensors. The resulting hidden states can be read as traffic regimes with different expected count levels, rather than as directly observed labels.

## Inference in log-space

The core implementation in `HMM/PHMMs_fixed.py` uses the standard Hidden Markov Model algorithms, with the forward and backward recursions carried out in log-space for numerical stability. This avoids underflow when multiplying many small emission and transition probabilities over a long sequence.

Parameter estimation uses Baum–Welch, the EM procedure for HMMs. The expected state occupancies update the Poisson rates, while expected state-to-state transitions update the transition matrix. Viterbi decoding then gives a single most-likely regime path for interpretation and plotting.

## Choosing the number of regimes

The repository trains models across a range of state counts and reports both Akaike Information Criterion (AIC) and Bayesian Information Criterion (BIC):

$$
\operatorname{AIC}=2k-2\ell,
\qquad
\operatorname{BIC}=k\log T-2\ell,
$$

where \\(\ell\\) is the fitted log-likelihood, \\(T\\) is the number of observations, and the implementation uses a parameter count based on the transition matrix and Poisson rates.

The accompanying report finds that models with four to seven states fit the traffic series well, with a seven-state model offering a useful balance between likelihood, information criteria, and interpretability. That choice is a modelling judgement, not a universal rule: the right state count depends on the data, initialization, evaluation split, and the question the regimes are meant to answer.

## Regime duration

The transition matrix also provides an interpretable time-scale. If \\(A_{ii}\\) is the probability of remaining in state \\(i\\), the expected dwell time is:

$$
\operatorname{E}[\text{dwell}_i] = \frac{1}{1-A_{ii}}.
$$

This turns a fitted transition probability into a concrete diagnostic: how long does the model expect a regime to persist before switching?

## Why this project matters to me

This project is one of my early attempts to connect probabilistic modelling with a real operational signal. It taught me to distinguish an observed count from the latent process that might have generated it, and to use model selection as part of the analysis rather than as an afterthought.

It also shaped how I think about later graph and machine-learning work. A useful model is not only a fitting mechanism; it is a compact language for stating assumptions. Here, the assumptions are that regimes are discrete, transitions are Markovian, and counts are Poisson conditional on a regime.

## Limitations and next questions

The implementation is intentionally educational and is not optimized for very long sequences or large-scale batching. Its initialization is random, so repeated fits can produce different local solutions. The model also assumes that overdispersion is adequately explained by regime switching; a Negative Binomial model may be more appropriate when dispersion is not primarily driven by latent regimes.

Natural extensions include covariate-dependent transition probabilities, non-homogeneous rates, Bayesian uncertainty over the number of states, and direct comparisons with Negative Binomial HMMs, zero-inflated models, or self-exciting processes. Any such comparison should preserve a held-out evaluation protocol rather than selecting a model only by in-sample likelihood.

## Links

- [Code repository](https://github.com/jurgendn/GPD_HMM_MHNN)
- [English thesis](https://drive.google.com/file/d/15XYR4TT4UQZu7sOrZPtwQK_9iZoHkyvt/view?usp=sharing)
- [Vietnamese thesis](https://drive.google.com/file/d/14QrVjtIg8m-wlFeyTHPhPOZkppqYiUKN/view?usp=sharing)
- [Projects index](/research-projects/)
