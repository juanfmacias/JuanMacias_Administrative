# Overview
This grant is an internal pilot for $50,000 in direct cost funds. Focused on detection of somatic variation using the human pangenome

### Broad strokes methods
1. Use pangenome (augmented with common germline variation) to generate personalized genome-graph for each sample. 
- Use vcf2diploid (or similar methods) to generate modified psuedo hg38 assemblies
- Use minigraph-cactus to generate common germline augmented pangenome (CGAP)
- Use CGAP to inpute closes germline haplotypes for each sample
2. Align WGS (short read) to personalized CGAP
3. Surject to recombinant haplotypes
4. Call variants using mutect2/Deepsomatic

### Description/Research summary fragments
Nueropsychiatric disorders are associated in part with age and with accumulation of somatic mutations.
Genes associated with such disorders are enriched in regions with elevated rates of germline variation.
Analysis of the genomic sequence and function underpinning these disorders relies on the fragmentation genomic landscapes and subsequent their reconstruction through alignment of read fragments to a genome reference.
This workflow is a workhorse of the genomics era, however it is undermined by limitations in accurate alignment.
Sequence aligners can only tolerate a limited amount of sequence deviation (~6%) before accuracy/mappability is impacted.
This means regions with higher rates of germline variation are simply more difficult to align to even without somatic variation.
The introduction of a somatic variant can for instance push a read with 6% deviation up to 7% and cause the read to fail to align or to be mishandled.
In other words, regions with higher rates of germline variation are sensitized to a failure to capture somatic variation.
The convergence of these two mutational phenomena, if these mutational phenomena converge at the genetic underpinnings of neuropsychiatric disorders will introduce a substantial acquisition bias in our understanding of the somatic variation underlying these disorders.
To overcome this bias, we propose to use a pangenomic approach to infer germline haplotypes, align to a graph-based representation of the infered haplotypes, and call somatic variation against it.
This approach will allow us to capture somatic variation in regions with elevated germline variation and thereby provide a more accurate description of the somatic mutational landscape in regions associated with neuropsychiatric disorders.
Our hypothesis is that coincidence of germline and somatic variation is elevated within regions associated with neuropsychiatric disorders and that this coincidence confounds traditional genomic analyses.

## Research Plan Summary - version 1
### Significance
Neuropsychiatric disorders have a significant genetic basis influenced by both germline variation and somatic mutations. Regions associated with these disorders tend to be enriched in genetic variation, leading to challenges in accurate analysis due to limitations in conventional alignment methods. Traditional sequence alignment to a reference genome is constrained by an approximately 6% sequence deviation tolerance, beyond which read accuracy and mappability degrade. This problem is further compounded in regions with high rates of germline variation, which become sensitized to the effects of even minor somatic mutations, pushing alignment deviations beyond acceptable limits. This convergence of germline and somatic variation results in substantial biases in detecting somatic mutations, leading to incomplete or inaccurate genomic descriptions of neuropsychiatric disorders.

To address these biases, we propose a pangenomic approach that incorporates inferred germline haplotypes and aligns read fragments to a graph-based representation of these haplotypes. By adopting this strategy, we aim to more comprehensively capture somatic variation in regions of high germline diversity, thereby providing a more nuanced and accurate understanding of the somatic mutational landscape underlying neuropsychiatric disorders.

Our central hypothesis is that the coincidence of germline and somatic variation is elevated in regions linked to neuropsychiatric disorders, and this convergence confounds current genomic analyses. The proposed research will lead to a more accurate identification of somatic mutations and contribute to a better understanding of the genetic underpinnings of neuropsychiatric disorders.

### Specific Aims
- Aim 1: Benchmark Personalized Pangenome Detection of HapMap Mixture Pseudo-Somatic Variants
We will benchmark the sensitivity and specificity of our personalized pangenomic approach by introducing known pseudo-somatic variants into HapMap mixture samples. The goal is to validate the efficacy of the graph-based alignment in detecting somatic mutations across regions with different levels of germline diversity.

- Aim 2: Generate a Germline-Augmented Pangenome
We will generate a pangenome that incorporates germline variants associated with neuropsychiatric disorders. By using graph-based models, we aim to improve the representation of genomic diversity and accurately capture regions with elevated germline variation. This pangenome will serve as the foundational reference for aligning read fragments in subsequent analyses.

