# Skill 5: Agent Checkpoints

Save and restore points for multi-step tasks.

Based on LDRIT's shorter-chain stability idea:
large tasks are easier to continue when each major step leaves a compact, restorable state.

## Location
`.seiryu/checkpoints/`

## When to use
- Starting a multi-step task (3+ steps)
- Completing a major step
- Something goes wrong and rollback is needed

## Before using

If `.seiryu/checkpoints/` does not exist:
- create it
- if the whole `.seiryu/` root is missing, read `skills/s6-setup.md`

## What counts as a major step

- A meaningful intermediate result exists
- The next step depends on the current result
- Failure after this point should not require redoing the whole chain

## Checkpoint lifecycle

### 1. Plan

- Create file: `task_{NNN}_{keyword}.json`
- Template: `templates/agent_checkpoint.json`
- Fill in: task_id, task_description, total_steps_estimate, next_plan
- If git is available, commit the checkpoint

### 2. Progress

- Update step number, completed items, current_result, next_plan
- Keep `context_summary` short and essential
- Do not create noise by updating for trivial sub-steps

### 3. Error

- Set status to `error`
- Record failure details in `current_result`
- Fill `rollback_info`
- Ask the user before rolling back

### 4. Completion

- Set status to `completed`
- Keep the checkpoint as a record
- If git is available, commit the completed state

## Cleanup

- Completed checkpoints: keep at least 30 days, then archive or delete if no longer useful
- Error checkpoints: keep until resolved or explicitly cleared
- Stale in-progress checkpoints: ask the user whether to resume or abandon
