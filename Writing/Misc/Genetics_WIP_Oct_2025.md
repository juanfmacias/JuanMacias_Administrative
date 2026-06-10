Cohen lab student: One attendee asked why we don’t simply perform pairwise comparisons across assemblies instead of building and using a pangenome. I explained that such pairwise comparisons essentially reinvent work that the graph already does more efficiently, since the graph integrates variation and enables read mapping in a unified representation.

Barak: Another question concerned why haplotype reconstruction might fail even if the founder haplotypes are present in the graph. I clarified that highly complex, nested variation can generate a combinatorial explosion of possible recombination paths, making resolution computationally impractical. In addition, copy number variation and heterozygosity create ambiguity in determining how many copies are actually present in a given individual.

Guoyan: On the effect of read length, I emphasized that our construction process is k-mer based rather than dependent on read length. This means that actual read length does not directly affect the genome construction step; what matters is the k-mer content.

Alex F: He asked about performance trade-offs when increasing haplotype representation. I noted that we do see a parabolic effect where adding haplotypes improves mapping up to a certain point, but beyond that, performance can decline unless we filter and personalize the graph to avoid dragging along unnecessary alleles. This effect persists even in the second release.

Nina: She suggested using haplotype assignment as an internal QC check in single-cell RNA-seq. I agreed that this is feasible in principle, as consistency can be informative, but data sparsity in single-cell RNA-seq imposes practical limitations.

Eric Li: He raised the issue of annotations, asking whether assembly-specific annotations are necessary. I explained that while comparative annotation per assembly would be ideal, projection from a reference onto other haplotypes is sufficient to start with. However, projection risks missing events such as copy number variation or duplications that would be captured with assembly-specific annotation.

Susan: She asked about phenotypic differences among the founders. I pointed out that founder lines are known to differ in traits such as cartilage regrowth and digit regeneration. While it is difficult to comprehensively phenotype each DO animal given their unique genotypes, the founder differences are well documented and relevant to our work.

Mike Meers: He asked how inversions appear in the graph. I explained that inversions can be represented explicitly as links connecting reversed segment ends, which is conceptually clean, but depending on the method, they can also manifest as insertion-like rearrangements.

Eric (follow-up): He later asked about using snarl trees to enumerate all possible paths through a subgraph. I noted that while this is indeed useful, generating subgraphs is not straightforward, is under-documented, and is prone to pitfalls that require trial and error to avoid.

Barak: His second question, clarified through discussion with Nina, was about using allele frequencies as priors in genome construction. I confirmed that incorporating allele frequency information is a strategy to bias towards more common alleles, which can improve the accuracy of assembly and reconstruction.