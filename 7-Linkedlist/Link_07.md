# 7. Insert at Given Position

## Problem

Given:

- Head of linked list
- A value
- A position `pos` (1-based index)

Do:

- Insert node at that position

---

# Core Idea

You don’t insert _at_ position directly.

You:

1. Go to **(pos - 1)th node**
2. Break link
3. Insert node in between

---

## Example

Insert 15 at position 2

Before:

```text
10 → 20 → 30 → NULL
```

After:

```text
10 → 15 → 20 → 30 → NULL
```

---

# Step-by-Step Logic

## Step 1: Validate Position

- `pos <= 0` → invalid
- handle separately

---

## Step 2: If position == 1

This is **insert at head**

```cpp
if (pos == 1) {
    newNode->next = head;
    return newNode;
}
```

---

## Step 3: Traverse to (pos - 1)

```cpp
Node* temp = head;

for (int i = 1; i < pos - 1 && temp != NULL; i++) {
    temp = temp->next;
}
```

---

## Step 4: Check if position valid

If:

```cpp
temp == NULL
```

Then position is out of bounds

---

## Step 5: Insert Node

```cpp
newNode->next = temp->next;
temp->next = newNode;
```

---

## Step 6: Return Head

---

# Algorithm Summary

1. validate pos
2. create node
3. if pos == 1 → insert at head
4. traverse to pos-1
5. if temp == NULL → invalid
6. link new node
7. return head

---

# Complete Code

```cpp
#include <bits/stdc++.h>
using namespace std;

class Node {
public:
    int data;
    Node* next;

    Node(int value) {
        data = value;
        next = NULL;
    }
};

void traverse(Node* head) {
    Node* temp = head;
    while (temp != NULL) {
        cout << temp->data << " ";
        temp = temp->next;
    }
    cout << endl;
}

Node* insertAtPosition(Node* head, int value, int pos) {
    // Step 1: Invalid position
    if (pos <= 0) {
        cout << "Invalid position\n";
        return head;
    }

    // Step 2: Create node
    Node* newNode = new Node(value);

    if (newNode == NULL) {
        cout << "Memory allocation failed\n";
        return head;
    }

    // Step 3: Insert at head
    if (pos == 1) {
        newNode->next = head;
        return newNode;
    }

    // Step 4: Traverse to (pos-1)
    Node* temp = head;

    for (int i = 1; i < pos - 1 && temp != NULL; i++) {
        temp = temp->next;
    }

    // Step 5: Position out of bounds
    if (temp == NULL) {
        cout << "Position out of bounds\n";
        delete newNode;
        return head;
    }

    // Step 6: Insert
    newNode->next = temp->next;
    temp->next = newNode;

    return head;
}

int main() {
    Node* head = NULL;

    head = insertAtPosition(head, 10, 1); // 10
    head = insertAtPosition(head, 20, 2); // 10 20
    head = insertAtPosition(head, 30, 3); // 10 20 30

    traverse(head);

    // Insert at position 2
    head = insertAtPosition(head, 15, 2);

    traverse(head);

    return 0;
}
```

---

# Dry Run

Initial:

```text
10 → 20 → 30
```

Insert 15 at pos = 2

### Step 1: Reach pos-1 (node 10)

### Step 2: Link

```text
newNode → 15
newNode->next = 20
10->next = 15
```

Final:

```text
10 → 15 → 20 → 30
```

---

# Output

```
10 20 30
10 15 20 30
```

---

# Edge Cases

## 1. pos <= 0

Invalid → reject

---

## 2. pos == 1

Handled as insert at head

---

## 3. pos > length + 1

Out of bounds → reject

---

## 4. Empty list

Only valid if:

```cpp
pos == 1
```

Otherwise invalid

---

## 5. Insertion at end

Works automatically:

- last node’s `next` becomes new node

---

# Critical Mistakes

### 1. Traversing to pos instead of pos-1

Breaks linking logic

---

### 2. Not checking NULL

Leads to segmentation fault

---

### 3. Wrong linking order

```cpp
temp->next = newNode;
newNode->next = temp->next; // WRONG
```

This creates self-loop

---

# Time Complexity

- O(n) due to traversal

---

# Real Insight

This is the first problem where:

- traversal + pointer manipulation both matter
- small mistake = full list corruption

---

# FOR NIKHIL

If you don’t clearly understand:

- why we go to `pos-1`
- why linking order matters

Then you’re just memorizing, not learning.
