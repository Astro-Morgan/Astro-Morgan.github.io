---
layout: default
title: Detailed Research Proposal
---

# Detailed Research Proposal: AEON-Flow Framework

This page provides the technical supplement to my main Statement of Purpose, detailing the specific model architectures, mathematical frameworks, and validation stages of my proposed doctoral research.

## Tier 1: The 'Aristotle'+'Kanon Flow' Anomaly Detection Instrument

The foundation of the entire framework is the high-fidelity, 190M-parameter teacher model, 'Plato'. This is a multi-headed pooling transformer designed to fuse two data modalities:

AION Embeddings: High-level, 768-dimensional sequence embeddings from the Polymathic-AI AION foundation model (Parker et al. 2025).

Denoised Spectra: 1D spectral data, pre-processed using our Whitened-Gaussian method and passed through a 1D CNN encoder.

The 'Plato' model's 32-dimensional latent space is engineered to be physically meaningful by using a triplet ordinal contrastive loss. This loss function forces latent-space distances to mirror the physical similarity of spectra, as defined by their Cross-Correlation Function (CCF), implicitly encoding both spectral and redshift transitional information.

This powerful latent space serves the first tier, my current production-scale tool: the 'Aristotle'+'Kanon Flow' system.

'Aristotle' is a lightweight (48M-parameter) "student" model, distilled from 'Plato'. It functions as a fast and efficient embedding tool.

'Kanon Flow' is a redshift-conditioned Continuous Normalizing Flow (CNF) trained on 'Aristotle's latent space.

This system serves as a probabilistic "afterburner" for traditional template-fitting pipelines (e.g., Redrock). By adapting the proven autoencoder+flow architecture for anomaly detection, it can robustly identify improbable redshifts and novel spectral anomalies by assigning a precise log-likelihood to any given spectrum.

## Tier 2: PhD Core Proposal — The 'Panta Rhei' Evolutionary Model

This validated 'Aristotle'+'Kanon Flow' framework serves as the foundation for the second tier of my project and the core of my PhD: the scientific instrument 'Panta Rhei'.

To build this, the 'Plato' teacher model will be retrained on a combined dataset of real (DESI) and synthetic (TNG, FIRE, etc.) galaxies. The CCF-based triplet ordinal contrastive loss is the key to this; it provides a principled and robust method to unify both domains into a single, shared latent space by forcing latent distances to mirror physical similarity, not pixel-level artifacts.

'Panta Rhei' will be this retrained 'Plato' model's own evolutionary flow network. However, to physically model population dynamics, a standard flow is insufficient. The model must account for the "birth" of new populations (formation) and the "death" of old ones (quenching). This 'source/sink' problem is a known challenge in trajectory inference. Therefore, 'Panta Rhei' must be trained using the state-of-the-art Wasserstein-Fisher-Rao (WFR) Flow Matching framework, which is designed specifically to learn these unbalanced dynamics. This adapts the 'trajectory inference' methodology from cell microbiology by learning two coupled functions:

A drift $f(\phi,z)$ (the 'average' evolutionary path)

A source/sink term $g(\phi,z)$ (population birth/death)

#### The Full Stochastic Model and Validation

The path of an individual galaxy, however, is governed by the full Stochastic Differential Equation (SDE):

$$d\phi = f(\phi,z)dz + \sigma(\phi,z)dW$$

where $\sigma(\phi,z)$ is the diffusion term that quantifies the unbiased, mean-zero stochasticity. This SDE is the complete physical model, and calibrating all its components ($f$, $g$, and $\sigma$) is the ultimate objective.

Having this full SDE allows us to move beyond simple trajectory inference and apply the rigorous mathematics of large deviation theory, specifically the Freidlin-Wentzell formulation. This framework provides the Onsager-Machlup action functional, a foundational tool from 1950s statistical physics that formally defines and solves for the "most probable path" an object will take through a stochastic state space. My proposed thesis is therefore a two-stage validation and calibration of this full framework, designed to build and test this action functional against cosmological simulations.

### Stage 1: Deterministic Validation

The first stage is a pure validation of the deterministic WFR-FM core. I will train on the full simulation snapshot data to learn $f_{\text{model}}$ and $g_{\text{model}}$. I will then validate this by comparing them against the ground-truth $f_{\text{sim}}$ (mean path) and $g_{\text{sim}}$ (source/sink rate) measured directly from the simulation merger trees. This "pure math" test validates the core method.

### Stage 2: Stochastic Calibration

The second, more advanced stage is to empirically calibrate the stochastic component, $\sigma(\phi,z)$. To do this, I will leverage the unified latent space by forming an observationally-matched simulation sub-sample through nearest-neighbor matching to the real DESI data. I will then use this simulation analog sample to measure the local scatter (the variance) of individual galaxy paths around the now-validated deterministic flow $f$. This will provide the first data-driven calibration for $\sigma(\phi,z)$, allowing for a full, probabilistic application of the Freidlin-Wentzell formulation to galaxy evolution.
