# 3. Create 2–3 Nodes Manually and Link

## Problem

You need to:

- Create multiple nodes
- Connect them using pointers
- Form an actual linked list

# Core Idea

A linked list is nothing but:

```text
[10 | * ] → [20 | * ] → [30 | NULL]
```

Each node’s `next` points to the next node.

# Step-by-Step Logic

## Step 1: Create Nodes Separately

```cpp
Node* n1 = new Node(10);
Node* n2 = new Node(20);
Node* n3 = new Node(30);
```

Right now memory looks like this (not connected):

```text
n1 → [10 | NULL]

n2 → [20 | NULL]

n3 → [30 | NULL]
```

They are **independent nodes**.

## Step 2: Link Nodes

Now connect them:

1. n1 should point to n2
2. n2 should point to n3

```cpp
n1->next = n2;
n2->next = n3;
```

Now structure becomes:

```text
n1 → [10 | * ] → [20 | * ] → [30 | NULL]
```

## Step 3: Define Head

Head always points to first node:

```cpp
Node* head = n1;
```

## Step 4: Traverse and Print

Use same traversal logic from previous step.

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

void printList(Node* head) {
    Node* temp = head;

    while (temp != NULL) {
        cout << temp->data << " ";
        temp = temp->next;
    }
    cout << endl;
}

int main() {
    // Step 1: Create nodes
    Node* n1 = new Node(10);
    Node* n2 = new Node(20);
    Node* n3 = new Node(30);

    // Step 2: Link nodes
    n1->next = n2;
    n2->next = n3;

    // Step 3: Set head
    Node* head = n1;

    // Step 4: Print list
    printList(head);

    return 0;
}
```

# Dry Run

Initial:

```text
n1 → [10 | * ]
n2 → [20 | * ]
n3 → [30 | NULL]
```

After linking:

```text
head → [10 | * ] → [20 | * ] → [30 | NULL]
```

Traversal:

| Step | temp | Output   |
| ---- | ---- | -------- |
| 1    | 10   | 10       |
| 2    | 20   | 10 20    |
| 3    | 30   | 10 20 30 |
| 4    | NULL | stop     |

---

# Output

```text
10 20 30
```

# Critical Mistakes (Don’t Ignore)

1. Forgetting to link nodes
   → You’ll print only one node

2. Wrong linking order

```cpp
n2->next = n1; // creates wrong direction
```

3. Not assigning head
   → You lose entry point

# Real Insight

This is the **first time you actually build a linked list**.

Everything later (insert, delete, reverse) is just:

> breaking and rejoining these links
