---
title: "Enable on-demand expertise with Agent Skills in Genkit Go"
url: "https://developers.googleblog.com/enable-on-demand-expertise-with-agent-skills-in-genkit-go/"
date: "2026-08-01"
feed_url: "https://developers.googleblog.com/feed/"
---
To prevent context window bloat and reduce token consumption, Genkit Go introduces Agent Skills based on a progressive disclosure architecture. Developers can package specialized instructions, scripts, and references into modular SKILL.md bundles where only the frontmatter metadata is initially exposed to the agent's system prompt. When a task matches the skill's description, Genkit's middleware dynamically loads the full instruction body and associated assets, ensuring the model accesses precise workflows exactly when needed.
