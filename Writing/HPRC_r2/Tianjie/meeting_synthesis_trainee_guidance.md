# Synthesis of Guidance to Trainee

This document synthesizes the specific guidance given to the trainee during a long (~6-hour) mentoring meeting involving the PI (dominant speaker) and the advisor. The transcript does not label speakers; attribution reflects that the PI delivered the majority of directive, evaluative, and scope-controlling guidance. The synthesis prioritizes analytical expectations, figure logic, scope control, and unresolved conceptual issues, rather than chronological discussion.

---

## 1. Core Direction from the PI

### 1.1 Clarify the scientific question before the method
- Repeated emphasis that every analysis must be driven by a clearly articulated question.
- Figures should not be built first and justified later.
- For each analysis, the trainee was expected to state:
  - what hypothesis is being tested,
  - what the null expectation is,
  - what outcome would be considered non-trivial or informative.
- The PI explicitly challenged analyses that appeared to be “ranking-based” without a statistical or conceptual null.

### 1.2 Avoid drifting between variation and differential frameworks
- Strong pushback when the analysis shifted implicitly from variation of methylation to differential methylation between populations.
- Mixing these two concepts within a single figure was flagged as conceptually confusing.
- The PI stated that variation-based analyses and differential analyses answer different questions and should be separated cleanly.
- If differential analysis is included, it must be justified as a second-order question, not blended into a variation-centric figure.

### 1.3 Streamline and narrow
- The PI repeatedly encouraged simplification:
  - fewer figures,
  - fewer analytical modes,
  - tighter narrative focus.
- If a figure does not clearly advance the core question, it should be cut or deferred.
- The phrase “streamline, streamline” captures the repeated guidance.

---

## 2. Standards Applied to Figures and Analyses

### 2.1 Every figure must have an explicit hypothesis
- The PI repeatedly asked: “What do you want the reader to conclude from this figure?”
- Figures without a clear expected outcome were criticized as descriptive but uninformative.
- The trainee was instructed to articulate, for each figure:
  - the expected pattern if nothing interesting is happening,
  - what deviation from that pattern would imply biologically.

### 2.2 Ranking-based enrichment is not sufficient on its own
- Analyses based on taking “top N” regions or pathways were flagged as vulnerable to selection bias.
- The PI emphasized that ranking alone induces dependency on arbitrary cutoffs.
- If ranking is used, the trainee must:
  - explain why the ranking metric is meaningful,
  - demonstrate robustness to cutoff choice,
  - or supplement with a statistical framework.

### 2.3 Control for multiple testing and chance findings
- The PI explicitly raised concern that large-scale computations can produce apparent patterns by chance.
- Differential or enrichment-style analyses must address:
  - how many tests are being performed,
  - why observed differences are unlikely to arise randomly.
- Failure to do so was described as a major weakness.

### 2.4 Consistency of analytical scale
- Switching between gene-level, region-level, and pathway-level summaries within a single figure was discouraged.
- Each figure should operate at one conceptual scale unless there is a compelling reason to bridge scales.
- Pathway-level summaries must be clearly connected back to the underlying regional or genomic signals.

---

## 3. Conceptual and Analytical Issues Raised

### 3.1 Variation versus differential methylation
- The PI repeatedly questioned why population-level differential methylation was being emphasized.
- They argued that differential methylation is less conceptually aligned with the project’s strength than differential variation.
- Key challenge posed:
  - Why look at mean differences between populations rather than differences in variability?
- The trainee acknowledged this tension and was encouraged to refocus on variation-centric analyses.

### 3.2 Interpretation of population-specific signals
- The PI noted that population-specific patterns are only compelling if:
  - the same genetic variation behaves differently across populations, or
  - the same epigenetic variation shows population-dependent behavior.
- Simply observing different top-ranked regions in different populations was described as weak without deeper justification.

### 3.3 Use of pathway and gene-set analyses
- Pathway-level analyses were treated as exploratory rather than definitive.
- The PI stressed that such analyses must answer a biological question, not simply catalog enriched terms.
- Analogies to single-cell marker identification were used to clarify expectations, but the PI emphasized that the analogy must be conceptually valid, not superficial.

### 3.4 Local versus global population labels
- A suggestion emerged to consider local ancestry or haplotype-based grouping rather than global population labels.
- The PI noted that haplotype blocks already encode genetic similarity and may offer a cleaner grouping variable.
- This was presented as a possible simplification rather than a required direction.

### 3.5 Structural variation as a source of novelty
- The PI stated explicitly that genuinely new insights are most likely to come from structural variation.
- Replicating known small-variant methylation associations was framed as necessary but not sufficient.
- Structural variation was highlighted as the most defensible source of novelty if supported by strong examples.

---

## 4. Expectations for Rigor and Analytical Ownership

- The trainee is expected to fully understand the construction and meaning of:
  - all matrices used,
  - all scores derived from those matrices,
  - all grouping variables and labels.
- The PI repeatedly asked the trainee to explain, in plain terms:
  - what exactly is in the matrix,
  - whether it represents methylation levels or variation of methylation,
  - and why that choice is appropriate.
- Ambiguity about the contents or interpretation of analytical objects was treated as a serious issue.

---

## 5. Action Items

### Priority 1: Conceptual clarity
- Decide explicitly whether the core analysis is about:
  - variation of methylation, or
  - differential methylation between populations.
- Remove mixed framing within single figures.

### Priority 2: Figure restructuring
- Revisit Figure 2 and ensure it focuses on a single analytical theme.
- Separate variation-based clustering from differential analyses into distinct figures if both are retained.
- For every figure, add a clear statement of the question being answered.

### Priority 3: Statistical justification
- Reduce reliance on arbitrary top-N rankings.
- Demonstrate robustness to cutoff choice or replace with statistically grounded methods.
- Address multiple testing explicitly where large numbers of regions or pathways are evaluated.

### Priority 4: Simplification and streamlining
- Cut analyses that do not directly advance the core question.
- Avoid expanding figures to include multiple loosely related panels.

### Priority 5: Structural variation focus
- Identify concrete examples where structural variation is clearly linked to methylation behavior.
- Use these as anchors rather than broad genome-wide summaries where possible.

---

## 6. Outstanding Unresolved Questions

- Should the central narrative be framed around methylation variability rather than population mean differences?
- What is the most defensible null model for population-specific methylation patterns?
- How should pathway-level summaries be justified beyond exploratory analysis?
- Are global population labels obscuring more meaningful haplotype-level structure?
- Which observed patterns are robust versus artifacts of ranking and selection?

---

## 7. Project Summary (Assistant’s Interpretation)

Based on the discussion in this meeting, the project appears to aim to characterize how genetic variation, particularly structural variation, is associated with variability in DNA methylation across individuals and populations.

The core analytical object is a genome-wide matrix summarizing methylation behavior (either levels or variation) across defined regions, with individuals or populations as the comparative axis. The central scientific question is not simply whether populations differ in methylation, but whether genetic variation leads to systematic differences in how methylation varies, and whether those differences are shared or population-specific.

The PI’s guidance consistently pushed the project away from:
- descriptive ranking exercises,
- loosely justified pathway enrichment,
- and mixed analytical frameworks,

and toward:
- explicit hypotheses,
- variation-centric reasoning,
- and a tighter focus on structural variation as a driver of novel insight.

The success of the project hinges on clarity of framing, disciplined figure construction, and a clear separation between exploratory analyses and defensible core results.

---

This synthesis reflects the PI’s dominant guidance style in this meeting: demand a clear question, resist analytical sprawl, and ensure that every figure earns its place by answering something specific and non-trivial.
