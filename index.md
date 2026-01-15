---
layout: project_page
permalink: /

title: PlugTrack: Multi-Perceptive Motion Analysis for Adaptive Fusion in Multi-Object Tracking 
affiliations:
    Kyung Hee University 
arxiv: https://arxiv.org/pdf/2511.13105
paper: https://openreview.net/pdf?id=5sAC3hZ3dq
code: https://github.com/VisualScienceLab-KHU/PlugTrack
---

![Figure1](/static/image/figure1.png)
*TD;LR: We observe that the primary bottleneck in 3D semantic scene graph prediction lies in object representation, which directly impacts the accuracy of predicate reasoning. (a) Baseline (VL-SAT) embeds object features non-discriminatively, leading to low-confidence
predictions and frequent object misclassifications, which degrade relationship accuracy. In contrast,
(b) our method embeds object features in a more discriminative manner, yielding high confidence
scores and more accurate object classifications. Consequently, relationship predictions are significantly improved, resulting in a more coherent and semantically accurate scene graph.*

<!-- Using HTML to center the abstract -->
<div class="columns is-centered has-text-centered">
    <div class="column is-four-fifths">
        <h2>Abstract</h2>
        <div class="content has-text-justified">
3D Semantic Scene Graph Prediction aims to detect objects and their semantic relationships in 3D scenes, and has emerged as a crucial technology for robotics and AR/VR applications. While previous research has addressed dataset limitations and explored various approaches including Open-Vocabulary settings, they frequently fail to optimize the representational capacity of object and relationship features, showing excessive reliance on Graph Neural Networks despite insufficient discriminative capability. In this work, we demonstrate through extensive analysis that the quality of object features plays a critical role in determining overall scene graph accuracy. To address this challenge, we design a highly discriminative object feature encoder and employ a contrastive pretraining strategy that decouples object representation learning from the scene graph prediction. This design not only enhances object classification accuracy but also yields direct improvements in relationship prediction. Notably, when plugging in our pretrained encoder into existing frameworks, we observe substantial performance improvements across all evaluation metrics. Additionally, whereas existing approaches have not fully exploited the integration of relationship information, we effectively combine both geometric and semantic features to achieve superior relationship prediction. Comprehensive experiments on the 3DSSG dataset demonstrate that our approach significantly <b>outperforms previous state-of-the-art methods</b>.
        </div>
    </div>
</div>

---

## Core Contributions
1. We identify the <b>overlooked importance of object representation in prior 3DSSG methods</b> and propose a Discriminative Object Feature Encoder, pretrained independently to serve as a robust semantic foundation—improving not only our model but also enhancing performance when integrated into existing frameworks.
2. A novel <b>Relationship Feature Encoder</b> that combines object pair embeddings with geometric relationship information, enhanced by LSE
3. A <b>Bidirectional Edge Gating mechanism</b> that explicitly models subject-object asymmetry, along with a <b>Global Spatial Enhancement</b> to incorporate holistic spatial context
4. We validate our approach through extensive experiments, achieving significant performance improvements over <b>state-of-the-art 3DSSG methods</b>.

<br>


## Proposed Method

> We propose a two-stage training framework for 3D semantic scene graph prediction. In the first stage, we pretrain an object encoder to learn discriminative object-level feature representations. In the second stage, we predict the full 3D scene graph using a graph neural network equipped with our proposed components: Bidirectional Edge Gating (BEG), Local Spatial Enhancement (LSE), and Global Spatial Enhancement (GSE).

![Object Encoder Pretrain](/static/image/figure2.png)

Architecture of first stage (object encoder pretraining): The encoder extracts object embedding from point clouds via affine transformation, aligned with text/visual CLIP features

![Scene Graph Prediction](/static/image/figure4.png)


Architecture of second stage (3D semantic scene graph prediction): Object features are refined via Global Spatial Enhancement to incorporate global spatial context based on inter-object distances, producing enhanced features. Simultaneously, the Local Spatial Enhancement locally preserves geometric relationships between object pairs. The Bidirectional Gated Graph Attention Network then selectively modulates the information of reverse edges, effectively capturing asymmetric relationships between objects


<br>


## 3D Scene Graph Prediction

![Qualitative Research](/static/image/figure5.png)

Qualitative comparison between baseline (VL-SAT) and ours: VL-SAT frequently misclassifies visually similar but semantically distinct objects such as cabinet and chair, or stool and garbage bin, which leads to erroneous relationship predictions. In contrast, our method correctly identifies object categories, thereby facilitating accurate and consistent relationship prediction

<br>

## Object Feature Representation

<div style="text-align: center;">
  <img src="./static/image/figure6.png" width="80%" alt="figure6">
</div>

We visualize the learned object embedding space using t-SNE for the ten most frequent object categories in the dataset. Compared to (a) baseline (VL-SAT), (b) our approach yields more compact and well-separated clusters, particularly for structurally similar object pairs such as *ceiling–floor*, *wall–door*, and *curtain–window*. These results suggest that our object encoder learns more discriminative features, which provide a semantically stronger foundation for subsequent relationship classification

<br>

## Citation
```
@article{heo2025object,
  title={Object-Centric Representation Learning for Enhanced 3D Scene Graph Prediction},
  author={Heo, KunHo and Kim, GiHyun and Kim, SuYeon and Cho, MyeongAh},
  journal={arXiv preprint arXiv:2510.04714},
  year={2025}
}
```