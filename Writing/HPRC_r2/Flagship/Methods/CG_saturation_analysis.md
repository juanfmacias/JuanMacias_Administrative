[x] TODO draft methods text from Cristian
[x] TODO draft methods text from Juan
[ ] TODO deposit code to repo

This reference to the CG saturation curve and dinucleotide growth analysis.

My code for this is: [Dinucleotide.Rmd](../../../../HPRC_r2/Panepigenome_flagship/CG_Growth/Dinucleotide.Rmd)

Essential figures for this part added to: "Supplementary_Figure_A.ai"

Text:
Per-dinucleotide counts were tabulated for the reference genome (GRCh38) and for the pangenome. For each of the 16 dinucleotides, percent growth was defined as the increase in pangenome count relative to that dinucleotide's own reference count, (Pangenome − Reference) / Reference × 100, normalizing each dinucleotide to its own reference abundance. A pangenome-count-weighted mean growth across dinucleotides was also computed. To assess whether growth scales with dinucleotide abundance, an ordinary least-squares regression of percent growth on reference count was fit across the 15 non-CpG dinucleotides, excluding CG. All analyses were performed in R.
