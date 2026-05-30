---
title: "Transfer Learning in Scientific Machine Learning"
date: 2026-05-28
layout: post
image: /assets/img/lora.jpg
thumbnail: /assets/img/lora.jpg
---

When training an AI/ML with CAE data, how can we minimize data generation and maximize return with expensive, scarce CAE data? Transfer Learning can be the breakthrough.

I'm attending the hashtag#NAFEMS Americas Conference for the first time. About a third of the talks, maybe more, are on AI/ML. Two clear trends stand out: hashtag#AgenticAI and hashtag#ScientificML (hashtag#PhysicsAI). I'll save Agentic AI for another post. This one is about Scientific ML, where the progress has been remarkable.
Architectures, both open-source and proprietary, have reached impressive levels of accuracy. UX and deployment have been refined to the point where end users no longer need to be AI/ML experts (a double-edged sword, but that's a separate conversation). Yet one critical piece still demands careful consideration: training data generation.

Over the years, I keep getting the same questions:
"How many CAE runs do we need to train a model?"
"What if my development program can be done with fewer runs than what's needed for training data?"

This is the ROI question that every engineering organization must answer before adopting SciML. In an industrial setting, we can't run thousands of CAE simulations for the sake of model building for every single design. The cost parity doesn't exist. On top of that, more data means more overhead for training (Data generation and training costs have been reviewed in an excellent article by Neil Ashton: https://lnkd.in/gQNVGiqF). So we need to be careful what we wish for: more data is a blessing and a curse. For SciML to scale in industry, we need a smarter way to maximize the return from expensive CAE simulations and maintain training cost under control.

Alok Warey and I tackled this head-on with Transfer Learning. The idea: take a model already trained on existing vehicle families and adapt it to a completely new, unseen vehicle with minimal additional data. We pretrained on four vehicle families, then fine-tuned for a fifth using just 30 CFD runs—compared to ~100 normally required.

We systematically compared three strategies:
→ Full Fine-Tuning
→ Lightweight (Partial) Fine-Tuning
→ Low-Rank Adaptation (LoRA)

The differences were dramatic. Curious which one worked and why the others failed? Check out our preprint: https://lnkd.in/ggmSG9xq (*Spoiler warning: see the figure.*)

Transfer Learning offers a practical path to keeping training data generation to a minimum while maintaining prediction quality. One pretrained backbone, lightweight adapters per vehicle family, trained in 90% less time from 70% less data. And we just took the first step with geometry: think of all the other things we can fine-tune against.

On a related note: it is time to consider diversifying the open-source databases to cover various vehicle families. Any takers to work with us?
