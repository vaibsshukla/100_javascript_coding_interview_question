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


