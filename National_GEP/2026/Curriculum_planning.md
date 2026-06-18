---
title: National GEP Curriculum Planning
date_requested: 2026-06-02
deadline: 2026-06-11
priority: Medium
---

# Overview
Here I will document my notes for this GEP workshop thing

## Notes
- Link to [brainstorming doc](https://docs.google.com/document/d/1kD5DXghcu9E6vTx_dM-x3D-e_vUfj5fwZFvZi8ustQs/edit?tab=t.dfvs2gs5oigy)
- Link to list of [Pangenome resources](https://docs.google.com/document/d/1fsY8kKBHbpgYpdgFstdzztF0qQaOVZLyQZRA7r3WPao/edit?tab=t.0#heading=h.2xyytp5bu57y)
- [schedule for event](https://thegep.sharepoint.com/:w:/s/2026NationalGEPFacultyWorkshop/IQCecSodcwZWSZ_8jsB1cQk2ATYd76UhX9-ph5wBEqQKC-w?rtime=F4CU0fHH3kg)
## Action Items

- [x] Review "Some examples of existing GEP curriculum"

- [x] Synthesize pangenomics as I think of it
- [x] Draft my thoughts
- [x] Wait for response from workshop team

### Brainstorming Pangenome Curriculum

Here is my thinking on the introductory curriculum and a first exercise we could pilot in the fall. I have written a fuller, graduate-level synthesis of the concepts separately (for a review I plan to write and I will inevitably teach this to graduate students, so I figured why not invest in my future students); what follows is the slice of it I think is my best guess of what is right for an introductory audience, along with the design calls I have made and outstanding questions to work through together.

## Audience and scope
I am pitching it at a beginning undergraduate, and I have built it in two tiers so that it matches our goal of starting at an introductory level and scaling to an investigation.

- The first tier is a beginner on-ramp: conceptual, with little or no compute, answering what a pangenome is and why one reference is not enough.
- The second tier is the investigation: students build a small pangenome and visualize it. This is more ambitious, and I would pitch it at intermediate students, or at a course that already has some computational footing.

The on-ramp can stand alone for instructors who only want the concept, while the investigation gives us the hands-on pilot.

## Learning objectives
Students will be able to:

- Define a pangenome and distinguish it from a single reference genome.
- Explain why a single reference is limiting, using a concrete example of reference bias.
- Define a haplotype and explain what it means to compare across haplotypes.
- Interpret a simple pangenome graph: identify shared sequence as a common path and variation as branches.
- Use a viewer to locate sequence present in some haplotypes but absent from the reference.
- Describe why pangenome representation matters for human health, through one motivating locus.

I am deliberately leaving some things out of the intro and saving them for later or for the graduate treatment: the microbial core and accessory framing, construction algorithms in any detail, population genetics, and personalization and surjection.

## The teaching arc

The spine I have in mind is paper graph, then read a real graph, then build a real graph, so that the compute only shows up at the end. Point by point:

1. The reference workflow, and why it breaks. How we normally map reads to one reference and reconstruct the individual, and what fails when a person carries sequence the reference does not contain. This is reference bias, and it motivates everything after it. I would treat a full alignment-algorithm walkthrough as optional depth, not core. (Exercise.)
2. What a pangenome is, from alignment to graph. Many genomes at once; at heart a multiple sequence alignment; a graph is just that alignment drawn as a shared path with branches. I define haplotype here. (Exercise.)

*Of note, it would be ideal if they already have some understanding of BLAST, as this could build off of that conceptually.*

3. Reading a graph: nodes, paths, bubbles. A path is one individual's route, a bubble is a site of variation, and bubbles come in flavors. (Exercise.)
4. Where graphs come from: assemblies and construction. You need assembled genomes, and a tool aligns them into the graph. I name Minigraph-Cactus here, lightly. (Setup, no exercise.)
5. Build it yourself: a locus-scale pangenome. (Exercise, and my pilot candidate from bfx workshop.)
6. Visualize and interpret what you built. (Exercise, paired with point 5.)
7. Why it matters: the human-health payoff. Tie the locus to phenotype and name what a single reference would have missed. This is largely interpretive, and I think the complex-locus material works better as homework than as core class time.

## The three exercises

These build on one another, and I have kept the compute footprint to the third.

**Exercise 1. Graph on paper.** I give students four or five short related sequences, their haplotypes, and they build a multiple sequence alignment by hand. Then they collapse the shared columns into a single path and branch the differences, drawing a small pangenome graph with a pencil. No compute. This is the conceptual keystone for me, because it makes the alignment-to-graph idea concrete before any software appears.

**Exercise 2. Read a real graph.** Students open a small pre-built graph in Bandage, trace a named haplotype's path, find the bubbles, and classify each as a substitution or an indel. The graph is one someone else built, so the only new skill is interpretation, not construction. This is their first contact with the real tool.

**Exercise 3. Build a real graph.** This is the investigation, and my candidate for the Fall 2026 pilot. On a pre-staged environment(?), students run Minigraph-Cactus on a small, locus-scale dataset and produce a graph in minutes. They then open their own graph in Bandage, locate the variation, and answer guided questions: what varies here, which haplotypes carry it, and what a single reference would have missed. Building, visualizing, and the human-health connection all meet in one activity. In particular I am thinking of a NuMT example, since they are super obvious (they can use BLAST to ID) and cancer associated phenomenon.

Can also load the specific case in the HPRC epigenome browser to view comparative alignment tracks

## Tools and compute

I want the investigation to use Minigraph-Cactus to build and Bandage to visualize, by design, because building a graph and seeing the bubbles is the most authentic and memorable thing students can do.

I am not going to pretend the constraints are not real. Minigraph-Cactus is command-line and heavy, and Bandage is a desktop application, so this sits above a true no-install bar. Two things make it workable:

- The data has to be small. A locus-scale build, one region pulled from a handful of haplotypes, finishes in minutes and produces a small graph, instead of the hours and large outputs of a genome-scale build.
- The compute has to be pre-staged I think. With fixed versions of everything. Changing versions can very much break things between tools.

Bandage is the lighter half. The graph file is small, so it opens on a laptop, with Bandage either installed once by students or preinstalled in the environment. I use BandageNG.


## Faculty training

Most of what faculty need is already in hand or falls out of the above:

- A conceptual primer, which my graduate-level synthesis already provides.
- Answer keys for the three exercises.
- A short walkthrough for Bandage and for running the build.
- The pre-staged compute environment, which is the main faculty-facing dependency.


## Action items

[x] TODO make slides, make module docs, make handouts?

<!-- workspace-atlas
status: done
-->
