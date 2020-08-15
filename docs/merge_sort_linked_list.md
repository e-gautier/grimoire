# Merge sort two linked list

```python
class Node:
    def __init__(self, value, next=None):
        self.value = value
        self.next = next


def display(node):
    while node != None:
        print(node.value, end="-")
        node = node.next
    print()


def get_middle_node(l):
    """
    Using a slow and a fast pointer.
    """
    if l == None:
        return l

    slow = l
    fast = l

    while fast.next != None and fast.next.next != None:
        slow = slow.next
        fast = fast.next.next

    return slow


def merge(left, right):
    result = None

    if left == None:
        return right
    if right == None:
        return left

    if left.value <= right.value:
        result = left
        result.next = merge(left.next, right)
    else:
        result = right
        result.next = merge(left, right.next)

    return result


def merge_sort(l):
    if l == None or l.next == None:
        return l

    middle = get_middle_node(l)
    next_from_middle = middle.next
    middle.next = None

    left = merge_sort(l)
    right = merge_sort(next_from_middle)

    return merge(left, right)


head = Node(
    4, Node(2, Node(8, Node(4, Node(3, Node(4, Node(1, Node(1, Node(9))))))))
)

display(head)
display(merge_sort(head))

```

> source: https://www.geeksforgeeks.org/merge-sort-for-linked-list/
