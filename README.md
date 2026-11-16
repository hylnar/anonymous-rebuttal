# Anonymous Rebuttal Evidence — Generalization of Relighting

This repository provides qualitative evidence for the rebuttal: our model,
trained on light-stage OLAT captures, **generalizes beyond its training
distribution** — to (1) full-body in-the-wild portraits and (2) general
everyday objects. All results are single-feed inference outputs (the w333
full-window configuration described in the paper), with no per-sample tuning
and no test-time adaptation.

**How to read the grids:** each row is one subject/object with 8 panels —
- col 1: input image;
- cols 2–4: one-light-at-a-time (OLAT) relit frames at lamp positions
  0 / 165 / 248 of the 331-lamp spiral (fixed exposure — near-black panels
  are expected when the active lamp faces away from the subject);
- cols 5–8: relighting under four novel environment maps — one environment
  per column, shared across all subjects/objects (auto exposure).

## 1. Full-body in-the-wild relighting (4 subjects)

Inputs are full-body portraits from SHHQ, preprocessed by our in-the-wild
pipeline (no light-stage capture; the model is never given the test subjects).

![fullbody overview](figs/overview_fullbody.png)

Full-resolution per-subject sheets: [`figs/fullbody/`](figs/fullbody/)
(subjects: 573, 4628, 4919, 7590).

## 2. General object relighting (Composition-1k, 10 objects)

Inputs are objects and pets from Composition-1k, relit under novel
illuminations.

Test domain (6 objects):

![comp1k test overview](figs/overview_comp1k_test.png)

Train-adobe domain (4 objects):

![comp1k train overview](figs/overview_comp1k_train.png)

Full-resolution per-object sheets: [`figs/comp1k/`](figs/comp1k/) (10 objects).

## 3. Comparison with diffusion-based relighting (with ground truth)

A held-out light-stage subject relit under three environment maps by two
diffusion-based relighting methods (RelightLive, DiffusionRenderer) and ours,
with **light-stage ground-truth (GT) composites** for reference. The diffusion
baselines introduce color casts, underexposure, and halo/compositing artifacts
around the hair; ours stays artifact-free with consistent identity and light
response closest to GT.

![diffusion comparison](figs/comparison_diffusion_relight.png)

## 4. Comparison with POLAR on in-the-wild inputs

Three in-the-wild subjects under an environment whose dominant light is
rotated **behind** (case 1, 180°), to the **side** (case 2, 90°), and to the
**front** (case 3, 0°) of the subject; all methods are shown with a common
portrait crop and size. Our light-stage simulation outputs OLAT frames over
the full lamp sphere — including lamps behind the subject — so back-lighting
is directly representable (cf. the rim lighting in case 1); POLAR's available
lamp directions are sparser and unpaired with ours (see the footer note in
the figure). Final two columns: our relight composited with POLAR's
background vs. POLAR's relight; rightmost: diffuse/chrome probes.

![polar comparison](figs/comparison_polar_wild.png)

---
*Anonymous evidence repository — provided for review only; please do not
attempt to identify the authors.*
