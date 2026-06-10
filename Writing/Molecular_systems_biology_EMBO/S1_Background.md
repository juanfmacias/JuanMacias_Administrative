# Overview
This section should describe the historical context of the transition from single reference genomes to pangenomes.
It should provide a philosophical overview of functional genomics and its relationship with pangenomes.
Finally, it should outline the objectives and structure of the review.

## Outline of section
- Definine functional genomics
  - types of genome function
- Explain the philosphy of how assays work
- Describe the reliance on a reference to reconstruct the functional landscape
- Address the flaws of the human genome reference and reference-based approaches
- Introduce the concept of a pangenome
- Set up the problem; which is how to perform functional genomics on a pangenome. Coined functional pangenomics

## Draft bits









--- BITS from benchmarking manuscript ---
traditionally relying on the human genome reference.

This reference has provided a framework for identifying, locating, and coordinating genes and genomic features, forming the foundation for modern human disease research.

However, three key limitations of this single genome reference obscure important aspects of genome biology.

First, the human genome reference, built from a small number of individuals, does not capture the genetic diversity across global populations.

Second, it is missing regions of the genome.

Finally, no single cell is fully represented by this reference.

This has created an urgent need for an updated and comprehensive genomic resource.

The Human Pangenome Reference Consortium (HPRC) addresses these limitations by creating a draft pangenome that integrates fully phased sequences from 47 individuals, including the complete CHM13 assembly19 and the hg38 reference.

All but the hg38 assembly have a corresponding and commercially available cell line.

It is hoped that this will provide a powerful, equitable, and inclusive resource for exploring the complexities of genomic landscapes.


Functional genomics, which studies the functions and interactions of genes and regulatory features, employs sequencing technologies such as ATAC-seq, RNA-seq, Hi-C, and WGBS to probe genomic function.

In these assays, DNA and RNA are fragmented, chemically sequenced, and mapped back to a genome, and the mapped reads are used to infer functional outputs such as gene expression, chromatin accessibility, chromatin interactions, and DNA methylation.


Mapping rate and read sequence content in libraries are also used to infer how well the assay was performed (QC metrics) and by extension how much confidence one can place in resulting functional estimates.

While the human genome reference has played a central role in these analyses, the extent to which reference genome choice (and degree of representativeness) impacts functional genomics analysis remains unclear.

In this study, we leverage fully phased genomes from five individuals to systematically quantify how reference genome choice (hg38, CHM13, Pangenome) versus personal genomes (maternal and paternal haplotypes) affects functional genomics results across ATAC-seq, RNA-seq, WGBS, and Hi-C assays (Figure 1).

These individuals were included in the draft pangenome.

Specifically, we evaluate the impact of reference choice on quality control metrics, read alignment, and functional outputs, and analyze how these effects vary locally and genome-wide.

Lastly, we investigate the non-uniform distribution of genome choice effects in regions with elevated genetic variation.

In summary, our study provides insights into the magnitude and variability of genome reference effects, offering guidance for researchers on selecting the most appropriate reference for functional genomics studies.


