### Quick Sort

```
function quickSort(arr){
    // If arr length is less that 1 then we can directly return that arr
    if(arr.length < 1) return arr;
    
    // we need to take a number to devide the array and check with pivot for small or large numbers 
    // we can take any number as pivot but preferrablew we take last element as pivot so it is good to traverse to each element 
    let pivot = arr[arr.length - 1];
    let left = [],right = [];
    
    for(let i = 0;i<arr.length - 1;i++){
        if(arr[i] < pivot) left.push(arr[i]) 
        else right.push(arr[i])
    }
    
    return [...quickSort(left) , pivot , ...quickSort(right)];
}

let arr = [123,23,3,55,2,2,5,6,7567,3,534,0];
console.log(quickSort(arr));
```
