---
title: "Building an in-house tissue clearing system"
date: 2025-01-01
weight: 3
draft: false
description: "Despite the ubiquity of cryostats and microtomes, important structures such as long range neural connections and highly necrotic tumor cores often do not survive histological sectioning. Tissue clearing addresses this by making whole organs transparent so they can be imaged intact in 3D. However, commercial clearing systems are an expensive investment, but every function they perform can be assembled from equipment already found in most biology labs."
summary: "Tissue clearing renders whole organs optically transparent, letting researchers image intact tissue in three dimensions rather than reconstructing it from thin sections, and it has quickly grown in popularity. Off-the-shelf clearing systems, however, are an expensive investment for a lab that already owns a cryostat or microtome. Here I describe the pros of tissue clearing, why building a clearing system in house may be an attractive solution for many labs, and why tissue clearing was required for me to study the development of necrotic cores in glioblastomas."
tags: ["tissue-clearing", "clarity", "imaging", "lab-engineering"]
hiddenInHomeList: true
hideMeta: true
cover:
  image: "images/projects/tissue-clearing-cover.jpg"
  alt: "CLARITY-cleared tissue sample, transparent enough to read printed text through it"
  relative: false
  hiddenInSingle: true
---

<style>
  .tc-placeholder { margin:2rem 0; padding:2.5rem 1.5rem; border:1px dashed var(--content); border-radius:8px; text-align:center; color:var(--secondary); font-size:.9rem; }
  .tc-refs { font-size:.9rem; line-height:1.8; padding-left:1.2rem; }
  .tc-refs a { text-decoration:none; }
  .tc-gallery { display:flex; gap:.75rem; overflow-x:auto; scroll-snap-type:x mandatory; -webkit-overflow-scrolling:touch; margin:2rem 0 .5rem; padding-bottom:.5rem; }
  .tc-gallery img { height:340px; width:auto; flex:0 0 auto; scroll-snap-align:start; border-radius:8px; display:block; }
  .tc-gallery-caption { margin:0 0 2rem; font-size:.85rem; color:var(--secondary); line-height:1.5; }
  @media (max-width:480px) {
    .tc-gallery img { height:260px; }
  }
  .tc-pair { display:grid; grid-template-columns:1fr 1fr; gap:1rem; margin:0 0 .6rem; }
  .tc-pair img { width:100%; aspect-ratio:4/3; object-fit:cover; border-radius:8px; display:block; }
</style>

<div class="tc-pair">
  <img src="/images/projects/tissue-clearing-sample-2.jpg" alt="CLARITY-cleared mouse brain on printed text, with the text visible through the tissue">
  <img src="/images/projects/tissue-clearing-cover.jpg" alt="CLARITY-cleared mouse brain, transparent enough to read printed text through it">
</div>
<p class="tc-gallery-caption">Cleared mouse brain using a built-in-house tissue clearing system</p>

Most of what we know about the structure of tissue comes from looking at it in thin slices. A cryostat or microtome cuts an organ into sections a few to a few dozen microns thick, each section is stained and imaged, and any three-dimensional picture has to be reconstructed after the fact. That works, but it destroys the very thing you often want to see: long-range connections, like axons projecting across a brain, a tumor's projections into surrounding tissue, or structurally unsound necrotic regions get cut into fragments, either getting lost completely or requiring tedious, error prone reconstruction.

Modern tissue clearing takes a different approach. Tissue is opaque mainly because lipids scatter light; remove the lipids while holding the proteins and nucleic acids in place, then match the refractive index of what remains, and an entire organ becomes transparent enough to image intact. CLARITY, developed by Karl Deisseroth and Kwanghun Chung, relies on infusing acrylamide monomers into the tissue and polymerizing them into a hydrogel mesh, then washing the lipids out with detergent <a href="#tc-ref1" id="tc-cite1">[1]</a>. Since then, tissue clearing has grown into a whole family of methods and an increasingly popular technique across neuroscience, oncology, and developmental biology <a href="#tc-ref2" id="tc-cite2">[2]</a><a href="#tc-ref3" id="tc-cite3">[3]</a>.

<div class="tc-gallery">
  <img src="/images/projects/tissue-clearing-setup-1.jpg" alt="Full in-house CLARITY clearing setup: power supply, water bath with SDS reservoir and buffer filter, recirculating pump, and clearing chamber connected by tubing" loading="lazy">
  <img src="/images/projects/tissue-clearing-setup-2.jpg" alt="Gel electrophoresis power supply running the tissue clearing program at 40 V" loading="lazy">
  <img src="/images/projects/tissue-clearing-setup-3.jpg" alt="Electrophoretic clearing chamber with electrode leads and inlet/outlet tubing" loading="lazy">
  <img src="/images/projects/tissue-clearing-setup-4.jpg" alt="Temperature-controlled water bath holding the SDS clearing solution reservoir and buffer filter" loading="lazy">
  <img src="/images/projects/tissue-clearing-setup-5.jpg" alt="Close-up of the SDS clearing solution reservoir in the water bath" loading="lazy">
</div>
<p class="tc-gallery-caption">The in-house electrophoretic tissue clearing setup.</p>

In most labs, tissue clearing is done using a commercial tissue clearing system. These systems represent a substantial investment, especially for labs that are smaller and/or already have access to a microtome or cryostat. The high opportunity cost of purchasing these systems usually precludes labs from implementing tissue clearing protocols at all.

However, the jobs that these systems do are relatively easy to recreate using equipment typically already present in biology labs for a fraction of the cost. Following the CLARITY protocol <a href="#tc-ref4" id="tc-cite4">[4]</a>, I was able to create a working tissue clearing system that I used to investigate the formation and 3D distribution of necrotic cores in orthotopic glioblastomas.

## References

<ol class="tc-refs">
<li id="tc-ref1">Chung K, Wallace J, Kim SY, et al. Structural and molecular interrogation of intact biological systems. <em>Nature</em>. 2013;497(7449):332&ndash;337. <a href="https://doi.org/10.1038/nature12107" target="_blank" rel="noopener">https://doi.org/10.1038/nature12107</a> <a href="#tc-cite1">↩</a></li>
<li id="tc-ref2">Richardson DS, Lichtman JW. Clarifying tissue clearing. <em>Cell</em>. 2015;162(2):246&ndash;257. <a href="https://doi.org/10.1016/j.cell.2015.06.067" target="_blank" rel="noopener">https://doi.org/10.1016/j.cell.2015.06.067</a> <a href="#tc-cite2">↩</a></li>
<li id="tc-ref3">Ueda HR, Ert&uuml;rk A, Chung K, et al. Tissue clearing and its applications in neuroscience. <em>Nat Rev Neurosci</em>. 2020;21(2):61&ndash;79. <a href="https://doi.org/10.1038/s41583-019-0250-1" target="_blank" rel="noopener">https://doi.org/10.1038/s41583-019-0250-1</a> <a href="#tc-cite3">↩</a></li>
<li id="tc-ref4">Chung Lab. CLARITY protocol. 2016. <a href="https://static1.squarespace.com/static/561beb9ae4b0edc5a7075cf2/t/57ba20d69f7456e36f2f6ce3/1504722155038/Chung+lab_CLARITY+protocol_08192016.pdf" target="_blank" rel="noopener">PDF</a> <a href="#tc-cite4">↩</a></li>
</ol>
