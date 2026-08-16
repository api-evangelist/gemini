---
title: "HeyGen x Google Cloud: Bringing Avatar IV to TPUs"
url: "https://developers.googleblog.com/heygen-x-google-cloud-bringing-avatar-iv-to-tpus/"
date: "2026-08-15"
feed_url: "https://developers.googleblog.com/feed/"
---
HeyGen ported their 18B+ parameter Avatar IV video generation model to Google Cloud's Trillium (v6e) TPUs via torchax and XLA, utilizing FSDP and Ulysses sequence parallelism across an eight-chip mesh. To achieve a 1.86x speedup for real-time streaming, the engineering team pipelined exposed all-to-all collectives, aligned sparse attention block sizes to eliminate mask padding, and bypassed softmax serial dependencies using a precomputed Cauchy-Schwarz upper bound. These custom Pallas kernel and compiler optimizations were deployed only after passing rigorous two-tier quality gates to guarante
