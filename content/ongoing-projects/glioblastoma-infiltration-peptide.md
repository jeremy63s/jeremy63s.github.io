---
title: "Generating a peptide to reduce glioblastoma infiltration"
date: 2026-08-01
draft: false
description: "A glypican-5-targeting peptide designed to dampen the neuronal hyperexcitability that drives glioblastoma growth and invasion."
summary: "Glioblastomas are among the most deadly cancers due in large part to how they interact with healthy tissue at the tumor margin. They tend to be highly infiltrative, extending cancerous projections far into healthy tissue. This makes complete clean resection by a neurosurgeon essentially impossible in most cases. Here I present data exploring a mechanism that may contribute to this effect, as well as data on a peptide I generated against glypican 5 that dampens crucial drivers of this effect."
tags: ["glioblastoma", "neuro-oncology", "peptide-engineering", "phage-display", "glypican-5"]
hiddenInHomeList: true
cover:
  image: "images/projects/glioblastoma-infiltration-peptide-cover.png"
  alt: "Confocal fluorescence image of cultured neurons showing synaptic puncta (green), dendritic/axonal processes (red), and nuclei (blue)"
  relative: false
  hiddenInSingle: true
---

<style>
  .kg-note-toggle { display:none; }
  .kg-note-label { color:#5b9df9; cursor:pointer; border-bottom:1px dotted #5b9df9; }
  .kg-note-text { display:none; margin:.5rem 0; padding:.75rem 1rem; background:var(--tertiary); border-left:3px solid #5b9df9; font-size:.9rem; line-height:1.6; border-radius:4px; }
  .kg-note-toggle:checked ~ .kg-note-text { display:block; }
  .kg-divider { border:none; border-top:1px solid var(--content); opacity:.25; margin:2.5rem 0; }
  .kg-figure { margin:2rem 0; padding:2.5rem 1.5rem; border:1px dashed var(--content); border-radius:8px; text-align:center; color:var(--secondary); font-size:.9rem; }
  .kg-fig-breakout {
    position:relative; left:50%; right:50%; margin-left:-50vw; margin-right:-50vw;
    width:100vw; max-width:100vw; padding:0 clamp(0px, 3vw, 32px); box-sizing:border-box;
    margin-top:1.75rem; margin-bottom:1.75rem;
  }
  .kg-fig-grid { display:grid; grid-template-columns: 1fr 1fr; gap:1.25rem; max-width:900px; margin:0 auto; }
  .kg-fig { margin:0; text-align:center; }
  .kg-fig img { width:100%; height:auto; border-radius:6px; background:#000; display:block; }
  .kg-fig-grid img { height:380px; object-fit:contain; }
  .kg-fig figcaption { margin-top:.5rem; font-size:.85rem; color:var(--secondary); line-height:1.5; }
  .kg-fig-row-bottom { display:flex; gap:2rem; justify-content:center; align-items:flex-end; flex-wrap:wrap; margin:1.75rem 0; }
  .kg-fig-intact { width:150px; }
  .kg-fig-chart { width:360px; max-width:100%; }
  .kg-fig-chart-lg { width:600px; max-width:100%; margin:0 auto; }
  .kg-neuron-grid { display:grid; grid-template-columns: repeat(3, 1fr); gap:14px; max-width:820px; margin:0 auto; }
  .kg-neuron-grid img { width:100%; aspect-ratio: 8/7; object-fit:cover; border-radius:4px; border:1px solid var(--border); background:transparent; display:block; }
  @media (max-width: 560px) {
    .kg-neuron-grid { grid-template-columns: repeat(3, 1fr); gap:8px; }
  }
  @media (max-width: 700px) {
    .kg-fig-grid { grid-template-columns: 1fr; }
  }
  .kg-refs { font-size:.9rem; line-height:1.8; padding-left:1.2rem; }
  .kg-refs a { text-decoration:none; }
  .kg-fig-hero { max-width:640px; margin:0 auto 2.25rem; }
</style>

<figure class="kg-fig kg-fig-hero">
  <img src="/images/projects/glioblastoma-infiltration-peptide-gfp-infiltration.png" alt="Coronal section of a GFP-labeled mouse glioma (green) showing extensive infiltration along white matter into the contralateral hemisphere, against a DAPI-stained (blue) background">
  <figcaption>"Glioblastoma (GBM) is the most aggressive and lethal form of brain tumor. Despite treatment, GBM recurrence is inevitable and tends to occur outside surgical margins or in locations remote to the primary tumor, highlighting the central role played by tumor infiltration in this malicious disease." <a href="#kg-ref11" id="kg-cite11">[11]</a></figcaption>
</figure>

Glioblastomas are among the most deadly cancers, full stop. With an average five-year survival rate of just 5% to 7%, research and innovation in the treatment of these tumors is essential. There has been rapidly growing interest in a critical interplay between glioblastomas and the surrounding neurons: neuronal activity has been established as a driver of glioma proliferation and infiltration <a href="#kg-ref1" id="kg-cite1">[1]</a>, leading these tumors to progress faster and become much harder for a surgeon to resect. Glioblastomas are also known to drive hyperexcitability through the release of toxic levels of glutamate <a href="#kg-ref2" id="kg-cite2">[2]</a>, setting the stage for a pernicious positive feedback loop. It is for these reasons that a compound capable of putting the brakes on this process is of utmost interest in the treatment of gliomas.

To address this, I generated a peptide (affectionately nicknamed "Kegstand") against <label for="kg-note-gpc5" class="kg-note-label">rh-glypican 5</label><input type="checkbox" id="kg-note-gpc5" class="kg-note-toggle"><span class="kg-note-text">Note: the glypican 5 used as bait was generated in eukaryotic cells (mouse) as we suspect the glycosylation may play a role in its effect on synapses.</span>. The reasons glypican 5 makes a good target, I reasoned, are:

- It is emerging that glypican 5 plays a role in the stabilization and strength of synaptic connections <a href="#kg-ref3" id="kg-cite3">[3]</a>.
- Glypican 5 appears to internalize slowly and only to a limited extent relative to classic internalizing drug targets, allowing me to sidestep the infamous "binding-site barrier" that plagues targeted drug delivery <a href="#kg-ref6" id="kg-cite6">[6]</a>, <a href="#kg-ref7" id="kg-cite7">[7]</a>. Because my payload is designed to act through a bystander effect rather than requiring receptor-mediated uptake, this limited internalization is a feature rather than a liability.
- Several glypican-family proteins are implicated in stress-response pathways <a href="#kg-ref8" id="kg-cite8">[8]</a>, <a href="#kg-ref9" id="kg-cite9">[9]</a>, and evidence from past projects suggests that glypican-5 may be upregulated in regions of high cellular stress (neurosphere and colocalization data), implying that glypican 5 is likely abundant in these hyper-excitable, glutamate-rich milieux <a href="#kg-ref4" id="kg-cite4">[4]</a>, <a href="#kg-ref10" id="kg-cite10">[10]</a>.

It is important to keep in mind that these errant, over-excited neurons in the tumor margins are not themselves unique, and thus any activity my peptide has on them would also translate to normal, healthy neurons — not ideal. This is why I use a multimerization scheme that builds off of the work of Kathlynn Brown <a href="#kg-ref5" id="kg-cite5">[5]</a> to keep distribution of this peptide local to the tumor and away from healthy tissue.

<hr class="kg-divider">

<div class="kg-fig-breakout">
  <div class="kg-fig-grid">
    <figure class="kg-fig">
      <img src="/images/projects/glioblastoma-infiltration-peptide-coronal-section.png" alt="Coronal brain section showing peptide accumulation concentrated in the glioblastoma relative to surrounding healthy tissue">
      <figcaption>Coronal section: peptide accumulation in glioblastoma versus healthy tissue.</figcaption>
    </figure>
    <figure class="kg-fig">
      <img src="/images/projects/glioblastoma-infiltration-peptide-coronal-zoom.png" alt="Zoomed-in view of the tumor region from the coronal section, showing dense peptide signal within the tumor margin">
      <figcaption>Zoomed view of the tumor region above.</figcaption>
    </figure>
  </div>
</div>

<div class="kg-fig-row-bottom">
  <figure class="kg-fig kg-fig-intact">
    <img src="/images/projects/glioblastoma-infiltration-peptide-intact-brain.png" alt="Whole intact brain showing a single focal region of fluorescent peptide signal">
    <figcaption>Intact brain: peptide signal localizes to the tumor.</figcaption>
  </figure>
  <figure class="kg-fig kg-fig-chart">
    <img src="/images/projects/glioblastoma-infiltration-peptide-biodistribution-quant.png" alt="Bar graph quantifying peptide accumulation inside versus outside the tumor region, comparing the targeting peptide (G5-2) to a non-targeting control (Azide)">
    <figcaption>Quantification of peptide accumulation inside versus outside the tumor region, for the targeting peptide (G5-2, left) and a non-targeting control (Azide, right).</figcaption>
  </figure>
</div>

<hr class="kg-divider">

As part of a "reverse rescue"–style experiment, I divided otherwise identical plates of neurons into three groups: one that received additional soluble glypican 5 on the first day in vitro (DIV), one that received identical glypican 5 plus a daily administration of Kegstand peptide, and one cultured according to standard neuron culture protocol as a control. I then fixed and stained for synapses and nuclei; the images were then quantified by number of synapses per neuron to investigate both:

- the connection between glypican 5 and synaptic formation, and
- the effect my peptide, Kegstand, has on neuronal processes and structures.

<hr class="kg-divider">

<div class="kg-fig-breakout">
  <figure class="kg-fig">
    <div class="kg-neuron-grid">
      <img src="/images/projects/glioblastoma-infiltration-peptide-neuron-gpc5-merged.png" alt="+GPC5, merged channels: synapses, processes, and nuclei">
      <img src="/images/projects/glioblastoma-infiltration-peptide-neuron-gpc5-peptide-merged.png" alt="+GPC5 +peptide, merged channels: synapses, processes, and nuclei">
      <img src="/images/projects/glioblastoma-infiltration-peptide-neuron-control-merged.png" alt="Control, merged channels: synapses, processes, and nuclei">
      <img src="/images/projects/glioblastoma-infiltration-peptide-neuron-gpc5-green.png" alt="+GPC5, synaptic marker channel alone">
      <img src="/images/projects/glioblastoma-infiltration-peptide-neuron-gpc5-peptide-green.png" alt="+GPC5 +peptide, synaptic marker channel alone">
      <img src="/images/projects/glioblastoma-infiltration-peptide-neuron-control-green.png" alt="Control, synaptic marker channel alone">
    </div>
    <figcaption>Confocal images of cultured neurons across the three conditions — left to right: +GPC5, +GPC5 +peptide, Control. Top row: merged channels (synapses, processes, nuclei); bottom row: synaptic marker channel alone.</figcaption>
  </figure>
</div>

<figure class="kg-fig kg-fig-chart-lg">
  <img src="/images/projects/glioblastoma-infiltration-peptide-synapse-quant.png" alt="Bar graph of synapses per neuron across Day 7, Day 10, and Day 14 for Control, GPC5, and Peptide+GPC5 conditions">
  <figcaption>Synapses per neuron (mean ± SD) at days 7, 10, and 14 across the three conditions.</figcaption>
</figure>

<hr class="kg-divider">

The data shows that neurons cultured in the presence of extra glypican 5 do indeed form synapses more readily than the control neurons at the same time points, with that difference only increasing at later time points. The neurons that received both excess glypican 5 and Kegstand peptide showed only slightly elevated synapse formation relative to the control group.

Investigation into Kegstand's effects on the electrical activity of neurons is currently ongoing as of August 2026; beyond this, I have studies planned to probe these questions in vivo.

<p align="center"><em>More to come…</em></p>

## References

<ol class="kg-refs">
<li id="kg-ref1">Venkatesh HS, Morishita W, Geraghty AC, et al. Electrical and synaptic integration of glioma into neural circuits. <em>Nature</em>. 2019;573(7775):539–545. <a href="https://doi.org/10.1038/s41586-019-1563-y" target="_blank" rel="noopener">https://doi.org/10.1038/s41586-019-1563-y</a> <a href="#kg-cite1">↩</a></li>
<li id="kg-ref2">Buckingham SC, Campbell SL, Haas BR, Montana V, Robel S, Ogunrinu T, Sontheimer H. Glutamate release by primary brain tumors induces epileptic activity. <em>Nat Med</em>. 2011;17(10):1269–1274. <a href="https://doi.org/10.1038/nm.2453" target="_blank" rel="noopener">https://doi.org/10.1038/nm.2453</a> <a href="#kg-cite2">↩</a></li>
<li id="kg-ref3">Bosworth AP, Contreras M, Sancho L, Salas IH, Paumier A, Novak SW, Manor U, Allen NJ. Astrocyte glypican 5 regulates synapse maturation and stabilization. <em>Cell Rep</em>. 2025;44(3):115374. <a href="https://doi.org/10.1016/j.celrep.2025.115374" target="_blank" rel="noopener">https://doi.org/10.1016/j.celrep.2025.115374</a> <a href="#kg-cite3">↩</a></li>
<li id="kg-ref4">Yu K, Lin CCJ, Hatcher A, Lozzi B, Kong K, Huang-Hobbs E, et al. PIK3CA variants selectively initiate brain hyperactivity during gliomagenesis. <em>Nature</em>. 2020;578(7793):166–171. <a href="https://doi.org/10.1038/s41586-020-1952-2" target="_blank" rel="noopener">https://doi.org/10.1038/s41586-020-1952-2</a> <a href="#kg-cite4">↩</a></li>
<li id="kg-ref5">Gray BP, Li S, Brown KC. From phage display to nanoparticle delivery: functionalizing liposomes with multivalent peptides improves targeting to a cancer biomarker. <em>Bioconjug Chem</em>. 2013;24(1):85–96. <a href="https://doi.org/10.1021/bc300498d" target="_blank" rel="noopener">https://doi.org/10.1021/bc300498d</a> <a href="#kg-cite5">↩</a></li>
<li id="kg-ref6">Fujimori K, Covell DG, Fletcher JE, Weinstein JN. A modeling analysis of monoclonal antibody percolation through tumors: a binding-site barrier. <em>J Nucl Med</em>. 1990;31(7):1191–1198. <a href="https://jnm.snmjournals.org/content/31/7/1191" target="_blank" rel="noopener">https://jnm.snmjournals.org/content/31/7/1191</a> <a href="#kg-cite6">↩</a></li>
<li id="kg-ref7">Thurber GM, Schmidt MM, Wittrup KD. Antibody tumor penetration: transport opposed by systemic and antigen-mediated clearance. <em>Adv Drug Deliv Rev</em>. 2008;60(12):1421–1434. <a href="https://doi.org/10.1016/j.addr.2008.04.012" target="_blank" rel="noopener">https://doi.org/10.1016/j.addr.2008.04.012</a> <a href="#kg-cite7">↩</a></li>
<li id="kg-ref8">Ebong EE, Lopez-Quintero SV, Rizzo V, Spray DC, Tarbell JM. Shear-induced endothelial NOS activation and remodeling via heparan sulfate, glypican-1, and syndecan-1. <em>Integr Biol (Camb)</em>. 2014;6(3):338–347. <a href="https://doi.org/10.1039/c3ib40199e" target="_blank" rel="noopener">https://doi.org/10.1039/c3ib40199e</a> <a href="#kg-cite8">↩</a></li>
<li id="kg-ref9">Cheng F, Mani K, van den Born J, Ding K, Belting M, Fransson LÅ. Nitric oxide-dependent processing of heparan sulfate in recycling S-nitrosylated glypican-1 takes place in caveolin-1-containing endosomes. <em>J Biol Chem</em>. 2002;277(46):44431–44439. <a href="https://doi.org/10.1074/jbc.M205241200" target="_blank" rel="noopener">https://doi.org/10.1074/jbc.M205241200</a> <a href="#kg-cite9">↩</a></li>
<li id="kg-ref10">Chung WJ, Lyons SA, Nelson GM, Hamza H, Gladson CL, Gillespie GY, Sontheimer H. Inhibition of cystine uptake disrupts the growth of primary brain tumors. <em>J Neurosci</em>. 2005;25(31):7101–7110. <a href="#kg-cite10">↩</a></li>
<li id="kg-ref11">Huang-Hobbs E, Cheng YT, Ko Y, Luna-Figueroa E, Lozzi B, Taylor KR, McDonald M, He P, Chen HC, Yang Y, Maleki E, Lee ZF, Murali S, Williamson MR, Choi D, Curry R, Bayley J, Woo J, Jalali A, Monje M, Noebels JL, Harmanci AS, Rao G, Deneen B. Remote neuronal activity drives glioma progression through SEMA4F. <em>Nature</em>. 2023;619(7971):844–850. <a href="https://doi.org/10.1038/s41586-023-06267-2" target="_blank" rel="noopener">https://doi.org/10.1038/s41586-023-06267-2</a> <a href="#kg-cite11">↩</a></li>
</ol>
