# Skill 1: User Profile Management (c_user)

Maintain a persistent profile of the user across conversations.

## Location
`.seiryu/user/default.md`

## When to use
- You notice stable user information worth remembering
- You want to check what you already know about the user

## If the profile does not exist

- Read `skills/s6-setup.md`
- If setup would interrupt the current task too much, create the profile from `templates/user_profile.md` with only the minimum known fields

## What is worth saving

Save only user-specific information that improves future collaboration:
- preferred language
- communication style
- stable work/study domain
- durable preferences or constraints

Do NOT auto-save:
- passwords
- API keys
- government IDs
- private financial or medical details
- one-off emotional states unless the user explicitly asks to preserve them

## How to use

**Reading:** read `.seiryu/user/default.md`

**Updating:**
1. Add observations under `AI 自動觀察紀錄`
2. Do NOT interrupt the user just to fill profile fields
3. Prefer durable facts over temporary details
4. If git is available and `.seiryu/` is a repository, commit with:
   `git add -A && git commit -m "seiryu: user profile updated"`
5. If git is unavailable, save the file and continue
