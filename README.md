## QUICK SORT 
### Example: Given a list of product reviews, sort them by rating (1-5 stars)
```js
function quickSort(arr){
    if(arr.length <= 1) return arr ;
    
    let pivot = arr[arr.length - 1];
    let left = [];let right = [];
    
    for(let i = 0;i < arr.length - 1;i++){
        if(arr[i] < pivot) left.push(arr[i])
        else right.push(arr[i])
    }
    
    return [...quickSort(left),pivot,...quickSort(right)]
    
}
let ratings = [5, 3, 1, 4, 2, 3, 5, 4, 1, 2];
console.log(quickSort(ratings)); // [1,1,2,2,3,3,4,4,5,5]
```

## TWO POINTER
### Example: Finding two products within budget
```js
function findPair(arr,k){
    let left = 0, right = arr.length-1;
    
    for(let i =0;i<arr.length-1;i++){
        if(arr[left]+arr[right] === k) return [arr[left],arr[right]];
        else if(arr[left]+arr[right] < k) left++;
        else right++
    }
}


let prices = [10, 20, 30, 40, 50, 60, 70]; // Sorted list
let budget = 90;
console.log(findPair(prices, budget)); // Output: [20, 70]
```

## Sliding Window
### Example: Find the Most Active User Session (Website Analytics) ,Given website login timestamps, find the 1-hour window with maximum logins
```js
function mostActiveWindow(arr,k){
    let currentWindowSum = 0,maxSum = 0;
    let startMinute = 0;
    for(let i = 0; i < k; i++){
        currentWindowSum += arr[i];
    }
    maxSum = currentWindowSum;
    
    for(let i = k; i < arr.length; i++) {
        currentWindowSum += arr[i] - arr[i-k];
        if(currentWindowSum > maxSum){
            maxSum = currentWindowSum;
            startMinute = i - k + 1;
        }
    }
    
    return {
        maxSum,
        startMinute,
        endMinute: startMinute + k -1
    }
}
let loginTimestamps = [5, 10, 15, 30, 40, 50, 80, 90, 100, 120];
let k = 3;
console.log(mostActiveWindow(loginTimestamps, k));
```
