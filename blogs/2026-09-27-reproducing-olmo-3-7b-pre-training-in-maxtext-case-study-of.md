---
title: "Reproducing OLMo 3 7B Pre-training in MaxText: case study of large scale training on TPUs"
url: "https://developers.googleblog.com/reproducing-olmo-3-7b-pre-training-in-maxtext-case-study-of-large-scale-training-on-tpus/"
date: "2026-09-27"
feed_url: "https://developers.googleblog.com/feed/"
---
The MaxText team successfully reproduced AI2’s OLMo 3 7B language model from scratch on Google Cloud TPUs using JAX/XLA, precisely matching the original PyTorch-on-GPU reference across pre-training and mid-training stages on all held-out evaluations. The implementation achieved up to 57.4% Model Flops Utilization (MFU) and demonstrated robust infrastructure portability by surviving mid-run cluster resizes and cross-generation TPU shifts without requiring recipe alterations. Crucially, the exercise proved the necessity of comprehensive held-out validation by catching a silent data-loader memori
