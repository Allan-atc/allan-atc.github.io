---
layout: project
type: project
image: img/CS3/ESUS1.png
image_fit: contain
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
  .gc-part2 .gc-frame{
    background: transparent;
    border: 0;
    box-shadow: none;
    padding: 0;
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

<details style="margin-top:1rem;">
  <summary style="display:flex; align-items:center; justify-content:space-between; gap:0.75rem; font-weight:700; font-size:1.15rem; background:#f8f9fa; border:1px solid rgba(0,0,0,.08); border-radius:12px; padding:.5rem .75rem; cursor:pointer; margin-bottom:1rem;">
    <span>▸ Part 1 - CAD</span>
    <span style="font-weight:400; font-size:0.9rem; color:#6c757d;">Read more</span>
  </summary>
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


</details>

<details style="margin-top:1rem;">
  <summary style="display:flex; align-items:center; justify-content:space-between; gap:0.75rem; font-weight:700; font-size:1.15rem; background:#f8f9fa; border:1px solid rgba(0,0,0,.08); border-radius:12px; padding:.5rem .75rem; cursor:pointer; margin-bottom:1rem;">
    <span>▸ Part 2 - mechanical</span>
    <span style="font-weight:400; font-size:0.9rem; color:#6c757d;">Read more</span>
  </summary>
<h3>Project Part 2 — ESUS 3U CubeSat</h3>
<div class="gc-part2">
<h4>STM Mechanical Qualification Campaign and Vibration Test Results</h4>

<h4>Objective</h4>
<p>
Led the STM mechanical qualification campaign focused on deployer constraints and launcher vibration environments.
</p>

<p>
I owned the end-to-end engineering work for the STM vibration qualification activity:
</p>
<ul>
  <li>Defined the test approach and acceptance criteria, and ensured compliance with requirements.</li>
  <li>Built the test configuration and instrumentation plan to measure internal structural response.</li>
  <li>Performed integrity assessment using pre-/post-resonance surveys and response analysis to identify any mechanical change.</li>
</ul>

<hr>

<h4>Test setup and instrumentation</h4>
<ul>
  <li><strong>Reference frame and axes:</strong> testing was performed along the CubeSat axes X, Y, Z.</li>
  <li><strong>Instrumentation strategy:</strong> I instrumented the STM with tri-axial accelerometers to capture both input control levels and the structural response. The core configuration used three 3-axis accelerometers, including one mounted at the card-rack center, plus additional sensors when needed for subsystem-level insight.</li>
  <li>The accelerometer placed at the rack center is the most relevant measurement because it captures what the internal stack actually experiences, not just the shaker table input.</li>
</ul>

photo accelerometre STM 
photo STM dans ISIPOD


<div class="row g-3 justify-content-center">
  <div class="col-md-6">
    <figure class="gc-figure">
      <div class="gc-frame gc-h-md d-flex align-items-center">
        <img src="{{ 'img/CS3/STM dans ISIPOD.jpg' | relative_url }}"
             alt="STM open — internal stack and structure"
             class="gc-media" loading="lazy" decoding="async">
      </div>
      <figcaption style="font-size: 0.9rem; color: gray; text-align: center;">Figure 8 — ESUS inside the deployer, mounted on the shaker table in the test configuration</figcaption>
    </figure>
  </div>
  <div class="col-md-6">
    <figure class="gc-figure">
      <div class="gc-frame gc-h-md d-flex align-items-center">
        <img src="{{ 'img/CS3/accelerometre STM.jpg' | relative_url }}"
             alt="CAD — card rack stack-up with PC104 spacing logic"
             class="gc-media" loading="lazy" decoding="async">
      </div>
      <figcaption style="font-size: 0.9rem; color: gray; text-align: center;">Figure 9 — Accelerometer placement on ESUS for vibration testing</figcaption>
    </figure>
  </div>
</div>

<hr>

<h4>Test plan and acceptance criteria</h4>
<p>
I used a structured integrity-check process: run a resonance survey before and after each environment to detect any mechanical change. Because the launcher had not been selected yet, I used the Arianespace VEGA vibration requirements as the reference case (most restrictive at the time).
</p>

<p><strong>Resonance survey</strong></p>
<ul>
  <li><strong>Input:</strong> 0.5 g, 5–2000 Hz, sweep rate 2 oct/min.</li>
</ul>

<p><strong>Acceptance logic</strong><br>
The resonance survey excites the CubeSat across a wide band to reveal its modes. I performed it before testing and after each test, enabling direct comparison of resonance frequencies and amplitudes. A significant change indicates internal failure or a mechanical-property change (loosening, damage, interface shift).
</p>

<ul>
  <li><strong>Success criterion:</strong> frequency shift &lt; 5% and amplitude shift &lt; 10% on the reference spectrum, over the comparison band (5 Hz to 120 Hz if the first mode is &lt;120 Hz, otherwise 5 Hz to the first mode).</li>
</ul>

<p><strong>Vibration environments</strong></p>
<ul>
  <li><strong>Quasi-static load:</strong> 12.5 g per axis at 35 Hz (represents launch accelerations)</li>
  <li><strong>Sinusoidal vibration:</strong> 5–125 Hz with amplitude schedule, 2 oct/min (represents launcher oscillations)</li>
  <li><strong>Random vibration:</strong> 20–2000 Hz PSD profile, 8.85 gRMS target, 120 s duration (stresses components and validates assembly)</li>
</ul>

<hr>

<h4>Results</h4>

<h5>1) Resonance survey and structural integrity</h5>
<p>
The first natural frequencies measured on the STM were:
</p>
<ul>
  <li><strong>X axis:</strong> 385 Hz</li>
  <li><strong>Y axis:</strong> 230 Hz</li>
  <li><strong>Z axis:</strong> 290 Hz</li>
