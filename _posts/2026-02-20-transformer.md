---
title: "Transformer"
date: 2026-02-20
layout: post
#image: /assets/img/data_pipeline_comparison.jpeg
#thumbnail: /assets/img/data_pipeline_comparison.jpeg
---

How can we efficiently process industry level large-scale CFD meshes in Transformer-based SciML without losing critical physical resolution?

Transformer is gaining significant momentum in SciML applications because it provides excellent long-distance relationship information, which is critical for many subsonic fluid dynamics in the parabolic regime. However, the O(N2) computational complexity has long been a bottleneck for industrial applications with millions of grid points, leading researchers to focus heavily on reducing this computational overhead. While Transolver (https://lnkd.in/gAH9XJdm) handles this by grouping similar points into slices and AB-UPT (https://lnkd.in/gDzbWEpW) effectively scales through randomly sampled supernodes and anchor points , I recently found a publication that provides a very attractive alternative called MSPT (https://lnkd.in/g2M53bkN).

In MSPT, the whole point cloud is split into multiple patches using a ball tree. At first glance, it might sound like a compromise compared to Transolver, which creates slices over relevant points by softmax to ensure a certain level of semantic relevance. In contrast, the patches in MSPT are partitioned based primarily on geometry. But the real innovation lies in how the attention is performed; it is not restricted only to the supernodes. A multi-scale attention is applied such that attention is performed among all cells within a single patch, combined with attention to the supernodes (functionally a cross-attention) and self-attention among those supernodes. The authors claim this unified operation captures both local and long-range relationships exceptionally well, and I can't wait to try it myself.

On a related note, as Transformers continue to gain more attention in SciML — pun intended — it makes me wonder if decimation should become a standard part of the preprocessing pipeline for industrial applications with multi-million grid points. There is certainly a potential for losing fidelity, but we must remember that high CFD mesh resolution is often a necessary evil required to solve the Navier-Stokes equations numerically. For anything other than solving those governing equations, such high density might actually be an overkill for a surrogate model.

Regarding benchmarking, the authors mentioned they had a difficult time reproducing the results of AB-UPT. In my personal opinion, AB-UPT still possesses unique features such as inherent data augmentation through random sampling, and its branched approach holds so much potential for various industrial applications. With the recent release of the Noether framework (https://lnkd.in/gyrP6hBM) , I hope to see even more rigorous studies exploring the strengths of the AB-UPT architecture in the near future.