# Skill 3: Load Past Context

Find and load relevant dialogue legacies from previous conversations.

## When to use
- User references past work
- You need historical context for the current topic

## Before searching

If `.seiryu/dialogues/` does not exist or has no legacy files:
- load nothing
- continue normally

Ignore:
- `_quarantine/`
- `compression_manifests/`

## How to search

### Step 1: Scan available legacies

List dialogue files in `.seiryu/dialogues/` by filename only.
If `archive_index.md` exists, include it in the candidate set.

### Step 2: Quick topic scan

For each candidate, read only the minimum needed:
- Level 1 files: first 5 lines
- Level 2 files (`L2_` prefix): first 8 lines
- `archive_index.md`: the table only

This gives topic + date + compressed context without loading full files.

### Step 3: Match and score

Compare the user request against the candidates:

| Signal | Points |
|--------|--------|
| Topic keyword matches user's words | +1 per match |
| Topic meaning is similar | +2 |
| Within last 7 days | +2 |
| Has unresolved items | +1 |
| Level 1 file | +1 |

This is **heuristic semantic matching**, not vector search. Use meaning, not just exact string overlap.

### Step 4: Load top results

- Read full content of the top 3 scoring legacies at most
- If a candidate is a Level 3 archive row, the row itself is the context
- If nothing scores above 0, load nothing

### Edge case: "Continue from last time"

- Load the most recent legacy regardless of topic score
- If multiple recent topics are plausible, ask the user to choose
