# Figure-Driven Project and Manuscript Planning Guide

This document describes a figure-based framework for planning and writing scientific manuscripts.

The core idea is that a manuscript is a sequence of questions and answers.  
Each figure answers one question.  
Panels within a figure explore that same question in multiple ways.

If you cannot clearly state what question a figure is answering, the figure is not ready to exist.

---

## Overall Structure

Manuscripts should be organized around three figure classes:

- Figure 1: Overview and framing
- Figures 2–5: Core results
- Figure 6: Biological application or exemplar

Each figure has a distinct role. Figures should not overlap in purpose.

---

## Figure 1: Overview and Framing

Role:
- Introduce the problem.
- Explain why it matters.
- Describe the high-level approach.
- Orient the reader to what kinds of results will follow.

Figure 1 sets the stage. It does not present results.

Typical contents:
- Minimal background needed to understand the problem.
- Conceptual or methodological schematic.
- Definitions of key terms, abstractions, or datasets.
- A high-level workflow or pipeline.

Figure 1 should make the reader comfortable and oriented, not convinced.

---

## Figures 2–5: Core Results

Role:
- These figures contain the scientific argument of the paper.
- Each figure answers one clear question.
- Panels within a figure provide convergent evidence addressing that same question.

Together, Figures 2–5 typically do the following:
- Establish that the method is computationally feasible.
- Show that results agree with existing approaches at a global level.
- Demonstrate reproducibility and consistency.
- Identify where and why the new approach provides improvement.

Important constraints:
- Each figure should make one point.
- Do not mix unrelated stories within a single figure.
- If a new question arises, it belongs in a new figure, not a new panel.

A useful test:
Before making a figure, write one sentence:
“This figure asks whether ________, and shows that ________.”

If you cannot write this sentence cleanly, the figure is not ready.

---

## Figure 6: Biological Application or Exemplar

Role:
- Apply the method to a biologically interesting dataset.
- Make the abstract results concrete and intuitive.
- Walk the reader through a specific example.

Figure 6 is illustrative, not evidentiary.

What belongs here:
- Single loci, samples, regions, or case studies.
- Cherry-picked examples are acceptable if clearly framed as illustrative.
- Visualizations that would be too specific or distracting earlier in the paper.

What does not belong here:
- New global claims.
- Results required to believe the main conclusions.

If Figure 6 were removed, the paper should still stand.

---

## Global Rules

- Every figure answers one question.
- Panels are variations on an answer, not new questions.
- Figures should appear in a logical order.
- If a figure does not fit one of the defined roles, it should not exist.

---

## Worked Example: methylGrapher (NAR)

This section shows how the framework maps onto a real paper:
methylGrapher: genome-graph-based processing of DNA methylation data from whole genome bisulfite sequencing (Nucleic Acids Research).

Figure 1:
- Introduces limitations of linear reference WGBS analysis.
- Motivates graph-based methylation analysis.
- Presents a schematic of the methylGrapher workflow.

Figures 2–5:

Figure 2 (computational and alignment performance):
- Benchmarks runtime, memory usage, and scalability.
- Compares alignment performance between linear and graph-based methods.
- Establishes computational feasibility.

Figure 3 (methylation and coverage benchmarking):
- Compares genome-wide methylation levels and coverage between methods.
- Assesses agreement and systematic differences.

Figure 4 (reproducibility and consistency):
- Compares replicate-to-replicate consistency.
- Compares consistency between linear and graph-based approaches.
- Demonstrates genome-wide stability.

Figure 5 (where the graph-based method improves results):
- Narrows focus to specific regions or contexts.
- Shows where the graph-based approach provides clear advantages.

Figure 6:
- Applies the method to a biologically interesting dataset.
- Presents a representative, cherry-picked example to build intuition.

---

## Draft Figures and Conceptual Planning

Before even executing the analysis, you should create *draft figures* that are conceptual.

Draft figures are not meant to be publication-ready. Their purpose is to force you to think through:
- What analysis will be performed.
- What quantities will be compared.
- How the results will be visualized.

This step is much easier once the question for the figure is clearly defined.

For each figure, you should be able to specify:
- The question the figure answers.
- The analysis or analyses needed to answer that question.
- The basic structure of the plots (what goes on each axis, what is being compared).

At this stage, it is often sufficient to sketch figures by hand, use placeholder data, or generate rough plots with minimal formatting.

Example:

If Figure 2 asks whether the method is computationally feasible and performs well at alignment, then you already know:
- You will benchmark runtime and resource usage.
- You will compare multiple methods or conditions.
- You will likely plot time or memory on the y-axis versus method or dataset on the x-axis.
- Alignment performance may be shown as rates or proportions across methods.

You do not need the final numbers yet or even to have performed any analyses.
You only need to know *what kind of numbers will go where*.

This process serves two purposes:
- It clarifies what analyses are actually required.
- It often reveals missing controls or comparisons early, before time is spent running large jobs.

A useful rule:
If you cannot sketch a rough version of the figure, you probably do not yet understand the question well enough.

Draft figures should be created for every figure before large-scale analysis begins.

---

## Final Notes

Good papers are not collections of analyses.
They are structured arguments. No one likes a data dump.

If you plan the figures correctly, the manuscript largely writes itself.

This plan is a guide, not a rigid rule.
We will deviate from it as the science guides us. That is expected and important.

Having a clear plan will make you more confident in your work, help you think deeply about your approach, and make the writing process much easier.

At the same time, it is important not to put everything on hold until the plan feels perfect. A rough draft is always better than no draft at all. Science and writing are both fundamentally exercises in recursive refinement.

Start rough. Revise often. Let the structure evolve as the science comes into focus.
But always have a full plan constructed.