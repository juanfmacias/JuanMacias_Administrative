# Overview
In this ELN I will plan out lessons for my Practical, Unified, Reproducible Research System (PURRS).
PURRS is a practical research system that integrates project organization, electronic lab notebooks, software tooling, analysis, and visualization into a single, continuous practice.
It emphasizes making the full research process explicit and reproducible, including exploratory steps, intermediate decisions, and revisions, rather than only final results.
The system is designed to operate under real computational and organizational constraints and to minimize human error by avoiding manual data handling wherever possible, such as hand-entered file names or spreadsheet-based processing.
Instead, data flow, file references, and transformations are handled programmatically to preserve consistency, traceability, and reproducibility across code, data, figures, and written reasoning.

## Course goal
To make the structure and reasoning of a practical, unified, reproducible research system explicit by showing how projects are conceived, organized, executed, debugged, and finalized under real constraints.

What the learner should gain
An internalized sense of how to structure scientific work so that ideas, data, code, figures, and reasoning remain continuously connected and reproducible without relying on fragile manual steps.

## Lesson 0. Defining the scope and purpose of PURRS.
1. Supporting a gapless research process
2. Providing peace of mind and enabling easy re-engagement with projects over time
3. Avoiding an overly taxing or brittle system
4. Facilitating collaboration and handoff
5. Considerations for AI-assisted work within the system

## Lesson 1. Establishing the research ecosystem.
1. Defining the sparse-mirrored directory system rooted at a single user top-level directory (for example juanfmacias).
2. Defining super-projects, projects, sub-projects, and ELN entries, and how README.md files weave entries into a narrative table of contents.
3. Establishing what lives in GitHub versus Box versus HPC systems by default (code, ELN text, figures, large data, logs).
4. Defining the mirroring rule across spaces (ELN, code, storage, compute): preserving the path from the user directory downward even when contents differ across locations.
5. Creating the top-level directory and initial super-project directories across multiple HPC systems (RIS, HTCF, Wang cluster).
6. Creating the top-level directory and initial super-project directories on the Mac using Box.
7. Installing PyCharm on macOS and configuring it as the primary interface for the system, including remote filesystem access to multiple HPC systems.
   * ssh
   * alias connect commands
8. Creating a GitHub ELN repository and connecting it to the local directory through PyCharm.
   * Github tokens
   * PyCharm commands (commit, push, update)
9. Creating a GitHub code repository and connecting it to both local and multiple HPC directories through PyCharm.
   * Scratch policies and code
10. Using PyCharm’s remote integration to edit, sync, and run code directly on directories residing on different HPC systems.
11. Building an alias toolbelt to reduce friction in maintaining and operating the system.
    * where aliases and environmental variables live
    * run commands (rc) files that runs every time you start an interactive shell.
      * ls ~/.bashrc
      * ls ~/.zshrc
      * load_cust_commands
      * gitpull_general
      * hearth

## Lesson 2. Selecting the HPRC sample and acquiring the raw data with full provenance.

## Lesson 3. Read QC and trimming decisions (FastQC, CutAdapt).

## Lesson 4. Alignment to the chosen reference and generation of CRAM (BWA-MEM + samtools).

## Lesson 5. Alignment QC and sanity checks (samtools stats and targeted spot checks).

## Lesson 6. Coverage track generation (bedtools genomecov or equivalent) and representation choices.

## Lesson 7. Compression and indexing of tracks for scalable access (bgzip, tabix).

## Lesson 8. Coverage deviation modeling and candidate-region calling.

## Lesson 9. Visualization and interpretation in RStudio (Rmd, ggplot, tidyverse) and export of key figures to the ELN.

## Lesson 10. Publishing results for others (rsync to Box, FTP copy, epigenome browser preparation).

## Lesson 11. Post-run organization, cleanup, and archive packaging for long-term storage.

## Lesson 12. Discussion and reflection.