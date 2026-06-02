# Algorithm 3: Task List Merging (Two-Way Sync)

## What the algorithm does

This algorithm merges two task lists:
- Local tasks (device)
- Remote tasks (server)

It ensures both systems stay synchronized by:
- Detecting differences
- Resolving conflicts
- Generating update instructions

---

## Core Idea

The algorithm treats synchronization as:

> "Both sources are partially correct. We must merge them into a single consistent state."

---

## Step-by-step breakdown

### Step 1: Collect all task IDs
The algorithm builds a union of keys:

---

### Step 2: Classify each task

Each task falls into one of three cases:

#### Case 1: Local only
→ Send to remote (create)

#### Case 2: Remote only
→ Send to local (create)

#### Case 3: Exists in both
→ Resolve conflict

---

## Conflict Resolution Logic

### 1. Latest update wins
Most fields are decided using:

Newer version overrides:
- title
- description
- priority
- due date

---

### 2. Special rule: Completion status
If one task is DONE:
- DONE overrides all other statuses

Reason:
- Completion is treated as a “final state”

---

### 3. Tags are merged
Instead of choosing one side:

---

### 4. Sync decisions
The algorithm outputs:

- mergedTasks
- toCreateLocal
- toCreateRemote
- toUpdateLocal
- toUpdateRemote

This allows bidirectional syncing.


