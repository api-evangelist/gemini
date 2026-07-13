---
title: "We terminated a TPU mid-training and it recovered in seconds: Introduction to elastic training with MaxText"
url: "https://developers.googleblog.com/we-terminated-a-tpu-mid-training-and-it-recovered-in-seconds-introduction-to-elastic-training-with-maxtext/"
date: ""
feed_url: "https://developers.googleblog.com/feed/"
---
Distributed AI training is notoriously fragile because losing a single machine typically crashes the entire multi-node job, forcing a time-consuming, full-workload infrastructure restart. To address this, Google’s JAX ecosystem utilizes elastic training via Pathways, which converts a hardware failure into a catchable Python exception so the running process can survive. When an unplanned failure occurs, the system automatically replaces only the broken worker, restores the last viable checkpoint from Cloud Storage, and resumes training in place—minimizing total downtime to under two minutes wit
