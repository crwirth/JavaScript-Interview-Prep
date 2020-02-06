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




