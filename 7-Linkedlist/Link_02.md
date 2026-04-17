# 2. Create Single Node and Print

## Problem

You have:

- One node (`head`)
- You need to print it using a **function (traversal)**

# Core Idea

Printing a linked list is not special.

It is just:

> Start from head → keep moving to next → stop at NULL

# Step-by-Step Logic

## Step 1: Create Node (same as before)

```cpp
Node* head = new Node(10);
```

Memory:

```
head → [10 | NULL]
```

## Step 2: Create Traversal Function

Function goal:

- Take `head`
- Print until NULL

## Step 3: Traversal Algorithm

1. Create a temporary pointer
2. Point it to head
3. Loop until NULL
4. Print data
5. Move forward

## Step 4: Breakdown (Important)

```
Node* temp = head;
```

You NEVER move head directly (common beginner mistake)

### Loop

```
while(temp != NULL)
```

Inside loop:

1. Print current node
2. Move to next

```
temp = temp->next;
```

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

// Traversal function
void printList(Node* head) {
    Node* temp = head;   // Step 1: create temp

    while (temp != NULL) {   // Step 2: loop till NULL
        cout << temp->data << " ";
        temp = temp->next;   // Step 3: move forward
    }
    cout << endl;
}

int main() {
    // Create single node
    Node* head = new Node(10);

    // Print using traversal
    printList(head);

    return 0;
}
```

# Dry Run

Initial:

```
head → [10 | NULL]
```

Execution:

| Step  | temp | Output |
| ----- | ---- | ------ |
| Start | 10   | -      |
| Print | 10   | 10     |
| Move  | NULL | -      |
| Stop  | -    | done   |

# Output

```
10
```

# Critical Mistakes (You must avoid)

1. Moving head instead of temp

```
head = head->next;  // destroys list
```

2. Forgetting NULL condition → infinite loop

3. Writing:

```
while(temp->next != NULL)
```

This skips last node

Correct:

```
while(temp != NULL)
```

# Real Insight

Traversal is the backbone of:

- insert
- delete
- reverse
- search

If traversal is weak, everything ahead collapses.
