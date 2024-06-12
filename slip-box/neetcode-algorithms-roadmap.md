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

## Notes

### My Style of Binary Search

```javascript
const search = (nums, target) => {
    let left = 0;
    let right = nums.length - 1;

    while(left <= right){
        const mid = Math.floor((left + right) / 2);

        if(nums[mid] === target) return mid;

        if(nums[mid] < target) {
            left = mid + 1;
        } else {
            right = mid -1;
        }
    }

    return -1;
};
```



## Resources

- How I Would Learn LeetCode If I Could Start Over [(video)](https://www.youtube.com/watch?v=aHZW7TuY_yo)
