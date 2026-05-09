---
title: "Speeding Up AI: Bringing Google Colossus to PyTorch via GCSFS and Rapid Bucket"
url: "https://developers.googleblog.com/speeding-up-ai-bringing-google-colossus-to-pytorch-via-gcsfs-and-rapid-bucket/"
date: ""
author: ""
feed_url: "https://developers.googleblog.com/feed/"
---
Google Cloud has introduced a high-performance integration that connects Rapid Storage directly to PyTorch via the fsspec interface to eliminate AI training bottlenecks. By utilizing Google’s Colossus architecture and bidirectional gRPC streaming, the solution offers up to 15 TiB/s aggregate throughput and significant reductions in latency. These improvements allow developers to speed up total training time by 23% with zero code changes required beyond updating the storage bucket type.
