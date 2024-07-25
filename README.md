<div align="center">
  <img height="60" src="https://img.icons8.com/color/344/javascript.png">
  <h1>100 JavaScript Coding Interview Questions</h1>
</div>

> [!NOTE]  
> This repo was created in 2024 and the questions provided here are therefore based on the JavaScript syntax and behavior at that time. Since JavaScript is a constantly evolving language, there are newer language features that are not covered by the questions here.

---

### Coding interview questions for arrays

---
###### 1. How do remove duplicates from a given array?

```javascript
function removeDuplicates(arr) {
  return arr.filter((item, index) => arr.indexOf(item) === index);
}

// Example usage:
const arrayWithDuplicates = [1, 2, 2, 3, 4, 4, 5];
const uniqueArray = removeDuplicates(arrayWithDuplicates);
console.log(uniqueArray); // Output: [1, 2, 3, 4, 5]
```
---
###### 2. How do you search for a target value in a rotated array?

```javascript
function searchRotatedArray(nums, target) {
  let left = 0;
  let right = nums.length - 1;

  while (left <= right) {
    const mid = Math.floor((left + right) / 2);

    if (nums[mid] === target) {
      return mid;
    }

    // Determine which half is sorted
    if (nums[left] <= nums[mid]) { // Left half is sorted
      if (nums[left] <= target && target < nums[mid]) {
        right = mid - 1;
      } else {
        left = mid + 1;
      }
    } else { // Right half is sorted
      if (nums[mid] < target && target <= nums[right]) {
        left = mid + 1;
      } else {
        right = mid - 1;
      }
    }
  }

  return -1; // Target not found
}

// Example usage:
const rotatedArray = [4, 5, 6, 7, 0, 1, 2];
const target = 0;
const result = searchRotatedArray(rotatedArray, target);
console.log(result); // Output: 4 (index of target 0 in the rotated array)

```
---

###### 3. How do you find the missing number in a given integer array of 1 to 100?

$$
 sum =  \begin{pmatrix}
    (n)(n+1)\\
  \hline
   2
  \end{pmatrix}
$$

$$
n=100;
$$
Expected 
$$
  sum =  \begin{pmatrix}
    (100)(100+1)\\
  \hline
   2
  \end{pmatrix}=5050
$$

```javascript
function findMissingNumber(arr) {
  const n = 100;
  const expectedSum = (n * (n + 1)) / 2;
  const actualSum = arr.reduce((acc, num) => acc + num, 0);
  
  return expectedSum - actualSum;
}

// Example usage:
const arrayWithMissingNumber = [1, 2, 3, /* ..., */ 99, 100]; // Example array with a missing number
const missingNumber = findMissingNumber(arrayWithMissingNumber);
console.log(missingNumber); // Output: The missing number

```
---



