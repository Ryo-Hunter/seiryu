# Skill 4: Compression

Prevent dialogue legacies from piling up endlessly while reducing the chance of irreversible loss.

Based on LDRIT inheritance distance decay:
older context usually contributes less, but compression must remain reversible for a while.

## When to use
- `.seiryu/dialogues/` has more than 20 Level 1 files
- `.seiryu/dialogues/` has more than 20 Level 2 files

## Safety rules

1. Do NOT compress files from the last 7 days unless the user explicitly asks
2. Before replacing older files, create a manifest record
3. Move originals to `_quarantine/` first
4. Do not permanently delete quarantined files immediately

## Locations

- Active legacies: `.seiryu/dialogues/`
- Quarantine: `.seiryu/dialogues/_quarantine/`
- Manifests: `.seiryu/dialogues/compression_manifests/`

## Three compression levels

### Level 1: Full Dialogue Legacy
- Template: `templates/dialogue_legacy.md`
- Size: 30-80 lines
- Filename: `YYYY-MM-DD_topic-keyword.md`

### Level 2: Compressed Summary
- Filename: `L2_YYYY-MM-DD_topic.md`
- Keep only decisions, unresolved items, and key dependency facts

### Level 3: Archive Index Entry
- One row in `dialogues/archive_index.md`
- Use `templates/archive_index.md` if the file does not exist yet

## Compression process

### Level 1 -> Level 2

When Level 1 count is greater than 20:
1. Select the oldest eligible 10 Level 1 files
2. Create one manifest file from `templates/compression_manifest.md`
3. For each file, extract only decisions, unresolved items, and key facts
4. Save the compressed result as `L2_...`
5. Move the original file into `_quarantine/`
6. If git is available, commit the change

### Level 2 -> Level 3

When Level 2 count is greater than 20:
1. Select the oldest eligible 10 Level 2 files
2. Ensure `archive_index.md` exists
3. Create one manifest file from `templates/compression_manifest.md`
4. Append one row per file to `archive_index.md`
5. Move the original Level 2 files into `_quarantine/`
6. If git is available, commit the change

## Cleanup

- Keep quarantined originals for at least 14 days
- Delete them only after the compressed replacements are verified useful
- If the user prefers maximum retention, keep quarantine indefinitely
