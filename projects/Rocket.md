---
layout: project
type: project
image: img/Rocket/Rocket1.JPG
title: "PEGGASUS — Rocket Design Project"
permalink: /projects/peggasus/
start_date: 2020-03-01
end_date: 
published: true
summary: "Designed and built a one-meter rocket as part of a competition. Used simulations to meet apogee, flight-time, landing-speed, and payload-recovery requirements."
period: High School Rocket Club
---

<div class="container py-3">

<hr>

<h4>Project Overview</h4>
<p>
In my senior year of high school, I participated in a rocket-design competition where, as a team of four, we designed and built a rocket named PEGGASUS to satisfy a strict set of requirements:
</p>

<ul>
  <li>Apogee: 200 m</li>
  <li>Rocket length: &gt; 1 m</li>
  <li>Flight time: 40–43 s</li>
  <li>Impact speed: &lt; 5 m/s</li>
  <li>Payload recovery: return an onboard egg intact using only everyday, off-the-shelf materials</li>
</ul>

<p align="center">
  <img src="{{ 'img/Rocket/Rocket1.JPG' | relative_url }}" alt="PEGGASUS launch" style="max-width: 700px; margin: 1rem auto; display:block;">
  <span style="font-size: 0.9rem; color: gray; display:block; text-align:center;">Figure 1 — PEGGASUS at liftoff</span>
</p>

<hr>

<h4>Technical approach</h4>
<p>
To meet these requirements, we used OpenRocket as the main design tool and followed a simulation-driven process. We ran simulations to converge on a configuration that satisfied the apogee and flight-time constraints. Based on the simulation results, we sized the recovery system accordingly, including a 76 cm diameter parachute to target the required descent profile. We iterated on geometry—nose cone shape, fin planform, and mass distribution—validated apogee, flight time, and stability in simulation, then built the hardware to match the simulated configuration as closely as possible.
</p>

<p align="center">
  <img src="{{ 'img/Rocket/Simulation Rocket.png' | relative_url }}" alt="OpenRocket simulation results" style="max-width: 750px; margin: 1rem auto; display:block;">
  <span style="font-size: 0.9rem; color: gray; display:block; text-align:center;">Figure 2 — OpenRocket simulation output</span>
</p>

<hr>

<h4>Key design choices</h4>
<ul>
  <li>CAD design: I modeled the nose cone in SolidWorks, optimized its shape for subsonic flight, and 3D-printed it for integration on the rocket.</li>
  <li>Stability and fin sizing: We iterated on the number and type of fins to maintain stability in windy conditions while staying consistent with the simulation model. We chose simple square fins to reduce uncertainty relative to OpenRocket assumptions.</li>
  <li>Payload protection: We designed egg protection using cotton and puffed rice. The puffed rice provided impact damping, while the cotton helped isolate the egg from vibrations.</li>
  <li>Electronics and deployment logic: We implemented a simple Raspberry Pi countdown to trigger (1) ignition at launch and (2) a delayed parachute deployment using a secondary igniter after a fixed delay.</li>
  <li>Integration layout: We defined the internal placement of the electronics, battery, igniters, parachute, and payload to preserve stability and enable reliable parachute deployment, targeting a center-of-mass to center-of-pressure offset below 5 cm.</li>
</ul>

<hr>

<h4>Results</h4>

<p>
<video controls playsinline preload="metadata" style="width: 100%; max-width: 300px; display: block; margin: 0.5rem auto;">
  <source src="{{ '/img/Rocket/video%20fusee.mp4' | relative_url }}" type="video/mp4">
  Your browser does not support the video tag.
</video>
<span style="font-size: 0.9rem; color: gray; display:block; text-align:center;">PEGGASUS launch</span>
</p>

<ul>
  <li>Simulation vs. reality: The propulsion and ballistic phases matched the simulation well overall. The main deviation came from recovery timing: the parachute deployed later than expected.</li>
</ul>