- Aim 3: Apply Personalized Pangenome to Detect Somatic Variation in Neuropsychiatric Disorders
Using the germline-augmented pangenome generated in Aim 1, we will analyze samples from individuals with neuropsychiatric disorders to detect somatic mutations. We hypothesize that this personalized pangenome approach will significantly enhance our ability to detect somatic mutations, particularly in regions enriched for germline variation, providing novel insights into the genetic architecture of neuropsychiatric disorders.

### Innovation
The proposed study employs a pangenomic approach to overcome the limitations of traditional linear genome references in capturing somatic variation in genetically diverse regions. By aligning to a graph-based model that incorporates germline haplotypes, our approach reduces biases associated with regions of high germline diversity, thereby enhancing our capacity to detect somatic variation. This innovative strategy not only addresses a critical technical limitation in genomic analysis but also opens new opportunities for understanding the interplay between germline and somatic mutations in complex disorders such as neuropsychiatric conditions.


## Preliminary Data
Take GWAS loci for neurodegenerative disorders from [GWAS catalog](https://www.ebi.ac.uk/gwas/efotraits/EFO_0005772) and plot density of hits against germline variation in draft pangenome graph.
Documented in ELN entry: [Pangenome_variation_vs_GWAS_Loci_Neurodegenerative_Disorders.md](SMaHT_Pilot_Preliminary_Results/Pangenome_variation_vs_GWAS_Loci_Neurodegenerative_Disorders.md)

**Update November 11 2024**
After meeting with Xiaoyu, I think I've decided to make some changes.
See: [SMaHT_Pilot_Preliminary_Results/Meeting_Nov_11_2024.md](SMaHT_Pilot_Preliminary_Results/Meeting_Nov_11_2024.md)

### Other preliminary data and published observations
Key points:
0. Hypothesis: Cumulative somatic and germline variation in the regulatory landscape of genes affecting cellular signaling of glial cells contribute to the manifestation of neuropsychiatric disorders.
1. Distortions in DNA methylation measurements are distorted by use of reference in regions proximal to genes associated with Dendrite morphogenesis/development
2. Distortions in expression measurements are distorted by use of reference in genes associated with cell surface interactions (CAMs, vesicle localizing, cell-substrate junction, etc)
2. Indel + SV elevated regions enriched for genes related to neurological processes (synaptic signaling, cell projection organization, neurogenesis, dendrite localization, Cadherens, etc)
3. Indel + SV elevated regions enriched for genes enriched for expression in astrocytes, fetal neurons, oligodendrocytes
4. Neural activity induces DSB
5. DSB are a major mechanistic source of SVs + Indels
6. Higher germline variation increases reference induced distortions


## Updated Synthesis of Observations and Preliminary Data
### Central Hypothesis
The interplay between germline and somatic variation in the regulatory landscape of genes influencing cellular signaling, particularly in glial cells, contributes to neuropsychiatric disorders. This interaction is underexplored due to biases introduced by traditional linear genome references, which fail to capture the full spectrum of genomic variation.

### Key Observations
1. Potential for Overlap Between Germline and Somatic Variation
- Genes associated with neurological processes (e.g., synaptic signaling, neurogenesis, dendrite morphogenesis) are enriched in regions with elevated indel and SV density.
- Neural activity-induced double-strand breaks (DSBs), a major source of SVs and indels, could contribute to the accumulation of somatic mutations in these regions.

2. Impact of Reference Genome on Measurements
- Traditional linear references distort:
  - DNA methylation measurements, particularly in genes associated with dendrite morphogenesis.
  - Expression measurements, especially for genes involved in cell surface interactions, cell adhesion, and vesicle localization.

3. Potential Reference-Induced Distortions in High-Variation Regions
- Elevated germline variation increases the likelihood of reference-induced biases, making somatic mutation detection more challenging in these regions.

4. Mechanistic Insights into Structural Variation and Germline-Somatic Interplay
- Neural activity induces DSBs, which are enriched in regulatory regions of neural genes.
- These processes may act in regions with existing germline variation, sensitizing them to somatic mutational effects.

### Preliminary Data Highlights
1. GWAS Loci and Germline Variation
- Early analysis suggests that GWAS loci for neurodegenerative disorders cluster in regions of high germline variation in a pangenome graph.
- Additional work is needed to confirm if neuropsychiatric disorder-associated regions exhibit elevated rates of germline variation, including indels and SVs.

2. Pangenome Insights into Neuropsychiatric Disorders
- Indels and SV-enriched regions overlap with:
  - Genes linked to dendrite morphogenesis, synaptic signaling, and neurogenesis.
  - Genes expressed in neural cells (astrocytes, oligodendrocytes, fetal neurons).

3. Need for Pangenomic Approaches
- Preliminary data highlight the potential of pangenomic alignments to reduce reference-induced distortions in regions linked to neuropsychiatric disorders, particularly in regulatory landscapes.

In my own words what I hope to show is that. Convergence of somatic and germline variation in transcriptional regulatory elements of glial cells disrupts their cellular cross-talk functions. Namely disrupting enhancer/promoter sequences, partly by disrupting TF binding sites.
These mutational events are obscured using a linear reference. Characterizing how these hidden events alter glial:neuron cross talk will shed light on NPD

### Conclusion and Next Steps
- While evidence linking elevated germline variation with neuropsychiatric disorder-associated regions is currently lacking, preliminary results provide a framework for testing this hypothesis.
- By further analyzing GWAS loci and leveraging pangenomic methods, we aim to demonstrate the extent to which germline variation overlaps with neuropsychiatric loci.
- This work will provide critical insights into the interplay between germline and somatic variation, potentially revealing novel aspects of the genetic architecture of neuropsychiatric disorders.


## Notes from meeting with Eric
- Use psychENCODE data for 3rd aim
- make aim 1 about benchmarking the pangenome approach with HapMap samples
- make aim 2 about how expanding the pangenome to include more variation improves the ability to detect somatic variation in regions with high germline variation
along with this also propose to identify regions/process whose elevated germline variation would sensitize it to somatic variation dropout
- make aim 3 to find candidates with psychENCODE/SMaHT data and validate with a cell reporter assays


Structure of Research plan:
1. Background
2. Aim 1: Benchmark Personalized Pangenome Detection of Somatic Variants using HapMap data and graph-based truth set
3. Significance of aim 1
4. Aim 2: Generate a Germline-Augmented Pangenome and map out regions sensitive to somatic variation dropout
5. Significance of aim 2
6. Aim 3: Apply Personalized Pangenome to Detect Somatic Variation in Neuropsychiatric Disorders
7. Significance of aim 3
8. Innovation
9. Approach and Anticipated Results
10. Relevance of Proposed Project to the field of Somatic Variation


## Notes from meeting with Ting
- Don't focus at all on disease. So don't mention neuropsychiatric disorders
- aim 1 should be showing that somatic variant detection is a function of germline variation
- aim 2 is demonstrating that the pangenome can do this
  - Show with truth set that the pangenome can do this
  - Develop this with dsa
  - Generalize results/methods

## Example grants
https://www.niaid.nih.gov/grants-contracts/sample-applications#r21

## Specific aims guidance
https://www.biosciencewriters.com/NIH-Grant-Applications-The-Anatomy-of-a-Specific-Aims-Page.aspx

## Instructions
https://grants.nih.gov/grants/funding/phs398/phs398.pdf

# Document Formatting
- Font size 11
- Font Arial
- Margins 0.5 inches
- Max of 4 pages total

# Current structure of research plan
- Background (1-2 paragraphs, half a page max)
- Specific Aims
  - Aim 1: Evaluate and map out the Impact of Germline Variation on short read Somatic Variant Detection
  - Aim 2: Benchmark Short Read based Personalized Pangenome Detection of Somatic Variants
- Significance
  - Significance of aim 1: By mapping the interplay between germline variation and somatic variant detection, we will provide a comprehensive understanding of the biases introduced by germline variation in somatic variant detection. Allowing us to identify the genomic regions most sensitive to somatic variant dropout and bounds of tolerable germline variation.
  - Significance of aim 2: By benchmarking the personalized pangenome approach against a truth set, we will determine whether the pangenome can overcome the limitations of a linear reference to accurately detect somatic variants under variable levels of germline variation. Including how well the pangenome can re-capitulate a donor-specific assembly.
- Innovation
- Approach and Anticipated Results
  - Aim 1
    - Task 1.1: Map reference induced distortions for each germline haplotype
    - Task 1.2: Map reference induced distortions with varying levels of somatic variation added
    - Task 1.3: Using in silico mixture of simulated reads with varying levels of somatic variation added, benchmark simulated somatic variant detection
    - Task 1.4: Estimate degree of variation per genomic interval of the pangenome
    - Task 1.5: Quantify association between pangenome germline variation with somatic variant detection and reference induced distortions
  - Aim 2
    - Task 2.1: Benchmark Personalized Pangenome Detection of simulated somatic variants
    - Task 2.2: Benchmark Personalized Pangenome Detection of Somatic Variants using HapMap sample mixture
    - Task 2.3: Benchmark Personalized Pangenome Detection against donor specific assemblies
- Relevance of Proposed Project to the field of Somatic Variation

# Aim 1
The goal of this aim is to evaluate the extent of the problem of germline variation in somatic variant detection. We will map out the regions of the genome most sensitive to somatic variant dropout due to germline variation. We will also determine the bounds of tolerable germline variation for accurate somatic variant detection.

## Task 1.1
- Using high quality HPRC donor assemblies (47 individuals, 94 haplotypes)
- For each donor haplotype, map out the genomic structure induced and reference induced distortions
- In order to make distortion mapping most directly informative to the somatic variant detection process, the mapping process seeks to mirror the properties of the reads and the alignment process as closely as possible.
- wgsim is used to simulate reads from each donor haplotype to a high coverage, retaining information as to the site reads are derived from
  - 2x150bp reads
- Per read source sites are lifted over to hg38 coordinates using minimap2 alignments and PAFtools, noting sources which cannot be lifted over
- Simulated reads are aligned back to the donor haplotype they were simulated from
- Alignment sites in donor haplotype coordinates are lifted over to hg38 coordinates in the same way as the source sites
- Simulated reads are separately aligned against the human genome reference (hg38)
- For each read three possible positions are generated, the source position in the donor assembly lifted to hg38, the alignment position in the donor assembly lifted to hg38, and the alignment position in hg38
- Using these obervatiosn, for intervals of hg38 coordinates we can calculate the fraction of reads derived from a site which map back to it.
- Generate a count matrix where the row corresponds to the interval a read was derived from and the column corresponds to the interval the read was aligned to
- The matrix is normalized row-wise by the sum of the row to generate a probability matrix
- For each matrix calculate two metrics.
  - The first is diagonal distortion, which is 1 minus the diagonal of the normalized matrix.
    - d(i) = P(Alignment to site i in donor | derived from site i)
  - The second is coverage distortion, which is calculated for each column as the 1 minus the sum of row values.
    - $coverageDistortion_{j}=(1-\frac{row_{i,j}}{\sum_{i=1}^{n} row_{i,j}})$
    - c(i,N) = sum(j=1 to N){ P(Alignment to site i in donor | derived from site j) }
  - There should be as many values as there are columns in the matrix.
- The diagonal distortion is a measure of the rate at which reads are misaligned to the site they were derived from.
  - diagonal distortion is bounded between 0 and 1
- The coverage distortion is a measure of the rate at which reads are misaligned to a site they were not derived from.
  - coverage distortion is bounded between 0 and positive infinity
- By comparing the donor alignment distortion metrics to the reference alignment distortion metrics, we can identify regions where alignment to the reference introduces distortions in alignment relative to the donor haplotype.
- This process is repeated for each donor haplotype and serves as a baseline distortion map against which the impact of added somatic variation can be measured.
- The per donor haplotype distortion maps are also compared across haplotypes to identify the regional variability in alignment distortion.

## Task 1.2
- Randomly select a subset of sites to introduce somatic variation from 0.6% of sites to 6% of sites in 0.6% increments
- At each level of somatic variation, repeat the process of simulating reads, aligning to the donor haplotype, aligning to the reference, and calculating the distortion metrics
- Compare the distortion metrics at each level of somatic variation to the baseline distortion metrics to identify the impact of somatic variation on alignment distortion

## Task 1.3
- For each donor haplotype, mix read form germline simulated read and somatic simulated reads at varying ratios.
  - From 0.5% up to 2% of reads being somatic reads
- For each mixture, align to hg38, and perform somatic variant calling using mutect2
- Compare the somatic variant calls to the ground truth to determine the sensitivity and specificity of somatic variant detection at each mixture level
  - Calculate the F1 score for each mixture level globally and per genomic interval
- As with the distortion metrics, compare across donor haplotypes to identify the regional variability in somatic variant detection sensitivity and specificity, but at different mixture levels and somatic variant rates

## Task 1.4
- For each genomic interval, determine the rate of germline variation in the corresponding interval of the draft pangenome.
  - Calculated as the total number of non-reference alleles in the interval minus average number of non-reference alleles in flanking intervals 10X the size of the interval divided by average number of non-reference alleles in flanking intervals 10X the size of the interval
- This is the weighted allele count rate (WACR), which is a measure of the rate of germline variation captured by the pangenome in the interval relative to the surrounding regions

## Task 1.5
- Using the distortion metrics and the germline variation rates, determine the association between germline variation and alignment distortion
- Compare WACR per interval to the corresponding distortion metrics to identify regions where germline variation is associated with alignment distortion
- Linear regression models will be used to quantify the association between germline variation and alignment distortion, with the distortion metrics as the dependent variable and WACR as the independent variable
  - The underlying distribution of the distortion metrics will be assessed to determine the appropriate regression model

# Aim 2
The goal of this aim is to determine whether the personalized pangenome approach can adequately address the challenges explored in Aim 1.
- Our expectation is that using hg38 will is most sensitive to germline variation and therefore will have the highest somatic variant dropout rate
- We would also expect that using that using a donor specific germline assembly will have the lowest somatic variant dropout rate
- Our question is whether the personalized pangenome method can sufficiently recapitulate the donor specific assembly. If it can, we would expect the somatic variant dropout rate to be similar to that of the donor specific assembly.
- This would suggest that the personalized pangenome method is a viable alternative to using a donor specific assembly for somatic variant detection.
- Though the pangenome may need to be augmented with additional variation to achieve this level of performance

## Task 2.1
- Using the same simulated reads as in task 1.3, align to the draft pangenome and perform somatic variant calling using mutect2
- Compare the somatic variant calls to the ground truth to determine the sensitivity and specificity of somatic variant detection using the pangenome
  - Calculate the F1 score globally and per genomic interval
  - Compare the results to the linear reference-based somatic variant detection to determine the improvement in somatic variant detection using the pangenome

## Task 2.2
- Using mixture of HapMap samples to serve as control sample
- Align cell mixture data to the either draft pangenome or hg38 and perform somatic variant calling using mutect2
- Compare the somatic variant calls to the assembly-derived truth set to determine the sensitivity and specificity of somatic variant detection methods
  - Calculate the F1 score globally and per genomic interval
- Compare the results to the linear reference-based somatic variant detection to that of the pangenome to determine the improvement in somatic variant detection using the pangenome

## Task 2.3
- Using the same cell mixture data, align to the donor-specific assembly (HG005) and perform somatic variant calling using mutect2
- Compare the somatic variant calls to the assembly-derived truth set to determine the sensitivity and specificity of somatic variant detection methods
  - Calculate the F1 score globally and per genomic interval

# Significance of Aim 1
By mapping the interplay between germline variation and somatic variant detection, we will provide a comprehensive understanding of the biases introduced by germline variation in somatic variant detection.
This will allow us to identify the genomic regions most sensitive to somatic variant dropout and the bounds of tolerable germline variation for accurate somatic variant detection.
This information will be critical for developing strategies to mitigate the impact of germline variation on somatic variant detection and improve the accuracy of genomic analyses in regions with high germline diversity.
Further these maps can be used to identify biological processes enriched in regions sensitive to somatic variant dropout, providing insights into the functional consequences of germline variation on somatic mutation detection.
These finding will be made easily available by integrating them into the WashU epigenome browser for public access

# Significance of Aim 2
By benchmarking the personalized pangenome approach against a truth set, we will determine whether the pangenome can overcome the limitations of a linear reference to accurately detect somatic variants under variable levels of germline variation.
This will provide critical insights into the feasibility and efficacy of using a personalized pangenome for somatic variant detection, particularly in regions with high germline diversity.
The results of this aim will inform the development of pangenomic methods for somatic variant detection and guide the integration of pangenomic approaches into routine genomic analyses.
The workflow will be made available as a docker container to facilitate its adoption by the broader research community as well as on AnVIL for cloud based analysis
