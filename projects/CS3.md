---
layout: project
type: project
image: img/CS3/ESUS1.png
title: "3U CubeSat: ESUS"
permalink: /projects/CS3/
start_date: January 2023
end_date: July 2024
published: true
summary: "Built the flight-representative mechanical CAD of a 3U CubeSat and derived the first Structural & Thermal Model (STM) to validate Phase B through deployer compatibility and mass-property verification."
period: CentraleSupélec Space Center for CubeSats
---

<div class="container py-3">
<style>
  /* --- ESUS image system --- */
  .gc-figure { margin: 1rem 0; }
  .gc-frame{
    background:#f8f9fa;
    border:1px solid rgba(0,0,0,.08);
    border-radius:14px;
    padding:.5rem;
    box-shadow:0 .25rem .75rem rgba(0,0,0,.06);
  }
  .gc-media{
    width:100%;
    height:100%;
    object-fit:contain;
    display:block;
  }
  .gc-caption{
    font-size:.85rem;
    color:#6c757d;
    margin-top:.4rem;
    text-align:center;
    line-height:1.2;
  }

  /* Controlled sizes */
  .gc-h-sm{ height:220px; }
  .gc-h-md{ height:280px; }
  .gc-h-lg{ height:360px; }
  .gc-h-banner{ height:240px; }

  /* Floats for “integrated in text” visuals */
  .gc-float{ max-width:340px; }
  @media (max-width: 767.98px){
    .gc-float{ float:none !important; max-width:100%; margin-left:0 !important; margin-right:0 !important; }
    .gc-h-sm, .gc-h-md, .gc-h-lg, .gc-h-banner{ height:auto; }
  }
</style>


<p>
<strong>Program:</strong> CentraleSupélec 3U CubeSat (ESUS)<br>
<strong>Sponsors / Technical support:</strong> French Space Agency (CNES), Thales Alenia Space<br>
<strong>Role:</strong> Structure & Thermal team (2 people) — I led structural work; teammate led thermal (tight coordination)
</p>

<!-- STM hero (open + closed) -->
<!-- STM hero (open + closed) -->


<h4>Objective</h4>
<p>
ESUS is a CentraleSupelec 3U CubeSat scheduled for launch in 2027, developed end-to-end by a team of ~30 engineering students and 5 faculty advisors, with sponsorship and technical support from the French Space Agency and Thales Alenia Space. The mission carries two payloads:
</p>

<ul>
  <li>an interferometer to measure the Sun’s diameter,</li>
  <li>an AI camera that analyzes images onboard and discards frames with excessive cloud cover to reduce memory and power usage.</li>
</ul>

<p>
Along with one other student, we formed the Structure & Thermal team. I was primarily responsible for the structural work, while my teammate focused on thermal aspects; however, the two domains were tightly coupled and required coordination. I built the flight-representative mechanical CAD of ESUS and derived from it the first Structural & Thermal Model (STM) to validate Phase B (Preliminary Design & Technology Completion) through mechanical qualification activities.
</p>

<div class="row g-3 justify-content-center">
  <div class="col-md-6">
    <figure class="gc-figure">
      <div class="gc-frame gc-h-md d-flex align-items-center">
        <img src="{{ '/img/CS3/ESUS_STM1.png' | relative_url }}" alt="ESUS STM — open configuration"
             class="gc-media" loading="lazy" decoding="async">
      </div>
      <figcaption style="font-size: 0.9rem; color: gray; text-align: center;">Figure 1 — ESUS STM (open configuration).</figcaption>
    </figure>
  </div>

  <div class="col-md-6">
    <figure class="gc-figure">
      <div class="gc-frame gc-h-md d-flex align-items-center">
        <img src="{{ '/img/CS3/ESUS_STM2.png' | relative_url }}" alt="ESUS STM — closed configuration"
             class="gc-media" loading="lazy" decoding="async">
      </div>
      <figcaption style="font-size: 0.9rem; color: gray; text-align: center;">Figure 2 — ESUS STM (closed configuration).</figcaption>
    </figure>
  </div>
</div>

<hr>

<h4>STM requirements</h4>
<ul>
  <li><strong>Form factor:</strong> compliant with a 3U envelope (340.5 × 100 × 100 mm) and compatible with P-POD-class interfaces via the ISIS iSiPod deployer.</li>
  <li><strong>Mechanical representativeness:</strong> replicate the mass distribution and equivalent inertia of the flight configuration.</li>
</ul>

<h4>Success criteria</h4>
<ul>
  <li>Same external geometry and interface features as the flight configuration.</li>
  <li>Equivalent system-level mass and inertia behavior and consistent subsystem placement, sufficient to replicate launch and on-orbit mechanical loads.</li>
</ul>

<hr>

<h4>1) Flight CAD architecture</h4>
<p>
I first created a full flight-representative CAD baseline of ESUS using real subsystem geometry—some provided by CNES, and some produced internally (by other students for the payload for example) or by me. This CAD was used to:
</p>

<ul>
  <li>lock deployer interfaces and critical tolerance stack-ups (rails/panels/fasteners) to guarantee clearance and reliable ejection,</li>
  <li>converge subsystem packaging and stack-up to meet mass distribution constraints, ensure connectivity between components, and account for thermal transfer considerations,</li>
  <li>establish the mass-property targets that the STM would need to reproduce,</li>
  <li>prepare the build of the flight model.</li>
</ul>

