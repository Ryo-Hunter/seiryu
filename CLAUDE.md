# Seiryu - Memory & Inheritance Skills

Seiryu is a skill module. It does not control your AI.
Use this file as the entry point.

## Entry rules

1. If the user mentions Seiryu or a `seiryu-v1.2/` path, read this file first.
2. If `.seiryu/` or `.seiryu/user/default.md` does not exist and memory is needed, read `skills/s6-setup.md`.
3. Read only the one skill you need right now.
4. Git commits are recommended when available, but memory actions must not fail just because git is unavailable.

## Skills

| Skill | File | When to use |
|-------|------|-------------|
| User Profile | skills/s1-profile.md | New stable user info observed |
| Dialogue Legacy | skills/s2-legacy.md | Conversation ending or context nearly full |
| Load Past Context | skills/s3-load.md | User references past work |
| Compression | skills/s4-compress.md | Too many legacy files accumulated |
| Agent Checkpoint | skills/s5-checkpoint.md | Multi-step task (3+ steps) |
| First Setup | skills/s6-setup.md | `.seiryu/` or user profile missing |

## Data location

All user data: `.seiryu/`
Templates: `templates/`

## Rule

Do NOT read all skill files at once.
Read only the one you need, when you need it.
