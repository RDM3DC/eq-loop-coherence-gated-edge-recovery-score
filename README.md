# Loop-Coherence-Gated Edge Recovery Score

**ID:** eq-loop-coherence-gated-edge-recovery-score  
**Score:** 93  
**Units:** OK  
**Theory:** PASS-WITH-ASSUMPTIONS  
**Source:** QWZ Recovery Dashboard + ARP locking lineage

## Equation

$$
E_{\mathrm{loop}}(t)=\frac{\eta_{\mathrm{tr}}(t)\,f_{\partial}(t)\,f_{\mathrm{top}}(t)}{1+\rho_{\mathrm{slip}}(t)}\,\exp\!\left[-\gamma\,|S(t)-S_{\mathrm{eq}}|\right]\left[(1-\kappa_{\Psi})+\frac{\kappa_{\Psi}}{2}\bigl(1+\Psi(t)\bigr)\right],\quad \Psi(t)=\frac{1}{N_p}\sum_{p=1}^{N_p}\cos\!\left(\frac{\Theta_p}{\pi_a}\right)
$$

## Description

Builds on LB #23 (Entropy-Gated Edge Recovery Score), LB #7 (Topological Coherence Order Parameter), and complements LB #8 (Flat-Channel Loop Signature (pi_f Health Observable)). This lineage-preserving recovery observable multiplies the transport-entropy score by a tunable loop-coherence gate derived from plaquette holonomy, so it distinguishes superficially good rerouting from genuinely loop-consistent, topologically locked recovery after damage and ablation.

## Assumptions

- Transfer efficiency eta_tr(t), boundary fraction f_partial(t), top-edge fraction f_top(t), slip density rho_slip(t), entropy S(t), and plaquette holonomies Theta_p(t) are measured on a common time window from the same damaged-lattice trajectory.
- Psi(t)=1/N_p sum_p cos(Theta_p/pi_a) is a valid loop-coherence proxy, with Psi near 1 in locked regimes and smaller values in disordered or slipping regimes.
- 0 <= kappa_Psi <= 1 so the loop-coherence factor is a bounded, dimensionless gate rather than a replacement for the transport score.
- pi_a > 0 and the plaquette count N_p is fixed over the comparison window.
- The observable is a reduced ranking and diagnostic score, not a microscopic replacement for the full adaptive conductance dynamics.

## Evidence

- Builds directly on LB #23 (Entropy-Gated Edge Recovery Score) and recovers LB #23 exactly when kappa_Psi = 0.
- Builds directly on LB #7 (Topological Coherence Order Parameter) and the plaquette holonomy equation Theta_p = sum sigma_p,e theta_R,e; in the locked limit Psi -> 1 the loop gate becomes neutral and E_loop -> E_edge.
- Companion to LB #8 (Flat-Channel Loop Signature (pi_f Health Observable)): LB #8 acts as a localized loop-health precursor, while E_loop is a system-level recovery ranker that stays high only when transport, entropy, and loop coherence agree.
- Dimensional check: eta_tr, f_partial, f_top, rho_slip, Psi, and exp[-gamma |S-S_eq|] are dimensionless, so E_loop is dimensionless like LB #23.
- Executable replication: AdaptiveCAD-Manim/solver/egatl.py already tracks effective transfer, boundary current, top-edge fraction, slip density, entropy gating, and damage/recovery protocols on the same QWZ-style lattice state.
- Replication artifact data/artifacts/arp_topology_benchmark_v2/arp_topology/outputs/recovery_demo/summary.json reproduces a damaged-lattice benchmark with full_law final boundary fraction 0.655135 versus principal_branch 0.477963 and transfer efficiency 0.462059 versus 0.305733, providing a concrete regime where a loop-consistency gate is meaningful.
- Experimental-style falsifier: compare runs with similar E_edge but different Psi(t) trajectories; the gated score should rank the more holonomy-coherent run higher and better predict sustained post-damage recovery.

## Repository Structure

```text
images/       visualizations and plots
simulations/  scripts and notebooks
derivations/  derivation notes
notes/        research notes
```

## Links

- TopEquations leaderboard: https://rdm3dc.github.io/TopEquations/leaderboard.html
- TopEquations repository: https://github.com/RDM3DC/TopEquations
- Recovery traces artifact: https://github.com/RDM3DC/TopEquations/blob/main/data/artifacts/arp_topology_benchmark_v2/arp_topology/outputs/recovery_demo/recovery_traces.png
