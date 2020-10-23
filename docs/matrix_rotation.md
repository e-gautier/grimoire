# Matrix rotation
```python
import unittest


def show(matrix):
    for row in matrix:
        print(row)


def rotate(matrix):
    for j in range(len(matrix) // 2):
        for i in range(j, len(matrix) - 1 - j):
            tmp = matrix[j][i]
            matrix[j][i] = matrix[i][len(matrix[0]) - 1 - j]
            matrix[i][len(matrix[0]) - 1 - j] = matrix[len(matrix) - 1 - j][len(matrix[len(matrix) - 1]) - 1 - i]
            matrix[len(matrix) - 1 - j][len(matrix[len(matrix) - 1]) - 1 - i] = matrix[len(matrix) - 1 - i][j]
            matrix[len(matrix) - 1 - i][j] = tmp


class TestCase(unittest.TestCase):
    def test_rotation(self):
        matrix = [
            [1, 2, 3, 4],
            [1, 2, 3, 4],
            [1, 2, 3, 4],
            [1, 2, 3, 4]
        ]

        rotate(matrix)

        self.assertEqual(
            [
                [4, 4, 4, 4],
                [3, 3, 3, 3],
                [2, 2, 2, 2],
                [1, 1, 1, 1]
            ],
            matrix
        )

        matrix = [
            [1, 2, 3],
            [1, 2, 3],
            [1, 2, 3]
        ]

        rotate(matrix)

        self.assertEqual(
            [
                [3, 3, 3],
                [2, 2, 2],
                [1, 1, 1]
            ],
            matrix
        )


if __name__ == '__main__':
    unittest.main()
```