# Protein Secondary Structure Prediction with LSTM

This project explores the use of Long Short-Term Memory (LSTM) networks to predict the secondary structure of proteins from their amino acid sequences.

## Dataset

The project uses a combination of three datasets:

*   CB513: A common benchmark for protein secondary structure prediction.
    * Source: [https://www.kaggle.com/datasets/tamzidhasan/protein-secondary-structure-casp12-cb513-ts115](https://www.kaggle.com/datasets/tamzidhasan/protein-secondary-structure-casp12-cb513-ts115)
*   CASP12: A dataset from the Critical Assessment of protein Structure Prediction (CASP) experiment.
    * Source: [https://predictioncenter.org/casp12/](https://predictioncenter.org/casp12/)
*   TS115: Another dataset commonly used for protein secondary structure prediction.
    * Source: [https://www.kaggle.com/datasets/tamzidhasan/protein-secondary-structure-casp12-cb513-ts115](https://www.kaggle.com/datasets/tamzidhasan/protein-secondary-structure-casp12-cb513-ts115)

These datasets contain protein sequences and their corresponding secondary structure annotations, derived from 3D structures determined by X-ray crystallography or NMR. The secondary structure is typically assigned using the DSSP tool, which classifies each amino acid into one of eight states:

*   H: α-helix
*   B: β-bridge
*   E: β-strand
*   G: 3-helix
*   I: π-helix
*   T: Turn
*   S: Bend
*   C: Coil (loops and irregular elements)

For this project, the eight-state classification is simplified to a three-state classification:

*   H: Helix (includes G, H, I)
*   E: Sheet (includes B, E)
*   C: Coil (includes T, S, C)

## Model Evolution

The final model (Model 6) was the result of an iterative development process, starting with a baseline model (Model 1) and gradually incorporating improvements:

* Model 1: Baseline model with a simple sequential architecture (74% accuracy).
* Model 2: Increased model capacity and added a convolutional layer for feature extraction (81% accuracy).
* Model 3: Refined activation functions in the LSTM and Dense layers (81% accuracy).
* Model 4: Incorporated hydrogen bond potential as a feature and added a bidirectional LSTM layer (82% accuracy).
* Model 5: Increased the embedding dimensionality for richer representations (85% accuracy).
* Model 6: Added more data from the CASP12 and TS115 datasets to improve generalization (94% accuracy).

This step-by-step refinement led to significant gains in accuracy and demonstrates the importance of exploring different techniques for improving model performance.

## Model

The core model is a hybrid architecture combining:

*   Embedding layers: To represent amino acids and their physicochemical properties.
*   Convolutional layers: To capture local patterns in the sequence.
*   Bidirectional LSTM layers: To learn long-range dependencies and sequential information.
*   Dense layers: To output the final predictions.

## Feature Engineering

The model's performance was enhanced through feature engineering, including:

*   Hydrophobicity: The normalized average hydrophobicity scale (CIDH920105) from the AAindex database was used to represent the hydrophobicity of each amino acid.
    * Source: 
        * AAindex database: [https://www.genome.jp/aaindex/](https://www.genome.jp/aaindex/)
*   Hydrogen bond potential: A custom function was developed to estimate the potential for hydrogen bond formation between amino acids based on their sequence positions and types.

## Training

The model was trained using the Adam optimizer and categorical cross-entropy loss. Class weights were used to address class imbalance in the dataset. Early stopping was implemented to prevent overfitting.

## Evaluation

The final model was evaluated on a held-out test set and achieved an accuracy of 94%, demonstrating its effectiveness in predicting protein secondary structure.

## Importance and Applications

Protein secondary structure prediction is a fundamental task in bioinformatics with broad applications in:

*   Protein folding and stability analysis
*   Function prediction
*   Drug discovery and design
*   Understanding protein-protein interactions

This project demonstrates the effectiveness of deep learning, particularly LSTM networks, in accurately predicting protein secondary structure. The insights gained from this project can contribute to advancements in protein science and related fields.

## Key Achievements

*   Achieved 94% accuracy on the combined dataset.
*   Successfully incorporated hydrophobicity and hydrogen bond potential features.
*   Improved the model's ability to predict helix structures.
*   Demonstrated the effectiveness of LSTM networks for protein secondary structure prediction.
*   Showcased the benefits of data augmentation and feature engineering.

## Future work

*   Explore the use of Transformers to potentially further improve accuracy.
*   Experiment with different model architectures and hyperparameters.
*   Evaluate the model on additional protein datasets.
*   Develop a web application or tool to make the model accessible to other researchers.
