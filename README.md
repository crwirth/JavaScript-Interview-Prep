# JavaScript-Interview-Prep

JavaScript Interview Prep Materials

Array Methods:

1. find()
- Iterates through an array and runs a callback on each value
- If the call back returns true at any point will return the value in the array that we are iterating ober
- Otherwise returns undefined

```javascript
let arr = [1,2,3];

arr.find(function(value, index, array){
  return value === 2;
});

// 2
```
2. findIndex()
- If the callback returns true for any single value, return the index at which that value is found
- Otherwise, return -1

```javascript
let arr = [1,2,3];

arr.findIndex(function(value, index, array){
  return value < 2;
}); // 0
```



