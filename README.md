Task Algorithm Deconstruction Project

## Overview

This project analyses three task management algorithms:

1. Task Priority Sorting
2. Task Text Parsing
3. Task List Merging (Two-way Sync)

These simulate real-world systems used in task management apps.

---

# 1. Task Priority Sorting

## What it does
Sorts tasks by importance using a weighted score.

## Score is based on:
- Priority level (LOW → URGENT)
- Due date proximity
- Completion status
- Tags (e.g. critical, blocker)
- Recent updates

## Key idea
Tasks are not just sorted — they are **scored based on urgency and context**.

---

# 2. Task Text Parser

## What it does
Converts free text into structured tasks.

Example:

Buy milk @shopping !2 #tomorrow


## Extracts:
- Title
- Priority (!1–!4 or named)
- Tags (@tag)
- Due dates (#today, #friday, #YYYY-MM-DD)

## Key idea
Uses pattern matching (regex) to turn unstructured text into structured data.

---

# 3. Task List Merging (Two-Way Sync)

## What it does
Syncs tasks between local and remote systems.

## Cases:
- Only local → send to remote
- Only remote → send to local
- Both exist → resolve conflict

---

## Conflict rules:

### 1. Latest update wins
Newer `updatedAt` overwrites most fields.

### 2. DONE status wins
Completed tasks override other states.

### 3. Tags are merged

tags = local ∪ remote


---

## Output
The algorithm returns:
- merged tasks
- tasks to create locally
- tasks to create remotely
- tasks to update on both sides

---

# Reflection

## What I learned
- Sorting uses scoring instead of simple ordering
- Parsing uses pattern matching to structure data
- Syncing behaves like a simplified version control system

## Challenges
- Understanding why some fields merge and others overwrite
- Understanding timestamp-based conflict resolution

## Improvement ideas
- Add deletion handling (tombstones)
- Use version numbers instead of timestamps
- Add field-level conflict detection

---

# Final Insight

These algorithms represent core backend patterns:
- Ranking system (prioritisation)
- Parser system (data extraction)
- Sync system (distributed consistency)
