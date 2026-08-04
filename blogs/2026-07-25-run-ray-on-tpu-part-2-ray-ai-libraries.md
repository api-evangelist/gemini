---
title: "Run Ray on TPU, Part 2: Ray AI libraries"
url: "https://developers.googleblog.com/run-ray-on-tpu-part-2-ray-ai-libraries/"
date: "2026-07-25"
feed_url: "https://developers.googleblog.com/feed/"
---
This second installment explores how Ray’s higher-level libraries—Serve, Data, and Train—abstract the complexities of running AI workloads on Google's TPU slices. Ray Serve uses a simple topology configuration to correctly gang-schedule large multi-host models, while Ray Data eliminates data-loading bottlenecks by feeding accelerators directly with native JAX batches. Finally, JaxTrainer streamlines distributed training across TPUs by automatically handling cross-slice coordination, checkpointing, and fault tolerance.
