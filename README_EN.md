# Seiryu v1.2

**The First God of the Four Gods System — Memory & Inheritance**

[繁體中文](README.md) | **English**

---

## What is Seiryu?

Every time you open a new AI chat window, the AI forgets everything — who you are, what you discussed, what decisions were made.

Seiryu keeps the things that matter. It saves user profiles, dialogue legacies, and task checkpoints as local files, so the next conversation can pick up where the last one left off.

No cloud, no database — just Markdown and JSON files on your machine.

---

## What's New in v1.2

| Improvement | Details |
|-------------|---------|
| More reliable triggers | Added explicit fallback for when AI doesn't detect Seiryu |
| Safe compression | Creates manifest before compression, quarantines originals instead of hard delete |
| Git optional | Core features work without git |
| Semantic matching | Load behavior clearly defined as heuristic semantic matching, not vector search |
| Clearer privacy | Added rules against auto-saving sensitive information |

---

## Six Skills

| Skill | What it does | When to use |
|-------|-------------|-------------|
| User Profile | Remembers who you are | When stable, worth-saving user info is discovered |
| Dialogue Legacy | Saves conversation highlights | When conversation ends or context is nearly full |
| Load History | Retrieves past records | When referencing past events |
| Compress | Organizes old records | When records accumulate too much |
| Checkpoint | Saves multi-step task progress | During complex tasks |
| First Setup | Initializes Seiryu | First use or when `.seiryu/` doesn't exist |

---

## Install

1. Place `seiryu-v1.2/` in your project directory
2. Add to `CLAUDE.md`: `Memory tools: seiryu-v1.2/`
3. If AI doesn't use it automatically, tell it: "Please read seiryu-v1.2/CLAUDE.md first"

For detailed integration options, see `INTEGRATION.md`

---

## Directory Structure

```text
seiryu-v1.2/
  CLAUDE.md                       <- Entry point (for AI)
  README.md                       <- Documentation (Chinese)
  README_EN.md                    <- Documentation (English)
  INTEGRATION.md                  <- Integration guide
  AUDIT.md                        <- v1.2 audit summary
  skills/                         <- Skill manuals (read on demand)
    s1-profile.md
    s2-legacy.md
    s3-load.md
    s4-compress.md
    s5-checkpoint.md
    s6-setup.md
  templates/                      <- Blank templates
    agent_checkpoint.json
    archive_index.md
    compression_manifest.md
    dialogue_legacy.md
    user_profile.md
  .seiryu/                        <- Data root (created after first use)
    user/
    dialogues/
      _quarantine/
      compression_manifests/
      archive_index.md
    checkpoints/
```

---

## Privacy

- All data stays on your machine
- Nothing is uploaded anywhere
- Passwords, API keys, credentials, and government IDs are never saved by default
- All files are Markdown or JSON — fully readable, editable, deletable

---

## Theory

Based on LDRIT (Life-Death Recursive Intelligence Theory).

AI intelligence isn't stored — it's regenerated every time. What gets inherited across conversations directly affects the quality of the next generation.

---

## Four Gods System

| God | Role | Version |
|-----|------|---------|
| Seiryu | Memory & Inheritance | v1.2 |
| Genbu | Defense & Protection | v0.1 |
| Byakko | Diagnosis & Analysis | v0.2 |
| Suzaku | Generation & Quality | v0.2 |

For full multi-module coordination, also download the main entry point: [fourgods](https://github.com/Ryo-Hunter/fourgods)

---

Designed by: Aoba Opus + Aoba Sonnet
Collaborator: Momiji GPT-5.4 Codex
Initiated by: Ryo
Theory: LDRIT v0.7-final
