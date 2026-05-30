---
title: "SciML Data Challenge"
date: 2026-05-29
layout: post
image: /assets/img/data_pipeline_comparison.jpeg
thumbnail: /assets/img/data_pipeline_comparison.jpeg
---

![Data pipeline comparison](/assets/img/data_pipeline_comparison.jpeg)

Data is the king of any AI and Machine Learning task, but in the world of Scientific Machine Learning (SciML), it acts more like a tyrant. Honestly, I often feel the presence of Sauron in my data farm whenever I start a new project—that heavy, overbearing weight of massive datasets looming over everything.

What makes SciML data so unique, and frankly difficult, is its sheer individual size. While traditional ML might deal with millions of tiny files, a single data point in SciML can easily take up hundreds of megabytes to a couple of gigabytes. It’s always a bit funny when I tell people I’m training a model with "only" a hundred data points; they think it’s a toy problem until they realize those hundred points are hogging several terabytes of storage. When you scale that up to something like the massive external aerodynamics dataset recently showcased by PhysicsX with over 20,000 data points (https://lnkd.in/g7WBwjeu) , the orchestration challenge becomes mind-boggling.

Having this much data is a blessing for model accuracy but a curse for practical training. You simply can’t feed this beast with a single GPU, making HPC an absolute necessity. But then we face the ultimate bottleneck: how do we actually get that data to the GPUs? The old-school solution of using a single, massive data farm with an NFS mount is quickly becoming a relic of the past because the latency is just unbearable, especially in cloud-based systems.

The industry is pushing toward leveraging local scratch with high-speed NVMe tucked inside each compute node. And while modern NVMes offer many terabytes of capacity, they still can't hold the entirety of a massive SciML training set. We need to actively "feed" the compute nodes—we need a sophisticated orchestration of the training data feed.

We can try Lazy Copy, prefetching at each epoch, or even look at solutions like Mosaic Streaming Dataset (MSD) that have revolutionized LLM training. However, SciML remains the outlier. Most streaming tools are optimized for billions of tiny samples, whereas in our world, a single data point might be larger than an entire shard in a typical LLM study.

So far, the research community in SciML has been rightfully obsessed with architecture—designing the next great PINN or Neural Operator. But as we move toward Foundation Models for physics, I believe it’s time to consider best practices for practical use. We need to start thinking deeply about how to orchestrate data management and training pipelines for these massive tensors, or we’ll find our fastest GPUs just sitting there, starving for data.

...and yes, as you might have guessed, I've been writing this post while waiting for my data to be copied to a local NVMe on my compute node from my data farm. I am the living proof of why data orchestration is so critical in SciML.
