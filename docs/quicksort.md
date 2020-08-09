# Quicksort

```python
def quick_sort(a, l, h):
    if l >= h:
        return

    pivot = a[h]
    biggest = l

    for j in range(l, h):
        if a[j] < pivot:
            a[j], a[biggest] = a[biggest], a[j]
            biggest += 1

    a[biggest], a[h] = a[h], a[biggest]

    quick_sort(a, l, biggest - 1)
    quick_sort(a, biggest + 1, h)


quick_sort(a, 0, len(arr) - 1)

```
