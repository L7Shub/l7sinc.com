# L7S Skill Capture Protocol

## Rule: Every Completed Task = One Skill

When any todo is marked `done`, the completing agent MUST also create or update a skill entry.

## Required Skill Fields

| Field | Description |
|-------|-------------|
| `id` | Unique kebab-case ID derived from the task |
| `name` | What this skill is called |
| `category` | One of: branding, pwa, payments, scheduling, automation, crm, content, compliance, bookkeeping, infra |
| `problem_solved` | The specific problem this skill eliminates |
| `input_required` | Array of things needed to apply this skill |
| `output_produced` | Array of artifacts/results this skill creates |
| `steps` | Ordered array of concrete steps |
| `code_pattern` | Key snippet or command pattern (keep short) |
| `gotchas` | Array of edge cases/mistakes to avoid |
| `reuse_instructions` | How to apply from scratch in a new context |
| `tags` | Array of searchable keywords |

## How to Add a Skill

### Option A: Add to skills-library.json directly
Append the skill object to the `skills` array in `agent/skills-library.json`.
Increment `total_skills` counter.
Update `last_updated` date.

### Option B: Create a skill patch file
Create `agent/skills/[skill-id].json` with just that skill's object.
A merge script will consolidate into skills-library.json.

## SQL Tracking (Session DB)
When capturing a skill, also log it in the session database:
```sql
INSERT INTO skills (id, name, category, description, date_captured, status)
VALUES ('skill-id', 'Skill Name', 'category', 'Description', '2026-03-30', 'active');
```

## Skill Quality Bar
A skill is ready when someone unfamiliar with the original task can:
1. Read `problem_solved` and know if this skill applies to their situation
2. Follow `steps` and produce the same output
3. Avoid the `gotchas` without prior experience
4. Find it via at least 3 relevant `tags`

## Workflow Assembly
When a new task arrives, FIRST check skills-library.json:
```
Does any existing skill solve this or part of this?
→ YES: Apply the skill, mark as times_used + 1
→ NO: Complete the task, then capture it as a new skill
```

This is how workflows become instant.
