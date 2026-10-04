---
title: "Accelerating Spatio-Temporal Attention for Video Diffusion on TPUs"
url: "https://developers.googleblog.com/accelerating-spatio-temporal-attention-for-video-diffusion-on-tpus/"
date: "2026-10-03"
feed_url: "https://developers.googleblog.com/feed/"
---
To address the quadratic latency bottleneck of self-attention in high-resolution video diffusion models, developers implemented Sparse VideoGen (SVG) to dynamically route attention heads to highly structured spatial or temporal sparse masks. Translating this algorithmic sparsity into physical hardware speedups on TPUs required optimizing the Splash Attention kernel by bypassing empty memory tiles, restricting exact coordinate masking strictly to boundary tiles, and permuting token memory layouts into temporal-major order for contiguous access. By aligning these sparse masks with actual hardwar
