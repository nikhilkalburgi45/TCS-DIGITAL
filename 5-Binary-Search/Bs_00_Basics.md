# What Binary Search Actually Is

Binary search is not “searching fast.”
It’s a **decision-based elimination strategy**.

You’re not checking every element—you’re **eliminating half of the search space every step**.

---

## Core Requirement (Non-negotiable)

If this is not true → **binary search is invalid**

- Array must be **sorted** (increasing or decreasing)
- OR the problem must have a **monotonic property**

---

# Core Intuition (Understand This or You’ll Fail)

You maintain a **search space**:

```
[low .......... high]
```

At every step:

- Pick middle → `mid`
- Decide:
  - Go left → eliminate right half
  - Go right → eliminate left half

---

# Why It Works (Real Reason)

Because the data has an **order (monotonicity)**:

```
F F F F T T T T   ← binary search works here
```

Once condition becomes true, it stays true (or vice versa)

---

# Standard Template (Burn this into memory)

```cpp
while (low <= high) {
    int mid = low + (high - low) / 2;

    if (condition) {
        high = mid - 1;
    } else {
        low = mid + 1;
    }
}
```

This is not code
This is a **pattern**

---

# 3 TYPES OF BINARY SEARCH (You MUST differentiate)

---

## 1. Search for exact element

Condition:

```cpp
if (arr[mid] == target)
```

---

## 2. Search for boundary (lower/upper bound)

Condition:

```cpp
if (arr[mid] >= target)   // move left
```

Used for:

- first occurrence
- lower bound
- insert position

---

## 3. Binary Search on Answer (MOST IMPORTANT)

You’re not searching array
You’re searching **answer space**

Example:

- minimum speed
- maximum capacity
- smallest valid value

Condition becomes:

```cpp
if (isValid(mid))   // monotonic function
```

---

# Visual Thinking (IMPORTANT)

Think like this:

```
low = 1, high = 100

mid = 50 → valid
→ maybe smaller exists → move left

mid = 25 → invalid
→ need bigger → move right
```

You are NOT searching values
You are searching **decision boundary**

---

# Most Important Tricks (This is what actually matters)

---

## Trick 1: Always define search space clearly

Bad:

> “I’ll start from 0 to n”

Good:

> “Answer lies between 1 to max(arr)”

---

## Trick 2: Identify monotonic function

Ask:

> If mid works, will all bigger/smaller also work?

If YES → binary search possible

---

## Trick 3: Store answer when moving left

```cpp
if (valid(mid)) {
    ans = mid;
    high = mid - 1;
}
```

If you forget this → wrong answer

---

## Trick 4: Avoid infinite loop

Wrong:

```cpp
while(low < high)
```

Use:

```cpp
while(low <= high)
```

---

## Trick 5: Overflow-safe mid

```cpp
mid = low + (high - low) / 2
```

---

## Trick 6: Know when to use `<` vs `<=`

- `<=` → exact search
- `<` → boundary problems (careful)

---

## Trick 7: Think in terms of "elimination"

Each step should remove half:

- If you’re not eliminating half → you’re doing it wrong

---

# Common Patterns You Must Recognize Instantly

---

## Pattern 1: Sorted array → direct binary search

Keywords:

- “find element”
- “index”
- “sorted”

---

## Pattern 2: First/Last occurrence

Keywords:

- “first”
- “last”
- “count duplicates”

---

## Pattern 3: Minimum/Maximum answer

Keywords:

- “minimum X such that…”
- “maximum Y such that…”

---

## Pattern 4: Feasibility problems

Keywords:

- “can we do this in X?”
- “is it possible?”

---

# Real Mistakes (Be honest—most people do this)

---

## Mistake 1: Treating it like linear search

If you're checking every element mentally → you're not doing BS

---

## Mistake 2: Not defining condition

If you can’t write:

```cpp
bool isValid(mid)
```

→ you don’t understand the problem

---

## Mistake 3: Wrong boundaries

People randomly write:

```cpp
low = 0, high = n-1
```

That only works for arrays
Not for answer-space problems

---

## Mistake 4: Panic on edge cases

Edge cases:

- single element
- all same elements
- target not present

---

# Mental Model (This will level you up)

Binary search is:

> “Find the **first point** where something changes”

---

# Quick Checklist Before Solving Any BS Problem

Ask yourself:

1. Is data sorted OR can I define monotonic condition?
2. What is my search space?
3. What does `mid` represent?
4. What is my condition?
5. When do I move left/right?
6. Am I storing answer correctly?

---
