---
title: "How to Evaluate Live & Voice Agents in ADK"
url: "https://developers.googleblog.com/how-to-evaluate-live-voice-agents-in-adk/"
date: "2026-08-30"
feed_url: "https://developers.googleblog.com/feed/"
---
Moving live voice agents from demo to production requires rigorous, automated testing to handle the unpredictability of real multi-turn conversations. ADK now provides native live evaluation, allowing developers to test graph-based agent workflows against LLM-driven simulated users that generate actual audio via Gemini TTS. By defining evaluation scenarios and natural-language rubrics, you can automatically score audio responses and tool executions, inspect the resulting transcripts in ADK Web, or run the CLI directly in your CI/CD pipeline.
