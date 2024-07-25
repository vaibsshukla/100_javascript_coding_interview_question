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
