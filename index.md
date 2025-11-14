---
layout: default
title: Andrew Morgan - Statement of Purpose
---

# Statement of Purpose

### Andrew Morgan

How do galaxies evolve? This is one of the most fundamental, unanswered questions in astrophysics. While modern surveys like the Dark Energy Spectroscopic Instrument (DESI) provide an unprecedented volume of data, a fundamental gap remains: we can observe millions of individual galaxy "snapshots" in time, but we cannot watch a single galaxy evolve. We currently lack the tools to robustly connect these static snapshots into a dynamic, physical narrative of their life cycles.

My research aims to build these tools. I am an astrophysicist driven to solve this core scientific problem by developing and applying novel, physically-grounded machine learning frameworks. My goal is to create a new instrument that learns the continuous, probabilistic "flow" of galaxy evolution, allowing us to move beyond static catalogs and model the population dynamics of the cosmos.

As an NSF CosmicAI Grant research intern at NOIRLab, I have already built the foundation for this instrument. This two-tiered system consists of:

1.  **A "Teacher" Model:** A 190M-parameter transformer that fuses spectral data (processed with a robust, whitened-Gaussian smoothing method) with embeddings from the AION foundation model (Parker et al. 2025). It learns a physically-meaningful latent space by using a novel contrastive loss, which forces latent distances to mirror the true physical similarity of spectra, as defined by their Cross-Correlation Function (CCF).

2.  **A "Student" Model + Flow:** A lightweight "student" model distilled from the teacher, which feeds its embeddings into a redshift-conditioned Continuous Normalizing Flow (CNF). This system acts as a probabilistic "afterburner" for traditional pipelines, capable of identifying out-of-distribution spectra and improbable redshifts, a tool I am currently deploying to help validate DESI data.

This validated system is the first step toward my core PhD proposal: to build a full evolutionary model. This involves retraining the teacher on a unified dataset of real (DESI) and synthetic (TNG, FIRE) galaxies, using our CCF-based loss to create a shared latent space. I will then use advanced flow-matching techniques (designed to handle population "birth" and "death") to learn the three key components of galaxy dynamics: the average evolutionary path (drift), the population change rate (source/sink), and the stochastic "randomness" of their paths (diffusion).

My thesis will be a rigorous, two-stage validation of this model. First, I will test the "drift" and "source/sink" components directly against the ground-truth merger trees from cosmological simulations. Second, I will use the simulation analogs to calibrate the "diffusion" term, completing the full stochastic model. This provides the rigorous mathematical framework needed to formally solve for the "most probable path" a galaxy will take as it evolves.

This research plan is ambitious, but it is grounded in a mature, existing framework and a step-by-step validation plan. The final instrument will have broad, immediate applications for the community.

* **What are the true timescales for galaxy quenching?** By learning the "drift" and "source/sink" terms, we can create the first *empirically-driven* flux maps of populations moving between the main sequence, green valley, and quiescent states.

* **Where do hydrodynamic simulations fail?** This tool will also act as a "referee" by leveraging its unified (real + synthetic) latent space. It will provide direct, interpretable insight into the specific spectral features and *physical processes* (e.g., feedback, mergers) that current hydrodynamic models fail to reproduce, and identify simulated objects that real data suggests do not exist.

A more detailed technical description of the model architectures, mathematical frameworks (e.g., WFR Flow Matching, Freidlin-Wentzell formulation), and the two-stage validation plan is available on my [**Detailed Research Proposal page**](research).

My prior work demonstrates I can implement and validate large-scale machine-learning systems for astronomical data analysis. My proposed thesis couples a rigorous, testable hypothesis with a realistic path to community-ready tools. With the mentoring and domain expertise available in your program, I am to turn this framework into a widely-adopted instrument for studying galaxy evolution in the Rubin and DESI era.
