# Overview
A core idea of this grant is that too much germline variation can cause alignment issues, even when just dealing with germline data.
That there are specific regions where germline variation is not high enough to prevent germline alignment, but the addition of somatic variation pushes the alignment error rate too high.
Thereby creating pockets of the genome where somatic variation is not being captured by traditional methods. I want to argue that certain traits are both associated with these regions and impacted by accumulation of somatic variation.
I want to argue Neurodegenerative diseases are associated with such polymoprhic regions, that accumulation of somatic variation in these regions is associated with the progression of the disease, and that the current methods are not capturing this somatic variation.

I asked Xioayu to meet to get feedback on the grant proposal.
Specifically focusing on the testing for enrichment of GWAS loci in regions with high germline variation.

## Whiteboard notes:
![Meeting_Nov_11_2024_Notes.png](Meeting_Nov_11_2024_Notes.png)

## Feedback
1. Maybe use Genome-wide values as background to calculate odds ratio
2. Use Distortion map process to directly population variaiton to change in alignment
3. On top of germline distortion map, add in controlled amount of simulated somatic variation
4. Look at chr19 region

## 1. Genome-wide values as background
I am currently taking the number GWAS loci for a give trait in a region with high polymorphism and dividing that by the number in moderate (background rate) polymorphism regions.
This is the High ratio referenced in my R code. His suggestion is to calculate the High ratio for the whole genome and use that as the background ratio.
If I divide the High ratio by the genome-wide ratio, I get the odds ratio. Which is a more standard way to calculate enrichment.

However, this doesn't consider how the number of observations affects the stability of the high ratio.
So at low observation counts, the high ratio being compared to the genome-wide ratio may not be reliable.
I could generate a randomized background by repeatedly sampling loci from the genome and calculating the ratio.
Then I could compare the high ratio to the distribution of background ratios. I am not sure though.

## 2. Distortion map
He suggested using the pipeline I have to map out reference induced distortion to identify regions based on germline variation.
If the germilne variation is high enough to cause distortion, then somatic variation is completely missed.

## 3. Add in controlled amount of simulated somatic variation
Building on the previous point, I could add in a controlled amount of simulated somatic variation to see how it impacts the distortion map.
Regions in which the addition of somatic variation causes the distortion to increase could be regions where somatic variation is not being captured.
Once these are identified, I could look at a variety of annotations/associations in/near them.

This approach would much more directly address the specific conditions I am interested in and is intuitive.
Unfortunately, It has two major drawbacks:
1. I don't have a good way to simulate somatic variation. In the sense that I don't have a good model of where/how somatic variation occurs. I could just randomly add in SNPs, but that isn't likely to be realistic.
2. This approach is slow and very computationally intensive. Even for a single haplotype it's a lot of compute power. I would ideally need to do this for all 94 haplotypes in the draft pangenome. So it would be an investment.

## 4. Look at chr19 region
He suggested looking at the chr19 region which has a big spike in the nuerodegenerative disease GWAS loci.
He thinks that region may be known to have high germline variation of zinc finger proteins. Namely copy number variation.

## Possible change to aims
One possible change to the aims would be to replace aim 3, which focuses on neurodegenerative diseases, with the reference guided distortion map approach.
Finding the regions in the genome where somatic variation cannot be captured due to high germline variation would itself be the aim.