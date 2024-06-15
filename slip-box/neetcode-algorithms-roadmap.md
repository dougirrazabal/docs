# NeetCode Algorithms Roadmap

Status: ⚠️ WIP

## Research

LeetCode is challenging and should be approached as a difficult subject.

### Start with the basics

Master the core algorithms until you understand the reasoning behind each line of code:

- Binary Search
- DFS (Depth-First Search)
- BFS (Breadth-First Search)
- Sliding Window

## JavaScript => Python
I’ve been solving LeetCode problems using JavaScript, and I’ve reached a point where I need built-in data structures for medium difficulty problems. Implementing these data structures will make the JavaScript code more complex.

### My Style of Binary Search

```python
def search(nums, target):
    left = 0
    right = len(nums) - 1

    while left <= right:
        mid = (left + right) // 2 # Double slash rounds down

        if nums[mid] == target:
            return mid

        if nums[mid] < target:
            left = mid + 1
        else:
            right = mid - 1

    return -1
```



## Resources

- How I Would Learn LeetCode If I Could Start Over [(video)](https://www.youtube.com/watch?v=aHZW7TuY_yo)
- Python for Coding Interviews - Everything you need to Know [(video)](https://www.youtube.com/watch?v=0K_eZGS5NsU)
