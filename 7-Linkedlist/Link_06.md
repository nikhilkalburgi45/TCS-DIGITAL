# 6. Insert at Tail

## Problem

Given:

- A linked list (may be empty)
- A value

Do:

- Insert node at the **end of the list**

---

# Core Idea

Unlike head insertion, here you **must reach the last node first**.

```text
head → 10 → 20 → 30 → NULL
                       ↑
                     insert here
```

---

# Step-by-Step Logic

## Step 1: Create New Node

```cpp
Node* newNode = new Node(value);
```

---

## Step 2: Handle Memory Failure

```cpp
if (newNode == NULL) {
    cout << "Memory allocation failed\n";
    return head;
}
```

---

## Step 3: Edge Case — Empty List

If list is empty:

```cpp
if (head == NULL) {
    return newNode;
}
```

Why?

- No traversal possible
- New node becomes head

---

## Step 4: Traverse to Last Node

```cpp
Node* temp = head;

while (temp->next != NULL) {
    temp = temp->next;
}
```

Stop at:

```text
lastNode → [data | NULL]
```

---

## Step 5: Link Last Node to New Node

```cpp
temp->next = newNode;
```

---

## Step 6: Return Head

Head doesn’t change

```cpp
return head;
```

---

# Algorithm Summary

1. create node
2. check allocation
3. if head == NULL → return newNode
4. traverse till last node
5. last->next = newNode
6. return head

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

Node* insertAtTail(Node* head, int value) {
    // Step 1: Create node
    Node* newNode = new Node(value);

    // Step 2: Memory check
    if (newNode == NULL) {
        cout << "Memory allocation failed\n";
        return head;
    }

    // Step 3: Empty list
    if (head == NULL) {
        return newNode;
    }

    // Step 4: Traverse to last node
    Node* temp = head;
    while (temp->next != NULL) {
        temp = temp->next;
    }

    // Step 5: Link
    temp->next = newNode;

    // Step 6: Return head
    return head;
}

int main() {
    Node* head = NULL;

    head = insertAtTail(head, 10);
    head = insertAtTail(head, 20);
    head = insertAtTail(head, 30);

    traverse(head);

    return 0;
}
```

---

# Dry Run

### Initial

```text
head → NULL
```

Insert 10:

```text
head → 10 → NULL
```

---

Insert 20:

Traversal:

- temp at 10
- temp->next = NULL → stop

```text
10 → 20 → NULL
```

---

Insert 30:

```text
10 → 20 → 30 → NULL
```

---

# Output

```
10 20 30
```

---

# Edge Cases

## 1. Empty List

Handled:

```cpp
if (head == NULL) return newNode;
```

---

## 2. Single Node List

```text
head → 10 → NULL
```

After insert:

```text
10 → 20 → NULL
```

---

## 3. Large List

Traversal cost increases → O(n)

---

## 4. Memory Failure

Handled safely

---

# Critical Mistakes

### 1. Wrong loop

```cpp
while(temp != NULL)
```

You’ll end at NULL → crash when doing `temp->next`

---

### 2. Forgetting empty case

Leads to segmentation fault

---

### 3. Losing head

If you do:

```cpp
head = head->next;
```

You destroy entry point

---

# Time Complexity

- Insert at head → O(1)
- Insert at tail → O(n)

Unless you maintain a **tail pointer**

---

# Real Insight

This operation exposes:

- traversal cost
- inefficiency of naive linked list

This is why in real systems:

- we maintain `tail` pointer

---

# FOR NIKHIL

If you don’t question this:

> “Why is insert at tail O(n)?”

You’re missing system-level thinking.

Better design:

- maintain `tail`
- get O(1)
