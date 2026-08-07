---
title: "Contrastive Viewpoint-Aware Shape Learning for Long-Term Person Re-Identification"
collection: projects
type: "Research project"
permalink: /research-project/cvsl-long-term-person-re-identification/
excerpt: "A WACV 2024 project on making person re-identification less dependent on clothing and more sensitive to stable body-shape cues."
date: 2024-03-01
---

## The question

Person re-identification asks whether two images captured by different cameras—or at different times—show the same person. That problem becomes much harder over the long term: clothing, hairstyle, and other appearance cues can change, while the camera viewpoint can make the same body look substantially different.

This project asks a simple question: **what can a model learn about identity when appearance is no longer reliable?**

The practical failure modes are easy to state. A person may appear in a different outfit, a face may be occluded, or two different people may wear similar clothes. A front-facing image and a side-view image of the same person can also have very different pixel-level appearances. A model that treats appearance as identity will therefore learn shortcuts that fail exactly when long-term matching matters.

## At a glance

- **Task:** long-term, cloth-changing person re-identification
- **Input:** RGB images together with 2D human-pose information
- **Core representation:** appearance features plus a graph-based body-shape embedding
- **Main mechanism:** viewpoint-aware contrastive learning
- **Venue:** IEEE/CVF Winter Conference on Applications of Computer Vision (WACV), 2024
- **Code:** [CVSL_LReID on GitHub](https://github.com/jurgendn/CVSL_LReID)

## The idea

Our paper, published at WACV 2024, proposes **Contrastive Viewpoint-aware Shape Learning (CVSL)**. The central idea is to combine two complementary signals:

- appearance features, which are informative but vulnerable to clothing changes;
- body-shape features extracted from 2D pose, which offer a more texture-invariant description of a person.

The shape branch represents the human skeleton as a graph and uses a Graph Attention Network to model relationships between body parts. We then use viewpoint-aware contrastive objectives to shape the embedding space: images of the same identity under different viewpoints should move closer, while different identities seen from a similar viewpoint should remain separable.

## How the model is organised

### 1. Relational Shape Embedding

The model first estimates 2D pose keypoints and treats the skeleton as a graph: joints are nodes, and anatomical relationships provide the edges. A refinement network maps the raw joint coordinates into a learned feature space. A Graph Attention Network then lets each body part aggregate information from related parts, so the representation can capture both local relationships and a global body configuration. Global pooling produces a shape embedding.

This design is useful because it makes the representation explicit. The model is not asked to discover body geometry only from texture; it receives a structured signal whose meaning is tied to the arrangement of body parts.

### 2. Appearance branch

The second branch extracts conventional visual features from the RGB image. In the paper, this branch uses a ResNet-50 backbone. Appearance remains valuable—it can distinguish people with similar silhouettes—but it is treated as one source of evidence rather than the whole identity representation.

### 3. Viewpoint-aware contrastive losses

The contrastive objectives encode the relationships that ordinary identity supervision misses:

- samples of the same identity under different viewpoints are treated as positives;
- samples of different identities under the same viewpoint are treated as negatives;
- hard cases with similar clothing receive additional pressure to remain separated.

In simplified form, the desired geometry is:

$$
\text{same identity} + \text{different viewpoint} \ \longrightarrow\ \text{closer},
$$

$$
\text{different identity} + \text{similar viewpoint} \ \longrightarrow\ \text{farther}.
$$

The important point is that viewpoint is not treated only as noise. It is used to decide which comparisons are informative during training.

### 4. Adaptive fusion

The shape and appearance embeddings are projected into a shared space and combined with learned, feature-wise weights. This allows the model to rely more on shape when clothing is misleading, while retaining appearance information when it is discriminative:

$$f = w^s \odot f^s + w^a \odot f^a.$$

## Evaluation

The paper evaluates the method on long-term, cloth-changing person Re-ID benchmarks, including LTCC and PRCC. The reported results are:

| Benchmark | Rank-1 | mAP |
| --- | ---: | ---: |
| LTCC | 44.5 | 21.3 |
| PRCC | 57.5 | 56.9 |

These numbers should be read in the setting defined by the paper—the cloth-changing evaluation protocols and splits—not as a claim that one score is universally comparable across all Re-ID benchmarks. The paper reports that CVSL improves on prior methods under these long-term conditions.

## What I learned from the project

The most important lesson was methodological: adding a structured module is not enough. The training objective has to express the invariance we care about. A pose graph can provide a useful inductive bias, but viewpoint-aware sampling and contrastive losses are what tell the model how identity should behave across observations.

That idea connects directly to my later work on graph partitioning and relational data. In both settings, the hard part is deciding which relationships are meaningful and which variation should not dominate the representation. The graph neural network is a tool; the research question is the invariance.

## Limitations and next questions

Pose-based shape cues are not a complete solution. They can be unreliable under occlusion, imperfect pose estimation, unusual poses, or low-quality images. Shape can also be insufficient when two people have similar body geometry. The method therefore still needs appearance features and a principled way to balance the two branches.

The natural next questions are whether richer temporal information, more robust pose estimation, or cross-modal cues can improve this balance—and how to evaluate identity stability without accidentally rewarding shortcuts from clothing or camera context.

## Why this project matters to me

CVSL is an early example of a research direction I keep returning to: use structure to separate stable information from misleading variation. Here, the structure is a human pose graph; the nuisance factors are clothing and viewpoint. The same pattern appears in my later work on graph partitioning and relational data—first identify what the representation should preserve, then design the learning objective around that invariance.

## Links

- [Read the paper]({{ page.paperurl | default: "https://openaccess.thecvf.com/content/WACV2024/papers/Nguyen_Contrastive_Viewpoint-Aware_Shape_Learning_for_Long-Term_Person_Re-Identification_WACV_2024_paper.pdf" }})
- [Code repository](https://github.com/jurgendn/CVSL_LReID)
- [Publication record](/publication/conferences/2024-03-01-contrastive-viewpoint-aware-shape-learning-for-long-term-person-re-identification)

## Citation

```bibtex
@InProceedings{Nguyen_2024_WACV,
  author    = {Vuong D. Nguyen and Khadija Khaldi and Dung Nguyen and Pranav Mantini and Shishir Shah},
  title     = {Contrastive Viewpoint-Aware Shape Learning for Long-Term Person Re-Identification},
  booktitle = {Proceedings of the IEEE/CVF Winter Conference on Applications of Computer Vision},
  year      = {2024}
}
```
