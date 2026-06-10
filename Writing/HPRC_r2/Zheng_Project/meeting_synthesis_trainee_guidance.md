# Synthesis of Guidance to Trainee

This document synthesizes the specific guidance given to the trainee during the ~6‑hour meeting with the PI (dominant speaker) and you. It focuses on scope control, analytical rigor, figure standards, action items, and unresolved issues. Speaker attribution reflects that the PI delivered the majority of directive and evaluative guidance, including repeated emphasis on not overselling claims.

---

## 1. Core Direction from the PI

### 1.1 Do not oversell the contribution
- Central instruction: *do not claim capabilities that are not explicitly demonstrated*.
- The current work should not be framed as a new “graph‑based epigenetic” or “pan‑epigenome” data structure unless such a structure actually exists.
- Mapping or projecting methylation values onto graph coordinates is acceptable, but this must be described as annotation, not as modification or extension of the graph itself.
- Hypothetical extensibility (for example, tissue‑specific labeling) must either be demonstrated with a concrete example or removed from the claims entirely.

### 1.2 Keep the scope narrow and defensible
- The story should remain tightly focused on what is actually analyzed.
- If the data are limited to methylation and a single cell type, the narrative must reflect that limitation.
- Broad functional or multi‑tissue implications should not be implied unless they are explicitly shown.

### 1.3 Figures over rhetoric
- The PI pushed for a figure‑first presentation style.
- Background explanations should be minimal and subordinate to what the figures actually show.
- Every major claim must be anchored in a figure.

---

## 2. Standards Applied to Figures and Analyses

### 2.1 Every figure must answer a question
- For each figure, the trainee was expected to state:
  - what the baseline or null expectation is,
  - what outcome would support that expectation,
  - what outcome would contradict it and why that matters.
- Descriptive catalogs without a motivating question were explicitly criticized.

### 2.2 Descriptive statistics are not enough
- Mean comparisons without variance or distributional context were rejected as uninterpretable.
- Acceptable alternatives include:
  - showing full distributions, or
  - explicitly displaying variance or spread.

### 2.3 Normalize before interpreting enrichment
- Claims that certain chromosomes or regions gain or lose more CpGs must be normalized by an appropriate denominator (for example, chromosome length) before interpretation.

### 2.4 Labeling discipline
- Use population‑level labels when possible rather than coarse continental groupings.
- Ensure sample labels follow established conventions rather than ad hoc exclusions or renaming.

---

## 3. Conceptual and Analytical Issues Raised

### 3.1 Ambiguity of “graph‑based epigenetic variation”
- The PI repeatedly stated that it was unclear what “graph‑based epigenetic variation” meant in concrete terms.
- If the final object is simply methylation values associated with graph coordinates, that must be stated explicitly.
- Any implication that tissue specificity or epigenetic state is encoded *within* the graph structure was challenged.

### 3.2 Tissue specificity claims require proof
- Hypothetical statements about how tissue information could be added were rejected.
- The minimum acceptable bar is a worked example that demonstrates the claim end‑to‑end.

### 3.3 Outliers and subgroup structure
- A subset of individuals appeared systematically different at the hypermethylation extreme.
- The trainee was instructed to investigate whether this reflects:
  - sex effects,
  - subgroup structure,
  - technical or assembly artifacts.
- Outliers must be interrogated, not waved away.

### 3.4 Skepticism about large reported effects
- A claimed ~20% shift was explicitly challenged as likely overstated or misinterpreted.
- The PI emphasized that if an effect is truly genetic, correlated features should move accordingly.
- If they do not, alternative explanations (technical, QC, representation artifacts) must be considered.

### 3.5 Mechanistic overlays require direct evidence
- Transposable‑element‑based explanations must be supported by explicit intersection and enrichment analyses.
- Broad mechanistic narratives without direct evidence were discouraged.

### 3.6 CpG loss and heterozygosity
- The PI highlighted a conceptual issue: CpG loss may reflect heterozygous absence of a site.
- The trainee was asked to clarify how methylation is defined or interpreted when only one allele carries the CpG.

---

## 4. Expectations for Rigor and Ownership

- The trainee is expected to understand every dataset, pipeline, and processing step used in the analysis.
- “Someone else ran this” is not an acceptable explanation.
- All thresholds, binning choices, and transformations must have explicit justification.
- After extended iteration, the expectation is that the trainee can clearly explain why observed patterns look the way they do.

---

## 5. Action Items

### Priority 1: Claims and framing
- Rewrite all high‑level language to match what is actually implemented.
- Remove or sharply qualify any tissue‑specific or multi‑modal claims without demonstrated examples.

### Priority 2: Figure revision
- Reorder the narrative so figures come first.
- For each figure, add an explicit expectation and interpretation.
- Remove or relegate purely descriptive panels to supplemental material.

### Priority 3: Statistical and visualization fixes
- Add distributional context or variance to all mean‑based comparisons.
- Normalize chromosome‑level comparisons appropriately.
- Replace continental labels with population labels where feasible.

### Priority 4: Investigate anomalies
- Diagnose the low‑hypermethylation subgroup.
- Re‑evaluate any large reported shifts and downgrade claims if they are not robust.

### Priority 5: Mechanistic support (only if retained)
- If TE‑driven explanations remain, provide direct evidence via overlap and enrichment analyses.

### Priority 6: Provenance and documentation
- Audit and document the origin and meaning of every imported dataset and annotation.

---

## 6. Outstanding Unresolved Questions

- What exactly is the final object produced by this work, and how should it be described without ambiguity?
- How, if at all, are haplotype, allele, or population labels formally linked to methylation values?
- How should methylation be interpreted when CpG sites are heterozygously absent?
- Which observed effects are biological versus technical or representational artifacts?

---

## 7. Project Summary (Assistant’s Interpretation)

Based on the discussion in the meeting, the project appears to be focused on the following core objective:

The project maps DNA methylation measurements onto pangenome graph coordinates in order to quantify how CpG presence, absence, and methylation levels differ across haplotypes and individuals relative to a reference backbone. The primary goal is to characterize how structural and sequence variation represented in a pangenome changes the *space in which methylation is observed*, rather than to build a new epigenetic graph data structure.

More concretely, the work:
- Uses graph-based coordinates (derived from a pangenome representation) to place CpG sites and their methylation values, including sites that are absent from a linear reference and therefore cannot be represented or lifted over cleanly.
- Compares the number, distribution, and methylation states of CpGs across individual haplotypes, populations, and references (for example, relative to a reference backbone such as GRCh38 or CHM13).
- Identifies where CpG gains and losses occur due to sequence and structural variation, and examines how those differences affect aggregate methylation summaries.
- Treats methylation as an annotation layered onto graph coordinates, not as a modification of the graph topology or a multi-layer epigenomic graph structure.

The scientific value of the project, as discussed, lies in showing that linear-reference-based methylation analyses systematically miss or misrepresent CpG content and methylation patterns in structurally variable regions, and that graph-coordinate-based annotation provides a more faithful accounting of methylation across diverse haplotypes. The emphasis is on quantification, comparison, and representation accuracy, not on tissue specificity, regulatory inference, or mechanistic epigenetic modeling.

This interpretation aligns with the PI’s repeated guidance to narrow the scope, avoid speculative extensions, and frame the contribution as a precise and defensible advance in how methylation data are represented and summarized in the context of pangenome variation.

---

This synthesis reflects the PI’s dominant guidance style: narrow the claims, enforce rigor, and ensure that every figure and statement can withstand close scrutiny by a skeptical reader.

