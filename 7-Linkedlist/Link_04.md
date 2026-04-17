# 4. Traverse Linked List

## Problem

Given:

- A linked list of any size

Do:

- Print all elements correctly

# Core Idea

Traversal = controlled pointer movement

```text
head → node → node → node → NULL
```

You must:

- start at head
- move step-by-step
- stop exactly at NULL

# Step-by-Step Logic

## Step 1: Function Definition

```cpp
void traverse(Node* head)
```

## Step 2: Handle Edge Case (Important)

If list is empty:

```cpp
if (head == NULL)
```

Why?

- Avoid unnecessary loop
- Avoid confusion

## Step 3: Create Temporary Pointer

```cpp
Node* temp = head;
```

Never touch head directly.

## Step 4: Loop

```cpp
while (temp != NULL)
```

## Step 5: Inside Loop

1. Print data
2. Move forward

```cpp
cout << temp->data << " ";
temp = temp->next;
```

---

## Step 6: End Cleanly

Print newline

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
    // Step 1: Edge case
    if (head == NULL) {
        cout << "List is empty" << endl;
        return;
    }

    // Step 2: Temp pointer
    Node* temp = head;

    // Step 3: Traverse
    while (temp != NULL) {
        cout << temp->data << " ";
        temp = temp->next;
    }

    cout << endl;
}

int main() {
    // Create list: 10 -> 20 -> 30
    Node* n1 = new Node(10);
    Node* n2 = new Node(20);
    Node* n3 = new Node(30);

    n1->next = n2;
    n2->next = n3;

    Node* head = n1;

    // Traverse
    traverse(head);

    return 0;
}
```

# Dry Run

List:

```text
head → 10 → 20 → 30 → NULL
```

Execution:

| Step | temp | Output   |
| ---- | ---- | -------- |
| 1    | 10   | 10       |
| 2    | 20   | 10 20    |
| 3    | 30   | 10 20 30 |
| 4    | NULL | stop     |

# Output

```text
10 20 30
```

# Critical Mistakes (This is where people fail)

### 1. Wrong loop condition

```cpp
while(temp->next != NULL)
```

Problem:

- last node never printed

### 2. Moving head instead of temp

```cpp
head = head->next;
```

You just destroyed the list.

### 3. Not handling empty list

Leads to:

- silent failure
- bad debugging

### 4. Infinite loop

If you forget:

```cpp
temp = temp->next;
```

# Real Insight

Traversal is used in:

- insert at position
- delete
- search
- reverse
- cycle detection

If this is not muscle memory, you will struggle later.
