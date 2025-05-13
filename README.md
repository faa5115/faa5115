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
Bloch simulations supporting my "Slice Encoding for the Reduction of Outflow Effects in bSSFP Imaging" paper.

Models flow dynamics and outflow-related artifacts in balanced steady-state sequences.

**spoiled_GRE_2D_ImageAcquisition/**
Simulates k-space acquisition in gradient recalled echo (GRE) imaging of digital phantoms.

Useful for understanding signal formation, phase behavior, and acquisition artifacts.

**blochSimulations/**
A teaching and research toolkit for visualizing core MRI signal phenomena:

* *Slice selection* 

* *Off-center excitation and the Fourier shift theorem* 

* *Phase encoding* 

* *K-space filling and trajectory effects* 

* *Phase errors due to RF cycling mismatches in bSSFP* 

* Banding artifact formation*  

**uncle_sam_recon/**
Code supporting the UNCLE SAM paper (unfolding coil-localized errors via structured matrix modeling).

Includes reconstruction techniques for recovering clean images from aliased or distorted multichannel data.

## Relevance to Broader Signal Processing
While this codebase is specific to MRI, the principles are broadly applicable:

Multi-channel signal reconstruction

Beamforming and spatial filtering

Statistical inference from noisy, incomplete measurements

GPU-based acceleration of real-time pipelines

If you’re coming from radar, sonar, or other sensor array domains, you may find this work relevant for signal modeling, simulation, or algorithm development.

Feel free to explore and reach out with questions. This repository is a work in progress—additional reconstructions and simulation demos are being added.
