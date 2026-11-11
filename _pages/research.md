---
layout: page
title: research
permalink: /research/
description: Electrified post-combustion CO₂ capture by magnetic induction swing adsorption (MISA) — dynamic cycle modelling in IDAES/Pyomo, surrogate modelling and multi-objective optimisation.
nav: true
nav_order: 1
---

{% comment %}
DRAFT. Before merging to main:
- Add the two figures marked TODO below (files go in assets/img/research/).
- Check every sentence against the published papers.
{% endcomment %}

## Electrifying CO₂ capture with induction-heated adsorbents

Temperature-swing adsorption usually regenerates the sorbent with steam or hot purge gas, which ties the capture unit to a heat supply and heats the bed slowly from the outside. **Magnetic induction swing adsorption (MISA)** instead heats a magnetic composite adsorbent directly, from inside the particles, with an alternating magnetic field. Regeneration then runs on electricity and can be fast and localised.

My PhD at [NTNU](https://www.ntnu.edu/ept), supervised by Prof. Thomas A. Adams II and funded through the NTNU–MIT Energy Research Programme (NMERP-C2), asks how MISA cycles should be designed, and what trade-offs they face, for post-combustion CO₂ capture. The adsorbent studied is the Fe₃O₄@HKUST-1 composite.

{% comment %}
TODO figure 1: MISA cycle schematic (steps of one cycle, with induction heating marked).
<div class="row justify-content-sm-center">
  <div class="col-sm-10 mt-3 mt-md-0">
    {% include figure.liquid path="assets/img/research/misa-cycle.png" class="img-fluid rounded z-depth-1" zoomable=true alt="Schematic of a magnetic induction swing adsorption cycle" caption="One MISA cycle. Replace with the final schematic." %}
  </div>
</div>
{% endcomment %}

## Approach

**First-principles dynamic models.** I build dynamic models of complete MISA cycles in [IDAES](https://idaes.org/)/[Pyomo](https://www.pyomo.org/). The isotherm, breakthrough and induction-heated desorption behaviour is calibrated and checked against published experimental data for Fe₃O₄@HKUST-1.

**Surrogates and active learning.** Full cycle simulations are expensive, so I train Gaussian-process surrogates on them and choose new simulation points by active learning.

**Multi-objective optimisation.** On the surrogates I run NSGA-II and MOPSO to map the purity–recovery and productivity–energy trade-offs of competing cycle designs.

{% comment %}
TODO figure 2: one Pareto front from the ChERD paper (purity–recovery or productivity–energy), with permission or redrawn.
<div class="row justify-content-sm-center">
  <div class="col-sm-10 mt-3 mt-md-0">
    {% include figure.liquid path="assets/img/research/pareto.png" class="img-fluid rounded z-depth-1" zoomable=true alt="Pareto fronts for four MISA cycle configurations" caption="Trade-offs between cycle configurations. Replace with the final figure." %}
  </div>
</div>
{% endcomment %}

## Results so far

- **Simulation framework:** an open-source IDAES framework for inductively heated adsorption, presented at ESCAPE-36 ([paper](https://doi.org/10.69997/sct.177673), [LAPSE:2026.0302](https://psecommunity.org/LAPSE:2026.0302)). The isotherm data, model equations and isotherm-fitting notebook are openly available as [supplementary material on LAPSE](https://psecommunity.org/LAPSE:2025.0725) (CC BY-SA 4.0).
- **Cycle design and optimisation:** four MISA cycle configurations, simulated and optimised, published in [_Chemical Engineering Research and Design_ 234, 720–739 (2026)](https://doi.org/10.1016/j.cherd.2026.09.029). The configuration code, simulation outputs and surrogate models are archived as [supplementary information on LAPSE](https://psecommunity.org/LAPSE:2026.0046) (CC BY-NC 4.0).
- **Recognition:** [Student Poster Award at GHGT-18](/news/2026-10-29-ghgt18-award/), Perth, 2026, among over 400 e-posters.

## Current work

I am extending the framework to temperature- and vacuum-swing (TVSA/VSA) cycles for the same magnetite–MOF adsorbent, and using batch Bayesian optimisation (qNEHVI) for sample-efficient multi-objective design.

## Publications from this project

{% bibliography --query @*[key=Sharma2026CHERD || key=Sharma2026ESCAPE] %}

See all [publications](/publications/).
