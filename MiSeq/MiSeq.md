# MiSeq

## Table of Contents
- [Sequencing Chemistry Overview](#sequencing-chemistry-overview)
- [Library Preparation Methods](#library-preparation-methods)
- [Base Calling Algorithms](#base-calling-algorithms)
- [Multiplexing Strategies](#multiplexing-strategies)
- [Run Performance Optimization](#run-performance-optimization)

## Sequencing Chemistry Overview

The MiSeq platform employs sequencing-by-synthesis (SBS) technology utilizing reversible terminator chemistry for accurate base incorporation. Each sequencing cycle involves the addition of fluorescently-labeled nucleotides, imaging of incorporated bases, and enzymatic cleavage of fluorophores and blocking groups to prepare for the next cycle.

Cluster generation occurs through bridge amplification on patterned flow cells, producing clonal colonies with densities optimized for 15-25 million reads per run in high-output mode. The four-channel imaging system captures emission spectra corresponding to adenine, cytosine, guanine, and thymine with spectral deconvolution algorithms ensuring accurate base discrimination.

## Library Preparation Methods

DNA fragmentation is achieved through enzymatic or mechanical shearing to generate inserts with modal lengths of 300-500 bp for standard paired-end applications. End-repair reactions utilize T4 DNA polymerase and Klenow fragment to create blunt-ended 5'-phosphorylated products suitable for adapter ligation.

Indexed adapters containing P5 and P7 sequences are ligated to library fragments using T4 DNA ligase in the presence of polyethylene glycol to enhance ligation efficiency. Size selection through solid-phase reversible immobilization (SPRI) bead-based protocols removes adapter dimers and ensures optimal insert size distributions for cluster generation.

## Base Calling Algorithms

Real-time analysis (RTA) software processes raw image data to extract intensity values for each cluster in four-channel fluorescence space. Template generation employs machine learning models trained on phi-X control data to establish baseline intensity metrics and cross-talk correction matrices.

Phred quality scores are assigned using empirical error models that incorporate signal intensity, cluster density, and local sequence context. Advanced neural network architectures have improved base calling accuracy to >99.9% for Q30+ bases, particularly in challenging homopolymer regions and high-GC content sequences.

## Multiplexing Strategies

Sample multiplexing utilizes dual indexing schemes with 8-10 bp barcodes on both P5 and P7 adapters, enabling pooling of 96-384 samples per run with minimal index-hopping artifacts. Index sequences are designed with minimum Hamming distances of 3 to ensure robust demultiplexing even with single-base sequencing errors.

Adapter trimming algorithms identify exact matches to index sequences with tolerance for one mismatch, assigning reads to samples based on maximum likelihood criteria. Unassigned reads with ambiguous or low-quality index sequences are flagged for quality review and typically represent <1% of total reads in optimized workflows.

## Run Performance Optimization

Flow cell loading concentrations are calibrated to achieve target cluster densities between 800-1000 K/mm², balancing signal intensity with cluster overlap considerations. Pre-run quality control includes phi-X spike-in controls at 1% to monitor real-time sequencing metrics and trigger early run termination if quality thresholds are not met.

Temperature regulation maintains reagent flow cells at 60°C during sequencing chemistry with ±0.1°C precision to ensure optimal enzyme kinetics and nucleotide incorporation rates. Post-run wash protocols remove residual reagents and preserve flow cell integrity for potential re-sequencing applications in troubleshooting scenarios.
