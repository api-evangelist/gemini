---
title: "Supercharging LLM inference on Google TPUs: Achieving 3X speedups with diffusion-style speculative decoding"
url: "https://developers.googleblog.com/supercharging-llm-inference-on-google-tpus-achieving-3x-speedups-with-diffusion-style-speculative-decoding/"
date: ""
author: ""
feed_url: "https://developers.googleblog.com/feed/"
---
Researchers at UCSD have successfully implemented DFlash, a block-diffusion speculative decoding method, on Google TPUs to bypass the sequential bottlenecks of traditional autoregressive drafting. By "painting" entire blocks of candidate tokens in a single forward pass rather than predicting them one-by-one, the system achieved average speedups of 3.13x, with peak performance nearly doubling that of existing methods like EAGLE-3.
