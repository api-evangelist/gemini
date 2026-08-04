---
title: "Systems Engineering Playbook: Optimizing Qwen 3.5-397B MoE on Ironwood (TPU7x)"
url: "https://developers.googleblog.com/systems-engineering-playbook-optimizing-qwen-35-397b-moe-on-ironwood-tpu7x/"
date: "2026-07-20"
feed_url: "https://developers.googleblog.com/feed/"
---
To serve the 397B-parameter Qwen 3.5 Mixture-of-Experts (MoE) model on Ironwood TPUs, engineers developed a modular JAX/Pallas optimization stack that achieved up to a 4.7x inference speedup for prefill-heavy workloads. The team bypassed severe hardware sharding constraints by deploying a hybrid Data Parallelism and Expert Parallelism (DP+EP) topology, paired with custom low-level communication fusions like a hierarchical reduce-scatter to optimize cross-device token routing. Finally, by executing hardware-aware custom kernels—such as Batched Ragged Page Attention and a fully-fused Gated Delta
