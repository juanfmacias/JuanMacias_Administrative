
# Overview

This is a brief overview of the surjection methods used in the Klotho paper.
The goal of this document is to provide a brief overview of the methods used in the paper.

Essentially the surjection tool has two phases: 
The first phase is the pre-computation of lookup objects.
The second phase is the actual surjection of a dataset.

## Pre-computation
This step is done because the process of surjection is computationally expensive.
So expensive that it is not feasible to do it on the fly.
So for a given genome-graph, we pre-compute a lookup object that contains the surjection of every cytosine in the genome.

ELN entry for this step: [GenerateCytosineAnnotationsFromGraph_andPrecomputeConversions.txt](..%2F..%2FMethylGrapher_Benchmarking%2FMethylGraph_PositionConversion%2FGenerateCytosineAnnotationsFromGraph_andPrecomputeConversions.txt)

### Run extract annotations on real graph
[run_extractCytosineAnnotationsFromGraphSegments.sh](..%2F..%2F..%2FGeneral_Code%2Frun_extractCytosineAnnotationsFromGraphSegments.sh)

### Splitting positions
[run_Batch_Split_Files.sh](..%2F..%2F..%2FGeneral_Code%2Frun_Batch_Split_Files.sh)

### Converting split cytosine positions
[run_Batch_convertSegmentToRef.sh](..%2F..%2F..%2FGeneral_Code%2Frun_Batch_convertSegmentToRef.sh)

### Build precomputed positions lookup dictionary and pickle it
[run_Batch_PicklePrecomputedPositionsHash.sh](..%2F..%2F..%2FGeneral_Code%2Frun_Batch_PicklePrecomputedPositionsHash.sh)

### Generate segment and offset keys for each split file
[run_Batch_Generate_Converted_SegmentAndOffsetKeys.sh](..%2F..%2F..%2FGeneral_Code%2Frun_Batch_Generate_Converted_SegmentAndOffsetKeys.sh)
[run_Batch_Move_Specific.sh](..%2F..%2F..%2FGeneral_Code%2Frun_Batch_Move_Specific.sh)


## Surjection
The surjection of a dataset is done by first loading the lookup object for the genome-graph.
Then for each cytosine in the dataset, we look up the surjection in the lookup object.

ELN entry for this step: [LiftingOverRealBenchmarkingDataFromMethyGrapher.txt](..%2F..%2FMethylGrapher_Benchmarking%2FLiftingOverRealBenchmarkingDataFromMethyGrapher.txt)

### 2. Subset out CG context. Also make then name of the output .graph.methyl instead of .graph2.methyl
grep "CG" ./HG00741/BRep2/graph2.methyl >./HG00741/BRep2/CG.graph.methyl

### 3. sort the CG.graph.methyl files by the first two columns and save the output to a new file with the .sorted extension
sort -k1,1 -k2,2n ./HG00741/BRep2/CG.graph.methyl >./HG00741/BRep2/CG.graph.methyl.sorted

### 4. Split .graph.methyl (input) file based on keys (precomputed lookup derived offset-segment keys) using the run_Batch_SplitFiles_by_PreSplitKeys_MGConversion.sh script
[run_Batch_SplitFiles_by_PreSplitKeys_MGConversion.sh](..%2F..%2F..%2FGeneral_Code%2Frun_Batch_SplitFiles_by_PreSplitKeys_MGConversion.sh)

### 5. Convert each CG.graph.methyl file to methylC format using the conversion script
[run_Batch_convertGraphMethyl_To_MethylC.sh](..%2F..%2F..%2FGeneral_Code%2Frun_Batch_convertGraphMethyl_To_MethylC.sh)

### 6. Combine all of the methylC files into a single file for each sample by BRep directory
cat HG00621/BRep1/SplitOutputFiles/*.methylC >HG00621/BRep1/CG.graph.Precomputed.methylC
[CompressDirectory.sh](..%2F..%2F..%2FGeneral_Code%2FHousekeeping_HTCF%2FCompressDirectory.sh)

## Description of algorithm
In this context, surjection is the process of collapsing down all graph coordinates within a minigraph-cactus derived graph to the reference coordinates of the genome reference serving as the base of the graph.
The version of the draft pangenome used here was built on the hg38 reference.
As such surjection collapses all non-hg38 segments down to hg38 coordinates.

This process of surjection is was performed using a tool called Ixchel (Github repo).
Here Ixchel takes all cytosines within the pangenome graph and precomputes their surjection to hg38 coordinates.
This precomputation is done to dramatically speed up the process of converting graph coordinates to hg38 coordinates for multiple samples.

The surjection pre-computation is done by first extracting all cytosines from the graph.
Then for each segment in the graph which bears a cytosine, the context of the segment is determined.

Specifically it checks whether it is reference segment, whether it is within one degree of seperation from a reference segment, whether it is within one degree of seperation downstream of more than one reference segment, the length of the segment, the length of the syntentic reference segment if any.

Segments within one degree of seperation downstream of a single reference segment or are themselves reference segments are considered to be "highest confidence" positional conversions.

For segments meeting this criteria, surjection is performed by taking the preceding reference segment starting position, adding to that the length of the preceding reference segment, and then adding the offset of the cytosine within the segment. A flag encoding segmental context is returned for every converted cytosine.
