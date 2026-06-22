---
name: Self-Improving
slug: self-improving
version: 1.0.0
description: Build compound knowledge over time with structured memory, correction learning, and graceful scaling across projects and years.
metadata: {"clawdbot":{"emoji":"🧠","requires":{"bins":[]},"os":["linux","darwin","win32"]}}
---

## Architecture

Memory lives in ~/self-improving/ with tiered structure. See `memory-template.md` for setup.

```
~/self-improving/
├── memory.md          # HOT: ≤100 lines, always loaded
├── index.md           # Topic index with line counts
├── projects/          # Per-project learnings
├── domains/           # Domain-specific (code, writing, comms)
├── archive/           # COLD: decayed patterns
└── corrections.md     # Last 50 corrections log
```

## Quick Reference

| Topic | File |
|-------|------|
| Learning mechanics | `learning.md` |
| Security boundaries | `boundaries.md` |
| Scaling rules | `scaling.md` |
| Memory operations | `operations.md` |

## Data Storage

All data stored in `~/self-improving/`. Create on first use:
```bash
mkdir -p ~/self-improving/{projects,domains,archive}
```

## Scope

This skill ONLY:
- Learns from explicit user corrections
- Stores preferences in local files (`~/self-improving/`)
- Reads its own memory files on activation

This skill NEVER:
- Accesses calendar, email, or contacts
- Makes network requests
- Reads files outside `~/self-improving/`
- Infers preferences from silence or observation

## Self-Modification

This skill NEVER modifies its own SKILL.md.
All learned data stored in `~/self-improving/memory.md` and subdirectories.

## Core Rules

### 1. Learn from Corrections Only
- Log when user explicitly corrects you
- Never infer from silence or observation
- After 3 identical corrections → ask to confirm as rule

### 2. Tiered Storage
| Tier | Location | Size Limit | Behavior |
|------|----------|------------|----------|
| HOT | memory.md | ≤100 lines | Always loaded |
| WARM | projects/, domains/ | ≤200 lines each | Load on context match |
| COLD | archive/ | Unlimited | Load on explicit query |

### 3. Automatic Promotion/Demotion
- Pattern used 3x in 7 days → promote to HOT
- Pattern unused 30 days → demote to WARM
- Pattern unused 90 days → archive to COLD
- Never delete without asking

### 4. Namespace Isolation
- Project patterns stay in `projects/{name}.md`
- Global preferences in HOT tier (memory.md)
- Domain patterns (code, writing) in `domains/`
- Cross-namespace inheritance: global → domain → project

### 5. Conflict Resolution
When patterns contradict:
1. Most specific wins (project > domain > global)
2. Most recent wins (same level)
3. If ambiguous → ask user

### 6. Compaction
When file exceeds limit:
1. Merge similar corrections into single rule
2. Archive unused patterns
3. Summarize verbose entries
4. Never lose confirmed preferences

### 7. Query Support
User can ask:
- "What do you know about X?" → search all tiers
- "Show my [project] patterns" → load specific namespace
- "Forget X" → remove from all tiers
- "What changed this month?" → show corrections.md

### 8. Transparency
- Every action from memory → cite source: "Using X (from projects/foo.md:12)"
- Weekly digest available: patterns learned, demoted, archived
- Full export on demand: all files as ZIP

### 9. Security Boundaries
See `boundaries.md` — never store credentials, health data, third-party info.

### 10. Graceful Degradation
If context limit hit:
1. Load only memory.md (HOT)
2. Load relevant namespace on demand
3. Never fail silently — tell user what's not loaded
