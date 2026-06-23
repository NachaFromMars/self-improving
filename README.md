# self-improving — Build compound knowledge over time

> Structured memory, correction learning, and graceful scaling across projects and years. A tiered knowledge store that grows smarter the longer you use it.

[![OpenClaw Skill](https://img.shields.io/badge/OpenClaw-Skill-blueviolet)](https://github.com/NachaFromMars)

## Overview
self-improving provides a structured framework for accumulating and organizing agent knowledge over time. Memory is split into a hot tier (≤100 lines, always loaded), per-project learnings, domain-specific knowledge, and a cold archive for decayed patterns. A corrections log tracks the last 50 corrections. Four reference files cover the learning mechanics, security boundaries, scaling rules, and memory operations.

## Features
- **HOT memory** — `memory.md` (≤100 lines, always in context)
- **Topic index** — `index.md` with line counts per topic
- **Per-project** — `projects/` for project-specific learnings
- **Domain-specific** — `domains/` (code, writing, communications)
- **Cold archive** — `archive/` for decayed patterns
- **Corrections log** — `corrections.md`, last 50 entries
- **References** — `learning.md`, `boundaries.md`, `scaling.md`, `operations.md`

## Usage / Quick Start
All memory lives in `~/self-improving/`. Create on first use, then let the skill maintain and query it over time.

## Trigger Keywords (OpenClaw)
self-improving, learn from mistakes, compound knowledge, build memory, correction learning, scale knowledge

## Related Skills
- [self-improving-agent](https://github.com/NachaFromMars/self-improving-agent) — event-driven correction capture
- [memory-tiering](https://github.com/NachaFromMars/memory-tiering) — HOT/WARM/COLD tier management

---
Part of the [NachaFromMars](https://github.com/NachaFromMars) OpenClaw skill ecosystem.
