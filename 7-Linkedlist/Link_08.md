Now we switch from inserting to **deleting**, which is more dangerous because you can easily lose memory or corrupt the list.

---

# 8. Delete from Head

## Problem

Given:

- Head of a linked list

Do:

- Remove the **first node**

---

# Core Idea

You are not “removing” the node magically.

You are:

1. Moving head forward
2. Deleting old node

---

## Before

```text id="7l5v70"
head → 10 → 20 → 30 → NULL
```

## After

```text id="r4h1y3"
head → 20 → 30 → NULL
```

---

# Step-by-Step Logic

## Step 1: Check if list is empty

```cpp id="n1w4j6"
if (head == NULL)
```

Nothing to delete

---

## Step 2: Store current head in temp

```cpp id="y9lql8"
Node* temp = head;
```

---

## Step 3: Move head to next node

```cpp id="t4mjdp"
head = head->next;
```

---

## Step 4: Delete old node

```cpp id="r53qvv"
delete temp;
```

---

## Step 5: Return updated head

---

# Algorithm Summary

1. if head == NULL → return
2. temp = head
3. head = head->next
4. delete temp
5. return head

---

# Complete Code

```cpp id="i6y3s4"
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

Node* deleteFromHead(Node* head) {
    // Step 1: Empty list
    if (head == NULL) {
        cout << "List is empty\n";
        return NULL;
    }

    // Step 2: Store head
    Node* temp = head;

    // Step 3: Move head
    head = head->next;

    // Step 4: Delete old node
    delete temp;

    // Step 5: Return updated head
    return head;
}

int main() {
    // Create list: 10 -> 20 -> 30
    Node* n1 = new Node(10);
    Node* n2 = new Node(20);
    Node* n3 = new Node(30);

    n1->next = n2;
    n2->next = n3;

    Node* head = n1;

    traverse(head);

    // Delete head
    head = deleteFromHead(head);

    traverse(head);

    return 0;
}
```

---

# Dry Run

Initial:

```text id="dprpvy"
head → 10 → 20 → 30
```

### Step 1

```text id="xk45xz"
temp → 10
```

### Step 2

```text id="z1b0zj"
head → 20
```

### Step 3

```text id="n6y8sp"
delete 10
```

Final:

```text id="h6o3kp"
head → 20 → 30
```

---

# Output

```text id="i3v3sl"
10 20 30
20 30
```

---

# Edge Cases

## 1. Empty List

```cpp id="0u2zav"
head = NULL
```

Handled:

- return NULL
- no crash

---

## 2. Single Node List

```text id="a1k6gq"
head → 10 → NULL
```

After deletion:

```text id="k5b6jo"
head → NULL
```

Important:

- list becomes empty

---

## 3. Multiple Deletions

Works repeatedly until list empty

---

# Critical Mistakes

### 1. Not using temp

```cpp id="nd7cmc"
head = head->next;
delete head;  // WRONG
```

You delete wrong node

---

### 2. Deleting before moving head

```cpp id="lt9dqa"
delete head;
head = head->next;  // accessing freed memory
```

Undefined behavior

---

### 3. Not handling empty list

Crash risk

---

# Time Complexity

- O(1)

---

# Real Insight

Delete from head is:

- simplest delete operation
- foundation for queue (dequeue)

---

# FOR NIKHIL

This pattern is important:

> store → move → delete

If you change order → memory corruption
