# NeetCode Algorithms Roadmap

LeetCode is challenging and should be approached as a difficult subject.

## Start with the basics

Master the core algorithms until you understand the reasoning behind each line of code:

- Binary Search
- DFS (Depth-First Search)
- BFS (Breadth-First Search)
- Sliding Window

## My Style of Binary Search

```python
def binarySearch(arr, target):
    L, R = 0, len(arr) - 1

    while L <= R:
        mid = (L + R) // 2

        if target > arr[mid]:
            L = mid + 1
        elif target < arr[mid]:
            R = mid - 1
        else:
            return mid
    return -1
```

## Resources

- How I Would Learn LeetCode If I Could Start Over [(video)](https://www.youtube.com/watch?v=aHZW7TuY_yo)
- Python for Coding Interviews - Everything you need to Know [(video)](https://www.youtube.com/watch?v=0K_eZGS5NsU)
