# Overview
In this entry I will describe the process of comparing germline variation in the draft pangenome against GWAS loci for neurodegenerative disorders.
My hope is that GWAS loci will have a dense pocked within regions of elevated germline variation.

## Setup box directory
```bash
cd /Users/juanmacias/Library/CloudStorage/Box-Box/LawsonLab/JuanMacias/Postdoc/SMaHT

mkdir Pangenome_variation_vs_GWAS_Loci_Neurodegenerative_Disorders
```

## Download ND GWAS loci to box
Downloading from [Here](https://www.ebi.ac.uk/gwas/efotraits/EFO_0005772)
![Screenshot 2024-11-08 at 3.30.52 PM.png](Screenshot%202024-11-08%20at%203.30.52%E2%80%AFPM.png)

```bash
cd /Users/juanmacias/Downloads/
mv gwas-association-downloaded_2024-11-08-EFO_0005772-withChildTraits.tsv /Users/juanmacias/Library/CloudStorage/Box-Box/LawsonLab/JuanMacias/Postdoc/SMaHT/Pangenome_variation_vs_GWAS_Loci_Neurodegenerative_Disorders/

cd /Users/juanmacias/Library/CloudStorage/Box-Box/LawsonLab/JuanMacias/Postdoc/SMaHT/Pangenome_variation_vs_GWAS_Loci_Neurodegenerative_Disorders/
```

## Download all GWAS loci
Downloading from [full GWAS catalog](https://www.ebi.ac.uk/gwas/docs/file-downloads)
