---
title: "Run Ray on TPU, Part 1: The foundations"
url: "https://developers.googleblog.com/run-ray-on-tpu-part-1-the-foundations/"
date: "2026-07-25"
feed_url: "https://developers.googleblog.com/feed/"
---
Ray 2.55 introduces official, first-class support for Google Cloud TPUs, enabling developers to run distributed Python workloads on Google's accelerators using the familiar Ray task-and-actor APIs. To handle the strict networking requirement of keeping multi-host TPU "slices" together over their Inter-Chip Interconnect (ICI), the KubeRay Operator on GKE automatically provisions and labels the underlying hardware layout. Ray Core utilizes these labels via its slice_placement_group() primitive to atomically reserve complete slices, allowing developers to deploy jobs through KubeRay, Ray Train, o
