# Neural network modelling of kinematic and dynamic features for signature verification

This repository contains the weights of a neural network model that estimates kinematic and dynamic features from online signature trajectories. The model is designed to mimic the capabilities of a UR5e robotic arm by using a multilayer perceptron (MLP)-based neural network to estimate angular positions, angular velocities, and force torques from the signature trajectory (x(t), y(t)).

The paper detailing this work is currently under review.

## Introduction

An online signature is typically represented by the parametric equations of its trajectory, denoted as (x(t), y(t)), which are captured when the signing tool contacts the digital surface. Signatures are a physiological biometric trait used in applications like access control, document forgery detection, and legal scenarios.

Since the execution of a signature inherently involves movements of the hand, arm, and forearm, these motions may contain kinematic and dynamic characteristics unique to the signer. Our work leverages this hypothesis by training an MLP-based neural network to estimate the kinematic and dynamic features, namely angular positions, angular velocities, and force torques.

## Dataset

The training data is derived from the MCYT330 dataset, which includes 16,500 online signatures. The dataset features the angular positions, angular velocities, and force torques recorded from a UR5e robotic arm during the execution of these signatures.

## Model

The model is an MLP-based neural network trained to estimate the kinematic and dynamic features of signatures. It takes the signature trajectory as input and outputs estimated features.

To address the inherent variability in signature lengths and styles, the model employs a sliding window approach that incorporates the coordinates of five preceding and succeeding points along with the current point. This technique enriches the input data with contextual information, enhancing the MLP's ability to capture the dynamics of signature movements.

The MLP architecture features a ReLU-activated hidden layer with twelve units, followed by a dropout layer with a 0.3 dropout rate to mitigate overfitting. The model is structured with three separate output heads, each comprising six units, to facilitate concurrent estimation of angular positions, velocities, and torques. The outputs are activated using the sigmoid function, ensuring they remain within the [0, 1] range, aligned with the normalization applied during preprocessing.

The model is trained using a composite loss function, which is the sum of mean squared error losses for each of the three output heads. This approach effectively balances simplicity and performance, enabling the model to generalize well across different datasets without the need for physical robotic systems, thus providing a cost-effective solution to estimating biomechanical features.

## Notebook description

The notebook includes steps for loading and preprocessing a sample of signature data, applying a sliding window approach to incorporate temporal context, and normalizing data with pre-fitted scalers. The notebook also provides visualizations of the estimated features, offering a flexible framework for analyzing biomechanical characteristics of signatures without requiring physical robotic systems.
