# MoRGANA study outline (v3 — signal-accumulation refocus)

**Target journal:** Nature Communications
**Framing:** Resource-first, framework as the engine. Population-genetics angle on ancestry.
**Refocus from v2:** The headline is now *reference-induced distortion of signal-accumulation assays at functional features (cCREs and genes)*. The genome-wide WGS distortion map is scaled back to a **chr16 proof-of-principle** that validates the framework before it is specialized to functional assays. Clinical relevance is **retained but routed through the features**: ENCODE cCRE–gene associations tie regulatory elements to their target genes, and genes are annotated for disease relevance (OMIM, ClinVar gene-level, ACMG SF), so distortion at a cCRE or gene inherits a clinical interpretation without analyzing individual variant coordinates. Position-level clinical-variant analysis (per-variant ClinVar/PharmGKB) is **deferred to a follow-up**. Local ancestry stays as the population-genetics angle.

---

## One-line pitch

A framework that quantifies how short-read alignment to a linear reference distorts the apparent *signal* in coverage-based functional assays — chromatin accessibility, ChIP, expression — separates that reference-induced distortion from assembly-intrinsic distortion at every interval, and maps it population-scale and haplotype-resolved across cCREs and genes, so that signal at any regulatory element or gene can be assessed as biology or alignment artifact — and, by linking cCREs to their target genes and genes to disease annotation, flags where that distortion lands on clinically important biology.

## Working title

*Population-scale maps of reference-induced distortion in signal-accumulation assays across human regulatory elements and genes.*

---

## What MoRGANA does (assay-agnostic framework)

MoRGANA quantifies how alignment to a linear reference distorts the apparent coverage landscape, and separates reference-induced from assembly-intrinsic distortion at every interval. The framework is **assay-agnostic**: an assay is just a read-generation profile fed into the same pipeline. WGS is the simplest profile and serves as the proof-of-principle; signal-accumulation assays are additional profiles.

### Pipeline (unchanged core)

1. **Simulate (now per-assay).** Reads are generated from a donor's phased assembly (the DSA) under an *assay-specific* profile — read length, pairing, fragment-size distribution, error model, and coverage/enrichment structure appropriate to the assay (e.g., nucleosome-aware fragmentation for ATAC, enrichment-weighted coverage for ChIP, spliced reads for RNA-seq). Each read carries its true source coordinate.
2. **Dual-align.** Every read is aligned twice: against the donor's own DSA, and against GRCh38.
3. **Lift to common coordinates.** Both alignments plus the true source position are lifted into GRCh38 space and made directly comparable.
4. **Build matrices.** Per interval, a `source × aligned` count matrix per haplotype: one from the reference alignment, one from the DSA-lifted alignment.
5. **Row-normalize.** `M[i, j] = P(source = j | aligned = i)`.
6. **Compute distortion metrics** (below).

### Metrics (unchanged definitions; coverage distortion is the headline for these assays)

- **Diagonal distortion at `i`** = `1 − M[i, i]` = `P(source ≠ i | aligned = i)`. Interval-as-destination, purity loss: of the reads/signal landing here, how much belongs here.
- **Coverage distortion at `j`** = `1 − Σᵢ M[i, j]` (column sum on the row-normalized matrix). Interval-as-source, mass conservation: of the signal originating here, is its mass conserved. Positive = deficit (signal diluted at busy destinations); negative = excess (signal credited at quiet destinations); zero = balanced.

For signal-accumulation assays, **coverage distortion is the primary readout**, because the assay's biological signal *is* accumulated coverage at a feature; diagonal distortion reports how much of the apparent signal at a feature is foreign.

### Dual-alignment decomposition (central)

- **DSA view** — distortion present even when reads align to the donor's own assembly: the intrinsic-difficulty floor (repeats, paralogy, segmental duplications).
- **Reference view** — total distortion under standard pipelines aligning to GRCh38.
- **Reference − DSA** — the purely reference-induced component, the part a better reference can fix.

### Population-scale application

Across ~230 HPRC2 haplotypes, MoRGANA produces per-feature distributions of distortion (median, IQR, SD, proportion-flagged) for each assay class, at every cCRE and gene — a haplotype-resolved distortion map no reference-centric mappability track can provide.

