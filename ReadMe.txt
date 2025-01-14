======================== DEDA-Fudan-Group2: Final Project ========================

Members (listed by division of labor): Wang Sukun, Huang Xiwen, Chen Zehao, Li Siyuan, Wang He

*==========================================================================
The data used in the project are all sourced from: Xiaojian Niu, Jiahao Gong, Sukun Wang, Haofan Qiang. Research on the Cascading Interdependent Mechanism of Upside and Downside Financial Risks across Stock and Bond Markets: Cascading Interdependent Multiplex Networks Approach from an Industry Perspective, 2024, Working Paper.

The project is divided into three parts, described as follows:

*--------------------------------------------------------------------------

1 Clustering (Path: FinalProject/1_Clustering)


1.1 Data Description

Entities: 29 industries (classified by Shenwan first-level industry categories);

Time and Frequency: January 9, 2009, to January 9, 2010 (late stage of the global financial crisis); weekly data.

Clustering metric: The total intensity of risk linkage for industry j, Risk_j. This is obtained by summing the risk contagion intensity (row j) and risk bearing intensity (column j) in the bond risk linkage network adjacency matrix. The adjacency matrix of the bond risk linkage network is calculated using the "Nonlinear Granger Causality Test Based on Leave-One-Out and Data Sharpening" on bond realized volatility (RV).


1.2 Clustering Methods

1.2.1 Spectral Clustering; Three display methods: Spectral clustering graph (graph_spectral_clustering.jpg); t-SNE graph (graph_tsne.jpg); UMAP graph (graph_umap.jpg)

1.2.2 Hierarchical Clustering One display method: Iris clustering tree (graph_iris_clustering.jpg)


1.3 Interpretation of Clustering Results

The specific industry name corresponding to each category's numerical label can be found in "result_clustering.txt" under Spectral Clustering Results and Hierarchical Clustering Results.

Industries in the same category exhibit more similar risk linkage characteristics, which may have economic significance (such as industries with similar characteristics, similar impacts from the global financial crisis, etc.).

*----------------------------------------------------------------------------

2 Minimum Spanning Tree (Path: FinalProject/2_MST)


2.1 Data Description

MST analyzes graphs composed of nodes and links.

Graph nodes: 58 nodes, representing 29 stock nodes and 29 bond nodes from different industries.

Graph links: The risk linkage intensity between different asset types within industries.

This section analyzes the risk linkage networks of the following four phases: Stock bull market (July 2014 - June 2015) Stock bear market (June 2015 - January 2016) Bond bull market (November 2013 - October 2016) Bond bear market (October 2016 - November 2017)


2.2 Minimum Spanning Tree Results

Image results: See “MST_vol_bad_stock_bull_nonlinear_network.jpg” and three other images.

Industry names: The industry names corresponding to node numbers in the images (in Chinese) can be found in “industry_mapping_rule.txt”; the industry names (in English) can be found in “label_vol_bad_bond_bear_nonlinear_network.txt”.

Result Interpretation: The minimum spanning tree retains the most critical part of the risk linkage network. If certain industries appear in all four phases, it indicates that these industries play an important role in risk linkage. Especially the industries occupying central positions, which highlights their critical status.

*-------------------------------------------------------------------------------

3 Machine Learning Prediction (Path: FinalProject/3_ML)


3.1 Data Description

Data structure: The downside risk linkage network in the stock market is represented by an adjacency matrix, composed of 29 industry stock asset nodes and their links.

Time and Frequency: June 5, 2008, to December 30, 2022, a total of 710 network adjacency matrices. Rolling window calculation is used, with a window of 250 days and a step size of one week (5 trading days).

Prediction approach: The following periods are designated as financial crisis periods, with the network characteristics during these periods labeled as 1, and those outside as 0. The model is trained to predict future financial crisis periods and evaluate its performance: (datetime(2007, 7, 26), datetime(2009, 12, 31)), # Global financial crisis (datetime(2013, 6, 7), datetime(2013, 12, 31)), # Bank liquidity crisis (datetime(2015, 6, 15), datetime(2016, 12, 20)) # Stock market crash


3.2 Training Settings

3.2.1 GNN Parameters

Hidden layers: hidden_channels=65; Classification types: num_classes=2; Node features: num_node_features=1; Link features: num_edge_features=1; Training iterations: epoch = 350.

3.2.2 Model Performance Metrics Prediction accuracy (higher is better), F1-score (higher is better), and F-Alarm (lower is better).


3.3 Training Process and Results

Training process accuracy time series graph: See “graph_accuracy_curve.jpg”.

Warning signal graph for the training set: See “graph_prediction_results.jpg”.

Sequential training results of Accuracy, F1-score, and F-Alarm: See “accuraciesGGNN.csv”.

*==================================================

The above is the description of all empirical work for the Final Project of Group2.

Authors: (Group Members) Wang Sukun, Huang Xiwen
