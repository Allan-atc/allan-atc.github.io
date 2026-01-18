---
layout: project
type: project
image: img/Rocket/Rocket1.JPG
title: "PEGGASUS — Rocket Design Project"
permalink: /projects/peggasus/
start_date: March 2020
end_date: 
published: true
summary: "One-week, simulation-driven rocket design and build meeting a strict apogee, flight-time, landing-speed, and payload-recovery requirement set."
period: High School Rocket Design Competition
---

<div class="container py-3">

<hr>

<h4>Objective</h4>
<p>
In my senior year of high school, I participated in a rocket-design competition where, as a team of four, we designed and built a rocket to satisfy a strict set of requirements:
</p>

<ul>
  <li><strong>Apogee:</strong> 200 m</li>
  <li><strong>Rocket length:</strong> &gt; 1 m</li>
  <li><strong>Flight time:</strong> 40–43 s</li>
  <li><strong>Impact speed:</strong> &lt; 5 m/s</li>
  <li><strong>Payload recovery:</strong> return an onboard egg intact using only everyday, off-the-shelf materials</li>
</ul>

<p align="center">
  <img src="{{ 'img/Rocket/Rocket1.JPG' | relative_url }}" alt="PEGGASUS launch" style="max-width: 600px; margin: 1rem auto; display:block;">
  <span style="font-size: 0.9rem; color: gray; display:block; text-align:center;">Figure 1 — PEGGASUS at liftoff</span>
</p>

<hr>

<h4>Technical approach</h4>
<p>
To meet these requirements, we used <strong>OpenRocket</strong> as the main design tool and followed a simulation-driven process. We ran simulations to converge on a configuration that satisfied the apogee and flight-time constraints. Based on the simulation results, we sized the recovery system accordingly, including a <strong>76 cm diameter parachute</strong> to target the required descent profile. We iterated on geometry—nose cone shape, fin planform, and mass distribution—validated apogee, flight time, and stability in simulation, then built the hardware to match the simulated configuration as closely as possible.
</p>

<p align="center">
  <img src="{{ 'img/Rocket/Simulation Rocket.png' | relative_url }}" alt="OpenRocket simulation results" style="max-width: 750px; margin: 1rem auto; display:block;">
  <span style="font-size: 0.9rem; color: gray; display:block; text-align:center;">Figure 2 — OpenRocket simulation output</span>
</p>

<hr>

<h4>Key design choices</h4>
<ul>
  <li><strong>CAD design:</strong> I modeled the nose cone in <strong>SolidWorks</strong>, optimized its shape for subsonic flight, and <strong>3D-printed</strong> it for integration on the rocket.</li>
  <li><strong>Stability and fin sizing:</strong> We iterated on the number and type of fins to maintain stability in windy conditions while staying consistent with the simulation model. We chose simple square fins to reduce uncertainty relative to OpenRocket assumptions.</li>
  <li><strong>Payload protection:</strong> We designed egg protection using cotton and puffed rice. The puffed rice provided impact damping, while the cotton helped isolate the egg from vibrations.</li>
  <li><strong>Electronics and deployment logic:</strong> We implemented a simple Raspberry Pi countdown to trigger (1) ignition at launch and (2) a delayed parachute deployment using a secondary igniter after a fixed delay.</li>
  <li><strong>Integration layout:</strong> We defined the internal placement of the electronics, battery, igniters, parachute, and payload to preserve stability and enable reliable parachute deployment, targeting a <strong>center-of-mass to center-of-pressure offset below 5 cm</strong>.</li>
</ul>

<hr>

<h4>Results</h4>

<p>
<video controls playsinline preload="metadata" style="width: 100%; max-width: 300px; display: block; margin: 0.5rem auto;">
  <source src="{{ '/img/Rocket/video%20fusee.mp4' | relative_url }}" type="video/mp4">
  Your browser does not support the video tag.
</video>
</p>

