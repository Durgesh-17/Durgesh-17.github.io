---
title: DSA in Python (Day 3)
date: 2023-05-30 18:00:00 +0530
categories: [DSA, Linked lists]
tags: [dsa in python, linked list, list] #tags should be lower cases
---

## Problem

> **QUESTION**: Write a function to reverse a linked list

Before we answer this question, we need to answer:

- What do we mean by linked list?
- How do we create a linked list in Python?
- How do we store numbers in a linked list?
- How do we retrieve numbers in a linked list

## Linked List

A linked list is a _data structure_ used for storing a sequence of elements. It's data with some structure (the sequence).

![linked list](/assets/img/linked-list.webp)

We'll implement linked lists which support the following operations:

- Create a list with given elements
- Display the elements in a list
- Find the number of elements in a list
- Retrieve the element at a given position
- Add or remove element(s)

```python
class Node():
    def __init__(self, a_number):
        self.data = a_number
        self.next = None
```

```python
class LinkedList():
    def __init__(self):
        self.head = None
```

```python
list1 = LinkedList()
list1.head = Node(2)
list1.head.next = Node(3)
list1.head.next.next = Node(4)
```

While it's OK to set value like this, we can add a couple of arguments.

```python
class LinkedList():
    def __init__(self):
        self.head = None

    def append(self, value):
        if self.head is None:
            self.head = Node(value)
        else:
            current_node = self.head
            while current_node.next is not None:
                current_node = current_node.next
            current_node.next = Node(value)

    def show_elements(self):
        current = self.head
        while current is not None:
            print(current.data)
            current = current.next

    def length(self):
        result = 0
        current = self.head
        while current is not None:
            result += 1
            current = current.next
        return result

    def get_element(self, position):
        i = 0
        current = self.head
        while current is not None:
            if i == position:
                return current.data
            current = current.next
            i += 1
        return None
```

```python
list2 = LinkedList()
list2.append(2)
list2.append(3)
list2.append(5)
list2.append(9)
```

Given a list of size `N`, the the number of statements executed for each of the steps:

- `append`: N steps
- `length`: N steps
- `get_element`: N steps
- `show_element`: N steps

## Reversing a Linked List - Solution

Here's a simple program to reverse a linked list.

```python
def reverse(l):
    if l.head is None:
        return

    current_node = l.head
    prev_node = None

    while current_node is not None:
        # Track the next node
        next_node = current_node.next

        # Modify the current node
        current_node.next = prev_node

        # Update prev and current
        prev_node = current_node
        current_node = next_node

    l.head = prev_node
```
