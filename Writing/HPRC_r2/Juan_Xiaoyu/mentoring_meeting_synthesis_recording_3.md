# Synthesis of Guidance to Trainee

This document synthesizes the specific guidance given to the trainee during the ~6‑hour mentoring meeting with the PI (dominant speaker), Juan, and the trainee. It focuses on scope control, analytical rigor, figure standards, action items, and unresolved issues. Speaker attribution reflects that the PI delivered the majority of directive and evaluative guidance, including repeated emphasis on not overselling claims.

---

## 1. Core Direction from the PI

### 1.1 Do not oversell the contribution
- Repeated, explicit instruction: *do not oversell*. Claims must not exceed what is directly demonstrated by the analyses.
- Polymorphic TE analyses should not be framed as broader statements about genome-wide selection, constraint, or regulatory architecture unless those conclusions are tightly supported.
- Comparisons between TEs, SNPs, and other SVs must be clearly caveated and literature-backed; otherwise, they should be presented as descriptive observations.

### 1.2 Keep the scope TE-focused and defensible
- This is a **TE paper**, not a general variant, QTL, or transcriptome paper.
- Analyses should center on what polymorphic versus fixed TEs reveal about TE biology, history, and functional consequences.
- QTL, methylation, and transcript analyses are supporting evidence, not the primary narrative.

### 1.3 Figures over rhetoric
- Figures should drive the story.
- Every major claim must map cleanly to a figure.
- Background discussion should be minimal and subordinate to what is actually shown.

---

## 2. Standards Applied to Figures and Analyses

### 2.1 Every figure must answer a question
- For each figure, the trainee was expected to articulate:
  - the null or baseline expectation,
  - what outcome would support that expectation,
  - what outcome would contradict it and why that matters.
- Purely descriptive catalogs without a motivating question were repeatedly challenged.

### 2.2 Allele frequency and selection arguments require caution
- Minor allele frequency distributions can be shown, but strong selection claims are risky.
- Confounders repeatedly emphasized by the PI:
  - variant age (younger TEs skew low frequency),
  - merging and ascertainment differences between TE insertions and SNPs.
- Any inference about tolerance, deleteriousness, or neutrality must be explicitly justified and cited.

### 2.3 Merging criteria matter
- Differences in how nearby insertions are merged can materially alter frequency spectra.
- Manual versus automated merging must be documented and justified.
- Biologically identical events split computationally should be acknowledged as such.

### 2.4 Annotation plots must respect reference bias
- Functional annotation is HG38-based.
- Reference TEs contributed to annotation itself, whereas non-reference MEIs represent insertion preferences.
- Mixing reference and non-reference MEIs in annotation summaries is misleading unless explicitly separated.

---

## 3. Conceptual and Analytical Issues Raised

### 3.1 Polymorphic vs fixed TEs
- Fixed TEs provide historical and functional context.
- Polymorphic TEs capture ongoing variation and population dynamics.
- Comparisons between these classes are meaningful but must respect age, ascertainment, and annotation differences.

### 3.2 TE age versus sequence diversity paradox
- A major unresolved issue: older TEs appear to show *lower* sequence diversity across populations than younger TEs.
- This contradicts naive neutral expectations.
- Multiple speculative explanations were discussed (drift, hitchhiking, recombination between similar copies, mapping artifacts), but **no resolution was reached**.
- The PI emphasized that this must be framed as either a potential artifact or an explicitly open biological question.

### 3.3 Constraint and deleteriousness metrics
- Use of CCR/CADD-like scores for MEIs is acceptable but subtle.
- Conceptual mismatch highlighted:
  - reference MEIs are treated as deletions in individuals lacking them,
  - potentially inflating deleteriousness for functionally important reference insertions.
- Background or random-insertion controls were suggested for intuition, but marked as lower priority.

### 3.4 Regulatory and transcript-level effects
- TE exonization, TE-derived transcript starts, and modular regulatory effects are of interest.
- Associations are acceptable; mechanistic claims are not.
- Strong preference for quantitative, anchorable statements (percentages, proportions) over narrative explanations.

---

## 4. Expectations for Rigor and Ownership

- The trainee is expected to understand and be able to explain:
  - all merging decisions,
  - all frequency thresholds,
  - all annotation sources and limitations.
- Confusing or counterintuitive patterns must be confronted directly, not smoothed over.
- If an effect cannot yet be explained, it should be labeled as such.

---

## 5. Action Items

### Priority 1: Framing and claims
- Tighten all high-level language to match what is explicitly demonstrated.
- Remove or qualify selection and constraint claims that lack direct support.

### Priority 2: Figure revisions
- Ensure each figure answers a clear question.
- Separate reference and non-reference MEIs in functional annotation analyses.
- Enforce consistent color schemes across figures.

### Priority 3: Methodological clarity
- Document and justify TE merging criteria.
- Explicitly discuss ascertainment bias and age effects in allele frequency analyses.

### Priority 4: Unresolved patterns
- Flag the TE age versus diversity pattern as unresolved and revisit later.
- Avoid speculative explanations unless clearly labeled as such.

---

## 6. Outstanding Unresolved Questions

- Why do older TEs show reduced sequence diversity across populations?
- How much of the observed frequency structure reflects biology versus merging or mapping artifacts?
- What is the most defensible neutral baseline for TE allele frequency comparisons?
- How should constraint metrics be interpreted for reference insertions conceptually treated as deletions?

---

## 7. Project Summary (Assistant’s Interpretation)

Based on the discussion, the project is best understood as follows:

The project systematically characterizes polymorphic transposable elements in human populations using a pangenome-scale resource, contrasting them with fixed TEs and other classes of variation to understand TE frequency spectra, age, diversity, and functional context. By integrating population frequency, methylation, transcript structure, and functional annotation, the study aims to clarify how polymorphic TEs differ from fixed elements and from other variants, while carefully accounting for reference bias, ascertainment effects, and methodological limitations.

The scientific contribution lies in quantitatively describing the population and functional properties of polymorphic TEs at scale, rather than in proposing new models of selection, regulation, or genome architecture. The emphasis is on precise measurement, careful comparison, and clear articulation of what can and cannot be concluded from the data.

---

This synthesis reflects the PI’s dominant guidance style throughout the meeting: constrain scope, prioritize rigor, and ensure that every claim is defensible under close scrutiny.

