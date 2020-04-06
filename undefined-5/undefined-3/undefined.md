# 퀵소트

```javascript
const quickSort = (arr, l, r) => {
    if (l < r) {
        const p = partision(arr, l, r);

        quickSort(arr, l, p - 1);
        quickSort(arr, p + 1, r);
    }
}

const partision = (arr, l, r) => {
    let i = l-1;

    for(let j=l; j <= r-1; j++) {
        if (arr[j] < arr[r]) {
            i++;
            swap(arr, i, j);
        }
    }
    i++;
    swap(arr, i, r);
    return i;
}

const swap = (arr, i, j) => {
    const a = arr[i];
    arr[i] = arr[j];
    arr[j] = a;
}
```



