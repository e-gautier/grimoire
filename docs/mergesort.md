# mergesort

```python
def merge_sort(a):
    if len(a) <= 1:
        return

    middle = len(a) // 2

    left = a[:middle]
    right = a[middle:]

    merge_sort(left)
    merge_sort(right)

    k = i = j = 0

    while i < len(left) and j < len(right):
        if left[i] <= right[j]:
            a[k] = left[i]
            i += 1
        else:
            a[k] = right[j]
            j += 1
        k += 1

    while i < len(left):
        a[k] = left[i]
        i += 1
        k += 1

    while j < len(right):
        a[k] = right[j]
        j += 1
        k += 1

merge_sort(a)

```
