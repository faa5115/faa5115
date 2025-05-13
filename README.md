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

Welcome to my research code repository. Although this work is grounded in medical imaging, the techniques implemented here reflect generalizable principles of signal processing, including phased-array signal reconstruction, spatial filtering, and inverse problem modeling. These approaches are directly relevant to applications such as radar imaging, sensor array processing, and beamforming.

## Overview
This repository contains GPU-accelerated and CPU-based implementations of:

Phased-array signal reconstruction, including stochastic matched filtering, spatial harmonic decomposition, and low-rank modeling

Bloch simulations for understanding MRI physics and RF signal behavior during acquisition

The code emphasizes physical modeling, time-domain and k-space analysis, and statistical recovery of signal under measurement and aliasing constraints. Several scripts offload computation to the GPU using MATLAB's gpuArray for performance.

## Folders
**reconstruction/** 
My implementations signal recovery from phased-array data.

Includes the following principles:
% matched filtering, stochastic matched filters, spatial harmonics, and low-rank recovery.
* *matched filtering* *
*   (SENSE in MRI terminology)
* *stochastic matched filtering * *
*    (Adaptive Coil Combine):  The same method as the matched filter reconstruction of SAR signal.  
* *Spatial Beamforming* *
*   I include a beamforming method used in MRI called Region Optimized Virtual Coils (ROVir).  I will later include a method I am working on publishing.  
* *Convolution Kernels to Estimate Fourier Spatial Harmonics (Done to reduce the sampling requirements needed in MRI)* *
*   In the MRI community, this includes methods such as SMASH, GRAPPA, SPIRiT, and our structured low rank matrix recovery method called UNCLE SAM.
* *The generation of phased array channel sensitivity maps by taking the eigenvalue decomposition of the convolution kernels* *
*   In MRI this is called * *E-SPIRiT* * 
* *The NUFFT and Gridding of non-uniformly sampled Fourier Coefficients* *

  
Emphasizes structured signal separation and efficient inverse solvers for high-dimensional data.

**flow_bSSFP_Bloch_Simulations/** 
Bloch simulations supporting my "Slice Encoding for the Reduction of Outflow Effects in bSSFP Imaging" paper.

Models flow dynamics and outflow-related artifacts in balanced steady-state sequences.

**spoiled_GRE_2D_ImageAcquisition/**
Simulates k-space acquisition in gradient recalled echo (GRE) imaging of digital phantoms.

Useful for understanding signal formation, phase behavior, and acquisition artifacts.

**blochSimulations/**
A teaching and research toolkit for visualizing core MRI signal phenomena:

* *Slice selection* *

* *Off-center excitation and the Fourier shift theorem* *

* *Phase encoding* *

* *K-space filling and trajectory effects* * 

* *Phase errors due to RF cycling mismatches in bSSFP* *

* Banding artifact formation* * 

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