### Pilot thresholds (locked from chr16 work)

- Diagonal distortion threshold: 0.15.
- Coverage distortion threshold: mode + 2 SD of the genome-wide coverage-distortion distribution.
- Diagonal difference threshold (DSA − reference): 0.1.
- Coverage difference threshold (DSA − reference): 1.

---

## Section outline with key claims

### Introduction (~750 words)
- **Claim 1.** Coverage-based functional assays (accessibility, ChIP, expression) read out *accumulated signal*, and short-read alignment to a linear reference systematically reshapes that signal in a donor-dependent way.
- **Claim 2.** Existing mappability and difficult-region tracks describe properties of the reference, not how a given donor's assay reads are handled when aligned to it; they cannot quantify donor-specific, haplotype-resolved, *assay-specific* distortion at the features that matter functionally.
- **Claim 3.** HPRC2 phased assemblies make it possible to simulate assay reads from ground-truth genomes at population scale and measure distortion as the deviation between truth and alignment.
- **Claim 4.** Because regulatory elements and genes can be connected to disease through ENCODE cCRE–gene associations and gene-level disease annotation, distortion maps over these features can be read for clinical consequence without resolving individual variants.
- **Setup.** We introduce MoRGANA, validate it as a chr16 WGS proof-of-principle, specialize it to signal-accumulation assays, and apply it across ~230 HPRC2 haplotypes to map reference-induced distortion across cCREs and genes, releasing the maps as a community resource. We show that distortion at functional features tracks local ancestry, and that linking cCREs to genes and genes to disease annotation concentrates a fraction of clinically important regulatory and genic biology in distorted intervals.

### Results 1. A framework for quantifying alignment-induced distortion in signal-accumulation assays
- Schematic + metric definitions; the assay-agnostic, per-assay-profile design.
- Two-alignment design; DSA intrinsic floor vs reference-induced component.
- Why coverage distortion is the natural readout for accumulated-signal assays.

### Results 2. chr16 WGS proof-of-principle
- HG002 walked end-to-end on chr16 (GIAB-annotated).
- MoRGANA recovers known difficult regions and produces interpretable matrices.
- Validation/enrichment against existing tracks (ENCODE blacklist, GIAB stratifications, segmental duplications, repeats) on chr16; quantification of intervals MoRGANA flags that existing tracks miss.
- DSA-vs-reference decomposition genome(chr16)-wide. Establishes the metrics and thresholds carried forward.

### Results 3. Reference-induced distortion across signal-accumulation assays
- Apply MoRGANA under each assay profile (ATAC-seq, histone/TF ChIP, RNA-seq) and compare distortion behavior across assays.
- **Claim.** Distortion magnitude and spatial pattern depend on assay read/fragment structure as well as on the underlying sequence; assays that target short, feature-localized signal behave differently from broad coverage.
- Sensitivity of distortion to fragment/read profile (motivates the supplementary parameter sweeps).

### Results 4. Distortion across ENCODE SCREEN cCREs
- Distortion stratified by cCRE class (promoter-like, proximal/distal enhancer-like, CTCF-bound, DNase-only).
- cCRE cores vs flanking regions.
- Population variability of distortion across cCRE-rich neighborhoods.
- **Claim.** Reference-induced distortion is non-randomly distributed across regulatory-element classes, with implications for which regulatory inferences (accessibility, TF occupancy, enhancer activity) are most susceptible to alignment artifact.

### Results 5. Distortion across GENCODE genes
- Distortion stratified by gene-body component (exon, intron, 5′ UTR, 3′ UTR, promoter, intergenic).
- Per-gene summary statistics across all protein-coding genes; identify the tail of consistently high-distortion genes.
- **Claim.** A definable set of genes carries consistent reference-induced distortion in expression/coverage assays, flagging loci where quantitative functional readouts should be treated with caution.

### Results 6. Population-scale maps and local-ancestry-patterned distortion
- Apply across ~230 HPRC2 haplotypes; per-feature median/IQR/SD/% flagged.
- Decompose features into **universal** (reference is the problem for everyone), **variable** (donor-specific structure), and **subset-specific** (ancestry/haplotype-linked) distortion classes.
- **Claim A.** A measurable fraction of cCREs and genes shows non-trivial reference-induced distortion under standard short-read functional pipelines.
- **Claim B.** Distortion at these features is haplotype-dependent and tracks local ancestry (pclai), consistent with distortion being a function of haplotype-reference divergence rather than a fixed property of the locus.
- **Claim C.** The magnitude of this dependence varies by feature class, with implications for which functional inferences are most sensitive to reference choice across ancestries.

