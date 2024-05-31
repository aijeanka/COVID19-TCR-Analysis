# Prediction of SARS-COVID19 Severity Based on Graph-Based Features of T-Cell Receptors’ CDR3 Amino Acid Sequences

## Overview

This project focuses on predicting the severity of COVID-19 by analyzing T-cell receptor (TCR) sequences using graph-based feature extraction methods. The study leverages the diversity and specificity of the complementarity determining region 3 (CDR3) in TCR sequences and employs computational tools like LZGraph to capture intricate patterns within the TCR repertoire.

## Table of Contents
1. [Introduction](#introduction)
2. [Methods](#methods)
3. [Results](#results)
4. [Discussion](#discussion)
5. [Conclusion](#conclusion)
6. [Future Work](#future-work)

## Introduction

### Translating Biological Data into Clinical Outcomes

Precision medicine aims to use individual patient data to gain insights into the roots of health problems, enabling personalized treatment plans. Understanding the severity of COVID-19 is crucial as it impacts patient hospitalizations and mortality.

### Why TCR Sequences?

TCRs play a critical role in the immune response by recognizing antigens presented by infected cells. The CDR3 loop in TCRs is highly variable and essential for antigen binding, making it a key focus for this study.

### Computational Approach: LZGraph

LZGraph is used to create graphs where nodes represent unique sequences (clonotypes) and edges represent similarities or functional relationships. Centralities like eigenvector centrality measure the influence of nodes within the network, providing insights into the structural dynamics of TCR sequences.

### Objective and Dataset Selection

The project aims to predict COVID-19 severity by analyzing TCR sequences using a graph-based feature extraction method. Initially, a small dataset was used, but it was later expanded to include 270 patients from a larger study.

## Methods

### Data Collection and Preprocessing

- **Data Source:** Datasets were obtained from the ImmPort portal and a subsequent study including patient ID, CDR3 sequences for both alpha and beta chains, gene information, clonotype, disease condition, sex, age, and race.
- **Data Cleaning:** Prefixes like "TRA:" and "TRB:" were removed from sequences, and missing values were handled appropriately.
- **Normalization and Clustering:** The 'Clone size' column was normalized, and K-means clustering was applied.

### Feature Extraction and Graph Construction

- **Graph-Based Feature Extraction:** Used LZGraph to construct graphs from beta sequences, calculating key metrics like eigenvector centrality.
- **K1000 Diversity Index:** Computed to quantify the diversity of TCR sequences.
- **Graph Visualization:** Visualized the structural arrangement of TCR sequences using NetworkX.

### Comprehensive Analysis for All Patients

- Iterative analysis was performed for all patients, calculating centrality measures and voterank scores, and merging these with clinical data to create a comprehensive dataset.

## Results

### Model Performance on TCR Beta Sequences

- **RandomForestClassifier:** Achieved a test accuracy of 0.56.
- **BalancedRandomForestClassifier:** Test accuracy of 0.52, slightly better at identifying severe cases.
- **GradientBoostingClassifier:** Test accuracy of 0.54.
- **KNeighborsClassifier:** Lowest performance with a test accuracy of 0.37.
- **StackingClassifier:** Combined multiple models, achieving a test accuracy of 0.57.
- **XGBClassifier:** Highest test accuracy of 0.59.

### Model Performance on Combined Alpha and Beta Sequences

- **RandomForestClassifier:** Test accuracy of 0.56.
- **BalancedRandomForestClassifier:** Test accuracy of 0.52.
- **GradientBoostingClassifier:** Test accuracy of 0.54.
- **KNeighborsClassifier:** Test accuracy of 0.37.
- **StackingClassifier:** Test accuracy of 0.57.
- **XGBClassifier:** Highest test accuracy of 0.59.

## Discussion

- The XGBClassifier consistently outperformed other models, demonstrating superior accuracy and robustness.
- The addition of alpha sequences did not significantly enhance most models' performance, indicating beta sequences alone might be sufficient for effective classification.

## Conclusion

- The XGBClassifier was the most effective model for predicting COVID-19 severity based on TCR sequences.
- Other models showed moderate performance, with KNeighborsClassifier being the least effective.

## Future Work

- **Feature Engineering:** Investigate additional techniques to extract more discriminative features.
- **Advanced Algorithms:** Explore deep learning techniques like CNNs or RNNs.
- **Data Augmentation:** Implement data augmentation techniques.
- **Model Ensembling:** Investigate more sophisticated ensembling techniques.
- **Hyperparameter Tuning:** Conduct extensive hyperparameter tuning.
- **Cross-Validation:** Employ more robust cross-validation strategies.
- **Class Imbalance:** Continue to address class imbalance through advanced techniques.
- **External Validation:** Validate models on external datasets.
- **Utilize AAPLZGraph and Clinical Data:** Integrate AAPLZGraph with clinical data for enhanced feature sets.
