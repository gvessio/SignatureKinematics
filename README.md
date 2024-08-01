# Neural network modelling of kinematic and dynamic features for signature verification

This repository contains the weights of a neural network model that estimates kinematic and dynamic features from online signature trajectories. The model is designed to mimic the capabilities of a UR5e robotic arm by using a multilayer perceptron neural network to estimate angular positions, angular velocities, and force torques from the signature trajectory (x(t), y(t)).

The paper detailing this work is currently under review.

## Introduction

An online signature is typically represented by the parametric equations of its trajectory, denoted as \((x(t), y(t))\), which are captured when the signing tool contacts the digital surface. Signatures are a physiological biometric trait used in applications like access control, document forgery detection, and legal scenarios.

Since the execution of a signature inherently involves movements of the hand, arm, and forearm, these motions may contain kinematic and dynamic characteristics unique to the signer. Our work leverages this hypothesis by training an MLP-based neural network to estimate the kinematic and dynamic features, namely angular positions \(\theta(t)\), angular velocities \(\omega(t)\), and force torques \(\tau(t)\).

## Dataset

The training data is derived from the MCYT330 dataset, which includes 16,500 online signatures. The dataset features the angular positions, angular velocities, and force torques recorded from a UR5e robotic arm during the execution of these signatures.

## Model

The model is an MLP-based neural network trained to estimate the kinematic and dynamic features of signatures. It takes the signature trajectory \((x(t), y(t))\) as input and outputs estimated features \((\hat{\theta}(t), \hat{\omega}(t), \hat{\tau}(t))\).

## Notebook description

The notebook includes steps for loading and preprocessing a sample of signature data, applying a sliding window approach to incorporate temporal context, and normalizing data with pre-fitted scalers. The notebook also provides visualizations of the estimated features, offering a flexible framework for analyzing biomechanical characteristics of signatures without requiring physical robotic systems.
