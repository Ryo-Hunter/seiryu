# Skill 2: Dialogue Legacy (c_dialogue)

Save the essential inheritance from a conversation so the next conversation can continue meaningfully.

## Location
`.seiryu/dialogues/`

## When to use
- Conversation is ending
- User explicitly asks to save progress
- Context is approaching limit, so a preemptive save is safer

## Context-limit auto-save rule

When context is getting long:
1. Tell the user you are saving progress now
2. Execute this skill
3. Continue the conversation

## Before saving

If `.seiryu/dialogues/` does not exist:
- create the directory
- if the whole `.seiryu/` root is missing, read `skills/s6-setup.md`

## How to generate a dialogue legacy

### Step 1: Filter with four questions

For each piece of information, ask:

1. Will the next conversation break without this?
2. Can this be re-derived from what remains?
3. Is this user-specific or generic?
4. Is this sensitive enough that it should NOT be auto-saved?

Keep:
- confirmed decisions
- unresolved items
- key definitions
- durable user preferences

Discard or omit:
- intermediate reasoning that can be re-derived
- routine chatter
- secrets, credentials, or sensitive identifiers unless the user explicitly asks to preserve them

### Step 2: Fill template

Use `templates/dialogue_legacy.md`

### Step 3: Save

- Filename: `YYYY-MM-DD_topic-keyword.md`
- Save to `.seiryu/dialogues/`

### Step 4: Optional git commit

If git is available and `.seiryu/` is already a repository:
`git add -A && git commit -m "seiryu: legacy - {topic keyword}"`

If not, saving the file alone is acceptable.

### Step 5: Check whether compression is needed

If `.seiryu/dialogues/` now has more than 20 Level 1 files, read `skills/s4-compress.md`
