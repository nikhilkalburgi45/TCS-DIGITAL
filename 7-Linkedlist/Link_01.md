# 1. Create a Node (Class + Constructor)

## Problem Understanding

You are not building a list yet.

You are building the **basic building block**:

> A single node that can store:

- data
- pointer to next node

## Mental Model (Very Important)

Think of a node like:

```
[data | next]
```

Example:

```
[20 | NULL]
```

## Step-by-Step Construction

### Step 1: Define Structure

You need:

- `data` → to store value
- `next` → pointer to next node

---

### Step 2: Create Class

```cpp
class Node {
public:
    int data;
    Node* next;
};
```

### Step 3: Add Constructor

Why constructor?
To initialize node at creation time

### Step 4: Constructor Logic

When node is created:

1. Assign value to `data`
2. Set `next = NULL`

## Final Code

```cpp
#include <bits/stdc++.h>
using namespace std;

class Node {
public:
    int data;
    Node* next;

    // Constructor
    Node(int value) {
        data = value;
        next = NULL;
    }
};

int main() {
    // Step 1: Create a node
    Node* head = new Node(10);

    // Step 2: Print the node data
    cout << "Data: " << head->data << endl;

    // Step 3: Check next pointer
    if (head->next == NULL) {
        cout << "Next is NULL" << endl;
    }

    return 0;
}
```

## Dry Run

```
Node* n1 = new Node(10);
```

Memory:

```
n1 → [10 | NULL]
```

---
