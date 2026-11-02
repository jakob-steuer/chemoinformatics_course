# docking_example

A worked set of SwissDock results for the docking exercise, for anyone whose own jobs did not come
back in time. **The analysis notebook downloads from here automatically — nothing to do by hand.**

Every archive is unmodified SwissDock output. Each contains a `parameters` file recording the
settings that produced it, so the notebook reads the settings out of the result rather than asking
you to remember what you clicked.

## The archives

Gefitinib and osimertinib, against EGFR wild type (4WKQ) and the resistant T790M/L858R form
(4I22), through both engines. Same box, same preparation, so they are comparable.

| archive | drug | structure | engine |
|---|---|---|---|
| `WT_gefitinib_vina.zip` | gefitinib | 4WKQ, wild type | AutoDock Vina |
| `WT_gefitinib_ac.zip` | gefitinib | 4WKQ, wild type | Attracting Cavities |
| `WT_gefitinib_ac_rep2.zip` | gefitinib | 4WKQ, wild type | Attracting Cavities, **repeat run** |
| `WT_osimertinib_vina.zip` | osimertinib | 4WKQ, wild type | AutoDock Vina |
| `WT_osimertinib_ac.zip` | osimertinib | 4WKQ, wild type | Attracting Cavities |
| `T790M_gefitinib_vina.zip` | gefitinib | 4I22, T790M/L858R | AutoDock Vina |
| `T790M_gefitinib_ac.zip` | gefitinib | 4I22, T790M/L858R | Attracting Cavities |
| `T790M_osimertinib_vina.zip` | osimertinib | 4I22, T790M/L858R | AutoDock Vina |

`WT_gefitinib_ac_rep2.zip` is a second submission of `WT_gefitinib_ac.zip` — same receptor file,
same settings, nothing changed. The difference between those two archives is the method's own
run-to-run noise, with nothing else mixed in.

## `receptors/`

The exact files that were uploaded, for ChimeraX and for reproducing a run. Chain A only, protein
only, waters and all heteroatoms removed, alternate locations stripped keeping altloc A.
`*_gefitinib_crystal.pdb` is the crystallographic pose — the **answer key** for the redocking
control, not an input. `CHECKSUMS.txt` covers every file.

## Settings used

| | AutoDock Vina | Attracting Cavities |
|---|---|---|
| sampling exhaustivity | 4 | 90 (the form's *medium*) |
| random initial conditions | — | 3 |
| cavity prioritisation | — | 70 (*buried*) |
| box size | 20 × 20 × 20 Å | 20 × 20 × 20 Å |
| box centre, 4WKQ | `1.5 194.2 20.4` | same |
| box centre, 4I22 | `10.2 -15.8 11.2` | same |

Box centres are the centroid of the crystallographic gefitinib in each structure. **The two are
completely different because they are different crystals** — coordinates are never transferable
between PDB entries, and using the wrong centre produces poses rather than an error.

## What this set shows

Gefitinib was in both crystals and was stripped out before docking, so the distance from a docked
pose to the crystal pose says whether the method reproduces a known answer. The convention is 2 Å.

| | top-pose RMSD | poses under 2 Å | ring system |
|---|---|---|---|
| Vina → 4WKQ | 2.88 Å | **0/20** | 1.13 Å |
| Vina → 4I22 | 3.45 Å | **0/20** | 0.75 Å |
| AC → 4WKQ, run 1 | 2.88 Å | 6/40 | 0.31 Å |
| AC → 4WKQ, run 2 | 3.41 Å | 2/40 | 0.30 Å |
| AC → 4I22 | **1.45 Å** | 5/40 | 0.35 Å |

- **Vina never generates a pose within 2 Å**, in either structure. The search is not reaching the
  answer, so no scoring function could rescue it.
- **The two identical AC runs disagree** — and the pose count changes threefold — while the ring
  system lands in the same place to 0.01 Å. The scaffold position is what the method determines
  reproducibly; a single whole-molecule RMSD is softer than it looks.
- AC passes the 2 Å test on one structure and fails on the other, same settings, same drug.

T790M makes gefitinib ~66× weaker in patients. Both engines predict the opposite — gefitinib
scores *tighter* on the mutant by Vina (−7.75 → −8.63 kcal/mol), by AC score (2.31 → −0.56) and by
SP-dG (−8.81 → −9.65 kcal/mol). Three scoring functions, all backwards on the case that matters
clinically, by margins far larger than the run-to-run noise above.

That is the lesson of the exercise, and the redocking control called it in advance: a protocol that
cannot place a ligand within 2 Å has not earned the right to rank two structures 0.9 kcal/mol
apart. T790M also raises EGFR's affinity for ATP, which a single docked pose cannot represent at
all.

## Note on one job

Osimertinib into 4I22 with Attracting Cavities is refused by SwissDock's estimator, which will not
accept a job it thinks takes over an hour. The setting that drives the cost is the number of
random initial conditions, not exhaustivity: at RIC 1 the same job is accepted. If
`*_osimertinib_ac_ric1.zip` files appear here, they are that pair, run at RIC 1 on **both**
structures so they stay comparable with each other.

## Credit

Produced with [SwissDock](https://www.swissdock.ch/) (Swiss Institute of Bioinformatics). If you
use it in published work, cite it — the citation is on their site. Structures 4WKQ and 4I22 are
from the [RCSB PDB](https://www.rcsb.org/).
