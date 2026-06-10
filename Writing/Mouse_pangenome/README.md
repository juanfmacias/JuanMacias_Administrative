# Overview
Here I will write out my thoughts and plans wrt our draft mouse pangenoem work.
We conducted the project, wrote up a manuscript, and it went through peer review.
We were rejected by Nature and Nature Genetics, we appealed to Nature Genetics.
The appeal worked, so we are now revising the manuscript for resubmission to Nature Genetics.
The big change is that we have added much better assemblies and made the primary reference a C57BL T2T assembly.

Here I will discuss for myself the changes that are needed for the revision.
And since basically everything must be re-run on account of a change in assembly, we must therefore narrow many of the
analyses to just the most important ones. For the sake of time.


## Notes:
Incorporate newly released telomere-to-telomere (T2T) assemblies into the mouse pangenome

Expand and clarify the limitations discussion about (i) the value of completeness and (ii) current tool constraints in highly repetitive or structurally complex regions

Substantially streamline the mapping performance section in the main text, moving “in-the-weeds” numerical detail and statistical reporting into the supplement

Add a gold-standard read-level mapping correctness evaluation for simulated reads (vg-style correctness assessment, as in vg map / Giraffe benchmarking patterns)

Add an algorithm-matched comparison by running vg giraffe on the linear reference, alongside existing results (keep the practical BWA vs Giraffe comparison, but add the controlled one).

Remove or rewrite unsupported interpretive claims about “Giraffe trading quantity for quality” and similar statements, and clarify that observed differences can reflect aligner behavior rather than graph structure.

Add a brief clarification of “surjection” as used in the vg ecosystem (and optionally acknowledge the set-theory meaning).

Add validation that reads aligning to the linear reference but lost after surjection are lower-quality or more gappy (alignment score and gap-profile comparisons)


Clarify the two mechanisms behind the surjection penalty: (i) filtering of lower-quality or mismapped linear alignments and (ii) inability to project graph-only sequence back to a reference that lacks it.

Fix the missing label for ED Fig 6d

Expand discussion on alternatives that avoid surjection loss by operating downstream in graph space

Reframe the reference-bias section to emphasize the quantities that matter (fraction of biased sites, bias magnitude distribution, tail counts of strongly biased sites), and move detailed statistical reporting to the supplement
Extend the real-data reference-bias analysis so it parallels the simulated analysis (number and fraction of biased sites, magnitude, and related summaries
Add stratified summaries by mapping quality, with explicit caveats that MAPQ and bias are coupled, and provide separate summaries for repetitive vs non-repetitive regions

Add a variant calling benchmark using a leave-one-out strategy among RI lines to make the link from improved alignment to improved downstream variant detection explicit
For the “pangenome personalization” section, include a comparison using Pangenie (while clarifying the vg workflow is an existing method, applied here in mouse)

Clarify the rationale for strain selection (18 distinct strains; why that set covers most use cases) and position future expansion as assemblies become available

Correct the statement about ref 40 (revise to say tandem repeats, not large-scale SVs)
Strengthen the paper’s functional consequence linkage without turning it into a full trait-mapping project by integrating matched RNA-seq to test whether allele-specific cCRE accessibility corresponds to allele-specific expression of nearby genes

For methylGrapher’s additional CpGs: characterize the genomic distribution and overlap with functional annotations (promoters, enhancers, regulatory features), with an explicit note about liftover limitations from graph space to the annotation coordinate system

Replace the unsupported “potential DMR” style claim with a formal differential methylation analysis (DSS) after converting calls to an appropriate linear coordinate system, since differential testing is not currently supported directly in graph space

For allele-specific ATAC with n=2 biological replicates: cross-validate the allele-specific ATAC peaks by identifying allelic imbalance genes in matched RNA-seq from the same samples.

Correct the BioProject accession number PRJNA31085 to PRJNA310854