### Results 7. Reference-induced distortion on clinically connected regulatory elements and genes
- The clinical-relevance section, kept inside the cCRE/gene framework via association rather than via variant coordinates.
- **Linkage.** Tie each cCRE to its predicted target gene(s) using ENCODE cCRE–gene associations (e.g., SCREEN-linked genes / ENCODE-rE2G distal links), then annotate genes for disease relevance (OMIM disease genes, ClinVar P/LP gene-level, ACMG SF v3.2 gene list). Distortion at a regulatory element inherits the clinical context of the gene it regulates; distortion at a gene inherits its own disease annotation.
- **Claim A.** A measurable fraction of disease-associated genes, and of the cCREs predicted to regulate them, fall in intervals with non-trivial reference-induced distortion under standard signal-accumulation pipelines.
- **Claim B.** Distortion on these clinically connected features is haplotype-dependent and ancestry-patterned (pclai), so the reliability of functional signal at disease-relevant regulatory and genic loci varies across ancestries.
- **Claim C.** The effect is concentrated rather than uniform: a definable, enumerable set of disease genes and their linked cCREs carries consistent distortion, providing a prioritized watch-list for functional-genomics studies of those loci.
- **Worked example.** A disease gene (or its distal enhancer) that is clean on the reference for some haplotypes but reference-distorted on others, with the cCRE–gene link and local ancestry overlaid to show the mechanism.
- Background comparison: do clinically connected features show stronger or distinct distortion than size/GC/repeat-matched non-clinical features?

### Discussion (~750 words)
- What the resource enables (locus-level reliability scoring for functional-genomics signal; QC for accessibility/ChIP/expression studies; ancestry-aware interpretation; a prioritized watch-list of disease genes and their regulatory elements where functional signal is reference-distorted).
- Limits of linear references for functional genomics; what pangenomes would need to deliver to reduce distortion of signal.
- Limitations (read/fragment-model realism, aligner choice, single platform, simulation vs real-data gap, surjection-free design choices).
- Natural follow-ups: position-level clinical-variant distortion (per-variant ClinVar/PharmGKB), extending the gene-level clinical angle of Results 7 down to individual variants; CHM13 and pangenome-reference comparisons using the same framework; somatic behavior (SMaHT extension); long-read analogs; genome-wide WGS scale-up beyond chr16.

### Methods (online)
Assay-specific simulation profiles, full pipeline, metric definitions, statistical thresholds, pclai integration, software availability.

---

## Figure plan

### Fig 1. MoRGANA framework
- **A.** Dual-alignment workflow: donor haplotype → assay-specific simulated reads → align to DSA + reference → lift to common coordinates.
- **B.** The two count matrices over a worked feature region.
- **C.** Metric definitions (diagonal, coverage distortion) as bar plots from the matrices.
- **D.** Decomposition: DSA distortion = intrinsic floor; reference − DSA = reference-induced.

### Fig 2. chr16 WGS proof-of-principle (HG002)
- **A.** chr16 track of diagonal and coverage distortion.
- **B.** Zoom into a known difficult region (segdup-rich locus) with matrices/metrics.
- **C.** Clean negative-control region.
- **D.** Enrichment vs existing tracks + DSA-vs-reference fractions on chr16.

### Fig 3. Distortion across signal-accumulation assays
- **A.** Per-assay distortion distributions (ATAC, ChIP, RNA-seq) at matched features.
- **B.** Spatial profile of distortion around a representative feature, by assay.
- **C.** Dependence of distortion on fragment/read profile.

### Fig 4. Distortion across cCREs
- **A.** Distortion by SCREEN cCRE class.
- **B.** cCRE cores vs flanks.
- **C.** Population variability across cCRE-rich neighborhoods.
- **D.** Worked cCRE example with matrices.

### Fig 5. Distortion across genes
- **A.** Distortion by GENCODE gene-body component.
- **B.** Per-gene distribution of mean/max distortion across all protein-coding genes; high-distortion tail called out.
- **C.** Worked high-distortion gene example.

