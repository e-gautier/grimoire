# Algorithms and data structures cheat sheet

|||
| :- | :- |
| Levenshtein Distance Algorithm | Useful for string edition |
| Kosaraju Algorithm | Useful for graph compression |
| Sparse matrix data structure | (>50% zero-entries) used as a matrix w/o loosing space |
| Nagle's algorithm | Used to improve the efficency of TCP connections when dealing with small packets to prevent a Silly Window Syndrome |

## Ranges
Two ranges are overlapping if `x1 <= y2 AND x2 <= y1`:
```python
import unittest


def is_overlapping(r1, r2):
    if r1[0] <= r2[1] and r2[0] <= r1[1]:
        return True

    return False


class TestCase(unittest.TestCase):
    def test_overlapping(self):
        self.assertTrue(is_overlapping([2, 12], [1, 3]))
        self.assertFalse(is_overlapping([1, 3], [5, 12]))


if __name__ == '__main__':
    unittest.main()
```
