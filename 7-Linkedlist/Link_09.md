# 9. Delete from Tail

## Problem

Given:

- Head of linked list

Do:

- Delete the **last node**

# Core Idea

You cannot directly jump to the last node.

You must:

1. Reach the **second last node**
2. Break its link
3. Delete last node

## Before

```text id="ymndjf"
head → 10 → 20 → 30 → NULL
```

## After

```text id="6osrnr"
head → 10 → 20 → NULL
```

# Step-by-Step Logic

## Step 1: Handle Empty List

```cpp id="s9c3fn"
if (head == NULL)
```

Nothing to delete

## Step 2: Handle Single Node

```cpp id="h3ybtq"
if (head->next == NULL)
```

Why?

- Only one node
- After deletion → list becomes empty

## Step 3: Traverse to Second Last Node

Condition:

```cpp id="7w1mhj"
while (temp->next->next != NULL)
```

Why?

- You want to stop at second last node

## Step 4: Store Last Node

```cpp id="g3fznw"
Node* last = temp->next;
```

## Step 5: Break Link

```cpp id="n2j3qf"
temp->next = NULL;
```

## Step 6: Delete Last Node

```cpp id="9d0s3g"
delete last;
```

## Step 7: Return Head

# Algorithm Summary

1. if head == NULL → return
2. if single node → delete & return NULL
3. traverse to second last
4. store last
5. break link
6. delete last
7. return head

# Complete Code

```cpp id="91y82m"
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

Node* deleteFromTail(Node* head) {
    // Step 1: Empty list
    if (head == NULL) {
        cout << "List is empty\n";
        return NULL;
    }

    // Step 2: Single node
    if (head->next == NULL) {
        delete head;
        return NULL;
    }

    // Step 3: Traverse to second last
    Node* temp = head;
    while (temp->next->next != NULL) {
        temp = temp->next;
    }

    // Step 4: Store last node
    Node* last = temp->next;

    // Step 5: Break link
    temp->next = NULL;

    // Step 6: Delete last
    delete last;

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

    // Delete tail
    head = deleteFromTail(head);

    traverse(head);

    return 0;
}
```

# Dry Run

Initial:

```text id="qhwcsf"
10 → 20 → 30 → NULL
```

### Step 1: Traverse

Stop at:

```text id="03gk0n"
temp → 20
```

### Step 2:

```text id="mav0x6"
last → 30
```

### Step 3:

```text id="t67xsb"
20 → NULL
```

### Step 4:

```text id="4s2whj"
delete 30
```

Final:

```text id="tb3gdb"
10 → 20 → NULL
```

# Output

```text id="i3c0ya"
10 20 30
10 20
```

# Edge Cases

## 1. Empty List

Handled safely

## 2. Single Node

```text id="i6q4gx"
10 → NULL
```

After delete:

```text id="2wstwh"
NULL
```

## 3. Two Nodes

```text id="0d1v2m"
10 → 20
```

Loop doesn’t run
temp stays at 10
Deletes 20 correctly

# Critical Mistakes

### 1. Wrong loop

```cpp id="q6lj9p"
while(temp->next != NULL)
```

You reach last node → then `temp->next` is NULL → crash

### 2. Not handling single node

Segmentation fault on:

```cpp id="8mvffr"
temp->next->next
```

### 3. Deleting before breaking link

Can cause dangling pointer

# Time Complexity

- O(n)

# Real Insight

Delete from tail is expensive because:

- no backward pointer

Better structure:

- Doubly Linked List → O(1)