### Fig 6. Population-scale map + local ancestry (headline)
- **A.** Per-feature median distortion across haplotypes with IQR; proportion-flagged.
- **B.** Universal vs variable vs subset-specific feature classes.
- **C.** Heatmap of haplotypes × features (representative region), ordered by similarity (ancestry structure).
- **D.** Local-ancestry stratification of distortion at high-impact cCREs/genes (pclai).
- **E.** Worked example: a feature high-distortion only on a subset of haplotypes, with local ancestry overlaid.

### Fig 7. Distortion on clinically connected regulatory elements and genes
- **A.** Schematic of the linkage: cCRE → target gene (ENCODE associations) → disease annotation (OMIM / ClinVar gene-level / ACMG SF).
- **B.** Distortion distributions for disease genes and their linked cCREs vs a matched non-clinical background.
- **C.** Top-ranked disease genes / linked cCREs by mean and variance of distortion across the cohort (the watch-list).
- **D.** Local-ancestry stratification of distortion at high-impact clinically connected features.
- **E.** Worked example: a disease gene or its distal enhancer, reference-distorted on a subset of haplotypes, with the cCRE–gene link and ancestry overlaid.

### Supplementary (anticipated)
- Assay-profile sensitivity (fragment size, read length 100/150/250 bp, enrichment model).
- Coverage-depth sensitivity.
- Aligner sensitivity (BWA-MEM vs BWA-MEM2; RNA-aware aligner for the RNA profile).
- Paired-end vs single-end (`--singleend` supported).
- Per-feature-class breakdowns; chr-by-chr summaries.

---

## Analysis gap list (chr16 pilot → refocused paper)

