## Hi there 👋

<!--
**faa5115/faa5115** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->


# Signal Modeling and Reconstruction in MRI

Welcome to my research code repository. While these tools were developed for medical imaging, the underlying techniques are broadly applicable to signal processing domains such as radar imaging, sensor array processing, and spatial beamforming.

This work focuses on:

Phased-array signal reconstruction

Inverse problem modeling

Statistical recovery from noisy or incomplete measurements


## Overview
% This repository contains GPU-accelerated and CPU-based implementations of:
%
% Phased-array signal reconstruction, including stochastic matched filtering, spatial harmonic decomposition, and low-rank modeling
%
% Bloch simulations for understanding MRI physics and RF signal behavior during acquisition
% 
% The code emphasizes physical modeling, time-domain and k-space analysis, and statistical recovery of signal under measurement and aliasing constraints. Several scripts offload computation to the GPU using MATLAB's gpuArray for performance.

This repository contains GPU-accelerated and CPU-based implementations of:

 *  Phased-array signal reconstruction, including:

 *  Matched filtering

 *  Stochastic matched filtering

 *  Spatial harmonic decomposition

 *  Low-rank matrix recovery

 *  Bloch simulations for physical signal modeling and acquisition behavior

 *  Efficient solvers and spatial filters under measurement constraints (aliasing, undersampling)

Several scripts offload computation to the GPU using MATLAB’s gpuArray.



## Folder Structure
**reconstruction/** 
Signal recovery from multichannel (phased-array) data. Core techniques include:


% matched filtering, stochastic matched filters, spatial harmonics, and low-rank recovery.
* *matched filtering*  
  Equivalent to SENSE in MRI; functionally identical to traditional SAR matched filtering.
* *stochastic matched filtering * 
  Adaptive methods for reconstructing signals with unknown or spatially varying profiles. 
* *Spatial Beamforming* 
  Implements a technique called ROVir (Region-Optimized Virtual Coils), which spatially filters unwanted signals. A new beamforming method under development will also be added.
* *Convolution Kernels to Estimate Fourier Spatial Harmonics (Done to reduce the sampling requirements needed in MRI)* *
  Reduces sampling requirements using methods analogous to SAR spatial harmonics. Includes SMASH, GRAPPA, SPIRiT, and a structured low-rank matrix recovery method we call UNCLE SAM.
* *The generation of phased array channel sensitivity maps by taking the eigenvalue decomposition of the convolution kernels* *
  In MRI, this is known as ESPIRiT. We generalize this to extract fat-only vs. water-only sensitivity maps.


* *The NUFFT and Gridding of non-uniformly sampled Fourier Coefficients* *
  Tools for reconstructing signals from non-Cartesian (non-uniform) k-space sampling.

  
These tools emphasize spatial filtering, structured inverse solvers, and efficient modeling of high-dimensional sensor data.

**flow_bSSFP_Bloch_Simulations/** 
Simulations supporting the paper "Slice Encoding for the Reduction of Outflow Effects in bSSFP Imaging".

  * Models flow artifacts and signal loss due to out-of-plane motion.

  * Useful for understanding signal behavior in the presence of spatial misregistration.

**spoiled_GRE_2D_ImageAcquisition/**
Simulates 2D k-space acquisition of digital phantoms under gradient recalled echo (GRE) imaging.

  * Helps visualize signal formation, phase behavior, and sampling artifacts.



**blochSimulations/**
A modular Bloch simulator toolkit for visualizing core MRI physics. Topics include:

  * Slice selection and excitation profiles

  * Phase encoding and Fourier shift properties

  * K-space trajectory simulation

  * Signal dropout and banding from phase inconsistencies
**uncle_sam_recon/**
Implements the UNCLE SAM method (Unfolding Coil-Localized Errors via Structured Matrix Modeling).

  * Recovers high-fidelity images from aliased or corrupted multichannel data.

  * Applies low-rank matrix modeling to isolate useful signal components.
## Relevance to Broader Signal Processing
Although this codebase originates in MRI research, it applies to many sensor-driven imaging and signal reconstruction tasks:

 * Beamforming and spatial filtering

 * Multi-channel signal recovery under noise and aliasing

 * Statistical inference from partial or corrupted data

 * GPU-accelerated computation for real-time pipelines

Engineers working in radar, sonar, EEG/MEG, or other sensor-array domains may find these methods valuable for modeling, simulation, or algorithm prototyping.

Feel free to explore and reach out with questions. This repository is a work in progress — more simulations and reconstruction pipelines are being added.

