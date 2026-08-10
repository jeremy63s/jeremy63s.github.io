---
title: "Crackle Gene"
date: 2026-04-29
draft: false
description: "A user-friendly tool for comparing two prokaryotic genomes down to the base — and up to the protein-level consequence."
tags: ["bioinformatics", "python", "streamlit"]
hiddenInHomeList: true
cover:
  image: "images/projects/crackle-gene-cover.png"
  alt: "Crackle Gene logo — Prokaryotic whole-genome comparison"
  relative: false
  hiddenInSingle: true
media:
  kind: "video"
  src: "/videos/projects/crackle-gene-launch.mp4"
links:
  - name: GitHub
    url: https://github.com/jeremy63s/crackle-gene
---

Crackle Gene is a user-friendly tool for comparing two complete prokaryotic genomes and pinpointing exactly what changed between them — down to the individual base, and up to the biological consequence of that change. You give it a reference genome and an evolved (or otherwise modified) genome, and it tells you where they differ, whether each difference falls inside a gene, and what that difference does to the encoded protein.

<!--more-->

## The problem it solves

Directed evolution, adaptive laboratory evolution, and strain-engineering experiments all produce the same core question: my organism now behaves differently — what in its genome is responsible? Answering that today usually means stitching together a pipeline of specialist command-line tools (an aligner, a variant caller, a gene predictor, an annotation lookup), each with its own file formats, coordinate conventions, and failure modes. That workflow is powerful but unforgiving: it assumes the user is comfortable on the command line, knows how to reconcile 0-based and 1-based coordinates, and can mentally translate a raw variant call into "this mutation knocked out that protein."

Crackle Gene collapses that pipeline into a single interactive app. The person running a directed-evolution experiment — often a bench biologist, not a bioinformatician — can paste or upload two FASTA sequences and get an interpreted, annotated comparison without writing a line of code or manually chaining tools.

## Why it's well-suited to prokaryotic and directed-evolution work

A few design choices make it fit this niche specifically:

- **It treats genomes as circular.** Bacterial and plasmid genomes are circular, so the "start" of a linear FASTA file is arbitrary. Crackle Gene rotates both sequences to a common landmark before comparing, so two genomes that are identical but linearized at different points don't produce a wall of spurious differences.
- **It reasons in terms of genes and reading frames, not just bases.** Rather than reporting a bare list of nucleotide changes, it predicts open reading frames (via Prodigal) on both strands and all three frames, tracks which ORFs are active across the alignment, and reports each mutation's effect on the protein — distinguishing point substitutions from insertions and deletions, and following how an indel shifts the downstream reading frame. For directed evolution, this is the difference between "there's a SNP at position 41,802" and "this single-base change introduces a premature stop in the target enzyme."
- **It surfaces the interesting changes automatically.** Two closely related genomes are ~identical almost everywhere; the signal is a handful of mutations buried in millions of bases. Crackle Gene chunks the genome, scores each chunk, and uses anomaly detection to flag the regions that actually diverge, so the user isn't left scrolling through a near-perfect alignment looking for the needle.
- **It connects changes to biology.** For any affected ORF, the user can submit the reference and evolved protein sequences to BLAST directly from the interface, turning "an unknown gene mutated" into "the gene for X acquired this change" without leaving the app.

## Who benefits

Labs running adaptive evolution, mutagenesis, or strain-engineering campaigns get a fast, visual read on which genes their selection pressure actually hit — and can hand that read to collaborators who would never open a terminal. More broadly, anyone comparing two closely related bacterial genomes (before/after, wild-type/mutant, ancestor/descendant) gets an accessible way to go from raw sequence to annotated, protein-level interpretation in one place.

## Built for ease of use

Crackle Gene's real contribution isn't any single algorithm — it's that the tedious, error-prone connective work between algorithms is handled for you. Every feature below exists to remove a step a user would otherwise do by hand.

- **Automatic anomaly detection — you don't have to pick a cutoff.** The naïve way to find changed regions is to set a similarity threshold and hope you chose well: too strict and you drown in false positives, too loose and you miss real mutations. Instead, Crackle Gene profiles each chunk on several independent signals at once — sequence similarity, length ratio, GC-content difference, and ORF density difference between reference and evolved — and fits an Isolation Forest that flags the chunks that stand out from the genome-wide norm. The result is a per-chunk anomaly score plotted as a color-coded bar chart (anomalous chunks in red) with a supporting feature table, so the interesting regions announce themselves. It's on by default, but a manual score threshold is always one toggle away for users who want direct control.
- **Automatic protein pairing — the tool figures out which ORF changed.** A single mutation can fall inside several overlapping reading frames (across strands and frames), and it isn't obvious which reference ORF should be compared against which evolved ORF. Crackle Gene resolves this for you: when a site is ambiguous, it scores every valid reference/evolved pairing by amino-acid overlap and ranks them, then presents the best match — while still letting you inspect the alternatives in a ranked table. Once a pairing is chosen, it renders the reference and evolved sequences side by side with mismatches highlighted and the two sequences coordinate-aligned (padding the one that starts later), so the exact change is visually obvious. A single toggle switches the same view between DNA and amino-acid representations.
- **Integrated Prodigal — gene prediction with nothing to install or invoke.** ORF prediction is done with Prodigal running in metagenomic mode, but the user never touches it: no temp files, no GFF parsing, no coordinate conversion. The pipeline runs it automatically on both strands, converts its output into an active-ORF frame tracker aligned to the genome, and shows progress as it goes. What would normally be a separate command-line step with its own output format is just part of pressing "Run."
- **One-click BLAST on the protein you care about.** Rather than copying a sequence out of the tool, reformatting it as FASTA, and pasting it into the NCBI website, each affected ORF gets a Submit button that sends its amino-acid sequence straight to BLASTp against the nr database and reports the top hits inline. Both the reference and evolved proteins can be submitted, and results are cached and collected on a dedicated results page, so identifying an unknown gene is a click rather than a context switch.
- **Dynamic chunk sizing — fast alignment without tuning.** Smith-Waterman alignment is optimal but quadratic in sequence length, so aligning two whole genomes as single strings is impractical. Crackle Gene divides each genome into sections and aligns them chunk-by-chunk, which keeps every individual alignment small and tractable, and runs a fast diagonal pre-check before committing to the full comparison. Crucially, it chooses a sensible number of chunks automatically from the genome's length — so a small plasmid and a multi-megabase chromosome are both handled well out of the box — while still letting the user override the count if they want.
- **A summary and export page that's ready to share.** Findings don't have to be re-derived to be communicated. A dedicated view lets you select the mutation sites you care about and renders each one as a clean, highlighted reference-vs-evolved block, in DNA or amino-acid form, with BLAST annotations attached. A "Copy all" button puts the whole summary on your clipboard, and a PDF-friendly layout paginates each mutation onto its own page for a printable report — turning an analysis session directly into something you can hand to a collaborator or drop into a lab notebook.
