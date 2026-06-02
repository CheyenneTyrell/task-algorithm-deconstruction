# Reflection Questions

## 1. How did the AI’s explanation change your understanding of the algorithm?

The AI explanation made the algorithm easier to understand by breaking it into steps:
- classification of tasks
- conflict resolution rules
- sync outputs

Before this, it looked like complex nested logic, but it is actually a structured decision system.

---

## 2. What aspects were still difficult to understand after AI explanation?

- Why certain fields (like tags) are merged instead of overwritten
- Why DONE status overrides timestamps
- How real-world systems handle edge cases like simultaneous edits or deletions

---

## 3. How would you explain this algorithm to another junior developer?

I would explain it like this:

> “We are syncing two copies of a task list. If a task exists only on one side, we copy it over. If it exists on both sides, we keep the newest changes and merge tags. Then we generate a list of updates so both sides become identical.”

---

## 4. Did you test this understanding against AI?

Yes. I tested understanding by asking what happens when:
- both sides update the same task differently
- timestamps conflict
- only some fields change

The model confirmed how each rule applies.

---

## 5. How might you improve the algorithm?

- Add deletion handling (tombstones)
- Use version numbers instead of only timestamps
- Allow configurable conflict rules
- Track change history instead of overwriting fields
- Detect field-level conflicts instead of full-task conflicts

---

## Final insight

This algorithm is essentially a simplified distributed synchronization system, similar to how version control systems merge changes.
