# Skill 6: First Setup

Initialize Seiryu for a new user or a new workspace.

## When to use
- No `.seiryu/` root exists
- No user profile exists in `.seiryu/user/`
- User explicitly asks to set up Seiryu

## Steps

### Step 1: Display startup message
```text
   青龍

東方已鎮
```

### Step 2: Show status
```text
+============================+
|  四神系統                    |
|  [青龍 OK] [朱雀  -]        |
|  [玄武  -] [白虎  -]        |
|                            |
|  東方已鎮                    |
+============================+
```

If other modules are already installed, show their status as OK instead of `-`.

### Step 3: Ask three questions in the user's language
1. What should I call you?
2. What is your main field of work or study?
3. What will you primarily use AI for?

### Step 4: Create the directory structure

Create:
- `.seiryu/user/`
- `.seiryu/dialogues/`
- `.seiryu/dialogues/_quarantine/`
- `.seiryu/dialogues/compression_manifests/`
- `.seiryu/checkpoints/`

### Step 5: Create starter files

- Create `.seiryu/user/default.md` from `templates/user_profile.md`
- Create `.seiryu/dialogues/archive_index.md` from `templates/archive_index.md`

### Step 6: Optional git initialization

If git is available and the user wants version tracking:
`git init && git add -A && git commit -m "seiryu: 東方已鎮"`

If git is unavailable, skip this step and continue.

### Step 7: Completion message

After setup, confirm:
`你的記憶已被守護。`

If the user's environment includes other Four Gods modules, you may mention them.
If Seiryu is installed standalone, do not imply that other modules are required.
