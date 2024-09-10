<div align="center">
  <img height="60" src="https://img.icons8.com/color/344/javascript.png">
  <h1>100 JavaScript Coding Interview Questions</h1>
</div>

> [!NOTE]  
> This repo was created in 2024 and the questions provided here are therefore based on the JavaScript syntax and behavior at that time. Since JavaScript is a constantly evolving language, there are newer language features that are not covered by the questions here.

# Table of Contents
- [Coding inter questions for arrays](#Coding-interview-questions-for-arrays)

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

###### 4. How do you find the duplicate number on a given integer array?

```javascript
function duplicateNumber(arr){
    let unique = []
    let duplicate = []
    for (const iterator of arr) {
        if(!unique.includes(iterator)){
            unique.push(iterator)
        }else{
            duplicate.push(iterator)
        }
    }
    return duplicate
    
}

let arr =[1, 1, 2, 2, 3, 4, 5]
console.log(duplicateNumber(arr)) // [ 1, 2 ]
```
---

###### 5. How do you find the largest and smallest number in an unsorted integer array?


```javascript
function findMaxMin(arr){
    let max = arr[0]
    let min = arr[0]
    for (const iterator of arr) {
       if(max <iterator){
        max = iterator
       }
       if(min > iterator){
        min = iterator
       }
        
    }
    return {max, min}
}

let arr =[6,2,7,9,1,8]
console.log(findMaxMin(arr))  // { max: 9, min: 1 }
```
---

###### 6. How do you find all pairs of an integer array whose sum is equal to a given number?


```javascript
function findPair(arr, tar){
let temp = []

for (let i = 0; i < arr.length; i++) {
    const first = arr[i];
    for (let j = i+1; j < arr.length; j++) {
        const second = arr[j];
        if(first+second == tar){
            temp.push({first,second})
        }
    }   
}
    return temp
}

let arr =[6,2,7,9,1,8,]
console.log(findPair(arr, 9)) // [ { first: 2, second: 7 }, { first: 1, second: 8 } ]
```
---

###### 7. How do you remove duplicates from an array in place?

```javascript
function removeDuplicate(arr){
    let unique = []
    let sortedArr = arr.sort((a,b)=>a-b)
    for (let index = 0; index < sortedArr.length; index++) {
        if(!unique.includes(sortedArr[index])){
unique.push(sortedArr[index])
        }
    }
    return unique
}
let arr = [9,1, 1, 2, 2, 3, 4, 5]

let uniqueEle = removeDuplicate(arr)
console.log(uniqueEle) // [ 1, 2, 3, 4, 5, 9 ]
```
---
###### 8. How to rotate an array left and right by a given number K?

```javascript
function rotateLeft(arr, noOfItems){
    let n = arr.length
    if(n>=noOfItems){
    return [...arr.slice(noOfItems),...arr.slice(0,noOfItems)]
    }
}

function rotateRight(arr, noOfItems){
    return [...arr.slice(arr.length-2),...arr.slice(0,arr.length-noOfItems)]

}

let arr = [1,2,3,4,5,6,7,8]

let leftRotatedArr = rotateLeft(arr,2)
console.log(leftRotatedArr) //[ 3, 4, 5, 6, 7, 8, 1, 2 ]

let arr1 = [1,2,3,4,5,6,7,8]

console.log(rotateRight(arr1,2)) // [ 7, 8, 1, 2, 3, 4, 5, 6 ]
```
---

###### 9. How do you find duplicates from an unsorted array?

```javascript
function findDuplicates(arr) {
    let seen = new Set();
    let duplicates = new Set();

    for (let num of arr) {
        if (seen.has(num)) {
            duplicates.add(num);
        } else {
            seen.add(num);
        }
    }

    return Array.from(duplicates);
}

let arr = [1, 2, 3, 1, 2, 3, 4, 5, 3, 6];
console.log(findDuplicates(arr)); // Output: [1, 2, 3]
```
---

###### 10. Given an array of integers sorted in ascending order, find the starting and ending position of a given value.

```javascript
function findIndex(arr,tar){
    let tempArr = [...arr]
   let start;
   let end;
   for (let index = 0; index < tempArr.length; index++) {
    if(tempArr[index] == tar){
    start = index
    break;}
   }

   for (let index = tempArr.length-1; index > 0; index--) {
    if(tempArr[index] == tar){
     end = index
     break;
    }
   }
   console.log(start)
   console.log(end)

   if(start == end){
    return ("Only One key present"+start)
   }else{
   return ("Start Index "+start+ " "+ " End "+ end)
   }
  
}

let arr = [ 1, 2, 7, 8, 8, 9, 8, 0, 0, 0, 8 ];
let str= findIndex(arr,8)
console.log(str)  // 'Start Index 3  End 10'


```
---

###### 11. Given an unsorted array of integers, find the length of the longest consecutive elements sequence.

```javascript
function longestConsecutive(nums) {
    if (nums.length === 0) return 0;
    
    const numSet = new Set(nums);
    let maxLength = 0;
    
    for (const num of numSet) {
        // Check if it's the start of a sequence
        if (!numSet.has(num - 1)) {
            console.log(num)

            let currentNum = num;
            let currentStreak = 1;
            
            // Count the length of the sequence
            while (numSet.has(currentNum + 1)) {
                currentNum++;
                currentStreak++;
            }
            
            // Update the max length
            maxLength = Math.max(maxLength, currentStreak);
        }
    }
    
    return maxLength;
}

const nums = [100, 4, 200, 1, 3, 2];
console.log(longestConsecutive(nums)); // Output: 4 (sequence is [1, 2, 3, 4])

```
---

###### 12. Given an integer array, find the contiguous subarray (containing at least one number) which has the largest sum and return its sum.
This problem is a classic example of Kadane's Algorithm, which efficiently solves the "Maximum Subarray" problem. Here's a breakdown of the approach:

**`// ->`** Approach:

1. Initialize two variables:
2. current_sum: Tracks the sum of the current subarray.
3. max_sum: Tracks the maximum sum encountered so far.
4. Traverse the array and for each element, decide whether to include it in the current subarray or start a new subarray from that element.
5. Update the max_sum whenever a larger sum is found.

```javascript
function maxSubArray(nums) {
    let current_sum = nums[0];
    let max_sum = nums[0];

    for (let i = 1; i < nums.length; i++) {
        current_sum = Math.max(nums[i], current_sum + nums[i]);
        max_sum = Math.max(max_sum, current_sum);
    }

    return max_sum;
}
let nums = [-2,1,-3,4,-1,2,1,-5,4];
console.log(maxSubArray(nums)); // Output: 6

```
---

###### 13. How do you reverse an array in place in Javascript?

**`// ->`** Approach:

Initialization: left starts at index 0 and right starts at the last index of the array.

Swapping: The values at the left and right indices are swapped using a temporary variable temp.

Pointers Update: After each swap, left is incremented and right is decremented to move towards the center of the array.

Termination: The loop terminates when left is no longer less than right, meaning all necessary swaps have been made.


```javascript
function reverseArray(arr) {
    let left = 0;            // Pointer starting at the beginning
    let right = arr.length - 1; // Pointer starting at the end

    while (left < right) {
        // Swap the elements at the left and right pointers
        let temp = arr[left];
        arr[left] = arr[right];
        arr[right] = temp;

        // Move pointers towards each other
        left++;
        right--;
    }

    return arr; // The array is now reversed in place
}

// Example usage:
let array = [1, 2, 3, 4, 5];
console.log(reverseArray(array)); // Output: [5, 4, 3, 2, 1]

```
---

###### 14. How are duplicates removed from an array without using any library?

```javascript
function removeDuplicates(arr) {
    let uniqueArray = [];
    let seen = new Map(); // Map to track seen values

    for (let i = 0; i < arr.length; i++) {
        let item = arr[i];
        if (!seen.has(item)) {
            uniqueArray.push(item);
            seen.set(item, true); // Mark item as seen
        }
    }

    return uniqueArray;
}

// Example usage:
let array = [1, 2, 2, 3, 4, 4, 5];
console.log(removeDuplicates(array)); // Output: [1, 2, 3, 4, 5]
```
---

###### 15. How to convert a byte array to a String?


```javascript
// Create a byte array (Uint8Array)
const byteArray = new Uint8Array([72, 101, 108, 108, 111]); // Represents the string "Hello"

// Create a TextDecoder instance
const decoder = new TextDecoder('utf-8'); // Specify the encoding (utf-8 is the default)

// Decode the byte array into a string
const decodedString = decoder.decode(byteArray);

console.log(decodedString); // Output: "Hello"
```
---

###### 16. How do you perform a binary search in a given array?


```javascript
function binarySearch(arr, target) {
    let low = 0;
    let high = arr.length - 1;

    while (low <= high) {
        let mid = Math.floor((low + high) / 2);

        if (arr[mid] === target) {
            return mid; // Target found at index mid
        } else if (arr[mid] < target) {
            low = mid + 1; // Search in the right half
        } else {
            high = mid - 1; // Search in the left half
        }
    }

    return -1; // Target not found
}

// Example usage:
let sortedArray = [1, 3, 5, 7, 9, 11];
let target = 7;
console.log(binarySearch(sortedArray, target)); // Output: 3 (index of 7)
```
---






