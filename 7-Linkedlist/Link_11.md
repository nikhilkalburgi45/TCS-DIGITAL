# 11. Search in Linked List

## Problem

Given:

- Head of linked list
- A key (value)

Do:

- Check if key exists
- Optionally return position

# Core Idea

You just:

1. Start from head
2. Compare each node
3. Move forward
4. Stop when found OR NULL

## Example

Search 20

```text
10 → 20 → 30 → NULL
```

Result:

- Found at position 2

# Step-by-Step Logic

## Step 1: Handle Empty List

```cpp
if (head == NULL)
```

Nothing to search

## Step 2: Initialize Traversal

```cpp
Node* temp = head;
int position = 1;
```

## Step 3: Traverse

```cpp
while (temp != NULL)
```

## Step 4: Compare

```cpp
if (temp->data == key)
```

If match → return position

## Step 5: Move Forward

```cpp
temp = temp->next;
position++;
```

## Step 6: Not Found

Return -1

# Algorithm Summary

1. if head NULL → return -1
2. temp = head, pos = 1
3. loop till NULL
4. if match → return pos
5. move forward
6. return -1

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

int search(Node* head, int key) {
    // Step 1: Empty list
    if (head == NULL) {
        return -1;
    }

    // Step 2: Initialize
    Node* temp = head;
    int position = 1;

    // Step 3: Traverse
    while (temp != NULL) {
        // Step 4: Compare
        if (temp->data == key) {
            return position;
        }

        // Step 5: Move forward
        temp = temp->next;
        position++;
    }

    // Step 6: Not found
    return -1;
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

    int key = 20;
    int result = search(head, key);

    if (result != -1)
        cout << "Found at position: " << result << endl;
    else
        cout << "Not found" << endl;

    return 0;
}
```

# Dry Run

List:

```text
10 → 20 → 30
```

Search key = 20

| Step | temp | position | match |
| ---- | ---- | -------- | ----- |
| 1    | 10   | 1        | no    |
| 2    | 20   | 2        | yes   |

Return 2

# Output

```
10 20 30
Found at position: 2
```

# Edge Cases

## 1. Empty List

Returns -1

## 2. Key at Head

Immediate return

## 3. Key at Tail

Full traversal required

## 4. Key Not Present

Return -1

## 5. Duplicate Values

Returns **first occurrence only**

# Critical Mistakes

### 1. Forgetting position increment

You’ll always return 1

### 2. Using `while(temp->next != NULL)`

Misses last node

### 3. Not handling empty list

Leads to confusion in debugging

# Time Complexity

- O(n)

# Real Insight

Search in linked list is inefficient compared to array:

- no indexing
- sequential access only
