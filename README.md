Modularity on the Karate Club Graph

Course: DSC212: Graph Theory Module (Research Assignment) Name: N Javeed Akbar Roll No.: IMS25134

Overview

This repository contains a Jupyter/Colab notebook that implements recursive spectral modularity partitioning from scratch on Zachary's Karate Club graph (34 nodes, 78 edges). The method follows Newman (2006), Modularity and community structure in networks, PNAS 103(23):8577-8582.

Repository contents
File	Description
Karate_Modularity_Spectral.ipynb	Main notebook: code, outputs and visualizations
Karate_Modularity_Walkthrough.pdf	Printable walkthrough of the code and results (optional reference)
README.md	This file
How to run

Google Colab (recommended)

Open https://colab.research.google.com and choose File -> Upload notebook.
Upload Karate_Modularity_Spectral.ipynb.
Click Runtime -> Run all. No manual edits are needed.

Locally

bash
pip install numpy pandas matplotlib networkx jupyter
jupyter notebook Karate_Modularity_Spectral.ipynb

Only NumPy, pandas, Matplotlib and NetworkX are used.

What the notebook does
Builds the adjacency matrix A and modularity matrix B = A - k k^T / 2m, and numerically checks Propositions 1 and 2 (B is symmetric, B·1 = 0).
Implements the leading-eigenvector bisection and recursive bisection, stopping a community when its leading eigenvalue is non-positive.
Visualizes the graph after every split (fixed spring layout, one colour per community, node labels).
Computes degree, betweenness, closeness and clustering after every split with NetworkX, and plots their evolution per node (line plots and heatmaps).
Compares the first split with the real club split (Mr. Hi vs. Officer).
Extra samples: other graphs (Les Miserables, Florentine families, caveman, ring of cliques), a comparison with NetworkX greedy and Louvain, and a planted-partition (stochastic block model) experiment scored with the adjusted Rand index.
Short discussion of which nodes stay central and how community structure affects the metrics.
Key results (Karate Club)
The first split agrees with the real split for 33 of 34 members (only node 8 differs).
The recursion ends with 5 communities, final Q = 0.409.
Nodes 0 and 33 stay in the top 5 for degree, betweenness and closeness at every iteration.
Implementation notes
Unweighted graph: edge weights shipped with recent NetworkX versions are removed, so the graph matches the handout (0/1 adjacency, 78 edges).
Metrics per community: metrics are computed on the subgraph induced by each node's current community (iteration 0 = whole graph); otherwise they would not change across splits.
Handout vs. Newman variant: the default follows the handout (plain block of B). Newman's refinement (diagonal correction plus a check that Q increases) is also implemented for comparison.
Reference

M. E. J. Newman (2006). Modularity and community structure in networks. Proceedings of the National Academy of Sciences, 103(23), 8577-8582.
