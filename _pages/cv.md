---
layout: archive
title: "CV"
permalink: /cv/
author_profile: true
redirect_from:
  - /resume
---

Hanoi, Vietnam · (+84) 39-309-5502 · [dungnt.samihust@gmail.com](mailto:dungnt.samihust@gmail.com)<br>
[GitHub](https://github.com/jurgendn) · [Google Scholar](https://scholar.google.com/citations?user=PmUg7BkAAAAJ) · LinkedIn: [confirm] · ORCID: [confirm]

About Me
======

Mathematics and Informatics graduate from the HUST Talent Program with two peer-reviewed international publications in graph algorithms and representation learning: WACV 2024 (CORE A) and RIVF 2025. My research focuses on random-walk algorithms, stochastic processes on networks, and graph machine learning for dynamic systems, alongside five years of experience building production ML systems in banking and computer vision.

Research Interests
======

Random walks on graphs · stochastic processes on networks · dynamic and large-scale graph algorithms · graph neural networks · representation learning · computer vision · probabilistic modelling · machine learning for decision systems

Education
======

**Hanoi University of Science and Technology**, Hanoi, Vietnam<br>
**Bachelor in Mathematics and Informatics (Talent Program)**, 2017–2022<br>

- Talent Program context: K62 cohort of 21 students with a dedicated Mathematics–Informatics curriculum.
- GPA: 3.28/4.0 (8.2/10).
- Thesis: *Network Model and Risk Assessment for the COVID-19 Pandemic in Vietnam*. Grade: A. Bachelor of Science Research Project, 8 credits.
- Code: [covid19-risk-evaluation](https://github.com/jurgendn/covid19-risk-evaluation)
- Relevant courses: Numerical Analysis (A+), Optimization Methods (A), Data Structures and Algorithms (A), Computation Programming (A+), Stochastic Models and Applications (A), Programming Techniques (A+), Object-Oriented Programming (A+), Decision Support System (A+), System Analysis and Design (A).
- Additional coursework: Social Network Analysis (University of California, Davis); Deep Learning with PyTorch: Generative Adversarial Networks (Coursera); Neo4j Graph Academy series covering Fundamentals, Cypher, Graph Data Modeling, and Building Neo4j Applications with Python.

Research Experience
======

**Graph Community Detection for Dynamic and Large-Scale Graphs**<br>
Institute of Mathematics, Vietnam Academy of Science and Technology · Apr 2025–present (part-time)<br>
Supervisor: Assoc. Prof. Phan Thi Ha Duong

- Develop scalable community-detection methods for dynamic graphs with 50,000+ nodes, targeting runtime and partition quality.
- Implement and optimize DF-Louvain community detection, achieving a 15–30× runtime improvement with Numba.
- Implement the random-walk-based refinement code, contribute to a partial proof of the paper's separation theorem, and extend the argument to localize modularity change within a cluster; published at RIVF 2025.
- Build a graph-community benchmarking toolkit and optimized overlapping-modularity routines used in the RIVF 2025 experimental evaluation.

**Spam Detection over Telephony Networks using Graph Neural Networks**<br>
Faculty of Applied Mathematics and Informatics, Hanoi University of Science and Technology · Nov 2024–present (part-time)<br>
Supervisor: Assoc. Prof. Dr. Ngoc C. Le

- Develop graph-based methods to detect spam and fraud calls over telephony call-history graphs.
- Design topology-aware behavioural features that capture malicious calling patterns from network structure.
- Implement and benchmark graph neural network architectures against a prepared benchmark dataset and baseline suite. Ongoing research; dataset and manuscript are in preparation.

**Graph-Based COVID-19 Risk Assessment Model**<br>
National Steering Committee for COVID-19 Prevention and Control · 2021

- Built a Markov-chain random-walk model over approximately 10,600 administrative units of Vietnam, using 30,000 Monte Carlo simulations to estimate regional outbreak risk under uncertain patient mobility.
- Worked within the National Steering Team for COVID-19 Prevention and Control.
- Led an eight-student team constructing and maintaining the regional adjacency graph from public geographic data and local administrative changes.
- Processed and validated 10,000+ patient records and generated ward-level risk maps for response work during Vietnam’s fourth COVID-19 wave (Apr–Jul 2021).
- Recognition documented by a service card and a Certificate of Merit from the Executive Committee of the Hanoi Youth Union.
- Code: [covid19-risk-evaluation](https://github.com/jurgendn/covid19-risk-evaluation)

**Long-Term Person Re-Identification**<br>
Remote collaboration with University of Houston researchers · 2023–2024

- Joined the project as its first member and contributed to the graph-based gait/shape representation and fusion network for long-term person re-identification.
- Co-designed the viewpoint-aware contrastive loss to reduce identity variation across viewpoints; the work was published at WACV 2024 (CORE A).
- Implemented and maintained the public codebase in my personal GitHub repository, including repository architecture, configuration/factory system, skeleton-graph components, and MEBOW orientation integration.
- Code: [CVSL_LReID](https://github.com/jurgendn/CVSL_LReID)

**Poisson Hidden Markov Model for Overdispersed Count Data**<br>
School of Applied Mathematics and Informatics, HUST · 2020

- Developed a Poisson HMM with Baum–Welch/EM estimation, forward–backward algorithms, and Viterbi decoding for overdispersed NYC traffic-count data.
- Code: [GPD_HMM_MHNN](https://github.com/jurgendn/GPD_HMM_MHNN)

Work experience
======

**Senior Data Scientist**, Vietnam Technological and Commercial Joint Stock Bank (Techcombank), Hanoi · Apr 2026–present

- Develop recommendation models for the bank-wide Hyper Personalization program, supporting individualized product and content recommendations across retail customer touchpoints.
- Build signature-duplication detection for copy-paste and template-replication forgeries as part of an AI document-fraud pipeline spanning transaction records and contracts.

**Data Scientist**, Vietnam Joint Stock Commercial Bank for Industry and Trade (VietinBank), Dong Da, Hanoi · Mar 2025–Apr 2026

- Designed a graph-based recommendation system over corporate transaction networks using centrality and network-structure signals, increasing conversion rate from 0.7% to 3.21%.
- Built and maintained MLflow model tracking/registry and GPU-enabled Kubernetes MLOps infrastructure supporting internal ML workflows.

**Machine Learning Engineer**, VMO Holdings Technology Joint Stock Company, Cau Giay, Hanoi · Apr 2023–Sep 2024

- Fine-tuned BERT, T5, and GPT variants for conversation-quality assessment.
- Adapted LLaVA-style models with CLIP-ViT and Swin vision backbones for multimodal tasks.
- Engineered automated retraining and drift-detection pipelines, reducing forecast MAPE from 0.24 to 0.14.

**AI Engineer**, Grooo International Joint Stock Company, Cau Giay, Hanoi · Apr 2021–Apr 2023

- Built an end-to-end surveillance identity-matching pipeline using RetinaFace and vector databases, reaching 98% accuracy in internal evaluation.
- Developed eKYC components including OCR, face recognition, anti-spoofing, and graph-based document parsing.
- Implemented GNN-based telephony fraud detection with active learning and continuous graph updates, reaching 96% accuracy in internal evaluation.

Publications
======

<ul>{% for post in site.publications reversed %}
  {% include archive-single-cv.html %}
{% endfor %}</ul>

Google Scholar: 49 citations, h-index 1 (accessed 2026-05-15).

Selected Projects
======

- [Graph-Based Epidemic Model Simulation](https://github.com/jurgendn/epidemic_model_simulation)
- [Network Model for COVID-19 Risk Evaluation in Vietnam](https://github.com/jurgendn/covid19-risk-evaluation)
- [Poisson Hidden Markov Models for Overdispersed Counts](https://github.com/jurgendn/GPD_HMM_MHNN)
- [Contrastive Viewpoint-Aware Shape Learning for Long-Term Person Re-Identification](https://github.com/jurgendn/CVSL_LReID)
- [Random-Walk Graph Partitioning – Dynamic Frontier](https://github.com/jurgendn/RWGP-DF)

Teaching Experience
======

**Teaching Assistant** (part-time), PlusPlus Academy, Dong Da, Hanoi · Apr 2021–Oct 2021

- Taught Python data-science and machine-learning libraries, including NumPy, Pandas, Scikit-learn, PyTorch, and TensorFlow, to a class of 15 students for [confirm hours]/week.
- Guided students through algorithm implementation and evaluated final machine-learning and computer-vision projects.

Awards, Honors & Activities
======

- **Third Prize**, Vietnamese Mathematical Olympiad (VMO), 2017 — awarded by the Ministry of Education and Training. Nationwide competition among provincial selective teams; number of contestants/selection ratio: [confirm].
- **Champion**, MLOps Marathon, 2023 — national MLOps competition organized by Open Factor Foundation; grand prize: 100,000,000 VND, among 121 opening-phase entrants.
  - Designed the serving architecture for the five-person team: separated API and model-worker processes, added Redis caching, distributed inference with RabbitMQ and Celery, and optimized JSON serialization/deserialization for 95th-percentile latency targets.
  - Scoring combined model accuracy (45%), system performance (45%), and drift detection (10%) across three progressive data-challenge phases.
- **Third Prize**, 38th Student Scientific Research Conference, School of Applied Mathematics and Informatics, HUST, 2021.
- **Certificate of Merit**, Executive Committee of the Hanoi Youth Union, Decision No. 2244 QĐ/TĐTN-VP, 30 September 2021, for achievements in COVID-19 prevention and control in Hanoi.
- **First Prize**, Mathematical Modeling Competition, Vietnam Mathematical Society, 2016.
- **Third Prize**, International Mathematics Tournament of the Towns, 2016.
- **Certificate of Distinction**, American Mathematics Contest 12 (AMC 12), AIME Qualifier, Mathematical Association of America, 2016.
- **Third Prize**, Province-level Mathematics Competition for High School Students, 2015.
- Sacombank Scholarship for academic excellence in mathematics, 2016.

Service and Leadership
======

- Technical Program Committee reviewer, RIVF 2025 — reviewed four papers.
- Invited to reviewer pools of CVPR, ECCV, and NeurIPS 2026.
- Head of Academic Committee, Hanoi Mathematical Modeling, 2020 — led a 10-member team collaborating with university faculty on problem design for high-school mathematical-modelling outreach.

Technical Skills
======

- **Programming:** Python, C++
- **Machine learning:** PyTorch, PyTorch Geometric, PyTorch Lightning, Scikit-learn, Optuna
- **Methods:** graph algorithms, graph neural networks, stochastic processes, Markov chains, Monte Carlo simulation, hidden Markov models, optimization, computer vision, representation learning
- **MLOps and infrastructure:** Docker, Kubernetes, MLflow, RabbitMQ, Kafka, Git, Metabase
- **Databases and graph tools:** Neo4j, Qdrant, MongoDB, PostgreSQL, SQL Server, Redis
- **Spoken languages:** Vietnamese (native), English (IELTS 6.5)
