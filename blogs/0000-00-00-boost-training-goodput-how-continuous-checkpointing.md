---
title: "Boost Training Goodput: How Continuous Checkpointing Optimizes Reliability in Orbax and MaxText"
url: "https://developers.googleblog.com/boost-training-goodput-how-continuous-checkpointing-optimizes-reliability-in-orbax-and-maxtext/"
date: ""
author: ""
feed_url: "https://developers.googleblog.com/feed/"
---
The newly introduced continuous checkpointing feature in Orbax and MaxText is designed to optimize the balance between reliability and performance during model training, addressing issues with conventional fixed-frequency checkpointing. Unlike fixed intervals—which can either compromise reliability or bottleneck performance—continuous checkpointing maximizes I/O bandwidth and minimizes failure risk by asynchronously initiating a new save operation only after the previous one successfully completes.
