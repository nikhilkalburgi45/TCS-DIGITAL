# 12. Find Length of Linked List

## Problem

Given:

- Head of linked list

Do:

- Return total number of nodes

# Core Idea

You are just counting nodes while traversing.

```text
head → node → node → node → NULL
          ↑ count++
```

# Step-by-Step Logic

## Step 1: Handle Empty List

```cpp
if (head == NULL)
    return 0;
```

## Step 2: Initialize

```cpp
Node* temp = head;
int count = 0;
```

## Step 3: Traverse

```cpp
while (temp != NULL)
```

## Step 4: Count + Move

```cpp
count++;
temp = temp->next;
```

## Step 5: Return Count

# Algorithm Summary

1. if head NULL → return 0
2. temp = head, count = 0
3. loop till NULL
4. increment count
5. move forward
6. return count

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

int findLength(Node* head) {
    // Step 1: Empty list
    if (head == NULL) {
        return 0;
    }

    // Step 2: Initialize
    Node* temp = head;
    int count = 0;

    // Step 3: Traverse
    while (temp != NULL) {
        // Step 4: Count + Move
        count++;
        temp = temp->next;
    }

    // Step 5: Return
    return count;
}

int main() {
    // Create list: 10 → 20 → 30
    Node* n1 = new Node(10);
    Node* n2 = new Node(20);
    Node* n3 = new Node(30);

    n1->next = n2;
    n2->next = n3;

    Node* head = n1;

    traverse(head);

    int len = findLength(head);
    cout << "Length: " << len << endl;

    return 0;
}
```

# Dry Run

List:

```text
10 → 20 → 30 → NULL
```

| Step | temp | count |
| ---- | ---- | ----- |
| 1    | 10   | 1     |
| 2    | 20   | 2     |
| 3    | 30   | 3     |
| 4    | NULL | stop  |

# Output

```text
10 20 30
Length: 3
```

# Edge Cases

## 1. Empty List

```cpp
head = NULL → length = 0
```

## 2. Single Node

```text
10 → NULL → length = 1
```

## 3. Large List

Works normally, but O(n)

## 4. Cyclic List (Important)

If there is a cycle:

```text
10 → 20 → 30 → 20 ...
```

Your loop:

```cpp
while(temp != NULL)
```

Will NEVER stop → infinite loop

This function assumes **no cycle**

# Critical Mistakes

### 1. Wrong loop condition

```cpp
while(temp->next != NULL)
```

Misses last node → wrong length

### 2. Forgetting `temp = temp->next`

Infinite loop

### 3. Not handling cycle case (advanced)

Not needed now, but important later

# Time Complexity

- O(n)

# Real Insight

Length is often used for:

- finding middle
- validating positions
- removing nth from end

But:

> Calling length repeatedly inside loops = bad design (O(n²))
