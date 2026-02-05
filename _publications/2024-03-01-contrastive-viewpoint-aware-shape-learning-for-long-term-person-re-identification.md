---
title: Contrastive viewpoint-aware shape learning for long-term person re-identification
collection: publications
category: conferences
permalink: /publication/conferences/2024-03-01-contrastive-viewpoint-aware-shape-learning-for-long-term-person-re-identification
excerpt: 'This paper is about the number 1. The number 2 is left for future work.'
date: 2024-03-01
venue: 'WACV'
slidesurl: 
paperurl: 'https://openaccess.thecvf.com/content/WACV2024/papers/Nguyen_Contrastive_Viewpoint-Aware_Shape_Learning_for_Long-Term_Person_Re-Identification_WACV_2024_paper.pdf'
bibtexurl: 'http://jurgendn.github.io/files/files/contrastive-viewpoint-aware-shape-learning-for-long-term-person-re-identification.bib'
codeurl: 'https://github.com/jurgendn/CVSL_LReID/blob/main/README.md'
citation: 'V. D. Nguyen, K. Khaldi, D. Nguyen, P. Mantini, and S. Shah, “Contrastive viewpoint-aware shape learning for long-term person re-identification,” in Proc. IEEE/CVF Winter Conf. on Applications of Computer Vision (WACV), 2024, pp. 1030–1038, doi: 10.1109/WACV57701.2024.00108.'
---

This repository contains research code for **CVSL (Contrastive Viewpoint-aware Shape Learning)**, a Long-term Person Re-Identification (LRe-ID) method that improves robustness to **clothing changes** and **viewpoint variations** by combining appearance cues with texture-invariant body shape cues.

## Problem
Classic Re-ID methods rely on appearance. In long-term scenarios this breaks down when:

- the same person changes clothes / hairstyle, or their face is occluded;
- different people wear similar clothes.

In addition, viewpoint shifts (front/side/back) can cause both texture and shape embeddings to drift, creating false matches.

## Method: CVSL

CVSL has two feature branches and learns them with viewpoint-aware objectives.

1) Relational Shape Embedding (RSE) branch

- Extracts **2D pose keypoints** and encodes them as a graph.
- Uses a **refinement MLP** to lift raw joint coordinates to a higher-dimensional space.
- Uses a **Graph Attention Network (GAT)** over the skeleton graph to capture local part relations and higher-order shape structure.
- Produces a global **shape embedding** via global pooling.

2) Texture (appearance) branch

- Uses a CNN backbone (ResNet-50 in the paper) to extract appearance features.
- Uses clothing-aware objectives to discourage over-reliance on clothing texture.

3) Contrastive Viewpoint-aware Losses (CVL)

- **Shape CVL**: positive pairs are the same identity across different viewpoints; negatives are different identities under the same viewpoint.
- **Appearance CVL**: encourages cross-view consistency and includes a hard-mined component to handle look-alike clothing cases.

4) Adaptive Fusion Module (AFM)

Instead of naive concatenation, AFM projects shape/appearance features to a shared space and learns adaptive weights:

$$f = w^s \odot f^s + w^a \odot f^a$$

## Results (cloth-changing setting)

Reported in the paper:

- LTCC: Rank-1 44.5, mAP 21.3
- PRCC: Rank-1 57.5, mAP 56.9

## 📄 Citation

If you use this code in your research, please cite:

```bibtex
@InProceedings{Nguyen_2024_WACV,
    author    = {Vuong D. Nguyen, Khadija Khaldi, Dung Nguyen, Pranav Mantini, Shishir Shah},
    title     = {Contrastive Viewpoint-Aware Shape Learning for Long-Term Person Re-Identification},
    booktitle = {Proceedings of the IEEE/CVF Winter Conference on Applications of Computer Vision (WACV)},
    month     = {January},
    year      = {2024},
    url       = {https://openaccess.thecvf.com/content/WACV2024/html/Nguyen_Contrastive_Viewpoint-Aware_Shape_Learning_for_Long-Term_Person_Re-Identification_WACV_2024_paper.html}
}
```

**Paper Link**: [WACV 2024 Open Access](https://openaccess.thecvf.com/content/WACV2024/html/Nguyen_Contrastive_Viewpoint-Aware_Shape_Learning_for_Long-Term_Person_Re-Identification_WACV_2024_paper.html)

## 📜 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

**Keywords**: Person Re-identification, Long-term ReID, Cloth-changing, Pose estimation, Graph Neural Networks, Contrastive Learning
