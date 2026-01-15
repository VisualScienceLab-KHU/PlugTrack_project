---
layout: project_page
permalink: /

title: "PlugTrack: Multi-Perceptive Motion Analysis for Adaptive Fusion in Multi-Object Tracking"
venue: "AAAI 2026"
affiliations: "Department of Software Convergence, Kyung Hee University"
emails: "{tmdwo8814, diplomat3334, maycho}@khu.ac.kr"

# Links
arxiv: "https://arxiv.org/abs/2511.13105"
paper: "https://arxiv.org/pdf/2511.13105.pdf"
code: "https://github.com/VisualScienceLab-KHU/PlugTrack"

# Optional (layout에서 사용)
description: "PlugTrack adaptively fuses Kalman filter and data-driven motion predictors via multi-perceptive motion analysis for robust multi-object tracking."
keywords: "Multi-Object Tracking, MOT, Kalman Filter, Motion Prediction, Adaptive Fusion, PlugTrack"

# Author list (layout이 동적으로 렌더링)
authors:
  - name: "Seungjae Kim"
    url: "https://tmdwo8814.github.io/"
  - name: "SeungJoon Lee"
    url: "https://my.surfit.io/w/1720083748"
  - name: "MyeongAh Cho"
    url: "https://myeongahcho.netlify.app/"
    sup: "*"
corresponding_mark: "*"
corresponding_text: "Corresponding Author"
---

![Teaser](/static/image/figure1.png)
Qualitative comparison of motion prediction on DanceTrack (frames 508–511). PlugTrack adaptively fuses Kalman filter and data-driven predictions to better handle both linear and non-linear motions, achieving up to +10.6 IoU gains.

<!-- Using HTML to center the abstract -->
<div class="columns is-centered has-text-centered">
  <div class="column is-four-fifths">
    <h2>Abstract</h2>
    <div class="content has-text-justified">
Multi-object tracking (MOT) predominantly follows the tracking-by-detection paradigm, where Kalman filters serve as the standard motion predictor due to computational efficiency but inherently fail on non-linear motion patterns. Conversely, recent data-driven motion predictors capture complex non-linear dynamics but suffer from limited domain generalization and computational overhead. Through extensive analysis, we reveal that even in datasets dominated by non-linear motion, Kalman filter outperforms data-driven predictors in up to 34% of cases, demonstrating that real-world tracking scenarios inherently involve both linear and non-linear patterns. To leverage this complementarity, we propose PlugTrack, a novel framework that adaptively fuses Kalman filter and data-driven motion predictors through multi-perceptive motion understanding. Our approach employs multi-perceptive motion analysis to generate adaptive blending factors. PlugTrack achieves significant performance gains on MOT17/MOT20 and state-of-the-art on DanceTrack without modifying existing motion predictors. To the best of our knowledge, PlugTrack is the first framework to bridge classical and modern motion prediction paradigms through adaptive fusion in MOT.
    </div>
  </div>
</div>

---

## Core Contributions
1. **Key insight:** Even in non-linear datasets, **Kalman filter can outperform data-driven predictors in a substantial fraction of cases** (e.g., up to 34%), motivating adaptive fusion rather than replacement.
2. **PlugTrack framework:** A **plug-and-play** mechanism that **adaptively fuses** Kalman filter and any data-driven motion predictor **without modifying** the base predictor.
3. **Multi-perceptive motion understanding:** Contextual Motion Encoder (CME) that analyzes motion via:
   - Motion Pattern Module (MPM),
   - Prediction Discrepancy Module (PDM),
   - Uncertainty Quantification Module (UQM).
4. **Stable training:** Monte Carlo Alpha Search (MCAS) to generate pseudo-GT blending factors and prevent bias collapse.
5. **Strong results + efficiency:** Consistent gains on MOT17/MOT20 and **SOTA on DanceTrack**, while maintaining real-time capability with minimal overhead.

<br>

## Proposed Method (Overview)

![Architecture](/static/image/figure3.png)

> PlugTrack consists of (1) Contextual Motion Encoder (CME) for multi-perceptive motion analysis and (2) Adaptive Blending Generator (ABG) that predicts coordinate-wise blending factors for alpha blending. MCAS is used during training to supervise optimal blending factors.

<br>

## Results

![MOT17_MOT20_Table](/static/image/table1.png)

- **MOT17/MOT20:** PlugTrack improves base predictors (e.g., TrackSSM / DiffMOT) and can reach strong HOTA/AssA scores.

![DanceTrack_Table](/static/image/table2.png)

- **DanceTrack:** PlugTrack(DiffMOT) achieves **SOTA HOTA** and improves association/identity metrics via adaptive fusion.

<br>

## Citation
```bibtex
@article{kim2025plugtrack,
  title   = {PlugTrack: Multi-Perceptive Motion Analysis for Adaptive Fusion in Multi-Object Tracking},
  author  = {Kim, Seungjae and Lee, SeungJoon and Cho, MyeongAh},
  journal = {arXiv preprint arXiv:2511.13105},
  year    = {2025}
}