<!-- Flight CAD visuals -->
<div class="row g-3 justify-content-center">
  <div class="col-md-6">
    <figure class="gc-figure">
      <div class="gc-frame gc-h-md d-flex align-items-center">
        <img src="{{ '/img/CS3/CAD_STM%20COMPLET%20OUVERT.jpg' | relative_url }}" alt="Flight CAD — full mechanical assembly"
             class="gc-media" loading="lazy" decoding="async">
      </div>
      <figcaption style="font-size: 0.9rem; color: gray; text-align: center;">Figure 3 — ESUS CAD: full mechanical assembly (open view)</figcaption>
    </figure>
  </div>

  <div class="col-md-6">
    <figure class="gc-figure">
      <div class="gc-frame gc-h-md d-flex align-items-center">
        <img src="{{ '/img/CS3/CAD_ferme%20panneau%20solaire.jpg' | relative_url }}" alt="Flight CAD — external panels and solar panel layout"
             class="gc-media" loading="lazy" decoding="async">
      </div>
      <figcaption style="font-size: 0.9rem; color: gray; text-align: center;">Figure 4 — ESUS CAD: external panels and solar panel layout</figcaption>
    </figure>
  </div>
</div>

<hr>

<h4>2) From CAD to STM: why mass dummies were necessary</h4>

<p><strong>The problem we had to solve</strong><br>
During Phase B, several flight components were not yet physically available—especially items provided by CNES and parts of the payload—although we did have the mechanical information needed to model them. Waiting for all flight hardware would have delayed system-level verification by months to years, preventing timely Phase B validation with sponsors.
</p>

<p><strong>The decision</strong><br>
I used mass dummies as an engineering solution. Even without final hardware, this approach allowed us to validate the mechanical aspects for Phase B:
</p>

<ul>
  <li>deployer interface compatibility and ejection behavior,</li>
  <li>vibration survivability and structural integrity trends (launcher-driven requirements),</li>
  <li>global mass properties (total mass, center of gravity, and inertia behavior).</li>
</ul>

<p>
To make the STM representative, dummy masses were sized using datasheet component masses. Their placement followed the real component layout on PCBs, and shapes were sometimes tuned (plates, blocks, butterfly geometries) to better reproduce inertia behavior rather than only matching total mass. This required that I manufactured aluminum or steel parts depending on the required density, using CentraleSupelec’s fabrication laboratory, including:
</p>

<ul>
  <li>waterjet cutting,</li>
  <li>laser cutting (CO<sub>2</sub> and fiber),</li>
  <li>3D printing (filament and resin) for smaller parts.</li>
</ul>

<figure class="gc-figure mx-auto" style="max-width: 520px;">
  <div class="gc-frame gc-h-sm d-flex align-items-center">
    <img src="{{ '/img/CS3/Ninao%20de%20CNES%20(forme%20papillions).png' | relative_url }}"
         alt="Example mass dummy tuned for inertia: butterfly-shaped geometry"
         class="gc-media" loading="lazy" decoding="async">
  </div>
  <figcaption style="font-size: 0.9rem; color: gray; text-align: center;">Figure 5 — Example component modeled with a butterfly-shaped geometry</figcaption>
</figure>


<hr>

<h4>3) STM definition, build, and integration</h4>
<p>The STM reproduces the CubeSat partitioning of the flight design:</p>

<!-- STM internal views -->
<ul>
  <li>a primary structure (4 aluminum rails and 4 aluminum frames),</li>
  <li>a card rack represented by steel/aluminum mass dummies mounted on PCB cards (stacked using M3 threaded rods with PC104 spacing logic),</li>
  <li>payload representation using aluminum/steel masses,</li>
  <li>PCB solar panels mounted on the lateral faces,</li>
  <li>S-band antennas represented by steel masses mounted on external aluminum panels.</li>
</ul>

<div class="row g-3 justify-content-center">
  <div class="col-md-6">
    <figure class="gc-figure">
      <div class="gc-frame gc-h-md d-flex align-items-center">
        <img src="{{ '/img/CS3/figure6.png' | relative_url }}"
             alt="STM open — internal stack and structure"
             class="gc-media" loading="lazy" decoding="async">
      </div>
      <figcaption style="font-size: 0.9rem; color: gray; text-align: center;">Figure 6 — STM open: internal stack, mass dummies, and flight-like integration</figcaption>
    </figure>
  </div>
  <div class="col-md-6">
    <figure class="gc-figure">
      <div class="gc-frame gc-h-md d-flex align-items-center">
        <img src="{{ '/img/CS3/CAD_Rack_carte.png' | relative_url }}"
             alt="CAD — card rack stack-up with PC104 spacing logic"
             class="gc-media" loading="lazy" decoding="async">
      </div>
      <figcaption style="font-size: 0.9rem; color: gray; text-align: center;">Figure 7 — CAD: avionics/card rack stack-up (PC104 spacing + threaded-rod architecture)</figcaption>
    </figure>
  </div>
</div>

<hr>

<h4>4) Results</h4>
<p>
Thanks to the STM, we obtained experimental measurements of the system mass and center of gravity location. Using the assembled STM, we measured:
</p>

<ul>
  <li><strong>Total mass:</strong> 2998 g (target was 3 kg)</li>
  <li><strong>Center of gravity offset relative to the structural geometric center:</strong> x = 0 mm, y = 2 mm, z = 7 mm</li>
</ul>

<p><strong>Compliance with iSiPod requirements</strong><br>
According to iSiPod specifications, the center of gravity must lie within a 20 × 20 × 60 mm rectangular box around the geometric center. Our measured center of gravity falls comfortably inside this volume, providing strong evidence that the mass-dummy strategy was effective and that the STM is representative enough to support meaningful deployer and qualification testing.
</p>

<p>
With this STM now representative of the flight configuration, we can proceed with mechanical testing and use the results to support Phase B validation, provided test outcomes meet expectations.
</p>

</div>
