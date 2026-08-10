---
title: "Peptide functionalized LNPs as an alternative to ADCs"
date: 2026-08-03
draft: false
description: "Antibody-drug conjugates have transformed cancer treatment, but the ones used against lung cancer carry a serious, often fatal side effect: interstitial lung disease. Peptide-functionalized LNPs offer an intriguing alternative; they are far less immunogenic, faster and cheaper to produce, and lack the structures thought to bring on ILD in these patients."
summary: "Antibody-drug conjugates have transformed cancer treatment, but the ones used against lung cancer carry a serious, often fatal side effect: interstitial lung disease. Peptide-functionalized LNPs offer an intriguing alternative; they are far less immunogenic, faster and cheaper to produce, and lack the structures thought to bring on ILD in these patients."
tags: ["drug-delivery", "lipid-nanoparticles", "peptide-engineering", "oncology", "antibody-drug-conjugates"]
hiddenInHomeList: true
cover:
  image: "images/projects/peptide-lnp-adc-cover.jpg"
  alt: "Confocal fluorescence image of cultured cells showing dense cytoskeletal and nuclear staining"
  relative: false
  hiddenInSingle: true
---

<style>
  .pl-note-toggle { display:none; }
  .pl-note-label { color:#5b9df9; cursor:pointer; border-bottom:1px dotted #5b9df9; }
  .pl-note-text { display:none; margin:.5rem 0; padding:.75rem 1rem; background:var(--tertiary); border-left:3px solid #5b9df9; font-size:.9rem; line-height:1.6; border-radius:4px; }
  .pl-note-toggle:checked ~ .pl-note-text { display:block; }
  .pl-divider { border:none; border-top:1px solid var(--content); opacity:.25; margin:2.5rem 0; }
  .pl-placeholder { margin:2rem 0; padding:2.5rem 1.5rem; border:1px dashed var(--content); border-radius:8px; text-align:center; color:var(--secondary); font-size:.9rem; }
  .pl-refs { font-size:.9rem; line-height:1.8; padding-left:1.2rem; }
  .pl-refs a { text-decoration:none; }
  .pl-list { font-size:1rem; line-height:1.7; color:var(--content); padding-left:1.3rem; margin:1rem 0; }
  .pl-list li { margin-bottom:.4rem; }

  .pl-fig { margin:2rem auto; max-width:520px; text-align:center; }
  .pl-fig img { width:100%; height:auto; display:block; border-radius:8px; background:#fff; padding:1rem; box-sizing:border-box; }
  .pl-fig figcaption { margin-top:.6rem; font-size:.85rem; color:var(--secondary); line-height:1.5; text-align:left; }
  .pl-fig-pair-breakout {
    position:relative; left:50%; right:50%; margin-left:-50vw; margin-right:-50vw;
    width:100vw; max-width:100vw; padding:0 clamp(0px, 3vw, 32px); box-sizing:border-box;
    margin-top:2rem;
  }
  .pl-fig-pair { display:grid; grid-template-columns:1fr 1fr; gap:1.25rem; margin:0 auto; max-width:900px; }
  .pl-fig-pair img { width:100%; height:340px; object-fit:contain; display:block; border-radius:8px; background:#fff; padding:.75rem; box-sizing:border-box; }
  .pl-fig-pair-caption { max-width:900px; margin:.6rem auto 2rem; font-size:.85rem; color:var(--secondary); line-height:1.5; text-align:left; }
  @media (max-width:480px) {
    .pl-fig-pair { grid-template-columns:1fr; }
  }

  .pl-compare { display:grid; grid-template-columns:1fr 1fr; gap:1.25rem; margin:2rem 0; }
  .pl-compare-col { border:1px solid var(--border); border-radius:8px; padding:1.25rem 1.4rem; }
  .pl-compare-col h4 { margin:0 0 .8rem; font-size:1rem; }
  .pl-compare-col ul { margin:0; padding-left:1.1rem; font-size:.88rem; line-height:1.6; color:var(--content); }
  .pl-compare-col li { margin-bottom:.4rem; }
  @media (max-width:640px) {
    .pl-compare { grid-template-columns:1fr; }
  }
</style>

Antibody-drug conjugates (ADCs) are one of the more important advances in cancer treatment over the last decade. By chemically attaching a cytotoxic "payload" drug to an antibody that recognizes a marker on the surface of cancer cells, ADCs deliver chemotherapy-grade toxicity with a level of targeting conventional chemotherapy never had, and they've meaningfully improved outcomes across breast, gastric, urothelial, and lung cancers, among others <a href="#pl-ref1" id="pl-cite1">[1]</a>. Trastuzumab deruxtecan — sold as Enhertu — is one of the clearest examples of that promise: in long-term follow-up of its pivotal head-to-head breast cancer trial, it extended median overall survival from 42.7 to 52.6 months compared with the prior standard of care <a href="#pl-ref2" id="pl-cite2">[2]</a>.

But Enhertu also illustrates the platform's most stubborn weakness. Beyond breast cancer, Enhertu is also FDA-approved for HER2-mutant non-small cell lung cancer, and it's in that setting that the platform's biggest liability shows up most clearly. Across the ADCs used against lung cancer, a severe, often irreversible, and sometimes fatal side effect called <a href="https://www.mayoclinic.org/diseases-conditions/interstitial-lung-disease/symptoms-causes/syc-20353108" target="_blank" rel="noopener">interstitial lung disease</a> (ILD) shows up in roughly one in five patients, the highest rate of any tumor type these drugs are used to treat <a href="#pl-ref3" id="pl-cite3">[3]</a>. Critically, ILD isn't specific to any one antibody's target: it occurs when alveolar macrophages in the lung take up circulating ADCs indiscriminately through their Fc receptors <a href="#pl-ref4" id="pl-cite4">[4]</a>. That uptake pathway depends on the same Fc region that gives an ADC its function, so it isn't something that can be engineered away. The current workaround is simply reducing the dose, but even at the lowest dose of Enhertu currently used in the clinic, it still leaves close to one in eight lung cancer patients with a serious lung complication <a href="#pl-ref5" id="pl-cite5">[5]</a>. That's the gap motivating a look at whether a different kind of targeted delivery vehicle could keep the advantage ADCs offer without carrying the same structural liability.

<figure class="pl-fig">
  <img src="/images/projects/peptide-lnp-adc-ild-mechanism.png" alt="Diagram showing an ADC binding an Fc-gamma receptor on a macrophage, being internalized, and triggering increased cytokine production">
  <figcaption>ADC binds to alveolar macrophage via the Fc&gamma;-receptor, the ADC is internalized and releases drug payload causing increased cytokine production leading to cytokine-mediated lung injury <a href="#pl-ref4" id="pl-cite4b">[4]</a>.</figcaption>
</figure>

One alternative is to swap the antibody for something structurally very different: a short peptide, attached not to the drug directly but to the surface of a lipid nanoparticle (LNP) — the same class of delivery vehicle used in mRNA vaccines — which carries the drug payload inside it instead. Peptides have generally been considered inferior to antibodies on the whole: they typically bind their target more weakly, and are degraded by circulating peptidases within minutes to hours after administration. However, peptides provoke little to no immune response, and they're often an order of magnitude cheaper to produce <a href="#pl-ref6" id="pl-cite6">[6]</a>.

<div class="pl-compare">
  <div class="pl-compare-col">
    <h4>IgG antibody (~150 kDa)</h4>
    <ul>
      <li>Carries an Fc region and constant domains that can form immune-recognized neoepitopes once conjugated to a linker and payload</li>
      <li>Produced in mammalian cell culture, with cell-line development, fermentation, and protein-folding quality control</li>
      <li>Production timeline typically measured in weeks to months</li>
    </ul>
  </div>
  <div class="pl-compare-col">
    <h4>Linear / multimerized peptide (~1&ndash;3 kDa)</h4>
    <ul>
      <li>No Fc region</li>
      <li>Significantly less immunogenic than antibodies</li>
      <li>Made by chemical synthesis: no cell line, no fermentation</li>
      <li>Production timeline typically measured in days</li>
    </ul>
  </div>
</div>

Additionally, the weaknesses of a peptide compared to an antibody as a ligand can be largely engineered away. Building on work from Kathlynn Brown's lab <a href="#pl-ref7" id="pl-cite7">[7]</a>, I created an LNP decorated with a peptide generated to bind to mucin 4, achieving a binding affinity (K<sub>D</sub>) below 9 nanomolar. For context, kinetic measurements of trastuzumab, the antibody inside Enhertu, put its own K<sub>D</sub> around 1&ndash;5 nM <a href="#pl-ref8" id="pl-cite8">[8]</a>.

<figure class="pl-fig">
  <img src="/images/projects/peptide-lnp-adc-kd-curve.png" alt="M4-3 peptide binding curve showing relative fluorescence units versus LNP concentration in nanomolar, with a K_D below 9 nanomolar">
</figure>

Given:

<ul class="pl-list">
  <li>the recent maturation of in-silico tools and pipelines like HADDOCK, ESMFold, and others, and</li>
  <li>that this peptide came from a simple linear random library,</li>
</ul>

there is reason to believe further optimization could yield a substantial <label for="pl-note-kd" class="pl-note-label">reduction in KD</label><input type="checkbox" id="pl-note-kd" class="pl-note-toggle"><span class="pl-note-text">Note: a reduction in KD is an increase in binding affinity.</span>.

The LNP scaffold itself also brings a delivery advantage: LNPs can be aerosolized and delivered by nebulizer, whereas whole antibodies are notoriously difficult to nebulize. The physical stress of aerosolization tends to unfold and aggregate the protein, and those aggregates are themselves capable of triggering an inflammatory response <a href="#pl-ref9" id="pl-cite9">[9]</a>. Inhaled liposomal formulations, by contrast, are already established in pulmonary medicine <a href="#pl-ref10" id="pl-cite10">[10]</a>. That matters directly for the ILD problem described above: an LNP delivered by inhalation can be concentrated at the tissue it needs to reach without ever entering systemic circulation in appreciable amounts, retaining the same kind of localization advantage ADCs get from tumor targeting, without ever presenting the Fc region that lets alveolar macrophages indiscriminately take up circulating ADCs in the first place.

<div class="pl-fig-pair-breakout">
  <div class="pl-fig-pair">
    <img src="/images/projects/peptide-lnp-adc-biodistribution.png" alt="Biodistribution of intranasally delivered M4-3-decorated LNPs across liver, spleen, kidney, heart, brain, and lungs over 3 days, showing preferential accumulation in the lungs">
    <img src="/images/projects/peptide-lnp-adc-biodistribution-ip.png" alt="Biodistribution of intraperitoneally delivered M4-3-decorated LNPs across liver, spleen, kidney, heart, brain, and lung over 3 days, showing accumulation concentrated in the liver and lung">
  </div>
  <p class="pl-fig-pair-caption">Comparison of LNP distribution between nasally vs intraperitoneally administered LNPs over time</p>
</div>

Protocols for loading highly potent "warhead therapeutics" into liposomes already exist, including a derivative of deruxtecan (the same payload used in Enhertu) <a href="#pl-ref11" id="pl-cite11">[11]</a>, though to my knowledge this has not yet been combined with a peptide-targeted LNP. Put together, a peptide-guided LNP platform offers a path to the same kind of targeted delivery that makes ADCs effective, yet:

<ul class="pl-list">
  <li>Is a fraction of the cost to develop and manufacture</li>
  <li>Does not have the same immunogenicity risks that come with antibodies</li>
  <li>Has the option to be delivered via nebulization</li>
  <li>And sidesteps entirely the mechanism by which ILD manifests itself</li>
</ul>

<p align="center"><em>More to come…</em></p>

## References

<ol class="pl-refs">
<li id="pl-ref1">Wu D, Yang K, He R, Yin R, Shui L. Antibody-drug conjugates in cancer therapy: current advances and prospects for breakthroughs. <em>Front Cell Dev Biol</em>. 2025;13:1669592. <a href="https://doi.org/10.3389/fcell.2025.1669592" target="_blank" rel="noopener">https://doi.org/10.3389/fcell.2025.1669592</a> <a href="#pl-cite1">↩</a></li>
<li id="pl-ref2">Cortés J, Hurvitz SA, Im SA, et al. Trastuzumab deruxtecan versus trastuzumab emtansine in HER2-positive metastatic breast cancer: long-term survival analysis of the DESTINY-Breast03 trial. <em>Nat Med</em>. 2024;30(8):2208–2215. <a href="https://doi.org/10.1038/s41591-024-03021-7" target="_blank" rel="noopener">https://doi.org/10.1038/s41591-024-03021-7</a> <a href="#pl-cite2">↩</a></li>
<li id="pl-ref3">Honnorat E, et al. Association of ADC target expression and interstitial lung disease in non-small cell lung cancer. <em>Cancers</em>. 2024;16(22):3753. <a href="#pl-cite3">↩</a></li>
<li id="pl-ref4">Koganemaru S, Fuchigami H, Morizono C, Shinohara H, Kuboki Y, Furuuchi K, Uenaka T, Doi T, Yasunaga M. Potential mechanisms of interstitial lung disease induced by antibody&ndash;drug conjugates based on quantitative analysis of drug distribution. <em>Mol Cancer Ther</em>. 2025;24(2):242&ndash;250. <a href="https://doi.org/10.1158/1535-7163.MCT-24-0267" target="_blank" rel="noopener">https://doi.org/10.1158/1535-7163.MCT-24-0267</a> <a href="#pl-cite4">↩</a> <a href="#pl-cite4b">↩</a></li>
<li id="pl-ref5">Janne PA, et al. Trastuzumab deruxtecan in HER2-mutant metastatic non-small cell lung cancer: primary results from DESTINY-Lung02. <em>J Clin Oncol</em>. 2023. <a href="#pl-cite5">↩</a></li>
<li id="pl-ref6">Liu M, Fang X, Yang Y, Wang C. Peptide-enabled targeted delivery systems for therapeutic applications. <em>Front Bioeng Biotechnol</em>. 2021;9:701504. <a href="https://doi.org/10.3389/fbioe.2021.701504" target="_blank" rel="noopener">https://doi.org/10.3389/fbioe.2021.701504</a> &middot; Wang L, Wang N, Zhang W, et al. Therapeutic peptides: current applications and future directions. <em>Signal Transduct Target Ther</em>. 2022;7:48. <a href="https://doi.org/10.1038/s41392-022-00904-4" target="_blank" rel="noopener">https://doi.org/10.1038/s41392-022-00904-4</a> <a href="#pl-cite6">↩</a></li>
<li id="pl-ref7">Gray BP, Li S, Brown KC. From phage display to nanoparticle delivery: functionalizing liposomes with multivalent peptides improves targeting to a cancer biomarker. <em>Bioconjug Chem</em>. 2013;24(1):85–96. <a href="https://doi.org/10.1021/bc300498d" target="_blank" rel="noopener">https://doi.org/10.1021/bc300498d</a> <a href="#pl-cite7">↩</a></li>
<li id="pl-ref8">Lua WH, Gan SKE, Lane DP, Verma CS. A search for synergy in the binding kinetics of trastuzumab and pertuzumab whole and F(ab) to Her2. <em>NPJ Breast Cancer</em>. 2015;1:15012. <a href="https://doi.org/10.1038/npjbcancer.2015.12" target="_blank" rel="noopener">https://doi.org/10.1038/npjbcancer.2015.12</a> <a href="#pl-cite8">↩</a></li>
<li id="pl-ref9">Sécher T, Bodier-Montagutelli E, Parent C, et al. Aggregates associated with instability of antibodies during aerosolization induce adverse immunological effects. <em>Pharmaceutics</em>. 2022;14(3):671. <a href="https://doi.org/10.3390/pharmaceutics14030671" target="_blank" rel="noopener">https://doi.org/10.3390/pharmaceutics14030671</a> <a href="#pl-cite9">↩</a></li>
<li id="pl-ref10">Shirley M. Amikacin liposome inhalation suspension: a review in <em>Mycobacterium avium</em> complex lung disease. <em>Drugs</em>. 2019;79(5):555–562. <a href="https://doi.org/10.1007/s40265-019-01095-z" target="_blank" rel="noopener">https://doi.org/10.1007/s40265-019-01095-z</a> <a href="#pl-cite10">↩</a></li>
<li id="pl-ref11">Li J, Yu J, Zhang B, et al. Rational design of DXd derivatives for liposomal drug delivery: towards safer and more effective cancer treatments. <em>Int J Pharm</em>. 2025;678:125688. <a href="https://doi.org/10.1016/j.ijpharm.2025.125688" target="_blank" rel="noopener">https://doi.org/10.1016/j.ijpharm.2025.125688</a> <a href="#pl-cite11">↩</a></li>
</ol>