</ul>

<p>
This meets the requirement of a first mode &gt; 100 Hz with a safety factor of 2.3.
</p>

<figure class="gc-figure mx-auto" style="max-width: 760px;">
  <div class="gc-frame gc-h-md d-flex align-items-center">
    <img src="{{ 'img/CS3/resonance survey.png' | relative_url }}"
         alt="Amplitude response of the structure accelerometer (X-axis): first vs last resonance survey"
         class="gc-media" loading="lazy" decoding="async">
  </div>
  <figcaption class="gc-caption">Figure 10 — Comparison of resonance surveys along the X-axis for the accelerometer mounted at the satellite center</figcaption>
</figure>

<hr>

<h5>2) Quasi-static load performance</h5>
<p>
From the quasi-static load test, the measured response at the STM accelerometers remained close to the commanded lateral acceleration, indicating an almost unit transfer function between the shaker input and the STM response. On the Z-axis, the maximum amplification factor was Q = 1.084, consistent with a stiff, well-coupled structure in this frequency range.
</p>

<div class="table-responsive">
  <table class="table table-sm align-middle">
    <thead>
      <tr>
        <th>Test axis</th>
        <th>Lateral (g)</th>
        <th>Accelerometer 1 (g)</th>
        <th>Accelerometer 2 (g)</th>
        <th>Accelerometer 3 (g)</th>
        <th>Max Q factor</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>Axis Z</td>
        <td>12.5</td>
        <td>13.5862</td>
        <td>13.4888</td>
        <td>13.4706</td>
        <td>1.08417</td>
      </tr>
    </tbody>
  </table>
</div>

<hr>

<h5>3) Sinusoidal vibration response</h5>
<p>
The structure response showed very limited amplification in the 5–120 Hz band:
</p>
<ul>
  <li>Max amplification ~16% (X)</li>
  <li>Max amplification ~18% (Y)</li>
  <li>Max amplification ~15% (Z)</li>
</ul>
<p>
This is consistent with the STM having no structural natural frequency within 5–120 Hz, which is exactly what we want for launcher-driven sinusoidal environments.
</p>

<div class="row g-3 justify-content-center">
  <div class="col-md-6">
    <figure class="gc-figure">
      <div class="gc-frame gc-h-md d-flex align-items-center">
        <img src="{{ 'img/CS3/figure7.jpg' | relative_url }}"
             alt="Structure accelerometer response during sinusoidal vibration (X-axis)"
             class="gc-media" loading="lazy" decoding="async">
      </div>
      <figcaption class="gc-caption">Figure 11 — Structure accelerometer response during sinusoidal vibration (X-axis)</figcaption>
    </figure>
  </div>
</div>

<hr>

<h5>4) Random vibration performance</h5>
<p>
Random vibration was performed with the VEGA PSD profile (20–2000 Hz, 8.85 gRMS, 120 s). The achieved control levels were close to the specification on each axis. The structural PSD measured on the STM captured the system response and confirmed stable behavior under broadband excitation.
</p>
<hr>

<h4>Issues</h4>
<p>
Beyond validating global dynamic behavior, the campaign also surfaced an integration weakness early. Two loose nuts were found, originating from the solar panel deployment mechanism. During the Y-axis random vibration test, a measurement artifact was observed and attributed to these nuts. The root cause was insufficient thread engagement: the threaded shaft length had not been updated after the solar generator PCB thickness was changed.
</p>

<hr>

<h4>Conclusion</h4>
<p>
I presented these results to CNES and Thales Alenia Space, and the Phase B review was validated.
</p>

<figure class="gc-figure mx-auto" style="max-width: 780px;">
  <div class="gc-frame gc-h-md d-flex align-items-center">
    <img src="{{ 'img/CS3/photoequipe.jpeg' | relative_url }}"
         alt="ESUS team photo"
         class="gc-media" loading="lazy" decoding="async">
  </div>
  <figcaption class="gc-caption">Figure 11 - ESUS team in Toulouse, France, after Phase B validation</figcaption>
</figure>

</div>

</details>
