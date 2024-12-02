# Protein Secondary Structure Prediction with LSTM

This project explores the use of Long Short-Term Memory (LSTM) networks for protein secondary structure prediction. The goal is to develop a model that can accurately predict the secondary structure (helix, sheet, or coil) of a protein given its amino acid sequence.

## Dataset

The project initially used the CB513 dataset, a popular benchmark for protein secondary structure prediction. To improve performance, additional data from the CASP12 and TS115 datasets was incorporated, creating a larger and more diverse training set.

## Model

The core model is a hybrid architecture combining:

*   Embedding layers: To represent amino acids and their physicochemical properties.
*   Convolutional layers: To capture local patterns in the sequence.
*   Bidirectional LSTM layers: To learn long-range dependencies and sequential information.
*   Dense layers: To output the final predictions.

## Feature Engineering

The model's performance was enhanced through feature engineering, including:

*   Hydrophobicity: The Kyte-Doolittle hydrophobicity scale was used to represent the hydrophobicity of each amino acid.
*   Hydrogen bond potential: A custom function was developed to estimate the potential for hydrogen bond formation between amino acids based on their sequence positions and types.

## Training

The model was trained using the Adam optimizer and categorical cross-entropy loss. Class weights were used to address class imbalance in the dataset. Early stopping was implemented to prevent overfitting.

## Evaluation

The model was evaluated on a held-out test set and achieved an accuracy of 94%, demonstrating its effectiveness in predicting protein secondary structure.

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
