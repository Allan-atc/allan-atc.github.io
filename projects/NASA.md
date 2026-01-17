---
layout: project
type: project
image: img/NASA/MPD.png
title: "Computational Modeling of a Lithium Magnetoplasmadynamic Thruster for Nuclear Electric Propulsion"
permalink: /projects/nasa/
start_date: August 2025
end_date: Present
published: true
summary: "This work aims to advance high-power propulsion for long-duration missions to Mars by optimizing thruster designs using a stability-oriented modeling framework."
period: NASA Space Technology Graduate Research - Stanford University
---

<div class="container py-3">

<p><strong>Program:</strong> NASA Space Technology Graduate Research (NSTGRO25)<br>
<strong>Principal Investigator:</strong> Prof. Mark Cappelli (Stanford University)<br>
<strong>NASA Research Collaborator:</strong> Dr. Kurt Polzin (NASA Marshall Space Flight Center)</p>

<hr>

<h4>Objective</h4>
<p>
High-power electric propulsion, including Nuclear Electric Propulsion (NEP), is a promising technology for future crewed and cargo missions to Mars. For high-power spacecraft, the self-field Magnetoplasmadynamic (MPD) configuration is especially attractive because it delivers strong performance.
</p>

<p>
A major barrier to operating MPDs at high current, which enables high specific impulse, is <em>onset</em>: a transition associated with large voltage fluctuations and severe anode erosion when the current exceeds a threshold. Onset is influenced by propellant choice, mass flow rate, and thruster geometry. However, its underlying causes remain insufficiently understood, and conventional computational tools such as MHD do not capture the physics that appears central to onset.
</p>

<p>
<strong>Goal:</strong> develop a predictive, physics-based simulation framework capable of predicting onset, to guide design and operating conditions that extend thruster lifetime for MPD thrusters relevant to Mars missions.
</p>

<hr>

<h4>Technical contribution</h4>

<p>
By retaining non-equilibrium thermodynamics and ionization dynamics, the formulation captures electrothermal behavior that single-fluid MHD cannot.
</p>

<h5>Linear stability model</h5>
<p>
I implemented a two-fluid, 1D formulation derived for the near-anode region, where instabilities are most critical. In this framework, electrons and heavy species are treated with separate energy balances, enabling non-equilibrium between electron temperature and gas temperature. The model explicitly includes ionization and recombination kinetics, ambipolar diffusion, Ohmic heating with Spitzer conductivity, viscous dissipation, and electron–heavy species energy exchange.
</p>

<p>
The governing equations are nondimensionalized, yielding a cubic dispersion relation whose roots provide the local instability growth rate as a function of the normalized axial wavenumber.
</p>

<h5>One-dimensional two-fluid solver and coupling strategy</h5>
<p>
To evaluate stability from computed plasma states, I developed a 1D two-fluid solver that computes the axial evolution of plasma properties along the channel, including:
</p>

<ul>
  <li>mass and momentum,</li>
  <li>electron density,</li>
  <li>electron temperature and heavy-species temperature,</li>
  <li>self-induced magnetic field,</li>
  <li>consistent chemistry terms: ionization–recombination, ambipolar diffusion, Ohmic heating, electron thermal conduction, and wall losses.</li>
</ul>

<p>
I then coupled the 1D solver to the 0D stability model: the solver provides axial profiles, a near-anode state is extracted, and the stability module computes the growth rate and evaluates an onset criterion for a magnetic field <em>B</em> that increases up to onset. For a given geometry, this workflow can be used to sweep operating conditions and record onset thresholds when the instability criterion is exceeded.
</p>

<hr>

<h4>My results</h4>
<p>
This coupled system was validated by reproducing key trends reported in the experimental literature:
</p>

<ul>
  <li><strong>Stability maps:</strong> growth rate vs. nondimensional wavenumber shows alternating stable and unstable bands.</li>
</ul>
<div style="display:flex; gap:1rem; flex-wrap:wrap; justify-content:center; align-items:flex-start;">
  <div style="max-width: 420px; flex: 1 1 320px; text-align:center;">
    <img src="{{ '/img/NASA/Figure%204.1.png' | relative_url }}" alt="Figure 1 — Growth rate vs. wavenumber at J = 2.0 × 10^6 A/m^2" style="width:100%; height:auto; margin: 1rem auto; display:block;">
  </div>
  <div style="max-width: 420px; flex: 1 1 320px; text-align:center;">
    <img src="{{ '/img/NASA/Figure_4.2.png' | relative_url }}" alt="Figure 1 — Growth rate vs. wavenumber at J = 2.0 × 10^6 A/m^2" style="width:100%; height:auto; margin: 1rem auto; display:block;">
  </div>
</div>
<p align="center" style="margin-top: 0.25rem;">
  <span style="font-size: 0.9rem; color: gray; display: block; text-align: center;">Figure 1 — Growth rate vs. wavenumber at J = 2.0 × 10^6 A/m<sup>2</sup></span>
</p>

<ul>
  <li><strong>Current density sensitivity:</strong> increasing discharge current density increases instability growth rate and narrows the stable operating window.</li>
</ul>
<p align="center">
  <img src="{{ '/img/NASA/Figure_4.3.png' | relative_url }}" alt="Figure 3 — Growth rate vs. wavenumber at J = 5.0 × 10^6 A/m^2" style="max-width: 500px; margin: 1rem auto; display:block;">
  <span style="font-size: 0.9rem; color: gray; display: block; text-align: center;">Figure 2 — Growth rate vs. wavenumber at J = 5.0 × 10^6 A/m<sup>2</sup></span>
</p>

<ul>
  <li><strong>Geometry correlation:</strong> for fixed mass flow rate, decreasing interelectrode length increases stability.</li>
</ul>
<p align="center">
  <img src="{{ '/img/NASA/Figure_4.5.png' | relative_url }}" alt="Figure 4 — Growth rate vs. interelectrode separation" style="max-width: 500px; margin: 1rem auto; display:block;">
  <span style="font-size: 0.9rem; color: gray; display: block; text-align: center;">Figure 3 — Growth rate vs. interelectrode separation</span>
</p>

<ul>
  <li><strong>Ionization-fraction threshold:</strong> strong sensitivity to near-anode ionization fraction. Above a critical value (approximately α ≈ 0.875), small current increases can lead to rapid stability loss.</li>
</ul>
<p align="center">
  <img src="{{ '/img/NASA/Figure_4.11%20alpha%20crit.png' | relative_url }}" alt="Figure 5 — Growth rate vs. ionization fraction α" style="max-width: 500px; margin: 1rem auto; display:block;">
  <span style="font-size: 0.9rem; color: gray; display: block; text-align: center;">Figure 4 — Growth rate vs. ionization fraction α</span>
</p>



</div>