### Tier 1 — required
1. **chr16 WGS proof-of-principle** end-to-end (HG002 walk + decomposition).
2. **Assay-specific simulation profiles** defined and validated (ATAC, ChIP, RNA-seq).
3. **Per-assay distortion** characterization at features.
4. **ENCODE SCREEN cCRE intersection** — distortion per cCRE class.
5. **cCRE core vs flank** analysis.
6. **GENCODE gene-body component** distortion analysis.
7. **Per-gene distortion summary** across all protein-coding genes (+ high-distortion tail).
8. **Population scale-up** of the feature analysis across ~230 HPRC2 haplotypes.
9. **Population summary statistics** per feature (median, IQR, SD, % flagged).
10. **Decomposition into intrinsic (DSA) vs reference-induced** at features.
11. **pclai cluster integration** into the distortion-metrics output (prereq for #12 and Fig 6C ancestry clustering).
12. **Local-ancestry stratification at cCREs/genes** using pclai.
13. **Validation/enrichment** of flagged features vs existing difficult-region tracks (on chr16 + at feature level).
14. **ENCODE cCRE–gene association ingestion** (SCREEN-linked genes / ENCODE-rE2G) to map regulatory elements to target genes.
15. **Gene-level disease annotation** ingestion (OMIM disease genes, ClinVar P/LP gene-level, ACMG SF v3.2 gene list).
16. **Clinical-relevance crossing**: distortion on disease genes and their linked cCREs, with matched-background comparison and ancestry stratification.

### Tier 2 — strongly recommended
17. Repeat-class and SV-proximity stratification of feature distortion.
18. Ancestry-structure clustering of the haplotype × feature heatmap (Fig 6C).

### Tier 3 — supplementary / robustness
19. Assay-profile sensitivity sweeps.
20. Read-length / coverage-depth sensitivity.
21. Aligner sensitivity.
22. Paired-end vs single-end.

### Out of scope for v1 (flagged in Discussion)
- Position-level clinical-variant distortion (per-variant ClinVar P/LP, PharmGKB/CPIC coordinates) — **deferred follow-up**. (Gene-level disease annotation via cCRE–gene linkage is **in**; see Results 7.)
- Genome-wide WGS distortion map beyond chr16.
- GRCh38 vs T2T-CHM13 comparison.
- Pangenome-reference comparison.
- Somatic mutagenesis (SMaHT extension).
- Long-read distortion.
- Variant-call performance benchmarking.

---

## Scope decisions

| Item | Decision |
|---|---|
| Headline framing | Reference-induced distortion of signal-accumulation assays at cCREs/genes |
| WGS distortion map | **chr16 only**, as proof-of-principle |
| Signal-accumulation assays | **IN, core.** Assay-specific simulation (ATAC, ChIP, RNA-seq) |
| cCRE distortion (SCREEN) | **IN.** Main figure |
| Gene distortion (GENCODE) | **IN.** Main figure |
| Population scale (HPRC2 ~230 haplotypes) | **IN** for the feature analysis |
| Local-ancestry stratification | **IN**, at cCREs/genes (pclai); population-genetics framing |
| Clinical relevance via gene linkage | **IN.** cCRE→gene (ENCODE associations) → gene-level disease annotation (OMIM, ClinVar P/LP gene-level, ACMG SF) |
| Position-level clinical-variant analysis | **OUT — deferred follow-up** (per-variant ClinVar/PharmGKB coordinates) |
| Variant-call benchmarking | OUT |
| CHM13 / pangenome reference comparison | OUT (own papers) |
| Somatic mutagenesis (SMaHT) | OUT (SMaHT paper) |
| Aligner / read-length / depth / SE-vs-PE sensitivity | IN, supplementary |
| Exemplar haplotype for proof-of-principle | HG002 (chr16) |
| Multi-cluster interval assignment | Majority-overlap |
| Cluster ID unification | Exact tuple matching (pclai BED col 10) |
| Resource access | BED tracks + downloadable per-feature tables for v1; portal as follow-up |

---

## Open methodological items before writing

- **Assay simulation realism.** Define defensible fragment/read models per assay: ATAC nucleosome-periodicity and Tn5 fragmentation, ChIP enrichment structure (and whether to model peak vs background separately), RNA-seq splice-aware read generation. Decide how much biological signal structure to impose vs. a neutral coverage profile that isolates the alignment effect.
- **Which assays make v1.** Confirm the assay set (ATAC + one ChIP flavor + RNA-seq?) and whether RNA-seq needs a splice-aware aligner and splice-aware lift, which complicates the common-coordinate step.
- **Feature ↔ interval mapping.** How cCREs and gene components map onto MoRGANA's fixed interval scheme; core vs flank window definitions; gene-component boundary handling.
- **cCRE–gene link source.** Choose the association set (SCREEN-linked genes vs ENCODE-rE2G vs an ABC-style model); decide how to handle multi-gene links and link confidence, and whether distal vs proximal links are treated separately.
- **Disease-gene annotation sources.** Settle OMIM / ClinVar (gene-level P/LP) / ACMG SF versions and how genes are deemed "disease-associated"; decide whether to weight by number/strength of associations.
- **Clinical background matching.** Define the non-clinical matched-background set (size, GC, repeat content, expression level) for the Results 7 comparison.
- **Genome-wide vs feature-targeted simulation.** Whether assay reads are simulated genome-wide (captures signal migrating *into* features) or feature-targeted (cheaper). Compute cost of assays × ~230 haplotypes is the main feasibility constraint — settle a strategy.
- **pclai resolution** at cCRE/gene scale; minimum-sample-per-cluster threshold; multiple-testing strategy (within-feature-class FDR vs pooled); matched-background sampling (size, GC, repeat content).
- **Interval scheme** generalization from the chr16 pilot binning.
- **Software/portal release plan.**
- **Path-parsing / pclai BED naming** verification before scale-up (per v2 notes: `strsplit` donor/haplotype extraction; HPRC2 vs GIAB-style HG002 naming).

---

## SMaHT relationship (for the Discussion section, unchanged in spirit)

MoRGANA's HPRC2 application produces the framework and the population-scale functional-feature resource. MoRGANA on SMaHT specializes it to per-donor read-handling profiles and to in silico somatic mutagenesis (introducing candidate somatic mutations into simulated fragments and measuring how they are handled). Both remain deferred to the SMaHT companion paper.

---

*Plan iteration: v3 — refocused on signal-accumulation assays (cCREs and genes); WGS reduced to a chr16 proof-of-principle; clinical relevance retained via ENCODE cCRE–gene linkage + gene-level disease annotation (position-level variant analysis deferred); local ancestry retained. Update as decisions evolve.*
