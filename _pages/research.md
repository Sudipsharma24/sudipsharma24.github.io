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
- Confirm the four figures match the published ChERD versions (they came from the CEJ_submission folder).
- Check every sentence against the published papers.
{% endcomment %}

## Electrifying CO₂ capture with induction-heated adsorbents

Temperature-swing adsorption usually regenerates the sorbent with steam or hot purge gas, which ties the capture unit to a heat supply and heats the bed slowly from the outside. **Magnetic induction swing adsorption (MISA)** instead heats a magnetic composite adsorbent directly, from inside the particles, with an alternating magnetic field. Regeneration then runs on electricity and can be fast and localised.

My PhD at [NTNU](https://www.ntnu.edu/ept), supervised by Prof. Thomas A. Adams II and funded through the NTNU–MIT Energy Research Programme (NMERP-C2), asks how MISA cycles should be designed, and what trade-offs they face, for post-combustion CO₂ capture. The adsorbent studied is the Fe₃O₄@HKUST-1 composite.

<div class="row justify-content-sm-center">
  <div class="col-sm-11 mt-3 mt-md-0">
    {% include figure.liquid path="assets/img/research/misa-bed-steps.webp" class="img-fluid rounded z-depth-1" zoomable=true alt="Three steps of a MISA cycle: adsorption of a 15% CO2 / 85% N2 feed with the induction coil off; desorption with the coil on and an N2 purge, releasing CO2; cooling with cold water in the jacket and cold N2" caption="The basic MISA steps. Adsorption: flue gas (15% CO₂ / 85% N₂) flows through the bed with the coil off. Desorption: the AC unit drives the induction coil, heating the adsorbent directly and releasing CO₂. Cooling: cold water and cold N₂ return the bed to adsorption temperature. From Sharma & Adams, <em>Chem. Eng. Res. Des.</em> 234 (2026)." %}
  </div>
</div>

## Approach

**First-principles dynamic models.** I build dynamic models of complete MISA cycles in [IDAES](https://idaes.org/)/[Pyomo](https://www.pyomo.org/). The isotherm, breakthrough and induction-heated desorption behaviour is calibrated and checked against published experimental data for Fe₃O₄@HKUST-1.

**Surrogates and active learning.** Full cycle simulations are expensive, so I train Gaussian-process surrogates on them and choose new simulation points by active learning.

**Multi-objective optimisation.** On the surrogates I run NSGA-II and MOPSO to map the purity–recovery and productivity–energy trade-offs of competing cycle designs.

<div class="row justify-content-sm-center">
  <div class="col-sm-12 mt-3 mt-md-0">
    {% include figure.liquid path="assets/img/research/surrogate-pareto-per-config.webp" class="img-fluid rounded z-depth-1" zoomable=true alt="Four panels, one per MISA configuration, showing Gaussian-process predictions, rigorous simulations and the Pareto front in purity-recovery space" caption="Surrogate-based optimisation for each configuration: Gaussian-process predictions (light points), rigorous IDAES simulations (dark points) and the resulting purity–recovery Pareto front (outlined). From Sharma & Adams, <em>Chem. Eng. Res. Des.</em> 234 (2026)." %}
  </div>
</div>

## Results so far

I compared four MISA cycle configurations of increasing complexity: a basic three-step cycle (A); cycles adding a CO₂ rinse and N₂ purge (B, C), with C also sweeping the bed with CO₂ product during desorption; and a cycle with two heating stages and product and N₂ recycle (D).

<div class="row justify-content-sm-center">
  <div class="col-sm-12 mt-3 mt-md-0">
    {% include figure.liquid path="assets/img/research/misa-configurations.webp" class="img-fluid rounded z-depth-1" zoomable=true alt="Process flow diagrams of MISA configurations A to D, showing the cycle steps, induction-heated beds and recycle streams" caption="The four cycle configurations studied. Induction-heated beds are shown in red and orange. From Sharma & Adams, <em>Chem. Eng. Res. Des.</em> 234 (2026)." %}
  </div>
</div>

Only Configuration D reaches the purity and recovery region shaded as a CCS target; Configuration C reaches the CCU region.

<div class="row justify-content-sm-center">
  <div class="col-sm-10 mt-3 mt-md-0">
    {% include figure.liquid path="assets/img/research/pareto-comparison.webp" class="img-fluid rounded z-depth-1" zoomable=true alt="Purity-recovery Pareto fronts of configurations A to D on one plot, with shaded CCU and CCS target regions" caption="Purity–recovery Pareto fronts of the four configurations, with the CCU and CCS target regions shaded. From Sharma & Adams, <em>Chem. Eng. Res. Des.</em> 234 (2026)." %}
  </div>
</div>

- **Simulation framework:** an open-source IDAES framework for inductively heated adsorption, presented at ESCAPE-36 ([paper](https://doi.org/10.69997/sct.177673), [LAPSE:2026.0302](https://psecommunity.org/LAPSE:2026.0302)). The isotherm data, model equations and isotherm-fitting notebook are openly available as [supplementary material on LAPSE](https://psecommunity.org/LAPSE:2025.0725) (CC BY-SA 4.0).
- **Cycle design and optimisation:** four MISA cycle configurations, simulated and optimised, published in [_Chemical Engineering Research and Design_ 234, 720–739 (2026)](https://doi.org/10.1016/j.cherd.2026.09.029). The configuration code, simulation outputs and surrogate models are archived as [supplementary information on LAPSE](https://psecommunity.org/LAPSE:2026.0046) (CC BY-NC 4.0).
- **Recognition:** [Student Poster Award at GHGT-18](/news/2026-10-29-ghgt18-award/), Perth, 2026, among over 400 e-posters.

## Current work

I am extending the framework to temperature- and vacuum-swing (TVSA/VSA) cycles for the same magnetite–MOF adsorbent, and using batch Bayesian optimisation (qNEHVI) for sample-efficient multi-objective design.

## Publications from this project

{% bibliography --query @*[key=Sharma2026CHERD || key=Sharma2026ESCAPE] %}

See all [publications](/publications/).
