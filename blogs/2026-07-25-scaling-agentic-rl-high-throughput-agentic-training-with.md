---
title: "Scaling Agentic RL: High-Throughput Agentic Training with Tunix"
url: "https://developers.googleblog.com/scaling-agentic-rl-high-throughput-agentic-training-with-tunix/"
date: "2026-07-25"
feed_url: "https://developers.googleblog.com/feed/"
---
Tunix is Google’s new JAX-native post-training library designed to eliminate TPU idling bottlenecks when training multi-turn, tool-using LLM reasoning agents. It maximizes hardware throughput by combining highly concurrent, asynchronous rollouts with a decoupled producer-consumer pipeline, ensuring the trainer is constantly fed even while agents wait on network I/O or environment steps. Additionally, Tunix provides plug-and-play abstractions and continuous macro-level profiling, allowing developers to easily integrate custom open-source environments and optimize complex distributed workflows w