<ul>
  <li><strong>Simulation vs. reality:</strong> The propulsion and ballistic phases matched the simulation well overall. The main deviation came from recovery timing: the parachute deployed later than expected.</li>
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
        <td><strong>Time to trajectory apex</strong></td>
        <td>\(\displaystyle t_{max}=t_{op}+\frac{v_{op}\cos(\alpha)}{g}\)</td>
        <td>\(\displaystyle t_{max}=t_{op}+\tau\,\ln\!\left(1+\frac{v_{op}\cos(\alpha)}{g\,\tau}\right)\)</td>
        <td>9.68 s</td>
        <td>9.69 s</td>
        <td>7.68 s</td>
        <td>7.76 s</td>
      </tr>

      <tr>
        <td><strong>Maximum altitude reached</strong></td>
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
        <td><strong>Horizontal range if the parachute does not deploy</strong></td>
        <td>\(\displaystyle O_x=v_{0}\sin(\alpha)\,(t-t_{0})\)</td>
        <td>\(\displaystyle O_x=v_{0}\sin(\alpha)\,\tau\left(1-e^{-\frac{t_{max}-t_{op}}{\tau}}\right)\)</td>
        <td>97.4 m</td>
        <td>97.4 m</td>
        <td>110 m</td>
        <td>47 m</td>
      </tr>

      <tr>
        <td><strong>Liftoff acceleration</strong></td>
        <td>\(\displaystyle a=-g+\frac{F}{m}\)</td>
        <td>\(\displaystyle a=-g+\frac{F}{m}\)</td>
        <td>34.3 m·s<sup>−2</sup></td>
        <td>34.3 m·s<sup>−2</sup></td>
        <td>36.6 m·s<sup>−2</sup></td>
        <td>—</td>
      </tr>

      <tr>
        <td><strong>Propulsion phase duration</strong></td>
        <td>\(\displaystyle t_{op}\)</td>
        <td>\(\displaystyle t_{op}\)</td>
        <td>2.18 s</td>
        <td>2.18 s</td>
        <td>2.18 s</td>
        <td>—</td>
      </tr>

      <tr>
        <td><strong>Velocity at the end of propulsion</strong></td>
        <td>\(\displaystyle v_{op}=\left(-g+\frac{F}{m}\right)\,t_{op}\)</td>
        <td>\(\displaystyle v_{op}=\left(-g+\frac{F}{m}\right)\tau\left(1-e^{-\frac{t_{op}}{\tau}}\right)\)</td>
        <td>74.8 m·s<sup>−1</sup></td>
        <td>74.8 m·s<sup>−1</sup></td>
        <td>66.2 m·s<sup>−1</sup></td>
        <td>72.1 m·s<sup>−1</sup></td>
      </tr>

      <tr>
        <td><strong>Ballistic-phase velocity components</strong></td>
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
        <td><strong>Speed at parachute deployment</strong></td>
        <td>\(\displaystyle v_{pa}=\sqrt{v_y^2(7s)+v_x^2(7s)}\)</td>
        <td>\(\displaystyle v_{pa}=\sqrt{v_y^2(7s)+v_x^2(7s)}\)</td>
        <td>13.91 m·s<sup>−1</sup></td>
        <td>13.86 m·s<sup>−1</sup></td>
        <td>5.5 m·s<sup>−1</sup></td>
        <td>12.4 m·s<sup>−1</sup></td>
      </tr>

      <tr>
        <td><strong>Impact speed at ground</strong></td>
        <td>\(\displaystyle v_{imp}=\sqrt{\frac{mg}{B\,\rho_{air}}}\)</td>
        <td>—</td>
        <td>5.82 m·s<sup>−1</sup></td>
        <td>—</td>
        <td>5.56 m·s<sup>−1</sup></td>
        <td>7.2 m·s<sup>−1</sup></td>
      </tr>

      <tr>
        <td><strong>Total flight time</strong></td>
        <td>—</td>
        <td>—</td>
        <td>—</td>
        <td>—</td>
        <td>53.5 s</td>
        <td>41.0 s</td>
      </tr>

      <tr>
        <td><strong>Altitude at end of propulsion</strong></td>
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
  <li><strong>What failed and why:</strong> The deployment sequence did not perform as intended because the same battery powered both igniters. After the first ignition, the remaining current was not sufficient to heat the copper wire fast enough to trigger the parachute charge. This issue affected roughly half of the teams, since the battery choice was imposed and not under our control.</li>
  <li><strong>Conclusion:</strong> Despite the recovery issue, the propulsion and ballistic predictions were highly accurate, confirming that the simulation-driven sizing approach was robust and that the main limitation was the deployment power margin rather than the aerodynamic design.</li>
</ul>

<p align="center">
  <img src="{{ 'img/Rocket/rocket destroy.JPG' | relative_url }}" alt="Post-flight rocket condition" style="max-width: 900px; margin: 1rem auto; display:block;">
  <span style="font-size: 0.9rem; color: gray; display:block; text-align:center;">Figure 3 — Post-flight condition (Rapid Unscheduled Disassembly)</span>
</p>

</div>
