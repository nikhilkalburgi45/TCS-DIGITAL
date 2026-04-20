# 5. Insert at Head (with Edge Cases)

## Problem

Given:

- A linked list (may be empty)
- A value

Do:

- Insert node at the **beginning**

---

# Core Idea

You are shifting the entry point.

```text
newNode → old head → rest
```

---

# Step-by-Step Logic

## Step 1: Create New Node

```cpp
Node* newNode = new Node(value);
```

---

## Step 2: Handle Memory Failure (rare but correct)

```cpp
if (newNode == NULL) {
    cout << "Memory allocation failed\n";
    return head;
}
```

---

## Step 3: Point New Node to Current Head

```cpp
newNode->next = head;
```

---

## Step 4: Move Head to New Node

```cpp
head = newNode;
```

---

## Step 5: Return Updated Head

```cpp
return head;
```

---

# Algorithm Summary

1. create node
2. check allocation
3. link to head
4. move head
5. return head

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

Node* insertAtHead(Node* head, int value) {
    // Step 1: Create node
    Node* newNode = new Node(value);

    // Step 2: Memory check
    if (newNode == NULL) {
        cout << "Memory allocation failed\n";
        return head;
    }

    // Step 3: Link
    newNode->next = head;

    // Step 4: Move head
    head = newNode;

    // Step 5: Return
    return head;
}

int main() {
    Node* head = NULL;  // Empty list case

    // Insert elements
    head = insertAtHead(head, 30);
    head = insertAtHead(head, 20);
    head = insertAtHead(head, 10);

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

### Insert 30

```text
newNode → [30 | NULL]
head → 30
```

---

### Insert 20

```text
newNode → [20 | * ] → 30
head → 20 → 30
```

---

### Insert 10

```text
newNode → [10 | * ] → 20
head → 10 → 20 → 30
```

---

# Output

```
10 20 30
```

---

# Edge Cases (Explicit)

## 1. Empty List

```cpp
head = NULL;
```

Handled automatically:

```cpp
newNode->next = NULL;
head = newNode;
```

---

## 2. Single Node List

```text
head → 10
```

After insert 5:

```text
head → 5 → 10
```

No issue.

---

## 3. Memory Allocation Failure

Handled:

```cpp
if (newNode == NULL)
```

---

## 4. Large Number of Insertions

Still O(1) each — no degradation.

---

# Critical Mistakes

### Wrong Order

```cpp
head = newNode;
newNode->next = head;
```

Creates self-loop:

```
5 → 5 → 5 → ...
```

---

### Not Returning Head

Caller still points to old head → bug

---

### Modifying Head Before Linking

Lose entire list

---

# Real Insight

Insert at head is:

- simplest operation
- safest operation
- foundation for stack implementation

---
