# Project - Detecting electrode inversion in an ECG
The ECG is a time series that measures the electrical activity of the heart. This is the main tool to diagnose heart diseases. Recording an ECG is simple: 3 electrodes are placed at the ends of limbs, and 6 on the anterior chest.This generates 12 time series, called leads, each corresponding to a difference in potential between a pair of electrodes.

The electrodes' position is very important to correctly interpret the ECG. Making the mistake of inverting electrodes compromises interpretation, either because the leads do not explore the expected area (errors in the measures of hypertrophia indices, in the analysis of the ST segment), or because they generate false abnormalities (fake Q waves, error in the heart's axis...).

Inversion errors are frequent (5% of ECGs), and only experts (cardiologists) manage to detect them. But most ECGs are not interpreted by experts: only 30% are, the rest being interpreted by nurses or general practitioners. An algorithm for automatic detection of electrode inversion is therefore paramount to the correct interpretation of ECGs and would improve the quality of diagnosis.

This project is intended to make you detect electrode inversion in an ECG. The dataset at your disposal contains ECGs from a cardiology center. An ECG will be labeled as correctly realised (0) or as inverted (1). The goal is to perform binary classification on these ECGs.

## Inversions
Electrode inversions do not necessarily correspond to the inversion of only 2 leads:

Precordial leads from (V1, ..., V6) can indeed be inverted: V1 becomes V6, V2 becomes V5...
But when certain pairs of electrodes are exchanged, several leads from I, II, III, AVF, AVR, AVL can be modified differently. For instance, if electrodes of the right and left arms are inverted, then I becomes -I, II and III are inverted, AVL and AVR are inverted and AVF remains the same. Read here for more details on the relationships between the different leads and how they can be affected by inversion: https://litfl.com/ecg-limb-lead-reversal-ecg-library/

## Data
Data is available at the following link: https://drive.google.com/file/d/1tdjqbkRNqxfDdNbb6pXiX8DvCaFlMOjd/view?usp=sharing

In the archive, you will find:

input_training.npy
output_training.npy
input_test.npy
The training data contains 1400 ECGs and their labels. For each ECG, the data consists of 10 seconds of recording for 12 leads, each sampled at 250Hz. The channels of the samples are in the following order: I, II, III, AVF, AVL, AVR, V1, V2, V3, V4, V5, V5, V6

The testing data contains 2630 ECGs on which you will give your predictions at the end of the homework in a numpy array with a shape (2630,).

Each input file therefore contains the ECG signal in the form (n_ecgs, n_leads=12, n_samples=2500).

