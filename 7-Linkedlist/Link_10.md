# 10. Delete at Given Position

## Problem

Given:

- Head of linked list
- Position `pos` (1-based)

Do:

- Delete node at that position


# Core Idea

You never delete directly.

You:

1. Reach **(pos - 1)th node**
2. Store node to delete
3. Re-link
4. Delete


## Example

Delete at position 2

Before:

```text id="n98e4z"
10 → 20 → 30 → NULL
```

After:

```text id="u0i0ux"
10 → 30 → NULL
```


# Step-by-Step Logic

## Step 1: Validate Position

```cpp id="5r5nrz"
if (pos <= 0)
```

Invalid


## Step 2: Handle Empty List

```cpp id="9rwz6v"
if (head == NULL)
```

Nothing to delete


## Step 3: If pos == 1 (Delete Head)

Use previous logic:

```cpp id="4y5r5d"
Node* temp = head;
head = head->next;
delete temp;
return head;
```


## Step 4: Traverse to (pos - 1)

```cpp id="4dts9u"
Node* temp = head;

for (int i = 1; i < pos - 1 && temp != NULL; i++) {
    temp = temp->next;
}
```


## Step 5: Check Validity

Two checks:

```cpp id="c8qj4q"
if (temp == NULL || temp->next == NULL)
```

Why?

- temp NULL → position too large
- temp->next NULL → no node to delete


## Step 6: Store Node to Delete

```cpp id="3r7c2g"
Node* nodeToDelete = temp->next;
```


## Step 7: Break Link

```cpp id="j4z2s1"
temp->next = nodeToDelete->next;
```


## Step 8: Delete Node

```cpp id="8lh6k3"
delete nodeToDelete;
```


## Step 9: Return Head


# Algorithm Summary

1. validate pos
2. if empty → return
3. if pos == 1 → delete head
4. traverse to pos-1
5. check validity
6. store node
7. relink
8. delete node
9. return head


# Complete Code

```cpp id="3svj88"
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

Node* deleteAtPosition(Node* head, int pos) {
    // Step 1: Invalid position
    if (pos <= 0) {
        cout << "Invalid position\n";
        return head;
    }

    // Step 2: Empty list
    if (head == NULL) {
        cout << "List is empty\n";
        return NULL;
    }

    // Step 3: Delete head
    if (pos == 1) {
        Node* temp = head;
        head = head->next;
        delete temp;
        return head;
    }

    // Step 4: Traverse to pos-1
    Node* temp = head;

    for (int i = 1; i < pos - 1 && temp != NULL; i++) {
        temp = temp->next;
    }

    // Step 5: Check bounds
    if (temp == NULL || temp->next == NULL) {
        cout << "Position out of bounds\n";
        return head;
    }

    // Step 6: Store node
    Node* nodeToDelete = temp->next;

    // Step 7: Relink
    temp->next = nodeToDelete->next;

    // Step 8: Delete
    delete nodeToDelete;

    return head;
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

    // Delete position 2
    head = deleteAtPosition(head, 2);

    traverse(head);

    return 0;
}
```


# Dry Run

Initial:

```text id="ux57ec"
10 → 20 → 30
```

Delete pos = 2

### Step 1: Reach pos-1

```text id="kvqk6y"
temp → 10
```


### Step 2:

```text id="g6bq9n"
nodeToDelete → 20
```


### Step 3:

```text id="5qz5av"
10 → 30
```


### Step 4:

```text id="4gff6g"
delete 20
```

Final:

```text id="6l0bl8"
10 → 30
```


# Output

```text id="kcr5c9"
10 20 30
10 30
```


# Edge Cases

## 1. pos <= 0

Invalid


## 2. Empty List

Handled


## 3. pos == 1

Delete head


## 4. pos > length

Handled via:

```cpp id="a1d6fg"
temp == NULL || temp->next == NULL
```


## 5. Single Node List

If pos == 1 → becomes empty
Else → invalid


# Critical Mistakes

### 1. Not handling pos == 1 separately

Breaks logic


### 2. Traversing incorrectly

You must stop at pos-1


### 3. Deleting before relinking

Leads to lost connection


### 4. Not checking temp->next

Segmentation fault


# Time Complexity

- O(n)


# Real Insight

This problem combines:

- insert logic
- delete logic
- traversal control

If this is shaky → you’ll fail harder problems like:

- reverse
- cycle detection
- intersection
