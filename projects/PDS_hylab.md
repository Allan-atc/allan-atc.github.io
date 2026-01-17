---
layout: project
type: project
image: img/NSTGRO/hero_mpd_schematic.png
title: "NASA NSTGRO — Modeling onset thresholds in lithium MPD thrusters (NEP)"
start_date: 2025-09
end_date: Ongoing
published: true
labels:
  - Electric Propulsion
  - MPD Thruster
  - Plasma Stability
  - Two-Fluid Modeling
  - Quasi-1D Solver
summary: "Stability-oriented simulation framework to predict onset thresholds in self-field lithium MPD thrusters and guide operating regimes and geometry choices."
period: Stanford University · NASA Marshall Space Flight Center
---

<div class="container py-3">

  <!-- Header / context -->
  <p class="lead">
    <b>Objective.</b> Build a physics-based tool to <b>predict “onset” thresholds</b> in self-field lithium MPD thrusters—an instability-driven operating limit linked to voltage hash, anode damage, and performance loss—and use it to guide operating regimes and geometry choices for Nuclear Electric Propulsion.
  </p>

  <p style="margin-top:0.5rem;">
    <b>Role:</b> Graduate Researcher (implementation + validation + coupling of models)<br>
    <b>Faculty Advisor / PI:</b> Mark Cappelli (Stanford) · <b>NASA Research Collaborator:</b> Kurt Polzin (NASA MSFC)
  </p>

  <!-- Hero visual -->
  <p align="center">
    <img src="../img/NSTGRO/hero_mpd_schematic.png"
         alt="Self-field MPD thruster schematic and where onset originates near the anode region."
         style="max-width: 900px; margin: 1rem auto; display:block;">
    <span style="font-size: 0.9rem; color: gray;">
      Self-field MPD thruster schematic and why the near-anode region matters for onset.
    </span>
  </p>

  <!-- MPD explanation (short, recruiter-friendly) -->
  <h3>What is a lithium MPD thruster (and what is “onset”)?</h3>
  <p>
    A magnetoplasmadynamic (MPD) thruster is a high-power electric propulsion device where a large discharge current interacts with the self-induced magnetic field to accelerate a plasma and produce thrust.
    Lithium is a strong candidate propellant for high-power MPDs because it can reach higher efficiency than inert gases in this regime.
  </p>
  <p>
    A key challenge in self-field MPDs at high current is <b>onset</b>: a transition associated with large voltage fluctuations (“voltage hash”), localized anode spots, and accelerated anode erosion—ultimately reducing efficiency and lifetime.
    Traditional single-fluid MHD models struggle to capture the electrothermal instability physics behind onset, motivating a stability-oriented, non-equilibrium modeling approach.
  </p>

  <!-- Your technical contribution (paragraphs, not bullets) -->
  <h3>My technical contribution</h3>
  <p>
    I implemented a <b>0D pointwise linear stability model</b> derived from a <b>two-fluid, non-equilibrium formulation</b> that retains separate electron and heavy-species energy balances and explicit ionization–recombination kinetics.
    The governing equations are nondimensionalized, leading to a dispersion relation whose roots provide a <b>local instability growth rate</b> as a function of normalized axial wavenumber.
  </p>
  <p>
    I then <b>validated</b> this 0D stability model by reproducing key trends reported in Preble’s work, including alternating stable/unstable bands in stability maps and the expected sensitivity to discharge current density.
    Finally, I defined an <b>onset criterion</b> combining (i) a critical near-anode ionization fraction and (ii) a growth-rate requirement to flag stability loss in a physically grounded way.
  </p>
  <p>
    To make the stability analysis usable from computed plasma states (rather than assumed ones), I developed a <b>quasi-1D two-fluid solver</b> that computes axial plasma profiles including ionization–recombination, ambipolar diffusion, Ohmic heating (Spitzer conductivity), electron thermal conduction, and distinct electron/heavy-species temperatures.
    This solver is <b>coupled</b> to the stability module: for each geometry and operating setup, the code extracts the near-anode state, evaluates growth rate, and records the operating point when the onset criterion is exceeded.
  </p>

  <!-- Method visuals -->
  <p align="center">
    <img src="../img/NSTGRO/pipeline_flow_stability.png"
         alt="Workflow: quasi-1D solver -> extract near-anode state -> stability module -> onset criterion -> record threshold."
         style="max-width: 900px; margin: 1rem auto; display:block;">
    <span style="font-size: 0.9rem; color: gray;">
      Workflow used in this project: quasi-1D profiles → near-anode state → stability growth rate → onset criterion → threshold recording.
    </span>
  </p>

  <!-- Results: show, then briefly interpret -->
  <h3>Results</h3>
  <p>
    The implemented 0D model reproduces the expected stability behavior and provides a quantitative growth-rate output that can be scanned across operating and geometry parameters.
    Representative results are shown below.
  </p>

  <div class="row">
    <div class="col-md-6">
      <p align="center">
        <img src="../img/NSTGRO/fig4_growth_rate_wavenumber_J2e6.png"
             alt="Growth rate vs wavenumber at J=2.0e6 A/m^2."
             style="max-width: 100%; margin: 0.5rem auto; display:block;">
        <span style="font-size: 0.9rem; color: gray;">
          Growth rate vs. wavenumber (J = 2.0×10<sup>6</sup> A/m²): baseline stability behavior.
        </span>
      </p>
    </div>

    <div class="col-md-6">
      <p align="center">
        <img src="../img/NSTGRO/fig5_growth_rate_wavenumber_J5e6.png"
             alt="Growth rate vs wavenumber at J=5.0e6 A/m^2."
             style="max-width: 100%; margin: 0.5rem auto; display:block;">
        <span style="font-size: 0.9rem; color: gray;">
          Increasing current density increases growth rate and narrows the stable operating window.
        </span>
      </p>
    </div>
  </div>

  <div class="row">
    <div class="col-md-6">
      <p align="center">
        <img src="../img/NSTGRO/fig6_growth_rate_interelectrode_separation.png"
             alt="Growth rate vs interelectrode separation / electrode length."
             style="max-width: 100%; margin: 0.5rem auto; display:block;">
        <span style="font-size: 0.9rem; color: gray;">
          Geometry effect (fixed mass flow): decreasing electrode length increases stability, consistent with experimental correlations.
        </span>
      </p>
    </div>

    <div class="col-md-6">
      <p align="center">
        <img src="../img/NSTGRO/fig7_growth_rate_vs_alpha.png"
             alt="Growth rate vs ionization fraction alpha."
             style="max-width: 100%; margin: 0.5rem auto; display:block;">
        <span style="font-size: 0.9rem; color: gray;">
          Strong sensitivity to near-anode ionization fraction; above a critical α (≈ 0.875), stability can be lost rapidly.
        </span>
      </p>
    </div>
  </div>

  <!-- Evaluation against objective (explicit, honest) -->
  <h3>Evaluation vs initial objective</h3>
  <p>
    The initial objective was to move beyond single-fluid MHD and build a <b>physics-based onset predictor</b> tied to measurable behavior.
    This milestone has been met through (1) a validated 0D stability formulation that captures non-equilibrium electrothermal behavior and (2) an onset criterion that can be evaluated from local plasma conditions.
  </p>
  <p>
    The coupled quasi-1D + stability workflow converts this into a <b>usable design/operations tool</b>: it can scan geometries and operating points and record threshold conditions when the instability criterion is exceeded.
    Ongoing work extends the pointwise model into a <b>full 1D gradient-based stability formulation</b> and compares predicted threshold scalings to experimental onset datasets from the literature to quantify predictive accuracy.
  </p>

  <!-- Optional: short “why it matters for propulsion engineering” -->
  <h3>Why this matters for a Propulsion Engineer role</h3>
  <p>
    This project is built around the same loop used in propulsion engineering: define an operating limit tied to hardware risk (anode loading), build a model that captures the right physics,
    validate against known trends, and turn it into a tool that can guide geometry and operating envelope decisions.
  </p>

</div>
