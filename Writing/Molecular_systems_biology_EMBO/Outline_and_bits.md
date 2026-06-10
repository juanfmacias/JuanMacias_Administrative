# Overview

## Background
- Historical context: transition from single reference genomes to pangenomes.
- Definition and scope of the pangenome (and pan-epigenome?).
- Overview of functional genomics and its relationship with pangenomes.
- Objectives and structure of the review.

## Non-human pangenomes
- History of graph-based applications in non-human species.

## Advances Enabled by Pangenomes
- Enhanced Representation of Genetic Diversity
  - Inclusion of population-level variations.
  - Applications in understanding/capturing rare variants, structural variants, and their functional impacts.

- Insights into Evolutionary/adaptation processes {Garrison}
  - Comparative analysis across life histories/biogeographies.
  - Comparative analyses across species.
  - Evolutionary insights revealed by conserved and divergent regions.
  - Harmonized haplotypes and allelic diversity.

- Contributions to Transposable Element Research {Bourque, Groza, Xiaoyu}
  - Impacts of transposable elements on genomic architecture and function.
  - Role of pangenomes in elucidating transposable element dynamics.

## Computational Challenges and Innovations
- Data Structures and Visualization Tools
  - Current formats for pangenomes
  - Current tools for pangenome visualization
    - ODGI, Bandage, comparative genome browser?
  - Gaps and requirements for future developments.

- Scaling Analyses for Large datasets
  - Computational bottlenecks in data storage, analysis, and interpretation.

- Innovations in machine learning for pangenome applications.

## Functional Genomics Applications of the Pangenome
- Gene Expression Analysis
  - How pangenomic approaches improve differential expression studies.
  - Impacts of removing reference biases on detecting subtle expression changes.

- DNA Methylation Studies
  - Advancing understanding of epigenomic regulation in diverse populations.
  - Integration of methylation data with pangenomes to study regulatory differences.
  - Gaps

- Chromatin Accessibility and Topology
  - Applications in mapping chromatin structure and accessibility.
  - Role of pangenomes in enhancing Hi-C and ATAC-seq analyses.
  - Gaps

- Histone Modifications
  - Detecting variability in histone marks across populations.
  - Insights into gene regulation and chromatin state using pangenomic methods.
  - Gaps

- Addressing Diploid and Allelic Imbalance Analysis
  - Discuss how the pangenome natively supports diploid data analysis, enabling the detection of allelelic imbalance.
  - Explain how this is achieved in part by reducing or eliminating reference alignment biases.
  - Highlight implications for studying functional genomics in diverse populations and detecting subtle regulatory differences.
  - Gaps

## Biological Contexts for Immediate Benefits of Pangenomes
I want to talk about these, but I also don't want to give away too much of my work.

- Processes with Elevated Variation in Diverse Populations
  - Immune system diversity: Major Histocompatibility Complex (MHC) and immune gene clusters.
- Glia genes
- etc etc

- Disease Mechanisms
  - Cancer: Identification of structural variants in tumor genomes.
  - Neurodegenerative diseases
  - Infectious/immune diseases

- Evolutionary Mechanisms
  - Adaptive evolution in diverse environments (amylase gene duplications).

## Addressing Analytical and Coordinate System Challenges
- Linear Space vs. Graph Space Analysis
  - Comparison of returning to a common linear reference versus maintaining graph-based analysis.
  - Challenges of surjection: mapping data from graph-based representations back to a linear coordinate system.
  - Implications for tool development and standardization in handling surjection complexities.

- Coordinate System Variability
  - a large concern for people is whether the coordinate system will be stable across versions of the pangenome.

## Translational / therapeutic Implications (? - maybe beyond the scope of this review)
- Impacts on identifying/representing disease-linked regulatory elements.
- Potential for precision medicine applications.
- CRISPR precision and off-target effects.

## Ethical, Social, and Economic Considerations (? - maybe beyond the scope of this review)
  - Equity in resource allocation and population representation.
  - Implications for data sharing and privacy.

## Feasibility and Potential of a Human Pan-Epigenome
- Challenges in integrating epigenomic data across individuals and populations.
- Proposed methodologies and resources needed.
- Cost-benefit analysis of creating a pan-epigenome.

## Future Goals and Challenges
- Toward a Unified Framework for Pangenomics
  - Integrating pangenomes with functional and epigenomic datasets.

- Pangenome as a Resource and Methodological Paradigm
  - Acknowledge that the pangenome itself is a reference and will be used widely.
  - Discuss the future of per-individual assemblies as technology advances.
  - Emphasize how pangenomic methods will address the task of analyzing variable genomic landscapes across populations.
  - Highlight that the pangenome is both a resource and a new methodological paradigm that will outlive the resource itself.

## Conclusion
- Recap of how pangenomes advance the field of functional genomics.
- The Importance of Genome Representation:
  - Discuss the effects of genome reference choice on functional genomics analyses, particularly the biases introduced by incomplete or non-representative references.
  - Emphasize the benefits and complexities of using fully resolved assemblies in personalized genomics.
- Toward a New Computational Paradigm:
  - Highlight the need for novel tools to handle the variability in mappability landscapes across populations.
  - Reference current efforts, such as the HPRC, that are driving the development of methodologies suited to this paradigm.
- Addressing Challenges in Read Alignment:
  - Acknowledge the trade-off between higher alignment quality and slightly lower alignment rates in pangenome applications.
  - Note the importance of high-quality alignments for specific applications, such as estimating allelic imbalance.
- Inclusivity in Genomic Studies:
  - Stress the potential of the pangenome to study genetic diversity comprehensively, uncovering regions previously inaccessible (genetic "dark matter").
  - Advocate for the development of pangenomic tools that enhance accuracy.
  - Call to action for continued innovation and collaboration.
