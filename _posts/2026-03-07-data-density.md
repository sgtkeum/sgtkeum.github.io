---
title: "Data Density"
date: 2026-03-07
layout: post
#image: /assets/img/data_pipeline_comparison.jpeg
#thumbnail: /assets/img/data_pipeline_comparison.jpeg
---

SciML (Scientific Machine Learning) comes with a unique set of "high-stakes" challenges. One is the sheer cost of data generation—requiring deep CAE expertise, massive compute, and time, as I mentioned in my previous post.

But there is another hurdle: Data Density. A single CFD or CAE data point can consist of millions of grid points. While these dense meshes are essential for solving the physics via traditional solvers, do we really need all of them for learning the physics?

I’m noticing a fascinating convergence in Transformer-based SciML architectures. The industry is moving away from "process everything at once" toward more strategic, sparse representations. NVIDIA DoMINO constructs computational stencils dynamically from randomly sampled points (https://lnkd.in/gynNsUSm). Emmi AI's AB-UPT (Anchored-Branched Universal Physics Transformer, https://lnkd.in/gDzbWEpW ) was ahead of the curve in Transformer-based approaches, introducing supernodes and anchor points to handle massive datasets efficiently. We've seen similar logic in MSPT(https://lnkd.in/g2M53bkN) , ArGEnt (https://lnkd.in/gvX2BC7V), and SMART (https://lnkd.in/g8GEk3rZ). Now, Transolver has officially joined the ranks, adopting random sampling in its latest evolution Transolver-3 (https://lnkd.in/gTjGUwkn).

While static decimation in preprocessing reduces data size, on-the-fly sampling (sampling randomly at each epoch) offers a secret weapon: Implicit Data Augmentation. By showing the model different points of the same physics at every pass, we force it to learn the underlying continuous field rather than just memorizing a fixed grid—a concept first championed by AB-UPT. But, as noted in the SMART paper sampling must be robust. (ArGEnt uses random sampling only once and keep it fixed throughout training.) If it's too aggressive or poorly distributed, we risk missing the small features or local gradients that define the physics.

The pace of development in Transformer-based SciML is breathtaking. (Funny thing is, I won't be able to keep up without the help of AI - NotebookLM has been really helpful, with audiovisual assistance like the infographic here, and even drafting this very post!) It’s rewarding to see the bottlenecks I face in an industrial setting being dismantled one by one by these evolving architectures.

With the architecture maturing so rapidly, the billion-dollar question shifts: Can our data generation pipelines keep up with the appetite of these new models? Do we really plan to run hundreds of CFD simulations for every single product program?