<div class="table-responsive" style="margin: 1rem 0;">
  <table class="table table-bordered table-sm align-middle" style="background:white; font-size: 0.85rem;">
    <caption style="caption-side: bottom; text-align:center; color: #6c757d; padding-top: .5rem; font-size: 0.8rem;">
      Analytical predictions (with/without drag) vs. OpenRocket simulation and altimeter measurements.<br>
      \(\displaystyle \tau=\frac{m}{B\,\rho_{air}}\). Rocket mass is assumed constant across all phases.
    </caption>
    <thead style="background:#f8f9fa;">
      <tr>
        <th style="min-width: 220px;">Metric</th>
        <th style="min-width: 360px;">Analytical model (1) — no drag</th>
        <th style="min-width: 420px;">Analytical model (2) — with drag</th>
        <th style="min-width: 120px;">Value (1)</th>
        <th style="min-width: 120px;">Value (2)</th>
        <th style="min-width: 140px;">OpenRocket</th>
        <th style="min-width: 140px;">Altimeter</th>
      </tr>
    </thead>

    <tbody>
      <tr>
        <td>Time to trajectory apex</td>
        <td>\(\displaystyle t_{max}=t_{op}+\frac{v_{op}\cos(\alpha)}{g}\)</td>
        <td>\(\displaystyle t_{max}=t_{op}+\tau\,\ln\!\left(1+\frac{v_{op}\cos(\alpha)}{g\,\tau}\right)\)</td>
        <td>9.68 s</td>
        <td>9.69 s</td>
        <td>7.68 s</td>
        <td>7.76 s</td>
      </tr>

      <tr>
        <td>Maximum altitude reached</td>
        <td>\(\displaystyle y_{max}=-\frac{v_{op}^{2}}{2g}+y_{op}\)</td>
        <td>\(\displaystyle
          y_{max}=
          -\tau\,(v_{op}\cos\alpha+\tau g)\left(-1+e^{-\frac{t_{max}-t_{op}}{\tau}}\right)
          -g\tau\,(t_{max}-t_{op})
          +y_{op}
        \)</td>
        <td>358.1 m</td>
        <td>357.6 m</td>
        <td>251.8 m</td>
        <td>248 m</td>
      </tr>

      <tr>
        <td>Horizontal range if the parachute does not deploy</td>
        <td>\(\displaystyle O_x=v_{0}\sin(\alpha)\,(t-t_{0})\)</td>
        <td>\(\displaystyle O_x=v_{0}\sin(\alpha)\,\tau\left(1-e^{-\frac{t_{max}-t_{op}}{\tau}}\right)\)</td>
        <td>97.4 m</td>
        <td>97.4 m</td>
        <td>110 m</td>
        <td>47 m</td>
      </tr>

      <tr>
        <td>Liftoff acceleration</td>
        <td>\(\displaystyle a=-g+\frac{F}{m}\)</td>
        <td>\(\displaystyle a=-g+\frac{F}{m}\)</td>
        <td>34.3 m·s<sup>−2</sup></td>
        <td>34.3 m·s<sup>−2</sup></td>
        <td>36.6 m·s<sup>−2</sup></td>
        <td>—</td>
      </tr>

      <tr>
        <td>Propulsion phase duration</td>
        <td>\(\displaystyle t_{op}\)</td>
        <td>\(\displaystyle t_{op}\)</td>
        <td>2.18 s</td>
        <td>2.18 s</td>
        <td>2.18 s</td>
        <td>—</td>
      </tr>

      <tr>
        <td>Velocity at the end of propulsion</td>
        <td>\(\displaystyle v_{op}=\left(-g+\frac{F}{m}\right)\,t_{op}\)</td>
        <td>\(\displaystyle v_{op}=\left(-g+\frac{F}{m}\right)\tau\left(1-e^{-\frac{t_{op}}{\tau}}\right)\)</td>
        <td>74.8 m·s<sup>−1</sup></td>
        <td>74.8 m·s<sup>−1</sup></td>
        <td>66.2 m·s<sup>−1</sup></td>
        <td>72.1 m·s<sup>−1</sup></td>
      </tr>

      <tr>
        <td>Ballistic-phase velocity components</td>
        <td>\(\displaystyle
          \begin{cases}
          v_y=v_{op}\cos(\alpha)-gt\\
          v_x=v_{op}\sin(\alpha)
          \end{cases}
        \)</td>
        <td>\(\displaystyle
          \begin{cases}
          v_y=(v_{op}\cos(\alpha)+\tau g)\,e^{-\frac{t}{\tau}}-\tau g\\
          v_x=v_{op}\sin(\alpha)\,e^{-\frac{t}{\tau}}
          \end{cases}
        \)</td>
        <td>—</td>
        <td>—</td>
        <td>—</td>
        <td>—</td>
      </tr>

      <tr>
        <td>Speed at parachute deployment</td>
        <td>\(\displaystyle v_{pa}=\sqrt{v_y^2(7s)+v_x^2(7s)}\)</td>
        <td>\(\displaystyle v_{pa}=\sqrt{v_y^2(7s)+v_x^2(7s)}\)</td>
        <td>13.91 m·s<sup>−1</sup></td>
        <td>13.86 m·s<sup>−1</sup></td>
        <td>5.5 m·s<sup>−1</sup></td>
        <td>12.4 m·s<sup>−1</sup></td>
      </tr>

      <tr>
        <td>Impact speed at ground</td>
        <td>\(\displaystyle v_{imp}=\sqrt{\frac{mg}{B\,\rho_{air}}}\)</td>
        <td>—</td>
        <td>5.82 m·s<sup>−1</sup></td>
        <td>—</td>
        <td>5.56 m·s<sup>−1</sup></td>
        <td>7.2 m·s<sup>−1</sup></td>
      </tr>

      <tr>
        <td>Total flight time</td>
        <td>—</td>
        <td>—</td>
        <td>—</td>
        <td>—</td>
        <td>53.5 s</td>
        <td>41.0 s</td>
      </tr>

      <tr>
        <td>Altitude at end of propulsion</td>
        <td>\(\displaystyle y_{op}=\frac{1}{2}\left(\frac{F}{m}-g\right)\,t_{op}^{2}\)</td>
        <td>\(\displaystyle y_{op}=\left(\frac{F}{m}-g\right)\tau\left[t_{op}-\tau\left(1-e^{-\frac{t_{op}}{\tau}}\right)\right]\)</td>
        <td>81.5 m</td>
        <td>81.6 m</td>
        <td>96.2 m</td>
        <td>—</td>
      </tr>
    </tbody>
  </table>

</div>


<ul>
  <li>What failed and why: The deployment sequence did not perform as intended because the same battery powered both igniters. After the first ignition, the remaining current was not sufficient to heat the copper wire fast enough to trigger the parachute charge. This issue affected roughly half of the teams, since the battery choice was imposed and not under our control.</li>
  <li>Conclusion: Despite the recovery issue, the propulsion and ballistic predictions were highly accurate, confirming that the simulation-driven sizing approach was robust and that the main limitation was the deployment power margin rather than the aerodynamic design.</li>
</ul>

<p align="center">
  <img src="{{ 'img/Rocket/rocket destroy.JPG' | relative_url }}" alt="Post-flight rocket condition" style="max-width: 900px; margin: 1rem auto; display:block;">
  <span style="font-size: 0.9rem; color: gray; display:block; text-align:center;">Figure 3 — Post-flight condition (after a rapid unscheduled disassembly)</span>
</p>

</div>
