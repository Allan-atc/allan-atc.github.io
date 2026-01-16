---
layout: project
type: project
image: img/NSTGRO/logo_nstgro.png
title: "NASA NSTGRO — Predicting onset thresholds in lithium MPD thrusters (NEP)"
start_date: 2025-09
end_date: Ongoing
published: true
labels:
  - Electric propulsion
  - Plasma modeling
  - Stability analysis
  - Quasi-1D solver
  - Numerical methods
  - Python
summary: "Implemented and validated a coupled flow–stability framework to predict onset thresholds in self-field lithium MPD thrusters for Nuclear Electric Propulsion trade studies."
period: Stanford University · NASA NSTGRO
---

<div class="container py-3">

  <!-- One-line hook (Outcome first) -->
  <p class="lead">
    Built a stability-oriented simulation framework that links local plasma physics near the anode to an <b>onset prediction criterion</b> for self-field lithium MPD thrusters (high-power NEP).
  </p>

  <!-- Quick facts (fast to parse) -->
  <div class="row g-3 my-2">
    <div class="col-md-5">
      <div class="p-3 border rounded">
        <h5 class="mb-2">Quick facts</h5>
        <ul class="mb-0">
          <li><b>Role:</b> Graduate Researcher (model owner / implementation)</li>
          <li><b>Advisor (PI):</b> Prof. Mark Cappelli (Stanford)</li>
          <li><b>NASA collaborator:</b> Dr. Kurt Polzin (NASA MSFC)</li>
          <li><b>Grant:</b> NSTGRO · 80NSSC25K0378</li>
          <li><b>Focus:</b> Onset thresholds (instability-driven operating limit)</li>
        </ul>
      </div>
    </div>

    <!-- Hero visual (system-level orientation) -->
    <div class="col-md-7">
      <figure class="m-0 p-3 border rounded text-center">
        <img src="../img/NSTGRO/hero_mpd_schematic.png"
             alt="System-level schematic of a self-field MPD thruster and where the onset model is evaluated (near-anode region)."
             style="max-width: 100%; height: auto; border-radius: 6px;">
        <figcaption style="font-size: 0.9rem; color: gray; margin-top: 0.5rem;">
          System-level view: self-field MPD thruster and where the stability metric is evaluated (near-anode region).
        </figcaption>
      </figure>
    </div>
  </div>

  <!-- My contributions (explicit and scannable) -->
  <div class="mt-4">
    <h4>My contributions</h4>
    <ul>
      <li><b>Implemented</b> a 0D pointwise linear stability model from a two-fluid, non-equilibrium formulation (dimensionless growth-rate criterion).</li>
      <li><b>Validated</b> the model by reproducing key trends from the literature (alternating stable/unstable bands; sensitivity to current density).</li>
      <li><b>Ran parametric scans</b> to quantify how stability changes with operating and geometry parameters (e.g., current density, interelectrode separation, ionization fraction).</li>
      <li><b>Defined an onset criterion</b> combining a critical ionization fraction and growth-rate requirement to mark stability loss.</li>
      <li><b>Developed a quasi-1D two-fluid solver</b> to compute axial plasma profiles (electron/heavy-species temperatures, transport, chemistry) and <b>coupled</b> it to the stability module to record onset thresholds.</li>
    </ul>
  </div>

  <!-- Key results (visual-first) -->
  <div class="mt-4">
    <h4>Key results (selected)</h4>

    <div class="row g-3">
      <div class="col-md-6">
        <figure class="p-3 border rounded m-0 text-center">
          <img src="../img/NSTGRO/fig4_growth_rate_wavenumber_J2e6.png"
               alt="Growth rate vs wavenumber at J = 2.0e6 A/m^2"
               style="max-width: 100%; height: auto; border-radius: 6px;">
          <figcaption style="font-size: 0.9rem; color: gray; margin-top: 0.5rem;">
            Growth rate vs. wavenumber (J = 2.0×10<sup>6</sup> A/m²) — baseline stability behavior.
          </figcaption>
        </figure>
      </div>

      <div class="col-md-6">
        <figure class="p-3 border rounded m-0 text-center">
          <img src="../img/NSTGRO/fig5_growth_rate_wavenumber_J5e6.png"
               alt="Growth rate vs wavenumber at J = 5.0e6 A/m^2"
               style="max-width: 100%; height: auto; border-radius: 6px;">
          <figcaption style="font-size: 0.9rem; color: gray; margin-top: 0.5rem;">
            Increasing current density increases growth rate and narrows the stable window.
          </figcaption>
        </figure>
      </div>

      <div class="col-md-6">
        <figure class="p-3 border rounded m-0 text-center">
          <img src="../img/NSTGRO/fig6_growth_rate_interelectrode_separation.png"
               alt="Growth rate vs interelectrode separation / electrode length"
               style="max-width: 100%; height: auto; border-radius: 6px;">
          <figcaption style="font-size: 0.9rem; color: gray; margin-top: 0.5rem;">
            Geometry sensitivity: decreasing interelectrode length increases stability (fixed mass flow).
          </figcaption>
        </figure>
      </div>

      <div class="col-md-6">
        <figure class="p-3 border rounded m-0 text-center">
          <img src="../img/NSTGRO/fig7_growth_rate_vs_alpha.png"
               alt="Growth rate vs ionization fraction alpha"
               style="max-width: 100%; height: auto; border-radius: 6px;">
          <figcaption style="font-size: 0.9rem; color: gray; margin-top: 0.5rem;">
            Strong sensitivity to near-anode ionization fraction; beyond a critical α the system rapidly destabilizes.
          </figcaption>
        </figure>
      </div>
    </div>

    <div class="mt-3 p-3 border rounded">
      <h5 class="mb-2">Engineering takeaway</h5>
      <ul class="mb-0">
        <li>Provides a <b>physics-based onset metric</b> that reduced-order models (single-fluid MHD) typically miss.</li>
        <li>Enables <b>design/ops trade studies</b>: how operating point and geometry shift stability margins (and therefore lifetime risk).</li>
        <li>Coupling stability analysis with a quasi-1D solver makes the criterion usable from <b>computed plasma profiles</b>, not just assumed states.</li>
      </ul>
    </div>
  </div>

  <!-- How it works (process visual helps) -->
  <div class="mt-4">
    <h4>Method (how the tool is used)</h4>

    <figure class="p-3 border rounded m-0 text-center">
      <img src="../img/NSTGRO/pipeline_flow_stability.png"
           alt="Pipeline: quasi-1D solver -> extract near-anode state -> 0D stability module -> onset criterion -> record threshold"
           style="max-width: 100%; height: auto; border-radius: 6px;">
      <figcaption style="font-size: 0.9rem; color: gray; margin-top: 0.5rem;">
        Workflow: quasi-1D solver computes axial profiles → extract near-anode state → stability module evaluates growth rate → onset flagged when criterion is exceeded.
      </figcaption>
    </figure>

    <details class="mt-3">
      <summary><b>Technical details (for curious readers)</b></summary>
      <div class="mt-2">
        <ul>
          <li>Two-fluid, non-equilibrium treatment with separate electron/heavy-species temperatures and ionization–recombination kinetics.</li>
          <li>0D stability model yields growth rate from a nondimensional dispersion relation evaluated at local plasma conditions.</li>
          <li>Quasi-1D solver advances mass/momentum, electron density, Te/Th, and self-induced magnetic field with consistent transport/chemistry.</li>
          <li>Onset threshold recorded when (i) growth rate becomes positive and (ii) critical ionization fraction condition is met.</li>
        </ul>
      </div>
    </details>
  </div>

  <!-- Next steps -->
  <div class="mt-4">
    <h4>Next steps</h4>
    <ul>
      <li>Extend the pointwise model into a <b>1D gradient-based stability formulation</b> to account for axial gradients in T, n, σ, and ionization.</li>
      <li>Compare predicted onset scalings against published experimental trends and datasets; use results to guide operating envelopes and geometry choices.</li>
    </ul>
  </div>

</div>
